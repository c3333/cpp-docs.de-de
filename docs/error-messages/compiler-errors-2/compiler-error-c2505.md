---
title: Compilerfehler C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: eabed85c61eaaa43b0106e0011f0357ece2e1ae1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221171"
---
# <a name="compiler-error-c2505"></a>Compilerfehler C2505

' Symbol ': ' __declspec (Modifizierer) ' kann nur auf Deklarationen oder Definitionen globaler Objekte oder statischer Datenmember angewendet werden.

Ein **`__declspec`** Modifizierer, der nur für den globalen Gültigkeitsbereich verwendet werden soll, wurde in einer Funktion verwendet.

Weitere Informationen finden Sie unter [appdomain](../../cpp/appdomain.md) und [process](../../cpp/process.md).

Im folgenden Beispiel wird C2505 generiert:

```cpp
// C2505.cpp
// compile with: /clr

// OK
__declspec(process) int ii;
__declspec(appdomain) int jj;

int main() {
   __declspec(process) int i;   // C2505
   __declspec(appdomain) int j;   // C2505
}
```
