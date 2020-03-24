---
title: Compilerwarnung (Stufe 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 4625f6bdb4aa6fe86ca881a8e36e5673e55ccb87
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185593"
---
# <a name="compiler-warning-level-3-c4414"></a>Compilerwarnung (Stufe 3) C4414

"Function": kurzsprung zur Funktion konvertiert in Near

Kurze Sprünge generieren eine kompakte Anweisung, die in einem begrenzten Bereich von der Anweisung zu einer Adresse verzweigt. Die Anweisung enthält einen kurzen Offset, der den Abstand zwischen dem Sprung und der Zieladresse (der Funktionsdefinition) darstellt. Beim Verknüpfungs Vorgang kann eine Funktion verschoben werden oder sich auf Link Zeit Optimierungen unterliegen, die bewirken, dass die Funktion aus dem Bereich verschoben wird, der von einem kurzen Offset erreichbar ist. Der Compiler muss einen speziellen Datensatz für den Sprung generieren, der erfordert, dass die "jmp"-Anweisung nah oder weit ist. Der Compiler hat die Konvertierung durchgeführt.

Der folgende Code generiert beispielsweise C4414:

```cpp
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```
