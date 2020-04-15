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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335259"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Exemplarische Vorgehensweise: Kompilieren eines C-Programms in der Befehlszeile

Visual C++ enthält einen C-Compiler, mit dem Sie alles erstellen können, von einfachen Konsolenprogrammen bis hin zu vollständigen Windows-Desktopanwendungen, mobilen Apps und mehr.

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie mithilfe eines Texteditors ein einfaches C-Programm im "Hello, World"-Stil erstellen und es dann in der Befehlszeile kompilieren. Wenn Sie lieber in C++ in der Befehlszeile arbeiten möchten, finden Sie weitere Informationen unter [Walkthrough: Kompilieren eines nativen C++-Programms in der Befehlszeile](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Wenn Sie die Visual Studio-IDE anstelle der Befehlszeile ausprobieren möchten, finden Sie weitere Informationen unter [Exemplarische Vorgehensweise: Arbeiten mit Projekten und Lösungen (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) oder [Verwenden der Visual Studio-IDE für C++ Desktop development](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Voraussetzungen

Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie entweder Visual Studio und die optionalen Visual C++-Komponenten oder die Buildtools für Visual Studio installiert haben.

Visual Studio ist eine leistungsstarke integrierte Entwicklungsumgebung, die einen voll funktionsfähigen Editor, Ressourcen-Manager, Debugger und Compiler für viele Sprachen und Plattformen unterstützt. Informationen zu diesen Features und zum Herunterladen und Installieren von Visual Studio, einschließlich der kostenlosen Visual Studio Community-Edition, finden Sie unter Installieren von [Visual Studio](/visualstudio/install/install-visual-studio).

Die Buildtools für Visual Studio-Versionen von Visual Studio installiert nur das Befehlszeilentoolset, die Compiler, Tools und Bibliotheken, die Sie zum Erstellen von C- und C++-Programmen benötigen. Es ist perfekt für den Aufbau von Labors oder Klassenzimmerübungen und wird relativ schnell installiert. Um nur das Befehlszeilentoolset zu installieren, laden Sie Build Tools for Visual Studio von der [Visual Studio-Downloadseite herunter,](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) und führen Sie das Installationsprogramm aus. Wählen Sie im Visual Studio-Installationsprogramm die **C++-Buildtools-Workload** aus, und wählen Sie **Installieren**aus.

Bevor Sie ein C- oder C++-Programm in der Befehlszeile erstellen können, müssen Sie überprüfen, ob die Tools installiert sind und über die Befehlszeile darauf zugreifen können. Visual C++ hat komplexe Anforderungen an die Befehlszeilenumgebung, um die verwendeten Tools, Header und Bibliotheken zu finden. **Sie können Visual C++ nicht ohne Vorbereitung in einem einfachen Eingabeaufforderungsfenster verwenden.** Sie benötigen ein *Eingabeaufforderungsfenster für Entwickler,* bei dem es sich um ein reguläres Eingabeaufforderungsfenster handelt, in dem alle erforderlichen Umgebungsvariablen festgelegt sind. Glücklicherweise installiert Visual C++ Verknüpfungen, damit Sie Entwicklerbefehlsanweisungen starten können, auf denen die Umgebung für Befehlszeilenbuilds eingerichtet ist. Leider unterscheiden sich die Namen der Eingabeaufforderungsverknüpfungen für Entwickler und deren Standort in fast jeder Version von Visual C++ und in verschiedenen Windows-Versionen. Ihre erste exemplarische Aufgabe besteht darin, die richtige Verknüpfung zu finden.

> [!NOTE]
> Eine Eingabeaufforderungsverknüpfung für Entwickler legt automatisch die richtigen Pfade für den Compiler und die Tools sowie für alle erforderlichen Header und Bibliotheken fest. Einige dieser Werte unterscheiden sich für jede Buildkonfiguration. Sie müssen diese Umgebungswerte selbst festlegen, wenn Sie keine der Verknüpfungen verwenden. Weitere Informationen finden Sie unter [Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds](setting-the-path-and-environment-variables-for-command-line-builds.md). Da die Buildumgebung komplex ist, wird dringend empfohlen, eine Eingabeaufforderungsverknüpfung für Entwickler zu verwenden, anstatt eine eigene zu erstellen.

Diese Anweisungen hängen davon ab, welche Version von Visual Studio Sie verwenden. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Öffnen einer Entwicklereingabeaufforderung in Visual Studio 2019

Wenn Sie Visual Studio 2019 unter Windows 10 installiert haben, öffnen Sie das Startmenü, und scrollen Sie dann nach unten, und öffnen Sie den Ordner **Visual Studio 2019** (nicht die Visual Studio 2019-App). Wählen Sie **Developer Command Prompt für VS 2019** aus, um das Eingabeaufforderungsfenster zu öffnen.

Wenn Sie eine andere Windows-Version verwenden, suchen Sie im Startmenü oder in der Startseite nach einem Visual Studio-Tools-Ordner, der eine Eingabeaufforderungsverknüpfung für Entwickler enthält. Sie können auch die Windows-Suchfunktion verwenden, um nach "Developer-Eingabeaufforderung" zu suchen und eine auszuwählen, die mit ihrer installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabeaufforderungsfenster zu öffnen.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Öffnen einer Entwicklereingabeaufforderung in Visual Studio 2017

Wenn Sie Visual Studio 2017 unter Windows 10 installiert haben, öffnen Sie das Startmenü, und scrollen Sie dann nach unten, und öffnen Sie den Ordner **Visual Studio 2017** (nicht die Visual Studio 2017-App). Wählen Sie **Developer Command Prompt für VS 2017** aus, um das Eingabeaufforderungsfenster zu öffnen.

Wenn Sie eine andere Windows-Version ausführen, suchen Sie im Startmenü oder auf der Startseite nach einem Visual Studio-Tools-Ordner, der eine Eingabeaufforderungsverknüpfung für Entwickler enthält. Sie können auch die Windows-Suchfunktion verwenden, um nach "Developer-Eingabeaufforderung" zu suchen und eine auszuwählen, die mit ihrer installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabeaufforderungsfenster zu öffnen.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Öffnen einer Entwicklereingabeaufforderung in Visual Studio 2015

Wenn Sie Microsoft Visual C++ Build Tools 2015 unter Windows 10 installiert haben, öffnen Sie das **Startmenü,** und scrollen Sie dann nach unten, und öffnen Sie den Ordner **Visual C++ Build Tools.** Wählen Sie **Visual C++ 2015 x86 Native Tools Command Prompt,** um das Eingabeaufforderungsfenster zu öffnen.

Wenn Sie eine andere Windows-Version ausführen, suchen Sie im Startmenü oder auf der Startseite nach einem Visual Studio-Tools-Ordner, der eine Eingabeaufforderungsverknüpfung für Entwickler enthält. Sie können auch die Windows-Suchfunktion verwenden, um nach "Developer-Eingabeaufforderung" zu suchen und eine auszuwählen, die mit ihrer installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabeaufforderungsfenster zu öffnen.

::: moniker-end

Überprüfen Sie als Nächstes, ob die Befehlsaufforderung für die Visual C++-Entwicklereingabe ordnungsgemäß eingerichtet ist. Geben Sie im Eingabeaufforderungsfenster ein, `cl` und überprüfen Sie, ob die Ausgabe etwa wie folgt aussieht:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Je nach Version von Visual C++ und installierten Updates kann es Unterschiede in den aktuellen Verzeichnis- oder Versionsnummern geben. Wenn die obige Ausgabe dem angezeigt wird, können Sie C- oder C++-Programme in der Befehlszeile erstellen.

> [!NOTE]
> Wenn beim Ausführen des **Befehls "cl'** nicht als interner oder externer Befehl, bedienbares Programm oder Batchdatei, Fehler C1034 oder Fehler LNK1104 beim Ausführen des Befehls cl erkannt wird, verwenden Sie entweder keine Entwicklereingabeaufforderung, oder es stimmt etwas mit der Installation von Visual C++ nicht. Sie müssen dieses Problem beheben, bevor Sie fortfahren können.

Wenn Sie die Eingabeaufforderungsverknüpfung für entwickler nicht finden können oder `cl`wenn beim Eingeben eine Fehlermeldung angezeigt wird, liegt möglicherweise bei der Visual C++-Installation ein Problem vor. Wenn Sie Visual Studio 2017 oder höher verwenden, installieren Sie die **Desktopentwicklung mit C++-Workload** im Visual Studio-Installationsprogramm neu. Weitere Informationen finden Sie unter Installieren der [C++-Unterstützung in Visual Studio](vscpp-step-0-installation.md). Oder installieren Sie die Buildtools auf der [Visual Studio-Downloadseite](https://visualstudio.microsoft.com/downloads/) neu. Fahren Sie nicht mit dem nächsten Abschnitt fort, bis dies funktioniert. Weitere Informationen zum Installieren und Beheben von Visual Studio finden Sie unter Installieren von [Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> Abhängig von der Version von Windows auf dem Computer und der Systemsicherheitskonfiguration müssen Sie möglicherweise mit der rechten Maustaste klicken, um das Kontextmenü für die Eingabeaufforderungsverknüpfung für Entwickler zu öffnen, und dann ausführen **als Administrator** auswählen, um das Programm, das Sie erstellen, erfolgreich zu erstellen und auszuführen, indem Sie diese exemplarische Vorgehensweise befolgen.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Erstellen einer C-Quelldatei und Kompilieren in der Befehlszeile

1. Geben Sie `cd c:\` im Eingabeaufforderungsfenster des Entwicklerbefehls ein, um das aktuelle Arbeitsverzeichnis in den Stamm Ihres Laufwerks C: zu ändern. Geben Sie `md c:\simple` als Nächstes ein, `cd c:\simple` um ein Verzeichnis zu erstellen, und geben Sie dann ein, um in dieses Verzeichnis zu wechseln. Dieses Verzeichnis enthält Ihre Quelldatei und das kompilierte Programm.

1. Geben `notepad simple.c` Sie die Eingabeaufforderung für den Entwickler ein. Wählen Sie im Benachrichtigungsdialogfeld "Notepad"- Und -Warnung die Option **Ja** aus, um eine neue simple.c-Datei in Ihrem Arbeitsverzeichnis zu erstellen.

1. Geben Sie in Notepad die folgenden Codezeilen ein:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Wählen Sie in der Notizblock-Menüleiste > **Dateispeichern** aus, um simple.c in Ihrem Arbeitsverzeichnis zu speichern. **File**

1. Wechseln Sie zurück zum Eingabeaufforderungsfenster für Entwickler. Geben `dir` Sie an der Eingabeaufforderung ein, um den Inhalt des Verzeichnisses c:-simple aufzulisten. Sie sollten die Quelldatei simple.c in der Verzeichnisliste sehen, die etwa wie folgt aussieht:

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

   Die Daten und andere Details unterscheiden sich auf Ihrem Computer. Wenn Die Quellcodedatei simple.c nicht angezeigt wird, stellen Sie sicher, dass Sie in das von Ihnen erstellte Verzeichnis c:-simple geändert haben, und stellen Sie in Notepad sicher, dass Sie die Quelldatei in diesem Verzeichnis gespeichert haben. Stellen Sie außerdem sicher, dass Sie den Quellcode mit einer .c Dateinamenerweiterung und nicht mit einer .txt-Erweiterung gespeichert haben.

1. Um Ihr Programm `cl simple.c` zu kompilieren, geben Sie die Eingabeaufforderung für den Entwickler ein.

   Sie können den ausführbaren Programmnamen simple.exe in den Zeilen der Ausgabeinformationen sehen, die der Compiler anzeigt:

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
   > Wenn sie eine Fehlermeldung wie "'cl' wird nicht als interner oder externer Befehl, bedienbares Programm oder Batchdatei erkannt", Fehler C1034, oder Fehler LNK1104, wird die Entwicklereingabeaufforderung nicht ordnungsgemäß eingerichtet. Informationen zum Beheben dieses Problems finden Sie im Abschnitt **"Öffnen eines Entwicklerbefehls".**

   > [!NOTE]
   > Wenn Sie einen anderen Compiler- oder Linkerfehler oder eine andere Warnung erhalten, überprüfen Sie den Quellcode, um Fehler zu korrigieren, speichern Sie ihn, und führen Sie den Compiler erneut aus. Informationen zu bestimmten Fehlern finden Sie im Suchfeld oben auf dieser Seite, um nach der Fehlernummer zu suchen.

1. Um Ihr Programm `simple` auszuführen, geben Sie die Eingabeaufforderung ein.

   Das Programm zeigt folgenden Text an und wird anschließend beendet:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Herzlichen Glückwunsch, Sie haben ein C-Programm über die Befehlszeile kompiliert und ausgeführt.

## <a name="next-steps"></a>Nächste Schritte

Dieses "Hello, World"-Beispiel ist ungefähr so einfach, wie ein C-Programm bekommen kann. Reale Programme haben Header-Dateien und mehr Quelldateien, Verknüpfen in Bibliotheken, und tun nützliche Arbeit.

Sie können die Schritte in dieser exemplarischen Vorgehensweise verwenden, um Ihren eigenen C-Code zu erstellen, anstatt den angezeigten Beispielcode einzugeben. Sie können auch viele C-Code-Beispielprogramme erstellen, die Sie an anderer Stelle finden. Um ein Programm mit zusätzlichen Quellcodedateien zu kompilieren, geben Sie sie alle in der Befehlszeile ein, z. B.:

`cl file1.c file2.c file3.c`

Der Compiler gibt ein Programm namens file1.exe aus. Um den Namen in program1.exe [/out](reference/out-output-file-name.md) zu ändern, fügen Sie eine /out-Linker-Option hinzu:

`cl file1.c file2.c file3.c /link /out:program1.exe`

Und um weitere Programmierfehler automatisch zu erfassen, empfehlen wir Ihnen, entweder die Warnungsstufe [/W3](reference/compiler-option-warning-level.md) oder [/W4](reference/compiler-option-warning-level.md) zu verwenden:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Der Compiler, cl.exe, verfügt über viele weitere Optionen, die Sie zum Erstellen, Optimieren, Debuggen und Analysieren des Codes anwenden können. Geben Sie eine `cl /?` Schnellliste an der Eingabeaufforderung für den Entwickler ein. Sie können auch separat kompilieren und verknüpfen und Linkeroptionen in komplexeren Buildszenarien anwenden. Weitere Informationen zu Compiler- und Linkeroptionen und -verwendung finden Sie unter [C/C++-Baureferenz](reference/c-cpp-building-reference.md).

Sie können NMAKE- und makefiles- oder MSBuild- und Projektdateien verwenden, um komplexere Projekte in der Befehlszeile zu konfigurieren und zu erstellen. Weitere Informationen zur Verwendung dieser Tools finden Sie unter [NMAKE Reference](reference/nmake-reference.md) und [MSBuild](msbuild-visual-cpp.md).

Die C- und C++-Sprachen sind ähnlich, aber nicht identisch. Der Microsoft C/C++-Compiler (MSVC) verwendet eine einfache Regel, um zu bestimmen, welche Sprache beim Kompilieren des Codes verwendet werden soll. Standardmäßig behandelt der MSVC-Compiler alle Dateien, die in .c enden, als C-Quellcode und alle Dateien, die in .cpp enden, als C++-Quellcode. Um den Compiler zu zwingen, alle Dateien als C nicht abhängig von der Dateinamenerweiterung zu behandeln, verwenden Sie die Compileroption [/Tc.](reference/tc-tp-tc-tp-specify-source-file-type.md)

MSVC ist mit dem ISO C99-Standard kompatibel, aber nicht streng konform. In den meisten Fällen wird portabler C-Code wie erwartet kompiliert und ausgeführt. Visual C++ unterstützt die meisten Änderungen in ISO C11 nicht. Bestimmte Bibliotheksfunktionen und POSIX-Funktionsnamen sind von MSVC veraltet. Die Funktionen werden unterstützt, aber die bevorzugten Namen haben sich geändert. Weitere Informationen finden Sie [unter Sicherheitsfeatures in der CRT-](../c-runtime-library/security-features-in-the-crt.md) und [Compilerwarnung (Stufe 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Erstellen eines Standard C++-Konsolenprogramms (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C-Sprachreferenz](../c-language/c-language-reference.md)<br/>
[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br/>
[Kompatibilität](../c-runtime-library/compatibility.md)
