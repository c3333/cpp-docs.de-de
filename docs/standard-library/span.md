---
title: '&lt;Spanne&gt;'
description: API-Referenz für den STL-Namespace (Standard Template Library), der eine vereinfachte Ansicht für eine zusammenhängende Sequenz von Objekten bereitstellt.
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: f4c6b141dfea6464e58d06e221a39a693469d31c
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039871"
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

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<span>

**Namespace:** std

**Compileroption:** [/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md)

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|name|BESCHREIBUNG|
|-|:-|
|[Spanne](span-class.md)| Stellt eine Ansicht für eine zusammenhängende Sequenz von-Objekten bereit. |

### <a name="operators"></a>Operatoren

|Name|BESCHREIBUNG|
|-|:-|
|[Operator =](span-class.md#op_eq)| Spannen Zuweisung |
|[KOM\[\]](span-class.md#op_at)| Elementzugriff |

### <a name="functions"></a>Functions

|Name|BESCHREIBUNG|
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| Die zugrunde liegenden schreibgeschützten Bytes der Spanne werden angezeigt. |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | Die zugrunde liegenden Bytes der Spanne werden angezeigt. |

### <a name="constants"></a>Konstanten

|Name|BESCHREIBUNG|
|-|:-|
| **dynamic_extent** | Gibt an, dass die Spannen Größe zur Laufzeit und nicht zur Kompilierzeit bestimmt wird. Wenn die Anzahl der Elemente in der Spanne zum Zeitpunkt der Kompilierung bekannt ist, wird Sie als `Extent` Vorlagen Parameter angegeben. Wenn die Zahl bis zur Laufzeit nicht bekannt ist, geben Sie `dynamic_extent` stattdessen an. |

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
