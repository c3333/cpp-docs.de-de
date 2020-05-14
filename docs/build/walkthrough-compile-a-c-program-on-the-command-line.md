---
title: 'Exemplarische Vorgehensweise: Kompilieren eines C-Programms in der Befehlszeile'
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: d807fa75b32b515c2222fec9ea9d070266303e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335259"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Exemplarische Vorgehensweise: Kompilieren eines C-Programms in der Befehlszeile

Visual C++ enthält einen C-Compiler, mit dem Sie alles von grundlegenden Konsolenprogrammen bis hin zu Windows-Desktopanwendungen, mobilen Apps und mehr erstellen können.

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein grundlegendes C++-Programm im „Hello World!“-Stil mithilfe eines Text-Editors erstellen und dieses dann über die Befehlszeile kompilieren. Wenn Sie lieber über die Befehlszeile in C++ arbeiten, finden Sie weitere Informationen unter [Walkthrough: Compiling a Native C++ Program on the Command Line (Exemplarische Vorgehensweise: Kompilieren eines nativen C++-Programms in der Befehlszeile)](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Wenn Sie die Visual Studio-IDE testen möchten, anstatt die Befehlszeile zu verwenden, finden Sie weitere Informationen unter [Exemplarische Vorgehensweise: Arbeiten mit Projekten und Projektmappen ( C++ )](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) oder [Verwenden der Visual Studio-IDE für die C++-Desktopentwicklung](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Voraussetzungen

Für die Durchführung dieser exemplarischen Vorgehensweise müssen entweder Visual Studio und die optionalen Visual C++-Komponenten oder die Buildtools für Visual Studio installiert sein.

Visual Studio ist eine leistungsstarke integrierte Entwicklungsumgebung, die einen voll funktionsfähigen Editor, Ressourcen-Manager, Debugger und Compiler für viele Sprachen und Plattformen unterstützt. Weitere Informationen zu diesen Features und zum Herunterladen und Installieren von Visual Studio, einschließlich der kostenlosen Visual Studio Community-Edition, finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio).

Die Buildtools für Visual Studio installieren nur das Befehlszeilen-Toolset, die Compiler, Tools und Bibliotheken, die Sie benötigen, um C- und C++-Programme zu erstellen. Sie eignen sich ideal für Buildlabs oder Übungen im Schulungskontext und werden schnell installiert. Laden Sie von der Seite für [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) die Buildtools für Visual Studio herunter, um nur das Befehlszeilen-Toolset zu installieren, und führen Sie das Installationsprogramm aus. Wählen Sie im Visual Studio-Installationsprogramm die Workload **C++-Buildtools** und anschließend **Installieren** aus.

Überprüfen Sie, ob die Tools installiert sind und Sie über die Befehlszeile darauf zugreifen können, bevor Sie ein C- oder C++-Programm über die Befehlszeile erstellen. Visual C++ hat komplexe Anforderungen an die Befehlszeilenumgebung hinsichtlich der Suche nach den verwendeten Tools, Headern und Bibliotheken. **Sie können Visual C++ nicht in einem einfachen Eingabeaufforderungsfenster** ohne bestimmte Vorbereitungen verwenden. Sie benötigen ein *Developer-Eingabeaufforderung*-Fenster, das ein reguläres Eingabeaufforderungsfenster ist, in dem alle erforderlichen Umgebungsvariablen festgelegt sind. Glücklicherweise installiert Visual C++ Verknüpfungen zum Starten einer Developer-Eingabeaufforderung, in der die Umgebung für Befehlszeilenbuilds eingerichtet ist. Leider unterscheiden sich die Namen der Verknüpfungen für die Developer-Eingabeaufforderung und deren Position in nahezu jeder Version von Visual C++ und unterschiedlichen Versionen von Windows. Ihre erste Aufgabe bei der exemplarischen Vorgehensweise besteht darin, die richtige Verknüpfung zu finden.

> [!NOTE]
> Eine Verknüpfung für die Developer-Eingabeaufforderung legt die richtigen Pfade für den Compiler und die Tools sowie für alle erforderlichen Header und Bibliotheken automatisch fest. Einige dieser Werte unterscheiden sich für jede Buildkonfiguration. Sie müssen diese Umgebungswerte selbst festlegen, wenn Sie keine der Verknüpfungen verwenden. Weitere Informationen finden Sie unter [Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds](setting-the-path-and-environment-variables-for-command-line-builds.md). Da die Buildumgebung komplex ist, wird dringend empfohlen, eine Verknüpfung zu einer Developer-Eingabeaufforderung zu verwenden, anstatt ihre eigenen Verknüpfung zu erstellen.

Die Anweisungen variieren, je nachdem, welche Version von Visual Studio Sie verwenden. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version**. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Öffnen einer Developer-Eingabeaufforderung in Visual Studio 2019

Wenn Sie Visual Studio 2019 unter Windows 10 installiert haben, öffnen Sie das Startmenü, scrollen Sie dann nach unten und öffnen Sie den Ordner **Visual Studio 2019** (nicht die Visual Studio 2019-App). Klicken Sie auf **Developer Command Prompt for VS 2019** (Developer-Eingabeaufforderung für VS 2019), um das Eingabeaufforderungsfenster zu öffnen.

Wenn Sie eine andere Version von Windows verwenden, suchen Sie im Startmenü oder auf der Startseite nach einem Ordner mit Visual Studio-Tools, der eine Verknüpfung für eine Developer-Eingabeaufforderung enthält. Sie können auch die Windows-Suchfunktion verwenden, um nach „Developer-Eingabeaufforderung“ zu suchen und die Version anzuklicken, die mit der installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabeaufforderungsfenster zu öffnen.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Öffnen einer Developer-Eingabeaufforderung in Visual Studio 2017

Wenn Sie Visual Studio 2017 unter Windows 10 installiert haben, öffnen Sie das Startmenü, scrollen Sie dann nach unten und öffnen Sie den Ordner **Visual Studio 2017** (nicht die Visual Studio 2017-App). Klicken Sie auf **Developer Command Prompt for VS 2017** (Developer-Eingabeaufforderung für VS 2017), um das Eingabeaufforderungsfenster zu öffnen.

Wenn Sie eine andere Version von Windows verwenden, suchen Sie im Startmenü oder auf der Startseite nach einem Ordner mit Visual Studio-Tools, der eine Verknüpfung für eine Developer-Eingabeaufforderung enthält. Sie können auch die Windows-Suchfunktion verwenden, um nach „Developer-Eingabeaufforderung“ zu suchen und die Version anzuklicken, die mit der installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabeaufforderungsfenster zu öffnen.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Öffnen einer Developer-Eingabeaufforderung in Visual Studio 2015

Wenn Sie Microsoft Visual C++ Build Tools 2015 unter Windows 10 installiert haben, öffnen Sie das Menü **Start**, scrollen dann nach unten und öffnen den Ordner **Visual C++ Build Tools**. Klicken Sie auf **Visual C++ 2015 x86 Native Tools Command Prompt** (Visual C++ 2015 x86 Native Tools-Eingabeaufforderung), um das Eingabeaufforderungsfenster zu öffnen.

Wenn Sie eine andere Version von Windows verwenden, suchen Sie im Startmenü oder auf der Startseite nach einem Ordner mit Visual Studio-Tools, der eine Verknüpfung für eine Developer-Eingabeaufforderung enthält. Sie können auch die Windows-Suchfunktion verwenden, um nach „Developer-Eingabeaufforderung“ zu suchen und die Version anzuklicken, die mit der installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabeaufforderungsfenster zu öffnen.

::: moniker-end

Überprüfen Sie als Nächstes, ob die Visual C++-Developer-Eingabeaufforderung ordnungsgemäß eingerichtet ist. Geben Sie im Eingabeaufforderungsfenster `cl` ein, und überprüfen Sie, ob die Ausgabe in etwa wie folgt aussieht:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Abhängig von der Visual C++-Version und den installierten Updates kann es Unterschiede im aktuellen Verzeichnis oder in den Versionsnummern geben. Wenn die oben genannte der angezeigten Ausgabe ähnelt, können Sie C- oder C++-Programme über die Befehlszeile erstellen.

> [!NOTE]
> Wenn eine Fehlermeldung wie z. B. "'cl' is not recognized as an internal or external command, operable program or batch file" („cl“ wurde nicht als interner oder externer Befehl, ausführbares Programm oder Batchdatei erkannt.), Fehler C1034 oder Fehler LNK1104 beim Ausführen des **cl**-Befehls ausgegeben wird, verwenden Sie entweder keine Developer-Eingabeaufforderung, oder es ist ein Fehler bei der Installation von Visual C++ aufgetreten. Sie müssen das Problem beheben, bevor Sie fortfahren können.

Wenn Sie die Verknüpfung für die Developer-Eingabeaufforderungen nicht finden, oder wenn Sie eine Fehlermeldung erhalten, wenn Sie `cl` eingeben, liegt ein Problem im Zusammenhang mit der Installation von Visual C++ vor. Wenn Sie Visual Studio 2017 oder höher verwenden, können Sie versuchen, die **Desktopentwicklung mit C++** -Workload im Visual Studio-Installationsprogramm neu zu installieren. Weitere Informationen finden Sie unter [Installieren der C++-Unterstützung in Visual Studio](vscpp-step-0-installation.md). Oder installieren Sie die Buildtools auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) erneut. Fahren Sie nicht mit dem nächsten Abschnitt fort, bis dies funktioniert. Weitere Informationen zur Installation und Problembehandlung von Visual Studio finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> Abhängig von der Version von Windows auf dem Computer und der Systemsicherheitskonfiguration müssen Sie ggf. mit der rechten Maustaste das Kontextmenü für die Verknüpfung der Developer-Eingabeaufforderung öffnen und dann auf **Als Administrator ausführen** klicken, um das Programm gemäß den Schritten dieser exemplarischen Vorgehensweise zu erstellen und auszuführen.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Erstellen einer C-Quelldatei und Kompilieren dieser über die Befehlszeile

1. Geben Sie im Fenster der Developer-Eingabeaufforderung `cd c:\` ein, um das aktuelle Arbeitsverzeichnis in das Stammverzeichnis des Laufwerks C: zu ändern. Als Nächstes geben Sie `md c:\simple` ein, um ein Verzeichnis zu erstellen. Geben Sie anschließend `cd c:\simple` ein, um zu diesem Verzeichnis zu wechseln. In diesem Verzeichnis werden die Quelldatei und das kompilierte Programm gespeichert.

1. Geben Sie in die Developer-Eingabeaufforderung `notepad simple.c` ein. Wählen Sie im angezeigten Dialogfeld mit der Editor-Warnung **Ja**, um eine neue Datei „simple.c“ in Ihrem Arbeitsverzeichnis zu erstellen.

1. Geben Sie im Editor die folgenden Codezeilen ein:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Wählen Sie in der Editor-Menüleiste **Datei** > **Speichern**, um „simple.c“ in Ihrem Arbeitsverzeichnis zu speichern.

1. Wechseln Sie zurück zum Developer-Eingabeaufforderungsfenster. Geben Sie `dir` in die Eingabeaufforderung ein, um den Inhalt des Verzeichnisses „c:\simple“ aufzulisten. Die Quelldatei „simple.c“ sollte in der Verzeichnisauflistung angezeigt werden, die in etwa wie folgt aussieht:

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   Die Datumsangaben und andere Details werden sich auf Ihrem Computer von den hier gezeigten unterscheiden. Wenn die Quellcodedatei „simple.c“ nicht angezeigt wird, vergewissern Sie sich, dass Sie in das von Ihnen erstellte Verzeichnis „c:\simple“ gewechselt sind. Stellen Sie zudem im Editor sicher, dass Sie die Quelldatei in diesem Verzeichnis gespeichert haben. Vergewissern Sie sich außerdem, dass Sie den Quellcode mit der Dateinamenerweiterung „.c“ und nicht mit der „.txt“-Erweiterung gespeichert haben.

1. Geben Sie in die Developer-Eingabeaufforderung `cl simple.c` ein, um das Programm zu kompilieren.

   Der Name des ausführbaren Programms „simple.exe“ wird in den vom Compiler erzeugten Ausgabeinformationen angezeigt:

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > Wenn eine Fehlermeldung wie z. B. "'cl' is not recognized as an internal or external command, operable program or batch file" („cl“ wurde nicht als interner oder externer Befehl, ausführbares Programm oder Batchdatei erkannt.), Fehler C1034 oder Fehler LNK1104 ausgegeben wird, ist die Developer-Eingabeaufforderung nicht ordnungsgemäß eingerichtet. Weitere Informationen zum Beheben dieses Problems finden Sie im Abschnitt **Öffnen einer Developer-Eingabeaufforderung**.

   > [!NOTE]
   > Überprüfen Sie den Quellcode, um Fehler zu beheben, ihn zu speichern und den Compiler dann noch mal auszuführen, wenn Sie einen anderen Compiler- oder Linkerfehler oder eine andere Warnung erhalten. Verwenden Sie das Suchfeld oben auf dieser Seite, um nach der Fehlernummer zu suchen und Informationen zu bestimmten Fehlern zu erhalten.

1. Geben Sie `simple` in der Eingabeaufforderung ein, um das Programm auszuführen.

   Das Programm zeigt folgenden Text an und wird anschließend beendet:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Herzlichen Glückwunsch, Sie haben mithilfe der Befehlszeile ein C-Programm kompiliert und ausgeführt.

## <a name="next-steps"></a>Nächste Schritte

Dieses „Hello World!“-Beispiel ist die einfachste Form eines C-Programms. Programme der realen Welt verfügen über Headerdateien und weitere Quelldateien, sind in Bibliotheken eingebunden und leisten nützliche Arbeit.

Sie können die Schritte in dieser exemplarischen Vorgehensweise verwenden, um Ihren eigenen C-Code zu erstellen, anstatt den gezeigten Beispielcode einzugeben. Außerdem können Sie viele C-Codebeispielprogramme erstellen, die Sie auch an anderer Stelle finden. Wenn Sie ein Programm mit zusätzlichen Quellcodedateien kompilieren möchten, geben Sie alle in der Befehlszeile ein. Beispiel:

`cl file1.c file2.c file3.c`

Der Compiler gibt ein Programm namens „file1.exe“ aus. Fügen Sie die Linkeroption [/out](reference/out-output-file-name.md) hinzu, um den Namen in „program1.exe“ zu ändern:

`cl file1.c file2.c file3.c /link /out:program1.exe`

Es empfiehlt sich, mithilfe der Warnstufenoptionen [/W3](reference/compiler-option-warning-level.md) oder [/W4](reference/compiler-option-warning-level.md) zu kompilieren, um automatisch weitere Programmierfehler zu erfassen:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Der Compiler, „cl.exe“, bietet viele weitere Optionen, die Sie zum Erstellen, Optimieren, Debuggen und Analysieren Ihres Codes nutzen können. Geben Sie `cl /?` in die Developer-Eingabeaufforderung ein, um eine kurze Liste anzuzeigen. Sie können die Kompilierung und Verknüpfung auch separat vornehmen und Linkeroptionen in komplexeren Buildszenarios anwenden. Weitere Informationen zu den Compiler- und Linkeroptionen und deren Verwendung finden Sie unter [Referenz zur C-/C++-Erstellung](reference/c-cpp-building-reference.md).

Sie können NMAKE und Makefiles oder MSBuild und Projektdateien zum Konfigurieren und Erstellen komplexerer Projekte in der Befehlszeile verwenden. Weitere Informationen zur Verwendung dieser Tools finden Sie unter [NMAKE-Referenz](reference/nmake-reference.md) und [MSBuild](msbuild-visual-cpp.md).

Die C- und C++-Sprachen sind ähnlich, aber nicht identisch. Der Microsoft C/C++-Compiler (MSVC) verwendet eine einfache Regel, um zu bestimmen, welche Sprache zum Kompilieren des Codes verwendet werden soll. Standardmäßig behandelt der MSVC-Compiler alle auf „.c“ endenden Dateien als C-Quellcode und alle auf „.cpp“ endenden Dateien als C++-Quellcode. Wenn Sie erzwingen möchten, dass vom Compiler alle Dateien unabhängig von der Dateierweiterung als C behandelt werden, verwenden Sie die Compileroption [/Tc](reference/tc-tp-tc-tp-specify-source-file-type.md).

MSVC ist mit dem ISO C99-Standard konform, jedoch nicht streng konform. In den meisten Fällen wird der portierbare C-Code wie erwartet kompiliert und ausgeführt. Die meisten Änderungen in ISO C11 werden von Visual C++ nicht unterstützt. Bestimmte Bibliotheksfunktionen und POSIX-Funktionsnamen werden von MSVC als veraltet markiert. Die Funktionen werden unterstützt, aber die bevorzugten Namen wurden geändert. Weitere Informationen finden Sie unter [Sicherheitsfunktionen in der CRT](../c-runtime-library/security-features-in-the-crt.md) und [Compilerwarnung C4996 (Stufe 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Erstellen eines Standard C++-Programms (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C-Sprachreferenz](../c-language/c-language-reference.md)<br/>
[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br/>
[Kompatibilität](../c-runtime-library/compatibility.md)
