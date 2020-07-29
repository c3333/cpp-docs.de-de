---
title: is_default_constructible-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_default_constructible
helpviewer_keywords:
- is_default_constructible
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
ms.openlocfilehash: 6e31220fa6b15d958e94e82322467cd73e1c3a6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215698"
---
# <a name="is_default_constructible-class"></a>is_default_constructible-Klasse

Testet, ob ein Typ einen Standardkonstruktor besitzt.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist true, wenn der Typ *T* ein Klassentyp ist, der einen Standardkonstruktor aufweist; andernfalls false. Dies entspricht dem Prädikat `is_constructible<T>`. Der Typ *T* muss ein kompletter Typ, **`void`** , oder ein Array mit unbekannter Grenze sein.

## <a name="example"></a>Beispiel

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
