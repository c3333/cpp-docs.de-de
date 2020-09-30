---
title: Compilerfehler C3039
ms.date: 11/04/2016
f1_keywords:
- C3039
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
ms.openlocfilehash: ea6efbfa95992b04ade5496e8c7253ee87319a93
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508362"
---
# <a name="compiler-error-c3039"></a>Compilerfehler C3039

"var": Die Indexvariable in der For-Anweisung von OpenMP kann keine reduction-Variable sein.

Da eine Indexvariable implizit privat ist, kann die Variable nicht in einer [reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) -Klausel in der einschließenden [parallel](../../parallel/openmp/reference/openmp-directives.md#parallel) -Direktive verwendet werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3039 generiert:

```cpp
// C3039.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel reduction(+: i)
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // C3039
         g_i += i;
   }
}
```
