---
title: Parallele Algorithmen
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: a31787172c89e23e5eb32aa203b9f541584c0f68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363209"
---
# <a name="parallel-algorithms"></a>Parallele Algorithmen

Die Parallel Patterns Library (PPL) stellt Algorithmen bereit, die gleichzeitig Arbeiten an Datensammlungen ausführen. Diese Algorithmen ähneln denen der C++-Standardbibliothek.

Die parallelen Algorithmen bestehen aus vorhandenen Funktionen in der Concurrency Runtime. Beispielsweise verwendet der [Algorithmus concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) ein [concurrency::structured_task_group-Objekt,](../../parallel/concrt/reference/structured-task-group-class.md) um die parallelen Schleifeniterationen auszuführen. Die `parallel_for` Algorithmuspartitionen funktionieren optimal, wenn man bedenkt, wie viele Rechenressourcen zur Verfügung stehen.

## <a name="sections"></a><a name="top"></a>Bereichen

- [Der parallel_for-Algorithmus](#parallel_for)

- [Der parallel_for_each-Algorithmus](#parallel_for_each)

- [Der parallel_invoke-Algorithmus](#parallel_invoke)

- [Die parallel_transform- und parallel_reduce-Algorithmen](#parallel_transform_reduce)

  - [Der parallel_transform-Algorithmus](#parallel_transform)

  - [Der parallel_reduce-Algorithmus](#parallel_reduce)

  - [Beispiel: Paralleles Ausführen der Zuordnung und Reduzierung](#map_reduce_example)

- [Partitionieren der Arbeit](#partitions)

- [Parallele Sortierung](#parallel_sorting)

  - [Auswählen eines Sortieralgorithmus](#choose_sort)

## <a name="the-parallel_for-algorithm"></a><a name="parallel_for"></a>Der parallel_for-Algorithmus

Der [Algorithmus concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) führt dieselbe Aufgabe wiederholt parallel aus. Jede dieser Aufgaben wird durch einen Iterationswert parametriert. Dieser Algorithmus ist nützlich, wenn Sie über einen Schleifentext verfügen, der keine Ressourcen für Iterationen dieser Schleife verwendet.

Der `parallel_for` Algorithmus partitioniert Aufgaben optimal für die parallele Ausführung. Es verwendet einen Work-Stealing-Algorithmus und Range-Stealing, um diese Partitionen auszugleichen, wenn Workloads unausgewogen sind. Wenn eine Schleifeniteration kooperativ blockiert, verteilt die Laufzeit den Iterationsbereich, der dem aktuellen Thread zugewiesen ist, an andere Threads oder Prozessoren weiter. Wenn ein Thread einen Reihe von Iterationen abschließt, verteilt die Laufzeit Arbeit von anderen Threads an diesen Thread. Der `parallel_for` Algorithmus unterstützt auch *verschachtelte Parallelität*. Wenn eine parallele Schleife eine andere parallele Schleife enthält, koordiniert die Laufzeit verarbeitungsressourcen zwischen den Schleifenkörpern auf effiziente Weise für die parallele Ausführung.

Der `parallel_for` Algorithmus hat mehrere überladene Versionen. Die erste Version nimmt einen Startwert, einen Endwert und eine Arbeitsfunktion (ein Lambda-Ausdruck, ein Funktionsobjekt oder einen Funktionszeiger) an. Die zweite Version nimmt einen Startwert, einen Endwert, einen Schrittwert und eine Arbeitsfunktion. Die erste Version dieser Funktion verwendet 1 als Schrittwert. Die übrigen Versionen verwenden Partitionerobjekte, mit `parallel_for` denen Sie angeben können, wie Bereiche zwischen Threads partitioniert werden sollen. Partitionierer werden im Abschnitt [Partitionierungsarbeit](#partitions) in diesem Dokument ausführlicher erläutert.

Sie können `for` viele Schleifen `parallel_for`konvertieren, um . Der `parallel_for` Algorithmus unterscheidet sich `for` jedoch wie folgt von der Anweisung:

- Der `parallel_for` `parallel_for` Algorithmus führt die Aufgaben nicht in einer vorgegebenen Reihenfolge aus.

- Der `parallel_for` Algorithmus unterstützt keine willkürlichen Beendigungsbedingungen. Der `parallel_for` Algorithmus wird beendet, wenn der aktuelle `last`Wert der Iterationsvariablen einen kleiner als ist.

- Der `_Index_type` Typparameter muss ein integraler Typ sein. Dieser integrale Typ kann signiert oder nicht signiert werden.

- Die Schleifeniteration muss vorwärts sein. Der `parallel_for` Algorithmus löst eine Ausnahme vom Typ `_Step` [std::invalid_argument](../../standard-library/invalid-argument-class.md) aus, wenn der Parameter kleiner als 1 ist.

- Der Ausnahmebehandlungsmechanismus für `parallel_for` den Algorithmus unterscheidet `for` sich von dem einer Schleife. Wenn mehrere Ausnahmen gleichzeitig in einem parallelen Schleifentext auftreten, gibt die Laufzeit nur `parallel_for`eine der Ausnahmen an den Thread weiter, der aufgerufen hat. Wenn eine Schleifeniteration eine Ausnahme auslöst, stoppt die Laufzeit die Gesamtschleife nicht sofort. Stattdessen wird die Schleife in den abgebrochenen Zustand versetzt, und die Laufzeit verwirft alle Aufgaben, die noch nicht gestartet wurden. Weitere Informationen zur Ausnahmebehandlung und parallelen Algorithmen finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Obwohl `parallel_for` der Algorithmus keine willkürlichen Beendigungsbedingungen unterstützt, können Sie die Löschung verwenden, um alle Aufgaben zu beenden. Weitere Informationen zur Stornierung finden Sie [unter Stornierung in der PPL](cancellation-in-the-ppl.md).

> [!NOTE]
> Die Planungskosten, die sich aus dem Lastenausgleich und der Unterstützung für Features wie Abbruch ergeben, können die Vorteile der parallelen Ausführung des Schleifentexts nicht überwinden, insbesondere wenn der Schleifenkörper relativ klein ist. Sie können diesen Overhead minimieren, indem Sie einen Partitionierer in der parallelen Schleife verwenden. Weitere Informationen finden Sie weiter unten in diesem Dokument unter [Partitionierungsarbeit.](#partitions)

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die `parallel_for` grundlegende Struktur des Algorithmus. In diesem Beispiel wird jeder Wert im Bereich [1, 5] parallel auf die Konsole gedruckt.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe:

```Output
1 2 4 3 5
```

Da `parallel_for` der Algorithmus für jedes Element parallel wirkt, variiert die Reihenfolge, in der die Werte in der Konsole gedruckt werden.

Ein vollständiges Beispiel, `parallel_for` das den Algorithmus verwendet, finden Sie unter [Gewusst wie: Schreiben einer parallel_for Schleife](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Oben](#top)]

## <a name="the-parallel_for_each-algorithm"></a><a name="parallel_for_each"></a>Der parallel_for_each-Algorithmus

Der [algorithmus concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) führt Aufgaben für einen iterativen Container aus, z. B. in der C++-Standardbibliothek, parallel. Er verwendet die gleiche Partitionierungslogik wie der `parallel_for`-Algorithmus.

Der `parallel_for_each` Algorithmus ähnelt dem C++-Standardbibliothekstd::for_each-Algorithmus, mit der Ausnahme, dass der [std::for_each](../../standard-library/algorithm-functions.md#for_each) `parallel_for_each` Algorithmus die Aufgaben gleichzeitig ausführt. Wie andere parallele `parallel_for_each` Algorithmen, führt die Aufgaben nicht in einer bestimmten Reihenfolge.

Obwohl `parallel_for_each` der Algorithmus sowohl auf Forward-Iteratoren als auch auf zufälligen Zugriffs-Iteratoren funktioniert, funktioniert er besser mit zufälligen Zugriffs-Iteratoren.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die `parallel_for_each` grundlegende Struktur des Algorithmus. In diesem Beispiel wird jeder Wert in einem [std::array-Objekt](../../standard-library/array-class-stl.md) parallel in die Konsole gedruckt.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe:

```Output
4 5 1 2 3
```

Da `parallel_for_each` der Algorithmus für jedes Element parallel wirkt, variiert die Reihenfolge, in der die Werte in der Konsole gedruckt werden.

Ein vollständiges Beispiel, `parallel_for_each` das den Algorithmus verwendet, finden Sie unter [Gewusst wie: Schreiben einer parallel_for_each Loop](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Oben](#top)]

## <a name="the-parallel_invoke-algorithm"></a><a name="parallel_invoke"></a>Der parallel_invoke-Algorithmus

Der [Algorithmus concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) führt eine Reihe von Aufgaben parallel aus. Sie wird erst zurückgegeben, wenn jeder Vorgang abgeschlossen ist. Dieser Algorithmus ist nützlich, wenn Sie mehrere unabhängige Aufgaben haben, die Sie gleichzeitig ausführen möchten.

Der `parallel_invoke` Algorithmus nimmt als Parameter eine Reihe von Arbeitsfunktionen (Lambda-Funktionen, Funktionsobjekte oder Funktionszeiger). Der `parallel_invoke` Algorithmus ist überladen, um zwischen zwei und zehn Parameter zu nehmen. Jede Funktion, an `parallel_invoke` die Sie übergeben, muss null Parameter annehmen.

Wie andere parallele `parallel_invoke` Algorithmen, führt die Aufgaben nicht in einer bestimmten Reihenfolge. Im Thema [Taskparallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md) wird `parallel_invoke` erläutert, wie sich der Algorithmus auf Aufgaben und Aufgabengruppen bezieht.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die `parallel_invoke` grundlegende Struktur des Algorithmus. In diesem Beispiel `twice` wird die Funktion gleichzeitig für drei lokale Variablen aufgeschrieben und das Ergebnis in die Konsole gedruckt.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
108 11.2 HelloHello
```

Beispiele für die `parallel_invoke` Verwendung des Algorithmus finden Sie unter [Gewusst wie: Verwenden parallel_invoke zum Schreiben einer parallelen Sortierroutine](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) und [How to: Use parallel_invoke to Execute Parallel Operations](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Oben](#top)]

## <a name="the-parallel_transform-and-parallel_reduce-algorithms"></a><a name="parallel_transform_reduce"></a>Die parallel_transform und parallel_reduce Algorithmen

[Die Algorithmen concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) und [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) sind parallele Versionen der C++-Standardbibliotheksalgorithmen [std::transform](../../standard-library/algorithm-functions.md#transform) bzw. [std::accumulate.](../../standard-library/numeric-functions.md#accumulate) Die Concurrency Runtime-Versionen verhalten sich wie die C++-Standardbibliotheksversionen, mit der Ausnahme, dass die Vorgangsreihenfolge nicht bestimmt wird, da sie parallel ausgeführt werden. Verwenden Sie diese Algorithmen, wenn Sie mit einem Satz arbeiten, der groß genug ist, um Leistungs- und Skalierbarkeitsvorteile aus der parallelen Verarbeitung zu erzielen.

> [!IMPORTANT]
> Die `parallel_transform` `parallel_reduce` und Algorithmen unterstützen nur zufälligen Zugriff, bidirektionale und Vorwärtsiteratoren, da diese Iteratoren stabile Speicheradressen erzeugen. Außerdem müssen diese Iteratoren`const` Nicht-l-Werte erzeugen.

### <a name="the-parallel_transform-algorithm"></a><a name="parallel_transform"></a>Der parallel_transform-Algorithmus

Sie können `parallel transform` den Algorithmus verwenden, um viele Datenparallelisierungsvorgänge auszuführen. Beispielsweise können Sie folgende Aktionen ausführen:

- Passen Sie die Helligkeit eines Bildes an, und führen Sie andere Bildverarbeitungsvorgänge durch.

- Summe oder nehmen Sie das Punktprodukt zwischen zwei Vektoren, und führen Sie andere numerische Berechnungen für Vektoren durch.

- Führen Sie eine 3D-Raytracing durch, bei der jede Iteration auf ein Pixel verweist, das gerendert werden muss.

Das folgende Beispiel zeigt die grundlegende Struktur, die zum Aufrufen des `parallel_transform` Algorithmus verwendet wird. In diesem Beispiel werden jedes Element eines std::[vektorobjekts](../../standard-library/vector-class.md) auf zwei Arten negiert. Auf dem ersten Weg wird ein Lambda-Ausdruck verwendet. Der zweite Weg verwendet [std::negate](../../standard-library/negate-struct.md), das von [std::unary_function](../../standard-library/unary-function-struct.md)ableitet.

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> In diesem Beispiel wird `parallel_transform`die grundlegende Verwendung von veranschaulicht. Da die Arbeitsfunktion keine nennenswerte Arbeit ausführt, ist in diesem Beispiel keine signifikante Leistungssteigerung zu erwarten.

Der `parallel_transform` Algorithmus hat zwei Überladungen. Die erste Überladung nimmt einen Eingangsbereich und eine unäre Funktion. Die unäre Funktion kann ein Lambda-Ausdruck sein, der ein Argument, ein `unary_function`Funktionsobjekt oder einen Typ verwendet, der von ableitet. Die zweite Überladung nimmt zwei Eingabebereiche und eine binäre Funktion an. Die binäre Funktion kann ein Lambda-Ausdruck sein, der zwei Argumente, ein Funktionsobjekt oder einen Typ verwendet, der von [std::binary_function](../../standard-library/binary-function-struct.md)ableitet. Das folgende Beispiel veranschaulicht diese Unterschiede.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> Der Iterator, den Sie `parallel_transform` für die Ausgabe von bereitstellen, muss den Eingangsiterator vollständig überlappen oder gar nicht überlappen. Das Verhalten dieses Algorithmus ist nicht angegeben, wenn sich die Eingabe- und Ausgabeiteratoren teilweise überlappen.

### <a name="the-parallel_reduce-algorithm"></a><a name="parallel_reduce"></a>Der parallel_reduce-Algorithmus

Der `parallel_reduce` Algorithmus ist nützlich, wenn Sie über eine Abfolge von Vorgängen verfügen, die die assoziative Eigenschaft erfüllen. (Dieser Algorithmus erfordert keine kommutative Eigenschaft.) Hier sind einige der Vorgänge, `parallel_reduce`die Sie mit ausführen können:

- Multiplizieren Sie Sequenzen von Matrizen, um eine Matrix zu erzeugen.

- Multiplizieren Sie einen Vektor mit einer Sequenz von Matrizen, um einen Vektor zu erzeugen.

- Berechnen Sie die Länge einer Sequenz von Zeichenfolgen.

- Kombinieren Sie eine Liste von Elementen, z. B. Zeichenfolgen, in einem Element.

Das folgende grundlegende Beispiel zeigt, wie der `parallel_reduce` Algorithmus verwendet wird, um eine Sequenz von Zeichenfolgen in einer Zeichenfolge zu kombinieren. Wie bei den `parallel_transform`Beispielen für sind in diesem einfachen Beispiel keine Leistungssteigerungen zu erwarten.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

In vielen Fällen können `parallel_reduce` Sie sich die Verwendung `parallel_for_each` des Algorithmus zusammen mit der [concurrency::combinable-Klasse](../../parallel/concrt/reference/combinable-class.md) als Abkürzung vorstellen.

### <a name="example-performing-map-and-reduce-in-parallel"></a><a name="map_reduce_example"></a>Beispiel: Ausführen von Map und Reduce in Parallel

Ein *Zuordnungsvorgang* wendet eine Funktion auf jeden Wert in einer Sequenz an. Ein *Reduktionsvorgang* kombiniert die Elemente einer Sequenz in einem Wert. Sie können die Funktionen C++ Standardlibrary [std::transform](../../standard-library/algorithm-functions.md#transform) und [std::accumulate](../../standard-library/numeric-functions.md#accumulate) verwenden, um Karten auszuführen und Vorgänge zu reduzieren. Bei vielen Problemen können Sie `parallel_transform` jedoch den Algorithmus verwenden, um `parallel_reduce` den Kartenvorgang parallel auszuführen, und der Algorithmus führt den Reduzierungsvorgang parallel aus.

Im folgenden Beispiel wird die Zeit verglichen, die benötigt wird, um die Summe der Primzahlen seriell und parallel zu berechnen. Die Kartenphase transformiert Nicht-Prime-Werte in 0, und die Reduktionsphase summiert die Werte.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Ein weiteres Beispiel, das eine Zuordnung ausführt und den Vorgang parallel reduziert, finden Sie unter [Gewusst wie: Ausführen von Zuordnungs- und Reduzieren von Vorgängen in Parallel](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Oben](#top)]

## <a name="partitioning-work"></a><a name="partitions"></a>Partitionierungsarbeit

Um einen Vorgang in einer Datenquelle zu parallelisieren, besteht ein wesentlicher Schritt darin, die Quelle in mehrere Abschnitte zu *partitionieren,* auf die gleichzeitig von mehreren Threads zugegriffen werden kann. Ein Partitionierer gibt an, wie ein paralleler Algorithmus Bereiche zwischen Threads partitionieren soll. Wie bereits in diesem Dokument erläutert, verwendet die PPL einen Standardmäßigen Partitionierungsmechanismus, der eine anfängliche Arbeitsauslastung erstellt und dann einen Work-Stealing-Algorithmus und Range Stealing verwendet, um diese Partitionen auszugleichen, wenn Workloads unausgewogen sind. Wenn z. B. eine Schleifeniteration einen Bereich von Iterationen abschließt, verteilt die Laufzeit Arbeit von anderen Threads an diesen Thread neu. In einigen Szenarien sollten Sie jedoch einen anderen Partitionierungsmechanismus angeben, der besser für Ihr Problem geeignet ist.

Die `parallel_for` `parallel_for_each`, `parallel_transform` und Algorithmen stellen überladene Versionen `_Partitioner`bereit, die einen zusätzlichen Parameter annehmen, . Dieser Parameter definiert den Partitionertyp, der Arbeit trennt. Hier sind die Arten von Partitionierern, die die PPL definiert:

[Parallelität::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Unterteilt die Arbeit in eine feste Anzahl von Bereichen (in der Regel die Anzahl der Arbeitsthreads, die für die Arbeit in der Schleife verfügbar sind). Dieser Partitionertyp `static_partitioner`ähnelt , verbessert jedoch die Cacheaffinität durch die Zuordnung von Bereichen zu Arbeitsthreads. Dieser Partitionierertyp kann die Leistung verbessern, wenn eine Schleife mehrmals über denselben Datensatz ausgeführt wird (z. B. eine Schleife innerhalb einer Schleife) und die Daten in den Cache passen. Dieser Partitionierer nimmt nicht vollständig an der Stornierung teil. Es verwendet auch keine kooperative Blockierungsemantik und kann daher nicht mit parallelen Schleifen verwendet werden, die eine Vorwärtsabhängigkeit aufweisen.

[Parallelität::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Unterteilt die Arbeit in eine anfängliche Anzahl von Bereichen (in der Regel die Anzahl der Arbeitsthreads, die für die Arbeit in der Schleife verfügbar sind). Die Laufzeit verwendet diesen Typ standardmäßig, wenn Sie keinen überladenen parallelen Algorithmus aufrufen, der einen `_Partitioner` Parameter annimmt. Jeder Bereich kann in Unterbereiche unterteilt werden und ermöglicht so einen Lastenausgleich. Wenn eine Reihe von Arbeiten abgeschlossen ist, verteilt die Laufzeit Arbeitsbereiche von anderen Threads an diesen Thread. Verwenden Sie diesen Partitionierer, wenn Ihre Workload nicht unter eine der anderen Kategorien fällt oder Sie volle Unterstützung für den Abbruch oder die kooperative Blockierung benötigen.

[Parallelität::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Unterteilt die Arbeit in Bereiche, sodass jeder Bereich mindestens die Anzahl der Iterationen hat, die durch die angegebene Chunk-Größe angegeben werden. Dieser Partitionierertyp ist am Lastenausgleich beteiligt. Die Laufzeit unterteilt jedoch keine Bereiche in Unterbereiche. Für jede Arbeitskraft wird die Laufzeit auf Abbruch `_Chunk_size` überprüft und den Lastenausgleich nach Abschluss der Iterationen durchführt.

[Parallelität::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Unterteilt die Arbeit in eine feste Anzahl von Bereichen (in der Regel die Anzahl der Arbeitsthreads, die für die Arbeit in der Schleife verfügbar sind). Dieser Partitionierertyp kann die Leistung verbessern, da er keinen Arbeitsdiebstahl verwendet und daher weniger Overhead hat. Verwenden Sie diesen Partitionierertyp, wenn jede Iteration einer parallelen Schleife einen festen und einheitlichen Arbeitsaufwand ausführt und Sie keine Unterstützung für Abbruch oder kooperatives Blockieren benötigen.

> [!WARNING]
> Die `parallel_for_each` `parallel_transform` und-Algorithmen unterstützen nur Container, die zufällige Zugriffs-Iteratoren (z. B. std::[vector](../../standard-library/vector-class.md)) für die statischen, einfachen und Affinitätspartitionierer verwenden. Die Verwendung von Containern, die bidirektionale und weiterleitende Iteratoren verwenden, führt zu einem Kompilierungsfehler. Der Standardpartitionierer `auto_partitioner`, unterstützt alle drei iteratortypen.

In der Regel werden diese Partitionierer auf `affinity_partitioner`die gleiche Weise verwendet, mit Ausnahme von . Die meisten Partitionertypen behalten den Status nicht bei und werden von der Laufzeit nicht geändert. Daher können Sie diese Partitionerobjekte an der Aufrufsite erstellen, wie im folgenden Beispiel gezeigt.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Sie müssen jedoch `affinity_partitioner` ein Objekt als`const`Nicht-, l-Wert-Referenz übergeben, damit der Algorithmus den Status für zukünftige Schleifen speichern kann, um sie wiederzuverwenden. Das folgende Beispiel zeigt eine grundlegende Anwendung, die denselben Vorgang für einen Datensatz mehrmals parallel ausführt. Die Verwendung `affinity_partitioner` von kann die Leistung verbessern, da das Array wahrscheinlich in den Cache passt.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> Seien Sie vorsichtig, wenn Sie vorhandenen Code ändern, `static_partitioner` der `affinity_partitioner`auf kooperativer Blockierungssemantik für die Verwendung oder verwendet wird. Diese Partitionierertypen verwenden keinen Lastenausgleich oder Bereichsdiebstahl und können daher das Verhalten Ihrer Anwendung ändern.

Die beste Methode, um zu bestimmen, ob ein Partitionierer in einem bestimmten Szenario verwendet werden soll, besteht darin, zu experimentieren und zu messen, wie lange die Vorgänge unter repräsentativen Lasten und Computerkonfigurationen abgeschlossen werden müssen. Die statische Partitionierung könnte z.B. möglicherweise auf einem Mehrkerncomputer mit nur wenigen Kernen für erhebliche Beschleunigung sorgen, doch bei Computern mit relativ vielen Kernen zu Verlangsamungen führen.

[[Oben](#top)]

## <a name="parallel-sorting"></a><a name="parallel_sorting"></a>Parallele Sortierung

Die PPL stellt drei Sortieralgorithmen bereit: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)und [concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Diese Sortieralgorithmen sind nützlich, wenn Sie über einen Datensatz verfügen, der davon profitieren kann, parallel sortiert zu werden. Insbesondere ist das parallele Sortieren nützlich, wenn Sie über ein großes Dataset verfügen oder wenn Sie einen rechen- teuren Vergleichsvorgang zum Sortieren Ihrer Daten verwenden. Jeder dieser Algorithmen sortiert Elemente an Ort und Stelle.

Die `parallel_sort` `parallel_buffered_sort` und Algorithmen sind beide vergleichsbasierte Algorithmen. Das heißt, sie vergleichen Elemente nach Wert. Der `parallel_sort` Algorithmus hat keine zusätzlichen Speicheranforderungen und eignet sich für die allgemeine Sortierung. Der `parallel_buffered_sort` Algorithmus kann `parallel_sort`besser als ausgeführt werden, erfordert jedoch O(N)-Leerzeichen.

Der `parallel_radixsort` Algorithmus ist hashbasiert. Das heißt, es verwendet ganzzahlige Schlüssel, um Elemente zu sortieren. Mithilfe von Schlüsseln kann dieser Algorithmus das Ziel eines Elements direkt berechnen, anstatt Vergleiche zu verwenden. Wie `parallel_buffered_sort`erfordert dieser Algorithmus O(N)-Leerraum.

Die folgende Tabelle fasst die wichtigen Eigenschaften der drei parallelen Sortieralgorithmen zusammen.

|Algorithmus|BESCHREIBUNG|Sortiermechanismus|Sortierstabilität|Arbeitsspeicheranforderungen|Zeitkomplexität|Iterator-Zugang|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Allgemeine Vergleichssortierung.|Vergleichsbasiert (aufsteigend)|Instabil|Keine|O((N/P)log(N/P) + 2N((P-1)/P))|Zufällig|
|`parallel_buffered_sort`|Schnellere allgemeine Vergleichs-basierte Sortierung, die O(N)-Speicherplatz erfordert.|Vergleichsbasiert (aufsteigend)|Instabil|Erfordert zusätzlichen O(N)-Speicherplatz|O((N/P)log(N))|Zufällig|
|`parallel_radixsort`|Ganzzahlschlüsselbasierte Sortierung, die O(N)-Leerzeichen erfordert.|Hash-basiert|Stable|Erfordert zusätzlichen O(N)-Speicherplatz|O(N/P)|Zufällig|

Die folgende Abbildung zeigt die wichtigen Eigenschaften der drei parallelen Sortieralgorithmen grafischer.

![Vergleich der Sortieralgorithmen](../../parallel/concrt/media/concrt_parallel_sorting.png "Vergleich der Sortieralgorithmen")

Diese parallelen Sortieralgorithmen folgen den Regeln der Abbruch- und Ausnahmebehandlung. Weitere Informationen zur Abbruch- und Ausnahmebehandlung in der Concurrency Runtime finden Sie unter [Abbrechen paralleler Algorithmen](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) und [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
> Diese parallelen Sortieralgorithmen unterstützen die Bewegungssemantik. Sie können einen Verschiebungszuweisungsoperator definieren, damit Swap-Vorgänge effizienter ausgeführt werden können. Weitere Informationen zur Verschiebungssemantik und zum Verschiebungszuweisungsoperator finden Sie unter [Rvalue Reference Declarator: &&](../../cpp/rvalue-reference-declarator-amp-amp.md)und [Move Constructors and Move Assignment Operators (C++)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Wenn Sie keinen Verschiebungszuweisungsoperator oder keine Swap-Funktion bereitstellen, verwenden die Sortieralgorithmen den Kopierkonstruktor.

Das folgende grundlegende Beispiel `parallel_sort` zeigt, `vector` wie `int` Sie werte sortieren. Verwendet standardmäßig `parallel_sort` [std::less,](../../standard-library/less-struct.md) um Werte zu vergleichen.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

In diesem Beispiel wird gezeigt, wie Eine benutzerdefinierte Vergleichsfunktion zur Verfügung steht. Es verwendet die [std::complex::real-Methode,](../../standard-library/complex-class.md#real) um [std::complex\<double>](../../standard-library/complex-double.md) Werte in aufsteigender Reihenfolge zu sortieren.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

Dieses Beispiel zeigt, wie dem `parallel_radixsort` Algorithmus eine Hashfunktion zur Verfügung stellt. In diesem Beispiel werden 3D-Punkte sortiert. Die Punkte werden nach ihrem Abstand von einem Referenzpunkt sortiert.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

Zur Veranschaulichung wird in diesem Beispiel ein relativ kleiner Datensatz verwendet. Sie können die Anfangsgröße des Vektors erhöhen, um mit Leistungsverbesserungen gegenüber größeren Datensätzen zu experimentieren.

In diesem Beispiel wird ein Lambdaausdruck als Hashfunktion verwendet. Sie können auch eine der integrierten Implementierungen der[hash-Klasse](../../standard-library/hash-class.md) std:: verwenden oder Ihre eigene Spezialisierung definieren. Sie können auch ein benutzerdefiniertes Hashfunktionsobjekt verwenden, wie in diesem Beispiel gezeigt:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

Die Hashfunktion muss einen integralen Typ zurückgeben ([std::is_integral::value](../../standard-library/is-integral-class.md) muss **true**sein). Dieser integrale Typ muss `size_t`in typ umwandelbar sein.

### <a name="choosing-a-sorting-algorithm"></a><a name="choose_sort"></a>Auswählen eines Sortieralgorithmus

In vielen `parallel_sort` Fällen bietet die beste Balance von Geschwindigkeit und Speicherleistung. Wenn Sie jedoch die Größe des Datensatzes, die Anzahl der verfügbaren Prozessoren `parallel_buffered_sort` oder `parallel_radixsort` die Komplexität der Vergleichsfunktion erhöhen, oder sie können besser funktionieren. Der beste Weg, um zu bestimmen, welcher Sortieralgorithmus in einem bestimmten Szenario verwendet werden soll, besteht darin, zu experimentieren und zu messen, wie lange es dauert, typische Daten unter repräsentativen Computerkonfigurationen zu sortieren. Beachten Sie bei der Auswahl einer Sortierstrategie die folgenden Richtlinien.

- Die Größe des Datensatzes. In diesem Dokument enthält ein *kleines* Dataset weniger als 1.000 Elemente, ein *mittleres* Dataset zwischen 10.000 und 100.000 Elemente und ein *großes* Dataset mehr als 100.000 Elemente.

- Die Menge an Arbeit, die Ihre Vergleichsfunktion oder Hashfunktion ausführt.

- Die Menge der verfügbaren Rechenressourcen.

- Die Eigenschaften Ihres Datensatzes. Beispielsweise kann ein Algorithmus für Daten, die bereits fast sortiert sind, gut funktionieren, aber nicht so gut für Daten, die vollständig unsortiert sind.

- Die Chunk-Größe. Das `_Chunk_size` optionale Argument gibt an, wenn der Algorithmus von einer Parallele zu einer seriellen Sortierimplementierung wechselt, während er die gesamte Sortierung in kleinere Arbeitseinheiten unterteilt. Wenn Sie beispielsweise 512 bereitstellen, wechselt der Algorithmus zur seriellen Implementierung, wenn eine Arbeitseinheit 512 oder weniger Elemente enthält. Eine serielle Implementierung kann die Gesamtleistung verbessern, da sie den Aufwand eliminiert, der erforderlich ist, um Daten parallel zu verarbeiten.

Es lohnt sich möglicherweise nicht, ein kleines Dataset parallel zu sortieren, selbst wenn Sie über eine große Anzahl verfügbarer Rechenressourcen verfügen oder Ihre Vergleichsfunktion oder Hashfunktion relativ viel Arbeit ausführt. Sie können die [Funktion std::sort](../../standard-library/algorithm-functions.md#sort) verwenden, um kleine Datasets zu sortieren. (`parallel_sort` `parallel_buffered_sort` und `sort` rufen Sie auf, wenn Sie eine Chunk-Größe angeben, die größer als das Dataset ist; sie `parallel_buffered_sort` müsste jedoch O(N)-Speicherplatz zuweisen, was aufgrund von Sperrkonflikten oder Speicherzuweisung zusätzliche Zeit in Anspruch nehmen könnte.)

Wenn Sie Speicher sparen müssen oder Ihr Speicherzunokator Sperrkonflikten unterliegt, können Sie `parallel_sort` ein mittelgroßes Dataset sortieren. `parallel_sort`erfordert keinen zusätzlichen Platz; die anderen Algorithmen benötigen O(N)-Leerraum.

Verwenden `parallel_buffered_sort` Sie diese Möglichkeit, um mittelgroße Datasets zu sortieren und wenn Ihre Anwendung den zusätzlichen O(N)-Speicherplatzbedarf erfüllt. `parallel_buffered_sort`kann besonders nützlich sein, wenn Sie über eine große Anzahl von Rechenressourcen oder eine teure Vergleichsfunktion oder Hashfunktion verfügen.

Verwenden `parallel_radixsort` Sie diese Möglichkeit, um große Datasets zu sortieren und wenn Ihre Anwendung den zusätzlichen O(N)-Speicherplatzbedarf erfüllt. `parallel_radixsort`kann besonders nützlich sein, wenn der entsprechende Vergleichsvorgang teurer ist oder wenn beide Vorgänge teuer sind.

> [!CAUTION]
> Das Implementieren einer guten Hashfunktion erfordert, dass Sie den Datasetbereich kennen und wissen, wie jedes Element im Dataset in einen entsprechenden nicht signierten Wert transformiert wird. Da der Hashvorgang für nicht signierte Werte funktioniert, sollten Sie eine andere Sortierstrategie in Betracht ziehen, wenn nicht signierte Hashwerte nicht erstellt werden können.

Im folgenden Beispiel wird `sort`die `parallel_sort` `parallel_buffered_sort`Leistung `parallel_radixsort` von , , und mit demselben großen Satz zufälliger Daten verglichen.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

In diesem Beispiel, in dem davon ausgegangen wird, dass es `parallel_radixsort` akzeptabel ist, O(N)-Speicherplatz während der Sortierung zuzuweisen, wird das beste Für sein Dataset auf dieser Computerkonfiguration ausgeführt.

[[Oben](#top)]

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Gewusst wie: Schreiben einer parallel_for-Schleife](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Zeigt, wie `parallel_for` der Algorithmus zum Durchführen der Matrixmultiplikation verwendet wird.|
|[Gewusst wie: Schreiben einer parallel_for_each-Schleife](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Zeigt, wie `parallel_for_each` der Algorithmus verwendet wird, um die Anzahl der Primzahlen in einem [std::array-Objekt](../../standard-library/array-class-stl.md) parallel zu berechnen.|
|[Gewusst wie: Verwenden von parallel_invoke zum Schreiben einer Runtime für paralleles Sortieren](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Erläutert, wie die Leistung des bitonischen Sortieralgorithmus mit dem `parallel_invoke`-Algorithmus verbessert werden.|
|[Gewusst wie: Verwenden parallel_invoke zum Ausführen paralleler Vorgänge](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Erläutert, wie die Leistung eines Programms mit dem `parallel_invoke`-Algorithmus verbessert werden kann, das mehrere Vorgänge in einer freigegebenen Datenquelle ausführt.|
|[Gewusst wie: Paralleles Ausführen von Zuordnungs- und Reduzierungsoperationen](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Zeigt, wie `parallel_transform` die `parallel_reduce` und Algorithmen verwendet werden, um eine Zuordnung auszuführen und den Vorgang zu reduzieren, der die Vorkommen von Wörtern in Dateien zählt.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Beschreibt die PPL, die ein imperatives Programmiermodell bietet, das Skalierbarkeit und Benutzerfreundlichkeit für die Entwicklung gleichzeitiger Anwendungen fördert.|
|[Abbruch in der PPL](cancellation-in-the-ppl.md)|Erläutert die Rolle des Abbruchs in der PPL, wie parallele Arbeit abgebrochen wird und wie bestimmt wird, wann eine Aufgabengruppe abgebrochen wird.|
|[Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Erläutert die Rolle der Ausnahmebehandlung in der Concurrency Runtime.|

## <a name="reference"></a>Verweis

[parallel_for-Funktion](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each-Funktion](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke Funktion](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner-Klasse](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner-Klasse](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner-Klasse](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner-Klasse](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort-Funktion](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort Funktion](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort-Funktion](reference/concurrency-namespace-functions.md#parallel_radixsort)
