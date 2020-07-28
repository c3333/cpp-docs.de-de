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
ms.openlocfilehash: a558761ff49c2b508a5bad6172cda2283801e30e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191728"
---
# <a name="optimizing-inline-assembly"></a>Optimieren der Inlineassembly

**Microsoft-spezifisch**

Das vorhanden sein eines- **`__asm`** Blocks in einer-Funktion wirkt sich auf die Optimierung auf verschiedene Weise aus. Zuerst versucht der Compiler nicht, den **`__asm`** Block selbst zu optimieren. Was Sie in der Assemblysprache schreiben, ist genau das, was Sie erhalten. Zweitens wirkt sich das vorhanden sein eines-Blocks auf den **`__asm`** Speicher der Register Variablen aus. Der Compiler vermeidet das Registrieren von Variablen in einem **`__asm`** Block, wenn der Inhalt des Registers durch den Block geändert würde **`__asm`** . Schließlich sind einige andere Funktions weite Optimierungen von der Aufnahme der Assemblysprache in einer Funktion betroffen.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
