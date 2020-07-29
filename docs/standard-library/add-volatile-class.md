---
title: add_volatile-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: e8c213a116ff7a7d4218179f0e944ac4f84a75e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230271"
---
# <a name="add_volatile-class"></a>add_volatile-Klasse

Wandelt einen **`volatile`** Typ aus dem angegebenen Typ um.

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

## <a name="remarks"></a>Bemerkungen

Eine Instanz von `add_volatile<T>` verfügt über einen Member, der t ist, **`typedef`** `type` Wenn *t* ein Verweis, eine Funktion oder ein flüchtiger qualifizierter Typ ist; andernfalls *T* **`volatile`** *T*. Der Alias `add_volatile_t` ist eine Verknüpfung für den Zugriff auf den Member **`typedef`** `type` .

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

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](type-traits.md)\
[remove_volatile-Klasse](remove-volatile-class.md)
