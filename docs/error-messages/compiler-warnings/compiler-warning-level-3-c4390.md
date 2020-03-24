---
title: Compilerwarnung (Stufe 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 63150f4ca801d3c377c7bc09b58a778bebf02b46
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198678"
---
# <a name="compiler-warning-level-3-c4390"></a>Compilerwarnung (Stufe 3) C4390

";": leere kontrollierte Anweisung gefunden; ist das beabsichtigt?

Ein Semikolon wurde nach einer Steuerelement Anweisung gefunden, die keine Anweisungen enthält.

Wenn Sie C4390 aufgrund eines Makros erhalten, sollten Sie das [Warning](../../preprocessor/warning.md) -Pragma verwenden, um C4390 im Modul zu deaktivieren, das das Makro enthält.

Im folgenden Beispiel wird C4390 generiert:

```cpp
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```
