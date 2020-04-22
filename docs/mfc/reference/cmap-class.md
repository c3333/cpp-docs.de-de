---
title: CMap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
ms.openlocfilehash: fbb34d4db41ef11cd01a6a8a7f20cafa0e737268
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749074"
---
# <a name="cmap-class"></a>CMap-Klasse

Eine Wörterbuchauflistungsklasse, die eindeutigen Schlüsseln Werte zuordnet.

## <a name="syntax"></a>Syntax

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Parameter

*Schlüssel*<br/>
Klasse des Objekts, das als Schlüssel für die Karte verwendet wird.

*ARG_KEY*<br/>
Datentyp, der für *KEY-Argumente* verwendet wird; in der Regel ein Verweis auf *KEY*.

*Wert*<br/>
Klasse des in der Karte gespeicherten Objekts.

*ARG_VALUE*<br/>
Datentyp, der für *VALUE-Argumente* verwendet wird; in der Regel ein Verweis auf *VALUE*.

## <a name="members"></a>Member

### <a name="public-structures"></a>Öffentliche Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMap::CPair](#cpair)|Eine geschachtelte Struktur, die einen Schlüsselwert und den Wert des zugeordneten Objekts enthält.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMap::CMap](#cmap)|Erstellt eine Auflistung, die Schlüssel Werten zuordnet.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMap::GetCount](#getcount)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[CMap::GetHashTableSize](#gethashtablesize)|Gibt die Anzahl der Elemente in der Hashtabelle zurück.|
|[CMap::GetNextAssoc](#getnextassoc)|Ruft das nächste Element zum Iterieren ab.|
|[CMap::GetSize](#getsize)|Gibt die Anzahl der Elemente in dieser Karte zurück.|
|[CMap::GetStartPosition](#getstartposition)|Gibt die Position des ersten Elements zurück.|
|[CMap::InitHashTable](#inithashtable)|Initialisiert die Hashtabelle und gibt deren Größe an.|
|[CMap::IsEmpty](#isempty)|Tests für die Leerzuordnungsbedingung (keine Elemente).|
|[CMap::Lookup](#lookup)|Sucht den Wert, der einem bestimmten Schlüssel zugeordnet ist.|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Gibt einen Zeiger auf das erste Element zurück.|
|[CMap::PGetNextAssoc](#pgetnextassoc)|Ruft einen Zeiger auf das nächste Element zum Iterieren ab.|
|[CMap::PLookup](#plookup)|Gibt einen Zeiger auf einen Schlüssel zurück, dessen Wert mit dem angegebenen Wert übereinstimmt.|
|[CMap::RemoveAll](#removeall)|Entfernt alle Elemente aus dieser Karte.|
|[CMap::RemoveKey](#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[CMap::SetAt](#setat)|Fügt ein Element in die Karte ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMap::Operator \[\]](#operator_at)|Fügt ein Element in die Karte `SetAt`ein – Operatorersetzung für .|

## <a name="remarks"></a>Bemerkungen

Nachdem Sie ein Schlüssel-Wert-Paar (Element) in die Karte eingefügt haben, können Sie das Paar effizient abrufen oder löschen, indem Sie den Schlüssel verwenden, um darauf zuzugreifen. Sie können auch über alle Elemente in der Karte iterieren.

Für den alternativen Zugriff auf Einträge wird eine Variable vom Typ POSITION verwendet. Sie können eine POSITION verwenden, um sich einen Eintrag zu "erinnern" und durch die Karte zu iterieren. Sie könnten denken, dass diese Iteration nach Schlüsselwert sequenziell ist; Es ist nicht. Die Reihenfolge der abgerufenen Elemente ist unbestimmt.

Bestimmte Memberfunktionen dieser Klasse rufen globale Hilfsfunktionen auf, die `CMap` für die meisten Verwendungen der Klasse angepasst werden müssen. Siehe [Auflistungsklassenhilfsprogramme](../../mfc/reference/collection-class-helpers.md) im Abschnitt Makros und Globale dateien in der **MFC-Referenz**.

`CMap`überschreibt [CObject::Serialize,](../../mfc/reference/cobject-class.md#serialize) um die Serialisierung und das Dumping seiner Elemente zu unterstützen. Wenn eine Karte mit `Serialize`, jedes Kartenelement in einem Archiv gespeichert wird, wird es nacheinander serialisiert. Die Standardimplementierung `SerializeElements` der Hilfsfunktion führt einen bitweisen Schreibvorgang durch. Informationen zur Serialisierung von Zeigerauflistungselementen, die von `CObject` anderen benutzerdefinierten Typen abgeleitet wurden, finden Sie unter [Gewusst wie: Erstellen einer typsicheren Auflistung](../../mfc/how-to-make-a-type-safe-collection.md).

Wenn Sie ein Diagnose-Dump der einzelnen Elemente in der Karte (Schlüssel und Werte) benötigen, müssen Sie die Tiefe des Dumpkontexts auf 1 oder höher festlegen.

Wenn `CMap` ein Objekt gelöscht wird oder wenn seine Elemente entfernt werden, werden die Schlüssel und Werte beide entfernt.

Die Ableitung der Kartenklassen ist ähnlich wie die Listenableitung. Im Artikel [Sammlungen](../../mfc/collections.md) finden Sie eine Veranschaulichung der Ableitung einer speziellen Listenklasse.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a>CMap::CMap

Erstellt eine leere Karte.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Gibt die Speicherzuweisungsgranularität zum Erweitern der Karte an.

### <a name="remarks"></a>Bemerkungen

Wenn die Karte wächst, wird der Speicher in Einheiten von *nBlockSize-Einträgen* zugewiesen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a>CMap::CPair

Enthält einen Schlüsselwert und den Wert des zugeordneten Objekts.

### <a name="remarks"></a>Bemerkungen

Dies ist eine verschachtelte Struktur innerhalb der Klasse [CMap](../../mfc/reference/cmap-class.md).

Die Struktur besteht aus zwei Bereichen:

- `key`Der tatsächliche Wert des Schlüsseltyps.

- `value`Der Wert des zugeordneten Objekts.

Es wird verwendet, um die Rückgabewerte von [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc)und [CMap::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung finden Sie im Beispiel für [CMap::PLookup](#plookup).

## <a name="cmapgetcount"></a><a name="getcount"></a>CMap::GetCount

Ruft die Anzahl der Elemente in der Karte ab.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMap::Lookup](#lookup).

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a>CMap::GetHashTableSize

Bestimmt die Anzahl der Elemente in der Hashtabelle für die Karte.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Hashtabelle.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a>CMap::GetNextAssoc

Ruft das Kartenelement `rNextPosition`unter `rNextPosition` ab und aktualisiert dann, um auf das nächste Element in der Karte zu verweisen.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parameter

*rNextPosition*<br/>
Gibt einen Verweis auf einen POSITION-Wert an, der von einem vorherigen `GetNextAssoc` oder `GetStartPosition` Aufruf zurückgegeben wird.

*Schlüssel*<br/>
Vorlagenparameter, der den Typ des Kartenschlüssels angibt.

*rKey*<br/>
Gibt den zurückgegebenen Schlüssel des abgerufenen Elements an.

*Wert*<br/>
Vorlagenparameter, der den Typ des Kartenwerts angibt.

*Rvalue*<br/>
Gibt den zurückgegebenen Wert des abgerufenen Elements an.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist besonders nützlich, um alle Elemente in der Karte zu durchlaufen. Beachten Sie, dass die Positionssequenz nicht unbedingt mit der Schlüsselwertsequenz identisch ist.

Wenn das abgerufene Element das letzte in der Karte ist, wird der neue Wert von *rNextPosition* auf NULL gesetzt.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMap::SetAt](#setat).

## <a name="cmapgetsize"></a><a name="getsize"></a>CMap::GetSize

Gibt die Anzahl der Kartenelemente zurück.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Karte.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Karte abzurufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a>CMap::GetStartPosition

Startet eine Karteniteration, indem ein POSITION-Wert `GetNextAssoc` zurückgegeben wird, der an einen Aufruf übergeben werden kann.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der eine Startposition für die Iterierung der Karte angibt; oder NULL, wenn die Karte leer ist.

### <a name="remarks"></a>Bemerkungen

Die Iterationssequenz ist nicht vorhersagbar. Daher hat das "erste Element in der Karte" keine besondere Bedeutung.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMap::SetAt](#setat).

## <a name="cmapinithashtable"></a><a name="inithashtable"></a>CMap::InitHashTable

Initialisiert die Hashtabelle.

```cpp
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Parameter

*hashSize*<br/>
Anzahl der Einträge in der Hashtabelle.

*bAllocNow*<br/>
Wenn TRUE, ordnet die Hashtabelle bei der Initialisierung zu. Andernfalls wird die Tabelle bei Bedarf zugewiesen.

### <a name="remarks"></a>Bemerkungen

Für eine optimale Leistung sollte die Hashtabellengröße eine Primzahl sein. Um Kollisionen zu minimieren, sollte die Größe etwa 20 Prozent größer sein als der größte erwartete Datensatz.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMap::Lookup](#lookup).

## <a name="cmapisempty"></a><a name="isempty"></a>CMap::IsEmpty

Bestimmt, ob die Karte leer ist.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn diese Karte keine Elemente enthält; andernfalls 0.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMap::RemoveAll](#removeall).

## <a name="cmaplookup"></a><a name="lookup"></a>CMap::Lookup

Sucht den Wert, der einem bestimmten Schlüssel zugeordnet ist.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parameter

*ARG_KEY*<br/>
Vorlagenparameter, der den Typ des *Schlüsselwerts* angibt.

*key*<br/>
Gibt den Schlüssel an, der das zu sanende Element identifiziert.

*Wert*<br/>
Gibt den Typ des nachzusehenden Werts an.

*Rvalue*<br/>
Empfängt den nachobenwert.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element gefunden wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

`Lookup`verwendet einen Hashalgorithmus, um das Kartenelement schnell mit einem Schlüssel zu finden, der genau mit dem angegebenen Schlüssel übereinstimmt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a>CMap::operator [ ]

Ein bequemer `SetAt` Ersatz für die Memberfunktion.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Vorlagenparameter, der den Typ des Kartenwerts angibt.

*ARG_KEY*<br/>
Vorlagenparameter, der den Typ des Schlüsselwerts angibt.

*key*<br/>
Der Schlüssel, der zum Abrufen des Werts aus der Karte verwendet wird.

### <a name="remarks"></a>Bemerkungen

Somit kann sie nur auf der linken Seite einer Zuweisungsanweisung (ein l-Wert) verwendet werden. Wenn kein Kartenelement mit dem angegebenen Schlüssel vorhanden ist, wird ein neues Element erstellt.

Es gibt keine "rechte Seite" (r-Wert) äquivalent zu diesem Operator, da es eine Möglichkeit, dass ein Schlüssel nicht in der Karte gefunden werden. Verwenden `Lookup` Sie die Memberfunktion für den Elementabruf.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMap::Lookup](#lookup).

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc

Gibt den ersten Eintrag des Kartenobjekts zurück.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den ersten Eintrag in der Karte; siehe [CMap::CPair](#cpair). Wenn die Karte keine Einträge enthält, ist der Wert NULL.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um einen Zeiger auf das erste Element im Kartenobjekt zurückzugeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a>CMap::PGetNextAssoc

Ruft das Kartenelement ab, auf das *pAssocRec*zeigt.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Parameter

*pAssocRet*<br/>
Verweist auf einen Karteneintrag, der von einem vorherigen [PGetNextAssoc-](#pgetnextassoc) oder [CMap::PGetFirstAssoc-Aufruf](#pgetfirstassoc) zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den nächsten Eintrag in der Karte; siehe [CMap::CPair](#cpair). Wenn das Element das letzte element in der Karte ist, ist der Wert NULL.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um alle Elemente in der Karte zu durchlaufen. Rufen Sie das erste `PGetFirstAssoc` Element mit einem Aufruf von ab, `PGetNextAssoc`und durchlaufen Sie dann die Karte mit aufeinanderfolgenden Aufrufen von .

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMap::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapplookup"></a><a name="plookup"></a>CMap::PLookup

Sucht den Wert, der einem bestimmten Schlüssel zugeordnet ist.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Schlüssel für das zu durchsuchende Element.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Schlüsselstruktur; siehe [CMap::CPair](#cpair). Wenn keine Übereinstimmung `CMap::PLookup` gefunden wird, wird NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um nach einem Kartenelement mit einem Schlüssel zu suchen, der genau mit dem angegebenen Schlüssel übereinstimmt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a>CMap::RemoveAll

Entfernt alle Werte aus dieser Karte, indem `DestructElements`die globale Hilfsfunktion aufgerufen wird.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Die Funktion funktioniert korrekt, wenn die Karte bereits leer ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a>CMap::RemoveKey

Sucht den Karteneintrag entsprechend dem angegebenen Schlüssel; wenn der Schlüssel gefunden wird, wird der Eintrag entfernt.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Parameter

*ARG_KEY*<br/>
Vorlagenparameter, der den Schlüsseltyp angibt.

*key*<br/>
Schlüssel für das zu entfernende Element.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Eintrag gefunden und erfolgreich entfernt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `DestructElements` Hilfsfunktion wird verwendet, um den Eintrag zu entfernen.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CMap::SetAt](#setat).

## <a name="cmapsetat"></a><a name="setat"></a>CMap::SetAt

Das primäre Mittel zum Einfügen eines Elements in eine Karte.

```cpp
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Parameter

*ARG_KEY*<br/>
Vorlagenparameter, der den Typ des *Schlüsselparameters* angibt.

*key*<br/>
Gibt den Schlüssel des neuen Elements an.

*ARG_VALUE*<br/>
Vorlagenparameter, der den Typ des *newValue-Parameters* angibt.

*newValue*<br/>
Gibt den Wert des neuen Elements an.

### <a name="remarks"></a>Bemerkungen

Zunächst wird der Schlüssel nachgeschlagen. Wenn der Schlüssel gefunden wird, wird der entsprechende Wert geändert. Andernfalls wird ein neues Schlüssel-Wert-Paar erstellt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel COLLECT](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
