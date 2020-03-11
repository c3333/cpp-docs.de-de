---
title: Multithreading bei C und Win32
ms.date: 08/09/2019
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
ms.openlocfilehash: 1764561e0b2b43b8a89d8a1eb2e85d84ce33c4fc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867052"
---
# <a name="multithreading-with-c-and-win32"></a>Multithreading bei C und Win32

Der Microsoft C/C++ Compiler (MSVC) bietet Unterstützung für das Erstellen von Multithreadanwendungen. Ziehen Sie die Verwendung mehrerer Threads in Erwägung, wenn Ihre Anwendung teure Vorgänge ausführen muss, die dazu führen, dass die Benutzeroberfläche nicht mehr reagiert.

Mit MSVC gibt es mehrere Möglichkeiten, mit mehreren Threads zu programmieren: Sie können C++/WinRT und die Windows-Runtime-Bibliothek, die MFC-Bibliothek (Microsoft Foundation Class C++),/CLI und die .NET-Laufzeit oder die C-Lauf Zeit Bibliothek und die Win32-API verwenden. In diesem Artikel geht es um Multithreading in C. Beispielcode finden Sie unter [Sample Multithread Program in C](sample-multithread-c-program.md).

## <a name="multithread-programs"></a>Multithreadprogramme

Ein Thread ist im Grunde ein Ausführungs Pfad durch ein Programm. Es ist auch die kleinste Ausführungs Einheit, die Win32 plant. Ein Thread besteht aus einem Stapel, dem Status der CPU-Register und einem Eintrag in der Ausführungs Liste des System Planers. Jeder Thread nutzt alle Ressourcen des Prozesses.

Ein Prozess besteht aus einem oder mehreren Threads und dem Code, den Daten und anderen Ressourcen eines Programms im Arbeitsspeicher. Typische Programmressourcen sind geöffnete Dateien, Semaphoren und dynamisch zugeordneter Speicher. Ein Programm wird ausgeführt, wenn der Systemplaner eine seiner Threads zur Ausführungs Steuerung übergibt. Der Planer bestimmt, welche Threads ausgeführt werden sollen und wann Sie ausgeführt werden sollen. Threads mit niedrigerer Priorität müssen möglicherweise warten, bis Threads mit höherer Priorität ihre Aufgaben erfüllen. Auf Multiprozessorcomputern kann der Planer einzelne Threads auf verschiedene Prozessoren verschieben, um die CPU-Last auszugleichen.

Jeder Thread in einem Prozess wird unabhängig voneinander betrieben. Wenn Sie Sie nicht untereinander sichtbar machen, werden die Threads einzeln ausgeführt, und die anderen Threads in einem Prozess sind nicht sichtbar. Threads, die gemeinsame Ressourcen gemeinsam nutzen, müssen jedoch ihre Arbeit mithilfe von Semaphoren oder einer anderen Methode der prozessübergreifenden Kommunikation koordinieren. Weitere Informationen zum Synchronisieren von Threads finden Sie unter [Schreiben eines multithreadwin32-Programms](#writing-a-multithreaded-win32-program).

## <a name="library-support-for-multithreading"></a>Bibliotheksunterstützung für Multithreading

Alle Versionen der CRT unterstützen jetzt Multithreading, mit Ausnahme der nicht Sperr Versionen einiger Funktionen. Weitere Informationen finden Sie unter [Leistung von Multithreadbibliotheken](../c-runtime-library/multithreaded-libraries-performance.md). Informationen zu den Versionen der CRT, die zum Verknüpfen mit Ihrem Code verfügbar sind, finden Sie unter [Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md).

## <a name="include-files-for-multithreading"></a>Includedateien für Multithreading

Standard-CRT-Includedateien deklarieren die C-Lauf Zeit Bibliotheksfunktionen, wenn Sie in den Bibliotheken implementiert werden. Wenn die Compileroptionen die [__fastcall oder __vectorcall](../build/reference/gd-gr-gv-gz-calling-convention.md) Aufruf Konventionen angeben, geht der Compiler davon aus, dass alle Funktionen mit der Register-Aufruf Konvention aufgerufen werden sollten. Die Lauf Zeit Bibliotheksfunktionen verwenden die C-Aufruf Konvention, und die Deklarationen in den standardmäßigen Includedateien teilen dem Compiler mit, dass korrekte externe Verweise auf diese Funktionen generiert werden.

## <a name="crt-functions-for-thread-control"></a>CRT-Funktionen für die Thread Steuerung

Alle Win32-Programme weisen mindestens einen Thread auf. Jeder Thread kann zusätzliche Threads generieren. Ein Thread kann seine Aufgabe schnell abschließen oder während der gesamten Lebensdauer eines Programms aktiv bleiben.

Die CRT-Bibliotheken stellen die folgenden Funktionen für die Thread Erstellung und-Beendigung bereit: [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md), [_endthread und _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).

Mit der `_beginthread`-Funktion und der `_beginthreadex`-Funktion wird ein neuer Thread erstellt; wenn der Vorgang erfolgreich war, wird ein Threadbezeichner zurückgegeben. Der Thread wird automatisch beendet, wenn die Ausführung abgeschlossen ist. Oder es kann mit einem `_endthread`-oder `_endthreadex`-Aufrufvorgang beendet werden.

> [!NOTE]
> Wenn Sie C-Lauf Zeit Routinen aus einem Programm, das mit "LIBCMT. lib" erstellt wurde, aufgerufen werden, müssen Sie die Threads mit der `_beginthread`-oder `_beginthreadex`-Funktion starten. Verwenden Sie nicht die Win32-Funktionen `ExitThread` und `CreateThread`. Bei der Verwendung von `SuspendThread` tritt möglicherweise ein Deadlock auf, wenn mehrere blockierte Threads darauf warten, dass der unterbrochene Thread den Zugriffsvorgang auf eine C-Laufzeitdatenstruktur abschließt.

### <a name="_core_the__beginthread_function"></a>Die Funktionen _beginthread und _beginthreadex

Die `_beginthread`-Funktion und die `_beginthreadex`-Funktion erstellen einen neuen Thread. Ein Thread nutzt den Code und die Datensegmente eines Prozesses gemeinsam mit anderen Threads in diesem Prozess, verfügt jedoch über eigene, eindeutige Registerwerte, Stapelspeicher und eine aktuelle Anweisungsadresse. Das System weist jedem Thread seine bestimmte CPU-Zeit zu, damit alle Threads in einem Prozess gleichzeitig ausgeführt werden können.

`_beginthread` und `_beginthreadex` ähneln [der Funktion "Funktion in der Win32](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) -API", haben jedoch folgende Unterschiede:

- Sie initialisieren bestimmte Variablen der C-Laufzeitbibliothek. Dies ist nur wichtig, wenn Sie die C-Lauf Zeit Bibliothek in ihren Threads verwenden.

- Mit `CreateThread` können Sicherheitsattribute gesteuert werden. Mit dieser Funktion können Sie einen Thread starten, der sich im angehaltenen Status befindet.

`_beginthread` und `_beginthreadex` geben ein Handle für den neuen Thread zurück, wenn der Vorgang erfolgreich war. Bei einem Fehler wird ein Fehlercode zurückgegeben.

### <a name="_core_the__endthread_function"></a>Die Funktionen _endthread und _endthreadex

Die [_endthread](../c-runtime-library/reference/endthread-endthreadex.md) -Funktion beendet einen von `_beginthread` erstellten Thread (und ähnlich `_endthreadex` beendet einen von `_beginthreadex`erstellten Thread). Threads werden automatisch beendet, wenn sie abgeschlossen sind. `_endthread` und `_endthreadex` sind zum bedingten Beenden aus einem Thread heraus sinnvoll. Ein für die Kommunikationsverarbeitung verantwortlicher Thread kann z. B. seine Aktivität einstellen, wenn die Steuerung des Kommunikationsanschlusses derzeit nicht möglich ist.

## <a name="writing-a-multithreaded-win32-program"></a>Schreiben von Win32-Multithreadprogrammen

Wenn Sie ein Programm mit mehreren Threads schreiben, müssen Sie das Verhalten und [die Verwendung der Programmressourcen](#_core_sharing_common_resources_between_threads)koordinieren. Stellen Sie außerdem sicher, dass jeder Thread [seinen eigenen Stapel](#_core_thread_stacks)erhält.

### <a name="_core_sharing_common_resources_between_threads"></a>Gemeinsame Nutzung allgemeiner Ressourcen zwischen Threads

> [!NOTE]
> Eine ähnliche Erörterung in der MFC-Sicht finden Sie unter [Multithreading: Programmiertipps](multithreading-programming-tips.md) und [Multithreading: Verwendungsweise der Synchronisierungs Klassen](multithreading-when-to-use-the-synchronization-classes.md).

Jeder Thread verfügt über einen eigenen Stapel und eine eigene Kopie der CPU-Register. Andere Ressourcen, z. B. Dateien, statische Daten und Heapspeicher, werden von allen Threads im Prozess gemeinsam genutzt. Threads, die diese gemeinsamen Ressourcen verwenden, müssen synchronisiert werden. Win32 bietet verschiedene Möglichkeiten zur Synchronisierung von Ressourcen, einschließlich Semaphore, kritischen Abschnitten, Ereignissen und Mutexen.

Wenn mehrere Threads auf statische Daten zugreifen, muss das Programm mögliche Ressourcenkonflikte verarbeiten können. Stellen Sie sich ein Programm vor, bei dem ein Thread eine statische Datenstruktur mit *x*-und*y* -Koordinaten für Elemente aktualisiert, die von einem anderen Thread angezeigt werden. Wenn der Aktualisierungs Thread die *x* -Koordinate ändert und vor dem Ändern der *y* -Koordinate vorzeitig entfernt wird, kann der Anzeige Thread vor der Aktualisierung der *y* -Koordinate geplant werden. In diesem Fall wird das Element an der falschen Stelle angezeigt. Durch die Verwendung von Semaphore zur Steuerung des Zugriffs auf die Struktur können Sie dieses Problem vermeiden.

Ein Mutex (Short für *Mut*Benutzer Zugriffs Protokollierung *Ex*clusion) ist eine Möglichkeit, zwischen Threads oder Prozessen zu kommunizieren, die asynchron voneinander ausgeführt werden. Diese Kommunikation kann verwendet werden, um die Aktivitäten mehrerer Threads oder Prozesse zu koordinieren, in der Regel durch Steuern des Zugriffs auf eine freigegebene Ressource durch Sperren und Entsperren der Ressource. Um dieses *x*,*y* -Koordinaten Update Problem zu lösen, legt der Update Thread einen Mutex fest, der angibt, dass die Datenstruktur verwendet wird, bevor das Update durchgeführt wird. Nach Verarbeitung der beiden Koordinaten wird der Mutex aufgehoben. Der Anzeigethread muss abwarten, bis der Mutex aufgehoben ist, bevor er die Anzeige aktualisieren kann. Dieser Prozess des Wartens auf einen Mutex wird häufig als *Blockierung* für einen Mutex bezeichnet, da der Prozess blockiert ist und nicht fortgesetzt werden kann, bis der Mutex gelöscht wird.

Das im [Beispiel-Multithread-c-Programm](sample-multithread-c-program.md) angezeigte Bounce. c-Programm verwendet einen Mutex mit dem Namen `ScreenMutex`, um Bildschirm Aktualisierungen zu koordinieren. Jedes Mal, wenn einer der Anzeigethreads zum Schreiben auf den Bildschirm bereit ist, ruft er `WaitForSingleObject` mit dem Handle für `ScreenMutex` und konstant unendlich auf, um anzugeben, dass der `WaitForSingleObject` Aufruf den Mutex blockieren sollte und kein Timeout. Wenn `ScreenMutex` eindeutig ist, legt die wait-Funktion den Mutex fest, damit andere Threads die Anzeige nicht beeinträchtigen können und die Ausführung des Threads fortgesetzt wird. Ansonsten wird der Thread solange blockiert, bis der Mutex aufgehoben wird. Wenn der Thread die Anzeige Aktualisierung abschließt, wird der Mutex durch Aufrufen von `ReleaseMutex`freigegeben.

Bildschirmaktualisierungen und statische Daten sind nur zwei der Ressourcen, bei deren Verwaltung mit Bedacht vorgegangen werden muss. Ein Programm verfügt möglicherweise über mehrere Threads, die auf dieselbe Datei zugreifen. Da durch einen anderen Thread möglicherweise der Dateizeiger verschoben wurde, muss von jedem Thread vor dem Lese- oder Schreibvorgang der Dateizeiger zurückgesetzt werden. Außerdem muss jeder Thread sicherstellen, dass er zwischen dem Zeitpunkt, an dem er den Zeiger positioniert, und dem Zeitpunkt, zu dem er auf die Datei zugreift, nicht vorzeitig entfernt wird. Diese Threads sollten eine Semaphor verwenden, um den Zugriff auf die Datei zu koordinieren, indem Sie die einzelnen Datei Zugriffe mit `WaitForSingleObject`-und `ReleaseMutex` aufrufen durchführen. Diese Vorgehensweise wird anhand des folgenden Codefragments erläutert:

```C
HANDLE    hIOMutex = CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

### <a name="_core_thread_stacks"></a>Thread Stapel

Der gesamte standardmäßige Stapelspeicher einer Anwendung ist für den ersten Ausführungsthread belegt, der als Thread 1 bezeichnet wird. Folglich müssen Sie für jeden von einem Programm zusätzlich benötigten Thread angeben, wie viel mehr Speicherplatz für einen separaten Stapel belegt werden soll. Das Betriebssystem ordnet dem Thread bei Bedarf zusätzlichen Stapelspeicher zu, Sie müssen jedoch einen Standardwert angeben.

Das erste Argument im `_beginthread`-Aufrufe ist ein Zeiger auf die `BounceProc`-Funktion, die die Threads ausführt. Das zweite Argument legt die Standardgröße des Stapel für den Thread fest. Das letzte Argument ist eine ID-Nummer, die an `BounceProc`übermittelt wird. `BounceProc` verwendet die ID-Nummer, um einen Ausgangswert für den Zufallszahlengenerator zu verwenden und das Farb Attribut und das Anzeige Zeichen des Threads auszuwählen.

Threads, die Aufrufe an die C-Laufzeitbibliothek oder die Win32-API richten, müssen über ausreichend Stapelspeicher für die Bibliotheks- und API-Funktionen verfügen, die von ihnen aufgerufen werden. Die C-`printf` Funktion erfordert mehr als 500 Bytes Stapel Speicher, und beim Aufrufen von Win32-API-Routinen sind 2 KB Stapel Speicher verfügbar.

Da jeder Thread über einen eigenen Stapel verfügt, können Sie potenzielle Konflikte in Bezug auf Datenelemente vermeiden, indem Sie so wenig statische Daten wie möglich verwenden. Achten Sie bei der Entwicklung eines Programms darauf, dass es automatische Stapelvariablen für alle Daten verwendet, die einem Thread zugehörig sein können. Die einzigen globalen Variablen im Bounce. c-Programm sind entweder Mutexe oder Variablen, die sich nach der Initialisierung nie ändern.

Win32 bietet auch Thread-Local Storage (TLS) zum Speichern von Thread bezogenen Daten. Weitere Informationen finden Sie unter [Thread Local Storage (TLS)](thread-local-storage-tls.md).

## <a name="avoiding-problem-areas-with-multithread-programs"></a>Vermeiden von Problembereichen bei Multithreadprogrammen

Es gibt mehrere Probleme, die beim Erstellen, verknüpfen oder Ausführen eines Multithread-C-Programms auftreten können. In der folgenden Tabelle werden einige der gängigeren Probleme beschrieben. (Eine ähnliche Erörterung in der MFC-Sicht finden Sie unter [Multithreading: Tipps](multithreading-programming-tips.md)für die Programmierung.)

|Problem|Wahrscheinliche Ursache|
|-------------|--------------------|
|Sie erhalten ein Meldungs Feld, das anzeigt, dass Ihr Programm eine Schutz Verletzung verursacht hat.|Viele Win32-Programmierfehler verursachen Schutz Verletzungen. Eine häufige Ursache für Schutz Verletzungen ist die indirekte Zuweisung von Daten zu Null-Zeigern. Da das Programm versucht, auf den Speicher zuzugreifen, der nicht zu ihm gehört, wird eine Schutz Verletzung ausgegeben.<br /><br /> Eine einfache Möglichkeit, die Ursache eines Schutz Verstoßes zu erkennen, besteht darin, das Programm mit Debuginformationen zu kompilieren und es dann über den Debugger in der Visual Studio-Umgebung auszuführen. Wenn der Schutz Fehler auftritt, überträgt Windows die Steuerung an den Debugger, und der Cursor befindet sich in der Zeile, die das Problem verursacht hat.|
|Das Programm generiert zahlreiche Kompilierungs-und Verknüpfungs Fehler.|Sie können viele potenzielle Probleme vermeiden, indem Sie die Warnstufe des Compilers auf einen der höchsten Werte und die Warnmeldungen festlegen. Mithilfe der Optionen auf Ebene 3 oder Ebene 4 Warnstufe können Sie unbeabsichtigte Datenkonvertierungen, fehlende Funktionsprototypen und die Verwendung von nicht-ANSI-Features erkennen.|

## <a name="see-also"></a>Weitere Informationen

[Multithreading-Unterstützung für älteren Code C++(Visual)](multithreading-support-for-older-code-visual-cpp.md)\
[Beispiel für ein Multithreadprogramm in C](sample-multithread-c-program.md) -\
[Thread lokaler Speicher (TLS)](thread-local-storage-tls.md)\
[Parallelität und asynchrone Vorgänge mit C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency)\
[Multithreading mit C++ und MFC](multithreading-with-cpp-and-mfc.md)
