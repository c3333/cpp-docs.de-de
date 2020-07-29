---
title: is_compound-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_compound
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
ms.openlocfilehash: ae2e3c66b3abf22bbefbcb0fcd3292f0a3dbdbe2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215711"
---
# <a name="is_compound-class"></a>is_compound-Klasse

Testet, ob der angegebene Typ nicht grundlegend ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>Parameter

*Genossenschaft*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats enthält, **`false`** Wenn der Typ der *Ty* ein grundlegender Typ ist (d. h., wenn [is_fundamental](../standard-library/is-fundamental-class.md) \<Ty> enthält **`true`** ); andernfalls enthält er **`true`** . Folglich enthält das Prädikat, **`true`** Wenn *Ty* ein Arraytyp, ein Funktionstyp, ein Zeiger auf **`void`** oder ein Objekt oder eine Funktion, ein Verweis, eine Klasse, eine Union, eine Enumeration oder ein Zeiger auf ein nicht statisches Klassenmember oder eine *CV-Qualified-* Form eines dieser Elemente ist.

## <a name="example"></a>Beispiel

```cpp
// std__type_traits__is_compound.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_compound<trivial> == " << std::boolalpha
        << std::is_compound<trivial>::value << std::endl;
    std::cout << "is_compound<int[]> == " << std::boolalpha
        << std::is_compound<int[]>::value << std::endl;
    std::cout << "is_compound<int()> == " << std::boolalpha
        << std::is_compound<int()>::value << std::endl;
    std::cout << "is_compound<int&> == " << std::boolalpha
        << std::is_compound<int&>::value << std::endl;
    std::cout << "is_compound<void *> == " << std::boolalpha
        << std::is_compound<void *>::value << std::endl;
    std::cout << "is_compound<int> == " << std::boolalpha
        << std::is_compound<int>::value << std::endl;

    return (0);
    }
```

```Output
is_compound<trivial> == true
is_compound<int[]> == true
is_compound<int()> == true
is_compound<int&> == true
is_compound<void *> == true
is_compound<int> == false
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)\
[is_class-Klasse](../standard-library/is-class-class.md)
