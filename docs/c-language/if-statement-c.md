---
title: if-Anweisung (C)
ms.date: 11/04/2016
f1_keywords:
- else
- if
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
ms.openlocfilehash: 6fe92d3f2927cd6c5b3df16850e2925fc42055d0
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684143"
---
# <a name="if-statement-c"></a>if-Anweisung (C)

Die Anweisung **`if`** steuert die bedingte Erstellung von Branches. Der Text einer **`if`** -Anweisung wird ausgeführt, wenn der Wert des Ausdrucks ungleich 0 (null) ist. Die Syntax für die Anweisung **`if`** weist zwei Formen auf.

## <a name="syntax"></a>Syntax

*Auswahlanweisung*: **if (**  *Ausdruck*  **)**  *Anweisung*

**if (**  *Ausdruck*  **)**  *Anweisung*  **`else`**  *Anweisung*

In beiden Formen der Anweisung **`if`** werden Ausdrücke ausgewertet, die über einen beliebigen Wert (keine Struktur) verfügen können, einschließlich aller Nebenwirkungen.

In der ersten Form der Syntax, wenn *expression* auf „true“ (Wert ungleich 0 [null]) festgelegt ist, wird *statement* ausgeführt. Wenn *expression* „false“ ist, wird *statement* ignoriert. In der zweiten Form der Syntax, die **`else`** verwendet, wird die zweite *Anweisung* ausgeführt, wenn für *Ausdruck* FALSE zurückgegeben wird. Bei beiden Formen geht die Steuerung von der Anweisung **`if`** zur nächsten Anweisung im Programm, wenn keine der Anweisungen ein **`break`** -, ein **`continue`** - oder ein **`goto`** -Element enthält.

Nachfolgend einige Beispiele für die **`if`** -Anweisung:

```C
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

In diesem Beispiel wird die Anweisung `y = x/i;` ausgeführt, wenn `i` größer als 0 ist. Wenn `i` kleiner oder gleich 0 ist, wird `i``x` und `f( x )``y` zugewiesen. Beachten Sie, dass die Anweisung, die die **`if`** -Klausel bildet, mit einem Semikolon endet.

Wenn Sie **`if`** -Anweisungen und **`else`** -Klauseln schachteln, verwenden Sie geschweifte Klammern, um die Anweisungen und Klauseln in Verbundanweisungen zu gruppieren, die Ihre Absicht verdeutlichen. Wenn keine Klammern vorhanden sind, löst der Compiler Mehrdeutigkeiten auf, indem er jedes **`else`** -Element dem nächstliegenden **`if`** -Element zuordnet, dem ein **`else`** -Element fehlt.

```C
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

Die Klausel **`else`** ist mit der inneren **`if`** -Anweisung in diesem Beispiel verbunden. Wenn `i` kleiner oder gleich 0 ist, wird `x` kein Wert zugewiesen.

```C
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

Die geschweiften Klammern, die die innere **`if`** -Anweisung in diesem Beispiel umgeben, machen den **`else`** -Teil der Klausel der äußeren **`if`** -Anweisung aus. Wenn `i` kleiner oder gleich 0 ist, wird `i``x` zugewiesen.

## <a name="see-also"></a>Siehe auch

[if-else-Anweisung (C++)](../cpp/if-else-statement-cpp.md)
