---
title: CMapStringToOb Class
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: b56e9052533269ba62d248312f07ac16db71bf4a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876373"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb Class

Eine Wörterbuchauflistungsklasse, die eindeutige `CString` -Objekte und `CObject` -Zeiger einander zuordnet.

## <a name="syntax"></a>Syntax

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapstringderob:: cmapstringdeob](#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapstringchanob:: GetCount](#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapstringthob:: gethashtablesize](#gethashtablesize)|Bestimmt die aktuelle Anzahl der Elemente in der Hash Tabelle.|
|[Cmapstringtob:: GetNextAssoc](#getnextassoc)|Ruft das nächste Element für die Iteration ab.|
|[Cmapstringgetob:: GetSize](#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapstringstarob:: GetStartPosition](#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[Cmapstringtoob:: hashkey](#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[Cmapstringthob:: inithashtable](#inithashtable)|Initialisiert die Hash Tabelle.|
|[Cmapstringdeob:: IsEmpty](#isempty)|Testet auf die leere Zuordnungs Bedingung (keine Elemente).|
|[Cmapstringyob:: Lookup](#lookup)|Sucht einen void-Zeiger auf der Grundlage der void-Zeiger Taste. Der Zeiger Wert, nicht die Entität, auf die er verweist, wird für den Schlüssel Vergleich verwendet.|
|[Cmapstringtoob:: lookupkey](#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[Cmapstringdeob:: RemoveAll](#removeall)|Entfernt alle Elemente aus dieser Zuordnung.|
|[Cmapstringtoob:: removekey](#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[Cmapstringto ob::](#setat)|Fügt ein Element in die Zuordnung ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapstringto ob:: Operator \[ \]](#operator_at)|Fügt ein Element in die Map –-Operator Ersetzung für `SetAt`ein.|

## <a name="remarks"></a>Bemerkungen

Nachdem Sie eine `CString`- `CObject*` Pair (-Element) in die Zuordnung eingefügt haben, können Sie das Paar effizient abrufen oder löschen, indem Sie eine Zeichenfolge oder einen `CString` Wert als Schlüssel verwenden. Sie können auch alle Elemente in der Zuordnung durchlaufen.

Eine Variable des Typs Position wird für den alternativen Zugriffs Zugriff in allen Karten Variationen verwendet. Sie können eine Position verwenden, um einen Eintrag zu speichern und die Zuordnung zu durchlaufen. Sie denken möglicherweise, dass diese Iterations nach Schlüsselwert sequenziell ist. Es ist nicht. Die Sequenz der abgerufenen Elemente ist unbestimmt.

`CMapStringToOb` enthält das `IMPLEMENT_SERIAL`-Makro, um die Serialisierung und das Absichern der zugehörigen Elemente zu unterstützen. Jedes Element wird wiederum serialisiert, wenn eine Karte in einem Archiv gespeichert wird, entweder mit dem überladenen Einfügungs Operator ( **<<** ) oder mit der `Serialize` Member-Funktion.

Wenn Sie ein Diagnose Abbild der einzelnen Elemente in der Zuordnung benötigen (der `CString`-Wert und der `CObject` Inhalt), müssen Sie die Tiefe des Sicherungs Kontexts auf 1 oder höher festlegen.

Wenn ein `CMapStringToOb` Objekt gelöscht wird oder wenn seine Elemente entfernt werden, werden die `CString` Objekte und die `CObject` Zeiger entfernt. Die Objekte, auf die durch die `CObject` Zeiger verwiesen wird, werden nicht zerstört.

Die Zuordnung der Karten Klasse ähnelt der Listen Ableitung. Im Artikel [Sammlungen](../../mfc/collections.md) finden Sie eine Abbildung der Ableitung einer speziellen Listen Klasse.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

##  <a name="cmapstringtoob"></a>Cmapstringderob:: cmapstringdeob

Erstellt eine leere `CString`-`CObject*`-Zuordnung.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parameter

*nblocksize*<br/>
Gibt die Speicher Belegungs Granularität für die Erweiterung der Zuordnung an.

### <a name="remarks"></a>Bemerkungen

Wenn die Zuordnung zunimmt, wird der Arbeitsspeicher in Einheiten von *nblocksize* -Einträgen zugeordnet.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb:: CMapStringToOb`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**Cmapptrworword (INT_PTR** `nBlockSize` **= 10);**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**Cmapstringtoptr (INT_PTR** `nBlockSize` **= 10);**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**Cmapstringdestring (INT_PTR** `nBlockSize` **= 10);**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**Cmapwordto ob (INT_PTR** `nBlockSize` **= 10);**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**Mapwordtoptr (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Eine Auflistung der `CAge`-Klasse, die in allen Sammlungs Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

##  <a name="getcount"></a>Cmapstringchanob:: GetCount

Bestimmt, wie viele Elemente in der Karte sind.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in dieser Karte.

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::GetCount`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount () Konstanten;**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount () Konstanten;**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount () Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount () Konstanten;**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount () Konstanten;**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount () Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen Sammlungs Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>Cmapstringthob:: gethashtablesize

Bestimmt die aktuelle Anzahl der Elemente in der Hash Tabelle.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente in der Hash Tabelle zurück.

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::GetHashTableSize`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Uint gethashtablesize () Konstanten;**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**Uint gethashtablesize () Konstanten;**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**Uint gethashtablesize () Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**Uint gethashtablesize () Konstanten;**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**Uint gethashtablesize () Konstanten;**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**Uint gethashtablesize () Konstanten;**|

##  <a name="getnextassoc"></a>Cmapstringtob:: GetNextAssoc

Ruft das MAP-Element bei *rnextposition*ab und aktualisiert dann *rnextposition* , um auf das nächste Element in der Zuordnung zu verweisen.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parameter

*rnextposition*<br/>
Gibt einen Verweis auf einen Positionswert an, der von einem vorherigen `GetNextAssoc` oder `GetStartPosition`-Befehl zurückgegeben wurde.

*rKey*<br/>
Gibt den zurückgegebenen Schlüssel des abgerufenen Elements an (eine Zeichenfolge).

*rValue*<br/>
Gibt den zurückgegebenen Wert des abgerufenen Elements an (ein `CObject` Zeiger). Weitere Informationen zu diesem Parameter finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist besonders nützlich für das Durchlaufen aller Elemente in der Zuordnung. Beachten Sie, dass die Positions Sequenz nicht notwendigerweise mit der Schlüsselwert Sequenz identisch ist.

Wenn das abgerufene Element das letzte in der Zuordnung ist, wird der neue Wert von *rnextposition* auf NULL festgelegt.

Stellen Sie für den *Rvalue* -Parameter sicher, dass Sie Ihren Objekttyp in **CObject\*&** umwandeln, was der Compiler erfordert, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

Dies gilt nicht für `GetNextAssoc` für Karten, die auf Vorlagen basieren.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::GetNextAssoc`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (Position &** *rnextposition* **, void\*&** *rKey* **, void\*&** *Rvalue* **) Konstanten;**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (Position &** *rnextposition* **, void\*&** *rKey* **, Word &** *Rvalue* **) Konstanten;**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (Position &** *rnextposition* **, CString &** *rKey* **, void\*&** *Rvalue* **) Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (Position &** *rnextposition* **, CString &** *rKey* **, CString &** *Rvalue* **) Konstanten;**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (Position &** *rnextposition* **, Word &** *rKey* **, CObject\*&** *Rvalue* **) Konstanten;**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (Position &** *rnextposition* **, Word &** *rKey* **, void\*&** *Rvalue* **) Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen Sammlungs Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>Cmapstringgetob:: GetSize

Gibt die Anzahl der Kartenelemente zurück.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Zuordnung.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Zuordnung abzurufen.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::GetSize`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize () Konstanten;**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize () Konstanten;**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize () Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize () Konstanten;**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize () Konstanten;**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize () Konstanten;**|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>Cmapstringstarob:: GetStartPosition

Startet eine Karten iterierung, indem ein Positionswert zurückgegeben wird, der an einen `GetNextAssoc`-Befehl übermittelt werden kann.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der eine Anfangs Position zum Durchlaufen der Zuordnung angibt. oder NULL, wenn die Zuordnung leer ist.

### <a name="remarks"></a>Bemerkungen

Die Iterations Sequenz ist nicht vorhersagbar. Daher hat das "erste Element in der Zuordnung" keine besondere Bedeutung.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::GetStartPosition`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Position GetStartPosition () Konstanten;**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**Position GetStartPosition () Konstanten;**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**Position GetStartPosition () Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**Position GetStartPosition () Konstanten;**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**Position GetStartPosition () Konstanten;**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**Position GetStartPosition () Konstanten;**|

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [cmapstringtob:: GetNextAssoc](#getnextassoc).

##  <a name="hashkey"></a>Cmapstringtoob:: hashkey

Berechnet den Hashwert eines angegebenen Schlüssels.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel, dessen Hashwert berechnet werden soll.

### <a name="return-value"></a>Rückgabewert

Der Hashwert des Schlüssels.

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::HashKey`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Uint-hashkey (void** <strong>\*</strong> `key` **) Konstanten;**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**Uint-hashkey (void** <strong>\*</strong> `key` **) Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**Uint-hashkey (LPCTSTR** `key` **) Konstanten;**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**Uint-hashkey (LPCTSTR** `key` **) Konstanten;**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**Uint-hashkey (Word** `key` **) Konstanten;**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**Uint-hashkey (Word** `key` **) Konstanten;**|

##  <a name="inithashtable"></a>Cmapstringthob:: inithashtable

Initialisiert die Hash Tabelle.

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Parameter

*HashSize*<br/>
Anzahl der Einträge in der Hash Tabelle.

*ballocnow*<br/>
Wenn true, wird die Hash Tabelle bei der Initialisierung zugewiesen. Andernfalls wird die Tabelle bei Bedarf zugewiesen.

### <a name="remarks"></a>Bemerkungen

Für eine optimale Leistung sollte die Hash Tabellengröße eine Primzahl sein. Um Konflikte zu minimieren, sollte die Größe ungefähr 20 Prozent größer sein als das größte erwartete DataSet.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::InitHashTable`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void inithashtable (uint** `hashSize` **, bool** `bAllocNow` **= true);**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**void inithashtable (uint** `hashSize` **, bool** `bAllocNow` **= true);**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**void inithashtable (uint** `hashSize` **, bool** `bAllocNow` **= true);**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**void inithashtable (uint** `hashSize` **, bool** `bAllocNow` **= true);**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**void inithashtable (uint** `hashSize` **, bool** `bAllocNow` **= true);**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**void inithashtable (uint** `hashSize` **, bool** `bAllocNow` **= true);**|

##  <a name="isempty"></a>Cmapstringdeob:: IsEmpty

Bestimmt, ob die Zuordnung leer ist.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn diese Zuordnung keine Elemente enthält; andernfalls 0.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [RemoveAll](#removeall).

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die **cmapstringtob:: IsEmpty**ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Bool IsEmpty () Konstanten;**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**Bool IsEmpty () Konstanten;**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool IsEmpty () Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**Bool IsEmpty () Konstanten;**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**Bool IsEmpty () Konstanten;**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**Bool IsEmpty () Konstanten;**|

##  <a name="lookup"></a>Cmapstringyob:: Lookup

Gibt einen `CObject` Zeiger auf der Grundlage eines `CString` Werts zurück.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Zeichen folgen Schlüssel an, der das Element identifiziert, das gesucht werden soll.

*rValue*<br/>
Gibt den zurückgegebenen Wert des aufsuchten Elements an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Element gefunden wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

`Lookup` verwendet einen Hash Algorithmus, um schnell das MAP-Element mit einem Schlüssel zu finden, der genau übereinstimmt (`CString` Wert).

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::LookUp`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Bool Lookup (void** <strong>\*</strong> `key` **, void\*&** `rValue` **) Konstanten;**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**Bool Lookup (void** <strong>\*</strong> `key` **, Word &** `rValue` **) Konstanten;**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool Lookup (LPCTSTR** `key` **, void\*&** `rValue` **) Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**Bool Lookup (LPCTSTR** `key` **, CString &** `rValue` **) Konstanten;**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**Bool Lookup (Word** `key` **, CObject\*&** `rValue` **) Konstanten;**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**Bool Lookup (Word** `key` **, void\*&** `rValue` **) Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen Sammlungs Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>Cmapstringtoob:: lookupkey

Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Zeichen folgen Schlüssel an, der das Element identifiziert, das gesucht werden soll.

*rKey*<br/>
Der Verweis auf den zugeordneten Schlüssel.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Schlüssel gefunden wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Verwendung eines Verweises auf einen Schlüssel ist unsicher, wenn er nach dem Entfernen des zugeordneten Elements aus der Zuordnung oder nach dem Entfernen der Zuordnung verwendet wird.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb:: LookupKey`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool lookupkey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) Konstanten;**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**Bool lookupkey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) Konstanten;**|

##  <a name="operator_at"></a>Cmapstringto ob:: Operator []

Ein bequemer Ersatz für die `SetAt` Member-Funktion.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf einen Zeiger auf ein `CObject` Objekt. oder NULL, wenn die Zuordnung leer ist oder der *Schlüssel* außerhalb des gültigen Bereichs liegt.

### <a name="remarks"></a>Bemerkungen

Daher kann Sie nur auf der linken Seite einer Zuweisungsanweisung (ein l-Wert) verwendet werden. Wenn kein MAP-Element mit dem angegebenen Schlüssel vorhanden ist, wird ein neues Element erstellt.

Es ist kein "Right Side" (r-Wert) äquivalent zu diesem Operator vorhanden, da es möglich ist, dass ein Schlüssel in der Zuordnung nicht gefunden wird. Verwenden Sie die `Lookup` Member-Funktion für das Abrufen von Elementen.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::operator []`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& Operator\[] (void \*</strong> `key` **\);**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**Word & Operator\[] (void** <strong>\*</strong> `key` **\);**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& Operator\[] (LPCTSTR** `key` **\);**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**CString-& Operator\[] (LPCTSTR** `key` **\);**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& Operator\[] (Word** `key` **\);**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& Operator\[] (Word** `key` **\);**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen Sammlungs Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>Cmapstringdeob:: RemoveAll

Entfernt alle Elemente aus dieser Zuordnung und zerstört die `CString` Schlüssel Objekte.

```
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Die `CObject` Objekte, auf die von jedem Schlüssel verwiesen wird, werden nicht zerstört. Die `RemoveAll` Funktion kann Speicher Verluste verursachen, wenn Sie nicht sicherstellen, dass die `CObject` Objekte, auf die verwiesen wird, zerstört werden.

Die Funktion funktioniert ordnungsgemäß, wenn die Zuordnung bereits leer ist.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::RemoveAll`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll ();**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll ();**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll ();**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll ();**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll ();**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen Sammlungs Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>Cmapstringtoob:: removekey

Sucht den Zuordnungs Eintrag, der dem angegebenen Schlüssel entspricht. Wenn der Schlüssel gefunden wird, wird der Eintrag von entfernt.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt die für die Kartensuche verwendete Zeichenfolge an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Eintrag gefunden und erfolgreich entfernt wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dies kann zu Speicher Verlusten führen, wenn das `CObject` Objekt nicht an anderer Stelle gelöscht wird.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::RemoveKey`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Bool removekey (void** <strong>\*</strong> `key` **);**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**Bool removekey (void** <strong>\*</strong> `key` **);**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool removekey (LPCTSTR** `key` **);**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**Bool removekey (LPCTSTR** `key` **);**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**Bool removekey (Word** `key` **);**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**Bool removekey (Word** `key` **);**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen Sammlungs Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>Cmapstringto ob::

Das primäre bedeutet, ein Element in eine Zuordnung einzufügen.

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt die Zeichenfolge an, die der Schlüssel des neuen Elements ist.

*newValue*<br/>
Gibt den `CObject` Zeiger an, bei dem es sich um den Wert des neuen Elements handelt.

### <a name="remarks"></a>Bemerkungen

Zuerst wird der Schlüssel gesucht. Wenn der Schlüssel gefunden wird, wird der entsprechende Wert geändert. Andernfalls wird ein neues Schlüssel-Wert-Element erstellt.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die `CMapStringToOb::SetAt`ähneln.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void-Aktivität (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[Cmapptrto Word](../../mfc/reference/cmapptrtoword-class.md)|**void-Aktivität (void** <strong>\*</strong> `key` **, Word** `newValue` **);**|
|[Cmapstringtoptr](../../mfc/reference/cmapstringtoptr-class.md)|**void-Aktivität (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[Cmapstringdestring](../../mfc/reference/cmapstringtostring-class.md)|**void-Aktivität (LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[Cmapworddeob](../../mfc/reference/cmapwordtoob-class.md)|**void-Aktivität (Word** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[Cmapwordtoptr](../../mfc/reference/cmapwordtoptr-class.md)|**void-Aktivität (Word** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Beispiel

Eine Auflistung der `CAge`-Klasse, die in allen Sammlungs Beispielen verwendet wird, finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr-Klasse](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord-Klasse](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr-Klasse](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString-Klasse](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb-Klasse](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr-Klasse](../../mfc/reference/cmapwordtoptr-class.md)
