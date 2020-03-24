---
title: do-while-Anweisung (C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: f52c065210a8861dc065508248a506770b039b1d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189272"
---
# <a name="do-while-statement-c"></a>do-while-Anweisung (C++)

Führt eine *Anweisung* wiederholt aus, bis die angegebene Beendigungs Bedingung (der *Ausdruck*) 0 (null) ergibt.

## <a name="syntax"></a>Syntax

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Bemerkungen

Der Test der Beendigungs Bedingung erfolgt nach jeder Ausführung der Schleife. Daher wird eine **do-while-** Schleife je nach dem Wert des Beendigungs Ausdrucks einmal oder mehrmals ausgeführt. Die **do-while**-Anweisung kann auch beendet werden, wenn eine [break](../cpp/break-statement-cpp.md)-, [goto](../cpp/goto-statement-cpp.md)- oder [return](../cpp/return-statement-cpp.md)-Anweisung innerhalb des Anweisungstexts ausgeführt wird.

Der *Ausdruck* muss einen arithmetischen Typ oder einen Zeigertyp aufweisen. Die Ausführung erfolgt folgendermaßen:

1. Der Anweisungstext wird ausgeführt.

1. Danach wird *expression*, der Ausdruck, ausgewertet. Wenn der *Ausdruck* „false“ ist, wird die **do-while**-Anweisung beendet und die Steuerung an die nächste Anweisung im Programm weitergegeben. Wenn *expression* „true“ (ungleich 0 [null]) ist, wird der Prozess wiederholt, beginnend mit Schritt 1.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die **do-while-** Anweisung veranschaulicht:

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>Weitere Informationen

[Iterationsanweisungen](../cpp/iteration-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[while-Anweisung (C++)](../cpp/while-statement-cpp.md)<br/>
[for-Anweisung (C++)](../cpp/for-statement-cpp.md)<br/>
[Bereichsbasiert für Anweisung (C++)](../cpp/range-based-for-statement-cpp.md)
