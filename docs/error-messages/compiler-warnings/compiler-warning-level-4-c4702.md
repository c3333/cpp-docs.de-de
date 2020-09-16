---
title: Compilerwarnung (Stufe 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: a2d1f6f4bdc20a35638274e2099c00428f4f6ddf
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684286"
---
# <a name="compiler-warning-level-4-c4702"></a>Compilerwarnung (Stufe 4) C4702

nicht erreichbarer Code

Diese Warnung ist das Ergebnis der compilerübereinstimmungs-Arbeit, die für Visual Studio .NET 2003: nicht erreichbarer Code ausgeführt wurde. Wenn der Compiler (Back-End) nicht erreichbaren Code erkennt, generiert er C4702, eine Warnung der Stufe 4.

Für Code, der sowohl in der Visual Studio .NET 2003-als auch in der Visual Studio .NET-Version von Visual C++ gültig ist, entfernen Sie den nicht erreichbaren Code, oder stellen Sie sicher, dass der gesamte Quellcode durch einen bestimmten Ausführungs Verlauf erreichbar ist.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C4702 generiert.

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

Beim Kompilieren mit **/GX**, **/EHC**, **/EHsc**oder **/EHac** und der Verwendung externer c-Funktionen kann der Code nicht erreichbar sein, da externe c-Funktionen nicht ausgelöst werden, sodass der catch-Block nicht erreichbar ist.  Wenn Sie der Meinung sind, dass diese Warnung ungültig ist, weil eine Funktion eine Ausnahme auslösen kann, kompilieren Sie mit **/EHa** oder **/EHS**, abhängig von der ausgelösten Ausnahme.

Weitere Informationen finden Sie unter [/eh (Ausnahme Behandlungsmodell)](../../build/reference/eh-exception-handling-model.md) .

Im folgenden Beispiel wird C4702 generiert.

```cpp
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```
