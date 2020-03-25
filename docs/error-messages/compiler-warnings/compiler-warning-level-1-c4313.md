---
title: Compilerwarnung (Stufe 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 14ac938d62b4c5b6f22957268721aea9c3ffef22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163049"
---
# <a name="compiler-warning-level-1-c4313"></a>Compilerwarnung (Stufe 1) C4313

„Funktion“: „Formatbezeichner“ in der Formatzeichenfolge steht mit der Argumentennummer vom Typ „Typ“ in Konflikt.

Es besteht ein Konflikt zwischen dem angegebenen Format und dem Wert, den Sie übergeben. Beispielsweise haben Sie einen 64-Bit-Parameter an einen nicht qualifizierten Formatbezeichner „%d“ übergeben, wohingegen ein 32-Bit-Ganzzahl-Parameter erwartet wird. Diese Warnung ist nur aktiv, wenn der Code für 64-Bit-Ziele kompiliert wird.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird C4313 generiert, wenn dies für 64-Bit-Ziele kompiliert wird.

```cpp
// C4313.cpp
// Compile by using: cl /W1 C4313.cpp
#include <stdio.h>
int main() {
   int * pI = 0;
   printf("%d", pI);   // C4313 on 64-bit platform code
   // Try one of the following lines instead:
   // printf("%p\n", pI);
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information
}
```
