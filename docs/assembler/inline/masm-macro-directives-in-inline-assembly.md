---
title: MASM-Makrodirektiven in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 38b73346fc52f6b5efe478f8eb960ad049fae924
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169278"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>MASM-Makrodirektiven in der Inlineassembly

**Microsoft-spezifisch**

Der Inline Assembler ist kein Makro Assembler. Sie können keine MASM-Makro Direktiven (**Makro**, `REPT`, **IRC**, `IRP`und `ENDM`) oder Makro Operatoren ( **<>** , **!** , **&** , `%`und `.TYPE`) verwenden. Ein `__asm`-Block kann jedoch C-Präprozessordirektiven verwenden. Weitere Informationen finden [Sie C++ unter Verwenden von C oder in __asm-Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden der Assemblysprache in __asm-Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
