---
title: CRBMap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: 9e367ccc875eedf63e4f47018598662af2dfcf7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331398"
---
# <a name="crbmap-class"></a>CRBMap-Klasse

Diese Klasse stellt eine Mapping-Struktur dar, die einen rot-schwarzen Binärbaum verwendet.

## <a name="syntax"></a>Syntax

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMap::CRBMap](#crbmap)|Der Konstruktor.|
|[CRBMap::-CRBMap](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|Rufen Sie diese Methode auf, `CRBMap` um Schlüssel oder Werte im Objekt zu suchen.|
|[CRBMap::RemoveKey](#removekey)|Rufen Sie diese Methode auf, um ein Element aus dem `CRBMap` Objekt zu entfernen, wenn der Schlüssel angegeben wird.|
|[CRBMap::SetAt](#setat)|Rufen Sie diese Methode auf, um ein Elementpaar in die Karte einzufügen.|

## <a name="remarks"></a>Bemerkungen

`CRBMap`bietet Unterstützung für ein Zuordnungsarray eines beliebigen Typs, das ein geordnetes Array von Schlüsselelementen und den zugehörigen Werten verwaltet. Jeder Schlüssel kann nur einen zugeordneten Wert haben. Elemente (bestehend aus einem Schlüssel und einem Wert) werden in einer binären Baumstruktur mit der [CRBMap::SetAt-Methode](#setat) gespeichert. Elemente können mit der [CRBMap::RemoveKey-Methode](#removekey) entfernt werden, die das Element mit dem angegebenen Schlüsselwert löscht.

Das Durchlaufen der Struktur wird mit Methoden wie [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)und [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue)ermöglicht.

Die *Parameter KTraits* und *VTraits* sind Merkmalsklassen, die zusätzlichen Code enthalten, der zum Kopieren oder Verschieben von Elementen erforderlich ist.

`CRBMap`wird von [CRBTree](../../atl/reference/crbtree-class.md)abgeleitet, das einen binären Baum mithilfe des Rot-Schwarz-Algorithmus implementiert. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) ist eine Variante, die mehrere Werte für jeden Schlüssel zulässt. Es ist auch `CRBTree`von abgeleitet und `CRBMap`teilt daher viele Features mit .

Eine Alternative `CRBMap` zu `CRBMultiMap` beiden und wird von der [CAtlMap-Klasse](../../atl/reference/catlmap-class.md) angeboten. Wenn nur eine kleine Anzahl von Elementen gespeichert werden muss, sollten Sie stattdessen die [CSimpleMap-Klasse](../../atl/reference/csimplemap-class.md) verwenden.

Eine vollständigere Erläuterung der verschiedenen Auflistungsklassen und ihrer Features und Leistungsmerkmale finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="crbmapcrbmap"></a><a name="crbmap"></a>CRBMap::CRBMap

Der Konstruktor.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Die Blockgröße.

### <a name="remarks"></a>Bemerkungen

Der Parameter *nBlockSize* ist ein Maß für die Speichermenge, die zugewiesen wird, wenn ein neues Element erforderlich ist. Größere Blockgrößen reduzieren Aufrufe von Speicherzuweisungsroutinen, verwenden jedoch mehr Ressourcen. Der Standardwert weist Speicherplatz für 10 Elemente gleichzeitig zu.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a>CRBMap::-CRBMap

Der Destruktor.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

## <a name="crbmaplookup"></a><a name="lookup"></a>CRBMap::Lookup

Rufen Sie diese Methode auf, `CRBMap` um Schlüssel oder Werte im Objekt zu suchen.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Gibt den Schlüssel an, der das zu sanende Element identifiziert.

*value*<br/>
Variable, die den nachobenden Wert empfängt.

### <a name="return-value"></a>Rückgabewert

Die erste Form der Methode gibt true zurück, wenn der Schlüssel gefunden wird, andernfalls false. Das zweite und dritte Formular geben einen Zeiger auf ein [CPair](crbtree-class.md#cpair_class)zurück.

### <a name="remarks"></a>Bemerkungen

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a>CRBMap::RemoveKey

Rufen Sie diese Methode auf, um ein Element aus dem `CRBMap` Objekt zu entfernen, wenn der Schlüssel angegeben wird.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel, der dem Elementpaar entspricht, das Sie entfernen möchten.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn der Schlüssel gefunden und entfernt wird, false bei Einem Fehler.

### <a name="remarks"></a>Bemerkungen

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a>CRBMap::SetAt

Rufen Sie diese Methode auf, um ein Elementpaar in die Karte einzufügen.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselwert, der `CRBMap` dem Objekt hinzugefügt werden soll.

*value*<br/>
Der Wert, der `CRBMap` dem Objekt hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt die Position des Schlüssel-Wert-Element-Paares im `CRBMap` Objekt zurück.

### <a name="remarks"></a>Bemerkungen

`SetAt`ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird. Wenn der Schlüssel nicht gefunden wird, wird ein neues Schlüssel-Wert-Paar erstellt.

Informationen zu den anderen verfügbaren Methoden finden Sie in der Dokumentation für die Basisklasse [CRBTree.](../../atl/reference/crbtree-class.md)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Siehe auch

[CRBTree-Klasse](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap-Klasse](../../atl/reference/catlmap-class.md)<br/>
[CRBMultiMap-Klasse](../../atl/reference/crbmultimap-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
