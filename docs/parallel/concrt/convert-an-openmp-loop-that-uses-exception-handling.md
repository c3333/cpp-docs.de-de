---
title: 'Gewusst wie: Konvertieren einer OpenMP-Schleife, in der die Ausnahmebehandlung verwendet wird, zur Verwendung der Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: ca2ee42d48d8fe9f66025b8f0d5eeb493fc91d10
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498466"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Gewusst wie: Konvertieren einer OpenMP-Schleife, in der die Ausnahmebehandlung verwendet wird, zur Verwendung der Concurrency Runtime

In diesem Beispiel wird veranschaulicht, wie eine [parallele](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)OpenMP-[for](../openmp/reference/openmp-directives.md#for-openmp) -Schleife konvertiert wird, die die Ausnahmebehandlung durchführt, um den Concurrency Runtime Ausnahme Behandlungs Mechanismus zu verwenden

In OpenMP müssen Ausnahmen in einem parallelen Bereich im gleichen Bereich und vom gleichen Thread abgefangen und behandelt werden. Eine Ausnahme, die den parallelen Bereich umgeht, wird vom Handler für nicht behandelte Ausnahmen abgefangen, der den Prozess standardmäßig beendet.

Wenn Sie im Concurrency Runtime eine Ausnahme im Text einer Arbeitsfunktion auslösen, die Sie an eine Aufgaben Gruppe übergeben, z. b. ein [parallelcurrency:: task_group](reference/task-group-class.md) -oder [parallelcurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) -Objekt, oder an einen parallelen Algorithmus wie z. b. Parallelität [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), speichert die Runtime diese Ausnahme und marshunkt Sie an den Kontext, der auf den Abschluss der Aufgaben Gruppe oder des Bei Aufgaben Gruppen ist der Warte Kontext der Kontext, der " [parallelcurrency:: task_group:: Wait](reference/task-group-class.md#wait), [parallelcurrency:: structured_task_group:: Wait](reference/structured-task-group-class.md#wait), parallelcurrency [:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait)" oder " [parallelcurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait)" aufruft. Der Wartekontext eines parallelen Algorithmus ist der Kontext, von dem dieser Algorithmus aufgerufen wurde. Darüber hinaus werden von der Runtime auch alle aktiven Aufgaben in der Aufgabengruppe (sowie alle aktiven Aufgaben in untergeordneten Aufgabengruppen) beendet sowie alle noch nicht gestarteten Aufgaben verworfen.

## <a name="example"></a>Beispiel

In diesem Beispiel wird veranschaulicht, wie Ausnahmen in einem OpenMP `parallel`-Bereich und in einem Aufruf von `parallel_for` behandelt werden. Die `do_work` -Funktion führt eine Speicher Belegungs Anforderung aus, die nicht erfolgreich ist und daher eine Ausnahme vom Typ [Std:: bad_alloc](../../standard-library/bad-alloc-class.md)auslöst. In der Version, die OpenMP verwendet, muss diese vom Thread, der diese Ausnahme auslöst, ebenfalls abgefangen werden. Mit anderen Worten muss die Ausnahme von jeder Iteration einer parallelen OpenMP-Schleife behandelt werden. In der Version mit der Concurrency Runtime wird eine Ausnahme, die von einem anderen Thread ausgelöst wird, vom Hauptthread abgefangen.

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-exception-handling_1.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
Using OpenMP...
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
Using the Concurrency Runtime...
An error of type 'class std::bad_alloc' occurred.
```

In der Version in diesem Beispiel mit OpenMP tritt die Ausnahme in der jeweiligen Schleifeniteration auf und wird dort auch behandelt. In der Version mit der Concurrency Runtime wird die Ausnahme von der Laufzeit gespeichert, alle aktiven Aufgaben werden beendet, noch nicht gestartete Aufgaben werden verworfen, und die Ausnahme, die `parallel_for` aufruft, wird an den Kontext gemarshallt.

Wenn Sie möchten, dass die Version mit OpenMP nach dem Auftreten der Ausnahme beendet wird, können Sie ein boolesche Flag verwenden, um den Fehler gegenüber anderen Schleifeniterationen anzuzeigen. Wie im Beispiel im Thema Gewusst [wie: Konvertieren einer OpenMP-Schleife, die einen Abbruch verwendet, um die Concurrency Runtime zu verwenden](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), führen nachfolgende Schleifen Iterationen keine Aktion aus, wenn das-Flag festgelegt ist. Umgekehrt können Sie die Ausnahme, wenn die Schleife mit der Concurrency Runtime nach dem Auftreten der Ausnahme fortgesetzt werden soll, im Text der parallelen Schleife selbst behandeln.

Andere Komponenten der Concurrency Runtime, wie asynchrone Agents und einfache Aufgaben, transportieren keine Ausnahmen. Stattdessen werden unbehandelte Ausnahmen vom Handler für nicht behandelte Ausnahmen abgefangen, der den Prozess standardmäßig beendet. Weitere Informationen zur Ausnahmebehandlung finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Weitere Informationen zu `parallel_for` und anderen parallelen Algorithmen finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `concrt-omp-exceptions.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc/OpenMP ConcRT-OMP-Exceptions. cpp**

## <a name="see-also"></a>Weitere Informationen

[Migrieren von OpenMP zur Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)
