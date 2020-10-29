---
title: /Qspectre
ms.date: 09/06/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.SpectreMitigation
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: a4872d18fed4523e235aee70839f1e482d78f345
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919110"
---
# <a name="qspectre"></a>/Qspectre

Gibt die Compilergenerierung von Anweisungen an, um bestimmte mit Spectre-Variante 1 zusammenhängende Sicherheitsrisiken abzumildern.

## <a name="syntax"></a>Syntax

> **/Qspectre**

## <a name="remarks"></a>Hinweise

Die Option **/Qspectre** ist in Visual Studio 2017, Version 15.5.5 und höher, und in Visual Studio 2015 Update 3 bis [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre) verfügbar. Sie bewirkt, dass der Compiler Anweisungen einfügt, um bestimmte [Spectre-Sicherheitsrisiken](https://spectreattack.com/spectre.pdf) zu verringern. Diese Sicherheitsrisiken werden als *spekulative Ausführungs Seitenkanalangriffe* bezeichnet. Sie wirken sich auf viele Betriebssysteme und moderne Prozessoren aus, einschließlich Prozessoren von Intel, AMD und Arm.

Die Option **/Qspectre** ist standardmäßig deaktiviert.

In ihrer ursprünglichen Version funktionierte die **/Qspectre** -Option nur mit optimiertem Code. In Visual Studio 2017, Version 15.7 und höher, wird die Option **/Qspectre** auf allen Optimierungsebenen unterstützt.

Microsoft Visual C++-Bibliotheken stehen ebenfalls in Versionen mit Spectre-Entschärfung zur Verfügung. Die Spectre-entschärften Bibliotheken für Visual Studio 2017 und höher können im Visual Studio-Installer heruntergeladen werden. Sie befinden sich auf der Registerkarte " **einzelne Komponenten** " unter **Compiler, Buildtools und Laufzeiten** und verfügen im Namen über "lisb for Spectre". Sowohl dll-als auch statische Laufzeitbibliotheken mit aktivierter Entschärfung sind für eine Teilmenge der Visual C++ Laufzeiten verfügbar: VC + + Start Code, vcruntime140, msvcp140, concrt140 und vcamp140. Die DLLs werden nur für die Anwendungs lokale Bereitstellung unterstützt. Der Inhalt der weitervertreibbaren Laufzeitbibliotheken Visual C++ 2017 und höher wurde nicht geändert.

Sie können auch Spectre-entschärfelte Bibliotheken für MFC und ATL installieren. Sie befinden sich auf der Registerkarte " **einzelne Komponenten** " unter **SDK, Bibliotheken und Frameworks** .

> [!NOTE]
> Für universelle Windows-Apps oder-Komponenten gibt es keine Versionen von Spectre-entschärten Bibliotheken. App-lokale Bereitstellung solcher Bibliotheken ist nicht möglich.

### <a name="applicability"></a>Anwendbarkeit

Wenn Ihr Code auf Daten angewendet wird, die eine Vertrauens Grenze überschreiten, empfiehlt es sich, die **/Qspectre** -Option zu verwenden, um den Code neu zu erstellen und erneut bereitzustellen, um dieses Problem so schnell wie möglich zu beheben. Ein Beispiel für einen solchen Code ist Code, der nicht vertrauenswürdige Eingaben lädt, die sich auf die Ausführung auswirken können. Beispielsweise Code, der Remote Prozedur Aufrufe ausführt, nicht vertrauenswürdige Eingaben oder Dateien analysiert oder andere Schnittstellen für die prozessübergreifende Kommunikation (Inter-Process Communication, IPC) verwendet. Standardtechniken wie das Verwenden einer Sandbox sind möglicherweise nicht ausreichend. Untersuchen Sie Ihre Sandkästen sorgfältig, bevor Sie entscheiden, dass Ihr Code keine Vertrauens Grenze überschreitet.

### <a name="availability"></a>Verfügbarkeit

Die **/Qspectre** -Option ist in Visual Studio 2017 Version 15.5.5 und in allen Updates für Microsoft C++ Compiler (MSVC) verfügbar, die am oder nach dem 23. Januar 2018 erstellt wurden. Verwenden Sie den Visual Studio-Installer, um den Compiler zu aktualisieren und um die Spectre-entschärften Bibliotheken als einzelne Komponenten zu installieren. Die **/Qspectre** -Option ist ferner in Visual Studio 2015 Update 3 bis zu einem Patch erhältlich. Weitere Informationen finden Sie in [KB 4338871](https://support.microsoft.com/help/4338871).

Alle Versionen von Visual Studio 2017 Version 15,5 und alle Vorschau Versionen von Visual Studio 2017 Version 15,6. schließt eine nicht dokumentierte Option ein, **/d2guardspecload** . Dies entspricht dem anfänglichen Verhalten von **/Qspectre** . Sie können **/d2guardspecload** verwenden, um in diesem Versionen des Compilers die gleichen Entschärfungen auf Ihren Code anzuwenden. Es wird empfohlen, den Build für die Verwendung von **/Qspectre** in Compilern zu aktualisieren, die die Option unterstützen. Die **/Qspectre** -Option unterstützt möglicherweise auch neue entschärfungen in späteren Versionen des Compilers.

### <a name="effect"></a>Wirkung

Die **/Qspectre** -Option gibt Code aus, um die Spectre-Variante 1, Bounds Check Bypass, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753) zu entschärfen. Sie funktioniert durch Einfügen von Anwendungen, die als Sperre der spekulativen Codeausführung fungieren. Die spezifischen Anweisungen zur Entschärfung der Prozessorspekulation hängen vom Prozessor und seiner Mikroarchitektur ab und können sich in kommenden Versionen des Compilers ändern.

Wenn Sie die **/Qspectre** -Option aktivieren, versucht der Compiler, Instanzen zu identifizieren, bei denen die spekulative Ausführung Grenzen Überprüfungen umgehen kann. An dieser Stelle werden die Anweisungen zur Barriere eingefügt. Es ist wichtig, dass Sie die Grenzwerte für die Analyse kennen, die ein Compiler zum Identifizieren von Instanzen von Variant 1 ausführen kann. Daher gibt es keine Garantie dafür, dass alle möglichen Instanzen von Variant 1 unter **/Qspectre** instrumentiert werden.

### <a name="performance-impact"></a>Auswirkungen auf die Leistung

Die Auswirkungen von **/Qspectre** auf die Leistung sind in mehreren sitbaren Codebasen zu vernachlässigen. Es gibt jedoch keine Garantie dafür, dass die Leistung Ihres Codes unter **/Qspectre** nicht beeinträchtigt ist. Sie sollten Benchmarks Ihres Codes vornehmen, um die Auswirkungen der Option auf die Leistung zu bestimmen. Wenn Sie wissen, dass die Entschärfung in einem Leistungs kritischen Block oder einer Leistungs kritischen Schleife nicht erforderlich ist, können Sie die Entschärfung selektiv deaktivieren, indem Sie eine [__declspec (Spectre (noentschärfung))](../../cpp/spectre.md) -Direktive verwenden. Diese Direktive ist nicht in Compilern verfügbar, die nur die **/d2guardspecload** -Option unterstützen.

### <a name="required-libraries"></a>Erforderliche Bibliotheken

Die **/Qspectre** -Compileroption generiert Code, der implizit Versionen der Laufzeitbibliotheken verknüpft, die erstellt wurden, um Spectre-entschärfungen bereitzustellen Diese Bibliotheken stellen optionale Komponenten dar, die mithilfe des Visual Studio-Installers installiert werden müssen:

- MSVC-Version *version_numbers* Libs for Spectre \[(x86 und x64) | (ARM) | (ARM64)]
- Visual C++ ATL für \[(x86/x64) | ARM | ARM64] mit Spectre-Entschärfungen
- Visual C++ MFC für \[x86/x64 | ARM | ARM64] mit Spectre-Entschärfungen

Wenn Sie Ihren Code mithilfe von **/Qspectre** erstellen und diese Bibliotheken nicht installiert sind, wird vom Buildsystem eine **Warnung ausgegeben MSB8038: Spectre Entschärfung ist aktiviert, aber Spectre-Entschärfungs Bibliotheken wurden nicht gefunden** . Wenn der MFC-oder ATL-Code nicht erstellt werden kann und der Linker einen Fehler meldet, wie z. b. einen schwerwiegenden **Fehler LNK1104: die Datei ' OLDNAMES. lib ' kann nicht geöffnet** werden. diese fehlenden Bibliotheken sind möglicherweise die Ursache.

### <a name="additional-information"></a>Zusätzliche Informationen

Weitere Informationen finden Sie in der offiziellen [Microsoft Security Advisory ADV180002 (Leitfaden zur Vermeidung von Sicherheitsrisiken für die spekulative Ausführung](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)). Anweisungen sind außerdem von Intel, [Speculative Execution Side Channel Mitigations](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf), und ARM, [Cache Speculation Side-channels](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf), erhältlich. Eine Windows-spezifische Übersicht über Spectre-und Meltdown-entschärfungen finden Sie Untergrund Legendes [zu den Auswirkungen von Spectre und entschärfungen auf Windows-Systemen](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/). Eine Übersicht über die von den MSVC-entschärfungen behandelten Spectre-Sicherheitsrisiken finden Sie unter Spectre-entschärfungen [in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) im C++-Teamblog.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

::: moniker range="msvc-160"

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **C/C++-** > **Code Generierung** aus.

1. Wählen Sie einen neuen Wert für die Eigenschaft **Spectre-Entschärfung** aus. Wählen Sie **OK** aus, um die Änderung zu übernehmen.

::: moniker-end

::: moniker range="<=msvc-150"

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf der Eigenschaftenseite auf **Konfigurationseigenschaften** > **C/C++** > **Befehlszeile** .

1. Geben Sie die Compileroption **/Qspectre** im Feld **Zusätzliche Optionen** ein. Wählen Sie **OK** aus, um die Änderung zu übernehmen.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[/Q-Optionen (Vorgänge auf niedriger Ebene)](q-options-low-level-operations.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-CompilerCommand-Line Syntax](compiler-command-line-syntax.md)
