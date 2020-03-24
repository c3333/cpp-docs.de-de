---
title: Compilerwarnung (Stufe 1) C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: 7a11112962872788df855bfc63b869193188fab9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164078"
---
# <a name="compiler-warning-level-1-c4074"></a>Compilerwarnung (Stufe 1) C4074

Initialisierer, die in den vom Compiler reservierten Initialisierungs Bereich eingefügt werden

Der von [#pragma init_seg](../../preprocessor/init-seg.md)angegebene compilerinitialisierungs Bereich ist von Microsoft reserviert. Der Code in diesem Bereich kann vor der Initialisierung der C-Lauf Zeit Bibliothek ausgeführt werden.

Im folgenden Beispiel wird C4074 generiert:

```cpp
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```
