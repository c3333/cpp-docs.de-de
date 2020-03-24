---
title: 'Recordset: Funktionsweise von AddNew, Edit und Delete (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
ms.openlocfilehash: 8799ac36c443898f1e32b539f017e682bbf3e033
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212905"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Recordset: Funktionsweise von AddNew, Edit und Delete (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie die Funktionen `AddNew`, `Edit`und `Delete` Member der-Klasse `CRecordset` funktionieren. Folgende Themen werden behandelt:

- [Funktionsweise von Datensätzen](#_core_adding_a_record)

- [Sichtbarkeit hinzugefügter Datensätze](#_core_visibility_of_added_records)

- [Funktionsweise der Bearbeitung von Datensätzen](#_core_editing_an_existing_record)

- [So funktioniert das Löschen von Datensätzen](#_core_deleting_a_record)

> [!NOTE]
>  Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Massen Abrufen von Zeilen verwenden, finden Sie weitere Informationen unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Als Ergänzung können Sie [Daten Satz Feld Austausch lesen: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), in der die entsprechende Rolle von RFX in Aktualisierungs Vorgängen beschrieben wird.

##  <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Hinzufügen eines Datensatzes

Das Hinzufügen eines neuen Datensatzes zu einem Recordset umfasst das Aufrufen der [AddNew](../../mfc/reference/crecordset-class.md#addnew) -Member-Funktion des Recordsets, das Festlegen der Werte der Felddatenmember des neuen Datensatzes und das Aufrufen der [Update](../../mfc/reference/crecordset-class.md#update) -Member-Funktion, um den Datensatz in die Datenquelle zu schreiben.

Als Vorbedingung zum Aufrufen von `AddNew`muss das Recordset nicht als schreibgeschützt geöffnet worden sein. Mithilfe der Funktionen `CanUpdate` und `CanAppend` Member können Sie diese Bedingungen ermitteln.

Wenn Sie `AddNew`abrufen:

- Der Datensatz im Bearbeitungs Puffer wird gespeichert, sodass der Inhalt wieder hergestellt werden kann, wenn der Vorgang abgebrochen wird.

- Die Felddatenmember sind gekennzeichnet, sodass Änderungen später erkannt werden können. Die Felddatenmember sind auch als "bereinigt" (unverändert) markiert und auf einen NULL-Wert festgelegt.

Nachdem Sie `AddNew`aufgerufen haben, stellt der Bearbeitungs Puffer einen neuen, leeren Datensatz dar, der mit Werten gefüllt werden kann. Zu diesem Zweck legen Sie die Werte manuell fest, indem Sie Ihnen zuweisen. Anstatt einen tatsächlichen Datenwert für ein Feld anzugeben, können Sie `SetFieldNull` aufzurufen, um den Wert NULL anzugeben.

Um die Änderungen zu übertragen, nennen Sie `Update`. Wenn Sie `Update` für den neuen Datensatz abrufen:

- Wenn Ihr ODBC-Treiber die `::SQLSetPos` ODBC-API-Funktion unterstützt, verwendet MFC die-Funktion, um den Datensatz in der Datenquelle hinzuzufügen. Mit `::SQLSetPos`kann MFC einen Datensatz effizienter hinzufügen, da er keine SQL-Anweisung erstellen und verarbeiten muss.

- Wenn `::SQLSetPos` nicht verwendet werden kann, führt MFC Folgendes aus:

   1. Wenn keine Änderungen erkannt werden, führt `Update` keine Aktion aus und gibt 0 zurück.

   1. Wenn Änderungen vorhanden sind, erstellt `Update` eine SQL **Insert** -Anweisung. Die Spalten, die von allen Dirty Field-Datenmembern dargestellt werden, sind in der **Insert** -Anweisung aufgeführt. Um das Einschließen einer Spalte zu erzwingen, müssen Sie die Funktion [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) Member aufrufen:

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` führt einen Commit für den neuen Datensatz aus – die **Insert** -Anweisung wird ausgeführt, und der Datensatz wird an die Tabelle in der Datenquelle (und das Recordset, wenn keine Momentaufnahme erfolgt) committet, es sei denn, eine Transaktion wird ausgeführt.

   1. Der gespeicherte Datensatz wird im Bearbeitungs Puffer wieder hergestellt. Der Datensatz, der vor dem `AddNew` aufgerufen wurde, ist wieder aktuell, unabhängig davon, ob die **Insert** -Anweisung erfolgreich ausgeführt wurde.

   > [!TIP]
   > Um die umfassende Kontrolle über einen neuen Datensatz zu erhalten, gehen Sie wie folgt vor: Legen Sie die Werte von Feldern fest, die Werte aufweisen, und legen Sie dann explizit alle Felder fest, die NULL bleiben, indem Sie `SetFieldNull` mit einem Zeiger auf das Feld und den Parameter true (Standard) aufrufen. Wenn Sie sicherstellen möchten, dass ein Feld nicht in die Datenquelle geschrieben wird, müssen Sie `SetFieldDirty` mit einem Zeiger auf das Feld und den Parameter false aufrufen und den Wert des Felds nicht ändern. Um zu ermitteln, ob ein Feld NULL sein darf, wenden Sie `IsFieldNullable`an.

   > [!TIP]
   > Um zu erkennen, wenn der Wert von recordsetdatenmembern geändert wird, verwendet MFC einen PSEUDO_NULL Wert, der für jeden Datentyp geeignet ist, den Sie in einem Recordset speichern können. Wenn Sie ein Feld explizit auf den PSEUDO_NULL Wert festlegen müssen und das Feld bereits als NULL gekennzeichnet ist, müssen Sie auch `SetFieldNull`aufrufen und dabei die Adresse des Felds im ersten Parameter und false im zweiten Parameter übergeben.

##  <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Sichtbarkeit hinzugefügter Datensätze

Wann ist ein hinzugefügter Datensatz für Ihr Recordset sichtbar? Hinzugefügte Datensätze werden manchmal angezeigt und werden manchmal nicht angezeigt, je nach zwei Dingen:

- Die Möglichkeiten des Treibers.

- Das Framework, das von dem Framework genutzt werden kann.

Wenn Ihr ODBC-Treiber die `::SQLSetPos` ODBC-API-Funktion unterstützt, verwendet MFC die-Funktion zum Hinzufügen von Datensätzen. Mit `::SQLSetPos`sind hinzugefügte Datensätze für alle aktualisierbaren MFC-Recordsets sichtbar. Ohne Unterstützung für die-Funktion sind hinzugefügte Datensätze nicht sichtbar, und Sie müssen `Requery` abrufen, um Sie anzuzeigen. Die Verwendung von `::SQLSetPos` ist ebenfalls effizienter.

##  <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Bearbeiten eines vorhandenen Datensatzes

Zum Bearbeiten eines vorhandenen Datensatzes in einem Recordset müssen Sie einen Bildlauf zum Datensatz ausführen, die Funktion zum [Bearbeiten](../../mfc/reference/crecordset-class.md#edit) von Elementen des Recordsets aufrufen, die Werte der Felddatenmember des neuen Datensatzes festlegen und die Funktion zum [Aktualisieren](../../mfc/reference/crecordset-class.md#update) von Membern aufrufen, um den geänderten Datensatz in die Datenquelle zu schreiben.

Als Vorbedingung zum Aufrufen von `Edit`muss das Recordset aktualisierbar sein und ein Datensatz aufweisen. Mithilfe der Funktionen `CanUpdate` und `IsDeleted` Member können Sie diese Bedingungen ermitteln. Der aktuelle Datensatz darf auch nicht bereits gelöscht worden sein, und es müssen Datensätze im Recordset vorhanden sein (sowohl `IsBOF` als auch `IsEOF` Rückgabe 0).

Wenn Sie `Edit`aufgerufen wird, wird der Datensatz im Bearbeitungs Puffer (der aktuelle Datensatz) gespeichert. Die Werte des gespeicherten Datensatzes werden später verwendet, um zu ermitteln, ob Felder geändert wurden.

Nachdem Sie `Edit`aufgerufen haben, stellt der Bearbeitungs Puffer weiterhin den aktuellen Datensatz dar, ist nun jedoch bereit, Änderungen an den Felddatenmembern zu akzeptieren. Um den Datensatz zu ändern, legen Sie die Werte aller Felddatenmember, die Sie bearbeiten möchten, manuell fest. Anstatt einen tatsächlichen Datenwert für ein Feld anzugeben, können Sie `SetFieldNull` aufzurufen, um den Wert NULL anzugeben. Um die Änderungen zu übertragen, wenden Sie `Update`an.

> [!TIP]
> Um aus `AddNew` oder `Edit` Modus zu gelangen, müssen Sie `Move` mit dem Parameter *AFX_MOVE_REFRESH*aufrufen.

Als Vorbedingung zum Aufrufen von `Update`darf das Recordset nicht leer sein, und der aktuelle Datensatz darf nicht gelöscht werden. `IsBOF`, `IsEOF`und `IsDeleted` sollten alle den Wert 0 (null) zurückgeben.

Wenn Sie `Update` für den bearbeiteten Datensatz abrufen:

- Wenn Ihr ODBC-Treiber die `::SQLSetPos` ODBC-API-Funktion unterstützt, verwendet MFC die-Funktion, um den Datensatz in der Datenquelle zu aktualisieren. Mit `::SQLSetPos`vergleicht der Treiber den Bearbeitungs Puffer mit dem entsprechenden Datensatz auf dem Server und aktualisiert den Datensatz auf dem Server, wenn die beiden unterschiedlich sind. Mit `::SQLSetPos`kann MFC einen Datensatz effizienter aktualisieren, da er keine SQL-Anweisung erstellen und verarbeiten muss.

   \- oder –

- Wenn `::SQLSetPos` nicht verwendet werden kann, führt MFC Folgendes aus:

   1. Wenn keine Änderungen vorgenommen wurden, führt `Update` keine Aktion aus und gibt 0 (null) zurück.

   1. Wenn Änderungen vorhanden sind, erstellt `Update` eine SQL **Update** -Anweisung. Die in der **Update** -Anweisung aufgeführten Spalten basieren auf den Felddatenmembern, die geändert wurden.

   1. `Update` führt einen Commit für die Änderungen aus – führt die **Update** -Anweisung aus – und der Datensatz wird in der Datenquelle geändert, aber nicht ausgeführt, wenn eine Transaktion ausgeführt wird (siehe [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) , um Informationen darüber zu erhalten, wie sich die Transaktion auf das Update auswirkt). ODBC speichert eine Kopie des Datensatzes, der ebenfalls geändert wird.

   1. Im Gegensatz zum Prozess für `AddNew`stellt der `Edit` Prozess den gespeicherten Datensatz nicht wieder her. Der bearbeitete Datensatz bleibt als aktueller Datensatz vorhanden.

   > [!CAUTION]
   > Wenn Sie die Aktualisierung eines Recordsets durch Aufrufen von `Update`vorbereiten, achten Sie darauf, dass das Recordset alle Spalten enthält, die den Primärschlüssel der Tabelle bilden (oder alle Spalten eines eindeutigen Indexes in der Tabelle oder genügend Spalten, um die Zeile eindeutig zu identifizieren). In einigen Fällen kann das Framework zur Identifizierung des Datensatzes, der in der Tabelle aktualisiert werden soll, nur die Spalten verwenden, die im Recordset ausgewählt sind. Ohne alle erforderlichen Spalten werden möglicherweise mehrere Datensätze in der Tabelle aktualisiert. In diesem Fall löst das Framework Ausnahmen aus, wenn Sie `Update`aufruft.

   > [!TIP]
   > Wenn Sie `AddNew` oder `Edit` aufrufen, nachdem Sie eine der beiden Funktionen aufgerufen haben, aber bevor Sie `Update`aufrufen, wird der Bearbeitungs Puffer mit dem gespeicherten Datensatz aktualisiert, und der neue oder bearbeitete Datensatz wird ersetzt. Dieses Verhalten bietet Ihnen die Möglichkeit, eine `AddNew` oder `Edit` abzubrechen und eine neue zu starten: Wenn Sie feststellen, dass der Datensatz in Bearbeitung fehlerhaft ist, können Sie einfach `Edit` oder `AddNew` erneut aufzurufen.

##  <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Löschen eines Datensatzes

Zum Löschen eines Datensatzes aus einem Recordset müssen Sie einen Bildlauf zum Datensatz ausführen und die Funktion zum [Löschen](../../mfc/reference/crecordset-class.md#delete) von Elementen des Recordsets aufrufen. Im Gegensatz zu `AddNew` und `Edit`erfordert `Delete` keinen übereinstimmenden `Update`.

Als Vorbedingung zum Aufrufen von `Delete`muss das Recordset aktualisierbar sein, und es muss sich in einem Datensatz befinden. Mithilfe der Funktionen `CanUpdate`, `IsBOF`, `IsEOF`und `IsDeleted` Member können Sie diese Bedingungen ermitteln.

Wenn Sie `Delete`abrufen:

- Wenn Ihr ODBC-Treiber die `::SQLSetPos` ODBC-API-Funktion unterstützt, verwendet MFC die-Funktion, um den Datensatz in der Datenquelle zu löschen. Die Verwendung von `::SQLSetPos` ist in der Regel effizienter als die Verwendung von SQL.

   \- oder –

- Wenn `::SQLSetPos` nicht verwendet werden kann, führt MFC Folgendes aus:

   1. Der aktuelle Datensatz im Bearbeitungs Puffer wird nicht als in `AddNew` und `Edit`gesichert.

   1. `Delete` erstellt eine SQL **Delete** -Anweisung, mit der der Datensatz entfernt wird.

      Der aktuelle Datensatz im Bearbeitungs Puffer wird nicht als in `AddNew` und `Edit`gespeichert.

   1. `Delete` Commit für den Löschvorgang durch – führt die **Delete** -Anweisung aus. Der Datensatz wird in der Datenquelle als gelöscht markiert und, wenn der Datensatz eine Momentaufnahme ist, in ODBC.

   1. Die Werte des gelöschten Datensatzes befinden sich weiterhin in den Felddatenmembern des Recordsets, aber die Felddatenmember sind als NULL gekennzeichnet, und die `IsDeleted` Member-Funktion des Recordsets gibt einen Wert ungleich 0 (null) zurück.

   > [!NOTE]
   > Nachdem Sie einen Datensatz gelöscht haben, sollten Sie einen Bildlauf zu einem anderen Datensatz durchführen, um den Bearbeitungs Puffer mit den Daten des neuen Datensatzes aufzufüllen. Es ist ein Fehler, `Delete` erneut aufzurufen oder `Edit`aufzurufen.

Informationen zu den in Aktualisierungs Vorgängen verwendeten SQL-Anweisungen finden Sie unter [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Weitere Informationen zu Aktualisierungen (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)
