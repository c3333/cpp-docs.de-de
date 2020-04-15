---
title: Parallele Container und Objekte
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: f3fb2bb57c8bcf65de0a7f74f2992050d8257429
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363048"
---
# <a name="parallel-containers-and-objects"></a>Parallele Container und Objekte

Die Parallel Patterns Library (PPL) enthält mehrere Container und Objekte, die einen threadsicheren Zugriff auf ihre Elemente ermöglichen.

Ein *gleichzeitiger Container* bietet parallelitätssicheren Zugriff auf die wichtigsten Vorgänge. Hier sind parallelitätssichere Mittelzeiger oder Iteratoren immer gültig. Es ist keine Garantie für die Elementinitialisierung oder einer bestimmten Durchlaufreihenfolge. Die Funktionalität dieser Container ähnelt denen, die von der C++-Standardbibliothek bereitgestellt werden. Die [concurrency::concurrent_vector-Klasse](../../parallel/concrt/reference/concurrent-vector-class.md) ähnelt beispielsweise der [klasse std::vector,](../../standard-library/vector-class.md) mit der Ausnahme, dass Sie `concurrent_vector` Elemente parallel anfügen können. Verwenden Sie gleichzeitige Container, wenn Sie parallelen Code haben, der sowohl Lese- als auch Schreibzugriff auf denselben Container erfordert.

Ein *gleichzeitiges Objekt* wird gleichzeitig zwischen Komponenten freigegeben. Ein Prozess, der den Zustand eines parallelen Objekts parallel berechnet, erzeugt dasselbe Ergebnis wie ein anderer Prozess, der denselben Status seriell berechnet. Die [concurrency::combinable-Klasse](../../parallel/concrt/reference/combinable-class.md) ist ein Beispiel für einen gleichzeitigen Objekttyp. Mit `combinable` der Klasse können Sie Berechnungen parallel durchführen und diese Berechnungen dann zu einem Endergebnis kombinieren. Verwenden Sie gleichzeitige Objekte, wenn Sie andernfalls einen Synchronisierungsmechanismus, z. B. einen Mutex, verwenden würden, um den Zugriff auf eine freigegebene Variable oder Ressource zu synchronisieren.

## <a name="sections"></a><a name="top"></a>Bereichen

In diesem Thema werden die folgenden parallelen Container und Objekte ausführlich beschrieben.

Gleichzeitige Container:

- [concurrent_vector Klasse](#vector)

  - [Unterschiede zwischen concurrent_vector und Vektor](#vector-differences)

  - [Parallelitätssichere Vorgänge](#vector-safety)

  - [Ausnahmesicherheit](#vector-exceptions)

- [concurrent_queue-Klasse](#queue)

  - [Unterschiede zwischen concurrent_queue und Warteschlange](#queue-differences)

  - [Parallelitätssichere Vorgänge](#queue-safety)

  - [Iterator-Unterstützung](#queue-iterators)

- [concurrent_unordered_map Klasse](#unordered_map)

  - [Unterschiede zwischen concurrent_unordered_map und unordered_map](#map-differences)

  - [Parallelitätssichere Vorgänge](#map-safety)

- [concurrent_unordered_multimap-Klasse](#unordered_multimap)

- [concurrent_unordered_set-Klasse](#unordered_set)

- [concurrent_unordered_multiset-Klasse](#unordered_multiset)

Gleichzeitige Objekte:

- [kombinierbare Klasse](#combinable)

  - [Methoden und Funktionen](#combinable-features)

  - [Beispiele](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>concurrent_vector Klasse

Die [concurrency::concurrent_vector-Klasse](../../parallel/concrt/reference/concurrent-vector-class.md) ist eine Sequenzcontainerklasse, mit der Sie genau wie die [std::vector-Klasse](../../standard-library/vector-class.md) nach dem Zufallsprinzip auf ihre Elemente zugreifen können. Die `concurrent_vector` Klasse ermöglicht parallelitätssichere Anhänge- und Elementzugriffsvorgänge. Anfügenvorgänge machen vorhandene Zeiger oder Iteratoren nicht ungültig. Iterator-Zugriffs- und Durchlaufvorgänge sind ebenfalls parallelitätssicher. Hier sind parallelitätssichere Mittelzeiger oder Iteratoren immer gültig. Es ist keine Garantie für die Elementinitialisierung oder einer bestimmten Durchlaufreihenfolge.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>Unterschiede zwischen concurrent_vector und Vektor

Die `concurrent_vector` Klasse ähnelt `vector` der Klasse. Die Komplexität von Anhängen, Elementzugriffs- und Iteratorzugriffsvorgängen für ein `concurrent_vector` Objekt ist die gleiche wie bei einem `vector` Objekt. Die folgenden Punkte `concurrent_vector` veranschaulichen, wo unterscheidet sich von: `vector`

- Anfügen, Elementzugriff, Iteratorzugriff und Iterator-Traversalvorgänge für ein `concurrent_vector` Objekt sind parallelitätssicher.

- Sie können Elemente nur am `concurrent_vector` Ende eines Objekts hinzufügen. Die `concurrent_vector` Klasse stellt `insert` die Methode nicht bereit.

- Ein `concurrent_vector` Objekt verwendet keine [Verschiebungssemantik,](../../cpp/rvalue-reference-declarator-amp-amp.md) wenn Sie es anfügen.

- Die `concurrent_vector` Klasse stellt `erase` die `pop_back` oder Methoden nicht bereit. Verwenden `vector`Sie wie bei die [clear-Methode,](reference/concurrent-vector-class.md#clear) um alle Elemente aus einem `concurrent_vector` Objekt zu entfernen.

- Die `concurrent_vector` Klasse speichert ihre Elemente nicht zusammenhängend im Speicher. Daher können Sie `concurrent_vector` die Klasse nicht auf alle Arten verwenden, wie Sie ein Array verwenden können. Für eine Variable mit `v` dem `concurrent_vector`Namen `&v[0]+2` typ erzeugt der Ausdruck beispielsweise undefiniertes Verhalten.

- Die `concurrent_vector` Klasse definiert die [grow_by](reference/concurrent-vector-class.md#grow_by) und [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) Methoden. Diese Methoden ähneln der [Resize-Methode,](reference/concurrent-vector-class.md#resize) mit der Ausnahme, dass sie parallelitätssicher sind.

- Ein `concurrent_vector` Objekt verschiebt seine Elemente nicht, wenn Sie es anfügen oder seine Größe ändern. Dadurch können vorhandene Zeiger und Iteratoren bei gleichzeitigen Vorgängen gültig bleiben.

- Die Laufzeit definiert keine spezielle `concurrent_vector` Version `bool`von für typ .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>Parallelitätssichere Vorgänge

Alle Methoden, die an ein `concurrent_vector` Objekt anhängen oder diese `concurrent_vector` vergrößern oder auf ein Element in einem Objekt zugreifen, sind parallelitätssicher. Hier sind parallelitätssichere Mittelzeiger oder Iteratoren immer gültig. Es ist keine Garantie für die Elementinitialisierung oder einer bestimmten Durchlaufreihenfolge. Die Ausnahme von dieser `resize` Regel ist die Methode.

Die folgende Tabelle `concurrent_vector` zeigt die gängigen Methoden und Operatoren, die parallelitätssicher sind.

||||
|-|-|-|
|[Auf](reference/concurrent-vector-class.md#at)|[Ende](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[Beginnen](reference/concurrent-vector-class.md#begin)|[Vorder-](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[back (Zurück)](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[Kapazität](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[Max_size](reference/concurrent-vector-class.md#max_size)|[Größe](reference/concurrent-vector-class.md#size)|

Vorgänge, die die Laufzeit für die Kompatibilität mit der C++-Standardbibliothek bereitstellt, `reserve`z. B. , sind nicht parallelitätssicher. Die folgende Tabelle zeigt die gängigen Methoden und Operatoren, die nicht parallelitätssicher sind.

|||
|-|-|
|[Zuweisen](reference/concurrent-vector-class.md#assign)|[Reservieren](reference/concurrent-vector-class.md#reserve)|
|[Klar](reference/concurrent-vector-class.md#clear)|[Größe](reference/concurrent-vector-class.md#resize)|
|[Operator=](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Vorgänge, die den Wert vorhandener Elemente ändern, sind nicht parallelitätssicher. Verwenden Sie ein Synchronisierungsobjekt, z. B. ein [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) Objekt, um gleichzeitige Lese- und Schreibvorgänge mit demselben Datenelement zu synchronisieren. Weitere Informationen zu Synchronisierungsobjekten finden Sie unter [Synchronisierungsdatenstrukturen](../../parallel/concrt/synchronization-data-structures.md).

Wenn Sie vorhandenen Code `vector` konvertieren, der für die Verwendung `concurrent_vector`verwendet wird, können gleichzeitige Vorgänge dazu führen, dass sich das Verhalten Der Anwendung ändert. Betrachten Sie beispielsweise das folgende Programm, das `concurrent_vector` gleichzeitig zwei Aufgaben für ein Objekt ausführt. Die erste Aufgabe fügt zusätzliche `concurrent_vector` Elemente an ein Objekt an. Die zweite Aufgabe berechnet die Summe aller Elemente im selben Objekt.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Obwohl `end` die Methode parallelitätssicher ist, bewirkt ein gleichzeitiger Aufruf `end` der push_back-Methode, dass sich der von zurückgegebene Wert ändert. [push_back](reference/concurrent-vector-class.md#push_back) Die Anzahl der Elemente, die der Iterator durchläuft, ist unbestimmt. Daher kann dieses Programm jedes Mal, wenn Sie es ausführen, ein anderes Ergebnis erzeugen. Wenn der Elementtyp nicht trivial ist, ist es möglich, `push_back` `end` dass eine Racebedingung zwischen und Aufrufen vorhanden ist. Die `end` Methode gibt möglicherweise ein Element zurück, das zugewiesen, aber nicht vollständig initialisiert ist.

### <a name="exception-safety"></a><a name="vector-exceptions"></a>Ausnahmesicherheit

Wenn ein Wachstums- oder Zuweisungsvorgang eine `concurrent_vector` Ausnahme auslöst, wird der Status des Objekts ungültig. Das Verhalten `concurrent_vector` eines Objekts, das sich in einem ungültigen Zustand befindet, ist nicht definiert, sofern nicht anders angegeben. Der Destruktor gibt jedoch immer den Speicher frei, den das Objekt zuweist, auch wenn sich das Objekt in einem ungültigen Zustand befindet.

Der Datentyp der Vektorelemente muss `T`die folgenden Anforderungen erfüllen. Andernfalls ist das `concurrent_vector` Verhalten der Klasse nicht definiert.

- Der Zerstörer darf nicht werfen.

- Wenn der Standard- oder Kopierkonstruktor ausgelöst wird, darf `virtual` der Destruktor nicht mit dem Schlüsselwort deklariert werden, und er muss mit null initialisiertem Speicher ordnungsgemäß funktionieren.

[[Oben](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a>concurrent_queue-Klasse

Mit [der concurrency::concurrent_queue-Klasse](../../parallel/concrt/reference/concurrent-queue-class.md) können Sie genau wie die [std::queue-Klasse](../../standard-library/queue-class.md) auf ihre Vorder- und Rückseitenelemente zugreifen. Die `concurrent_queue` Klasse ermöglicht parallelitätssichere Enqueue- und Dequeue-Vorgänge. Hier sind parallelitätssichere Mittelzeiger oder Iteratoren immer gültig. Es ist keine Garantie für die Elementinitialisierung oder einer bestimmten Durchlaufreihenfolge. Die `concurrent_queue` Klasse bietet auch Iteratorunterstützung, die nicht parallelitätssicher ist.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>Unterschiede zwischen concurrent_queue und Warteschlange

Die `concurrent_queue` Klasse ähnelt `queue` der Klasse. Die folgenden Punkte `concurrent_queue` veranschaulichen, wo unterscheidet sich von: `queue`

- Ein- und Auswarteschlangenvorgänge für ein `concurrent_queue` Objekt sind parallelitätssicher.

- Die `concurrent_queue` Klasse bietet Iteratorunterstützung, die nicht parallelitätssicher ist.

- Die `concurrent_queue` Klasse stellt `front` die `pop` oder Methoden nicht bereit. Die `concurrent_queue` Klasse ersetzt diese Methoden, indem sie die [try_pop-Methode](reference/concurrent-queue-class.md#try_pop) definiert.

- Die `concurrent_queue` Klasse stellt `back` die Methode nicht bereit. Daher können Sie nicht auf das Ende der Warteschlange verweisen.

- Die `concurrent_queue` Klasse [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) stellt die unsafe_size `size` Methode anstelle der Methode bereit. Die `unsafe_size` Methode ist nicht parallelitätssicher.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>Parallelitätssichere Vorgänge

Alle Methoden, die in die `concurrent_queue` Warteschlange eines Objekts ein- oder aus der Warteschlange stehen, sind parallelitätssicher. Hier sind parallelitätssichere Mittelzeiger oder Iteratoren immer gültig. Es ist keine Garantie für die Elementinitialisierung oder einer bestimmten Durchlaufreihenfolge.

Die folgende Tabelle `concurrent_queue` zeigt die gängigen Methoden und Operatoren, die parallelitätssicher sind.

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Obwohl `empty` die Methode parallelitätssicher ist, kann ein gleichzeitiger Vorgang `empty` dazu führen, dass die Warteschlange vergrößert oder verkleinert wird, bevor die Methode zurückgegeben wird.

Die folgende Tabelle zeigt die gängigen Methoden und Operatoren, die nicht parallelitätssicher sind.

|||
|-|-|
|[Klar](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>Iterator-Unterstützung

Der `concurrent_queue` bietet Iteratoren, die nicht parallelitätssicher sind. Es wird empfohlen, diese Iteratoren nur zum Debuggen zu verwenden.

Ein `concurrent_queue` Iterator durchquert Elemente nur in Vorwärtsrichtung. Die folgende Tabelle zeigt die Operatoren, die jeder Iterator unterstützt.

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|`operator++`|Wechselt zum nächsten Element in der Warteschlange. Dieser Operator ist überlastet, um sowohl die Semantik vor- als auch nach dem Inkrementell bereitzustellen.|
|`operator*`|Ruft einen Verweis auf das aktuelle Element ab.|
|`operator->`|Ruft einen Zeiger auf das aktuelle Element ab.|

[[Oben](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>concurrent_unordered_map Klasse

Die [concurrency::concurrent_unordered_map-Klasse](../../parallel/concrt/reference/concurrent-unordered-map-class.md) ist eine assoziative Containerklasse, die genau wie die [std::unordered_map-Klasse](../../standard-library/unordered-map-class.md) eine unterschiedliche Länge von Elementen des Typs [std::pair\<const Key, Ty>](../../standard-library/pair-structure.md)steuert. Stellen Sie sich eine ungeordnete Karte als Wörterbuch vor, dem Sie ein Schlüssel- und Wertpaar hinzufügen oder einen Wert nach Schlüssel suchen können. Diese Klasse ist nützlich, wenn Sie über mehrere Threads oder Aufgaben verfügen, die gleichzeitig auf einen freigegebenen Container zugreifen, ihn einfügen oder aktualisieren müssen.

Das folgende Beispiel zeigt die `concurrent_unordered_map`grundlegende Struktur für die Verwendung von . In diesem Beispiel werden Zeichentasten in den Bereich ['a', 'i'] eingefügt. Da die Reihenfolge der Vorgänge nicht festgelegt ist, ist auch der endgültige Wert für jeden Schlüssel unbestimmt. Es ist jedoch sicher, die Einfügungen parallel durchzuführen.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Ein Beispiel, `concurrent_unordered_map` das zum Parallelen Ausführen einer Zuordnung und zum Reduzieren des Vorgangs verwendet wird, finden Sie unter [Gewusst wie: Ausführen von Zuordnungs- und Reduzieren von Vorgängen in Parallel](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>Unterschiede zwischen concurrent_unordered_map und unordered_map

Die `concurrent_unordered_map` Klasse ähnelt `unordered_map` der Klasse. Die folgenden Punkte `concurrent_unordered_map` veranschaulichen, wo unterscheidet sich von: `unordered_map`

- Die `erase` `bucket`, `bucket_count`, `bucket_size` und `unsafe_erase`Die `unsafe_bucket` `unsafe_bucket_count`Methoden `unsafe_bucket_size`heißen , , und , bzw. . Die `unsafe_` Namenskonvention gibt an, dass diese Methoden nicht parallelitätssicher sind. Weitere Informationen zur Parallelitätssicherheit finden Sie unter [Concurrency-Safe Operations](#map-safety).

- Einfügevorgänge machen keine vorhandenen Zeiger oder Iteratoren ungültig, noch ändern sie die Reihenfolge der Elemente, die bereits in der Karte vorhanden sind. Einfüge- und Durchlaufvorgänge können gleichzeitig ausgeführt werden.

- `concurrent_unordered_map`unterstützt nur Vorwärtsiteration.

- Durch das Einfügen werden die Iteratoren, `equal_range`die von zurückgegeben werden, nicht ungültig oder aktualisiert. Die Einfügung kann ungleiche Elemente am Ende des Bereichs anhängen. Der Start-Iterator zeigt auf ein gleiches Element.

Um Deadlocks zu vermeiden, gibt es keine Methode, eine Sperre zu `concurrent_unordered_map` sperren, wenn der Speicherzuweisungs-, Hashfunktionen oder anderer benutzerdefinierter Code aufruft. Außerdem müssen Sie sicherstellen, dass die Hashfunktion immer gleiche Schlüssel auf denselben Wert auswertet. Die besten Hashfunktionen verteilen Schlüssel gleichmäßig über den Hashcodebereich.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>Parallelitätssichere Vorgänge

Die `concurrent_unordered_map` Klasse ermöglicht parallelitätssichere Insert- und Elementzugriffsvorgänge. Insert-Vorgänge machen vorhandene Zeiger oder Iteratoren nicht ungültig. Iterator-Zugriffs- und Durchlaufvorgänge sind ebenfalls parallelitätssicher. Hier sind parallelitätssichere Mittelzeiger oder Iteratoren immer gültig. Es ist keine Garantie für die Elementinitialisierung oder einer bestimmten Durchlaufreihenfolge. Die folgende Tabelle zeigt `concurrent_unordered_map` die häufig verwendeten Methoden und Operatoren, die parallelitätssicher sind.

|||||
|-|-|-|-|
|[Auf](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[Einfügen](reference/concurrent-unordered-map-class.md#insert)|`size`|

Obwohl `count` die Methode sicher von gleichzeitig ausgeführten Threads aufgerufen werden kann, können verschiedene Threads unterschiedliche Ergebnisse erhalten, wenn gleichzeitig ein neuer Wert in den Container eingefügt wird.

Die folgende Tabelle zeigt die häufig verwendeten Methoden und Operatoren, die nicht parallelitätssicher sind.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[Operator=](reference/concurrent-unordered-map-class.md#operator_eq)

Zusätzlich zu diesen Methoden ist jede `unsafe_` Methode, die mit beginnt, auch nicht parallelitätssicher.

[[Oben](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>concurrent_unordered_multimap-Klasse

Die [parallelität::concurrent_unordered_multimap-Klasse](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) ähnelt `concurrent_unordered_map` der Klasse, mit der Ausnahme, dass mehrere Werte demselben Schlüssel zugeordnet werden können. Es unterscheidet sich `concurrent_unordered_map` auch in den folgenden Weisen:

- Die [concurrent_unordered_multimap::insert-Methode](reference/concurrent-unordered-multimap-class.md#insert) gibt einen Iterator anstelle von `std::pair<iterator, bool>`zurück.

- Die `concurrent_unordered_multimap` Klasse stellt `operator[]` weder die `at` Methode bereit noch die Methode bereit.

Das folgende Beispiel zeigt die `concurrent_unordered_multimap`grundlegende Struktur für die Verwendung von . In diesem Beispiel werden Zeichentasten in den Bereich ['a', 'i'] eingefügt. `concurrent_unordered_multimap`ermöglicht es einem Schlüssel, mehrere Werte zu haben.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Oben](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>concurrent_unordered_set-Klasse

Die [parallelität::concurrent_unordered_set-Klasse](../../parallel/concrt/reference/concurrent-unordered-set-class.md) ähnelt `concurrent_unordered_map` der Klasse, außer dass sie Werte anstelle von Schlüssel- und Wertpaaren verwaltet. Die `concurrent_unordered_set` Klasse stellt `operator[]` weder die `at` Methode bereit noch die Methode bereit.

Das folgende Beispiel zeigt die `concurrent_unordered_set`grundlegende Struktur für die Verwendung von . In diesem Beispiel werden Zeichenwerte in den Bereich ['a', 'i'] eingefügt. Es ist sicher, die Einfügungen parallel durchzuführen.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Oben](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>concurrent_unordered_multiset Klasse

Die [parallelität::concurrent_unordered_multiset-Klasse](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) ähnelt `concurrent_unordered_set` der Klasse, außer dass sie doppelte Werte zulässt. Es unterscheidet sich `concurrent_unordered_set` auch in den folgenden Weisen:

- Die [concurrent_unordered_multiset::insert-Methode](reference/concurrent-unordered-multiset-class.md#insert) gibt einen Iterator anstelle von `std::pair<iterator, bool>`zurück.

- Die `concurrent_unordered_multiset` Klasse stellt `operator[]` weder die `at` Methode bereit noch die Methode bereit.

Das folgende Beispiel zeigt die `concurrent_unordered_multiset`grundlegende Struktur für die Verwendung von . In diesem Beispiel werden Zeichenwerte in den Bereich ['a', 'i'] eingefügt. `concurrent_unordered_multiset`ermöglicht, dass ein Wert mehrmals auftritt.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Oben](#top)]

## <a name="combinable-class"></a><a name="combinable"></a>kombinierbare Klasse

Die [concurrency::combinable-Klasse](../../parallel/concrt/reference/combinable-class.md) bietet wiederverwendbaren, threadlokalen Speicher, mit dem Sie detaillierte Berechnungen durchführen und diese Berechnungen dann zu einem Endergebnis zusammenführen können. Stellen Sie sich ein `combinable`-Objekt wie eine Reduktionsvariable vor.

Die `combinable` Klasse ist nützlich, wenn Sie über eine Ressource verfügen, die von mehreren Threads oder Aufgaben gemeinsam genutzt wird. Die `combinable` Klasse hilft Ihnen, den freigegebenen Status zu eliminieren, indem sie den Zugriff auf freigegebene Ressourcen auf eine sperrfreie Weise bereitstellt. Daher bietet diese Klasse eine Alternative zur Verwendung eines Synchronisierungsmechanismus, z. B. eines Mutex, um den Zugriff auf freigegebene Daten aus mehreren Threads zu synchronisieren.

### <a name="methods-and-features"></a><a name="combinable-features"></a>Methoden und Funktionen

Die folgende Tabelle zeigt einige der `combinable` wichtigen Methoden der Klasse. Weitere Informationen zu `combinable` allen Klassenmethoden finden Sie unter [combinable Class](../../parallel/concrt/reference/combinable-class.md).

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Ruft einen Verweis auf die lokale Variable ab, die dem aktuellen Threadkontext zugeordnet ist.|
|[Klar](reference/combinable-class.md#clear)|Entfernt alle threadlokalen Variablen `combinable` aus dem Objekt.|
|[Kombinieren](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Verwendet die bereitgestellte Kombinationsfunktion, um einen endgültigen Wert aus dem Satz aller threadlokalen Berechnungen zu generieren.|

Die `combinable` Klasse ist eine Vorlagenklasse, die für das endgültige zusammengeführte Ergebnis parametrisiert wird. Wenn Sie den Standardkonstruktor `T` aufrufen, muss der Vorlagenparametertyp über einen Standardkonstruktor und einen Kopierkonstruktor verfügen. Wenn `T` der Vorlagenparametertyp nicht über einen Standardkonstruktor verfügt, rufen Sie die überladene Version des Konstruktors auf, die eine Initialisierungsfunktion als Parameter verwendet.

Sie können zusätzliche Daten `combinable` in einem Objekt speichern, nachdem Sie die [Combine-](reference/combinable-class.md#combine) oder [combine_each-Methoden](reference/combinable-class.md#combine_each) aufrufen. Sie können die `combine` `combine_each` und Methoden auch mehrmals aufrufen. Wenn sich kein `combinable` lokaler Wert `combine` in `combine_each` einem Objekt ändert, erzeugen die und Methoden bei jedem Aufruf dasselbe Ergebnis.

### <a name="examples"></a><a name="combinable-examples"></a>Beispiele

Beispiele für die Verwendung `combinable` der Klasse finden Sie in den folgenden Themen:

- [Gewusst wie: Verbessern der Leistung mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Gewusst wie: Kombinieren von Gruppen mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Oben](#top)]

## <a name="related-topics"></a>Verwandte Themen

[Gewusst wie: Erhöhen der Effizienz mithilfe von parallelen Containern](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Zeigt, wie parallele Container verwendet werden, um Daten effizient zu speichern und gleichzeitig darauf zuzugreifen.

[Gewusst wie: Verbessern der Leistung mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Zeigt, wie `combinable` die Klasse verwendet wird, um den freigegebenen Status zu eliminieren und dadurch die Leistung zu verbessern.

[Gewusst wie: Kombinieren von Gruppen mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Zeigt, wie `combine` eine Funktion zum Zusammenführen von threadlokalen Datensätzen verwendet wird.

[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Beschreibt die PPL, die ein imperatives Programmiermodell bietet, das Skalierbarkeit und Benutzerfreundlichkeit für die Entwicklung gleichzeitiger Anwendungen fördert.

## <a name="reference"></a>Verweis

[concurrent_vector Klasse](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue-Klasse](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map Klasse](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap-Klasse](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set-Klasse](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset-Klasse](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[kombinierbare Klasse](../../parallel/concrt/reference/combinable-class.md)
