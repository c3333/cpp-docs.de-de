---
title: 'Exemplarische Vorgehensweise: Kompilieren eines nativen C++-Programms über die Befehlszeile'
description: Verwenden Sie den Microsoft C++-Compiler über die Eingabeaufforderung.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335232"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Exemplarische Vorgehensweise: Kompilieren eines nativen C++-Programms über die Befehlszeile

Visual Studio enthält einen C- und C++-Befehlszeilencompiler. Sie können ihn verwenden, um von grundlegenden Konsolen-Apps bis hin zu Universelle Windows-Plattform-Apps, Desktop-Apps, Gerätetreibern und .NET-Komponenten alles zu erstellen.

In dieser exemplarischen Vorgehensweise erstellen Sie zunächst ein grundlegendes C++-Programm im „Hello World!“-Stil mithilfe eines Text-Editors und kompilieren dieses dann über die Befehlszeile. Wenn Sie die Visual Studio-IDE testen möchten, anstatt die Befehlszeile zu verwenden, finden Sie weitere Informationen unter [Exemplarische Vorgehensweise: Arbeiten mit Projekten und Projektmappen ( C++ )](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) oder [Verwenden der Visual Studio-IDE für die C++-Desktopentwicklung](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

In dieser exemplarischen Vorgehensweise können Sie anstelle des hier erwähnten Programms auch Ihr eigenes C++-Programm verwenden. Sie können auch ein C++-Codebeispiel aus einem anderen Hilfeartikel verwenden.

## <a name="prerequisites"></a>Voraussetzungen

Für die Durchführung dieser exemplarischen Vorgehensweise müssen entweder Visual Studio und die optionale Workload **Desktopentwicklung mit C++** oder die Befehlszeilenbuildtools für Visual Studio installiert sein.

Visual Studio ist eine *integrierte Entwicklungsumgebung* (IDE). Diese unterstützt einen umfangreichen Editor, Ressourcen-Manager, Debugger und Compiler für viele Sprachen und Plattformen. Zu den verfügbaren Versionen gehört die kostenlose Visual Studio Community-Edition, die alle die C- und C++-Entwicklung unterstützen. Informationen zum Herunterladen und Installieren von Visual Studio finden Sie unter [Installieren der C++-Unterstützung in Visual Studio](vscpp-step-0-installation.md).

Die Buildtools für Visual Studio installieren nur die Befehlszeilencompiler, Tools und Bibliotheken, die Sie benötigen, um C- und C++-Programme zu erstellen. Sie eignen sich ideal für Buildlabs oder Übungen im Schulungskontext und werden schnell installiert. Suchen Sie auf der Seite für [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) nach den Buildtools für Visual Studio, um nur die Befehlszeilentools zu installieren.

Überprüfen Sie, ob die Tools installiert sind und Sie über die Befehlszeile darauf zugreifen können, bevor Sie ein C- oder C++-Programm über die Befehlszeile erstellen. Visual C++ hat komplexe Anforderungen an die Befehlszeilenumgebung hinsichtlich der Suche nach den verwendeten Tools, Headern und Bibliotheken. **Sie können Visual C++ nicht in einem einfachen Eingabeaufforderungsfenster** ohne bestimmte Vorbereitungen verwenden. Glücklicherweise installiert Visual C++ Verknüpfungen zum Starten einer Developer-Eingabeaufforderung, in der die Umgebung für Befehlszeilenbuilds eingerichtet ist. Leider unterscheiden sich die Namen der Verknüpfungen für die Developer-Eingabeaufforderung und deren Position in nahezu jeder Version von Visual C++ und unterschiedlichen Versionen von Windows. Die erste Aufgabe bei der exemplarischen Vorgehensweise besteht darin, herauszufinden, welche Verknüpfung sich am besten eignet.

> [!NOTE]
> Eine Verknüpfung für die Developer-Eingabeaufforderung legt die richtigen Pfade für den Compiler und die Tools sowie für alle erforderlichen Header und Bibliotheken automatisch fest. Sie müssen diese Umgebungswerte selbst festlegen, wenn Sie ein reguläres **Eingabeaufforderungsfenster** verwenden. Weitere Informationen finden Sie unter [Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds](setting-the-path-and-environment-variables-for-command-line-builds.md). Es wird empfohlen, dass Sie eine Verknüpfung für die Developer-Eingabeaufforderung verwenden, anstatt Ihre eigene zu entwickeln.

### <a name="open-a-developer-command-prompt"></a>Öffnen einer Developer-Eingabeaufforderung

1. Öffnen Sie das Startmenü, und klicken Sie auf **Alle Apps**, wenn Sie Visual Studio 2017 oder höher unter Windows 10 installiert haben. Scrollen Sie nach unten, und öffnen Sie den Ordner **Visual Studio** (nicht die Visual Studio-Anwendung). Klicken Sie auf **Developer Command Prompt for VS** (Developer-Eingabeaufforderung für VS), um das Eingabeaufforderungsfenster zu öffnen.

   Öffnen Sie das **Startmenü**, und klicken Sie auf **Alle Apps**, wenn Sie die Microsoft Visual C++-Buildtools 2015 unter Windows 10 installiert haben. Scrollen Sie nach unten, und öffnen Sie den Ordner **Visual C++-Buildtools**. Klicken Sie auf **Visual C++ 2015 x86 Native Tools Command Prompt** (Visual C++ 2015 x86 Native Tools-Eingabeaufforderung), um das Eingabeaufforderungsfenster zu öffnen.

   Sie können auch die Windows-Suchfunktion verwenden, um nach „Developer-Eingabeaufforderung“ zu suchen und die Version anzuklicken, die mit der installierten Version von Visual Studio übereinstimmt. Verwenden Sie die Verknüpfung, um das Eingabeaufforderungsfenster zu öffnen.

1. Überprüfen Sie als Nächstes, ob die Visual C++-Developer-Eingabeaufforderung ordnungsgemäß eingerichtet ist. Geben Sie im Eingabeaufforderungsfenster `cl` ein, und überprüfen Sie, ob die Ausgabe in etwa wie folgt aussieht:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Möglicherweise gibt es Unterschiede hinsichtlich der aktuellen Verzeichnis- oder Versionsnummern. Diese Werte sind abhängig von der Visual C++-Version und allen installierten Updates. Wenn die oben genannte der angezeigten Ausgabe ähnelt, können Sie C- oder C++-Programme über die Befehlszeile erstellen.

   > [!NOTE]
   > Wenn eine Fehlermeldung wie z. B. "'cl' is not recognized as an internal or external command, operable program or batch file" („cl“ wurde nicht als interner oder externer Befehl, ausführbares Programm oder Batchdatei erkannt.), Fehler C1034 oder Fehler LNK1104 beim Ausführen des **`cl`** -Befehls ausgegeben wird, verwenden Sie entweder keine Developer-Eingabeaufforderung, oder es ist ein Fehler bei der Installation von Visual C++ aufgetreten. Sie müssen das Problem beheben, bevor Sie fortfahren können.

   Wenn Sie die Verknüpfung für die Developer-Eingabeaufforderungen nicht finden, oder wenn Sie eine Fehlermeldung erhalten, wenn Sie `cl` eingeben, liegt ein Problem im Zusammenhang mit der Installation von Visual C++ vor. Versuchen Sie, die Visual C++-Komponente in Visual Studio erneut zu installieren, oder installieren Sie die Microsoft Visual C++-Buildtools noch mal. Fahren Sie nicht mit dem nächsten Abschnitt fort, bis der **`cl`** -Befehl funktioniert. Weitere Informationen zur Installation und Problembehandlung von Visual C++ finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Abhängig von der Version von Windows auf dem Computer und der Systemsicherheitskonfiguration müssen Sie ggf. mit der rechten Maustaste das Kontextmenü für die Verknüpfung der Developer-Eingabeaufforderung öffnen und dann auf **Als Administrator ausführen** klicken, um das Programm gemäß den Schritten dieser exemplarischen Vorgehensweise zu erstellen und auszuführen.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Erstellen einer Visual C++-Quelldatei und Kompilieren über die Befehlszeile

1. Geben Sie im Developer-Eingabeaufforderungsfenster `md c:\hello` ein, um ein Verzeichnis zu erstellen. Geben Sie anschließend `cd c:\hello` ein, um zu diesem Verzeichnis zu wechseln. In diesem Verzeichnis werden die Quelldatei und das kompilierte Programm erstellt.

1. Geben Sie im Eingabeaufforderungsfenster `notepad hello.cpp` ein.

   Klicken Sie auf **Ja**, wenn Sie vom Editor aufgefordert werden, eine Datei zu erstellen. Durch diesen Schritt wird ein leeres Editor-Fenster geöffnet, in das Sie Ihren Code in einer Datei namens „hello.cpp“ eingeben können.

1. Geben Sie im Editor die folgenden Codezeilen ein:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Dieser Code ist ein sehr einfaches Programm, das eine Zeile Text auf den Bildschirm schreibt und dann beendet wird. Um Fehler zu minimieren, kopieren Sie diesen Code, und fügen Sie ihn in Editor ein.

1. Speichern Sie Ihre Arbeit. Wählen Sie im Editor im Menü **Datei** den Befehl **Speichern**aus.

   Herzlichen Glückwunsch, Sie haben die C++-Quelldatei „hello.cpp“ erstellt, die nun kompiliert werden kann.

1. Wechseln Sie zurück zum Developer-Eingabeaufforderungsfenster. Geben Sie `dir` in die Eingabeaufforderung ein, um den Inhalt des Verzeichnisses „c:\hello“ aufzulisten. Die Quelldatei „hello.cpp“ sollte in der Verzeichnisauflistung angezeigt werden, die in etwa wie folgt aussieht:

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

   Die Datumsangaben und andere Details werden sich auf Ihrem Computer von den hier gezeigten unterscheiden. Stellen Sie sicher, dass Sie zu dem von Ihnen erstellten Verzeichnis *c:\\hello* wechseln, wenn die Quellcodedatei *hello.cpp* nicht angezeigt wird. Stellen Sie im Editor sicher, dass Sie die Quelldatei in diesem Verzeichnis gespeichert haben. Stellen Sie außerdem sicher, dass Sie den Quellcode mit der Dateinamenerweiterung *`.cpp`* und nicht mit der *`.txt`* -Erweiterung gespeichert haben.

1. Geben Sie in die Developer-Eingabeaufforderung `cl /EHsc hello.cpp` ein, um das Programm zu kompilieren.

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
   > Wenn eine Fehlermeldung wie z. B. "'cl' is not recognized as an internal or external command, operable program or batch file" („cl“ wurde nicht als interner oder externer Befehl, ausführbares Programm oder Batchdatei erkannt.), Fehler C1034 oder Fehler LNK1104 ausgegeben wird, ist die Developer-Eingabeaufforderung nicht ordnungsgemäß eingerichtet. Weitere Informationen zum Beheben dieses Problems finden Sie im Abschnitt **Öffnen einer Developer-Eingabeaufforderung**.

   > [!NOTE]
   > Überprüfen Sie den Quellcode, um Fehler zu beheben, ihn zu speichern und den Compiler dann noch mal auszuführen, wenn Sie einen anderen Compiler- oder Linkerfehler oder eine andere Warnung erhalten. Verwenden Sie das Suchfeld auf dieser MSDN-Seite, um nach der Fehlernummer zu suchen und Informationen zu bestimmten Fehlern zu erhalten.

1. Geben Sie zum Ausführen des hello.exe-Programms an der Eingabeaufforderung `hello`ein.

   Das Programm zeigt folgenden Text an und wird anschließend beendet:

   ```Output
   Hello, world, from Visual C++!
   ```

   Herzlichen Glückwunsch, Sie haben mithilfe der Befehlszeilentools ein C++-Programm kompiliert und ausgeführt.

## <a name="next-steps"></a>Nächste Schritte

Dieses „Hello World!“-Beispiel ist die einfachste Form eines C++-Programms. In realen Programmen sind in der Regel Headerdateien, weitere Quelldateien und Links zu Bibliotheken enthalten.

Sie können die Schritte in dieser exemplarischen Vorgehensweise verwenden, um Ihren eigenen C++-Code zu erstellen, anstatt den gezeigten Beispielcode einzugeben. Mit diesen Schritten können Sie auch viele C++-Codebeispielprogramme erstellen, die Sie auch an anderer Stelle finden. Sie können Ihren Quellcode verwenden und Ihre Apps in jedem beschreibbaren Verzeichnis erstellen. Standardmäßig erstellt die Visual Studio-IDE Projekte in Ihrem Benutzerordner in einem *source\\repos*-Unterordner. Ältere Versionen können Projekte im Ordner *Dokumente\\Visual Studio \<version>\\* Projekte* ablegen.

Wenn Sie ein Programm mit zusätzlichen Quellcodedateien kompilieren möchten, geben Sie alle in der Befehlszeile ein. Beispiel:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

Die `/EHsc`-Befehlszeilenoption weist den Compiler an, das C++-Standardausnahmebehandlungsverhalten zu aktivieren. Ohne diesen Vorgang können ausgelöste Ausnahmen zu nicht zerstörten Objekten und Ressourcenverlusten führen. Weitere Informationen finden Sie unter [/EH (Ausnahmebehandlungsmodell)](reference/eh-exception-handling-model.md).

Wenn Sie zusätzliche Quelldateien angeben, verwendet der Compiler die erste Eingabedatei zum Erstellen des Programmnamens. In diesem Fall wird ein Programm namens „file1.exe“ ausgegeben. Fügen Sie die Linkeroption [/out](reference/out-output-file-name.md) hinzu, um den Namen in „program1.exe“ zu ändern.

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Es empfiehlt sich, mithilfe der Warnstufenoptionen [/W3](reference/compiler-option-warning-level.md) oder [/W4](reference/compiler-option-warning-level.md) zu kompilieren, um automatisch weitere Programmierfehler zu erfassen:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Der Compiler „cl.exe“ bietet viele weitere Optionen. Sie können diese zum Erstellen, Optimieren, Debuggen und Analysieren Ihres Codes anwenden. Geben Sie `cl /?` in die Developer-Eingabeaufforderung ein, um eine kurze Liste anzuzeigen. Sie können die Kompilierung und Verknüpfung auch separat vornehmen und Linkeroptionen in komplexeren Buildszenarios anwenden. Weitere Informationen zu den Compiler- und Linkeroptionen und deren Verwendung finden Sie unter [Referenz zur C-/C++-Erstellung](reference/c-cpp-building-reference.md).

Sie können NMAKE und Makefiles, MSBuild und Projektdateien oder CMake zum Konfigurieren und Erstellen komplexerer Projekte in der Befehlszeile verwenden. Weitere Informationen zur Verwendung dieser Tools finden Sie unter [NMAKE-Referenz](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md) und [CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md).

Die C- und C++-Sprachen sind ähnlich, aber nicht identisch. Der MSVC-Compiler verwendet eine einfache Regel, um zu bestimmen, welche Sprache verwendet werden soll, wenn der Code kompiliert wird. Standardmäßig behandelt der MSVC-Compiler auf *`.c`* endende Dateien wie C-Quellcode und auf *`.cpp`* endende Dateien wie C++-Quellcode. Wenn Sie erzwingen möchten, dass vom Compiler alle Dateien unabhängig von der C++-Dateierweiterung behandelt werden, verwenden Sie die Compileroption [/TP](reference/tc-tp-tc-tp-specify-source-file-type.md).

Der MSVC-Compiler enthält eine C-Laufzeitbibliothek (C Runtime Library, CRT), die mit kleinen Ausnahmen dem ISO C99-Standard entspricht. Portabler Code wird in der Regel wie erwartet kompiliert und ausgeführt. Bestimmte veraltete Bibliotheksfunktionen und mehrere POSIX-Funktionsnamen werden vom MSVC-Compiler als veraltet markiert. Die Funktionen werden unterstützt, aber die bevorzugten Namen wurden geändert. Weitere Informationen finden Sie unter [Sicherheitsfunktionen in der CRT](../c-runtime-library/security-features-in-the-crt.md) und [Compilerwarnung C4996 (Stufe 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Siehe auch

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
