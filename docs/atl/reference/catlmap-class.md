---
title: CAtlMap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 8954eeae28f13fb50643646b41c032588ecc278f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748656"
---
# <a name="catlmap-class"></a>CAtlMap-Klasse

Diese Klasse stellt Methoden zum Erstellen und Verwalten eines Kartenobjekts bereit.

## <a name="syntax"></a>Syntax

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

#### <a name="parameters"></a>Parameter

*K*<br/>
Der Schlüsselelementtyp.

*V*<br/>
Der Wertelementtyp.

*KTraits*<br/>
Der Code, der zum Kopieren oder Verschieben von Schlüsselelementen verwendet wird. Weitere Informationen finden Sie unter [CElementTraits-Klasse.](../../atl/reference/celementtraits-class.md)

*VTraits*<br/>
Der Code, der zum Kopieren oder Verschieben von Wertelementen verwendet wird.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ, der verwendet wird, wenn ein Schlüssel als Eingabeargument übergeben wird|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ, der verwendet wird, wenn ein Schlüssel als Ausgabeargument zurückgegeben wird.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ, der verwendet wird, wenn ein Wert als Eingabeargument übergeben wird.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ, der verwendet wird, wenn ein Wert als Ausgabeargument übergeben wird.|

### <a name="public-classes"></a>Öffentliche Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlMap::CPair-Klasse](#cpair_class)|Eine Klasse, die die Schlüssel- und Wertelemente enthält.|

### <a name="cpair-data-members"></a>CPair-Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPair::m_key](#m_key)|Das Datenelement, in dem das Schlüsselelement gespeichert wird.|
|[CPair::m_value](#m_value)|Das Datenelement, in dem das Wertelement gespeichert wird.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Der Konstruktor.|
|[CAtlMap::-CAtlMap](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Rufen Sie diese Methode auf, um einen ASSERT zu verursachen, wenn der `CAtlMap` ungültig ist.|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Rufen Sie diese Methode auf, `CAtlMap` um das automatische Erneuthastieren des Objekts zu deaktivieren.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Rufen Sie diese Methode auf, `CAtlMap` um das automatische Rehashing des Objekts zu aktivieren.|
|[CAtlMap::GetAt](#getat)|Rufen Sie diese Methode auf, um das Element an einer angegebenen Position in der Karte zurückzugeben.|
|[CAtlMap::GetCount](#getcount)|Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Karte abzurufen.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Rufen Sie diese Methode auf, um die Anzahl der Abschnitte in der Hashtabelle der Zuordnung zu bestimmen.|
|[CAtlMap::GetKeyAt](#getkeyat)|Rufen Sie diese Methode auf, um den `CAtlMap` an der angegebenen Position im Objekt gespeicherten Schlüssel abzurufen.|
|[CAtlMap::GetNext](#getnext)|Rufen Sie diese Methode auf, um einen Zeiger `CAtlMap` auf das nächste im Objekt gespeicherte Elementpaar abzurufen.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Ruft das nächste Element zum Iterieren ab.|
|[CAtlMap::GetNextKey](#getnextkey)|Rufen Sie diese Methode auf, `CAtlMap` um den nächsten Schlüssel aus dem Objekt abzurufen.|
|[CAtlMap::GetNextValue](#getnextvalue)|Rufen Sie diese Methode auf, `CAtlMap` um den nächsten Wert aus dem Objekt abzurufen.|
|[CAtlMap::GetStartPosition](#getstartposition)|Rufen Sie diese Methode auf, um eine Karteniteration zu starten.|
|[CAtlMap::GetValueAt](#getvalueat)|Rufen Sie diese Methode auf, um den `CAtlMap` wert, der an einer bestimmten Position im Objekt gespeichert ist, abzurufen.|
|[CAtlMap::InitHashTable](#inithashtable)|Rufen Sie diese Methode auf, um die Hashtabelle zu initialisieren.|
|[CAtlMap::IsEmpty](#isempty)|Rufen Sie diese Methode auf, um ein leeres Kartenobjekt zu testen.|
|[CAtlMap::Suche](#lookup)|Rufen Sie diese Methode auf, `CAtlMap` um Schlüssel oder Werte im Objekt zu suchen.|
|[CAtlMap::Rehash](#rehash)|Rufen Sie diese Methode `CAtlMap` auf, um das Objekt erneut zu hashen.|
|[CAtlMap::Alle entfernen](#removeall)|Rufen Sie diese Methode auf, um alle Elemente aus dem `CAtlMap` Objekt zu entfernen.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Rufen Sie diese Methode auf, um `CAtlMap` das Element an der angegebenen Position im Objekt zu entfernen.|
|[CAtlMap::RemoveKey](#removekey)|Rufen Sie diese Methode auf, um ein Element aus dem `CAtlMap` Objekt zu entfernen, wenn der Schlüssel angegeben wird.|
|[CAtlMap::SetAt](#setat)|Rufen Sie diese Methode auf, um ein Elementpaar in die Karte einzufügen.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Rufen Sie diese Methode auf, `CAtlMap` um die optimale Last des Objekts festzulegen.|
|[CAtlMap::SetValueAt](#setvalueat)|Rufen Sie diese Methode auf, um den `CAtlMap` an einer bestimmten Position im Objekt gespeicherten Wert zu ändern.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Ersetzt oder fügt dem `CAtlMap`ein neues Element hinzu.|

## <a name="remarks"></a>Bemerkungen

`CAtlMap`bietet Unterstützung für ein Mapping-Array eines beliebigen Typs, das ein ungeordnetes Array von Schlüsselelementen und den zugehörigen Werten verwaltet. Elemente (bestehend aus einem Schlüssel und einem Wert) werden mithilfe eines Hashalgorithmus gespeichert, sodass eine große Datenmenge effizient gespeichert und abgerufen werden kann.

Die *Parameter KTraits* und *VTraits* sind Merkmalsklassen, die zusätzlichen Code enthalten, der zum Kopieren oder Verschieben von Elementen erforderlich ist.

Eine Alternative `CAtlMap` zu wird von der [CRBMap-Klasse](../../atl/reference/crbmap-class.md) angeboten. `CRBMap`speichert auch Schlüssel-Wert-Paare, weist jedoch unterschiedliche Leistungsmerkmale auf. Die Zeit, die zum Einfügen eines Elements, Suchen eines `CRBMap` Schlüssels oder Löschen eines Schlüssels aus einem Objekt erforderlich ist, ist von *Ordnungsprotokoll(n)*, wobei *n* die Anzahl der Elemente ist. Für `CAtlMap`nehmen alle diese Vorgänge in der Regel eine konstante Zeit in Anspruch, obwohl Worst-Case-Szenarien möglicherweise der Reihenfolge *n*sind. Daher `CAtlMap` ist in einem typischen Fall schneller.

Der andere `CRBMap` Unterschied `CAtlMap` zwischen und wird beim Durchlaufen der gespeicherten Elemente deutlich. In `CRBMap`einem werden die Elemente in einer sortierten Reihenfolge aufgerufen. In `CAtlMap`a werden die Elemente nicht sortiert, und es kann keine Reihenfolge abgeleitet werden.

Wenn eine kleine Anzahl von Elementen gespeichert werden muss, sollten Sie stattdessen die [CSimpleMap-Klasse](../../atl/reference/csimplemap-class.md) verwenden.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlcoll.h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::AssertValid

Rufen Sie diese Methode auf, um einen ASSERT zu verursachen, wenn das `CAtlMap` Objekt ungültig ist.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Bemerkungen

In Debugbuilds verursacht diese Methode einen `CAtlMap` ASSERT, wenn das Objekt ungültig ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap::CAtlMap

Der Konstruktor.

```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Parameter

*nBins*<br/>
Die Anzahl der Lagerplätze, die Zeiger auf die gespeicherten Elemente bereitstellen. Weitere Informationen zu den Abschnitten finden Sie unter Hinweise weiter unten in diesem Thema, um eine Erläuterung der Abschnitte zu erhalten.

*fOptimalLoad*<br/>
Das optimale Lastverhältnis.

*fLoThreshold*<br/>
Der untere Schwellenwert für das Lastverhältnis.

*fHiThreshold*<br/>
Der obere Schwellenwert für das Lastverhältnis.

*nBlockSize*<br/>
Die Blockgröße.

### <a name="remarks"></a>Bemerkungen

`CAtlMap`verweist auf alle gespeicherten Elemente, indem zuerst ein Index mithilfe eines Hashalgorithmus für den Schlüssel erstellt wird. Dieser Index verweist auf einen "bin", der einen Zeiger auf die gespeicherten Elemente enthält. Wenn der Lagerplatz bereits verwendet wird, wird eine verknüpfte Liste erstellt, um auf die nachfolgenden Elemente zuzugreifen. Das Durchlaufen einer Liste ist langsamer als der direkte Zugriff auf das richtige Element, sodass die Kartenstruktur die Speicheranforderungen gegen die Leistung abwägen muss. Die Standardparameter wurden ausgewählt, um in den meisten Fällen gute Ergebnisse zu erzielen.

Das Lastverhältnis ist das Verhältnis zwischen der Anzahl der Lagerplätze zur Anzahl der im Kartenobjekt gespeicherten Elemente. Wenn die Kartenstruktur neu berechnet wird, wird der *Parameterwert fOptimalLoad* verwendet, um die Anzahl der erforderlichen Lagerplätze zu berechnen. Dieser Wert kann mit der [CAtlMap::SetOptimalLoad-Methode](#setoptimalload) geändert werden.

Der *Parameter fLoThreshold* ist der niedrigere Wert, `CAtlMap` den das Lastverhältnis erreichen kann, bevor die optimale Größe der Karte neu berechnet wird.

Der *Parameter fHiThreshold* ist der obere Wert, `CAtlMap` den das Lastverhältnis erreichen kann, bevor das Objekt die optimale Größe der Karte neu berechnet.

Dieser Neuberechnungsprozess (auch rehashing genannt) ist standardmäßig aktiviert. Wenn Sie diesen Prozess deaktivieren möchten, vielleicht wenn Sie viele Daten gleichzeitig eingeben, rufen Sie die [CAtlMap::DisableAutoRehash-Methode](#disableautorehash) auf. Reaktivieren Sie es mit der [CAtlMap::EnableAutoRehash-Methode.](#enableautorehash)

Der Parameter *nBlockSize* ist ein Maß für die Speichermenge, die zugewiesen wird, wenn ein neues Element erforderlich ist. Größere Blockgrößen reduzieren Aufrufe von Speicherzuweisungsroutinen, verwenden jedoch mehr Ressourcen.

Bevor Daten gespeichert werden können, ist es notwendig, die Hashtabelle mit einem Aufruf von [CAtlMap::InitHashTable](#inithashtable)zu initialisieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap::-CAtlMap

Der Destruktor.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap::CPair-Klasse

Eine Klasse, die die Schlüssel- und Wertelemente enthält.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Bemerkungen

Diese Klasse wird von den Methoden [CAtlMap::GetNext](#getnext) und [CAtlMap::Lookup](#lookup) verwendet, um auf die in der Zuordnungsstruktur gespeicherten Schlüssel- und Wertelemente zuzugreifen.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::DisableAutoRehash

Rufen Sie diese Methode auf, `CAtlMap` um das automatische Erneuthastieren des Objekts zu deaktivieren.

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn das automatische Rehashing aktiviert ist (was standardmäßig der Fall ist), wird die Anzahl der Abschnitte in der Hashtabelle automatisch neu berechnet, wenn der Auslastungswert (das Verhältnis der Anzahl der Lagerplätze zur Anzahl der im Array gespeicherten Elemente) die zum Zeitpunkt der Erstellung der Zuordnung angegebenen Maximal- oder Minimalwerte überschreitet.

`DisableAutoRehash`ist besonders nützlich, wenn der Karte eine große Anzahl von Elementen gleichzeitig hinzugefügt wird. Anstatt den Rehashing-Prozess jedes Mal auszulösen, wenn die `DisableAutoRehash`Grenzwerte überschritten werden, ist es effizienter, aufzurufen, die Elemente hinzuzufügen und schließlich [CAtlMap::EnableAutoRehash](#enableautorehash)aufzurufen.

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap::EnableAutoRehash

Rufen Sie diese Methode auf, `CAtlMap` um das automatische Rehashing des Objekts zu aktivieren.

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn das automatische Rehashing aktiviert ist (was standardmäßig der Fall ist), wird die Anzahl der Abschnitte in der Hashtabelle automatisch neu berechnet, wenn der Auslastungswert (das Verhältnis der Anzahl der Lagerplätze zur Anzahl der im Array gespeicherten Elemente) die maximalen oder minimalen Werte überschreitet, die zum Zeitpunkt der Erstellung der Karte angegeben wurden.

`EnableAutoRefresh`wird am häufigsten nach einem Aufruf von [CAtlMap::DisableAutoRehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap::GetAt

Rufen Sie diese Methode auf, um das Element an einer angegebenen Position in der Karte zurückzugeben.

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

*key*<br/>
Vorlagenparameter, der den Typ des Kartenschlüssels angibt.

*value*<br/>
Vorlagenparameter, der den Typ des Kartenwerts angibt.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das aktuelle Paar von Schlüssel-Wert-Elementen zurück, die in der Karte gespeichert sind.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap::GetCount

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Karte abzurufen.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente im Kartenobjekt zurück. Ein einzelnes Element ist ein Schlüssel-Wert-Paar.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap::GetHashTableSize

Rufen Sie diese Methode auf, um die Anzahl der Abschnitte in der Hashtabelle der Zuordnung zu bestimmen.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Lagerplätze in der Hashtabelle zurück. Eine Erklärung finden Sie unter [CAtlMap::CAtlMap.](#catlmap)

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap::GetKeyAt

Rufen Sie diese Methode auf, um den `CAtlMap` an der angegebenen Position im Objekt gespeicherten Schlüssel abzurufen.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den Schlüssel zurück, der an der angegebenen Position im `CAtlMap` Objekt gespeichert ist.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap::GetNext

Rufen Sie diese Methode auf, um einen Zeiger `CAtlMap` auf das nächste im Objekt gespeicherte Elementpaar abzurufen.

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das nächste Paar von Schlüssel-Wert-Elementen zurück, die in der Karte gespeichert sind. Der *Pos-Positionszähler* wird nach jedem Anruf aktualisiert. Wenn das abgerufene Element das letzte in der Karte ist, wird *pos* auf NULL gesetzt.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap::GetNextAssoc

Ruft das nächste Element zum Iterieren ab.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

*key*<br/>
Vorlagenparameter, der den Typ des Kartenschlüssels angibt.

*value*<br/>
Vorlagenparameter, der den Typ des Kartenwerts angibt.

### <a name="remarks"></a>Bemerkungen

Der *Pos-Positionszähler* wird nach jedem Anruf aktualisiert. Wenn das abgerufene Element das letzte in der Karte ist, wird *pos* auf NULL gesetzt.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap::GetNextKey

Rufen Sie diese Methode auf, `CAtlMap` um den nächsten Schlüssel aus dem Objekt abzurufen.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den nächsten Schlüssel in der Karte zurück.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positionszähler *pos*. Wenn keine einträge mehr in der Karte vorhanden sind, wird der Positionszähler auf NULL gesetzt.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap::GetNextValue

Rufen Sie diese Methode auf, `CAtlMap` um den nächsten Wert aus dem Objekt abzurufen.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den nächsten Wert in der Karte zurück.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positionszähler *pos*. Wenn keine einträge mehr in der Karte vorhanden sind, wird der Positionszähler auf NULL gesetzt.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap::GetStartPosition

Rufen Sie diese Methode auf, um eine Karteniteration zu starten.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Startposition zurück, oder NULL wird zurückgegeben, wenn die Karte leer ist.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine Karteniteration zu `GetNextAssoc` starten, indem Sie einen POSITION-Wert zurückgeben, der an die Methode übergeben werden kann.

> [!NOTE]
> Die Iterationssequenz ist nicht vorhersagbar

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap::GetValueAt

Rufen Sie diese Methode auf, um den `CAtlMap` wert, der an einer bestimmten Position im Objekt gespeichert ist, abzurufen.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den Wert zurück, der an der angegebenen Position im `CAtlMap` Objekt gespeichert ist.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap::InitHashTable

Rufen Sie diese Methode auf, um die Hashtabelle zu initialisieren.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parameter

*nBins*<br/>
Die Anzahl der von der Hashtabelle verwendeten Lagerplätze. Eine Erklärung finden Sie unter [CAtlMap::CAtlMap.](#catlmap)

*bAllocNow*<br/>
Ein Flag, das angibt, wann Speicher zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei erfolgreicher Initialisierung zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

`InitHashTable`muss aufgerufen werden, bevor Elemente in der Hashtabelle gespeichert werden.  Wenn diese Methode nicht explizit aufgerufen wird, wird sie automatisch aufgerufen, wenn ein `CAtlMap` Element zum ersten Mal mithilfe der vom Konstruktor angegebenen Bin-Anzahl hinzugefügt wird.  Andernfalls wird die Karte mithilfe der neuen Lagerplatzanzahl initialisiert, die durch den Parameter *nBins* angegeben wird.

Wenn der Parameter *bAllocNow* false ist, wird der für die Hashtabelle benötigte Speicher erst zugewiesen, wenn er zuerst benötigt wird. Dies kann nützlich sein, wenn es ungewiss ist, ob die Karte verwendet wird.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap::IsEmpty

Rufen Sie diese Methode auf, um ein leeres Kartenobjekt zu testen.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Karte leer ist, andernfalls FALSE.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::KINARGTYPE

Typ, der verwendet wird, wenn ein Schlüssel als Eingabeargument übergeben wird.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap::KOUTARGTYPE

Typ, der verwendet wird, wenn ein Schlüssel als Ausgabeargument zurückgegeben wird.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap::Suche

Rufen Sie diese Methode auf, `CAtlMap` um Schlüssel oder Werte im Objekt zu suchen.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Schlüssel an, der das zu sanende Element identifiziert.

*value*<br/>
Variable, die den nachobenden Wert empfängt.

### <a name="return-value"></a>Rückgabewert

Die erste Form der Methode gibt true zurück, wenn der Schlüssel gefunden wird, andernfalls false. Die zweite und dritte Form geben einen Zeiger auf ein [CPair](#cpair_class) zurück, das als Position für Aufrufe von [CAtlMap::GetNext](#getnext) usw. verwendet werden kann.

### <a name="remarks"></a>Bemerkungen

`Lookup`verwendet einen Hashalgorithmus, um schnell das Kartenelement zu finden, das einen Schlüssel enthält, der genau mit dem angegebenen Schlüsselparameter übereinstimmt.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap::Operator\[\]

Ersetzt oder fügt dem `CAtlMap`ein neues Element hinzu.

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel des hinzuzufügenden oder zu ersetzenden Elements.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den Wert zurück, der dem angegebenen Schlüssel zugeordnet ist.

### <a name="example"></a>Beispiel

Wenn der Schlüssel bereits vorhanden ist, wird das Element ersetzt. Wenn der Schlüssel nicht vorhanden ist, wird ein neues Element hinzugefügt. Siehe Beispiel für [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap::Rehash

Rufen Sie diese Methode `CAtlMap` auf, um das Objekt erneut zu hashen.

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parameter

*nBins*<br/>
Die neue Anzahl von Abschnitten, die in der Hashtabelle verwendet werden sollen. Eine Erklärung finden Sie unter [CAtlMap::CAtlMap.](#catlmap)

### <a name="remarks"></a>Bemerkungen

Wenn *nBins* 0 `CAtlMap` ist, wird eine angemessene Zahl basierend auf der Anzahl der Elemente in der Karte und der optimalen Lasteinstellung berechnet. Normalerweise ist der Rehashing-Prozess automatisch, aber wenn [CAtlMap::DisableAutoRehash](#disableautorehash) aufgerufen wurde, führt diese Methode die erforderliche Größenänderung durch.

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap::Alle entfernen

Rufen Sie diese Methode auf, um alle Elemente aus dem `CAtlMap` Objekt zu entfernen.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Bemerkungen

Löscht das `CAtlMap` Objekt und gibt den Speicher frei, der zum Speichern der Elemente verwendet wird.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::RemoveAtPos

Rufen Sie diese Methode auf, um `CAtlMap` das Element an der angegebenen Position im Objekt zu entfernen.

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

### <a name="remarks"></a>Bemerkungen

Entfernt das Schlüssel-Wert-Paar, das an der angegebenen Position gespeichert ist. Der Speicher, der zum Speichern des Elements verwendet wird, wird freigegeben. Die POSITION, auf die von *pos* verwiesen wird, wird ungültig, und während die POSITION aller anderen Elemente in der Karte gültig bleibt, behalten sie nicht unbedingt die gleiche Reihenfolge bei.

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::RemoveKey

Rufen Sie diese Methode auf, um ein Element aus dem `CAtlMap` Objekt zu entfernen, wenn der Schlüssel angegeben wird.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel, der dem Elementpaar entspricht, das Sie entfernen möchten.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Schlüssel gefunden und entfernt wird, FALSE bei Fehler.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap::SetAt

Rufen Sie diese Methode auf, um ein Elementpaar in die Karte einzufügen.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselwert, der `CAtlMap` dem Objekt hinzugefügt werden soll.

*value*<br/>
Der Wert, der `CAtlMap` dem Objekt hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt die Position des Schlüssel-Wert-Element-Paares im `CAtlMap` Objekt zurück.

### <a name="remarks"></a>Bemerkungen

`SetAt`ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird. Wenn der Schlüssel nicht gefunden wird, wird ein neues Schlüssel-Wert-Paar erstellt.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::SetOptimalLoad

Rufen Sie diese Methode auf, `CAtlMap` um die optimale Last des Objekts festzulegen.

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Parameter

*fOptimalLoad*<br/>
Das optimale Lastverhältnis.

*fLoThreshold*<br/>
Der untere Schwellenwert für das Lastverhältnis.

*fHiThreshold*<br/>
Der obere Schwellenwert für das Lastverhältnis.

*bRehashNow*<br/>
Flag, das angibt, ob die Hashtabelle neu berechnet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode definiert den optimalen `CAtlMap` Lastwert für das Objekt neu. Siehe [CAtlMap::CAtlMap](#catlmap) für eine Erläuterung der verschiedenen Parameter. Wenn *bRehashNow* true ist und die Anzahl der Elemente außerhalb der minimalen und maximalen Werte liegt, wird die Hashtabelle neu berechnet.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::SetValueAt

Rufen Sie diese Methode auf, um den `CAtlMap` an einer bestimmten Position im Objekt gespeicherten Wert zu ändern.

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der durch einen vorherigen Aufruf von [CAtlMap::GetNextAssoc](#getnextassoc) oder [CAtlMap::GetStartPosition](#getstartposition)zurückgegeben wird.

*value*<br/>
Der Wert, der `CAtlMap` dem Objekt hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Ändert das Wertelement, das an `CAtlMap` der angegebenen Position im Objekt gespeichert ist.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::VINARGTYPE

Typ, der verwendet wird, wenn ein Wert als Eingabeargument übergeben wird.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

Typ, der verwendet wird, wenn ein Wert als Ausgabeargument übergeben wird.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap::CPair::m_key

Das Datenelement, in dem das Schlüsselelement gespeichert wird.

```
const K m_key;
```

### <a name="parameters"></a>Parameter

*K*<br/>
Der Schlüsselelementtyp.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap::CPair::m_value

Das Datenelement, in dem das Wertelement gespeichert wird.

```
V  m_value;
```

### <a name="parameters"></a>Parameter

*V*<br/>
Der Wertelementtyp.

## <a name="see-also"></a>Weitere Informationen

[Marquee-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV-Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
