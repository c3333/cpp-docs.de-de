---
title: /analyze (Codeanalyse)
description: Die Syntax und Verwendung der Microsoft C++-Compiler/analyze-Option.
ms.date: 07/27/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: 643d8428e3760926832429db5a4425e078ed776b
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389791"
---
# <a name="analyze-code-analysis"></a>`/analyze`(Code Analyse)

Aktiviert Codeanalyse- und Steueroptionen.

## <a name="syntax"></a>Syntax

::: moniker range=">=vs-2017"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***Erweiterung*\
> **`/analyze:log`***Dateiname*\
> **`/analyze:max_paths`***Zahl*\
> **`/analyze:only`**\
> **`/analyze:plugin`***Plug-in-dll*\
> **`/analyze:quiet`**\
> **`/analyze:ruleset`***Regelsatz*\
> **`/analyze:stacksize`***Zahl*\
> **`/analyze:WX-`**

::: moniker-end
::: moniker range="vs-2015"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***Erweiterung*\
> **`/analyze:log`***Dateiname*\
> **`/analyze:max_paths`***Zahl*\
> **`/analyze:only`**\
> **`/analyze:plugin`***Plug-in-dll*\
> **`/analyze:quiet`**\
> **`/analyze:stacksize`***Zahl*\
> **`/analyze:WX-`**

::: moniker-end

## <a name="arguments"></a>Argumente

**`/analyze`**\
Aktiviert die Analyse im Standardmodus. Die Analyse Ausgabe wird wie andere Fehlermeldungen an die Konsole oder das Visual Studio- **Ausgabe** Fenster weitergeleitet. Verwenden **`/analyze-`** Sie, um die Analyse explizit zu deaktivieren.

**`/analyze:autolog`**\
Ausführliche Analyseergebnisse werden als XML in eine Datei geschrieben, die denselben Basis Namen wie die Quelldatei und eine Erweiterung von hat *`.pftlog`* . **`/analyze:autolog-`** deaktiviert diese Protokolldatei.

**`/analyze:autolog:ext`***Erweiterung*\
Ausführliche Analyseergebnisse werden als XML in eine Datei geschrieben, die denselben Basis Namen wie die Quelldatei und eine Erweiterung der *Erweiterung*hat.

**`/analyze:log`***Dateiname*\
Ausführliche Analyseergebnisse werden als XML in die Datei geschrieben, die durch *filename*angegeben wird.

**`/analyze:max_paths`***Zahl*\
Der mit dieser Option verwendete *Number* -Parameter gibt die maximale Anzahl von Codepfade an, die analysiert werden sollen. Wenn dieser Parameter nicht angegeben wird, ist die Zahl standardmäßig 256. Größere Werte führen zu einer gründlicheren Überprüfung, aber die Analyse kann länger dauern.

**`/analyze:only`**\
In der Regel generiert der Compiler Code und führt nach der Ausführung der Analyse eine erweiterte Syntaxprüfung durch. Durch die **`/analyze:only`** Option wird dieser Code Generierungs Durchlauf deaktiviert. Dadurch wird die Analyse schneller, aber keine Compilerfehler und-Warnungen ausgegeben, die der Code Generierungs Durchlauf des Compilers möglicherweise findet. Wenn das Programm keine Fehler bei der Codegenerierung hat, sind die Analyseergebnisse möglicherweise unzuverlässig. Es wird empfohlen, diese Option nur zu verwenden, wenn der Code die Syntax Überprüfung der Codegenerierung bereits ohne Fehler durchläuft.

**`/analyze:plugin`***Plug-in-dll*\
Aktiviert das angegebene PREfast-Plug-in als Teil der Code Analyse Ausführungen.

::: moniker range="<=vs-2017"

LocalEspC.dll ist das Plug-in, das Parallelitäts bezogene Code Analyse Überprüfungen im Bereich der C261XX-Warnungen implementiert. Beispiel: [C26100](/cpp/code-quality/c26100), [C26101](/cpp/code-quality/c26101),..., [C26167](/cpp/code-quality/c26167).

Verwenden Sie diese Compileroption, um LocalEspC.dll auszuführen:**`/analyze:plugin LocalEspC.dll`**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck.dll implementiert neben läufigkeits bezogene Code Analyse Überprüfungen im Bereich der C261XX-Warnungen. Beispiel: [C26100](/cpp/code-quality/c26100), [C26101](/cpp/code-quality/c26101),..., [C26167](/cpp/code-quality/c26167).

Um ConcurrencyCheck.dll auszuführen, führen Sie zuerst den folgenden Befehl über eine Developer-Eingabeaufforderung aus:

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

Verwenden Sie dann diese Compileroption: **`/analyze:plugin EspXEngine.dll`** .

Um CppCoreCheck.dll auszuführen, führen Sie zuerst den folgenden Befehl über eine Developer-Eingabeaufforderung aus:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Verwenden Sie dann diese Compileroption: **`/analyze:plugin EspXEngine.dll`** .

::: moniker-end

**`/analyze:quiet`**\
Deaktiviert die Analyzer-Ausgabe in die Konsole oder das **Ausgabe** Fenster von Visual Studio.

::: moniker range=">=vs-2017"

**`/analyze:ruleset`***FILE_PATH. RuleSet*\
Ermöglicht Ihnen die Angabe der zu analysierenden Regelsätze, einschließlich benutzerdefinierter Regelsätze, die Sie selbst erstellen können. Wenn dieser Switch festgelegt ist, ist die Regel-Engine effizienter, da Sie vor der Ausführung nicht-Member des angegebenen Regelsatzes ausschließt. Andernfalls prüft die Engine alle Regeln.

Die RuleSets, die mit Visual Studio ausgeliefert werden, finden Sie unter *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* .

Der folgende Beispiel benutzerdefinierte Regelsatz weist das Regel Modul an, nach C6001 und C26494 zu suchen. Sie können diese Datei beliebig lange platzieren, wenn Sie über eine *`.ruleset`* Erweiterung verfügt, und Sie geben den vollständigen Pfad im Argument an.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

**`/analyze:stacksize`***Zahl*\
Der mit dieser Option verwendete *Number* -Parameter gibt die Größe (in Bytes) des Stapel Rahmens an, für den die Warnung [C6262](/cpp/code-quality/c6262) generiert wird. Der Leerraum vor der *Zahl* ist optional. Wenn dieser Parameter nicht angegeben wird, beträgt die Stapel Rahmengröße standardmäßig 16 KB.

**`/analyze:WX-`**\
Code Analyse Warnungen werden nicht als Fehler behandelt, wenn Sie mit kompilieren **`/WX`** . Weitere Informationen finden Sie unter [ `/WX` (Warnstufe)](compiler-option-warning-level.md).

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Übersicht über die Code Analyse für c/C++](/cpp/code-quality/code-analysis-for-c-cpp-overview) und [Code Analyse für c/C++-Warnungen](/cpp/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**  >  Seite allgemeine**Code Analyse**für die Konfiguration aus  >  **General** .

1. Ändern Sie eine oder mehrere der **Code Analyse** Eigenschaften.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

1. Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)\
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
