---
title: 'Gewusst wie: Erhöhen der Effizienz mithilfe von parallelen Containern'
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: 361e0e32efb45468ba108ee975879f990ac98395
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008323"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Gewusst wie: Erhöhen der Effizienz mithilfe von parallelen Containern

In diesem Thema wird aufgezeigt, wie parallele Container verwendet werden, um Daten effizient zu speichern und parallel auf sie zuzugreifen.

Im Beispielcode werden der Satz von Primzahlen und Carmichael-Zahlen parallel berechnet. Anschließend berechnet der Code für jede Carmichael-Zahl die Primfaktoren dieser Zahl.

## <a name="example-determine-if-an-input-value-is-a-prime-number"></a>Beispiel: bestimmen, ob ein Eingabe Wert eine Primzahl ist

Im folgenden Beispiel wird die `is_prime`-Funktion gezeigt, durch die bestimmt wird, ob ein Eingabewert eine Primzahl ist, und die `is_carmichael`-Funktion, durch die bestimmt wird, ob der Eingabewert eine Carmichael-Zahl ist.

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example-compute-prime-and-carmichael-numbers"></a>Beispiel: Berechnen von Primzahlen und Carmichael-Zahlen

Im folgenden Beispiel werden die Funktionen `is_prime` und `is_carmichael` zum Berechnen der Sätze von Primzahlen und Carmichael-Zahlen verwendet. Das Beispiel verwendet die Parallelität [::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) und Parallelität [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) Algorithmen, um jeden Satz parallel zu berechnen. Weitere Informationen zu parallelen Algorithmen finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

In diesem Beispiel wird ein " [parallelcurrency:: Concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) "-Objekt verwendet, um den Satz von Carmichael-Zahlen zu speichern, da dieses Objekt später als Arbeits Warteschlange verwendet wird. Es verwendet ein " [parallelcurrency:: Concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) "-Objekt, um den Satz von Primzahlen zu speichern, da es später diese Menge durchläuft, um Prim Faktoren zu ermitteln.

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example-find-all-prime-factors-of-a-given-value"></a>Beispiel: Suchen aller Prim Faktoren eines bestimmten Werts

Im folgenden Beispiel wird die `prime_factors_of`-Funktion veranschaulicht, von der die Versuchsdivision verwendet wird, um alle Primfaktoren des angegebenen Werts zu suchen.

Diese Funktion verwendet den " [parallelcurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) -Algorithmus zum Durchlaufen der Auflistung von Primzahlen. Das `concurrent_vector`-Objekt macht es möglich, dass die parallele Schleife dem Ergebnis gleichzeitig Primfaktoren hinzufügen kann.

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example-processes-each-element-in-the-queue-of-carmichael-numbers"></a>Beispiel: verarbeitet jedes Element in der Warteschlange von Carmichael-Zahlen.

In diesem Beispiel wird jedes Element in der Warteschlange von Carmichael-Zahlen verarbeitet, indem zum Berechnen der Primfaktoren die `prime_factors_of`-Funktion aufgerufen wird. Es führt diese Arbeit mithilfe einer Aufgabengruppe parallel aus. Weitere Informationen zu Aufgaben Gruppen finden Sie unter [Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

In diesem Beispiel werden die Primfaktoren für jede Carmichael-Zahl gedruckt, wenn diese Zahl mehr als vier Primfaktoren hat.

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example-finished-parallel-container-code-sample"></a>Beispiel: Fertigstellung von parallelem Container Codebeispiel

Im folgenden Code wird das vollständige Beispiel veranschaulicht, in dem parallele Container zum Berechnen der Primfaktoren der Carmichael-Zahlen verwendet werden.

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe.

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `carmichael-primes.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc Carmichael-primes. cpp**

## <a name="see-also"></a>Siehe auch

[Parallele Container und Objekte](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector-Klasse](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[Concurrent_queue-Klasse](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[Parallel_invoke-Funktion](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for-Funktion](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[Task_group-Klasse](reference/task-group-class.md)
