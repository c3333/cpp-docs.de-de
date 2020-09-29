---
title: 'Gewusst wie: Erstellen einer Aufgabe, die nach einer Verzögerung abgeschlossen wird'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 80bfdeb7586f9c32592bc408a9de0c9188b77a29
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413787"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Gewusst wie: Erstellen einer Aufgabe, die nach einer Verzögerung abgeschlossen wird

In diesem Beispiel wird gezeigt, wie die Klassen [parallelcurrency:: Task](../../parallel/concrt/reference/task-class.md), [parallelcurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [parallelcurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [parallelcurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [parallelcurrency:: Timer](../../parallel/concrt/reference/timer-class.md)und [parallelcurrency:: Callcenter](../../parallel/concrt/reference/call-class.md) verwendet werden, um eine Aufgabe zu erstellen, die nach einer Verzögerung abgeschlossen wird. Mit dieser Methode können Sie Schleifen erstellen, die gelegentlich Daten abrufen, Timeouts einführen, die Verarbeitung von Benutzereingaben für einen vorab festgelegten Zeitraum verzögern usw.

## <a name="example-complete_after-and-cancel_after_timeout-functions"></a>Beispiel: complete_after-und cancel_after_timeout Funktionen

Im folgenden Beispiel werden die Funktionen `complete_after` und `cancel_after_timeout` dargestellt. Die- `complete_after` Funktion erstellt ein- `task` Objekt, das nach der angegebenen Verzögerung abgeschlossen wird. Sie verwendet ein `timer` -Objekt und ein- `call` Objekt, um ein- `task_completion_event` Objekt nach der angegebenen Verzögerung festzulegen. Mithilfe der- `task_completion_event` Klasse können Sie eine Aufgabe definieren, die abgeschlossen wird, nachdem ein Thread oder ein anderer Task signalisiert hat, dass ein Wert verfügbar ist. Wenn das Ereignis festgelegt ist, werden listeneraufgaben ausgeführt, und ihre Fortsetzungen werden geplant.

> [!TIP]
> Weitere Informationen zu den `timer` -und- `call` Klassen, die Teil der Asynchronous Agents Library sind, finden Sie unter [asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md).

Die- `cancel_after_timeout` Funktion baut auf der- `complete_after` Funktion auf, um eine Aufgabe abzubrechen, wenn diese Aufgabe nicht vor einem angegebenen Timeout beendet wird. Die- `cancel_after_timeout` Funktion erstellt zwei Aufgaben. Der erste Task gibt den Erfolg an und wird nach Abschluss der bereitgestellten Aufgabe abgeschlossen. die zweite Aufgabe zeigt einen Fehler an und wird nach dem angegebenen Timeout abgeschlossen. Die- `cancel_after_timeout` Funktion erstellt eine Fortsetzungs Aufgabe, die ausgeführt wird, wenn die Erfolgs-oder Fehler Aufgabe abgeschlossen ist. Wenn die Fehler Aufgabe zuerst abgeschlossen wird, bricht die Fortsetzung die tokenquelle ab, um die gesamte Aufgabe abzubrechen.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example-compute-count-of-prime-numbers"></a>Beispiel: Berechnen der Anzahl von Primzahlen

Im folgenden Beispiel wird die Anzahl von Primzahlen im Bereich [0, 100000] mehrmals berechnet. Der Vorgang schlägt fehl, wenn er nicht in einem bestimmten Zeitraum beendet wird. Die- `count_primes` Funktion zeigt, wie die-Funktion verwendet wird `cancel_after_timeout` . Sie zählt die Anzahl der primes im angegebenen Bereich und schlägt fehl, wenn die Aufgabe nicht in der angegebenen Zeit beendet wird. Die- `wmain` Funktion Ruft die- `count_primes` Funktion mehrmals auf. Jedes Mal wird das Zeitlimit halbiert. Das Programm wird beendet, nachdem der Vorgang nicht im aktuellen Zeit Limit abgeschlossen wurde.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Wenn Sie diese Technik verwenden, um Aufgaben nach einer Verzögerung abzubrechen, werden alle nicht gestarteten Aufgaben nicht gestartet, nachdem die gesamte Aufgabe abgebrochen wurde. Allerdings ist es wichtig, dass alle Aufgaben mit langer Ausführungszeit rechtzeitig auf den Abbruch reagieren. Weitere Informationen zum Aufgaben Abbruch finden Sie unter [Abbruch in der ppl](cancellation-in-the-ppl.md).

## <a name="complete-code-example"></a>Vollständiges Codebeispiel

Im folgenden finden Sie den gesamten Code für dieses Beispiel:

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen ein, `task-delay.cpp` und führen Sie dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster aus.

**cl.exe/EHsc Task-Delay. cpp**

## <a name="see-also"></a>Weitere Informationen

[Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Task-Klasse (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source-Klasse](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token-Klasse](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event-Klasse](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[Timer-Klasse](../../parallel/concrt/reference/timer-class.md)<br/>
[callclass](../../parallel/concrt/reference/call-class.md)<br/>
[Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Abbruch in der PPL](cancellation-in-the-ppl.md)
