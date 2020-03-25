---
title: _emit Pseudoinstruction
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: 8be250aadf20dc4a7dee6a0b565ece21840339d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169473"
---
# <a name="_emit-pseudoinstruction"></a>_emit Pseudoinstruction

**Microsoft-spezifisch**

Der **_emit** Pseudoinstruction definiert ein Byte an der aktuellen Position im aktuellen Textsegment. Der **_emit** Pseudoinstruction ähnelt der [DB](../../assembler/masm/db.md) -Direktive von MASM.

Das folgende Fragment fügt die Bytes 0x4A, 0x43 und 0x4B in den Code ein:

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
    randasm
    }
```

> [!CAUTION]
> Wenn `_emit` Anweisungen generiert, die Register ändern, und Sie die Anwendung mit Optimierungen kompilieren, kann der Compiler nicht bestimmen, welche Register betroffen sind. Wenn `_emit` z. b. eine Anweisung generiert, die das **Rax** -Register ändert, weiß der Compiler nicht, dass **Rax** geändert wurde. Der Compiler kann dann eine falsche Annahme über den Wert in vornehmen, der nach der Ausführung des Inline Assembler Codes registriert wird. Folglich kann die Anwendung bei der Ausführung unvorhersehbares Verhalten aufweisen.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden der Assemblysprache in __asm-Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
