---
title: Compilerfehler C3015
ms.date: 11/04/2016
f1_keywords:
- C3015
helpviewer_keywords:
- C3015
ms.assetid: d5e8e50b-7542-4b2d-8665-1b22072a5bc6
ms.openlocfilehash: db87b035d76d4e3d2cf3f05c30ebddf0b6d22d5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232104"
---
# <a name="compiler-error-c3015"></a>Compilerfehler C3015

Die Initialisierung in der For-Anweisung von OpenMP weist eine ungültige Form auf.

Eine **`for`** -Schleife in einer OpenMP-Anweisung muss vollständig und explizit angegeben werden.

Im folgenden Beispiel wird C3015 generiert:

```cpp
// C3015.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (; i < 0; i += j)   // C3015
      // Try the following line instead:
      // for (i = 0; i < 0; i++)
         --j;
   }
}
```
