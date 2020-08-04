---
title: /cgthreads (Codegenerierungsthreads)
ms.date: 07/31/2020
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: 319a42ab68f02df6019ff283f1039ef3d561c4a0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520874"
---
# <a name="cgthreads-code-generation-threads"></a>`/cgthreads`(Code Generierungs Threads)

Legt die Anzahl der cl.exe-Threads fest, die für Optimierung und Codegenerierung verwendet werden.

## <a name="syntax"></a>Syntax

> **`/cgthreads1`**\
> **`/cgthreads2`**\
> **`/cgthreads3`**\
> **`/cgthreads4`**\
> **`/cgthreads5`**\
> **`/cgthreads6`**\
> **`/cgthreads7`**\
> **`/cgthreads8`**

## <a name="arguments"></a>Argumente

**`cgthreadsN`**\
Die maximale Anzahl von Threads, die von cl.exe verwendet werden sollen, wobei *N* eine Zahl zwischen 1 und 8 ist.

## <a name="remarks"></a>Bemerkungen

Die **`cgthreads`** -Option gibt die maximale Anzahl von Threads an, die cl.exe parallel für die Optimierungs-und Code Generierungs Phasen der Kompilierung verwenden. Beachten Sie, dass kein Leerzeichen zwischen **`cgthreads`** und dem *Number* -Argument vorhanden sein kann. Standardmäßig verwendet cl.exe vier Threads, als wären Sie **`/cgthreads4`** angegeben. Wenn mehr Prozessorkerne verfügbar sind, kann sich die Buildzeiten durch einen höheren *Zahlen* Wert verbessern. Diese Option ist besonders nützlich, wenn Sie mit [ `/GL` (Optimierung des gesamten Programms)](gl-whole-program-optimization.md)kombiniert wird.

Für einen Build können mehrere Stufen der Parallelität angegeben werden. Der msbuild.exe-Schalter **`/maxcpucount`** gibt die Anzahl der MSBuild-Prozesse an, die parallel ausgeführt werden können. Das Compilerflag [ `/MP` (Build with multiple Processes)](mp-build-with-multiple-processes.md) gibt die Anzahl der cl.exe Prozesse an, die die Quelldateien gleichzeitig kompilieren. Die **`cgthreads`** Option gibt die Anzahl der Threads an, die von den einzelnen cl.exe Prozessen verwendet werden. Der Prozessor kann nur so viele Threads gleichzeitig ausführen, wie Prozessorkerne vorhanden sind. Es ist nicht sinnvoll, für alle diese Optionen gleichzeitig größere Werte anzugeben, und es kann ein kontra Wert sein. Weitere Informationen zum parallelen Erstellen von Projekten finden Sie unter [Paralleles Erstellen von mehreren Projekten](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** in include **`cgthreadsN`** , wobei *`N`* ein Wert von 1 bis 8 ist, und wählen Sie dann **OK**aus.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
