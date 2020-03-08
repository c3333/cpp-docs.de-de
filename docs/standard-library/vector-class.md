---
title: vector-Klasse
description: Verweis für die C++ Implementierung der Microsoft-Standard Bibliothek von Class Vector.
ms.date: 02/07/2020
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
ms.openlocfilehash: ed987409dc99ea9b1dade632a5fa5deeb322347a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890860"
---
# <a name="vector-class"></a>vector-Klasse

Die C++ Vektor Klasse der Standard Bibliothek ist eine Klassen Vorlage für Sequenz Container. Ein Vektor speichert Elemente eines bestimmten Typs in einer linearen Anordnung und ermöglicht schnellen zufälligen Zugriff auf jedes Element. Ein Vektor ist der bevorzugte Container für eine Sequenz, wenn die Leistung mit Wahl freiem Zugriff eine Premium-Leistung ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>Parameter

*Typ*\
Der im Vektor zu speichernde Elementdatentyp.

*Zuordner\*
Der Typ, der das gespeicherte allocator-Objekt darstellt, das Details zum Belegen und Freigeben von Arbeitsspeicher für den Vektor kapselt. Dieses Argument ist optional, und der Standardwert ist `allocator<Type>`.

## <a name="remarks"></a>Bemerkungen

Vektoren ermöglichen konstante Zeiteinfügungen und -löschungen am Ende der Sequenz. Für das Einfügen oder Löschen von Elementen in der Mitte eines Vektors ist lineare Zeit erforderlich. Der [Deque-Klassen](../standard-library/deque-class.md) Container ist bei Einfügungen und Löschungen am Anfang und Ende einer Sequenz schneller. Der [List-Klassen](../standard-library/list-class.md) Container ist bei Einfügungen und Löschungen an einer beliebigen Position innerhalb einer Sequenz schneller.

Eine Speicherneubelegung für einen Vektor findet statt, wenn eine Memberfunktion die Sequenz, die in dem vector-Objekt enthalten ist, über dessen aktuelle Speicherkapazität hinaus vergrößern muss. Andere Einfügungen und Löschungen können verschiedene Speicheradressen innerhalb der Sequenz ändern. In allen diesen Fällen werden Iteratoren oder Verweise auf geänderte Teile der Sequenz ungültig. Wenn keine Neuzuordnung stattfindet, bleiben nur Iteratoren und Verweise vor dem Einfüge-/Löschpunkt gültig.

Der [Vektor\<bool-> Klasse](../standard-library/vector-bool-class.md) ist eine vollständige Spezialisierung des Klassen Vorlagen Vektors für Elemente vom Typ `bool`. Sie verfügt über eine Zuweisung für den zugrunde liegenden Typ, der von der Spezialisierung verwendet wird.

Der [Vektor\<bool > Reference-Klasse](../standard-library/vector-bool-class.md#reference_class) ist eine geschachtelte Klasse, deren Objekte Verweise auf Elemente (einzelne Bits) in einem Vektor\<booleschen > Objekt bereitstellen können.

## <a name="members"></a>Members

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[vector](#vector)|Erstellt einen Vektor einer bestimmten Größe bzw. mit Elementen eines bestimmten Werts oder mit einem bestimmten `allocator`-Element oder als vollständige bzw. teilweise Kopie eines anderen Vektors.|

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[allocator_type](#allocator_type)|Ein Typ, der die `allocator`-Klasse für das Vektorobjekt darstellt.|
|[const_iterator](#const_iterator)|Ein Typ, der einen Iterator mit wahlfreiem Zugriff bereitstellt, mit dem ein **const**-Element in einem Vektor gelesen werden kann.|
|[const_pointer](#const_pointer)|Ein Typ, der einen Zeiger auf ein **const**-Element in einem Vektor bereitstellt.|
|[const_reference](#const_reference)|Ein Typ, der einen Verweis auf ein in einem Vektor gespeichertes **Konstanten** Element bereitstellt. Sie wird zum Lesen und Ausführen von **Konstanten** Vorgängen verwendet.|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen Iterator mit direktem Zugriff bereitstellt, mit dem jedes **const**-Element im Vektor gelesen werden kann.|
|[difference_type](#difference_type)|Ein Typ, der die Differenz zwischen den Adressen von zwei Elementen in einem Vektor bereitstellt.|
|[iterator](#iterator)|Ein Typ, der einen Iterator mit wahlfreiem Zugriff bereitstellt, mit dem jedes Element in einem Vektor gelesen oder geändert werden kann.|
|[pointer](#pointer)|Ein Typ, der einen Zeiger auf ein Element in einem Vektor bereitstellt.|
|[Referenz](#reference)|Ein Typ, der einen Verweis auf ein in einem Vektor gespeichertes Element bereitstellt.|
|[reverse_iterator](#reverse_iterator)|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem jedes Element in einem umgekehrten Vektor gelesen oder geändert werden kann.|
|[size_type](#size_type)|Ein Typ, der die Anzahl von Elementen in einem Vektor zählt.|
|[value_type](#value_type)|Ein Typ, der den in einem Vektor gespeicherten Datentyp darstellt.|

### <a name="functions"></a>Functions

|||
|-|-|
|[assign](#assign)|Löscht einen Vektor und kopiert die angegebenen Elemente in den leeren Vektor.|
|[at](#at)|Gibt einen Verweis auf das Element an einer angegebenen Position in dem Vektor zurück.|
|[Rückseite](#back)|Gibt einen Verweis auf das letzte Element des Vektors zurück.|
|[begin](#begin)|Gibt einen Iterator mit wahlfreiem Zugriff für das erste Element im Vektor zurück.|
|[Kapazität](#capacity)|Gibt die Anzahl von Elementen zurück, die der Vektor enthalten kann, ohne zusätzlichen Speicher zuzuweisen.|
|[cbegin](#cbegin)|Gibt einen const-Iterator mit wahlfreiem Zugriff für das erste Element im Vektor zurück.|
|[cend](#cend)|Gibt einen für wahlfreien Zugriff eingerichteten konstanten Iterator zurück, der unmittelbar hinter das Ende des Vektors zeigt.|
|[crbegin](#crbegin)|Gibt einen const-Iterator zum ersten Element in einem umgekehrten Vektor zurück.|
|[crend](#crend)|Gibt einen const-Iterator zum Ende eines umgekehrten Vektors zurück.|
|[Löschen](#clear)|Löscht die Elemente des Vektors.|
|[data](#data)|Gibt einen Zeiger auf das erste Element im Vektor zurück.|
|[emplace](#emplace)|Fügt ein direkt konstruiertes Element an einer angegebenen Position in den Vektor ein.|
|[emplace_back](#emplace_back)|Fügt ein direkt konstruiertes Element am Ende des Vektors ein.|
|[empty](#empty)|Testet, ob der Vektorcontainer leer ist.|
|[end](#end)|Gibt einen Iterator mit wahlfreiem Zugriff zurück, der auf das Ende des Vektors zeigt.|
|[erase](#erase)|Entfernt ein Element oder eine Reihe von Elementen aus angegebenen Positionen in einem Vektor.|
|[Vorderseite](#front)|Gibt einen Verweis auf das erste Element in einem Vektor zurück.|
|[get_allocator](#get_allocator)|Gibt ein Objekt an die `allocator`-Klasse zurück, das von einem Vektor verwendet wird.|
|[insert](#insert)|Fügt ein Element oder eine Reihe von Elementen an einer angegebenen Position in den Vektor ein.|
|[max_size](#max_size)|Gibt die Maximallänge des Vektors zurück.|
|[pop_back](#pop_back)|Löscht das Element am Ende des Vektors.|
|[push_back](#push_back)|Fügt ein Element am Ende des Vektors hinzu.|
|[rbegin](#rbegin)|Gibt einen Iterator an das erste Element in einem umgekeherten Vektor zurück.|
|[rend](#rend)|Gibt einen Iterator zum Ende eines umgekehrten Vektors zurück.|
|[reserve](#reserve)|Reserviert eine Mindestspeicherlänge für ein Vektorobjekt.|
|[resize](#resize)|Gibt eine neue Größe für einen Vektor an.|
|[shrink_to_fit](#shrink_to_fit)|Verwirft Überkapazität.|
|[size](#size)|Gibt die Anzahl von Elementen in dem Vektor zurück.|
|[swap](#swap)|Tauscht die Elemente zweier Vektoren aus.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[operator[]](#op_at)|Gibt einen Verweis auf das Vektorelement an einer angegebenen Position zurück.|
|[operator=](#op_eq)|Ersetzt die Elemente des Vektors durch eine Kopie eines anderen Vektors.|

## <a name="allocator_type"></a>allocator_type

Ein Typ, der die Zuweisungsklasse für das Vektorobjekt darstellt.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Bemerkungen

`allocator_type` ist ein Synonym für den Vorlagenparameter `Allocator`.

### <a name="example"></a>Beispiel

In dem Beispiel für [get_allocator](#get_allocator) finden Sie ein Beispiel, das `allocator_type` verwendet.

## <a name="assign"></a>einräumen

Löscht einen Vektor und kopiert die angegebenen Elemente in den leeren Vektor.

```cpp
void assign(size_type count, const Type& value);
void assign(initializer_list<Type> init_list);

template <class InputIterator>
void assign(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>Parameter

*erste*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*Letzter*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*Anzahl*\
Die Anzahl von Kopien eines Elements, das in den Vektor eingefügt wird.

*value*\
Der Wert des Elements, das in den Vektor eingefügt wird.

*init_list*\
Das initializer_list-Element, in den die zu kopierenden Elemente eingefügt werden.

### <a name="remarks"></a>Bemerkungen

Zuerst löscht `assign` alle vorhandenen Elemente in einem Vektor. `assign` fügt dann entweder einen angegebenen Bereich von Elementen aus dem ursprünglichen Vektor in einen Vektor ein oder fügt Kopien eines neuen angegebenen Wert Elements in einen Vektor ein.

### <a name="example"></a>Beispiel

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}
```

## <a name="at"></a>an

Gibt einen Verweis auf das Element an einer angegebenen Position in dem Vektor zurück.

```cpp
reference at(size_type position);

const_reference at(size_type position) const;
```

### <a name="parameters"></a>Parameter

*Positions*\
Dier Feldindex oder Positionsnummer des Elements, das auf den Vektor verweisen soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Element, das im Argument indiziert ist. Wenn die *Position* größer als die Größe des Vektors ist, löst `at` eine Ausnahme aus.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `at` einem `const_reference`zugewiesen wird, kann das Vektor Objekt nicht geändert werden. Wenn `at` dem Rückgabewert von `reference` zugewiesen wird, kann das Vektorobjekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>Zurück

Gibt einen Verweis auf das letzte Element des Vektors zurück.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Rückgabewert

Das letzte Element des Vektors. Wenn der Vektor leer ist, ist der Rückgabewert nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `back` einem `const_reference`zugewiesen wird, kann das Vektor Objekt nicht geändert werden. Wenn `back` dem Rückgabewert von `reference` zugewiesen wird, kann das Vektorobjekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element in einem leeren Vektor ein Laufzeitfehler auf. Weitere Informationen finden Sie unter über [prüfte Iteratoren](../standard-library/checked-iterators.md).

### <a name="example"></a>Beispiel

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a>beginnen

Gibt einen Iterator mit wahlfreiem Zugriff für das erste Element im Vektor zurück.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator mit direktem Zugriff, der das erste Element im `vector` adressiert oder auf die Position zeigt, der auf einen leeren `vector` folgt. Vergleichen Sie immer den mit [Vector:: End](#end) zurückgegebenen Wert, um sicherzustellen, dass er gültig ist.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `begin` einem [Vector:: const_iterator](#const_iterator)zugewiesen wird, kann das `vector` Objekt nicht geändert werden. Wenn dem Rückgabewert `begin` einem [vector::iterator](#iterator) zugewiesen wird, kann das `vector`-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
    *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a>persönlich

Gibt die Anzahl von Elementen zurück, die der Vektor enthalten kann, ohne zusätzlichen Speicher zuzuweisen.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Speicherlänge, die für den Vektor zugewiesen wurde.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion [resize](#resize) arbeitet effizienter, wenn ausreichend Arbeitsspeicher dafür zugeordnet wird. Verwenden Sie die Memberfunktion [reserve](#reserve), um die Größe des zugewiesenen Arbeitsspeichers anzugeben.

### <a name="example"></a>Beispiel

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a>cbegin

Gibt einen **Konstanten** Iterator zurück, der das erste Element im Bereich adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **konstanter** Random-Access-Iterator, der auf das erste Element des Bereichs zeigt oder die Position direkt hinter dem Ende eines leeren Bereichs (für einen leeren Bereich, `cbegin() == cend()`).

### <a name="remarks"></a>Bemerkungen

Mit dem Rückgabewert `cbegin`können die Elemente im Bereich nicht geändert werden.

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

Ein **konstanter** Random-Access-Iterator, der direkt hinter das Ende des Bereichs zeigt.

### <a name="remarks"></a>Bemerkungen

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines Bereichs übergeben hat.

Sie können diese Memberfunktion anstelle der `end()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [automatischen](../cpp/auto-cpp.md) Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollten `Container` ein änderbarer (nicht **konstanter) Container**sein, der `end()` und `cend()`unterstützt.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden. Verwenden Sie Sie nur für Vergleiche.

## <a name="clear"></a>Klartext

Löscht die Elemente des Vektors.

```cpp
void clear();
```

### <a name="example"></a>Beispiel

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a>const_iterator

Ein Typ, der einen Iterator mit wahlfreiem Zugriff bereitstellt, mit dem ein **const**-Element in einem Vektor gelesen werden kann.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein Typ `const_iterator` kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

In dem Beispiel für [back](#back) finden Sie ein Beispiel, in dem `const_iterator` verwendet wird.

## <a name="const_pointer"></a>const_pointer

Ein Typ, der einen Zeiger auf ein **const**-Element in einem Vektor bereitstellt.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein Typ `const_pointer` kann nicht zum Ändern des Werts eines Elements verwendet werden.

Ein [Iterator](#iterator) wird häufiger für den Zugriff auf ein Vektorelement verwendet.

## <a name="const_reference"></a>const_reference

Ein Typ, der einen Verweis auf ein in einem Vektor gespeichertes **Konstanten** Element bereitstellt. Sie wird zum Lesen und Ausführen von **Konstanten** Vorgängen verwendet.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Bemerkungen

Ein Typ `const_reference` kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Ein Typ, der einen Iterator mit direktem Zugriff bereitstellt, mit dem jedes **const**-Element im Vektor gelesen werden kann.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein Typ `const_reverse_iterator` kann den Wert eines Elements nicht ändern und wird verwendet, um den Vektor in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Im Beispiel für [rbegin](#rbegin) wird verdeutlicht, wie ein Iterator deklariert und verwendet wird.

## <a name="crbegin"></a>crbegin

Gibt einen const-Iterator zum ersten Element in einem umgekehrten Vektor zurück.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter const-Iterator mit direktem Zugriff, mit dem das erste Element in einem umgekehrten [vector](../standard-library/vector-class.md) adressiert wird (bzw. mit dem das ehemals letzte Element in der nicht umgekehrten `vector` adressiert wird).

### <a name="remarks"></a>Bemerkungen

Mit dem Rückgabewert `crbegin`kann das `vector` Objekt nicht geändert werden.

### <a name="example"></a>Beispiel

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a>crend

Gibt einen const-Iterator zurück, mit dem die Position adressiert wird, die dem letzten Element eines umgekehrten Vektors folgt.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein const_reverse-Iterator mit direktem Zugriff, mit dem die Position adressiert wird, die dem letzten Element in einem umgekehrten [vector](../standard-library/vector-class.md) folgt (der Speicherort, der dem ersten Element im nicht umgekehrten `vector` vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einem umgekehrten `vector` auf die gleiche Weise verwendet, wie [vector::cend](#cend) bei einem `vector` verwendet wird.

Mit dem Rückgabewert `crend` (entsprechend dekrementiert) kann das `vector` Objekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob das Ende der `vector` von einem umgekehrten Iterator erreicht wurde.

Der von `crend` zurückgegebene Wert darf nicht dereferenziert werden. Verwenden Sie Sie nur für Vergleiche.

### <a name="example"></a>Beispiel

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

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

## <a name="data"></a>Vorrats

Gibt einen Zeiger auf das erste Element im Vektor zurück.

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Element im [vector](../standard-library/vector-class.md) oder auf die Position, die auf einen leeren `vector` folgt.

### <a name="example"></a>Beispiel

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1_ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_ptr = c1.data();
    *c1_ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1_ptr++)
    {
        cout << " " << *c1_ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a>difference_type

Ein Typ, der den Unterschied zwischen zwei Iteratoren, die auf Elemente innerhalb desselben Vektors verweisen, bereitstellt.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

Ein `difference_type` kann auch als die Anzahl von Elementen zwischen zwei Zeigern beschrieben werden, da ein Zeiger auf ein Element die entsprechende Adresse enthält.

Ein [Iterator](#iterator) wird häufiger für den Zugriff auf ein Vektorelement verwendet.

### <a name="example"></a>Beispiel

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

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

## <a name="emplace"></a>emplace

Fügt ein direkt konstruiertes Element an einer angegebenen Position in den Vektor ein.

```cpp
template <class... Types>
iterator emplace(
    const_iterator position,
    Types&&... args);
```

### <a name="parameters"></a>Parameter

*Positions*\
Die Position im [vector](../standard-library/vector-class.md), an der das erste Element eingefügt wird.

*args*\
Konstruktorargumente Die Funktion leitet auf Grundlage der bereitgestellten Argumente die erforderliche die Konstruktorüberladung ab.

### <a name="return-value"></a>Rückgabewert

Die Funktion gibt einen Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element in den `vector` eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Jeder Einfügevorgang kann kostspielig sein. eine Erörterung der `vector` Leistung finden Sie unter [Vector-Klasse](../standard-library/vector-class.md) .

### <a name="example"></a>Beispiel

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

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

## <a name="emplace_back"></a>emplace_back

Fügt ein direkt konstruiertes Element am Ende des Vektors ein.

```cpp
template <class... Types>
void emplace_back(Types&&... args);
```

### <a name="parameters"></a>Parameter

*args*\
Konstruktorargumente Die Funktion leitet auf Grundlage der bereitgestellten Argumente die erforderliche die Konstruktorüberladung ab.

### <a name="example"></a>Beispiel

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}
```

## <a name="empty"></a>leer

Testet, ob der Vektor leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**true** , wenn der Vektor leer ist. **false** , wenn der Vektor nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a>Schließlich

Gibt den "past-the-end"-Iterator zurück.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Rückgabewert

Der "past-the-end"-Iterator für den Vektor. Wenn der Vektor leer ist, `vector::end() == vector::begin()`.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `end` einer Variablen vom Typ "`const_iterator`" zugewiesen wird, kann das Vektor Objekt nicht geändert werden. Wenn der Rückgabewert von `end` einer Variablen vom Typ `iterator`zugewiesen wird, kann das Vektor Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a>Löschen

Entfernt ein Element oder eine Reihe von Elementen aus angegebenen Positionen in einem Vektor.

```cpp
iterator erase(
    const_iterator position);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parameter

*Positions*\
Die Position des von dem Vektor zu entfernenden Elements.

*erste*\
Die Position des ersten Elements, das von dem Vektor entfernt werden soll.

*Letzter*\
Die Position direkt hinter dem letzten von dem Vektor entfernten Element.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste über die entfernten Elemente hinaus verbliebene Element festlegt, oder ein Zeiger, der das Ende des Vektors darstellt, wenn kein solches Element vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a>Beifahrer

Gibt einen Verweis auf das erste Element in einem Vektor zurück.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das erste Element im Vektorobjekt. Wenn der Vektor leer ist, ist die Rückgabe nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `front` einem `const_reference`zugewiesen wird, kann das Vektor Objekt nicht geändert werden. Wenn der Rückgabewert von `front` einem **reference** zugewiesen wird, kann das Vektorobjekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element in einem leeren Vektor ein Laufzeitfehler auf. Weitere Informationen finden Sie unter über [prüfte Iteratoren](../standard-library/checked-iterators.md).

### <a name="example"></a>Beispiel

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a>get_allocator

Gibt eine Kopie des Zuweisungsobjekts zurück, das zum Erstellen eines Vektors verwendet wird.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Die von dem Vektor verwendete Zuweisung.

### <a name="remarks"></a>Bemerkungen

Zuweisungen für die Vektorklasse geben an, wie die Klasse einen Speicher verwaltet. Für die meisten Programmieranforderungen genügen die standardmäßigen Zuweisungen mit Containerklassen der C++-Standardbibliothek. Das Schreiben und verwenden ihrer eigenen zuordnerklasse ist C++ eine erweiterte Funktion.

### <a name="example"></a>Beispiel

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a>setze

Fügt ein Element, mehrere Elemente oder einen Bereich von Elementen an einer angegebenen Position in den Vektor ein.

```cpp
iterator insert(
    const_iterator position,
    const Type& value);

iterator insert(
    const_iterator position,
    Type&& value);

void insert(
    const_iterator position,
    size_type count,
    const Type& value);

template <class InputIterator>
void insert(
    const_iterator position,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>Parameter

*Positions*\
Die Position in dem Vektor, an der das erste Element eingefügt wird.

*value*\
Der Wert des Elements, das in den Vektor eingefügt wird.

*Anzahl*\
Die Anzahl von Elementen, die in den Vektor eingefügt werden.

*erste*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*Letzter*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

### <a name="return-value"></a>Rückgabewert

Die ersten zwei `insert`-Funktionen geben einen Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element in den Vektor eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Als Vorbedingung dürfen *First* und *Last* keine Iteratoren in den Vektor sein, oder das Verhalten ist nicht definiert. Jeder Einfügevorgang kann kostspielig sein. eine Erörterung der `vector` Leistung finden Sie unter [Vector-Klasse](../standard-library/vector-class.md) .

### <a name="example"></a>Beispiel

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   const auto v2 = v1;
   v1.insert( v1.begin( )+1, v2.begin( )+2, v2.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
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
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a>Iterator

Ein Typ, der einen Iterator mit wahlfreiem Zugriff bereitstellt, mit dem jedes Element in einem Vektor gelesen oder geändert werden kann.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein **Iterator**-Typ kann zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [begin](#begin).

## <a name="max_size"></a>max_size

Gibt die Maximallänge des Vektors zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die mögliche Maximallänge des Vektors.

### <a name="example"></a>Beispiel

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="op_at"></a>[]-Operator

Gibt einen Verweis auf das Vektorelement an einer angegebenen Position zurück.

```cpp
reference operator[](size_type position);

const_reference operator[](size_type position) const;
```

### <a name="parameters"></a>Parameter

*Positions*\
Die Position des angegebenen Vektorelements.

### <a name="return-value"></a>Rückgabewert

Wenn die angegebene Position größer oder gleich der Größe des Containers ist, ist das Ergebnis nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `operator[]` einem `const_reference`zugewiesen wird, kann das Vektor Objekt nicht geändert werden. Wenn der Rückgabewert von `operator[]` einem Verweis zugewiesen wird, kann das Vektorobjekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element außerhalb des Vektorobjekts ein Laufzeitfehler auf. Weitere Informationen finden Sie unter über [prüfte Iteratoren](../standard-library/checked-iterators.md).

### <a name="example"></a>Beispiel

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="op_eq"></a>Operator =

Ersetzt die Elemente des Vektors durch eine Kopie eines anderen Vektors.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Der [vector](../standard-library/vector-class.md), der in den `vector` kopiert wird.

### <a name="remarks"></a>Bemerkungen

Nachdem alle vorhandenen Elemente in einem `vector`gelöscht wurden, `operator=` entweder kopiert oder verschiebt den Inhalt von *right* in den `vector`.

### <a name="example"></a>Beispiel

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

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
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>Zeichner

Ein Typ, der einen Zeiger auf ein Element in einem Vektor bereitstellt.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein Typ **pointer** kann zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
    using namespace std;
    vector<int> v;
    v.push_back( 11 );
    v.push_back( 22 );

    vector<int>::pointer ptr = &v[0];
    cout << *ptr << endl;
    ptr++;
    cout << *ptr << endl;
    *ptr = 44;
    cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a>pop_back

Löscht das Element am Ende des Vektors.

```cpp
void pop_back();
```

### <a name="remarks"></a>Bemerkungen

Ein Codebeispiel finden Sie unter [vector::push_back()](#push_back).

## <a name="push_back"></a>push_back

Fügt ein Element am Ende des Vektors hinzu.

```cpp
void push_back(const T& value);

void push_back(T&& value);
```

### <a name="parameters"></a>Parameter

*value*\
Der Wert, der dem am Ende des Vektors hinzugefügten Element zugewiesen werden soll.

### <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a>rbegin

Gibt einen Iterator an das erste Element in einem umgekeherten Vektor zurück.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter Iterator mit direktem Zugriff, mit dem das erste Element in einem umgekehrten Vektor adressiert wird (bzw. mit dem das ehemals letzte Element in der nicht umgekehrten Vektor adressiert wird).

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `rbegin` einem `const_reverse_iterator`zugewiesen wird, kann das Vektor Objekt nicht geändert werden. Wenn `rbegin` dem Rückgabewert von `reverse_iterator` zugewiesen wird, kann das Vektorobjekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a>Angabe

Ein Typ, der einen Verweis auf ein in einem Vektor gespeichertes Element bereitstellt.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Beispiel

Unter [at](#at) finden Sie ein Beispiel zur Verwendung von **reference** in der Vektorklasse.

## <a name="rend"></a>rend

Gibt einen Iterator zurück, mit dem die Position adressiert wird, die dem letzten Element eines umgekehrten Vektors folgt.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter Iterator mit direktem Zugriff, mit dem die Position adressiert wird, die dem letzten Element in einem umgekehrten Vektor folgt (die Position, die dem ersten Element im nicht umgekehrten Vektor vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einem umgekehrten Vektor auf die gleiche Weise verwendet, wie [end](#end) bei einem Vektor verwendet wird.

Wenn der Rückgabewert von `rend` einem `const_reverse_iterator`zugewiesen wird, kann das Vektor Objekt nicht geändert werden. Wenn `rend` dem Rückgabewert von `reverse_iterator` zugewiesen wird, kann das Vektorobjekt geändert werden.

`rend` kann verwendet werden, um zu testen, ob das Ende des Vektors von einem umgekehrten Iterator erreicht wurde.

Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden. Verwenden Sie Sie nur für Vergleiche.

### <a name="example"></a>Beispiel

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

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

## <a name="reserve"></a>Schutz

Reserviert eine Mindestlänge von Speicher für ein Vektorobjekt und weist Speicherplatz zu, falls erforderlich.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>Parameter

*Anzahl*\
Die minimale Speicherlänge, die für für den Vektor zugeordnet werden soll.

### <a name="example"></a>Beispiel

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a>Größe

Gibt eine neue Größe für einen Vektor an.

```cpp
void resize(size_type new_size);
void resize(size_type new_size, Type value);
```

### <a name="parameters"></a>Parameter

*new_size*\
Die neue Größe des Vektors.

*value*\
Der Initialisierungswert für neue Elemente, der zum Vektor hinzugefügt wird, wenn die neue Größe die Originalgröße übersteigt. Wenn der Wert ausgelassen wird, verwenden die neuen Objekte ihren Standardkonstruktor.

### <a name="remarks"></a>Bemerkungen

Wenn die Größe des Containers kleiner als die angeforderte Größe ist, *new_size*`resize` dem Vektor Elemente hinzu, bis die angeforderte Größe erreicht ist. Wenn die Größe des Containers die angeforderte Größe überschreitet, löscht `resize` die Elemente, die dem Ende des Containers am nächsten sind, bis er die Größe *new_size*erreicht. Wenn die aktuelle Größe des Containers der angeforderten Größe entspricht, wird keine Aktion ausgeführt.

[size](#size) gibt die aktuelle Größe des Vektors an.

### <a name="example"></a>Beispiel

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }
    cout << endl;
}

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a>reverse_iterator

Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem jedes Element in einem umgekehrten Vektor gelesen oder geändert werden kann.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `reverse_iterator`-Typ wird verwendet, um den Vektor in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [rbegin](#rbegin).

## <a name="shrink_to_fit"></a>shrink_to_fit

Verwirft Überkapazität.

```cpp
void shrink_to_fit();
```

### <a name="example"></a>Beispiel

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a>Größe

Gibt die Anzahl von Elementen in dem Vektor zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge des Vektors.

### <a name="example"></a>Beispiel

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a>size_type

Ein Typ, der die Anzahl von Elementen in einem Vektor zählt.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [capacity](#capacity).

## <a name="swap"></a>Wechsel

Tauscht die Elemente zweier Vektoren aus.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Ein Vektor, der die auszutauschenden Elemente bereitstellt. Oder ein Vektor, dessen Elemente mit den Elementen im Vektor nach *Links*ausgetauscht werden sollen.

*Linker*\
Ein Vektor, dessen Elemente mit den Elementen im Vektor *Rechts*ausgetauscht werden sollen.

### <a name="example"></a>Beispiel

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a>value_type

Ein Typ, der den in einem Vektor gespeicherten Datentyp darstellt.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Bemerkungen

`value_type` ist ein Synonym für den Vorlagenparameter `Type`.

### <a name="example"></a>Beispiel

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a>ve

Erstellt einen Vektor. Über Ladungen erstellen einen Vektor einer bestimmten Größe oder mit Elementen eines bestimmten Werts. Oder als Kopie eines ganz oder teilweise eines anderen Vektors. Bei einigen über Ladungen können Sie auch die zu verwendende Zuweisung angeben.

```cpp
vector();
explicit vector(const Allocator& allocator);
explicit vector(size_type count);
vector(size_type count, const Type& value);
vector(size_type count, const Type& value, const Allocator& allocator);

vector(const vector& source);
vector(vector&& source);
vector(initializer_list<Type> init_list, const Allocator& allocator);

template <class InputIterator>
vector(InputIterator first, InputIterator last);
template <class InputIterator>
vector(InputIterator first, InputIterator last, const Allocator& allocator);
```

### <a name="parameters"></a>Parameter

*Zuordner\*
Die mit diesem Objekt zu verwendende Zuweisungsklasse. [get_allocator](#get_allocator) gibt die Zuweisungsklasse für das Objekt zurück.

*Anzahl*\
Die Anzahl der Elemente im erstellten Vektor.

*value*\
Der Wert der Elemente im erstellten Vektor.

*Quell*\
Der Vektor, dessen Kopie der erstellte Vektor ist.

*erste*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*Letzter*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*init_list*\
Die `initializer_list`, die die zu Kopier-Elemente enthält.

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren speichern ein zuordnerobjekt (*Zuweisung*) und initialisieren den Vektor.

Die ersten beiden Konstruktoren geben einen leeren ursprünglichen Vektor an. Der zweite Konstruktor gibt explizit den zu verwendenden zuordnertyp (*zuordnertyp*) an.

Der dritte Konstruktor gibt eine Wiederholung einer angegebenen*Anzahl (Anzahl*) von Elementen des Standardwerts für die Klasse `Type`an.

Der vierte und fünfte Konstruktoren geben eine Wiederholung der (*count*) Elemente des Wert *Werts an.*

Der sechste Konstruktor gibt eine Kopie der Vektor *Quelle*an.

Der siebte Konstruktor verschiebt die Vektor *Quelle*.

Beim achten Konstruktor wird zum Angeben des Elements ein initializer_list-Element verwendet.

Mit den neunten und zehnten Konstruktoren wird der Bereich [`first`, `last`) eines Vektors kopiert.

### <a name="example"></a>Beispiel

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}
```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>Weitere Informationen

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
