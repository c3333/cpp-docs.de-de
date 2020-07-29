---
title: is_void-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_void
helpviewer_keywords:
- is_void class
- is_void
ms.assetid: 99b0de3b-1b38-4949-b053-080e5363174e
ms.openlocfilehash: 49fef050393f7196fe26aa172ac02792ae5c717e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212227"
---
# <a name="is_void-class"></a>is_void-Klasse

Testet, ob der Typ ein void-Typ ist.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
struct is_void;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn der Typ " *T* " **`void`** oder eine CV-qualifizierte Form von ist; **`void`** andernfalls "false".

## <a name="example"></a>Beispiel

```cpp
// std__type_traits__is_void.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_void<trivial> == " << std::boolalpha
        << std::is_void<trivial>::value << std::endl;
    std::cout << "is_void<void()> == " << std::boolalpha
        << std::is_void<void()>::value << std::endl;
    std::cout << "is_void<void> == " << std::boolalpha
        << std::is_void<void>::value << std::endl;

    return (0);
    }
```

```Output
is_void<trivial> == false
is_void<void()> == false
is_void<void> == true
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
