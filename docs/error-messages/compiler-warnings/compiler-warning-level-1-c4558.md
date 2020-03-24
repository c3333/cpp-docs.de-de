---
title: Compilerwarnung (Stufe 1) C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: 26bf1603588f522e2bec366586984896190f2d65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162295"
---
# <a name="compiler-warning-level-1-c4558"></a>Compilerwarnung (Stufe 1) C4558

der Wert des Operanden ' value ' liegt außerhalb des gültigen Bereichs ' lowerbound-upperbound '.

Der an eine Assembly-sprach Anweisung übergebenen Wert liegt außerhalb des Bereichs, der für den-Parameter angegeben ist. Der Wert wird abgeschnitten.

Im folgenden Beispiel wird C4558 generiert:

```cpp
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```
