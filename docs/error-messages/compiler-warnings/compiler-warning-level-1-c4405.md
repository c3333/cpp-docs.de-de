---
title: Compilerwarnung (Stufe 1) C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 7ec06e80ac8f61802258a62594029b15a55ebe42
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162568"
---
# <a name="compiler-warning-level-1-c4405"></a>Compilerwarnung (Stufe 1) C4405

"Bezeichner": Bezeichner ist ein reserviertes Wort

Ein Wort, das für die Inlineassembly reserviert ist, wird als Variablenname verwendet. Dies kann zu unvorhersehbaren Ergebnissen führen. Um diese Warnung zu beheben, vermeiden Sie das Benennen von Variablen, die für die Inlineassembly reserviert sind. Im folgenden Beispiel wird C4405 generiert:

```cpp
// C4405.cpp
// compile with: /W1
// processor: x86
void func1() {
   int mov = 0, i = 0;
   _asm {
      mov mov, 0;   // C4405
      // instead, try ..
      // mov i, 0;
   }
}

int main() {
}
```
