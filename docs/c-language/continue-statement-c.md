---
title: continue-Anweisung (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: 3cf5d1c25b8edc70bd686ca26ad98b15b970383c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218909"
---
# <a name="continue-statement-c"></a>continue-Anweisung (C)

Die **`continue`** -Anweisung übergibt die Steuerung an die nächste Iteration der nächsten einschließenden **`do`** -, **`for`** - oder **`while`** -Anweisung, in der sie angezeigt wird, und umgeht alle verbleibenden Anweisungen im **`do`** -, **`for`** - oder **`while`** -Anweisungstext.

## <a name="syntax"></a>Syntax

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**continue ;**

Die nächste Iteration einer **`do`** -, **`for`** - oder **`while`** -Anweisung wird wie folgt bestimmt:

- Innerhalb einer **`do`** -Anweisung oder einer **`while`** -Anweisung wird die nächste Iteration mit einer erneuten Auswertung des Ausdrucks der **`do`** -Anweisung oder der **`while`** -Anweisung begonnen.

- Eine **`continue`** -Anweisung in einer **`for`** -Anweisung führt dazu, dass der Schleifenausdruck der **`for`** -Anweisung ausgewertet wird. Anschließend wertet der Compiler den bedingten Ausdruck neu aus und beendet oder durchläuft den Anweisungstext je nach Ergebnis. Weitere Informationen zur **`for`** -Anweisung und den Nonterminals finden Sie in der [for-Anweisung](../c-language/for-statement-c.md).

In diesem Beispiel wird die **`continue`** -Anweisung veranschaulicht:

```
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

In diesem Beispiel wird der Anweisungstext ausgeführt, während `i` größer als 0 ist. Zunächst wird `f(i)` zu `x` zugewiesen. Wenn `x` gleich 1 ist, wird die **`continue`** -Anweisung ausgeführt. Die übrigen Anweisungen im Text werden ignoriert, und die Ausführung wird am Anfang der Schleife mit der Auswertung des Schleifentests fortgesetzt.

## <a name="see-also"></a>Siehe auch

[continue-Anweisung](../cpp/continue-statement-cpp.md)
