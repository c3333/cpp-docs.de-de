---
title: 'Gewusst wie: Implementieren verschiedener Producer-Consumer-Muster'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 70813adf6715a2bcaf4af7370ce43d99c44263bd
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413774"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Gewusst wie: Implementieren verschiedener Producer-Consumer-Muster

In diesem Thema wird die Implementierung des Producer-Consumer-Musters in der Anwendung beschrieben. Bei diesem Muster sendet der *Producer* Nachrichten an einen Nachrichtenblock, während der *Consumer* Nachrichten aus diesem Block ausliest.

In diesem Thema werden zwei Szenarien beschrieben. Im ersten Szenario muss der Consumer alle Nachrichten empfangen, die der Producer sendet. Im zweiten Szenario ruft der Consumer in regelmäßigen Abständen Daten ab und muss daher nicht jede Nachricht empfangen.

In beiden Beispielen in diesem Thema werden Nachrichten mithilfe von Agents, Nachrichtenblöcken und Nachrichtenübergabefunktionen vom Producer an den Consumer übertragen. Der Producer-Agent verwendet die Funktion " [parallelcurrency:: Send](reference/concurrency-namespace-functions.md#send) ", um Nachrichten in ein [parallelcurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) -Objekt zu schreiben. Der Consumer-Agent verwendet die Funktion " [parallelcurrency:: Receive](reference/concurrency-namespace-functions.md#receive) " zum Lesen von Nachrichten aus einem " [parallelcurrency:: ISource](../../parallel/concrt/reference/isource-class.md) "-Objekt. Beide Agents enthalten einen Sentinelwert, um das Ende der Verarbeitung zu koordinieren.

Weitere Informationen zu asynchronen Agents finden Sie unter [asynchrone Agents](../../parallel/concrt/asynchronous-agents.md). Weitere Informationen zu Nachrichten Blöcken und Nachrichten Übergabe Funktionen finden Sie unter [asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md) und [Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md).

## <a name="example-send-series-of-numbers-to-consumer-agent"></a>Beispiel: Senden von Reihen von Zahlen an den Consumer-Agent

In diesem Beispiel sendet der Producer-Agent eine Reihe von Zahlen an den Consumer-Agent. Diese werden vom Consumer empfangen und ihr Durchschnitt wird berechnet. Anschließend wird der Durchschnitt in die Konsole geschrieben.

In diesem Beispiel wird ein " [parallelcurrency:: Unbounded_buffer](reference/unbounded-buffer-class.md) "-Objekt verwendet, um dem Producer die Warteschlange für Nachrichten Die `unbounded_buffer`-Klasse implementiert `ITarget` und `ISource`, damit Producer und Consumer Nachrichten über einen gemeinsamen Puffer senden und empfangen können. Die Funktionen `send` und `receive` koordinieren die Aufgabe, die Daten vom Producer an den Consumer weiterzugeben.

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
The average is 50.
```

## <a name="example-send-series-of-stock-quotes-to-consumer-agent"></a>Beispiel: Senden von Reihen von Aktienkursen an den Consumer-Agent

In diesem Beispiel sendet der Producer-Agent eine Reihe von Aktienkursen an den Consumer-Agent. Der Consumer-Agent liest den aktuellen Kurs in regelmäßigen Abständen und gibt ihn an der Konsole aus.

Dieses Beispiel ähnelt dem vorherigen, mit dem Unterschied, dass es ein " [parallelcurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) "-Objekt verwendet, um dem Producer zu ermöglichen, eine Nachricht mit dem Consumer gemeinsam zu nutzen. Wie im vorherigen Beispiel implementiert die `overwrite_buffer`-Klasse `ITarget` und `ISource`, sodass Producer und Consumer einen gemeinsamen Nachrichtenpuffer nutzen können.

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe.

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

Anders als bei einem `unbounded_buffer`-Objekt entfernt die `receive`-Funktion die Nachricht nicht aus dem `overwrite_buffer`-Objekt. Wenn der Consumer den Nachrichtenpuffer mehr als einmal ausliest, bevor der Producer diese Nachricht überschreibt, erhält der Empfänger jedes Mal dieselbe Nachricht.

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `producer-consumer.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

**cl.exe/EHsc Producer-Consumer. cpp**

## <a name="see-also"></a>Weitere Informationen

[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchrone Agents](../../parallel/concrt/asynchronous-agents.md)<br/>
[Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md)
