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
ms.openlocfilehash: 916dce0346bebfc5ff65ca558ae75317a187660a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169538"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Datendirektiven und Operatoren in der Inlineassembly

**Microsoft-spezifisch**

Obwohl ein `__asm` Block auf C-oder C++ -Datentypen und-Objekte verweisen kann, kann er keine Datenobjekte mit MASM-Direktiven oder-Operatoren definieren. Insbesondere können Sie die Definitions Direktiven **DB**, `DW`, **DD**, `DQ`, `DT`und `DF`oder die Operatoren `DUP` oder nicht verwenden **.** MASM-Strukturen und-Einträge sind ebenfalls nicht verfügbar. Der Inline Assembler akzeptiert nicht die Direktiven `STRUC`, `RECORD`, **Width**oder **Mask**.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden der Assemblysprache in __asm-Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
