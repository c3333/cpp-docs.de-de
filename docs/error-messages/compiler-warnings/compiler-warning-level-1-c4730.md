---
title: Compilerwarnung (Stufe 1) C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: ba6d305a414e99bd22ca603aaac2615994780c7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185762"
---
# <a name="compiler-warning-level-1-c4730"></a>Compilerwarnung (Stufe 1) C4730

"Main": das Mischen von _m64 und Gleit Komma Ausdrücken kann zu fehlerhaftem Code führen.

Eine Funktion verwendet [__m64](../../cpp/m64.md) -und **float** -/**Double** -Typen. Da die MMX-und Gleit Komma Register denselben physischen Register Bereich aufweisen (nicht gleichzeitig verwendet werden können), kann die Verwendung von `__m64`-und **float** -/**doppelten** Typen in der gleichen Funktion zu Daten Beschädigungen führen, die möglicherweise eine Ausnahme verursachen.

Um `__m64` Typen und Gleit Komma Typen in derselben Funktion sicher zu verwenden, muss jede Anweisung, die einen der Typen verwendet, durch die systeminterne Funktion **_m_empty ()** (für MMX) oder **_m_femms ()** (für 3DNow!) getrennt werden.

Im folgenden Beispiel wird C4730 generiert:

```cpp
// C4730.cpp
// compile with: /W1
// processor: x86
#include "mmintrin.h"

void func(double)
{
}

int main(__m64 a, __m64 b)
{
   __m64 m;
   double f;
   f = 1.0;
   m = _m_paddb(a, b);
   // uncomment the next line to resolve C4730
   // _m_empty();
   func(f * 3.0);   // C4730
}
```
