---
title: Verwenden von Clang-Tidy in Visual Studio
description: Verwenden von Clang-Tidy in Visual Studio für die Microsoft C++-Codeanalyse.
ms.date: 02/19/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.openlocfilehash: ff32f522eaacee67e19aedaa1153b2c68edc98d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355148"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Verwenden von Clang-Tidy in Visual Studio

::: moniker range="<=vs-2017"

Die Unterstützung für Clang-Tidy erfordert Visual Studio 2019 Version 16.4 oder höher. Um die Dokumentation für diese Version **Version** anzuzeigen, legen Sie das Visual Studio Version-Selektor-Steuerelement für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end

::: moniker range=">=vs-2019"

Die Codeanalyse unterstützt [Clang-Tidy](https://clang.llvm.org/extra/clang-tidy/) nativ für MSBuild- und CMake-Projekte, unabhängig davon, ob Sie Clang- oder MSVC-Toolsets verwenden. Clang-Tidy-Prüfungen können als Teil der Hintergrundcodeanalyse ausgeführt werden. Sie werden als In-Editor-Warnungen (Squiggles) angezeigt und in der Fehlerliste angezeigt.

Die Clang-Tidy-Unterstützung ist ab Visual Studio 2019 Version 16.4 verfügbar. Sie wird automatisch eingeschlossen, wenn Sie eine C++-Workload im Visual Studio Installer auswählen.

Clang-Tidy ist das Standardanalysetool bei Verwendung des Toolsets LLVM/clang-cl, das sowohl in MSBuild als auch in CMake verfügbar ist. Sie können es konfigurieren, wenn Sie ein MSVC-Toolset verwenden, um neben der Standardmäßigen Codeanalyse-Erfahrung ausgeführt oder ersetzt zu werden. Wenn Sie das clang-cl-Toolset verwenden, ist Microsoft Code Analysis nicht verfügbar.

Clang-Tidy wird nach erfolgreicher Kompilierung ausgeführt. Möglicherweise müssen Sie Quellcodefehler beheben, um Clang-Tidy-Ergebnisse zu erhalten.

## <a name="msbuild"></a>MSBuild

Sie können Clang-Tidy so konfigurieren, dass es sowohl als Teil der Codeanalyse als auch als Build unter der Seite **Codeanalyse** > **Allgemein** im Fenster Projekteigenschaften ausgeführt wird. Optionen zum Konfigurieren des Tools finden Sie im Untermenü Clang-Tidy.

Weitere Informationen finden Sie unter [Gewusst wie: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

In CMake-Projekten können Sie Clang-Tidy-Prüfungen innerhalb `CMakeSettings.json`konfigurieren. Klicken Sie nach dem Öffnen in der oberen rechten Ecke des CMake-Projekteinstellungs-Editors auf "Bearbeiten von JSON". Die folgenden Schlüssel werden erkannt:

- `enableMicrosoftCodeAnalysis`: Aktiviert Microsoft-Codeanalyse
- `enableClangTidyCodeAnalysis`: Ermöglicht clang-Tidy-Analyse
- `clangTidyChecks`: Clang-Tidy-Konfiguration, angegeben als durch Kommas getrennte Liste, d. d. a. aktivierte oder deaktivierte Prüfungen

Wenn keine der Optionen "aktivieren" angegeben ist, wählt Visual Studio das Analysetool aus, das dem verwendeten Platform Toolset entspricht.

## <a name="warning-display"></a>Warnanzeige

Clang-Tidy-Läufe führen zu Warnungen, die in der Fehlerliste angezeigt werden, und als In-Editor-Squiggles unter relevanten Codeabschnitten. Verwenden Sie die Spalte "Kategorie" in der Fehlerliste, um Clang-Tidy-Warnungen zu sortieren und zu organisieren. Sie können In-Editor-Warnungen konfigurieren, indem Sie die Einstellung "Codeanalyse-Squiggles deaktivieren" unter > **Werkzeugoptionen**umschalten. **Tools**

## <a name="clang-tidy-configuration"></a>Clang-Tidy-Konfiguration

Sie können die Prüfungen konfigurieren, die clang-tidy in Visual Studio ausgeführt werden, über die Option **Clang-Tidy Checks.** Diese Eingabe wird für das **Argument --checks** des Werkzeugs bereitgestellt. Jede weitere Konfiguration kann *`.clang-tidy`* in benutzerdefinierten Dateien enthalten sein. Weitere Informationen finden Sie in der [Clang-Tidy-Dokumentation auf LLVM.org](https://clang.llvm.org/extra/clang-tidy/).

## <a name="see-also"></a>Siehe auch

- [Clang/LLVM-Unterstützung für MSBuild-Projekte](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Clang/LLVM-Unterstützung für CMake-Projekte](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)

::: moniker-end
