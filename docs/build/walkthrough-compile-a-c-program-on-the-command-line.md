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
ms.openlocfilehash: 1b4e7f0f188ce7b3003f12cb7acafaf15a03d86a
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078255"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Exemplarische Vorgehensweise: Kompilieren eines C-Programms in der Befehlszeile

Visual C++ bietet einen C-Compiler, mit dem Sie alles von einfachen Konsolenprogrammen bis hin zu vollständigen Windows-Desktop Anwendungen, mobilen apps und mehr erstellen können.

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie mit einem Text-Editor ein einfaches "Hello, World"-C-Programm erstellen und dann in der Befehlszeile kompilieren. Wenn Sie lieber in C++ der Befehlszeile arbeiten, finden Sie weitere Informationen unter Exemplarische Vorgehensweise [: Kompilieren eines nativen C++ Programms in der Befehlszeile](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Wenn Sie die Visual Studio-IDE testen möchten, anstatt die Befehlszeile zu verwenden, finden Sie weitere Informationen unter Exemplarische Vorgehensweise [:C++arbeiten mit Projekten und Projektmappen ()](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) oder [Verwenden der Visual Studio-IDE für C++ die Desktop Entwicklung](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Voraussetzungen

Um diese exemplarische Vorgehensweise durchführen zu können, müssen Sie entweder Visual Studio und C++ die optionalen visuellen Komponenten oder die Buildtools für Visual Studio installiert haben.

Visual Studio ist eine leistungsstarke integrierte Entwicklungsumgebung, die einen voll funktionsfähigen Editor, Ressourcen-Manager, Debugger und Compiler für viele Sprachen und Plattformen unterstützt. Weitere Informationen zu diesen Features und zum herunterladen und Installieren von Visual Studio, einschließlich der kostenlosen Visual Studio Community Edition, finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio).

Die Buildtools für Visual Studio-Version von Visual Studio installieren nur das Befehlszeilen-Toolset, die Compiler, Tools und Bibliotheken, die Sie benötigen, um C++ C und Programme zu erstellen. Es eignet sich ideal für buildlabs oder Schulungs Übungen und die Installation relativ schnell. Um nur das Befehlszeilen-Toolset zu installieren, laden Sie Build Tools für Visual Studio von der [Visual Studio-Download](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) Seite herunter, und führen Sie das Installationsprogramm aus. Wählen Sie im Visual Studio-Installer die  **C++ Arbeitsauslastung Build Tools** aus, und wählen Sie dann **Installieren**aus.

Bevor Sie ein C-oder C++ -Programm in der Befehlszeile erstellen können, müssen Sie sicherstellen, dass die Tools installiert sind und dass Sie über die Befehlszeile darauf zugreifen können. Visual C++ hat komplexe Anforderungen an die Befehlszeilen Umgebung, um die verwendeten Tools, Header und Bibliotheken zu finden. Das **visuelle C++ Element kann nicht in einem einfachen Eingabe** Aufforderungs Fenster ohne Vorbereitung verwendet werden. Sie benötigen ein *Eingabe* Aufforderungs Fenster für Entwickler, bei dem es sich um ein reguläres Eingabe Aufforderungs Fenster handelt, das alle erforderlichen Umgebungsvariablen enthält. Glücklicherweise installiert Visual C++ die Tastenkombinationen, mit denen Sie Entwickler Eingabe Aufforderungen starten können, bei denen die Umgebung für Befehlszeilenbuilds eingerichtet ist. Leider unterscheiden sich die Namen der Verknüpfungen für Entwickler-Eingabe Aufforderungen und deren Position in nahezu jeder Version von C++ Visual und unterschiedlichen Versionen von Windows. Die erste Exemplarische Vorgehensweise ist die Suche nach der richtigen Verknüpfung, die verwendet werden soll.

> [!NOTE]
> Eine Eingabe Aufforderungs Verknüpfung für Entwickler legt automatisch die richtigen Pfade für den Compiler und die Tools sowie für alle erforderlichen Header und Bibliotheken fest. Einige dieser Werte unterscheiden sich für jede Buildkonfiguration. Sie müssen diese Umgebungs Werte selbst festlegen, wenn Sie keine der Tastenkombinationen verwenden. Weitere Informationen finden Sie unter [Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds](setting-the-path-and-environment-variables-for-command-line-builds.md). Da die Buildumgebung Komplex ist, empfehlen wir dringend, dass Sie eine Eingabeaufforderung für Entwickler verwenden, anstatt ihre eigenen zu erstellen.

Diese Anweisungen sind abhängig von der verwendeten Version von Visual Studio. Bevor Sie fortfahren, stellen Sie sicher, dass die Versions Auswahl in der linken oberen Ecke dieser Seite ordnungsgemäß festgelegt ist.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Öffnen Sie eine Developer-Eingabeaufforderung in Visual Studio 2019

Wenn Sie Visual Studio 2019 unter Windows 10 installiert haben, öffnen Sie das Startmenü, Scrollen Sie nach unten, und öffnen Sie den Ordner **Visual Studio 2019** (nicht die Visual Studio 2019-APP). Wählen Sie **Developer-Eingabeaufforderung für vs 2019 aus** , um das Eingabe Aufforderungs Fenster zu öffnen.

Wenn Sie eine andere Version von Windows verwenden, suchen Sie im Startmenü oder auf der Startseite nach einem Visual Studio-Tools-Ordner, der eine Eingabe Aufforderungs Verknüpfung für Entwickler enthält. Sie können auch die Windows Search-Funktion verwenden, um nach "Developer Command Prompt" zu suchen und eine solche auszuwählen, die mit der installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabe Aufforderungs Fenster zu öffnen.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Öffnen Sie eine Developer-Eingabeaufforderung in Visual Studio 2017

Wenn Sie Visual Studio 2017 unter Windows 10 installiert haben, öffnen Sie das Startmenü, Scrollen Sie nach unten, und öffnen Sie den Ordner **Visual Studio 2017** (nicht die Visual Studio 2017-APP). Wählen Sie **Developer-Eingabeaufforderung für vs 2017 aus** , um das Eingabe Aufforderungs Fenster zu öffnen.

Wenn Sie eine andere Version von Windows ausführen, suchen Sie im Startmenü oder auf der Startseite nach einem Visual Studio-Tools-Ordner, der eine Eingabe Aufforderungs Verknüpfung für Entwickler enthält. Sie können auch die Windows Search-Funktion verwenden, um nach "Developer Command Prompt" zu suchen und eine solche auszuwählen, die mit der installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabe Aufforderungs Fenster zu öffnen.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Öffnen Sie eine Developer-Eingabeaufforderung in Visual Studio 2015

Wenn Sie Microsoft Visual C++ Build Tools 2015 unter Windows 10 installiert haben, öffnen Sie das Startmenü, Scrollen Sie nach unten, und öffnen Sie den Ordner **Visual C++ Build Tools** . **Start** Wählen **Sie C++ Visual 2015 x86 Native Tools-Eingabeaufforderung** aus, um das Eingabe Aufforderungs Fenster zu öffnen.

Wenn Sie eine andere Version von Windows ausführen, suchen Sie im Startmenü oder auf der Startseite nach einem Visual Studio-Tools-Ordner, der eine Eingabe Aufforderungs Verknüpfung für Entwickler enthält. Sie können auch die Windows Search-Funktion verwenden, um nach "Developer Command Prompt" zu suchen und eine solche auszuwählen, die mit der installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabe Aufforderungs Fenster zu öffnen.

::: moniker-end

Überprüfen Sie als nächstes, C++ ob die Visual Developer-Eingabeaufforderung ordnungsgemäß eingerichtet ist. Geben Sie im Eingabe Aufforderungs Fenster `cl` ein, und überprüfen Sie, ob die Ausgabe in etwa wie folgt aussieht:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Abhängig von der Version von Visual C++ und allen installierten Updates gibt es möglicherweise Unterschiede in den aktuellen Verzeichnis-oder Versionsnummern. Wenn die oben genannte Ausgabe ähnlich aussieht wie Sie sehen, können Sie C-oder C++ -Programme in der Befehlszeile erstellen.

> [!NOTE]
> Wenn Sie eine Fehlermeldung wie z. b. "CL" wird nicht als interner oder externer Befehl, ausführbares Programm oder eine Batchdatei (Fehler C1034 oder Fehler LNK1104) erkennen, wenn Sie den **cl** -Befehl ausführen, verwenden Sie entweder keine Entwickler-Eingabeaufforderung, oder es ist ein Fehler bei der Installation C++der Visualisierung aufgetreten. Sie müssen dieses Problem beheben, bevor Sie fortfahren können.

Wenn Sie die Verknüpfung für Entwickler-Eingabe Aufforderungen nicht finden oder wenn Sie eine Fehlermeldung erhalten, wenn Sie `cl`eingeben, C++ kann bei der visuellen Installation ein Problem auftreten. Wenn Sie Visual Studio 2017 oder höher verwenden, versuchen Sie, die **Desktop Entwicklung mit der C++**  Arbeitsauslastung im Visual Studio-Installer erneut zu installieren. Weitere Informationen finden Sie [unter C++ Installieren der Unterstützung in Visual Studio](vscpp-step-0-installation.md). Oder installieren Sie die Buildtools über die [Visual Studio-Download](https://visualstudio.microsoft.com/downloads/) Seite neu. Fahren Sie nicht mit dem nächsten Abschnitt fort, bis dies funktioniert. Weitere Informationen zur Installation und Problembehandlung von Visual Studio finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> Abhängig von der Windows-Version auf dem Computer und der System Sicherheitskonfiguration müssen Sie möglicherweise mit der rechten Maustaste klicken, um das Kontextmenü für die Eingabeaufforderung für Entwickler-Eingabeaufforderung zu öffnen. Wählen Sie dann **als Administrator ausführen** aus, um das in dieser exemplarischen Vorgehensweise erstellte Programm erfolgreich zu erstellen und auszuführen.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Erstellen Sie eine C-Quelldatei, und kompilieren Sie Sie in der Befehlszeile.

1. Geben Sie im Eingabe Aufforderungs Fenster des Entwicklers `cd c:\` ein, um das aktuelle Arbeitsverzeichnis in das Stammverzeichnis des Laufwerks C: zu ändern. Geben Sie als nächstes `md c:\simple` ein, um ein Verzeichnis zu erstellen, und geben Sie dann `cd c:\simple` ein, um zu diesem Verzeichnis zu wechseln. Dieses Verzeichnis enthält die Quelldatei und das kompilierte Programm.

1. Geben Sie `notepad simple.c` an der Developer-Eingabeaufforderung ein. Wählen Sie im angezeigten Dialogfeld Notepad-Warnung die Option **Ja** aus, um eine neue einfache c-Datei in Ihrem Arbeitsverzeichnis zu erstellen.

1. Geben Sie im Editor die folgenden Codezeilen ein:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Wählen Sie in der Editor-Menüleiste **Datei** > **Speichern** aus, um Simple. c in Ihrem Arbeitsverzeichnis zu speichern.

1. Wechseln Sie zurück zum Entwickler-Eingabe Aufforderungs Fenster. Geben Sie `dir` an der Eingabeaufforderung ein, um den Inhalt des Verzeichnisses "c:\simple ein" aufzulisten. Die Quelldatei "Simple. c" sollte in der Verzeichnis Auflistung angezeigt werden, was etwa wie folgt aussieht:

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

   Die Datumsangaben und andere Details unterscheiden sich auf Ihrem Computer. Wenn die Quell Code Datei "Simple. c" nicht angezeigt wird, stellen Sie sicher, dass Sie das Verzeichnis "c:\simple ein" geändert haben, das Sie erstellt haben, und stellen Sie sicher, dass Sie die Quelldatei in diesem Verzeichnis gespeichert haben. Stellen Sie außerdem sicher, dass Sie den Quellcode mit der Dateinamenerweiterung ". c" und nicht mit der Erweiterung ". txt" gespeichert haben.

1. Geben Sie `cl simple.c` an der Developer-Eingabeaufforderung ein, um das Programm zu kompilieren.

   Der ausführbare Programmname "Simple. exe" wird in den Ausgabeinformationen angezeigt, die der Compiler anzeigt:

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
   > Wenn Sie einen Fehler wie "CL" erhalten, der nicht als interner oder externer Befehl, ausführbares Programm oder eine Batchdatei (Fehler C1034 oder Fehler LNK1104) erkannt wird, ist die Entwickler-Eingabeaufforderung nicht ordnungsgemäß eingerichtet. Weitere Informationen zum Beheben dieses Problems finden Sie im Abschnitt **Öffnen einer Developer-Eingabeaufforderung** .

   > [!NOTE]
   > Wenn Sie einen anderen Compiler oder Linker-Fehler oder eine andere Warnung erhalten, überprüfen Sie den Quellcode, um alle Fehler zu beheben, speichern Sie ihn, und führen Sie den Compiler erneut aus. Um Informationen zu bestimmten Fehlern zu erhalten, verwenden Sie das Suchfeld am oberen Rand dieser Seite, um nach der Fehlernummer zu suchen.

1. Geben Sie `simple` an der Eingabeaufforderung ein, um das Programm auszuführen.

   Das Programm zeigt folgenden Text an und wird anschließend beendet:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Herzlichen Glückwunsch, Sie haben ein C-Programm mit der Befehlszeile kompiliert und ausgeführt.

## <a name="next-steps"></a>Nächste Schritte

Dieses "Hello, World"-Beispiel ist so einfach wie ein C-Programm. In realen Programmen sind Header Dateien und weitere Quelldateien vorhanden, die in Bibliotheken verknüpft sind und nützliche Arbeiten bewirken.

Sie können die Schritte in dieser exemplarischen Vorgehensweise verwenden, um Ihren eigenen C-Code zu erstellen, anstatt den gezeigten Beispielcode einzugeben. Sie können auch viele C-Codebeispiel Programme erstellen, die Sie an anderer Stelle finden. Wenn Sie ein Programm mit zusätzlichen Quell Code Dateien kompilieren möchten, geben Sie alle in der Befehlszeile ein, z. b.:

`cl file1.c file2.c file3.c`

Der Compiler gibt ein Programm mit dem Namen file1. exe aus. Um den Namen in Program1. exe zu ändern, fügen Sie eine [/out](reference/out-output-file-name.md) Linker-Option hinzu:

`cl file1.c file2.c file3.c /link /out:program1.exe`

Um automatisch mehr Programmierfehler zu erfassen, empfiehlt es sich, die Kompilierung entweder mithilfe der [/w3](reference/compiler-option-warning-level.md) -Option oder der [/W4](reference/compiler-option-warning-level.md) -Warnstufe zu kompilieren:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Der Compiler "CL. exe" verfügt über viele weitere Optionen, die Sie zum Erstellen, optimieren, Debuggen und analysieren Ihres Codes anwenden können. Geben Sie `cl /?` an der Developer-Eingabeaufforderung ein, um eine kurze Liste zu erhalten. Sie können auch separat kompilieren und verknüpfen und Linkeroptionen in komplexeren Buildszenarien anwenden. Weitere Informationen zu den Optionen und der Verwendung von Compileroptionen und Linkeroptionen finden Sie unter [C/C++ Building Reference](reference/c-cpp-building-reference.md).

Sie können NMAKE-und Makefiles-oder MSBuild-und Projektdateien verwenden, um komplexere Projekte in der Befehlszeile zu konfigurieren und zu erstellen. Weitere Informationen zur Verwendung dieser Tools finden Sie unter [NMAKE Reference](reference/nmake-reference.md) und [MSBuild](msbuild-visual-cpp.md).

Die C- C++ und-Sprachen sind ähnlich, aber nicht identisch. Der Microsoft C/C++ Compiler (MSVC) verwendet eine einfache Regel, um zu bestimmen, welche Sprache verwendet werden soll, wenn der Code kompiliert wird. Standardmäßig behandelt der MSVC-Compiler alle Dateien, die mit. c enden, als c-Quellcode und alle Dateien, die auf. cpp C++ enden, als Quellcode. Verwenden Sie die [/TC](reference/tc-tp-tc-tp-specify-source-file-type.md) -Compileroption, um zu erzwingen, dass der Compiler alle Dateien als nicht von der Dateinamenerweiterung abhängige C behandelt.

MSVC ist mit dem ISO C99-Standard kompatibel, jedoch nicht streng kompatibel. In den meisten Fällen wird der Portable C-Code wie erwartet kompiliert und ausgeführt. Visual C++ unterstützt den größten Teil der Änderungen in ISO C11 nicht. Bestimmte Bibliotheksfunktionen und POSIX-Funktionsnamen werden von MSVC als veraltet markiert. Die Funktionen werden unterstützt, aber die bevorzugten Namen wurden geändert. Weitere Informationen finden Sie unter [Sicherheitsfunktionen in der CRT](../c-runtime-library/security-features-in-the-crt.md) und [Compilerwarnung (Stufe 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Weitere Informationen

[Exemplarische Vorgehensweise: Erstellen eines Standard C++-Konsolenprogramms (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C-Sprachreferenz](../c-language/c-language-reference.md)<br/>
[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br/>
[Kompatibilität](../c-runtime-library/compatibility.md)
