---
title: EVEN- und ALIGN-Anweisungen
ms.date: 08/30/2018
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
ms.openlocfilehash: 63fa73988b9b9433a988035789a923ac73936214
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441577"
---
# <a name="even-and-align-directives"></a>EVEN- und ALIGN-Anweisungen

**Microsoft-spezifisch**

Obwohl der Inline Assembler die meisten MASM-Direktiven nicht unterstützt, unterstützt er `EVEN` und **Ausrichtung**. Diese Direktiven fügen bei Bedarf **NOP** -Anweisungen (keine Operation) in den Assemblycode ein, um Bezeichnungen an bestimmten Grenzen auszurichten. Dadurch wird die Anweisung zum Abrufen von Vorgängen für einige Prozessoren effizienter.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden der Assemblysprache in __asm-Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>