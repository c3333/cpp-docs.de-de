---
title: '&lt;functional&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: b396e5c692129821c0deb9aef9469a5c54e600b0
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424764"
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt;-Operatoren

## <a name="op_eq_eq"></a>Operator = =

Testet, ob das aufrufbare Objekt leer ist.

```cpp
template <class Fty>
    bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parameter

*Raffinierte*\
Der zu umschließende Funktionstyp.

*f* -\
Das Funktionsobjekt

\ für den *NPC*
Ein Nullzeiger.

### <a name="remarks"></a>Hinweise

Beide Operatoren nehmen ein Argument, das einen Verweis auf ein `function`-Objekt darstellt, und ein Argument, das eine Nullzeigerkonstante ist. Beide geben nur dann true zurück, wenn das `function`-Objekt ist leer.

### <a name="example"></a>Beispiel

```cpp
// std__functional__operator_eq.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
```

```Output
empty == true
empty == false
```

## <a name="op_neq"></a>Operator! =

Testet, ob das aufrufbare Objekt nicht leer ist.

```cpp
template <class Fty>
    bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parameter

*Raffinierte*\
Der zu umschließende Funktionstyp.

*f* -\
Das Funktionsobjekt

\ für den *NPC*
Ein Nullzeiger.

### <a name="remarks"></a>Hinweise

Beide Operatoren nehmen ein Argument, das einen Verweis auf ein `function`-Objekt darstellt, und ein Argument, das eine Nullzeigerkonstante ist. Beide geben nur dann TRUE zurück, wenn das `function`-Objekt nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// std__functional__operator_ne.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == "
        << (fn0 != 0) << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == "
        << (fn1 != 0) << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```
