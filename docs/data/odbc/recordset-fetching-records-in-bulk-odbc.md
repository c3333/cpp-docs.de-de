---
title: 'Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
ms.openlocfilehash: cd9597da7ab4c405f90a145182d63945cef48c53
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079825"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Class `CRecordset` bietet Unterstützung für das Abrufen von Massen Zeilen, d. h., mehrere Datensätze können während eines einzelnen Abruf Vorgangs gleichzeitig abgerufen werden, anstatt jeweils einen Datensatz aus der Datenquelle abzurufen. Sie können das Massen Abrufen von Zeilen nur in einer abgeleiteten `CRecordset` Klasse implementieren. Der Vorgang zum Übertragen von Daten aus der Datenquelle in das Recordset-Objekt wird als Massendaten Satz Feld Austausch (Bulk RFX) bezeichnet. Beachten Sie Folgendes: Wenn Sie das Massen Abrufen von Zeilen in einer `CRecordset`-abgeleiteten Klasse nicht verwenden, werden Daten über den Daten Satz Feld Austausch (RFX) übertragen. Weitere Informationen finden Sie unter [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

In diesem Thema wird Folgendes erläutert:

- [Wie CRecordset das Abrufen von Massen Zeilen unterstützt](#_core_how_crecordset_supports_bulk_row_fetching).

- [Einige besondere Überlegungen beim Abrufen von Massen Zeilen](#_core_special_considerations).

- [So implementieren Sie den Massendaten Satz Feld Austausch](#_core_how_to_implement_bulk_record_field_exchange).

##  <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Unterstützt das Abrufen von Massen Zeilen durch CRecordset

Vor dem Öffnen des Recordset-Objekts können Sie eine Rowsetgröße mit der `SetRowsetSize` Member-Funktion definieren. Die Rowsetgröße gibt an, wie viele Datensätze während eines einzelnen Abruf Vorgangs abgerufen werden sollen. Wenn das Massen Abrufen von Zeilen implementiert ist, beträgt die standardrowsetgröße 25. Wenn das Abrufen von Massen Zeilen nicht implementiert ist, bleibt die Rowsetgröße bei 1 festgelegt.

Nachdem Sie die Rowsetgröße initialisiert haben, können Sie die Funktion [Open](../../mfc/reference/crecordset-class.md#open) Member aufzurufen. Hier müssen Sie die `CRecordset::useMultiRowFetch`-Option des *dwOptions* -Parameters angeben, um das Massen Abrufen von Zeilen zu implementieren. Außerdem können Sie die Option `CRecordset::userAllocMultiRowBuffers` festlegen. Der Massendaten Satz Feld Austauschmechanismus verwendet Arrays, um die verschiedenen Daten Zeilen zu speichern, die während eines Abruf Vorgangs abgerufen werden. Diese Speicherpuffer können automatisch vom Framework zugeordnet werden, oder Sie können Sie manuell zuordnen. Die Angabe der Option `CRecordset::userAllocMultiRowBuffers` bedeutet, dass Sie die Zuordnung durchführen.

In der folgenden Tabelle werden die von `CRecordset` bereitgestellten Element Funktionen aufgelistet, um das Abrufen von Massen Zeilen zu unterstützen.

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[Checkrow* Terror](../../mfc/reference/crecordset-class.md#checkrowseterror)|Eine virtuelle Funktion, die alle Fehler behandelt, die während des Abrufens auftreten.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementiert den Massendaten Satz Feld Austausch. Wird automatisch aufgerufen, um mehrere Daten Zeilen von der Datenquelle an das Recordset-Objekt zu übertragen.|
|[Getrowsetsize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Ruft die aktuelle Einstellung für die Rowsetgröße ab.|
|[Getrowsfetch](../../mfc/reference/crecordset-class.md#getrowsfetched)|Gibt an, wie viele Zeilen nach einem bestimmten Abruf Vorgang tatsächlich abgerufen wurden. In den meisten Fällen ist dies die Rowsetgröße, es sei denn, es wurde ein unvollständiges Rowset abgerufen.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Gibt einen Abruf Status für eine bestimmte Zeile in einem Rowset zurück.|
|[Aktuerfrischendes Rowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Aktualisiert die Daten und den Status einer bestimmten Zeile innerhalb eines Rowsets.|
|[Setrowsetcurrsorposition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Verschiebt den Cursor in eine bestimmte Zeile innerhalb eines Rowsets.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Eine virtuelle Funktion, die die Einstellung für die Rowsetgröße auf den angegebenen Wert ändert.|

##  <a name="special-considerations"></a><a name="_core_special_considerations"></a>Besondere Überlegungen

Obwohl das Abrufen von Massen Zeilen eine Leistungssteigerung ist, funktionieren bestimmte Features anders. Beachten Sie Folgendes, bevor Sie das Abrufen von Massen Zeilen beschließen:

- Das Framework ruft automatisch die `DoBulkFieldExchange` Member-Funktion auf, um Daten aus der Datenquelle in das Recordset-Objekt zu übertragen. Die Daten werden jedoch nicht aus dem Recordset zurück in die Datenquelle übertragen. Das Aufrufen der Funktionen `AddNew`, `Edit`, `Delete`oder `Update` Members führt zu einer fehlgeschlagenen-Assertion. Obwohl `CRecordset` derzeit keinen Mechanismus zum Aktualisieren von Massendaten Zeilen bereitstellt, können Sie eigene Funktionen mithilfe der ODBC-API-Funktion `SQLSetPos`schreiben. Weitere Informationen zu `SQLSetPos`finden Sie in der MSDN-Dokumentation in der *ODBC SDK-Programmier Referenz* .

- Die Element Funktionen `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`und `SetFieldNull` können nicht für Recordsets verwendet werden, die das Abrufen von Massen Zeilen implementieren. Sie können `GetRowStatus` jedoch anstelle von `IsDeleted`und `GetODBCFieldInfo` anstelle von `IsFieldNullable`aufzurufen.

- Der `Move`-Vorgang positioniert das Recordset nach Rowset. Angenommen, Sie öffnen ein Recordset, das über 100 Datensätze mit einer anfänglichen Rowsetgröße von 10 verfügt. `Open` Ruft die Zeilen 1 bis 10 ab, wobei der aktuelle Datensatz in Zeile 1 positioniert ist. Ein-`MoveNext` Ruft das nächste Rowset und nicht die nächste Zeile ab. Dieses Rowset besteht aus den Zeilen 11 bis 20, wobei der aktuelle Datensatz in Zeile 11 positioniert ist. Beachten Sie, dass `MoveNext` und `Move( 1 )` nicht äquivalent sind, wenn das Abrufen von Massen Zeilen implementiert wird. `Move( 1 )` Ruft das Rowset ab, das eine Zeile aus dem aktuellen Datensatz startet. In diesem Beispiel ruft der Aufruf von `Move( 1 )` nach dem Aufruf von `Open` das Rowset ab, das aus den Zeilen 2 bis 11 besteht, wobei der aktuelle Datensatz in Zeile 2 positioniert ist. Weitere Informationen finden Sie unter der [Move](../../mfc/reference/crecordset-class.md#move) Member-Funktion.

- Im Gegensatz zum Daten Satz Feld Austausch unterstützen die Assistenten keinen Massendaten Satz Feld Austausch. Dies bedeutet, dass Sie Ihre Felddatenmember manuell deklarieren und `DoBulkFieldExchange` manuell überschreiben müssen, indem Sie Aufrufe der Massen-RFX-Funktionen schreiben. Weitere Informationen finden Sie unter [Daten Satz Feld Austausch-Funktionen](../../mfc/reference/record-field-exchange-functions.md) in der *Klassen Bibliotheks Referenz*.

##  <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>So implementieren Sie einen Massendaten Satz Feld Austausch

Der Massendaten Satz Feld Austausch überträgt ein Rowset von Daten aus der Datenquelle in das Recordset-Objekt. Die Massen-RFX-Funktionen verwenden Arrays zum Speichern dieser Daten sowie Arrays, um die Länge der einzelnen Datenelemente im Rowset zu speichern. In ihrer Klassendefinition müssen Sie die Felddatenmember als Zeiger definieren, um auf die Daten Arrays zuzugreifen. Außerdem müssen Sie einen Satz von Zeigern definieren, um auf die Längen Arrays zuzugreifen. Alle Parameter Datenmember sollten nicht als Zeiger deklariert werden. das Deklarieren von Parameterdatenmembern bei Verwendung des Massendaten Satz-Feld Austauschs entspricht der Deklaration bei der Verwendung von Daten Satz Feld Austausch Der folgende Code zeigt ein einfaches Beispiel:

```cpp
class MultiRowSet : public CRecordset
{
public:
   // Field/Param Data
      // field data members
      long* m_rgID;
      LPSTR m_rgName;

      // pointers for the lengths
      // of the field data
      long* m_rgIDLengths;
      long* m_rgNameLengths;

      // input parameter data member
      CString m_strNameParam;

   .
   .
   .
}
```

Sie können diese Speicherpuffer entweder manuell zuordnen, oder das Framework muss die Zuordnung durchführen. Um die Puffer selbst zuzuordnen, müssen Sie die Option `CRecordset::userAllocMultiRowBuffers` des Parameters *dwOptions* in der `Open` Member-Funktion angeben. Stellen Sie sicher, dass Sie die Größe der Arrays mindestens gleich der Rowsetgröße festlegen. Wenn Sie möchten, dass das Framework die Zuordnung durchführen soll, sollten Sie die Zeiger auf Null initialisieren. Dies erfolgt in der Regel im Konstruktor des Recordset-Objekts:

```cpp
MultiRowSet::MultiRowSet( CDatabase* pDB )
   : CRecordset( pDB )
{
   m_rgID = NULL;
   m_rgName = NULL;
   m_rgIDLengths = NULL;
   m_rgNameLengths = NULL;
   m_strNameParam = "";

   m_nFields = 2;
   m_nParams = 1;

   .
   .
   .
}
```

Zum Schluss müssen Sie die `DoBulkFieldExchange` Member-Funktion überschreiben. Bei den Felddatenmembern werden die Massen-RFX-Funktionen aufgerufen. bei allen Parameterdatenmembern werden die RFX-Funktionen aufgerufen. Wenn Sie das Recordset geöffnet haben, indem Sie eine SQL-Anweisung oder eine gespeicherte Prozedur an `Open`übergeben, muss die Reihenfolge, in der Sie die Massen-RFX-Aufrufe vornehmen, der Reihenfolge der Spalten im Recordset entsprechen. Ebenso muss die Reihenfolge der RFX-Aufrufe für Parameter der Reihenfolge der Parameter in der SQL-Anweisung oder der gespeicherten Prozedur entsprechen.

```cpp
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )
{
   // call the Bulk RFX functions
   // for field data members
   pFX->SetFieldType( CFieldExchange::outputColumn );
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),
                  &m_rgID, &m_rgIDLengths );
   RFX_Text_Bulk( pFX, _T( "[colName]" ),
                  &m_rgName, &m_rgNameLengths, 30 );

   // call the RFX functions for
   // for parameter data members
   pFX->SetFieldType( CFieldExchange::inputParam );
   RFX_Text( pFX, "NameParam", m_strNameParam );
}
```

> [!NOTE]
>  Bevor die abgeleitete `CRecordset` Klasse den Gültigkeitsbereich verlässt, müssen Sie die `Close` Member-Funktion abrufen. Dadurch wird sichergestellt, dass der vom Framework zugewiesene Arbeitsspeicher freigegeben wird. Es empfiehlt sich, `Close`stets explizit aufzurufen, unabhängig davon, ob Sie das Massen Abrufen von Zeilen implementiert haben.

Weitere Informationen zum Daten Satz Feld Austausch (RFX) finden Sie unter [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Weitere Informationen zum Verwenden von Parametern finden Sie unter [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) und [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset:: m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
