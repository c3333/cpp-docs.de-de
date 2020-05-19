---
title: Ausdrucksanweisung (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: 736ed4fbbd9f87c675c0bb9566c6c31287e77917
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233708"
---
# <a name="expression-statement-c"></a>Ausdrucksanweisung (C)

Wenn eine Ausdrucksanweisung ausgeführt wird, wird der Ausdruck nach den in [Ausdrücke und Zuweisungen](../c-language/expressions-and-assignments.md) erläuterten Regeln ausgewertet.

## <a name="syntax"></a>Syntax

*expression-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ausdruck*<sub>opt</sub> **;**

Alle Nebeneffekte der Ausdrucksauswertung werden abgeschlossen, bevor die nächste Anweisung ausgeführt wird. Eine leere Ausdrucksanweisung wird als NULL-Anweisung bezeichnet. Weitere Informationen finden Sie unter [Die NULL-Anweisung](../c-language/null-statement-c.md).

Diese Beispiele veranschaulichen Ausdrucksanweisungen.

```C
x = ( y + 3 );            /* x is assigned the value of y + 3  */
x++;                      /* x is incremented                  */
x = y = 0;                /* Both x and y are initialized to 0 */
proc( arg1, arg2 );       /* Function call returning void      */
y = z = ( f( x ) + 3 );   /* A function-call expression        */
```

In der letzten Anweisung, dem Funktionsaufrufsausdruck, wird der Wert des Ausdrucks, der jeden beliebigen Wert, der von der Funktion zurückgegeben wird, um 3 erhöht und dann den beiden Variablen `y` und `z` zugewiesen.

## <a name="see-also"></a>Siehe auch

[Anweisungen](../c-language/statements-c.md)
