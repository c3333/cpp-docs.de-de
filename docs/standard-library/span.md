---
title: '&lt;Spanne&gt;'
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: ebd0a30c677ea44f95e64e2d2ba010bc99cb412b
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226313"
---
# <a name="ltspangt"></a>&lt;Spanne&gt;

Eine `span` ist eine Ansicht über einer zusammenhängenden Sequenz von-Objekten. Sie ermöglicht den schnellen und sicheren Zugriff. Anders als `vector` oder `array` werden die Elemente, auf die Sie Zugriff bietet, nicht "besitzen". 

Ausführliche Informationen finden Sie unter [span class](span-class.md) . Im folgenden finden Sie ein Beispiel dafür, wie eine Spanne verwendet werden kann:

```cpp
#include <span>
#include <iostream>

void Show(std::span<int> someValues)
{
    // show values in reverse
    for (auto rIt = someValues.rbegin(); rIt != someValues.rend(); ++rIt)
    {
        std::cout << *rIt;
    }

    // show a subspan
    for (auto& i : someValues.subspan(1, 2))
    {
        std::cout << i;
    }
}

int main()
{
    int numbers[]{ 0,1,2,3,4 };
    Show(numbers); // note conversion from array to span
}
```

## <a name="requirements"></a>Anforderungen

**Header:**\<span>

**Namespace:** std

**Compileroption:** /Std: c + + Latest

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|||
|-|:-|
|[Spanne](span-class.md)| Stellt eine Ansicht für eine zusammenhängende Sequenz von-Objekten bereit. |

### <a name="operators"></a>Operatoren

|||
|-|:-|
|[Operator =](span-class.md#op_eq)| Spannen Zuweisung |
|[KOM\[\]](span-class.md#op_at)| Elementzugriff |

### <a name="functions"></a>Functions

|||
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| Die zugrunde liegenden schreibgeschützten Bytes der Spanne werden angezeigt. |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | Die zugrunde liegenden Bytes der Spanne werden angezeigt. |

### <a name="constants"></a>Konstanten

|||
|-|:-|
| **dynamic_extent** | Gibt an, dass die Spannen Größe zur Laufzeit und nicht zur Kompilierzeit bestimmt wird. Wenn die Anzahl der Elemente in der Spanne zum Zeitpunkt der Kompilierung bekannt ist, wird Sie als `Extent` Vorlagen Parameter angegeben. Wenn die Zahl bis zur Laufzeit nicht bekannt ist, geben Sie `dynamic_extent` stattdessen an. |

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
