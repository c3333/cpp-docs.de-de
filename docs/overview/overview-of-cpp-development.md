---
title: Übersicht über die C++-Entwicklung in Visual Studio
description: Die Visual Studio-IDE unterstützt C++-Entwicklung unter Windows, Linux, Android und iOS mit einem Code-Editor, Debugger, Testframeworks, statischen Analysetools und weiteren Programmiertools.
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 4e04e189b44fe61759a9422139d856ab8a09f201
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "77415712"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Übersicht über die C++-Entwicklung in Visual Studio

Als Teil der integrierten Visual Studio-Entwicklungsumgebung (IDE) verwendet Microsoft C++ (MSVC) viele Fenster und Tools, die auch in zahlreichen anderen Sprachen verwendet werden. Viele davon, z.B. der **Projektmappen-Explorer**, der Code-Editor und der Debugger, sind unter [Visual Studio-IDE](/visualstudio/get-started/visual-studio-ide) dokumentiert. Ein gemeinsam verwendetes Tool oder Fenster verfügt in C++ häufig über etwas andere Funktionen als für andere Sprachen. Einige Fenster oder Tools sind nur in den Editionen Visual Studio Professional oder Visual Studio Enterprise verfügbar.

Zusätzlich zu den gemeinsam verwendeten Tools in der integrierten Visual Studio-Entwicklungsumgebung verfügt MSVC über mehrere Tools, die speziell auf die Entwicklung von nativem Code ausgelegt sind. Diese Tools sind ebenfalls in diesem Artikel aufgeführt. Eine Liste der Tools, die in jeder Edition von Visual Studio verfügbar sind, finden Sie unter [Visual C++ Tools and Features in Visual Studio Editions (Tools und Features von C++ in den Visual Studio-Editionen)](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Erstellen von Projekten

Ein *Projekt* ist im Grunde eine Reihe von Quellcodedateien und Ressourcen wie Bilder oder Datendateien, aus denen ein ausführbares Programm oder eine ausführbare Bibliothek erstellt wird.

Visual Studio unterstützt alle Projektsysteme und benutzerdefinierten Buildtools, die Sie verwenden möchten, und bietet vollständige Unterstützung für IntelliSense, das Durchsuchen und das Debuggen:

- Bei **MSBuild** handelt es sich um das native Projektsystem für Visual Studio. Wenn Sie im Hauptmenü **Datei** > **Neu** > **Projekt** auswählen, sehen Sie viele Arten von MSBuild-*Projektvorlagen*, die Sie beim schnellen Einstieg in die Entwicklung verschiedener Arten von C++-Anwendungen unterstützen.

   ::: moniker range="vs-2019"

   ![Neue Projektvorlagen](../build/media/mathclient-project-name-2019.png "Visual Studio 2019, Dialogfeld „Neues Projekt“")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![Projektvorlagen](media/vs2017-new-project.png "Visual Studio 2017, Dialogfeld „Neues Projekt“")

   ::: moniker-end

   Sie sollten diese Vorlagen generell für neue Projekte verwenden, es sei denn, Sie verwenden bestehende CMake-Projekte oder ein anderes Projektsystem. Weitere Informationen finden Sie unter [Creating and managing MSBuild-based projects](../build/creating-and-managing-visual-cpp-projects.md) (Erstellen und Verwalten von MSBuild-basierten Projekten).

- **CMake** ist ein plattformübergreifendes Buildsystem, das in die Visual Studio-IDE integriert ist, wenn Sie die Workload „Desktopentwicklung mit C++“ installieren. Sie können die CMake-Projektvorlage für neue Projekte verwenden oder einfach einen Ordner mit einer CMakeLists.txt-Datei öffnen. Weitere Informationen finden Sie unter [CMake-Projekte in Visual Studio](../build/cmake-projects-in-visual-studio.md).

- Alle anderen C++-Buildsysteme, einschließlich einer losen Dateisammlung, werden über das Feature **Ordner öffnen** unterstützt. Sie erstellen einfache JSON-Dateien, um Ihr Buildprogramm aufzurufen und Debugsitzungen zu konfigurieren. Weitere Informationen finden Sie unter [Open Folder projects for C++ (Verwenden von „Ordner öffnen“ mit Projekten in Visual C++)](../build/open-folder-projects-cpp.md).

## <a name="add-to-source-control"></a>Zur Quellcodeverwaltung hinzufügen

Mithilfe von Quellcodeverwaltung können Sie die Arbeit mehrerer Entwickler koordinieren, im Bearbeitungsprozess stehende Arbeit von Produktionscode trennen und Ihren Quellcode sichern. Visual Studio unterstützt Git und [Team Foundation Version Control \(TFVC\)](/azure/devops/repos/tfvc/) über sein Fenster **Team Explorer**.

::: moniker range="vs-2019"

![Team Explorer](media/vs2019-team-explorer.png "Visual Studio 2017, Team Explorer")

::: moniker-end

::: moniker range="<=vs-2017"

![Team Explorer](media/vs2017-team-explorer.png "Visual Studio 2017, Team Explorer")

::: moniker-end

Weitere Informationen zur Git-Integration mit Repositorys in Azure finden Sie unter [Share your code with Visual Studio 2017 and Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017) (Teilen Ihres Codes mit Visual Studio 2017 und Azure Repos Git). Informationen zur Git-Integration mit GitHub finden Sie unter [GitHub Extension for Visual Studio (GitHub-Erweiterung für Visual Studio)](https://visualstudio.github.com/).

## <a name="obtain-libraries"></a>Abrufen von Bibliotheken

Verwenden Sie zum Beziehen und Installieren von Drittanbieterbibliotheken de[vcpkg](../build/vcpkg.md)-Paket-Manager. Im Katalog sind derzeit mehr als 900 Open Source-Bibliotheken verfügbar.

## <a name="create-user-interfaces-with-designers"></a>Erstellen von Benutzeroberflächen mit Designern

Wenn Ihr Programm über eine Benutzeroberfläche verfügt, können Sie einen Designer verwenden, um sie schnell mit Steuerelementen wie Schaltflächen, Listenfeldern usw. auszustatten. Wenn Sie ein Steuerelement aus dem Toolbox-Fenster ziehen und es auf der Entwurfsoberfläche ablegen, erstellt Visual Studio die erforderlichen Ressourcen und den Code, damit es funktioniert. Anschließend schreiben Sie den Code, um das Aussehen und Verhalten anzupassen.

![Designer und Toolbox](media/vs2017-toolbox-designer.png "Visual Studio 2017, Toolbox und Designer")

Weitere Informationen zum Entwerfen einer Benutzeroberfläche für eine UWP-App finden Sie unter [Design und Benutzeroberfläche](https://developer.microsoft.com/windows/design).

Weitere Informationen zum Erstellen einer Benutzeroberfläche für eine MFC-Anwendung finden Sie unter [MFC Desktop Applications (MFC-Desktopanwendungen)](../mfc/mfc-desktop-applications.md). Weitere Informationen zu Win32-Windows-Programmen finden Sie unter [Windows Desktop Applications (Windows-Desktopanwendungen)](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Schreiben von Code

Nachdem Sie ein Projekt erstellt haben, werden alle Projektdateien im Fenster des **Projektmappen-Explorers** angezeigt. (Eine *Projektmappe* ist ein logischer Container für ein oder mehrere verwandte Projekte.) Wenn Sie auf im **Projektmappen-Explorer** auf eine H- oder CPP-Datei klicken, wird die Datei im Code-Editor geöffnet.

![Projektmappen-Explorer und Code-Editor](media/vs2017-solution-explorer-code-editor.png "Visual Studio 2017, Projektmappen-Explorer und Code-Editor")

Der Code-Editor ist ein spezielles Textverarbeitungsprogramm für C++-Quellcode. Er versieht Sprachschlüsselwörter, Methoden- und Variablennamen sowie andere Elemente im Codes mit verschiedenen Farben, sodass der Code besser lesbar und einfacher zu verstehen ist. Darüber hinaus sind Tools für das Umgestalten von Code, Navigieren zwischen verschiedenen Dateien und Verstehen von Codestrukturen enthalten. Weitere Informationen finden Sie unter [Schreiben und Umgestalten von Code](../ide/writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Hinzufügen und Bearbeiten von Ressourcen

Ein Windows-Programm oder eine Windows-DLL enthält in der Regel einige *Ressourcen* wie Dialogfelder, Symbole, Bilder, lokalisierbare Zeichenfolgen, Begrüßungsbildschirme, Datenbankverbindungszeichenfolgen oder sonstige Daten. Visual Studio enthält Tools, mit denen Sie Ressourcen hinzufügen und bearbeiten können. Weitere Informationen finden Sie unter [Arbeiten mit Ressourcendateien](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Erstellen (Kompilieren und Verknüpfen)

Klicken Sie in der Menüleiste auf **Erstellen** > **Projektmappe erstellen**, oder drücken Sie die Tastenkombination **STRG+UMSCHALT+B**, um ein Projekt zu kompilieren und zu verknüpfen. Buildfehler und Warnungen werden in der Fehlerliste gemeldet (**STRG+\\, E**). Das **Ausgabefenster** (**ALT+2**) zeigt Informationen zum Buildprozess an.

![Ausgabefenster und Fehlerliste](media/vs2017-output-error-list.png "Visual Studio 2017, Ausgabefenster und Fehlerliste")

Weitere Informationen zum Konfigurieren von Builds finden Sie unter [Working with Project Properties (Arbeiten mit Projekteigenschaften)](../build/working-with-project-properties.md) und [Projects and build systems (Projekte und Buildsysteme)](../build/projects-and-build-systems-cpp.md).

Sie können auch den Compiler (cl.exe) und viele andere buildbezogene, eigenständige Tools (z.B. NMAKE und LIB) direkt über die Befehlszeile verwenden. Weitere Informationen finden Sie unter [Build C/C++ code on the command line (Erstellen von C- oder C++-Code über die Befehlszeile)](../build/building-on-the-command-line.md) and [C/C++ Building Reference (Referenz zur C/C++-Erstellung)](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Debug

Debuggen Sie durch Drücken von **F5**. Die Ausführung hält bei allen von Ihnen festgelegten Haltepunkten an (indem Sie **F9** drücken). Sie können den Code auch zeilenweise durchlaufen (**F10**), die Werte von Variablen oder Registern anzeigen und in einigen Fällen sogar Änderungen am Code vornehmen und das Debuggen fortsetzen, ohne neu kompilieren zu müssen. Die folgende Abbildung zeigt eine Debugsitzung mit bei einem Haltepunkt angehaltener Ausführung. Die Werte der Datenstrukturelemente sind im Fenster **Überwachen** sichtbar.

![Debugsitzung](media/vs2017-debug-watch.png "Visual Studio 2017, Debugsitzung")

Weitere Informationen finden Sie unter [Debuggen in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Test

Visual Studio enthält das Microsoft-Komponententest-Framework für C++ und Unterstützung für Boost.Test, Google Test und CTest. Führen Sie Ihre Tests im Fenster **Test-Explorer** aus:

![Test-Explorer](media/cpp-test-explorer-passed.png "Visual Studio 2017, Test-Explorer")

Weitere Informationen finden Sie unter [Verifying Code by Using Unit Tests](/visualstudio/test/unit-test-your-code) (Überprüfen von Code mithilfe von Komponententests) und [Write unit tests for C/C++ in Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp) (Schreiben von Komponententests für C/C++ in Visual Studio).

## <a name="analyze"></a>Analysieren

Visual Studio enthält statische Codeanalysetools, die potenzielle Probleme in Ihrem Quellcode erkennen können. Diese Tools beinhalten eine Implementierung der [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)-Regelüberprüfung. Weitere Informationen finden Sie unter [Code analysis for C/C++ overview (Übersicht: Codeanalyse für C/C++)](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Bereitstellen fertiger Anwendungen

Sowohl herkömmliche Desktopanwendungen als auch UWP-Apps können über den Microsoft Store bei Kunden bereitgestellt werden. Die Bereitstellung von CRT wird automatisch im Hintergrund durchgeführt. Weitere Informationen finden Sie unter [Veröffentlichen von Windows-Apps und -Spielen](/windows/uwp/publish/).

Sie können auch einen nativen C++-Desktop auf einem anderen Computer bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von Desktopanwendungen](../windows/deploying-native-desktop-applications-visual-cpp.md).

Weitere Informationen zum Bereitstellen eines C++/CLI-Programms finden Sie im [Deployment Guide for Developers (Bereitstellungshandbuch für Entwickler)](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="next-steps"></a>Nächste Schritte

Informationen zu weiteren Features von Visual Studio finden Sie in den folgenden Artikeln:

> [!div class="nextstepaction"]
> [Informationen zur Verwendung des Code-Editors](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [Erfahren Sie mehr über Projekte und Projektmappen](/visualstudio/get-started/tutorial-projects-solutions)
