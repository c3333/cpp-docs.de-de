---
title: Compilerwarnung (Stufe 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: 72483b734a1463b7b211c49ef21a01536ffa0ea1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185723"
---
# <a name="compiler-warning-level-1-c4731"></a>Compilerwarnung (Stufe 1) C4731

"Pointer": Frame Zeiger Register "Register" geändert durch Inline-Assemblycode

Ein Frame Zeiger Register wurde geändert. Sie müssen das Register in Ihrem Inlineassemblyblock oder in einer Frame Variablen (lokal oder Parameter, abhängig vom geänderten Register) speichern und wiederherstellen, oder der Code funktioniert möglicherweise nicht ordnungsgemäß.

Im folgenden Beispiel wird C4731 generiert:

```cpp
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

EBP ist der Frame Zeiger (FPO ist nicht zulässig) und wird geändert. Wenn `p` später referenziert wird, wird relativ zu `EBP`auf Sie verwiesen. `EBP` wurde jedoch vom Code überschrieben, sodass das Programm nicht ordnungsgemäß funktioniert und möglicherweise sogar einen Fehler aufweist.
