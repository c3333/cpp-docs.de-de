---
title: Crbtree-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 7b8e47b5cd0ac278711947abc867956333371be3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833490"
---
# <a name="crbtree-class"></a>Crbtree-Klasse

Diese Klasse stellt Methoden zum Erstellen und Verwenden eines roten schwarzen Baums bereit.

## <a name="syntax"></a>Syntax

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
```

#### <a name="parameters"></a>Parameter

*Km*<br/>
Der Schlüssel Elementtyp.

*V*<br/>
Der Wert Elementtyp.

*Kmerkmalen*<br/>
Der Code, der zum Kopieren oder Verschieben von Schlüsselelementen verwendet wird. Weitere Informationen finden Sie unter [celementtrait-Klasse](../../atl/reference/celementtraits-class.md) .

*Vmerkmalen*<br/>
Der Code, der zum Kopieren oder Verschieben von Wert Elementen verwendet wird.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|[Crbtree:: kinargtype](#kinargtype)|Der Typ, der verwendet wird, wenn eine Taste als Eingabe Argument übermittelt wird.|
|[Crbtree:: koutargtype](#koutargtype)|Der Typ, der verwendet wird, wenn eine Taste als Ausgabe Argument zurückgegeben wird.|
|[Crbtree:: vinargtype](#vinargtype)|Der Typ, der verwendet wird, wenn ein Wert als Eingabe Argument übermittelt wird.|
|[Crbtree:: voutargtype](#voutargtype)|Der Typ, der verwendet wird, wenn ein Wert als Ausgabe Argument ausgegeben wird.|

### <a name="public-classes"></a>Öffentliche Klassen

|Name|Beschreibung|
|----------|-----------------|
|[Crbtree:: cpair-Klasse](#cpair_class)|Eine-Klasse, die die Schlüssel-und Wert Elemente enthält.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Crbtree:: ~ crbtree](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Crbtree:: findfirstkeyafter](#findfirstkeyafter)|Mit dieser Methode können Sie die Position des Elements suchen, das den nächsten verfügbaren Schlüssel verwendet.|
|[Crbtree:: GetAt](#getat)|Mit dieser Methode können Sie das Element an einer bestimmten Position in der Struktur abrufen.|
|[Crbtree:: GetCount](#getcount)|Mit dieser Methode können Sie die Anzahl der Elemente in der Struktur abrufen.|
|[Crbtree:: GE-Adposition](#getheadposition)|Rufen Sie diese Methode auf, um den Positionswert für das Element am Anfang der Struktur abzurufen.|
|[Crbtree:: getkeyat](#getkeyat)|Mit dieser Methode können Sie den Schlüssel von einer angegebenen Position in der Struktur abrufen.|
|[Crbtree:: GetNext](#getnext)|Rufen Sie diese Methode auf, um einen Zeiger auf ein Element zu erhalten, das im- `CRBTree` Objekt gespeichert ist, und setzen Sie die Position auf das nächste Element.|
|[Crbtree:: GetNextAssoc](#getnextassoc)|Mit dieser Methode können Sie den Schlüssel und den Wert eines in der Zuordnung gespeicherten Elements abrufen und die Position mit dem nächsten Element fortsetzen.|
|[Crbtree:: getnextkey](#getnextkey)|Mit dieser Methode können Sie den Schlüssel eines in der Struktur gespeicherten Elements abrufen und die Position bis zum nächsten Element fortsetzen.|
|[Crbtree:: getnextvalue](#getnextvalue)|Mit dieser Methode können Sie den Wert eines in der Struktur gespeicherten Elements abrufen und die Position bis zum nächsten Element fortsetzen.|
|[Crbtree:: GetPrev](#getprev)|Rufen Sie diese Methode auf, um einen Zeiger auf ein Element zu erhalten, das im- `CRBTree` Objekt gespeichert ist, und aktualisieren Sie dann die Position auf das vorherige Element.|
|[Crbtree:: gettailposition](#gettailposition)|Mit dieser Methode können Sie den Positionswert für das Element am Ende der Struktur abrufen.|
|[Crbtree:: getvalueat](#getvalueat)|Rufen Sie diese Methode auf, um den Wert abzurufen, der an einer bestimmten Position im-Objekt gespeichert ist `CRBTree` .|
|[Crbtree:: IsEmpty](#isempty)|Mit dieser Methode können Sie auf ein leeres Struktur Objekt testen.|
|[Crbtree:: RemoveAll](#removeall)|Mit dieser Methode können Sie alle Elemente aus dem- `CRBTree` Objekt entfernen.|
|[Crbtree:: RemoveAt](#removeat)|Ruft diese Methode auf, um das Element an der angegebenen Position im `CRBTree` Objekt zu entfernen.|
|[Crbtree:: setvalueat](#setvalueat)|Ruft diese Methode auf, um den Wert zu ändern, der an einer bestimmten Position im-Objekt gespeichert ist `CRBTree` .|

## <a name="remarks"></a>Bemerkungen

Eine rote schwarze Struktur ist eine binäre Such Struktur, in der ein zusätzliches Paar von Informationen pro Knoten verwendet wird, um sicherzustellen, dass die Struktur "ausgeglichen" bleibt, d. h. die Struktur Höhe wächst nicht unverhältnismäßig groß und wirkt sich auf die Leistung aus.

Diese Vorlagen Klasse ist für die Verwendung durch [CRBMap](../../atl/reference/crbmap-class.md) und [CRBMultiMap](../../atl/reference/crbmultimap-class.md)konzipiert. Der Großteil der Methoden, die diese abgeleiteten Klassen bilden, wird von bereitgestellt `CRBTree` .

Eine ausführlichere Erläuterung der verschiedenen Sammlungs Klassen und ihrer Features und Leistungsmerkmale finden Sie unter [ATL](../../atl/atl-collection-classes.md)-Auflistungs Klassen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcoll. h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a> Crbtree:: cpair-Klasse

Eine-Klasse, die die Schlüssel-und Wert Elemente enthält.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Bemerkungen

Diese Klasse wird von den Methoden [crbtree:: GetAt](#getat), [crbtree:: GetNext](#getnext)und [crbtree:: GetPrev](#getprev) verwendet, um auf die in der Baumstruktur gespeicherten Schlüssel-und Wert Elemente zuzugreifen.

Die Elemente lauten wie folgt:

|Datenelement|Beschreibung|
|-|-|
|`m_key`|Der Datenmember, der das Schlüsselelement speichert.|
|`m_value`|Der Datenmember, der das Value-Element speichert.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a> Crbtree:: ~ crbtree

Der Destruktor.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei. Ruft [crbtree:: RemoveAll](#removeall) auf, um alle Elemente zu löschen.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a> Crbtree:: findfirstkeyafter

Mit dieser Methode können Sie die Position des Elements suchen, das den nächsten verfügbaren Schlüssel verwendet.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Ein Schlüsselwert.

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert des Elements zurück, das den nächsten verfügbaren Schlüssel verwendet. Wenn keine weiteren Elemente vorhanden sind, wird NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Methode vereinfacht das Durchlaufen der Struktur, ohne die Positionswerte vorher berechnen zu müssen.

## <a name="crbtreegetat"></a><a name="getat"></a> Crbtree:: GetAt

Mit dieser Methode können Sie das Element an einer bestimmten Position in der Struktur abrufen.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positionswert.

*key*<br/>
Die Variable, die den Schlüssel empfängt.

*value*<br/>
Die Variable, die den Wert empfängt.

### <a name="return-value"></a>Rückgabewert

Die ersten beiden Formulare geben einen Zeiger auf ein [cpair](#cpair_class)zurück. Das dritte Formular erhält einen Schlüssel und einen Wert für die angegebene Position.

### <a name="remarks"></a>Bemerkungen

Der Positionswert kann zuvor durch einen Aufrufen einer Methode wie [crbtree:: geteadposition](#getheadposition) oder [crbtree:: gettailposition](#gettailposition)bestimmt werden.

In Debugbuilds tritt ein Assertionsfehler auf, wenn *POS* gleich NULL ist.

## <a name="crbtreegetcount"></a><a name="getcount"></a> Crbtree:: GetCount

Mit dieser Methode können Sie die Anzahl der Elemente in der Struktur abrufen.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente (jedes Schlüssel-Wert-Paar ist ein Element) zurück, das in der Struktur gespeichert ist.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a> Crbtree:: GE-Adposition

Rufen Sie diese Methode auf, um den Positionswert für das Element am Anfang der Struktur abzurufen.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert für das Element am Anfang der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Der von zurückgegebene Wert `GetHeadPosition` kann mit Methoden wie [crbtree:: getkeyat](#getkeyat) oder [crbtree:: GetNext](#getnext) verwendet werden, um die Struktur zu durchlaufen und Werte abzurufen.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a> Crbtree:: getkeyat

Mit dieser Methode können Sie den Schlüssel von einer angegebenen Position in der Struktur abrufen.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positionswert.

### <a name="return-value"></a>Rückgabewert

Gibt den Schlüssel zurück, der an Positions- *POS* in der Struktur gespeichert ist.

### <a name="remarks"></a>Bemerkungen

Wenn *POS* kein gültiger Positionswert ist, sind die Ergebnisse unvorhersehbar. In Debugbuilds tritt ein Assertionsfehler auf, wenn *POS* gleich NULL ist.

## <a name="crbtreegetnext"></a><a name="getnext"></a> Crbtree:: GetNext

Rufen Sie diese Methode auf, um einen Zeiger auf ein Element zu erhalten, das im- `CRBTree` Objekt gespeichert ist, und setzen Sie die Position auf das nächste Element.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Aufrufen von Methoden wie [crbtree:: GE-Adposition](#getheadposition) oder [crbtree:: findfirstkeyafter](#findfirstkeyafter)zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den nächsten [cpair](#cpair_class) -Wert in der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Der *POS* -Positionswert wird nach jedem-Aufrufpunkt aktualisiert. Wenn das abgerufene Element das letzte in der Struktur ist, wird *POS* auf NULL festgelegt.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a> Crbtree:: GetNextAssoc

Mit dieser Methode können Sie den Schlüssel und den Wert eines in der Zuordnung gespeicherten Elements abrufen und die Position mit dem nächsten Element fortsetzen.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Aufrufen von Methoden wie [crbtree:: GE-Adposition](#getheadposition) oder [crbtree:: findfirstkeyafter](#findfirstkeyafter)zurückgegeben wurde.

*key*<br/>
Ein Vorlagen Parameter, der den Typ des Schlüssels der Struktur angibt.

*value*<br/>
Ein Vorlagen Parameter, der den Typ des Struktur Werts angibt.

### <a name="remarks"></a>Bemerkungen

Der *POS* -Positionswert wird nach jedem-Aufrufpunkt aktualisiert. Wenn das abgerufene Element das letzte in der Struktur ist, wird *POS* auf NULL festgelegt.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a> Crbtree:: getnextkey

Mit dieser Methode können Sie den Schlüssel eines in der Struktur gespeicherten Elements abrufen und die Position bis zum nächsten Element fortsetzen.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Aufrufen von Methoden wie [crbtree:: GE-Adposition](#getheadposition) oder [crbtree:: findfirstkeyafter](#findfirstkeyafter)zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den nächsten Schlüssel in der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positions Leistungspunkt ( *POS*). Wenn in der Struktur keine weiteren Einträge vorhanden sind, wird der Positions-Counter auf NULL festgelegt.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a> Crbtree:: getnextvalue

Mit dieser Methode können Sie den Wert eines in der Struktur gespeicherten Elements abrufen und die Position bis zum nächsten Element fortsetzen.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Aufrufen von Methoden wie [crbtree:: GE-Adposition](#getheadposition) oder [crbtree:: findfirstkeyafter](#findfirstkeyafter)zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den nächsten Wert in der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positions Leistungspunkt ( *POS*). Wenn in der Struktur keine weiteren Einträge vorhanden sind, wird der Positions-Counter auf NULL festgelegt.

## <a name="crbtreegetprev"></a><a name="getprev"></a> Crbtree:: GetPrev

Rufen Sie diese Methode auf, um einen Zeiger auf ein Element zu erhalten, das im- `CRBTree` Objekt gespeichert ist, und aktualisieren Sie dann die Position auf das vorherige Element.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Aufrufen von Methoden wie [crbtree:: GE-Adposition](#getheadposition) oder [crbtree:: findfirstkeyafter](#findfirstkeyafter)zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den vorherigen [cpair](#cpair_class) -Wert zurück, der in der Struktur gespeichert ist.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positions Leistungspunkt ( *POS*). Wenn in der Struktur keine weiteren Einträge vorhanden sind, wird der Positions-Counter auf NULL festgelegt.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a> Crbtree:: gettailposition

Mit dieser Methode können Sie den Positionswert für das Element am Ende der Struktur abrufen.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert für das Element am Ende der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Der von zurückgegebene Wert `GetTailPosition` kann mit Methoden wie [crbtree:: getkeyat](#getkeyat) oder [crbtree:: GetPrev](#getprev) verwendet werden, um die Struktur zu durchlaufen und Werte abzurufen.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a> Crbtree:: getvalueat

Rufen Sie diese Methode auf, um den Wert abzurufen, der an einer bestimmten Position im-Objekt gespeichert ist `CRBTree` .

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Aufrufen von Methoden wie [crbtree:: GE-Adposition](#getheadposition) oder [crbtree:: findfirstkeyafter](#findfirstkeyafter)zurückgegeben wurde.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den-Wert zurück, der an der angegebenen Position im-Objekt gespeichert ist `CRBTree` .

## <a name="crbtreeisempty"></a><a name="isempty"></a> Crbtree:: IsEmpty

Mit dieser Methode können Sie auf ein leeres Struktur Objekt testen.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Struktur leer ist, andernfalls false.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a> Crbtree:: kinargtype

Der Typ, der verwendet wird, wenn eine Taste als Eingabe Argument übermittelt wird.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a> Crbtree:: koutargtype

Der Typ, der verwendet wird, wenn eine Taste als Ausgabe Argument zurückgegeben wird.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a> Crbtree:: RemoveAll

Mit dieser Methode können Sie alle Elemente aus dem- `CRBTree` Objekt entfernen.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Bemerkungen

Löscht das- `CRBTree` Objekt und gibt den Arbeitsspeicher frei, der zum Speichern der Elemente verwendet wird.

## <a name="crbtreeremoveat"></a><a name="removeat"></a> Crbtree:: RemoveAt

Ruft diese Methode auf, um das Element an der angegebenen Position im `CRBTree` Objekt zu entfernen.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Aufrufen von Methoden wie [crbtree:: GE-Adposition](#getheadposition) oder [crbtree:: findfirstkeyafter](#findfirstkeyafter)zurückgegeben wurde.

### <a name="remarks"></a>Bemerkungen

Entfernt das Schlüssel-Wert-Paar, das an der angegebenen Position gespeichert ist. Der zum Speichern des Elements verwendete Arbeitsspeicher wird freigegeben. Die Position, auf die von *POS* verwiesen wird, ist ungültig, und während die Position aller anderen Elemente in der Struktur gültig bleibt, behalten Sie nicht notwendigerweise dieselbe Reihenfolge bei.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a> Crbtree:: setvalueat

Ruft diese Methode auf, um den Wert zu ändern, der an einer bestimmten Position im-Objekt gespeichert ist `CRBTree` .

```cpp
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Der Positions-Counter, der von einem vorherigen Aufrufen von Methoden wie [crbtree:: GE-Adposition](#getheadposition) oder [crbtree:: findfirstkeyafter](#findfirstkeyafter)zurückgegeben wurde.

*value*<br/>
Der Wert, der dem-Objekt hinzugefügt werden soll `CRBTree` .

### <a name="remarks"></a>Bemerkungen

Ändert das Value-Element, das an der angegebenen Position im-Objekt gespeichert ist `CRBTree` .

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a> Crbtree:: vinargtype

Der Typ, der verwendet wird, wenn ein Wert als Eingabe Argument übermittelt wird.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a> Crbtree:: voutargtype

Der Typ, der verwendet wird, wenn ein Wert als Ausgabe Argument ausgegeben wird.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)
