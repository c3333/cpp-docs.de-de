---
title: '&lt;hash_set&gt; Funktionen'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 1774b0b29c7750e716f1f56def5d29ac329abec0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845808"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt; Funktionen

[Wechsel](#swap)\
[swap (hash_multiset)](#swap_hash_multiset)

## <a name="swap"></a><a name="swap"></a> Wechsel

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Tauscht die Elemente zweier hash_sets aus.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die hash_set, die die auszutauschenden Elemente bereitstellen, oder die hash_set, deren Elemente mit denen des hash_set *Links*ausgetauscht werden sollen.

*linken*\
Die hash_set, deren Elemente mit denen des hash_set *Rechts*ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die `swap` Vorlagen Funktion ist ein Algorithmus, der sich auf die Container Klasse spezialisiert hash_set, um den Member-Funktions `left.` [Austausch](../standard-library/hash-set-class.md#swap)( `right` ) auszuführen. Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der Vorlagenfunktion

**Vorlage \<class T> void Swap (t&, t&),**

in der Algorithmusklasse funktioniert mittels Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberklasse [hash_set::swap](../standard-library/hash-set-class.md#swap) finden Sie ein Beispiel, das die Vorlagenversion `swap` verwendet.

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a> austauschen (hash_multiset)

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Tauscht die Elemente zweier hash_multisets aus.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die Hash_multiset, die die auszutauschenden Elemente bereitstellen, oder die Hash_multiset, deren Elemente mit denen des Hash_multiset *Links*ausgetauscht werden sollen.

*linken*\
Die Hash_multiset, deren Elemente mit denen des Hash_multiset *Rechts*ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die `swap` Vorlagen Funktion ist ein Algorithmus, der sich auf die Container Klasse spezialisiert hash_multiset, um den Member-Funktions `left.` [Austausch](../standard-library/hash-multiset-class.md#swap)( `right` ) auszuführen. Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der Vorlagenfunktion

**Vorlage \<class T> void Swap (t&, t&),**

in der Algorithmusklasse funktioniert mittels Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberklasse [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) finden Sie ein Beispiel, das die Vorlagenversion `swap` verwendet.

## <a name="see-also"></a>Weitere Informationen

[<hash_set>](../standard-library/hash-set.md)
