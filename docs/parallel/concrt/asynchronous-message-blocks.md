---
title: Asynchrone Nachrichtenblöcke
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: 6697bdd296a3c71f03bc22986efa47dd586d5d9e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217908"
---
# <a name="asynchronous-message-blocks"></a>Asynchrone Nachrichtenblöcke

Die Agents Library stellt mehrere Nachrichtenblocktypen bereit, mit deren Hilfe Nachrichten threadsicher zwischen Anwendungskomponenten weitergegeben werden können. Diese Nachrichtenblock Typen werden häufig mit den verschiedenen Nachrichten Übergabe Routinen verwendet, wie z. b. " [parallelcurrency:: Send](reference/concurrency-namespace-functions.md#send)", " [parallelcurrency:: Asend](reference/concurrency-namespace-functions.md#asend)", " [parallelcurrency:: Receive](reference/concurrency-namespace-functions.md#receive)" und " [parallelcurrency:: Try_receive](reference/concurrency-namespace-functions.md#try_receive)". Weitere Informationen zu den Nachrichten Übergabe Routinen, die von der Agents Library definiert werden, finden Sie unter [Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md).

## <a name="sections"></a><a name="top"></a>Strecken

Dieses Thema enthält folgende Abschnitte:

- [Quellen und Ziele](#sources_and_targets)

- [Nachrichtenweitergabe](#propagation)

- [Übersicht über Nachrichtenblocktypen](#overview)

- [UNBOUNDED_BUFFER-Klasse](#unbounded_buffer)

- [overwrite_buffer-Klasse](#overwrite_buffer)

- [Single_assignment-Klasse](#single_assignment)

- [callclass](#call)

- [Transformer-Klasse](#transformer)

- [Choice-Klasse](#choice)

- [join- und multitype_join-Klasse](#join)

- [Timer-Klasse](#timer)

- [Nachrichtenfilterung](#filtering)

- [Nachrichtenreservierung](#reservation)

## <a name="sources-and-targets"></a><a name="sources_and_targets"></a>Quellen und Ziele

Quelle und Ziel sind zwei wichtige Beteiligte bei der Nachrichtenübergabe. Eine *Quelle* verweist auf einen Kommunikations Endpunkt, der Nachrichten sendet. Ein *Ziel* bezieht sich auf einen Kommunikations Endpunkt, der Nachrichten empfängt. Sie können sich eine Quelle als Endpunkt vorstellen, von dem gelesen wird, und ein Ziel als Endpunkt, in den geschrieben wird. Anwendungen verbinden Quellen und Ziele miteinander, um *Messaging Netzwerke*zu bilden.

Die Agents Library verwendet zwei abstrakte Klassen zur Darstellung von Quellen und Zielen: [parallelcurrency:: ISource](../../parallel/concrt/reference/isource-class.md) und [parallelcurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md). Nachrichtenblocktypen, die als Quelle dienen, werden von der `ISource`-Klasse abgeleitet, während Nachrichtenblocktypen, die als Ziel dienen, von der `ITarget`-Klasse abgeleitet werden. Nachrichtenblocktypen, die als Quelle und Ziel dienen, werden von der `ISource`-Klasse und der `ITarget`-Klasse abgeleitet.

[Nach[oben](#top)]

## <a name="message-propagation"></a><a name="propagation"></a>Nachrichten Weitergabe

Die *Nachrichten* Weitergabe ist das Senden einer Nachricht von einer Komponente an eine andere. Wenn eine Nachricht für einen Nachrichtenblock bereitgestellt wird, kann er diese Nachricht akzeptieren, ablehnen oder verschieben. Jeder Nachrichtenblocktyp speichert und überträgt Nachrichten auf unterschiedliche Weise. Beispielsweise speichert die `unbounded_buffer`-Klasse eine unendliche Anzahl von Nachrichten, die `overwrite_buffer`-Klasse speichert jeweils nur eine Nachricht, und die Transformatorklasse speichert eine geänderte Version jeder Nachricht. Diese Nachrichtenblocktypen werden im Folgenden ausführlicher beschrieben.

Wenn ein Nachrichtenblock eine Meldung akzeptiert, können optionale Arbeiten durchgeführt werden, und wenn es sich bei dem Nachrichtenblock um eine Quelle handelt, kann die resultierende Nachricht an einen anderen Member im Netzwerk weitergegeben werden. Mithilfe einer Filterfunktion können Nachrichtenblöcke einzelne Nachrichten ablehnen, die nicht empfangen werden sollen. Filter werden weiter unten in diesem Thema im Abschnitt " [Nachrichtenfilterung](#filtering)" ausführlicher beschrieben. Ein Nachrichtenblock, der eine Meldung verschiebt, kann sie reservieren und später verarbeiten. Die Nachrichten Reservierung wird weiter unten in diesem Thema im Abschnitt " [Nachrichten Reservierung](#reservation)" ausführlicher beschrieben.

Mit der Agents Library können Nachrichten von Nachrichtenblöcken synchron oder asynchron übergeben werden. Wenn Sie eine Nachricht synchron an einen Nachrichtenblock übergeben, z. B. mit der `send`-Funktion, wird der aktuelle Kontext von der Laufzeit blockiert, bis die Nachricht vom Zielblock akzeptiert oder abgelehnt wird. Wenn Sie eine Nachricht asynchron an einen Nachrichtenblock übergeben, z. B. mit der `asend`-Funktion, wird die Nachricht von der Laufzeit für das Ziel bereitgestellt, und wenn die Nachricht vom Ziel akzeptiert wird, wird von der Laufzeit eine asynchrone Aufgabe geplant, um die Nachricht an den Empfänger weiterzugeben. Die Laufzeit verwendet einfache Aufgaben, um Nachrichten auf kooperative Weise weiterzugeben. Weitere Informationen zu Lightweight-Aufgaben finden Sie unter [Taskplaner](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Anwendungen verbinden Quellen und Ziele, und bilden so Messagingnetzwerke. Normalerweise verknüpfen Sie das Netzwerk, und rufen `send` oder `asend` auf, um Daten an das Netzwerk zu übergeben. Um einen Quell Nachrichtenblock mit einem Ziel zu verbinden, wenden Sie die Methode " [parallelcurrency:: ISource:: link_target](reference/isource-class.md#link_target) " an. Wenn Sie einen Quell Block von einem Ziel trennen möchten, müssen Sie die Methode " [parallelcurrency:: ISource:: unlink_target](reference/isource-class.md#unlink_target) " aufzurufen. Um einen Quell Block von allen Zielen zu trennen, müssen Sie die Methode " [parallelcurrency:: ISource:: unlink_targets](reference/isource-class.md#unlink_targets) " aufzurufen. Wenn sich einer der vordefinierten Nachrichtenblocktypen nicht mehr im Bereich befindet oder zerstört wird, werden die Verknüpfungen mit den Zielblöcken automatisch aufgehoben. Bei einigen Nachrichtenblocktypen ist die maximale Anzahl der Ziele eingeschränkt, in die geschrieben werden kann. Im folgenden Abschnitt werden die Einschränkungen beschrieben, die für die vordefinierten Nachrichtenblocktypen gelten.

[Nach[oben](#top)]

## <a name="overview-of-message-block-types"></a><a name="overview"></a>Übersicht über Nachrichten Block Typen

In der folgenden Tabelle wird die Rolle der wichtigen Nachrichtenblocktypen kurz beschrieben.

[unbounded_buffer](#unbounded_buffer)<br/>
Speichert eine Nachrichtenwarteschlange.

[overwrite_buffer](#overwrite_buffer)<br/>
Speichert eine Nachricht, die mehrmals geschrieben und gelesen werden kann.

[single_assignment](#single_assignment)<br/>
Speichert eine Nachricht, die ein Mal geschrieben und gelesen werden kann.

[call](#call)<br/>
Führt beim Empfang einer Nachricht Arbeiten aus.

[ans](#transformer)<br/>
Führt Arbeiten aus, wenn Daten empfangen werden, und sendet das Ergebnis dieser Arbeiten an einen anderen Zielblock. Die `transformer`-Klasse kann für unterschiedliche Eingabe- und Ausgabetypen verwendet werden.

[choice](#choice)<br/>
Wählt aus einer Gruppe Quellen die erste verfügbare Nachricht aus.

[join und multitype join](#join)<br/>
Warten, bis alle Nachrichten, die von einer Gruppe Quellen empfangen werden sollen, empfangen wurden, und setzen die Nachrichten zu einer Nachricht für einen anderen Nachrichtenblock zusammen.

[Messer](#timer)<br/>
Sendet eine Nachricht in regelmäßigen Intervallen an einen Zielblock.

Diese Nachrichtenblocktypen haben unterschiedliche Eigenschaften, sodass sie für unterschiedliche Situationen nützlich sind. Zu diesen Eigenschaften zählen folgende:

- *Weitergabetyp*: gibt an, ob der Nachrichtenblock als Datenquelle, als Empfänger von Daten oder beides fungiert.

- *Nachrichten*Sortierung: gibt an, ob der Nachrichtenblock die ursprüngliche Reihenfolge beibehält, in der Nachrichten gesendet oder empfangen werden. Vordefinierte Nachrichtenblocktypen behalten die ursprüngliche Reihenfolge bei, in der Nachrichten gesendet oder empfangen werden.

- *Quell Anzahl*: die maximale Anzahl von Quellen, aus denen der Nachrichtenblock gelesen werden kann.

- *Ziel Anzahl*: die maximale Anzahl von Zielen, in die der Nachrichtenblock schreiben kann.

In der folgenden Tabelle wird der Bezug dieser Eigenschaften auf die verschiedenen Nachrichtenblocktypen beschrieben.

|Nachrichtenblocktyp|Weitergabetyp (Quelle, Ziel oder beides)|Nachrichtenreihenfolge (sortiert oder nicht sortiert)|Quellenanzahl|Zielanzahl|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|Both|Bestellt|Unbegrenzt|Unbegrenzt|
|`overwrite_buffer`|Both|Bestellt|Unbegrenzt|Unbegrenzt|
|`single_assignment`|Both|Bestellt|Unbegrenzt|Unbegrenzt|
|`call`|Ziel|Bestellt|Unbegrenzt|Nicht zutreffend|
|`transformer`|Both|Bestellt|Unbegrenzt|1|
|`choice`|Both|Bestellt|10|1|
|`join`|Both|Bestellt|Unbegrenzt|1|
|`multitype_join`|Both|Bestellt|10|1|
|`timer`|`Source`|Nicht zutreffend|Nicht zutreffend|1|

In den folgenden Abschnitten werden die Nachrichtenblocktypen ausführlicher beschrieben.

[Nach[oben](#top)]

## <a name="unbounded_buffer-class"></a><a name="unbounded_buffer"></a>UNBOUNDED_BUFFER-Klasse

Die Klasse " [parallelcurrency:: Unbounded_buffer](reference/unbounded-buffer-class.md) " stellt eine allgemeine asynchrone Messaging Struktur dar. Diese Klasse speichert eine FIFO-Nachrichtenwarteschlange (First In, First Out), in die mehrere Quellen Nachrichten schreiben oder aus der mehrere Ziele Nachrichten auslesen können. Wenn ein Ziel eine Nachricht von einem `unbounded_buffer`-Objekt empfängt, wird diese Nachricht aus der Nachrichtenwarteschlange entfernt. Daher können die einzelnen Nachrichten nur von einem Ziel empfangen werden, obwohl ein `unbounded_buffer`-Objekt mehrere Ziele haben kann. Die `unbounded_buffer`-Klasse ist hilfreich, wenn Sie mehrere Nachrichten an eine andere Komponente übergeben möchten und diese Komponente alle Nachrichten empfangen muss.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die grundlegende Struktur für die Verwendung der `unbounded_buffer`-Klasse veranschaulicht. In diesem Beispiel werden drei Werte an ein `unbounded_buffer`-Objekt gesendet und wieder von diesem Objekt zurückgegeben.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
334455
```

Ein umfassendes Beispiel, das die Verwendung der-Klasse veranschaulicht, finden Sie unter Gewusst `unbounded_buffer` [wie: Implementieren verschiedener Producer-Consumer-Muster](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[Nach[oben](#top)]

## <a name="overwrite_buffer-class"></a><a name="overwrite_buffer"></a>overwrite_buffer-Klasse

Die Klasse " [parallelcurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) " ähnelt der- `unbounded_buffer` Klasse, mit dem Unterschied, dass ein `overwrite_buffer` Objekt nur eine Nachricht speichert. Wenn ein Ziel eine Nachricht von einem `overwrite_buffer`-Objekt empfängt, wird diese Nachricht darüber hinaus auch nicht aus dem Puffer entfernt. Daher empfangen mehrere Ziele eine Kopie der Nachricht.

Die `overwrite_buffer`-Klasse ist hilfreich, wenn Sie mehrere Nachrichten an eine andere Komponente übergeben möchten, diese Komponente jedoch nur den letzten Wert benötigt. Diese Klasse ist darüber hinaus auch hilfreich, wenn Sie eine Nachricht an mehreren Komponenten übertragen möchten.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die grundlegende Struktur für die Verwendung der `overwrite_buffer`-Klasse veranschaulicht. In diesem Beispiel werden drei Werte an ein `overwrite _buffer`-Objekt gesendet, und der aktuelle Wert wird dreimal aus dem gleichen Objekt gelesen. Dieses Beispiel ähnelt dem Beispiel für die `unbounded_buffer`-Klasse. Allerdings speichert die `overwrite_buffer`-Klasse nur eine Nachricht. Darüber hinaus wird die Nachricht von der Laufzeit nicht aus einem `overwrite_buffer`-Objekt entfernt, nachdem sie gelesen wurde.

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
555555
```

Ein umfassendes Beispiel, das die Verwendung der-Klasse veranschaulicht, finden Sie unter Gewusst `overwrite_buffer` [wie: Implementieren verschiedener Producer-Consumer-Muster](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[Nach[oben](#top)]

## <a name="single_assignment-class"></a><a name="single_assignment"></a>Single_assignment-Klasse

Die Klasse " [parallelcurrency:: Single_assignment](../../parallel/concrt/reference/single-assignment-class.md) " ähnelt der- `overwrite_buffer` Klasse, mit der Ausnahme, dass ein- `single_assignment` Objekt nur einmal geschrieben werden kann. Wenn ein Ziel eine Nachricht von einem `overwrite_buffer`-Objekt empfängt, wird diese Nachricht wie bei der `single_assignment`-Klasse nicht aus diesem Objekt entfernt. Daher empfangen mehrere Ziele eine Kopie der Nachricht. Die `single_assignment`-Klasse ist hilfreich, wenn Sie eine Nachricht an mehrere Komponenten übertragen möchten.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die grundlegende Struktur für die Verwendung der `single_assignment`-Klasse veranschaulicht. In diesem Beispiel werden drei Werte an ein `single_assignment`-Objekt gesendet, und der aktuelle Wert wird dreimal aus dem gleichen Objekt gelesen. Dieses Beispiel ähnelt dem Beispiel für die `overwrite_buffer`-Klasse. Die `overwrite_buffer`-Klasse und die `single_assignment`-Klasse speichern jeweils eine einzelne Nachricht, in die `single_assignment`-Klasse kann jedoch nur einmal geschrieben werden.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
333333
```

Ein umfassendes Beispiel, das zeigt, wie die-Klasse verwendet wird, finden Sie unter Exemplarische Vorgehensweise `single_assignment` [: Implementieren von Futures](../../parallel/concrt/walkthrough-implementing-futures.md).

[Nach[oben](#top)]

## <a name="call-class"></a><a name="call"></a>callclass

Die " [parallelcurrency:: callclass](../../parallel/concrt/reference/call-class.md) " fungiert als Nachrichtenempfänger, der beim Empfangen von Daten eine Arbeitsfunktion ausführt. Bei dieser Arbeitsfunktion kann es sich um einen Lambdaausdruck, ein Funktionsobjekt oder einen Funktionszeiger handeln. Ein `call`-Objekt verhält sich anders als ein gewöhnlicher Funktionsaufruf, da es parallel zu anderen Komponenten agiert, die Nachrichten an das Objekt senden. Wenn ein `call`-Objekt beim Empfang einer Nachricht Arbeiten ausführt, fügt es die empfangene Nachricht einer Warteschlange hinzu. Jedes `call`-Objekt verarbeitet Nachrichten in der Warteschlange in der Reihenfolge, in der sie empfangen werden.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die grundlegende Struktur für die Verwendung der `call`-Klasse veranschaulicht. In diesem Beispiel wird ein `call`-Objekt erstellt, das jeden empfangenen Wert an der Konsole ausgibt. Anschließend werden im Beispiel drei Werte an das `call`-Objekt gesendet. Da das- `call` Objekt Nachrichten in einem separaten Thread verarbeitet, verwendet dieses Beispiel auch eine Counter-Variable und ein [Ereignis](../../parallel/concrt/reference/event-class.md) Objekt, um sicherzustellen, dass das- `call` Objekt alle Nachrichten verarbeitet, bevor die `wmain` Funktion zurückgegeben wird.

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
334455
```

Ein umfassendes Beispiel, das zeigt, wie die `call` -Klasse verwendet wird, finden Sie unter Gewusst [wie: Bereitstellen von Arbeitsfunktionen für die Call-und Transformer-Klassen](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).

[Nach[oben](#top)]

## <a name="transformer-class"></a><a name="transformer"></a>Transformer-Klasse

Die Klasse " [parallelcurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) " fungiert sowohl als Nachrichtenempfänger als auch als Nachrichten Absender. Die `transformer`-Klasse ist gleicht der `call`-Klasse, da sie beim Empfang von Daten eine benutzerdefinierte Arbeitsfunktion ausführt. Die `transformer`-Klasse sendet jedoch auch das Ergebnis der Arbeitsfunktion an Empfängerobjekte. Wie ein `call`-Objekt agiert ein `transformer`-Objekt parallel zu anderen Komponenten, die Nachrichten an das Objekt senden. Wenn ein `transformer`-Objekt beim Empfang einer Nachricht Arbeiten ausführt, fügt es die empfangene Nachricht einer Warteschlange hinzu. Jedes `transformer`-Objekt verarbeitet die eigenen Nachrichten in der Warteschlange in der Reihenfolge, in der sie empfangen werden.

Die `transformer`-Klasse sendet die eigene Nachricht an ein Ziel. Wenn Sie den- `_PTarget` Parameter im Konstruktor auf festlegen `NULL` , können Sie das Ziel später angeben, indem Sie die [parallelcurrency:: link_target](reference/source-block-class.md#link_target) -Methode aufrufen.

Im Gegensatz zu allen anderen asynchronen Nachrichtenblocktypen, die von der Agents Library bereitgestellt werden, kann die `transformer`-Klasse für unterschiedliche Eingabe- und Ausgabetypen verwendet werden. Aufgrund dieser Fähigkeit, Daten von einem Typ in einen anderen transformieren zu können, ist die `transformer`-Klasse in vielen parallelen Netzwerken eine wichtige Komponente. Zudem können Sie differenziertere Parallelitätsfunktionen in die Arbeitsfunktion eines `transformer`-Objekts integrieren.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die grundlegende Struktur für die Verwendung der `transformer`-Klasse veranschaulicht. In diesem Beispiel wird ein- `transformer` Objekt erstellt, das jeden Eingabe **`int`** Wert um 0,33 multipliziert, um einen **`double`** Wert als Ausgabe zu erzeugen. Anschließend werden im Beispiel transformierten Werte vom selben `transformer`-Objekt empfangen und an der Konsole ausgegeben.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
10.8914.5218.15
```

Ein umfassendes Beispiel, das zeigt, wie die- `transformer` Klasse verwendet wird, finden Sie unter Gewusst [wie: Verwenden von Transformer in einer Daten Pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

[Nach[oben](#top)]

## <a name="choice-class"></a><a name="choice"></a>Choice-Klasse

Die Klasse " [parallelcurrency:: Choice](../../parallel/concrt/reference/choice-class.md) " wählt die erste verfügbare Nachricht aus einer Gruppe von Quellen aus. Die `choice` -Klasse stellt einen Steuerungs Fluss Mechanismus anstelle eines Datenfluss Mechanismus dar (im Thema [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md) werden die Unterschiede zwischen Datenfluss und Ablauf Steuerung beschrieben).

Der Lesevorgang bei einem choice-Objekt gleicht dem Aufruf der API-Funktion `WaitForMultipleObjects` von Windows, wenn der `bWaitAll`-Parameter auf `FALSE` festgelegt ist. Die `choice`-Klasse bindet Daten jedoch nicht an ein externes Synchronisierungsobjekt, sondern an das Ereignis selbst.

In der Regel verwenden Sie die- `choice` Klasse zusammen mit der Funktion " [parallelcurrency:: Receive](reference/concurrency-namespace-functions.md#receive) ", um den Steuerungs Fluss in Ihrer Anwendung zu steuern. Verwenden Sie die `choice`-Klasse, wenn Sie unter Nachrichtenpuffern auswählen müssen, die andere Typen aufweisen. Verwenden Sie die `single_assignment`-Klasse, wenn Sie unter Nachrichtenpuffern auswählen müssen, die denselben Typ aufweisen.

Es ist wichtig, in welcher Reihenfolge Quellen mit einem `choice`-Objekt verknüpft werden, da die Reihenfolge bestimmen kann, welche Nachricht ausgewählt wird. Stellen Sie sich beispielsweise den Fall vor, dass mehrere Nachrichtenpuffer, die bereits eine Nachricht enthalten, mit einem `choice`-Objekt verknüpft werden. Das `choice`-Objekt wählt die Nachricht aus der ersten Quelle aus, mit der es verknüpft wird. Nach der Verknüpfung aller Quellen behält das `choice`-Objekt die Reihenfolge, in der die einzelnen Quellen eine Nachricht empfangen, bei.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die grundlegende Struktur für die Verwendung der `choice`-Klasse veranschaulicht. In diesem Beispiel wird die Funktion " [parallelcurrency:: Make_choice](reference/concurrency-namespace-functions.md#make_choice) " zum Erstellen eines- `choice` Objekts verwendet, das zwischen drei Nachrichten Blöcken auswählt. Anschließend werden im Beispiel verschiedene Fibonacci-Zahlen berechnet, und jedes Ergebnis wird in einem anderen Nachrichtenblock gespeichert. Im Beispiel wird dann in der Konsole eine Meldung angezeigt, die auf dem Vorgang basiert, der zuerst beendet wurde.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe:

```Output
fib35 received its value first. Result = 9227465
```

Da der Task, der<sup>die 35-</sup> te-Datei "fbonacci" berechnet, nicht garantiert zuerst abgeschlossen wird, kann die Ausgabe dieses Beispiels variieren.

In diesem Beispiel wird der " [parallelcurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) -Algorithmus verwendet, um die" fbonacci "-Zahlen parallel zu berechnen. Weitere Informationen zu `parallel_invoke` finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

Ein vollständiges Beispiel, das zeigt, wie die- `choice` Klasse verwendet wird, finden [Sie unter Gewusst wie: Auswählen von abgeschlossenen Aufgaben](../../parallel/concrt/how-to-select-among-completed-tasks.md).

[Nach[oben](#top)]

## <a name="join-and-multitype_join-classes"></a><a name="join"></a>Join-und multitype_join-Klassen

Mit den Klassen " [parallelcurrency:: Join](../../parallel/concrt/reference/join-class.md) " und " [parallelcurrency:: multitype_join](../../parallel/concrt/reference/multitype-join-class.md) " können Sie warten, bis jeder Member einer Gruppe von Quellen eine Nachricht empfängt. Die `join`-Klasse wird für Quellobjekte verwendet, die einen allgemeinen Nachrichtentyp aufweisen. Die `multitype_join`-Klasse wird für Quellobjekte verwendet, die andere Nachrichtentypen aufweisen können.

Der Lesevorgang bei einem `join` oder einem `multitype_join`-Objekt ähnelt dem Aufrufen der API-Funktion `WaitForMultipleObjects` von Windows, wenn der `bWaitAll`-Parameter auf `TRUE` festgelegt ist. Ähnlich wie ein `choice`-Objekt verwenden das `join`- und das `multitype_join`-Objekt einen Ereignismechanismus, der Daten nicht an ein externes Synchronisierungsobjekt, sondern an das Ereignis selbst bindet.

Beim Lesen aus einem- `join` Objekt wird ein Std::[Vector](../../standard-library/vector-class.md) -Objekt erzeugt. Beim Lesen aus einem- `multitype_join` Objekt wird ein Std::[Tupel](../../standard-library/tuple-class.md) -Objekt erzeugt. Elemente treten in diesen Objekten in der Reihenfolge auf, in der die entsprechenden Quellpuffer mit dem `join`-Objekt oder mit dem `multitype_join`-Objekt verknüpft werden. Da die Reihenfolge, in der Quellpuffer mit einem `join`-Objekt oder einem `multitype_join`-Objekt verknüpft werden, von der Reihenfolge der Elemente im resultierenden `vector`-Objekt oder `tuple`-Objekt abhängig ist, wird empfohlen, die Verknüpfung zwischen einem vorhandenen Quellpuffer und einem Join nicht aufzuheben. Andernfalls ist das daraus folgende Verhalten möglicherweise undefiniert.

### <a name="greedy-versus-non-greedy-joins"></a>Gierige und nicht gierige Joins

Die `join`-Klasse und die `multitype_join`-Klasse unterstützen das Konzept gieriger und nicht gieriger Joins. Ein *gieriger Join* akzeptiert eine Nachricht aus jeder seiner Quellen, wenn Nachrichten verfügbar werden, bis alle Nachrichten verfügbar sind. Ein *nicht gieriger Join* empfängt Nachrichten in zwei Phasen. Zunächst wartet ein nicht gieriger Join, bis eine Nachricht aus eine der Quelle bereitgestellt wird. Nachdem alle Quellmeldungen verfügbar sind, versucht ein nicht gieriger Join dann, diese Nachrichten zu reservieren. Wenn alle Nachrichten reserviert werden können, werden die einzelnen Nachrichten verarbeitet und an das Ziel weitergegeben. Wenn dies nicht der Fall ist, werden die Nachrichtenreservierungen freigegeben oder abgebrochen und es wird gewartet, bis die einzelnen Quellen eine Nachricht empfangen.

Gierige Joins erzielen im Vergleich zu nicht gierigen Joins eine bessere Leistung, da sie Nachrichten sofort empfangen. In seltenen Fällen können gierige Joins jedoch zu Deadlocks führen. Verwenden Sie einen nicht gierigen Join, wenn Sie mehrere Joins haben, die ein oder mehrere gemeinsame Quellobjekte enthalten.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die grundlegende Struktur für die Verwendung der `join`-Klasse veranschaulicht. In diesem Beispiel wird die Funktion " [parallelcurrency:: Make_join](reference/concurrency-namespace-functions.md#make_join) " zum Erstellen eines- `join` Objekts verwendet, das von drei- `single_assignment` Objekten empfängt. In diesem Beispiel werden verschiedene Fibonacci-Zahlen berechnet, das jeweilige Ergebnis wird in einem eigenen `single_assignment`-Objekt gespeichert, und die einzelnen Ergebnisse im `join`-Objekt werden an der Konsole ausgegeben. Dieses Beispiel ähnelt dem Beispiel für die `choice`-Klasse; im Unterschied dazu wartet die `join`-Klasse jedoch, bis alle Nachrichtenblöcke eine Nachricht empfangen haben.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

In diesem Beispiel wird der " [parallelcurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) -Algorithmus verwendet, um die" fbonacci "-Zahlen parallel zu berechnen. Weitere Informationen zu `parallel_invoke` finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

Vollständige Beispiele, die zeigen, wie Sie die- `join` Klasse verwenden, finden [Sie unter Gewusst wie: Auswählen von abgeschlossenen Aufgaben](../../parallel/concrt/how-to-select-among-completed-tasks.md) und Exemplarische Vorgehensweise [: Verwenden von Join zum Verhindern von](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)Deadlocks.

[Nach[oben](#top)]

## <a name="timer-class"></a><a name="timer"></a>Timer-Klasse

Die parallelcurrency::[Timer-Klasse](../../parallel/concrt/reference/timer-class.md) fungiert als Nachrichtenquelle. Ein `timer`-Objekt sendet nach Ablauf einer angegebenen Zeitdauer eine Nachricht an ein Ziel. Die `timer`-Klasse ist hilfreich, wenn der Versand einer Nachricht verzögert werden muss oder wenn eine Nachricht in regelmäßigen Intervallen gesendet werden muss.

Die `timer`-Klasse sendet die eigene Nachricht an nur ein Ziel. Wenn Sie den- `_PTarget` Parameter im Konstruktor auf festlegen `NULL` , können Sie das Ziel später angeben, indem Sie die [parallelcurrency:: ISource:: link_target](reference/source-block-class.md#link_target) -Methode aufrufen.

Ein `timer`-Objekt kann ein sich wiederholendes oder ein sich nicht wiederholendes Objekt sein. Um einen sich wiederholenden Timer zu erstellen, übergeben **`true`** Sie für den- `_Repeating` Parameter, wenn Sie den-Konstruktor aufrufen. Andernfalls übergeben **`false`** Sie für den- `_Repeating` Parameter, um einen nicht wiederholenden Timer zu erstellen. Wenn das Timer-Objekt ein sich wiederholendes Objekt ist, wird dieselbe Nachricht nach jedem Intervall an das entsprechende Ziel gesendet.

Die Agents Library erstellt `timer`-Objekte im nicht gestarteten Zustand. Um ein Timer-Objekt zu starten, müssen Sie die Methode " [parallelcurrency:: Timer:: Start](reference/timer-class.md#start) " aufzurufen. Um ein- `timer` Objekt zu entfernen, zerstören Sie das-Objekt, oder wenden Sie die Methode " [parallelcurrency:: Timer:: stoppt](reference/timer-class.md#stop) " an Um einen sich wiederholenden Timer anzuhalten, wenden Sie die Methode " [parallelcurrency:: Timer::p ause](reference/timer-class.md#pause) " an.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die grundlegende Struktur für die Verwendung der `timer`-Klasse veranschaulicht. Im Beispiel wird mit dem `timer`-Objekt und dem `call`-Objekt der Status eines längeren Vorgangs angegeben.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe:

```Output
Computing fib(42)..................................................result is 267914296
```

Ein umfassendes Beispiel, das die Verwendung der- `timer` Klasse veranschaulicht, finden [Sie unter Gewusst wie: Senden einer Nachricht in regelmäßigen Abständen](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).

[Nach[oben](#top)]

## <a name="message-filtering"></a><a name="filtering"></a>Nachrichtenfilterung

Wenn Sie ein Nachrichtenblock Objekt erstellen, können Sie eine *Filterfunktion* angeben, die bestimmt, ob der Nachrichtenblock eine Nachricht akzeptiert oder ablehnt. Eine Filterfunktion ist eine hilfreiche Möglichkeit, um sicherzustellen, dass nur bestimmte Werte von einem Nachrichtenblock empfangen werden.

Im folgenden Beispiel wird veranschaulicht, wie ein `unbounded_buffer`-Objekt erstellt wird, das eine Filterfunktion verwendet, um nur gerade Zahlen zu akzeptieren. Ungerade Zahlen werden vom `unbounded_buffer`-Objekt zurückgewiesen, sodass ungerade Zahlen nicht an die Zielblöcke weitergegeben werden.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
0 2 4 6 8
```

Eine Filterfunktion kann eine Lambda-Funktion, ein Funktionsobjekt oder ein Funktionszeiger sein. Jede Filterfunktion nimmt eines der folgenden Formate an.

```Output
bool (T)
bool (T const &)
```

Um das unnötige Kopieren von Daten zu vermeiden, verwenden Sie das zweite Format bei einem aggregierten Typ, der anhand des Werts weitergegeben wird.

Die Nachrichtenfilterung unterstützt das *Daten* Fluss Programmiermodell, in dem Komponenten Berechnungen ausführen, wenn Sie Daten empfangen. Beispiele für die Verwendung von Filterfunktionen zum Steuern des Datenflusses in einem Nachrichten Übergabe Netzwerk finden Sie unter Gewusst [wie: Verwenden eines Nachrichten Block Filters](../../parallel/concrt/how-to-use-a-message-block-filter.md), Exemplarische Vorgehensweise: [Erstellen eines Daten](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)Fluss-Agents und Exemplarische Vorgehensweise [: Erstellen eines Bild Verarbeitungs Netzwerks](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[Nach[oben](#top)]

## <a name="message-reservation"></a><a name="reservation"></a>Nachrichten Reservierung

Die *Nachrichten Reservierung* ermöglicht einem Nachrichtenblock, eine Nachricht zur späteren Verwendung zu reservieren. In aller Regel wird die Nachrichtenreservierung nicht direkt verwendet. Kenntnisse der Nachrichtenreservierung helfen Ihnen jedoch möglicherweise, das Verhalten vordefinierter Nachrichtenblocktypen besser zu verstehen.

Beispiel: gierige und nicht gierige Joins. Beide Jointypen verwenden die Nachrichtenreservierung, um Meldungen für die spätere Verwendung zu reservieren. Wie bereits beschrieben, werden Nachrichten bei nicht gierigen Joins in zwei Phasen empfangen. In der ersten Phase wartet ein nicht gieriges `join`-Objekt, bis von den einzelnen Quellen eine Nachricht empfangen wurde. Ein nicht gieriger Join versucht anschließend, jede dieser Nachrichten zu reservieren. Wenn alle Nachrichten reserviert werden können, werden die einzelnen Nachrichten verarbeitet und an das Ziel weitergegeben. Wenn dies nicht der Fall ist, werden die Nachrichtenreservierungen freigegeben oder abgebrochen und es wird gewartet, bis die einzelnen Quellen eine Nachricht empfangen.

Bei einem gierigen Join, der auch Eingabenachrichten aus einer Reihe von Quellen liest, werden mithilfe der Nachrichtenreservierung weitere Nachrichten gelesen, während darauf gewartet wird, dass eine Nachricht von jeder Quelle empfangen wird. Angenommen, ein gieriger Join empfängt Nachrichten vom Nachrichtenblock `A` und vom Nachrichtenblock `B`. Wenn der gierige Join zwei Nachrichten von B empfängt, jedoch noch keine Nachrichten von `A` erhalten hat, wird die eindeutige Nachrichten-ID für die zweite Nachrichten von `B` vom gierigen Join gespeichert. Nachdem der gierige Join eine Meldung von `A` empfangen hat und diese Nachrichten weitergibt, wird anhand dieser Nachrichten-ID ermittelt, ob die zweite Nachricht von `B` weiterhin verfügbar ist.

Sie können die Nachrichtenreservierung verwenden, wenn Sie eigene Nachrichtenblocktypen implementieren. Ein Beispiel zum Erstellen eines benutzerdefinierten Nachrichtenblock Typs finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Nachrichten Blocks](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).

[Nach[oben](#top)]

## <a name="see-also"></a>Weitere Informationen

[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)
