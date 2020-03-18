---
title: Ausnahmebehandlung in der Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
ms.openlocfilehash: 4c7fee363da023b9252471a35aaecd262a55f17c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427464"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Ausnahmebehandlung in der Concurrency Runtime

Die Concurrency Runtime übermittelt viele Arten von Fehlern mithilfe der C++-Ausnahmebehandlung. Zu diesen Fehlern zählen die falsche Verwendung der Runtime, Runtime-Fehler wie etwa das Nichtabrufen einer Ressource sowie Fehler, die in Arbeitsfunktionen auftreten, die Sie für Aufgaben und Aufgabengruppen bereitstellen. Wenn eine Aufgabe oder eine Aufgabengruppe eine Ausnahme auslöst, wird diese Ausnahme von der Runtime gespeichert und an den Kontext gemarshallt, der wartet, bis die Aufgabe oder Aufgabengruppe beendet wird. Bei Komponenten wie bei einfachen Aufgaben und Agents verwaltet die Runtime keine Ausnahmen. In diesen Fällen müssen Sie einen eigenen Mechanismus für die Ausnahmenbehandlung implementieren. In diesem Thema wird beschrieben, wie die Runtime Ausnahmen behandelt, die von Aufgaben, Aufgabengruppen, einfachen Aufgaben und asynchronen Agents ausgelöst werden, und wie auf Ausnahmen von den Anwendungen reagiert wird.

## <a name="key-points"></a>Wesentliche Punkte

- Wenn eine Aufgabe oder eine Aufgabengruppe eine Ausnahme auslöst, wird diese Ausnahme von der Runtime gespeichert und an den Kontext gemarshallt, der wartet, bis die Aufgabe oder Aufgabengruppe beendet wird.

- Umschließen Sie nach Möglichkeit jeden Aufrufe von [parallelcurrency:: Task:: Get](reference/task-class.md#get) und [parallelcurrency:: Task:: Wait](reference/task-class.md#wait) mit einem `try`/`catch` Block, um Fehler zu behandeln, die Sie wiederherstellen können. Die Runtime beendet die App, wenn eine Aufgabe eine Ausnahme auslöst und diese Ausnahme nicht durch die Aufgabe, eine ihrer Fortsetzungen oder die Haupt-App abgefangen wird.

- Eine aufgabenbasierte Fortsetzung wird immer ausgeführt. Dabei ist unerheblich, ob die Vorgängeraufgabe erfolgreich abgeschlossen wurde, eine Ausnahme ausgelöst hat oder abgebrochen wurde. Eine wertbasierte Fortsetzung wird nicht ausgeführt, wenn die Vorgängeraufgabe eine Ausnahme auslöst oder abgebrochen wird.

- Da aufgabenbasierte Fortsetzungen immer ausgeführt werden, erwägen Sie, am Ende der Fortsetzungskette eine aufgabenbasierte Fortsetzung hinzuzufügen. Damit kann sichergestellt werden, dass der Code alle Ausnahmen berücksichtigt.

- Die Laufzeit löst " [parallelcurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) " aus, wenn Sie " [parallelcurrency:: Task:: Get](reference/task-class.md#get) " aufgerufen haben und diese Aufgabe abgebrochen wird.

- Die Runtime verwaltet keine Ausnahmen für einfache Aufgaben und Agents.

## <a name="top"></a>In diesem Dokument

- [Aufgaben und Fortsetzungen](#tasks)

- [Aufgaben Gruppen und parallele Algorithmen](#task_groups)

- [Von der Laufzeit ausgelöste Ausnahmen](#runtime)

- [Mehrere Ausnahmen](#multiple)

- [Abbruch](#cancellation)

- [Einfache Aufgaben](#lwts)

- [Asynchrone Agents](#agents)

## <a name="tasks"></a>Aufgaben und Fortsetzungen

In diesem Abschnitt wird beschrieben, wie die Runtime Ausnahmen behandelt, die von [parallelcurrency:: Task](../../parallel/concrt/reference/task-class.md) -Objekten und deren Fortsetzungen ausgelöst werden. Weitere Informationen zum Task-und Fortsetzungs Modell finden Sie unter [Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Wenn Sie im Text einer Arbeitsfunktion, die Sie an ein `task` Objekt übergeben, eine Ausnahme auslösen, speichert die Runtime diese Ausnahme und Marshalls Sie in den Kontext, der " [parallelcurrency:: Task:: Get](reference/task-class.md#get) " oder " [parallelcurrency:: Task:: Wait](reference/task-class.md#wait)" aufruft. Die Dokument [Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md) beschreibt aufgabenbasierte und Wert basierte Fortsetzungen, aber Zusammenfassend wird eine Wert basierte Fortsetzung einen Parameter vom Typ `T`, und eine aufgabenbasierte Fortsetzung nimmt einen Parameter vom Typ "`task<T>`" an. Wenn eine Aufgabe, die ausgelöst wird, über eine oder mehrere wertbasierte Fortsetzungen verfügt, wird die Ausführung dieser Fortsetzungen nicht geplant. Dieses Verhalten wird im folgenden Beispiel veranschaulicht:

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

Eine aufgabenbasierte Fortsetzung ermöglicht es, jede Ausnahme zu behandeln, die von der Vorgängeraufgabe ausgelöst wird. Eine aufgabenbasierte Fortsetzung wird immer ausgeführt. Dabei ist unerheblich, ob die Aufgabe erfolgreich abgeschlossen wurde, eine Ausnahme ausgelöst hat oder abgebrochen wurde. Wenn eine Aufgabe eine Ausnahme auslöst, wird die Ausführung ihrer aufgabenbasierten Fortsetzungen geplant. Im folgenden Beispiel wird eine Aufgabe dargestellt, die immer ausgelöst wird. Die Aufgabe verfügt über zwei Fortsetzungen: eine ist wertbasiert und die andere aufgabenbasiert. Die aufgabenbasierte Ausnahme wird immer ausgeführt und kann daher die Ausnahme abfangen, die von der Vorgängeraufgabe ausgelöst wird. Wenn das Beispiel darauf wartet, dass beide Fortsetzungen beendet werden, wird die Ausnahme erneut ausgelöst, da die Aufgabenausnahme immer ausgelöst wird, wenn `task::get` oder `task::wait` aufgerufen wird.

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

Es wird empfohlen, aufgabenbasierte Fortsetzungen zu verwenden, um Ausnahmen abzufangen, die Sie behandeln können. Da aufgabenbasierte Fortsetzungen immer ausgeführt werden, erwägen Sie, am Ende der Fortsetzungskette eine aufgabenbasierte Fortsetzung hinzuzufügen. Damit kann sichergestellt werden, dass der Code alle Ausnahmen berücksichtigt. Im folgenden Beispiel wird eine grundlegende wertbasierte Fortsetzungskette dargestellt. Die dritte Aufgabe in der Kette wird ausgelöst und daher werden alle folgenden wertbasierten Fortsetzungen nicht ausgeführt. Allerdings ist die endgültige Fortsetzung aufgabenbasiert und wird daher immer ausgeführt. Diese letzte Fortsetzung behandelt die Ausnahme, die von der dritten Aufgabe ausgelöst wird.

Es wird empfohlen, die spezifischsten Ausnahmen möglichst abzufangen. Sie können diese endgültige aufgabenbasierte Fortsetzung weglassen, wenn Sie keine spezifischen Ausnahmen abzufangen haben. Alle Ausnahmen werden nicht behandelt und können die App beenden.

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
> Sie können die Methode " [parallelcurrency:: task_completion_event:: set_exception](../../parallel/concrt/reference/task-completion-event-class.md) " verwenden, um eine Ausnahme einem Aufgaben Abschluss Ereignis zuzuordnen. In der Dokument [Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md) wird die Klasse " [parallelcurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) " ausführlicher beschrieben.

" [parallelcurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) " ist ein wichtiger Lauf Zeit Ausnahmetyp, der sich auf `task`bezieht. Die Runtime löst `task_canceled` aus, wenn Sie `task::get` aufrufen und diese Aufgabe abgebrochen wird. (Im Gegensatz dazu gibt `task::wait` [task_status:: abgebrochen](reference/concurrency-namespace-enums.md#task_group_status) zurück und löst nicht aus.) Sie können diese Ausnahme von einer aufgabenbasierten Fortsetzung oder beim Abrufen von `task::get`abfangen und behandeln. Weitere Informationen zum Aufgaben Abbruch finden Sie unter [Abbruch in der ppl](cancellation-in-the-ppl.md).

> [!CAUTION]
> Lösen Sie nie `task_canceled` in Ihrem Code aus. Stattdessen wird " [parallelcurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) " aufgerufen.

Die Runtime beendet die App, wenn eine Aufgabe eine Ausnahme auslöst und diese Ausnahme nicht durch die Aufgabe, eine ihrer Fortsetzungen oder die Haupt-App abgefangen wird. Wenn die Anwendung abstürzt, können Sie Visual Studio so konfigurieren, dass eine Unterbrechung erfolgt, wenn C++-Ausnahmen ausgelöst werden. Nachdem Sie die Position des Ausnahmefehlers ermittelt haben, verwenden Sie eine aufgabenbasierte Fortsetzung, um ihn zu beheben.

Im Abschnitt [Ausnahmen, die von der Laufzeit](#runtime) in diesem Dokument ausgelöst werden, wird beschrieben, wie Sie mit Lauf Zeit Ausnahmen ausführlicher arbeiten.

[[Nach oben](#top)]

## <a name="task_groups"></a>Aufgaben Gruppen und parallele Algorithmen

In diesem Abschnitt wird beschrieben, wie die Runtime Ausnahmen behandelt, die von Aufgabengruppen ausgelöst werden. Dieser Abschnitt gilt auch für parallele Algorithmen, wie z. b. Parallelität [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), da diese Algorithmen auf Aufgaben Gruppen aufbauen.

> [!CAUTION]
> Es ist wichtig, dass Sie die Auswirkungen von Ausnahmen auf abhängige Aufgaben verstehen. Empfohlene Vorgehensweisen für die Verwendung der Ausnahmebehandlung bei Tasks oder parallelen Algorithmen finden Sie im Abschnitt Grundlegendes zur [Auswirkung der Abbruch-und Ausnahmebehandlung auf die Objekt Zerstörung](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) in den bewährten Methoden des Themas Parallel Patterns Library.

Weitere Informationen zu Aufgaben Gruppen finden Sie unter [Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Weitere Informationen zu parallelen Algorithmen finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

Wenn Sie im Text einer Arbeitsfunktion, die Sie an eine Parallelität übergeben, eine [Ausnahme auslösen: task_group](reference/task-group-class.md) -oder [parallelcurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) -Objekt speichert die Runtime diese Ausnahme und Marshalls Sie in den Kontext, der ["parallelcurrency:: task_group:: Wait](reference/task-group-class.md#wait), [parallelcurrency:: structured_task_group:: Wait](reference/structured-task-group-class.md#wait), parallelcurrency: [: task_group](reference/task-group-class.md#run_and_wait):: run_and_wait" oder " [parallelcurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait)" aufruft. Darüber hinaus werden von der Runtime auch alle aktiven Aufgaben in der Aufgabengruppe (sowie alle aktiven Aufgaben in untergeordneten Aufgabengruppen) beendet sowie alle noch nicht gestarteten Aufgaben verworfen.

Im folgenden Beispiel wird die grundlegende Struktur einer Arbeitsfunktion dargestellt, die eine Ausnahme auslöst. Im Beispiel werden die Werte von zwei `task_group`-Objekten mithilfe eines `point`-Objekts parallel ausgegeben. Die `print_point`-Arbeitsfunktion gibt die Werte eines `point`-Objekts an der Konsole aus. Die Arbeitsfunktion löst eine Ausnahme aus, wenn der Eingabewert `NULL` ist. Diese Ausnahme wird von der Runtime gespeichert und an den Kontext gemarshallt, der `task_group::wait` aufruft.

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

Ein umfassendes Beispiel, in dem die Ausnahmebehandlung in einer Aufgaben Gruppe verwendet wird, finden Sie unter Gewusst [wie: Verwenden der Ausnahmebehandlung, um von einer parallelen Schleife zu unterbrechen](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

[[Nach oben](#top)]

## <a name="runtime"></a>Von der Laufzeit ausgelöste Ausnahmen

Eine Ausnahme kann von einem Aufruf der Runtime ausgelöst werden. Die meisten Ausnahme Typen, mit Ausnahme von Parallelität [:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) und [parallelcurrency:: Operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), weisen auf einen Programmierfehler hin. Diese Fehler sind in der Regel nicht behebbar und dürfen daher durch Anwendungscode weder abgefangen noch behandelt werden. Es wird empfohlen, bei der Diagnose von Programmierfehlern nur nicht behebbare Fehler im Anwendungscode abzufangen oder zu behandeln. Die von der Runtime definierten Ausnahmetypen zu kennen, erleichtert jedoch die Diagnose von Programmierfehlern.

Der Mechanismus für die Ausnahmenbehandlung ist bei Ausnahmen, die durch die Runtime ausgelöst werden, derselbe wie bei Ausnahmen, der durch Arbeitsfunktionen ausgelöst werden. Die Funktion " [parallelcurrency:: Receive](reference/concurrency-namespace-functions.md#receive) " löst z. b. `operation_timed_out` aus, wenn keine Nachricht im angegebenen Zeitraum empfangen wird. Wenn `receive` eine Ausnahme in einer Arbeitsfunktion auslöst, die an eine Aufgabengruppe übergeben wird, wird diese Ausnahme von der Runtime gespeichert und an den Kontext gemarshallt, der `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait` oder `structured_task_group::run_and_wait` aufruft.

Im folgenden Beispiel wird der " [parallelcurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) -Algorithmus verwendet, um zwei Aufgaben parallel auszuführen. Die erste Aufgabe wartet fünf Sekunden und sendet dann eine Nachricht an einen Nachrichtenpuffer. Die zweite Aufgabe wartet mithilfe der `receive`-Funktion drei Sekunden auf eine Nachricht vom selben Nachrichtenpuffer. Die `receive`-Funktion löst die `operation_timed_out`-Ausnahme aus, wenn die Nachricht nicht im angegebenen Zeitraum empfangen wird.

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
The operation timed out.
```

Um sicherzustellen, dass die Anwendung ordnungsgemäß beendet wird, muss der Code beim Aufrufen der Runtime Ausnahmen behandeln. Behandeln Sie auch Ausnahmen, wenn Sie externen Code wie etwa die Bibliothek eines Drittanbieters aufrufen, der die Concurrency Runtime verwendet.

[[Nach oben](#top)]

## <a name="multiple"></a>Mehrere Ausnahmen

Wenn eine Aufgabe oder paralleler Algorithmus mehrere Ausnahmen empfängt, wird nur eine dieser Ausnahmen von der Runtime an den aufrufenden Kontext gemarshallt. Dabei kann nicht vorhergesagt werden, welche Ausnahme von der Runtime gemarshallt wird.

Im folgenden Beispiel werden mithilfe des `parallel_for`-Algorithmus Zahlen an der Konsole ausgegeben. Es wird eine Ausnahme ausgegeben, wenn der Eingabewert kleiner als ein Mindestwert oder größer als ein Maximalwert ist. In diesem Beispiel können mehrere Arbeitsfunktionen eine Ausnahme auslösen.

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

Nachfolgend wird eine Beispielausgabe für dieses Beispiel angezeigt.

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[Nach oben](#top)]

## <a name="cancellation"></a>Streichung

Nicht alle Ausnahmen geben einen Fehler an. Ein Suchalgorithmus kann beispielsweise mithilfe der Ausnahmenbehandlung die zugehörige Aufgabe beenden, sobald das Ergebnis gefunden ist. Weitere Informationen zur Verwendung von Abbruch Mechanismen in Ihrem Code finden Sie unter [Abbruch in der ppl](../../parallel/concrt/cancellation-in-the-ppl.md).

[[Nach oben](#top)]

## <a name="lwts"></a>Leichte Aufgaben

Eine leichte Aufgabe ist eine Aufgabe, die Sie direkt aus einem [parallelcurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) -Objekt planen. Einfache Aufgaben erfordern einen geringeren Aufwand als gewöhnliche Aufgaben. Die Runtime fängt jedoch keine Ausnahmen ab, die von einfachen Aufgaben ausgelöst werden. Stattdessen wird die Ausnahme vom Handler für nicht behandelte Ausnahmen abgefangen, der den Prozess standardmäßig beendet. Verwenden Sie daher in der Anwendung einen entsprechenden Fehlerbehandlungsmechanismus. Weitere Informationen zu Lightweight-Aufgaben finden Sie unter [Taskplaner](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Nach oben](#top)]

## <a name="agents"></a>Asynchrone Agents

Die Runtime verwaltet wie bei einfachen Aufgaben auch keine Ausnahmen, die von asynchronen Agents ausgelöst werden.

Das folgende Beispiel zeigt eine Möglichkeit, Ausnahmen in einer Klasse zu behandeln, die von " [parallelcurrency:: Agent](../../parallel/concrt/reference/agent-class.md)" abgeleitet wird. In diesem Beispiel wird die `points_agent`-Klasse definiert. Die `points_agent::run`-Methode liest `point`-Objekte aus dem Nachrichtenpuffer und gibt sie an der Konsole aus. Die `run`-Methode löst beim Empfang eines `NULL`-Zeigers eine Ausnahme aus.

Die `run`-Methode umgibt alle Arbeiten in einem `try`-`catch` Block. Die Ausnahme wird vom `catch`-Block in einem Nachrichtenpuffer gespeichert. Die Anwendung überprüft, ob im Agent ein Fehler aufgetreten ist. Hierzu wird dieser Puffer nach Abschluss des Agents gelesen.

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

Da der `try`-`catch` Block außerhalb der `while` Schleife vorhanden ist, beendet der Agent die Verarbeitung, wenn der erste Fehler auftritt. Wenn sich die `try`-`catch`-Block innerhalb der `while` Schleife befunden hat, wird der Agent nach einem Fehler fortgesetzt.

In diesem Beispiel werden Ausnahmen in einem Nachrichtenpuffer gespeichert, damit eine andere Komponente den Agent beim Ausführen auf Fehler überwachen kann. In diesem Beispiel wird ein " [parallelcurrency:: Single_assignment](../../parallel/concrt/reference/single-assignment-class.md) "-Objekt verwendet, um den Fehler zu speichern. Wenn ein Agent mehrere Ausnahmen behandelt speichert die `single_assignment`-Klasse nur die erste Nachricht, die an sie übergeben wird. Wenn Sie nur die letzte Ausnahme speichern möchten, verwenden Sie die Klasse " [parallelcurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) ". Verwenden Sie die Klasse " [parallelcurrency:: Unbounded_buffer](reference/unbounded-buffer-class.md) ", um alle Ausnahmen zu speichern. Weitere Informationen zu diesen Nachrichten Blöcken finden Sie unter [asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md).

Weitere Informationen zu asynchronen Agents finden Sie unter [asynchrone Agents](../../parallel/concrt/asynchronous-agents.md).

[[Nach oben](#top)]

## <a name="summary"></a> Zusammenfassung

[[Nach oben](#top)]

## <a name="see-also"></a>Siehe auch

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br/>
[Abbruch in der PPL](cancellation-in-the-ppl.md)<br/>
[Aufgabenplanung](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Asynchrone Agents](../../parallel/concrt/asynchronous-agents.md)
