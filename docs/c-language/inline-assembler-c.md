---
title: Inlineassembler (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
ms.openlocfilehash: f6bff3bfef64b45c8a02bb9ad69d2731ba778525
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229609"
---
# <a name="inline-assembler-c"></a>Inlineassembler (C)

**Microsoft-spezifisch**

Mit dem Inlineassembler können Sie Assemblysprachanweisungen direkt in C-Quellprogramme einbetten, ohne zusätzliche Assembly- oder Verknüpfungsschritte. Der Inlineassembler ist im Compiler integriert, daher benötigen Sie keinen getrennten Assembler wie den Microsoft Macro Assembler (MASM).

Da der Inlineassembler keine separaten Assembly- und Verknüpfungsschritte erfordert, ist er einfacher als ein getrennter Assembler. Der Inlineassemblycode kann alle C-Variablen und -Funktionsnamen verwenden, die sich im Gültigkeitsbereich befinden. Daher ist es einfach, ihn in den C-Programmcode zu integrieren. Und da der Assemblycode mit C-Anweisungen kombiniert werden kann, kann er Aufgaben ausführen, die in C allein mühsam oder unmöglich sind.

Das **`__asm`** -Schlüsselwort ruft den Inlineassembler auf und kann überall vorkommen, wo eine C-Anweisung gültig ist. Es kann nicht allein stehen. Ihm muss eine Assemblyanweisung, eine Gruppe von Anweisungen, die in geschweifte Klammern eingeschlossen sind, oder zumindest ein leeres Paar geschweifter Klammern folgen. Der Begriff „ **`__asm`** -Block“ bezieht sich hier auf eine beliebige Anweisung bzw. Gruppe von Anweisungen, unabhängig davon, ob in geschweifte Klammern gesetzt oder nicht.

Der folgende Code ist ein einfacher **`__asm`** -Block, der in geschweifte Klammern eingeschlossen ist. (Der Code ist eine Prologsequenz für eine benutzerdefinierte Funktion).

```
__asm
{
   push ebp
   mov  ebp, esp
   sub  esp, __LOCAL_SIZE
}
```

Alternativ können Sie **`__asm`** vor jede Assemblyanweisung setzen:

```
__asm push ebp
__asm mov  ebp, esp
__asm sub  esp, __LOCAL_SIZE
```

Da das **`__asm`** -Schlüsselwort ein Trennzeichen für Anweisungen ist, können Sie die Assemblyanweisungen auch in die gleiche Zeile einfügen:

```
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Funktionsattribute](../c-language/function-attributes.md)
