---
title: Compilerfehler C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: f3650d994e3102f71ab1d3598a4d1482f50b3334
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510034"
---
# <a name="compiler-error-c3899"></a>Compilerfehler C3899

"var": die Verwendung des l-Werts eines initonly-Datenmembers ist nicht direkt innerhalb eines parallelen Bereichs in der Klasse "Class" zulässig.

Ein [initonly-Datenmember (C++/CLI)](../../dotnet/initonly-cpp-cli.md) kann nicht innerhalb dieses Teils eines Konstruktors initialisiert werden, der sich in einem [parallelen](../../parallel/openmp/reference/openmp-directives.md#parallel) Bereich befindet.  Dies liegt daran, dass der Compiler eine interne Verschiebung dieses Codes durchführt, sodass er nicht mehr Teil des Konstruktors ist.

Um dies aufzulösen, initialisieren Sie den initonly-Datenmember im Konstruktor, jedoch außerhalb des parallelen Bereichs.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3899 generiert.

```cpp
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```
