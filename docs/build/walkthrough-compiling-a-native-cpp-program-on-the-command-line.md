---
title: 'Exemplarische Vorgehensweise: Kompilieren eines systemeigenen C++-Programms in der Befehlszeile'
description: Verwenden Sie den Microsoft C++-Compiler aus einer Eingabeaufforderung.
ms.custom: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: c24fdfdaef612059d5c2fbaaa58f10d83f5fe3a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335232"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Exemplarische Vorgehensweise: Kompilieren eines systemeigenen C++-Programms in der Befehlszeile

Visual Studio enthält einen Befehlszeilen-C- und C++-Compiler. Sie können damit alles erstellen, von einfachen Konsolen-Apps bis hin zu universellen Windows-Plattform-Apps, Desktop-Apps, Gerätetreibern und .NET-Komponenten.

In dieser exemplarischen Vorgehensweise erstellen Sie mithilfe eines Texteditors ein einfaches C++-Programm im Stile von "Hello, World" und kompilieren es dann in der Befehlszeile. Wenn Sie die Visual Studio-IDE anstelle der Befehlszeile ausprobieren möchten, finden Sie weitere Informationen unter [Exemplarische Vorgehensweise: Arbeiten mit Projekten und Lösungen (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) oder [Verwenden der Visual Studio-IDE für C++ Desktop development](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

In dieser exemplarischen Vorgehensweise können Sie Ihr eigenes C++-Programm verwenden, anstatt das angezeigte Programm einzugeben. Sie können auch ein C++-Codebeispiel aus einem anderen Hilfeartikel verwenden.

## <a name="prerequisites"></a>Voraussetzungen

Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie entweder Visual Studio und die optionale **Desktopentwicklung mit C++-Workload** oder die Befehlszeile Buildtools für Visual Studio installiert haben.

Visual Studio ist eine *integrierte Entwicklungsumgebung* (IDE). Es unterstützt einen voll funktionsfähigen Editor, Ressourcen-Manager, Debugger und Compiler für viele Sprachen und Plattformen. Zu den verfügbaren Versionen gehört die kostenlose Visual Studio Community-Edition, und alle können die C- und C++-Entwicklung unterstützen. Informationen zum Herunterladen und Installieren von Visual Studio finden Sie unter Installieren der [C++-Unterstützung in Visual Studio](vscpp-step-0-installation.md).

Die Buildtools für Visual Studio installieren nur die Befehlszeilencompiler, Tools und Bibliotheken, die Sie zum Erstellen von C- und C++-Programmen benötigen. Es ist perfekt für den Aufbau von Labors oder Klassenzimmerübungen und wird relativ schnell installiert. Um nur die Befehlszeilentools zu installieren, suchen Sie auf der [Seite Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) nach Buildtools für Visual Studio.

Bevor Sie ein C- oder C++-Programm in der Befehlszeile erstellen können, überprüfen Sie, ob die Tools installiert sind, und Sie können über die Befehlszeile darauf zugreifen. Visual C++ hat komplexe Anforderungen an die Befehlszeilenumgebung, um die verwendeten Tools, Header und Bibliotheken zu finden. **Sie können Visual C++ nicht in einem einfachen Eingabeaufforderungsfenster verwenden,** ohne eine Vorbereitung zu leisten. Glücklicherweise installiert Visual C++ Verknüpfungen, damit Sie eine Entwicklereingabeaufforderung starten können, auf der die Umgebung für Befehlszeilenbuilds eingerichtet ist. Leider unterscheiden sich die Namen der Eingabeaufforderungsverknüpfungen für Entwickler und deren Standort in fast jeder Version von Visual C++ und in verschiedenen Windows-Versionen. Ihre erste exemplarische Aufgabe besteht darin, die richtige Aufgabe zu finden.

> [!NOTE]
> Eine Eingabeaufforderungsverknüpfung für Entwickler legt automatisch die richtigen Pfade für den Compiler und die Tools sowie für alle erforderlichen Header und Bibliotheken fest. Sie müssen diese Umgebungswerte selbst festlegen, wenn Sie ein reguläres **Eingabeaufforderungsfenster** verwenden. Weitere Informationen finden Sie unter [Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds](setting-the-path-and-environment-variables-for-command-line-builds.md). Es wird empfohlen, eine Eingabeaufforderungsverknüpfung für Entwickler zu verwenden, anstatt eine eigene zu erstellen.

### <a name="open-a-developer-command-prompt"></a>Öffnen einer Entwicklereingabeaufforderung

1. Wenn Sie Visual Studio 2017 oder höher unter Windows 10 installiert haben, öffnen Sie das Startmenü, und wählen Sie **Alle Apps**aus. Führen Sie einen Bildlauf nach unten durch, und öffnen Sie den **Visual Studio-Ordner** (nicht die Visual Studio-Anwendung). Wählen Sie **Developer Command Prompt for VS** aus, um das Eingabeaufforderungsfenster zu öffnen.

   Wenn Sie Microsoft Visual C++ Build Tools 2015 unter Windows 10 installiert haben, öffnen Sie das **Startmenü,** und wählen Sie **Alle Apps**aus. Scrollen Sie nach unten, und öffnen Sie den Ordner **Visual C++ Build Tools.** Wählen Sie **Visual C++ 2015 x86 Native Tools Command Prompt,** um das Eingabeaufforderungsfenster zu öffnen.

   Sie können auch die Windows-Suchfunktion verwenden, um nach "Developer-Eingabeaufforderung" zu suchen und eine auszuwählen, die mit ihrer installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabeaufforderungsfenster zu öffnen.

1. Überprüfen Sie als Nächstes, ob die Befehlsaufforderung für die Visual C++-Entwicklereingabe ordnungsgemäß eingerichtet ist. Geben Sie im Eingabeaufforderungsfenster ein, `cl` und überprüfen Sie, ob die Ausgabe etwa wie folgt aussieht:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Es kann Unterschiede in den aktuellen Verzeichnis- oder Versionsnummern geben. Diese Werte hängen von der Version von Visual C++ und allen installierten Updates ab. Wenn die obige Ausgabe dem angezeigt wird, können Sie C- oder C++-Programme in der Befehlszeile erstellen.

   > [!NOTE]
   > Wenn beim Ausführen des Befehls ein Fehler wie "'cl' nicht als interner oder externer Befehl, bedienbares Programm oder Batchdatei erkannt wird", Fehler C1034, oder Fehler LNK1104, wenn Sie den **`cl`** Befehl ausführen, verwenden Sie entweder keine Entwicklereingabe, oder etwas stimmt mit der Installation von Visual C++ nicht. Sie müssen dieses Problem beheben, bevor Sie fortfahren können.

   Wenn Sie die Eingabeaufforderungsverknüpfung für entwickler nicht finden können oder `cl`wenn beim Eingeben eine Fehlermeldung angezeigt wird, liegt möglicherweise bei der Visual C++-Installation ein Problem vor. Versuchen Sie, die Visual C++-Komponente in Visual Studio neu zu installieren, oder installieren Sie die Microsoft Visual C++-Buildtools neu. Fahren Sie nicht mit dem nächsten **`cl`** Abschnitt fort, bis der Befehl funktioniert. Weitere Informationen zum Installieren und Beheben von Visual C++ finden Sie unter Installieren von [Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Abhängig von der Version von Windows auf dem Computer und der Systemsicherheitskonfiguration müssen Sie möglicherweise mit der rechten Maustaste klicken, um das Kontextmenü für die Eingabeaufforderungsverknüpfung für Entwickler zu öffnen, und dann ausführen **als Administrator** auswählen, um das Programm, das Sie erstellen, erfolgreich zu erstellen und auszuführen, indem Sie diese exemplarische Vorgehensweise befolgen.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Erstellen einer Visual C++-Quelldatei und Kompilieren in der Befehlszeile

1. Geben Sie `md c:\hello` im Eingabeaufforderungsfenster des Entwicklerbefehls `cd c:\hello` ein, um ein Verzeichnis zu erstellen, und geben Sie dann ein, um in dieses Verzeichnis zu wechseln. In diesem Verzeichnis werden die Quelldatei und das kompilierte Programm erstellt.

1. Geben `notepad hello.cpp` Sie das Eingabeaufforderungsfenster ein.

   Wählen Sie **Ja,** wenn Sie von Notepad aufgefordert werden, eine Datei zu erstellen. Dieser Schritt öffnet ein leeres Notizblockfenster, in dem Sie Ihren Code in eine Datei mit dem Namen hello.cpp eingeben können.

1. Geben Sie in Notepad die folgenden Codezeilen ein:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Dieser Code ist ein einfaches Programm, das eine Textzeile auf den Bildschirm schreibt und dann beendet. Um Fehler zu minimieren, kopieren Sie diesen Code, und fügen Sie ihn in Editor ein.

1. Speichern Sie Ihre Arbeit. Wählen Sie im Editor im Menü **Datei** den Befehl **Speichern**aus.

   Herzlichen Glückwunsch, Sie haben eine C++-Quelldatei hello.cpp erstellt, die kompiliert werden kann.

1. Wechseln Sie zurück zum Eingabeaufforderungsfenster für Entwickler. Geben `dir` Sie an der Eingabeaufforderung ein, um den Inhalt des Verzeichnisses c:-hello aufzulisten. Sie sollten die Quelldatei hello.cpp in der Verzeichnisliste sehen, die etwa wie folgt aussieht:

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   Die Daten und andere Details unterscheiden sich auf Ihrem Computer. Wenn Ihre Quellcodedatei *hello.cpp*nicht angezeigt wird, stellen Sie sicher, dass Sie in das von Ihnen erstellte *Verzeichnis\\c: hello* geändert haben. Stellen Sie in Notepad sicher, dass Sie die Quelldatei in diesem Verzeichnis gespeichert haben. Stellen Sie außerdem sicher, dass *`.cpp`* Sie den Quellcode *`.txt`* mit einer Dateinamenerweiterung und nicht mit einer Erweiterung gespeichert haben.

1. Geben Sie in der `cl /EHsc hello.cpp` Eingabeaufforderung für die Entwicklereingabe ein, um Ihr Programm zu kompilieren.

   Der cl.exe-Compiler generiert eine OBJ-Datei, die den kompilierten Code enthält, und führt dann den Linker aus, um ein ausführbares Programm namens „hello.exe“ zu erstellen. Dieser Name wird in den Zeilen der Ausgabeinformationen angezeigt, die der Compiler anzeigt. Die Ausgabe des Compilers sollte etwa wie folgt aussehen:

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > Wenn sie eine Fehlermeldung wie "'cl' wird nicht als interner oder externer Befehl, bedienbares Programm oder Batchdatei erkannt", Fehler C1034, oder Fehler LNK1104, wird die Entwicklereingabeaufforderung nicht ordnungsgemäß eingerichtet. Informationen zum Beheben dieses Problems finden Sie im Abschnitt **"Öffnen eines Entwicklerbefehls".**

   > [!NOTE]
   > Wenn Sie einen anderen Compiler- oder Linkerfehler oder eine andere Warnung erhalten, überprüfen Sie den Quellcode, um Fehler zu korrigieren, speichern Sie ihn, und führen Sie den Compiler erneut aus. Informationen zu bestimmten Fehlern finden Sie im Suchfeld auf dieser MSDN-Seite, um nach der Fehlernummer zu suchen.

1. Geben Sie zum Ausführen des hello.exe-Programms an der Eingabeaufforderung `hello`ein.

   Das Programm zeigt folgenden Text an und wird anschließend beendet:

   ```Output
   Hello, world, from Visual C++!
   ```

   Herzlichen Glückwunsch, Sie haben ein C++-Programm mithilfe der Befehlszeilentools kompiliert und ausgeführt.

## <a name="next-steps"></a>Nächste Schritte

Dieses "Hello, World"-Beispiel ist ungefähr so einfach wie ein C++-Programm erhalten kann. Reale Programme haben in der Regel Header-Dateien, mehr Quelldateien und Link zu Bibliotheken.

Sie können die Schritte in dieser exemplarischen Vorgehensweise verwenden, um Ihren eigenen C++-Code zu erstellen, anstatt den angezeigten Beispielcode einzugeben. Mit diesen Schritten können Sie auch viele C++-Codebeispielprogramme erstellen, die Sie an anderer Stelle finden. Sie können Ihren Quellcode ablegen und Ihre Apps in einem beliebigen beschreibbaren Verzeichnis erstellen. Standardmäßig erstellt die Visual Studio-IDE Projekte in Ihrem Benutzerordner in einem *\\Quellrepos-Unterordner.* Ältere Versionen können Projekte in einer *Documents\\Visual Studio-Version \<>\\ *Projects*-Ordner s.

Um ein Programm mit zusätzlichen Quellcodedateien zu kompilieren, geben Sie sie alle in der Befehlszeile ein, z. B.:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

Die `/EHsc` Befehlszeilenoption weist den Compiler an, das standardmäßige C++-Ausnahmebehandlungsverhalten zu aktivieren. Ohne sie können ausgelöste Ausnahmen zu unzerstörten Objekten und Ressourcenlecks führen. Weitere Informationen finden Sie unter [/EH (Ausnahmebehandlungsmodell)](reference/eh-exception-handling-model.md).

Wenn Sie zusätzliche Quelldateien angeben, verwendet der Compiler die erste Eingabedatei, um den Programmnamen zu erstellen. In diesem Fall gibt es ein Programm namens file1.exe aus. Um den Namen in program1.exe [/out](reference/out-output-file-name.md) zu ändern, fügen Sie eine /out-Linker-Option hinzu:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Und um weitere Programmierfehler automatisch zu erfassen, empfehlen wir Ihnen, entweder die Warnungsstufe [/W3](reference/compiler-option-warning-level.md) oder [/W4](reference/compiler-option-warning-level.md) zu verwenden:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Der Compiler, cl.exe, hat viele weitere Optionen. Sie können sie anwenden, um Ihren Code zu erstellen, zu optimieren, zu debuggen und zu analysieren. Geben Sie eine `cl /?` Schnellliste an der Eingabeaufforderung für den Entwickler ein. Sie können auch separat kompilieren und verknüpfen und Linkeroptionen in komplexeren Buildszenarien anwenden. Weitere Informationen zu Compiler- und Linkeroptionen und -verwendung finden Sie unter [C/C++-Baureferenz](reference/c-cpp-building-reference.md).

Sie können NMAKE und makefiles, MSBuild und Projektdateien oder CMake verwenden, um komplexere Projekte in der Befehlszeile zu konfigurieren und zu erstellen. Weitere Informationen zur Verwendung dieser Tools finden Sie unter [NMAKE Reference](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md)und [CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md).

Die C- und C++-Sprachen sind ähnlich, aber nicht identisch. Der MSVC-Compiler verwendet eine einfache Regel, um zu bestimmen, welche Sprache beim Kompilieren des Codes verwendet werden soll. Standardmäßig behandelt der MSVC-Compiler Dateien, *`.c`* die als C-Quellcode enden, und Dateien, die *`.cpp`* als C++-Quellcode enden. Um den Compiler zu zwingen, alle Dateien unabhängig von der Dateinamenerweiterung als C++ zu behandeln, verwenden Sie die Compileroption [/TP.](reference/tc-tp-tc-tp-specify-source-file-type.md)

Der MSVC-Compiler enthält eine C-Runtime-Bibliothek (CRT), die dem ISO C99-Standard entspricht, mit kleineren Ausnahmen. Portabler Code wird in der Regel wie erwartet kompiliert und ausgeführt. Bestimmte veraltete Bibliotheksfunktionen und mehrere POSIX-Funktionsnamen sind vom MSVC-Compiler veraltet. Die Funktionen werden unterstützt, aber die bevorzugten Namen haben sich geändert. Weitere Informationen finden Sie [unter Sicherheitsfeatures in der CRT-](../c-runtime-library/security-features-in-the-crt.md) und [Compilerwarnung (Stufe 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Siehe auch

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)<br/>
[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
