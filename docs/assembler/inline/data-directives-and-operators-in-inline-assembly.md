---
title: Datendirektiven und Operatoren in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: bcacb0cdd26181da3cf80a582866c1e30567d043
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192352"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Datendirektiven und Operatoren in der Inlineassembly

**Microsoft-spezifisch**

Obwohl ein **`__asm`** Block auf C-oder C++-Datentypen und-Objekte verweisen kann, kann er keine Datenobjekte mit MASM-Direktiven oder-Operatoren definieren. Insbesondere können Sie die Definitions Direktiven **DB**, `DW` , **DD**, `DQ` , `DT` , und `DF` oder die-Operatoren `DUP` oder **diese**nicht verwenden. MASM-Strukturen und-Einträge sind ebenfalls nicht verfügbar. Der Inline Assembler akzeptiert nicht die Direktiven, `STRUC` `RECORD` , **Width**oder **Mask**.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Verwenden der Assemblysprache in __asm Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
