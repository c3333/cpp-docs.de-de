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
ms.openlocfilehash: 628ffb2feee385a4114b0dbea074f81678c529d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367109"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

> [!NOTE]
> Sie können jetzt Datensätze in einer Sammeloperation effizienter hinzufügen. Weitere Informationen finden Sie unter [Recordset: Hinzufügen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
> Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Abrufen von Massenzeilen verwenden, finden Sie weitere Informationen unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Mit aktualisierbaren Momentaufnahmen und Dynasets können Sie Datensätze hinzufügen, bearbeiten (aktualisieren) und löschen. In diesem Thema wird Folgendes erläutert:

- [So ermitteln Sie, ob Ihr Recordset aufrüstbar ist.](#_core_determining_whether_your_recordset_is_updatable)

- [So fügen Sie einen neuen Datensatz](#_core_adding_a_record_to_a_recordset)hinzu.

- [So bearbeiten Sie einen vorhandenen Datensatz](#_core_editing_a_record_in_a_recordset).

- [So löschen Sie einen Datensatz](#_core_deleting_a_record_from_a_recordset).

Weitere Informationen dazu, wie Updates durchgeführt werden und wie Ihre Updates anderen Benutzern angezeigt werden, finden Sie unter [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Wenn Sie einen Datensatz hinzufügen, ändern oder löschen, ändert das Recordset die Datenquelle normalerweise sofort. Alternativ können Sie Gruppen zusammengehöriger Aktualisierungen zu Transaktionen zusammenfassen. Während einer Transaktion werden die Aktualisierungen nicht vor Bestätigung der Transaktion endgültig. So können Sie die Änderungen zurücksetzen. Informationen zu Transaktionen finden Sie unter [Transaktion (ODBC)](../../data/odbc/transaction-odbc.md).

In der folgenden Tabelle ist zusammengefasst, welche Optionen für Recordsets zur Verfügung stehen mit den jeweiligen Aktualisierungsmerkmalen.

### <a name="recordset-readupdate-options"></a>Lese- und Aktualisierungsoptionen von Recordsets

|type|Lesen|Datensatz bearbeiten|Datensatz löschen|Neue hinzufügen (anhängen)|
|----------|----------|-----------------|-------------------|------------------------|
|Schreibgeschützt|J|N|N|N|
|Nur erweiterbar|J|N|N|J|
|Ohne Einschränkungen aktualisierbar|J|J|J|J|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>Bestimmen, ob Ihr Recordset aktualisierbar ist

Ein Recordset-Objekt ist aktualisierbar, wenn die Datenquelle aktualisierbar ist und Sie das Recordset als aktualisierbar geöffnet haben. Außerdem hängt die Aktualisierbarkeit von der verwendeten SQL-Anweisung ab, von den Fähigkeiten des ODBC-Treibers und davon, ob die ODBC-Cursorbibliothek geladen ist. Sie können ein schreibgeschütztes Recordset oder eine schreibgeschützte Datenquelle nicht aktualisieren.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>So stellen Sie fest, ob das Recordset aktualisierbar ist

1. Rufen Sie die [CanUpdate-Memberfunktion](../../mfc/reference/crecordset-class.md#canupdate) des Recordset-Objekts auf.

   `CanUpdate` gibt einen Wert ungleich 0 (null) zurück, falls das Recordset aktualisierbar ist.

Standardmäßig sind Recordsets vollständig aktualisierbar `AddNew` `Edit`(Sie `Delete` können , und Vorgänge ausführen). Sie können jedoch auch die Option [appendOnly](../../mfc/reference/crecordset-class.md#open) verwenden, um aktualisierbare Recordsets zu öffnen. Zu einem auf diese Weise geöffneten Recordset können Sie lediglich mit `AddNew` neue Datensätze hinzufügen. Sie können keine vorhandenen Datensätze bearbeiten oder löschen. Sie können testen, ob ein Recordset nur zum Anfügen geöffnet ist, indem Sie die [CanAppend-Memberfunktion](../../mfc/reference/crecordset-class.md#canappend) aufrufen. `CanAppend` gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset vollständig aktualisierbar ist oder nur zum Anhängen geöffnet ist.

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
> Wenn Sie sich darauf vorbereiten, `Update`ein Recordset durch Aufrufen zu aktualisieren, achten Sie darauf, dass das Recordset alle Spalten enthält, aus denen der Primärschlüssel der Tabelle (oder alle Spalten eines eindeutigen Indexes in der Tabelle) besteht. In einigen Fällen kann das Framework zur Identifizierung des Datensatzes, der in der Tabelle aktualisiert werden soll, nur die Spalten verwenden, die im Recordset ausgewählt sind. Wenn nicht sämtliche benötigten Spalten zur Verfügung stehen, werden möglicherweise mehrere Datensätze in der Tabelle aktualisiert. Hierdurch kann die referenzielle Integrität der Tabelle beschädigt werden. In diesem Fall löst das Framework `Update`Ausnahmen aus, wenn Sie aufrufen.

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>Hinzufügen eines Datensatzes zu einem Recordset

Sie können einem Recordset neue Datensätze hinzufügen, wenn die [CanAppend-Memberfunktion](../../mfc/reference/crecordset-class.md#canappend) einen Wert ungleich Null zurückgibt.

#### <a name="to-add-a-new-record-to-a-recordset"></a>So fügen Sie einem Recordset einen neuen Datensatz hinzu

1. Stellen Sie sicher, dass das Recordset erweiterbar ist.

1. Rufen Sie die [AddNew-Memberfunktion](../../mfc/reference/crecordset-class.md#addnew) des Recordset-Objekts auf.

   `AddNew` bereitet das Recordset so vor, dass dieses als Bearbeitungspuffer fungieren kann. Alle Felddatenmember werden auf den Sonderwert Null festgelegt und als unverändert markiert, sodass nur geänderte (schmutzige) Werte beim Aufrufen von [Update](../../mfc/reference/crecordset-class.md#update)in die Datenquelle geschrieben werden.

1. Stellen Sie die Werte der Felddatenmember des neuen Datensatzes ein.

   Weisen Sie den Felddatenmembern Werte zu. Felddatenelemente, denen Sie keinen Wert zugewiesen haben, werden nicht in die Datenquelle geschrieben.

1. Rufen Sie die Memberfunktion des Recordset-Objekts `Update` auf.

   `Update`schließt die Hinzufügung ab, indem der neue Datensatz in die Datenquelle geschrieben wird. Informationen zu den Vorjahren, `Update`wenn Sie nicht aufrufen können, finden Sie unter [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Informationen dazu, wie das Hinzufügen von Datensätzen funktioniert und wann hinzugefügte Datensätze in Ihrem Recordset sichtbar sind, finden Sie unter [Recordset: How AddNew, Edit, and Delete Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

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
> Um einen `AddNew` `Edit` oder einen Anruf abzubrechen, rufen Sie einfach einen anderen Aufruf oder `AddNew` `Edit` Aufruf `Move` mit dem Parameter *AFX_MOVE_REFRESH* an. Datenmember werden auf ihre vorherigen Werte `Edit` zurückgesetzt, und Sie befinden sich noch im Modus oder `Add` im Modus.

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>Bearbeiten eines Datensatzes in einem Recordset

Sie können vorhandene Datensätze bearbeiten, wenn die [CanUpdate-Memberfunktion](../../mfc/reference/crecordset-class.md#canupdate) Ihres Recordsets einen Wert ungleich Null zurückgibt.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>So bearbeiten Sie einen vorhandenen Datensatz in einem Recordset

1. Stellen Sie sicher, dass das Recordset aktualisierbar ist.

1. Wechseln Sie zu dem Datensatz, den Sie aktualisieren möchten.

1. Rufen Sie die [Memberfunktion Bearbeiten](../../mfc/reference/crecordset-class.md#edit) des Recordset-Objekts auf.

   `Edit` bereitet das Recordset so vor, dass dieses als Bearbeitungspuffer fungieren kann. Alle Felddatenmember werden so markiert, dass das Recordset später feststellen kann, ob sie geändert wurden. Die neuen Werte für geänderte Felddatenmember werden beim Aufrufen von [Update](../../mfc/reference/crecordset-class.md#update)in die Datenquelle geschrieben.

1. Stellen Sie die Werte der Felddatenmember des neuen Datensatzes ein.

   Weisen Sie den Felddatenmembern Werte zu. Felddatenmember, denen Sie keine Werte zuweisen, bleiben unverändert.

1. Rufen Sie die Memberfunktion des Recordset-Objekts `Update` auf.

   `Update`schließt die Bearbeitung ab, indem der geänderte Datensatz in die Datenquelle geschrieben wird. Informationen zu den Vorjahren, `Update`wenn Sie nicht aufrufen können, finden Sie unter [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Nachdem Sie einen Datensatz bearbeitet haben, bleibt er der aktuelle Datensatz.

Das folgende Beispiel `Edit` zeigt einen Vorgang. Dabei wird vorausgesetzt, dass der Benutzer zu einem Datensatz gewechselt hat, den er bearbeiten möchte.

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
> Um einen `AddNew` `Edit` oder einen Anruf abzubrechen, rufen Sie einfach einen anderen Aufruf oder `AddNew` `Edit` Aufruf `Move` mit dem Parameter *AFX_MOVE_REFRESH* an. Datenmember werden auf ihre vorherigen Werte `Edit` zurückgesetzt, und Sie befinden sich noch im Modus oder `Add` im Modus.

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>Löschen eines Datensatzes aus einem Recordset

Sie können Datensätze löschen, wenn die [CanUpdate-Memberfunktion](../../mfc/reference/crecordset-class.md#canupdate) Ihres Recordsets einen Wert ungleich Null zurückgibt.

#### <a name="to-delete-a-record"></a>So löschen Sie einen Datensatz

1. Stellen Sie sicher, dass das Recordset aktualisierbar ist.

1. Wechseln Sie zu dem Datensatz, den Sie aktualisieren möchten.

1. Rufen Sie die [Löschmemberfunktion](../../mfc/reference/crecordset-class.md#delete) des Recordset-Objekts auf.

   `Delete`markiert den Datensatz sofort als gelöscht, sowohl im Recordset als auch in der Datenquelle.

   Im `AddNew` `Edit`Gegensatz `Delete` zu `Update` und , hat keinen entsprechenden Anruf.

1. Wechseln Sie zu einem anderen Datensatz.

   > [!NOTE]
   >  Beim Scrollen durch das Recordset werden gelöschte Datensätze unter Umständen nicht übersprungen. Weitere Informationen finden [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) Sie unter IsDeleted-Memberfunktion.

Das folgende Beispiel `Delete` zeigt einen Vorgang. Dabei wird vorausgesetzt, dass der Benutzer zu einem zu löschenden Datensatz gewechselt ist. Nachdem `Delete` aufgerufen wird, ist es wichtig, zu einem neuen Datensatz zu wechseln.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Weitere Informationen zu den `AddNew`Auswirkungen `Edit`der `Delete` , - und Memberfunktionen finden Sie unter [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
