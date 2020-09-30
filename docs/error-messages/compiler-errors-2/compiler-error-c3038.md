---
title: Compilerfehler C3038
ms.date: 11/04/2016
f1_keywords:
- C3038
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
ms.openlocfilehash: 7da7dcf1f03c05511ba4bb970e898bc06b9ae3bd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508421"
---
# <a name="compiler-error-c3038"></a>Compilerfehler C3038

"Var": Die Variable in der private-Klausel kann im umschließenden Kontext keine reduction-Variable sein.

Variablen in der [reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) -Klausel einer parallel-Direktive können nicht in einer [private](../../parallel/openmp/reference/openmp-clauses.md#private-openmp) -Klausel für eine Arbeitsteilungsdirektive angegeben werden, die an das parallele Konstrukt gebunden ist.

Im folgenden Beispiel wird C3038 generiert.

```cpp
// C3038.cpp
// compile with: /openmp /c
int g_i, g_i2;

int main() {
   int i;

   #pragma omp parallel reduction(+: g_i)
   {
      #pragma omp for private(g_i)   // C3038
      // try the following line instead
      // #pragma omp for private(g_i2)
      for (i = 0; i < 10; ++i)
         g_i += i;
   }
}
```
