---
title: Verwenden von Clang-Tidy in Visual Studio
description: Verwenden von Clang-Tidy in Visual Studio für Microsoft C++ Code Analyse.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
ms.openlocfilehash: 5b2da222caea435bdb24d774b5e93c995e734bb7
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919071"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Verwenden von Clang-Tidy in Visual Studio

::: moniker range="<=msvc-150"

Die Unterstützung für Clang-Tidy erfordert Visual Studio 2019, Version 16,4 oder höher. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end

::: moniker range=">=msvc-160"

Die Code Analyse unterstützt [clang-tidy](https://clang.llvm.org/extra/clang-tidy/) sowohl für MSBuild-als auch für cmake-Projekte, unabhängig davon, ob clang-oder MSVC-Toolsets verwendet werden. Clang-Tidy Prüfungen können als Teil der Hintergrund Code Analyse ausgeführt werden. Sie werden als Warnungen im Editor (Wellenlinien) angezeigt, und Sie werden in der Fehlerliste angezeigt.

Clang-Tidy-Unterstützung ist ab Visual Studio 2019, Version 16,4, verfügbar. Sie wird automatisch eingeschlossen, wenn Sie eine C++-Arbeitsauslastung in der Visual Studio-Installer auswählen.

Clang-Tidy ist das Standardanalyse Tool, wenn Sie das llvm/clang-cl-Toolset verwenden, das sowohl in MSBuild als auch in cmake verfügbar ist. Sie können Sie konfigurieren, wenn Sie ein MSVC-Toolset verwenden, um Sie parallel auszuführen oder um die standardmäßige Code Analyse zu ersetzen. Wenn Sie das clang-cl-Toolset verwenden, ist die Microsoft-Code Analyse nicht verfügbar.

Clang-Tidy nach erfolgreicher Kompilierung ausgeführt. Möglicherweise müssen Sie Quell Code Fehler auflösen, um Clang-Tidy Ergebnisse zu erhalten.

## <a name="msbuild"></a>MSBuild

Sie können Clang-Tidy so konfigurieren, dass Sie als Teil der Code Analyse ausgeführt wird, und auf der Seite "allgemeine **Code Analyse** "  >  **General** im Projekt Eigenschaftenfenster. Optionen zum Konfigurieren des Tools finden Sie im Untermenü Clang-Tidy.

Weitere Informationen finden Sie unter Gewusst [wie: Festlegen von Code Analyse Eigenschaften für C/C++-Projekte](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

In cmake-Projekten können Sie Clang-Tidy Prüfungen innerhalb von konfigurieren `CMakeSettings.json` . Wählen Sie nach dem Öffnen in der oberen rechten Ecke des Editors für den cmake-Projekteinstellungen die Option "JSON bearbeiten" aus. Die folgenden Schlüssel werden erkannt:

- `enableMicrosoftCodeAnalysis`: Aktiviert die Microsoft-Code Analyse.
- `enableClangTidyCodeAnalysis`: Aktiviert Clang-Tidy Analyse
- `clangTidyChecks`: Clang-Tidy Konfiguration, die als durch Trennzeichen getrennte Liste angegeben ist, d. h., ob Sie aktiviert oder deaktiviert werden soll.

Wenn keine der Optionen "enable" angegeben wird, wählt Visual Studio das Analysetool aus, das dem verwendeten Platt Form Toolset entspricht.

## <a name="warning-display"></a>Anzeige von Warnungen

Clang-Tidy Ausführungen führen zu Warnungen, die in der Fehlerliste angezeigt werden, und als im Editor befindliche Wellenlinien unterhalb relevanter Code Abschnitte. Verwenden Sie die Spalte "Category" im Fehlerliste, um Clang-Tidy Warnungen zu sortieren und zu organisieren. Sie können in-Editor-Warnungen konfigurieren, indem **Sie unter Extras** Optionen auf die Einstellung "Code Analyse Wellenlinien deaktivieren" umschalten  >  **Options** .

## <a name="clang-tidy-configuration"></a>Clang-Tidy Konfiguration

Über die Option " **clang-saubere Prüfungen** " können Sie überprüfen, ob "clang-tidy" in Visual Studio ausgeführt wird. Diese Eingabe wird dem- **`--checks`** Argument des Tools bereitgestellt. Jede weitere Konfiguration kann in benutzerdefinierte Dateien aufgenommen werden *`.clang-tidy`* . Weitere Informationen finden Sie in der [clang-bereinigen-Dokumentation auf llvm.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Siehe auch

- [Clang/llvm-Unterstützung für MSBuild-Projekte](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Clang/llvm-Unterstützung für cmake-Projekte](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
