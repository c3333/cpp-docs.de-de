---
title: Debuggen und Listen für die Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: 3254fb6b750466de0a38230c5e1cfa067c476f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169512"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Debuggen und Listen für die Inlineassembly

**Microsoft-spezifisch**

Programme, die Inline-Assemblycode enthalten, können mit einem Debugger auf Quell Ebene Debuggen, wenn Sie mit der [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) -Option kompilieren.

Innerhalb des C++ -Debuggers können Sie Haltepunkte sowohl in C-als auch in-und-assemblysprachlinien festlegen. Wenn Sie gemischte Assemblys und den Quell Modus aktivieren, können Sie sowohl die Quell-als auch die disassemblierte Form des Assemblycodes anzeigen.

Beachten Sie, dass das Debuggen durch das Platzieren mehrerer Assemblyanweisungen oder Quell Sprachanweisungen in einer Zeile beeinträchtigt Im Quell Modus können Sie mit dem Debugger Haltepunkte in einer einzelnen Zeile festlegen, aber nicht für einzelne Anweisungen in derselben Zeile. Das gleiche Prinzip gilt für einen `__asm` Block, der als C-Makro definiert ist, das zu einer einzelnen logischen Zeile erweitert wird.

Wenn Sie eine gemischte Quell-und assemblyauflistung mit der [/FAS](../../build/reference/fa-fa-listing-file.md) -Compileroption erstellen, enthält die Auflistung sowohl das Quell-als auch das assemblyformular jeder assemblysprachenzeile Makros werden in Auflistungen nicht erweitert, aber Sie werden während der Kompilierung erweitert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden der Assemblysprache in __asm-Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
