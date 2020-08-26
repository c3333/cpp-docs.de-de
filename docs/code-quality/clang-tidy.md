---
title: Verwenden von clang-tidy in Visual Studio
description: Verwendung von clang-tidy in Visual Studio für Microsoft C++ Code Analyse.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
ms.openlocfilehash: 30378ab0713d5e00e704f778646b9d60856f2234
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842467"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Verwenden von clang-tidy in Visual Studio

::: moniker range="<=vs-2017"

Für die Unterstützung von clang-Tidy ist Visual Studio 2019 Version 16,4 oder höher erforderlich. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end

::: moniker range=">=vs-2019"

Die Code Analyse unterstützt [clang-tidy](https://clang.llvm.org/extra/clang-tidy/) sowohl für MSBuild-als auch für cmake-Projekte, unabhängig davon, ob clang-oder MSVC-Toolsets verwendet werden. Clang-saubere Überprüfungen können als Teil der Hintergrund Code Analyse ausgeführt werden. Sie werden als Warnungen im Editor (Wellenlinien) angezeigt, und Sie werden in der Fehlerliste angezeigt.

Clang-saubere Unterstützung steht ab Visual Studio 2019, Version 16,4, zur Verfügung. Sie wird automatisch eingeschlossen, wenn Sie eine C++-Arbeitsauslastung in der Visual Studio-Installer auswählen.

Clang-Tidy ist das Standardanalyse Tool, wenn Sie das llvm/clang-cl-Toolset verwenden, das sowohl in MSBuild als auch in cmake verfügbar ist. Sie können Sie konfigurieren, wenn Sie ein MSVC-Toolset verwenden, um Sie parallel auszuführen oder um die standardmäßige Code Analyse zu ersetzen. Wenn Sie das clang-cl-Toolset verwenden, ist die Microsoft-Code Analyse nicht verfügbar.

Clang-Tidy wird nach erfolgreicher Kompilierung ausgeführt. Möglicherweise müssen Sie Quell Code Fehler auflösen, um clang-saubere Ergebnisse zu erhalten.

## <a name="msbuild"></a>MSBuild

Sie können clang-tidy so konfigurieren, dass Sie als Teil der Code Analyse ausgeführt werden und auf der Seite "allgemeine **Code Analyse**"  >  **General** im Projekt Eigenschaftenfenster erstellt werden. Optionen zum Konfigurieren des Tools finden Sie im Untermenü clang-tidy.

Weitere Informationen finden Sie unter Gewusst [wie: Festlegen von Code Analyse Eigenschaften für C/C++-Projekte](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

In cmake-Projekten können Sie clang-saubere Überprüfungen innerhalb von konfigurieren `CMakeSettings.json` . Wählen Sie nach dem Öffnen in der oberen rechten Ecke des Editors für den cmake-Projekteinstellungen die Option "JSON bearbeiten" aus. Die folgenden Schlüssel werden erkannt:

- `enableMicrosoftCodeAnalysis`: Aktiviert die Microsoft-Code Analyse.
- `enableClangTidyCodeAnalysis`: Aktiviert die clang-saubere Analyse
- `clangTidyChecks`: Clang-saubere Konfiguration, angegeben als eine durch Trennzeichen getrennte Liste, d. h., ob Sie aktiviert oder deaktiviert werden soll.

Wenn keine der Optionen "enable" angegeben wird, wählt Visual Studio das Analysetool aus, das dem verwendeten Platt Form Toolset entspricht.

## <a name="warning-display"></a>Anzeige von Warnungen

Clang-saubere Ausführungen führen zu Warnungen, die in der Fehlerliste angezeigt werden, und als in-Editor-Wellenlinien unterhalb relevanter Code Abschnitte. Verwenden Sie die Spalte "Category" im Fehlerliste, um clang-saubere Warnungen zu sortieren und zu organisieren. Sie können in-Editor-Warnungen konfigurieren, indem **Sie unter Extras**Optionen auf die Einstellung "Code Analyse Wellenlinien deaktivieren" umschalten  >  **Options**.

## <a name="clang-tidy-configuration"></a>Clang-saubere Konfiguration

Über die Option " **clang-saubere Prüfungen** " können Sie überprüfen, ob "clang-tidy" in Visual Studio ausgeführt wird. Diese Eingabe wird dem- **`--checks`** Argument des Tools bereitgestellt. Jede weitere Konfiguration kann in benutzerdefinierte Dateien aufgenommen werden *`.clang-tidy`* . Weitere Informationen finden Sie in der [clang-bereinigen-Dokumentation auf llvm.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Weitere Informationen

- [Clang/llvm-Unterstützung für MSBuild-Projekte](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Clang/llvm-Unterstützung für cmake-Projekte](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
