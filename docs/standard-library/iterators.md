---
title: Iterators
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: c3bb2825ec6ad98f523fa4c3a616d0807eac50a8
ms.sourcegitcommit: 5ef9697b4cb1947bec9669be57bc920d2c4d82a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87870151"
---
# <a name="iterators"></a>Iterators

Ein Iterator ist ein Objekt, das Elemente in einem C++-Standardbibliothekscontainer durchlaufen kann und den Zugriff auf einzelne Elemente bereitstellt. Alle C++-Standardbibliothekscontainer stellen Iteratoren bereit, damit Algorithmen standardisiert auf ihre Elemente zugreifen können, ohne dass die Art des Containers von Bedeutung ist, in dem die Elemente gespeichert werden.

Sie können Iteratoren explizit mit Element-und globalen Funktionen wie `begin()` und `end()` und Operatoren wie `++` und verwenden `--` , um vorwärts oder rückwärts zu wechseln. Sie können Iteratoren auch implizit mit einer Range-for-Schleife oder (bei einigen iteratortypen) dem Index Operator verwenden `[]` .

In der C++-Standardbibliothek ist der Anfang einer Sequenz oder eines Bereichs das erste Element. Das Ende einer Sequenz oder eines Bereichs wird immer als eins hinter dem letzten Element definiert. Die globalen Funktionen `begin` und `end` geben Iteratoren zu einem angegebenen Container zurück. Die typische explizite Iteratorschleife durch alle Elemente in einem Container sieht folgendermaßen aus:

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

Das Gleiche kann einfacher mit einer range-for-Schleife erreicht werden:

```cpp
for (auto num : vec)
{
    // no dereference operator
    cout << num << " ";
}
```

Es gibt fünf Kategorien von Iteratoren. Die Kategorien zum Erhöhen der Leistung sind:

- **Ausgabe**. Ein *Ausgabeiterator* `X` kann eine Sequenz mithilfe des-Operators vorwärts durchlaufen `++` und ein Element nur einmal schreiben, indem der-Operator verwendet wird __`*`__ .

- **Eingabe**. Ein *eingabeiterator* `X` kann eine Sequenz mithilfe des-Operators vorwärts durchlaufen `++` und ein Element beliebig oft mithilfe des- `*` Operators lesen. Sie können eingabeiteratoren mithilfe der `==` `!=` Operatoren und vergleichen. Nachdem Sie eine Kopie eines eingabeiterators erhöht haben, kann keine der anderen Kopien sicher verglichen, dereferenziert oder später inkrementiert werden.

- **Weiterleiten**. Ein *forward-Iterator* `X` kann eine Sequenz mit dem Operator + + vorwärts durchlaufen und jedes beliebige Element lesen oder nicht konstante Elemente beliebig oft mithilfe des- `*` Operators schreiben. Sie können mithilfe des-Operators auf Element Elemente zugreifen `->` und Forward-Iteratoren mithilfe der `==` `!=` Operatoren und vergleichen. Sie können mehrere Kopien eines Forward-Iterators anfertigen, wobei jede einzelne unabhängig dereferenziert und inkrementiert werden kann. Ein forward-Iterator, der ohne Verweis auf einen Container initialisiert wird, wird als *null-forward-Iterator*bezeichnet. Null-Forward-Iteratoren vergleichen immer gleich.

- **Bidirektional**. Ein *bidirektionaler Iterator* `X` kann an die Stelle eines Forward-Iterators gelangen. Sie können jedoch auch einen bidirektionalen Iterator Dekrement wie in `--X` , `X--` oder verringern `(V = *X--)` . Sie können auf Elementmitglieder zugreifen und bidirektionale Iteratoren genauso wie Forward-Iteratoren vergleichen.

- **Zufälliger Zugriff**. Ein *Iterator mit zufälligem Zugriff* `X` kann den Platz eines bidirektionalen Iterators einnehmen. Mit einem Random-Access-Iterator können Sie den Index Operator verwenden, `[]` um auf Elemente zuzugreifen. Sie können die `+` `-` `+=` Operatoren, und verwenden, `-=` um eine angegebene Anzahl von Elementen vorwärts oder rückwärts zu bewegen und den Abstand zwischen Iteratoren zu berechnen. Bidirektionale Iteratoren können mit `==` , `!=` ,, `<` `>` , `<=` und `>=` verglichen werden.

Alle Iteratoren können zugewiesen oder kopiert werden. Es wird davon ausgegangen, dass es sich um Lightweight-Objekte handelt, und Sie werden oft als Wert und nicht als Verweis zurückgegeben. Beachten Sie zudem, dass einer der zuvor beschriebenen Vorgänge eine Ausnahme auslösen kann, wenn er für einen gültigen Iterator ausgeführt wird.

Die Hierarchie der Iteratorkategorien kann durch das Zeigen von drei Sequenzen zusammengefasst werden. Für den schreibgeschützten Zugriff auf eine Sequenz können Sie Folgendes verwenden:

> Ausgabeiterator \
> -> forward-Iterator \
> -> bidirektionaler Iterator \
> -> Random-Access-Iterator

Der Pfeil nach rechts meint: „kann ersetzt werden durch“. Jeder einen Ausgabeiterator aufrufende Algorithmus sollte beispielsweise problemlos mit einem Forward-Iterator funktionieren; dies gilt jedoch *nicht* umgekehrt.

Für den schreibgeschützten Zugriff auf eine Sequenz können Sie Folgendes verwenden:

> eingabeiterator \
> -> forward-Iterator \
> -> bidirektionaler Iterator \
> -> Random-Access-Iterator

In diesem Fall ist ein Eingabeiterator die schwächste aller Kategorien.

Schließlich können Sie für den Lese-/Schreibzugriff auf eine Sequenz Folgendes verwenden:

> forward-Iterator \
> -> bidirektionaler Iterator \
> -> Random-Access-Iterator

Ein Objektzeiger kann immer als ein Random-Access-Iterator fungieren. Er kann demnach als eine beliebige Kategorie des Iterators fungieren, wenn er den entsprechenden Lese-/Schreibzugriff auf die Sequenz unterstützt, die er festlegt.

Ein Iterator `Iterator`, der dem Objektzeiger nicht entspricht, muss zudem die Membertypen definieren, die durch die Spezialisierung `iterator_traits<Iterator>` erforderlich ist. Diese Anforderungen können erfüllt werden, indem `Iterator` von dem öffentlichen basisklasseniterator abgeleitet wird. [iterator](../standard-library/iterator-struct.md)

Es ist wichtig, die Zusagen und Einschränkungen jeder iteratorkategorie zu verstehen, um zu sehen, wie Iteratoren von Containern und Algorithmen in der C++-Standard Bibliothek verwendet werden.

> [!NOTE]
> Sie können die explizite Verwendung von Iteratoren mithilfe von range-for-Schleifen umgehen. Weitere Informationen finden Sie unter [Range-based for-Anweisung](../cpp/range-based-for-statement-cpp.md).

Microsoft C++ bietet jetzt überprüfte Iteratoren und Debugiteratoren, um sicherzustellen, dass Sie die Begrenzungen Ihres Containers nicht überschreiben. Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md) und [Unterstützung für Iteratordebugging](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Weitere Informationen

[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
