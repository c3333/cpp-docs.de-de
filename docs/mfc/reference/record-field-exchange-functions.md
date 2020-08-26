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
ms.openlocfilehash: 9bb1b7bcbce16bba8029fcfbbeea7552b1d4a0ba
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843598"
---
# <a name="record-field-exchange-functions"></a>Funktionen für den Datensatzfeldaustausch

Dieses Thema enthält die Datensatzfeldaustausch (RFX, Bulk-RFX und DFX)-Funktionen, mit denen die Übertragung von Daten zwischen einem Recordset-Objekt und den zugehörigen Datenquellen automatisiert und andere Datenvorgänge ausgeführt werden.

Wenn Sie die ODBC-basierten Klassen verwenden und einen Massenzeilenabruf implementiert haben, müssen Sie die `DoBulkFieldExchange` -Memberfunktion des `CRecordset` manuell überschreiben, indem Sie die Bulk-RFX-Funktionen für jedes Datenelement aufrufen, das einer Datenquellspalte entspricht.

Wenn Sie das Massen Abrufen von Zeilen in den ODBC-basierten Klassen nicht implementiert haben oder wenn Sie die DAO-basierten Klassen (veraltet) verwenden, überschreibt der Klassen-Assistent die `DoFieldExchange` Member-Funktion von `CRecordset` oder `CDaoRecordset` durch Aufrufen der RFX-Funktionen (für ODBC-Klassen) oder der DFX-Funktionen (für DAO-Klassen) für jedes Feld Datenelement in Ihrem Recordset.

Die Datensatzfeldaustausch-Funktionen übertragen jedes Mal Daten, wenn das Framework `DoFieldExchange` oder `DoBulkFieldExchange`aufruft. Jede Funktion überträgt einen bestimmten Datentyp.

Weitere Informationen über die Verwendung dieser Funktionen finden Sie in den Artikeln [Datensatzfeldaustausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Weitere Informationen über das gesammelte Abrufen von Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Für Datenspalten, die Sie dynamisch binden, können Sie auch die RFX- oder DFX-Funktionen selbst aufrufen, wie in den Artikeln [Recordset: Dynamisches Binden von Spalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)beschrieben. Darüber hinaus können Sie Ihre eigenen benutzerdefinierten RFX- oder DFX-Routinen schreiben, wie im technischen Hinweis [43](../../mfc/tn043-rfx-routines.md) (für ODBC) und im technischen Hinweis [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (für DAO) erläutert.

Ein Beispiel für RFX und Bulk-RFX-Funktionen, wie Sie in `DoFieldExchange` den `DoBulkFieldExchange` Funktionen und auftreten, finden Sie unter [RFX_Text](#rfx_text) und [RFX_Text_Bulk] #rfx_text_bulk). DFX-Funktionen sind den RFX-Funktionen sehr ähnlich.

### <a name="rfx-functions-odbc"></a>RFX-Funktionen (ODBC)

|Name|Beschreibung|
|-|-|
|[RFX_Binary](#rfx_binary)|Überträgt Byte-Arrays vom Typ [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Überträgt boolesche Daten.|
|[RFX_Byte](#rfx_byte)|Überträgt ein einzelnes Byte an Daten.|
|[RFX_Date](#rfx_date)|Überträgt Zeit-und Datumsdaten mit [ctime](../../atl-mfc-shared/reference/ctime-class.md) oder TIMESTAMP_STRUCT.|
|[RFX_Double](#rfx_double)|Überträgt Gleitkommazahl mit doppelter Genauigkeit.|
|[RFX_Int](#rfx_int)|Überträgt Ganzzahldaten.|
|[RFX_Long](#rfx_long)|Überträgt lange Ganzzahldaten.|
|[RFX_LongBinary](#rfx_longbinary)|Überträgt BLOB-Daten (Binary Large Object) mit einem Objekt der [CLongBinary](clongbinary-class.md) Klasse.|
|[RFX_Single](#rfx_single)|Überträgt Gleitkommadaten.|
|[RFX_Text](#rfx_text)|Überträgt Zeichenfolgendaten.|

### <a name="bulk-rfx-functions-odbc"></a>Bulk-RFX-Funktionen (ODBC)

|Name|Beschreibung|
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

|Name|Beschreibung|
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

## <a name="rfx_binary"></a><a name="rfx_binary"></a> RFX_Binary

Überträgt Arrays von Bytes zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_BINARY, SQL_VARBINARY oder SQL_LONGVARBINARY.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs [CByteArray](cbytearray-class.md)aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*nMaxLength*<br/>
Die maximal zulässige Länge der übertragenen Zeichenfolge oder des Arrays. Der Standardwert von *nMaxLength* ist 255. Zulässige Werte sind 1 bis INT_MAX. Das Framework ordnet diese Menge an Speicherplatz für die Daten zu. Um die optimale Leistung zu erzielen, übergeben Sie einen Wert, der groß genug ist, um das größte erwartete Datenelement zu verarbeiten

### <a name="remarks"></a>Bemerkungen

Daten in der Datenquelle dieser Typen werden dem Typ und vom Typ `CByteArray` im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_bool"></a><a name="rfx_bool"></a> RFX_Bool

Überträgt boolesche Daten zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_BIT.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert des Typs bool vom angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_byte"></a><a name="rfx_byte"></a> RFX_Byte

Überträgt einzelne Bytes zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_TINYINT.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs Byte vom angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_date"></a><a name="rfx_date"></a> RFX_Date

Überträgt `CTime` oder TIMESTAMP_STRUCT Daten zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_DATE, SQL_TIME oder SQL_TIMESTAMP.

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

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert. der Wert, der übertragen werden soll. Die verschiedenen Versionen der-Funktion nehmen unterschiedliche Datentypen für den Wert auf:

Die erste Version der Funktion nimmt einen Verweis auf ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt an. Bei einer Übertragung von Recordset in die Datenquelle wird dieser Wert vom angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

Die zweite Version der Funktion nimmt einen Verweis auf eine- `TIMESTAMP_STRUCT` Struktur auf. Sie müssen diese Struktur selbst vor dem-Befehl einrichten. Für diese Version ist weder die Unterstützung für den Dialog Datenaustausch (DDX) noch die Unterstützung des Code-Assistenten verfügbar. Die dritte Version der-Funktion funktioniert ähnlich wie die erste Version, mit dem Unterschied, dass Sie einen Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt annimmt.

### <a name="remarks"></a>Bemerkungen

Die `CTime` -Version der-Funktion erzwingt den mehr Aufwand für einige zwischen Verarbeitung und hat einen etwas begrenzten Bereich. Wenn Sie einen dieser Faktoren zu eingeschränkt finden, verwenden Sie die zweite Version der Funktion. Beachten Sie jedoch den fehlenden Code-Assistenten und die DDX-Unterstützung sowie die Anforderung, dass Sie die Struktur selbst einrichten.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_double"></a><a name="rfx_double"></a> RFX_Double

Überträgt **doppelte float** -Daten zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_DOUBLE.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`double`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_int"></a><a name="rfx_int"></a> RFX_Int

Überträgt ganzzahlige Daten zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_SMALLINT.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`int`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_long"></a><a name="rfx_long"></a> RFX_Long

Überträgt lange ganzzahlige Daten zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_INTEGER.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`long`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a> RFX_LongBinary

Überträgt Binary Large Object (BLOB)-Daten mithilfe der [CLongBinary](clongbinary-class.md) -Klasse zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_LONGVARBINARY oder SQL_LONGVARCHAR.

### <a name="syntax"></a>Syntax

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs `CLongBinary` aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_single"></a><a name="rfx_single"></a> RFX_Single

Überträgt Gleit Komma Daten zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_REAL.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`float`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_text"></a><a name="rfx_text"></a> RFX_Text

Überträgt `CString` Daten zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL oder SQL_NUMERIC.

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

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse `CFieldExchange` . Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs `CString` aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*nMaxLength*<br/>
Die maximal zulässige Länge der übertragenen Zeichenfolge oder des Arrays. Der Standardwert von *nMaxLength* ist 255. Zulässige Werte sind 1 bis INT_MAX). Das Framework ordnet diese Menge an Speicherplatz für die Daten zu. Um die optimale Leistung zu erzielen, übergeben Sie einen Wert, der groß genug ist, um das größte erwartete Datenelement zu verarbeiten

*ncolumntype*<br/>
Wird hauptsächlich für Parameter verwendet. Eine ganze Zahl, die den Datentyp des Parameters angibt. Der Typ ist ein ODBC-Datentyp der Form **SQL_XXX**.

*nskala*<br/>
Gibt die Skala für Werte des ODBC-Typs SQL_DECIMAL oder SQL_NUMERIC an. *nscale* ist nur nützlich, wenn Parameterwerte festgelegt werden. Weitere Informationen finden Sie im Thema "Genauigkeit, Skalierung, Länge und Anzeige Größe" in Anhang D der *ODBC SDK-Programmier Referenz*.

### <a name="remarks"></a>Bemerkungen

Die Daten in der Datenquelle aller dieser Typen werden dem Recordset zugeordnet und werden aus `CString` diesem zugeordnet.

### <a name="example"></a>Beispiel

In diesem Beispiel werden mehrere Aufrufe von gezeigt `RFX_Text` . Beachten Sie auch die beiden Aufrufe von `CFieldExchange::SetFieldType` . Für Parameter müssen Sie den `SetFieldType` -und den zugehörigen RFX-Aufrufvorgang schreiben. Der Aufruf der Ausgabe Spalte und die zugehörigen RFX-Aufrufe werden normalerweise von einem Code-Assistenten geschrieben.

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

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a> RFX_Binary_Bulk

Überträgt mehrere Zeilen von Byte Daten aus einer Spalte einer ODBC-Datenquelle an ein entsprechendes Array in einem von `CRecordset` abgeleiteten Objekt.

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

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](cfieldexchange-class.md) -Objekt. Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*prgbytevals*<br/>
Ein Zeiger auf ein Array von Byte Werten. Dieses Array speichert die Daten, die aus der Datenquelle in das Recordset übertragen werden sollen.

*prglengths*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Länge der einzelnen Werte im Array, auf die von *prgbytevals*verwiesen wird, in Byte. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen NULL-Wert enthält. Weitere Informationen finden Sie in der ODBC-API `SQLBindCol` -Funktion in der *ODBC SDK-Programmier Referenz*.

*nMaxLength*<br/>
Die maximal zulässige Länge der im Array gespeicherten Werte, auf die durch *prgbytevals*verwiesen wird. Um sicherzustellen, dass die Daten nicht abgeschnitten werden, übergeben Sie einen Wert, der groß genug ist, um das größte erwartete Datenelement zu verarbeiten.

### <a name="remarks"></a>Bemerkungen

Die Datenquellen Spalte kann den ODBC-Typ SQL_BINARY, SQL_VARBINARY oder SQL_LONGVARBINARY aufweisen. Das Recordset muss einen Felddatenmember vom Typ "Zeiger auf Byte" definieren.

Wenn Sie *prgbytevals* und *prglengths* auf Null initialisieren, werden die Arrays, auf die Sie zeigen, automatisch zugeordnet, wobei die Größe der Rowsetgröße entspricht.

> [!NOTE]
> Der Massendaten Satz Feld Austausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um das Recordset aktualisierbar zu machen, müssen Sie die ODBC-API-Funktion verwenden `SQLSetPos` .

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC) und in](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a> RFX_Bool_Bulk

Überträgt mehrere Zeilen von booleschen Daten aus einer Spalte einer ODBC-Datenquelle an ein entsprechendes Array in einem von `CRecordset` abgeleiteten Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](cfieldexchange-class.md) -Objekt. Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*prgboolvals*<br/>
Ein Zeiger auf ein Array von booleschen Werten. Dieses Array speichert die Daten, die aus der Datenquelle in das Recordset übertragen werden sollen.

*prglengths*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Länge der einzelnen Werte im Array in Bytes, auf die durch *prgboolvals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen NULL-Wert enthält. Weitere Informationen finden Sie in der ODBC-API `SQLBindCol` -Funktion in der *ODBC SDK-Programmier Referenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellen Spalte muss den ODBC-Typ "SQL_BIT" aufweisen. Das Recordset muss einen Felddatenmember vom Typ Zeiger auf bool definieren.

Wenn Sie *prgboolvals* und *prglengths* auf Null initialisieren, werden die Arrays, auf die Sie zeigen, automatisch zugeordnet, wobei die Größe der Rowsetgröße entspricht.

> [!NOTE]
> Der Massendaten Satz Feld Austausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um das Recordset aktualisierbar zu machen, müssen Sie die ODBC-API-Funktion verwenden `SQLSetPos` .

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC) und in](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a> RFX_Byte_Bulk

Überträgt mehrere Zeilen von einzelnen Bytes aus einer Spalte einer ODBC-Datenquelle an ein entsprechendes Array in einem von `CRecordset` abgeleiteten Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](cfieldexchange-class.md) -Objekt. Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*prgbytevals*<br/>
Ein Zeiger auf ein Array von Byte Werten. Dieses Array speichert die Daten, die aus der Datenquelle in das Recordset übertragen werden sollen.

*prglengths*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Länge der einzelnen Werte im Array, auf die von *prgbytevals*verwiesen wird, in Byte. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen NULL-Wert enthält. Weitere Informationen finden Sie in der ODBC-API `SQLBindCol` -Funktion in der *ODBC SDK-Programmier Referenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellen Spalte muss den ODBC-Typ "SQL_TINYINT" aufweisen. Das Recordset muss einen Felddatenmember vom Typ "Zeiger auf Byte" definieren.

Wenn Sie *prgbytevals* und *prglengths* auf Null initialisieren, werden die Arrays, auf die Sie zeigen, automatisch zugeordnet, wobei die Größe der Rowsetgröße entspricht.

> [!NOTE]
> Der Massendaten Satz Feld Austausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um das Recordset aktualisierbar zu machen, müssen Sie die ODBC-API-Funktion verwenden `SQLSetPos` .

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC) und in](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a> RFX_Date_Bulk

Überträgt mehrere Zeilen von TIMESTAMP_STRUCT Daten aus einer Spalte einer ODBC-Datenquelle an ein entsprechendes Array in einem von `CRecordset` abgeleiteten Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](cfieldexchange-class.md) -Objekt. Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*prggs*<br/>
Ein Zeiger auf ein Array von TIMESTAMP_STRUCT Werten. Dieses Array speichert die Daten, die aus der Datenquelle in das Recordset übertragen werden sollen. Weitere Informationen zum TIMESTAMP_STRUCT-Datentyp finden Sie im Thema "C-Datentypen" in Anhang D der *ODBC SDK-Programmier Referenz*.

*prglengths*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Länge der einzelnen Werte im Array in Bytes, auf die durch *prgtvals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen NULL-Wert enthält. Weitere Informationen finden Sie in der ODBC-API `SQLBindCol` -Funktion in der *ODBC SDK-Programmier Referenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellen Spalte kann den ODBC-Typ SQL_DATE, SQL_TIME oder SQL_TIMESTAMP aufweisen. Das Recordset muss einen Felddatenmember vom Typ Zeiger auf TIMESTAMP_STRUCT definieren.

Wenn Sie *prgzvals* und *prglengths* auf Null initialisieren, werden die Arrays, auf die Sie zeigen, automatisch zugeordnet, wobei die Größe der Rowsetgröße entspricht.

> [!NOTE]
> Der Massendaten Satz Feld Austausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um das Recordset aktualisierbar zu machen, müssen Sie die ODBC-API-Funktion verwenden `SQLSetPos` .

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC) und in](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a> RFX_Double_Bulk

Überträgt mehrere Zeilen mit Gleit Komma Daten mit doppelter Genauigkeit aus einer Spalte einer ODBC-Datenquelle in ein entsprechendes Array in einem von `CRecordset` abgeleiteten Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](cfieldexchange-class.md) -Objekt. Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*prdsblvals*<br/>
Ein Zeiger auf ein Array von- **`double`** Werten. Dieses Array speichert die Daten, die aus der Datenquelle in das Recordset übertragen werden sollen.

*prglengths*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Länge der einzelnen Werte im Array in Bytes, auf die durch *prdsblvals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen NULL-Wert enthält. Weitere Informationen finden Sie in der ODBC-API `SQLBindCol` -Funktion in der *ODBC SDK-Programmier Referenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellen Spalte muss den ODBC-Typ "SQL_DOUBLE" aufweisen. Das Recordset muss einen Felddatenmember vom Typ "Zeiger auf" definieren **`double`** .

Wenn Sie *prdsblvals* und *prglengths* auf Null initialisieren, werden die Arrays, auf die Sie zeigen, automatisch zugeordnet, wobei die Größe der Rowsetgröße entspricht.

> [!NOTE]
> Der Massendaten Satz Feld Austausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um das Recordset aktualisierbar zu machen, müssen Sie die ODBC-API-Funktion verwenden `SQLSetPos` .

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC) und in](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a> RFX_Int_Bulk

Überträgt ganzzahlige Daten zwischen den Felddatenmembern eines `CRecordset` -Objekts und den Spalten eines Datensatzes in der Datenquelle des ODBC-Typs SQL_SMALLINT.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CFieldExchange](cfieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen zu den Vorgängen, die ein- `CFieldExchange` Objekt angeben kann, finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`int`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

### <a name="example"></a>Beispiel

Siehe [RFX_Text](#rfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a> RFX_Long_Bulk

Überträgt mehrere Zeilen mit langen ganzzahligen Daten aus einer Spalte einer ODBC-Datenquelle an ein entsprechendes Array in einem von `CRecordset` abgeleiteten Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](cfieldexchange-class.md) -Objekt. Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*prglongvals*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Daten, die aus der Datenquelle in das Recordset übertragen werden sollen.

*prglengths*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Länge der einzelnen Werte im Array in Bytes, auf die von *prglongvals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen NULL-Wert enthält. Weitere Informationen finden Sie in der ODBC-API `SQLBindCol` -Funktion in der *ODBC SDK-Programmier Referenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellen Spalte muss den ODBC-Typ "SQL_INTEGER" aufweisen. Das Recordset muss einen Felddatenmember vom Typ "Zeiger auf" definieren **`long`** .

Wenn Sie *prglongvals* und *prglengths* auf Null initialisieren, werden die Arrays, auf die Sie zeigen, automatisch zugeordnet, wobei die Größe der Rowsetgröße entspricht.

> [!NOTE]
> Der Massendaten Satz Feld Austausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um das Recordset aktualisierbar zu machen, müssen Sie die ODBC-API-Funktion verwenden `SQLSetPos` .

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC) und in](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a> RFX_Single_Bulk

Überträgt mehrere Zeilen von Gleit Komma Daten aus einer Spalte einer ODBC-Datenquelle in ein entsprechendes Array in einem von `CRecordset` abgeleiteten Objekt.

### <a name="syntax"></a>Syntax

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](cfieldexchange-class.md) -Objekt. Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*prgfltvals*<br/>
Ein Zeiger auf ein Array von- **`float`** Werten. Dieses Array speichert die Daten, die aus der Datenquelle in das Recordset übertragen werden sollen.

*prglengths*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Länge der einzelnen Werte im Array in Bytes, auf die von *prgfltvals*verwiesen wird. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen NULL-Wert enthält. Weitere Informationen finden Sie in der ODBC-API `SQLBindCol` -Funktion in der *ODBC SDK-Programmier Referenz*.

### <a name="remarks"></a>Bemerkungen

Die Datenquellen Spalte muss den ODBC-Typ "SQL_REAL" aufweisen. Das Recordset muss einen Felddatenmember vom Typ "Zeiger auf" definieren **`float`** .

Wenn Sie *prgfltvals* und *prglengths* auf Null initialisieren, werden die Arrays, auf die Sie zeigen, automatisch zugeordnet, wobei die Größe der Rowsetgröße entspricht.

> [!NOTE]
> Der Massendaten Satz Feld Austausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um das Recordset aktualisierbar zu machen, müssen Sie die ODBC-API-Funktion verwenden `SQLSetPos` .

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC) und in](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Siehe [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a> RFX_Text_Bulk

Überträgt mehrere Zeilen von Zeichendaten aus einer Spalte einer ODBC-Datenquelle an ein entsprechendes Array in einem von `CRecordset` abgeleiteten Objekt.

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

*PFX*<br/>
Ein Zeiger auf ein [CFieldExchange](cfieldexchange-class.md) -Objekt. Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren. Weitere Informationen finden Sie im Artikel [Daten Satz Feld Austausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Der Name einer Datenspalte.

*prgstranvals*<br/>
Ein Zeiger auf ein Array von LPSTR-Werten. Dieses Array speichert die Daten, die aus der Datenquelle in das Recordset übertragen werden sollen. Beachten Sie, dass diese Werte mit der aktuellen Version von ODBC nicht Unicode sein können.

*prglengths*<br/>
Ein Zeiger auf ein Array von langen ganzen Zahlen. Dieses Array speichert die Länge der einzelnen Werte im Array in Bytes, auf die durch *prgstrauvals*verwiesen wird. Diese Länge schließt das NULL-Beendigungs Zeichen aus. Beachten Sie, dass der Wert SQL_NULL_DATA gespeichert wird, wenn das entsprechende Datenelement einen NULL-Wert enthält. Weitere Informationen finden Sie in der ODBC-API `SQLBindCol` -Funktion in der *ODBC SDK-Programmier Referenz*.

*nMaxLength*<br/>
Die maximal zulässige Länge der im Array gespeicherten Werte, auf die durch *prgstranvals*verwiesen wird, einschließlich des NULL-Beendigungs Zeichens. Um sicherzustellen, dass die Daten nicht abgeschnitten werden, übergeben Sie einen Wert, der groß genug ist, um das größte erwartete Datenelement zu verarbeiten.

### <a name="remarks"></a>Bemerkungen

Die Datenquellen Spalte kann den ODBC-Typ SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL oder SQL_NUMERIC aufweisen. Das Recordset muss einen Felddatenmember des Typs LPSTR definieren.

Wenn Sie *prgstrauvals* und *prglengths* auf Null initialisieren, werden die Arrays, auf die Sie zeigen, automatisch zugeordnet, wobei die Größe der Rowsetgröße entspricht.

> [!NOTE]
> Der Massendaten Satz Feld Austausch überträgt nur Daten aus der Datenquelle an das Recordset-Objekt. Um das Recordset aktualisierbar zu machen, müssen Sie die ODBC-API-Funktion verwenden `SQLSetPos` .

Weitere Informationen finden Sie in den Artikeln [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC) und in](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Beispiel

Sie müssen Anrufe manuell in Ihre `DoBulkFieldExchange` außer Kraft Setzung schreiben. In diesem Beispiel wird ein-und `RFX_Text_Bulk` ein-Rückruf `RFX_Long_Bulk` für die Datenübertragung gezeigt. Diesen aufrufen wird ein Aufruf von [CFieldExchange:: SetFieldType](cfieldexchange-class.md#setfieldtype)vorangestellt. Beachten Sie, dass Sie für Parameter die RFX-Funktionen anstelle der Bulk-RFX-Funktionen aufzurufen müssen.

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

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="dfx_binary"></a><a name="dfx_binary"></a> DFX_Binary

Überträgt Byte Arrays zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

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

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs [CByteArray](cbytearray-class.md)aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*nprezuzugröße*<br/>
Das Framework ordnet diese Menge an Arbeitsspeicher zu. Wenn Ihre Daten größer sind, weist das Framework nach Bedarf mehr Speicherplatz zu. Legen Sie für eine bessere Leistung diese Größe auf einen Wert fest, der groß genug ist, um erneute Zuordnungen zu verhindern Die Standardgröße wird in afxdao definiert. H-Datei als AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standardwert (AFX_DAO_DISABLE_FIELD_CACHE) verwendet keine doppelte Pufferung, und Sie müssen [SetFieldDirty](cdaorecordset-class.md#setfielddirty) und [SetFieldNull](cdaorecordset-class.md#setfieldnull) selbst aufrufen. Der andere mögliche Wert, AFX_DAO_ENABLE_FIELD_CACHE, verwendet die doppelte Pufferung, und Sie müssen keine zusätzlichen Schritte durchführen, um die Felder "Dirty" oder "Null" zu markieren. Vermeiden Sie aus Leistungs-und Arbeitsspeicher Gründen diesen Wert, es sei denn, die Binärdaten sind relativ klein.

> [!NOTE]
> Sie können steuern, ob die Daten für alle Felder standardmäßig doppelt gepuffert werden, indem Sie [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)festlegen.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_BYTES in DAO zugeordnet und geben [CByteArray](cbytearray-class.md) in das Recordset ein.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_bool"></a><a name="dfx_bool"></a> DFX_Bool

Überträgt boolesche Daten zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert des Typs bool vom angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen `SetFieldDirty` und `SetFieldNull` selbst anrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_BOOL in DAO und dem Typ bool im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_byte"></a><a name="dfx_byte"></a> DFX_Byte

Überträgt einzelne Bytes zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs Byte vom angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen `SetFieldDirty` und `SetFieldNull` selbst anrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_BYTES in DAO und dem Typ Byte im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_currency"></a><a name="dfx_currency"></a> DFX_Currency

Überträgt Währungs Daten zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset in die Datenquelle wird dieser Wert vom angegebenen Datenmember des Typs [COleCurrency](colecurrency-class.md)entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen `SetFieldDirty` und `SetFieldNull` selbst anrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_CURRENCY in DAO und dem Typ [COleCurrency](colecurrency-class.md) im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a> DFX_DateTime

Überträgt Zeit-und Datumsdaten zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Die Funktion nimmt einen Verweis auf ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt an. Bei einer Übertragung von Recordset in die Datenquelle wird dieser Wert vom angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen `SetFieldDirty` und `SetFieldNull` selbst anrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_DATE in DAO und dem Typ [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) im Recordset zugeordnet.

> [!NOTE]
> `COleDateTime` ersetzt [ctime](../../atl-mfc-shared/reference/ctime-class.md) und TIMESTAMP_STRUCT zu diesem Zweck in den DAO-Klassen. `CTime` und TIMESTAMP_STRUCT werden weiterhin für die ODBC-basierten Datenzugriffsklassen verwendet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_double"></a><a name="dfx_double"></a> DFX_Double

Überträgt **doppelte float** -Daten zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`double`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen `SetFieldDirty` und `SetFieldNull` selbst anrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_R8 in DAO und dem Typ **Double Float** im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_long"></a><a name="dfx_long"></a> DFX_Long

Überträgt lange ganzzahlige Daten zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`long`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen `SetFieldDirty` und `SetFieldNull` selbst anrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_I4 in DAO und **`long`** dem Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a> DFX_LongBinary

**Wichtig** Es wird empfohlen, anstelle dieser Funktion [DFX_Binary](#dfx_binary) zu verwenden.

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

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert des Typs [CLongBinary](clongbinary-class.md)aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwprezuzugrößengröße*<br/>
Das Framework ordnet diese Menge an Arbeitsspeicher zu. Wenn Ihre Daten größer sind, weist das Framework nach Bedarf mehr Speicherplatz zu. Legen Sie für eine bessere Leistung diese Größe auf einen Wert fest, der groß genug ist, um erneute Zuordnungen zu verhindern

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standardwert (AFX_DISABLE_FIELD_CACHE) verwendet keine doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_ENABLE_FIELD_CACHE. Verwendet die doppelte Pufferung, und Sie müssen keine zusätzlichen Schritte durchführen, um die Felder "Dirty" oder "Null" zu markieren. Vermeiden Sie aus Leistungs-und Arbeitsspeicher Gründen diesen Wert, es sei denn, die Binärdaten sind relativ klein.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

`DFX_LongBinary` wird aus Gründen der Kompatibilität mit den MFC-ODBC-Klassen bereitgestellt. Die- `DFX_LongBinary` Funktion überträgt binäre Large-Object (BLOB)-Daten mithilfe der-Klasse `CLongBinary` zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle. Daten werden zwischen dem Typ DAO_BYTES in DAO und dem Typ " [CLongBinary](clongbinary-class.md) " im Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_short"></a><a name="dfx_short"></a> DFX_Short

Überträgt kurze ganzzahlige Daten zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`short`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen `SetFieldDirty` und `SetFieldNull` selbst anrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_I2 in DAO und **`short`** dem Recordset zugeordnet.

> [!NOTE]
> `DFX_Short` entspricht [RFX_Int](#rfx_int) für die ODBC-basierten Klassen.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_single"></a><a name="dfx_single"></a> DFX_Single

Überträgt Gleit Komma Daten zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

### <a name="syntax"></a>Syntax

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parameter

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset an eine Datenquelle wird der Wert des Typs **`float`** aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen `SetFieldDirty` und `SetFieldNull` selbst anrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_R4 in DAO und **`float`** dem Recordset zugeordnet.

### <a name="example"></a>Beispiel

Siehe [DFX_Text](#dfx_text).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="dfx_text"></a><a name="dfx_text"></a> DFX_Text

Überträgt `CString` Daten zwischen den Felddatenmembern eines [CDaoRecordset](cdaorecordset-class.md) -Objekts und den Spalten eines Datensatzes in der Datenquelle.

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

*PFX*<br/>
Ein Zeiger auf ein Objekt der Klasse [CDaoFieldExchange](cdaofieldexchange-class.md). Dieses Objekt enthält Informationen, um den Kontext für die einzelnen Aufrufe der Funktion zu definieren.

*szName*<br/>
Der Name einer Datenspalte.

*value*<br/>
Der im angegebener Datenmember gespeicherte Wert – der Wert, der übertragen werden soll. Bei einer Übertragung von Recordset in die Datenquelle wird der Wert des Typs [CString](../../atl-mfc-shared/reference/cstringt-class.md)aus dem angegebenen Datenmember entnommen. Bei einer Übertragung von einer Datenquelle zu einem Recordset wird der Wert im angegebenen Datenmember gespeichert.

*nprezuzugröße*<br/>
Das Framework ordnet diese Menge an Arbeitsspeicher zu. Wenn Ihre Daten größer sind, weist das Framework nach Bedarf mehr Speicherplatz zu. Legen Sie für eine bessere Leistung diese Größe auf einen Wert fest, der groß genug ist, um erneute Zuordnungen zu verhindern

*dwBindOptions*<br/>
Eine Option, mit der Sie den doppelten Puffer Puffer Mechanismus von MFC zum Erkennen von Recordsetfeldern nutzen können, die geändert wurden. Der Standard AFX_DAO_ENABLE_FIELD_CACHE verwendet die doppelte Pufferung. Der andere mögliche Wert ist AFX_DAO_DISABLE_FIELD_CACHE. Wenn Sie diesen Wert angeben, überprüft MFC dieses Feld nicht. Sie müssen [SetFieldDirty](cdaorecordset-class.md#setfielddirty) und [SetFieldNull](cdaorecordset-class.md#setfieldnull) selbst aufrufen.

> [!NOTE]
> Sie können steuern, ob die Datenstandard mäßig durch Festlegen von [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)gepuffert werden.

### <a name="remarks"></a>Bemerkungen

Daten werden zwischen dem Typ DAO_CHAR in DAO zugeordnet (oder, wenn das Symbol _UNICODE definiert ist, DAO_WCHAR), und geben [CString](../../atl-mfc-shared/reference/cstringt-class.md) in das Recordset ein.  n

### <a name="example"></a>Beispiel

In diesem Beispiel werden mehrere Aufrufe von gezeigt `DFX_Text` . Beachten Sie auch die beiden Aufrufe von [CDaoFieldExchange:: SetFieldType](cdaofieldexchange-class.md#setfieldtype). Sie müssen den ersten `SetFieldType` -und den **DFX** -Aufrufvorgang schreiben. Der zweite Aufruf und die zugehörigen **DFX** -Aufrufe werden normalerweise vom Code-Assistenten geschrieben, der die-Klasse generiert hat.

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

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[CRecordset::D ofieldexchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::D obulkfieldexchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::D ofieldexchange](cdaorecordset-class.md#dofieldexchange)
