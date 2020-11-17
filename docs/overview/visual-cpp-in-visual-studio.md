---
title: C++ in Visual Studio
description: Erfahren Sie, wie Sie den Compiler, den Code-Editor und zugehörige Tools für Microsoft C/C++ in Visual Studio verwenden, um Programme für Windows, Linux, Android und iOS zu entwickeln.
ms.date: 11/05/2020
ms.technology: cpp-ide
helpviewer_keywords:
- Visual C++, home page
ms.openlocfilehash: 32d8f45c1ae0ffeabcfd7b22988f125b138c1f4d
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334155"
---
# <a name="c-in-visual-studio"></a>C++ in Visual Studio

:::moniker range="msvc-160"

> [!NOTE]
> Diese Entwicklerdokumentation gilt für Visual Studio 2019. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version**. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.
>
> Wenn Sie zum Ausführen eines Programms ein weitervertreibbares Microsoft Visual C++ 2019-Paket suchen, wechseln Sie auf der Microsoft Visual Studio-Website zur Seite [Downloads](https://visualstudio.microsoft.com/downloads/). Erweitern Sie unter **Alle Downloads** den Abschnitt **Sonstige Tools und Frameworks**. Wählen Sie Ihre Zielarchitektur aus, und klicken Sie auf die Schaltfläche **Download**.
>
> Wenn Sie das Gewünschte nicht finden, öffnen Sie die Seite [Ältere Downloads](https://visualstudio.microsoft.com/vs/older-downloads/). Erweitern Sie den Abschnitt **Weitervertreibbare Komponenten und Buildtools**. Suchen Sie die weitervertreibbare Version, die Sie herunterladen möchten, wählen Sie Ihre Zielarchitektur aus, und klicken Sie auf die Schaltfläche **Download**.

:::moniker-end

:::moniker range="msvc-150"

> [!NOTE]
> Diese Entwicklerdokumentation gilt für Visual Studio 2017. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version**. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.
>
> Wenn Sie zum Ausführen eines Programms ein weitervertreibbares Paket für Microsoft Visual C++ 2017 oder niedriger suchen, wechseln Sie auf der Microsoft Visual Studio-Website zur Seite [Ältere Downloads](https://visualstudio.microsoft.com/vs/older-downloads/). Erweitern Sie den Abschnitt **Weitervertreibbare Komponenten und Buildtools**. Suchen Sie die weitervertreibbare Version, die Sie herunterladen möchten, wählen Sie Ihre Zielarchitektur aus, und klicken Sie auf die Schaltfläche **Download**.

:::moniker-end

:::moniker range="msvc-140"

> [!NOTE]
> Diese Entwicklerdokumentation gilt für Visual Studio 2015. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version**. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.
>
> Wenn Sie zum Ausführen eines Programms ein weitervertreibbares Paket für Microsoft Visual C++ 2015 oder niedriger suchen, wechseln Sie auf der Microsoft Visual Studio-Website zur Seite [Ältere Downloads](https://visualstudio.microsoft.com/vs/older-downloads/). Erweitern Sie den Abschnitt **Weitervertreibbare Komponenten und Buildtools**. Suchen Sie die weitervertreibbare Version, die Sie herunterladen möchten, wählen Sie Ihre Zielarchitektur aus, und klicken Sie auf die Schaltfläche **Download**.

:::moniker-end

Microsoft Visual C++ (MSVC) bezeichnet die Entwicklungstools und Bibliotheken für C++, C und Assemblysprachen, die als Teil von Visual Studio unter Windows verfügbar sind. Mit diesen Tools und Bibliotheken können Sie Apps für die Universelle Windows Plattform (UWP), Windows-Desktop- und Serveranwendungen und plattformübergreifende Bibliotheken und Apps, die unter Windows, Linux, Android und iOS ausgeführt werden, sowie verwaltete Apps und Bibliotheken erstellen, die .NET Framework verwenden. Sie können MSVC verwenden, um verschiedenste Komponenten zu schreiben: von einfachen Konsolen-Apps bis hin zu höchst anspruchsvollen und komplexen Apps für Windows-Desktop, von Gerätetreibern und Betriebssystemkomponenten bis hin zu plattformübergreifenden Spielen für mobile Geräte, vom kleinen IoT-Gerät bis hin zum Hochleistungscomputing mit mehreren Servern in der Azure-Cloud.

Visual Studio 2015, 2017 und 2019 können parallel installiert sein. Sie können Visual Studio 2019 (Compilertoolset v142) oder Visual Studio 2017 (v141) verwenden, um Programme mit den Toolsets aus Visual Studio 2017 (v141) und Visual Studio 2015 (v140) zu bearbeiten und zu kompilieren.

## <a name="whats-new-and-conformance-history"></a>Verlauf von Neuerungen und Konformität

[Neuerungen bei C++ in Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)\
Erfahren Sie, welche Neuerungen es für Visual Studio gibt.

[Neuerungen bei C++ in Visual Studio 2003 bis 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
Erfahren Sie, welche Neuerungen es in C++ für die einzelnen Visual Studio-Versionen von 2003 bis 2015 gibt.

[Verbesserungen der C++-Konformität in Visual Studio 2015](cpp-conformance-improvements.md)\
Weitere Informationen zu Verbesserungen bei der Übereinstimmung mit C++-Standards in Visual Studio

[Microsoft C++-Sprachkonformitätstabelle](visual-cpp-language-conformance.md)\
Eine Liste der Konformitätsstatus nach Feature im MSVC-C++-Compiler.

[Änderungsverlauf von Microsoft C/C++ von 2003 bis 2015](../porting/visual-cpp-change-history-2003-2015.md)\
Machen Sie sich mit den bedeutenden Änderungen in Vorversionen vertraut.

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>Installieren von Visual Studio und Ausführen eines Upgrades für frühere Versionen

[Installieren der C++-Unterstützung in Visual Studio](../build/vscpp-step-0-installation.md)\
Laden Sie Visual Studio herunter, und installieren Sie das Microsoft C/C++-Toolset.

[Microsoft C++-Leitfaden: Portieren und Upgraden](../porting/visual-cpp-porting-and-upgrading-guide.md)\
Anleitung zum Portieren von Code und Upgraden von Projekten zu Visual Studio 2015 oder höher, um von der größeren Compilerkonformität mit dem C++-Standard sowie den stark verbesserten Kompilierungszeiten und Sicherheitsfeatures wie der Spectre-Entschärfung zu profitieren.

[C++-Tools und -Features in Visual Studio-Editionen](visual-cpp-tools-and-features-in-visual-studio-editions.md)\
Informieren Sie sich über die verschiedenen Visual Studio-Editionen.

[Unterstützte Plattformen](supported-platforms-visual-cpp.md)\
Finden Sie heraus, welche Plattformen vom Microsoft C/C++-Compiler unterstützt werden.

## <a name="learn-c"></a>Einführung in C#

[Willkommen zurück bei C++](../cpp/welcome-back-to-cpp-modern-cpp.md)\
Erfahren Sie mehr über moderne C++-Programmiertechniken, die auf C++11 und höher basieren, und mithilfe derer Sie schnellen und sicheren Code schreiben und viele Probleme der C-Programmierung vermeiden können.

[Standard-C++](https://isocpp.org/)\
Lernen Sie C++ kennen, verschaffen Sie sich einen Überblick über das moderne C++, und greifen Sie auf Links für Bücher, Artikel, Gespräche und Ereignisse zu.

[Kennenlernen von Visual Studio und Erstellen des erstes C++-Projekts](../build/vscpp-step-1-create.md)\
Beginnen Sie mit dem Schreiben von C++-Code in Visual Studio.

[Visual Studio: C++ -Beispiele](visual-cpp-samples.md)\
Informationen zu den von Microsoft bereitgestellten C++-Codebeispielen.

## <a name="c-development-tools"></a>C++-Entwicklungstools

[Übersicht über die C++-Entwicklung in Visual Studio](overview-of-cpp-development.md)\
Informationen zur Verwendung der Visual Studio-IDE zum Erstellen von Projekten, Bearbeiten von Code, Verknüpfen von Bibliotheken, Kompilieren, Debuggen, Erstellen von Komponententests, Ausführen von statischen Analysen, Bereitstellen etc.

[Projekte und Buildsysteme](../build/projects-and-build-systems-cpp.md)\
Erstellen und Konfigurieren von C++-Projekten, CMake-Projekten und anderen Arten von Projekten mit dem MSVC-Compiler und Linkeroptionen in Visual Studio

[Schreiben und Refactoring von C++-Code](../ide/writing-and-refactoring-code-cpp.md)\
Erfahren Sie, wie die Produktivitätsfeatures im C++-Editor zum Umgestalten, Navigieren, Verstehen und Schreiben von Code verwendet werden.

[Debugging native code (Debuggen von nativem Code)](/visualstudio/debugger/debugging-native-code)\
Verwenden des Visual Studio-Debuggers mit C++-Projekten

[Übersicht über die Codeanalyse für C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)\
Verwenden von SAL-Anmerkungen oder der C++ Core Guidelines-Überprüfungen, um statische Analysen durchführen.

[Schreiben von Komponententests für C/C++ in Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp)\
Erstellen von Komponententests mit dem Microsoft-Komponententest-Framework für C++, Google Test-, Boost.Test oder CTest.

## <a name="write-applications-in-c"></a>Schreiben von Anwendungen in C++

[Universelle Windows-Apps (C++)](../cppcx/universal-windows-apps-cpp.md)\
Rufen Sie Anleitungen und Referenzmaterial im Windows Developer Center ab. Weitere Informationen zur Entwicklung von UWP-Apps finden Sie unter [Einführung in die Universelle Windows-Plattform](/windows/uwp/get-started/universal-application-platform-guide) und [Erstellen Ihrer ersten UWP-App mit C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

[Desktopanwendungen (C++)](../windows/desktop-applications-visual-cpp.md)\
Informationen zum Erstellen von traditionellen nativen C++-Desktopanwendungen für Windows.

[.NET-Programmierung mit C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)\
Informationen zum Erstellen von DLLs, die die Interoperabilität zwischen nativen C++- und .NET-Programmen ermöglicht, die in Sprachen wie C# oder Visual Basic geschrieben werden.

[Linux-Programmierung](../linux/index.yml)\
Verwenden Sie die Visual Studio-IDE, um einen Linux-Remotecomputer für die Kompilierung mit GCC zu programmieren und bereitzustellen.

[Erstellen von C/C++-DLLs in Visual Studio](../build/dlls-in-visual-cpp.md)\
Stellen Sie fest, wie Win32, ATL und MFC zum Erstellen von Windows-Desktop DLLs verwendet werden und Informationen zum Kompilieren und Registrieren der DLL bereitstellen.

[Parallele Programmierung](../parallel/parallel-programming-in-visual-cpp.md)\
Erfahren Sie, wie Sie die Parallel Patterns Library, C++ AMP, OpenMP und andere Funktionen in Verbindung mit Multithreading unter Windows verwenden.

[Empfohlene Vorgehensweisen bezüglich der Sicherheit](../security/security-best-practices-for-cpp.md)\
Erfahren Sie, wie Sie Anwendungen vor bösartigem Code und nicht autorisierter Verwendung schützen.

[Cloud- und Webprogrammierung](../cloud/cloud-and-web-programming-in-visual-cpp.md)\
In C++ haben Sie mehrere Optionen, um eine Verbindung mit dem Web und der Cloud herzustellen.

[Datenzugriff](../data/data-access-in-cpp.md)\
Erfahren Sie, wie Verbindungen zu Datenbanken mithilfe von ODBC und OLEDB hergestellt werden.

[Text und Zeichenfolgen](../text/text-and-strings-in-visual-cpp.md)\
Hier erhalten Sie Informationen zum Arbeiten mit verschiedenen Text- und Zeichenfolgenformaten und Codierungen für die lokale und internationale Entwicklung.

## <a name="languages-reference"></a>Sprachreferenz

[C#-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)\
Der Referenzleitfaden zur Microsoft-Implementierung der Programmiersprache C++.

[C/C++-Präprozessorreferenz](../preprocessor/c-cpp-preprocessor-reference.md)\
Allgemeine Referenzen zum gemeinsam genutzten Präprozessor für die Sprachen C und C++.

[C-Programmiersprachenreferenz](../c-language/c-language-reference.md)\
Der Referenzleitfaden zur Microsoft-Implementierung der Programmiersprache C.

[Intrinsische Compilerfunktionen und Assemblysprache](../intrinsics/compiler-intrinsics-and-assembly-language.md)\
Leitfäden zu den intrinsischen Compilerfunktionen, die von den Microsoft C/C++-Compilern auf den einzelnen Plattformen unterstützt oder implementiert werden.

## <a name="c-libraries-in-visual-studio"></a>C++-Bibliotheken in Visual Studio

Die folgenden Abschnitte enthalten Informationen über die verschiedenen C- und C++-Bibliotheken, die in Visual Studio enthalten sind.

[Referenz zur C-Laufzeitbibliothek](../c-runtime-library/c-run-time-library-reference.md)\
Umfasst Alternativen mit erhöhter Sicherheit für Funktionen, die bekanntermaßen Sicherheitsprobleme aufwerfen.

[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)\
Die C++-Standardbibliothek.

[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)\
Unterstützung für COM-Komponenten und Apps.

[Bibliotheken der Microsoft Foundation Class (MFC)](../mfc/mfc-desktop-applications.md)\
Unterstützung zur Erstellung von Desktop-Apps mit herkömmlichen oder Office-Formatbenutzeroberflächen.

[Parallel Patterns Library (PPL)](../parallel/concrt/parallel-patterns-library-ppl.md)\
Asynchrone und parallele Algorithmen, die auf der CPU ausgeführt werden.

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)\
Enorm parallele Algorithmen, die auf der GPU ausgeführt werden.

[Windows Runtime Template Library (WRL)](../cppcx/wrl/windows-runtime-cpp-template-library-wrl.md)\
Apps und Komponenten für UWP (Universelle Windows-Plattform).

[.NET-Programmierung mit C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)\
Programmierung für die Common Language Runtime (CLR).

## <a name="third-party-open-source-c-libraries"></a>Open Source-Bibliotheken für C++ von Drittanbietern

Das plattformübergreifende Befehlszeilentool **vcpkg** vereinfacht das Erkennen und Installieren von mehr als 900 Open Source-Bibliotheken für C++ erheblich. Weitere Informationen finden Sie unter [vcpkg: Ein C++-Paket-Manager für Windows](../build/vcpkg.md).

## <a name="feedback-and-community"></a>Feedback und Community

[Fragen und Antworten zur Microsoft-Dokumentation](/answers/topics/c%2B%2B.html)\
Die Microsoft-Dokumentation enthält durchsuchbare Foren für Fragen und Antworten. Fügen Sie Ihrem Beitrag ein `C++`-Tag hinzu, um bei Problemen mit C++ Hilfe von der Community zu erhalten.

[Melden eines Problems mit dem Microsoft C/C++-Toolset](how-to-report-a-problem-with-the-visual-cpp-toolset.md)\
Erfahren Sie mehr über die Erstellung effektiver Fehlerberichte für das Microsoft C/C++-Toolset (Compiler, Linker und andere Tools) und über die verschiedenen Wege, auf denen Sie den Bericht übermitteln können.

Microsoft [C++-Teamblog](https://devblogs.microsoft.com/cppblog/)\
Hier finden Sie weitere Informationen zu neuen Funktionen sowie aktuelle Informationen von den Entwicklern der C++-Tools in Visual Studio.

[Visual Studio C++-Entwicklercommunity](https://aka.ms/vsfeedback/browsecpp)\
Hier können Sie Hilfe erhalten, Fehler melden und Vorschläge für C++ in Visual Studio unterbreiten.
