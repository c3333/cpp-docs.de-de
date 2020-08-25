---
title: Parallele Container und Objekte
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 7387173378e79a4707008a11846eab19d7ae4341
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831787"
---
# <a name="parallel-containers-and-objects"></a>Parallele Container und Objekte

Die Parallel Patterns Library (PPL) umfasst mehrere Container und Objekte, die Thread sicheren Zugriff auf ihre Elemente bereitstellen.

Ein *gleichzeitiger Container* bietet neben läufigkeits sicheren Zugriff auf die wichtigsten Vorgänge. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge. Die Funktionen dieser Container ähneln denen, die von der C++-Standard Bibliothek bereitgestellt werden. Die Klasse " [parallelcurrency:: Concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) " ähnelt z. b. der [Std:: Vector](../../standard-library/vector-class.md) -Klasse, mit der Ausnahme, dass die- `concurrent_vector` Klasse es Ihnen ermöglicht, Elemente parallel anzufügen. Verwenden Sie gleichzeitige Container, wenn Sie über parallelen Code verfügen, der sowohl Lese-als auch Schreibzugriff auf denselben Container erfordert.

Ein *gleichzeitiges-Objekt* wird gleichzeitig zwischen-Komponenten freigegeben Ein Prozess, der den Status eines gleichzeitigen-Objekts parallel berechnet, erzeugt dasselbe Ergebnis wie ein anderer Prozess, der den gleichen Zustand serialisiert berechnet. Die [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) -Klasse ist ein Beispiel für einen gleichzeitigen Objekttyp. `combinable`Mit der-Klasse können Sie Berechnungen parallel ausführen und diese Berechnungen dann zu einem endgültigen Ergebnis kombinieren. Verwenden Sie gleichzeitige Objekte, wenn Sie andernfalls einen Synchronisierungs Mechanismus verwenden möchten, z. b. einen Mutex, um den Zugriff auf eine freigegebene Variable oder Ressource zu synchronisieren.

## <a name="sections"></a><a name="top"></a> Strecken

In diesem Thema werden die folgenden parallelen Container und Objekte ausführlich beschrieben.

Gleichzeitige Container:

- [concurrent_vector-Klasse](#vector)

  - [Unterschiede zwischen Concurrent_vector und Vektor](#vector-differences)

  - [Parallelitäts sichere Vorgänge](#vector-safety)

  - [Ausnahme Sicherheit](#vector-exceptions)

- [Concurrent_queue-Klasse](#queue)

  - [Unterschiede zwischen Concurrent_queue und Warteschlange](#queue-differences)

  - [Parallelitäts sichere Vorgänge](#queue-safety)

  - [Iteratorunterstützung](#queue-iterators)

- [concurrent_unordered_map-Klasse](#unordered_map)

  - [Unterschiede zwischen concurrent_unordered_map und unordered_map](#map-differences)

  - [Parallelitäts sichere Vorgänge](#map-safety)

- [concurrent_unordered_multimap-Klasse](#unordered_multimap)

- [concurrent_unordered_set-Klasse](#unordered_set)

- [concurrent_unordered_multiset-Klasse](#unordered_multiset)

Gleichzeitige Objekte:

- [combinable-Klasse](#combinable)

  - [Methoden und Features](#combinable-features)

  - [Beispiele](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a> concurrent_vector-Klasse

Die " [parallelcurrency:: Concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) "-Klasse ist eine Sequenz Container Klasse, die Sie genau wie die [Std:: Vector](../../standard-library/vector-class.md) -Klasse nach dem Zufallsprinzip auf die Elemente zugreifen können. Die `concurrent_vector` -Klasse ermöglicht Parallelitäts sichere Anfüge-und Element Zugriffs Vorgänge. Durch Anfüge Vorgänge werden vorhandene Zeiger oder Iteratoren nicht für ungültig erklärt. Iteratorzugriffe und Durchlauf Vorgänge sind ebenfalls Parallelitäts sicher. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a> Unterschiede zwischen Concurrent_vector und Vektor

Die- `concurrent_vector` Klasse ähnelt der- `vector` Klasse. Die Komplexität von Append-, Element-und iteratorzugriffsvorgängen für ein- `concurrent_vector` Objekt entspricht dem für ein- `vector` Objekt. Die folgenden Punkte veranschaulichen, wo `concurrent_vector` von abweicht `vector` :

- Anfügen, Element Zugriff, iteratorzugriff und iteratortraversal-Vorgänge auf einem- `concurrent_vector` Objekt sind Parallelitäts sicher.

- Sie können Elemente nur am Ende eines-Objekts hinzufügen `concurrent_vector` . Die- `concurrent_vector` Klasse stellt die- `insert` Methode nicht bereit.

- Ein- `concurrent_vector` Objekt verwendet keine Verschiebungs [Semantik](../../cpp/rvalue-reference-declarator-amp-amp.md) , wenn Sie es anfügen.

- Die- `concurrent_vector` Klasse stellt die- `erase` Methode oder die-Methode nicht bereit `pop_back` . `vector`Verwenden Sie wie bei die [Clear](reference/concurrent-vector-class.md#clear) -Methode, um alle Elemente aus einem-Objekt zu entfernen `concurrent_vector` .

- Die- `concurrent_vector` Klasse speichert ihre Elemente nicht im Arbeitsspeicher zusammenhängend. Daher können Sie die- `concurrent_vector` Klasse nicht in allen Möglichkeiten verwenden, wie Sie ein Array verwenden können. Beispielsweise `v` erzeugt der Ausdruck für eine Variable mit dem Namen des Typs ein nicht `concurrent_vector` `&v[0]+2` definiertes Verhalten.

- Die `concurrent_vector` -Klasse definiert die Methoden [grow_by](reference/concurrent-vector-class.md#grow_by) und [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) . Diese Methoden ähneln der [Größe](reference/concurrent-vector-class.md#resize) -Methode, mit dem Unterschied, dass Sie Parallelitäts sicher sind.

- Ein- `concurrent_vector` Objekt verlagert seine Elemente nicht, wenn Sie es anfügen oder die Größe ändern. Dadurch können vorhandene Zeiger und Iteratoren während gleichzeitiger Vorgänge gültig bleiben.

- Die Laufzeit definiert keine spezialisierte Version von für den `concurrent_vector` Typ **`bool`** .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a> Parallelitäts sichere Vorgänge

Alle Methoden, die an die Größe eines-Objekts anfügen oder vergrößern oder auf `concurrent_vector` ein-Element in einem- `concurrent_vector` Objekt zugreifen, sind Parallelitäts sicher. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge. Die Ausnahme von dieser Regel ist die- `resize` Methode.

In der folgenden Tabelle sind die allgemeinen `concurrent_vector` Methoden und Operatoren aufgeführt, die Parallelitäts sicher sind.

:::row:::
   :::column span="":::
      [`at`](reference/concurrent-vector-class.md#at)\
      [`back`](reference/concurrent-vector-class.md#back)\
      [`begin`](reference/concurrent-vector-class.md#begin)\
      [`capacity`](reference/concurrent-vector-class.md#capacity)
   :::column-end:::
   :::column span="":::
      [`empty`](reference/concurrent-vector-class.md#empty)\
      [`end`](reference/concurrent-vector-class.md#end)\
      [`front`](reference/concurrent-vector-class.md#front)\
      [`grow_by`](reference/concurrent-vector-class.md#grow_by)
   :::column-end:::
   :::column span="":::
      [`grow_to_at_least`](reference/concurrent-vector-class.md#grow_to_at_least)\
      [`max_size`](reference/concurrent-vector-class.md#max_size)\
      [`operator[]`](reference/concurrent-vector-class.md#operator_at)\
      [`push_back`](reference/concurrent-vector-class.md#push_back)
   :::column-end:::
   :::column span="":::
      [`rbegin`](reference/concurrent-vector-class.md#rbegin)\
      [`rend`](reference/concurrent-vector-class.md#rend)\
      [`size`](reference/concurrent-vector-class.md#size)
   :::column-end:::
:::row-end:::

Vorgänge, die die Common Language Runtime für die Kompatibilität mit der C++-Standard Bibliothek bereitstellt, z `reserve` . b., sind nicht Parallelitäts sicher. In der folgenden Tabelle sind die allgemeinen Methoden und Operatoren aufgeführt, die nicht Parallelitäts sicher sind.

:::row:::
   :::column span="":::
      [`assign`](reference/concurrent-vector-class.md#assign)\
      [`clear`](reference/concurrent-vector-class.md#clear)
   :::column-end:::
   :::column span="":::
      [`operator=`](reference/concurrent-vector-class.md#operator_eq)\
      [`reserve`](reference/concurrent-vector-class.md#reserve)
   :::column-end:::
   :::column span="":::
      [`resize`](reference/concurrent-vector-class.md#resize)
   :::column-end:::
   :::column span="":::
      [`shrink_to_fit`](reference/concurrent-vector-class.md#shrink_to_fit)
   :::column-end:::
:::row-end:::

Vorgänge, bei denen der Wert vorhandener Elemente geändert wird, sind nicht Parallelitäts sicher. Verwenden Sie ein Synchronisierungs Objekt, z. b. ein [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) Objekt, um gleichzeitige Lese-und Schreibvorgänge mit demselben Datenelement zu synchronisieren. Weitere Informationen zu Synchronisierungs Objekten finden Sie unter [Synchronisierungs Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md).

Wenn Sie vorhandenen Code konvertieren, der `vector` von verwendet `concurrent_vector` wird, können gleichzeitige Vorgänge bewirken, dass sich das Verhalten der Anwendung ändert. Stellen Sie sich z. b. das folgende Programm vor, das gleichzeitig zwei Aufgaben für ein- `concurrent_vector` Objekt ausführt. Die erste Aufgabe fügt zusätzliche Elemente an ein- `concurrent_vector` Objekt an. Der zweite Task berechnet die Summe aller Elemente im selben-Objekt.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Obwohl die `end` -Methode Parallelitäts sicher ist, bewirkt ein gleichzeitiger Aufrufe der [push_back](reference/concurrent-vector-class.md#push_back) -Methode, dass der von zurückgegebene Wert `end` geändert wird. Die Anzahl der Elemente, die der Iterator durchläuft, ist unbestimmt. Daher kann dieses Programm jedes Mal, wenn Sie es ausführen, ein anderes Ergebnis liefern. Wenn der Elementtyp nicht trivial ist, ist es möglich, dass eine Racebedingung zwischen `push_back` -und- `end` aufrufen vorhanden ist. Die `end` -Methode gibt möglicherweise ein Element zurück, das zugeordnet, aber nicht vollständig initialisiert wurde.

### <a name="exception-safety"></a><a name="vector-exceptions"></a> Ausnahme Sicherheit

Wenn eine Vergrößerung oder ein Zuweisungs Vorgang eine Ausnahme auslöst, wird der Status des `concurrent_vector` Objekts ungültig. Das Verhalten eines- `concurrent_vector` Objekts, das sich in einem ungültigen Zustand befindet, ist nicht definiert, sofern nicht anders angegeben. Der Dekonstruktor gibt jedoch immer den Speicher frei, den das Objekt zuordnet, auch wenn sich das Objekt in einem ungültigen Zustand befindet.

Der Datentyp der Vektor Elemente, `T` , muss die folgenden Anforderungen erfüllen. Andernfalls ist das Verhalten der- `concurrent_vector` Klasse nicht definiert.

- Der Dekonstruktor darf nicht auslösen.

- Wenn der Standard-oder Kopierkonstruktor auslöst, darf der Dekonstruktor nicht mit dem **`virtual`** -Schlüsselwort deklariert werden, und er muss ordnungsgemäß mit NULL initialisiertem Arbeitsspeicher funktionieren.

[Nach[oben](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a> Concurrent_queue-Klasse

Die Klasse " [parallelcurrency:: Concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) " ermöglicht Ihnen genau wie die [Std:: Queue](../../standard-library/queue-class.md) -Klasse den Zugriff auf Ihre Front-und Back-Elemente. Die `concurrent_queue` -Klasse ermöglicht Parallelitäts sichere Einreihen in Warteschlangen-und Dequeue-Vorgänge. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge. Die- `concurrent_queue` Klasse stellt auch iteratorunterstützung bereit, die nicht Parallelitäts sicher ist.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a> Unterschiede zwischen Concurrent_queue und Warteschlange

Die- `concurrent_queue` Klasse ähnelt der- `queue` Klasse. Die folgenden Punkte veranschaulichen, wo `concurrent_queue` von abweicht `queue` :

- Enqueue-und Dequeue-Vorgänge für ein- `concurrent_queue` Objekt sind Parallelitäts sicher.

- Die- `concurrent_queue` Klasse stellt iteratorunterstützung bereit, die nicht Parallelitäts sicher ist.

- Die- `concurrent_queue` Klasse stellt die- `front` Methode oder die-Methode nicht bereit `pop` . Die- `concurrent_queue` Klasse ersetzt diese Methoden durch Definieren der [try_pop](reference/concurrent-queue-class.md#try_pop) -Methode.

- Die- `concurrent_queue` Klasse stellt die- `back` Methode nicht bereit. Daher können Sie nicht auf das Ende der Warteschlange verweisen.

- Die- `concurrent_queue` Klasse stellt die [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) -Methode anstelle der- `size` Methode bereit. Die `unsafe_size` Methode ist nicht Parallelitäts sicher.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a> Parallelitäts sichere Vorgänge

Alle Methoden, die aus einem-Objekt in die Warteschlange eingereiht bzw. aus dieser entfernt werden, sind Parallelitäts `concurrent_queue` sicher Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge.

In der folgenden Tabelle sind die allgemeinen `concurrent_queue` Methoden und Operatoren aufgeführt, die Parallelitäts sicher sind.

:::row:::
   :::column span="":::
      [`empty`](reference/concurrent-queue-class.md#empty)
   :::column-end:::
   :::column span="":::
      [`get_allocator`](reference/concurrent-queue-class.md#get_allocator)
   :::column-end:::
   :::column span="":::
      [`push`](reference/concurrent-queue-class.md#push)
   :::column-end:::
   :::column span="":::
      [`try_pop`](reference/concurrent-queue-class.md#try_pop)
   :::column-end:::
:::row-end:::

Obwohl die `empty` -Methode Parallelitäts sicher ist, kann ein paralleler Vorgang dazu führen, dass die Warteschlange vergrößert oder verkleinert wird, bevor die `empty` Methode zurückgegeben wird.

In der folgenden Tabelle sind die allgemeinen Methoden und Operatoren aufgeführt, die nicht Parallelitäts sicher sind.

:::row:::
   :::column span="":::
      [`clear`](reference/concurrent-queue-class.md#clear)
   :::column-end:::
   :::column span="":::
      [`unsafe_begin`](reference/concurrent-queue-class.md#unsafe_begin)
   :::column-end:::
   :::column span="":::
      [`unsafe_end`](reference/concurrent-queue-class.md#unsafe_end)
   :::column-end:::
   :::column span="":::
      [`unsafe_size`](reference/concurrent-queue-class.md#unsafe_size)
   :::column-end:::
:::row-end:::

### <a name="iterator-support"></a><a name="queue-iterators"></a> Iteratorunterstützung

`concurrent_queue`Stellt Iteratoren bereit, die nicht Parallelitäts sicher sind. Es wird empfohlen, diese Iteratoren nur zum Debuggen zu verwenden.

Ein `concurrent_queue` Iterator durchläuft nur Elemente in Vorwärtsrichtung. In der folgenden Tabelle sind die Operatoren aufgeführt, die jeder Iterator unterstützt.

|Operator|Beschreibung|
|--------------|-----------------|
|`operator++`|Wechselt zum nächsten Element in der Warteschlange. Dieser Operator ist überladen, um die Semantik für die präinkrement-und Postinkrement bereitzustellen.|
|`operator*`|Ruft einen Verweis auf das aktuelle Element ab.|
|`operator->`|Ruft einen Zeiger auf das aktuelle Element ab.|

\[[Oben](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a> concurrent_unordered_map-Klasse

Die Klasse " [parallelcurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) " ist eine assoziative Container Klasse, die genau wie die [Std:: unordered_map](../../standard-library/unordered-map-class.md) -Klasse eine Sequenz von Elementen variabler Länge vom Typ [Std::p Air \<const Key, Ty> ](../../standard-library/pair-structure.md)steuert. Stellen Sie sich eine ungeordnete Zuordnung als Wörterbuch vor, dem Sie ein Schlüssel-Wert-Paar hinzufügen können, oder suchen Sie nach einem Wert nach Schlüssel. Diese Klasse ist hilfreich, wenn Sie über mehrere Threads oder Tasks verfügen, die gleichzeitig auf einen freigegebenen Container zugreifen, ihn einfügen oder aktualisieren müssen.

Das folgende Beispiel zeigt die grundlegende Struktur für die Verwendung von `concurrent_unordered_map` . In diesem Beispiel werden Zeichen Schlüssel im Bereich [' a ', ' i '] eingefügt. Da die Reihenfolge der Vorgänge nicht bestimmt ist, wird der endgültige Wert für jeden Schlüssel ebenfalls nicht bestimmt. Es ist jedoch sicher, dass die Einfügungen parallel durchgeführt werden.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Ein Beispiel für die Verwendung `concurrent_unordered_map` von zum Ausführen einer Zuordnung und reduzieren des Vorgangs parallel finden Sie unter Vorgehens [Weise: Paralleles Ausführen von Map-und Reduzierungs Vorgängen](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a> Unterschiede zwischen concurrent_unordered_map und unordered_map

Die- `concurrent_unordered_map` Klasse ähnelt der- `unordered_map` Klasse. Die folgenden Punkte veranschaulichen, wo `concurrent_unordered_map` von abweicht `unordered_map` :

- Die `erase` `bucket` Methoden,, und `bucket_count` `bucket_size` heißen,, `unsafe_erase` `unsafe_bucket` `unsafe_bucket_count` `unsafe_bucket_size` bzw.. Die `unsafe_` Benennungs Konvention gibt an, dass diese Methoden nicht Parallelitäts sicher sind. Weitere Informationen zur Parallelitäts Sicherheit finden Sie unter Parallelitäts [sichere Vorgänge](#map-safety).

- Einfügevorgänge machen vorhandene Zeiger oder Iteratoren nicht ungültig und ändern nicht die Reihenfolge der Elemente, die bereits in der Zuordnung vorhanden sind. INSERT-und traversiingvorgänge können gleichzeitig erfolgen.

- `concurrent_unordered_map` unterstützt nur Forward-Iterationen.

- Durch Einfügen werden die Iteratoren, die von zurückgegeben werden, nicht ungültig oder aktualisiert `equal_range` . Beim Einfügen können am Ende des Bereichs ungleiche Elemente angefügt werden. Der BEGIN-Iterator zeigt auf ein Gleichheits Element.

Um Deadlocks zu vermeiden, hält keine Methode von `concurrent_unordered_map` eine Sperre, wenn Sie die Speicherzuweisung, Hash Funktionen oder anderen benutzerdefinierten Code aufruft. Außerdem müssen Sie sicherstellen, dass die Hash Funktion immer gleichwertige Schlüssel mit demselben Wert auswertet. Die besten Hash Funktionen verteilen Schlüssel gleichmäßig über den Hash Code Bereich.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a> Parallelitäts sichere Vorgänge

Die `concurrent_unordered_map` -Klasse ermöglicht Parallelitäts sichere Einfüge-und Element Zugriffs Vorgänge. Einfügevorgänge machen vorhandene Zeiger oder Iteratoren ungültig. Iteratorzugriffe und Durchlauf Vorgänge sind ebenfalls Parallelitäts sicher. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge. In der folgenden Tabelle werden die häufig verwendeten `concurrent_unordered_map` Methoden und Operatoren aufgeführt, die Parallelitäts sicher sind.

:::row:::
   :::column span="":::
      [`at`](reference/concurrent-unordered-map-class.md#at)\
      [`begin`](reference/concurrent-unordered-map-class.md#begin)\
      [`cbegin`](reference/concurrent-unordered-map-class.md#cbegin)\
      [`cend`](reference/concurrent-unordered-map-class.md#cend)
   :::column-end:::
   :::column span="":::
      [`count`](reference/concurrent-unordered-map-class.md#count)\
      [`empty`](reference/concurrent-unordered-map-class.md#empty)\
      [`end`](reference/concurrent-unordered-map-class.md#cend)\
      [`equal_range`](reference/concurrent-unordered-map-class.md#equal_range)
   :::column-end:::
   :::column span="":::
      [`find`](reference/concurrent-unordered-map-class.md#find)\
      [`get_allocator`](reference/concurrent-unordered-map-class.md#get_allocator)\
      [`hash_function`](reference/concurrent-unordered-map-class.md#hash_function)\
      [`insert`](reference/concurrent-unordered-map-class.md#insert)
   :::column-end:::
   :::column span="":::
      [`key_eq`](reference/concurrent-unordered-map-class.md#key_eq)\
      [`max_size`](reference/concurrent-unordered-map-class.md#max_size)\
      [`operator[]`](./reference/concurrent-unordered-map-class.md#operator_at)\
      [`size`](reference/concurrent-unordered-map-class.md#size)
   :::column-end:::
:::row-end:::

Obwohl die- `count` Methode sicher von gleichzeitig ausgeführten Threads aufgerufen werden kann, können unterschiedliche Threads andere Ergebnisse empfangen, wenn ein neuer Wert gleichzeitig in den Container eingefügt wird.

Die folgende Tabelle zeigt die häufig verwendeten Methoden und Operatoren, die nicht Parallelitäts sicher sind.

:::row:::
   :::column span="":::
      [`clear`](reference/concurrent-unordered-map-class.md#clear)\
      [`load_factor`](reference/concurrent-unordered-map-class.md#load_factor)
   :::column-end:::
   :::column span="":::
      [`max_load_factor`](reference/concurrent-unordered-map-class.md#max_load_factor)
   :::column-end:::
   :::column span="":::
      [`operator=`](reference/concurrent-unordered-map-class.md#operator_eq)
   :::column-end:::
   :::column span="":::
      [`rehash`](reference/concurrent-unordered-map-class.md#rehash)
   :::column-end:::
:::row-end:::

Zusätzlich zu diesen Methoden ist jede Methode, die mit beginnt, `unsafe_` auch nicht Parallelitäts sicher.

[Nach[oben](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a> concurrent_unordered_multimap-Klasse

Die [parallelcurrency:: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) -Klasse ähnelt der- `concurrent_unordered_map` Klasse, mit der Ausnahme, dass mehrere Werte dem gleichen Schlüssel zugeordnet werden können. Dies unterscheidet sich auch von `concurrent_unordered_map` der folgenden Art:

- Die [concurrent_unordered_multimap:: Insert](reference/concurrent-unordered-multimap-class.md#insert) -Methode gibt einen Iterator anstelle von zurück `std::pair<iterator, bool>` .

- Die- `concurrent_unordered_multimap` Klasse stellt weder `operator[]` noch die-Methode bereit `at` .

Das folgende Beispiel zeigt die grundlegende Struktur für die Verwendung von `concurrent_unordered_multimap` . In diesem Beispiel werden Zeichen Schlüssel im Bereich [' a ', ' i '] eingefügt. `concurrent_unordered_multimap` ermöglicht es, dass ein Schlüssel mehrere Werte hat.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[Nach[oben](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a> concurrent_unordered_set-Klasse

Die [parallelcurrency:: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) -Klasse ähnelt der- `concurrent_unordered_map` Klasse, mit der Ausnahme, dass Sie Werte anstelle von Schlüssel-Wert-Paaren verwaltet. Die- `concurrent_unordered_set` Klasse stellt weder `operator[]` noch die-Methode bereit `at` .

Das folgende Beispiel zeigt die grundlegende Struktur für die Verwendung von `concurrent_unordered_set` . In diesem Beispiel werden Zeichen Werte im Bereich [' a ', ' i '] eingefügt. Es ist sicher, dass die Einfügungen parallel durchgeführt werden.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[Nach[oben](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a> concurrent_unordered_multiset-Klasse

Die [parallelcurrency:: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) -Klasse ähnelt der- `concurrent_unordered_set` Klasse, mit der Ausnahme, dass Sie doppelte Werte zulässt. Dies unterscheidet sich auch von `concurrent_unordered_set` der folgenden Art:

- Die [concurrent_unordered_multiset:: Insert](reference/concurrent-unordered-multiset-class.md#insert) -Methode gibt einen Iterator anstelle von zurück `std::pair<iterator, bool>` .

- Die- `concurrent_unordered_multiset` Klasse stellt weder `operator[]` noch die-Methode bereit `at` .

Das folgende Beispiel zeigt die grundlegende Struktur für die Verwendung von `concurrent_unordered_multiset` . In diesem Beispiel werden Zeichen Werte im Bereich [' a ', ' i '] eingefügt. `concurrent_unordered_multiset` ermöglicht, dass ein Wert mehrmals auftritt.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[Nach[oben](#top)]

## <a name="combinable-class"></a><a name="combinable"></a> combinable-Klasse

Die Klasse " [parallelcurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) " stellt einen wiederverwendbaren lokalen Thread Speicher bereit, mit dem Sie differenzierte Berechnungen ausführen und diese Berechnungen anschließend in ein Endergebnis zusammenführen können. Stellen Sie sich ein `combinable`-Objekt wie eine Reduktionsvariable vor.

Die- `combinable` Klasse ist nützlich, wenn Sie über eine Ressource verfügen, die von mehreren Threads oder Tasks gemeinsam genutzt wird. Mithilfe der- `combinable` Klasse können Sie den freigegebenen Zustand eliminieren, indem Sie den Zugriff auf freigegebene Ressourcen sperren. Daher bietet diese Klasse eine Alternative zur Verwendung eines Synchronisierungs Mechanismus, z. b. eines Mutex, um den Zugriff auf freigegebene Daten aus mehreren Threads zu synchronisieren.

### <a name="methods-and-features"></a><a name="combinable-features"></a> Methoden und Features

In der folgenden Tabelle sind einige der wichtigen Methoden der- `combinable` Klasse aufgeführt. Weitere Informationen zu allen `combinable` Klassen Methoden finden Sie unter [combinable Class](../../parallel/concrt/reference/combinable-class.md).

|Methode|Beschreibung|
|------------|-----------------|
|[nah](reference/combinable-class.md#local)|Ruft einen Verweis auf die lokale Variable ab, die dem aktuellen Thread Kontext zugeordnet ist.|
|[Löschen](reference/combinable-class.md#clear)|Entfernt alle lokalen Thread Variablen aus dem- `combinable` Objekt.|
|[Combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Verwendet die bereitgestellte Combine-Funktion, um einen endgültigen Wert aus dem Satz aller Thread lokalen Berechnungen zu generieren.|

Bei der- `combinable` Klasse handelt es sich um eine Vorlagen Klasse, die nach dem abschließenden zusammengeführten Ergebnis parametrisiert wird. Wenn Sie den Standardkonstruktor aufrufen, `T` muss der Vorlagen Parametertyp über einen Standardkonstruktor und einen Kopierkonstruktor verfügen. Wenn der `T` Vorlagen Parametertyp nicht über einen Standardkonstruktor verfügt, müssen Sie die überladene Version des Konstruktors aufrufen, der eine Initialisierungsfunktion als Parameter annimmt.

Sie können zusätzliche Daten in einem- `combinable` Objekt speichern, nachdem Sie die Methoden zum [kombinieren](reference/combinable-class.md#combine) oder [combine_each](reference/combinable-class.md#combine_each) aufgerufen haben. Sie können die `combine` -Methode und die-Methode auch mehrmals aufzurufen `combine_each` . Wenn kein lokaler Wert in einem- `combinable` Objekt geändert wird, `combine` führen die-Methode und die- `combine_each` Methode jedes Mal, wenn Sie aufgerufen werden, zu demselben Ergebnis.

### <a name="examples"></a><a name="combinable-examples"></a> Beispiele

Beispiele zur Verwendung der- `combinable` Klasse finden Sie in den folgenden Themen:

- [Gewusst wie: verbessern der Leistung mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Gewusst wie: Kombinieren von Gruppen mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[Nach[oben](#top)]

## <a name="related-topics"></a>Verwandte Themen

[Gewusst wie: erhöhen der Effizienz mithilfe paralleler Container](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Zeigt, wie parallele Container verwendet werden, um Daten effizient zu speichern und parallel auf Sie zuzugreifen.

[Gewusst wie: verbessern der Leistung mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Zeigt, wie die `combinable` -Klasse verwendet wird, um den Freigabe Zustand zu eliminieren und damit die Leistung zu verbessern.

[Gewusst wie: Kombinieren von Gruppen mithilfe von combinable](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Zeigt, wie eine `combine` Funktion zum Zusammenführen von Thread lokalen Datensätzen verwendet wird.

[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Beschreibt die ppl, die ein Imperatives Programmiermodell bereitstellt, das die Skalierbarkeit und Benutzerfreundlichkeit für die Entwicklung gleichzeitiger Anwendungen fördert.

## <a name="reference"></a>Referenz

[concurrent_vector-Klasse](../../parallel/concrt/reference/concurrent-vector-class.md)

[Concurrent_queue-Klasse](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map-Klasse](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap-Klasse](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set-Klasse](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset-Klasse](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable-Klasse](../../parallel/concrt/reference/combinable-class.md)
