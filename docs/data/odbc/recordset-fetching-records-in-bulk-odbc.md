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
ms.openlocfilehash: ec4d83481f6335d4c40ffb8f004b617f2ee09c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367032"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Die `CRecordset` Klasse bietet Unterstützung für das Abrufen von Massenzeilen, was bedeutet, dass mehrere Datensätze gleichzeitig während eines einzelnen Abrufs abgerufen werden können, anstatt einen Datensatz gleichzeitig aus der Datenquelle abzurufen. Sie können das Abrufen von Massenzeilen nur in einer abgeleiteten `CRecordset` Klasse implementieren. Der Prozess der Datenübertragung von der Datenquelle zum Recordset-Objekt wird als Massendatensatzfeldaustausch (Bulk RFX) bezeichnet. Beachten Sie, dass Daten über Datensatzfeldaustausch (RFX) übertragen werden, wenn Sie das Abrufen von Massenzeilen in einer `CRecordset`-abgeleiteten Klasse nicht verwenden. Weitere Informationen finden Sie unter [Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

In diesem Thema wird Folgendes erläutert:

- [Wie CRecordset das Abrufen von Massenzeilen unterstützt](#_core_how_crecordset_supports_bulk_row_fetching).

- [Einige besondere Überlegungen bei der Verwendung von Massenzeilenabruf](#_core_special_considerations).

- [So implementieren Sie Massendatensatzfeldaustausch](#_core_how_to_implement_bulk_record_field_exchange).

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Wie CRecordset Das Abrufen von Massenreihen unterstützt

Bevor Sie das Recordset-Objekt öffnen, können `SetRowsetSize` Sie mit der Memberfunktion eine Rowsetgröße definieren. Die Rowsetgröße gibt an, wie viele Datensätze während eines einzelnen Abrufs abgerufen werden sollen. Wenn das Abrufen von Massenzeilen implementiert ist, beträgt die Standardgröße des Rowsets 25. Wenn das Abrufen von Massenzeilen nicht implementiert ist, bleibt die Rowsetgröße auf 1 festgelegt.

Nachdem Sie die Rowsetgröße initialisiert haben, rufen Sie die [Funktion Öffnen](../../mfc/reference/crecordset-class.md#open) der Member auf. Hier müssen Sie `CRecordset::useMultiRowFetch` die Option des *Parameters dwOptions* angeben, um das Abrufen von Massenzeilen zu implementieren. Sie können die `CRecordset::userAllocMultiRowBuffers` Option zusätzlich festlegen. Der Massendatensatzfeldaustauschmechanismus verwendet Arrays, um die mehreren Datenzeilen zu speichern, die während eines Abrufs abgerufen wurden. Diese Speicherpuffer können automatisch vom Framework zugewiesen werden, oder Sie können sie manuell zuweisen. Die Angabe `CRecordset::userAllocMultiRowBuffers` der Option bedeutet, dass Sie die Zuordnung erledigen.

In der folgenden Tabelle sind `CRecordset` die Memberfunktionen aufgeführt, die zum Abrufen von Massenzeilen bereitgestellt werden.

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Virtuelle Funktion, die alle Fehler behandelt, die beim Abrufen auftreten.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementiert massenseitiger Datensatzfeldaustausch. Wird automatisch aufgerufen, um mehrere Datenzeilen aus der Datenquelle an das Recordset-Objekt zu übertragen.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Ruft die aktuelle Einstellung für die Rowsetgröße ab.|
|[GetRowsFetcheded](../../mfc/reference/crecordset-class.md#getrowsfetched)|Gibt an, wie viele Zeilen nach einem bestimmten Abruf tatsächlich abgerufen wurden. In den meisten Fällen ist dies die Rowsetgröße, es sei denn, ein unvollständiges Rowset wurde abgerufen.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Gibt einen Abrufstatus für eine bestimmte Zeile innerhalb eines Rowsets zurück.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Aktualisiert die Daten und den Status einer bestimmten Zeile innerhalb eines Rowsets.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Verschiebt den Cursor in eine bestimmte Zeile innerhalb eines Rowsets.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Virtuelle Funktion, die die Einstellung für die Rowsetgröße auf den angegebenen Wert ändert.|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a>Besondere Überlegungen

Obwohl das Abrufen von Massenzeilen eine Leistungssteigerung ist, funktionieren bestimmte Funktionen unterschiedlich. Bevor Sie sich entscheiden, das Abrufen von Massenzeilen zu implementieren, sollten Sie Folgendes beachten:

- Das Framework ruft `DoBulkFieldExchange` automatisch die Memberfunktion auf, um Daten von der Datenquelle an das Recordset-Objekt zu übertragen. Daten werden jedoch nicht vom Recordset zurück in die Datenquelle übertragen. Das `AddNew`Aufrufen `Edit` `Delete`der `Update` Funktionen , , oder Member führt zu einer fehlgeschlagenen Assertion. Obwohl `CRecordset` derzeit kein Mechanismus zum Aktualisieren von Massendatenzeilen vorgesehen ist, können Sie `SQLSetPos`ihre eigenen Funktionen mithilfe der ODBC-API-Funktion schreiben. Weitere Informationen `SQLSetPos`zu finden Sie in der *ODBC SDK-Programmiererreferenz* in der MSDN-Dokumentation.

- Die `IsDeleted`Memberfunktionen `IsFieldDirty` `IsFieldNull`, `IsFieldNullable` `SetFieldDirty`, `SetFieldNull` , , und können nicht für Recordsets verwendet werden, die das Abrufen von Massenzeilen implementieren. Sie können jedoch `GetRowStatus` anstelle `IsDeleted`von `GetODBCFieldInfo` anrufen und `IsFieldNullable`anstelle von .

- Die `Move` Operationen richten Ihr Recordset nach Rowset neu ein. Angenommen, Sie öffnen ein Recordset mit 100 Datensätzen mit einer anfänglichen Rowsetgröße von 10. `Open`ruft die Zeilen 1 bis 10 ab, wobei der aktuelle Datensatz in Zeile 1 positioniert ist. Ein Aufruf `MoveNext` zum Abrufen des nächsten Rowsets und nicht der nächsten Zeile. Dieses Rowset besteht aus den Zeilen 11 bis 20, wobei der aktuelle Datensatz in Zeile 11 positioniert ist. Beachten `MoveNext` Sie, dass und `Move( 1 )` sind nicht gleichwertig, wenn Massenzeilen abruft implementiert wird. `Move( 1 )`ruft das Rowset ab, das 1 Zeile aus dem aktuellen Datensatz beginnt. In diesem Beispiel `Move( 1 )` ruft `Open` ein Aufruf nach dem Aufrufen das Rowset ab, das aus den Zeilen 2 bis 11 besteht, wobei der aktuelle Datensatz in Zeile 2 positioniert ist. Weitere Informationen finden Sie unter die Funktion [Member verschieben.](../../mfc/reference/crecordset-class.md#move)

- Im Gegensatz zum Datensatzfeldaustausch unterstützen die Assistenten den Massendatensatzfeldaustausch nicht. Dies bedeutet, dass Sie Ihre Felddatenmember manuell `DoBulkFieldExchange` deklarieren und manuell überschreiben müssen, indem Sie Aufrufe an die Bulk-RFX-Funktionen schreiben. Weitere Informationen finden Sie unter [Datensatzfeldaustauschfunktionen](../../mfc/reference/record-field-exchange-functions.md) in der *Klassenbibliotheksreferenz*.

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Implementieren von Massendatensatzfeldaustausch

Massendatensatzfeldaustausch überträgt ein Rowset von Daten aus der Datenquelle an das Recordset-Objekt. Die Bulk-RFX-Funktionen verwenden Arrays, um diese Daten zu speichern, sowie Arrays, um die Länge jedes Datenelements im Rowset zu speichern. In ihrer Klassendefinition müssen Sie die Felddatenmember als Zeiger definieren, um auf die Datenarrays zuzugreifen. Darüber hinaus müssen Sie einen Satz von Zeigern definieren, um auf die Arrays der Längen zugreifen zu können. Parameterdatenmember sollten nicht als Zeiger deklariert werden. Das Deklarieren von Parameterdatenelementen bei Verwendung des Massendatensatzfeldaustauschs entspricht dem Deklarieren, wenn Datensatzfeldaustausch verwendet wird. Der folgende Code zeigt ein einfaches Beispiel:

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

Sie können diese Speicherpuffer entweder manuell zuweisen oder das Framework die Zuordnung vornehmen lassen. Um die Puffer selbst zuzuweisen, `CRecordset::userAllocMultiRowBuffers` müssen Sie die Option `Open` des Parameters *dwOptions* in der Memberfunktion angeben. Stellen Sie sicher, dass die Größe der Arrays mindestens der Rowsetgröße entspricht. Wenn Sie möchten, dass das Framework die Zuweisung ausführt, sollten Sie die Zeiger auf NULL initialisieren. Dies geschieht in der Regel im Konstruktor des Recordset-Objekts:

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

Schließlich müssen Sie die `DoBulkFieldExchange` Memberfunktion überschreiben. Rufen Sie für die Felddatenmember die Bulk-RFX-Funktionen auf. für alle Parameterdatenmember die RFX-Funktionen aufrufen. Wenn Sie das Recordset geöffnet haben, indem `Open`Sie eine SQL-Anweisung oder eine gespeicherte Prozedur an übergeben, muss die Reihenfolge, in der Sie die Bulk-RFX-Aufrufe ausführen, der Reihenfolge der Spalten im Recordset entsprechen. Ebenso muss die Reihenfolge der RFX-Aufrufe für Parameter der Reihenfolge der Parameter in der SQL-Anweisung oder gespeicherten Prozedur entsprechen.

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
> Sie müssen `Close` die Memberfunktion `CRecordset` aufrufen, bevor die abgeleitete Klasse den Gültigkeitsbereich verlässt. Dadurch wird sichergestellt, dass der vom Framework zugewiesene Speicher freigegeben wird. Es ist eine gute Programmierpraxis, immer explizit aufzurufen, `Close`unabhängig davon, ob Sie das Abrufen von Massenzeilen implementiert haben.

Weitere Informationen zum Datensatzfeldaustausch (Record Field Exchange, RFX) finden Sie unter [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX . Weitere Informationen zur Verwendung von Parametern finden Sie unter [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) und [Recordset: Parametrieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
