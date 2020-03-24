---
title: Compilerwarnung (Stufe 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: cf0c6e9e2c33887082f945f3f2200d808ac13cd2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174257"
---
# <a name="compiler-warning-level-2-c4146"></a>Compilerwarnung (Stufe 2) C4146

Unärer Minus-Operator, der auf nicht signierten Typ angewendet wird, Ergebnis ist noch nicht signiert

Nicht signierte Typen können nur nicht negative Werte enthalten, daher ist die unäre Minuszeichen (Negation) in der Regel nicht sinnvoll, wenn Sie auf einen Typ ohne Vorzeichen angewendet werden. Sowohl der Operand als auch das Ergebnis sind nicht negativ.

Dies geschieht praktisch, wenn der Programmierer versucht, den minimalen ganzzahligen Wert (-2147483648) auszudrücken. Dieser Wert kann nicht als-2147483648 geschrieben werden, da der Ausdruck in zwei Phasen verarbeitet wird:

1. Die Zahl 2147483648 wird ausgewertet. Da der Wert größer als der maximale ganzzahlige Wert 2147483647 ist, ist der Typ von 2147483648 nicht [int](../../c-language/integer-types.md), sondern `unsigned int`.

1. Unäres Minus wird auf den Wert mit einem nicht signierten Ergebnis angewendet, das ebenfalls 2147483648 ist.

Der nicht signierte Typ des Ergebnisses kann zu unerwartetem Verhalten führen. Wenn das Ergebnis in einem Vergleich verwendet wird, kann ein nicht signierter Vergleich verwendet werden, z. b. wenn der andere Operand eine `int`ist. Dadurch wird erläutert, warum das unten aufgeführte Beispielprogramm nur eine Zeile ausgibt.

Die erwartete zweite Zeile, `1 is greater than the most negative int`, wird nicht gedruckt, weil `((unsigned int)1) > 2147483648` false ist.

Sie können C4146 vermeiden, indem Sie INT_MIN aus Limits. h verwenden, das den Typ " **int int**" aufweist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4146 generiert:

```cpp
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```
