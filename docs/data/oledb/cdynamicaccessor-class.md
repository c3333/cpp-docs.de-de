---
title: CDynamicAccessor-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
ms.openlocfilehash: 6182d66b49647758bf17ab160d536e39b97b8c0f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216478"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor-Klasse

Ermöglicht den Zugriff auf eine Datenquelle, wenn Sie das Datenbankschema (die zugrunde liegende Struktur der Datenbank) nicht kennen.

## <a name="syntax"></a>Syntax

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: atldbcli. h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[AddBindEntry](#addbindentry)|Fügt beim Überschreiben des Standard Accessors dem Ausgabespalten einen Bindungs Eintrag hinzu.|
|[CDynamicAccessor](#cdynamicaccessor)|Instanziiert und initialisiert das- `CDynamicAccessor` Objekt.|
|[Close](#close)|Hebt die Bindung aller Spalten auf, gibt den zugewiesenen Speicher frei und gibt den [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) -Schnittstellen Zeiger in der-Klasse frei.|
|[GetBlobHandling](#getblobhandling)|Ruft den Wert für die BLOB-Behandlung der aktuellen Zeile ab.|
|[GetBlobSizeLimit](#getblobsizelimit)|Ruft die maximale BLOB-Größe in Bytes ab.|
|[GetBookmark](#getbookmark)|Ruft das Lesezeichen für die aktuelle Zeile ab.|
|[GetColumnCount](#getcolumncount)|Ruft die Anzahl der Spalten im Rowset ab.|
|[GetColumnFlags](#getcolumnflags)|Ruft die Spalten Eigenschaften ab.|
|[GetColumnInfo](#getcolumninfo)|Ruft die Spalten Metadaten ab.|
|[GetColumnName](#getcolumnname)|Ruft den Namen einer angegebenen Spalte ab.|
|[GetColumnType](#getcolumntype)|Ruft den Datentyp einer angegebenen Spalte ab.|
|[GetLength](#getlength)|Ruft die maximal mögliche Länge einer Spalte in Bytes ab.|
|[GetOrdinal](#getordinal)|Ruft den Spalten Index mit einem angegebenen Spaltennamen ab.|
|[GetStatus](#getstatus)|Ruft den Status einer angegebenen Spalte ab.|
|[GetValue](#getvalue)|Ruft die Daten aus dem Puffer ab.|
|[SetBlobHandling](#setblobhandling)|Legt den Wert für die BLOB-Behandlung für die aktuelle Zeile fest.|
|[SetBlobSizeLimit](#setblobsizelimit)|Legt die maximale BLOB-Größe in Bytes fest.|
|[SetLength](#setlength)|Legt die Länge der Spalte in Bytes fest.|
|[SetStatus](#setstatus)|Legt den Status einer angegebenen Spalte fest.|
|[SetValue](#setvalue)|Speichert die Daten im Puffer.|

## <a name="remarks"></a>Bemerkungen

Verwenden `CDynamicAccessor` Sie Methoden zum Abrufen von Spalten Informationen, wie z. b. Spaltennamen, Spalten Anzahl, Datentyp usw. Anschließend verwenden Sie diese Spalten Informationen, um einen Accessor dynamisch zur Laufzeit zu erstellen.

Die Spalten Informationen werden in einem Puffer gespeichert, der von dieser Klasse erstellt und verwaltet wird. Abrufen von Daten aus dem Puffer mithilfe von [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).

Eine Erläuterung und Beispiele für die Verwendung der dynamischen [Accessorklassen finden Sie unter Verwenden dynamischer Accessoren](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicaccessoraddbindentry"></a><a name="addbindentry"></a>CDynamicAccessor:: AddBindEntry

Fügt den Ausgabespalten einen Bindungs Eintrag hinzu.

### <a name="syntax"></a>Syntax

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Parameter

*Opo*<br/>
in Eine-Struktur, die `DBCOLUMNINFO` Spalten Informationen enthält. Siehe "DBCOLUMNINFO-Strukturen" in [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, wenn Sie den mit erstellten Standard Accessor überschreiben `CDynamicAccessor` (siehe Gewusst [wie: Abrufen von Daten](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessorcdynamicaccessor"></a><a name="cdynamicaccessor"></a>CDynamicAccessor:: CDynamicAccessor

Instanziiert und initialisiert das- `CDynamicAccessor` Objekt.

### <a name="syntax"></a>Syntax

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Parameter

*eblobhandling*<br/>
Gibt an, wie die Binary Large Object (BLOB)-Daten behandelt werden sollen. Der Standardwert ist DBBLOBHANDLING_DEFAULT. Unter [setblobhandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) finden Sie eine Beschreibung der dbblobhandlingenum-Werte.

*nblobsize*<br/>
Die maximale BLOB-Größe in Bytes. Spaltendaten über diesen Wert werden als BLOB behandelt. Der Standardwert ist 8.000. Weitere Informationen finden Sie unter [setblobsizelimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) .

### <a name="remarks"></a>Bemerkungen

Wenn Sie den-Konstruktor verwenden, um das Objekt zu initialisieren `CDynamicAccessor` , können Sie angeben, wie blobobjekte gebunden werden. BLOB können binäre Daten enthalten, z. b. Grafiken, Sound oder kompilierten Code. Standardmäßig werden Spalten mit mehr als 8.000 Bytes als blobwerte behandelt, und es wird versucht, Sie an ein Objekt zu binden `ISequentialStream` . Sie können jedoch einen anderen Wert als die BLOB-Größe angeben.

Sie können auch angeben, wie `CDynamicAccessor` Spaltendaten behandelt werden sollen, die sich als BLOB-Daten qualifizieren: Sie können BLOB-Daten auf die Standard Weise verarbeiten. Sie können BLOB-Daten überspringen (nicht binden), oder Sie können BLOB-Daten im vom Anbieter zugewiesenen Speicher binden.

## <a name="cdynamicaccessorclose"></a><a name="close"></a>CDynamicAccessor:: Close

Hebt die Bindung aller Spalten auf, gibt den zugewiesenen Speicher frei und gibt den [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) -Schnittstellen Zeiger in der-Klasse frei.

### <a name="syntax"></a>Syntax

```cpp
void Close() throw();
```

## <a name="cdynamicaccessorgetblobhandling"></a><a name="getblobhandling"></a>CDynamicAccessor:: getblobhandling

Ruft den Wert für die BLOB-Behandlung der aktuellen Zeile ab.

### <a name="syntax"></a>Syntax

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt den von [setblobhandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)festgelegten BLOB-Behandlungs Wert *eblobhandling* zurück.

## <a name="cdynamicaccessorgetblobsizelimit"></a><a name="getblobsizelimit"></a>CDynamicAccessor:: getblobsizelimit

Ruft die maximale BLOB-Größe in Bytes ab.

### <a name="syntax"></a>Syntax

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Bemerkungen

Gibt den von [setblobsizelimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)festgelegten BLOB-Behandlungs Wert *nblobsize* zurück.

## <a name="cdynamicaccessorgetbookmark"></a><a name="getbookmark"></a>CDynamicAccessor:: GetBookmark

Ruft das Lesezeichen für die aktuelle Zeile ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Parameter

*pBookmark*<br/>
vorgenommen Ein Zeiger auf das [CBookmark](../../data/oledb/cbookmark-class.md) -Objekt.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Zum `DBPROP_IRowsetLocate` Abrufen eines Lesezeichens müssen Sie auf VARIANT_TRUE festlegen.

## <a name="cdynamicaccessorgetcolumncount"></a><a name="getcolumncount"></a>CDynamicAccessor:: GetColumnCount

Ruft die Anzahl der Spalten ab.

### <a name="syntax"></a>Syntax

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der abgerufenen Spalten.

## <a name="cdynamicaccessorgetcolumnflags"></a><a name="getcolumnflags"></a>CDynamicAccessor:: getcolumnflags

Ruft die Spalten Eigenschaften ab.

### <a name="syntax"></a>Syntax

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

*pflags*<br/>
vorgenommen Ein Zeiger auf eine Bitmaske, die Spalten Eigenschaften beschreibt. Siehe "DBCOLUMNFLAGS-Enumerationstyp" in [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) in der *OLE DB Programmierer-Referenz*.

### <a name="return-value"></a>Rückgabewert

Gibt zurück, **`true`** Wenn die Spalten Eigenschaften erfolgreich abgerufen werden. Andernfalls wird zurückgegeben **`false`** .

### <a name="remarks"></a>Bemerkungen

Die Spaltennummer ist von eins versetzt. Die Spalte 0 (null) ist ein Sonderfall. Es ist das Lesezeichen, wenn es verfügbar ist.

## <a name="cdynamicaccessorgetcolumninfo"></a><a name="getcolumninfo"></a>CDynamicAccessor:: GetColumnInfo

Gibt die von den meisten Consumern benötigten Spaltenmetadaten zurück.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Parameter

*prowset*<br/>
in Ein Zeiger auf die [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) -Schnittstelle.

*pcolumns*<br/>
vorgenommen Ein Zeiger auf den Arbeitsspeicher, in den die Anzahl der Spalten im Rowset zurückgegeben werden soll. Diese Zahl schließt die Lesezeichen Spalte ein, sofern vorhanden.

*ppcolumninfo*<br/>
vorgenommen Ein Zeiger auf den Arbeitsspeicher, in den ein Array von-Strukturen zurückgegeben werden soll `DBCOLUMNINFO` . Siehe "DBCOLUMNINFO-Strukturen" in [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) in der *OLE DB Programmierer-Referenz*.

*ppStringsBuffer*<br/>
vorgenommen Ein Zeiger auf den Arbeitsspeicher, in dem ein Zeiger auf den Speicher für alle Zeichen folgen Werte (Namen, die entweder innerhalb von *ColumnID* oder für *pwszName*verwendet werden) in einem einzelnen Zuordnungs Block zurückgegeben werden.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Informationen zu den Datentypen, und finden Sie unter [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) in der *OLE DB Programmierer-Referenz* `DBORDINAL` `DBCOLUMNINFO` `OLECHAR` .

## <a name="cdynamicaccessorgetcolumnname"></a><a name="getcolumnname"></a>CDynamicAccessor:: GetColumnName

Ruft den Namen der angegebenen Spalte ab.

### <a name="syntax"></a>Syntax

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

### <a name="return-value"></a>Rückgabewert

Der Name der angegebenen Spalte.

## <a name="cdynamicaccessorgetcolumntype"></a><a name="getcolumntype"></a>CDynamicAccessor:: GetColumnType

Ruft den Datentyp einer angegebenen Spalte ab.

### <a name="syntax"></a>Syntax

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

*pType*<br/>
vorgenommen Ein Zeiger auf den Datentyp der angegebenen Spalte.

### <a name="return-value"></a>Rückgabewert

Gibt **`true`** bei Erfolg oder **`false`** bei Fehler zurück.

## <a name="cdynamicaccessorgetlength"></a><a name="getlength"></a>CDynamicAccessor:: GetLength

Ruft die Länge der angegebenen Spalte ab.

### <a name="syntax"></a>Syntax

```cpp
bool GetLength(DBORDINAL nColumn,
   DBLENGTH* pLength) const throw();

bool GetLength(const CHAR* pColumnName,
   DBLENGTH* pLength) const throw();

bool GetLength(const WCHAR* pColumnName,
   DBLENGTH* pLength) const throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

*pcolumnname*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Spaltennamen enthält.

*pLength*<br/>
vorgenommen Ein Zeiger auf die ganze Zahl, die die Länge der Spalte in Bytes enthält.

### <a name="return-value"></a>Rückgabewert

Gibt zurück, **`true`** Wenn die angegebene Spalte gefunden wurde. Andernfalls gibt diese Funktion zurück **`false`** .

### <a name="remarks"></a>Bemerkungen

Die erste außer Kraft Setzung nimmt die Spaltennummer an, und die zweite und Dritte über schreibungen nehmen den Spaltennamen im ANSI-bzw. Unicode-Format.

## <a name="cdynamicaccessorgetordinal"></a><a name="getordinal"></a>CDynamicAccessor:: getor

Ruft die Spaltennummer ab, wenn ein Spaltenname angegeben ist.

### <a name="syntax"></a>Syntax

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>Parameter

*pcolumnname*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Spaltennamen enthält.

*portieren*<br/>
vorgenommen Ein Zeiger auf die Spaltennummer.

### <a name="return-value"></a>Rückgabewert

Gibt zurück, **`true`** Wenn eine Spalte mit dem angegebenen Namen gefunden wird. Andernfalls gibt diese Funktion zurück **`false`** .

## <a name="cdynamicaccessorgetstatus"></a><a name="getstatus"></a>CDynamicAccessor:: GetStatus

Ruft den Status der angegebenen Spalte ab.

### <a name="syntax"></a>Syntax

```cpp
bool GetStatus(DBORDINAL nColumn,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const CHAR* pColumnName,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const WCHAR* pColumnName,
   DBSTATUS* pStatus) const throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

*pcolumnname*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Spaltennamen enthält.

*pstatus*<br/>
vorgenommen Ein Zeiger auf die Variable, die den Spalten Status enthält. Weitere Informationen finden Sie unter [DBStatus](/previous-versions/windows/desktop/ms722617(v=vs.85)) in der *OLE DB Programmierer-Referenz* .

### <a name="return-value"></a>Rückgabewert

Gibt zurück, **`true`** Wenn die angegebene Spalte gefunden wurde. Andernfalls gibt diese Funktion zurück **`false`** .

## <a name="cdynamicaccessorgetvalue"></a><a name="getvalue"></a>CDynamicAccessor:: GetValue

Ruft die Daten für eine angegebene Spalte ab.

### <a name="syntax"></a>Syntax

```cpp
void* GetValue(DBORDINAL nColumn) const throw();

void* GetValue(const CHAR* pColumnName) const throw();

void* GetValue(const WCHAR* pColumnName) const throw();

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();

template < class ctype >
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();

template < class ctype >
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();
```

#### <a name="parameters"></a>Parameter

*ctype*<br/>
in Ein Vorlagen Parameter, der jeden Datentyp außer Zeichen folgen Typen ( `CHAR*` , `WCHAR*` ) behandelt, die eine besondere Behandlung erfordern. `GetValue`verwendet den entsprechenden Datentyp basierend auf den hier angegebenen Angaben.

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

*pcolumnname*<br/>
in Der Spaltenname.

*pData*<br/>
vorgenommen Der Zeiger auf den Inhalt der angegebenen Spalte.

### <a name="return-value"></a>Rückgabewert

Wenn Sie Zeichen folgen Daten übergeben möchten, verwenden Sie die nicht Vorlagen basierten Versionen von `GetValue` . Die nicht auf Vorlagen basierenden Versionen dieser Methode geben zurück **`void*`** , die auf den Teil des Puffers verweist, der die angegebenen Spaltendaten enthält. Gibt NULL zurück, wenn die Spalte nicht gefunden wurde.

Für alle anderen Datentypen ist es einfacher, die Vorlagen basierten Versionen von zu verwenden `GetValue` . Die Vorlagen Versionen geben **`true`** bei Erfolg oder **`false`** bei Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die Versionen nicht Vorlagen, um Spalten zurückzugeben, die Zeichen folgen und die Vorlagen Versionen für Spalten enthalten, die andere Datentypen enthalten.

Im Debugmodus erhalten Sie eine-Erklärung, wenn die Größe von *pData* ungleich der Größe der Spalte ist, auf die Sie verweist.

## <a name="cdynamicaccessorsetblobhandling"></a><a name="setblobhandling"></a>CDynamicAccessor:: setblobhandling

Legt den Wert für die BLOB-Behandlung für die aktuelle Zeile fest.

### <a name="syntax"></a>Syntax

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Parameter

*eblobhandling*<br/>
Gibt an, wie die BLOB-Daten verarbeitet werden sollen. Die folgenden Werte sind möglich:

- DBBLOBHANDLING_DEFAULT: Verarbeiten von Spaltendaten, die größer als *nblobsize* (wie durch festgelegt) sind, `SetBlobSizeLimit` als BLOB-Daten und durch das- `ISequentialStream` Objekt oder- `IStream` Objekt Mit dieser Option wird versucht, jede Spalte zu binden, die Daten enthält, die größer als *nblobsize* sind oder als DBTYPE_IUNKNOWN als BLOB-Daten aufgeführt sind.

- DBBLOBHANDLING_NOSTREAMS: Verarbeiten von Spaltendaten, die größer als *nblobsize* (wie von festgelegt `SetBlobSizeLimit` ) sind, als BLOB-Daten, und rufen Sie Sie durch einen Verweis in einem vom Anbieter zugewiesenen, consumereigenen Speicher ab. Diese Option eignet sich für Tabellen mit mehr als einer BLOB-Spalte, und der Anbieter unterstützt nur ein `ISequentialStream` Objekt pro Accessor.

- DBBLOBHANDLING_SKIP: überspringen (keine Bindung) Spalten, die als enthaltende blobzeichen qualifiziert sind (der-Accessor bindet oder Ruft den Spaltenwert nicht ab, sondern ruft weiterhin den Spalten Status und die-Länge ab).

### <a name="remarks"></a>Bemerkungen

Sie sollten `SetBlobHandling` vor `Open` aufrufen.

Die Konstruktormethode [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) legt den Wert für die BLOB-Behandlung auf DBBLOBHANDLING_DEFAULT fest.

## <a name="cdynamicaccessorsetblobsizelimit"></a><a name="setblobsizelimit"></a>CDynamicAccessor:: setblobsizelimit

Legt die maximale BLOB-Größe in Bytes fest.

### <a name="syntax"></a>Syntax

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Parameter

*nblobsize*<br/>
Gibt die Größenbeschränkung für das BLOB an.

### <a name="remarks"></a>Bemerkungen

Legt die maximale BLOB-Größe in Bytes fest. Spaltendaten, die größer als dieser Wert sind, werden als BLOB behandelt. Einige Anbieter verfügen über extrem große Größen für Spalten (z. b. 2 GB). Anstatt zu versuchen, Arbeitsspeicher für eine Spalte mit dieser Größe zuzuweisen, würden Sie in der Regel versuchen, diese Spalten als blobspeicher zu binden. Auf diese Weise müssen Sie nicht den gesamten Arbeitsspeicher zuordnen, aber Sie können trotzdem alle Daten lesen, ohne dass die Daten abgeschnitten werden müssen. Es gibt jedoch einige Fälle, in denen Sie erzwingen können, dass `CDynamicAccessor` große Spalten in ihren systemeigenen Datentypen gebunden werden. Rufen Sie dazu auf, `SetBlobSizeLimit` bevor Sie aufrufen `Open` .

Die Konstruktormethode [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) legt die maximale BLOB-Größe auf einen Standardwert von 8.000 Bytes fest.

## <a name="cdynamicaccessorsetlength"></a><a name="setlength"></a>CDynamicAccessor:: SetLength

Legt die Länge der angegebenen Spalte fest.

### <a name="syntax"></a>Syntax

```cpp
bool SetLength(DBORDINAL nColumn,
   DBLENGTH nLength)throw();

bool SetLength(const CHAR* pColumnName,
   DBLENGTH nLength) throw();

bool SetLength(const WCHAR* pColumnName,
   DBLENGTH nLength) throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

*nlength*<br/>
in Die Länge der Spalte in Bytes.

*pcolumnname*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Spaltennamen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt zurück, **`true`** Wenn die angegebene Spaltenlänge erfolgreich festgelegt wurde. Andernfalls gibt diese Funktion zurück **`false`** .

## <a name="cdynamicaccessorsetstatus"></a><a name="setstatus"></a>CDynamicAccessor:: SetStatus

Legt den Status der angegebenen Spalte fest.

### <a name="syntax"></a>Syntax

```cpp
bool SetStatus(DBORDINAL nColumn,
   DBSTATUS status)throw();

bool SetStatus(const CHAR* pColumnName,
   DBSTATUS status) throw();

bool SetStatus(const WCHAR* pColumnName,
   DBSTATUS status) throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

*status*<br/>
in Der Spalten Status. Weitere Informationen finden Sie unter [DBStatus](/previous-versions/windows/desktop/ms722617(v=vs.85)) in der *OLE DB Programmierer-Referenz* .

*pcolumnname*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Spaltennamen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt zurück, **`true`** Wenn der angegebene Spalten Status erfolgreich festgelegt wurde. Andernfalls gibt diese Funktion zurück **`false`** .

## <a name="cdynamicaccessorsetvalue"></a><a name="setvalue"></a>CDynamicAccessor:: SetValue

Speichert Daten für eine angegebene Spalte.

### <a name="syntax"></a>Syntax

```cpp
template <class ctype>
bool SetValue(
   DBORDINAL nColumn,
   constctype& data) throw( );

template <class ctype>
bool SetValue(
   const CHAR * pColumnName,
   const ctype& data) throw( );

template <class ctype>
bool SetValue(
   const WCHAR *pColumnName,
   const ctype& data) throw( );
```

#### <a name="parameters"></a>Parameter

*ctype*<br/>
in Ein Vorlagen Parameter, der jeden Datentyp außer Zeichen folgen Typen ( `CHAR*` , `WCHAR*` ) behandelt, die eine besondere Behandlung erfordern. `GetValue`verwendet den entsprechenden Datentyp basierend auf den hier angegebenen Angaben.

*pcolumnname*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Spaltennamen enthält.

*data*<br/>
in Der Zeiger auf den Arbeitsspeicher, der die Daten enthält.

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

### <a name="return-value"></a>Rückgabewert

Wenn Sie Zeichen folgen Daten festlegen möchten, verwenden Sie die nicht Vorlagen basierten Versionen von `GetValue` . Die nicht auf Vorlagen basierenden Versionen dieser Methode geben zurück **`void*`** , die auf den Teil des Puffers verweist, der die angegebenen Spaltendaten enthält. Gibt NULL zurück, wenn die Spalte nicht gefunden wurde.

Für alle anderen Datentypen ist es einfacher, die Vorlagen basierten Versionen von zu verwenden `GetValue` . Die Vorlagen Versionen geben **`true`** bei Erfolg oder **`false`** bei Fehler zurück.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor-Klasse](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor-Klasse](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor-Klasse](../../data/oledb/cmanualaccessor-class.md)
