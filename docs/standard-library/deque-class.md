---
title: deque-Klasse
ms.date: 11/04/2016
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
ms.openlocfilehash: 1edcabf526d0f3aa2ba52ba3fd0fc656c5ae6b9c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838544"
---
# <a name="deque-class"></a>deque-Klasse

Ordnet Elemente eines angegebenen Typs in einer linearen Anordnung an, und aktiviert, wie ein Vektor, schnellen zufälligen Zugriff auf jedes Element sowie effizientes Einfügen und Löschen auf der Rückseite des Containers. Im Gegensatz zu einem Vektor, unterstützt die `deque`-Klasse allerdings auch das effiziente Einfügen und Löschen im Vordergrund des Containers.

## <a name="syntax"></a>Syntax

```unstlib
template <class Type, class Allocator =allocator<Type>>
class deque
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der in der Doppelschlange zu speichernde Elementdatentyp.

*Allocator*\
Der Typ, der das gespeicherte Zuordnungsobjekt darstellt, das Details zum Belegen und Freigeben des Arbeitsspeichers der Doppelschlange kapselt. Dieses Argument ist optional, und der Standardwert ist " **zuordcator \<Type> **".

## <a name="remarks"></a>Bemerkungen

Die Auswahl des Containertyps sollte im Allgemeinen auf Grundlage des für die Anwendung erforderlichen Suchen und Einfügetyps erfolgen. Als Container zum Verwalten einer Sequenz sollten bevorzugt [Vektoren](../standard-library/vector-class.md) verwendet werden, wenn es darauf ankommt, dass auf alle Elemente direkt zugegriffen werden kann, und wenn Elemente nur am Ende einer Sequenz eingefügt oder gelöscht werden müssen. Die Leistung des list-Containers ist optimal, wenn Elemente konstant an jeder Stelle innerhalb der Sequenz effizient eingefügt und gelöscht werden können. Solche Vorgänge in der Mitte der Sequenz benötigen Elementkopien und -Zuweisungen, die zur Anzahl von Elementen in der Sequenz proportional sind (lineare Zeit).

Die Neuzuordnung von Doppelschlangen tritt auf, wenn Elemente der Sequenz von einer Memberfunktion eingefügt oder gelöscht werden müssen:

- Beim Einfügen eines Elements in eine leere Sequenz bzw. beim Löschen eines Elements zum Verlassen einer leeren Sequenz, werden Iteratoren ungültig, die bisher von [begin](#begin) und [end](#end) zurückgegeben wurden.

- Wenn ein Element an der ersten Position der Doppelschlange eingefügt wird, werden anschließend alle Iteratoren, allerdings keine Verweise, die vorhandene Elemente festlegen, ungültig.

- Wenn ein Element am Ende der Doppelschlange eingefügt wird, werden mit Ausnahme von Verweisen [end](#end) und alle Iteratoren ungültig, mit denen vorhandene Elemente festgelegt werden.

- Wenn ein Element im Vordergrund der Doppelschlange gelöscht wird, werden nur dieser Iterator und die Verweise auf das gelöschte Element ungültig.

- Wenn das letzte Element am Ende der Doppelschlange gelöscht wird, werden nur dieser Iterator am letzen Element und die Verweise auf das gelöschte Element ungültig.

Andernfalls werden alle Iteratoren und Verweise durch das Einfügen und Löschen eines Elements und ungültig.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[deque](#deque)|Erstellt ein Objekt vom Typ `deque`. Es werden mehrere Konstruktoren bereitgestellt, um den Inhalt der neuen `deque` auf unterschiedliche Weise einzurichten: leer, mit einer angegebenen Anzahl leerer Elemente geladen, Inhalte verschoben oder aus anderen kopiert, `deque` Inhalte, die mit einem Iterator kopiert oder verschoben wurden, und ein Element, das in die Zeiten kopiert wurde `deque` `count` . Einige der Konstruktoren ermöglichen die Verwendung eines benutzerdefinierten `allocator` zum Erstellen von Elementen.|

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[allocator_type](#allocator_type)|Ein Typ, der die `allocator`-Klassentyp für das `deque`-Objekt darstellt.|
|[const_iterator](#const_iterator)|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem auf Elemente in der als zugegriffen werden kann. `deque`**`const`**|
|[const_pointer](#const_pointer)|Ein Typ, der einen Zeiger auf ein Element in einer `deque`-als `const.` bereitstellt.|
|[const_reference](#const_reference)|Ein Typ, der einen Verweis auf ein Element in einer `deque` zum Lesen und für andere Vorgänge als `const.` bereitstellt|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, der auf Elemente in der als zugreifen und diese lesen kann `deque` **`const`** . Die Doppelschlange wird umgekehrt angezeigt. Weitere Informationen finden Sie unter [reverse_iterator-Klasse](../standard-library/reverse-iterator-class.md).|
|[difference_type](#difference_type)|Ein Typ, der den Unterschied zwischen zwei Iteratoren mit zufälligem Zugriff, die auf Elemente in derselben `deque` verweisen, bereitstellt.|
|[Iterator](#iterator)|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem jedes Element in einer `deque` gelesen oder geändert werden kann.|
|[Zeichner](#pointer)|Ein Typ, der einen Zeiger auf ein Element in einer `deque` bereitstellt.|
|[Referenz](#reference)|Ein Typ, der einen Verweis auf ein in einer `deque` gespeichertes Element bereitstellt.|
|[reverse_iterator](#reverse_iterator)|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem ein Element in einer `deque` gelesen oder geändert werden kann. Die Doppelschlange wird in umgekehrter Reihenfolge angezeigt.|
|[size_type](#size_type)|Ein Typ, der die Anzahl von Elementen in einer `deque` zählt.|
|[value_type](#value_type)|Ein Typ, der den in einer `deque` gespeicherten Datentyp darstellt.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[assign](#assign)|Löscht Elemente aus einer `deque` und kopiert eine neue Sequenz von Elementen in die Ziel-`deque`.|
|[at](#at)|Gibt einen Verweis auf das Element an einer angegebenen Position in der `deque` zurück.|
|[Zurück](#back)|Gibt einen Verweis auf das letzte Element der `deque` zurück.|
|[beginnen](#begin)|Gibt ein Iterator mit zufälligem Zugriff zurück, der das erste Element in der `deque` adressiert.|
|[cbegin](#cbegin)|Gibt einen const-Iterator auf das erste Element im `deque`-Objekt zurück.|
|[cend](#cend)|Gibt einen Iterator mit zufälligem Zugriff zurück **`const`** , der direkt hinter das Ende der verweist `deque` .|
|[Löschen](#clear)|Löscht alle Elemente einer `deque` auf.|
|[crbegin](#crbegin)|Gibt einen direkten const-Iterator mit zufälligem Zugriff zum ersten Element in der `deque` zurück, das in umgekehrter Reihenfolge angezeigt wird.|
|[crend](#crend)|Gibt einen direkten const-Iterator mit zufälligem Zugriff zum ersten Element in der `deque` zurück, das in umgekehrter Reihenfolge angezeigt wird.|
|[emplace](#emplace)|Fügt ein direkt konstruiertes Element an einer angegebenen Position in die `deque` ein.|
|[emplace_back](#emplace_back)|Fügt ein direkt konstruiertes Element am Ende der `deque` ein.|
|[emplace_front](#emplace_front)|Fügt ein direkt konstruiertes Element am Anfang der `deque` ein.|
|[empty](#empty)|Gibt zurück **`true`** , wenn die `deque` Elemente 0 (null) enthält, und, **`false`** Wenn Sie ein oder mehrere-Elemente enthält.|
|[end](#end)|Gibt einen Iterator mit zufälligem Zugriff zurück, der auf eine Position unmittelbar nach dem Ende der `deque` verweist.|
|[erase](#erase)|Entfernt ein Element oder eine Reihe von Elementen in einer `deque` aus angegebenen Speicherorten.|
|[Beifahrer](#front)|Gibt einen Verweis auf das erste Element in einer `deque` zurück.|
|[get_allocator](#get_allocator)|Gibt eine Kopie des zum Erstellen der `allocator` verwendeten `deque`-Objekts zurück.|
|[insert](#insert)|Fügt ein Element, mehrere Elemente oder einen Reihe von Elementen an einer angegebenen Position in die `deque` ein.|
|[max_size](#max_size)|Gibt die mögliche Maximallänge der `deque` zurück.|
|[pop_back](#pop_back)|Löscht das Element am Ende der `deque`.|
|[pop_front](#pop_front)|Löscht das Element am Anfang der `deque`.|
|[push_back](#push_back)|Fügt am Ende der `deque` ein Element hinzu.|
|[push_front](#push_front)|Fügt am Anfang der `deque` ein Element hinzu.|
|[rbegin](#rbegin)|Gibt dem ersten Element einen Iterator mit zufälligem Zugriff in umgekehrter `deque` zurück.|
|[rend](#rend)|Gibt einen Iterator mit zufälligem Zugriff zurück, der grade über das letzte Element in einer umgekehrten `deque` zeigt.|
|[Größe](#resize)|Gibt eine neue Größe für eine `deque` an.|
|[shrink_to_fit](#shrink_to_fit)|Verwirft Überkapazität.|
|[size](#size)|Gibt die Anzahl von Elementen in der `deque` zurück.|
|[swap](#swap)|Tauscht die Elemente zweier `deque`n.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[operator&#91;&#93;](#op_at)|Gibt einen Verweis auf das `deque`-Element an einer angegebenen Position zurück.|
|[Operator =](#op_eq)|Ersetzt die Elemente der `deque` mit einer Kopie einer anderen `deque`.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

Ein Typ, der die Zuweisungsklasse für das deque-Objekt darstellt.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Bemerkungen

`allocator_type` ist ein Synonym für den Vorlagenparameter `Allocator`.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [get_allocator](#get_allocator).

## <a name="assign"></a><a name="assign"></a> einräumen

Löscht Elemente aus einer Doppelschlange und kopiert einen neuen Satz von Elementen in die Zieldoppelschlange.

```cpp
template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);

void assign(
    size_type Count,
    const Type& Val);

void assign(initializer_list<Type> IList);
```

### <a name="parameters"></a>Parameter

*Erstes*\
Die Position des ersten Elements in dem aus der Argumentdoppelschlange zu kopierenden Elementbereich.

*Letzten*\
Die Position des ersten Elements hinter dem aus der Argumentdoppelschlange zu kopierenden Elementbereich.

*Countdown*\
Die Anzahl von Kopien eines Elements, das in die Doppelschlange eingefügt wird.

*Ster*\
Der Wert des Elements, das in die Doppelschlange eingefügt wird.

*IList*\
Das initializer_list-Element, das in die Doppelschlange eingefügt wird.

### <a name="remarks"></a>Bemerkungen

Nachdem alle vorhandenen Elemente in der Zieldoppelschlange gelöscht sind, wird von `assign` entweder ein angegebener Elementbereich aus der ursprünglichen oder einer anderen Doppelschlange in die Zieldoppelschlange eingefügt, oder es werden Kopien eines neuen Elements eines angegebenen Werts in die Zieldoppelschlange eingefügt.

### <a name="example"></a>Beispiel

```cpp
// deque_assign.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <initializer_list>

int main()
{
    using namespace std;
    deque <int> c1, c2;
    deque <int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    deque<int> d1{ 1, 2, 3, 4 };
    initializer_list<int> iList{ 5, 6, 7, 8 };
    d1.assign(iList);

    cout << "d1 = ";
    for (int i : d1)
        cout << i;
    cout << endl;

    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (int i : c1)
        cout << i;
    cout << endl;
}
```

```Output
d1 = 5678c1 =102030c1 =5060c1 =4444444
```

## <a name="at"></a><a name="at"></a> an

Gibt einen Verweis auf das Element an einer angegebenen Position in der Doppelschlange zurück.

```cpp
reference at(size_type pos);

const_reference at(size_type pos) const;
```

### <a name="parameters"></a>Parameter

*POS*\
Der Feldindex (oder die Positionsnummer) des Elements, das auf die Doppelschlange verweisen soll.

### <a name="return-value"></a>Rückgabewert

Wenn *POS* größer als die Größe der Doppel Schlange ist, wird von `at` eine Ausnahme ausgelöst.

### <a name="return-value"></a>Rückgabewert

Wenn der Rückgabewert von `at` einem `const_reference` zugewiesen wird, kann das deque-Objekt nicht geändert werden. Wenn der Rückgabewert von `at` einem `reference` zugewiesen wird, kann das deque-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// deque_at.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int& i = c1.at( 0 );
   int& j = c1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a><a name="back"></a> Zurück

Gibt einen Verweis auf das letzte Element der Doppelschlange zurück.

```cpp
reference back();
const_reference back() const;
```

### <a name="return-value"></a>Rückgabewert

Das letzte Element der Doppelschlange. Wenn die Doppelschlange leer ist, ist der Rückgabewert nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `back` einem `const_reference` zugewiesen wird, kann das deque-Objekt nicht geändert werden. Wenn der Rückgabewert von `back` einem `reference` zugewiesen wird, kann das deque-Objekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element in einer leeren Doppelschlange ein Laufzeitfehler auf.  Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md) .

### <a name="example"></a>Beispiel

```cpp
// deque_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

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

Gibt einen Iterator zurück, der das erste Element in der Doppelschlange adressiert.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator mit direktem Zugriff, der das erste Element in der Doppelschlange adressiert oder auf die Position zeigt, der auf eine leere Doppelschlange folgt.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `begin` einem `const_iterator` zugewiesen wird, kann das deque-Objekt nicht geändert werden. Wenn der Rückgabewert von `begin` einem zugewiesen wird `iterator` , kann das Debug-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// deque_begin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::const_iterator c1_cIter;

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

Ein **`const`** Random-Access-Iterator, der auf das erste Element des Bereichs zeigt oder die Position direkt hinter dem Ende eines leeren Bereichs (für einen leeren Bereich `cbegin() == cend()` ).

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

Ein Random-Access-Iterator, der auf eine Position unmittelbar nach dem Ende des Bereichs verweist.

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

Löscht alle Elemente einer Doppelschlange auf.

```cpp
void clear();
```

### <a name="example"></a>Beispiel

```cpp
// deque_clear.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the deque is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the deque is initially 3
The size of the deque after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, **`const`** der auf ein-Element in der Doppel Schlange zugreifen und es lesen kann.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_iterator`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [back](#back).

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Stellt einen Zeiger auf ein- **`const`** Element in einer Doppel Schlange bereit.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_pointer`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden. Ein [Iterator](#iterator) wird häufiger für den Zugriff auf ein deque-Element verwendet.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einer Doppel Schlange zum Lesen und Ausführen von **`const`** Vorgängen gespeichert ist.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reference`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

```cpp
// deque_const_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const deque <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem jedes beliebige Element in der Doppel Schlange gelesen werden kann **`const`** .

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reverse_iterator`-Typ kann nicht den Wert eines Elements ändern und wird verwendet, um die Doppelschlange in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Im Beispiel für [rbegin](#rbegin) wird verdeutlicht, wie ein Iterator deklariert und verwendet wird.

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

Gibt einen const-Iterator zum ersten Element in einer umgekehrten Doppelschlange zurück.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter const-Iterator mit direktem Zugriff, mit dem das erste Element in einer umgekehrten [deque](../standard-library/deque-class.md) adressiert wird (bzw. mit dem das ehemals letzte Element in der nicht umgekehrten `deque` adressiert wird).

### <a name="remarks"></a>Bemerkungen

Bei dem Rückgabewert von `crbegin` kann das `deque`-Objekt nicht geändert werden.

### <a name="example"></a>Beispiel

```cpp
// deque_crbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator v1_Iter;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of deque is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed deque is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of deque is 1.
The first element of the reversed deque is 2.
```

## <a name="crend"></a><a name="crend"></a> crend

Gibt einen const-Iterator zurück, mit dem die Position adressiert wird, die dem letzten Element einer umgekehrten Doppelschlange folgt.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein const_reverse-Iterator mit direktem Zugriff, mit dem die Position adressiert wird, die dem letzten Element in einer umgekehrten [deque](../standard-library/deque-class.md) folgt (die Position, die dem ersten Element in der nicht umgekehrten Doppelschlange vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einer umgekehrten `deque` auf die gleiche Weise verwendet, wie [array::cend](../standard-library/array-class-stl.md#cend) bei einer `deque` verwendet wird.

Mit dem Rückgabewert von `crend` (entsprechend verringert) kann das `deque`-Objekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob das Ende der Doppelschlange von einem umgekehrten Iterator erreicht wurde.

Der von `crend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// deque_crend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="deque"></a><a name="deque"></a> Deque

Die Anzahl von Elementen in der erstellten Liste.

```cpp
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,
    const Type& Val,
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>
deque(
   InputIterator First,
   InputIterator Last,
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```

### <a name="parameters"></a>Parameter

*Irdische*\
Die mit diesem Objekt zu verwendende Zuweisungsklasse.

*Countdown*\
Die Anzahl von Elementen in der erstellten Doppelschlange.

*Ster*\
Der Wert der Elemente in der erstellten Doppelschlange.

*Richting*\
Die Doppelschlange, deren Kopie die erstellte Doppelschlange ist.

*Erstes*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*Letzten*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*IList*\
Das zu kopierende initializer_list-Element.

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren speichern ein*Zuordnungs*Objekt (Al) und initialisieren die Doppel Schlange.

Die ersten beiden Konstruktoren geben eine leere ursprüngliche Doppelschlange an, der zweite gibt auch den zu verwendenden Belegungsfunktionstyp (`_Al`).

Der dritte Konstruktor gibt eine Wiederholung einer angegebenen Anzahl (`count`) von Elementen des Standardwerts für die Klasse `Type` an.

Der vierte und fünfte Konstruktoren geben eine Wiederholung von-Elementen (*count*) von value an `val` .

Der sechste Konstruktor gibt eine Kopie der Doppel Schlange *Rechts*an.

Mit den siebten und achten Konstruktoren wird der Bereich `[First, Last)` einer Doppelschlange kopiert.

Der siebte Konstruktor verschiebt die Doppel Schlange nach *Rechts*.

Der achte Konstruktor kopiert den Inhalt eines initializer_list-Elements.

Keine der Konstruktoren führen Zwischenneuzuordnungen aus.

### <a name="example"></a>Beispiel

```cpp
/ compile with: /EHsc
#include <deque>
#include <iostream>
#include <forward_list>

int main()
{
    using namespace std;

    forward_list<int> f1{ 1, 2, 3, 4 };

    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });

    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1(3);

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2(5, 2);

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3(3, 1, c2.get_allocator());

    // Create a copy, deque c4, of deque c2
    deque <int> c4(c2);

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    deque <int> c5(c4.begin(), c4_Iter);

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

    initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for (int i : c1)
        cout << i << " ";
    cout << endl;

    cout << "c2 = ";
    for (int i : c2)
        cout << i << " ";
    cout << endl;

    cout << "c3 = ";
    for (int i : c3)
        cout << i << " ";
    cout << endl;

    cout << "c4 = ";
    for (int i : c4)
        cout << i << " ";
    cout << endl;

    cout << "c5 = ";
    for (int i : c5)
        cout << i << " ";
    cout << endl;

    cout << "c6 = ";
    for (int i : c6)
        cout << i << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7(move(c6));
    deque <int>::iterator c7_Iter;

    cout << "c7 =";
    for (int i : c7)
        cout << i << " ";
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    for (int i : c9)
        cout << i << " ";
    cout << endl;

    int x = 3;
}
// deque_deque.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
    using namespace std;
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;

    // Create an empty deque c0
    deque <int> c0;

    // Create a deque c1 with 3 elements of default value 0
    deque <int> c1( 3 );

    // Create a deque c2 with 5 elements of value 2
    deque <int> c2( 5, 2 );

    // Create a deque c3 with 3 elements of value 1 and with the
    // allocator of deque c2
    deque <int> c3( 3, 1, c2.get_allocator( ) );

    // Create a copy, deque c4, of deque c2
    deque <int> c4( c2 );

    // Create a deque c5 by copying the range c4[ first,  last)
    c4_Iter = c4.begin( );
    c4_Iter++;
    c4_Iter++;
    deque <int> c5( c4.begin( ), c4_Iter );

    // Create a deque c6 by copying the range c4[ first,  last) and
    // c2 with the allocator of deque
    c4_Iter = c4.begin( );
   c4_Iter++;
   c4_Iter++;
   c4_Iter++;
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );

    // Create a deque c8 by copying the contents of an initializer_list
    // using brace initialization
    deque<int> c8({ 1, 2, 3, 4 });

        initializer_list<int> iList{ 5, 6, 7, 8 };
    deque<int> c9( iList);

    cout << "c1 = ";
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
        cout << *c1_Iter << " ";
    cout << endl;

    cout << "c2 = ";
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
        cout << *c2_Iter << " ";
    cout << endl;

    cout << "c3 = ";
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
        cout << *c3_Iter << " ";
    cout << endl;

    cout << "c4 = ";
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )
        cout << *c4_Iter << " ";
    cout << endl;

    cout << "c5 = ";
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )
        cout << *c5_Iter << " ";
    cout << endl;

    cout << "c6 = ";
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )
        cout << *c6_Iter << " ";
    cout << endl;

    // Move deque c6 to deque c7
    deque <int> c7( move(c6) );
    deque <int>::iterator c7_Iter;

    cout << "c7 =" ;
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )
        cout << " " << *c7_Iter;
    cout << endl;

    cout << "c8 = ";
    for (int i : c8)
        cout << i << " ";
    cout << endl;

    cout << "c9 = ";
    or (int i : c9)
        cout << i << " ";
    cout << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Ein Typ, der den Unterschied zwischen zwei Iteratoren bereitstellt, die auf Elemente innerhalb derselben Doppelschlange verweisen.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

Ein `difference_type` kann auch als die Anzahl der Elemente zwischen zwei Zeigern beschrieben werden.

### <a name="example"></a>Beispiel

```cpp
// deque_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <deque>
#include <algorithm>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   deque <int>::difference_type df_typ1, df_typ2, df_typ3;

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

Fügt ein direkt konstruiertes Element an einer angegebenen Position in die Doppelschlange ein.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parameter

*_Where*\
Die Position in der [Doppelschlange](../standard-library/deque-class.md), an der das erste Element eingefügt wird.

*ster*\
Der Wert des Elements, das in den `deque` eingefügt wird.

### <a name="return-value"></a>Rückgabewert

Die Funktion gibt einen Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element in die Doppelschlange eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Einfügevorgänge können sehr speicherintensiv sein. Eine Abhandlung zur Leistung von `deque` finden Sie unter `deque`.

### <a name="example"></a>Beispiel

```cpp
// deque_emplace.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   deque <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a><a name="emplace_back"></a> emplace_back

Fügt ein direkt konstruiertes Element am Ende der Doppelschlange ein.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das Element, das am Ende der [Doppelschlange](../standard-library/deque-class.md) hinzugefügt wird.

### <a name="example"></a>Beispiel

```cpp
// deque_emplace_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_back( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

Fügt ein direkt konstruiertes Element am Ende der Doppelschlange ein.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das Element, das am [Anfang der Doppel](../standard-library/deque-class.md)Schlange hinzugefügt wird.

### <a name="example"></a>Beispiel

```cpp
// deque_emplace_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;

   v1.push_back( 1 );
   if ( v1.size( ) != 0 )
      cout << "Last element: " << v1.back( ) << endl;

   v1.push_back( 2 );
   if ( v1.size( ) != 0 )
      cout << "New last element: " << v1.back( ) << endl;

// initialize a deque of deques by moving v1
   deque < deque <int> > vv1;

   vv1.emplace_front( move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      cout << "Moved last element: " << vv1[0].back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved last element: 2
```

## <a name="empty"></a><a name="empty"></a> leer

Testet, ob eine Doppelschlange leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die Doppel Schlange leer ist. , **`false`** Wenn die Doppel Schlange nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// deque_empty.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The deque is empty." << endl;
   else
      cout << "The deque is not empty." << endl;
}
```

```Output
The deque is not empty.
```

## <a name="end"></a><a name="end"></a> Schließlich

Gibt einen Iterator zurück, mit dem die Position adressiert wird, die dem letzten Element einer Doppelschlange folgt.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator mit direktem Zugriff, mit dem die Position adressiert wird, die dem letzten Element einer Doppelschlange folgt. Wenn die Doppelschlange leer ist, gilt: deque::end == deque::begin.

### <a name="remarks"></a>Bemerkungen

`end` wird verwendet, um zu testen, ob ein Iterator das Ende der Doppel Schlange erreicht hat.

### <a name="example"></a>Beispiel

```cpp
// deque_end.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
   *c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // deque <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The deque is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The deque is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> Löschen

Entfernt ein Element oder eine Reihe von Elementen in einer Doppelschlange aus angegebenen Positionen.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parameter

*_Where*\
Die Position des Elements, das in der Doppelschlange entfernt werden soll.

*erstes*\
Die Position des ersten Elements, das in der Doppelschlange entfernt werden soll.

*letzten*\
Die Position direkt nach dem letzten in der Doppelschlange entfernten Element.

### <a name="return-value"></a>Rückgabewert

Ein Iterator mit direktem Zugriff, mit dem das erste über die entfernten Elemente hinaus verbliebene Element festgelegt wird, oder ein Zeiger, mit dem das Ende der Doppelschlange dargestellt wird, wenn kein solches Element vorhanden ist.

### <a name="remarks"></a>Bemerkungen

`erase` löst nie eine Ausnahme aus.

### <a name="example"></a>Beispiel

```cpp
// deque_erase.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial deque is: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the deque becomes:  ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, deque becomes: ";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << *Iter << " ";
   cout << endl;
}
```

```Output
The initial deque is: 10 20 30 40 50
After erasing the first element, the deque becomes:  20 30 40 50
After erasing all elements but the first, deque becomes: 20
```

## <a name="front"></a><a name="front"></a> Beifahrer

Gibt einen Verweis auf das erste Element in einer Doppelschlange zurück.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn die Doppelschlange leer ist, ist die Rückgabe nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `front` einem `const_reference` zugewiesen wird, kann das deque-Objekt nicht geändert werden. Wenn der Rückgabewert von `front` einem `reference` zugewiesen wird, kann das deque-Objekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element in einer leeren Doppelschlange ein Laufzeitfehler auf.  Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md) .

### <a name="example"></a>Beispiel

```cpp
// deque_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.front( );
   const int& ii = c1.front( );

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The second integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Gibt eine Kopie des allocator-Objekts zurück, das zum Erstellen der Doppelschlange verwendet wird.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Das von der Doppelschlange verwendete allocator-Objekt.

### <a name="remarks"></a>Bemerkungen

Allocator-Objekte für die deque-Klasse geben an, wie die Klasse einen Speicher verwaltet. Für die meisten Programmieranforderungen reichen die Standard-Zuweisungen aus C++-Standardbibliothek-Containerklassen aus. Schreiben und Verwenden Ihrer eigener Zuweisungsklasse ist ein C++ -Thema für Fortgeschrittene.

### <a name="example"></a>Beispiel

```cpp
// deque_get_allocator.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   deque <int> c1;
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   deque <int> c3( c1.get_allocator( ) );

   deque <int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> setze

Fügt ein Element oder mehrere Elemente oder ein Reihe von Elementen an einer bestimmten Position in die Doppelschlange ein.

```cpp
iterator insert(
    const_iterator Where,
    const Type& Val);

iterator insert(
    const_iterator Where,
    Type&& Val);

void insert(
    iterator Where,
    size_type Count,
    const Type& Val);

template <class InputIterator>
void insert(
    iterator Where,
    InputIterator First,
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>
IList);
```

### <a name="parameters"></a>Parameter

*Was*\
Die Position in der Zieldoppelschlange, an der das erste Element eingefügt wird.

*Ster*\
Der Wert des Elements, das in die Doppelschlange eingefügt wird.

*Countdown*\
Die Anzahl von Elementen, die in die Doppelschlange eingefügt werden.

*Erstes*\
Die Position des ersten Elements in dem Elementbereich in der Argumentdoppelschlange, die kopiert werden soll.

*Letzten*\
Die Position des ersten Elements hinter dem Elementbereich in der Argumentdoppelschlange, die kopiert werden soll.

*IList*\
Das initializer_list-Element der einzufügenden Elemente.

### <a name="return-value"></a>Rückgabewert

Die ersten zwei Einfügefunktionen geben ein Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element in die Doppelschlange eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Jeder Einfügevorgang kann ressourcenintensiv sein.

## <a name="iterator"></a><a name="iterator"></a> Iterator

Ein Typ, der einen Iterator mit direktem Zugriff bereitstellt, mit dem jedes Element in einer Doppelschlange gelesen oder geändert werden kann.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein-Typ `iterator` kann zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [begin](#begin).

## <a name="max_size"></a><a name="max_size"></a> max_size

Gibt die Maximallänge der Doppelschlange zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die mögliche Maximallänge der Doppelschlange.

### <a name="example"></a>Beispiel

```cpp
// deque_max_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   i = c1.max_size( );
   cout << "The maximum possible length of the deque is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_at"></a> []-Operator

Gibt einen Verweis auf das deque-Element an einer angegebenen Position zurück.

```cpp
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```

### <a name="parameters"></a>Parameter

*POS*\
Die Position des deque-Elements, auf das verwiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Element, dessen Position im Argument angegeben wird. Wenn die angegebene Position größer oder gleich der Größe der Doppelschlange ist, ist das Ergebnis nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `operator[]` einem `const_reference` zugewiesen wird, kann das deque-Objekt nicht geändert werden. Wenn der Rückgabewert von `operator[]` einem `reference` zugewiesen wird, kann das deque-Objekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element außerhalb der Doppelschlange ein Laufzeitfehler auf.  Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md) .

### <a name="example"></a>Beispiel

```cpp
// deque_op_ref.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   cout << "The first integer of c1 is " << c1[0] << endl;
   int& i = c1[1];
   cout << "The second integer of c1 is " << i << endl;
}
```

```Output
The first integer of c1 is 10
The second integer of c1 is 20
```

## <a name="operator"></a><a name="op_eq"></a> Operator =

Ersetzt die Elemente für diese Doppelschlange mithilfe der Elemente aus einer anderen Doppelschlange.

```cpp
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die Doppelschlange, die den neuen Inhalt bereitstellt.

### <a name="remarks"></a>Bemerkungen

Die erste Überschreibung kopiert Elemente von *Rechts*in diese Doppel Schlange, die Quelle der Zuweisung. Mit der zweiten außer Kraft Setzung werden Elemente von *Rechts*in diese Doppel Schlange verschoben.

Elemente, die in dieser Doppelschlange enthalten sind, bevor der Operator ausgeführt wird, werden entfernt.

### <a name="example"></a>Beispiel

```cpp
// deque_operator_as.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
using namespace std;

typedef deque<int> MyDeque;

template<typename MyDeque> struct S;

template<typename MyDeque> struct S<MyDeque&> {
  static void show( MyDeque& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
    cout << endl;
  }
};

template<typename MyDeque> struct S<MyDeque&&> {
  static void show( MyDeque&& d ) {
    MyDeque::const_iterator iter;
    for (iter = d.cbegin(); iter != d.cend(); iter++)
       cout << *iter << " ";
cout << " via unnamed rvalue reference " << endl;
  }
};

int main( )
{
   MyDeque d1, d2;

   d1.push_back(10);
   d1.push_back(20);
   d1.push_back(30);
   d1.push_back(40);
   d1.push_back(50);

   cout << "d1 = " ;
   S<MyDeque&>::show( d1 );

   d2 = d1;
   cout << "d2 = ";
   S<MyDeque&>::show( d2 );

   cout << "     ";
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );
}
```

## <a name="pointer"></a><a name="pointer"></a>-Zeiger

Stellt einen Zeiger auf ein Element in einer [Doppelschlange](../standard-library/deque-class.md) bereit.

```unstlib
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein-Typ `pointer` kann zum Ändern des Werts eines Elements verwendet werden. Ein [Iterator](#iterator) wird häufiger für den Zugriff auf ein deque-Element verwendet.

## <a name="pop_back"></a><a name="pop_back"></a> pop_back

Löscht das Element am Ende der Doppelschlange.

```cpp
void pop_back();
```

### <a name="remarks"></a>Bemerkungen

Das letzte Element darf nicht leer sein. `pop_back` löst nie eine Ausnahme aus.

### <a name="example"></a>Beispiel

```cpp
// deque_pop_back.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the deque, the "
      "last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the deque, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

Löscht das Element am Anfang einer Doppelschlange.

```cpp
void pop_front();
```

### <a name="remarks"></a>Bemerkungen

Das erste Element darf nicht leer sein. `pop_front` löst nie eine Ausnahme aus.

### <a name="example"></a>Beispiel

```cpp
// deque_pop_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the "
      "deque, the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the deque, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> push_back

Fügt ein Element am Ende der Doppelschlange hinzu.

```cpp
void push_back(const Type& val);

void push_back(Type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das Element, das am Ende der Doppelschlange hinzugefügt wird.

### <a name="remarks"></a>Bemerkungen

Wenn eine Ausnahme ausgelöst wird, bleibt die Doppelschlange unverändert, und die Ausnahme wird erneut ausgelöst.

## <a name="push_front"></a><a name="push_front"></a> push_front

Fügt am Anfang einer Doppelschlange ein Element hinzu.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das am Anfang der Doppelschlange hinzugefügte Element.

### <a name="remarks"></a>Bemerkungen

Wenn eine Ausnahme ausgelöst wird, bleibt die Doppelschlange unverändert, und die Ausnahme wird erneut ausgelöst.

### <a name="example"></a>Beispiel

```cpp
// deque_push_front.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a deque of strings
   deque <string> c2;
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

Gibt einen Iterator an das erste Element in einer umgekehrten Doppelschlange zurück.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter Iterator mit direktem Zugriff, mit dem das erste Element in einer umgekehrten Doppelschlange adressiert wird (bzw. mit dem das ehemals letzte Element in der nicht umgekehrten Doppelschlange adressiert wird).

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einer umgekehrten Doppelschlange auf die gleiche Weise verwendet, wie [begin](#begin) bei einer Doppelschlange verwendet wird.

Wenn der Rückgabewert von `rbegin` einem `const_reverse_iterator` zugewiesen wird, kann das deque-Objekt nicht geändert werden. Wenn der Rückgabewert von `rbegin` einem `reverse_iterator` zugewiesen wird, kann das deque-Objekt geändert werden.

Mit `rbegin` kann eine Doppelschlange rückwärts durchlaufen werden.

### <a name="example"></a>Beispiel

```cpp
// deque_rbegin.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rbegin( );
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;

   cout << "The deque contains the elements: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << "in that order.";
   cout << endl;

   // rbegin can be used to iterate through a deque in reverse order
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rbegin( );
   *c1_rIter = 40;  // This would have caused an error if a
                    // const_reverse iterator had been declared as
                    // noted above
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;
}
```

```Output
Last element in the deque is 30.
The deque contains the elements: 10 20 30 in that order.
The reversed deque is: 30 20 10
Last element in deque is now 40.
```

## <a name="reference"></a><a name="reference"></a> Angabe

Ein Typ, der einen Verweis auf ein in einer Doppelschlange gespeichertes Element bereitstellt.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Beispiel

```cpp
// deque_reference.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="rend"></a><a name="rend"></a> rend

Gibt einen Iterator zurück, mit dem die Position adressiert wird, die dem letzten Element einer umgekehrten Doppelschlange folgt.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter Iterator mit direktem Zugriff, mit dem die Position adressiert wird, die dem letzten Element in einer umgekehrten Doppelschlange folgt (die Position, die dem ersten Element in der nicht umgekehrten Doppelschlange vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einer umgekehrten Doppelschlange auf die gleiche Weise verwendet, wie [end](#end) bei einer Doppelschlange verwendet wird.

Wenn der Rückgabewert von `rend` einem `const_reverse_iterator` zugewiesen wird, kann das deque-Objekt nicht geändert werden. Wenn der Rückgabewert von `rend` einem `reverse_iterator` zugewiesen wird, kann das deque-Objekt geändert werden.

`rend` kann verwendet werden, um zu testen, ob das Ende der Doppelschlange von einem umgekehrten Iterator erreicht wurde.

Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// deque_rend.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;

   deque <int> c1;
   deque <int>::iterator c1_Iter;
   deque <int>::reverse_iterator c1_rIter;
   // If the following line had replaced the line above, an error
   // would have resulted in the line modifying an element
   // (commented below) because the iterator would have been const
   // deque <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --; // Decrementing a reverse iterator moves it forward
                // in the deque (to point to the first element here)
   cout << "The first element in the deque is: " << *c1_rIter << endl;

   cout << "The deque is: ";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << *c1_Iter << " ";
   cout << endl;

   // rend can be used to test if an iteration is through all of
   // the elements of a reversed deque
   cout << "The reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--; // Decrementing the reverse iterator moves it backward
               // in the reversed deque (to the last element here)
   *c1_rIter = 40; // This modification of the last element would
                   // have caused an error if a const_reverse
                   // iterator had been declared (as noted above)
   cout << "The modified reversed deque is: ";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << *c1_rIter << " ";
   cout << endl;
}
```

```Output
The first element in the deque is: 10
The deque is: 10 20 30
The reversed deque is: 30 20 10
The modified reversed deque is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> Größe

Gibt für eine Doppelschlange eine neue Größe an.

```cpp
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parameter

*_Newsize*\
Die neue Größe der Doppelschlange.

*ster*\
Der Wert der neuen Elemente, die zur Doppelschlange hinzugefügt werden sollen, wenn die neue Größe die ursprüngliche Größe überschreitet. Wenn der Wert ausgelassen wird, werden dem Standardwert die neuen Elemente für die Klasse zugewiesen.

### <a name="remarks"></a>Bemerkungen

Wenn die Größe der Doppel Schlange kleiner ist als die angeforderte Größe, *_Newsize*werden Elemente der Doppel Schlange hinzugefügt, bis Sie die angeforderte Größe erreicht.

Wenn die Größe der Doppel Schlange größer ist als die angeforderte Größe, werden die Elemente, die dem Ende der Doppel Schlange am nächsten sind, gelöscht, bis die Doppel Schlange die Größe *_Newsize*erreicht.

Wenn die vorhandene Größe der Doppelschlange der angeforderten Größe entspricht, wird keine Aktion durchgeführt.

[size](#size) gibt die aktuelle Größe der Doppelschlange an.

### <a name="example"></a>Beispiel

```cpp
// deque_resize.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is: 4
The value of the last element is 40
The size of c1 is now: 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

Ein Typ, der einen Iterator mit direktem Zugriff bereitstellt, mit dem ein Element in einer umgekehrten Doppelschlange gelesen oder geändert werden kann.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `reverse_iterator`-Typ, der zum Durchlaufen der Doppelschlange verwendet wird.

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter rbegin.

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> shrink_to_fit

Verwirft Überkapazität.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Bemerkungen

Es gibt keine portierbare Möglichkeit festzustellen, ob mit `shrink_to_fit` der von einer [Doppelschlange](../standard-library/deque-class.md) belegte Speicher reduziert wird.

### <a name="example"></a>Beispiel

```cpp
// deque_shrink_to_fit.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> v1;
   //deque <int>::iterator Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
   v1.shrink_to_fit();
   cout << "Current size of v1 = "
      << v1.size( ) << endl;
}
```

```Output
Current size of v1 = 1
Current size of v1 = 1
```

## <a name="size"></a><a name="size"></a> Größe

Gibt die Anzahl der Elemente in der Doppelschlange zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge der Doppelschlange.

### <a name="example"></a>Beispiel

```cpp
// deque_size.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1;
   deque <int>::size_type i;

   c1.push_back( 1 );
   i = c1.size( );
   cout << "The deque length is " << i << "." << endl;

   c1.push_back( 2 );
   i = c1.size( );
   cout << "The deque length is now " << i << "." << endl;
}
```

```Output
The deque length is 1.
The deque length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Ein Typ, der die Anzahl von Elementen in einer Doppelschlange zählt.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [size](#size).

## <a name="swap"></a><a name="swap"></a> Wechsel

Tauscht die Elemente von zwei deque-Objekten aus.

```cpp
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die Doppelschlange, in der die auszutauschenden Elemente bereitgestellt werden, oder die Doppelschlange, deren Elemente mit denen der Doppelschlange `left` ausgetauscht werden sollen.

*linken*\
Eine Doppel Schlange, deren Elemente mit denen der Doppel Schlange nach *Rechts*ausgetauscht werden sollen.

### <a name="example"></a>Beispiel

```cpp
// deque_swap.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2, c3;
   deque <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap<>(c1, c2);
   cout << "After swapping with c2, deque c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original deque c1 is: 1 2 3
After swapping with c2, deque c1 is: 10 20
After swapping with c3, deque c1 is: 100
After swapping with c2, deque c1 is: 1 2 3
```

## <a name="value_type"></a><a name="value_type"></a> value_type

Ein Typ, der den in einer Doppelschlange gespeicherten Datentyp darstellt.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Bemerkungen

`value_type` ist ein Synonym für den Vorlagenparameter `Type`.

### <a name="example"></a>Beispiel

```cpp
// deque_value_type.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>
int main( )
{
   using namespace std;
   deque<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
