---
title: CMapStringToOb-Klasse
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
ms.openlocfilehash: 6520d1c38701647ae51450b9b9800a7cd2701b7a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754592"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb-Klasse

Eine Wörterbuchauflistungsklasse, die eindeutige `CString` -Objekte und `CObject` -Zeiger einander zuordnet.

## <a name="syntax"></a>Syntax

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cmapstringtoob::Cmapstringtoob](#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMapStringToOb::GetCount](#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapstringtoob::GetHashTableSize](#gethashtablesize)|Bestimmt die aktuelle Anzahl von Elementen in der Hashtabelle.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Ruft das nächste Element zum Iterieren ab.|
|[CMapStringToOb::GetSize](#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[Cmapstringtoob::GetStartPosition](#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[CMapStringToOb::HashKey](#hashkey)|Berechnet den Hashwert eines angegebenen Schlüssels.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Initialisiert die Hashtabelle.|
|[Cmapstringtoob::Isempty](#isempty)|Tests für die Leerzuordnungsbedingung (keine Elemente).|
|[CMapStringToOb::Lookup](#lookup)|Sucht einen leeren Zeiger basierend auf dem leeren Zeigerschlüssel. Der Zeigerwert, nicht die Entität, auf die er verweist, wird für den Schlüsselvergleich verwendet.|
|[CMapStringToOb::LookupKey](#lookupkey)|Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.|
|[CMapStringToOb::Alle entfernen](#removeall)|Entfernt alle Elemente aus dieser Karte.|
|[CMapStringToOb::RemoveKey](#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[Cmapstringtoob::Setat](#setat)|Fügt ein Element in die Karte ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMapStringToOb::operator \[\]](#operator_at)|Fügt ein Element in die Karte `SetAt`ein – Operatorersetzung für .|

## <a name="remarks"></a>Bemerkungen

Nachdem `CString` -  `CObject*` Sie ein Paar (Element) in die Karte eingefügt haben, können Sie `CString` das Paar mithilfe einer Zeichenfolge oder eines Werts als Schlüssel effizient abrufen oder löschen. Sie können auch über alle Elemente in der Karte iterieren.

Eine Variable vom Typ POSITION wird für den alternativen Eintragszugriff in allen Kartenvariationen verwendet. Sie können eine POSITION verwenden, um sich einen Eintrag zu "erinnern" und durch die Karte zu iterieren. Sie könnten denken, dass diese Iteration nach Schlüsselwert sequenziell ist; Es ist nicht. Die Reihenfolge der abgerufenen Elemente ist unbestimmt.

`CMapStringToOb`enthält das `IMPLEMENT_SERIAL` Makro, um die Serialisierung und das Dumping seiner Elemente zu unterstützen. Jedes Element wird nacheinander serialisiert, wenn eine Karte in einem **<<** Archiv gespeichert wird, entweder mit dem überladenen Einfügeoperator ( ) oder mit der `Serialize` Memberfunktion.

Wenn Sie ein Diagnose-Dump der einzelnen Elemente `CString` in `CObject` der Karte (Wert und Inhalt) benötigen, müssen Sie die Tiefe des Dumpkontexts auf 1 oder höher festlegen.

Wenn `CMapStringToOb` ein Objekt gelöscht wird oder wenn `CString` seine Elemente `CObject` entfernt werden, werden die Objekte und Zeiger entfernt. Die Objekte, auf `CObject` die von den Zeigern verwiesen wird, werden nicht zerstört.

Die Ableitung der Kartenklassen ist ähnlich wie die Listenableitung. Im Artikel [Sammlungen](../../mfc/collections.md) finden Sie eine Veranschaulichung der Ableitung einer speziellen Listenklasse.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxcoll.h

## <a name="cmapstringtoobcmapstringtoob"></a><a name="cmapstringtoob"></a>Cmapstringtoob::Cmapstringtoob

Erstellt eine `CString`leere -to-Map. `CObject*`

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Gibt die Speicherzuweisungsgranularität zum Erweitern der Karte an.

### <a name="remarks"></a>Bemerkungen

Wenn die Karte wächst, wird der Speicher in Einheiten von *nBlockSize-Einträgen* zugewiesen.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb:: CMapStringToOb`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

## <a name="cmapstringtoobgetcount"></a><a name="getcount"></a>CMapStringToOb::GetCount

Bestimmt, wie viele Elemente sich in der Karte befinden.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in dieser Karte.

### <a name="remarks"></a>Bemerkungen

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::GetCount`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

## <a name="cmapstringtoobgethashtablesize"></a><a name="gethashtablesize"></a>Cmapstringtoob::GetHashTableSize

Bestimmt die aktuelle Anzahl von Elementen in der Hashtabelle.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente in der Hashtabelle zurück.

### <a name="remarks"></a>Bemerkungen

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::GetHashTableSize`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize( ) const;**|

## <a name="cmapstringtoobgetnextassoc"></a><a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc

Ruft das Map-Element bei *rNextPosition*ab und aktualisiert *dann rNextPosition,* um auf das nächste Element in der Karte zu verweisen.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parameter

*rNextPosition*<br/>
Gibt einen Verweis auf einen POSITION-Wert an, der von einem vorherigen `GetNextAssoc` oder `GetStartPosition` Aufruf zurückgegeben wird.

*rKey*<br/>
Gibt den zurückgegebenen Schlüssel des abgerufenen Elements (eine Zeichenfolge) an.

*Rvalue*<br/>
Gibt den zurückgegebenen Wert des `CObject` abgerufenen Elements (ein Zeiger) an. Weitere Informationen zu diesem Parameter finden Sie unter Hinweise.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist besonders nützlich, um alle Elemente in der Karte zu durchlaufen. Beachten Sie, dass die Positionssequenz nicht unbedingt mit der Schlüsselwertsequenz identisch ist.

Wenn das abgerufene Element das letzte in der Karte ist, wird der neue Wert von *rNextPosition* auf NULL gesetzt.

Achten Sie für den *Parameter rValue* darauf, den Objekttyp in **\*CObject**zu umlegen, was der Compiler benötigt, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

Dies gilt `GetNextAssoc` nicht für Karten, die auf Vorlagen basieren.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::GetNextAssoc`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\* ** *rKey* **, void\* ** *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\* ** *rKey* **, WORD&** *rValue* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, void\* ** *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, CString&** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, CObject\* ** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, void\* ** *rValue* **) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

## <a name="cmapstringtoobgetsize"></a><a name="getsize"></a>CMapStringToOb::GetSize

Gibt die Anzahl der Kartenelemente zurück.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Karte.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Karte abzurufen.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::GetSize`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

## <a name="cmapstringtoobgetstartposition"></a><a name="getstartposition"></a>Cmapstringtoob::GetStartPosition

Startet eine Karteniteration, indem ein POSITION-Wert `GetNextAssoc` zurückgegeben wird, der an einen Aufruf übergeben werden kann.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der eine Startposition für die Iterierung der Karte angibt; oder NULL, wenn die Karte leer ist.

### <a name="remarks"></a>Bemerkungen

Die Iterationssequenz ist nicht vorhersagbar. Daher hat das "erste Element in der Karte" keine besondere Bedeutung.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::GetStartPosition`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition( ) const;**|

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMapStringToOb::GetNextAssoc](#getnextassoc).

## <a name="cmapstringtoobhashkey"></a><a name="hashkey"></a>CMapStringToOb::HashKey

Berechnet den Hashwert eines angegebenen Schlüssels.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel, dessen Hashwert berechnet werden soll.

### <a name="return-value"></a>Rückgabewert

Der Hashwert des Schlüssels

### <a name="remarks"></a>Bemerkungen

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::HashKey`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey( void** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey( void** <strong>\*</strong> `key` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey( WORD** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey( WORD** `key` **) const;**|

## <a name="cmapstringtoobinithashtable"></a><a name="inithashtable"></a>CMapStringToOb::InitHashTable

Initialisiert die Hashtabelle.

```cpp
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Parameter

*hashSize*<br/>
Anzahl der Einträge in der Hashtabelle.

*bAllocNow*<br/>
Wenn TRUE, ordnet die Hashtabelle bei der Initialisierung zu. Andernfalls wird die Tabelle bei Bedarf zugewiesen.

### <a name="remarks"></a>Bemerkungen

Für eine optimale Leistung sollte die Hashtabellengröße eine Primzahl sein. Um Kollisionen zu minimieren, sollte die Größe etwa 20 Prozent größer sein als der größte erwartete Datensatz.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::InitHashTable`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|

## <a name="cmapstringtoobisempty"></a><a name="isempty"></a>Cmapstringtoob::Isempty

Bestimmt, ob die Karte leer ist.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn diese Karte keine Elemente enthält; andernfalls 0.

### <a name="example"></a>Beispiel

Siehe Beispiel für [RemoveAll](#removeall).

### <a name="remarks"></a>Bemerkungen

Die folgende Tabelle zeigt andere Memberfunktionen, die **CMapStringToOb ähneln:: IsEmpty**.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty( ) const;**|

## <a name="cmapstringtooblookup"></a><a name="lookup"></a>CMapStringToOb::Lookup

Gibt `CObject` einen Zeiger basierend `CString` auf einem Wert zurück.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Zeichenfolgenschlüssel an, der das zu sanende Element identifiziert.

*Rvalue*<br/>
Gibt den zurückgegebenen Wert aus dem nachgeschlagenen Element an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element gefunden wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

`Lookup`verwendet einen Hashalgorithmus, um das Kartenelement schnell mit `CString` einem Schlüssel zu finden, der genau übereinstimmt (Wert).

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::LookUp`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Lookup( void** <strong>\*</strong> `key` **, void\* ** `rValue` ) **const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Lookup( void** <strong>\*</strong> `key` **, WORD&** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup( LPCTSTR** `key` **, void\* ** `rValue` ) **const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL Lookup( LPCTSTR** `key` **, CString&** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup( WORD** `key` **\* , CObject** `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup( WORD** `key` **, void\* ** `rValue` ) **const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

## <a name="cmapstringtooblookupkey"></a><a name="lookupkey"></a>CMapStringToOb::LookupKey

Gibt einen Verweis auf den Schlüssel zurück, der dem angegebenen Schlüsselwert zugeordnet ist.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Zeichenfolgenschlüssel an, der das zu sanende Element identifiziert.

*rKey*<br/>
Der Verweis auf den zugeordneten Schlüssel.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Schlüssel gefunden wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Verwendung eines Verweises auf einen Schlüssel ist unsicher, wenn er verwendet wird, nachdem das zugeordnete Element aus der Karte entfernt wurde oder nachdem die Karte zerstört wurde.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb:: LookupKey`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|

## <a name="cmapstringtooboperator--"></a><a name="operator_at"></a>CMapStringToOb::operator [ ]

Ein bequemer `SetAt` Ersatz für die Memberfunktion.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf einen `CObject` Zeiger auf ein Objekt; oder NULL, wenn die Karte leer ist oder der *Schlüssel* anicht zulässig ist.

### <a name="remarks"></a>Bemerkungen

Somit kann sie nur auf der linken Seite einer Zuweisungsanweisung (ein l-Wert) verwendet werden. Wenn kein Kartenelement mit dem angegebenen Schlüssel vorhanden ist, wird ein neues Element erstellt.

Es gibt keine "rechte Seite" (r-Wert) äquivalent zu diesem Operator, da es eine Möglichkeit, dass ein Schlüssel nicht in der Karte gefunden werden. Verwenden `Lookup` Sie die Memberfunktion für den Elementabruf.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::operator []`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*&\[Operator \* ](void</strong> `key` ** \);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD&\[Operator ](void** <strong>\*</strong> `key` ** \);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*&\[Operator ](lpctstr** `key` ** \);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString&\[Operator ](lpctstr** `key` ** \);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*&\[Operator ](Word** `key` ** \);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*&\[Operator ](Wort** `key` ** \);**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

## <a name="cmapstringtoobremoveall"></a><a name="removeall"></a>CMapStringToOb::Alle entfernen

Entfernt alle Elemente aus dieser Karte `CString` und zerstört die Wichtigsten objekte.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Die `CObject` Objekte, auf die von jedem Schlüssel verwiesen wird, werden nicht zerstört. Die `RemoveAll` Funktion kann Speicherverluste verursachen, wenn Sie `CObject` nicht sicherstellen, dass die referenzierten Objekte zerstört werden.

Die Funktion funktioniert korrekt, wenn die Karte bereits leer ist.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::RemoveAll`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll( );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll( );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll( );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll( );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll( );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

## <a name="cmapstringtoobremovekey"></a><a name="removekey"></a>CMapStringToOb::RemoveKey

Sucht den Karteneintrag entsprechend dem angegebenen Schlüssel; wenn der Schlüssel gefunden wird, wird der Eintrag entfernt.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt die Zeichenfolge an, die für die Kartensuche verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Eintrag gefunden und erfolgreich entfernt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dies kann zu Speicherverlusten führen, wenn das `CObject` Objekt nicht an anderer Stelle gelöscht wird.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::RemoveKey`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey( LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey( LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey( WORD** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey( WORD** `key` **);**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

## <a name="cmapstringtoobsetat"></a><a name="setat"></a>Cmapstringtoob::Setat

Das primäre Mittel zum Einfügen eines Elements in eine Karte.

```cpp
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt die Zeichenfolge an, die der Schlüssel des neuen Elements ist.

*newValue*<br/>
Gibt den `CObject` Zeiger an, der der Wert des neuen Elements ist.

### <a name="remarks"></a>Bemerkungen

Zunächst wird der Schlüssel nachgeschlagen. Wenn der Schlüssel gefunden wird, wird der entsprechende Wert geändert. Andernfalls wird ein neues Schlüssel-Wert-Element erstellt.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CMapStringToOb::SetAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt( void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt( void** <strong>\*</strong> `key` **, WORD** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt( LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt( WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt( WORD** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

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
