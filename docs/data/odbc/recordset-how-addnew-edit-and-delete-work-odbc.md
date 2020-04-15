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
ms.openlocfilehash: 63718a6be3a9ce19ddbce923a84def21448c42a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367001"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Recordset: Funktionsweise von AddNew, Edit und Delete (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema `AddNew` `Edit`wird `Delete` erläutert, wie `CRecordset` die , - und Memberfunktionen von Klassen funktionieren. Folgende Themen werden behandelt:

- [Funktionsweise des Hinzufügens von Datensätzen](#_core_adding_a_record)

- [Sichtbarkeit der hinzugefügten Datensätze](#_core_visibility_of_added_records)

- [Funktionsweise der Bearbeitung von Datensätzen](#_core_editing_an_existing_record)

- [Funktionsweise des Löschens von Datensätzen](#_core_deleting_a_record)

> [!NOTE]
> Dieses Thema bezieht sich auf von `CRecordset` abgeleitete Objekte, in denen das gesammelte Abrufen von Zeilen nicht implementiert wurde. Wenn Sie das Abrufen von Massenzeilen verwenden, finden Sie weitere Informationen unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Als Ergänzung können Sie [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md)lesen, das die entsprechende Rolle von RFX in Aktualisierungsvorgängen beschreibt.

## <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Hinzufügen eines Datensatzes

Das Hinzufügen eines neuen Datensatzes zu einem Recordset umfasst das Aufrufen der [AddNew-Memberfunktion](../../mfc/reference/crecordset-class.md#addnew) des Recordsets, das Festlegen der Werte der Felddatenmember des neuen Datensatzes und das Aufrufen der [Memberfunktion Aktualisieren](../../mfc/reference/crecordset-class.md#update) zum Schreiben des Datensatzes in die Datenquelle.

Als Voraussetzung für `AddNew`den Aufruf darf das Recordset nicht schreibgeschützt geöffnet worden sein. Mit `CanUpdate` `CanAppend` den und Memberfunktionen können Sie diese Bedingungen bestimmen.

Wenn Sie `AddNew`anrufen:

- Der Datensatz im Bearbeitungspuffer wird gespeichert, sodass sein Inhalt wiederhergestellt werden kann, wenn der Vorgang abgebrochen wird.

- Die Felddatenmember sind gekennzeichnet, sodass sie später Änderungen erkennen können. Die Felddatenmember werden ebenfalls als sauber (unverändert) markiert und auf Null gesetzt.

Nach dem `AddNew`Aufruf stellt der Bearbeitungspuffer einen neuen, leeren Datensatz dar, der mit Werten ausgefüllt werden kann. Dazu legen Sie die Werte manuell fest, indem Sie ihnen zuweisen. Anstatt einen tatsächlichen Datenwert für ein Feld `SetFieldNull` anzugeben, können Sie aufrufen, um den Wert Null anzugeben.

Um Ihre Änderungen zu `Update`übernehmen, rufen Sie an. Wenn Sie `Update` nach dem neuen Datensatz aufrufen:

- Wenn Ihr ODBC-Treiber die `::SQLSetPos` ODBC-API-Funktion unterstützt, verwendet MFC die Funktion, um den Datensatz in der Datenquelle hinzuzufügen. Mit `::SQLSetPos`kann MFC einen Datensatz effizienter hinzufügen, da er keine SQL-Anweisung erstellen und verarbeiten muss.

- Wenn `::SQLSetPos` mFC nicht verwendet werden kann, führt Folgendes aus:

   1. Wenn keine Änderungen `Update` erkannt werden, wird nichts unternommen und gibt 0 zurück.

   1. Wenn Änderungen vorgenommen `Update` werden, wird eine SQL **INSERT-Anweisung** erstellt. Die Spalten, die von allen schmutzigen Felddatenelementen dargestellt werden, werden in der **INSERT-Anweisung** aufgeführt. Um das Einwerden einer Spalte zu erzwingen, rufen Sie die [SetFieldDirty-Memberfunktion](../../mfc/reference/crecordset-class.md#setfielddirty) auf:

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update`überträgt den neuen Datensatz – die **INSERT-Anweisung** wird ausgeführt, und der Datensatz wird an die Tabelle in der Datenquelle (und dem Recordset, wenn nicht ein Snapshot) festgeschrieben, es sei denn, eine Transaktion wird ausgeführt.

   1. Der gespeicherte Datensatz wird im Bearbeitungspuffer wiederhergestellt. Der Datensatz, der `AddNew` vor dem Aufruf aktuell war, ist wieder aktuell, unabhängig davon, ob die **INSERT-Anweisung** erfolgreich ausgeführt wurde.

   > [!TIP]
   > Um einen neuen Datensatz vollständig zu steuern, gehen Sie wie folgt vor: Legen Sie die Werte aller `SetFieldNull` Felder fest, die Werte haben, und legen Sie dann explizit alle Felder fest, die Null bleiben, indem Sie mit einem Zeiger auf das Feld und den Parameter TRUE (Standard) aufrufen. Wenn Sie sicherstellen möchten, dass ein Feld nicht `SetFieldDirty` in die Datenquelle geschrieben wird, rufen Sie mit einem Zeiger auf das Feld und den Parameter FALSE auf, und ändern Sie den Wert des Felds nicht. Um zu bestimmen, ob ein Feld `IsFieldNullable`Null sein darf, rufen Sie auf.

   > [!TIP]
   > Um zu erkennen, wann Recordset-Datenmember den Wert ändern, verwendet MFC einen PSEUDO_NULL Wert, der für jeden Datentyp geeignet ist, den Sie in einem Recordset speichern können. Wenn Sie explizit ein Feld auf den PSEUDO_NULL Wert festlegen müssen und das `SetFieldNull`Feld bereits als Null markiert ist, müssen Sie auch aufrufen, die Adresse des Feldes im ersten Parameter und FALSE im zweiten Parameter übergeben.

## <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Sichtbarkeit der hinzugefügten Datensätze

Wann ist ein hinzugefügter Datensatz für Ihr Recordset sichtbar? Hinzugefügte Datensätze werden manchmal angezeigt und sind manchmal nicht sichtbar, abhängig von zwei Dingen:

- Wozu Ihr Fahrer in der Lage ist.

- Was der Rahmen nutzen kann.

Wenn Ihr ODBC-Treiber die `::SQLSetPos` ODBC-API-Funktion unterstützt, verwendet MFC die Funktion, um Datensätze hinzuzufügen. Mit `::SQLSetPos`sind hinzugefügte Datensätze für jedes aktualisierbare MFC-Recordset sichtbar. Ohne Unterstützung für die Funktion sind hinzugefügte `Requery` Datensätze nicht sichtbar, und Sie müssen sie aufrufen, um sie anzuzeigen. Die `::SQLSetPos` Verwendung ist auch effizienter.

## <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Bearbeiten eines vorhandenen Datensatzes

Das Bearbeiten eines vorhandenen Datensatzes in einem Recordset umfasst einen Bildlauf zum Datensatz, das Aufrufen der [Memberfunktion Bearbeiten](../../mfc/reference/crecordset-class.md#edit) des Recordsets, das Festlegen der Werte der Felddatenmember des neuen Datensatzes und das Aufrufen der [Memberfunktion Aktualisieren,](../../mfc/reference/crecordset-class.md#update) um den geänderten Datensatz in die Datenquelle zu schreiben.

Als Voraussetzung für `Edit`den Aufruf muss das Recordset aufdemadienbar und auf einem Datensatz sein. Mit `CanUpdate` `IsDeleted` den und Memberfunktionen können Sie diese Bedingungen bestimmen. Der aktuelle Datensatz darf auch nicht bereits gelöscht worden sein, und `IsBOF` `IsEOF` es müssen Datensätze im Recordset vorhanden sein (beide und Return 0).

Beim Aufrufen `Edit`wird der Datensatz im Bearbeitungspuffer (dem aktuellen Datensatz) gespeichert. Die Werte des gespeicherten Datensatzes werden später verwendet, um zu erkennen, ob sich Felder geändert haben.

Nach dem `Edit`Aufruf stellt der Bearbeitungspuffer weiterhin den aktuellen Datensatz dar, kann nun aber Änderungen an den Felddatenmembern akzeptieren. Um den Datensatz zu ändern, legen Sie manuell die Werte aller Felddatenelemente fest, die Sie bearbeiten möchten. Anstatt einen tatsächlichen Datenwert für ein Feld `SetFieldNull` anzugeben, können Sie aufrufen, um den Wert Null anzugeben. Um Ihre Änderungen `Update`zu übertragen, rufen Sie an.

> [!TIP]
> Um aus `AddNew` dem `Edit` Modus `Move` oder dem Modus auszusteigen, rufen Sie mit dem Parameter *AFX_MOVE_REFRESH*an.

Als Voraussetzung für `Update`den Aufruf darf das Recordset nicht leer sein, und der aktuelle Datensatz darf nicht gelöscht worden sein. `IsBOF`, `IsEOF`und `IsDeleted` sollten alle 0 zurückgeben.

Wenn Sie `Update` den bearbeiteten Datensatz aufrufen:

- Wenn Ihr ODBC-Treiber die `::SQLSetPos` ODBC-API-Funktion unterstützt, verwendet MFC die Funktion, um den Datensatz in der Datenquelle zu aktualisieren. Mit `::SQLSetPos`vergleicht der Treiber ihren Bearbeitungspuffer mit dem entsprechenden Datensatz auf dem Server und aktualisiert den Datensatz auf dem Server, wenn die beiden daten. Mit `::SQLSetPos`kann MFC einen Datensatz effizienter aktualisieren, da er keine SQL-Anweisung erstellen und verarbeiten muss.

   \- oder -

- Wenn `::SQLSetPos` mFC nicht verwendet werden kann, führt Folgendes aus:

   1. Wenn keine Änderungen vorgenommen `Update` wurden, tut nichts und gibt 0 zurück.

   1. Wenn Änderungen vorgenommen `Update` werden, wird eine SQL **UPDATE-Anweisung** erstellt. Die in der **UPDATE-Anweisung** aufgeführten Spalten basieren auf den geänderten Felddatenelementen.

   1. `Update`Überträgt die Änderungen – führt die **UPDATE-Anweisung** aus – und der Datensatz wird in der Datenquelle geändert, aber nicht festgeschrieben, wenn eine Transaktion ausgeführt wird (siehe [Transaktion: Ausführen einer Transaktion in einem Recordset (ODBC),](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) um Informationen darüber zu erhalten, wie sich die Transaktion auf die Aktualisierung auswirkt). ODBC speichert eine Kopie des Datensatzes, die sich ebenfalls ändert.

   1. Im Gegensatz `AddNew`zum `Edit` Prozess für stellt der Prozess den gespeicherten Datensatz nicht wieder her. Der bearbeitete Datensatz bleibt als aktueller Datensatz erhalten.

   > [!CAUTION]
   > Wenn Sie sich darauf vorbereiten, `Update`ein Recordset durch Aufrufen zu aktualisieren, achten Sie darauf, dass das Recordset alle Spalten enthält, aus denen der Primärschlüssel der Tabelle besteht (oder alle Spalten eines eindeutigen Indexes in der Tabelle oder genügend Spalten, um die Zeile eindeutig zu identifizieren). In einigen Fällen kann das Framework zur Identifizierung des Datensatzes, der in der Tabelle aktualisiert werden soll, nur die Spalten verwenden, die im Recordset ausgewählt sind. Ohne alle erforderlichen Spalten können mehrere Datensätze in der Tabelle aktualisiert werden. In diesem Fall löst das Framework `Update`Ausnahmen aus, wenn Sie aufrufen.

   > [!TIP]
   > Wenn Sie `AddNew` `Edit` eine der beiden Funktionen zuvor, `Update`aber vor dem Aufruf aufgerufen haben, wird der Bearbeitungspuffer mit dem gespeicherten Datensatz aktualisiert, wodurch der neue oder der ausgeführte Datensatz ersetzt wird. Dieses Verhalten gibt Ihnen eine `AddNew` Möglichkeit, ein oder `Edit` ein neues abzubrechen: Wenn Sie feststellen, dass `Edit` `AddNew` der datensatzbereite Datensatz fehlerhaft ist, rufen Sie einfach an oder erneut.

## <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Löschen eines Datensatzes

Das Löschen eines Datensatzes aus einem Recordset umfasst einen Bildlauf zum Datensatz und das Aufrufen der [Stammfunktion Löschen](../../mfc/reference/crecordset-class.md#delete) des Recordsets. Im `AddNew` `Edit`Gegensatz `Delete` zu und erfordert `Update`kein übereinstimmender Aufruf von .

Als Voraussetzung für `Delete`den Aufruf muss das Recordset updaierbar sein und sich auf einem Datensatz begeben. Mit `CanUpdate` `IsBOF`den `IsEOF`Funktionen `IsDeleted` , , und Member können Sie diese Bedingungen bestimmen.

Wenn Sie `Delete`anrufen:

- Wenn Ihr ODBC-Treiber die `::SQLSetPos` ODBC-API-Funktion unterstützt, verwendet MFC die Funktion, um den Datensatz in der Datenquelle zu löschen. Die `::SQLSetPos` Verwendung ist in der Regel effizienter als die Verwendung von SQL.

   \- oder -

- Wenn `::SQLSetPos` mFC nicht verwendet werden kann, führt Folgendes aus:

   1. Der aktuelle Datensatz im Bearbeitungspuffer wird `AddNew` nicht `Edit`wie in und gesichert.

   1. `Delete`erstellt eine **DELETE** SQL DELETE-Anweisung, die den Datensatz entfernt.

      Der aktuelle Datensatz im Bearbeitungspuffer wird `AddNew` `Edit`nicht wie in und gespeichert.

   1. `Delete`übergibt die Löschung – führt die **DELETE-Anweisung** aus. Der Datensatz wird in der Datenquelle und, wenn es sich um einen Snapshot handelt, in ODBC als gelöscht markiert.

   1. Die Werte des gelöschten Datensatzes befinden sich weiterhin in den Felddatenelementen des Recordsets, `IsDeleted` aber die Felddatenmember sind als Null markiert, und die Memberfunktion des Recordsets gibt einen Wert ungleich Null zurück.

   > [!NOTE]
   > Nach dem Löschen eines Datensatzes sollten Sie zu einem anderen Datensatz scrollen, um den Bearbeitungspuffer mit den Daten des neuen Datensatzes aufzufüllen. Es ist ein `Delete` Fehler, erneut `Edit`aufzurufen oder aufzurufen.

Informationen zu den SQL-Anweisungen, die in Aktualisierungsvorgängen verwendet werden, finden Sie unter [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Weitere Informationen zu Aktualisierungen (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)
