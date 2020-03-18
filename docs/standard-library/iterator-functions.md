---
title: '&lt;iterator&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- xutility/std::advance
- xutility/std::back_inserter
- xutility/std::begin
- xutility/std::cbegin
- xutility/std::cend
- xutility/std::distance
- xutility/std::end
- xutility/std::front_inserter
- xutility/std::inserter
- xutility/std::make_checked_array_iterator
- xutility/std::make_move_iterator
- xutility/std::make_unchecked_array_iterator
- xutility/std::next
- xutility/std::prev
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
helpviewer_keywords:
- std::advance [C++]
- std::back_inserter [C++]
- std::begin [C++]
- std::cbegin [C++]
- std::cend [C++]
- std::distance [C++]
- std::end [C++]
- std::front_inserter [C++]
- std::inserter [C++]
- std::make_checked_array_iterator [C++]
- std::make_move_iterator [C++]
- std::make_unchecked_array_iterator [C++]
- std::next [C++]
- std::prev [C++]
ms.openlocfilehash: 69f1007f0c7f587e81313f5de97947410bf243df
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425646"
---
# <a name="ltiteratorgt-functions"></a>&lt;iterator&gt;-Funktionen

## <a name="advance"></a>Vorwarnung

Damit kann ein Iterator um eine bestimmte Anzahl von Positionen vorwärts verschoben werden.

```cpp
template <class InputIterator, class Distance>
    void advance(InputIterator& InIt, Distance Off);
```

### <a name="parameters"></a>Parameter

*Init* -\
Der Iterator, der vorwärts verschoben werden soll und die Anforderungen für einen Eingabeiterator erfüllen muss.

*Aus*\
Ein Ganzzahltyp, der in den Differenztyp des Iterators konvertierbar ist und die Anzahl von Schritten angibt, um die die Position des Iterators vorwärts verschoben werden soll.

### <a name="remarks"></a>Hinweise

Der dabei durchlaufene Bereich darf nicht singulär sein, wobei die Iteratoren dereferenzierbar sein oder hinter dem Ende liegen müssen.

Wenn das `InputIterator` die Anforderungen für einen bidirektionalen iteratortyp erfüllt, kann *Off* negativ sein. Wenn `InputIterator` ein Eingabe-oder Forward-iteratortyp ist, darf *Off* nicht negativ sein.

Die Funktion "Advance" hat eine Konstante Komplexität, wenn `InputIterator` die Anforderungen für einen Random-Access-Iterator erfüllt. Andernfalls weist Sie lineare Komplexität auf und ist daher möglicherweise aufwendig.

### <a name="example"></a>Beispiel

```cpp
// iterator_advance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = 1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 4 );
   cout << "LPOS is advanced 4 steps forward to point"
        << " to the fifth element: "
        << *LPOS << "." << endl;

   advance ( LPOS , -3 );
   cout << "LPOS is moved 3 steps back to point to the "
        << "2nd element: " << *LPOS << "." << endl;
}
```

```Output
The list L is: ( 1 2 3 4 5 6 7 8 ).
The iterator LPOS initially points to the first element: 1.
LPOS is advanced 4 steps forward to point to the fifth element: 5.
LPOS is moved 3 steps back to point to the 2nd element: 2.
```

## <a name="back_inserter"></a>back_inserter

Damit wird ein Iterator erstellt, mit dem Elemente an das Ende eines bestimmten Containers eingefügt werden können.

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>Parameter

*_Cont*\
Der Container, in dem die Einfügung am Ende ausgeführt werden sollte.

### <a name="return-value"></a>Rückgabewert

Eine `back_insert_iterator`, die dem Container Objekt *_Cont*zugeordnet ist.

### <a name="remarks"></a>Hinweise

In der C++-Standardbibliothek muss das Argument auf einen der drei Sequenzcontainer verweisen, die die Memberfunktion `push_back`: [deque-Klasse](../standard-library/deque-class.md), [list-Klasse](../standard-library/list-class.md) oder [vector-Klasse](../standard-library/vector-class.md) haben.

### <a name="example"></a>Beispiel

```cpp
// iterator_back_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 3 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;
*backiter = 40;

   // Alternatively, insertions can be done with the
   // back_insert_iterator member function
   back_inserter ( vec ) = 500;
   back_inserter ( vec ) = 600;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 0 1 2 ).
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).
```

## <a name="begin"></a>beginnen

Ruft einen Iterator für das erste Element in einem angegebenen Container ab.

```cpp
template <class Container>
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>
Ty *begin(Ty (& array)[Size]);
```

### <a name="parameters"></a>Parameter

*\*
Ein Container.

*Array*\
Ein Array von Objekten des Typs `Ty`.

### <a name="return-value"></a>Rückgabewert

Die ersten beiden Vorlagenfunktionen geben `cont.begin()` zurück. Die erste Funktion ist nicht konstant; die zweite ist konstant.

Die dritte Vorlagen Funktion gibt das *Array*zurück.

### <a name="example"></a>Beispiel

Es empfiehlt sich, diese Vorlagenfunktion anstelle des Containermembers `begin()` zu verwenden, wenn ein eher generisches Verhalten erforderlich ist.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <vector>

template <typename C> void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(begin(c), end(c), std::greater<>());
}

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        std::cout << e << " ";
    }

    std::cout << "\n";
}

int main() {
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(v);
    reverse_sort(v);
    print(v);

    std::cout << "--\n";

    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(arr);
    reverse_sort(arr);
    print(arr);
}
```

```Output
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1
--
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1
```

Die Funktion `reverse_sort` unterstützt Container jeder Art, neben den normalen Arrays, da sie die Nichtmemberversion von `begin()` aufruft. Wenn `reverse_sort` zur Verwendung des Containermembers `begin()` codiert wurde:

```cpp
template <typename C>
void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(c.begin(), c.end(), std::greater<>());

}
```

Das Senden eines Arrays würde in diesem Fall folgenden Compilerfehler verursachen:

```Output
error C2228: left of '.begin' must have class/struct/union
```

## <a name="cbegin"></a>cbegin

Ruft einen const-Iterator für das erste Element in einem angegebenen Container ab.

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>Parameter

*\*
Ein Container oder ein initializer_list-Element.

### <a name="return-value"></a>Rückgabewert

Eine `cont.begin()`-Konstante.

### <a name="remarks"></a>Hinweise

Diese Funktion arbeitet mit allen C++-Standardbibliothekscontainern und mit [initializer_list](../standard-library/initializer-list-class.md).

Sie können diese Memberfunktion anstelle der `begin()`-Vorlagenfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [automatischen](../cpp/auto-cpp.md) Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollten Sie `Container` ein änderbarer (nicht **konstanter) Container**oder `initializer_list` einer beliebigen Art sein, der `begin()` und `cbegin()`unterstützt.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Ruft einen const-Iterator für das Element ab, das auf das letzte Element im angegebenen Container folgt.

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>Parameter

*\*
Ein Container oder ein initializer_list-Element.

### <a name="return-value"></a>Rückgabewert

Eine `cont.end()`-Konstante.

### <a name="remarks"></a>Hinweise

Diese Funktion arbeitet mit allen C++-Standardbibliothekscontainern und mit [initializer_list](../standard-library/initializer-list-class.md).

Sie können diese Memberfunktion anstelle der [end()](../standard-library/iterator-functions.md#end)-Vorlagenfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [automatischen](../cpp/auto-cpp.md) Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollten Sie `Container` ein änderbarer (nicht **konstanter) Container**oder `initializer_list` einer beliebigen Art sein, der `end()` und `cend()`unterstützt.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="crbegin"></a>crbegin

```cpp
template <class C> constexpr auto crbegin(const C& c) -> decltype(std::rbegin(c));
```

## <a name="crend"></a>crend

```cpp
template <class C> constexpr auto crend(const C& c) -> decltype(std::rend(c));
```

## <a name="data"></a>Vorrats

```cpp
template <class C> constexpr auto data(C& c) -> decltype(c.data());
template <class C> constexpr auto data(const C& c) -> decltype(c.data());
template <class T, size_t N> constexpr T* data(T (&array)[N]) noexcept;
template <class E> constexpr const E* data(initializer_list<E> il) noexcept;
```

## <a name="distance"></a>Flüge

Bestimmt die Anzahl von Inkrementen zwischen den durch zwei Iteratoren festgelegten Positionen.

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>Parameter

*erste*\
Der erste Iterator, dessen Abstand zum zweiten ermittelt werden soll.

*Letzter*\
Der zweite Iterator, dessen Abstand zum ersten ermittelt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt an, wie oft der *erste* Schritt erhöht werden muss, bis der *Letzte*Wert gleich ist.

### <a name="remarks"></a>Hinweise

Die Distance-Funktion hat Konstante Komplexität, wenn `InputIterator` die Anforderungen für einen Random-Access-Iterator erfüllt. Andernfalls weist Sie lineare Komplexität auf und ist daher möglicherweise aufwendig.

### <a name="example"></a>Beispiel

```cpp
// iterator_distance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 7 );
   cout << "LPOS is advanced 7 steps forward to point "
        << " to the eighth element: "
        << *LPOS << "." << endl;

   list<int>::difference_type Ldiff ;
   Ldiff = distance ( L.begin ( ) , LPOS );
   cout << "The distance from L.begin( ) to LPOS is: "
        << Ldiff << "." << endl;
}
```

```Output
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).
The iterator LPOS initially points to the first element: -2.
LPOS is advanced 7 steps forward to point  to the eighth element: 12.
The distance from L.begin( ) to LPOS is: 7.
```

## <a name="empty"></a>leer

```cpp
template <class C> constexpr auto empty(const C& c) -> decltype(c.empty());
template <class T, size_t N> constexpr bool empty(const T (&array)[N]) noexcept;
template <class E> constexpr bool empty(initializer_list<E> il) noexcept;
```

## <a name="end"></a>Schließlich

Ruft einen Iterator für das Element ab, das auf das letzte Element im angegebenen Container folgt.

```cpp
template <class Container>
auto end(Container& cont)
   -> decltype(cont.end());

template <class Container>
auto end(const Container& cont)
   -> decltype(cont.end());

template <class Ty, class Size>
Ty *end(Ty (& array)[Size]);
```

### <a name="parameters"></a>Parameter

*\*
Ein Container.

*Array*\
Ein Array von Objekten des Typs `Ty`.

### <a name="return-value"></a>Rückgabewert

Die ersten zwei Vorlagenfunktionen geben `cont.end()` zurück (die erste ist keine Konstante und die zweite ist eine Konstante.)

Die dritte Vorlagenfunktion gibt `array + Size` zurück.

### <a name="remarks"></a>Hinweise

Ein Codebeispiel finden Sie unter [begin](../standard-library/iterator-functions.md#begin).

## <a name="front_inserter"></a>front_inserter

Damit wird ein Iterator erstellt, mit dem Elemente an den Anfang eines bestimmten Containers eingefügt werden können.

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>Parameter

*_Cont*\
Das Containerobjekt, dessen Front ein eingefügtes Element hat.

### <a name="return-value"></a>Rückgabewert

Eine `front_insert_iterator`, die dem Container Objekt *_Cont*zugeordnet ist.

### <a name="remarks"></a>Hinweise

Die Memberfunktion [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator) von der front_insert_iterator-Klasse kann ebenfalls verwendet werden.

In der C++-Standardbibliothek muss das Argument auf einen der drei Sequenzcontainer verweisen, die die Memberfunktion `push_back`: [deque-Klasse](../standard-library/deque-class.md) oder „list-Klasse“ haben.

### <a name="example"></a>Beispiel

```cpp
// iterator_front_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template function to insert an element
   front_insert_iterator< list < int> > Iter(L);
*Iter = 100;

   // Alternatively, you may use the front_insert member function
   front_inserter ( L ) = 200;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( -1 0 1 2 3 4 5 6 7 8 ).
After the front insertions, the list L is:
( 200 100 -1 0 1 2 3 4 5 6 7 8 ).
```

## <a name="inserter"></a>Codeausschnitteinfüger

Eine hilfsvorlagen Funktion, mit der Sie `inserter(_Cont, _Where)` anstelle von `insert_iterator<Container>(_Cont, _Where)`verwenden können.

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>Parameter

*_Cont*\
Der Container, zu dem neue Elemente hinzugefügt werden sollen.

*_Where*\
Ein Iterator, der nach der Einfügemarke sucht.

### <a name="remarks"></a>Hinweise

Die Vorlagen Funktion gibt [Insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator)`<Container>(_Cont, _Where)`zurück.

### <a name="example"></a>Beispiel

```cpp
// iterator_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 2 ; i < 5 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template version to insert an element
   insert_iterator<list <int> > Iter( L, L.begin ( ) );
*Iter = 1;

   // Alternatively, using the member function to insert an element
   inserter ( L, L.end ( ) ) = 500;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( 20 30 40 ).
After the insertions, the list L is:
( 1 20 30 40 500 ).
```

## <a name="make_checked_array_iterator"></a>make_checked_array_iterator

Erstellt einen [checked_array_iterator](../standard-library/checked-array-iterator-class.md), der von anderen Algorithmen verwendet werden kann.

> [!NOTE]
> Bei dieser Funktion handelt es sich um eine Microsoft-Erweiterung der C++-Standardbibliothek. Der Code, der mit dieser Funktion implementiert wird, ist nicht auf C++-Standardbuildumgebungen übertragbar, die die Microsoft-Erweiterung nicht unterstützen.

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>Parameter

*Ptr* -\
Ein Zeiger auf das Zielarray.

*Größe*\
Die Größe des Zielarrays.

*Index*\
Optionaler Index im Array.

### <a name="return-value"></a>Rückgabewert

Eine Instanz von `checked_array_iterator`.

### <a name="remarks"></a>Hinweise

Die `make_checked_array_iterator`-Funktion wird im `stdext`-Namespace definiert.

Diese Funktion akzeptiert einen Rohzeiger – was normalerweise im Hinblick auf eine Überschreitung der Begrenzungen problematisch wäre –, und umschließt ihn in einer [checked_array_iterator](../standard-library/checked-array-iterator-class.md)-Klasse, die die Überprüfung ausführt. Da diese Klasse als überprüft markiert ist, gibt die C++-Standardbibliothek hierzu keine Warnung aus. Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein [Vektor](../standard-library/vector-class.md) erstellt und mit 10 Elementen gefüllt. Der Inhalt des Vektors wird mithilfe des Kopieralgorithmus in ein Array kopiert. Anschließend wird `make_checked_array_iterator` verwendet, um das Ziel anzugeben. Daraufhin erfolgt eine absichtliche Verletzung der Begrenzungen bei der Überprüfung, sodass eine Debugassertionsfehler ausgelöst wird.

```cpp
// make_checked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_checked_array_iterator
#include <memory> // std::make_unique
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

int main()
{
    const size_t dest_size = 10;
    // Old-school but not exception safe, favor make_unique<int[]>
    // int* dest = new int[dest_size];
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);
    int* dest = updest.get(); // get a raw pointer for the demo

    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    // Add another element to the vector to force an overrun.
    v.push_back(10);
    // The next line causes a debug assertion when it executes.
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));
}
```

## <a name="make_move_iterator"></a>make_move_iterator

Erstellt einen `move iterator`, der den bereitgestellten Iterator als `stored`-Iterator enthält.

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>Parameter

*_IT*\
Der Iterator, der im neuen Move-Iterator gespeichert ist.

### <a name="remarks"></a>Hinweise

Die Vorlagen Funktion gibt `move_iterator` `<Iterator>(_It)`zurück.

## <a name="make_unchecked_array_iterator"></a>make_unchecked_array_iterator

Erstellt ein [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)-Objekt, das von anderen Algorithmen verwendet werden kann.

> [!NOTE]
> Bei dieser Funktion handelt es sich um eine Microsoft-Erweiterung der C++-Standardbibliothek. Der Code, der mit dieser Funktion implementiert wird, ist nicht auf C++-Standardbuildumgebungen übertragbar, die die Microsoft-Erweiterung nicht unterstützen.

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>Parameter

*Ptr* -\
Ein Zeiger auf das Zielarray.

### <a name="return-value"></a>Rückgabewert

Eine Instanz von `unchecked_array_iterator`.

### <a name="remarks"></a>Hinweise

Die `make_unchecked_array_iterator`-Funktion wird im `stdext`-Namespace definiert.

Diese Funktion akzeptiert einen Rohzeiger und umschließt ihn in einer Klasse, die keine Überprüfung ausführt und daher nichts optimiert. Sie deaktiviert jedoch auch Compilerwarnungen wie [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Dies ist daher eine zielgerichtete Methode zur Bearbeitung von nicht aktivierten Zeigerwarnungen, ohne diese global zu deaktivieren oder den Aufwand der Überprüfung in Kauf zu nehmen. Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein [Vektor](../standard-library/vector-class.md) erstellt und mit 10 Elementen gefüllt. Der Inhalt des Vektors wird mithilfe des Kopieralgorithmus in ein Array kopiert. Anschließend wird `make_unchecked_array_iterator` verwendet, um das Ziel anzugeben.

```cpp
// make_unchecked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_unchecked_array_iterator
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

int main()
{
    const size_t dest_size = 10;
    int *dest = new int[dest_size];
    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun will trigger undefined behavior)
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    delete[] dest;
}
```

## <a name="next"></a>weiter

Führt eine bestimmte Anzahl von Iterationen aus und gibt die neue Position des Iterators zurück.

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Parameter

*erste*\
Die aktuelle Position.

*_Off*\
Die Anzahl der Iterationen.

### <a name="return-value"></a>Rückgabewert

Gibt die neue iteratorposition zurück, nachdem *_Off* Zeiten durchlaufen wurde.

### <a name="remarks"></a>Hinweise

Die Vorlagen Funktion gibt `next` inkrementierten *_Off* Zeiten zurück.

## <a name="prev"></a>Prev

Führt eine bestimmte Anzahl von Iterationen rückwärts aus und gibt die neue Position des Iterators zurück.

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Parameter

*erste*\
Die aktuelle Position.

*_Off*\
Die Anzahl der Iterationen.

### <a name="remarks"></a>Hinweise

Die Vorlagenfunktion gibt `next` dekrementiert `off`-Zeiten zurück.

## <a name="rbegin"></a>rbegin

```cpp
template <class C> constexpr auto rbegin(C& c) -> decltype(c.rbegin());
template <class C> constexpr auto rbegin(const C& c) -> decltype(c.rbegin());
```

## <a name="rend"></a>rend

```cpp
template <class C> constexpr auto rend(C& c) -> decltype(c.rend());
template <class C> constexpr auto rend(const C& c) -> decltype(c.rend());
```

## <a name="size"></a>Größe

```cpp
template <class C> constexpr auto size(const C& c) -> decltype(c.size());
template <class T, size_t N> constexpr size_t size(const T (&array)[N]) noexcept;
```
