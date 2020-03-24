---
title: 'Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
ms.openlocfilehash: 14fc26709541135e80a2e0fe4de872cc75221874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213004"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

> [!NOTE]
>  Sie können jetzt Datensätze in einer Sammeloperation effizienter hinzufügen. Weitere Informationen finden Sie unter [Recordset: Hinzufügen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
>  Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Massen Abrufen von Zeilen verwenden, finden Sie weitere Informationen unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Mit aktualisierbaren Momentaufnahmen und Dynasets können Sie Datensätze hinzufügen, bearbeiten (aktualisieren) und löschen. In diesem Thema wird Folgendes erläutert:

- [Bestimmen, ob das Recordset aktualisierbar ist](#_core_determining_whether_your_recordset_is_updatable).

- Vorgehens [Weise beim Hinzufügen eines neuen Datensatzes](#_core_adding_a_record_to_a_recordset)

- [Bearbeiten eines vorhandenen Datensatzes](#_core_editing_a_record_in_a_recordset)

- [Löschen eines Datensatzes](#_core_deleting_a_record_from_a_recordset).

Weitere Informationen zur Art und Weise, wie Updates ausgeführt werden und wie Sie für andere Benutzer angezeigt werden, finden Sie unter [Recordset: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Wenn Sie einen Datensatz hinzufügen, ändern oder löschen, ändert das Recordset die Datenquelle normalerweise sofort. Alternativ können Sie Gruppen zusammengehöriger Aktualisierungen zu Transaktionen zusammenfassen. Während einer Transaktion werden die Aktualisierungen nicht vor Bestätigung der Transaktion endgültig. So können Sie die Änderungen zurücksetzen. Weitere Informationen zu Transaktionen finden Sie unter [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

In der folgenden Tabelle ist zusammengefasst, welche Optionen für Recordsets zur Verfügung stehen mit den jeweiligen Aktualisierungsmerkmalen.

### <a name="recordset-readupdate-options"></a>Lese- und Aktualisierungsoptionen von Recordsets

|type|Lesen|Datensatz bearbeiten|Datensatz löschen|Neue hinzufügen (anhängen)|
|----------|----------|-----------------|-------------------|------------------------|
|Schreibgeschützt|J|N|N|N|
|Nur erweiterbar|J|N|N|J|
|Ohne Einschränkungen aktualisierbar|J|J|J|J|

##  <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>Ermitteln, ob das Recordset aktualisierbar ist

Ein Recordset-Objekt ist aktualisierbar, wenn die Datenquelle aktualisierbar ist und Sie das Recordset als aktualisierbar geöffnet haben. Außerdem hängt die Aktualisierbarkeit von der verwendeten SQL-Anweisung ab, von den Fähigkeiten des ODBC-Treibers und davon, ob die ODBC-Cursorbibliothek geladen ist. Sie können ein schreibgeschütztes Recordset oder eine schreibgeschützte Datenquelle nicht aktualisieren.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>So stellen Sie fest, ob das Recordset aktualisierbar ist

1. Ruft die [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) -Member-Funktion des Recordset-Objekts auf.

   `CanUpdate` gibt einen Wert ungleich 0 (null) zurück, falls das Recordset aktualisierbar ist.

Standardmäßig sind Recordsets vollständig aktualisierbar (Sie können `AddNew`, `Edit`und `Delete` Vorgänge ausführen). Sie können jedoch auch die Option [AppendOnly](../../mfc/reference/crecordset-class.md#open) verwenden, um aktualisierbare Recordsets zu öffnen. Zu einem auf diese Weise geöffneten Recordset können Sie lediglich mit `AddNew` neue Datensätze hinzufügen. Sie können keine vorhandenen Datensätze bearbeiten oder löschen. Sie können testen, ob ein Recordset nur zum Anhängen geöffnet ist, indem Sie die [CanAppend](../../mfc/reference/crecordset-class.md#canappend) -Member-Funktion aufrufen. `CanAppend` gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset vollständig aktualisierbar ist oder nur zum Anhängen geöffnet ist.

Der folgende Codeausschnitt zeigt, wie Sie `CanUpdate` in einem Recordset-Objekt mit dem Namen `rsStudentSet` aufrufen können:

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
>  Wenn Sie die Aktualisierung eines Recordsets durch Aufrufen von `Update`vorbereiten, achten Sie darauf, dass das Recordset alle Spalten enthält, die den Primärschlüssel der Tabelle bilden (oder alle Spalten eines eindeutigen Indexes in der Tabelle). In einigen Fällen kann das Framework zur Identifizierung des Datensatzes, der in der Tabelle aktualisiert werden soll, nur die Spalten verwenden, die im Recordset ausgewählt sind. Wenn nicht sämtliche benötigten Spalten zur Verfügung stehen, werden möglicherweise mehrere Datensätze in der Tabelle aktualisiert. Hierdurch kann die referenzielle Integrität der Tabelle beschädigt werden. In diesem Fall löst das Framework Ausnahmen aus, wenn Sie `Update`aufruft.

##  <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>Hinzufügen eines Datensatzes zu einem Recordset

Sie können einem Recordset neue Datensätze hinzufügen, wenn die [kanappend](../../mfc/reference/crecordset-class.md#canappend) -Member-Funktion einen Wert ungleich 0 (null) zurückgibt.

#### <a name="to-add-a-new-record-to-a-recordset"></a>So fügen Sie einem Recordset einen neuen Datensatz hinzu

1. Stellen Sie sicher, dass das Recordset erweiterbar ist.

1. Ruft die [AddNew](../../mfc/reference/crecordset-class.md#addnew) -Member-Funktion des Recordset-Objekts auf.

   `AddNew` bereitet das Recordset so vor, dass dieses als Bearbeitungspuffer fungieren kann. Alle Felddatenmember werden auf den Sonderwert NULL festgelegt und als unverändert gekennzeichnet, sodass nur geänderte (geänderte) Werte in die Datenquelle geschrieben werden, wenn Sie [Update](../../mfc/reference/crecordset-class.md#update)aufruft.

1. Stellen Sie die Werte der Felddatenmember des neuen Datensatzes ein.

   Weisen Sie den Felddatenmembern Werte zu. Felddatenelemente, denen Sie keinen Wert zugewiesen haben, werden nicht in die Datenquelle geschrieben.

1. Ruft die `Update` Member-Funktion des Recordset-Objekts auf.

   `Update` schließt die Addition ab, indem der neue Datensatz in die Datenquelle geschrieben wird. Weitere Informationen zu Vorgängen, wenn Sie `Update`nicht aufzurufen, finden Sie unter [Recordset: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Informationen dazu, wie das Hinzufügen von Datensätzen funktioniert und wann hinzugefügte Datensätze im Recordset sichtbar sind, finden Sie unter [Recordset: Funktionsweise von AddNew, Edit und delete work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

Das folgende Beispiel zeigt, wie Sie einen neuen Datensatz hinzufügen:

```cpp
if( !rsStudent.Open( ) )
    return FALSE;
if( !rsStudent.CanAppend( ) )
    return FALSE;                      // no field values were set
rsStudent.AddNew( );
rsStudent.m_strName = strName;
rsStudent.m_strCity = strCity;
rsStudent.m_strStreet = strStreet;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not added; no field values were set." );
    return FALSE;
}
```

> [!TIP]
>  Um einen `AddNew` oder einen `Edit` aufzurufen, führen Sie einfach einen weiteren aufrufen `AddNew` oder `Edit` aus, oder rufen Sie `Move` mit dem *AFX_MOVE_REFRESH* -Parameter auf. Datenmember werden auf Ihre vorherigen Werte zurückgesetzt, und Sie befinden sich weiterhin im `Edit` oder `Add` Modus.

##  <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>Bearbeiten eines Datensatzes in einem Recordset

Sie können vorhandene Datensätze bearbeiten, wenn die [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) -Member-Funktion Ihres Recordsets einen Wert ungleich 0 (null) zurückgibt.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>So bearbeiten Sie einen vorhandenen Datensatz in einem Recordset

1. Stellen Sie sicher, dass das Recordset aktualisierbar ist.

1. Wechseln Sie zu dem Datensatz, den Sie aktualisieren möchten.

1. Ruft die [Edit](../../mfc/reference/crecordset-class.md#edit) Member-Funktion des Recordset-Objekts auf.

   `Edit` bereitet das Recordset so vor, dass dieses als Bearbeitungspuffer fungieren kann. Alle Felddatenmember werden so markiert, dass das Recordset später feststellen kann, ob sie geändert wurden. Die neuen Werte für geänderte Felddatenmember werden in die Datenquelle geschrieben, wenn Sie [Update](../../mfc/reference/crecordset-class.md#update)aufruft.

1. Stellen Sie die Werte der Felddatenmember des neuen Datensatzes ein.

   Weisen Sie den Felddatenmembern Werte zu. Felddatenmember, denen Sie keine Werte zuweisen, bleiben unverändert.

1. Ruft die `Update` Member-Funktion des Recordset-Objekts auf.

   `Update` schließt die Bearbeitung ab, indem der geänderte Datensatz in die Datenquelle geschrieben wird. Weitere Informationen zu Vorgängen, wenn Sie `Update`nicht aufzurufen, finden Sie unter [Recordset: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Nachdem Sie einen Datensatz bearbeitet haben, bleibt er der aktuelle Datensatz.

Das folgende Beispiel zeigt einen `Edit` Vorgang. Dabei wird vorausgesetzt, dass der Benutzer zu einem Datensatz gewechselt hat, den er bearbeiten möchte.

```cpp
rsStudent.Edit( );
rsStudent.m_strStreet = strNewStreet;
rsStudent.m_strCity = strNewCity;
rsStudent.m_strState = strNewState;
rsStudent.m_strPostalCode = strNewPostalCode;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not updated; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> Um einen `AddNew` oder einen `Edit` aufzurufen, führen Sie einfach einen weiteren aufrufen `AddNew` oder `Edit` aus, oder rufen Sie `Move` mit dem *AFX_MOVE_REFRESH* -Parameter auf. Datenmember werden auf Ihre vorherigen Werte zurückgesetzt, und Sie befinden sich weiterhin im `Edit` oder `Add` Modus.

##  <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>Löschen eines Datensatzes aus einem Recordset

Sie können Datensätze löschen, wenn die [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) -Member-Funktion Ihres Recordsets einen Wert ungleich 0 (null) zurückgibt.

#### <a name="to-delete-a-record"></a>So löschen Sie einen Datensatz

1. Stellen Sie sicher, dass das Recordset aktualisierbar ist.

1. Wechseln Sie zu dem Datensatz, den Sie aktualisieren möchten.

1. Ruft die [Delete](../../mfc/reference/crecordset-class.md#delete) -Member-Funktion des Recordset-Objekts auf.

   `Delete` markiert den Datensatz sofort als gelöscht, sowohl im Recordset als auch in der Datenquelle.

   Im Gegensatz zu `AddNew` und `Edit`hat `Delete` keinen entsprechenden `Update`-Befehl.

1. Wechseln Sie zu einem anderen Datensatz.

   > [!NOTE]
   >  Beim Scrollen durch das Recordset werden gelöschte Datensätze unter Umständen nicht übersprungen. Weitere Informationen finden Sie unter der [isDeleted](../../mfc/reference/crecordset-class.md#isdeleted) -Member-Funktion.

Das folgende Beispiel zeigt einen `Delete` Vorgang. Dabei wird vorausgesetzt, dass der Benutzer zu einem zu löschenden Datensatz gewechselt ist. Nachdem `Delete` aufgerufen wurde, ist es wichtig, zu einem neuen Datensatz zu wechseln.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Weitere Informationen zu den Auswirkungen der Funktionen `AddNew`, `Edit`und `Delete` Member finden Sie unter [Recordset: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
