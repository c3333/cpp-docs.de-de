---
title: CMFCFilterChunkValueImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
ms.openlocfilehash: c89d41f7db43d9504bfc22cbf35a59fcceb511e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752360"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl-Klasse

Dies ist eine Klasse, die sowohl die Chunk- als auch die Eigenschaftswertpaarlogik vereinfacht.

## <a name="syntax"></a>Syntax

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::'CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Zerstört das Objekt.|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Erstellt das Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Clear](#clear)|Löscht den ChunkValue.|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Kopiert diesen Chunk in eine Struktur, die die Eigenschaften eines Chunks beschreibt.|
|[CMFCFilterChunkValueImpl::KopierenVon](#copyfrom)|Initialisiert diesen Chunk-Wert aus dem anderen Wert.|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Ruft die Chunk-GUID ab.|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Ruft die Block-PID (Eigenschafts-ID) ab.|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Ruft den Chunk-Typ ab.|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Ruft den Zeichenfolgenwert ab.|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Ruft den Wert als zugeordnete Propvariante ab.|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Gibt den nicht zugewiesenen Wert (interner Wert) zurück.|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Überprüft, ob dieser Eigenschaftswert gültig ist oder nicht.|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Ist überladen. Legt die Eigenschaft nach Schlüssel auf einen booleschen Wert fest.|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Legt die Eigenschaft nach Schlüssel auf ein DWORD fest.|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Legt die Eigenschaft nach Schlüssel auf eine Dateizeit fest.|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Legt die Eigenschaft nach Schlüssel auf int64 fest.|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Legt die Eigenschaft nach Schlüssel auf einen int fest.|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Legt die Eigenschaft nach Schlüssel auf long fest.|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Legt die Eigenschaft nach Schlüssel auf eine SystemTime fest.|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Legt die Eigenschaft nach Schlüssel auf eine Unicode-Zeichenfolge fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Eine Hilfsfunktion, die die allgemeinen Eigenschaften des Chunks festlegt.|

## <a name="remarks"></a>Bemerkungen

Zur Verwendung erstellen Sie einfach eine CMFCFilterChunkValueImpl-Klasse der richtigen Art

Beispiel:

CMFCFilterChunkValueImpl-Chunk;

hr = Chunk. SetBoolValue(PKEY_IsAttachment, true);

oder

hr = Chunk. SetFileTimeValue(PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFCFilterChunkValueImpl::Clear

Löscht den ChunkValue.

```cpp
void Clear();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

Erstellt das Objekt.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::'CMFCFilterChunkValueImpl

Zerstört das Objekt.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFCFilterChunkValueImpl::CopyChunk

Kopiert diesen Chunk in eine Struktur, die die Eigenschaften eines Chunks beschreibt.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Parameter

*pStatChunk*<br/>
Ein Zeiger auf den Zielwert, der die Eigenschaften des Chunks beschreibt.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFCFilterChunkValueImpl::KopierenVon

Initialisiert diesen Chunk-Wert aus dem anderen Wert.

```cpp
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parameter

*pValue*<br/>
Gibt den Quellwert an, aus dem kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFCFilterChunkValueImpl::GetChunkGUID

Ruft die Chunk-GUID ab.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf eine GUID, die den Chunk identifiziert.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFCFilterChunkValueImpl::GetChunkPID

Ruft die Block-PID (Eigenschafts-ID) ab.

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der die Eigenschafts-ID enthält.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFCFilterChunkValueImpl::GetChunkType

Ruft den Chunk-Typ ab.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Rückgabewert

Ein CHUNKSTATE-Enumeratwert, der angibt, ob der aktuelle Chunk eine Texttypeigenschaft oder eine Werttypeigenschaft ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFCFilterChunkValueImpl::GetString

Ruft den Zeichenfolgenwert ab.

```
CString &GetString();
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die den Chunk-Wert enthält.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFCFilterChunkValueImpl::GetValue

Ruft den Wert als zugeordnete Propvariante ab.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Parameter

*ppPropVariant*<br/>
Wenn die Funktion zurückgegeben wird, enthält dieser Parameter den Chunk-Wert.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn PROPVARIANT erfolgreich zugewiesen wurde und der Chunk-Wert erfolgreich in *ppPropVariant*kopiert wurde. andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFCFilterChunkValueImpl::GetValueNoAlloc

Gibt den nicht zugewiesenen Wert (interner Wert) zurück.

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Rückgabewert

Gibt den aktuellen Chunk-Wert zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFCFilterChunkValueImpl::IsValid

Überprüft, ob dieser Eigenschaftswert gültig ist oder nicht.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der aktuelle Chunk-Wert gültig ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFCFilterChunkValueImpl::SetBoolValue

Ist überladen. Legt die Eigenschaft nach Schlüssel auf einen booleschen Wert fest.

```
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    VARIANT_BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*bVal*<br/>
Gibt den festzulegenden Chunk-Wert an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFCFilterChunkValueImpl::SetChunk

Eine Hilfsfunktion, die die allgemeinen Eigenschaften des Chunks festlegt.

```
HRESULT SetChunk(
    REFPROPERTYKEY pkey,
    CHUNKSTATE chunkType=CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFCFilterChunkValueImpl::SetDwordValue

Legen Sie die Eigenschaft nach Schlüssel auf ein DWORD fest.

```
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,
    DWORD dwVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*dwVal*<br/>
Gibt den festzulegenden Chunk-Wert an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFCFilterChunkValueImpl::SetFileTimeValue

Legen Sie die Eigenschaft nach Schlüssel auf eine Dateizeit fest.

```
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,
    FILETIME dtVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*dtVal*<br/>
Gibt den festzulegenden Chunk-Wert an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFCFilterChunkValueImpl::SetInt64Value

Legen Sie die Eigenschaft nach Schlüssel auf int64 fest.

```
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,
    __int64 nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*nVal*<br/>
Gibt den festzulegenden Chunk-Wert an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFCFilterChunkValueImpl::SetIntValue

Legen Sie die Eigenschaft nach Schlüssel auf einen int fest.

```
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,
    int nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*nVal*<br/>
Gibt den festzulegenden Chunk-Wert an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFCFilterChunkValueImpl::SetLongValue

Legen Sie die Eigenschaft nach Schlüssel auf long fest.

```
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,
    long lVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*lVal*<br/>
Gibt den festzulegenden Chunk-Wert an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFCFilterChunkValueImpl::SetSystemTimeValue

Legt die Eigenschaft nach Schlüssel auf eine SystemTime fest.

```
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,
    const SYSTEMTIME& systemTime,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*Systemtime*<br/>
Gibt den festzulegenden Chunk-Wert an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFCFilterChunkValueImpl::SetTextValue

Legt die Eigenschaft nach Schlüssel auf eine Unicode-Zeichenfolge fest.

```
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,
    LPCTSTR pszValue,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parameter

*pkey*<br/>
Gibt einen Eigenschaftsschlüssel an.

*pszValue*<br/>
Gibt den festzulegenden Chunk-Wert an.

*chunkType*<br/>
Flags geben an, ob dieser Chunk einen Texttyp oder eine Werttypeigenschaft enthält. Flagwerte werden der CHUNKSTATE-Enumeration entnommen.

*locale*<br/>
Die Sprache und Untersprache, die einem Textabschnitt zugeordnet sind. Das Blockgebietsschema wird von Dokumentindizierern verwendet, um den richtigen Wortumbruch von Text auszuführen. Wenn es sich bei dem Chunk weder um einen Texttyp noch um einen Werttyp mit Datentyp VT_LPWSTR, VT_LPSTR oder VT_BSTR handelt, wird dieses Feld ignoriert.

*cwcLenQuelle*<br/>
Die Länge in Zeichen des Quelltextes, von dem der aktuelle Chunk abgeleitet wurde. Ein Nullwert bedeutet Zeichen-für-Zeichen-Entsprechung zwischen dem Quelltext und dem abgeleiteten Text. Ein Wert ungleich Null bedeutet, dass eine solche direkte Entsprechung nicht besteht.

*cwcStartSource*<br/>
Der Offset, von dem der Quelltext für einen abgeleiteten Abschnitt im Quellabschnitt beginnt.

*chunkBreakType*<br/>
Der Typ der Unterbrechung, die den vorherigen Block vom aktuellen Block trennt. Die Werte stammen aus der CHUNK_BREAKTYPE-Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein Fehlercode.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)
