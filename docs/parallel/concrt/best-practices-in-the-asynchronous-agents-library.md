---
title: Empfohlene Vorgehensweisen in der Asynchronous Agents Library
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: 99780de11d85831a6901f370d2491f15ef88c0b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231740"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>Empfohlene Vorgehensweisen in der Asynchronous Agents Library

In diesem Dokument wird die effektive Verwendung der Asynchronous Agents Library beschrieben. Die Agents Library begünstigt ein akteurbasiertes Programmiermodell und die prozessinterne Nachrichtenübergabe für simple Datenfluss- und Pipelinesaufgaben.

Weitere Informationen zur Agents Library finden Sie unter [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="sections"></a><a name="top"></a>Strecken

Dieses Dokument enthält folgende Abschnitte:

- [Isolieren von Status mit Agents](#isolation)

- [Begrenzen der Anzahl von Nachrichten in einer Datenpipeline mit einem Einschränkungsmechanismus](#throttling)

- [Keine detaillierte Arbeit in einer Datenpipeline](#fine-grained)

- [Keine Übergabe von großer Nutzlasten für Nachrichten anhand des Werts](#large-payloads)

- [Verwenden von shared_ptr in einem Datennetzwekr bei unklarem Besitzer](#ownership)

## <a name="use-agents-to-isolate-state"></a><a name="isolation"></a>Verwenden von Agents zum Isolieren des Zustands

Die Agents Library stellt Alternativen zum Freigabezustand bereit, indem sie das Verbinden isolierter Komponenten durch einen asynchronen Nachrichtenübergabemechanismum ermöglicht. Asynchrone Agents sind am effektivsten, wenn der interne Zustand von anderen Komponenten isoliert werden kann. Aufgrund der Isolierung des Status wirken mehrere Komponenten i. d. R. nicht auf freigegebene Daten. Die Isolierung des Status ermöglicht eine Skalierung der Anwendung, da Konflikte im freigegebenen Speicher reduziert werden. Ferner wird dadurch die Wahrscheinlichkeit von Deadlocks und Racebedingungen verringert, da der Zugriff auf die freigegebenen Daten nicht zwischen den Komponenten synchronisiert werden muss.

In der Regel isolieren Sie den Zustand in einem Agent, indem Sie die Datenmember in den **`private`** **`protected`** Abschnitten oder der Agent-Klasse und mithilfe von Nachrichten Puffern die Zustandsänderungen übermitteln. Das folgende Beispiel zeigt die- `basic_agent` Klasse, die von " [parallelcurrency:: Agent](../../parallel/concrt/reference/agent-class.md)" abgeleitet wird. Die `basic_agent`-Klasse verwendet zwei Meldungspuffer zur Kommunikation mit externen Komponenten. Ein Nachrichtenpuffer enthält eingehende Meldungen, der andere Nachrichtenpuffer enthält ausgehende Nachrichten.

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

Umfassende Beispiele zum Definieren und Verwenden von Agents finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer agentbasierten Anwendung](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) und Exemplarische Vorgehensweise [: Erstellen eines Daten](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)Fluss-Agents.

[Nach[oben](#top)]

## <a name="use-a-throttling-mechanism-to-limit-the-number-of-messages-in-a-data-pipeline"></a><a name="throttling"></a>Einschränken der Anzahl von Nachrichten in einer Daten Pipeline mithilfe eines Drosselungs Mechanismus

Viele Nachrichten Puffer Typen, z. b. " [parallelcurrency:: Unbounded_buffer](reference/unbounded-buffer-class.md)", können eine unbegrenzte Anzahl von Nachrichten enthalten. Wenn Nachrichten vom Nachrichtenproducer schneller an eine Datenpipeline gesendet werden, als diese vom Consumer verarbeitet werden können, kann der Speicherstatus der Anwendung auf Speichermangel hinweisen. Mit einem Einschränkungsmechanismus wie einem Semaphor können Sie die Anzahl der Nachrichten begrenzen, die zu einem gegebenen Zeitpunkt gleichzeitg in einer Datenpipepline aktiv sind.

Im Folgenden einfachen Beispiel wird veranschaulicht, wie die Anzahl der Nachrichten in einer Datenpipeline mit einem Semaphor eingeschränkt wird. Die Daten Pipeline verwendet die Funktion " [parallelcurrency:: Wait](reference/concurrency-namespace-functions.md#wait) ", um einen Vorgang zu simulieren, der mindestens 100 Millisekunden benötigt. Da die Nachrichten vom Absender schneller erzeugt werden, als diese vom Consumer verarbeitet werden können, wird in diesem Beispiel die `semaphore`-Klasse definiert, sodass die Anzahl der aktiven Nachrichten von der Anwendung eingeschränkt werden kann.

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

Die Pipeline wird vom `semaphore`-Objekt eingeschränkt, sodass maximal zwei Nachrichten gleichzeitig verarbeitet werden können.

Der Producer in diesem Beispiel sendet verhältnismäßig wenig Nachrichten an den Consumer. Daher ist dieses Beispiel ungeeignet, um eine Situation mit einem Mangel an Arbeitsspeicher zu veranschaulichen. Dieser Mechanismus ist jedoch hilfreich, wenn eine Datenpipeline eine relativ hohe Anzahl von Meldungen enthält.

Weitere Informationen zum Erstellen der Semaphor-Klasse, die in diesem Beispiel verwendet wird, finden Sie unter Gewusst [wie: Implementieren einer kooperativen Semaphor mithilfe der Context-Klasse](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

[Nach[oben](#top)]

## <a name="do-not-perform-fine-grained-work-in-a-data-pipeline"></a><a name="fine-grained"></a>Keine fein abgestimmte Arbeit in einer Daten Pipeline ausführen

Die Agents Library ist besonders hilfreich, wenn die Arbeit, die von einer Datenpipeline ausgeführt wird, eher simpel ist. Beispielsweise könnte eine Anwendungskomponente Daten aus einer Datei oder einer Netzwerkverbindung lesen und ab und zu Daten an eine andere Komponente senden. Das Protokoll, das die Agents-Bibliothek zur Weitergabe von Nachrichten verwendet, bewirkt, dass der Mechanismus für die Nachrichten Übergabe mehr Aufwand als die von der [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) bereitgestellten Aufgaben paralleler Konstrukte hat. Deshalb müssen Sie sicherstellen, dass die Arbeit, die von einer Datenpipeline ausgeführt wird, lang genug dauert, um diesen Mehraufwand auszugleichen.

Obwohl eine Datenpipeline am effektivsten ist, wenn die Aufgaben simpel sind, können in jeder Phase der Datenpipeline PPL-Konstrukte wie Aufgabengruppen und parallele Algorithmen verwendet werden, um differenziertere Aufgaben auszuführen. Ein Beispiel für ein undifferenziertes Datennetzwerk, das in jeder Verarbeitungsphase differenzierte Parallelität verwendet, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Bild Verarbeitungs Netzwerks](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[Nach[oben](#top)]

## <a name="do-not-pass-large-message-payloads-by-value"></a><a name="large-payloads"></a>Große Nachrichten-Nutzlasten nicht nach Wert übergeben

In einigen Fällen wird von der Laufzeit eine Kopie einer Nachricht erstellt und von einem Nachrichtenpuffer an einen anderen Nachrichtenpuffer übergeben. Die Klasse " [parallelcurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) " bietet z. b. eine Kopie jeder Nachricht, die Sie an jedes ihrer Ziele empfängt. Die Laufzeit erstellt außerdem eine Kopie der Nachrichten Daten, wenn Sie Nachrichten Übergabe Funktionen wie z. b. Parallelität [:: Send](reference/concurrency-namespace-functions.md#send) und [parallelcurrency:: Receive](reference/concurrency-namespace-functions.md#receive) zum Schreiben von Nachrichten und zum Lesen von Nachrichten aus einem Nachrichten Puffer verwenden. Auch wenn dieser Mechanismus dazu beiträgt, das Risiko zu verringern, dass freigegebene Daten gleichzeitig geschrieben werden, kann die Arbeitsspeicherleistung darunter leiden, dass die Nachrichten relativ hoch ist.

Sie können die Arbeitsspeicherleistung beim Übergeben von Nachrichten mit einer großen Nutzlast verbessern, indem Sie Zeiger und Verweise verwenden. Im folgenden Beispiel wird die Übergabe umfangreicher Nachrichten anhand des Werts mit der Übergabe von Zeigern auf den gleichen Nachrichtentyp verglichen. Im Beispiel werden zwei Agent-Typen definiert, `producer` und `consumer`, die auf `message_data`-Objekte angewendet werden. In dem Beispiel wird die Zeit, die der Producer benötigt, um mehrere `message_data`-Objekte an den Consumer zu senden, mit der Zeit verglichen, die der Producer-Agent benötigt, um mehrere Zeiger auf `message_data`-Objekte an den Consumer zu senden.

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe:

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

Die Version mit Zeiger weist eine bessere Leistungauf, da von der Laufzeit während der Übergabe vom Producer an den Consumer nicht eine vollständige Kopie jedes `message_data`-Objekts erstellt werden muss.

[Nach[oben](#top)]

## <a name="use-shared_ptr-in-a-data-network-when-ownership-is-undefined"></a><a name="ownership"></a>Verwenden von shared_ptr in einem Datennetzwerk, wenn der Besitz nicht definiert ist

Beim Senden von Nachrichten anhand des Zeigers über eine Pipeline oder ein Netzwerk zur Übergabe von Nachrichten wird der Arbeitsspeicher für jede Nachricht i. d. R. am Anfang des Netzwerks zugewiesen und am Ende des Netzwerks freigegeben. Obwohl dieser Mechanismus normalerweise gut funktioniert, kann er jedoch in einigen Fällen kaum oder nicht verwendet werden. Betrachten Sie beispielsweise den Fall eines Datennetzwerkes mit mehreren Endknoten. In diesem Fall gibt es keine klare Position, um den Arbeitsspeicher für die Nachrichten freizugeben.

Um dieses Problem zu beheben, können Sie einen Mechanismus verwenden, z. b. " [Std:: shared_ptr](../../standard-library/shared-ptr-class.md)", der es ermöglicht, dass ein Zeiger mehreren Komponenten gehört. Wenn das endgültige `shared_ptr`-Objekt zerstört wird, das eine Ressource besitzt, wird auch die Ressource freigegeben.

Im folgenden Beispiel wird veranschaulicht, wie mit `shared_ptr` Zeigerwerte für mehrere Nachrichtenpuffer gemeinsam verwendet werden können. Im Beispiel wird ein [parallelcurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) -Objekt mit drei Parallelitäts [:: Callcenter](../../parallel/concrt/reference/call-class.md) -Objekten verbunden. Die `overwrite_buffer`-Klasse stellt Nachrichten für die einzelnen Ziele bereit. Da das Datennetzwerk am Ende mehrere Besitzer der Daten aufweist, werden die einzelnen `shared_ptr`-Objekte mit `call` in die Lage versetzt, den Besitz der Nachrichten zu teilen.

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe:

```Output
Creating resource 42...
receiver1: received resource 42
Creating resource 64...
receiver2: received resource 42
receiver1: received resource 64
Destroying resource 42...
receiver2: received resource 64
Destroying resource 64...
```

## <a name="see-also"></a>Weitere Informationen

[Bewährte Methoden für Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Exemplarische Vorgehensweise: Erstellen einer agentbasierten Anwendung](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[Exemplarische Vorgehensweise: Erstellen eines Datenfluss-Agents](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Exemplarische Vorgehensweise: Erstellen eines Bild Verarbeitungs Netzwerks](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Bewährte Methoden in der Parallel Patterns Library](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Allgemeine bewährte Methoden für die Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
