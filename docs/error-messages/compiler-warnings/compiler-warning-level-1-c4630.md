---
title: Compilerwarnung (Stufe 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 3a533afe141a465fb034ba7d90b22a8206bf0910
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230622"
---
# <a name="compiler-warning-level-1-c4630"></a>Compilerwarnung (Stufe 1) C4630

"Symbol": der Speicherklassenspezifizierer "extern" ist für die Element Definition unzulässig.

Ein Datenmember oder eine Member-Funktion ist als definiert **`extern`** . Member können nicht extern sein, auch wenn ganze Objekte dies möglich sind. Der Compiler ignoriert das- **`extern`** Schlüsselwort. Im folgenden Beispiel wird C4630 generiert:

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```
