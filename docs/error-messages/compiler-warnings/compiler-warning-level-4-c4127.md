---
title: Compilerwarnung (Stufe 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 9d4397c11c4d2f0f9013c7df914cbc4be9fd4e9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198483"
---
# <a name="compiler-warning-level-4-c4127"></a>Compilerwarnung (Stufe 4) C4127

> Bedingter Ausdruck ist konstant

## <a name="remarks"></a>Bemerkungen

Der steuernde Ausdruck einer **if** -Anweisung oder **while** -Schleife wird zu einer Konstanten ausgewertet. Aufgrund ihrer allgemeinen idiomatischen Verwendung, beginnend mit Visual Studio 2015 Update 3, wird die Warnung durch triviale Konstanten wie 1 oder **true** nicht auslöst, es sei denn, Sie sind das Ergebnis eines Vorgangs in einem Ausdruck.

Wenn der steuernde Ausdruck einer **while** -Schleife eine Konstante ist, weil die Schleife in der Mitte beendet wird, empfiehlt es sich, die **while** -Schleife durch eine **for** -Schleife zu ersetzen. Sie können die Initialisierung, den Beendigungs Test und das Schleifen Inkrement einer for-Schleife weglassen, was bewirkt, **dass** die Schleife wie `while(1)`unendlich ist, und Sie können die Schleife aus dem Text der **for** -Anweisung beenden.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt zwei Möglichkeiten, wie C4127 generiert wird, und zeigt, wie eine for-Schleife verwendet wird, um die Warnung zu vermeiden:

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```

Diese Warnung kann auch generiert werden, wenn eine Kompilierzeit Konstante in einem bedingten Ausdruck verwendet wird:

```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```
