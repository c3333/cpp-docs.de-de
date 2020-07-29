---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Nachrichtenblocks'
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: f95eaf7e1da41bd473ab15d12330d0177b98ccdf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219494"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Nachrichtenblocks

In diesem Dokument wird beschrieben, wie ein benutzerdefinierter Nachrichtenblocktyp erstellt wird, um eingehende Nachrichten nach Priorität zu sortieren.

Obwohl die integrierten Nachrichtenblocktypen eine breite Palette von Funktionen bereitstellen, können Sie auch eigene Nachrichtenblocktypen erstellen und anpassen, um die Anforderungen Ihrer Anwendung zu erfüllen. Eine Beschreibung der integrierten Nachrichtenblock Typen, die von der Asynchronous Agents Library bereitgestellt werden, finden Sie unter [asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Voraussetzungen

Lesen Sie die folgenden Dokumente, bevor Sie mit dieser exemplarischen Vorgehensweise beginnen:

- [Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)

- [Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>Strecken

Diese exemplarische Vorgehensweise enthält folgende Abschnitte:

- [Entwerfen eines benutzerdefinierten Nachrichtenblocks](#design)

- [Definieren der priority_buffer-Klasse](#class)

- [Vollständiges Beispiel](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>Entwerfen eines benutzerdefinierten Nachrichten Blocks

Nachrichtenblöcke sind am Senden und Empfangen von Nachrichten beteiligt. Ein Nachrichtenblock, der Nachrichten sendet, wird als *Quell Block*bezeichnet. Ein Nachrichtenblock, der Nachrichten empfängt, wird als *Zielblock*bezeichnet. Ein Nachrichtenblock, der Nachrichten sendet und empfängt, wird als *propagatorblock*bezeichnet. Die Agents Library verwendet die abstrakte Klasse " [parallelcurrency:: ISource](../../parallel/concrt/reference/isource-class.md) ", um Quell Blöcke darzustellen, und die abstrakte Klasse " [parallelcurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) ", die Ziel Blöcke darstellt. Nachrichtenblocktypen, die als Quelle dienen, werden von der `ISource`-Klasse abgeleitet, während Nachrichtenblocktypen, die als Ziel dienen, von der `ITarget`-Klasse abgeleitet werden.

Der Nachrichtenblocktyp kann prinzipiell unmittelbar von `ISource` und `ITarget` abgeleitet werden. Die Agents Library definiert jedoch drei Basisklassen, deren Funktionalität weitestgehend der aller Nachrichtenblocktypen entspricht. Beispiel: parallelitätssicheres Behandeln von Fehlern und parallelitätssicheres Verbinden von Nachrichtenblöcken. Die Klasse " [parallelcurrency:: source_block](../../parallel/concrt/reference/source-block-class.md) " wird von abgeleitet `ISource` und sendet Nachrichten an andere Blöcke. Die Klasse " [parallelcurrency:: target_block](../../parallel/concrt/reference/target-block-class.md) " wird von abgeleitet `ITarget` und empfängt Nachrichten von anderen Blöcken. Die " [parallelcurrency::p ropagator_block](../../parallel/concrt/reference/propagator-block-class.md) -Klasse wird von `ISource` und abgeleitet `ITarget` und sendet Nachrichten an andere Blöcke und empfängt Nachrichten von anderen Blöcken. Es wird empfohlen, Infrastrukturdetails mit diesen drei Basisklassen zu behandeln, sodass Sie sich auf das Verhalten des Nachrichtenblocks konzentrieren können.

Die Klassen `source_block`, `target_block` und `propagator_block` sind Vorlagen, die auf der Grundlage eines Typs parametrisiert werden, der die Verbindungen oder Links zwischen Quell- und Zielblöcken verwaltet, sowie auf Grundlage eines Typs, der die Verarbeitung von Nachrichten verwaltet. Die Agents Library definiert zwei Typen, die Link Verwaltung, Parallelität [:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) und Parallelität [:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)ausführen. Die `single_link_registry`-Klasse ermöglicht das Verknüpfen eines Nachrichtenblocks mit einer Quelle oder einem Ziel. Die `multi_link_registry`-Klasse ermöglicht das Verknüpfen eines Nachrichtenblocks mit mehreren Quellen oder mehreren Zielen. Die Agents Library definiert eine Klasse, die die Nachrichten Verwaltung durchführt, Parallelität [:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). Die `ordered_message_processor`-Klasse ermöglicht Nachrichtenblöcken die Verarbeitung von Nachrichten in der Reihenfolge ihres Empfangs.

Im folgenden Beispiel wird die Beziehung zwischen Nachrichtenblöcken sowie Quellen und Zielen veranschaulicht. In diesem Beispiel wird die Deklaration der Klasse " [parallelcurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) " veranschaulicht.

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

Die `transformer`-Klasse wird von `propagator_block` abgeleitet und fungiert daher als Quell- sowie als Zielblock. Sie akzeptiert Nachrichten vom Typ `_Input` und sendet Nachrichten vom Typ `_Output`. Die `transformer`-Klasse gibt `single_link_registry` als Link-Manager für alle Zielblöcke und `multi_link_registry` als Link-Manager für alle Quellblöcke an. Aus diesem Grund kann ein `transformer`-Objekt ein Ziel sowie eine unbegrenzte Anzahl von Quellen haben.

Eine Klasse, die von abgeleitet wird, `source_block` muss sechs Methoden implementieren: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)und [resume_propagation](reference/source-block-class.md#resume_propagation). Eine Klasse, die von abgeleitet `target_block` ist, muss die [propagate_message](reference/propagator-block-class.md#propagate_message) -Methode implementieren und optional die [send_message](reference/propagator-block-class.md#send_message) -Methode implementieren. Ableitungen von `propagator_block` sowie von `source_block` und `target_block` sind funktional äquivalent.

Die `propagate_to_any_targets`-Methode wird von der Laufzeit aufgerufen, um alle eingehenden Nachrichten synchron oder asynchron zu verarbeiten und alle ausgehenden Nachrichten weiterzugeben. Die `accept_message`-Methode wird von Zielblöcken aufgerufen, um Nachrichten zu akzeptieren. Viele Nachrichtenblocktypen wie `unbounded_buffer` senden Nachrichten nur an das erste Ziel, das diese empfangen würde. Daher wird der Besitz der Nachricht auf das Ziel übertragen. Andere Nachrichtenblock Typen, wie z. b. " [parallelcurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)", bieten den einzelnen Ziel Blöcken Nachrichten. `overwrite_buffer` erstellt daher eine Kopie der Nachricht für alle diesbezüglichen Ziele.

Mit den Methoden `reserve_message`, `consume_message`, `release_message` und `resume_propagation` können Nachrichtenblöcke an der Reservierung von Nachrichten teilnehmen. Zielblöcke rufen die `reserve_message`-Methode auf, wenn eine Nachricht für sie bereitgestellt wird, die zur späteren Verwendung reserviert werden muss. Nach dem Reservieren einer Nachricht durch den Zielblock kann dieser die `consume_message`-Methode aufrufen, um die Nachricht zu verarbeiten, oder die `release_message`-Methode, um die Reservierung abzubrechen. Analog zur `accept_message`-Methode kann die Implementierung von `consume_message` den Besitz der Nachricht übertragen oder eine Kopie der Nachricht zurückgeben. Nachdem eine reservierte Nachricht von einem Zielblock verarbeitet oder freigegeben wurde, wird die `resume_propagation`-Methode von der Laufzeit aufgerufen. Diese Methode setzt die Nachrichtenweitergabe i. d. R. mit der nächsten Nachricht in der Warteschlange fort.

Die `propagate_message`-Methode wird von der Laufzeit aufgerufen, um eine Nachricht asynchron von einem anderen Block zum aktuellen zu übertragen. Die `send_message`-Methode ähnelt der `propagate_message`-Methode, sendet die Nachrichten im Unterschied zu dieser jedoch synchron an die Zielblöcke. Die Standardimplementierung von `send_message` weist alle eingehenden Nachrichten zurück. Die Laufzeit ruft keine der Methoden auf, wenn von der Nachricht nicht die optionale Filterfunktion übergeben wird, die dem Zielblock zugeordnet ist. Weitere Informationen zu Nachrichten filtern finden Sie unter [asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md).

[Nach[oben](#top)]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>Definieren der priority_buffer-Klasse

Die `priority_buffer`-Klasse ist ein benutzerdefinierter Nachrichtenblocktyp, der eingehende Meldungen zunächst nach der Priorität und anschließend nach der Reihenfolge ihres Empfangs sortiert. Die `priority_buffer` -Klasse ähnelt der Klasse " [parallelcurrency:: Unbounded_buffer](reference/unbounded-buffer-class.md) ", da Sie eine Warteschlange für Nachrichten enthält und auch weil Sie sowohl als Quell-als auch als Ziel Nachrichtenblock fungiert und sowohl mehrere Quellen als auch mehrere Ziele aufweisen kann. `unbounded_buffer` legt als Kriterium für die Weitergabe von Nachrichten jedoch nur die Reihenfolge ihres Empfangs aus den Quellen zugrunde.

Die `priority_buffer` -Klasse empfängt Nachrichten vom Typ Std::[Tupel](../../standard-library/tuple-class.md) , die `PriorityType` -Elemente und- `Type` Elemente enthalten. `PriorityType` verweist auf den Typ, der die Priorität einer Nachricht angibt; `Type` verweist auf den Datenteil der Nachricht. Die `priority_buffer`-Klasse sendet Nachrichten vom Typ `Type`. Die `priority_buffer` -Klasse verwaltet auch zwei Nachrichten Warteschlangen: ein [Std::p riority_queue](../../standard-library/priority-queue-class.md) -Objekt für eingehende Nachrichten und ein Std::[Queue](../../standard-library/queue-class.md) -Objekt für ausgehende Nachrichten. Das Sortieren von Nachrichten nach der Priorität ist hilfreich, wenn ein `priority_buffer`-Objekt mehrere Nachrichten gleichzeitig oder bevor diese von Consumern gelesen werden empfängt.

Zusätzlich zu den sieben Methoden, die von einer Klasse implementiert werden müssen, die von `propagator_block` abgeleitet wird, überschreibt die `priority_buffer`-Klasse die noch die `link_target_notification`-Methode und die `send_message`-Methode. Die `priority_buffer`-Klasse definiert außerdem zwei öffentliche Hilfsmethoden (, `enqueue` und `dequeue`) sowie eine private Hilfsmethode ( `propagate_priority_order`).

Im folgenden Verfahren wird beschrieben, wie die `priority_buffer`-Klasse implementiert wird.

#### <a name="to-define-the-priority_buffer-class"></a>So definieren Sie die priority_buffer-Klasse

1. Erstellen Sie eine C++-Header Datei, und benennen Sie Sie `priority_buffer.h` . Sie können auch eine bestehende Headerdatei verwenden, die Teil Ihres Projekts ist.

1. `priority_buffer.h`Fügen Sie in den folgenden Code ein.

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. Definieren Sie im- `std` Namespace Spezialisierungs-und "Std [:: less](../../standard-library/less-struct.md) " und " [Std:: Greater](../../standard-library/greater-struct.md) ", die auf "parallelcurrency::[Message](../../parallel/concrt/reference/message-class.md) "-Objekte reagieren.

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   Die `priority_buffer`-Klasse speichert `message`-Objekte in einem `priority_queue`-Objekt. Mit diesen Typspezialisierungen können die Nachrichten von der Prioritätswarteschlange anhand ihrer Priorität sortiert werden. Die Priorität ist das erste Element des `tuple`-Objekts.

1. Deklarieren Sie die `concurrencyex`-Klasse im `priority_buffer`-Namespace.

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   Die `priority_buffer`-Klasse wird von `propagator_block` abgeleitet. Sie kann daher Meldungen senden und empfangen. Die `priority_buffer`-Klasse mehrere Ziele aufweisen, die Nachrichten vom Typ `Type` empfangen. Sie kann außerdem mehrere Quellen aufweisen, die Nachrichten vom Typ `tuple<PriorityType, Type>` senden.

1. **`private`** Fügen Sie im-Abschnitt der- `priority_buffer` Klasse die folgenden Member-Variablen hinzu.

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   Das `priority_queue`-Objekt enthält eingehende Nachrichten, das `queue`-Objekt enthält ausgehende Nachrichten. Ein `priority_buffer`-Objekt kann mehrere Nachrichten gleichzeitig empfangen. Das `critical_section`-Objekt synchronisiert den Zugriff auf die Warteschlange für eingehende Nachrichten.

1. Definieren Sie im **`private`** -Abschnitt den Kopierkonstruktor und den Zuweisungs Operator. Dadurch wird verhindert, dass `priority_queue`-Objekte zugewiesen werden können.

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. **`public`** Definieren Sie im-Abschnitt die Konstruktoren, die vielen Nachrichtenblock Typen gemeinsam sind. Definieren Sie auch den Destruktor.

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. Definieren Sie im **`public`** -Abschnitt die `enqueue` -Methoden und `dequeue` . Diese Hilfsmethoden bieten eine alternative Möglichkeit, Nachrichten an ein `priority_buffer`-Objekt zu senden und von diesem zu empfangen.

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. Definieren Sie im- **`protected`** Abschnitt die- `propagate_to_any_targets` Methode.

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   Die `propagate_to_any_targets`-Methode überträgt die Nachricht, die sich in der Eingabewarteschlange an erster Stelle befindet, an die Ausgabewarteschlange, und gibt alle Nachrichten an die Ausgabewarteschlange weiter.

1. Definieren Sie im- **`protected`** Abschnitt die- `accept_message` Methode.

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Wenn die `accept_message`-Methode von einem Zielblock aufgerufen wird, wird der Besitz der Nachricht von der `priority_buffer`-Klasse auf den ersten Zielblock übertragen, der diesen akzeptiert. (Dieses Verhalten ist vergleichbar mit `unbounded_buffer`).

1. Definieren Sie im- **`protected`** Abschnitt die- `reserve_message` Methode.

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   Die `priority_buffer`-Klasse ermöglicht einem Zielblock, eine Nachricht zu reservieren, wenn der Bezeichner der bereitgestellten Nachricht mit dem Bezeichner der Nachricht übereinstimmt, die an erster Position in der Warteschlange steht. Anders ausgedrückt kann die Nachricht von einem Ziel reserviert werden, wenn vom `priority_buffer`-Objekt noch keine weitere Nachricht empfangen und die aktuelle Nachricht noch nicht weitergegeben wurde.

1. Definieren Sie im- **`protected`** Abschnitt die- `consume_message` Methode.

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Die `consume_message`-Methode wird von einem Zielblock aufgerufen, um den Besitz der reservierten Methode zu übertragen.

1. Definieren Sie im- **`protected`** Abschnitt die- `release_message` Methode.

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Die `release_message`-Methode wird von einem Zielblock aufgerufen, um die Reservierung einer Nachricht abzubrechen.

1. Definieren Sie im- **`protected`** Abschnitt die- `resume_propagation` Methode.

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Nachdem eine reservierte Nachricht von einem Zielblock verarbeitet oder freigegeben wurde, wird die `resume_propagation`-Methode von der Laufzeit aufgerufen. Diese Methode gibt alle Nachrichten weiter, die sich in der Ausgabewarteschlange befinden.

1. Definieren Sie im- **`protected`** Abschnitt die- `link_target_notification` Methode.

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   Die Membervariable `_M_pReservedFor` wird von der Basisklasse `source_block` definiert. Diese Membervariable zeigt ggf. auf den Zielblock mit der Reservierung für die Nachricht, die sich an erster Stelle in der Warteschlange befindet. `link_target_notification` wird von der Laufzeit aufgerufen, wenn ein neues Ziel mit dem `priority_buffer`-Objekt verknüpft wird. Diese Methode gibt alle Nachrichten in der Ausgabewarteschlange weiter, wenn kein Ziel eine Reservierung aufweist.

1. Definieren Sie im- **`private`** Abschnitt die- `propagate_priority_order` Methode.

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Diese Methode gibt alle Nachrichten von der Ausgabewarteschlange weiter. Jede Nachricht in der Warteschlange wird für alle Zielblöcke bereitgestellt, bis einer der Zielblöcke die Meldung akzeptiert. Die `priority_buffer`-Klasse behält die Reihenfolge der ausgehenden Nachrichten bei. Daher muss die erste Nachricht in der Ausgabewarteschlange von einem Zielblock akzeptiert werden, bevor eine andere Meldung von dieser Methode für die Zielblöcke bereitgestellt wird.

1. Definieren Sie im- **`protected`** Abschnitt die- `propagate_message` Methode.

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   Die `propagate_message`-Methode ermöglicht der `priority_buffer`-Klasse als Nachrichtenempfänger oder -ziel fungieren. Diese Methode empfängt die vom angegebenen Quellblock bereitgestellte Nachricht und fügt sie in die Prioritätswarteschlange ein. Anschließend werden alle Ausgabenachrichten von der `propagate_message`-Methode asynchron an die Zielblöcke gesendet.

   Die Laufzeit ruft diese Methode auf, wenn Sie die Funktion " [parallelcurrency:: Asend](reference/concurrency-namespace-functions.md#asend) " aufrufen oder wenn der Nachrichtenblock mit anderen Nachrichten Blöcken verbunden ist.

1. Definieren Sie im- **`protected`** Abschnitt die- `send_message` Methode.

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   Die `send_message`-Methode ähnelt der `propagate_message`-Methode. Im Unterschied zu dieser sendet sie die Ausgabemeldungen jedoch synchron.

   Diese Methode wird von der Laufzeit während eines synchronen Sendevorgangs aufgerufen, z. b. beim Aufrufen der Funktion " [parallelcurrency:: Send](reference/concurrency-namespace-functions.md#send) ".

Die `priority_buffer`-Klasse enthält Konstruktorüberladungen, die in vielen Nachrichtenblocktypen verwendet werden. Einige Konstruktorüberladungen akzeptieren [parallelcurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) -oder [parallelcurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) -Objekte, die es ermöglichen, dass der Nachrichtenblock von einem bestimmten Aufgabenplaner verwaltet wird. Andere Konstruktorüberladungen übernehmen eine Filterfunktion. Filterfunktionen ermöglichen Nachrichtenblöcken das Annehmen oder Ablehnen von Nachrichten anhand der Nutzlast. Weitere Informationen zu Nachrichten filtern finden Sie unter [asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md). Weitere Informationen zu Aufgabenplaner finden Sie unter [Taskplaner](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Da die `priority_buffer` -Klasse Nachrichten nach Priorität und dann nach der Reihenfolge sortiert, in der Nachrichten empfangen werden, ist diese Klasse am nützlichsten, wenn Sie Nachrichten asynchron empfängt, z. b. Wenn Sie die Funktion " [parallelcurrency:: Asend](reference/concurrency-namespace-functions.md#asend) " aufzurufen, oder wenn der Nachrichtenblock mit anderen Nachrichten Blöcken verbunden ist.

[Nach[oben](#top)]

## <a name="the-complete-example"></a><a name="complete"></a>Das komplette Beispiel

Im folgenden Beispiel wird die vollständige Definition der `priority_buffer`-Klasse veranschaulicht.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

Das folgende Beispiel führt gleichzeitig eine Anzahl von `asend` -und [parallelcurrency:: Receive](reference/concurrency-namespace-functions.md#receive) -Vorgängen für ein- `priority_buffer` Objekt aus.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

Die `priority_buffer`-Klasse ordnet die Nachrichten zunächst nach der Priorität und anschließend nach der Reihenfolge ihres Empfangs. In diesem Beispiel werden Nachrichten mit höherer numerischer Priorität am Anfang der Warteschlange eingefügt.

[Nach[oben](#top)]

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie die Definition der `priority_buffer` -Klasse in eine Datei mit `priority_buffer.h` dem Namen und das Testprogramm in eine Datei mit dem Namen ein, `priority_buffer.cpp` und führen Sie dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster aus.

**cl.exe/EHsc priority_buffer. cpp**

## <a name="see-also"></a>Weitere Informationen

[Exemplarische Vorgehensweisen Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md)
