---
title: while-Anweisung (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 168b1fc20d165c44c3230a8d1094c99b689ddbb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233547"
---
# <a name="while-statement-c"></a>while-Anweisung (C++)

Führt die *Anweisung* wiederholt aus, bis der *Ausdruck* NULL ergibt.

## <a name="syntax"></a>Syntax

```
while ( expression )
   statement
```

## <a name="remarks"></a>Bemerkungen

Der Test des *Ausdrucks* findet vor jeder Ausführung der Schleife statt. Daher wird eine- **`while`** Schleife NULL oder mehrmals ausgeführt. der *Ausdruck* muss einen ganzzahligen Typ, einen Zeigertyp oder einen Klassentyp mit eindeutiger Konvertierung in einen ganzzahligen oder Zeigertyp aufweisen.

Eine- **`while`** Schleife kann auch beendet werden, wenn eine [break](../cpp/break-statement-cpp.md)-, [goto](../cpp/goto-statement-cpp.md)-oder [Return](../cpp/return-statement-cpp.md) -Anweisung innerhalb des Anweisungs Texts ausgeführt wird. Verwenden Sie [Continue](../cpp/continue-statement-cpp.md) , um die aktuelle Iterations Schleife zu beenden, ohne die Schleife zu beenden **`while`** . **`continue`** übergibt die Steuerung an die nächste Iterations **`while`** Schleife.

Der folgende Code verwendet eine- **`while`** Schleife, um nachfolgende Unterstriche aus einer Zeichenfolge zu kürzen:

```cpp
// while_statement.cpp

#include <string.h>
#include <stdio.h>
char *trim( char *szSource )
{
    char *pszEOS = 0;

    //  Set pointer to character before terminating NULL
    pszEOS = szSource + strlen( szSource ) - 1;

    //  iterate backwards until non '_' is found
    while( (pszEOS >= szSource) && (*pszEOS == '_') )
        *pszEOS-- = '\0';

    return szSource;
}
int main()
{
    char szbuf[] = "12345_____";

    printf_s("\nBefore trim: %s", szbuf);
    printf_s("\nAfter trim: %s\n", trim(szbuf));
}
```

Die Beendigungsbedingung wird am Anfang der Schleife ausgewertet. Solange keine nachgestellten Unterstriche vorhanden sind, wird die Schleife nicht ausgeführt.

## <a name="see-also"></a>Siehe auch

[Iterationsanweisungen](../cpp/iteration-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[do-while-Anweisung (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for-Anweisung (C++)](../cpp/for-statement-cpp.md)<br/>
[Bereichsbasiert für Anweisung (C++)](../cpp/range-based-for-statement-cpp.md)
