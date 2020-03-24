---
title: Übersicht über Inlineassembler
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
ms.openlocfilehash: 6233e07e115c21a0a173f094079dc9c1753533b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169396"
---
# <a name="inline-assembler-overview"></a>Übersicht über Inlineassembler

**Microsoft-spezifisch**

Mit dem Inline Assembler können Sie Assemblysprachanweisungen in Ihre C C++ -und Quell Programme einbetten, ohne zusätzliche Assembly-und Link Schritte auszuführen. Der Inlineassembler ist im Compiler integriert, daher benötigen Sie keinen getrennten Assembler wie den Microsoft Macro Assembler (MASM).

Da der Inlineassembler keine separaten Assembly- und Verknüpfungsschritte erfordert, ist er einfacher als ein getrennter Assembler. Inline-Assemblycode kann alle C++ c-oder Variablen-oder Funktionsnamen verwenden, die sich im Gültigkeitsbereich befinden. Daher ist es einfach C++ , ihn in den c-und Code Ihres Programms zu integrieren. Und da der Assemblycode mit c-und C++ -Anweisungen gemischt werden kann, kann er Aufgaben ausführen, die in c C++ oder allein mühsam oder unmöglich sind.

Das [__asm](../../assembler/inline/asm.md) -Schlüsselwort Ruft den Inline Assembler auf und kann überall vorkommen C++ , wo eine C-oder-Anweisung zulässig ist. Es kann nicht allein stehen. Ihm muss eine Assemblyanweisung, eine Gruppe von Anweisungen, die in geschweifte Klammern eingeschlossen sind, oder zumindest ein leeres Paar geschweifter Klammern folgen. Der Begriff "`__asm`-Block" bezieht sich hier auf eine beliebige Anweisung bzw. Gruppe von Anweisungen, unabhängig davon, ob in geschweifte Klammern gesetzt oder nicht.

Der folgende Code ist ein einfacher `__asm` Block, der in geschweiften Klammern eingeschlossen ist. (Der Code ist eine Prologsequenz für eine benutzerdefinierte Funktion).

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

Alternativ können Sie `__asm` vor jede Assemblyanweisung setzen:

```cpp
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Da das `__asm`-Schlüsselwort ein Trennzeichen für Anweisungen ist, können Sie die Assemblyanweisungen auch in die gleiche Zeile einfügen:

```cpp
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Inlineassembler](../../assembler/inline/inline-assembler.md)<br/>
