---
title: is_class-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_class
helpviewer_keywords:
- is_class class
- is_class
ms.assetid: 96fc34a3-a81b-4ec6-b7fb-baafde1a0f4e
ms.openlocfilehash: 4122ad2b4adbd0ed290f26428560c569b3754d7d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222445"
---
# <a name="is_class-class"></a>is_class-Klasse

Testet, ob der Typ eine Klasse ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
struct is_class;
```

### <a name="parameters"></a>Parameter

*Genossenschaft*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn die *typanty* ein Typ ist, der als **`class`** oder oder in einem-Formular definiert ist **`struct`** `cv-qualified` , andernfalls "false".

## <a name="example"></a>Beispiel

```cpp
// std__type_traits__is_class.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_class<trivial> == " << std::boolalpha
        << std::is_class<trivial>::value << std::endl;
    std::cout << "is_class<int> == " << std::boolalpha
        << std::is_class<int>::value << std::endl;

    return (0);
    }
```

```Output
is_class<trivial> == true
is_class<int> == false
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)\
[is_compound-Klasse](../standard-library/is-compound-class.md)\
[is_union-Klasse](../standard-library/is-union-class.md)
