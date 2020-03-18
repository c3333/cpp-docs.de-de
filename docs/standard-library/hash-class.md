---
title: hash-Klasse
ms.date: 11/04/2016
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
helpviewer_keywords:
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
ms.openlocfilehash: aa51e56197ba79afbe2bd2597596c52b23a4f65b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446580"
---
# <a name="hash-class"></a>hash-Klasse

Berechnet den Hashcode für einen Wert.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
struct hash {
    size_t operator()(Ty val) const;
};
```

## <a name="remarks"></a>Bemerkungen

Das Funktionsobjekt definiert eine Hashfunktion, die geeignet ist, Werte des *Ty*-Typs einer Verteilung von Indexwerten zuzuordnen. Der Member `operator()` gibt einen Hashcode für *Val*zurück, der für die Verwendung mit Klassen Vorlagen `unordered_map`, `unordered_multimap`, `unordered_set`und `unordered_multiset`geeignet ist. Die Standardbibliothek bietet Spezialisierungen für grundlegende Typen: *Ty* kann ein beliebiger skalarer Typ sein, einschließlich Zeigertypen und Enumerationstypen. Zusätzlich gibt es Spezialisierungen für die Bibliothekstypen `string`, `wstring`, `u16string`, `u32string`, `string_view`, `wstring_view`, `u16string_view`, `u32string_view`, `bitset`, `error_code`, `error_condition`, `optional`, `shared_ptr`, `thread`, `type_index`, `unique_ptr`, `variant` und `vector<bool>`.

## <a name="example"></a>Beispiel

```cpp
// std__functional__hash.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <unordered_set>

int main()
    {
    std::unordered_set<int, std::hash<int> > c0;
    c0.insert(3);
    std::cout << *c0.find(3) << std::endl;

    return (0);
    }
```

```Output
3
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<funktionale >

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<unordered_map>](../standard-library/unordered-map.md)\
[unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md)\
[unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md)\
[<unordered_set>](../standard-library/unordered-set.md)
