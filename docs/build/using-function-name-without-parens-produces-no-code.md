---
title: Bei Verwendung eines Funktionsnamens ohne "()" wird kein Code generiert
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 51be77dc8f4fe072ea6cc46dd51e38862649feda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314597"
---
# <a name="using-function-name-without--produces-no-code"></a>Bei Verwendung eines Funktionsnamens ohne "()" wird kein Code generiert

Wenn ein im Programm deklarierter Funktionsname ohne Klammern verwendet wird, generiert der Compiler keinen Code. Dies tritt unabhängig davon auf, ob die Funktion Parameter verwendet, da der Compiler die Funktionsadresse berechnet. Da der Funktionsaufrufoperator "()" jedoch nicht vorhanden ist, wird kein Aufruf durchgeführt. Das Ergebnis sieht ungefähr wie folgt aus:

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

In Visual C++ wird selbst bei Verwendung von Warnstufe 4 keine Diagnoseausgabe generiert. Es wird keine Warnung ausgegeben und kein Code erzeugt.

Der unten aufgeführte Beispielcode wird (mit einer Warnung) kompiliert und führt eine ordnungsgemäße Verknüpfung ohne Fehler aus, generiert jedoch keinen Code, der auf `funcn( )` verweist. Damit dies ordnungsgemäß funktioniert, fügen Sie den Funktionsaufrufoperator "()" hinzu.

```
#include <stdio.h>
void funcn();

int main() {
   funcn;      /* missing function call operator;
                  call will fail.  Use funcn() */
   }

void funcn() {
   printf("\nHello World\n");
}
```

## <a name="see-also"></a>Siehe auch

[Codeoptimierung](optimizing-your-code.md)
