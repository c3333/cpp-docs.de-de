---
title: front_insert_iterator-Klasse
ms.date: 11/04/2016
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
ms.openlocfilehash: 455db433aff1c1aa241beeb6e2435807959b7dd4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317146"
---
# <a name="front_insert_iterator-class"></a>front_insert_iterator-Klasse

Beschreibt einen Iteratoradapter, der den Anforderungen eines Ausgabeiterators entspricht. Er fügt Elemente in den Anfang einer Sequenz ein, anstatt sie zu überschreiben, und bietet somit Semantik, die sich von der Semantik zum Überschreiben unterscheidet, die von den Iteratoren der C++-Sequenzcontainer bereitgestellt wird. Die `front_insert_iterator`-Klasse ist für den Typ des Containers vorlagenbasiert.

## <a name="syntax"></a>Syntax

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>Parameter

*Container*\
Der Typ des Containers, an dessen Anfang Elemente von einem `front_insert_iterator` eingefügt werden sollen.

## <a name="remarks"></a>Bemerkungen

Der Container muss den Anforderungen einer Sequenz zum Einfügen am Anfang entsprechen, in der es möglich ist, die Elemente am Anfang der Sequenz in amortisierter konstanter Zeit einzufügen. Die Sequenzcontainer der C++-Standardbibliothek, die durch die [deque-Klasse](../standard-library/deque-class.md) und die [list-Klasse](../standard-library/list-class.md) definiert werden, stellen die erforderliche `push_front`-Memberfunktion bereit und erfüllen diese Anforderungen. Im Gegensatz dazu erfüllen die Sequenzcontainer, die von der [vector-Klasse](../standard-library/vector-class.md) definiert sind, diese Anforderungen nicht und können nicht zur Verwendung mit `front_insert_iterator`-Objekten angepasst werden. Ein `front_insert_iterator` muss immer mit seinem Container initialisiert werden.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|Damit wird ein Iterator erstellt, mit dem Elemente an den Anfang eines bestimmten Containerobjekts eingefügt werden können.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[container_type](#container_type)|Ein Typ, der den Container darstellt, in dem eine Einfügung am Anfang vorgenommen werden soll.|
|[Verweis](#reference)|Ein Typ, der einen Verweis auf ein Element in einer Sequenz enthält, die durch den zugehörigen Container gesteuert wird.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator*](#op_star)|Dereferencing-Operator wird verwendet, um den \* `i`  =  `x` Ausgabe-Iterator-Ausdruck für eine Fronteinfügung zu implementieren.|
|[Operator++](#op_add_add)|Inkrementiert `front_insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.|
|[Operator=](#op_eq)|Zuweisungsoperator, der verwendet wird, \* `i`  =  `x` um den Ausgabeiteratorausdruck für eine Fronteinfügung zu implementieren.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile**: \<Iterator>

**Namespace:** std

## <a name="front_insert_iteratorcontainer_type"></a><a name="container_type"></a>front_insert_iterator::container_type

Ein Typ, der den Container darstellt, in dem eine Einfügung am Anfang vorgenommen werden soll.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist synonym mit dem Vorlagenparameter *Container*.

### <a name="example"></a>Beispiel

```cpp
// front_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> >::container_type L2 = L1;
   front_inserter ( L2 ) = 20;
   front_inserter ( L2 ) = 10;
   front_inserter ( L2 ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 10 20 ).
*/
```

## <a name="front_insert_iteratorfront_insert_iterator"></a><a name="front_insert_iterator"></a>front_insert_iterator::front_insert_iterator

Damit wird ein Iterator erstellt, mit dem Elemente an den Anfang eines bestimmten Containerobjekts eingefügt werden können.

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parameter

*_Cont*\
Das Containerobjekt, in das `front_insert_iterator` Elemente einfügen soll

### <a name="return-value"></a>Rückgabewert

Ein `front_insert_iterator` für das Parametercontainerobjekt

### <a name="example"></a>Beispiel

```cpp
// front_insert_iterator_front_insert_iterator.cpp
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
   for (i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   front_inserter ( L ) = 20;

   // Alternatively, one may use the template function
   front_insert_iterator< list < int> > Iter(L);
*Iter = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_star"></a>front_insert_iterator::Operator\*

Dereferenziert den Iterator zum Einfügen und gibt das Element zurück, das es adressiert

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt den Wert des adressierten Elements zurück

### <a name="remarks"></a>Bemerkungen

Wird verwendet, um den Ausgabeiteratorausdruck =  ** \*Iter-Wert**zu implementieren.**value** Wenn `Iter` es sich um einen Iterator handelt, der ein Element in einer Sequenz adressiert, ersetzt ** \*der Iter-Wert** = **value** dieses Element durch einen Wert und ändert nicht die Gesamtzahl der Elemente in der Sequenz.

### <a name="example"></a>Beispiel

```cpp
// front_insert_iterator_deref.cpp
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
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   front_insert_iterator< list < int> > Iter(L);
*Iter = 20;

   // Alternatively, you may use
   front_inserter ( L ) = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_add_add"></a>front_insert_iterator::operator++

Inkrementiert `back_insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Ein `front_insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.

### <a name="remarks"></a>Bemerkungen

Sowohl der Prä- als auch der Postinkrement-Operator geben das gleichen Ergebnis zurück.

### <a name="example"></a>Beispiel

```cpp
// front_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_eq"></a>front_insert_iterator::operator=

Fügt einen Wert (per Push) am Anfang des Containers an

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parameter

*Val*\
Der Wert, der dem Container zugewiesen werden soll

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das letzte, am Anfang des Containers eingefügte Element

### <a name="remarks"></a>Bemerkungen

Der erster Memberoperator wertet `container.push_front( val)` aus und gibt `*this` zurück.

Der zweite Memberoperator wertet Folgendes aus:

`container->push_front((typename Container::value_type&&) val)`,

danach gibt er `*this` zurück.

### <a name="example"></a>Beispiel

```cpp
// front_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratorreference"></a><a name="reference"></a>front_insert_iterator::Referenz

Ein Typ, der einen Verweis auf ein Element in einer Sequenz enthält, die durch den zugehörigen Container gesteuert wird.

```cpp
typedef typename Container::reference reference;
```

### <a name="example"></a>Beispiel

```cpp
// front_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   front_insert_iterator<list<int> > fiivIter( L );
*fiivIter = 10;
*fiivIter = 20;
*fiivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)
      cout << *LIter << " ";
   cout << ")." << endl;

   front_insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*/
```

## <a name="see-also"></a>Siehe auch

[\<iterator>](../standard-library/iterator.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)
