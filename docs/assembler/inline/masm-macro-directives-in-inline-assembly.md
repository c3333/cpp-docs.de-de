---
title: MASM-Makrodirektiven in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 964f70aeef6e0e62ac4b941b2cc26d3e7c7ef466
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191793"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>MASM-Makrodirektiven in der Inlineassembly

**Microsoft-spezifisch**

Der Inline Assembler ist kein Makro Assembler. Sie können keine MASM-Makro Direktiven (**Makro**, `REPT` , **IRC**, `IRP` , und `ENDM` ) oder Makro Operatoren ( **<>** , **!**, **&** , `%` und `.TYPE` ) verwenden. Ein- **`__asm`** Block kann jedoch C-Präprozessordirektiven verwenden. Weitere Informationen finden [Sie unter Verwenden von C oder C++ in __asm-Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Verwenden der Assemblysprache in __asm Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
