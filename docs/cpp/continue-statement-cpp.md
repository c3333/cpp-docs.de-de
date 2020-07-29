---
title: continue-Anweisung (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 55a81338f1a0f9036a6d42c4bac7c99489c18d64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228998"
---
# <a name="continue-statement-c"></a>continue-Anweisung (C++)

Erzwingt die Übertragung der Steuerung an den steuernden Ausdruck der kleinsten einschließenden [DO](../cpp/do-while-statement-cpp.md)-, [for](../cpp/for-statement-cpp.md)-oder [while](../cpp/while-statement-cpp.md) -Schleife.

## <a name="syntax"></a>Syntax

```
continue;
```

## <a name="remarks"></a>Bemerkungen

Alle verbleibenden Anweisungen in der aktuellen Iteration werden nicht ausgeführt. Die nächste Iteration der Schleife wird wie folgt bestimmt:

- In einer- **`do`** oder- **`while`** Schleife wird die nächste Iterations Anweisung gestartet, indem der steuernde Ausdruck der-oder-Anweisung erneut ausgewertet wird **`do`** **`while`** .

- In einer- **`for`** Schleife (unter Verwendung der-Syntax `for( <init-expr> ; <cond-expr> ; <loop-expr> )` ) wird die- `<loop-expr>` Klausel ausgeführt. Anschließend wird die `<cond-expr>`-Klausel neu ausgewertet und, je nach Ergebnis, wird die Schleife entweder beendet oder es tritt eine andere Iteration auf.

Das folgende Beispiel zeigt, wie die **`continue`** -Anweisung verwendet werden kann, um Code Abschnitte zu umgehen und die nächste Iterations Schleife zu beginnen.

## <a name="example"></a>Beispiel

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>Siehe auch

[Sprunganweisungen](../cpp/jump-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
