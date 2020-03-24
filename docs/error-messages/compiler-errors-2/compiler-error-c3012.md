---
title: Compilerfehler C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 69f0544815804e9827631be81bf9735a95bd1a22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176701"
---
# <a name="compiler-error-c3012"></a>Compilerfehler C3012

> "*intrinsisch*": eine intrinsische Funktion ist nicht direkt in einem parallelen Bereich zulässig.

Eine [systeminterne Compilerfunktion](../../intrinsics/compiler-intrinsics.md) ist in einem `omp parallel` Bereich nicht zulässig. Um dieses Problem zu beheben, verschieben Sie die systeminternen Elemente aus der Region, oder ersetzen Sie Sie durch nicht intrinsische Entsprechungen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3012 generiert und eine Möglichkeit gezeigt, Sie zu beheben:

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```
