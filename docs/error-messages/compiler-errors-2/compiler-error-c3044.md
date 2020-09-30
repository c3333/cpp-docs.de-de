---
title: Compilerfehler C3044
ms.date: 11/04/2016
f1_keywords:
- C3044
helpviewer_keywords:
- C3044
ms.assetid: 9f3e25b2-4676-49ab-97bf-6c88cd0fa377
ms.openlocfilehash: 0ac2a6a86ffd719dbb5f39fc085d3f5cbca0567d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506363"
---
# <a name="compiler-error-c3044"></a>Compilerfehler C3044

section: Nur bei direkter Schachtelung unter einer sections-Direktive von OpenMP zulässig.

Der Compiler hat herausgefunden, dass eine `section` -Direktive falsch verwendet wurde. Weitere Informationen finden Sie unter [Abschnitte](../../parallel/openmp/reference/openmp-directives.md#sections-openmp).

Im folgenden Beispiel wird C3044 generiert:

```cpp
// C3044.cpp
// compile with: /openmp /c
#include "omp.h"
int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
         ++n2;
      }

      #pragma omp section   // C3044
      {
         ++n3;
      }
   }

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
         #pragma omp section   // OK
         {
            ++n3;
         }
      }
   }
}
```
