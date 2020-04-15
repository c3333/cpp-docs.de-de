---
title: Inlineassembler
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++]
- assembler [C++], inline
- assembly language [C++], inline
- inline assembler [C++]
- inline assembly [C++]
ms.assetid: 7e13f18f-3628-4306-8b81-4a6d09c043fe
ms.openlocfilehash: 2050f59601755a93c73b743debacbf52ba9cec05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318080"
---
# <a name="inline-assembler"></a>Inlineassembler

**Microsoft Specific**

Die Assemblysprache dient vielen Zwecken, wie etwa der Verbesserung der Programmgeschwindigkeit, der Verringerung der Speicheranforderungen und der Steuerung der Hardware. Sie können den Inlineassembler verwenden, um Assemblysprachanweisungen ohne zusätzliche Assembly- und Verknüpfungsschritte direkt in die C- und C++-Quellprogramme einzubetten. Der Inlineassembler wird in den Compiler integriert, daher benötigen Sie keinen getrennten Assembler wie den Microsoft Macro Assembler (MASM).

> [!NOTE]
> Programme mit Inlineassemblercode sind nicht vollständig auf andere Hardwareplattformen übertragbar. Wenn Ihnen Portabilität wichtig ist, vermeiden Sie beim Entwerfen die Verwendung des Inlineassemblers.

Die Inline-Baugruppe wird auf den ARM- und x64-Prozessoren nicht unterstützt.  In folgenden Themen wird erklärt, wie der Inlineassembler von Visual C/C++ mit x86-Prozessoren zu verwenden ist:

- [Übersicht über Inlineassembler](../../assembler/inline/inline-assembler-overview.md)

- [Vorteile von Inlineassemblys](../../assembler/inline/advantages-of-inline-assembly.md)

- [__asm](../../assembler/inline/asm.md)

- [Verwenden der Assemblysprache in __asm-Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)

- [Verwenden von C oder C++ in __asm-Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)

- [Verwenden und Beibehalten von Registern in der Inlineassembly](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)

- [Springen zu Bezeichnungen in der Inlineassembly](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)

- [Aufrufen von C-Funktionen in der Inline-Baugruppe](../../assembler/inline/calling-c-functions-in-inline-assembly.md)

- [Aufrufen von C++-Funktionen in der Inlineassembly](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)

- [Definieren von __asm-Blöcken als C-Makros](../../assembler/inline/defining-asm-blocks-as-c-macros.md)

- [Optimieren der Inlineassembly](../../assembler/inline/optimizing-inline-assembly.md)

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[CompilerIntrinsics und Assemblylanguage](../../intrinsics/compiler-intrinsics-and-assembly-language.md)<br/>
[C++-Sprachreferenz](../../cpp/cpp-language-reference.md)<br/>
