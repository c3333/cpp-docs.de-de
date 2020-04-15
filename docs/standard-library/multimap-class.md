---
title: multimap-Klasse
ms.date: 10/18/2018
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
ms.openlocfilehash: 2f6ae50a825d6eff2eb64c84b209fa81c4b7949f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363856"
---
# <a name="multimap-class"></a>multimap-Klasse

Die Mehrfachzuordnungsklasse der C++-Standardbibliothek wird zum Speichern und Abrufen von Daten aus Auflistungen verwendet, in denen es sich bei jedem Element um ein Paar mit einem Datenwert und einem Sortierschlüssel handelt. Der Wert der Schlüssel muss nicht eindeutig sein und wird verwendet, um die Daten automatisch zu sortieren. Der Wert eines Elements in einer Mehrfachzuordnung, aber nicht der zugehörige Schlüsselwert, wird möglicherweise direkt geändert. Stattdessen müssen die Schlüsselwerte, die alten Elementen zugeordnet sind, gelöscht, und stattdessen neuen Schlüsselwerten für neue Elemente zugeordnet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der in der Mehrfachzuordnung zu speichernde Schlüsseldatentyp.

*Typ*\
Der in der Mehrfachzuordnung zu speichernde Elementdatentyp.

*Merkmale*\
Der Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Mehrfachzuordnung zu bestimmen. Das binäre Prädikat `less<Key>` ist der Standardwert.

In C ++ 14 können Sie heterogenes Nachschlagen durch Angabe des `std::less<>` oder `std::greater<>` Prädikats, das keine Typparameter aufweist, aktivieren. Weitere Informationen finden Sie unter [Heterogenes Nachschlagen in assoziativen Containern](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14).

*Zuweisung*\
Der Typ, der das gespeicherte Zuordnungsobjekt darstellt, das Details zum Belegen und Freigeben des Arbeitsspeichers der Zuordnung kapselt. Dieses Argument ist optional, und der Standardwert ist `allocator<pair <const Key, Type> >`.

## <a name="remarks"></a>Bemerkungen

Auf die Mehrfachzuordnungsklasse der C++-Standardbibliothek treffen die folgenden Punkte zu:

- Ein assoziativer Container, der ein Container variabler Größe ist, der den effizienten Abruf von Elementwerten auf Grundlage eines zugeordneten Schlüsselwert unterstützt.

- Umkehrbar, da bidirektionale Iteratoren für den Zugriff auf die Elemente bereitgestellt werden.

- Sortiert, da die Elemente anhand von Schlüsselwerten innerhalb des Containers mit einer angegebenen Vergleichsfunktion sortiert werden.

- Mehrfach, da die Elemente keine eindeutige Schlüssel aufweisen müssen, damit ein Schlüsselwert über viele zugeordnete Elementdatenwerte verfügen kann.

- Ein Paar assoziativer Container, da sich die Elementdatenwerte von den Schlüsselwerten unterscheiden.

- Eine Klassenvorlage, da die bereitgestellte Funktionalität generisch ist und daher unabhängig vom spezifischen Datentyp ist, der als Elemente oder Schlüssel enthalten ist. Die für Elemente und Schlüssel zu verwendenden Datentypen werden stattdessen in der Klassenvorlage zusammen mit der Vergleichsfunktion und der Zuweisung als Parameter angegeben.

Der von der Zuordnungsklasse bereitgestellte Iterator ist bidirektional. Die Klassenmemberfunktionen [insert](#insert) und [multimap](#multimap) weisen jedoch Versionen auf, die einen abgeschwächten Eingabeiterator als Vorlagenparameter akzeptieren. Die Funktionalitätsanforderungen dieses Eingabeiterators sind weniger umfangreich als die Anforderungen, die von der Klasse bidirektionaler Iteratoren gewährleistet werden. Die verschiedenen Iteratorkonzepte bilden eine Family, die durch Verfeinerungen in ihrer Funktionen verknüpft ist. Jedes Iteratorkonzept weist einen eigenen Satz von Anforderungen auf, und die damit funktionierenden Algorithmen müssen die Annahmen hinsichtlich der von diesem Iteratortyp bereitgestellten Anforderungen begrenzen. Es kann davon ausgegangen werden, dass ein Eingabeiterator möglicherweise so dereferenziert wird, dass er auf ein Objekt verweist und dieses möglicherweise zum folgenden Iterator in der Sequenz erhöht. Das ist ein minimaler Funktionssatz, allerdings genügt er, um sinnvoll über einen Bereich von `[First, Last)`-Iteratoren im Kontext der Klassenmemberfunktionen zu sprechen.

Die Auswahl des Containertyps sollte im Allgemeinen auf Grundlage des für die Anwendung erforderlichen Suchen und Einfügetyps erfolgen. Assoziative Container sind für Such-, Einfüge- und Entfernvorgänge optimiert. Die Memberfunktionen, die diese Vorgänge explizit unterstützen, sind effizient und führen sie in einer Zeit aus, die zum Logarithmus der Elementanzahl im Container im Durchschnitt proportional ist. Das Einfügen von Elementen führt nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen von Elementen werden nur solche Iteratoren ungültig, die speziell auf die entfernten Elemente gezeigt haben.

Die Mehrfachzuordnung sollte der ausgewählte assoziative Container sein, wenn die Bedingungen, mit denen die Werte von der Anwendung den Schlüsseln zugeordnet werden, erfüllt werden. Ein Modell für diesen Strukturtyp ist eine sortierte Liste von Schlüsselwörtern mit zugeordneten Zeichenfolgewerten, die, sagen wir, Definitionen bereitstellen, in denen die Wörter nicht immer eindeutig definiert wurden. Wenn die Schlüsselwörter stattdessen eindeutig definiert werden, damit die Schlüssel eindeutig sind, ist eine Zuordnung der gewählte Container. Wenn hingegen nur die Wortliste gespeichert wurde, ist ein Satz der richtige Container. Wenn mehrfaches Vorkommen der Wörter zugelassen wird, ist eine Multimenge die geeignete Containerstruktur.

Die Mehrfachzuordnung sortiert die von ihr gesteuerten Elemente, indem ein gespeichertes Funktionsobjekt des Typs [key_compare](#key_compare) aufgerufen wird. Bei diesem gespeicherten Objekt handelt es sich um eine Vergleichsfunktion, auf die durch Aufrufen der Memberfunktion [key_comp](#key_comp) zugegriffen werden kann. Im Allgemeinen müssen die Elemente der Vorwärtsiteratoren etwas weniger als vergleichbar sein, um diese Sortierung zu erstellen, sodass beliebige zwei Elemente möglicherweise als gleichwertig bestimmt werden (in dem Sinne, dass keins geringer als das Andere ist), oder dass eins geringer als das Andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Etwas technischer betrachtet ist die Vergleichsfunktion ein binäres Prädikat, das eine strenge schwache Sortierung im mathematischen Sinn verursacht. Bei einem binären `f(x,y)`-Prädikat handelt es sich um ein Funktionsobjekt, das die zwei Argumentobjekte `x` und `y` aufweist sowie einen Rückgabewert von "true" oder "false". Eine Sortierung, die bei einem Satz erzeugt wird, ist eine strenge schwache Sortierung, wenn das binäre Prädikat irreflexiv, antisymmetrisch und transitiv ist, und wenn die Äquivalenz transitiv ist; wobei zwei Objekte `x` und `y` so definiert werden, dass sie äquivalent sind, wenn sowohl `f(x,y)` als auch `f(y,x)` "false" ist. Wenn der stärkere Gleichheitszustand zwischen Schlüsseln die Äquivalenz ersetzt, erfolgt die Sortierung total (d. h., alle Elemente werden zueinander sortiert), und die verglichenen Schlüssel sind von den einander nicht mehr zu unterscheiden.

In C ++ 14 können Sie heterogenes Nachschlagen durch Angabe des `std::less<>` oder `std::greater<>` Prädikats, das keine Typparameter aufweist, aktivieren. Weitere Informationen finden Sie unter [Heterogenes Nachschlagen in assoziativen Containern](../standard-library/stl-containers.md#sequence_containers).

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[multimap](#multimap)|Erstellt ein `multimap`-Element, das leer oder die Kopie eines ganzen anderen `multimap`-Elements oder eines Teils davon ist.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[allocator_type](#allocator_type)|Ein Typ, der die `allocator`-Klassentyp für das `multimap`-Objekt darstellt.|
|[const_iterator](#const_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, der ein **const-Element** im lesen `multimap`kann.|
|[const_pointer](#const_pointer)|Ein Typ, der einen Zeiger auf `multimap`ein **const-Element** in einem bereitstellt.|
|[const_reference](#const_reference)|Ein Typ, der einen Verweis auf `multimap` ein **const-Element** bereitstellt, das zum Lesen und Ausführen von **const-Vorgängen** in einem gespeichert ist.|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, der jedes **const-Element** im lesen `multimap`kann.|
|[difference_type](#difference_type)|Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen eines `multimap`-Elements in einen Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.|
|[Iterator](#iterator)|Ein Typ, der den Unterschied zwischen zwei Iteratoren, die auf Elemente innerhalb derselben `multimap` verweisen, bereitstellt.|
|[key_compare](#key_compare)|Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen im `multimap`-Element zu bestimmen.|
|[key_type](#key_type)|Ein Typ, mit dem das Sortierschlüsselobjekt beschrieben wird, das jedes Element von `multimap` bildet.|
|[mapped_type](#mapped_type)|Ein Typ, der den in einer `multimap` gespeicherten Datentyp darstellt.|
|[Zeiger](#pointer)|Ein Typ, der einen Zeiger auf `multimap`ein **const-Element** in einem bereitstellt.|
|[Verweis](#reference)|Ein Typ, der einen Verweis auf ein in einer `multimap` gespeichertes Element bereitstellt.|
|[reverse_iterator](#reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einem umgekehrten `multimap`-Element gelesen oder geändert werden kann.|
|[Size_type](#size_type)|Ein ganzzahliger Typ ohne Vorzeichen, der einen `multimap`Zeiger auf ein **const-Element** in einem bereitstellt.|
|[Value_type](#value_type)|Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Elemente als Sortierschlüssel vergleichen kann, um die relative Position im `multimap`-Element zu bestimmen.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Beginnen](#begin)|Gibt ein Iterator zurück, der das erste Element im `multimap`-Element adressiert.|
|[cbegin](#cbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im `multimap`-Element adressiert.|
|[cend](#cend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines `multimap`-Elements nachfolgt.|
|[Klar](#clear)|Löscht alle Elemente einer `multimap` auf.|
|[count](#count)|Gibt die Anzahl von Elementen in einem `multimap`-Element zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.|
|[crbegin](#crbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im umgekehrten `multimap`-Element adressiert.|
|[crend](#crend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten `multimap`-Elements nachfolgt.|
|[emplace](#emplace)|Fügt ein Element ein, das vor Ort in ein `multimap`-Element erstellt wird.|
|[emplace_hint](#emplace_hint)|Fügt ein Element ein, das vor Ort mit einem Platzierungshinweis in ein `multimap`-Element erstellt wird.|
|[empty](#empty)|Testet, ob ein `multimap`-Element leer ist.|
|[Ende](#end)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element einem `multimap`-Element nachfolgt.|
|[equal_range](#equal_range)|Sucht den Bereich von Elementen, in dem der Schlüssel des Elements einem angegebenen Wert entspricht.|
|[erase](#erase)|Es wird ein Element oder ein Bereich von Elementen in einem `multimap` von angegebenen Speicherorten entfernt, oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.|
|[find](#find)|Gibt einen Iterator zurück, der die erste Position eines Elements in einem `multimap`-Element adressiert, das einen Schlüssel aufweist, der einem angegebenen Schlüssel entspricht.|
|[get_allocator](#get_allocator)|Gibt eine Kopie des zum Erstellen von `allocator` verwendeten `multimap`-Objekts zurück.|
|[Einfügen](#insert)|Fügt ein Element oder einen Elementbereich in ein `multimap`-Element ein.|
|[key_comp](#key_comp)|Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in `multimap` verwendet wird.|
|[lower_bound](#lower_bound)|Gibt einen Iterator zum ersten Element in einem `multimap`-Element mit einem Schlüssel zurück, der gleich oder größer ist als ein angegebener Schlüssel.|
|[Max_size](#max_size)|Gibt die Maximallänge der `multimap` zurück.|
|[rbegin](#rbegin)|Gibt einen Iterator zurück, der das erste Element in einem umgekehrten `multimap`-Element adressiert.|
|[rend](#rend)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten `multimap`-Elements nachfolgt.|
|[Größe](#size)|Gibt die Anzahl von Elementen in der `multimap` zurück.|
|[swap](#swap)|Tauscht die Elemente zweier `multimap`n.|
|[upper_bound](#upper_bound)|Gibt einen Iterator zum ersten Element in einem `multimap`-Element mit einem Schlüssel zurück, der größer ist als ein angegebener Schlüssel.|
|[value_comp](#value_comp)|Die Memberfunktion gibt ein Funktionsobjekt zurück, das die Reihenfolge der Elemente in einer `multimap` bestimmt, indem ihre Schlüsselwerte verglichen werden.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_eq)|Ersetzt die Elemente eines `multimap`-Elements durch eine Kopie eines anderen `multimap`-Elements.|

## <a name="requirements"></a>Anforderungen

**Header:** \<map>

**Namespace:** std

Die Paare ( **key**, **value**) werden in einer Mehrfachzuordnung als Objekte des Typs `pair` gespeichert. Die Paarklasse erfordert den Header \<utility>, der durch \<map> automatisch enthalten ist.

## <a name="multimapallocator_type"></a><a name="allocator_type"></a>multimap::allocator_type

Ein Typ, der die Zuweisungsklasse für das multimap-Objekt darstellt.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Beispiel

In dem Beispiel für [get_allocator](#get_allocator) finden Sie ein Beispiel, das `allocator_type` verwendet.

## <a name="multimapbegin"></a><a name="begin"></a>multimap::begin

Gibt einen Iterator zurück, der das erste Element in der Mehrfachzuordnung adressiert.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der das erste Element in der Mehrfachzuordnung oder den auf eine leere Mehrfachzuordnung folgenden Speicherort adressiert.

### <a name="example"></a>Beispiel

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="multimapcbegin"></a><a name="cbegin"></a>multimap::cbegin

Gibt **const** einen const-Iterator zurück, der das erste Element im Bereich adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **const** bidirektionaler Zugriffsiterator, der auf das erste Element des Bereichs oder die Position direkt `cbegin() == cend()`hinter dem Ende eines leeren Bereichs zeigt (für einen leeren Bereich, ).

### <a name="remarks"></a>Bemerkungen

Bei dem Rückgabewert `cbegin` können die Elemente im Bereich nicht geändert werden.

Sie können diese Memberfunktion anstelle der `begin()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. `Container` Betrachten Sie im Beispiel einen veränderbaren (nicht-const) Container `cbegin()`jeder Art, der und unterstützt. **const** `begin()`

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="multimapcend"></a><a name="cend"></a>multimap::cend

Gibt **const** einen const-Iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **const** bidirektionaler Zugriffsiterator, der direkt über das Ende des Bereichs zeigt.

### <a name="remarks"></a>Bemerkungen

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines Bereichs übergeben hat.

Sie können diese Memberfunktion anstelle der `end()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. `Container` Betrachten Sie im Beispiel einen veränderbaren (nicht-const) Container `cend()`jeder Art, der und unterstützt. **const** `end()`

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="multimapclear"></a><a name="clear"></a>multimap::klar

Löscht alle Elemente einer Mehrfachzuordnung.

```cpp
void clear();
```

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der multimap::clear-Elementfunktion gezeigt.

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="multimapconst_iterator"></a><a name="const_iterator"></a>multimap::const_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein **const**-Element in der Mehrfachzuordnung gelesen werden kann.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_iterator`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

Die `const_iterator` durch Multimap definierten [value_type](#value_type)Punkte auf Objekte `pair<const Key, Type>`value_type , die vom Typ sind. Der Wert des Schlüssels ist durch das erste Memberpaar verfügbar, und der Wert des zugeordneten Elements durch das zweite Memberpaar.

Verwenden Sie `const_iterator` den **->** Operator, um einen *cIter* zu dereferenzieren, der auf ein Element in einer Multimap zeigt.

Um auf den Wert des Schlüssels `cIter->first`für das `(*cIter).first`Element zuzugreifen, verwenden Sie , was der entspricht. Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `cIter->second`, was `(*cIter).second`der entspricht.

### <a name="example"></a>Beispiel

Im Beispiel für [begin](#begin) finden Sie ein Beispiel mit `const_iterator`.

## <a name="multimapconst_pointer"></a><a name="const_pointer"></a>multimap::const_pointer

Ein Typ, der einen Zeiger auf ein **const**-Element in einer Mehrfachzuordnung bereitstellt.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_pointer`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [iterator](#iterator)-Typ für den Zugriff auf Elemente in einem multimap-Objekt verwendet werden.

## <a name="multimapconst_reference"></a><a name="const_reference"></a>multimap::const_reference

Ein Typ, der einen Verweis auf ein **const**-Element bereitstellt, das in einer Mehrfachzuordnung zum Lesen und Ausführen von **const**-Operationen gespeichert ist.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Beispiel

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>multimap::const_reverse_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes **const**-Element in einer Mehrfachzuordnung gelesen werden kann.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reverse_iterator`-Typ kann nicht den Wert eines Elements ändern. Er wird verwendet, um die Mehrfachzuordnung in umgekehrter Reihenfolge zu durchlaufen.

Die `const_reverse_iterator` durch Multimap definierten [value_type](#value_type)Punkte auf Objekte `pair<const Key, Type>`value_type , die vom Typ sind. Der Wert des Schlüssels ist durch das erste Memberpaar verfügbar, und der Wert des zugeordneten Elements durch das zweite Memberpaar.

Verwenden Sie `const_reverse_iterator` den **->** Operator, um einen *crIter* zu dereferenzieren, der auf ein Element in einer Multimap verweist.

Um auf den Wert des Schlüssels `crIter->first`für das `(*crIter).first`Element zuzugreifen, verwenden Sie , was der entspricht. Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `crIter->second`, was `(*crIter).first`der entspricht.

### <a name="example"></a>Beispiel

Im Beispiel für [rend](#rend) wird verdeutlicht, wie ein `const_reverse_iterator` deklariert und verwendet wird.

## <a name="multimapcount"></a><a name="count"></a>multimap::zählen

Gibt die Anzahl der Elemente in einer Mehrfachzuordnung zurück, deren Schlüssel mit einem über einen Parameter angegebenen Schlüssel übereinstimmen.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Schlüssel der Elemente, die aus der Mehrfachzuordnung abgeglichen werden.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, deren Sortierschlüssel mit dem Parameterschlüssel übereinstimmen; 0, wenn keine Mehrfachzuordnung ein Element mit einem übereinstimmenden Schlüssel enthält.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Anzahl der Elemente im Bereich zurück.

\[lower_bound(*Taste*), upper_bound(*Taste*) )

die über einen *Schlüsselwertschlüssel*verfügen .

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion „hash_multimap::count“ gezeigt.

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in multimap,
    // so duplicates are allowed and counted
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
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="multimapcrbegin"></a><a name="crbegin"></a>multimap::crbegin

Gibt einen const-Iterator zurück, der das erste Element in einer umgekehrten Mehrfachzuordnung adressiert.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler const-Iterator, der das erste Element in einer umgekehrten [Mehrfachzuordnung](../standard-library/multimap-class.md) bzw. das ehemals letzte Element in der nicht umgekehrten `multimap` adressiert.

### <a name="remarks"></a>Bemerkungen

`crbegin` wird mit einer umgekehrten `multimap` auf die gleiche Weise verwendet, wie [begin](#begin) mit einer `multimap` verwendet wird.

Bei dem Rückgabewert von `crbegin` kann das `multimap`-Objekt nicht geändert werden.

Mit `crbegin` lässt sich eine `multimap` rückwärts durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="multimapcrend"></a><a name="crend"></a>multimap::crend

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der dem letzten Element einer umgekehrten Mehrfachzuordnung folgt.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const_reverse-Iterator, der den Speicherort adressiert, der dem letzten Element in einer umgekehrten [Mehrfachzuordnung](../standard-library/multimap-class.md) folgt (d.h. den Speicherort, der dem ersten Element in der nicht umgekehrten `multimap` vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einer umgekehrten `multimap` auf dieselbe Weise wie [multimap::end](#end) bei einer `multimap` verwendet.

Bei dem Rückgabewert von `crend` kann das `multimap`-Objekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob das Ende der `multimap` von einem umgekehrten Iterator erreicht wurde.

Der von `crend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="multimapdifference_type"></a><a name="difference_type"></a>multimap::difference_type

Ein Ganzzahltyp mit Vorzeichen, mit dem sich die Anzahl von Elementen einer Mehrfachzuordnung in einem Bereich zwischen Elementen darstellen lässt, auf die Iteratoren zeigen.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

`difference_type` ist der Typ, der beim Subtrahieren oder Inkrementieren über Iteratoren des Containers zurückgegeben wird. Der `difference_type` wird in der Regel verwendet, um die Anzahl der Elemente `first` im `last`Bereich [*first*, *last*) zwischen den Iteratoren und `last`, enthält das Element, auf das von `first` und der Bereich der Elemente bis, aber nicht einschließlich, das Element, auf das von gezeigt wird, darzustellen.

Bitte beachten Sie, dass die Subtraktion zwischen Iteratoren nur von Iteratoren mit zufälligem Zugriff unterstützt wird, die über einen Container mit zufälligem Zugriff wie „vector“ bereitgestellt werden. Dies gilt, obwohl `difference_type` für alle Iteratoren verfügbar ist, die die Anforderungen eines Eingabeiterators erfüllen. Hierzu zählt auch die Klasse bidirektionaler Iteratoren, die von umkehrbaren Containern wie „set“ unterstützt wird.

### <a name="example"></a>Beispiel

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="multimapemplace"></a><a name="emplace"></a>multimap::emplace

Es wird ein Element eingefügt, das vor Ort konstruiert wird (keine Kopieren- oder Verschiebevorgänge werden ausgeführt).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Args*|Die weitergeleiteten Argumente zur Konstruktion eines Elements, das in die Mehrfachzuordnung eingefügt werden soll.|

### <a name="return-value"></a>Rückgabewert

Ein Iterator zum neu eingefügten Element.

### <a name="remarks"></a>Bemerkungen

Von dieser Funktion werden keine Verweise auf Containerelemente für ungültig erklärt, aber möglicherweise werden alle Iteratoren für den Containers für ungültig erklärt.

Wenn während des Einfügens eine Ausnahme ausgelöst wird, bleibt der Container unverändert, und die Ausnahme wird erneut ausgelöst.

Der [value_type](../standard-library/map-class.md#value_type) eines Elements wird paarweise angegeben, sodass der Wert eines Elements ein geordnetes Paar ist, bei dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

### <a name="example"></a>Beispiel

```cpp
// multimap_emplace.cpp
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
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="multimapemplace_hint"></a><a name="emplace_hint"></a>multimap::emplace_hint

Fügt ein Element mit einem Platzierungshinweis ein, das vor Ort erstellt wird (Es werden keine Kopier- oder Verschiebevorgänge ausgeführt).

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Args*|Die weitergeleiteten Argumente zur Konstruktion eines Elements, das in die Mehrfachzuordnung eingefügt werden soll.|
|*where*|Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Wenn dieser Punkt unmittelbar vor der Stelle liegt, *an der*das Einfügen in der amortisierten konstanten Zeit anstelle der logarithmischen Zeit erfolgen kann.)|

### <a name="return-value"></a>Rückgabewert

Ein Iterator zum neu eingefügten Element.

### <a name="remarks"></a>Bemerkungen

Von dieser Funktion werden keine Verweise auf Containerelemente für ungültig erklärt, aber möglicherweise werden alle Iteratoren für den Containers für ungültig erklärt.

Wird während des Einbaus eine Ausnahme ausgelöst, wird der Zustand des Containers nicht geändert.

Der [value_type](../standard-library/map-class.md#value_type) eines Elements wird paarweise angegeben, sodass der Wert eines Elements ein geordnetes Paar ist, bei dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

Ein Codebeispiel finden Sie unter [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="multimapempty"></a><a name="empty"></a>multimap::leer

Überprüft, ob eine Mehrfachzuordnung leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Mehrfachzuordnung leer ist, und **FALSE**, wenn sie nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="multimapend"></a><a name="end"></a>multimap::end

Gibt den "past-the-end"-Iterator zurück.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Rückgabewert

Der "past-the-end"-Iterator. Wenn die Mehrfachzuordnung leer ist, dann gilt `multimap::end() == multimap::begin()`.

### <a name="remarks"></a>Bemerkungen

**end** wird verwendet, um zu überprüfen, ob ein Iterator das Ende seiner Mehrfachzuordnung übergeben hat.

Der von **end** zurückgegebene Wert darf nicht dereferenziert werden.

Ein Codebeispiel finden Sie unter [multimap::find](#find).

## <a name="multimapequal_range"></a><a name="equal_range"></a>multimap::equal_range

Sucht den Bereich von Elementen, in dem der Schlüssel des Elements einem angegebenen Wert entspricht.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden Mehrfachzuordnung verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Iteratorenpaar, bei dem der erste Iterator der [lower_bound](#lower_bound) des Schlüssels und der zweite Iterator der [upper_bound](#upper_bound) des Schlüssels ist.

Sie können auf den ersten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **verwenden** Sie \*( `pr`. **zuerst**). Sie können auf den zweiten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **zweiten** und um den oberen gebundenen Iterator zu dereferenzieren, verwenden \*Sie ( `pr`. **zweitens**).

### <a name="example"></a>Beispiel

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="multimaperase"></a><a name="erase"></a>multimap::löschen

Es wird ein Element oder ein Bereich von Elementen in einer Mehrfachzuordnung von angegebenen Speicherorten entfernt oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.

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

*Wo*\
Die Position des zu entfernenden Elements.

*Ersten*\
Die Position des ersten zu entfernenden Elements.

*letzte*\
Die Position direkt hinter dem letzten zu entfernenden Element.

*Schlüssel*\
Der Schlüssel der zu entfernenden Elemente.

### <a name="return-value"></a>Rückgabewert

Bei den ersten beiden Memberfunktionen ist es ein bidirektionaler Iterator, der das erste über die entfernten Elemente hinaus verbliebe Element festlegt, oder ein Element, das das Ende der Zuordnung darstellt, wenn kein solches Element vorhanden ist.

Für die dritte Memberfunktion wird die Anzahl der von der Mehrfachzuordnung entfernten Elemente zurück gegeben.

### <a name="remarks"></a>Bemerkungen

Ein Codebeispiel finden Sie unter [map::erase](../standard-library/map-class.md#erase).

## <a name="multimapfind"></a><a name="find"></a>multimap::finden

Gibt einen Iterator zurück, der auf den ersten Speicherort eines Elements in einer Mehrfachzuordnung verweist, der einen Schlüssel gleich einem angegebenen Schlüssel aufweist.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Schlüsselwert, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden Mehrfachzuordnung übereinstimmt.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Speicherort eines Elements mit einem angegebenen Schlüssel verweist, oder der Speicherort, der dem letzten Element in der Mehrfachzuordnung (`multimap::end()`) nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Iterator zurück, der auf ein Element in der Mehrfachzuordnung verweist, dessen Sortierschlüssel dem Argumentschlüssel unter einem binären Prädikat entspricht, das eine Reihenfolge basierend auf der Beziehung „Less than comparability“ auslöst.

Wird einem `const_iterator` der Rückgabewert von `find` zugewiesen wird, kann das multimap-Objekt nicht geändert werden. Wenn der Rückgabewert von `find` `iterator`einem zugewiesen ist, kann das Multimap-Objekt geändert werden.

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
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
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

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="multimapget_allocator"></a><a name="get_allocator"></a>multimap::get_allocator

Gibt eine Kopie des Zuweisungsobjekts zurück, das zum Erstellen einer Mehrfachzuordnung verwendet wird.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Die von der Mehrfachzuordnung verwendete Zuweisung.

### <a name="remarks"></a>Bemerkungen

Zuweisungen für die Mehrfachzuordnungsklasse geben an, wie die Klasse Speicherplatz verwaltet. Für die meisten Programmieranforderungen reichen die Standard-Zuweisungen aus C++-Standardbibliothek-Containerklassen aus. Schreiben und Verwenden Ihrer eigener Zuweisungsklasse ist ein C++ -Thema für Fortgeschrittene.

### <a name="example"></a>Beispiel

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="multimapinsert"></a><a name="insert"></a>multimap::einfügen

Fügt ein Element oder einen Elementbereich in eine Mehrfachzuordnung ein.

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

|Parameter|BESCHREIBUNG|
|-|-|
|*Val*|Der Wert eines in die Mehrfachzuordnung einzufügenden Elements.|
|*Where*|Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Wenn dieser Punkt unmittelbar vor *Where*vorangeht, kann das Einfügen in der amortisierten konstanten Zeit anstelle der logarithmischen Zeit erfolgen.)|
|*Valty*|Vorlagenparameter, der den Argumenttyp angibt, den die Zuordnung verwenden kann, um ein Element von [value_type](../standard-library/map-class.md#value_type)zu erstellen, und *Val* als Argument perfekt vorwärts leitet.|
|*Ersten*|Die Position des ersten zu kopierenden Elements.|
|*letzte*|Die Position direkt über den letzten zu kopierenden Elements.|
|*Inputiterator*|Das Vorlagenfunktionsargument, das den Anforderungen eines [Eingabeiterators](../standard-library/input-iterator-tag-struct.md) erfüllt, der auf Elemente eines Typs zeigt, der zum Erstellen von [value_type](../standard-library/map-class.md#value_type)-Objekten verwendet werden kann.|
|*IList*|Die [initializer_list,](../standard-library/initializer-list.md) aus dem die Elemente kopiert werden sollen.|

### <a name="return-value"></a>Rückgabewert

Die Einzelelement-Memberfunktionen (1) und (2) geben einen Iterator an die Position zurück, an der das neue Element in die Multimap eingefügt wurde.

Die Einzelelement-Memberfunktionen (3) und (4), geben einen Iterator zurück, der auf die Position zeigt, an der das neue Element in die Multimap eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Von dieser Funktion werden keine Zeiger oder Verweise für ungültig erklärt, aber möglicherweise werden alle Iteratoren für den Containers für ungültig erklärt.

Wird beim Einfügen von nur einem Element eine Ausnahme ausgelöst, wird der Zustand des Containers nicht geändert. Wird beim Einfügen mehrerer Elementen eine Ausnahme ausgelöst, wird der Container in einem nicht angegebenen doch gültigen Zustand belassen.

Das [value_type](../standard-library/map-class.md#value_type)-Element eines Containers ist eine Typedef, die dem Container angehört. Bei einer Zuordnung ist `multimap<K, V>::value_type``pair<const K, V>`. Der Wert eines Elements ist ein sortiertes Paar, in dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

Die Bereichsmemberfunktion (5) fügt die Sequenz von Elementwerten in eine Multimap ein, die `[First, Last)`jedem Element entspricht, das von einem Iterator im Bereich adressiert wird. Daher wird *Last* nicht eingefügt. Die Containermemberfunktion `end()` bezieht sich auf die Position direkt hinter dem letzten Element im Container. Z. B fügt die Anweisung `m.insert(v.begin(), v.end());` alle Elemente von `v` in `m` ein.

Die Memberfunktion (6) der Initialisiererliste verwendet ein [initializer_list](../standard-library/initializer-list.md)-Element, um Elemente in die Zuordnung zu kopieren.

Informationen zum Einfügen eines lokal erstellten Elements (d.h. wenn keine Kopier- oder Verschiebevorgänge ausgeführt werden) finden Sie unter [multimap::emplace](#emplace) und [multimap::emplace_hint](#emplace_hint).

### <a name="example"></a>Beispiel

```cpp
// multimap_insert.cpp
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
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
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
    multimap<int, string>  m3;
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

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="multimapiterator"></a><a name="iterator"></a>multimap::iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einer Mehrfachzuordnung gelesen oder geändert werden kann.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Bemerkungen

Die `iterator` durch Multimap definierten [value_type](#value_type)Punkte auf Objekte `pair<const Key, Type>`value_type , die vom Typ sind. Der Wert des Schlüssels ist durch das erste Memberpaar verfügbar, und der Wert des zugeordneten Elements durch das zweite Memberpaar.

Um einen `iterator` *Iter* zu dereferenzieren, der auf **->** ein Element in einer Multimap zeigt, verwenden Sie den Operator.

Um auf den Wert des Schlüssels `Iter->first`für das `(*Iter).first`Element zuzugreifen, verwenden Sie , was der entspricht. Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `Iter->second`, was `(*Iter).second`der entspricht.

Ein `iterator` Typ kann verwendet werden, um den Wert eines Elements zu ändern.

### <a name="example"></a>Beispiel

Im Beispiel für [begin](#begin) wird verdeutlicht, wie ein `iterator` deklariert und verwendet wird.

## <a name="multimapkey_comp"></a><a name="key_comp"></a>multimap::key_comp

Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in einer Mehrfachzuordnung verwendet wird.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Funktionsobjekt zurück, das eine Mehrfachzuordnung zum Sortieren der jeweiligen Elemente verwendet.

### <a name="remarks"></a>Bemerkungen

Das gespeicherte Objekt definiert die Memberfunktion

`bool operator( const Key& x, const Key& y);`

Sie gibt nur dann TRUE zurück, wenn *x* in der Sortierreihenfolge *y* vorausgeht.

### <a name="example"></a>Beispiel

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
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

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
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

## <a name="multimapkey_compare"></a><a name="key_compare"></a>multimap::key_compare

Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Reihenfolge zweier Elemente in der Mehrfachzuordnung zu bestimmen.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Bemerkungen

`key_compare` ist ein Synonym für den Vorlagenparameter `Traits`.

Weitere Informationen zu `Traits` finden Sie unter [multimap-Klasse](../standard-library/multimap-class.md).

### <a name="example"></a>Beispiel

Im Beispiel für [key_comp](#key_comp) wird verdeutlicht, wie ein `key_compare` deklariert und verwendet wird.

## <a name="multimapkey_type"></a><a name="key_type"></a>multimap::key_type

Ein Typ, mit dem das Sortierschlüsselobjekt beschrieben wird, aus dem die einzelnen Elemente der Mehrfachzuordnung bestehen.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

`key_type` ist ein Synonym für den Vorlagenparameter `Key`.

Weitere Informationen zu `Key` finden Sie im Abschnitt „Hinweise“ unter [multimap-Klasse](../standard-library/multimap-class.md).

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie `key_type` deklariert und verwendet wird.

## <a name="multimaplower_bound"></a><a name="lower_bound"></a>multimap::lower_bound

Gibt einen Iterator zum ersten Element in einer Mehrfachzuordnung mit einem Schlüssel zurück, der mindestens so groß ist wie ein benutzerdefinierter Schlüssel.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden Mehrfachzuordnung verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Iteratoren oder `const_iterator`-Elemente, die entweder den Speicherort eines Elements in einer Mehrfachzuordnung mit einem Schlüssel adressieren, der mindestens so groß ist wie der Argumentschlüssel, oder die, wenn für den Schlüssel keine Übereinstimmung gefunden wird, den Speicherort adressieren, der dem letzten Element in der Mehrfachzuordnung folgt.

Wird einem `const_iterator` der Rückgabewert von `lower_bound` zugewiesen wird, kann das multimap-Objekt nicht geändert werden. Wird einem **Iterator** der Rückgabewert von `lower_bound` zugewiesen wird, kann das multimap-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="multimapmapped_type"></a><a name="mapped_type"></a>multimap::mapped_type

Ein Typ, der den in einer Mehrfachzuordnung gespeicherten Datentyp darstellt.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Bemerkungen

`mapped_type` ist ein Synonym für den Vorlagenparameter `Type`.

Weitere Informationen zu `Type` finden Sie unter [multimap-Klasse](../standard-library/multimap-class.md).

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie `key_type` deklariert und verwendet wird.

## <a name="multimapmax_size"></a><a name="max_size"></a>multimap::max_size

Gibt die Maximallänge der Mehrfachzuordnung zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximal mögliche Länge der Mehrfachzuordnung.

### <a name="example"></a>Beispiel

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimapmultimap"></a><a name="multimap"></a>multimap::multimap

Erstellt eine Mehrfachzuordnung, die leer oder die Kopie einer ganzen anderen Mehrfachzuordnung oder eines Teils davon ist.

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Al*|Die für dieses multimap-Objekt zu verwendende Speicherreservierungsklasse, dessen Standard "Allocator" ist.|
|*Comp*|Die Vergleichsfunktion vom Typ `constTraits`, die verwendet wird, um die Elemente in der Zuordnung zu sortieren, deren Standard `Traits` ist.|
|*Richting*|Die Zuordnung, deren Kopie der erstellte Satz sein soll.|
|*Ersten*|Die Position des ersten Elements in dem zu kopierenden Elementbereich.|
|*letzte*|Die Position des ersten Elements nach dem zu kopierenden Elementbereich.|
|*IList*|Das initializer_list-Element, aus dem die Elemente kopiert werden sollen.|

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren speichern ein Zuweisungsobjekt eines bestimmten Typs, das Arbeitsspeicher für die Mehrfachzuordnung verwaltet und später zurückgegeben werden kann, indem [get_allocator](#get_allocator) aufgerufen wird. Der Zuweisungsparameter wird häufig aus den Klassendeklarationen und den Vorverarbeitungsmakros weggelassen, die zum Ersetzen alternativer Zuweisungen verwendet werden.

Alle Konstruktoren initialisieren ihre Mehrfachzuordnung.

Alle Konstruktoren speichern ein Funktionsobjekt des Typs `Traits`, mit dem sich die Schlüssel der Mehrfachzuordnung sortieren lassen und das später zurückgegeben werden kann, indem [key_comp](#key_comp) aufgerufen wird.

Die ersten drei Konstruktoren geben eine leere Anfangsmultimap an, der zweite gibt den Typ der Vergleichsfunktion (*Comp*) an, die zum Festlegen der Reihenfolge der Elemente verwendet werden soll, und der dritte gibt explizit den zu verwendenden Zuweisungstyp (*Al*) an. Das Schlüsselwort **explizit** unterdrückt bestimmte Arten der automatischen Typkonvertierung.

Der vierte Konstruktor gibt eine Kopie der Multimap *Right*an.

Der fünfte Konstruktor gibt eine Kopie der Multimap an, indem *er Nach rechts*bewegt.

Der sechste, siebte und achte Konstruktor kopiert die Member eines initializer_list-Elements.

Mit den nächsten drei Konstruktoren wird der `[First, Last)`-Bereich, einer Zuordnung kopiert, wobei sich die Explizitheit bei Angabe des Typs der Vergleichsfunktion der Klasse `Traits` und "Allocator" erhöht.

### <a name="example"></a>Beispiel

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of greater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
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

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}
```

## <a name="multimapoperator"></a><a name="op_eq"></a>multimap::operator=

Ersetzt die Elemente einer Mehrfachzuordnung durch eine Kopie einer anderen Mehrfachzuordnung.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Richting*|Die [Mehrfachzuordnung](../standard-library/multimap-class.md), die in `multimap` kopiert wird.|

### <a name="remarks"></a>Bemerkungen

Nach dem Löschen vorhandener `multimap`Elemente `operator=` in einem kopiert oder verschiebt sich der Inhalt von *rechts* in die `multimap`.

### <a name="example"></a>Beispiel

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

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

## <a name="multimappointer"></a><a name="pointer"></a>multimap::pointer

Ein Typ, der einen Zeiger auf ein Element in einer Mehrfachzuordnung bereitstellt.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `pointer` Typ kann verwendet werden, um den Wert eines Elements zu ändern.

In den meisten Fällen sollte ein [iterator](#iterator)-Typ für den Zugriff auf Elemente in einem multimap-Objekt verwendet werden.

## <a name="multimaprbegin"></a><a name="rbegin"></a>multimap::rbegin

Gibt einen Iterator zurück, der das erste Element in einer umgekehrten Mehrfachzuordnung adressiert.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der das erste Element in einer umgekehrten Mehrfachzuordnung oder das ehemals letzte Element in der nicht umgekehrten Mehrfachzuordnung adressiert.

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einer umgekehrten Mehrfachzuordnung auf dieselbe Weise wie [begin](#begin) bei einer Mehrfachzuordnung verwendet.

Wenn einem `const_reverse_iterator` der Rückgabewert von `rbegin` zugewiesen wird, kann das multimap-Objekt nicht geändert werden. Wenn einem `reverse_iterator` der Rückgabewert von `rbegin` zugewiesen wird, kann das multimap-Objekt geändert werden.

Mit `rbegin` lässt sich eine Mehrfachzuordnung rückwärts durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="multimapreference"></a><a name="reference"></a>multimap::Referenz

Ein Typ, der auf ein in einer Mehrfachzuordnung gespeichertes Element verweist.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Beispiel

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="multimaprend"></a><a name="rend"></a>multimap::rend

Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element in einer umgekehrten Mehrfachzuordnung folgt.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der den Speicherort adressiert, der dem letzten Element in einer umgekehrten Mehrfachzuordnung folgt (d.h. den Speicherort, der dem ersten Element in der nicht umgekehrten Mehrfachzuordnung vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einer umgekehrten Mehrfachzuordnung auf dieselbe Weise wie [end](../standard-library/map-class.md#end) bei einer Mehrfachzuordnung verwendet.

Wenn einem `const_reverse_iterator` der Rückgabewert von `rend` zugewiesen wird, kann das multimap-Objekt nicht geändert werden. Wenn einem `reverse_iterator` der Rückgabewert von `rend` zugewiesen wird, kann das multimap-Objekt geändert werden.

Mit `rend` lässt sich überprüfen, ob ein umgekehrter Iterator das Ende seiner Mehrfachzuordnung erreicht hat.

Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="multimapreverse_iterator"></a><a name="reverse_iterator"></a>multimap::reverse_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einer umgekehrten Mehrfachzuordnung gelesen oder geändert werden kann.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Mit einem `reverse_iterator`-Typ lässt sich die Mehrfachzuordnung in umgekehrter Reihenfolge durchlaufen.

Die `reverse_iterator` durch Multimap definierten [value_type](#value_type)Punkte auf Objekte `pair<const Key, Type>`value_type , die vom Typ sind. Der Wert des Schlüssels ist durch das erste Memberpaar verfügbar, und der Wert des zugeordneten Elements durch das zweite Memberpaar.

Verwenden Sie `reverse_iterator` den **->** Operator, um einen *rIter* zu dereferenzieren, der auf ein Element in einer Multimap zeigt.

Um auf den Wert des Schlüssels `rIter->first`für das `(*rIter).first`Element zuzugreifen, verwenden Sie , was der entspricht. Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `rIter->second`, was `(*rIter).second`der entspricht.

### <a name="example"></a>Beispiel

Im Beispiel für [rbegin](#rbegin) wird verdeutlicht, wie ein `reverse_iterator` deklariert und verwendet wird.

## <a name="multimapsize"></a><a name="size"></a>multimap::Größe

Gibt die Anzahl von Elementen in der Mehrfachzuordnung zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge der Mehrfachzuordnung.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung dermultimap::size-Memberfunktion gezeigt.

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="multimapsize_type"></a><a name="size_type"></a>multimap::size_type

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einer Mehrfachzuordnung zählt.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Beispiel

Im Beispiel für [size](#size) wird verdeutlicht, wie ein `size_type` deklariert und verwendet wird.

## <a name="multimapswap"></a><a name="swap"></a>multimap::swap

Tauscht die Elemente zweier Mehrfachzuordnungen aus.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die Mehrfachzuordnung, in der die auszutauschenden Elemente bereitgestellt werden, oder die Mehrfachzuordnung, deren Elemente mit denen der Mehrfachzuordnung `left` ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion macht keine Verweise, Zeiger oder Iteratoren ungültig, die Elemente in zwei Mehrfachzuordnungen bezeichnen, deren Elemente ausgetauscht werden.

### <a name="example"></a>Beispiel

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="multimapupper_bound"></a><a name="upper_bound"></a>multimap::upper_bound

Gibt dem ersten Element in einer Mehrfachzuordnung einen Iterator mit einem Schlüssel zurück, der größer ist als ein benutzerdefinierter Schlüssel.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden Mehrfachzuordnung verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Iterator oder ein `const_iterator`, der den Speicherort eines Elements in einer Mehrfachzuordnung mit einem Schlüssel adressiert, der größer ist als der Argumentschlüssel, oder der den Speicherort adressiert, der dem letzten Element in der Mehrfachzuordnung folgt, wenn für den Schlüssel keine Übereinstimmung gefunden wird.

Wenn der Rückgabewert einem `const_iterator` zugewiesen wird, kann das multimap-Objekt nicht geändert werden. Wenn der Rückgabewert einem `iterator`zugewiesen ist, kann das Multimap-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="multimapvalue_comp"></a><a name="value_comp"></a>multimap::value_comp

Die Memberfunktion gibt ein Funktionsobjekt zurück, das die Reihenfolge der Elemente in einer Mehrfachzuordnung bestimmt, indem die jeweiligen Schlüsselwerte verglichen werden.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Vergleichsfunktionsobjekt zurück, das eine Mehrfachzuordnung zum Sortieren der jeweiligen Elemente verwendet.

### <a name="remarks"></a>Bemerkungen

Für eine Multimap *m*sind, wenn zwei Elemente *e1*(*k1*, *d1*) `value_type`und *e2*(*k2*, *d2*) Objekte vom Typ sind, wobei `m.key_comp(k1, k2)` *k1* und *k2* ihre Schlüssel vom Typ `key_type` und *d1* und *d2* ihre Daten vom Typ `mapped_type`sind, dann `m.value_comp(e1, e2)` entspricht dies .

### <a name="example"></a>Beispiel

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="multimapvalue_type"></a><a name="value_type"></a>multimap::value_type

Ein Typ, der dem als Element in einer Zuordnung gespeicherten Objekttyp entspricht.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Beispiel

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
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

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Siehe auch

[Container](../cpp/containers-modern-cpp.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)
