---
title: goto und bezeichnete Anweisungen (C)
ms.date: 11/04/2016
f1_keywords:
- goto
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
ms.openlocfilehash: d84aa6701ef030dc494f6a40a7223d6f9bcd5073
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199983"
---
# <a name="goto-and-labeled-statements-c"></a>goto und bezeichnete Anweisungen (C)

Die Anweisung **`goto`** überträgt die Steuerung an eine Bezeichnung. Die angegebene Bezeichnung muss sich in derselben Funktion befinden und kann nur vor einer Anweisung in derselben Funktion stehen.

## <a name="syntax"></a>Syntax

*Anweisung*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jump-statement*

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`goto`**  *Bezeichner*  **;**

*labeled-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichner*  **:**  *Anweisung*

Eine Anweisungsbezeichnung ist nur für eine **`goto`** -Anweisung von Bedeutung. In jedem anderen Kontext werden Anweisungen mit Bezeichnung ohne Berücksichtigung dieser Bezeichnung ausgeführt.

Ein *jump-statement* muss sich in der gleichen Funktion befinden und kann nur vor einer Anweisung in der gleichen Funktion stehen. Die *Bezeichnernamen*, die auf **`goto`** folgen, verfügen über einen eigenen Namespace, sodass keine Konflikte zwischen diesen Namen und anderen Bezeichnern auftreten. Bezeichnungen können nicht erneut deklariert werden. Weitere Informationen finden Sie unter [Namespaces](../c-language/name-spaces.md).

Es ist guter Programmierstil, die Anweisungen **`break`** , **`continue`** und **`return`** nach Möglichkeit der Anweisung **`goto`** vorzuziehen. Da die Anweisung **`break`** nur eine Ebene der Schleife beendet, ist möglicherweise eine **`goto`** -Anweisung erforderlich, um eine tief geschachtelte Schleife zu beenden.

Im folgenden Beispiel wird die Verwendung der **`goto`** -Anweisung veranschaulicht:

```c
// goto.c
#include <stdio.h>

int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 3; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 5 )
                goto stop;
        }
    }

    /* This message does not print: */
    printf_s( "Loop exited. i = %d\n", i );

    stop: printf_s( "Jumped to stop. i = %d\n", i );
}
```

In diesem Beispiel überträgt eine **`goto`** -Anweisung die Steuerung an den Punkt mit der Bezeichnung `stop`, wenn `i` gleich 5 ist.

## <a name="see-also"></a>Siehe auch

[Anweisungen](../c-language/statements-c.md)
