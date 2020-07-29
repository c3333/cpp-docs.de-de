---
title: is_pointer-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pointer
helpviewer_keywords:
- is_pointer class
- is_pointer
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
ms.openlocfilehash: 3429875f53d65de0161c4d6f87fde7a335bb369e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222341"
---
# <a name="is_pointer-class"></a>is_pointer-Klasse

Testet, ob der Typ ein Zeiger ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
struct is_pointer;
```

### <a name="parameters"></a>Parameter

*Genossenschaft*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn die *typanty* ein Zeiger auf **`void`** , ein Zeiger auf ein Objekt oder ein Zeiger auf eine Funktion oder ein- `cv-qualified` Formular von einem davon ist, andernfalls "false". Beachten Sie, dass `is_pointer` false enthält, wenn *Ty* ein Zeiger auf einen Member ist, oder ein Zeiger auf eine Member-Funktion.

## <a name="example"></a>Beispiel

```cpp
// std__type_traits__is_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_pointer<trivial> == " << std::boolalpha
        << std::is_pointer<trivial>::value << std::endl;
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha
        << std::is_pointer<int trivial::*>::value << std::endl;
    std::cout << "is_pointer<trivial *> == " << std::boolalpha
        << std::is_pointer<trivial *>::value << std::endl;
    std::cout << "is_pointer<int> == " << std::boolalpha
        << std::is_pointer<int>::value << std::endl;
    std::cout << "is_pointer<int *> == " << std::boolalpha
        << std::is_pointer<int *>::value << std::endl;

    return (0);
    }
```

```Output
is_pointer<trivial> == false
is_pointer<int trivial::*> == false
is_pointer<trivial *> == true
is_pointer<int> == false
is_pointer<int *> == true
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)\
[is_member_pointer-Klasse](../standard-library/is-member-pointer-class.md)\
[is_reference-Klasse](../standard-library/is-reference-class.md)
