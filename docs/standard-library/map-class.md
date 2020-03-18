---
title: map-Klasse
ms.date: 10/18/2018
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
ms.openlocfilehash: d25d8837c549b425416632ee07e23bb57fbd17ae
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425538"
---
# <a name="map-class"></a>map-Klasse

Wird zum Speichern und Abrufen von Daten aus einer Auflistung verwendet, in der jedes Element ein Paar ist, das einen Datenwert und einen Sortierschlüssel aufweist. Der Wert des Schlüssels ist eindeutig und wird verwendet, zum automatischen Sortieren der Daten verwendet.

Der Wert eines Elements in einer Zuordnung kann direkt geändert werden. Der Schlüsselwert ist eine Konstante und kann nicht geändert werden. Stattdessen müssen die Schlüsselwerte, die alten Elementen zugeordnet sind, gelöscht und neue Schlüsselwerte für neue Elemente eingefügt werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Key,
    class Type,
    class Traits = less<Key>,
    class Allocator=allocator<pair <const Key, Type>>>
class map;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der in der Zuordnung zu speichernde Schlüsseldatentyp.

*Typ*\
Der in der Zuordnung zu speichernde Elementdatentyp.

*Merkmale*\
Der Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Zuordnung zu bestimmen. Dieses Argument ist optional, und das binäre Prädikat `less<Key>` ist der Standardwert.

In C ++ 14 können Sie heterogenes Nachschlagen durch Angabe des std::less<>-Prädikats aktivieren, das keine Typparameter aufweist. Weitere Informationen finden Sie unter [Heterogenes Nachschlagen in assoziativen Containern](../standard-library/stl-containers.md#sequence_containers)

*Zuordner\*
Der Typ, der das gespeicherte Zuordnungsobjekt darstellt, das Details zum Belegen und Freigeben des Arbeitsspeichers der Zuordnung kapselt. Dieses Argument ist optional, und der Standardwert ist `allocator<pair<const Key, Type> >`.

## <a name="remarks"></a>Hinweise

Die map-Klasse der C++-Standardbibliothek ist:

- Ein Container variabler Größe, der Elementwerte effizient auf Grundlage zugeordneter Schlüsselwerte abruft.

- Umkehrbar, da bidirektionale Iteratoren für den Zugriff auf die Elemente bereitgestellt werden.

- Sortiert, da die Elemente entsprechend einer angegebenen Vergleichsfunktion nach Schlüsselwerten sortiert werden.

- Eindeutig. Eindeutig, da jedes der Elemente einen eindeutigen Schlüssel aufweisen muss.

- Ein Paar-assoziativer Container, da sich die Elementdatenwerte von den Schlüsselwerten unterscheiden.

- Eine Klassen Vorlage, da die von ihr bereitgestellte Funktionalität generisch und unabhängig vom Element-oder Schlüsseltyp ist. Die für Elemente und Schlüssel verwendeten Datentypen werden in der Klassenvorlage zusammen mit der Vergleichsfunktion und der Zuweisung als Parameter angegeben.

Der von einer Zuordnungsklasse bereitgestellte Iterator ist ein bidirektionaler Iterator. Die Klassenmemberfunktionen [insert](#insert) und [map](#map) weisen allerdings Versionen auf, die einen abgeschwächten Eingabeiterator als einen Vorlagenparameter akzeptieren, dessen Funktionalitätsanforderungen weniger umfangreich sind, als die von der Klasse bidirektionaler Iteratoren garantierten. Die verschiedenen Iteratorkonzepte sind durch Verfeinerungen in ihrer Funktionen verknüpft. Jedes Iteratorkonzept weist einen eigenen Satz von Anforderungen auf, und damit einhergehenden Algorithmen müssen durch diese Anforderungen beschränkt werden. Ein Eingabeiterator kann dereferenziert werden, um auf ein Objekt zu verweisen und wird zum folgenden Iterator in der Sequenz erhöht.

Es wird empfohlen, dass Sie die Auswahl des Containertyps auf Grundlage der für die Anwendung erforderlichen Such- und Einfügeweise treffen. Assoziative Container sind auf Such-, Einfüge- und Entfernvorgänge optimiert. Die Memberfunktionen, die diese Vorgänge explizit unterstützen, führen sie in einer Zeit für den schlimmsten Fall aus, die zum Logarithmus der Elementanzahl im Container proportional ist. Das Einfügen von Elementen führt nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen von Elementen werden nur solche Iteratoren ungültig, die speziell auf die entfernten Elemente gezeigt haben.

Es wird empfohlen, die Zuordnung der ausgewählten assoziativen Container zu erstellen, wenn die Bedingungen zur Zuordnung der Werte mit Schlüssel von der Anwendung erfüllt werden. Ein Modell dieser Art von Struktur ist eine geordnete Liste eindeutig auftretender Schlüsselwörter, die Zeichenfolgewerte zugeordnet aufweisen, die Definitionen bereitstellen. Wenn ein Wort über mehrere genaue Definition verfügt, sodass der Schlüssel nicht eindeutig ist, ist eine Mehrfachzuordnung der ausgewählte Container. Wenn nur die Wortliste gespeichert wird, ist ein Satz der geeignete Container. Wenn mehrfaches Vorkommen der Wörter zulässig ist, ist eine Multimenge geeignet.

Die Zuordnung sortiert die von ihr gesteuerten Elemente, indem ein gespeichertes Funktionsobjekt vom Typ [key_compare](#key_compare) aufgerufen wird. Bei diesem gespeicherten Objekt handelt es sich um eine Vergleichsfunktion, auf die zugegriffen wird, indem die [key_compare](#key_comp)-Methode aufgerufen wird. Im Allgemeinen werden beliebige zwei angegebene Elemente verglichen, um zu bestimmen, ob eins kleiner als das andere ist, oder ob sie sich entsprechen. Obwohl alle Elemente verglichen werden, wird eine sortierte Sequenz antivalenter Elementen erstellt.

> [!NOTE]
> Die Vergleichsfunktion ist ein binäres Prädikat, das eine strenge schwache Sortierung im üblichen mathematischen Sinn erzeugt. Bei einem binären f (x, y)-Prädikat handelt es sich um ein Funktions Objekt, das die zwei Argument Objekte x und y aufweist sowie einen Rückgabewert von **true** oder **false**. Eine für einen Satz vorgegebene Reihenfolge ist eine strikte schwache Reihenfolge, wenn das binäre Prädikat unreflexiv, antisymmetrisch und transitiv ist und wenn die Äquivalenz transitiv ist, wobei die beiden Objekte x und y als Äquivalent definiert werden, wenn sowohl f (x, y) als auch f (y, x) **false**sind. Wenn der stärkere Gleichheitszustand zwischen Schlüsseln die Äquivalenz ersetzt, erfolgt die Sortierung total (d. h., alle Elemente werden zueinander sortiert), und die verglichenen Schlüssel sind von den einander nicht mehr zu unterscheiden.
>
> In C ++ 14 können Sie heterogenes Nachschlagen durch Angabe des `std::less<>` oder `std::greater<>` Prädikats, das keine Typparameter aufweist, aktivieren. Weitere Informationen finden Sie unter [Heterogenes Nachschlagen in assoziativen Containern](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[map](#map)|Erstellt eine Liste einer bestimmten Größe bzw. mit Elementen eines bestimmten Werts oder mit einem bestimmten `allocator`-Element oder als vollständige bzw. teilweise Kopie einer anderen Zuordnung.|

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[allocator_type](#allocator_type)|Eine Typdefinition für die `allocator`-Klasse für das Zuordnungsobjekt.|
|[const_iterator](#const_iterator)|Eine typedef für einen bidirektionalen Iterator, mit dem ein **Konstanten** Element in der Zuordnung gelesen werden kann.|
|[const_pointer](#const_pointer)|Eine typedef für einen Zeiger auf ein **Konstanten** Element in einer Zuordnung.|
|[const_reference](#const_reference)|Eine typedef für einen Verweis auf ein **Konstanten** Element, das in einer Zuordnung zum Lesen und Ausführen von **Konstanten** Vorgängen gespeichert ist.|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes **const**-Element in einer Zuordnung gelesen werden kann.|
|[difference_type](#difference_type)|Ein Ganzzahltyp mit Vorzeichen für die Anzahl von Elementen einer Zuordnung in einem Bereich zwischen Elementen, auf die von Iteratoren gezeigt wird.|
|[iterator](#iterator)|Eine Typedef für einen bidirektionalen Iterator, der ein beliebiges Element in einer Zuordnung lesen oder ändern kann.|
|[key_compare](#key_compare)|Eine Typedef für ein Funktionsobjekt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen in der Zuordnung zu bestimmen.|
|[key_type](#key_type)|Eine Typedef für den in jedem Element der Zuordnung gespeicherten Sortierschlüssel.|
|[mapped_type](#mapped_type)|Eine Typedef für die in jedem Element einer Zuordnung gespeicherten Daten.|
|[pointer](#pointer)|Eine typedef für einen Zeiger auf ein **Konstanten** Element in einer Zuordnung.|
|[reference](#reference)|Eine Typedef für einen Verweis auf ein in einer Zuordnung gespeichertes Element.|
|[reverse_iterator](#reverse_iterator)|Eine Typdefinition für einen bidirektionalen Iterator, der ein beliebiges Element in einer reservierten Zuordnung lesen oder ändern kann.|
|[size_type](#size_type)|Eine Ganzzahltypedef ohne Vorzeichen für die Anzahl von Elementen in einer Zuordnung.|
|[value_type](#value_type)|Eine Typedef für den Typ des Objekts, der als Element in einer Zuordnung gespeichert wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|Beschreibung|
|-|-|
|[at](#at)|Sucht ein Element mit einem angegebenen Schlüsselwert.|
|[begin](#begin)|Gibt einen Iterator zurück, der auf das erste Element in der Zuordnung zeigt.|
|[cbegin](#cbegin)|Gibt einen konstanten Iterator zurück, der auf das erste Element in der Zuordnung zeigt.|
|[cend](#cend)|Gibt einen konstanten "past-the-end"-Iterator zurück.|
|[clear](#clear)|Löscht alle Elemente einer Zuordnung auf.|
|[count](#count)|Gibt die Anzahl von Elementen in einer Zuordnung zurück, deren Schlüssel dem in einem Parameter angegebenen Schlüssel entspricht.|
|[crbegin](#crbegin)|Gibt einen konstanten Iterator zurück, der auf das erste Element in einer umgekehrten Zuordnung zeigt.|
|[crend](#crend)|Gibt einen konstanten Iterator zurück, der auf den Speicherort zeigt, der hinter dem letzten Element einer umgekehrten Zuordnung liegt.|
|[emplace](#emplace)|Fügt ein Element ein, das vor Ort in die Zuordnung erstellt wird.|
|[emplace_hint](#emplace_hint)|Fügt ein Element ein, das vor Ort mit einem Platzierungshinweis in die Zuordnung erstellt wird.|
|[leer](#empty)|Gibt **true** zurück, wenn eine Zuordnung leer ist.|
|[end](#end)|Gibt den "past-the-end"-Iterator zurück.|
|[equal_range](#equal_range)|Gibt ein Paar von Iteratoren zurück. Der erste Iterator im Paar zeigt auf das erste Element in `map` mit einem Schlüssel, der größer ist, als ein bestimmter Schlüssel. Der zweite Iterator im Paar zeigt auf das erste Element in `map` mit einem Schlüssel, die größer oder gleich dem Schlüssel ist.|
|[erase](#erase)|Entfernt ein Element oder eine Reihe von Elementen in einer Zuordnung aus den angegebenen Positionen.|
|[find](#find)|Gibt einen Iterator zurück, der auf den Speicherort eines Elements in einer Zuordnung zeigt, der einen Schlüssel gleich einem angegebenen Schlüssel aufweist.|
|[get_allocator](#get_allocator)|Gibt eine Kopie des zum Erstellen der Zuordnung verwendeten `allocator`-Objekts zurück.|
|[insert](#insert)|Fügt ein Element oder einen Reihe von Elementen an einer angegebenen Position in die Zuordnung ein.|
|[key_comp](#key_comp)|Gibt eine Kopie des Vergleichsobjekts zurück, das verwendet wird, um die Schlüssel in einer Zuordnung zu sortieren.|
|[lower_bound](#lower_bound)|Gibt einen Iterator zum ersten Element in einer Zuordnung zurück, die einen Schlüsselwert aufweist, der gleich oder größer ist als ein angegebener Schlüssel.|
|[max_size](#max_size)|Gibt die Maximallänge der Zuordnung zurück.|
|[rbegin](#rbegin)|Gibt einen Iterator zurück, der auf das erste Element in einer umgekehrten Zuordnung zeigt.|
|[rend](#rend)|Gibt einen Iterator zurück, der auf den Speicherort zeigt, der hinter dem letzten Element einer umgekehrten Zuordnung liegt.|
|[size](#size)|Gibt die Anzahl von Elementen in der Zuordnung zurück.|
|[swap](#swap)|Tauscht die Elemente zweier Zuordnungen aus.|
|[upper_bound](#upper_bound)|Gibt einen Iterator zum ersten Element in einer Zuordnung zurück, die einen Schlüsselwert aufweist, der größer ist als ein angegebener Schlüssel.|
|[value_comp](#value_comp)|Ruft eine Kopie des Vergleichsobjekts ab, das verwendet wird, um Elementwerte in einer Zuordnung zu sortieren.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[operator[]](#op_at)|Fügt ein Element in eine Zuordnung mit einem angegebenen Schlüsselwert ein.|
|[operator=](#op_eq)|Ersetzt die Elemente einer Zuordnung durch einer Kopie einer anderen Zuordnung.|

## <a name="allocator_type"></a>allocator_type

Ein Typ, der die Zuweisungsklasse für das map-Objekt darstellt.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Beispiel

In dem Beispiel für [get_allocator](#get_allocator) finden Sie ein Beispiel, das `allocator_type` verwendet.

## <a name="at"></a>an

Sucht ein Element mit einem angegebenen Schlüsselwert.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parameter

Schlüssel * \
Der Schlüsselwert, das gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf den Datenwert des gefundenen Elements.

### <a name="remarks"></a>Hinweise

Wird der als Argument angegebene Schlüsselwert nicht gefunden, löst die Funktion ein Objekt der [out_of_rage](../standard-library/out-of-range-class.md)-Klasse aus.

### <a name="example"></a>Beispiel

```cpp
// map_at.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

typedef std::map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
    }
```

## <a name="begin"></a>beginnen

Gibt einen Iterator zurück, der das erste Element im map-Element adressiert.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der das erste Element in der Zuordnung oder den auf eine Leere Zuordnung folgenden Speicherort adressiert.

### <a name="example"></a>Beispiel

```cpp
// map_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err because the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
The first element of m1 is now 1
```

## <a name="cbegin"></a>cbegin

Gibt einen **Konstanten** Iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **konstanter** bidirektionaler Iterator, der das erste Element im Bereich oder die Position direkt hinter dem Ende eines leeren Bereichs adressiert (für einen leeren Bereich, `cbegin() == cend()`).

### <a name="remarks"></a>Hinweise

Bei dem Rückgabewert `cbegin` können die Elemente im Bereich nicht geändert werden.

Sie können diese Memberfunktion anstelle der `begin()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [automatischen](../cpp/auto-cpp.md) Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollten `Container` ein änderbarer (nicht **konstanter) Container**sein, der `begin()` und `cbegin()`unterstützt.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Gibt einen **Konstanten** Iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **konstanter** bidirektionaler-Access-Iterator, der direkt hinter das Ende des Bereichs zeigt.

### <a name="remarks"></a>Hinweise

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines Bereichs übergeben hat.

Sie können diese Memberfunktion anstelle der `end()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [automatischen](../cpp/auto-cpp.md) Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollten `Container` ein änderbarer (nicht **konstanter) Container**sein, der `end()` und `cend()`unterstützt.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="clear"></a>Klartext

Löscht alle Elemente einer Zuordnung auf.

```cpp
void clear();
```

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der „map::clear“-Memberfunktion gezeigt.

```cpp
// map_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 4));

    i = m1.size();
    cout << "The size of the map is initially "
         << i << "." << endl;

    m1.clear();
    i = m1.size();
    cout << "The size of the map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the map is initially 2.
The size of the map after clearing is 0.
```

## <a name="const_iterator"></a>const_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein **const**-Element in der Zuordnung gelesen werden kann.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Hinweise

Ein `const_iterator`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

Der von Map definierte `const_iterator` verweist auf Elemente, die Objekte [value_type](#value_type)sind, vom Typ `pair`\< **constkey**, **Type**>, dessen erster Member der Schlüssel zum Element und dessen zweiter Member das zugeordnete Datum ist, das vom Element gehalten wird.

Verwenden Sie zum Aufheben der Dereferenzierung eines `const_iterator` `cIter` das auf ein Element in einer Zuordnung verweist, den `->`-Operator.

Um auf den Wert des Schlüssels für das Element zuzugreifen, verwenden Sie `cIter` -> **First**, das (\* `cIter`) entspricht. **first** entspricht, um auf den Wert des zugeordneten Datums für das Element zuzugreifen.

Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `cIter` -> **Sekunde**, das (\* `cIter`) entspricht. **second** entspricht, um auf den Wert des zugeordneten Datums für das Element zuzugreifen.

### <a name="example"></a>Beispiel

In dem Beispiel für [begin](#begin) finden Sie ein Beispiel, das `const_iterator` verwendet.

## <a name="const_pointer"></a>const_pointer

Ein Typ, der einen Zeiger auf ein **const**-Element in einer Zuordnung bereitstellt.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Hinweise

Ein `const_pointer`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem map-Objekt verwendet werden.

## <a name="const_reference"></a>const_reference

Ein Typ, der einen Verweis auf ein **const**-Element bereitstellt, das in einer Zuordnung zum Lesen und Ausführen von **const**-Vorgängen gespeichert ist.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Beispiel

```cpp
// map_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes **const**-Element in einer Zuordnung gelesen werden kann.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Hinweise

Ein `const_reverse_iterator`-Typ kann nicht den Wert eines Elements ändern und wird verwendet, um die Zuordnung in umgekehrter Reihenfolge zu durchlaufen.

Der von Map definierte `const_reverse_iterator` verweist auf Elemente, die Objekte [value_type](#value_type)sind, die vom Typ `pair<const Key, Type>`sind, dessen erster Member der Schlüssel zum Element und dessen zweiter Member das zugeordnete Datum ist, das vom Element gehalten wird.

Um einen `const_reverse_iterator crIter` zu dereferenzieren, der auf ein Element in einer Zuordnung zeigt, verwenden Sie den `->`-Operator.

Um auf den Wert des Schlüssels für das Element zuzugreifen, verwenden Sie `crIter` -> **First**, das (\* `crIter`) entspricht. **zuerst**.

Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `crIter` -> **Sekunde**, das (\* `crIter`) entspricht. **zuerst**.

### <a name="example"></a>Beispiel

Im Beispiel für [rend](#rend) wird verdeutlicht, wie ein `const_reverse_iterator` deklariert und verwendet wird.

## <a name="count"></a>Countdown

Gibt die Anzahl von Elementen in einer Zuordnung zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Schlüsselwert der aus der Zuordnung zu entfernenden Elemente.

### <a name="return-value"></a>Rückgabewert

1, wenn die Zuordnung ein Element enthält, dessen Sortierungsschlüssel dem Parameterschlüssel entspricht; 0, wenn die Zuordnung kein Element mit einem übereinstimmenden Schlüssel enthält.

### <a name="remarks"></a>Hinweise

Die Memberfunktion ermöglicht die Rückgabe der Anzahl von Elementen *x* im Bereich

\[ lower_bound (*Schlüssel*), upper_bound (*Schlüssel*))

0 oder 1 für eine Zuordnung, was einem eindeutigen assoziativen Container entspricht.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion „map::count“ gezeigt.

```cpp
// map_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Keys must be unique in map, so duplicates are ignored
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 1.
The number of elements in m1 with a sort key of 2 is: 1.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>crbegin

Gibt einen const-Iterator zurück, der das erste Element in einer umgekehrten Zuordnung adressiert.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler const-Iterator, der auf das erste Element in einer umgekehrten [map](../standard-library/map-class.md) oder auf das letzte Element der vormals nicht umgekehrten `map` verweist.

### <a name="remarks"></a>Hinweise

`crbegin` wird bei einer umgekehrten `map` auf dieselbe Weise wie [begin](#begin) bei einer `map` verwendet.

Bei dem Rückgabewert von `crbegin` kann das `map`-Objekt nicht geändert werden

Mit `crbegin` lässt sich eine `map` rückwärts durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// map_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
```

## <a name="crend"></a>crend

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der auf das letzte Element einer umgekehrten Zuordnung folgt.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const_reverse-Iterator, der den Standort anspricht, der dem letzten Element in einer umgekehrten [map](../standard-library/map-class.md) nachfolgt (der Speicherort, der dem ersten Element in der nicht umgekehrten `map` vorangegangen war).

### <a name="remarks"></a>Hinweise

`crend` wird bei einer umgekehrten Zuordnung auf die gleiche Weise verwendet, wie [end](#end) bei einer `map` verwendet wird.

Bei dem Rückgabewert von `crend` kann das `map`-Objekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob das Ende der `map` von einem umgekehrten Iterator erreicht wurde.

Der von `crend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// map_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
```

## <a name="difference_type"></a>difference_type

Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen einer Zuordnung in einem Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Hinweise

`difference_type` ist der Typ, der beim Subtrahieren oder Inkrementieren über Iteratoren des Containers zurückgegeben wird. `difference_type` wird normalerweise verwendet, um die Anzahl von Elementen im Bereich *(first, last)* zwischen den Iteratoren `first` und `last` darzustellen. Dazu gehört das Element, auf das durch `first` gezeigt wird und der Bereich von Elementen bis zu (aber nicht einschließlich) dem Element, auf das durch `last` gezeigt wird.

Bitte beachten Sie, dass die Subtraktion zwischen Iteratoren nur von Iteratoren mit zufälligem Zugriff unterstützt wird, die über einen Container mit zufälligem Zugriff wie „vector“ bereitgestellt werden. Dies gilt, obwohl `difference_type` für alle Iteratoren verfügbar ist, die die Anforderungen eines Eingabeiterators erfüllen. Hierzu zählt auch die Klasse bidirektionaler Iteratoren, die von umkehrbaren Containern wie „set“ unterstützt wird.

### <a name="example"></a>Beispiel

```cpp
// map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 2, 30 ) );

   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a map
   map <int, int>::difference_type  df_count = 1;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter)
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the map m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the map m1 is: 4.
```

## <a name="emplace"></a>emplace

Es wird ein Element eingefügt, das vor Ort in eine Zuordnung konstruiert wird (keine Kopieren- oder Verschiebevorgänge werden ausgeführt).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parameter

*args*\
Die Argumente, die zum Erstellen eines in die Zuordnung einzufügenden Elements weitergeleitet werden, es sei denn, es ist bereits ein Element enthalten, dessen Wert gleichwertig sortiert wird.

### <a name="return-value"></a>Rückgabewert

Ein [paar](../standard-library/pair-structure.md) , dessen **boolesche** Komponente true ist, wenn eine Einfügung erfolgt ist, und false, wenn die Zuordnung bereits ein Element eines äquivalenten Werts in der Reihenfolge enthielt. Die iteratorkomponente des Rückgabewert Paars zeigt auf das neu eingefügte Element, wenn die **boolesche** Komponente true ist, oder auf das vorhandene Element, wenn die **boolesche** Komponente false ist.

Um auf die iteratorkomponente eines `pair` `pr`zuzugreifen, verwenden Sie `pr.first`; Verwenden Sie `*pr.first`, um ihn zu dereferenzieren. Um auf die **boolesche** Komponente zuzugreifen, verwenden Sie `pr.second`. Eine Beispiel finden Sie unter Beispielcode weiter unten in diesem Artikel.

### <a name="remarks"></a>Hinweise

Durch diese Funktion werden keine Iteratoren oder Verweise ungültig.

Wird während des Einbaus eine Ausnahme ausgelöst, wird der Zustand des Containers nicht geändert.

Der [value_type](#value_type) eines Elements wird paarweise angegeben, damit der Wert eines Elements ein geordnetes Paar ist, bei dem die erste Komponente und der Schlüsselwert sowie die zweite Komponente und der Datenwert des Elements jeweils identisch sind.

### <a name="example"></a>Beispiel

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    map<int, string> m1;

    auto ret = m1.emplace(10, "ten");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
        cout << "map not modified" << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;

    ret = m1.emplace(10, "one zero");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a>emplace_hint

Fügt ein Element mit einem Platzierungshinweis ein, das vor Ort erstellt wird (Es werden keine Kopier- oder Verschiebevorgänge ausgeführt).

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parameter

*args*\
Die zum Erstellen eines in die Zuordnung einzufügenden Elements weitergeleiteten Argumente, es sei denn, die Zuordnung enthält dieses Element bereits, oder üblicher, es sei denn ein Element, dessen Schlüssel gleichwertig sortiert wird, ist bereits enthalten.

*Where*\
Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Wenn dieser Punkt unmittelbar vor *dem*Speicherort von liegt, kann die Einfügung in amortisierter konstanter Zeit anstelle der logarithmischen Zeit erfolgen.)

### <a name="return-value"></a>Rückgabewert

Ein Iterator zum neu eingefügten Element.

Wenn die Einfügung fehlerhaft war, da das Element bereits vorhanden ist, wird ein Iterator an das vorhandene Element mit dem Schlüssel zurückgegeben.

### <a name="remarks"></a>Hinweise

Durch diese Funktion werden keine Iteratoren oder Verweise ungültig.

Wird während des Einbaus eine Ausnahme ausgelöst, wird der Zustand des Containers nicht geändert.

Der [value_type](#value_type) eines Elements wird paarweise angegeben, damit der Wert eines Elements ein geordnetes Paar ist, bei dem die erste Komponente und der Schlüsselwert sowie die zweite Komponente und der Datenwert des Elements jeweils identisch sind.

### <a name="example"></a>Beispiel

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    map<string, string> m1;

    // Emplace some test data
    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "map starting data: ";
    print(m1);
    cout << endl;

    // Emplace with hint
    // m1.end() should be the "next" element after this emplacement
    m1.emplace_hint(m1.end(), "Doug", "Engineering");

    cout << "map modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="empty"></a>leer

Prüft, ob eine Zuordnung leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Zuordnung leer ist; **FALSE**, wenn sie nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// map_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The map m1 is empty." << endl;
   else
      cout << "The map m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The map m2 is empty." << endl;
   else
      cout << "The map m2 is not empty." << endl;
}
```

```Output
The map m1 is not empty.
The map m2 is empty.
```

## <a name="end"></a>Schließlich

Gibt den "past-the-end"-Iterator zurück.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Rückgabewert

Der "past-the-end"-Iterator. Wenn die Zuordnung leer ist, dann gilt `map::end() == map::begin()`.

### <a name="remarks"></a>Hinweise

`end` wird verwendet, um zu testen, ob ein Iterator das Ende seiner Karte überschritten hat.

Der von `end` zurückgegebene Wert darf nicht dereferenziert werden.

Ein Codebeispiel finden Sie unter [map::find](#find).

## <a name="equal_range"></a>equal_range

Gibt ein Iteratorenpaar zurück,das sowohl das [lower_bound](#lower_bound) als auch das [upper_bound](#upper_bound) des Schlüssels repräsentiert.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüsselwert, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden Zuordnung verglichen wird.

### <a name="return-value"></a>Rückgabewert

Sie können auf den ersten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **first** verwenden, und Sie können einen lower_bound-Iterator dereferenzieren, indem Sie \*( `pr`. **first**) verwenden. Sie können auf den zweiten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **second** verwenden, und Sie können einen upper_bound-Iterator dereferenzieren, indem Sie \*( `pr`. **second**) verwenden.

### <a name="example"></a>Beispiel

```cpp
// map_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef map <int, int, less<int> > IntMap;
   IntMap m1;
   map <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The map m1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of map m1 with a key >= 40 is: "
           << p2.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the map m1 is: 20.
The upper bound of the element with a key of 2 in the map m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The map m1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>Löschen

Es wird ein Element oder ein Bereich von Elementen in einer Zuordnung von angegebenen Speicherorten entfernt oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>Parameter

*Where*\
Die Position des zu entfernenden Elements.

*Erste*\
Die Position des ersten zu entfernenden Elements.

*Letzter*\
Die Position direkt hinter dem letzten zu entfernenden Element.

*Schlüssel*\
Der Schlüsselwert der zu entfernenden Elemente.

### <a name="return-value"></a>Rückgabewert

Bei den ersten beiden Memberfunktionen ist es ein bidirektionaler Iterator, der das erste über die entfernten Elemente hinaus verbliebe Element festlegt, oder ein Element, das das Ende der Zuordnung darstellt, wenn kein solches Element vorhanden ist.

Für die dritte Memberfunktion wird die Anzahl der von der Zuordnung entfernten Elemente zurück gegeben.

### <a name="example"></a>Beispiel

```cpp
// map_erase.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions
#include <utility>  // make_pair()

using namespace std;

using mymap = map<int, string>;

void printmap(const mymap& m) {
    for (const auto& elem : m) {
        cout << " [" << elem.first << ", " << elem.second << "]";
    }
    cout << endl << "size() == " << m.size() << endl << endl;
}

int main()
{
    mymap m1;

    // Fill in some data to test with, one at a time
    m1.insert(make_pair(1, "A"));
    m1.insert(make_pair(2, "B"));
    m1.insert(make_pair(3, "C"));
    m1.insert(make_pair(4, "D"));
    m1.insert(make_pair(5, "E"));

    cout << "Starting data of map m1 is:" << endl;
    printmap(m1);
    // The 1st member function removes an element at a given position
    m1.erase(next(m1.begin()));
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;
    printmap(m1);

    // Fill in some data to test with, one at a time, using an initializer list
    mymap m2
    {
        { 10, "Bob" },
        { 11, "Rob" },
        { 12, "Robert" },
        { 13, "Bert" },
        { 14, "Bobby" }
    };

    cout << "Starting data of map m2 is:" << endl;
    printmap(m2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    m2.erase(next(m2.begin()), prev(m2.end()));
    cout << "After the middle elements are deleted, the map m2 is:" << endl;
    printmap(m2);

    mymap m3;

    // Fill in some data to test with, one at a time, using emplace
    m3.emplace(1, "red");
    m3.emplace(2, "yellow");
    m3.emplace(3, "blue");
    m3.emplace(4, "green");
    m3.emplace(5, "orange");
    m3.emplace(6, "purple");
    m3.emplace(7, "pink");

    cout << "Starting data of map m3 is:" << endl;
    printmap(m3);
    // The 3rd member function removes elements with a given Key
    mymap::size_type count = m3.erase(2);
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from m3 is: " << count << "." << endl;
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;
    printmap(m3);
}
```

## <a name="find"></a>sich

Gibt einen Iterator zurück, der auf den Speicherort eines Elements in einer Zuordnung verweist, der einen Schlüssel gleich einem angegebenen Schlüssel aufweist.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Schlüsselwert, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden Zuordnung übereinstimmt.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Speicherort eines Elements mit einem angegebenen Schlüssel verweist, oder der Speicherort, der dem letzten Element in der Zuordnung (`map::end()`) nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt einen Iterator zurück, der auf ein Element in der Zuordnung verweist, dessen Sortierschlüssel dem Argumentschlüssel unter einem binären Prädikat entspricht, das eine Reihenfolge basierend auf der Beziehung „Less than comparability“ auslöst.

Wenn der Rückgabewert von `find` einem `const_iterator` zugewiesen wird, kann das map-Objekt nicht geändert werden. Wenn der Rückgabewert von `find` einem `iterator`zugewiesen wird, kann das Map-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting map m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified map m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="get_allocator"></a>get_allocator

Gibt eine Kopie des allocator-Objekts zurück, das zum Erstellen der Zuordnung verwendet wird.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zuweisung, die von der Zuordnung verwendet wird.

### <a name="remarks"></a>Hinweise

Zuweisungen für die map-Klasse geben an, wie die Klasse einen Speicher verwaltet. Für die meisten Programmieranforderungen genügen die standardmäßigen Zuweisungen mit Containerklassen der C++-Standardbibliothek. Schreiben und Verwenden Ihrer eigener Zuweisungsklasse ist ein C++ -Thema für Fortgeschrittene.

### <a name="example"></a>Beispiel

```cpp
// map_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int>::allocator_type m1_Alloc;
   map <int, int>::allocator_type m2_Alloc;
   map <int, double>::allocator_type m3_Alloc;
   map <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   map <int, int> m1;
   map <int, int, allocator<int> > m2;
   map <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated\n"
        << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated\n"
        << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a map m4
   // with the allocator of map m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable." << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable." << endl;
   }
}
```

## <a name="insert"></a>setze

Fügt ein Element oder einen Elementbereich in eine Zuordnung ein.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parameter

*Val* -\
Der Wert eines in die Zuordnung einzufügenden Elements, es sei denn, es ist bereits ein Element enthalten, dessen Schlüssel gleichwertig sortiert wird.

*Where*\
Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Wenn dieser Punkt unmittelbar vor *dem*Speicherort von liegt, kann die Einfügung in amortisierter konstanter Zeit anstelle der logarithmischen Zeit erfolgen.)

*Valty* -\
Ein Vorlagen Parameter, der den Argumenttyp angibt, der von der Zuordnung verwendet werden kann, um ein Element [value_type](#value_type)zu erstellen, und das *Val* perfekt als Argument weiterleitet.

*Erste*\
Die Position des ersten zu kopierenden Elements.

*Letzter*\
Die Position direkt über den letzten zu kopierenden Elements.

*InputIterator* -\
Das Vorlagenfunktionsargument, das den Anforderungen eines [Eingabeiterators](../standard-library/input-iterator-tag-struct.md) erfüllt, der auf Elemente eines Typs zeigt, der zum Erstellen von [value_type](#value_type)-Objekten verwendet werden kann.

*IList* -\
Das [initializer_list](../standard-library/initializer-list.md)-Element, aus dem die Elemente kopiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Einzelelement-Element Funktionen (1) und (2) geben ein [paar](../standard-library/pair-structure.md) zurück, dessen **boolesche** Komponente true ist, wenn eine Einfügung erfolgt ist, und false, wenn die Zuordnung bereits ein Element enthielt, dessen Schlüssel einen entsprechenden Wert in der Reihenfolge enthielt. Die iteratorkomponente des Rückgabewert Paars zeigt auf das neu eingefügte Element, wenn die **boolesche** Komponente true ist, oder auf das vorhandene Element, wenn die **boolesche** Komponente false ist.

Die Einzelelement-Memberfunktionen mit Hinweis (3) und (4) geben einen Iterator zurück, der auf die Position zeigt, an der das neue Element in die Zuordnung eingefügt wurde, oder, falls ein Element mit einem entsprechenden Schlüssel bereits vorhanden ist, auf das vorhandene Element.

### <a name="remarks"></a>Hinweise

Durch diese Funktion werden keine Iteratoren, Zeiger oder Verweise ungültig.

Wird beim Einfügen von nur einem Element eine Ausnahme ausgelöst, wird der Zustand des Containers nicht geändert. Wird beim Einfügen mehrerer Elementen eine Ausnahme ausgelöst, wird der Container in einem nicht angegebenen doch gültigen Zustand belassen.

Um auf die iteratorkomponente einer `pair` `pr` zuzugreifen, die von den Elementen mit einem Element zurückgegeben wird, verwenden Sie `pr.first`; um den Iterator innerhalb des zurückgegebenen Paars zu dereferenzieren, verwenden Sie `*pr.first`, und geben Sie ein Element an. Um auf die **boolesche** Komponente zuzugreifen, verwenden Sie `pr.second`. Eine Beispiel finden Sie unter Beispielcode weiter unten in diesem Artikel.

Das [value_type](#value_type)-Element eines Containers ist eine Typedef, die dem Container angehört; für die map ist `map<K, V>::value_type``pair<const K, V>`. Der Wert eines Elements ist ein sortiertes Paar, in dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

Die Bereichsmemberfunktion (5) fügt die Sequenz von Elementwerten in eine Zuordnung ein, die jedem Element entspricht, das von einem Iterator im Bereich `[First, Last)` adressiert wird. Daher wird `Last` nicht eingefügt. Die Containermemberfunktion `end()` bezieht sich auf die Position direkt hinter dem letzten Element im Container. Z. B versucht die Anweisung `m.insert(v.begin(), v.end());` alle Elemente von `v` in `m` einzufügen. Nur Elemente, die eindeutige Werte im Bereich aufweisen werden eingefügt. Duplikate werden ignoriert. Um zu betrachten welche Elemente abgelehnt werden, verwenden Sie die Einzelelementversionen von `insert`.

Die Memberfunktion (6) der Initialisiererliste verwendet ein [initializer_list](../standard-library/initializer-list.md)-Element, um Elemente in die Zuordnung zu kopieren.

Informationen zum Einfügen eines lokal erstellten Elements (d.h. wenn keine Kopier- oder Verschiebevorgänge ausgeführt werden) finden Sie unter [map::emplace](#emplace) und [map::emplace_hint](#emplace_hint).

### <a name="example"></a>Beispiel

```cpp
// map_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    map<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    auto ret = m1.insert(make_pair(1, 111));
    if (!ret.second){
        auto pr = *ret.first;
        cout << "Insert failed, element with key value 1 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "The modified key and mapped values of m1 are:" << endl;
        print(m1);
    }
    cout << endl;

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    map<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    map<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    map<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="iterator"></a>Iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einer Zuordnung gelesen oder geändert werden kann.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Hinweise

Der durch Map definierte Iterator zeigt auf Elemente, bei denen es sich um Objekte [value_type](#value_type)handelt, die vom Typ `pair<const Key, Type>`sind, dessen erster Member der Schlüssel zum Element und dessen zweiter Member das zugeordnete Datum ist, das vom Element gehalten wird.

Verwenden Sie den `->`-Operator, um einen *iteratorIter* zu dereferenzieren, der auf ein Element in einer Zuordnung zeigt.

Um auf den Wert des Schlüssels für das Element zuzugreifen, verwenden Sie `Iter->first`, das `(*Iter).first`entspricht. Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `Iter->second`, das `(*Iter).second`entspricht.

### <a name="example"></a>Beispiel

Ein Beispiel für das Deklarieren und Verwenden von `iterator`finden Sie unter Beispiel für [Begin](#begin) .

## <a name="key_comp"></a>key_comp

Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in einer Zuordnung verwendet wird.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Funktionsobjekt zurück, das eine Zuordnung zum Sortieren ihrer Elemente verwendet.

### <a name="remarks"></a>Hinweise

Das gespeicherte Objekt definiert die Memberfunktion

`bool operator(const Key& left, const Key& right);`

die **TRUE** zurückgibt, wenn `left` vorangestellt ist und nicht gleich `right` in der Sortierreihenfolge ist.

### <a name="example"></a>Beispiel

```cpp
// map_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   map <int, int, greater<int> > m2;
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a>key_compare

Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen in der Zuordnung zu bestimmen.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Hinweise

`key_compare` ist ein Synonym für die Vorlagen Parameter *Merkmale*.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [Map-Klasse](../standard-library/map-class.md) .

### <a name="example"></a>Beispiel

Im Beispiel für [key_comp](#key_comp) wird verdeutlicht, wie ein `key_compare` deklariert und verwendet wird.

## <a name="key_type"></a>key_type

Eine Typ, der den in jedem Element der Zuordnung gespeicherten Sortierschlüssel beschreibt.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Hinweise

`key_type` ist ein Synonym für den Vorlagen Parameter *Schlüssel*.

Weitere Informationen zu *Key*finden Sie im Abschnitt "Hinweise" des Themas [map Class](../standard-library/map-class.md) .

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie ein `key_type` deklariert und verwendet wird.

## <a name="lower_bound"></a>lower_bound

Gibt einen Iterator zum ersten Element in einer Zuordnung mit einem Schlüsselwert zurück, der gleich oder größer ist, als ein angegebener Schlüssel.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüsselwert, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden Zuordnung verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein `iterator` oder `const_iterator`, der den Speicherort eines Elements in einer Zuordnung adressiert, der einen Schlüssel hat, der gleich oder größer als der Argument Schlüssel ist, oder der den Speicherort adressiert, der dem letzten Element in der Zuordnung nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

Wenn der Rückgabewert von `lower_bound` einem `const_iterator` zugewiesen wird, kann das map-Objekt nicht geändert werden. Wenn der Rückgabewert von `lower_bound` einem `iterator`zugewiesen wird, kann das Map-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// map_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The first element of map m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for this key, end( ) is returned
   m1_RcIter = m1. lower_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of map m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );
   cout << "The element of m1 with a key matching "
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key of 2 is: 20.
The map m1 doesn't have an element with a key of 4.
The element of m1 with a key matching that of the last element is: 30.
```

## <a name="map"></a>bilden

Erstellt eine Zuordnung, die leer oder die Kopie einer vollständigen anderen Zuordnung oder eines Teils davon ist.

```cpp
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,
    const Traits& Comp);

map(
    initializer_list<value_type> IList,
    const Traits& Comp,
    const Allocator& Allocator);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parameter

*Al* -\
Die für dieses Zuordnungsobjekt zu verwendende Speicherzuweisungsklasse, dessen Standard `Allocator` ist.

*Comp*\
Die Vergleichsfunktion vom Typ `const Traits`, die verwendet wird, um die Elemente in der Zuordnung zu sortieren, deren Standard `hash_compare` ist.

*Rechte*\
Die Zuordnung, deren Kopie der erstellte Satz sein soll.

*Erste*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*Letzter*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*IList* -\
Das initializer_list-Element, von dem die Elemente kopiert werden sollen.

### <a name="remarks"></a>Hinweise

In allen Konstruktoren wird ein Zuweisungsobjekttyp gespeichert, mit dem der Arbeitsspeicher für die Zuordnung verwaltet wird, und das später zurückgegeben werden kann, indem [get_allocator](#get_allocator) aufgerufen wird. Der Zuweisungsparameter wird häufig aus den Klassendeklarationen und den Vorverarbeitungsmakros weggelassen, die zum Ersetzen alternativer Zuweisungen verwendet werden.

Alle Konstruktoren initialisieren die Zuordnung.

In allen Konstruktoren wird ein Funktionsobjekt vom Typ „Traits“ gespeichert, das verwendet wird, um unter den Schlüsseln der Zuordnung eine Sortierung vorzunehmen, und das später zurückgegeben werden kann, indem [key_comp](#key_comp) aufgerufen wird.

Die ersten drei Konstruktoren geben eine leere ursprüngliche Zuordnung an, wobei die zweite den Typ der Vergleichsfunktion (*Comp*) angibt, die zum Festlegen der Reihenfolge der Elemente verwendet werden soll, und der dritte explizit den zu verwendenden zuordnertyp (*Al*) angibt. Das **Schlüsselwort unterdrückt bestimmte** Arten automatischer Typkonvertierung.

Der vierte Konstruktor gibt eine Kopie der Zuordnungs *rechten*an.

Der fünfte Konstruktor gibt eine Kopie der Zuordnung an, indem nach *Rechts*verschoben wird.

Der sechste, siebte und achte Konstruktor verwendet ein initializer_list-Element, aus dem die Member kopiert werden.

Mit den nächsten drei Konstruktoren wird der `[First, Last)`-Bereich, einer Zuordnung kopiert, wobei sich die Explizitheit bei Angabe des Typs der Vergleichsfunktion der Klasse `Traits` und "Allocator" erhöht.

### <a name="example"></a>Beispiel

```cpp
// map_map.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;
    map <int, int, less<int> >::iterator m2_Iter;

    // Create an empty map m0 of key type integer
    map <int, int> m0;

    // Create an empty map m1 with the key comparison
    // function of less than, then insert 4 elements
    map <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty map m2 with the key comparison
    // function of greater than, then insert 2 elements
    map <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a map m3 with the
    // allocator of map m1
    map <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    map <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, map m4, of map m1
    map <int, int> m4(m1);

    // Create a map m5 by copying the range m1[ first,  last)
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    map <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a map m6 by copying the range m4[ first,  last)
    // and with the allocator of map m2
    map <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for(auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m7 by moving m5
    cout << "m7 =";
    map<int, int> m7(move(m5));
    for (auto i : m7)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m8 by copying in an initializer_list
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m9 with an initializer_list and a comparator
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m10 with an initializer_list, a comparator, and an allocator
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;
}
```

## <a name="mapped_type"></a>mapped_type

Ein Typ, der die in einer Zuordnung gespeicherten Daten darstellt.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Hinweise

Der Typ `mapped_type` ist ein Synonym für den *typvorlagen* Parameter der Klasse.

Weitere Informationen zum *Typ* finden Sie im Thema [map Class](../standard-library/map-class.md) .

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie ein `mapped_type` deklariert und verwendet wird.

## <a name="max_size"></a>max_size

Gibt die Maximallänge der Zuordnung zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die mögliche Maximallänge der Zuordnung.

### <a name="example"></a>Beispiel

```cpp
// map_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="op_at"></a>[]-Operator

Fügt ein Element in eine Zuordnung mit einem angegebenen Schlüsselwert ein.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Schlüsselwert des einzufügenden Elements.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf den Datenwert des eingefügten Elements.

### <a name="remarks"></a>Hinweise

Wenn der Argumentschlüsselwert nicht gefunden wird, wird er zusammen mit dem Standardwert des Datentyps eingefügt.

`operator[]` können zum Einfügen von Elementen in eine Zuordnung `m` mithilfe von `m[key] = DataValue;` verwendet werden, wobei `DataValue` der Wert des `mapped_type` des Elements mit dem Schlüsselwert *Key*ist.

Wenn `operator[]` zum Einfügen von Elementen verwendet wird, gibt der zurückgegebene Verweis nicht an, ob eine Einfügung ein bereits vorhandenes Element ändert oder ein neues erstellt. Die Memberfunktionen [find](#find) und [insert](#insert) können verwendet werden, um zu bestimmen, ob ein Element mit einem bestimmten Schlüssel vor einer Einfügung bereits vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// map_op_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a map using the operator[] member function
   m1[ 1 ] = 10;

   // Compare other ways to insert objects into a map
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );
   m1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   m1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   m1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

// insert by moving key
    map<string, int> c2;
    string str("abc");
    cout << "c2[move(str)] == " << c2[move(str)] << endl;
    cout << "c2["abc"] == " << c2["abc"] << endl;

    return (0);
}
```

```Output
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
The keys of the mapped elements are now: 1 2 3 5.
The values of the mapped elements are now: 10 40 30 0.
c2[move(str)] == 0
c2["abc"] == 1
```

## <a name="op_eq"></a>Operator =

Ersetzt die Elemente einer Zuordnung durch einer Kopie einer anderen Zuordnung.

```cpp
map& operator=(const map& right);
map& operator=(map&& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Die [Zuordnung](../standard-library/map-class.md), die in die `map` kopiert wird.

### <a name="remarks"></a>Hinweise

Nachdem alle vorhandenen Elemente in einem `map`gelöscht wurden, `operator=` entweder kopiert oder verschiebt den Inhalt von *right* in die Karte.

### <a name="example"></a>Beispiel

```cpp
// map_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   map<int, int> v1, v2, v3;
   map<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="pointer"></a>Zeichner

Ein Typ, der einen Zeiger auf ein Element in einer Zuordnung bereitstellt.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Hinweise

Ein Type-`pointer` kann verwendet werden, um den Wert eines Elements zu ändern.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem map-Objekt verwendet werden.

## <a name="rbegin"></a>rbegin

Gibt einen Iterator zurück, der das erste Element in einer umgekehrten Zuordnung adressiert.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der auf das erste Element in einer umgekehrten map oder auf das letzte Element der vormals nicht umgekehrten map verweist.

### <a name="remarks"></a>Hinweise

`rbegin` wird bei einer umgekehrten Zuordnung auf die gleiche Weise verwendet, wie [begin](#begin) bei einer Zuordnung verwendet wird.

Wenn der Rückgabewert von `rbegin` einem `const_reverse_iterator` zugewiesen wird, kann das map-Objekt nicht geändert werden. Wenn der Rückgabewert von `rbegin` einem `reverse_iterator` zugewiesen wird, kann das map-Objekt geändert werden.

`rbegin` kann verwendet werden, um eine Zuordnung rückwärts zu durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// map_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the first element in the reversed map is 2.
```

## <a name="reference"></a>Angabe

Ein Typ, der einen Verweis auf ein in einer Zuordnung gespeichertes Element bereitstellt.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Beispiel

```cpp
// map_reference.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>rend

Gibt einen Iterator zurück, der den Speicherort adressiert, der auf das letzte Element einer umgekehrten Zuordnung folgt.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der den Standort anspricht, der dem letzten Element in einer umgekehrten Zuordnung nachfolgt (der Speicherort, der dem ersten Element in der nicht umgekehrten Zuordnung vorangegangen war).

### <a name="remarks"></a>Hinweise

`rend` wird bei einer umgekehrten Zuordnung auf die gleiche Weise verwendet, wie [end](#end) bei einer Zuordnung verwendet wird.

Wenn der Rückgabewert von `rend` einem `const_reverse_iterator` zugewiesen wird, kann das map-Objekt nicht geändert werden. Wenn der Rückgabewert von `rend` einem `reverse_iterator` zugewiesen wird, kann das map-Objekt geändert werden.

`rend` kann verwendet werden, um zu testen, ob das Ende der Zuordnung von einem umgekehrten Iterator erreicht wurde.

Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// map_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the last element in the reversed map is 2.
```

## <a name="reverse_iterator"></a>reverse_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einer umgekehrten Zuordnung gelesen oder geändert werden kann.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Hinweise

Ein `reverse_iterator`-Typ kann nicht den Wert eines Elements ändern und wird verwendet, um die Zuordnung in umgekehrter Reihenfolge zu durchlaufen.

Der von Map definierte `reverse_iterator` verweist auf Elemente, die Objekte [value_type](#value_type)sind, die vom Typ `pair<const Key, Type>`sind, dessen erster Member der Schlüssel zum Element und dessen zweiter Member das zugeordnete Datum ist, das vom Element gehalten wird.

Um einen `reverse_iterator` *Riter* zu dereferenzieren, der auf ein Element in einer Zuordnung zeigt, verwenden Sie den `->`-Operator.

Um auf den Wert des Schlüssels für das Element zuzugreifen, verwenden Sie `rIter` -> **First**, das (\* `rIter`) entspricht. **first** entspricht, um auf den Wert des zugeordneten Datums für das Element zuzugreifen. Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `rIter` -> **Sekunde**, das (\* `rIter`) entspricht. **first** entspricht, um auf den Wert des zugeordneten Datums für das Element zuzugreifen.

### <a name="example"></a>Beispiel

Im Beispiel für [rbegin](#rbegin) wird verdeutlicht, wie `reverse_iterator` deklariert und verwendet wird.

## <a name="size"></a>Größe

Gibt die Anzahl von Elementen in der Zuordnung zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge der Zuordnung.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion „map::size“ gezeigt.

```cpp
// map_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1, m2;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The map length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The map length is now " << i << "." << endl;
}
```

```Output
The map length is 1.
The map length is now 2.
```

## <a name="size_type"></a>size_type

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einer Zuordnung darstellen kann.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Beispiel

Im Beispiel für [size](#size) wird verdeutlicht, wie `size_type` deklariert und verwendet wird.

## <a name="swap"></a>Wechsel

Tauscht die Elemente zweier Zuordnungen aus.

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Das map-Argument, das die Elemente bereitstellt, mit denen die Zielzuordnung getauscht werden soll.

### <a name="remarks"></a>Hinweise

Die Memberfunktion macht keine Verweise, Zeiger oder Iteratoren ungültig, die Elemente in den zwei Zuordnungen bezeichnen, deren Elemente ausgetauscht werden sollen.

### <a name="example"></a>Beispiel

```cpp
// map_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   map <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   //m2 is said to be the argument map; m1 the target map
   m1.swap( m2 );

   cout << "After swapping with m2, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original map m1 is: 10 20 30.
After swapping with m2, map m1 is: 100 200.
After swapping with m3, map m1 is: 300.
```

## <a name="upper_bound"></a>upper_bound

Gibt einen Iterator zum ersten Element in einer Zuordnung mit einem Schlüsselwert zurück, der größer ist als ein angegebener Schlüssel.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüsselwert, der mit dem Sortierschlüsselwert eines Elements aus der zu durchsuchenden Zuordnung verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein `iterator` oder `const_iterator`, der den Speicherort eines Elements in einer Zuordnung adressiert, der einen Schlüssel hat, der größer als der Argument Schlüssel ist, oder der den Speicherort adressiert, der dem letzten Element in der Zuordnung nachfolgt, wenn keine Entsprechung für den Schlüssel gefunden wird.

Wenn der Rückgabewert einem `const_iterator` zugewiesen wird, kann das map-Objekt nicht geändert werden. Wenn der Rückgabewert einem `iterator`zugewiesen wird, kann das Map-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// map_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of map m1 with a key "
        << "greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   m1_RcIter = m1. upper_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of map m1 with a key > 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );
   cout << "The 1st element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key greater than 2 is: 30.
The map m1 doesn't have an element with a key greater than 4.
The 1st element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>value_comp

Die Memberfunktion gibt ein Funktionsobjekt zurück, das die Reihenfolge der Elemente in einer Zuordnung bestimmt, indem ihre Schlüsselwerte verglichen werden.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Vergleichsfunktionsobjekt zurück, das ein map-Element zum Sortieren seiner Elemente verwendet.

### <a name="remarks"></a>Hinweise

Wenn für eine Karte *m*die zwei Elemente *E1*(*K1*, *D1*) und *E2*(*K2*, *D2*) Objekte vom Typ `value_type`sind, wobei *K1* und *K1* Ihre Schlüssel vom Typ sind `key_type` und *D1* und *D2* Ihre Daten vom Typ `mapped_type`sind, entspricht `m.value_comp(e1, e2)` `m.key_comp(k1, k2)`. Ein gespeichertes Objekt definiert die Memberfunktion

`bool operator( value_type& left, value_type& right);`

die **TRUE** zurückgibt, wenn der Schlüsselwert von `left` vorangestellt ist und nicht dem Schlüsselwert von `right` in der Sortierreihenfolge entspricht.

### <a name="example"></a>Beispiel

```cpp
// map_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   pair< map<int,int>::iterator, bool > pr1, pr2;

   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if(vc1( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>value_type

Der Typ des Objekts, der als Element in einer Zuordnung gespeichert wird.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Beispiel

```cpp
// map_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: key_type key1;
   map <int, int> :: mapped_type mapped1;
   map <int, int> :: value_type value1;
   map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a map
   m1.insert ( cInt2Int ( 2, 20 ) );
   m1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the map is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

## <a name="see-also"></a>Siehe auch

[Containers (Container)](../cpp/containers-modern-cpp.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
