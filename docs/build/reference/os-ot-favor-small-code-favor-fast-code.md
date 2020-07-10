---
title: /Os, /Ot (Kompakten Code bevorzugen, Schnellen Code bevorzugen)
description: Die MSVC-Compileroptionen/OS und/OT geben an, ob beim Optimieren von Code die Größe oder Geschwindigkeit bevorzugt werden soll.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
ms.openlocfilehash: 384019ddf7b80b8dd4e00197d73d1e4ac536634c
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180824"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>`/Os`, `/Ot` (Kleinen Code bevorzugen, schnellen Code bevorzugen)

Minimiert oder maximiert die Größe von exe-und DLLs.

## <a name="syntax"></a>Syntax

> **`/Os`**\
> **`/Ot`**

## <a name="remarks"></a>Bemerkungen

**`/Os`**(Kleinen Code bevorzugen) minimiert die Größe von exe-und DLLs, indem der Compiler angewiesen wird, die Größe gegenüber der Geschwindigkeit zu bevorzugen. Der Compiler kann viele C-und C++-Konstrukte auf funktionale ähnliche Sequenzen von Computercode reduzieren. Gelegentlich bieten diese Unterschiede Kompromisse zwischen Größe und Geschwindigkeit. **`/Os`** Mit den **`/Ot`** Optionen und können Sie eine bevorzugte Einstellung für eine der folgenden Optionen angeben:

**`/Ot`**(Schnellen Code bevorzugen) maximiert die Geschwindigkeit von EXEs und DLLs, indem der Compiler angewiesen wird, die Geschwindigkeit der Größe zu bevorzugen. **`/Ot`** ist die Standardeinstellung, wenn Optimierungen aktiviert sind. Der Compiler kann viele C-und C++-Konstrukte auf funktionale ähnliche Sequenzen von Computercode reduzieren. Gelegentlich bieten diese Unterschiede Kompromisse zwischen Größe und Geschwindigkeit. Die **`/Ot`** Option wird durch die [`/O2`](o1-o2-minimize-size-maximize-speed.md) Option (maximale Geschwindigkeit) impliziert. Die **`/O2`** Option kombiniert mehrere Optionen, um schnelleren Code zu liefern.

> [!NOTE]
> Informationen, die bei der Profilerstellung für Testläufe gesammelt werden, überschreiben alle Optimierungen, die andernfalls wirksam sind, wenn Sie **`/Ob`** , **`/Os`** oder angeben **`/Ot`** . Weitere Informationen finden Sie unter [Profilgesteuerte Optimierungen](../profile-guided-optimizations.md).

### <a name="x86-specific-example"></a>x86-spezifisches Beispiel

Im folgenden Beispielcode wird der Unterschied zwischen der Option **`/Os`** (kleinen Code bevorzugen) und der **`/Ot`** Option (schneller Code bevorzugen) veranschaulicht:

> [!NOTE]
> In diesem Beispiel wird das erwartete Verhalten beim Verwenden von **`/Os`** oder beschrieben **`/Ot`** . Das Compilerverhalten von Release zu Release führt jedoch möglicherweise zu unterschiedlichen Optimierungen für den folgenden Code.

```c
/* differ.c
  This program implements a multiplication operator
  Compile with /Os to implement multiply explicitly as multiply.
  Compile with /Ot to implement as a series of shift and LEA instructions.
*/
int differ(int x)
{
    return x * 71;
}
```

Wenn *`differ.c`* für Size () kompiliert wird **`/Os`** , implementiert der Compiler den multiplizierten Ausdruck in der Return-Anweisung explizit als Multiplikation, um eine kurze, aber langsamere Codefolge zu erstellen:

```asm
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Wenn *`differ.c`* für die Geschwindigkeit () kompiliert wird **`/Ot`** , implementiert der Compiler den Multiplikations Ausdruck in der Return-Anweisung als eine Reihe von Shift und `LEA` Anweisungen, um eine schnelle, aber längere Sequenz von Code zu erstellen:

```asm
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Optimierung** aus.

1. Ändern Sie die Eigenschaft **favor Size oder Speed** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Weitere Informationen

[/O-Optionen (Code optimieren)](o-options-optimize-code.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
