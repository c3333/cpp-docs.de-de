---
title: Optimieren der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: 0051b16ddc19e233cfac2688c0b77e1e023f0833
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169265"
---
# <a name="optimizing-inline-assembly"></a>Optimieren der Inlineassembly

**Microsoft-spezifisch**

Das vorhanden sein eines `__asm` Blocks in einer Funktion wirkt sich auf die Optimierung auf verschiedene Weise aus. Zuerst versucht der Compiler nicht, den `__asm` Block zu optimieren. Was Sie in der Assemblysprache schreiben, ist genau das, was Sie erhalten. Zweitens wirkt sich das vorhanden sein eines `__asm` Blocks auf den Speicher der Register Variablen aus. Der Compiler vermeidet das Registrieren von Variablen in einem `__asm` Block, wenn der Inhalt des Registers durch den `__asm`-Block geändert wird. Schließlich sind einige andere Funktions weite Optimierungen von der Aufnahme der Assemblysprache in einer Funktion betroffen.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Inlineassembler](../../assembler/inline/inline-assembler.md)<br/>
