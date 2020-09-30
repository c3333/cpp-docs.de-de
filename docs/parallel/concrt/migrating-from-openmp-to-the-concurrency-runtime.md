---
title: Migrieren von OpenMP zur Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 081d0ae8b312d827a0af98dd45c62f7563e81677
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507755"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migrieren von OpenMP zur Concurrency Runtime

Concurrency Runtime ermöglicht eine Vielzahl von Programmiermodellen. Diese Modelle überlappen oder ergänzen die Modelle von anderen Bibliotheken. In den Dokumenten in diesem Abschnitt wird [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) mit dem Concurrency Runtime verglichen, und es werden Beispiele zum Migrieren von vorhandenem OpenMP-Code zur Verwendung des Concurrency Runtime bereitgestellt.

Das OpenMP-Programmiermodell wird durch einen offenen Standard definiert und verfügt über klar definierte Bindungen zu den Programmiersprachen Fortran und C/C++. OpenMP-Versionen 2,0 und 2,5, die vom Microsoft C++-Compiler unterstützt werden, eignen sich gut für parallele Algorithmen, die iterativ sind. Das heißt, Sie führen eine parallele Iterationen für ein Array von Daten aus. OpenMP 3,0 unterstützt neben iterativen Aufgaben auch nicht iterative Tasks.

OpenMP ist am effizientesten, wenn der Grad an Parallelität vorgegeben ist und mit den verfügbaren Ressourcen auf dem System übereinstimmt. Das OpenMP-Modell eignet sich besonders gut für High Performance Computing, bei dem sehr große Berechnungs Probleme auf die Verarbeitungs Ressourcen eines einzelnen Computers verteilt werden. In diesem Szenario ist die Hardware Umgebung in der Regel korrigiert, und der Entwickler kann bei der Ausführung des Algorithmus einen exklusiven Zugriff auf alle Computerressourcen erwarten.

Weniger eingeschränkte Rechen Umgebungen sind jedoch möglicherweise nicht für OpenMP geeignet. Beispielsweise sind rekursive Probleme (z. b. der QuickSort-Algorithmus oder das Durchsuchen einer Datenstruktur) schwieriger zu implementieren, indem OpenMP 2,0 und 2,5 verwendet werden. Der Concurrency Runtime ergänzt die Funktionen von OpenMP durch Bereitstellen der [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md) und der [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Die Bibliothek für asynchrone Agents unterstützt grob abgestimmte Aufgaben Parallelität. die PPL unterstützt differenziertere parallele Aufgaben. Der Concurrency Runtime stellt die Infrastruktur bereit, die für die parallele Ausführung von Vorgängen erforderlich ist, sodass Sie sich auf die Logik ihrer Anwendung konzentrieren können. Da jedoch die Concurrency Runtime eine Vielzahl von Programmier Modellen ermöglicht, kann der Planungsaufwand größer sein als andere Parallelitäts Bibliotheken, wie z. b. OpenMP. Daher wird empfohlen, die Leistung inkrementell zu testen, wenn Sie den vorhandenen OpenMP-Code für die Verwendung der Concurrency Runtime konvertieren.

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Beim Migrieren von OpenMP zum Concurrency Runtime

Es kann vorteilhaft sein, vorhandenen OpenMP-Code zu migrieren, um die Concurrency Runtime in den folgenden Fällen zu verwenden.

|Fälle|Vorteile des Concurrency Runtime|
|-----------|-------------------------------------------|
|Sie benötigen ein erweiterbares Framework für die parallele Programmierung.|Viele der Funktionen in der Concurrency Runtime können erweitert werden. Sie können auch vorhandene Funktionen zu neuen Funktionen kombinieren. Da OpenMP Compilerdirektiven stützt, kann es nicht problemlos erweitert werden.|
|Ihre Anwendung profitiert von der kooperativen Blockierung.|Wenn ein Task blockiert wird, weil er eine Ressource erfordert, die noch nicht verfügbar ist, können die Concurrency Runtime andere Aufgaben ausführen, während die erste Aufgabe auf die Ressource wartet.|
|Ihre Anwendung profitiert vom dynamischen Lastenausgleich.|Der Concurrency Runtime verwendet einen Planungs Algorithmus, der die Zuordnung von Computerressourcen anpasst, wenn sich Workloads ändern. Wenn der Scheduler in OpenMP Rechenressourcen einem parallelen Bereich zuordnet, werden diese Ressourcen Zuordnungen während der gesamten Berechnung korrigiert.|
|Sie benötigen Unterstützung für die Ausnahmebehandlung.|Die PPL ermöglicht das Abfangen von Ausnahmen sowohl innerhalb als auch außerhalb eines parallelen Bereichs oder einer parallelen Schleife. In OpenMP muss die Ausnahme in der parallelen Region oder Schleife behandelt werden.|
|Sie benötigen einen Abbruchmechanismus.|Die PPL ermöglicht es Anwendungen, sowohl einzelne Aufgaben als auch parallele Arbeitsstrukturen abzubrechen. OpenMP erfordert, dass die Anwendung einen eigenen Abbruchmechanismus implementiert.|
|Paralleler Code muss in einem anderen Kontext beendet werden, von dem er gestartet wird.|Mit der Concurrency Runtime können Sie eine Aufgabe in einem Kontext starten und dann auf diese Aufgabe in einem anderen Kontext warten oder diese abbrechen. In OpenMP müssen alle parallelen Aufgaben in dem Kontext abgeschlossen werden, von dem aus Sie gestartet werden.|
|Sie benötigen erweiterte Debuggingunterstützung.|Visual Studio stellt die Fenster **parallele Stapel** und **parallele Aufgaben** bereit, sodass Sie Multithreadanwendungen einfacher debuggen können.<br /><br /> Weitere Informationen zur Debugunterstützung für das Concurrency Runtime finden [Sie unter Verwenden des Fensters "Aufgaben](/visualstudio/debugger/using-the-tasks-window)", [Verwenden des Fensters "parallele Stapel](/visualstudio/debugger/using-the-parallel-stacks-window)" und Exemplarische Vorgehensweise [: Debuggen einer parallelen Anwendung](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Wenn keine Migration von OpenMP zum Concurrency Runtime

In den folgenden Fällen wird beschrieben, wann es möglicherweise nicht angebracht ist, vorhandenen OpenMP-Code für die Verwendung des Concurrency Runtime zu migrieren.

|Fälle|Erklärung|
|-----------|-----------------|
|Ihre Anwendung erfüllt Ihre Anforderungen bereits.|Wenn Sie mit der Anwendungsleistung und der aktuellen Debugunterstützung zufrieden sind, ist die Migration möglicherweise nicht geeignet.|
|Ihre parallelen Schleifen Texte führen nur wenig Arbeit aus.|Der Aufwand des Concurrency Runtime Task Planers kann die Vorteile der parallelen Ausführung des Schleifen Texts nicht überwinden, insbesondere wenn der Schleifen Text relativ klein ist.|
|Ihre Anwendung ist in C geschrieben.|Da die Concurrency Runtime viele C++ Features verwendet, ist Sie möglicherweise nicht geeignet, wenn Sie keinen Code schreiben können, der es der C-Anwendung ermöglicht, Sie vollständig zu verwenden.|

## <a name="related-topics"></a>Verwandte Themen

[Gewusst wie: Konvertieren einer parallelen OpenMP for-Schleife für die Verwendung der Concurrency Runtime](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

In einer einfachen Schleife, in der die parallel-und [for](../openmp/reference/openmp-directives.md#for-openmp) -Direktiven von OpenMP verwendet werden, wird veranschaulicht, wie Sie in die Concurrency Runtime [Parallelität](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) -Algorithmus konvertiert wird.

[Gewusst wie: Konvertieren einer OpenMP-Schleife, die einen Abbruch verwendet, zum Verwenden des Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
Bei einer [parallelen](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)OpenMP[for](../openmp/reference/openmp-directives.md#for-openmp) -Schleife, in der nicht alle Iterationen ausgeführt werden müssen, wird veranschaulicht, wie Sie diese für die Verwendung des Concurrency Runtime Abbruchmechanismus konvertieren.

[Gewusst wie: Konvertieren einer OpenMP-Schleife, in der die Ausnahmebehandlung verwendet wird, zur Verwendung des Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
Bei einer [parallelen](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)OpenMP[for](../openmp/reference/openmp-directives.md#for-openmp) -Schleife, die die Ausnahmebehandlung durchführt, wird veranschaulicht, wie die Methode konvertiert wird, um den Concurrency Runtime Ausnahme Behandlungs Mechanismus zu verwenden.

[Gewusst wie: Konvertieren einer OpenMP-Schleife, in der eine reduction-Variable verwendet wird, zur Verwendung der Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
Bei einer [parallelen](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)OpenMP[for](../openmp/reference/openmp-directives.md#for-openmp) -Schleife, die die [Reduction](../openmp/reference/openmp-clauses.md#reduction) -Klausel verwendet, wird veranschaulicht, wie Sie diese für die Verwendung der Concurrency Runtime konvertieren.

## <a name="see-also"></a>Weitere Informationen

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)
