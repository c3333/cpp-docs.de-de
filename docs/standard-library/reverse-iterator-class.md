---
title: reverse_iterator-Klasse
ms.date: 03/27/2019
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
ms.openlocfilehash: 882d0f7f4930e9d809098a29384a962d0aa8f4ea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373437"
---
# <a name="reverse_iterator-class"></a>reverse_iterator-Klasse

Die Klassenvorlage ist ein Iteratoradapter, der ein umgekehrtes Iteratorobjekt beschreibt, das sich wie ein zufälliger oder bidirektionaler Iterator verhält, nur umgekehrt. Er ermöglicht es, einen Bereich rückwärts zu durchlaufen.

## <a name="syntax"></a>Syntax

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>Parameter

RandomIterator Der Typ, der den Iterator darstellt, der angepasst werden soll, um rückwärts zu arbeiten.

## <a name="remarks"></a>Bemerkungen

Vorhandene C++-Standardbibliothekscontainer definieren auch die Typen `reverse_iterator` und `const_reverse_iterator` und verfügen über die Memberfunktionen `rbegin` und `rend`, die Reverse-Iteratoren zurückgeben. Diese Iteratoren verfügen über Semantik zum Überschreiben. Der `reverse_iterator` Adapter ergänzt diese Funktionalität, da er Insert-Semantik bietet und auch mit Streams verwendet werden kann.

`reverse_iterator` Der, der einen bidirektionalen Iterator erfordert, `operator+=` `operator+`darf `operator-=` `operator-`keine `operator[]`der Memberfunktionen , , , oder aufrufen, die nur mit Iteratoren mit zufälligem Zugriff verwendet werden dürfen.

Der Bereich eines Iterators ist [*erster*, *letzter*), wobei die eckige Klammer auf der linken Seite die Aufnahme der *ersten* und die Klammer auf der rechten Seite die Aufnahme von Elementen bis zum letzten *selbst* anzeigt. Dieselben Elemente sind in der umgekehrten Sequenz [ **rev** - *first*, **rev** - *last*) enthalten, so dass, wenn *zuletzt* das One-Past-the-End-Element in einer Sequenz ist, dann das erste Element **zuerst** - *in* der umgekehrten Sequenz auf \*(*zuletzt* - 1) zeigt. Die Identität, die alle umgekehrten Iteratoren auf die zugrunde liegenden Iteratoren bezieht:

&\*( **reverse_iterator** ( *i* \*) ) == &( *i* - 1 ).

In der Praxis bedeutet dies, dass in der umgekehrten Sequenz das reverse_iterator-Objekt auf das Element verweist, das eine Position hinter dem Element (rechts davon) liegt, auf das der Iterator in der ursprünglichen Sequenz verwiesen hat. Wenn ein Iterator das Element 6 in der Sequenz adressierte (2, 4, 6, 8), dann adressiert `reverse_iterator` das Element 4 in der umgekehrten Sequenz (8, 6, 4, 2).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[reverse_iterator](#reverse_iterator)|Erstellt aus einem zugrunde liegenden Iterator einen standardmäßigen `reverse_iterator` oder `reverse_iterator`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[difference_type](#difference_type)|Ein Typ, mit dem der Unterschied zwischen zwei `reverse_iterator`en bereitgestellt wird, die auf Elemente innerhalb desselben Containers verweisen.|
|[iterator_type](#iterator_type)|Ein Typ, der einen zugrunde liegenden Iterator für einen `reverse_iterator` bereitstellt.|
|[Zeiger](#pointer)|Ein Typ, mit dem ein Zeiger auf ein Element bereitgestellt wird, die von `reverse_iterator` adressiert werden.|
|[Verweis](#reference)|Ein Typ, mit dem ein Verweis auf ein Element bereitgestellt wird, die von `reverse_iterator` adressiert werden.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[base](#base)|Stellt den zugrunde liegenden Iterator aus `reverse_iterator` wieder her.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[operator_star](#op_star)|Gibt das Element zurück, das ein `reverse_iterator` adressiert.|
|[Operator+](#op_add)|Fügt einen Offset zu einem Iterator hinzu und gibt den neuen `reverse_iterator` zurück, der auf das eingefügte Element an der neuen Offsetposition zeigt.|
|[Operator++](#op_add_add)|Erhöht `reverse_iterator` zum nächsten Element.|
|[Operator+=](#op_add_eq)|Fügt einen angegebenen Offset aus einem `reverse_iterator` hinzu.|
|[Betreiber-](#operator-)|Subtrahiert einen Offset von einem `reverse_iterator` und gibt einen `reverse_iterator` zurück, der das Element an die Offsetposition adressiert.|
|[Betreiber--](#operator--)|Verringert `reverse_iterator` zum vorherigen Element.|
|[operator-=](#operator-_eq)|Subtrahiert einen angegebenen Offset von einem `reverse_iterator`.|
|[Operator->](#op-arrow)|Gibt einen Zeiger auf das Element zurück, das von `reverse_iterator` adressiert wird.|
|[operator&#91;&#93;](#op_at)|Gibt einen Verweis auf ein Elementoffset aus dem Element zurück, das von `reverse_iterator` mithilfe der angegebenen Anzahl von Positionen adressiert wird.|

## <a name="requirements"></a>Anforderungen

**Header:** \<iterator>

**Namespace:** std

## <a name="reverse_iteratorbase"></a><a name="base"></a>reverse_iterator::Basis

Stellt den zugrunde liegenden Iterator aus `reverse_iterator` wieder her.

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>Rückgabewert

Der `reverse_iterator` zugrunde liegenden Iterator.

### <a name="remarks"></a>Bemerkungen

Die Identität, die alle umgekehrten Iteratoren auf die zugrunde liegenden Iteratoren bezieht:

&\*( `reverse_iterator` ( *i* ) \*) == &( *i* - 1 ).

In der Praxis bedeutet dies, dass in der umgekehrten Sequenz `reverse_iterator` auf das Element verweist, das eine Position hinter dem Element (rechts davon) liegt, auf das der Iterator in der ursprünglichen Sequenz verwiesen hat. Wenn ein Iterator das Element 6 in der Sequenz adressierte (2, 4, 6, 8), dann adressiert `reverse_iterator` das Element 4 in der umgekehrten Sequenz (8, 6, 4, 2).

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_base.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );
   cout << "The iterator pos points to: " << *pos << "." << endl;

   typedef reverse_iterator<vector<int>::iterator>::iterator_type it_vec_int_type;

   reverse_iterator<it_vec_int_type> rpos ( pos );
   cout << "The reverse_iterator rpos points to: " << *rpos
        << "." << endl;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
```

## <a name="reverse_iteratordifference_type"></a><a name="difference_type"></a>reverse_iterator::difference_type

Ein Typ, mit dem der Unterschied zwischen zwei `reverse_iterator`en bereitgestellt wird, die auf Elemente innerhalb desselben Containers verweisen.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der `reverse_iterator`-Differenztyp ist identisch mit den Differenztyp des Iterators.

Der `iterator_traits` \< Typ ist ein Synonym für den Iterator-Merkmalstyp **RandomIterator**> **::pointer**.

### <a name="example"></a>Beispiel

Unter [reverse_iterator::operator&#91;&#93;](#op_at) finden Sie ein Beispiel für das Deklarieren und Verwenden von `difference_type`.

## <a name="reverse_iteratoriterator_type"></a><a name="iterator_type"></a>reverse_iterator::iterator_type

Ein Typ, der einen zugrunde liegenden Iterator für einen `reverse_iterator` bereitstellt.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Iterator` dar.

### <a name="example"></a>Beispiel

Unter [reverse_iterator::base](#base) finden Sie ein Beispiel für das Deklarieren und Verwenden von `iterator_type`.

## <a name="reverse_iteratoroperator"></a><a name="op_star"></a>reverse_iterator::Operator\*

Gibt das Element, das ein reverse_iterator behandelt, zurück.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert der Elemente, die durch den reverse_iterator behoben wurden.

### <a name="remarks"></a>Bemerkungen

Der Operator \*gibt zurück ( **aktuell** - 1).

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_op_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );

   // Declare a difference type for a parameter
   // declare a reference return type
   reverse_iterator<vector<int>::iterator>::reference refpos = *pos;
   cout << "The iterator pos points to: " << refpos << "." << endl;
}
```

## <a name="reverse_iteratoroperator"></a><a name="op_add"></a>reverse_iterator::operator+

Fügt einen Offset zu einem Iterator hinzu und gibt den neuen `reverse_iterator` zurück, der auf das eingefügte Element an der neuen Offsetposition zeigt.

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>Parameter

*Aus*\
Der zum umgekehrten Iterator hinzuzufügende Offset.

### <a name="return-value"></a>Rückgabewert

Ein `reverse_iterator`, der das Offsetelement adressiert.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion kann nur verwendet werden, wenn die `reverse_iterator` die Anforderungen für einen Random-Access-Iterator erfüllt.

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_op_add.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 + 2; // offset added
   cout << "After the +2 offset, the iterator rVPOS2 points\n"
        << " to the 3rd element in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS2 points
to the 3rd element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_add"></a>reverse_iterator::operator++

Erhöht den reverse_iterator auf das vorherige Element.

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Der erste Operator gibt den präinkrementierten `reverse_iterator` zurück, der zweite Postinkrementoperator gibt eine Kopie des inkrementierten `reverse_iterator` zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion kann nur verwendet werden, wenn die `reverse_iterator` die Anforderungen für einen bidirektionaler Iterator erfüllt.

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1++;  // postincrement, preincrement: ++rVPSO1

   cout << "After incrementing, the iterator rVPOS1 points\n"
        << " to the second element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 9.
After incrementing, the iterator rVPOS1 points
to the second element in the reversed sequence: 7.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_eq"></a>reverse_iterator::operator+=

Fügt einen angegebenen Offset aus einem reverse_iterator hinzu.

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>Parameter

*Aus*\
Der Offset, um den der Iterator inkrementiert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das von `reverse_iterator` adressierte Element.

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_op_addoff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1+=2;   // addition of an offset
   cout << "After the +2 offset, the iterator rVPOS1 now points\n"
        << " to the third element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS1 now points
to the third element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-"></a>reverse_iterator::Operator-

Subtrahiert einen Offset von einem `reverse_iterator` und gibt einen `reverse_iterator` zurück, der das Element an die Offsetposition adressiert.

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>Parameter

*Aus*\
Der Offset, der vom reverse_iterator subtrahiert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein `reverse_iterator`, der das Offsetelement adressiert.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion kann nur verwendet werden, wenn die `reverse_iterator` die Anforderungen für einen Random-Access-Iterator erfüllt.

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_op_sub.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 - 2; // offset subtracted
   cout << "After the -2 offset, the iterator rVPOS2 points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS2 points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator--"></a><a name="operator--"></a>reverse_iterator::Operator--

Erniedrigt den reverse_iterator auf das vorherige Element.

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>Rückgabewert

Der erste Operator gibt den prädekrementierten `reverse_iterator` zurück, der zweite Postdekrementoperator gibt eine Kopie des dekrementierten `reverse_iterator` zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion kann nur verwendet werden, wenn die `reverse_iterator` die Anforderungen für einen bidirektionaler Iterator erfüllt.

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_op_decr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;
   rVPOS1--;  // postdecrement, predecrement: --rVPSO1

   cout << "After the decrement, the iterator rVPOS1 points\n"
        << " to the next-to-last element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 1.
After the decrement, the iterator rVPOS1 points
to the next-to-last element in the reversed sequence: 3.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-_eq"></a>reverse_iterator::operator-=

Subtrahiert einen angegebenen Offset von einem `reverse_iterator`.

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>Parameter

*Aus*\
Der Offset, der vom `reverse_iterator` subtrahiert werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion kann nur verwendet werden, wenn die `reverse_iterator` die Anforderungen für einen Random-Access-Iterator erfüllt.

Der Operator wertet **den aktuellen** + *Aus* aus und ** \*gibt**diese zurück.

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_op_suboff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1-=2;      // Subtraction of an offset
   cout << "After the -2 offset, the iterator rVPOS1 now points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS1 now points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator-gt"></a><a name="op-arrow"></a>reverse_iterator::Operator-&gt;

Gibt einen Zeiger auf das Element zurück, das von `reverse_iterator` adressiert wird.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das von `reverse_iterator` adressierte Element.

### <a name="remarks"></a>Bemerkungen

Der Operator gibt ** & \* \*diese**zurück.

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_ptrto.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back(pVector::value_type(1,2));
   vec.push_back(pVector::value_type(3,4));
   vec.push_back(pVector::value_type(5,6));

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::reverse_iterator rpvIter;
   cout << "The vector vec reversed is:\n( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++ )
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "The iterator pos points to:\n( " << pos -> first << ", "
   << pos -> second << " )" << endl << endl;

   pVector::reverse_iterator rpos (pos);

   // Use operator -> with return type: why type int and not int*
   int fint = rpos -> first;
   int sint = rpos -> second;

   cout << "The reverse_iterator rpos points to:\n( " << fint << ", "
   << sint << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The reverse_iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratoroperator"></a><a name="op_at"></a>reverse_iterator::operator[]

Gibt einen Verweis auf ein Elementoffset aus dem Element zurück, das von `reverse_iterator` mithilfe der angegebenen Anzahl von Positionen adressiert wird.

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>Parameter

*Aus*\
Der Offset von der `reverse_iterator`-Adresse.

### <a name="return-value"></a>Rückgabewert

Der Verweis auf den Elementoffset.

### <a name="remarks"></a>Bemerkungen

Der Operator <strong>\*</strong>gibt zurück ( ** \*dies** + `Off`).

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_ret_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 8 );
   reverse_iterator<vector<int>::iterator> rpos ( pos );

   // Declare a difference type for a parameter
   reverse_iterator<vector<int>::iterator>::difference_type diff = 2;

   cout << "The iterator pos points to: " << *pos << "." << endl;
   cout << "The iterator rpos points to: " << *rpos << "." << endl;

   // Declare a reference return type & use operator[]
   reverse_iterator<vector<int>::iterator>::reference refrpos = rpos [diff];
   cout << "The iterator rpos now points to: " << refrpos << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator pos points to: 8.
The iterator rpos points to: 6.
The iterator rpos now points to: 2.
```

## <a name="reverse_iteratorpointer"></a><a name="pointer"></a>reverse_iterator::pointer

Ein Typ, mit dem ein Zeiger auf ein Element bereitgestellt wird, die von `reverse_iterator` adressiert werden.

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Der `iterator_traits` \< Typ ist ein Synonym für den Iterator-Merkmalstyp *RandomIterator*> **::pointer**.

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back( pVector::value_type( 1,2 ) );
   vec.push_back( pVector::value_type( 3,4 ) );
   vec.push_back( pVector::value_type( 5,6 ) );

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n" << "( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl;

   pVector::reverse_iterator rpvIter;
   cout << "\nThe vector vec reversed is:\n" << "( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++)
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "\nThe iterator pos points to:\n"
        << "( " << pos -> first << ", "
        << pos -> second << " )" << endl;

   pVector::reverse_iterator rpos (pos);
   cout << "\nThe iterator rpos points to:\n"
        << "( " << rpos -> first << ", "
        << rpos -> second << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratorreference"></a><a name="reference"></a>reverse_iterator::Referenz

Ein Typ, mit dem ein Verweis auf ein Element bereitgestellt wird, das von reverse_iterator adressiert wird.

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>Bemerkungen

Der `iterator_traits` \< Typ ist ein Synonym für den Iterator-Merkmalstyp *RandomIterator*> **::reference**.

### <a name="example"></a>Beispiel

Beispiele für die Deklaribilieren und Verwendung `reference`finden Sie unter [reverse_iterator::operator&#91;&#93;](#op_at) oder [reverse_iterator::operator*](#op_star) .

## <a name="reverse_iteratorreverse_iterator"></a><a name="reverse_iterator"></a>reverse_iterator::reverse_iterator

Erstellt aus einem zugrunde liegenden Iterator einen standardmäßigen `reverse_iterator` oder `reverse_iterator`.

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Iterator, der auf `reverse_iterator` angepasst werden soll.

### <a name="return-value"></a>Rückgabewert

Erstellt aus einem zugrunde liegenden Iterator einen standardmäßigen `reverse_iterator` oder `reverse_iterator`.

### <a name="remarks"></a>Bemerkungen

Die Identität, die alle umgekehrten Iteratoren auf die zugrunde liegenden Iteratoren bezieht:

&\*( `reverse_iterator` ( *i* ) \*) == &( *i* - 1 ).

In der Praxis bedeutet dies, dass in der umgekehrten Sequenz das reverse_iterator-Objekt auf das Element verweist, das eine Position hinter dem Element (rechts davon) liegt, auf das der Iterator in der ursprünglichen Sequenz verwiesen hat. Wenn ein Iterator das Element 6 in der Sequenz adressierte (2, 4, 6, 8), dann adressiert `reverse_iterator` das Element 4 in der umgekehrten Sequenz (8, 6, 4, 2).

### <a name="example"></a>Beispiel

```cpp
// reverse_iterator_reverse_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 4 );
   cout << "The iterator pos = " << *pos << "." << endl;

   vector <int>::reverse_iterator rpos ( pos );
   cout << "The reverse_iterator rpos = " << *rpos
        << "." << endl;
}
```

## <a name="see-also"></a>Siehe auch

[\<iterator>](../standard-library/iterator.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)
