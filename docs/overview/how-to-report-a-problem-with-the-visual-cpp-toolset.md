---
title: Melden eines Problems mit dem Microsoft C++-Toolset
description: So erstellen Sie einen nützlichen Problembericht und Informationen zur Reproduktion für das Microsoft C++-Toolset
ms.date: 09/24/2019
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 7a89966b46efbef9800f3f3ddf836723bbb3b06f
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334246"
---
# <a name="how-to-report-a-problem-with-the-microsoft-c-toolset-or-documentation"></a>Melden eines Problems mit dem Microsoft C++-Toolset oder der -Dokumentation

Wenn Probleme mit dem Microsoft C++-Compiler (MSVC), dem Linker oder anderen Tools oder Bibliotheken auftreten, teilen Sie uns dies bitte mit. Wenn in unserer Dokumentation ein Fehler vorliegt, möchten wir das natürlich auch wissen.

## <a name="how-to-report-a-c-toolset-issue"></a>Melden eines Problems mit einem C++-Toolset

Am einfachsten informieren Sie uns über ein Problem, indem Sie uns einen Bericht mit einer Beschreibung des Problems senden, das Sie entdeckt haben. Der Bericht sollte alle notwendigen Informationen dazu enthalten, wie Sie Ihr Programm erstellen. Zudem sollte der Bericht eine *Reproduktion* umfassen, also einen kompletten Testfall, den wir verwenden können, um das Problem auf unseren Computern zu reproduzieren. Mithilfe dieser Informationen können wir schnell prüfen, ob in unserem Code ein Fehler vorliegt oder das Problem möglicherweise lokal in Ihrer Umgebung besteht. Wir können ermitteln, ob andere Versionen des Compilers betroffen sind, und die Ursache diagnostizieren.

In den folgenden Abschnitten erfahren Sie, was einen guten Bericht ausmacht. Wir beschreiben, wie Sie eine Reproduktion für das von Ihnen erkannte Problem generieren und wie Sie Ihren Bericht an das Produktteam senden. Ihre Berichte sind wichtig für uns und andere Entwickler wie Sie. Vielen Dank für Ihren Beitrag zur Verbesserung von Microsoft C++!

## <a name="how-to-prepare-your-report"></a>Vorbereiten des Berichts

Ein guter Bericht ist wichtig, denn für uns ist es schwierig, das von Ihnen gefundene Problem zu reproduzieren, wenn wir nicht über alle notwendigen Informationen verfügen. Je besser Ihr Bericht ist, desto effektiver können wir das Problem reproduzieren und untersuchen.

Ihr Bericht sollte mindestens die folgenden Elemente enthalten:

- Die vollständigen Informationen zur Version des Toolsets, das Sie verwenden.

- Die vollständige „cl.exe“-Befehlszeile, die zum Erstellen Ihres Code verwendet wurde.

- Eine ausführliche Beschreibung des Problems, das Sie gefunden haben.

- Bei einer Reproduktion handelt es sich um ein vollständiges, vereinfachtes und unabhängiges Quellcodebeispiel, das das Problem veranschaulicht.

Lesen Sie weiter, um mehr über das Erstellen einer guten Reproduktion und die spezifischen Informationen zu erfahren, die wir benötigen, und wo Sie diese finden können.

### <a name="the-toolset-version"></a>Die Version des Toolsets

Wir benötigen vollständige Informationen zur Version sowie zur Zielarchitektur des Toolsets, das das Problem verursacht. So können wir Ihre Reproduktion mit dem gleichen Toolset auf unseren Computern nachstellen. Wenn wir das Problem reproduzieren können, verfügen wir über einen Ausgangspunkt, um zu untersuchen, welche anderen Versionen des Toolsets dasselbe Problem aufweisen.

#### <a name="to-report-the-full-version-of-your-compiler"></a>So geben Sie die vollständige Version Ihres Compilers an

1. Öffnen Sie die **Developer-Eingabeaufforderung**, die der Version von Visual Studio entspricht, und die Konfigurationsarchitektur, die zum Erstellen Ihres Projekts verwendet wurde. Wenn Sie beispielsweise Anwendungen für x64-Ziele mithilfe von Visual Studio 2017 für x64 erstellen, wählen Sie **x64 Native Tools-Eingabeaufforderung für Visual Studio 2017** aus. Weitere Informationen finden Sie unter [Developer command prompt shortcuts (Tastenkombinationen für die Developer-Eingabeaufforderung)](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts).

1. Geben Sie im Fenster „Developer-Eingabeaufforderung“ den Befehl **cl /Bv** ein.

Die Ausgabe sollte etwa so aussehen:

```Output
C:\Users\username\Source>cl /Bv
Microsoft (R) C/C++ Optimizing Compiler Version 19.14.26428.1 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\cl.exe:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1xx.dll:      Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c2.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\link.exe:      Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\mspdb140.dll:  Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\1033\clui.dll: Version 19.14.26428.1

cl : Command line error D8003 : missing source filename
```

Kopieren Sie die gesamte Ausgabe in den Bericht.

### <a name="the-command-line"></a>Die Befehlszeile

Wir benötigen die exakte Befehlszeile cl.exe mit sämtlichen Argumenten, die Sie zum Erstellen Ihres Codes verwendet haben. So können wir den Buildprozess auf exakt die gleiche Weise auf unseren Computern ausführen. Das ist wichtig, da das aufgetretene Problem eventuell nur existiert, wenn der Build mit einem bestimmten Argument oder einer Kombination von Argumenten erstellt wird.

Diese Informationen finden Sie am besten unmittelbar nach dem Auftreten des Problems im Buildprotokoll. Dadurch wird sichergestellt, dass die Befehlszeile genau die gleichen Argumente enthält, die möglicherweise zum Problem beitragen.

#### <a name="to-report-the-contents-of-the-command-line"></a>So melden Sie den Inhalt der Befehlszeile

1. Wechseln Sie zur Daten **CL.command.1.tlog**, und öffnen Sie sie. Standardmäßig befindet sich diese Datei im Ordner „Dokumente“ unter \\Visual Studio *Version*\\Projects\\*Projektmappenname*\\*Projektname*\\*Configuration*\\*Projektname*.tlog\\CL.command.1.tlog oder im Ordner „Benutzer“ unter \\Source\\Repos\\*Projektmappenname*\\*Projektname*\\*Configuration*\\*Projektname*.tlog\\CL.command.1.tlog. Wenn Sie ein anderes Buildsystem verwenden oder den Standardspeicherort für Ihr Projekt geändert haben, kann der Speicherort abweichen.

   In dieser Datei finden Sie die Namen Ihrer Quellcodedateien, gefolgt von den Befehlszeilenargumenten zu deren Kompilierung, jeweils in separaten Zeilen.

1. Suchen Sie die Zeile, die den Namen der Quellcodedatei enthält, in der das Problem auftritt. Die Zeile darunter enthält die zugehörigen cl.exe-Befehlsargumente.

Kopieren Sie die gesamte Befehlszeile in den Bericht.

### <a name="a-description-of-the-problem"></a>Eine Beschreibung des Problems

Wir benötigen eine ausführliche Beschreibung des gefundenen Problems. So können wir überprüfen, ob wir den gleichen Effekt auf unseren Computern feststellen. Manchmal ist es für uns auch hilfreich zu wissen, was Sie erreichen wollten und welches Ergebnis Sie erwartet haben.

Eine gute Beschreibung enthält die **exakten Fehlermeldungen**, die das Toolset ausgibt, bzw. das genaue Laufzeitverhalten, das Sie feststellen. Wir benötigen diese Informationen, um zu überprüfen, ob das Problem richtig reproduziert wurde. Geben Sie nicht nur die letzte Fehlermeldung, sondern die **gesamte** Ausgabe des Compilers an. Wir müssen alle Gegebenheiten überblicken können, die vor dem Ihnen ausgestellten Bericht vorhanden waren. Wenn Sie das Problem mit dem Befehlszeilencompiler duplizieren können, wird die Ausgabe dieses Compilers bevorzugt. Die IDE und andere Buildsysteme filtern möglicherweise die Fehlermeldungen, die Ihnen angezeigt werden, oder erfassen nur die erste Zeile einer Fehlermeldung.

Wenn der Fehler darin besteht, dass der Compiler ungültigen Code akzeptiert und keine Diagnose generiert, erwähnen Sie dies in Ihrem Bericht.

Fügen Sie zum Melden eines Problems mit dem Laufzeitverhalten eine **genaue Kopie** der Ausgabe des Programms und die erwartete Ausgabe hinzu. Im Idealfall betten Sie diese in die Ausgabeanweisung selbst ein, z.B. `printf("This should be 5: %d\n", actual_result);`. Erwähnen Sie ebenfalls, falls das Programm abstürzt oder nicht reagiert.

Fügen Sie weitere Details hinzu, die beim Diagnostizieren Ihres Problems hilfreich sein können, z.B. Problemumgehungen, die Sie möglicherweise entdeckt haben. Vermeiden Sie die Wiederholung von Informationen, die an anderer Stelle in Ihrem Bericht vorhanden ist.

### <a name="the-repro"></a>Die Reproduktion

Eine *Reproduktion* ist ein vollständiges, unabhängiges Quellcodebeispiel. Dieses Beispiel veranschaulicht das von Ihnen ermittelte Problem auf reproduzierbare Weise, daher der Name. Wir benötigen eine Reproduktion, um den Fehler auf unseren Computern zu reproduzieren. Der Code sollte alle notwendigen Elemente enthalten, um eine grundlegende ausführbare Datei zu erstellen, die sich kompilieren und ausführen lässt. Bzw. die sich kompilieren und ausführen *ließe*, wenn das von Ihnen ermittelte Problem nicht bestünde. Eine Reproduktion ist kein Codeausschnitt. Sie sollte alle Funktionen und Klassen sowie alle erforderlichen #include-Direktiven enthalten, auch für die Standardheader.

#### <a name="what-makes-a-good-repro"></a>Was zeichnet eine gute Reproduktion aus?

Eine gute Reproduktion weist folgende Merkmale auf:

- **Minimal.** Reproduktionen sollten so klein wie möglich sein und dennoch das aufgetretene Problem exakt veranschaulichen. Reproduktionen müssen weder komplex noch realistisch sein. Sie müssen nur den Code zeigen, der mit der Standardimplementierung oder der dokumentierten Compilerimplementierung konform ist. Im Fall einer fehlenden Diagnose sollte Ihre Reproduktion den nicht konformen Code zeigen. Einfache und zielführende Reproduktionen, die nur so viel Code enthalten, wie zum Veranschaulichen des Problems notwendig ist, sind am besten. Wenn Sie Code entfernen oder den Code vereinfachen können, ohne Konformität einzubüßen oder das Problem zu verändern, ist dies erwünscht. Sie müssen keine Gegenbeispiele für funktionierenden Code einfügen.

- **Unabhängig.** In Reproduktionen sollten unnötige Abhängigkeiten vermieden werden. Wenn Sie das Problem ohne Drittanbieterbibliotheken reproduzieren können, ist dies erwünscht. Wenn Sie das Problem abgesehen von einfachen Ausgabeanweisungen (z.B. `puts("this shouldn't compile");`, `std::cout << value;` und `printf("%d\n", value);`) ohne Bibliothekscode reproduzieren können, ist dies erwünscht. Idealerweise kann das Beispiel in eine einzige Quellcodedatei ohne Verweise auf Benutzerheader komprimiert werden. Für uns ist es enorm hilfreich, wenn Sie die Menge des Codes verringern, den wir als mögliche Ursache des Problems untersuchen müssen.

- **Neueste Compilerversion.** Reproduktionen müssen mit dem neuesten Update der neuesten Version des Toolsets erstellt werden. Sie können auch die neueste Prereleaseversion des nächsten Updates oder des nächsten Hauptrelease verwenden. Probleme, die in älteren Versionen des Toolsets auftreten, wurden in neueren Versionen häufig behoben. Fehlerbehebungen werden nur in Ausnahmefälle für ältere Versionen bereitgestellt.

- Ein **Vergleich mit anderen Compilern** wurde durchgeführt (falls relevant). Bei Reproduktionen, die portablen C++-Code enthalten, muss das Verhalten mit anderen Compilern, falls möglich, verglichen werden. Der C++-Standard bestimmt letztendlich die Korrektheit des Programms, und kein Compiler ist perfekt. Wenn jedoch Clang und GCC Ihren Code ohne Diagnose akzeptieren, MSVC aber nicht, dann haben Sie möglicherweise einen Fehler in unserem Compiler gefunden. (Weitere Möglichkeiten bestehen in den unterschiedlichen Verhaltensweisen von Unix und Windows, in verschiedenen Implementierungsebenen der C++-Standards usw.) Wenn Ihr Code von allen Compilern abgelehnt wird, ist es eher wahrscheinlich, dass Ihr Code Fehler enthält. Die verschiedenen angezeigten Fehlermeldungen können Sie dabei unterstützen, das Problem selbst zu diagnostizieren.

   Eine Liste der Onlinecompiler, mit denen Sie Ihren Code testen können, finden Sie unter [Online C++ compilers (C++-Onlinecompiler)](https://isocpp.org/blog/2013/01/online-c-compilers) auf der ISO C++-Website, oder Sie verwenden diese zusammengestellte [List of Online C++ Compilers (Liste der C++-Onlinecompiler)](https://arnemertz.github.io/online-compilers/) auf GitHub. Zu den Beispielen zählen [Wandbox](https://wandbox.org/), [Compiler Explorer](https://godbolt.org/) und [Coliru](https://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Die Websites für Onlinecompiler stehen nicht in Verbindung mit Microsoft. Viele Websites für Onlinecompiler werden als persönliche Projekte betrieben. Einige Websites sind zu dem Zeitpunkt, zu dem Sie diesen Artikel lesen, möglicherweise nicht mehr verfügbar, Sie können aber nach anderen Websites suchen, die Sie verwenden können.

Probleme mit dem Compiler, dem Linker und den Bibliotheken weisen üblicherweise bestimmte Merkmale auf. Die Art des aufgetretenen Problems bestimmt, welche Art von Reproduktion in den Bericht aufgenommen werden soll. Ohne geeignete Reproduktion gibt es nichts, was wir untersuchen könnten. Im Folgenden finden Sie einige der Arten von Problemen, die auftreten können. Sie finden auch Anleitungen dazu, wie Sie die Reproduktion generieren, die Sie für den Bericht zur jeweiligen Problemart verwenden.

#### <a name="frontend-parser-crash"></a>Front-End-Absturz (in der Analysephase)

Front-End-Abstürze erfolgen in der Analysephase des Compilers. In der Regel gibt der Compiler den [schwerwiegenden Fehler C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md) aus und verweist auf die Quellcodedatei und die Nummer der Codezeile, in der der Fehler auftritt. Häufig wird eine Datei namens „msc1.cpp“ erwähnt, dieses Detail können Sie aber ignorieren.

Stellen Sie bei dieser Art von Absturz eine [vorverarbeitete Reproduktion](#preprocessed-repros) bereit.

Hier ist ein Beispiel der Ausgabe des Compilers bei dieser Art von Absturz:

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend-code-generation-crash"></a>Back-End-Absturz (Codegenerierung)

Back-End-Abstürze erfolgen in der Codegenerierungsphase des Compilers. In der Regel gibt der Compiler den [schwerwiegenden Fehler C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md) aus und verweist möglicherweise nicht auf die Quellcodedatei und die Nummer der Codezeile, in der das Problem auftritt. Häufig wird die Datei „compiler\\utc\\src\\p2\\main.c“ erwähnt, dieses Detail können Sie aber ignorieren.

Stellen Sie für diese Art von Absturz eine [Linkreproduktion](#link-repros) bereit, wenn Sie die Link-Zeitcodegenerierung (Link-Time Code Generation, LTCG) verwenden, die vom Befehlszeilenargument **/GL** für „cl.exe“ aktiviert wurde. Wenn dies nicht der Fall ist, stellen Sie stattdessen eine [vorverarbeitete Reproduktion](#preprocessed-repros) bereit.

Hier finden Sie ein Beispiel der Ausgabe des Compilers bei einem Back-End-Absturz, wenn LTCG nicht verwendet wird. Wenn Ihre Compilerausgabe wie folgt aussieht, sollten Sie eine [vorverarbeitete Reproduktion](#preprocessed-repros) bereitstellen.

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

Wenn in der Zeile, die mit **INTERNAL COMPILER ERROR** beginnt, „link.exe“ anstatt „cl.exe“ angegeben ist, war LTCG aktiviert. Stellen Sie in diesem Fall eine [Linkreproduktion](#link-repros) bereit. Wenn aus der Fehlermeldung des Compilers nicht hervorgeht, ob LTCG aktiviert wurde, sehen Sie sich die Befehlszeilenargumente an. Sie haben diese in einem vorherigen Schritt für das Befehlszeilenargument **/GL** aus Ihrem Buildprotokoll kopiert.

#### <a name="linker-crash"></a>Linkerabstürze

Linkerabstürze treten in der Verknüpfungsphase nach Ausführung des Compilers auf. In der Regel gibt der Linker [Linkertoolfehler LNK1000](../error-messages/tool-errors/linker-tools-error-lnk1000.md) aus.

> [!NOTE]
> Wenn in der Ausgabe „C1001“ oder „LTCG“ erwähnt wird, lesen Sie stattdessen den Abschnitt [Back-End-Absturz (Codegenerierung)](#backend-code-generation-crash).

Stellen Sie bei dieser Art von Absturz eine [Linkreproduktion](#link-repros) bereit.

Hier sehen Sie ein Beispiel für die Compilerausgabe bei dieser Art von Absturz:

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

Wenn inkrementelle Verknüpfungen aktiviert sind und der Absturz nach der erfolgreichen anfänglichen Verknüpfung stattgefunden hat (d.h. erst nach der ersten vollständigen Verknüpfung, auf der nachfolgende inkrementelle Verknüpfungen basieren), stellen Sie eine Kopie der Objekt- und Bibliotheksdateien (OBJ und LIB) bereit, die den Quelldateien entsprechen, die nach Abschluss der anfänglichen Verknüpfung geändert wurden.

#### <a name="bad-code-generation"></a>Generierung von fehlerhaftem Code

Eine Generierung von fehlerhaftem Code kommt selten vor. Sie tritt auf, wenn der Compiler irrtümlicherweise falschen Code erzeugt, der zum Absturz Ihrer Anwendung zur Laufzeit führt. Stattdessen sollte er korrekten Code generieren oder ein Problem zur Kompilierzeit erkennen. Wenn Sie der Ansicht sind, dass das aufgetretene Problem zur Generierung von fehlerhaftem Code führt, erstellen Sie Ihren Bericht analog zu [ Back-End-Absturz (Codegenerierung)](#backend-code-generation-crash).

Stellen Sie für diese Art von Absturz eine [Linkreproduktion](#link-repros) bereit, wenn Sie das Befehlszeilenargument **/GL** für „cl.exe“ verwenden. Andernfalls stellen Sie eine [vorverarbeitete Reproduktion](#preprocessed-repros) bereit.

## <a name="how-to-generate-a-repro"></a>Generieren einer Reproduktion

Eine [gute Reproduktion](#what-makes-a-good-repro) ist entscheidend, damit wir die Quelle des Problems ermitteln können. Bevor Sie einen der im Folgenden beschriebenen Schritte für bestimmte Arten von Reproduktionen ausführen, versuchen Sie, den Code, der das Problem veranschaulicht, so weit wie möglich zu reduzieren. Versuchen Sie, Abhängigkeiten, erforderliche Header und Bibliotheken so weit wie möglich zu vermeiden. Beschränken Sie die verwendeten Compileroptionen und Präprozessordefinitionen, wenn möglich.

Es folgenden Anweisungen zum Generieren der verschiedenen Arten von Reproduktionen, mit deren Hilfe Sie verschiedene Arten von Problemen melden.

### <a name="preprocessed-repros"></a>Vorverarbeitete Reproduktionen

Eine *vorverarbeitete Reproduktion* ist eine einzelne Quelldatei, die ein Problem veranschaulicht. Sie wird aus der Ausgabe des C-Präprozessors generiert. Um eine solche Datei zu erstellen, verwenden Sie die Compileroption **/P** in der ursprünglichen Quelldatei für die Reproduktion. Diese Option fügt die enthaltenen Header inline ein, um Abhängigkeiten von zusätzlichen Quell- und Headerdateien zu entfernen. Die Option löst auch Makros, bedingte #ifdef-Anweisungen und andere Präprozessorbefehle auf, für die eine Abhängigkeit von Ihrer lokalen Umgebung bestehen könnte.

> [!NOTE]
> Vorverarbeitete Reproduktionen sind für Probleme nicht besonders nützlich, die das Ergebnis von Fehlern der Implementierung unserer Standardbibliothek sein können, da die neueste in Bearbeitung befindliche Implementierung häufig ausgetauscht wird, um zu prüfen, ob das Problem bereits behoben wurde. Führen Sie in diesem Fall keine Vorverarbeitung der Reproduktion aus. Wenn Sie das Problem nicht zu einer einzelne Quelldatei reduzieren können, packen Sie Ihren Code in eine ZIP-Datei o.ä., oder erwägen Sie eine IDE-Projektreproduktion. Weitere Informationen finden Sie unter [Andere Reproduktionen](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>So erfolgt die Vorverarbeitung einer Quellcodedatei

1. Erfassen Sie die Befehlszeilenargumente, die zum Erstellen Ihrer Reproduktion verwendet wurden, wie unter [So melden Sie den Inhalt der Befehlszeile](#to-report-the-contents-of-the-command-line) beschrieben.

1. Öffnen Sie die **Developer-Eingabeaufforderung**, die der Version von Visual Studio entspricht, und die Konfigurationsarchitektur, die zum Erstellen Ihres Projekts verwendet wurde.

1. Wechseln Sie zu dem Verzeichnis, das die Reproduktion Ihres Projekts enthält.

1. Geben Sie im Konsolenfenster der Developer-Eingabeaufforderung den Befehl **cl /P***Argumente* *Dateiname.cpp* ein. Verwenden Sie die oben erfasste Liste der Argumente als *Argumente*. *Dateiname.cpp* ist der Name Ihrer Reproduktionsquelldatei. Dieser Befehl repliziert die Befehlszeile, die Sie für die Reproduktion verwendet haben, beendet jedoch die Kompilierung nach dem Durchlauf des Präprozessors. Dann schreibt der Befehl den vorverarbeiteten Quellcode in die Datei *Dateiname.i*.

Wenn Sie eine C++- oder CX-Quellcodedatei vorverarbeiten oder das Feature „C++-Module“ verwenden, sind einige zusätzliche Schritte erforderlich. Weitere Informationen finden Sie in den folgenden Abschnitten.

Nachdem Sie die vorverarbeitete Datei generiert haben, sollten Sie sicherstellen, dass das Problem immer noch reproduziert wird, wenn Sie die vorverarbeitete Datei kompilieren.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>So bestätigen Sie, dass die vorverarbeitete Datei den Fehler weiterhin reproduziert

1. Geben Sie im Konsolenfenster der Developer-Eingabeaufforderung den Befehl **cl** *Argumente* **/TP** *Dateiname.i* ein, um „cl.exe“ anzuweisen, die vorverarbeitete Datei als C++-Quelldatei zu kompilieren. Diese *Argumente* sind die gleichen wie oben erfasst, aber ohne die Argumente **/D** und **/I**. Das liegt daran, dass diese bereits in der vorverarbeiteten Datei enthalten waren. *Dateiname.i* ist der Name Ihrer vorverarbeiteten Datei.

1. Vergewissern Sie sich, dass das Problem reproduziert wird.

Fügen Sie Ihrem Bericht schließlich die vorverarbeitete Reproduktion (*Dateiname*.i) an.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Vorverarbeitete C++/CX WinRT/UWP-Codereproduktionen

Wenn Sie C++ oder CX verwenden, um Ihre ausführbare Datei zu erstellen, sind einige zusätzliche Schritte erforderlich, um eine vorverarbeitete Reproduktion zu erstellen und zu überprüfen.

#### <a name="to-preprocess-ccx-source-code"></a>Vorverarbeiten von C++/CX-Quellcode

1. Erstellen Sie wie unter [To preprocess a source code file (Vorverarbeiten einer Quellcodedatei)](#to-preprocess-a-source-code-file) beschrieben eine vorverarbeitete Quelldatei.

1. Durchsuchen Sie die Datei _Dateiname_.i nach **#using-Direktiven**.

1. Erstellen Sie eine Liste aller Dateien, auf die verwiesen wird. Lassen Sie alle Windows\*.winmd- und platform.winmd-Dateien sowie „mscorlib.dll“ aus.

Wenn Sie überprüfen möchten, ob die vorverarbeitete Datei das Problem immer noch reproduziert,

1. erstellen Sie ein neues Verzeichnis für die vorverarbeitete Datei, und kopieren Sie sie in das neue Verzeichnis.

1. Kopieren Sie die WINMD-Dateien aus Ihrer **#using-Liste** in das neue Verzeichnis.

1. Erstellen Sie eine leere vccorlib.h-Datei im neuen Verzeichnis.

1. Bearbeiten Sie die vorverarbeitete Datei, um alle **#using-Direktiven** für „mscorlib.dll“ zu entfernen.

1. Bearbeiten Sie die vorverarbeitete Datei, um alle absoluten Pfade in die reinen Dateinamen der kopierten WINMD-Dateien zu ändern.

Überprüfen Sie wie zuvor, dass die vorverarbeitete Datei das Problem immer noch reproduziert.

### <a name="preprocessed-c-modules-repros"></a>Reproduktionen vorverarbeiteter C++-Module

Wenn Sie das Modulfeature des C++-Compilers verwenden, sind verschiedene Schritte erforderlich, um eine vorverarbeitete Reproduktion zu erstellen und zu überprüfen.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Vorverarbeiten einer Quellcodedatei, die ein Modul verwendet

1. Erfassen Sie die Befehlszeilenargumente, die zum Erstellen Ihrer Reproduktion verwendet wurden, wie unter [So melden Sie den Inhalt der Befehlszeile](#to-report-the-contents-of-the-command-line) beschrieben.

1. Öffnen Sie die **Developer-Eingabeaufforderung**, die der Version von Visual Studio entspricht, und die Konfigurationsarchitektur, die zum Erstellen Ihres Projekts verwendet wurde.

1. Wechseln Sie zu dem Verzeichnis, das die Reproduktion Ihres Projekts enthält.

1. Geben Sie im Konsolenfenster der Developer-Eingabeaufforderung den Befehl **cl /P***Argumente* *Dateiname.cpp* ein. Die *Argumente* sind die oben erfassten Argumente, und *Dateiname.cpp* ist der Name der Quelldatei, die das Modul nutzt.

1. Ändern Sie das Verzeichnis, das das Reproduktionsprojekt enthält, das die Modulschnittstelle (die IFC-Ausgabe) erstellt hat.

1. Erfassen Sie die Befehlszeilenargumente, die zum Erstellen der Modulschnittstelle verwendet wurden.

1. Geben Sie im Konsolenfenster der Developer-Eingabeaufforderung den Befehl **cl /P** *Argumente* *Modulname.ixx* ein. Die *Argumente* sind die oben erfassten Argumente, und *Modulname.ixx* ist der Name der Datei, die die Modulschnittstelle nutzt.

Nachdem Sie die vorverarbeitete Datei generiert haben, sollten Sie sicherstellen, dass das Problem immer noch reproduziert wird, wenn Sie die vorverarbeitete Datei verwenden.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>So bestätigen Sie, dass die vorverarbeitete Datei den Fehler weiterhin reproduziert

1. Wechseln Sie im Fenster der Entwicklerkonsole zu dem Verzeichnis, das die Reproduktion Ihres Projekts enthält.

1. Geben Sie wie zuvor den Befehl **cl** *Argumente* **/TP** *Dateiname*.i ein, um die vorverarbeitete Datei so zu kompilieren, als wäre sie eine C++-Quelldatei.

1. Überprüfen Sie wie zuvor, dass die vorverarbeitete Datei das Problem immer noch reproduziert.

Fügen Sie die vorverarbeiteten Reproduktionsdateien (*Dateiname*.i und *Modulname*.i) schließlich zusammen mit der IFC-Ausgabe Ihrem Bericht hinzu.

### <a name="link-repros"></a>Linkreproduktionen

Bei einer *Linkreproduktion* handelt es sich um die vom Linker generierten Inhalte eines Verzeichnisses, die entweder von der Umgebungsvariable **link\_repro** oder als Argument für die Linkeroption [/LINKREPRO](../build/reference/linkrepro.md) angegeben werden. Sie enthält Buildartefakte, die zusammen ein Problem veranschaulichen, das zur Verknüpfungszeit auftritt. Beispiele hierfür sind Back-End-Abstürze, bei denen die Link-Zeitcodegenerierung involviert ist, oder Linkerabstürze. Diese Buildartefakte werden in Form von Linkereingaben benötigt, damit das Problem reproduziert werden kann. Mit dieser Umgebungsvariable lässt sich eine Linkreproduktion ganz einfach erstellen. Sie aktiviert die integrierte Funktion des Linkers zum Generieren einer Reproduktion.

#### <a name="to-generate-a-link-repro-using-the-link_repro-environment-variable"></a>So generieren Sie eine Linkreproduktion mithilfe der Umgebungsvariablen „link_repro“

1. Erfassen Sie die Befehlszeilenargumente, die zum Erstellen Ihrer Reproduktion verwendet wurden, wie unter [So melden Sie den Inhalt der Befehlszeile](#to-report-the-contents-of-the-command-line) beschrieben.

1. Öffnen Sie die **Developer-Eingabeaufforderung**, die der Version von Visual Studio entspricht, und die Konfigurationsarchitektur, die zum Erstellen Ihres Projekts verwendet wurde.

1. Wechseln Sie im Konsolenfenster der Developer-Eingabeaufforderung zu dem Verzeichnis, das die Reproduktion Ihres Projekts enthält.

1. Geben Sie **mkdir linkrepro** ein, um ein Verzeichnis mit dem Namen *linkrepro* für die Linkreproduktion zu erstellen. Sie können auch einen anderen Namen verwenden, um eine andere Linkreproduktion zu erfassen.

1. Geben Sie den Befehl **set link\_repro=linkrepro** ein, um die Umgebungsvariable **link\_repro** auf das Verzeichnis festzulegen, das Sie erstellt haben. Wenn Ihr Build von einem anderen Verzeichnis aus ausgeführt wird, was bei komplexeren Projekten häufig der Fall ist, sollten Sie für **link\_repro** stattdessen den vollständigen Pfad zu Ihrem Verzeichnis für die Linkreproduktion festlegen.

1. Geben Sie im Konsolenfenster der Developer-Eingabeaufforderung den Befehl **devenv** ein, um das reproduzierte Projekt in Visual Studio zu erstellen. So wird sichergestellt, dass der Wert der Umgebungsvariablen **link\_repro** für Visual Studio sichtbar ist. Verwenden Sie zum Erstellen des Projekts über die Befehlszeile die oben erfassten Befehlszeilenargumente, um den reproduzierten Build zu duplizieren.

1. Erstellen Sie das reproduzierte Projekt, und vergewissern Sie sich, dass das erwartete Problem aufgetreten ist.

1. Wenn Sie Visual Studio für den Build verwendet haben, schließen Sie das Programm.

1. Geben Sie im Konsolenfenster der Developer-Eingabeaufforderung den Befehl **set link\_repro=** ein, um die Umgebungsvariable **link\_repro** zu löschen.

Packen Sie abschließend die Reproduktion, indem Sie das gesamte Verzeichnis für die Linkreproduktion in eine ZIP-Datei o.ä. komprimieren, und fügen Sie diese an Ihren Bericht an.

Die Linkeroption **/LINKREPRO** hat dieselbe Auswirkung wie die Umgebungsvariable **link\_repro**. Sie können die Option [/LINKREPROTARGET](../build/reference/linkreprotarget.md) verwenden, um den Namen anzugeben, nach dem für die generierte Linkreproduktion gefiltert werden soll. Damit Sie die Option **/LINKREPROTARGET** verwenden können, müssen Sie außerdem die Linkeroption **/OUT** angeben.

#### <a name="to-generate-a-link-repro-using-the-linkrepro-option"></a>So generieren Sie eine Linkreproduktion mithilfe der Option /LINKREPRO

1. Erstellen Sie ein Verzeichnis für die Linkreproduktion. Im Folgenden wird der von Ihnen erstellte vollständige Verzeichnispfad als _directory-path_ bezeichnet. Setzen Sie den Pfad in doppelte Anführungszeichen, wenn er Leerzeichen enthält.

1. Fügen Sie der Linkerbefehlszeile den Befehl **/LINKREPRO:** _directory-path_ hinzu. Öffnen Sie in Visual Studio das Dialogfeld **Eigenschaftenseiten** für Ihr Projekt. Klicken Sie auf der Eigenschaftenseite auf **Konfigurationseigenschaften** > **Linker** > **Befehlszeile**. Geben Sie anschließend in das Feld **Zusätzliche Optionen** die Option **/LINKREPRO:** _directory-path_ ein. Klicken Sie auf **OK**, um die Änderungen zu speichern.

1. Erstellen Sie das reproduzierte Projekt, und vergewissern Sie sich, dass das erwartete Problem aufgetreten ist.

Packen Sie abschließend die Reproduktion, indem Sie das gesamte Verzeichnis der Linkreproduktion (_directory-path_) in eine ZIP-Datei o.ä. komprimieren, und fügen Sie diese an Ihren Bericht an.

### <a name="other-repros"></a>Andere Reproduktionen

Wenn Sie das Problem nicht auf eine einzelne Quelldatei oder vorverarbeitete Reproduktion reduzieren können und das Problem keine Linkreproduktion erfordert, können wir ein IDE-Projekt untersuchen. Alle Hinweise zum Erstellen einer sinnvollen Reproduktion gelten immer noch: Der Code sollte minimal und eigenständig sein. Das Problem sollte in unseren neuesten Tools auftreten und ggf. in anderen Compilern nicht zu beobachten sein.

Erstellen Sie Ihre Reproduktion als minimales IDE-Projekt, und erstellen Sie dann ein Paket, indem Sie die gesamte Verzeichnisstruktur in einer ZIP-Datei o.ä. komprimieren und diese an Ihren Bericht anfügen.

## <a name="ways-to-send-your-report"></a>Möglichkeiten zum Senden Ihres Berichts

Sie haben mehrere gute Möglichkeiten, uns Ihren Bericht zu übermitteln. Die können das in Visual Studio integrierte Tool [Ein Problem melden](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) oder die Seite der [Visual Studio-Entwicklercommunity]( https://aka.ms/feedback/report?space=62) verwenden. Unten auf dieser Seite finden Sie auch eine Schaltfläche **Produktfeedback**. Diese Entscheidung richtet sich danach, ob Sie die integrierten Tools in der IDE verwenden möchten, um Screenshots zu erfassen und Ihren Bericht zu organisieren. Wenn Sie dies nicht möchten, können Sie direkt die Website der Developer Community nutzen.

> [!NOTE]
> Unabhängig davon, wie Sie den Bericht senden, respektiert Microsoft Ihre Privatsphäre. Microsoft verpflichtet sich der Einhaltung aller Datenschutzgesetze- und regeln. Informationen dazu, wie wir Daten behandeln, die Sie uns senden, finden Sie in der [Datenschutzerklärung von Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="use-the-report-a-problem-tool"></a>Nutzen des Tools „Problem melden“

Das Tool **Problem melden** in Visual Studio bietet Benutzern von Visual Studio die Möglichkeit, Probleme mit einigen wenigen Mausklicks zu melden. Das Tool zeigt ein einfaches Formular an, in dem Sie detaillierte Informationen zu einem gefundenen Problem senden können. Sie können diesen Bericht dann senden, ohne die IDE verlassen zu müssen.

Es ist einfach und praktisch, von der IDE aus ein Problem über das Tool **Problem melden** zu melden. Sie können über die Titelleiste darauf zugreifen, indem Sie auf das Symbol **Feedback senden** neben dem Suchfeld **Schnellstart** klicken. Alternativ dazu finden Sie das Tool auf der Menüleiste unter **Hilfe** > **Feedback senden** > **Problem melden**.

Wenn Sie ein Problem melden möchten, suchen Sie zunächst in der Developer Community nach ähnlichen Problemen. Wenn das Problem bereits zuvor gemeldet wurde, stimmen Sie für den entsprechenden Bericht ab, und fügen Sie Kommentare mit zusätzlichen Einzelheiten hinzu. Wenn Sie kein Problem dieser Art finden, klicken Sie auf die Schaltfläche **Neues Problem melden** am Ende des Feedbackdialogfelds von Visual Studio, und befolgen Sie die Schritte, um Ihr Problem einzureichen.

### <a name="use-the-visual-studio-developer-community-pages"></a>Verwenden Sie die Seiten der Visual Studio Developer Community

Die Seiten der Visual Studio Developer Community bietet eine weitere einfache Möglichkeit zum Melden von Problemen und zum Finden von Lösungen für Visual Studio und den C++-Compiler, für Tools und für Bibliotheken. Es gibt spezifische Entwicklercommunityseiten für [Visual Studio](https://aka.ms/feedback/report?space=8), [Visual Studio für Mac](https://aka.ms/feedback/report?space=41), [.NET](https://aka.ms/feedback/report?space=61), [C++](https://aka.ms/feedback/report?space=62), [Azure DevOps](https://aka.ms/feedback/report?space=21) und [Azure DevOps Server](https://aka.ms/feedback/report?space=22).

Unterhalb der Communityregisterkarten (am oberen Rand jeder Seite) befindet sich ein Suchfeld. Mit diesem Feld können Sie Beiträge suchen, die Probleme ähnlich dem Ihrem melden. Möglicherweise sind Lösungen oder andere nützliche Informationen bezüglich Ihres Problems bereits vorhanden. Wenn jemand zuvor das gleiche Problem gemeldet hat, stimmen Sie für den entsprechenden Bericht ab, und kommentieren Sie ihn, anstatt einen neuen Problembericht zu erstellen. Wenn Sie einen Bericht kommentieren, für einen Bericht abstimmen oder ein neues Problem melden möchten, werden Sie möglicherweise aufgefordert, sich bei Ihrem Visual Studio-Konto anzumelden. Bei der ersten Anmeldung müssen Sie der Developer Community-App Zugriff auf Ihr Profil gewähren.

Durchsuchen Sie bei Problemen mit dem C++-Compiler, dem Linker und anderen Tools und Bibliotheken zuerst die Seite der [C++-Entwicklercommunity](https://aka.ms/vsfeedback/browsecpp). Wenn Sie nach Ihrem Problem suchen und es noch nicht gemeldet wurde, wählen Sie die Schaltfläche **Problem melden** neben dem Suchfeld aus. Sie können Ihren Reproduktionscode und die Befehlszeile sowie Screenshots, Links zu ähnlichen Diskussionen oder andere Informationen hinzufügen, die Sie für relevant und nützlich halten.

> [!TIP]
> Für andere Arten von Problemen, die möglicherweise in Visual Studio auftreten, jedoch nicht mit dem C++-Toolset zusammenhängen (z.B. Benutzeroberflächenprobleme, defekte IDE-Funktionalität oder allgemeine Abstürze), verwenden Sie das Tool **Problem melden** in der IDE. Dies ist die beste Wahl, da das Tool über Screenshotfunktionen verfügt und Benutzeroberflächenaktionen aufzeichnen kann, die zu dem aufgetretenen Problem geführt haben. Für diese Art von Fehlern können Sie auch auf der Website der [Visual Studio-Entwicklercommunity](https://aka.ms/feedback/report?space=8) nach Lösungsvorschlägen suchen. Weitere Informationen finden Sie unter [Melden eines Problems mit Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="reports-and-privacy"></a>Berichte und Datenschutz

**Alle Informationen in Berichten sowie alle Kommentare und Antworten sind standardmäßig öffentlich sichtbar**. Dies ist in der Regel ein Vorteil, da die gesamte Community Einblicke in die Probleme, Lösungen und Problemumgehungen anderer Benutzer hat. Wenn Sie Ihre Daten oder Ihre Identität jedoch aus Gründen des Datenschutzes oder des geistigen Eigentums nicht veröffentlichen möchten, gibt es Optionen, die Sie nutzen können.

Wenn Sie Ihre Identität nicht offenlegen möchten, [erstellen Sie ein neues Microsoft-Konto](https://signup.live.com/), das keine personenbezogenen Informationen enthält. Verwenden Sie dieses Konto, um Ihren Bericht zu erstellen.

**Fügen Sie keine Informationen, die privat bleiben sollen, in den Titel oder den Inhalt des ursprünglichen Berichts ein, denn dieser ist öffentlich.** Geben Sie stattdessen an, dass Sie Details privat in einem separaten Kommentar senden. Wenn Sie sicherstellen möchten, dass für Ihren Bericht die richtige Zielgruppe festgelegt ist, sollten Sie **cppcompiler** in die Themenliste des Problemberichts einfügen. Sobald der Problembericht erstellt ist, können Sie festlegen, wer Ihre Antworten und Anlagen anzeigen kann.

#### <a name="to-create-a-problem-report-for-private-information"></a>Erstellen eines Problemberichts für private Informationen

1. Klicken Sie im erstellten Bericht auf **Kommentar hinzufügen**, um eine private Beschreibung des Problems zu erstellen.

1. Verwenden Sie im Antwort-Editor das Dropdown-Steuerelement unter den Schaltflächen **Senden** und **Abbrechen**, um die Zielgruppe für Ihre Antwort festzulegen. Nur die angegebenen Personen können die privaten Antworten sowie enthaltene Bilder, Links und Code anzeigen. Wählen Sie **Viewable by moderators and the original poster** (Sichtbar für Moderatoren und den Verfasser) aus, um die Sichtbarkeit auf Microsoft-Mitarbeiter und sich selbst zu beschränken.

1. Fügen Sie die Beschreibung und weitere erforderliche Informationen, Bilder und Dateianlagen für die Reproduktion hinzu. Klicken Sie auf die Schaltfläche **Senden**, um diese Informationen privat zu senden.

   Für Dateianhänge sind maximal 10 Dateien mit maximal 2 GB zulässig. Fordern Sie bei größeren Uploads in einem privaten Kommentar eine Upload-URL an.

Alle Antworten unter diesem Kommentar haben die Sichtbarkeit, die Sie angegeben haben. Dies gilt auch, wenn das Dropdown-Steuerelement in Antworten den Status der eingeschränkten Sichtbarkeit nicht korrekt anzeigt.

Seien Sie sehr vorsichtig, um Ihre Privatsphäre nicht zu gefährden und Ihre vertraulichen Daten nicht öffentlich preiszugeben. Beschränken Sie alle Interaktionen mit Microsoft auf die Antworten unterhalb eines eingeschränkten Kommentars. Antworten auf andere Kommentare können dazu führen, dass Sie versehentlich vertrauliche Informationen offenlegen.

## <a name="how-to-report-a-c-documentation-issue"></a>So melden Sie einen Fehler in der C++-Dokumentation

Wir verwenden GitHub-Tickets, um Fehler in unserer Dokumentation zu erfassen. Sie können GitHub-Tickets jetzt direkt von einer Inhaltsseite aus erstellen. So können Sie besser mit Autoren und Produktteams kommunizieren. Wenn Ihnen ein Fehler (ein falsches Codebeispiel, eine verwirrende Erklärung, eine schwerwiegende Auslassung oder auch nur ein Tippfehler) in einer Dokumentation auffällt, können Sie uns ganz leicht darüber informieren. Scrollen Sie auf der Seite ganz nach unten, und klicken Sie auf **Sign in to give documentation feedback** (Anmelden und Feedback zur Dokumentation geben). Sie müssen ein GitHub-Konto einrichten, falls Sie noch keines besitzen. Wenn Sie über ein GitHub-Konto verfügen, können Sie alle Issues zu unserer Dokumentation und den zugehörigen Status anzeigen. Sie erhalten auch Benachrichtigungen, wenn an einem von Ihnen gemeldeten Issue Änderungen vorgenommen wurden. Weitere Informationen erhalten Sie unter [A New Feedback System Is Coming to docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs) (Neues Feedbacksystem auf docs.microsoft.com).

Wenn Sie die Schaltfläche „Feedback zur Dokumentation“ verwenden, erstellen Sie ein dokumentationsbezogenes Issue auf GitHub. Im Issue werden automatisch einige Informationen zu der Seite ausgefüllt, auf der Sie das Issue erstellen. Auf diese Weise erfahren wir, wo das Problem besteht, bearbeiten Sie daher diese Informationen nicht. Fügen Sie nur Angaben zu dem Problem hinzu. Wenn Sie möchten, können Sie auch einen Vorschlag zur Fehlerbehebung machen. [Unsere C++-Dokumente sind Open Source](https://github.com/MicrosoftDocs/cpp-docs/) – wenn Sie also selbst eine Fehlerbehebung einreichen möchten, können Sie dies tun. Weitere Informationen zum Beitragen zur Dokumentation finden Sie im [Leitfaden für Mitwirkende](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) auf GitHub.
