---
title: value_compare-Klasse
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: d64d51869ca8db1ed42e9d33691f59da4473d8d0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447567"
---
# <a name="value_compare-class"></a>value_compare-Klasse

Stellt ein Funktionsobjekt bereit, das die Elemente einer hash_map vergleichen kann, indem die Werte ihrer Schlüssel verglichen werden, um deren relative Reihenfolge in der hash_map zu bestimmen.

## <a name="syntax"></a>Syntax

```cpp
class value_compare
    : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
        const value_type& left,
        const value_type& right) const
    {
        return (comp(left.first, right.first));
    }

protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>Bemerkungen

Die Vergleichskriterien, die von Value_compare zwischen `value_types` ganzer Elemente in einem hash_map bereitgestellt werden, werden von einem Vergleich zwischen den Schlüsseln der entsprechenden Elemente durch die Erweiterung der Erweiterungs Klasse verursacht. Der Member-Funktions Operator verwendet die Objekt `comp` vom Typ `key_compare` der im von Value_compare bereitgestellten Funktions Objekt gespeichert ist, um die Sortierschlüssel Komponenten von zwei Elementen zu vergleichen.

Bei hash_sets und hash_multisets, bei denen es sich um einfache Container handelt, bei denen die Schlüsselwerte mit den Elementwerten übereinstimmen, stimmt value_compare mit `key_compare` überein; bei hash_maps und hash_multimaps nicht, da der Wert von Elementen vom Typ `pair` nicht mit dem Wert des Elementschlüssels identisch ist.

## <a name="example"></a>Beispiel

Im Beispiel für [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) wird verdeutlicht, wie value_compare deklariert und verwendet wird.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<hash_map >

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[binary_function Struct (binary_function-Struktur)](../standard-library/binary-function-struct.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
