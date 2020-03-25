---
title: Compilerwarnung (Stufe 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: 198873792743a9ccdee94d44e2a0599348589ee6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163205"
---
# <a name="compiler-warning-level-1-c4258"></a>Compilerwarnung (Stufe 1) C4258

' Variable ': die Definition aus der for-Schleife wird ignoriert. die Definition aus dem einschließenden Bereich wird verwendet "

Unter [/Ze](../../build/reference/za-ze-disable-language-extensions.md) und [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)gehen in einer [for](../../cpp/for-statement-cpp.md) -Schleife definierte Variablen außerhalb des Gültigkeits Bereichs, nachdem die **for** -Schleife beendet wurde. Diese Warnung tritt auf, wenn eine Variable mit dem gleichen Namen wie die Schleifenvariable, aber in der einschließenden Schleife definiert ist, erneut in dem Bereich verwendet wird, der die **for** -Schleife enthält. Beispiel:

```cpp
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```
