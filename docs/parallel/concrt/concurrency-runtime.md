---
title: Concurrency Runtime
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: 84a52b8a509edad86f64c28df843e92f1441f2f0
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538656"
---
# <a name="concurrency-runtime"></a>Concurrency Runtime

Die Concurrency Runtime für C++ hilft Ihnen beim Schreiben robuster, skalierbarer und reaktionsschneller paralleler Anwendungen. Es stellt eine höhere Abstraktionsebene bereit, sodass Sie die Infrastrukturdetails im Zusammenhang mit der Parallelität nicht verwalten müssen. Sie können mit ihm außerdem Planungsrichtlinien angeben, die den Servicequalitätsforderungen Ihrer Anwendungen entsprechen. Verwenden Sie diese Ressourcen für die ersten Schritte beim Arbeiten mit der Concurrency Runtime.

Die Referenz Dokumentation finden Sie unter [Referenz](../../parallel/concrt/reference/reference-concurrency-runtime.md).

> [!TIP]
> Die Concurrency Runtime basiert stark auf C++11-Funktionen und übernimmt den moderneren C++-Stil. Weitere Informationen finden Sie unter [Willkommen zurück bei C++](../../cpp/welcome-back-to-cpp-modern-cpp.md).

## <a name="choosing-concurrency-runtime-features"></a>Auswählen von Concurrency Runtime-Funktionen

|||
|-|-|
|[Übersicht](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Erläutert die Bedeutung der Concurrency Runtime und beschreibt ihre wichtigsten Funktionen.|
|[Vergleich mit anderen Parallelitätsmodellen](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Beschreibt die Concurrency Runtime im Vergleich mit anderen Parallelitätsmodellen, z. B. dem Windows-Threadpool und OpenMP, damit Sie das Parallelitätsmodell verwenden können, das die Anforderungen Ihrer Anwendungen am besten erfüllt.|
|[Migrieren von OpenMP zur Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Vergleicht OpenMP mit der Concurrency Runtime und enthält Beispiele, in denen das Migrieren von vorhandenem OpenMP-Code für die Verwendung der Concurrency Runtime gezeigt wird.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Stellt die PPL vor, die parallele Schleifen, Aufgaben und parallele Container bereitstellt.|
|[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)|Erläutert die Verwendung von asynchronen Agents und asynchroner Nachrichtenübergabe, um auf einfache Weise Datenfluss- und Pipelineaufgaben in die Anwendungen zu integrieren.|
|[Aufgabenplanung](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Stellt den Aufgabenplaner vor, mit dem Sie die Leistung Ihrer Desktop-Apps, die die Concurrency Runtime verwenden, optimieren können.|

## <a name="task-parallelism-in-the-ppl"></a>Aufgabenparallelität in der PPL

|||
|-|-|
|[Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Gewusst wie: Verwenden von parallel_invoke zum Schreiben einer Runtime für paralleles Sortieren](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Vorgehensweise: Verwenden von parallel_invoke zum Ausführen paralleler Vorgänge](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Gewusst wie: Erstellen einer Aufgabe, die nach einer Verzögerung abgeschlossen wird](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Beschreibt Aufgaben und Aufgabengruppen, mit denen Sie asynchronen Code schreiben und parallele Arbeit in kleinere Teile zerlegen können.|
|[Exemplarische Vorgehensweise: Implementieren von Futures](../../parallel/concrt/walkthrough-implementing-futures.md)|Veranschaulicht, wie Concurrency Runtime-Funktionen kombiniert werden, um den Funktionsumfang zu erweitern.|
|[Exemplarische Vorgehensweise: Entfernen von Arbeit aus einem Benutzeroberflächenthread](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Veranschaulicht, wie die Arbeit, die vom UI-Thread in einer MFC-Anwendung ausgeführt wird, in einen Arbeitsthread verschoben wird.|
|[Bewährte Methoden in der Parallel Patterns Library](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Allgemeine bewährte Methoden für die Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Bietet Tipps und empfohlene Vorgehensweisen für das Arbeiten mit der PPL.|

## <a name="data-parallelism-in-the-ppl"></a>Datenparallelität in der PPL

|||
|-|-|
|[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Gewusst wie: Schreiben einer parallel_for-Schleife](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Gewusst wie: Schreiben einer parallel_for_each-Schleife](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Gewusst wie: Paralleles Ausführen von Zuordnungs- und Reduzierungsoperationen](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Beschreibt `parallel_for`, `parallel_for_each`, `parallel_invoke`und andere parallele Algorithmen. Verwenden Sie parallele Algorithmen, um Probleme mit *Datenparallelität* im Zusammenhang mit Auflistungen von Daten zu lösen.|
|[Parallele Container und Objekte](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Gewusst wie: Erhöhen der Effizienz mithilfe von parallelen Containern](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Gewusst wie: Verbessern der Leistung mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Gewusst wie: Kombinieren von Gruppen mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Beschreibt die `combinable` -Klasse sowie `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`und andere parallele Container. Verwenden Sie parallele Container und Objekte, wenn Sie Container benötigen, die threadsicheren Zugriff auf die zugehörigen Elemente bieten.|
|[Bewährte Methoden in der Parallel Patterns Library](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Allgemeine bewährte Methoden für die Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Bietet Tipps und empfohlene Vorgehensweisen für das Arbeiten mit der PPL.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>Abbrechen von Aufgaben und parallelen Algorithmen

|||
|-|-|
|[Abbruch in der PPL](cancellation-in-the-ppl.md)|Beschreibt die Rolle des Abbruchs in der PPL, einschließlich des Initiierens und Beantwortens von Abbruchanforderungen.|
|[Gewusst wie: Verwenden eines Abbruchs zum Verlassen einer Parallel-Schleife](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Gewusst wie: Verwenden der Ausnahmebehandlung zum Verlassen einer Parallel-Schleife](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Veranschaulicht zwei Möglichkeiten, parallele Arbeit mit Daten abzubrechen.|

## <a name="universal-windows-platform-apps"></a>Universelle Windows-Plattform-Apps

|||
|-|-|
|[Erstellen von asynchronen Vorgängen in C++ für UWP-apps](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Beschreibt einige der wichtigsten Punkte, die Sie berücksichtigen sollten, wenn Sie die Concurrency Runtime verwenden, um asynchrone Vorgänge in einer UWP-APP zu entwickeln.|
|[Exemplarische Vorgehensweise: Verbinden von Verwendungsaufgaben und XML-HTTP-Anforderungen](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Zeigt, wie ppl-Aufgaben mit den `IXMLHTTPRequest2` Schnitt `IXMLHTTPRequest2Callback` stellen und kombiniert werden, um HTTP-Get-und Post-Anforderungen an einen Webdienst in einer UWP-APP zu senden.|
|[Windows-Runtime App-Beispiele](https://code.msdn.microsoft.com/windowsapps)|Enthält herunterladbare Codebeispiele und Demo-Apps für Windows 8. x. Die C++-Beispiele verwenden Concurrency Runtime-Funktionen wie PPL-Aufgaben, um Daten im Hintergrund zu verarbeiten und so die Reaktionsfähigkeit aufrechtzuerhalten.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Datenflussprogrammierung in der Asynchronous Agents Library

|||
|-|-|
|[Asynchrone Agents](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Asynchrone Nachrichtenblöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Gewusst wie: Implementieren verschiedener Producer-Consumer-Muster](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Gewusst wie: Bereitstellen von Arbeitsfunktionen für die call- und transformer-Klassen](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Gewusst wie: Verwenden von transformer in einer Datenpipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Gewusst wie: Auswählen von abgeschlossenen Aufgaben](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Gewusst wie: Senden einer Nachricht in regelmäßigen Intervallen](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Gewusst wie: Verwenden eines Nachrichtenblockfilters](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Beschreibt asynchrone Agents, Nachrichtenblöcke und Nachrichtenübergabefunktionen, bei denen es sich um die Bausteine zum Durchführen von Datenflussvorgängen in der Concurrency Runtime handelt.|
|[Exemplarische Vorgehensweise: Erstellen einer agentbasierten Anwendung](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Datenfluss-Agent](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Veranschaulicht die Erstellung von einfachen auf Agents basierenden Anwendungen.|
|[Exemplarische Vorgehensweise: Erstellen eines Bildverarbeitungsnetzwerks](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Veranschaulicht das Erstellen eines Netzwerks asynchroner Nachrichtenblöcke für die Bildverarbeitung.|
|[Exemplarische Vorgehensweise: Verhindern von Deadlocks mit join](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Veranschaulicht anhand des Philosophenproblems, wie sich mit der Concurrency Runtime Deadlocks in der Anwendung verhindern lassen.|
|[Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Nachrichtenblocks](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Veranschaulicht, wie ein benutzerdefinierter Nachrichtenblocktyp erstellt wird, um eingehende Nachrichten nach Priorität zu sortieren.|
|[Bewährte Methoden in der Bibliothek für asynchrone Agents](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Allgemeine bewährte Methoden für die Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Bietet Tipps und empfohlene Vorgehensweisen für das Arbeiten mit Agents.|

## <a name="exception-handling-and-debugging"></a>Ausnahmebehandlung und Debuggen

|||
|-|-|
|[Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Beschreibt das Arbeiten mit Ausnahmen in der Concurrency Runtime.|
|[Diagnosetools für die parallele Ausführung](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Erläutert, wie Sie die Feinabstimmung von Anwendungen ausführen und die Concurrency Runtime so effizient wie möglich nutzen.|

## <a name="tuning-performance"></a>Optimieren der Leistung

|||
|-|-|
|[Diagnosetools für die parallele Ausführung](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Erläutert, wie Sie die Feinabstimmung von Anwendungen ausführen und die Concurrency Runtime so effizient wie möglich nutzen.|
|[Scheduler-Instanzen](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Gewusst wie: Verwalten einer Planerinstanz](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Scheduler-Richtlinien](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Gewusst wie: Angeben von bestimmten Planerrichtlinien](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Gewusst wie: Erstellen von Agents, die bestimmte Planerrichtlinien verwenden](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Veranschaulicht das Arbeiten mit Planerinstanzen und Planerrichtlinien. Bei Desktop-Apps können Sie mit Planerrichtlinien bestimmten Arten von Arbeitslasten spezielle Regeln zuordnen. Beispielsweise können Sie eine Planerinstanz erstellen, um einige Aufgaben mit höherer Threadpriorität auszuführen und andere Aufgaben mit dem Standardplaner mit normaler Threadpriorität auszuführen.|
|[Planen von Gruppen](../../parallel/concrt/schedule-groups.md)<br /><br /> [Gewusst wie: Beeinflussen der Ausführungsreihenfolge mithilfe von Zeitplangruppen](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Veranschaulicht die Verwendung von Planungsgruppen, um verwandte Aufgaben zusammen zu gruppieren. Sie können beispielsweise einen hohen Grad an Lokalität zwischen verwandten Aufgaben anfordern, wenn es Vorteile bietet, dass diese Aufgaben auf demselben Prozessorknoten ausgeführt werden.|
|[Einfache Aufgaben](../../parallel/concrt/lightweight-tasks.md)|Erläutert, wie einfache Aufgaben hilfreich für das Erstellen von Arbeit sind, die keinen Lastenausgleich oder Abbruch erfordert, sowie für das Anpassen von vorhandenem Code für die Verwendung mit der Concurrency Runtime.|
|[Kontexte](../../parallel/concrt/contexts.md)<br /><br /> [Gewusst wie: Implementieren einer kooperativen Semaphore mithilfe der Context-Klasse](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Vorgehensweise: Verwenden der Überzeichnung zum Versetzen der Latenz](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Beschreibt, wie das Verhalten der Threads gesteuert wird, die von der Concurrency Runtime verwaltet werden.|
|[Speicherverwaltungsfunktionen](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Gewusst wie: Verbessern der Arbeitsspeicherleistung mithilfe von Alloc und Free](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Beschreibt die Speicherverwaltungsfunktionen der Concurrency Runtime, die das parallele Reservieren und Freigeben von Arbeitsspeicher unterstützen.|

## <a name="additional-resources"></a>Weitere Ressourcen

|||
|-|-|
|[Muster und Tipps für die asynchrone Programmierung in Hilo (Windows Store-Apps mit C++ und XAML)](/previous-versions/windows/apps/jj160321(v=win.10))|Erfahren Sie, wie wir die Concurrency Runtime verwendet haben, um asynchrone Vorgänge in Hilo zu implementieren, einer Windows-Runtime-APP, die C++ und XAML verwendet.|
|[Parallel Programming in Native Code blog (Blog zum Thema paralleles Programmieren in nativem Code)](/archive/blogs/nativeconcurrency)|Bietet zusätzliche ausführliche Blogartikel zur parallelen Programmierung in der Concurrency Runtime.|
|[Parallel Computing in C++ and Native Code forum (Forum zum Thema paralleles Computing in C++ und nativem Code)](https://go.microsoft.com/fwlink/p/?linkid=183874)|Ermöglicht Ihnen die Teilnahme an Communitydiskussionen über die Concurrency Runtime.|
|[Parallele Programmierung](/dotnet/standard/parallel-programming/index)|Vermittelt Ihnen das parallele Programmiermodell, das in der .NET Framework verfügbar ist.|

## <a name="see-also"></a>Weitere Informationen

[Referenz](../../parallel/concrt/reference/reference-concurrency-runtime.md)
