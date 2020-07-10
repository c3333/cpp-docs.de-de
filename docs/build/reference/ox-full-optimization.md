---
title: /Ox (die meisten Geschwindigkeits Optimierungen aktivieren)
description: Die Option MSVC/Ox kombiniert einige der compileroptimierungs-Optionen für Geschwindigkeit in einer einzigen Option.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: 10893fe1cf032f2ab56f27aa4af95b050c2ec37e
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180837"
---
# <a name="ox-enable-most-speed-optimizations"></a>`/Ox`(Die meisten Geschwindigkeits Optimierungen aktivieren)

Die- **`/Ox`** Compileroption ermöglicht eine Kombination von Optimierungen, die die Geschwindigkeit bevorzugen. In einigen Versionen der Visual Studio-IDE und der compilerhilfe Meldung wird Sie als " *vollständige Optimierung*" bezeichnet, aber die **`/Ox`** Compileroption aktiviert nur eine Teilmenge der von aktivierten Optionen für die Geschwindigkeits Optimierung **`/O2`** .

## <a name="syntax"></a>Syntax

> **`/Ox`**

## <a name="remarks"></a>Bemerkungen

Die **`/Ox`** Compileroption aktiviert die **`/O`** Compileroptionen, die Geschwindigkeit bevorzugen. Die **`/Ox`** Compileroption enthält nicht die zusätzlichen Optionen [ `/GF` (vermeiden doppelter](gf-eliminate-duplicate-strings.md) Zeichen folgen) und [ `/Gy` (Funktionsebene verknüpfen)](gy-enable-function-level-linking.md) , die von [ `/O1` oder aktiviert `/O2` werden (minimieren Sie die Größe, maximieren Sie die Geschwindigkeit)](o1-o2-minimize-size-maximize-speed.md). Die zusätzlichen, von und angewendeten Optionen **`/O1`** **`/O2`** können Zeiger auf Zeichen folgen oder Funktionen zur Freigabe einer Zieladresse verursachen, was sich auf das Debuggen und die strikte sprach Konformität auswirken kann. Die **`/Ox`** -Option ist eine einfache Möglichkeit, die meisten Optimierungen zu aktivieren, ohne **`/GF`** und einzubeziehen **`/Gy`** . Weitere Informationen finden Sie in den Beschreibungen der [`/GF`](gf-eliminate-duplicate-strings.md) Optionen und [`/Gy`](gy-enable-function-level-linking.md) .

Die **`/Ox`** Compileroption ist identisch mit der Verwendung der folgenden Optionen in Kombination:

- [ `/Ob` (Inline Funktionserweiterung)](ob-inline-function-expansion.md), wobei der Option-Parameter 2 ( **`/Ob2`** ) ist

- [`/Oi`(Intrinsische Funktionen generieren)](oi-generate-intrinsic-functions.md)

- [`/Ot`(Schnellen Code bevorzugen)](os-ot-favor-small-code-favor-fast-code.md)

- [`/Oy`(Frame Zeiger Auslassung)](oy-frame-pointer-omission.md)

**`/Ox`** schließt sich gegenseitig aus:

- [`/O1`(Größe minimieren)](o1-o2-minimize-size-maximize-speed.md)

- [`/O2`(Geschwindigkeit maximieren)](o1-o2-minimize-size-maximize-speed.md)

- [`/Od`(Deaktivieren (Debuggen))](od-disable-debug.md)

Wenn Sie angeben, können Sie die Geschwindigkeit der- **`/Ox`** Compileroption Abbrechen **`/Oxs`** , die die- **`/Ox`** Compileroption mit kombiniert [ `/Os` (kleinen Code bevorzugen)](os-ot-favor-small-code-favor-fast-code.md). Die kombinierten Optionen bevorzugen kleinere Codegröße.  Die **`/Oxs`** Option ist exakt identisch mit der Angabe **`/Ox`** **`/Os`** , wann die Optionen in dieser Reihenfolge angezeigt werden.

Wenn Sie alle verfügbaren Optimierungen auf Dateiebene für Releasebuilds anwenden möchten, wird [ `/O2` ](o1-o2-minimize-size-maximize-speed.md) empfohlen, anstelle von **`/Ox`** und [ `/O1` (Minimierung der Größe)](o1-o2-minimize-size-maximize-speed.md) anstelle von anzugeben (Geschwindigkeit zu maximieren) **`/Oxs`** . Beachten Sie bei der Optimierung der Releasebuilds auch die Compileroption [ `/GL` (gesamte Programm Optimierung)](gl-whole-program-optimization.md) und die [ `/LTCG` Linkeroption (Link-Time Code Generation)](ltcg-link-time-code-generation.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Optimierung** aus.

1. Ändern Sie die Eigenschaft **Optimierung** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Weitere Informationen

[`/O`Optionen (Code optimieren)](o-options-optimize-code.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
