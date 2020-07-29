---
title: Allgemein empfohlene Vorgehensweisen in der Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: 77ca8acbd3dedc28aaa6c330c3e91ed09046d162
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228452"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Allgemein empfohlene Vorgehensweisen in der Concurrency Runtime

Dieses Dokument beschreibt empfohlene Vorgehensweisen, die für mehrere Bereiche der Concurrency Runtime gelten.

## <a name="sections"></a><a name="top"></a>Strecken

Dieses Dokument enthält folgende Abschnitte:

- [Verwenden Sie nach Möglichkeit Konstrukte für die kooperative Synchronisierung](#synchronization)

- [Vermeiden Sie langwierige Aufgaben, die nicht zurückgehalten werden](#yield)

- [Verwenden Sie die Überzeichnung für den Offset von blockierenden Vorgängen oder von Vorgängen mit langer Wartezeit](#oversubscription)

- [Verwenden Sie nach Möglichkeit parallele Speicherverwaltungsfunktionen](#memory)

- [Verwenden Sie RAII zum Verwalten der Lebensdauer von Parallelitätsobjekten](#raii)

- [Erstellen Sie keine Parallelitätsobjekte im globalen Gültigkeitsbereich](#global-scope)

- [Verwenden Sie keine Parallelitätsobjekte in freigegebenen Datensegmenten](#shared-data)

## <a name="use-cooperative-synchronization-constructs-when-possible"></a><a name="synchronization"></a>Verwenden Sie nach Möglichkeit kooperative Synchronisierungs Konstrukte.

Die Concurrency Runtime stellt viele parallelitätssichere Konstrukte bereit, die kein externes Synchronisierungsobjekt erfordern. Beispielsweise stellt die [parallelcurrency:: Concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) -Klasse Parallelitäts sichere Anfüge-und Element Zugriffs Vorgänge bereit. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge. In Fällen, in denen Sie exklusiven Zugriff auf eine Ressource benötigen, stellt die Laufzeit jedoch die Klassen [parallelcurrency:: CRITICAL_SECTION](../../parallel/concrt/reference/critical-section-class.md), [parallelcurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)und [parallelcurrency:: Event](../../parallel/concrt/reference/event-class.md) bereit. Diese Typen weisen kooperatives Verhalten auf. Deshalb kann der Aufgabenplaner Verarbeitungsressourcen neu einem anderen Kontext zuteilen, während die erste Aufgabe auf Daten wartet. Verwenden Sie nach Möglichkeit diese Synchronisierungstypen statt anderer Synchronisierungsmechanismen, z. B. die von der Windows-API bereitgestellten Synchronisierungsmechanismen, die kein kooperatives Verhalten aufweisen. Weitere Informationen zu diesen Synchronisierungs Typen und ein Codebeispiel finden Sie unter [Synchronisierung von Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md) und [vergleichen der Synchronisierungs Datenstrukturen mit der Windows-API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[Nach[oben](#top)]

## <a name="avoid-lengthy-tasks-that-do-not-yield"></a><a name="yield"></a>Vermeiden Sie langwierige Aufgaben, die nicht

Da sich der Taskplaner kooperativ verhält, stellt er keine Fairness zwischen Aufgaben bereit. Daher kann eine Aufgabe das Starten anderer Aufgaben verhindern. Dies ist zwar in manchen Fällen akzeptabel, kann jedoch in anderen Fällen Deadlocks oder Ressourcenmangel verursachen.

Im folgenden Beispiel übersteigt die Anzahl der ausgeführten Aufgaben die Anzahl der zugeteilten Verarbeitungsressourcen. Die erste Aufgabe wird nicht an den Taskplaner abgetreten, und daher wird die zweite Aufgabe erst gestartet, nachdem die erste Aufgabe beendet wurde.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

Es gibt mehrere Möglichkeiten, die Zusammenarbeit zwischen den beiden Aufgaben zu ermöglichen. Eine Möglichkeit besteht darin, eine Aufgabe mit langer Ausführungszeit gelegentlich an den Aufgabenplaner abzutreten. Im folgenden Beispiel wird die- `task` Funktion so geändert, dass die " [parallelcurrency:: context:: Yield](reference/context-class.md#yield) "-Methode aufgerufen wird, um die Ausführung an den Aufgabenplaner zu übergeben, sodass eine andere Aufgabe ausgeführt werden kann.

[!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
1: 250000000
2: 250000000
1: 500000000
2: 500000000
1: 750000000
2: 750000000
1: 1000000000
2: 1000000000
```

Die `Context::Yield`-Methode gibt nur an einen anderen aktiven Thread des Planers, zu dem der aktuelle Thread gehört, an eine einfache Aufgabe oder an einen anderen Betriebssystemthread zurück. Diese Methode führt nicht zu einer Arbeit, die für die Ausführung in einem [parallelcurrency:: task_group](reference/task-group-class.md) -oder [parallelcurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) -Objekt geplant ist, aber noch nicht gestartet wurde.

Es gibt weitere Verfahren, die Zusammenarbeit zwischen Aufgaben mit langer Ausführungsdauer zu ermöglichen. Sie können eine große Aufgabe in kleinere Unteraufgaben aufteilen. Sie können auch Überzeichnung während einer langwierigen Aufgabe aktivieren. Durch Überzeichnung können Sie mehr Threads als die Anzahl der verfügbaren Hardwarethreads erstellen. Überzeichnung ist von besonderem Nutzen, wenn eine langwierige Aufgabe einen hohen Betrag an Wartezeit beinhaltet, z. B. das Lesen von Daten von einem Datenträger oder über eine Netzwerkverbindung. Weitere Informationen zu Lightweight-Aufgaben und über Abonnements finden Sie unter [Taskplaner](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[Nach[oben](#top)]

## <a name="use-oversubscription-to-offset-operations-that-block-or-have-high-latency"></a><a name="oversubscription"></a>Verwenden von über schreibungen zum Versetzen von Vorgängen, die eine hohe Latenz blockieren oder aufweisen

Der Concurrency Runtime stellt Synchronisierungs primitive, z. b. "Parallelität [:: CRITICAL_SECTION](../../parallel/concrt/reference/critical-section-class.md)", bereit, die es ermöglichen, dass Aufgaben gemeinsam blockiert werden und einander liefern. Wenn eine Aufgabe kooperativ blockiert oder zurückgehalten wird, kann der Taskplaner Verarbeitungsressourcen neu einem anderen Kontext zuteilen, während die erste Aufgabe auf Daten wartet.

Es gibt Fälle, in denen Sie den von der Concurrency Runtime bereitgestellten kooperativen Blockierungsmechanismus nicht verwenden können. Zum Beispiel verwendet eine externe Bibliothek möglicherweise einen anderen Synchronisierungsmechanismus. Ein weiteres Beispiel ist das Ausführen eines Vorgangs, der einen hohen Betrag an Wartezeit beinhalten kann, wenn Sie z. B. die `ReadFile`-Funktion der Windows-API zum Lesen von Daten über eine Netzwerkverbindung verwenden. In diesen Fällen kann Überzeichnung die Ausführung anderer Aufgaben ermöglichen, wenn sich eine andere Aufgabe im Leerlauf befindet. Durch Überzeichnung können Sie mehr Threads als die Anzahl der verfügbaren Hardwarethreads erstellen.

Betrachten Sie die folgende Funktion `download`, mit der die Datei an der angegebenen URL heruntergeladen wird. In diesem Beispiel wird die [parallelcurrency:: context:: Oversubscribe](reference/context-class.md#oversubscribe) -Methode verwendet, um die Anzahl aktiver Threads vorübergehend zu erhöhen.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

Da die `GetHttpFile`-Funktion einen Vorgang mit potenzieller Wartezeit ausführt, kann Überzeichnung die Ausführung anderer Aufgaben ermöglichen, während die aktuelle Aufgabe auf Daten wartet. Die vollständige Version dieses Beispiels finden Sie unter Gewusst [wie: Verwenden der Überzeichnung zum Offset der Latenz](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)Zeit.

[Nach[oben](#top)]

## <a name="use-concurrent-memory-management-functions-when-possible"></a><a name="memory"></a>Parallele Speicherverwaltungsfunktionen verwenden, wenn möglich

Verwenden Sie die Speicherverwaltungsfunktionen "Parallelität [:: Alloc](reference/concurrency-namespace-functions.md#alloc) " und " [parallelcurrency:: Free](reference/concurrency-namespace-functions.md#free)", wenn Sie differenzierte Aufgaben haben, die häufig kleine Objekte mit einer relativ kurzen Lebensdauer zuordnen. Die Concurrency Runtime verwaltet für jeden ausgeführten Thread einen eigenen Arbeitsspeichercache. Die `Alloc`-Funktion und die `Free`-Funktion reservieren Arbeitsspeicher in diesen Caches und geben Arbeitsspeicher in den Caches frei, ohne Sperren oder Arbeitsspeicherbarrieren zu verwenden.

Weitere Informationen zu diesen Speicherverwaltungsfunktionen finden Sie unter [Taskplaner](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Ein Beispiel, in dem diese Funktionen verwendet werden, finden Sie unter Gewusst [wie: Verwenden von "Zuweisung" und "kostenlos" zur Verbesserung der Speicherleistung](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

[Nach[oben](#top)]

## <a name="use-raii-to-manage-the-lifetime-of-concurrency-objects"></a><a name="raii"></a>Verwenden von RAII zum Verwalten der Lebensdauer von Parallelitäts Objekten

Die Concurrency Runtime verwendet die Ausnahmebehandlung zum Implementieren von Funktionen, z. B. Abbruch. Schreiben Sie daher ausnahmesicheren Code, wenn Sie die Laufzeit oder eine andere Bibliothek aufrufen, die die Laufzeit aufruft.

Das RAII-Muster ( *Resource Acquisition Is Initialization* ) ist eine Möglichkeit, die Lebensdauer eines Parallelitäts Objekts in einem bestimmten Bereich sicher zu verwalten. Unter dem RAII-Muster wird dem Stapel eine Datenstruktur zugeordnet. Diese Datenstruktur initialisiert oder ruft eine Ressource ab, wenn sie erstellt wird, und zerstört oder gibt diese Ressource frei, wenn die Datenstruktur zerstört wird. Das RAII-Muster garantiert, dass der Destruktor aufgerufen wird, bevor der einschließende Bereich beendet wird. Dieses Muster ist hilfreich, wenn eine Funktion mehrere- **`return`** Anweisungen enthält. Das Muster erleichtert Ihnen außerdem das Schreiben von ausnahmesicherem Code. Wenn eine- **`throw`** Anweisung bewirkt, dass der Stapel entladen wird, wird der Dekonstruktor für das RAII-Objekt aufgerufen. Daher wird die Ressource immer ordnungsgemäß gelöscht oder freigegeben.

Die Common Language Runtime definiert mehrere Klassen, die das RAII-Muster verwenden, z. b. " [parallelcurrency:: critical_section:: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) " und " [parallelcurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)". Diese Hilfsklassen werden als Bereichs bezogene *Sperren*bezeichnet. Diese Klassen bieten mehrere Vorteile, wenn Sie mit der Verwendung von [parallelcurrency:: CRITICAL_SECTION](../../parallel/concrt/reference/critical-section-class.md) -oder [parallelcurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) -Objekten arbeiten. Der Konstruktor dieser Klassen erhält Zugriff auf das bereitgestellte `critical_section`-Objekt bzw. `reader_writer_lock`-Objekt, und der Destruktor gibt den Zugriff auf das Objekt frei. Da eine bewertete Sperre den Zugriff auf das gegenseitige Ausschlussobjekt automatisch freigibt, wenn es zerstört wird, muss das zugrunde liegende Objekt nicht manuell entsperrt werden.

Betrachten Sie die folgende Klasse `account`, die durch eine externe Bibliothek definiert ist und deshalb nicht geändert werden kann.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

Im folgenden Beispiel werden mehrere Transaktionen für ein `account`-Objekt parallel ausgeführt. Im Beispiel wird ein `critical_section`-Objekt zum Synchronisieren des Zugriffs auf das `account`-Objekt verwendet, da die `account`-Klasse nicht parallelitätssicher ist. Für jeden parallelen Vorgang wird ein `critical_section::scoped_lock`-Objekt verwendet, um sicherzustellen, dass das `critical_section`-Objekt entsperrt wird, wenn der Vorgang erfolgreich ausgeführt wird oder fehlschlägt. Wenn der Kontostand negativ ist, löst der `withdraw`-Vorgang eine Ausnahme aus und schlägt fehl.

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe:

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

Weitere Beispiele, in denen das RAII-Muster verwendet wird, um die Lebensdauer von Parallelitäts Objekten zu verwalten, finden Sie unter Exemplarische Vorgehensweise [: Entfernen von Arbeit aus einem Benutzeroberflächen Thread](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), Gewusst [wie: Verwenden der Kontext Klasse zum Implementieren einer kooperativen Semaphore](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)und Gewusst [wie: Verwenden der Überzeichnung zum](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)versetzen der Latenzzeit.

[Nach[oben](#top)]

## <a name="do-not-create-concurrency-objects-at-global-scope"></a><a name="global-scope"></a>Keine Parallelitäts Objekte im globalen Gültigkeitsbereich erstellen

Wenn Sie ein Parallelitätsobjekt im globalen Gültigkeitsbereich erstellen, kann dies zu Problemen wie Deadlocks oder Arbeitsspeicher-Zugriffsverletzungen in der Anwendung führen.

Wenn Sie z. B. ein Concurrency Runtime-Objekt erstellen, erstellt die Laufzeit einen Standardplaner, sofern noch kein Planer erstellt wurde. Ein Laufzeitobjekt, das während der globalen Objekterstellung erstellt wird, führt dementsprechend dazu, dass die Laufzeit diesen Standardplaner erstellt. Dieser Vorgang verwendet jedoch eine interne Sperre, die die Initialisierung anderer Objekte behindern kann, die die Concurrency Runtime-Infrastruktur unterstützen. Diese interne Sperre wird eventuell von einem anderen Infrastrukturobjekt benötigt, das noch nicht initialisiert wurde, und daher tritt möglicherweise ein Deadlock in der Anwendung auf.

Im folgenden Beispiel wird die Erstellung eines globalen [parallelcurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) -Objekts veranschaulicht. Dieses Muster gilt nicht nur für die `Scheduler`-Klasse, sondern auch für alle anderen Typen, die von der Concurrency Runtime bereitgestellt werden. Es wird empfohlen, dieses Muster nicht anzuwenden, da es zu einem unerwarteten Verhalten in der Anwendung führen kann.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

Beispiele für die richtige Methode zum Erstellen von `Scheduler` Objekten finden Sie unter [Taskplaner](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[Nach[oben](#top)]

## <a name="do-not-use-concurrency-objects-in-shared-data-segments"></a><a name="shared-data"></a>Verwenden Sie keine Parallelitäts Objekte in freigegebenen Datensegmenten.

Der Concurrency Runtime unterstützt nicht die Verwendung von Parallelitäts Objekten in einem freigegebenen Daten Abschnitt, z. b. ein Daten Abschnitt, der von der [data_seg](../../preprocessor/data-seg.md) -Anweisung erstellt wird `#pragma` . Ein über Prozessgrenzen hinweg gemeinsam genutztes Parallelitätsobjekt kann einen inkonsistenten oder ungültigen Zustand der Laufzeit verursachen.

[Nach[oben](#top)]

## <a name="see-also"></a>Siehe auch

[Bewährte Methoden für Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Taskplaner](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Synchronisierungs Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Vergleichen der Synchronisierungs Datenstrukturen mit der Windows-API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[Gewusst wie: verbessern der Arbeitsspeicher Leistung mithilfe von "Zuweisung" und "kostenlos"](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[Gewusst wie: Verwenden der Überzeichnung zum Versetzen der Latenzzeit](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[Gewusst wie: Implementieren einer kooperativen Semaphore mithilfe der Context-Klasse](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Exemplarische Vorgehensweise: Entfernen von Arbeit aus einem Benutzeroberflächen Thread](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[Bewährte Methoden in der Parallel Patterns Library](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Bewährte Methoden in der Bibliothek für asynchrone Agents](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
