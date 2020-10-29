---
title: /QIntel-jcc-erratum
description: Beschreibt die/QIntel-JCC-Erratum-Option von Microsoft C/C++ Compiler (MSVC).
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: c66dd4bb25647ce193bce4db5dc4ebb1268277c0
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921372"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=msvc-150"

Die **/QIntel-JCC-Erratum** -Option ist in Visual Studio 2019, Version 16,5 und höher, verfügbar.

::: moniker-end

::: moniker range=">=msvc-160"

Gibt an, dass der Compiler Anweisungen generiert, um die Auswirkungen auf die Leistung zu mindern, die durch den Intel Jump Conditional Code (JCC) Erratum-Mikro Code Update in bestimmten Intel-Prozessoren verursacht werden.

## <a name="syntax"></a>Syntax

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>Hinweise

Unter **/QIntel-JCC-Erratum** erkennt der Compiler Sprung-und Makro Verknüpfungen, die auf einer 32-Byte-Grenze überschreiten oder enden. Diese Anweisungen werden an die Grenze ausgerichtet. Durch diese Änderung werden die Auswirkungen von Mikro Code Aktualisierungen auf die Leistung verringert, die JCC Erratum in bestimmten Intel-Prozessoren verhindern. Weitere Informationen zum Erratum finden Sie unter entschärfungen [für Jump Conditional Code Erratum](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf) auf der Intel-Website.

Die **/QIntel-JCC-Erratum** -Option ist in Visual Studio 2019, Version 16,5 und höher, verfügbar. Diese Option ist nur in Compilern verfügbar, die auf x86 und x64 abzielen. Die Option ist nicht in Compilern verfügbar, die auf ARM-Prozessoren abzielen.

Die **/QIntel-JCC-Erratum** -Option ist standardmäßig deaktiviert und funktioniert nur in optimierten Builds. Mit dieser Option kann die Codegröße erhöht werden.

**/QIntel-JCC-Erratum** ist nicht mit [/CLR](clr-common-language-runtime-compilation.md)kompatibel.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **C/C++-** > **Code Generierung** aus.

1. Wählen Sie einen Wert für die Eigenschaft **Intel JCC Erratum Entschärfung aktivieren** aus. Wählen Sie **OK** aus, um die Änderung zu übernehmen.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[/Q-Optionen (Vorgänge auf niedriger Ebene)](q-options-low-level-operations.md)\
[MSVC-Compileroptionen](compiler-options.md)\
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)

::: moniker-end
