---
title: /Os, /Ot (Kompakten Code bevorzugen, Schnellen Code bevorzugen)
ms.date: 11/04/2016
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
ms.openlocfilehash: 0eda9461b3ef730e0e0a832aa94a688e03c7e1bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336186"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Kompakten Code bevorzugen, Schnellen Code bevorzugen)

Minimiert oder maximiert die Größe von EXEs und DLLs.

## <a name="syntax"></a>Syntax

```
/Os
/Ot
```

## <a name="remarks"></a>Bemerkungen

**/Os** (Favor Small Code) minimiert die Größe von EXEs und DLLs, indem der Compiler angewiesen wird, Größe gegenüber Geschwindigkeit zu bevorzugen. Der Compiler kann viele C- und C++-Konstrukte auf funktional ähnliche Sequenzen von Maschinencode reduzieren. Gelegentlich bieten diese Unterschiede Kompromisse von Größe zu Geschwindigkeit. Mit den Optionen **/Os** und **/Ot** können Sie eine Voreinstellung für eine einstellung zu einander angeben:

**/Ot** (Favor Fast Code) maximiert die Geschwindigkeit von EXEs und DLLs, indem er den Compiler anweist, Geschwindigkeit über Größe zu bevorzugen. (Dies ist die Standardeinstellung.) Der Compiler kann viele C- und C++-Konstrukte auf funktional ähnliche Sequenzen von Maschinencode reduzieren. Gelegentlich bieten diese Unterschiede Kompromisse von Größe zu Geschwindigkeit. Die Option **/Ot** wird durch die Option Geschwindigkeit maximieren ([/O2](o1-o2-minimize-size-maximize-speed.md)) impliziert. Die Option **/O2** kombiniert mehrere Optionen, um sehr schnellen Code zu erzeugen.

Wenn Sie **/Os** oder **/Ot**verwenden, müssen Sie auch [/Og](og-global-optimizations.md) angeben, um den Code zu optimieren.

> [!NOTE]
> Informationen, die aus Profilerstellungstestläufen gesammelt werden, überschreiben Optimierungen, die andernfalls wirksam wären, wenn Sie **/Ob**, **/Os**oder **/Ot**angeben. Weitere Informationen finden Sie unter [Profilgesteuerte Optimierungen](../profile-guided-optimizations.md).

**x86-spezifisch**

Der folgende Beispielcode veranschaulicht den Unterschied zwischen den Optionen "Kleiner Code favor" (**/Os**) und der Option "Schneller Code favorisieren" (**/Ot**):

> [!NOTE]
> Im Folgenden wird das erwartete Verhalten bei der Verwendung von **/Os** oder **/Ot**beschrieben. Das Compilerverhalten von Release zu Release kann jedoch zu unterschiedlichen Optimierungen für den folgenden Code führen.

```
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

Wie im Fragment des Maschinencodes unten gezeigt, implementiert der Compiler, wenn DIFFER.c für Größe (**/Os**) kompiliert wird, den multiplizierten Ausdruck in der return-Anweisung explizit als Multiplikation, um eine kurze, aber langsamere Sequenz von Code zu erzeugen:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Wenn DIFFER.c für Geschwindigkeit kompiliert wird (**/Ot**), implementiert der Compiler den Multiplikatorausdruck in der Return-Anweisung alternativ als eine Reihe von Verschiebungen und `LEA` Anweisungen, um eine schnelle, aber längere Sequenz von Code zu erzeugen:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**END x86 Spezifisch**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Optimierung.**

1. Ändern Sie die **Eigenschaft "Begünstigte Größe" oder "Geschwindigkeit".**

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Siehe auch

[/O-Optionen (Code optimieren)](o-options-optimize-code.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
