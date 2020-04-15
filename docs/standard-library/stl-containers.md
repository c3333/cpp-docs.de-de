---
title: C++-Standardbibliothekscontainer
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, class template containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 01be754dd7b418f64cf495d7563f65b323265df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376704"
---
# <a name="c-standard-library-containers"></a>C++-Standardbibliothekscontainer

Die Standardbibliothek stellt unterschiedliche typsichere Container zum Speichern verknüpfter Objekte bereit. Die Container sind Klassenvorlagen. Wenn Sie eine Containervariable deklarieren, geben Sie den Typ der Elemente an, die der Container enthalten soll. Container können mit Initialisiererlisten erstellt werden. Sie verfügen über Memberfunktionen zum Hinzufügen und Entfernen von Elementen und zum Durchführen anderer Vorgänge.

Mit [Iteratoren](../standard-library/iterators.md) können Sie die einzelnen Elemente in einem Container durchlaufen und darauf zugreifen. Sie können Iteratoren explizit verwenden, indem Sie ihre Memberfunktionen und Operatoren sowie globale Funktionen verwenden. Sie können sie auch implizit verwenden, z. B. mit einer range-for-Schleife. Iteratoren für alle C++-Standardbibliothekscontainer haben eine gemeinsame Schnittstelle, aber jeder Container definiert seine eigenen speziellen Iteratoren.

Container können in drei Kategorien unterteilt werden: Sequenzcontainer, assoziative Container und Containeradapter.

## <a name="sequence-containers"></a><a name="sequence_containers"></a> Sequenzcontainer

Sequenzcontainer wahren die Reihenfolge der von Ihnen angegebenen eingefügten Elemente.

Ein `vector`-Container verhält sich wie ein Array, kann jedoch nach Bedarf automatisch erweitert werden. Er wird mit direktem Zugriff bzw. zusammenhängend gespeichert, und ist in der Länge hochgradig flexibel. Aus diesen und weiteren Gründen ist `vector` der bevorzugte Sequenzcontainer für die meisten Anwendungen. Verwenden Sie einen Vektor, wenn Sie sich nicht sicher sind, welchen Sequenzcontainertyp Sie verwenden sollen. Weitere Informationen finden Sie unter [vector-Klasse](../standard-library/vector-class.md).

Ein `array` Container hat einige `vector`der Stärken von , aber die Länge ist nicht so flexibel. Weitere Informationen finden Sie unter [vector-Klasse](../standard-library/array-class-stl.md).

Ein `deque`-Container (doppelseitige Warteschlange) ermöglichen schnelles Einfügen und Löschen am Anfang und Ende des Containers. Es teilt die Vorteile von , `vector`für den zuzufälligen Zugriff und die flexible Länge von , ist aber nicht zusammenhängend. Weitere Informationen finden Sie unter [deque-Klasse](../standard-library/deque-class.md).

Ein `list` Container ist eine doppelt verknüpfte Liste, die bidirektionalen Zugriff, schnelle Einfügungen und schnelle Löschungen an einer beliebigen Stelle im Container ermöglicht, aber Sie können nicht zufällig auf ein Element im Container zugreifen. Weitere Informationen finden Sie unter [list-Klasse](../standard-library/list-class.md).

Ein `forward_list`-Container ist eine einfach verknüpfte Liste. Er ist die Version mit Vorwärtszugriff von `list`. Weitere Informationen finden Sie unter [forward_list-Klasse](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Assoziative Container

In assoziativen Containern werden Elemente in einer vordefinierten Reihenfolge eingefügt, z. B. sortiert aufsteigend. Unsortierte assoziative Container sind ebenfalls verfügbar. Assoziative Container können in zwei Teilbereiche gruppiert werden: Zuordnungen und Sätze.

`map` (manchmal auch als ein Wörterbuch bezeichnet) besteht aus einem Schlüssel-Wert-Paar. Der Schlüssel wird zum Sortieren der Reihenfolge verwendet, und der Wert wird dem Schlüssel zugeordnet. Z. B. kann `map` eindeutige Schlüssel enthalten, die jedes einzelne Wort in einem Text und die entsprechenden Werte darstellen, die die Häufigkeit darstellen, mit der jedes Wort im Text angezeigt wird. Die unsortierte Version von `map` ist `unordered_map`. Weitere Informationen finden Sie unter [map-Klasse](../standard-library/map-class.md) und [unordered_map-Klasse](../standard-library/unordered-map-class.md).

Ein `set`-Element ist lediglich ein aufsteigender Container eindeutiger Elemente. Der Wert ist auch gleichzeitig der Schlüssel. Die unsortierte Version von `set` ist `unordered_set`. Weitere Informationen finden Sie unter [set-Klasse](../standard-library/set-class.md) und [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Sowohl `map` als auch `set` ermöglichen das Einfügen nur einer Instanz eines Schlüssels oder Elements in den Container. Wenn mehrere Instanzen der Elemente erforderlich sind, verwenden Sie `multimap` oder `multiset`. Die unsortierten Versionen sind `unordered_multimap` und `unordered_multiset`. Weitere Informationen finden Sie unter [multimap-Klasse](../standard-library/multimap-class.md), [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md), [multiset-Klasse](../standard-library/multiset-class.md) und [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Bei sortierten Zuordnungen und Sätzen werden bidirektionale Iteratoren unterstützt, und bei den unsortierten Entsprechungen werden Vorwärtsiteratoren unterstützt. Weitere Informationen finden Sie unter [Iteratoren](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Heterogenes Nachschlagen in assoziativen Containern (C++14)

Die geordneten assoziativen Container (Map, Multimap, Set und Multiset) unterstützen jetzt eine heterogene Suche, was bedeutet, dass Sie nicht `find()` mehr `lower_bound()`den genau gleichen Objekttyp wie der Schlüssel oder das Element in Memberfunktionen wie und übergeben müssen. Stattdessen können Sie einen beliebigen Typ übergeben, für den ein überladener `operator<` definiert ist, mit dem ein Vergleich mit dem Schlüsseltyp aktiviert wird.

Heterogenes Nachschlagen wird auf Opt-in-Basis aktiviert, wenn Sie den `std::less<>`- oder `std::greater<>`-„diamond functor“-Vergleichsoperator beim Deklarieren der Containervariablen angeben, wie im Folgenden dargestellt:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Bei Verwendung des Standardvergleichsoperators weist der Container dasselbe Verhalten wie in C++11 und früheren Versionen auf.

Das folgende Beispiel zeigt, `operator<` wie Sie `std::set` überladen werden, damit Benutzer von a Suchschritte ausführen können, `BigObject::id` indem Sie einfach eine kleine Zeichenfolge übergeben, die mit dem Member jedes Objekts verglichen werden kann.

```cpp
#include <set>
#include <string>
#include <iostream>
#include <functional>

using namespace std;

class BigObject
{
public:
    string id;
    explicit BigObject(const string& s) : id(s) {}
    bool operator< (const BigObject& other) const
    {
        return this->id < other.id;
    }

    // Other members....
};

inline bool operator<(const string& otherId, const BigObject& obj)
{
    return otherId < obj.id;
}

inline bool operator<(const BigObject& obj, const string& otherId)
{
    return obj.id < otherId;
}

int main()
{
    // Use C++14 brace-init syntax to invoke BigObject(string).
    // The s suffix invokes string ctor. It is a C++14 user-defined
    // literal defined in <string>
    BigObject b1{ "42F"s };
    BigObject b2{ "52F"s };
    BigObject b3{ "62F"s };
    set<BigObject, less<>> myNewSet; // C++14
    myNewSet.insert(b1);
    myNewSet.insert(b2);
    myNewSet.insert(b3);
    auto it = myNewSet.find(string("62F"));
    if (it != myNewSet.end())
        cout << "myNewSet element = " << it->id << endl;
    else
        cout << "element not found " << endl;

    // Keep console open in debug mode:
    cout << endl << "Press Enter to exit.";
    string s;
    getline(cin, s);
    return 0;
}

//Output: myNewSet element = 62F
```

Die folgenden Memberfunktionen in Map, Multimap, Set und Multiset wurden überladen, um eine heterogene Suche zu unterstützen:

1. Suchen

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Containeradapter

Ein Containeradapter ist die Variante einer Sequenz oder eines assoziativen Containers, die die Schnittstelle zwecks Einfachheit und Verständlichkeit einschränkt. Containeradapter unterstützen keine Iteratoren.

Ein `queue`-Container folgt der FIFO-Semantik (first in, first out). Das erste *abgelegte* Element, d.h. das in Warteschlange eingefügte, ist das erste, das entnommen wird, d.h. aus der Warteschlange *entfernt* wird. Weitere Informationen finden Sie unter [queue-Klasse](../standard-library/queue-class.md).

Ein `priority_queue`-Container wird so organisiert, dass das Element, das über den höchsten Wert verfügt, immer zuerst in der Warteschlange steht. Weitere Informationen finden Sie unter [priority_queue-Klasse](../standard-library/priority-queue-class.md).

Ein `stack`-Container folgt der LIFO-Semantik (last in, first out). Das letzte Element, das auf dem Stapel abgelegt wird, ist das erste entnommene Element. Weitere Informationen finden Sie unter [stack-Klasse](../standard-library/stack-class.md).

Da Containeradapter keine Iteratoren unterstützen, können sie nicht mit den C++-Standardbibliotheksalgorithmen verwendet werden. Weitere Informationen finden Sie unter [Algorithmen](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Anforderungen für Containerelemente

Im Allgemeinen können Elemente, die in einen C++-Standardbibliothekscontainer eingefügt werden, fast jeden Objekttyp haben, wenn sie kopiert werden können. Nur verschiebbare Elemente – z. B. `vector<unique_ptr<T>>`, die mithilfe von `unique_ptr<>` erstellt werden, funktionieren, solange keine Memberfunktionen aufgerufen werden, die versuchen, sie zu kopieren.

Der Destruktor darf keine Ausnahme auslösen.

Sortierte assoziative Container (früher im Artikel beschrieben) müssen einen öffentlich definierten Vergleichsoperator aufweisen. (Standardmäßig ist `operator<` der Operator, allerdings werden auch Typen, die nicht mit `operator<` arbeiten, unterstützt.

Einige Vorgänge in Containern könnten auch einen öffentlichen Standardkonstruktor und einen öffentlichen Äquivalenzoperator erfordern. Beispielsweise benötigen die unsortierten assoziativen Container eine Unterstützung für Gleichheit und Hashverfahren.

## <a name="accessing-container-elements"></a>Zugreifen auf Containerelemente

Auf Containerelemente wird mithilfe von Iteratoren zugegriffen. Weitere Informationen finden Sie unter [Iteratoren](../standard-library/iterators.md).

> [!NOTE]
> Sie können auch [bereichsbasierte For-Schleifen](../cpp/range-based-for-statement-cpp.md) verwenden, um C++-Standardbibliotheksauflistungen zu durchlaufen.

## <a name="comparing-containers"></a>Vergleichen von Containern

Alle Container überladen den Operator „==“ zum Vergleichen von zwei Containern desselben Typs, die den gleichen Elementtyp aufweisen. Sie können == verwenden,\<um eine\<Vektorzeichenfolge> mit einer anderen Vektorzeichenfolge\<> zu vergleichen, aber Sie können sie nicht verwenden, um eine Vektorzeichenfolge> mit einer Listenzeichenfolge\<> oder einer Vektorzeichenfolge\<> mit einem Vektor-Zeichen*>\<zu vergleichen.  In C++98/03 können Sie [std::equal](algorithm-functions.md#equal) oder [std::mismatch](algorithm-functions.md#mismatch) verwenden, um unterschiedliche Containertypen und/oder Elementtypen zu vergleichen. In C++11 können Sie auch [std::is_permutation](algorithm-functions.md#is_permutation)verwenden. Aber in all diesen Fällen gehen die Funktionen davon aus, dass die Container gleich lang sind. Wenn der zweite Bereich kürzer als der erste ist, kommt es zu nicht definiertem Verhalten. Wenn der zweite Bereich länger ist, sind die Ergebnisse möglicherweise trotzdem falsch, da der Vergleich nie über das Ende des ersten Bereichs hinaus fortgesetzt wird.

### <a name="comparing-dissimilar-containers-c14"></a>Vergleichen unterschiedlicher Container (C++14)

In C++14 und höher können Sie unterschiedliche Container und/oder unterschiedliche Elementtypen `std::mismatch`vergleichen, indem Sie einen der , oder `std::is_permutation` Funktionsüberladungen verwenden, die `std::equal`zwei vollständige Bereiche annehmen. Mit diesen Überladungen können Sie Container mit unterschiedlicher Länge vergleichen. Diese Überladungen sind weniger für Benutzerfehler anfällig und sind beim Vergleichen von Containern mit unterschiedlicher Länge so optimiert, dass sie in konstanter Zeit FALSE zurückgeben. Daher empfehlen wir Ihnen, diese Überladungen zu verwenden, es sei denn, Sie haben einen klaren Grund, einen [std::list-Container](../standard-library/list-class.md) nicht zu verwenden, der nicht von den Dual-Range-Optimierungen profitiert.

## <a name="see-also"></a>Siehe auch

[Parallelcontainer](../parallel/concrt/parallel-containers-and-objects.md)\
[\<Probenbehälter>](../standard-library/sample-container.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
