---
title: Funktionen zum Übergeben von Meldungen
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 3709e7b5280b96b2b77ec850a06ed15d0e42a7e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194627"
---
# <a name="message-passing-functions"></a>Funktionen zum Übergeben von Meldungen

Die Bibliothek für asynchrone Agents bietet verschiedene Funktionen, mit denen Sie Nachrichten zwischen Komponenten übergeben können.

Diese Nachrichten Übergabe Funktionen werden mit den verschiedenen Nachrichtenblock Typen verwendet. Weitere Informationen zu den Nachrichtenblock Typen, die vom Concurrency Runtime definiert werden, finden Sie unter [asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="sections"></a><a name="top"></a>Strecken

In diesem Thema werden die folgenden Nachrichten Übergabe Funktionen beschrieben:

- [Senden und Asend](#send)

- [empfangen und Try_receive](#receive)

- [Beispiele](#examples)

## <a name="send-and-asend"></a><a name="send"></a>Senden und Asend

Die Funktion " [parallelcurrency:: Send](reference/concurrency-namespace-functions.md#send) " sendet synchron eine Nachricht an das angegebene Ziel, und die Funktion " [parallelcurrency:: Asend](reference/concurrency-namespace-functions.md#asend) " sendet eine Nachricht asynchron an das angegebene Ziel. Sowohl die `send` -als auch die- `asend` Funktion warten, bis das Ziel anzeigt, dass die Nachricht letztendlich akzeptiert oder abgelehnt wird.

Die- `send` Funktion wartet, bis das Ziel die Nachricht annimmt oder ablehnt, bevor Sie zurückkehrt. Die `send` Funktion gibt zurück, **`true`** Wenn die Nachricht übermittelt wurde, und **`false`** andernfalls. Da die `send` Funktion synchron funktioniert, wartet die `send` Funktion, bis das Ziel die Nachricht empfängt, bevor Sie zurückgegeben wird.

Umgekehrt wartet die `asend` Funktion nicht darauf, dass das Ziel die Nachricht annimmt oder ablehnt, bevor Sie zurückkehrt. Stattdessen gibt die `asend` Funktion zurück, **`true`** Wenn das Ziel die Nachricht annimmt und Sie letztendlich übernimmt. Andernfalls `asend` gibt den **`false`** Wert zurück, um anzugeben, dass das Ziel die Nachricht abgelehnt hat oder die Entscheidung über die Nachricht, ob die Nachricht übernommen wird, verschoben hat.

[Nach[oben](#top)]

## <a name="receive-and-try_receive"></a><a name="receive"></a>empfangen und Try_receive

Die Funktionen " [parallelcurrency:: Receive](reference/concurrency-namespace-functions.md#receive) " und " [parallelcurrency:: Try_receive](reference/concurrency-namespace-functions.md#try_receive) " lesen Daten aus einer bestimmten Quelle. Die `receive` Funktion wartet darauf, dass Daten verfügbar werden, während die `try_receive` Funktion sofort zurückgegeben wird.

Verwenden Sie die- `receive` Funktion, wenn Sie über die Daten verfügen müssen, um fortzufahren. Verwenden Sie die- `try_receive` Funktion, wenn Sie den aktuellen Kontext nicht blockieren dürfen oder wenn die Daten nicht fortgesetzt werden müssen.

[Nach[oben](#top)]

## <a name="examples"></a><a name="examples"></a> Beispiele

Beispiele, in denen die `send` `asend` Funktionen und verwendet `receive` werden, finden Sie in den folgenden Themen:

- [Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)

- [Gewusst wie: Implementieren verschiedener Producer-Consumer-Muster](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Gewusst wie: Bereitstellen von Arbeitsfunktionen für die Call-und Transformer-Klassen](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Gewusst wie: Verwenden von Transformer in einer Daten Pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Gewusst wie: Auswählen von abgeschlossenen Aufgaben](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Gewusst wie: Senden einer Nachricht in regelmäßigen Abständen](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Gewusst wie: Verwenden eines Nachrichten Block Filters](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[Nach[oben](#top)]

## <a name="see-also"></a>Weitere Informationen

[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send-Funktion](reference/concurrency-namespace-functions.md#send)<br/>
[ASend-Funktion](reference/concurrency-namespace-functions.md#asend)<br/>
[Receive-Funktion](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive-Funktion](reference/concurrency-namespace-functions.md#try_receive)
