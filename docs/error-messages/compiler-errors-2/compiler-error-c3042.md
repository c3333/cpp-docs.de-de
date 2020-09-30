---
title: Compilerfehler C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: 8cd27f492a72277c383afa5ca335a073b1a0519c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506396"
---
# <a name="compiler-error-c3042"></a>Compilerfehler C3042

copyprivate- und nowait-Klauseln dürfen nicht zusammen in der 'Direktive'-Direktive von OpenMP vorkommen.

Die [copyprivate](../../parallel/openmp/reference/openmp-clauses.md#copyprivate) - und [nowait](../../parallel/openmp/reference/openmp-clauses.md#nowait) -Klauseln schließen sich in der angegebenen Richtung gegenseitig aus. Entfernen Sie eine oder beide der `copyprivate` - oder `nowait` -Klauseln.

Im folgenden Beispiel wird C3042 generiert.

```cpp
// C3042.cpp
// compile with: /openmp /c
#include <stdio.h>
#include "omp.h"

double d;

int main() {
    #pragma omp parallel private(d)
   {
      #pragma omp single copyprivate(d) nowait   // C3042
      {
      }
   }
}
```
