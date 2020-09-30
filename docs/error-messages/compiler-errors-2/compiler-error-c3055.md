---
title: Compilerfehler C3055
ms.date: 11/04/2016
f1_keywords:
- C3055
helpviewer_keywords:
- C3055
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
ms.openlocfilehash: ed0f031fcd0ff0c621556bf73572d720fc2c1352
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501624"
---
# <a name="compiler-error-c3055"></a>Compilerfehler C3055

'Symbol': Auf das Symbol kann erst verwiesen werden, wenn es in der threadprivate-Direktive verwendet wird.

Es wurde auf ein Symbol verwiesen und dieses dann in einer [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) -Klausel verwendet. Dies ist nicht zulässig.

Im folgenden Beispiel wird C3055 generiert:

```cpp
// C3055.cpp
// compile with: /openmp
int x, y;
int z = x;
#pragma omp threadprivate(x, y)   // C3055

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Mögliche Lösung:

```cpp
// C3055b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
