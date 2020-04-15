---
title: CRBTree-Klasse
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
ms.openlocfilehash: 56c9db9d1a7bcd7fe2a2647d8b1339d223c4b66b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331242"
---
# <a name="crbtree-class"></a>CRBTree-Klasse

Diese Klasse stellt Methoden zum Erstellen und Verwenden eines rot-schwarzen Baumes bereit.

## <a name="syntax"></a>Syntax

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
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
|[CRBTree::KINARGTYPE](#kinargtype)|Typ, der verwendet wird, wenn ein Schlüssel als Eingabeargument übergeben wird.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Typ, der verwendet wird, wenn ein Schlüssel als Ausgabeargument zurückgegeben wird.|
|[CRBTree::VINARGTYPE](#vinargtype)|Typ, der verwendet wird, wenn ein Wert als Eingabeargument übergeben wird.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Typ, der verwendet wird, wenn ein Wert als Ausgabeargument übergeben wird.|

### <a name="public-classes"></a>Öffentliche Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRBTree::CPair-Klasse](#cpair_class)|Eine Klasse, die die Schlüssel- und Wertelemente enthält.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRBTree::'CRBTree](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Rufen Sie diese Methode auf, um die Position des Elements zu ermitteln, das den nächsten verfügbaren Schlüssel verwendet.|
|[CRBTree::GetAt](#getat)|Rufen Sie diese Methode auf, um das Element an einer bestimmten Position in der Struktur abzurufen.|
|[CRBTree::GetCount](#getcount)|Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Struktur abzurufen.|
|[CRBTree::GetHeadPosition](#getheadposition)|Rufen Sie diese Methode auf, um den Positionswert für das Element am Kopf der Struktur abzurufen.|
|[CRBTree::GetKeyAt](#getkeyat)|Rufen Sie diese Methode auf, um den Schlüssel von einer bestimmten Position in der Struktur abzurufen.|
|[CRBTree::GetNext](#getnext)|Rufen Sie diese Methode auf, um einen `CRBTree` Zeiger auf ein im Objekt gespeichertes Element abzurufen und die Position zum nächsten Element zu überweisen.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Rufen Sie diese Methode auf, um den Schlüssel und den Wert eines elements abzurufen, das in der Karte gespeichert ist, und die Position zum nächsten Element weiterzuleiten.|
|[CRBTree::GetNextKey](#getnextkey)|Rufen Sie diese Methode auf, um den Schlüssel eines Elements abzurufen, das in der Struktur gespeichert ist, und die Position zum nächsten Element zu übersteigen.|
|[CRBTree::GetNextValue](#getnextvalue)|Rufen Sie diese Methode auf, um den Wert eines elements abzurufen, das in der Struktur gespeichert ist, und die Position an das nächste Element weiterzuleiten.|
|[CRBTree::GetPrev](#getprev)|Rufen Sie diese Methode auf, um einen `CRBTree` Zeiger auf ein im Objekt gespeichertes Element abzurufen und dann die Position auf das vorherige Element zu aktualisieren.|
|[CRBTree::GetTailPosition](#gettailposition)|Rufen Sie diese Methode auf, um den Positionswert für das Element am Ende der Struktur abzurufen.|
|[CRBTree::GetValueAt](#getvalueat)|Rufen Sie diese Methode auf, um den `CRBTree` wert, der an einer bestimmten Position im Objekt gespeichert ist, abzurufen.|
|[CRBTree::IsEmpty](#isempty)|Rufen Sie diese Methode auf, um ein leeres Strukturobjekt zu testen.|
|[CRBTree::Alle entfernen](#removeall)|Rufen Sie diese Methode auf, um alle Elemente aus dem `CRBTree` Objekt zu entfernen.|
|[CRBTree::RemoveAt](#removeat)|Rufen Sie diese Methode auf, um `CRBTree` das Element an der angegebenen Position im Objekt zu entfernen.|
|[CRBTree::SetValueAt](#setvalueat)|Rufen Sie diese Methode auf, um den `CRBTree` an einer bestimmten Position im Objekt gespeicherten Wert zu ändern.|

## <a name="remarks"></a>Bemerkungen

Ein rot-schwarzer Baum ist ein binärer Suchbaum, der ein zusätzliches Bit an Informationen pro Knoten verwendet, um sicherzustellen, dass er "ausgewogen" bleibt, d. h., die Baumhöhe wird nicht unverhältnismäßig groß und beeinträchtigt die Leistung.

Diese Vorlagenklasse wurde für die Verwendung durch [CRBMap](../../atl/reference/crbmap-class.md) und [CRBMultiMap](../../atl/reference/crbmultimap-class.md)entwickelt. Der Großteil der Methoden, aus denen diese `CRBTree`abgeleiteten Klassen bestehen, wird von bereitgestellt.

Eine vollständigere Erläuterung der verschiedenen Auflistungsklassen und ihrer Features und Leistungsmerkmale finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a>CRBTree::CPair-Klasse

Eine Klasse, die die Schlüssel- und Wertelemente enthält.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Bemerkungen

Diese Klasse wird von den Methoden [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext)und [CRBTree::GetPrev verwendet,](#getprev) um auf die in der Struktur gespeicherten Schlüssel- und Wertelemente zuzugreifen.

Die Mitglieder sind wie folgt:

|||
|-|-|
|`m_key`|Das Datenelement, in dem das Schlüsselelement gespeichert wird.|
|`m_value`|Das Datenelement, in dem das Wertelement gespeichert wird.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a>CRBTree::'CRBTree

Der Destruktor.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei. Ruft [CRBTree::RemoveAll](#removeall) auf, um alle Elemente zu löschen.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a>CRBTree::FindFirstKeyAfter

Rufen Sie diese Methode auf, um die Position des Elements zu ermitteln, das den nächsten verfügbaren Schlüssel verwendet.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Ein Schlüsselwert.

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert des Elements zurück, das den nächsten verfügbaren Schlüssel verwendet. Wenn keine weiteren Elemente vorhanden sind, wird NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Diese Methode erleichtert das Durchqueren des Baumes, ohne vorher Positionswerte berechnen zu müssen.

## <a name="crbtreegetat"></a><a name="getat"></a>CRBTree::GetAt

Rufen Sie diese Methode auf, um das Element an einer bestimmten Position in der Struktur abzurufen.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionswert.

*key*<br/>
Die Variable, die den Schlüssel empfängt.

*value*<br/>
Die Variable, die den Wert empfängt.

### <a name="return-value"></a>Rückgabewert

Die ersten beiden Formulare geben einen Zeiger auf ein [CPair](#cpair_class)zurück. Das dritte Formular erhält einen Schlüssel und einen Wert für die angegebene Position.

### <a name="remarks"></a>Bemerkungen

Der Positionswert kann zuvor mit einem Aufruf einer Methode wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::GetTailPosition](#gettailposition)bestimmt werden.

In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

## <a name="crbtreegetcount"></a><a name="getcount"></a>CRBTree::GetCount

Rufen Sie diese Methode auf, um die Anzahl der Elemente in der Struktur abzurufen.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der elemente (jedes Schlüssel-Wert-Paar ist ein Element) zurück, die in der Struktur gespeichert sind.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a>CRBTree::GetHeadPosition

Rufen Sie diese Methode auf, um den Positionswert für das Element am Kopf der Struktur abzurufen.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert für das Element am Kopf der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene `GetHeadPosition` Wert kann mit Methoden wie [CRBTree::GetKeyAt](#getkeyat) oder [CRBTree::GetNext](#getnext) verwendet werden, um die Struktur zu durchlaufen und Werte abzurufen.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a>CRBTree::GetKeyAt

Rufen Sie diese Methode auf, um den Schlüssel von einer bestimmten Position in der Struktur abzurufen.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionswert.

### <a name="return-value"></a>Rückgabewert

Gibt den Schlüssel zurück, der an position *pos* in der Struktur gespeichert ist.

### <a name="remarks"></a>Bemerkungen

Wenn *pos* kein gültiger Positionswert ist, sind die Ergebnisse unvorhersehbar. In Debugbuilds tritt ein Assertionsfehler auf, wenn *pos* gleich NULL ist.

## <a name="crbtreegetnext"></a><a name="getnext"></a>CRBTree::GetNext

Rufen Sie diese Methode auf, um einen `CRBTree` Zeiger auf ein im Objekt gespeichertes Element abzurufen und die Position zum nächsten Element zu überweisen.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der von einem vorherigen Aufruf von Methoden wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::FindFirstKeyAfter](#findfirstkeyafter)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den nächsten [CPair-Wert](#cpair_class) in der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Der *Pos-Positionszähler* wird nach jedem Anruf aktualisiert. Wenn das abgerufene Element das letzte in der Struktur ist, wird *pos* auf NULL gesetzt.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a>CRBTree::GetNextAssoc

Rufen Sie diese Methode auf, um den Schlüssel und den Wert eines elements abzurufen, das in der Karte gespeichert ist, und die Position zum nächsten Element weiterzuleiten.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der von einem vorherigen Aufruf von Methoden wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::FindFirstKeyAfter](#findfirstkeyafter)zurückgegeben wird.

*key*<br/>
Vorlagenparameter, der den Typ des Baumschlüssels angibt.

*value*<br/>
Vorlagenparameter, der den Typ des Baumwerts angibt.

### <a name="remarks"></a>Bemerkungen

Der *Pos-Positionszähler* wird nach jedem Anruf aktualisiert. Wenn das abgerufene Element das letzte in der Struktur ist, wird *pos* auf NULL gesetzt.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a>CRBTree::GetNextKey

Rufen Sie diese Methode auf, um den Schlüssel eines Elements abzurufen, das in der Struktur gespeichert ist, und die Position zum nächsten Element zu übersteigen.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der von einem vorherigen Aufruf von Methoden wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::FindFirstKeyAfter](#findfirstkeyafter)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den nächsten Schlüssel in der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positionszähler *pos*. Wenn keine weiteren Einträge in der Struktur vorhanden sind, wird der Positionszähler auf NULL gesetzt.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a>CRBTree::GetNextValue

Rufen Sie diese Methode auf, um den Wert eines elements abzurufen, das in der Struktur gespeichert ist, und die Position an das nächste Element weiterzuleiten.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der von einem vorherigen Aufruf von Methoden wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::FindFirstKeyAfter](#findfirstkeyafter)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den nächsten Wert in der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positionszähler *pos*. Wenn keine weiteren Einträge in der Struktur vorhanden sind, wird der Positionszähler auf NULL gesetzt.

## <a name="crbtreegetprev"></a><a name="getprev"></a>CRBTree::GetPrev

Rufen Sie diese Methode auf, um einen `CRBTree` Zeiger auf ein im Objekt gespeichertes Element abzurufen und dann die Position auf das vorherige Element zu aktualisieren.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der von einem vorherigen Aufruf von Methoden wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::FindFirstKeyAfter](#findfirstkeyafter)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den vorherigen [CPair-Wert](#cpair_class) zurück, der in der Struktur gespeichert ist.

### <a name="remarks"></a>Bemerkungen

Aktualisiert den aktuellen Positionszähler *pos*. Wenn keine weiteren Einträge in der Struktur vorhanden sind, wird der Positionszähler auf NULL gesetzt.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a>CRBTree::GetTailPosition

Rufen Sie diese Methode auf, um den Positionswert für das Element am Ende der Struktur abzurufen.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Positionswert für das Element am Ende der Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Der zurückgegebene `GetTailPosition` Wert kann mit Methoden wie [CRBTree::GetKeyAt](#getkeyat) oder [CRBTree::GetPrev](#getprev) verwendet werden, um die Struktur zu durchlaufen und Werte abzurufen.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a>CRBTree::GetValueAt

Rufen Sie diese Methode auf, um den `CRBTree` wert, der an einer bestimmten Position im Objekt gespeichert ist, abzurufen.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der von einem vorherigen Aufruf von Methoden wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::FindFirstKeyAfter](#findfirstkeyafter)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf den Wert zurück, der an der angegebenen Position im `CRBTree` Objekt gespeichert ist.

## <a name="crbtreeisempty"></a><a name="isempty"></a>CRBTree::IsEmpty

Rufen Sie diese Methode auf, um ein leeres Strukturobjekt zu testen.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Struktur leer ist, andernfalls FALSE.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a>CRBTree::KINARGTYPE

Typ, der verwendet wird, wenn ein Schlüssel als Eingabeargument übergeben wird.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a>CRBTree::KOUTARGTYPE

Typ, der verwendet wird, wenn ein Schlüssel als Ausgabeargument zurückgegeben wird.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a>CRBTree::Alle entfernen

Rufen Sie diese Methode auf, um alle Elemente aus dem `CRBTree` Objekt zu entfernen.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Bemerkungen

Löscht das `CRBTree` Objekt und gibt den Speicher frei, der zum Speichern der Elemente verwendet wird.

## <a name="crbtreeremoveat"></a><a name="removeat"></a>CRBTree::RemoveAt

Rufen Sie diese Methode auf, um `CRBTree` das Element an der angegebenen Position im Objekt zu entfernen.

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der von einem vorherigen Aufruf von Methoden wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::FindFirstKeyAfter](#findfirstkeyafter)zurückgegeben wird.

### <a name="remarks"></a>Bemerkungen

Entfernt das Schlüssel-Wert-Paar, das an der angegebenen Position gespeichert ist. Der Speicher, der zum Speichern des Elements verwendet wird, wird freigegeben. Die POSITION, auf die von *pos* verwiesen wird, wird ungültig, und während die POSITION aller anderen Elemente in der Struktur gültig bleibt, behalten sie nicht unbedingt die gleiche Reihenfolge bei.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a>CRBTree::SetValueAt

Rufen Sie diese Methode auf, um den `CRBTree` an einer bestimmten Position im Objekt gespeicherten Wert zu ändern.

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionszähler, der von einem vorherigen Aufruf von Methoden wie [CRBTree::GetHeadPosition](#getheadposition) oder [CRBTree::FindFirstKeyAfter](#findfirstkeyafter)zurückgegeben wird.

*value*<br/>
Der Wert, der `CRBTree` dem Objekt hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Ändert das Wertelement, das an `CRBTree` der angegebenen Position im Objekt gespeichert ist.

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a>CRBTree::VINARGTYPE

Typ, der verwendet wird, wenn ein Wert als Eingabeargument übergeben wird.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a>CRBTree::VOUTARGTYPE

Typ, der verwendet wird, wenn ein Wert als Ausgabeargument übergeben wird.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
