---
title: Funktionen für den Datensatzfeldaustausch
ms.date: 09/17/2019
f1_keywords:
- AFXDB/RFX_Binary
- AFXDB/RFX_Bool
- AFXDB/RFX_Byte
- AFXDB/RFX_Date
- AFXDB/RFX_Double
- AFXDB/RFX_Int
- AFXDB/RFX_Long
- AFXDB/RFX_LongBinary
- AFXDB/RFX_Single
- AFXDB/RFX_Text
- AFXDB/RFX_Binary_Bulk
- AFXDB/RFX_Bool_Bulk
- AFXDB/RFX_Byte_Bulk
- AFXDB/RFX_Date_Bulk
- AFXDB/RFX_Double_Bulk
- AFXDB/RFX_Int_Bulk
- AFXDB/RFX_Long_Bulk
- AFXDB/RFX_Single_Bulk
- AFXDB/RFX_Text_Bulk
- AFXDB/DFX_Binary
- AFXDB/DFX_Bool
- AFXDB/DFX_Byte
- AFXDB/DFX_Currency
- AFXDB/DFX_DateTime
- AFXDB/DFX_Double
- AFXDB/DFX_Long
- AFXDB/DFX_LongBinary
- AFXDB/DFX_Short
- AFXDB/DFX_Single
- AFXDB/DFX_Text
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions [MFC]
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions [MFC]
- DFX functions [MFC]
- bulk RFX functions [MFC]
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions [MFC]
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
ms.openlocfilehash: bfd3ba64a33547b8a27e0f3bc896f39c94486464
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372978"
---
# <a name="record-field-exchange-functions"></a>Funktionen für den Datensatzfeldaustausch

Dieses Thema enthält die Datensatzfeldaustausch (RFX, Bulk-RFX und DFX)-Funktionen, mit denen die Übertragung von Daten zwischen einem Recordset-Objekt und den zugehörigen Datenquellen automatisiert und andere Datenvorgänge ausgeführt werden.

Wenn Sie die ODBC-basierten Klassen verwenden und einen Massenzeilenabruf implementiert haben, müssen Sie die `DoBulkFieldExchange` -Memberfunktion des `CRecordset` manuell überschreiben, indem Sie die Bulk-RFX-Funktionen für jedes Datenelement aufrufen, das einer Datenquellspalte entspricht.

Wenn Sie das Abrufen von Massenzeilen in den ODBC-basierten Klassen nicht implementiert haben oder wenn Sie die `DoFieldExchange` DAO-basierten Klassen (veraltet) verwenden, überschreibt ClassWizard die Memberfunktion von `CRecordset` oder `CDaoRecordset` durch Aufrufen der RFX-Funktionen (für ODBC-Klassen) oder der DFX-Funktionen (für DAO-Klassen) für jeden Felddatenmember in Ihrem Recordset.

Die Datensatzfeldaustausch-Funktionen übertragen jedes Mal Daten, wenn das Framework `DoFieldExchange` oder `DoBulkFieldExchange`aufruft. Jede Funktion überträgt einen bestimmten Datentyp.

Weitere Informationen über die Verwendung dieser Funktionen finden Sie in den Artikeln [Datensatzfeldaustausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Für Datenspalten, die Sie dynamisch binden, können Sie auch die RFX- oder DFX-Funktionen selbst aufrufen, wie in den Artikeln [Recordset: Dynamisches Binden von Spalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)beschrieben. Darüber hinaus können Sie Ihre eigenen benutzerdefinierten RFX- oder DFX-Routinen schreiben, wie im technischen Hinweis [43](../../mfc/tn043-rfx-routines.md) (für ODBC) und im technischen Hinweis [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (für DAO) erläutert.

Ein Beispiel für RFX- und Bulk-RFX-Funktionen, wie sie in der `DoFieldExchange` und `DoBulkFieldExchange` Funktionen angezeigt werden, finden Sie unter [RFX_Text](#rfx_text) und [RFX_Text_Bulk]#rfx_text_bulk). DFX-Funktionen sind den RFX-Funktionen sehr ähnlich.

### <a name="rfx-functions-odbc"></a>RFX-Funktionen (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|Überträgt Byte-Arrays vom Typ [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Überträgt boolesche Daten.|
|[RFX_Byte](#rfx_byte)|Überträgt ein einzelnes Byte an Daten.|
|[RFX_Date](#rfx_date)|Überträgt Zeit- und Datumsdaten mit [CTime](../../atl-mfc-shared/reference/ctime-class.md) oder TIMESTAMP_STRUCT.|
|[RFX_Double](#rfx_double)|Überträgt Gleitkommazahl mit doppelter Genauigkeit.|
|[RFX_Int](#rfx_int)|Überträgt Ganzzahldaten.|
|[RFX_Long](#rfx_long)|Überträgt lange Ganzzahldaten.|
|[RFX_LongBinary](#rfx_longbinary)|Überträgt BLOB-Daten (Binary Large Object) mit einem Objekt der [CLongBinary](clongbinary-class.md) Klasse.|
|[RFX_Single](#rfx_single)|Überträgt Gleitkommadaten.|
|[RFX_Text](#rfx_text)|Überträgt Zeichenfolgendaten.|

### <a name="bulk-rfx-functions-odbc"></a>Bulk-RFX-Funktionen (ODBC)

|||
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|Überträgt Arrays von Bytedaten.|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|Überträgt Arrays von booleschen Daten.|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|Überträgt Arrays von Einzelbytes.|
|[RFX_Date_Bulk](#rfx_date_bulk)|Überträgt Arrays von Daten des Typs TIMESTAMP_STRUCT.|
|[RFX_Double_Bulk](#rfx_double_bulk)|Überträgt Arrays von Gleitkommadaten mit doppelter Genauigkeit.|
|[RFX_Int_Bulk](#rfx_int_bulk)|Überträgt Arrays von Ganzzahldaten.|
|[RFX_Long_Bulk](#rfx_long_bulk)|Überträgt Arrays von langen Ganzzahldaten.|
|[RFX_Single_Bulk](#rfx_single_bulk)|Überträgt Arrays von Gleitkommadaten.|
|[RFX_Text_Bulk](#rfx_text_bulk)|Überträgt Arrays von Daten des Typs LPSTR.|

### <a name="dfx-functions-dao"></a>DFX-Funktionen (DAO)

|||
|-|-|
|[DFX_Binary](#dfx_binary)|Überträgt Byte-Arrays vom Typ [CByteArray](cbytearray-class.md).|
|[DFX_Bool](#dfx_bool)|Überträgt boolesche Daten.|
|[DFX_Byte](#dfx_byte)|Überträgt ein einzelnes Byte an Daten.|
|[DFX_Currency](#dfx_currency)|Überträgt Währungsdaten vom Typ [COleCurrency](colecurrency-class.md).|
|[DFX_DateTime](#dfx_datetime)|Überträgt Datums- und Uhrzeitdaten vom Typ [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|
|[DFX_Double](#dfx_double)|Überträgt Gleitkommazahl mit doppelter Genauigkeit.|
|[DFX_Long](#dfx_long)|Überträgt lange Ganzzahldaten.|
|[DFX_LongBinary](#dfx_longbinary)|Überträgt BLOB-Daten (Binary Large Object) mit einem Objekt der `CLongBinary` -Klasse. Bei DAO wird empfohlen, dass Sie stattdessen [DFX_Binary](#dfx_binary) verwenden.|
|[DFX_Short](#dfx_short)|Überträgt kurze Ganzzahldaten.|
|[DFX_Single](#dfx_single)|Überträgt Gleitkommadaten.|
|[DFX_Text](#dfx_text)|Überträgt Zeichenfolgendaten.|

=============================================

## <a name="rfx_binary"></a><a name="rfx_binary"></a>RFX_Binary

Überträgt Arrays von Bytes zwischen `CRecordset` den Felddatenmembern eines Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_BINARY, SQL_VARBINARY oder SQL_LONGVARBINARY.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ [CByteArray](cbytearray-class.md)vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*nMaxLength*<br/>
Die maximal zulässige Länge der übergebenen Zeichenfolge oder des Arrays. Der Standardwert von *nMaxLength* ist 255. Die gesetzlichen Werte sind 1 bis INT_MAX. Das Framework reserviert diesen Speicherplatz für die Daten. Übergeben Sie einen Wert, der groß genug ist, um das größte erwartete Datenelement aufzunehmen, um eine optimale Leistung zu erzielen.

### <a name="remarks"></a>Bemerkungen

Daten in der Datenquelle dieser Typen werden dem `CByteArray` und dem Typ im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_bool"></a><a name="rfx_bool"></a>RFX_Bool

Überträgt boolesche Daten zwischen `CRecordset` den Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_BIT.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ BOOL vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_byte"></a><a name="rfx_byte"></a>RFX_Byte

Überträgt einzelne Bytes zwischen den `CRecordset` Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_TINYINT.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ BYTE vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_date"></a><a name="rfx_date"></a>RFX_Date

Überträgt `CTime` oder TIMESTAMP_STRUCT Daten zwischen `CRecordset` den Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_DATE, SQL_TIME oder SQL_TIMESTAMP.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   CTime& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   TIMESTAMP_STRUCT& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   COleDateTime& value);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert; den zu übertragenden Wert. Die verschiedenen Versionen der Funktion verwenden unterschiedliche Datentypen für den Wert:

Die erste Version der Funktion nimmt einen Verweis auf ein [CTime-Objekt.](../../atl-mfc-shared/reference/ctime-class.md) Bei einer Übertragung von Recordset in die Datenquelle wird dieser Wert dem angegebenen Datenmember entnommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

Die zweite Version der Funktion nimmt `TIMESTAMP_STRUCT` einen Verweis auf eine Struktur. Sie müssen diese Struktur vor dem Aufruf selbst einrichten. Für diese Version ist weder die Unterstützung für den Dialogdatenaustausch (DDX) noch die Unterstützung des Code-Assistenten verfügbar. Die dritte Version der Funktion funktioniert ähnlich wie die erste Version, außer dass sie einen Verweis auf ein [COleDateTime-Objekt](../../atl-mfc-shared/reference/coledatetime-class.md) nimmt.

### <a name="remarks"></a>Bemerkungen

Die `CTime` Version der Funktion verursacht den Overhead einer Zwischenverarbeitung und hat einen etwas begrenzten Bereich. Wenn Sie einen dieser Faktoren als zu einschränkend empfinden, verwenden Sie die zweite Version der Funktion. Beachten Sie jedoch den Mangel an Code-Assistenten und DDX-Unterstützung und die Anforderung, dass Sie die Struktur selbst einrichten.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_double"></a><a name="rfx_double"></a>RFX_Double

Überträgt **doppelte Floatdaten** zwischen den `CRecordset` Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_DOUBLE.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ **double**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_int"></a><a name="rfx_int"></a>RFX_Int

Überträgt ganzzahlige Daten zwischen den `CRecordset` Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_SMALLINT.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert des Typs **int**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_long"></a><a name="rfx_long"></a>RFX_Long

Überträgt lange ganzzahlige Daten zwischen `CRecordset` den Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_INTEGER.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ **long**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a>RFX_LongBinary

Überträgt bLOB-Daten (Binary Large Object) mithilfe der Klasse `CRecordset` [CLongBinary](clongbinary-class.md) zwischen den Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_LONGVARBINARY oder SQL_LONGVARCHAR.

### <a name="syntax"></a>Syntax

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die `CLongBinary`Datenquelle wird der Wert des Typs vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_single"></a><a name="rfx_single"></a>RFX_Single

Überträgt Gleitkommadaten zwischen den `CRecordset` Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_REAL.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ **float**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_text"></a><a name="rfx_text"></a>RFX_Text

Überträgt `CString` Daten zwischen den `CRecordset` Felddatenmembern eines Objekts und Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL oder SQL_NUMERIC.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein `CFieldExchange`Objekt der Klasse . Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die `CString`Datenquelle wird der Wert des Typs vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*nMaxLength*<br/>
Die maximal zulässige Länge der übergebenen Zeichenfolge oder des Arrays. Der Standardwert von *nMaxLength* ist 255. Die gesetzlichen Werte sind 1 bis INT_MAX). Das Framework reserviert diesen Speicherplatz für die Daten. Übergeben Sie einen Wert, der groß genug ist, um das größte erwartete Datenelement aufzunehmen, um eine optimale Leistung zu erzielen.

*nColumnType*<br/>
Wird hauptsächlich für Parameter verwendet. Eine ganze Zahl, die den Datentyp des Parameters angibt. Der Typ ist ein ODBC-Datentyp des Formulars **SQL_XXX**.

*Nscale*<br/>
Gibt den Maßstab für Werte des ODBC-Typs SQL_DECIMAL oder SQL_NUMERIC an. *nScale* ist nur nützlich, wenn Parameterwerte gesetzt werden. Weitere Informationen finden Sie im Thema "Präzision, Skalierung, Länge und Anzeigegröße" in Anhang D der *ODBC SDK-Programmiererreferenz*.

### <a name="remarks"></a>Bemerkungen

Daten in der Datenquelle all dieser Typen werden `CString` dem Recordset zugeordnet und aus dem Recordset.

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt `RFX_Text`mehrere Aufrufe von . Beachten Sie auch `CFieldExchange::SetFieldType`die beiden Aufrufe von . Für Parameter müssen Sie `SetFieldType` den Aufruf und seinen RFX-Aufruf schreiben. Der Ausgabespaltenaufruf und die zugehörigen RFX-Aufrufe werden normalerweise von einem Code-Assistenten geschrieben.

```cpp
void CCustomer::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   // Macros such as RFX_Text() and RFX_Int() are dependent on the
   // type of the member variable, not the type of the field in the database.
   // ODBC will try to automatically convert the column value to the requested type
   RFX_Long(pFX, _T("[CustomerID]"), m_CustomerID);
   RFX_Text(pFX, _T("[ContactFirstName]"), m_ContactFirstName);
   RFX_Text(pFX, _T("[PostalCode]"), m_PostalCode);
   RFX_Text(pFX, _T("[L_Name]"), m_L_Name);
   RFX_Long(pFX, _T("[BillingID]"), m_BillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a>RFX_Binary_Bulk

Überträgt mehrere Zeilen von Bytedaten aus einer Spalte einer ODBC-Datenquelle an ein entsprechendes Array in einem `CRecordset`-derived-Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](cfieldexchange-class.md) Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*prgByteVals*<br/>
Ein Zeiger auf ein Array von BYTE-Werten. Dieses Array speichert die Daten, die von der Datenquelle in das Recordset übertragen werden sollen.

*prgLengths*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Länge in Bytes jedes Werts im Array, auf das von *prgByteVals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen Nullwert enthält. Weitere Informationen finden Sie in `SQLBindCol` der ODBC-API-Funktion in der *ODBC SDK-Programmiererreferenz*.

*nMaxLength*<br/>
Die maximal zulässige Länge der im Array gespeicherten Werte, auf die von *prgByteVals*verwiesen wird. Um sicherzustellen, dass Daten nicht abgeschnitten werden, übergeben Sie einen Wert, der groß genug ist, um das größte erwartete Datenelement aufzunehmen.

### <a name="remarks"></a>Bemerkungen

Die Datenquellenspalte kann über einen ODBC-Typ von SQL_BINARY, SQL_VARBINARY oder SQL_LONGVARBINARY verfügen. Das Recordset muss einen Felddatenmember des Typzeigers auf BYTE definieren.

Wenn Sie *prgByteVals* und *prgLengths* auf NULL initialisieren, werden die Arrays, auf die sie verweisen, automatisch zugewiesen, wobei die Größen der Rowsetgröße entsprechen.

> [!NOTE]
> Der Massendatensatzfeldaustausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um Ihr Recordset aktualisierbar zu machen, müssen `SQLSetPos`Sie die ODBC-API-Funktion verwenden.

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a>RFX_Bool_Bulk

Überträgt mehrere Zeilen boolescher Daten aus einer Spalte einer ODBC-Datenquelle an ein entsprechendes Array in einem `CRecordset`-derived-Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](cfieldexchange-class.md) Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*prgBoolVals*<br/>
Ein Zeiger auf ein Array von BOOL-Werten. Dieses Array speichert die Daten, die von der Datenquelle in das Recordset übertragen werden sollen.

*prgLengths*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Länge in Bytes jedes Werts im Array, auf das von *prgBoolVals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen Nullwert enthält. Weitere Informationen finden Sie in `SQLBindCol` der ODBC-API-Funktion in der *ODBC SDK-Programmiererreferenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellenspalte muss über einen ODBC-Typ SQL_BIT verfügen. Das Recordset muss einen Felddatenmember des Typzeigers auf BOOL definieren.

Wenn Sie *prgBoolVals* und *prgLengths* auf NULL initialisieren, werden die Arrays, auf die sie verweisen, automatisch zugewiesen, wobei die Größen der Rowsetgröße entsprechen.

> [!NOTE]
> Der Massendatensatzfeldaustausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um Ihr Recordset aktualisierbar zu machen, `SQLSetPos`müssen Sie die ODBC-API-Funktion verwenden.

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a>RFX_Byte_Bulk

Überträgt mehrere Zeilen einzelner Bytes aus einer Spalte einer ODBC-Datenquelle auf ein entsprechendes Array in einem `CRecordset`-derived-Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](cfieldexchange-class.md) Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*prgByteVals*<br/>
Ein Zeiger auf ein Array von BYTE-Werten. Dieses Array speichert die Daten, die von der Datenquelle in das Recordset übertragen werden sollen.

*prgLengths*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Länge in Bytes jedes Werts im Array, auf das von *prgByteVals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen Nullwert enthält. Weitere Informationen finden Sie in `SQLBindCol` der ODBC-API-Funktion in der *ODBC SDK-Programmiererreferenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellenspalte muss über einen ODBC-Typ SQL_TINYINT verfügen. Das Recordset muss einen Felddatenmember des Typzeigers auf BYTE definieren.

Wenn Sie *prgByteVals* und *prgLengths* auf NULL initialisieren, werden die Arrays, auf die sie verweisen, automatisch zugewiesen, wobei die Größen der Rowsetgröße entsprechen.

> [!NOTE]
> Der Massendatensatzfeldaustausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um Ihr Recordset aktualisierbar zu machen, `SQLSetPos`müssen Sie die ODBC-API-Funktion verwenden.

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a>RFX_Date_Bulk

Überträgt mehrere Zeilen TIMESTAMP_STRUCT Daten aus einer Spalte einer ODBC-Datenquelle auf ein entsprechendes Array in einem `CRecordset`-derived-Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](cfieldexchange-class.md) Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*prgTSVals*<br/>
Ein Zeiger auf ein Array von TIMESTAMP_STRUCT Werten. Dieses Array speichert die Daten, die von der Datenquelle in das Recordset übertragen werden sollen. Weitere Informationen zum TIMESTAMP_STRUCT Datentyps finden Sie im Thema "C-Datentypen" in Anhang D der *ODBC SDK-Programmiererreferenz*.

*prgLengths*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Länge in Bytes jedes Werts im Array, auf das von *prgTSVals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen Nullwert enthält. Weitere Informationen finden Sie in `SQLBindCol` der ODBC-API-Funktion in der *ODBC SDK-Programmiererreferenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellenspalte kann über einen ODBC-Typ von SQL_DATE, SQL_TIME oder SQL_TIMESTAMP verfügen. Das Recordset muss einen Felddatenmember des Typzeigers auf TIMESTAMP_STRUCT definieren.

Wenn Sie *prgTSVals* und *prgLengths* auf NULL initialisieren, werden die Arrays, auf die sie verweisen, automatisch zugewiesen, wobei die Größen der Rowsetgröße entsprechen.

> [!NOTE]
> Der Massendatensatzfeldaustausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um Ihr Recordset aktualisierbar zu machen, `SQLSetPos`müssen Sie die ODBC-API-Funktion verwenden.

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a>RFX_Double_Bulk

Überträgt mehrere Zeilen mit Gleitkommadaten mit doppelter Genauigkeit aus einer Spalte `CRecordset`einer ODBC-Datenquelle an ein entsprechendes Array in einem -derived-Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](cfieldexchange-class.md) Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*prgDblVals*<br/>
Ein Zeiger auf ein Array mit **doppelten** Werten. Dieses Array speichert die Daten, die von der Datenquelle in das Recordset übertragen werden sollen.

*prgLengths*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Länge in Bytes jedes Werts im Array, auf das von *prgDblVals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen Nullwert enthält. Weitere Informationen finden Sie in `SQLBindCol` der ODBC-API-Funktion in der *ODBC SDK-Programmiererreferenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellenspalte muss über einen ODBC-Typ SQL_DOUBLE verfügen. Das Recordset muss einen Felddatenmember des Typzeigers zum **Verdoppeln**definieren.

Wenn Sie *prgDblVals* und *prgLengths* auf NULL initialisieren, werden die Arrays, auf die sie verweisen, automatisch zugewiesen, wobei die Größen der Rowsetgröße entsprechen.

> [!NOTE]
> Der Massendatensatzfeldaustausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um Ihr Recordset aktualisierbar zu machen, `SQLSetPos`müssen Sie die ODBC-API-Funktion verwenden.

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a>RFX_Int_Bulk

Überträgt ganzzahlige Daten zwischen den `CRecordset` Felddatenmembern eines Objekts und den Spalten eines Datensatzes auf der Datenquelle des ODBC-Typs SQL_SMALLINT.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen zu den `CFieldExchange` Vorgängen, die ein Objekt angeben kann, finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert des Typs **int**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a>RFX_Long_Bulk

Überträgt mehrere Zeilen mit langen ganzzahligen Daten aus einer Spalte einer `CRecordset`ODBC-Datenquelle an ein entsprechendes Array in einem -derived-Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](cfieldexchange-class.md) Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*prgLongVals*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Daten, die von der Datenquelle in das Recordset übertragen werden sollen.

*prgLengths*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Länge in Bytes jedes Werts im Array, auf das von *prgLongVals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen Nullwert enthält. Weitere Informationen finden Sie in `SQLBindCol` der ODBC-API-Funktion in der *ODBC SDK-Programmiererreferenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellenspalte muss über einen ODBC-Typ SQL_INTEGER verfügen. Das Recordset muss einen Felddatenmember des Typzeigers auf **long**definieren.

Wenn Sie *prgLongVals* und *prgLengths* auf NULL initialisieren, werden die Arrays, auf die sie verweisen, automatisch zugewiesen, wobei die Größen der Rowsetgröße entsprechen.

> [!NOTE]
> Der Massendatensatzfeldaustausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um Ihr Recordset aktualisierbar zu machen, `SQLSetPos`müssen Sie die ODBC-API-Funktion verwenden.

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a>RFX_Single_Bulk

Überträgt mehrere Zeilen von Gleitkommadaten aus einer Spalte einer `CRecordset`ODBC-Datenquelle an ein entsprechendes Array in einem -derived-Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](cfieldexchange-class.md) Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*prgFltVals*<br/>
Ein Zeiger auf ein Array von **Float-Werten.** Dieses Array speichert die Daten, die von der Datenquelle in das Recordset übertragen werden sollen.

*prgLengths*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Länge in Bytes jedes Werts im Array, auf das von *prgFltVals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen Nullwert enthält. Weitere Informationen finden Sie in `SQLBindCol` der ODBC-API-Funktion in der *ODBC SDK-Programmiererreferenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellenspalte muss über einen ODBC-Typ SQL_REAL verfügen. Das Recordset muss einen Felddatenmember des Typzeigers zum **float**definieren.

Wenn Sie *prgFltVals* und *prgLengths* auf NULL initialisieren, werden die Arrays, auf die sie verweisen, automatisch zugewiesen, wobei die Größen der Rowsetgröße entsprechen.

> [!NOTE]
> Der Massendatensatzfeldaustausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um Ihr Recordset aktualisierbar zu machen, `SQLSetPos`müssen Sie die ODBC-API-Funktion verwenden.

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a>RFX_Text_Bulk

Überträgt mehrere Zeilen von Zeichendaten aus einer Spalte einer ODBC-Datenquelle auf ein entsprechendes Array in einem `CRecordset`-derived-Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein [CFieldExchange-Objekt.](cfieldexchange-class.md) Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Datensatzfeldaustausch: Funktionsweise](../../data/odbc/record-field-exchange-how-rfx-works.md)von RFX .

*Szname*<br/>
Der Name einer Datenspalte.

*prgStrVals*<br/>
Ein Zeiger auf ein Array von LPSTR-Werten. Dieses Array speichert die Daten, die von der Datenquelle in das Recordset übertragen werden sollen. Beachten Sie, dass diese Werte mit der aktuellen Version von ODBC nicht Unicode sein können.

*prgLengths*<br/>
Ein Zeiger auf ein Array langer ganzer Zahlen. Dieses Array speichert die Länge in Bytes jedes Werts im Array, auf das von *prgStrVals*verwiesen wird. Diese Länge schließt das Nullbeendigungszeichen aus. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen Nullwert enthält. Weitere Informationen finden Sie in `SQLBindCol` der ODBC-API-Funktion in der *ODBC SDK-Programmiererreferenz*.

*nMaxLength*<br/>
Die maximal zulässige Länge der im Array gespeicherten Werte, auf die *prgStrVals*zeigt, einschließlich des Nullbeendigungszeichens. Um sicherzustellen, dass Daten nicht abgeschnitten werden, übergeben Sie einen Wert, der groß genug ist, um das größte erwartete Datenelement aufzunehmen.

### <a name="remarks"></a>Bemerkungen

Die Datenquellenspalte kann einen ODBC-Typ von SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL oder SQL_NUMERIC aufweisen. Das Recordset muss ein Felddatenelement vom Typ LPSTR definieren.

Wenn Sie *prgStrVals* und *prgLengths* auf NULL initialisieren, werden die Arrays, auf die sie verweisen, automatisch zugewiesen, wobei die Größen der Rowsetgröße entsprechen.

> [!NOTE]
> Der Massendatensatzfeldaustausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um Ihr Recordset aktualisierbar zu machen, `SQLSetPos`müssen Sie die ODBC-API-Funktion verwenden.

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) und [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Sie müssen Anrufe manuell `DoBulkFieldExchange` in Ihre Außerkraftsetzung schreiben. Dieses Beispiel zeigt `RFX_Text_Bulk`einen Aufruf von , `RFX_Long_Bulk`sowie einen Aufruf von für die Datenübertragung. Diesen Aufrufen geht ein Aufruf von [CFieldExchange::SetFieldType](cfieldexchange-class.md#setfieldtype)voraus. Beachten Sie, dass Sie für Parameter die RFX-Funktionen anstelle der Bulk-RFX-Funktionen aufrufen müssen.

```cpp
void CMultiCustomer::DoBulkFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Long_Bulk(pFX, _T("[CustomerID]"), &m_pCustomerID, &m_pcCustomerID);
   RFX_Text_Bulk(pFX, _T("[ContactFirstName]"), &m_pContactFirstName, &m_pcContactFirstName, 50);
   RFX_Text_Bulk(pFX, _T("[PostalCode]"), &m_pPostalCode, &m_pcPostalCode, 50);
   RFX_Text_Bulk(pFX, _T("[L_Name]"), &m_pL_Name, &m_pcL_Name, 50);
   RFX_Long_Bulk(pFX, _T("[BillingID]"), &m_pBillingID, &m_pcBillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb.h

## <a name="dfx_binary"></a><a name="dfx_binary"></a>DFX_Binary

Überträgt Arrays von Bytes zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ [CByteArray](cbytearray-class.md)vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*nPreAllocSize*<br/>
Das Framework weist diese Speichermenge vorab zu. Wenn Ihre Daten größer sind, wird dem Framework bei Bedarf mehr Speicherplatz zugewiesen. Um eine bessere Leistung zu erzielen, legen Sie diese Größe auf einen Wert fest, der groß genug ist, um Umschichtungen zu verhindern. Die Standardgröße ist im AFXDAO definiert. H-Datei als AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_DISABLE_FIELD_CACHE verwendet keine doppelte Pufferung, und Sie müssen [SetFieldDirty](cdaorecordset-class.md#setfielddirty) und [SetFieldNull](cdaorecordset-class.md#setfieldnull) selbst aufrufen. Der andere mögliche Wert, AFX_DAO_ENABLE_FIELD_CACHE, verwendet doppelte Pufferung, und Sie müssen keine zusätzliche Arbeit leisten, um Felder als schmutzig oder Null zu markieren. Vermeiden Sie diesen Wert aus Leistungs- und Speichergründen, es sei denn, die Binärdaten sind relativ klein.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig für alle Felder doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen Typ DAO_BYTES in DAO und Typ [CByteArray](cbytearray-class.md) im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_bool"></a><a name="dfx_bool"></a>DFX_Bool

Überträgt boolesche Daten zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ BOOL vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen `SetFieldDirty` `SetFieldNull` anrufen und sich selbst.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Die Daten werden zwischen typ DAO_BOOL in DAO und typ BOOL im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_byte"></a><a name="dfx_byte"></a>DFX_Byte

Überträgt einzelne Bytes zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ BYTE vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen `SetFieldDirty` `SetFieldNull` anrufen und sich selbst.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen Typ DAO_BYTES in DAO und BYTE im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_currency"></a><a name="dfx_currency"></a>DFX_Currency

Überträgt Währungsdaten zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird dieser Wert dem angegebenen Datenmember vom Typ [COleCurrency](colecurrency-class.md)entnommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen `SetFieldDirty` `SetFieldNull` anrufen und sich selbst.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen Typ DAO_CURRENCY in DAO und Typ [COleCurrency](colecurrency-class.md) im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a>DFX_DateTime

Überträgt Zeit- und Datumsdaten zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Die Funktion nimmt einen Verweis auf ein [COleDateTime-Objekt.](../../atl-mfc-shared/reference/coledatetime-class.md) Bei einer Übertragung von Recordset in die Datenquelle wird dieser Wert dem angegebenen Datenmember entnommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen `SetFieldDirty` `SetFieldNull` anrufen und sich selbst.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen Typ DAO_DATE in DAO und Typ [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) im Recordset zugeordnet.

> [!NOTE]
> `COleDateTime`ersetzt [CTime](../../atl-mfc-shared/reference/ctime-class.md) und TIMESTAMP_STRUCT zu diesem Zweck in den DAO-Klassen. `CTime`und TIMESTAMP_STRUCT werden weiterhin für die ODBC-basierten Datenzugriffsklassen verwendet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_double"></a><a name="dfx_double"></a>DFX_Double

Überträgt **doppelte Float-Daten** zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ **double**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen `SetFieldDirty` `SetFieldNull` anrufen und sich selbst.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Die Daten werden zwischen typ DAO_R8 in DAO und **double float** im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_long"></a><a name="dfx_long"></a>DFX_Long

Überträgt lange ganzzahlige Daten zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ **long**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen `SetFieldDirty` `SetFieldNull` anrufen und sich selbst.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Die Daten werden zwischen typ DAO_I4 in DAO und type **long** im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a>DFX_LongBinary

**Wichtig** Es wird empfohlen, [DFX_Binary](#dfx_binary) anstelle dieser Funktion zu verwenden.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ [CLongBinary](clongbinary-class.md)vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwPreAllocSize*<br/>
Das Framework weist diese Speichermenge vorab zu. Wenn Ihre Daten größer sind, wird dem Framework bei Bedarf mehr Speicherplatz zugewiesen. Um eine bessere Leistung zu erzielen, legen Sie diese Größe auf einen Wert fest, der groß genug ist, um Umschichtungen zu verhindern.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DISABLE_FIELD_CACHE verwendet keine doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_ENABLE_FIELD_CACHE. Verwendet doppelte Pufferung, und Sie müssen keine zusätzliche Arbeit leisten, um Felder schmutzig oder Null zu markieren. Vermeiden Sie diesen Wert aus Leistungs- und Speichergründen, es sei denn, die Binärdaten sind relativ klein.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

`DFX_LongBinary`wird für die Kompatibilität mit den MFC ODBC-Klassen bereitgestellt. Die `DFX_LongBinary` Funktion überträgt binäre BLOB-Daten `CLongBinary` (Large-Object) mithilfe einer Klasse zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle. Daten werden zwischen Typ DAO_BYTES in DAO und Typ [CLongBinary](clongbinary-class.md) im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_short"></a><a name="dfx_short"></a>DFX_Short

Überträgt kurze Ganzzahldaten zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ **short**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen `SetFieldDirty` `SetFieldNull` anrufen und sich selbst.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Die Daten werden zwischen typ DAO_I2 in DAO und typ **short** im Recordset zugeordnet.

> [!NOTE]
> `DFX_Short`entspricht [RFX_Int](#rfx_int) für die ODBC-basierten Klassen.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_single"></a><a name="dfx_single"></a>DFX_Single

Überträgt Gleitkommadaten zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ **float**vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen `SetFieldDirty` `SetFieldNull` anrufen und sich selbst.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Die Daten werden zwischen typ DAO_R4 in DAO und typ **float** im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="dfx_text"></a><a name="dfx_text"></a>DFX_Text

Überträgt `CString` Daten zwischen den Felddatenmembern eines [CDaoRecordset-Objekts](cdaorecordset-class.md) und Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*Pfx*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für jeden Aufruf der Funktion zu definieren.

*Szname*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebenen Datenelement gespeicherte Wert – der zu übertragende Wert. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert vom Typ [CString](../../atl-mfc-shared/reference/cstringt-class.md)vom angegebenen Datenmember übernommen. Bei einer Übertragung von der Datenquelle zum Recordset wird der Wert im angegebenen Datenmember gespeichert.

*nPreAllocSize*<br/>
Das Framework weist diese Speichermenge vorab zu. Wenn Ihre Daten größer sind, wird dem Framework bei Bedarf mehr Speicherplatz zugewiesen. Um eine bessere Leistung zu erzielen, legen Sie diese Größe auf einen Wert fest, der groß genug ist, um Umschichtungen zu verhindern.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffermechanismus von MFC nutzen können, um geänderte Recordsetfelder zu erkennen. Der Standardwert AFX_DAO_ENABLE_FIELD_CACHE verwendet doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, führt MFC keine Überprüfung dieses Feldes durch. Sie müssen [SetFieldDirty](cdaorecordset-class.md#setfielddirty) und [SetFieldNull](cdaorecordset-class.md#setfieldnull) selbst aufrufen.

> [!NOTE]
> Sie können steuern, ob Daten standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Die Daten werden zwischen typ DAO_CHAR in DAO (oder, wenn das Symbol _UNICODE definiert ist, DAO_WCHAR) und dem Typ [CString](../../atl-mfc-shared/reference/cstringt-class.md) im Recordset zugeordnet.  n

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt `DFX_Text`mehrere Aufrufe von . Beachten Sie auch die beiden Aufrufe von [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype). Sie müssen den ersten `SetFieldType` Aufruf und seinen **DFX-Aufruf** schreiben. Der zweite Aufruf und die zugehörigen **DFX-Aufrufe** werden normalerweise vom Code-Assistenten geschrieben, der die Klasse generiert hat.

```cpp
void CCustSet::DoFieldExchange(CDaoFieldExchange* pFX)
{
   pFX->SetFieldType(CDaoFieldExchange::param);
   DFX_Text(pFX, _T("Param"), m_strParam);
   pFX->SetFieldType(CDaoFieldExchange::outputColumn);
   DFX_Short(pFX, _T("EmployeeID"), m_EmployeeID);
   DFX_Text(pFX, _T("LastName"), m_LastName);
   DFX_Short(pFX, _T("Age"), m_Age);
   DFX_DateTime(pFX, _T("hire_date"), m_hire_date);
   DFX_DateTime(pFX, _T("termination_date"), m_termination_date);

   CDaoRecordset::DoFieldExchange(pFX);
}
```

### <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
