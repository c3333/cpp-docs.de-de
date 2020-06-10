---
title: add_volatile-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: 1a4ad8a86b88cdfa98f043bb49ba6eeff8b090c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619203"
---
# <a name="add_volatile-class"></a>add_volatile-Klasse

Wandelt einen **flüchtigen** Typ aus dem angegebenen Typ um.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der zu ändernde Typ.

## <a name="remarks"></a>Hinweise

Eine Instanz von `add_volatile<T>` verfügt über einen Member **typedef** , der `type` *t* ist, wenn *t* ein Verweis, eine Funktion oder ein flüchtiger qualifizierter Typ ist; andernfalls **flüchtig** *t*. Der Alias `add_volatile_t` ist eine Verknüpfung für den Zugriff auf die **typedef** -Member `type` .

## <a name="example"></a>Beispiel

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_volatile_t<int> *p = (volatile int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_volatile<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_volatile<int> == int
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[<type_traits>](type-traits.md)\
[remove_volatile-Klasse](remove-volatile-class.md)
