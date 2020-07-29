---
title: 'Gewusst wie: Verwenden von parallel_invoke zum Schreiben einer Runtime für paralleles Sortieren'
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 9d84cdbecb7cc6d39cb30077780c558db85888c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222718"
---
# <a name="how-to-use-parallel_invoke-to-write-a-parallel-sort-routine"></a>Gewusst wie: Verwenden von parallel_invoke zum Schreiben einer Runtime für paralleles Sortieren

In diesem Dokument wird beschrieben, wie der [parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) -Algorithmus verwendet wird, um die Leistung des bitischen Sortieralgorithmus zu verbessern. Der bitonische Sortieralgorithmus unterteilt die Eingabesequenz rekursiv in kleinere sortierte Partitionen. Der bitonische Sortieralgorithmus kann parallel ausgeführt werden, da alle Partitionsvorgänge von allen anderen Vorgängen unabhängig sind.

Obwohl die bitonische Sortierung ein Beispiel für ein *Sortierungs Netzwerk* ist, das alle Kombinationen von Eingabe Sequenzen sortiert, werden in diesem Beispiel Sequenzen sortiert, deren Längen eine Potenz von zwei ist.

> [!NOTE]
> Dieses Beispiel verwendet eine parallele Sortierungsroutine zur Veranschaulichung. Sie können auch die integrierten Sortieralgorithmen verwenden, die die ppl bereitstellt: Parallelität [::p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), Parallelität [::p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)und Parallelität [::p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Weitere Informationen finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

## <a name="sections"></a><a name="top"></a>Strecken

In diesem Dokument werden die folgenden Aufgaben erläutert:

- [Serielles Ausführen der bitonischen Sortierung](#serial)

- [Verwenden von parallel_invoke für die parallele bitonische Suche](#parallel)

## <a name="performing-bitonic-sort-serially"></a><a name="serial"></a>Seriale durchführen von bitonischer Sortierung

Im folgenden Beispiel wird die serielle Version des bitonischen Sortieralgorithmus dargestellt. Die `bitonic_sort`-Funktion unterteilt die Sequenz in zwei Partitionen, sortiert diese Partitionen in entgegengesetzten Richtungen, und führt dann die Ergebnisse zusammen. Diese Funktion ruft sich selbst zweimal auf, um alle Partitionen rekursiv zu sortieren.

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[Nach[oben](#top)]

## <a name="using-parallel_invoke-to-perform-bitonic-sort-in-parallel"></a><a name="parallel"></a>Verwenden von parallel_invoke, um eine bitonische Sortierung parallel auszuführen

In diesem Abschnitt wird beschrieben, wie der bitonischen Sortieralgorithmus mit dem `parallel_invoke`-Algorithmus parallel ausgeführt werden kann.

### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>So führen Sie den bitonischen Sortieralgorithmus parallel aus

1. Fügen Sie für die Headerdatei ppl.h eine `#include`-Direktive hinzu.

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. Fügen Sie eine- **`using`** Direktive für den `concurrency` Namespace hinzu.

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. Erstellen Sie die neue Funktion `parallel_bitonic_mege` für den `parallel_invoke`-Algorithmus, um die Sequenzen parallel zusammenzuführen, wenn genügend Arbeit vorhanden ist. Rufen Sie andernfalls `bitonic_merge` auf, um die Sequenzen seriell zusammenzuführen.

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. Führen Sie einen Prozess aus, der demjenigen im Schritt weiter oben gleicht, jedoch für die `bitonic_sort`-Funktion ausgeführt wird.

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. Erstellen Sie eine überladene Version der `parallel_bitonic_sort`-Funktion, durch die das Array in aufsteigender Reihenfolge sortiert wird.

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

Mit dem `parallel_invoke`-Algorithmus wird der Aufwand reduziert, indem die letzte einer Reihe von Aufgaben im aufrufenden Kontext ausgeführt wird. Beispielsweise wird in der `parallel_bitonic_sort`-Funktion die erste Aufgabe in einem separaten Kontext und die zweite Aufgabe im aufrufenden Kontext ausgeführt.

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

Im folgenden vollständigen Beispiel wird sowohl die serielle als auch die parallele Version des bitonischen Sortieralgorithmus durchgeführt. Das Beispiel gibt außerdem die Zeit, die zum Ausführen beider Berechnungen benötigt wird, an der Konsole aus.

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

Die folgende Beispielausgabe entspricht einem Ergebnis auf einem Computer mit vier Prozessoren.

```Output
serial time: 4353
parallel time: 1248
```

[Nach[oben](#top)]

### <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen ein, `parallel-bitonic-sort.cpp` und führen Sie dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster aus.

> **cl.exe/EHsc parallel-Bitonic-Sort. cpp**

## <a name="robust-programming"></a>Stabile Programmierung

In diesem Beispiel `parallel_invoke` wird der Algorithmus anstelle der Klasse " [parallelcurrency:: task_group](reference/task-group-class.md) " verwendet, da die Lebensdauer der einzelnen Aufgaben Gruppen nicht über eine Funktion hinausgeht. Es wird empfohlen, wenn möglich `parallel_invoke`-Objekte zu verwenden, da diese im Vergleich zu `task group`-Objekten einen geringeren Ausführungsaufwand erfordern, sodass Sie einen leistungsfähigeren Code schreiben können.

Die parallelen Versionen einiger Algorithmen erzielen nur eine bessere Leistung, wenn es genügend Arbeit gibt. So ruft beispielsweise die `parallel_bitonic_merge`-Funktion die serielle Version `bitonic_merge` auf, wenn in der Sequenz 500 oder weniger Elemente vorhanden sind. Sie können die allgemeine Vorgehensweise bei der Sortierung auch an dem voraussichtlichen Arbeitsaufwand ausrichten. Beispielsweise ist es möglicherweise effizienter, die serielle Version des QuickSort-Algorithmus zu verwenden, wenn das Array weniger als 500 Elemente enthält, wie im folgenden Beispiel gezeigt:

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

Analog zu allen anderen parallelen Algorithmen wird empfohlen, nach Bedarf Profile und Anpassungen für den Code bereitzustellen.

## <a name="see-also"></a>Weitere Informationen

[Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Parallel_invoke-Funktion](reference/concurrency-namespace-functions.md#parallel_invoke)
