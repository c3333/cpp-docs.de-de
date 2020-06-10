---
title: _1-Objekt
ms.date: 11/04/2016
f1_keywords:
- _1
- std::_1
- functional/std::_1
helpviewer_keywords:
- _1 object
ms.assetid: 30c3c480-ff31-4708-94be-7d0d65f243c9
ms.openlocfilehash: 8fdb53ea03031f2bf1634a105275c72263ee20e3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620927"
---
# <a name="_1-object"></a>_1-Objekt

Platzhalter für austauschbare Argumente.

## <a name="syntax"></a>Syntax

```cpp
namespace placeholders {
    extern unspecified _1, _2, ... _M
} // namespace placeholders (within std)
```

## <a name="remarks"></a>Hinweise

Bei den Objekten `_1, _2, ... _M` handelt es sich um Platzhalter, die das erste, zweite,..., mth-Argument in einem Funktions aufrufeines Objekts festlegen, das von [Bind](functional-functions.md#bind)zurückgegeben wird. Sie verwenden `_N`, um anzugeben, wo das n-te Argument bei Auswertung des Bindungsausdrucks eingefügt werden soll.

In dieser Implementierung lautet der Wert von `M` 20.

## <a name="example"></a>Beispiel

```cpp
// std__functional_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
    {
    std::cout << x << "^2 == " << x * x << std::endl;
    }

void product(double x, double y)
    {
    std::cout << x << "*" << y << " == " << x * y << std::endl;
    }

int main()
    {
    double arg[] = {1, 2, 3};

    std::for_each(&arg[0], &arg[3], square);
    std::cout << std::endl;

    std::for_each(&arg[0], &arg[3], std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], &arg[3], std::bind(square, _1));

    return (0);
    }
```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```
