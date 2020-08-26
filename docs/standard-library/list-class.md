---
title: list-Klasse
ms.date: 11/04/2016
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
ms.openlocfilehash: ec53e2a907cd38b262ec305d10ae63ad746f29b5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833334"
---
# <a name="list-class"></a>list-Klasse

Die klassenklasse der C++-Standard Bibliothek ist eine Klassen Vorlage von Sequenz Containern, die ihre Elemente in einer linearen Anordnung verwalten und effiziente Einfügungen und Löschungen an jedem Speicherort innerhalb der Sequenz ermöglichen. Die Sequenz wird als bidirektionale verknüpfte Liste von Elementen gespeichert, die jeweils einen Member vom Typ *Type* enthalten.

## <a name="syntax"></a>Syntax

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der in der Liste zu speichernde Elementdatentyp.

*Allocator*\
Der Typ, der das gespeicherte Zuordnungsobjekt darstellt, das Details zum Belegen und Freigeben des Arbeitsspeichers der Liste kapselt. Dieses Argument ist optional, und der Standardwert ist `allocator<Type>`.

## <a name="remarks"></a>Bemerkungen

Die Auswahl des Containertyps sollte im Allgemeinen auf Grundlage des für die Anwendung erforderlichen Suchen und Einfügetyps erfolgen. Vektoren sollten der bevorzugte Container zum Verwalten einer Sequenz sein, wenn zufälliger Zugriff auf jedes Element unbedingt erforderlich und das Einfügen oder Löschen von Elementen nur am Ende einer Sequenz notwendig ist. Die Leistung des deque-Klassencontainers hat Vorrang, wenn zufälliger Zugriff erforderlich ist und Einfügungen und Löschungen sowohl am Anfang als auch am Ende einer Sequenz unbedingt notwendig sind.

Die Listen-Memberfunktionen [merge](#merge), [reverse](#reverse), [unique](#unique), [remove](#remove) und [remove_if](#remove_if) wurden für die Verwendung mit Listenobjekten optimiert und bieten eine leistungsstarke Alternative zu ihren generischen Entsprechungen.

Die Neuzuordnung von Listen tritt auf, wenn Elemente der Liste von einer Memberfunktion eingefügt oder gelöscht werden müssen. In solchen Fällen werden nur Iteratoren oder Verweise auf gelöschte Teile der gesteuerten Sequenz ungültig.

Schließen Sie den Standard Header der C++-Standardbibliothek ein \<list> , um die [Container](../standard-library/stl-containers.md) Klassen-Vorlagenliste und mehrere unterstützende Vorlagen zu definieren.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|BESCHREIBUNG|
|-|-|
|[list](#list)|Erstellt eine Liste einer bestimmten Größe bzw. mit Elementen eines bestimmten Werts oder mit einem bestimmten `allocator`-Element oder als vollständige bzw. teilweise Kopie einer anderen Liste.|

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[allocator_type](#allocator_type)|Ein Typ, mit dem die `allocator`-Klasse für ein Listenobjekt dargestellt wird.|
|[const_iterator](#const_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein **`const`** Element in einer Liste gelesen werden kann.|
|[const_pointer](#const_pointer)|Ein Typ, der einen Zeiger auf ein- **`const`** Element in einer Liste bereitstellt.|
|[const_reference](#const_reference)|Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einer Liste zum Lesen und Ausführen von **`const`** Vorgängen gespeichert ist.|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes **`const`** Element in einer Liste gelesen werden kann.|
|[difference_type](#difference_type)|Ein Typ, der den Unterschied zwischen zwei Iteratoren, die auf Elemente innerhalb derselben Liste verweisen, bereitstellt.|
|[Iterator](#iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einer Liste gelesen oder geändert werden kann.|
|[Zeichner](#pointer)|Ein Typ, der einen Zeiger auf ein Element in einer Liste bereitstellt.|
|[Referenz](#reference)|Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einer Liste zum Lesen und Ausführen von **`const`** Vorgängen gespeichert ist.|
|[reverse_iterator](#reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einer umgekehrten Liste gelesen oder geändert werden kann.|
|[size_type](#size_type)|Ein Typ, der die Anzahl von Elementen in einer Liste zählt.|
|[value_type](#value_type)|Ein Typ, der den in einer Liste gespeicherten Datentyp darstellt.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[assign](#assign)|Löscht Elemente aus einer Liste und kopiert einen neuen Satz von Elementen in die Zielliste.|
|[Zurück](#back)|Gibt einen Verweis auf das letzte Element einer Liste zurück.|
|[beginnen](#begin)|Gibt einen Iterator zurück, der das erste Element in einer Liste adressiert.|
|[cbegin](#cbegin)|Gibt einen konstanten Iterator zurück, der das erste Element in einer Liste adressiert.|
|[cend](#cend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element einer Liste nachfolgt.|
|[Löschen](#clear)|Löscht alle Elemente einer Liste.|
|[crbegin](#crbegin)|Gibt einen konstanten Iterator zurück, der das erste Element in einer umgekehrten Liste adressiert.|
|[crend](#crend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten Listenelements nachfolgt.|
|[emplace](#emplace)|Fügt ein direkt konstruiertes Element an einer angegebenen Position in die Liste ein.|
|[emplace_back](#emplace_back)|Fügt ein direkt konstruiertes Element am Ende einer Liste ein.|
|[emplace_front](#emplace_front)|Fügt ein direkt konstruiertes Element am Anfang einer Liste ein.|
|[empty](#empty)|Testet, ob eine Liste leer ist.|
|[end](#end)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element einer Liste nachfolgt.|
|[erase](#erase)|Entfernt ein Element oder eine Reihe von Elementen in einer Liste aus angegebenen Speicherorten.|
|[Beifahrer](#front)|Gibt einen Verweis auf das erste Element in einer Liste zurück.|
|[get_allocator](#get_allocator)|Gibt eine Kopie des `allocator`-Objekts zurück, das zum Erstellen einer Liste verwendet wird.|
|[insert](#insert)|Fügt ein Element oder mehrere Elemente oder ein Reihe von Elementen an einer bestimmten Position in die Liste ein.|
|[max_size](#max_size)|Gibt die Maximallänge einer Liste zurück.|
|[merge](#merge)|Entfernt die Elemente aus der Argumentliste, fügt sie in die Zielliste ein und sortiert den neuen, kombinierten Elementsatz in aufsteigender Reihenfolge oder in einer anderen angegebenen Reihenfolge.|
|[pop_back](#pop_back)|Löscht das Element am Ende einer Liste.|
|[pop_front](#pop_front)|Löscht das Element am Anfang einer Liste.|
|[push_back](#push_back)|Fügt am Ende einer Liste ein Element hinzu.|
|[push_front](#push_front)|Fügt am Anfang einer Liste ein Element hinzu.|
|[rbegin](#rbegin)|Gibt einen Iterator zurück, der das erste Element in einer umgekehrten Liste adressiert.|
|[remove](#remove)|Löscht Elemente in einer Liste, die einen angegebenen Wert entsprechen.|
|[remove_if](#remove_if)|Löscht Elemente aus der Liste, für die ein angegebenes Prädikat erfüllt ist.|
|[rend](#rend)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element einer umgekehrten Liste nachfolgt.|
|[Größe](#resize)|Gibt eine neue Größe für eine Liste an.|
|[reverse](#reverse)|Kehrt die Reihenfolge um, in der die Elemente in einer Liste auftreten.|
|[size](#size)|Gibt die Anzahl von Elementen in einer Liste zurück.|
|[sort](#sort)|Ordnet die Elemente einer Liste in aufsteigender Reihenfolge oder in Bezug auf eine andere Reihenfolgebeziehung.|
|[splice](#splice)|Entfernt Elemente aus der Argumentliste und fügt sie in die Zielliste ein.|
|[swap](#swap)|Tauscht die Elemente zweier Listen aus.|
|[unique](#unique)|Entfernt benachbarte doppelte Elemente oder benachbarte Elemente, die einige andere binäre Prädikate aus der Liste erfüllen.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator =](#op_eq)|Ersetzt die Elemente der Liste mit einer Kopie einer anderen Liste.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: \<list>

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

Ein Typ, mit dem die Zuweisungsklasse für ein Listenobjekt dargestellt wird.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Bemerkungen

`allocator_type` ist ein Synonym für die Vorlagen Parameter *Zuweisung*.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get_allocator](#get_allocator).

## <a name="assign"></a><a name="assign"></a> einräumen

Löscht Elemente aus einer Liste und kopiert einen neuen Satz von Elementen in eine Zielliste.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign
    initializer_list<Type> IList);

template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parameter

*Erstes*\
Die Position des ersten Elements in dem aus der Argumentliste zu kopierenden Elementbereich.

*Letzten*\
Die Position des ersten Elements direkt hinter dem aus der Argumentliste zu kopierenden Elementbereich.

*Countdown*\
Die Anzahl von Kopien eines Elements, das in die Liste eingefügt wird.

*Ster*\
Der Wert des Elements, das in die Liste eingefügt wird.

*IList*\
Das initializer_list-Element, das die einzufügenden Elemente enthält.

### <a name="remarks"></a>Bemerkungen

Nachdem alle vorhandenen Elemente in der Zielliste gelöscht sind, wird entweder ein angegebener Elementbereich aus der ursprünglichen Liste oder aus einer anderen Liste in die Zielliste eingefügt, oder es werden Kopien eines neuen Elements eines angegebenen Werts in die Zielliste eingefügt.

### <a name="example"></a>Beispiel

```cpp
// list_assign.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    list<int> c1, c2;
    list<int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign({ 10, 20, 30, 40 });
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40
```

## <a name="back"></a><a name="back"></a> Zurück

Gibt einen Verweis auf das letzte Element einer Liste zurück.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Rückgabewert

Das letzte Element der Liste. Wenn die Liste leer ist, ist der Rückgabewert nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn `back` dem Rückgabewert von `const_reference` zugewiesen wird, kann das Listenobjekt nicht geändert werden. Wenn `back` dem Rückgabewert von `reference` zugewiesen wird, kann das Listenobjekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element in einer leeren Liste ein Laufzeitfehler auf.  Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md) .

### <a name="example"></a>Beispiel

```cpp
// list_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a><a name="begin"></a> beginnen

Gibt einen Iterator zurück, der das erste Element in einer Liste adressiert.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der das erste Element in der Liste adressiert oder auf den Speicherort hinweist, der auf eine leere Liste folgt.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `begin` einem zugewiesen wird `const_iterator` , können die Elemente im Listen Objekt nicht geändert werden. Wenn der Rückgabewert von `begin` einem zugewiesen wird `iterator` , können die Elemente im Listen Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// list_begin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

Gibt einen **`const`** Iterator zurück, der das erste Element im Bereich adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** bidirektionaler-Access-Iterator, der auf das erste Element des Bereichs zeigt oder die Position direkt hinter dem Ende eines leeren Bereichs (für einen leeren Bereich `cbegin() == cend()` ).

### <a name="remarks"></a>Bemerkungen

Bei dem Rückgabewert `cbegin` können die Elemente im Bereich nicht geändert werden.

Sie können diese Memberfunktion anstelle der `begin()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollte `Container` ein änderbarer (nicht) Container sein, **`const`** der und unterstützt `begin()` `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

Gibt einen **`const`** Iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** bidirektionaler-Access-Iterator, der direkt hinter das Ende des Bereichs zeigt.

### <a name="remarks"></a>Bemerkungen

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines Bereichs übergeben hat.

Sie können diese Memberfunktion anstelle der `end()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollte `Container` ein änderbarer (nicht) Container sein, **`const`** der und unterstützt `end()` `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="clear"></a><a name="clear"></a> Klartext

Löscht alle Elemente einer Liste.

```cpp
void clear();
```

### <a name="example"></a>Beispiel

```cpp
// list_clear.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the list is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of list after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the list is initially 3
The size of list after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein **`const`** Element in einer Liste gelesen werden kann.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_iterator`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [back](#back).

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Stellt einen Zeiger auf ein- **`const`** Element in einer Liste bereit.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_pointer`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem Listenobjekt verwendet werden.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einer Liste zum Lesen und Ausführen von **`const`** Vorgängen gespeichert ist.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reference`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

```cpp
// list_const_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const list <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error because c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes **`const`** Element in einer Liste gelesen werden kann.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reverse_iterator`-Typ kann nicht den Wert eines Elements ändern und wird verwendet, um die Liste in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [rbegin](#rbegin).

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

Gibt einen konstanten Iterator zurück, der das erste Element in einer umgekehrten Liste adressiert.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionalem Iterator bezieht sich auf das erste Element in einer umgekehrten Liste (oder auf das ehemals letzte Element in der nicht umgekehrten Liste `list`).

### <a name="remarks"></a>Bemerkungen

`crbegin` wird bei einer umgekehrten Liste auf die gleiche Weise verwendet, wie [list::begin](#begin) bei `list` verwendet wird.

Bei dem Rückgabewert von `crbegin` kann das Listenobjekt nicht geändert werden. Mit [list::rbegin](#rbegin) kann eine Liste rückwärts durchlaufen werden.

### <a name="example"></a>Beispiel

```cpp
// list_crbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_crIter = c1.crbegin( );
   cout << "The last element in the list is " << *c1_crIter << "." << endl;
}
```

```Output
The last element in the list is 30.
```

## <a name="crend"></a><a name="crend"></a> crend

Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten Listenelements nachfolgt.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der sich auf den Standort bezieht, der dem letzten Element in einer umgekehrten [Liste](../standard-library/list-class.md) nachfolgt (der Speicherort, der dem ersten Element in der nicht umgekehrten `list` vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einer umgekehrten Liste auf die gleiche Weise verwendet, wie [list::end](#end) bei `list` verwendet wird.

Bei dem Rückgabewert von `crend` kann das `list`-Objekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob das Ende der `list` von einem umgekehrten Iterator erreicht wurde.

Der von `crend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// list_crend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_crIter = c1.crend( );
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_crIter << endl;
}
```

```Output
The first element in the list is: 10
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen einer Liste in einem Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

`difference_type` ist der Typ, der beim Subtrahieren oder Inkrementieren über Iteratoren des Containers zurückgegeben wird. `difference_type` wird normalerweise verwendet, um die Anzahl von Elementen im Bereich [`first`, `last`) zwischen den Iteratoren `first` und `last` darzustellen. Dazu gehört das Element, auf das durch `first` gezeigt wird und der Bereich von Elementen bis zu (aber nicht einschließlich) dem Element, auf das durch `last` gezeigt wird.

Beachten Sie, dass die Subtraktion zwischen Iteratoren nur von Random-Access-Iteratoren, die über einen Random-Access-Container bereitgestellt werden – beispielsweise [vector-Klasse](../standard-library/vector-class.md) – unterstützt wird, obwohl `difference_type` für alle Iteratoren verfügbar ist, die die Anforderungen für einen Eingabeiterator erfüllen, wozu auch die Klasse bidirektionaler Iteratoren gehört, die von umkehrbaren Containern wie Satz unterstützt wird.

### <a name="example"></a>Beispiel

```cpp
// list_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <list>
#include <algorithm>

int main( )
{
   using namespace std;

   list <int> c1;
   list <int>::iterator   c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

    list <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

Fügt ein direkt konstruiertes Element an einer angegebenen Position in die Liste ein.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>Parameter

*Was*\
Die Position in der [Zielliste](../standard-library/list-class.md) , an der das erste Element eingefügt wird.

*ster*\
Das Element, das am Ende der `list` hinzugefügt wird.

### <a name="remarks"></a>Bemerkungen

Wenn eine Ausnahme ausgelöst wird, bleibt die `list` unverändert, und die Ausnahme wird erneut ausgelöst.

### <a name="example"></a>Beispiel

```cpp
// list_emplace.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace(c2.begin(), move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_back"></a><a name="emplace_back"></a> emplace_back

Fügt ein direkt konstruiertes Element am Ende einer Liste ein.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das Element, das am Ende der [Liste](../standard-library/list-class.md)hinzugefügt wird.

### <a name="remarks"></a>Bemerkungen

Wenn eine Ausnahme ausgelöst wird, bleibt die `list` unverändert, und die Ausnahme wird erneut ausgelöst.

### <a name="example"></a>Beispiel

```cpp
// list_emplace_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

Fügt ein direkt konstruiertes Element am Anfang einer Liste ein.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das am Anfang der [Liste](../standard-library/list-class.md) hinzugefügte Element.

### <a name="remarks"></a>Bemerkungen

Wenn eine Ausnahme ausgelöst wird, bleibt die `list` unverändert, und die Ausnahme wird erneut ausgelöst.

### <a name="example"></a>Beispiel

```cpp
// list_emplace_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="empty"></a><a name="empty"></a> leer

Testet, ob eine Liste leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die Liste leer ist. , **`false`** Wenn die Liste nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// list_empty.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The list is empty." << endl;
   else
      cout << "The list is not empty." << endl;
}
```

```Output
The list is not empty.
```

## <a name="end"></a><a name="end"></a> Schließlich

Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element einer Liste nachfolgt.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der den Speicherort adressiert, der dem letzten Element einer Liste nachfolgt. Wenn die Liste leer ist, dann gilt `list::end == list::begin`.

### <a name="remarks"></a>Bemerkungen

`end` wird verwendet, um zu testen, ob ein Iterator das Ende seiner Liste erreicht hat.

### <a name="example"></a>Beispiel

```cpp
// list_end.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
*c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is "
        << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // list <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The list is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The list is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> Löschen

Entfernt ein Element oder eine Reihe von Elementen in einer Liste aus angegebenen Speicherorten.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parameter

*Was*\
Die Position des von der Liste zu entfernenden Elements.

*erstes*\
Die Position des ersten Elements, das von der Liste entfernt werden soll.

*letzten*\
Die Position direkt hinter dem letzten von der Liste entfernten Element.

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der das erste über die entfernten Elemente hinaus verbliebene Element festlegt, oder ein Zeiger, der das Ende der Liste darstellt, wenn kein solches Element vorhanden ist

### <a name="remarks"></a>Bemerkungen

Es erfolgt keine Neuzuordnung. Die Iteratoren und Verweise werden nur für die gelöschten Elemente ungültig.

`erase` löst nie eine Ausnahme aus.

### <a name="example"></a>Beispiel

```cpp
// list_erase.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial list is:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the list becomes:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, the list becomes: ";
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
The initial list is: 10 20 30 40 50
After erasing the first element, the list becomes: 20 30 40 50
After erasing all elements but the first, the list becomes:  20
```

## <a name="front"></a><a name="front"></a> Beifahrer

Gibt einen Verweis auf das erste Element in einer Liste zurück.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn die Liste leer ist, ist die Rückgabe nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn `front` dem Rückgabewert von `const_reference` zugewiesen wird, kann das Listenobjekt nicht geändert werden. Wenn `front` dem Rückgabewert von `reference` zugewiesen wird, kann das Listenobjekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element in einer leeren Liste ein Laufzeitfehler auf.  Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md) .

### <a name="example"></a>Beispiel

```cpp
// list_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );

   int& i = c1.front();
   const int& ii = c1.front();

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The first integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The first integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Gibt eine Kopie des Zuweisungsobjekts zurück, das zum Erstellen einer Liste verwendet wird.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zuweisung von der Liste verwendet.

### <a name="remarks"></a>Bemerkungen

Zuweisungen für die Listenklasse geben an, wie die Klasse einen Speicher verwaltet. Für die meisten Programmieranforderungen reichen die Standard-Zuweisungen aus C++-Standardbibliothek-Containerklassen aus. Schreiben und Verwenden Ihrer eigener Zuweisungsklasse ist ein C++ -Thema für Fortgeschrittene.

### <a name="example"></a>Beispiel

```cpp
// list_get_allocator.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   list <int> c1;
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   list <int> c3( c1.get_allocator( ) );

   list<int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> setze

Fügt ein Element oder mehrere Elemente oder ein Reihe von Elementen an einer bestimmten Position in die Liste ein.

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parameter

*Was*\
Die Position in der Zielliste, an der das erste Element eingefügt wird.

*Ster*\
Der Wert des Elements, das in die Liste eingefügt wird.

*Countdown*\
Die Anzahl von Elementen, die in die Liste eingefügt werden.

*Erstes*\
Die Position des ersten Elements in dem Elementbereich in der Argumentliste, die kopiert werden soll.

*Letzten*\
Die Position des ersten Elements hinter dem Elementbereich in der Argumentliste, die kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Die ersten zwei Einfügefunktionen geben ein Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element in die Liste eingefügt wurde.

### <a name="example"></a>Beispiel

```cpp
// list_class_insert.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    list <int> c1, c2;
    list <int>::iterator Iter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    c1.insert(Iter, 100);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    Iter++;
    c1.insert(Iter, 2, 200);

    cout << "c1 =";
    for(auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.insert(++c1.begin(), c2.begin(), --c2.end());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    // initialize a list of strings by moving
    list < string > c3;
    string str("a");

    c3.insert(c3.begin(), move(str));
    cout << "Moved first element: " << c3.front() << endl;

    // Assign with an initializer_list
    list <int> c4{ {1, 2, 3, 4} };
    c4.insert(c4.begin(), { 5, 6, 7, 8 });

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> Iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einer Liste gelesen oder geändert werden kann.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein-Typ `iterator` kann zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [begin](#begin).

## <a name="list"></a><a name="list"></a> List

Erstellt eine Liste einer bestimmten Größe bzw. mit Elementen eines bestimmten Werts oder mit einer bestimmten Zuweisung oder als vollständige bzw. teilweise Kopie einer anderen Liste.

```cpp
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>
list(InputIterator First, InputIterator Last);

template <class InputIterator>
list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parameter

*Irdische*\
Die mit diesem Objekt zu verwendende Zuweisungsklasse.

*Countdown*\
Die Anzahl von Elementen in der erstellten Liste.

*Ster*\
Der Werttyp der Elemente in der Liste.

*Richting*\
Die Liste, deren Kopie die erstellte Liste ist.

*Erstes*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*Letzten*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*IList*\
Das initializer_list-Element, das die zu kopierenden Elemente enthält.

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren speichern ein*Zuordnungs*Objekt (Al) und initialisieren die Liste.

[get_allocator](#get_allocator) gibt eine Kopie des Zuweisungsobjekts zurück, das zum Erstellen der Liste verwendet wird.

Die ersten beiden Konstruktoren geben eine leere ursprüngliche Liste an, wobei die zweite den zu verwendenden zuordnertyp (*Al*) angibt.

Der dritte Konstruktor gibt eine Wiederholung einer angegebenen*Anzahl (Anzahl*) von Elementen des Standardwerts für die Klasse an `Type` .

Der vierte und fünfte Konstruktoren geben eine Wiederholung der (*count*) Elemente des Werts *Val*an.

Der sechste Konstruktor gibt eine Kopie der Liste *Rechts*an.

Der siebte Konstruktor verschiebt die Liste nach *Rechts*.

Beim achten Konstruktor wird zum Angeben des Elements ein initializer_list-Element verwendet.

Die folgenden zwei Konstruktoren kopieren den `[First, Last)`-Bereich einer Liste.

Keine der Konstruktoren führen Zwischenneuzuordnungen aus.

### <a name="example"></a>Beispiel

```cpp
// list_class_list.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty list c0
    list <int> c0;

    // Create a list c1 with 3 elements of default value 0
    list <int> c1(3);

    // Create a list c2 with 5 elements of value 2
    list <int> c2(5, 2);

    // Create a list c3 with 3 elements of value 1 and with the
    // allocator of list c2
    list <int> c3(3, 1, c2.get_allocator());

    // Create a copy, list c4, of list c2
    list <int> c4(c2);

    // Create a list c5 by copying the range c4[ first,  last)
    list <int>::iterator c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    list <int> c5(c4.begin(), c4_Iter);

    // Create a list c6 by copying the range c4[ first,  last) and with
    // the allocator of list c2
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;

    cout << "c6 =";
    for (auto c : c6)
        cout << " " << c;
    cout << endl;

    // Move list c6 to list c7
    list <int> c7(move(c6));
    cout << "c7 =";
    for (auto c : c7)
        cout << " " << c;
    cout << endl;

    // Construct with initializer_list
    list<int> c8({ 1, 2, 3, 4 });
    cout << "c8 =";
    for (auto c : c8)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4
```

## <a name="max_size"></a><a name="max_size"></a> max_size

Gibt die Maximallänge einer Liste zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die mögliche Maximallänge der Liste.

### <a name="example"></a>Beispiel

```cpp
// list_max_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   i = c1.max_size( );
   cout << "Maximum possible length of the list is " << i << "." << endl;
}
```

## <a name="merge"></a><a name="merge"></a> Merge

Entfernt die Elemente aus der Argumentliste, fügt sie in die Zielliste ein und sortiert den neuen, kombinierten Elementsatz in aufsteigender Reihenfolge oder in einer anderen angegebenen Reihenfolge.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die Argumentliste, die mit der Zielliste zusammengeführt werden soll.

*zuschreiben*\
Der Vergleichsoperator, der zum Sortieren der Elemente in der Zielliste verwendet wird.

### <a name="remarks"></a>Bemerkungen

Das Argumentlisten *Recht* wird mit der Zielliste zusammengeführt.

Die Argument- und die Zielliste müssen mit derselben Vergleichsbeziehung sortiert werden, mit der die resultierende Sequenz sortiert werden soll. Die Standardreihenfolge für die erste Member-Funktion ist die aufsteigende Reihenfolge. Die zweite Member-Funktion erzwingt den vom Benutzer angegebenen Vergleichs Vorgang *Comp* der-Klasse `Traits` .

### <a name="example"></a>Beispiel

```cpp
// list_merge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;

   c1.push_back( 3 );
   c1.push_back( 6 );
   c2.push_back( 2 );
   c2.push_back( 4 );
   c3.push_back( 5 );
   c3.push_back( 1 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   cout << "c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order
   c2.sort( greater<int>( ) );
   cout << "After merging c1 with c2 and sorting with >: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   cout << "c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;

   c2.merge( c3, greater<int>( ) );
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
c1 = 3 6
c2 = 2 4
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2
c3 = 5 1
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1
```

## <a name="operator"></a><a name="op_eq"></a> Operator =

Ersetzt die Elemente der Liste mit einer Kopie einer anderen Liste.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die [Liste](../standard-library/list-class.md), die in die `list` kopiert wird.

### <a name="remarks"></a>Bemerkungen

Nachdem ein vorhandenes Element in einem gelöscht `list` wurde, kopiert oder verschiebt der Operator den Inhalt von *direkt* in den `list` .

### <a name="example"></a>Beispiel

```cpp
// list_operator_as.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int> v1, v2, v3;
   list<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = forward< list<int> >(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a><a name="pointer"></a>-Zeiger

Stellt einen Zeiger auf ein Element in einer Liste bereit.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein-Typ `pointer` kann zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem Listenobjekt verwendet werden.

## <a name="pop_back"></a><a name="pop_back"></a> pop_back

Löscht das Element am Ende einer Liste.

```cpp
void pop_back();
```

### <a name="remarks"></a>Bemerkungen

Das letzte Element darf nicht leer sein. `pop_back` löst nie eine Ausnahme aus.

### <a name="example"></a>Beispiel

```cpp
// list_pop_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the list, "
           "the last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the list, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

Löscht das Element am Anfang einer Liste.

```cpp
void pop_front();
```

### <a name="remarks"></a>Bemerkungen

Das erste Element darf nicht leer sein. `pop_front` löst nie eine Ausnahme aus.

### <a name="example"></a>Beispiel

```cpp
// list_pop_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the list, "
         "the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the list, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> push_back

Fügt am Ende einer Liste ein Element hinzu.

```cpp
void push_back(const Type& val);
void push_back(Type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das Element, das am Ende der Liste hinzugefügt wird.

### <a name="remarks"></a>Bemerkungen

Wenn eine Ausnahme ausgelöst wird, bleibt die Liste unverändert, und die Ausnahme wird erneut ausgelöst.

### <a name="example"></a>Beispiel

```cpp
// list_push_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   if ( c1.size( ) != 0 )
      cout << "Last element: " << c1.back( ) << endl;

   c1.push_back( 2 );
   if ( c1.size( ) != 0 )
      cout << "New last element: " << c1.back( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved first element: a
```

## <a name="push_front"></a><a name="push_front"></a> push_front

Fügt am Anfang einer Liste ein Element hinzu.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das am Anfang der Liste hinzugefügte Element.

### <a name="remarks"></a>Bemerkungen

Wenn eine Ausnahme ausgelöst wird, bleibt die Liste unverändert, und die Ausnahme wird erneut ausgelöst.

### <a name="example"></a>Beispiel

```cpp
// list_push_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

Gibt einen Iterator zurück, mit dem das erste Element in einer umgekehrten Liste behandelt wird.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionalem Iterator, mit dem das erste Element in einer umgekehrten Liste adressiert wird (bzw. mit dem das ehemals letzte Element in der nicht umgekehrten Liste adressiert wird).

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einer umgekehrten Liste auf die gleiche Weise verwendet, wie [begin](#begin) bei einer Liste verwendet wird.

Wenn `rbegin` dem Rückgabewert von `const_reverse_iterator` zugewiesen wird, kann das Listenobjekt nicht geändert werden. Wenn `rbegin` dem Rückgabewert von `reverse_iterator` zugewiesen wird, kann das Listenobjekt geändert werden.

Mit `rbegin` kann eine Liste rückwärts durchlaufen werden.

### <a name="example"></a>Beispiel

```cpp
// list_rbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line replaced the line above, *c1_rIter = 40;
   // (below) would be an error
   //list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_rIter = c1.rbegin( );
   cout << "The last element in the list is " << *c1_rIter << "." << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration through a list in
   // reverse order
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rbegin( );
*c1_rIter = 40;
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;
}
```

```Output
The last element in the list is 30.
The list is: 10 20 30
The reversed list is: 30 20 10
The last element in the list is now 40.
```

## <a name="reference"></a><a name="reference"></a> Angabe

Ein Typ, der einen Verweis auf ein in einer Liste gespeichertes Element bereitstellt.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Beispiel

```cpp
// list_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="remove"></a><a name="remove"></a> aufgeh

Löscht Elemente in einer Liste, die einen angegebenen Wert entsprechen.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Der Wert, der, sofern er von einem Element gehalten wird, das Entfernen dieses Elements aus der Liste verursacht.

### <a name="remarks"></a>Bemerkungen

Die Reihenfolge der verbleibenden Elemente ist nicht beeinflusst.

### <a name="example"></a>Beispiel

```cpp
// list_remove.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 5 );
   c1.push_back( 100 );
   c1.push_back( 5 );
   c1.push_back( 200 );
   c1.push_back( 5 );
   c1.push_back( 300 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove( 5 );
   cout << "After removing elements with value 5, the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 5 100 5 200 5 300
After removing elements with value 5, the list becomes c2 = 100 200 300
```

## <a name="remove_if"></a><a name="remove_if"></a> remove_if

Löscht Elemente aus einer Liste, für die ein angegebenes Prädikat erfüllt ist.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>Parameter

*pred*\
Das unäre Prädikat, das bei Erfüllung durch ein Element das Löschen dieses Elements in der Liste zur Folge hat.

### <a name="example"></a>Beispiel

```cpp
// list_remove_if.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

template <class T> class is_odd : public std::unary_function<T, bool>
{
public:
   bool operator( ) ( T& val )
   {
   return ( val % 2 ) == 1;
   }
};

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 3 );
   c1.push_back( 4 );
   c1.push_back( 5 );
   c1.push_back( 6 );
   c1.push_back( 7 );
   c1.push_back( 8 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove_if( is_odd<int>( ) );

   cout << "After removing the odd elements, "
        << "the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 3 4 5 6 7 8
After removing the odd elements, the list becomes c2 = 4 6 8
```

## <a name="rend"></a><a name="rend"></a> rend

Gibt ein Iterator zurück, der den Standort adressiert, der dem letzten Element in einer umgekehrten Liste nachfolgt.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der den Standort anspricht, der dem letzten Element in einer umgekehrten Liste nachfolgt (der Speicherort, der dem ersten Element in der nicht umgekehrten Liste vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einer umgekehrten Liste auf die gleiche Weise verwendet, wie [end](#end) bei einer Liste verwendet wird.

Wenn `rend` dem Rückgabewert von `const_reverse_iterator` zugewiesen wird, kann das Listenobjekt nicht geändert werden. Wenn `rend` dem Rückgabewert von `reverse_iterator` zugewiesen wird, kann das Listenobjekt geändert werden.

`rend` kann verwendet werden, um zu testen, ob das Ende der Liste von einem umgekehrten Iterator erreicht wurde.

Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// list_rend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error would
   // have resulted in the line modifying an element (commented below)
   // because the iterator would have been const
   // list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_rIter << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rend can be used to test if an iteration is through all of the
   // elements of a reversed list
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--;  // Decrementing the reverse iterator moves it backward
                // in the reversed list (to the last element here)

*c1_rIter = 40;  // This modification of the last element would have
                    // caused an error if a const_reverse iterator had
                    // been declared (as noted above)

   cout << "The modified reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;
}
```

```Output
The first element in the list is: 10
The list is: 10 20 30
The reversed list is: 30 20 10
The modified reversed list is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> Größe

Gibt eine neue Größe für eine Liste an.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parameter

*_Newsize*\
Die neue Größe der verknüpften Liste.

*ster*\
Der Wert der neuen, der Liste hinzuzufügenden Elemente, wenn die neue Größe die ursprüngliche Größe überschreitet. Wenn der Wert ausgelassen wird, werden dem Standardwert die neuen Elemente für die Klasse zugewiesen.

### <a name="remarks"></a>Bemerkungen

Wenn die Größe der Liste kleiner als die angeforderte Größe ist, *_Newsize*werden der Liste Elemente hinzugefügt, bis Sie die angeforderte Größe erreicht.

Wenn die Größe der Liste die angeforderte Größe überschreitet, werden die Elemente, die dem Ende der Liste am nächsten sind, gelöscht, bis die Liste die Größe *_Newsize*erreicht.

Wenn die vorhandene Größe der Liste der angeforderten Größe entspricht, wird keine Aktion durchgeführt.

[size](#size) gibt die aktuelle Größe der Liste wider.

### <a name="example"></a>Beispiel

```cpp
// list_resize.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is 4
The value of the last element is 40
The size of c1 is now 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse"></a><a name="reverse"></a> umgekehr

Kehrt die Reihenfolge um, in der die Elemente in einer Liste auftreten.

```cpp
void reverse();
```

### <a name="example"></a>Beispiel

```cpp
// list_reverse.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.reverse( );
   cout << "Reversed c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
c1 = 10 20 30
Reversed c1 = 30 20 10
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einer umgekehrten Liste gelesen oder geändert werden kann.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `reverse_iterator`-Typ wird verwendet, um die Liste in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [rbegin](#rbegin).

## <a name="size"></a><a name="size"></a> Größe

Gibt die Anzahl von Elementen in einer Liste zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge der Liste.

### <a name="example"></a>Beispiel

```cpp
// list_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   c1.push_back( 5 );
   i = c1.size( );
   cout << "List length is " << i << "." << endl;

   c1.push_back( 7 );
   i = c1.size( );
   cout << "List length is now " << i << "." << endl;
}
```

```Output
List length is 1.
List length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Ein Typ, der die Anzahl von Elementen in einer Liste zählt.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [size](#size).

## <a name="sort"></a><a name="sort"></a> Gefährtin

Ordnet die Elemente einer Liste in aufsteigender Reihenfolge oder in Bezug auf eine andere benutzerdefinierte Reihenfolge.

```cpp
void sort();

template <class Traits>
    void sort(Traits comp);
```

### <a name="parameters"></a>Parameter

*zuschreiben*\
Der zum Sortieren aufeinanderfolgender Elemente verwendete Vergleichsoperator.

### <a name="remarks"></a>Bemerkungen

Mit der ersten Memberfunktion werden die Elemente standardmäßig in eine aufsteigende Reihenfolge gebracht.

Die Member-Vorlagen Funktion ordnet die Elemente gemäß dem vom Benutzer angegebenen Vergleichs Vorgang *Comp* der Klasse an `Traits` .

### <a name="example"></a>Beispiel

```cpp
// list_sort.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 20 );
   c1.push_back( 10 );
   c1.push_back( 30 );

   cout << "Before sorting: c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( );
   cout << "After sorting c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( greater<int>( ) );
   cout << "After sorting with 'greater than' operation, c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
Before sorting: c1 = 20 10 30
After sorting c1 = 10 20 30
After sorting with 'greater than' operation, c1 = 30 20 10
```

## <a name="splice"></a><a name="splice"></a> Splice

Entfernt Elemente aus einer Quellliste und fügt sie in eine Zielliste ein.

```cpp
// insert the entire source list
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source);

// insert one element of the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);

// insert a range of elements from the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```

### <a name="parameters"></a>Parameter

*Was*\
Die Position in der Zielliste, vor der die Elemente eingefügt werden sollen.

*Ausgangs*\
Die Quellliste, die in die Zielliste eingefügt werden soll.

*Verstärkt*\
Das Element, das aus der Quellliste eingefügt werden soll.

*Erstes*\
Das erste Element im Bereich, das aus der Quellliste eingefügt werden soll.

*Letzten*\
Die erste Position hinter dem letzten Element im Bereich, das aus der Quellliste eingefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Das erste Paar von Element Funktionen fügt alle Elemente in der Quell Liste vor der Position, auf die von *Where* verwiesen wird, in die Zielliste ein und entfernt alle Elemente aus der Quell Liste. ( `&Source` darf nicht gleich sein **`this`** .)

Das zweite Paar von Element Funktionen fügt das Element, auf das der *ITER* verweist, vor der Position in der Zielliste ein, auf die von *Where* verwiesen wird, und entfernt *ITER* aus der Quell Liste. (Wenn `Where == Iter || Where == ++Iter` ist, findet keine Änderung statt.)

Das dritte Paar von Element Funktionen fügt den von [ `First` ,) angegebenen Bereich `Last` vor dem-Element in der Zielliste ein, auf die von *Where* verwiesen wird, und entfernt den Bereich von Elementen aus der Quell Liste. (Wenn `&Source == this` , darf der Bereich `[First, Last)` nicht das Element enthalten, auf das von *Where*verwiesen wird.)

Wenn der Bereichs-Splice `N`-Elemente und `&Source != this` einfügt, wird ein Objekt der [iterator](../standard-library/forward-list-class.md#iterator)-Klasse um das `N`-vergrößert erhöht.

In allen diesen Fällen bleiben Iteratoren, Zeiger oder Verweise, die auf zusammengeführte Elemente verweisen, gültig und werden in den Zielcontainer übertragen.

### <a name="example"></a>Beispiel

```cpp
// list_splice.cpp
// compile with: /EHsc /W4
#include <list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    list<int> c1{10,11};
    list<int> c2{20,21,22};
    list<int> c3{30,31};
    list<int> c4{40,41,42,43};

    list<int>::iterator where_iter;
    list<int>::iterator first_iter;
    list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    --last_iter;
    c2.splice(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)
```

## <a name="swap"></a><a name="swap"></a> Wechsel

Tauscht die Elemente zweier Listen aus.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>Parameter

*Richting*\
Die Liste, in der die auszutauschenden Elemente bereitgestellt werden, oder die Liste, deren Elemente mit denen der Liste nach *Links*ausgetauscht werden sollen.

*linken*\
Eine Liste, deren Elemente mit denen der Liste *Rechts*ausgetauscht werden sollen.

### <a name="example"></a>Beispiel

```cpp
// list_swap.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original list c1 is: 1 2 3
After swapping with c2, list c1 is: 10 20
After swapping with c3, list c1 is: 100
```

## <a name="unique"></a><a name="unique"></a> gem

Entfernt benachbarte doppelte Elemente oder benachbarte Elemente, die einige andere binäre Prädikate aus einer Liste erfüllen.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*pred*\
Das binäre Prädikat, das zum Vergleichen von aufeinander folgenden Elementen verwendet wird.

### <a name="remarks"></a>Bemerkungen

Bei dieser Funktion wird davon ausgegangen, dass die Liste sortiert ist, sodass alle doppelten Elemente benachbart sind. Duplikate, die nicht nebeneinander angezeigt werden, werden nicht gelöscht.

Die erste Memberfunktion entfernt jedes Element, das mit dem vorherigen Element übereinstimmt.

Die zweite Member-Funktion entfernt jedes Element, das die Prädikat Funktion *pred* erfüllt, im Vergleich zum vorherigen Element. Sie können alle binären Funktions Objekte verwenden, die im \<functional> -Header für das Argument " *pred* " deklariert sind, oder Sie können eine eigene erstellen.

### <a name="example"></a>Beispiel

```cpp
// list_unique.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;
   not_equal_to<int> mypred;

   c1.push_back( -10 );
   c1.push_back( 10 );
   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 20 );
   c1.push_back( -10 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.unique( );
   cout << "After removing successive duplicate elements, c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   list <int> c3 = c2;
   c3.unique( mypred );
   cout << "After removing successive unequal elements, c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = -10 10 10 20 20 -10
After removing successive duplicate elements, c2 = -10 10 20 -10
After removing successive unequal elements, c3 = -10 -10
```

## <a name="value_type"></a><a name="value_type"></a> value_type

Ein Typ, der den in einer Liste gespeicherten Datentyp darstellt.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Bemerkungen

`value_type` ist ein Synonym für den Vorlagenparameter *type*.

### <a name="example"></a>Beispiel

```cpp
// list_value_type.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```
