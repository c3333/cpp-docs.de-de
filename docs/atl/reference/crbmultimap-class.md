---
title: CRBMultiMap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 1e36bc267b3a539d2d1d4bf370b9cdc33828c760
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331422"
---
# <a name="crbmultimap-class"></a>CRBMultiMap-Klasse

Diese Klasse stellt eine Zuordnungsstruktur dar, die es ermöglicht, dass jeder Schlüssel mit einem Rot-Schwarzen-Binärbaum mit mehr als einem Wert verknüpft werden kann.

## <a name="syntax"></a>Syntax

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
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

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Der Konstruktor.|
|[CRBMultiMap::-CRBMultiMap](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Rufen Sie diese Methode auf, um die Position des ersten Elements mit einem bestimmten Schlüssel zu finden.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Rufen Sie diese Methode auf, um den Wert abzurufen, der einem bestimmten Schlüssel zugeordnet ist, und aktualisieren Sie den Positionswert.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Rufen Sie diese Methode auf, um das Element abzurufen, das einem bestimmten Schlüssel zugeordnet ist, und aktualisieren Sie den Positionswert.|
|[CRBMultiMap::Einfügen](#insert)|Rufen Sie diese Methode auf, um ein Elementpaar in die Karte einzufügen.|
|[CRBMultiMap::RemoveKey](#removekey)|Rufen Sie diese Methode auf, um alle Schlüssel-/Wertelemente für einen bestimmten Schlüssel zu entfernen.|

## <a name="remarks"></a>Bemerkungen

`CRBMultiMap`bietet Unterstützung für ein Zuordnungsarray eines beliebigen Typs, das ein geordnetes Array von Schlüsselelementen und Werten verwaltet. Im Gegensatz zur [CRBMap-Klasse](../../atl/reference/crbmap-class.md) kann jeder Schlüssel mit mehr als einem Wert verknüpft werden.

Elemente (bestehend aus einem Schlüssel und einem Wert) werden in einer binären Baumstruktur mit der [CRBMultiMap::Insert-Methode](#insert) gespeichert. Elemente können mit der [CRBMultiMap::RemoveKey-Methode](#removekey) entfernt werden, die alle Elemente löscht, die mit dem angegebenen Schlüssel übereinstimmen.

Das Durchlaufen der Struktur wird mit Methoden wie [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)und [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)ermöglicht. Der Zugriff auf die potenziell mehreren Werte pro Schlüssel ist mit den Methoden [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)und [CRBMultiMap::GetNextWithKey](#getnextwithkey) möglich. Im Beispiel für [CRBMultiMap::CRBMultiMap](#crbmultimap) finden Sie eine Darstellung dieses Beispiels in der Praxis.

Die *Parameter KTraits* und *VTraits* sind Merkmalsklassen, die zusätzlichen Code enthalten, der zum Kopieren oder Verschieben von Elementen erforderlich ist.

`CRBMultiMap`wird von [CRBTree](../../atl/reference/crbtree-class.md)abgeleitet, das einen binären Baum mithilfe des Rot-Schwarz-Algorithmus implementiert. Eine Alternative `CRBMultiMap` `CRBMap` zur [CAtlMap-Klasse](../../atl/reference/catlmap-class.md) bietet und wird angeboten. Wenn nur eine kleine Anzahl von Elementen gespeichert werden muss, sollten Sie stattdessen die [CSimpleMap-Klasse](../../atl/reference/csimplemap-class.md) verwenden.

Eine vollständigere Erläuterung der verschiedenen Auflistungsklassen und ihrer Features und Leistungsmerkmale finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a>CRBMultiMap::CRBMultiMap

Der Konstruktor.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Die Blockgröße.

### <a name="remarks"></a>Bemerkungen

Der Parameter *nBlockSize* ist ein Maß für die Speichermenge, die zugewiesen wird, wenn ein neues Element erforderlich ist. Größere Blockgrößen reduzieren Aufrufe von Speicherzuweisungsroutinen, verwenden jedoch mehr Ressourcen. Der Standardwert weist Speicherplatz für 10 Elemente gleichzeitig zu.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a>CRBMultiMap::-CRBMultiMap

Der Destruktor.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a>CRBMultiMap::FindFirstWithKey

Rufen Sie diese Methode auf, um die Position des ersten Elements mit einem bestimmten Schlüssel zu finden.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Schlüssel an, der das zu findende Element identifiziert.

### <a name="return-value"></a>Rückgabewert

Gibt die POSITION des ersten Schlüssel-/Wertelements zurück, wenn der Schlüssel gefunden wird, andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Ein Schlüssel `CRBMultiMap` im kann über einen oder mehrere zugeordnete Werte verfügen. Diese Methode stellt den Positionswert des ersten Werts bereit (der in der Tat der einzige Wert sein kann), der diesem bestimmten Schlüssel zugeordnet ist. Der zurückgegebene Positionswert kann dann mit [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) oder [CRBMultiMap::GetNextWithKey](#getnextwithkey) verwendet werden, um den Wert zu erhalten und die Position zu aktualisieren.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

Siehe Beispiel für [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a>CRBMultiMap::GetNextValueWithKey

Rufen Sie diese Methode auf, um den Wert abzurufen, der einem bestimmten Schlüssel zugeordnet ist, und den Positionswert zu aktualisieren.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionswert, der entweder mit einem Aufruf von [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) oder [CRBMultiMap::GetNextWithKey](#getnextwithkey)oder einem vorherigen Aufruf von `GetNextValueWithKey`abgerufen wurde.

*key*<br/>
Gibt den Schlüssel an, der das zu findende Element identifiziert.

### <a name="return-value"></a>Rückgabewert

Gibt das Elementpaar zurück, das dem angegebenen Schlüssel zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Der Positionswert wird aktualisiert, um auf den nächsten Wert zu verweisen, der dem Schlüssel zugeordnet ist. Wenn keine weiteren Werte vorhanden sind, wird der Positionswert auf NULL gesetzt.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

Siehe Beispiel für [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a>CRBMultiMap::GetNextWithKey

Rufen Sie diese Methode auf, um das Element abzurufen, das einem bestimmten Schlüssel zugeordnet ist, und den Positionswert zu aktualisieren.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Der Positionswert, der entweder mit einem Aufruf von [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) oder [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)oder einem vorherigen Aufruf von `GetNextWithKey`abgerufen wurde.

*key*<br/>
Gibt den Schlüssel an, der das zu findende Element identifiziert.

### <a name="return-value"></a>Rückgabewert

Gibt das nächste [CRBTree::CPair Class-Element](crbtree-class.md#cpair_class) zurück, das dem angegebenen Schlüssel zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Der Positionswert wird aktualisiert, um auf den nächsten Wert zu verweisen, der dem Schlüssel zugeordnet ist. Wenn keine weiteren Werte vorhanden sind, wird der Positionswert auf NULL gesetzt.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

## <a name="crbmultimapinsert"></a><a name="insert"></a>CRBMultiMap::Einfügen

Rufen Sie diese Methode auf, um ein Elementpaar in die Karte einzufügen.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselwert, der `CRBMultiMap` dem Objekt hinzugefügt werden soll.

*value*<br/>
Der Wert, der `CRBMultiMap` dem Objekt hinzugefügt werden soll und dem *Schlüssel*zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Gibt die Position des Schlüssel-Wert-Element-Paares im `CRBMultiMap` Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

Siehe Beispiel für [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapremovekey"></a><a name="removekey"></a>CRBMultiMap::RemoveKey

Rufen Sie diese Methode auf, um alle Schlüssel-/Wertelemente für einen bestimmten Schlüssel zu entfernen.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Schlüssel an, der die zu löschenden Elemente identifiziert.

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Werte zurück, die dem angegebenen Schlüssel zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

`RemoveKey`löscht alle Schlüssel-/Wertelemente, die über einen Schlüssel verfügen, der mit dem *Schlüssel*übereinstimmt.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

Siehe Beispiel für [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Siehe auch

[CRBTree-Klasse](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap-Klasse](../../atl/reference/catlmap-class.md)<br/>
[CRBMap-Klasse](../../atl/reference/crbmap-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
