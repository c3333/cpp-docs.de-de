---
title: 'Gewusst wie: Konvertieren einer parallel-for-Schleife in OpenMP zur Verwendung der Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 4f523f9f6de7f1ffb4c3b578b60de587239dffb6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507881"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Gewusst wie: Konvertieren einer parallel-for-Schleife in OpenMP zur Verwendung der Concurrency Runtime

In diesem Beispiel wird veranschaulicht, wie eine grundlegende Schleife konvertiert wird, die die parallele OpenMP-und [for](../openmp/reference/openmp-directives.md#for-openmp) -Direktiven verwendet, um den Concurrency Runtime [Parallelitäts](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) [:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) -Algorithmus zu verwenden.

## <a name="example---prime-count"></a>Beispiel: Primzahl

In diesem Beispiel wird die Anzahl der Primzahlen in einem Array von Zufallswerten sowohl mit OpenMP als auch mit der Concurrency Runtime berechnet.

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

Der `parallel_for`-Algorithmus und OpenMP 3.0 lassen als Indextyp einen ganzzahligen Typ mit Vorzeichen und einen ganzzahligen Typ ohne Vorzeichen zu. Der `parallel_for`-Algorithmus stellt außerdem sicher, dass der angegebene Bereich bei einem Typ mit Vorzeichen keinen Überlauf verursacht. Version 2.0 und 2.5 von OpenMP lassen nur ganzzahlige Indextypen mit Vorzeichen zu. In OpenMP wird außerdem der Indexbereich nicht überprüft.

In der Version dieses Beispiels, in der die Concurrency Runtime verwendet wird, wird auch ein [parallelcurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) -Objekt anstelle der [Atomic](../openmp/reference/openmp-directives.md#atomic) -Direktive verwendet, um den Leistungswert zu erhöhen, ohne dass eine Synchronisierung erforderlich ist

Weitere Informationen zu `parallel_for` und anderen parallelen Algorithmen finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md). Weitere Informationen zur `combinable` -Klasse finden Sie unter [parallele Container und Objekte](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="example---use-stdarray"></a>Beispiel: Verwenden von "Std:: Array"

In diesem Beispiel wird das vorherige-Objekt so geändert, dass es für ein [Std:: Array](../../standard-library/array-class-stl.md) -Objekt anstelle eines nativen Arrays fungiert. Da in den Versionen 2,0 und 2,5 von OpenMP nur in einem Konstrukt signierte ganzzahlige Index Typen zulässig `parallel_for` sind, können Iteratoren nicht parallel zum Zugreifen auf die Elemente eines C++-Standard Bibliotheks Containers verwendet werden. Die Parallel Patterns Library (PPL) stellt den Algorithmus "Parallelität [::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) " bereit, der Aufgaben parallel für einen iterativen Container ausführt, wie z. b. die von der C++-Standard Bibliothek bereitgestellten. Er verwendet die gleiche Partitionierungslogik wie der `parallel_for`-Algorithmus. Der `parallel_for_each` Algorithmus ähnelt dem [Std:: for_each](../../standard-library/algorithm-functions.md#for_each) -Algorithmus der C++-Standard Bibliothek, mit dem Unterschied, dass der `parallel_for_each` Algorithmus die Aufgaben gleichzeitig ausführt.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `concrt-omp-count-primes.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc/OpenMP ConcRT-OMP-count-primes. cpp**

## <a name="see-also"></a>Weitere Informationen

[Migrieren von OpenMP zur Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br/>
[Parallele Container und Objekte](../../parallel/concrt/parallel-containers-and-objects.md)
