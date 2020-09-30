---
title: 'Gewusst wie: Konvertieren einer OpenMP-Schleife mit Abbruch zur Verwendung der Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: adde6decc086b883c50e52d12e388197e185fb39
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505948"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Gewusst wie: Konvertieren einer OpenMP-Schleife mit Abbruch zur Verwendung der Concurrency Runtime

Bei einigen parallelen Schleifen müssen nicht alle Iterationen ausgeführt werden. Beispielsweise kann ein Algorithmus, mit dem nach einem Wert gesucht wird, beendet werden, sobald der Wert gefunden wurde. OpenMP stellt keinen Mechanismus bereit, um aus einer parallelen Schleife auszubrechen. Sie können jedoch einen booleschen Wert oder ein Flag verwenden, damit die Iteration einer Schleife angeben kann, dass der gesuchte Wert gefunden wurde. Die Concurrency Runtime stellt Funktionen bereit, mit denen eine Aufgabe andere Aufgaben abbrechen kann, die noch nicht gestartet wurden.

In diesem Beispiel wird veranschaulicht, wie eine [parallele](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)OpenMP-[for](../openmp/reference/openmp-directives.md#for-openmp) -Schleife konvertiert wird, die nicht erfordert, dass alle Iterationen den Concurrency Runtime Abbruchmechanismus verwenden.

## <a name="example"></a>Beispiel

In diesem Beispiel werden sowohl OpenMP als auch das Concurrency Runtime verwendet, um eine parallele Version des [Std:: any_of](../../standard-library/algorithm-functions.md#any_of) -Algorithmus zu implementieren. In der OpenMP-Version in diesem Beispiel wird mit einem Flag die Erfüllung der Bedingung für alle parallelen Schleifeniterationen koordiniert. Die Version, die die Concurrency Runtime verwendet, verwendet die Methode " [parallelcurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) ", um den gesamten Vorgang zu beenden, wenn die Bedingung erfüllt ist.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

In der Version mit OpenMP werden, auch wenn das Flag festgelegt ist, alle Schleifeniterationen ausgeführt. Bei einer Aufgabe mit untergeordneten Aufgaben müsste das Flag darüber hinaus auch für diese verfügbar sein, um den Abbruch des Vorgangs zu signalisieren. Wenn in der Concurrency Runtime eine Aufgaben Gruppe abgebrochen wird, wird die gesamte Arbeitsstruktur, einschließlich untergeordneter Aufgaben, von der Common Language Runtime abgebrochen. Der Algorithmus "Parallelität [::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) " verwendet Aufgaben, um Arbeit auszuführen. Wenn die Stamm Aufgabe durch eine Iterations Schleife abgebrochen wird, wird die gesamte Struktur der Berechnung ebenfalls abgebrochen. Wenn eine Arbeitsstruktur abgebrochen wird, startet die Laufzeit keine neuen Tasks. Aufgaben, die bereits gestartet wurden, wird von der Laufzeit jedoch eine Fertigstellung ermöglicht. Aktive Schleifeniterationen können im Falle des `parallel_for_each`-Algorithmus also ihre Ressourcen bereinigen.

Im Beispiel kann das Ergebnis in beiden Versionen durch mehrere Schleifeniterationen parallel festgelegt und der Gesamtvorgang kann abgebrochen werden, wenn das Array mehr als eine Kopie des gesuchten Werts enthält. Mit einem Synchronisierungsprimitiven wie einem kritischen Abschnitt können Sie ggf. sicherstellen, dass Arbeiten nur von einer Aufgabe ausgeführt werden, wenn eine Bedingung erfüllt ist.

Sie können Aufgaben mit der PPL auch mit der Ausnahmebehandlung abbrechen. Weitere Informationen zu Abbruch finden Sie unter [Abbruch in der ppl](cancellation-in-the-ppl.md).

Weitere Informationen zu `parallel_for_each` und anderen parallelen Algorithmen finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `concrt-omp-parallel-any-of.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc/OpenMP ConcRT-omp-parallel-any-of. cpp**

## <a name="see-also"></a>Weitere Informationen

[Migrieren von OpenMP zur Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Abbruch in der PPL](cancellation-in-the-ppl.md)<br/>
[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)
