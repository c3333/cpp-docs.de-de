---
title: Übersicht über Inlineassembler
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 3872dcb194146bf0f4c89b0be03a49b5fe3a9e37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192079"
---
# <a name="inline-assembler-overview"></a>Übersicht über Inlineassembler

**Microsoft-spezifisch**

Mit dem Inline Assembler können Sie Assemblysprachanweisungen in Ihre C-und C++-Quell Programme einbetten, ohne zusätzliche Assembly-und Link Schritte auszuführen. Der Inlineassembler ist im Compiler integriert, daher benötigen Sie keinen getrennten Assembler wie den Microsoft Macro Assembler (MASM).

Da der Inlineassembler keine separaten Assembly- und Verknüpfungsschritte erfordert, ist er einfacher als ein getrennter Assembler. Inline-Assemblycode kann alle c-oder C++-Variablen oder Funktionsnamen verwenden, die sich im Gültigkeitsbereich befinden. Daher ist es einfach, ihn in den C-und C++-Code Ihres Programms zu integrieren Und da der Assemblycode mit c-und C++-Anweisungen gemischt werden kann, kann er Aufgaben ausführen, die in c oder C++ allein mühsam oder unmöglich sind.

Das [__asm](../../assembler/inline/asm.md) -Schlüsselwort Ruft den Inline Assembler auf und kann überall dort vorkommen, wo eine C-oder C++-Anweisung zulässig ist. Es kann nicht allein stehen. Ihm muss eine Assemblyanweisung, eine Gruppe von Anweisungen, die in geschweifte Klammern eingeschlossen sind, oder zumindest ein leeres Paar geschweifter Klammern folgen. Der Begriff " **`__asm`** Block" bezieht sich hier auf eine beliebige Anweisung oder Gruppe von Anweisungen, egal ob in geschweiften Klammern.

Der folgende Code ist ein einfacher Block, der in geschweiften **`__asm`** Klammern eingeschlossen ist. (Der Code ist eine Prologsequenz für eine benutzerdefinierte Funktion).

```cpp
// asm_overview.cpp
// processor: x86
void __declspec(naked) main()
{
    // Naked functions must provide their own prolog...
    __asm {
        push ebp
        mov ebp, esp
        sub esp, __LOCAL_SIZE
    }

    // ... and epilog
    __asm {
        pop ebp
        ret
    }
}
```

Alternativ können Sie **`__asm`** jede Assemblyanweisung in den Vordergrund stellen:

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Da das- **`__asm`** Schlüsselwort ein Trennzeichen für Anweisungen ist, können Sie auch Assemblyanweisungen in die gleiche Zeile einfügen:

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
