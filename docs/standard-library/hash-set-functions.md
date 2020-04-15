---
title: '&lt;hash_set&gt; Funktionen'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: d7df6b3c5dc0d0d493d17b3e9995bc4758ffd6d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370589"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt; Funktionen

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a><a name="swap"></a>Swap

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
Die hash_set, die die zu tauschenden Elemente oder die hash_set, deren Elemente mit denen der hash_set *links*ausgetauscht werden sollen.

*Links*\
Die hash_set, deren Elemente mit denen des hash_set *Rechten*ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die `swap` Vorlagenfunktion ist ein Algorithmus, der auf die `left.`Containerklasse hash_set zum Ausführen des Memberfunktions-Swaps ( [swap](../standard-library/hash-set-class.md#swap)`right`) spezialisiert ist. Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der Vorlagenfunktion

**template \<class T> void swap(T&, T&),**

in der Algorithmusklasse funktioniert mittels Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberklasse [hash_set::swap](../standard-library/hash-set-class.md#swap) finden Sie ein Beispiel, das die Vorlagenversion `swap` verwendet.

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a>Swap (hash_multiset)

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Tauscht die Elemente zweier hash_multisets aus.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die hash_multiset, die die zu tauschenden Elemente oder die hash_multiset, deren Elemente mit denen der hash_multiset *links*ausgetauscht werden sollen.

*Links*\
Die hash_multiset, deren Elemente mit denen des hash_multiset *Rechten*ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die `swap` Vorlagenfunktion ist ein Algorithmus, der auf die `left.`Containerklasse hash_multiset zum Ausführen des Memberfunktions-Swaps ( [swap](../standard-library/hash-multiset-class.md#swap)`right`) spezialisiert ist. Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der Vorlagenfunktion

**template \<class T> void swap(T&, T&),**

in der Algorithmusklasse funktioniert mittels Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberklasse [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) finden Sie ein Beispiel, das die Vorlagenversion `swap` verwendet.

## <a name="see-also"></a>Siehe auch

[<hash_set><](../standard-library/hash-set.md)
