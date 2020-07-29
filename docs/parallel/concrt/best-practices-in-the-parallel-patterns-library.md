---
title: Empfohlene Vorgehensweisen in der Parallel Patterns Library
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: 0bd49dda881df402a8c511714c22be37da3a50c4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231727"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>Empfohlene Vorgehensweisen in der Parallel Patterns Library

Dieses Dokument beschreibt die optimale, effektive Nutzung der Parallel Patterns Library (PPL). Die PPL bietet allgemeine Container, Objekte und Algorithmen zum Ausführen von differenziertem Parallelismus.

Weitere Informationen zur ppl finden Sie unter [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

## <a name="sections"></a><a name="top"></a>Strecken

Dieses Dokument enthält folgende Abschnitte:

- [Kleine Schleifenkörper nicht parallelisieren](#small-loops)

- [Parallelität auf der höchstmöglichen Ebene ausdrücken](#highest)

- [parallel_invoke zum Lösen von Divide-and-Conquer-Problemen verwenden](#divide-and-conquer)

- [Abbruch und Ausnahmebehandlung zum Verlassen einer Parallelschleife verwenden](#breaking-loops)

- [Verstehen, wie sich Abbruch und Ausnahmebehandlung auf die Objektlöschung auswirken](#object-destruction)

- [Kein wiederholtes Blockieren in einer parallelen Schleife](#repeated-blocking)

- [Keine Blockierungsvorgänge beim Abbrechen paralleler Aufgaben ausführen](#blocking)

- [Nicht auf freigegebene Daten in einer parallelen Schleife schreiben](#shared-writes)

- [False Sharing nach Möglichkeit vermeiden](#false-sharing)

- [Sicherstellen, dass Variablen während der Lebensdauer einer Aufgabe gültig sind.](#lifetime)

## <a name="do-not-parallelize-small-loop-bodies"></a><a name="small-loops"></a>Kleine Schleifenkörper nicht parallelisieren

Die Parallelisierung von relativ kleinen Schleifenkörpern kann dazu führen, dass der entsprechende Planungsaufwand die Vorteile der parallelen Verarbeitung zunichte machen. Betrachten Sie das folgende Beispiel, das jedes Elementpaar in zwei Arrays hinzufügt.

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

Die Arbeitsauslastung für jede Iteration der parallelen Schleife ist zu klein, um vom Aufwand für die parallele Verarbeitung zu profitieren. Sie können die Leistung dieser Schleife verbessern, indem Sie mehr Arbeit im Schleifenkörper oder durch das serielle Ausführen der Schleife erledigen.

[Nach[oben](#top)]

## <a name="express-parallelism-at-the-highest-possible-level"></a><a name="highest"></a>Express Parallelität auf der höchsten möglichen Ebene

Wenn Sie Code nur auf niedriger Ebene parallelisieren, können Sie ein Fork-Join-Konstrukt einführen, das nicht mit der steigenden Anzahl der Prozessoren skaliert. Ein *Fork-Join-* Konstrukt ist ein Konstrukt, bei dem eine Aufgabe ihre Arbeit in kleinere parallele subtasks unterteilt und darauf wartet, dass diese Teilaufgaben abgeschlossen werden. Jede Unteraufgabe kann sich selbst rekursiv auf weitere Unteraufgaben aufteilen.

Obwohl das Fork-Join-Modell zur Lösung verschiedener Probleme hilfreich sein kann, gibt es Situationen, in denen der Synchronisierungsaufwand die Skalierbarkeit verringern kann. Betrachten Sie beispielsweise den folgenden seriellen Code, der Bilddaten verarbeitet.

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

Da jede Schleifeniteration unabhängig ist, können Sie einen Großteil der Arbeit parallelisieren, wie im folgenden Beispiel gezeigt wird. In diesem Beispiel wird der " [parallelcurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) -Algorithmus verwendet, um die äußere Schleife zu parallelisieren.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

Das folgende Beispiel veranschaulicht ein Fork-Join-Konstrukt durch Aufrufen der `ProcessImage`-Funktion in einer Schleife. Jeder Aufruf von `ProcessImage` wird erst zurückgegeben, wenn jede Unteraufgabe abgeschlossen ist.

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

Wenn jede Iteration der parallelen Schleife fast keine Arbeit ausführt oder die Arbeit, die von der parallelen Schleife ausgeführt wird, unausgeglichenen ist, d. h. einige Schleifeniterationen dauern länger als andere, kann der Planungsaufwand, der erforderlich ist, um Arbeit häufig aufzuteilen und zu verknüpfen, die Vorteile für die parallele Ausführung überwiegen. Dieser Aufwand nimmt mit der Anzahl der Prozessoren zu.

Um den Planungsaufwand in diesem Beispiel zu reduzieren, können Sie äußere Schleifen parallelisieren, bevor Sie innere Schleifen parallelisieren, oder Sie verwenden ein anderes paralleles Konstrukt, z. B. Pipelines. Im folgenden Beispiel wird die- `ProcessImages` Funktion so geändert, dass der Algorithmus "Parallelität [::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) " verwendet wird, um die äußere Schleife zu parallelisieren.

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

Ein ähnliches Beispiel, in dem eine Pipeline verwendet wird, um die Bildverarbeitung parallel auszuführen, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Bild Verarbeitungs Netzwerks](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[Nach[oben](#top)]

## <a name="use-parallel_invoke-to-solve-divide-and-conquer-problems"></a><a name="divide-and-conquer"></a>Verwenden Sie parallel_invoke, um Probleme mit der Aufteilung und Eroberung zu lösen.

Ein Teilungs- *und Eroberungs* Problem ist eine Form des Fork-Join-Konstrukts, das Rekursion verwendet, um eine Aufgabe in Unteraufgaben aufzuteilen. Zusätzlich zu den Klassen "parallelcurrency [:: task_group](reference/task-group-class.md) " und " [parallelcurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) " können Sie auch den Algorithmus "Parallelität [::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) " verwenden, um Probleme mit der Aufteilung und Eroberung zu lösen. Die `parallel_invoke`-Algorithmus verfügt über eine kompaktere Syntax als Aufgabengruppenobjekte und ist nützlich, wenn Sie eine feste Anzahl paralleler Aufgaben haben.

Das folgende Beispiel veranschaulicht die Verwendung des `parallel_invoke`-Algorithmus zum Implementieren des bitonischen Sortieralgorithmus.

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

Mit dem `parallel_invoke`-Algorithmus wird der Aufwand reduziert, indem die letzte einer Reihe von Aufgaben im aufrufenden Kontext ausgeführt wird.

Die vollständige Version dieses Beispiels finden Sie unter Gewusst [wie: Verwenden von parallel_invoke zum Schreiben einer parallelen Sortier Routine](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Weitere Informationen zum `parallel_invoke` Algorithmus finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

[Nach[oben](#top)]

## <a name="use-cancellation-or-exception-handling-to-break-from-a-parallel-loop"></a><a name="breaking-loops"></a>Verwenden der Abbruch-oder Ausnahmebehandlung, um von einer parallelen Schleife zu unterbrechen

Die PPL bietet zwei Möglichkeiten, um parallele Arbeitsvorgänge abzubrechen, die von einer Aufgabengruppe oder einem parallelen Algorithmus ausgeführt werden. Eine Möglichkeit besteht darin, den Abbruchmechanismus zu verwenden, der von den Klassen [parallelcurrency:: task_group](reference/task-group-class.md) und [parallelcurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) bereitgestellt wird. Eine andere Möglichkeit ist das Auslösen einer Ausnahme im Text einer Arbeitsfunktion einer Aufgabe. Der Abbruchmechanismus ist effizienter als die Ausnahmebehandlung beim Abbrechen einer parallelen Arbeitsstruktur. Eine *parallele Arbeits* Struktur ist eine Gruppe verwandter Aufgaben Gruppen, in der einige Aufgaben Gruppen andere Aufgaben Gruppen enthalten. Der Abbruchmechanismus bricht eine Aufgabengruppe und ihre untergeordneten Aufgabengruppen von oben nach unten ab. Bei der Ausnahmebehandlung wird dagegen die umgekehrte Reihenfolge verwendet (Bottom-Up-Ansatz), sodass jede untergeordnete Aufgabengruppe einzeln abgebrochen werden muss.

Wenn Sie direkt mit einem Aufgaben Gruppen Objekt arbeiten, verwenden Sie die Methoden " [parallelcurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) " oder " [parallelcurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) ", um die Arbeit abzubrechen, die zu dieser Aufgaben Gruppe gehört. Zum Abbrechen eines parallelen Algorithmus, z. B. `parallel_for`, erstellen Sie eine übergeordnete Aufgabengruppe brechen diese Aufgabengruppe ab. Betrachten Sie beispielsweise die folgende Funktion `parallel_find_any`, die parallel nach einem Wert in einem Array sucht.

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

Da parallele Algorithmen Aufgabengruppen verwenden, wenn eine der parallelen Iterationen die übergeordnete Aufgabengruppe abbricht, wird die gesamte Aufgabe abgebrochen. Die vollständige Version dieses Beispiels finden Sie unter Gewusst [wie: Verwenden von Abbruch zum Unterbrechen einer parallelen Schleife](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).

Obwohl die Ausnahmebehandlung eine weniger effiziente Möglichkeit zum Abbrechen paralleler Aufgaben als der Abbruch ist, gibt es Fälle, in denen Ausnahmebehandlung sinnvoll ist. Zum Beispiel führt die folgende Methode, `for_all`, rekursiv eine Arbeitsfunktion auf jedem Knoten einer `tree`-Struktur aus. In diesem Beispiel ist der `_children` Datenmember eine [Std:: List](../../standard-library/list-class.md) , die- `tree` Objekte enthält.

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

Der Aufrufer der `tree::for_all`-Methode kann eine Ausnahme auslösen, wenn es nicht erforderlich ist, dass die Arbeitsfunktion für jedes Element der Struktur aufgerufen wird. Das folgende Beispiel zeigt die `search_for_value`-Funktion, die nach einem Wert im bereitgestellten `tree`-Objekt sucht. Die `search_for_value`-Funktion verwendet eine Arbeitsfunktion, die eine Ausnahme auslöst, wenn das aktuelle Element der Struktur mit dem bereitgestellten Wert übereinstimmt. Die `search_for_value`-Funktion verwendet einen `try-catch`-Block, um die Ausnahme zu erfassen und das Ergebnis in der Konsole auszugeben.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

Die vollständige Version dieses Beispiels finden Sie unter Gewusst [wie: Verwenden der Ausnahmebehandlung, um von einer parallelen Schleife zu unterbrechen](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

Allgemeine Informationen zu den von der ppl bereitgestellten Abbruch-und Ausnahme Behandlungs Mechanismen finden Sie unter [Abbruch in der ppl](cancellation-in-the-ppl.md) und [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

[Nach[oben](#top)]

## <a name="understand-how-cancellation-and-exception-handling-affect-object-destruction"></a><a name="object-destruction"></a>Grundlegendes zur Auswirkung der Abbruch-und Ausnahmebehandlung auf die Objekt Zerstörung

Eine abgebrochene Aufgabe in einer Struktur paralleler Arbeitsaufgaben kann dazu führen, dass untergeordnete Aufgaben nicht ausgeführt werden. Dies kann Probleme verursachen, wenn eine der untergeordneten Aufgaben einen Vorgang ausführen soll, der für die Anwendung von Bedeutung ist, beispielsweise das Freigeben einer Ressource. Darüber hinaus kann ein Aufgabenabbruch eine Ausnahme über einen Objektdestruktor weitergeben und ein nicht definiertes Verhalten in der Anwendung verursachen.

Im folgenden Beispiel beschreibt die `Resource`-Klasse eine Ressource und die `Container`-Klasse einen Container, der Ressourcen enthält. Im ihrem Destruktor ruft die `Container`-Klasse die `cleanup`-Methode für zwei ihrer `Resource`-Member parallel auf und ruft dann die `cleanup`-Methode für den dritten `Resource`-Member auf.

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

Obwohl dieses Muster selbst keine Probleme hat, sollten Sie den folgenden Code verwenden, der zwei Aufgaben parallel ausführt. Die erste Aufgabe erstellt ein `Container`-Objekt, und die zweite Aufgabe bricht die gesamte Aufgabe ab. Zum Beispiel verwendet das Beispiel zwei [parallelcurrency:: Event](../../parallel/concrt/reference/event-class.md) -Objekte, um sicherzustellen, dass der Abbruch nach der `Container` Erstellung des-Objekts auftritt und dass das- `Container` Objekt zerstört wird, nachdem der Abbruch Vorgang stattfindet.

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
Container 1: Freeing resources...Exiting program...
```

Dieses Codebeispiel enthält die folgenden Probleme, die dazu führen, dass es sich möglicherweise anders als erwartet verhält:

- Der Abbruch der übergeordneten Aufgabe bewirkt, dass die untergeordnete Aufgabe, der aufzurufende Parallelität [::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke), ebenfalls abgebrochen wird. Aus diesem Grund werden diese beiden Ressourcen nicht freigegeben.

- Der Abbruch der übergeordneten Aufgabe bewirkt, dass die untergeordnete Aufgabe eine interne Ausnahme auslöst. Da der `Container`-Destruktor diese Ausnahme nicht behandelt, wird die Ausnahme aufwärts weitergegeben, und die dritte Ressource wird nicht freigegeben.

- Die Ausnahme, die von der untergeordneten Aufgabe ausgelöst wird, wird über den `Container`-Destruktor weitergegeben. Durch das Auslösen von einem Destruktor wird die Anwendung in einen nicht definierten Zustand versetzt.

Es wird empfohlen, keine wichtigen Vorgänge, z. B. das Freigeben von Ressourcen, in den Aufgaben auszuführen, sofern Sie nicht garantieren können, dass diese Aufgaben nicht abgebrochen werden. Außerdem wird empfohlen, keine Laufzeitfunktionen zu verwenden, die im Destruktor der Typen ausgelöst werden können.

[Nach[oben](#top)]

## <a name="do-not-block-repeatedly-in-a-parallel-loop"></a><a name="repeated-blocking"></a>Nicht wiederholt in einer parallelen Schleife blockieren

Eine parallele Schleife, wie z. b. Parallelität [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) oder Parallelität [::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , die durch blockierende Vorgänge dominiert wird, kann dazu führen, dass die Laufzeit viele Threads über einen kurzen Zeitraum erstellt.

Die Concurrency Runtime führt zusätzliche Arbeiten aus, wenn eine Aufgabe beendet oder kooperativ blockiert oder zurückgehalten wird. Wenn eine parallelen Schleifeniteration blockiert, kann die Laufzeit eine andere Iteration starten. Wenn keine Leerlaufthreads verfügbar sind, erstellt die Laufzeit einen neuen Thread.

Wenn der Text einer parallelen Schleife gelegentlich blockt, hilft dieser Mechanismus beim Maximieren des Gesamtaufgabendurchsatzes. Wenn viele Iterationen blockieren, kann die Laufzeit viele Threads erstellen, um die zusätzlichen Arbeitsvorgänge auszuführen. Dies kann zu Arbeitsspeichermangel oder unzureichender Nutzung von Hardwareressourcen führen.

Sehen Sie sich das folgende Beispiel an, das die Funktion " [parallelcurrency:: Send](reference/concurrency-namespace-functions.md#send) " in jeder Iterations `parallel_for` Schleife aufruft. Da `send` kooperativ blockiert, erstellt die Laufzeit einen neuen Thread, um zusätzliche Arbeit bei jedem Aufruf von `send` auszuführen.

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

Wir empfehlen, den Code neu zu gestalten, um dieses Muster zu vermeiden. In diesem Beispiel können Sie die Erstellung zusätzlicher Threads vermeiden, indem Sie `send` in einer seriellen **`for`** Schleife aufrufen.

[Nach[oben](#top)]

## <a name="do-not-perform-blocking-operations-when-you-cancel-parallel-work"></a><a name="blocking"></a>Keine Blockierungs Vorgänge durchführen, wenn Sie parallele Arbeiten Abbrechen

Führen Sie nach Möglichkeit keine blockierenden Vorgänge aus, bevor Sie die [parallelcurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) -Methode oder die [parallelcurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) -Methode aufzurufen, um parallele Arbeiten abzubrechen.

Wenn eine Aufgabe einen kooperativen Blockierungsvorgang ausführt, kann die Laufzeit andere Aufgaben ausführen, während die erste Aufgabe auf Daten wartet. Die Laufzeit plant die wartende Aufgabe neu, wenn die Blockierung aufgehoben wird. Die Laufzeit plant in der Regel Aufgaben neu, die vor kurzem entsperrt wurden, bevor sie Aufgaben, die vor längerer Zeit entsperrt wurden, neu plant. Aus diesem Grund könnte die Laufzeit unnötige Arbeit während des blockierenden Vorgangs planen, was zu Leistungseinbußen führt. Wenn Sie also einen Blockierungsvorgang ausführen, bevor Sie parallele Arbeitsvorgänge abbrechen, kann der blockierende Vorgang den Aufruf von `cancel` verzögern. Dies führt dazu, dass andere Aufgaben unnötige Arbeit ausführen.

Das folgende Beispiel definiert die `parallel_find_answer`-Funktion, die ein Element des bereitgestellten Arrays sucht, das der angegebenen Prädikatfunktion entspricht. Wenn die Prädikat Funktion zurückgibt **`true`** , erstellt die parallel work-Funktion ein `Answer` -Objekt und bricht die gesamte Aufgabe ab.

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

Der `new`-Operator führt eine Heapzuordnung aus, die blockieren könnte. Die Laufzeit führt nur dann andere Aufgaben aus, wenn der Task einen kooperativen Blockierungs Aufrufvorgang ausführt, z. b. einen aufrufsvorgang von " [parallelcurrency:: critical_section:](reference/critical-section-class.md#lock)

Das folgende Beispiel zeigt, wie Sie unnötige Arbeiten verhindern und damit die Leistung verbessern. In diesem Beispiel wird die Aufgabengruppe abgebrochen, bevor sie den Speicher für das `Answer`-Objekt zuweist.

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[Nach[oben](#top)]

## <a name="do-not-write-to-shared-data-in-a-parallel-loop"></a><a name="shared-writes"></a>In einer parallelen Schleife nicht in freigegebene Daten schreiben

Der Concurrency Runtime bietet verschiedene Datenstrukturen, z. b. [Concurrency:: CRITICAL_SECTION](../../parallel/concrt/reference/critical-section-class.md), die den gleichzeitigen Zugriff auf freigegebene Daten synchronisieren. Diese Datenstrukturen sind in vielen Fällen hilfreich, wenn z. B. mehrere Aufgaben nur selten gemeinsamen Zugriff auf eine Ressource erfordern.

Betrachten Sie das folgende Beispiel, das den Algorithmus "Parallelität [::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) " und ein- `critical_section` Objekt verwendet, um die Anzahl von Primzahlen in einem [Std:: Array](../../standard-library/array-class-stl.md) -Objekt zu berechnen. Dieses Beispiel skaliert nicht, da jeder Thread warten muss, um auf die freigegebene Variable `prime_sum` zuzugreifen.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

Dieses Beispiel kann auch zu Leistungseinbußen führen, da der häufige Sperrvorgang die Schleife effektiv serialisiert. Wenn darüber hinaus ein Concurrency Runtime-Objekt einen Blockierungsvorgang ausführt, erstellt der Planer möglicherweise einen zusätzlichen Thread, um andere Aufgaben auszuführen, während der erste Thread auf Daten wartet. Wenn die Laufzeit viele Threads erstellt, da viele Aufgaben auf freigegebene Daten warten, kann die Anwendungsleistung abnehmen oder die Anwendung in einen Ressourcenmangelzustand versetzt werden.

Die ppl definiert die Klasse " [parallelcurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) ", die Ihnen hilft, den freigegebenen Zustand zu eliminieren, indem Sie den Zugriff auf freigegebene Ressourcen auf Sperr freie Weise bereitstellen. Die `combinable`-Klasse stellt lokalen Threadspeicher bereit, mit dem Sie differenzierte Berechnungen ausführen und dann diese Berechnungen in einem Endergebnis zusammenführen können. Stellen Sie sich ein `combinable`-Objekt wie eine Reduktionsvariable vor.

Im folgenden Beispiel wird das vorherige mithilfe eines `combinable`-Objekts anstelle eines `critical_section`-Objekts zum Berechnen der Summe geändert. Dieses Beispiel skaliert, da jeder Thread eine eigene lokale Kopie der Summe enthält. In diesem Beispiel wird die [parallelcurrency:: combinable:: Combine](reference/combinable-class.md#combine) -Methode verwendet, um die lokalen Berechnungen in das Endergebnis zu überführen.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

Die vollständige Version dieses Beispiels finden Sie unter Gewusst [wie: verbessern der Leistung mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Weitere Informationen zur `combinable` -Klasse finden Sie unter [parallele Container und Objekte](../../parallel/concrt/parallel-containers-and-objects.md).

[Nach[oben](#top)]

## <a name="when-possible-avoid-false-sharing"></a><a name="false-sharing"></a>Vermeiden Sie nach Möglichkeit falsche Freigabe

Eine *falsche Freigabe* tritt auf, wenn mehrere gleichzeitige Tasks, die auf separaten Prozessoren ausgeführt werden, in Variablen schreiben, die sich in der gleichen Cache Zeile befinden. Wenn eine Aufgabe in eine der Variablen schreibt, wird die Cachezeile für beide Variablen ungültig. Jeder Prozessor muss die Cachezeile jedes Mal neu laden, wenn die Cachezeile ungültig ist. Daher kann False Sharing zu Leistungseinbußen in der Anwendung führen.

Das folgende grundlegende Beispiel zwei gleichzeitige Aufgaben, die jeweils eine gemeinsame Zählervariable erhöhen.

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

Um die gemeinsame Nutzung von Daten zwischen den beiden Aufgaben zu vermeiden, können Sie das Beispiel so ändern, dass zwei Zählervariablen verwendet werden. In diesem Beispiel wird der endgültige Zählerwert berechnet, nachdem die Aufgaben beendet wurden. Dieses Beispiel veranschaulicht jedoch False Sharing, da sich die Variablen `count1` und `count2` wahrscheinlich in derselben Cachezeile befinden.

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

Eine Möglichkeit zur Eliminierung von False Sharing besteht darin, sicherzustellen, dass sich die Zählervariablen in unterschiedlichen Cachezeilen befinden. Das folgende Beispiel richtet die Variablen `count1` und `count2` auf 64-Byte-Grenzen aus.

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

In diesem Beispiel wird davon ausgegangen, dass die Größe des Arbeitsspeichercaches höchstens 64 Byte beträgt.

Es wird empfohlen, dass Sie die Klasse " [parallelcurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) " verwenden, wenn Sie Daten zwischen Aufgaben freigeben müssen. Die `combinable`-Klasse erstellt lokale Threadvariablen derart, dass False Sharing weniger wahrscheinlich ist. Weitere Informationen zur `combinable` -Klasse finden Sie unter [parallele Container und Objekte](../../parallel/concrt/parallel-containers-and-objects.md).

[Nach[oben](#top)]

## <a name="make-sure-that-variables-are-valid-throughout-the-lifetime-of-a-task"></a><a name="lifetime"></a>Stellen Sie sicher, dass die Variablen während der gesamten Lebensdauer einer Aufgabe gültig sind.

Wenn Sie einer Aufgabengruppe oder einem parallelen Algorithmus einen Lambdaausdruck bereitstellen, gibt die Erfassungsklausel an, ob der Text des Lambdaausdrucks auf Variablen im einschließenden Bereich als Wert oder als Verweis zugreift. Wenn Sie Variablen als Verweis an einen Lambdaausdruck übergeben, müssen Sie sicherstellen, dass die Lebensdauer dieser Variablen bis zum Beenden der Aufgabe erhalten bleibt.

Betrachten Sie das folgende Beispiel, in dem die `object`-Klasse und die `perform_action`-Funktion definiert werden. Die `perform_action`-Funktion erstellt eine `object`-Variable und führt eine Aktion für diese Variable asynchron durch. Da die Aufgabe nicht unbedingt vor der Rückgabe der `perform_action`-Funktion beendet wird, stürzt das Programm ab oder zeigt nicht definiertes Verhalten, wenn die `object`-Variable beim Ausführen der Aufgabe gelöscht wird.

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

Je nach den Anforderungen Ihrer Anwendung können Sie eine der folgenden Methoden verwenden, um zu garantieren, dass Variablen während der Lebensdauer der einzelnen Aufgaben gültig bleiben.

Das folgende Beispiel übergibt die `object`-Variable als Wert an die Aufgabe. Aus diesem Grund funktioniert die Aufgabe mit der eigenen Kopie der Variablen.

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

Da die `object`-Variable als Wert übergeben wird, werden alle Zustandsänderungen, die für diese Variablen auftreten, nicht in der ursprünglichen Kopie angezeigt.

Im folgenden Beispiel wird die-Methode [task_group](reference/task-group-class.md#wait) verwendet, um sicherzustellen, dass die Aufgabe abgeschlossen ist, bevor die- `perform_action` Funktion zurückgegeben wird.

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

Da die Aufgabe jetzt abgeschlossen ist, bevor die Funktion beendet wird, verhält sich die `perform_action`-Funktion nicht mehr asynchron.

Das folgende Beispiel ändert die `perform_action`-Funktion für die Übergabe eines Verweises an die `object`-Variable. Der Aufrufer muss sicherstellen, dass die Lebensdauer der `object`-Variable gültig ist, bis die Aufgabe abgeschlossen ist.

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

Sie können auch einen Zeiger zur Steuerung der Lebensdauer eines Objekts verwenden, das Sie an eine Aufgabengruppe oder einen parallelen Algorithmus übergeben.

Weitere Informationen zu Lambda-Ausdrücken finden Sie unter [Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md).

[Nach[oben](#top)]

## <a name="see-also"></a>Weitere Informationen

[Bewährte Methoden für Concurrency Runtime](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Parallele Container und Objekte](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br/>
[Abbruch in der PPL](cancellation-in-the-ppl.md)<br/>
[Behandlung von Ausnahmen](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Exemplarische Vorgehensweise: Erstellen eines Bild Verarbeitungs Netzwerks](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Gewusst wie: Verwenden von parallel_invoke zum Schreiben einer parallelen Sortier Routine](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br/>
[Gewusst wie: Verwenden von Abbruch zum Abbrechen einer parallelen Schleife](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br/>
[Gewusst wie: verbessern der Leistung mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
[Bewährte Methoden in der Bibliothek für asynchrone Agents](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br/>
[Allgemeine bewährte Methoden für die Concurrency Runtime](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
