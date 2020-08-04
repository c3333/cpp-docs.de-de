---
title: Beispielprogramm
ms.date: 11/04/2016
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
ms.openlocfilehash: da8c772a3534df2c865c18959329ac850e359160
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218857"
---
# <a name="example-program"></a>Beispielprogramm

Das folgende C-Quellprogramm besteht aus zwei Quelldateien. Es vermittelt eine Übersicht über einige der verschiedenen Deklarationen und Definitionen, die in einem C-Programm möglich sind. In späteren Abschnitten dieses Buchs wird beschrieben, wie diese Deklarationen, Definitionen und Initialisierungen geschrieben und C-Schlüsselwörter wie **`static`** und **`extern`** verwendet werden. Die `printf`-Funktion wird in der C-Headerdatei STDIO.H deklariert.

Die Funktionen `main` und `max` befinden sich in separaten Dateien, und die Ausführung des Programms beginnt mit der `main`-Funktion. Es werden keine expliziten Benutzerfunktionen vor `main` ausgeführt.

```
/*****************************************************************
                    FILE1.C - main function
*****************************************************************/

#define ONE     1
#define TWO     2
#define THREE   3
#include <stdio.h>

int a = 1;                       // Defining declarations
int b = 2;                       //  of external variables

extern int max( int a, int b );  // Function prototype

int main()                       // Function definition
{                                //  for main function
    int c;                       // Definitions for
    int d;                       //  two uninitialized
                                 //  local variables

    extern int u;                // Referencing declaration
                                 //  of external variable
                                 //  defined elsewhere
    static int v;                // Definition of variable
                                 //  with continuous lifetime

    int w = ONE, x = TWO, y = THREE;
    int z = 0;

    z = max( x, y );             // Executable statements
    w = max( z, w );
    printf_s( "%d %d\n", z, w );
    return 0;
}

/****************************************************************
            FILE2.C - definition of max function
****************************************************************/

int max( int a, int b )          // Note formal parameters are
                                 //  included in function header
{
    if( a > b )
        return( a );
    else
        return( b );
}
```

FILE1.C enthält den Prototyp für die `max`-Funktion. Diese Art der Deklaration wird manchmal als "Vorwärtsdeklaration" bezeichnet, da die Funktion deklariert wird, bevor sie verwendet wird. Die Definition für die `main`-Funktion enthält Aufrufe von `max`.

Die mit `#define` beginnenden Zeilen sind Präprozessordirektiven. Diese Direktiven weisen den Präprozessor an, die Bezeichner `ONE`, `TWO` und `THREE` jeweils durch die Zahlen `1`, `2` und `3` in FILE1.C zu ersetzen. Jedoch gelten die Direktiven nicht für FILE2.C, die separat kompiliert und dann mit FILE1.C. verknüpft wird. Die mit `#include` beginnende Zeile weist den Compiler an, die Datei STDIO.H einzuschließen, die den Prototyp für die `printf`-Funktion enthält. [Präprozessordirektiven](../preprocessor/preprocessor-directives.md) werden in der *Präprozessorreferenz* erläutert.

FILE1.C verwendet definierende Deklarationen, um die globalen Variablen `a` und `b` zu initialisieren. Die lokalen Variablen `c` und `d` werden deklariert, aber nicht initialisiert. Für all diese Variablen wird Speicher zugeordnet. Die statischen und externen Variablen, `u` und `v`, werden automatisch mit 0 initialisiert. Daher werden nur `a`, `b`, `u` und `v` sinnvolle Werte enthalten, wenn sie deklariert werden, da sie entweder explizit oder implizit initialisiert werden. FILE2.C enthält die Funktionsdefinition für `max`. Diese Definition erfüllt die Aufrufe von `max` in FILE1.C.

Die Lebensdauer und Sichtbarkeit von Bezeichnern werden unter [Lebensdauer, Bereich, Sichtbarkeit und Verknüpfung](../c-language/lifetime-scope-visibility-and-linkage.md) behandelt. Weitere Informationen zu Funktionen finden Sie unter [Funktionen](../c-language/functions-c.md).

## <a name="see-also"></a>Siehe auch

[Quelldateien und Quellprogramme](../c-language/source-files-and-source-programs.md)
