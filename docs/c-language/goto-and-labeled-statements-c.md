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
ms.openlocfilehash: b5e0d602332c87510b1fe5f59db3e497b88f0acb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299116"
---
# <a name="goto-and-labeled-statements-c"></a>goto und bezeichnete Anweisungen (C)

Die Anweisung `goto` übertragt die Steuerung an eine Bezeichnung. Die angegebene Bezeichnung muss sich in derselben Funktion befinden und kann nur vor einer Anweisung in derselben Funktion stehen.

## <a name="syntax"></a>Syntax

*Anweisung*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jump-statement*

*jump-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto**  *Bezeichner*  **;**

*labeled-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Bezeichner*  **:**  *Anweisung*

Eine Anweisungsmarke ist nur für eine `goto`-Anweisung sinnvoll. In jedem anderen Kontext wird eine bezeichnete Anweisung ohne Berücksichtigung der Bezeichnung ausgeführt.

Ein *jump-statement* muss sich in der gleichen Funktion befinden und kann nur vor einer Anweisung in der gleichen Funktion stehen. Der Satz der *Bezeichnernamen*, die auf `goto` folgen, verfügt über einen eigenen Namespace, sodass die Namen nicht mit anderen Bezeichnern in Konflikt treten. Bezeichnungen können nicht erneut deklariert werden. Weitere Informationen finden Sie unter [Namespaces](../c-language/name-spaces.md).

Zur Programmierung empfiehlt es sich, die **break**-, **continue**- und `return`-Anweisung der `goto`-Anweisung vorzuziehen, wann immer dies möglich ist. Da die **break**-Anweisung nur eine Ebene der Schleife beendet, ist möglicherweise eine `goto`-Anweisung erforderlich, um die Schleife aus einer tief verschachtelten Schleife heraus zu beenden.

In diesem Beispiel wird die `goto`-Anweisung veranschaulicht.

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

In diesem Beispiel übergibt eine `goto`-Anweisung die Steuerung an den Punkt mit der Bezeichnung `stop`, wenn `i` gleich 5 ist.

## <a name="see-also"></a>Siehe auch

[Anweisungen](../c-language/statements-c.md)
