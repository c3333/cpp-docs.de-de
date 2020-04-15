---
title: insert_iterator-Klasse
ms.date: 11/04/2016
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
ms.openlocfilehash: 2865db023425fa301ad5440a0dc8ed491213f33f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368055"
---
# <a name="insert_iterator-class"></a>insert_iterator-Klasse

Beschreibt einen Iteratoradapter, der den Anforderungen eines Ausgabeiterators entspricht. Er fügt Elemente in eine Sequenz ein, anstatt sie zu überschreiben, und bietet somit Semantik, die sich von der Semantik zum Überschreiben unterscheidet, die von den Iteratoren der C++-Sequenz und assoziativen Containern bereitgestellt wird. Die `insert_iterator`-Klasse ist für den Typ des Containers, der angepasst wird, vorlagenbasiert.

## <a name="syntax"></a>Syntax

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>Parameter

*Container*\
Der Typ des Containers, in den Elementen von einem `insert_iterator` eingefügt werden sollen.

## <a name="remarks"></a>Bemerkungen

Der Container `Container` des Typs muss die Anforderungen für einen Container mit variabler Größe erfüllen `Container::iterator` `Container::value_type` und über eine `Container::iterator`Zwei-Argument-Insert-Memberfunktion verfügen, bei der die Parameter vom Typ sind und der einen Typ zurückgibt. Die C++-Standardbibliothekssequenz und sortierte assoziative Container erfüllen diese Anforderungen und können mit `insert_iterator`-Objekten angepasst werden. Für assoziative Container wird das Positionsargument als Hinweis behandelt, der die Leistung je nach Qualität potenziell verbessern oder verschlechtern kann. Ein `insert_iterator` muss immer mit seinem Container initialisiert werden.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[insert_iterator](#insert_iterator)|Erstellt einen `insert_iterator`, der ein Element an einer bestimmten Position in einen Container einfügt.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[container_type](#container_type)|Ein Typ, der den Container darstellt, in dem eine allgemeine Einfügung vorgenommen werden soll.|
|[Verweis](#reference)|Ein Typ, der einen Verweis auf ein Element in einer Sequenz enthält, die durch den zugehörigen Container gesteuert wird.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator*](#op_star)|Der Dereferenzierungsoperator, der verwendet wird, um den Ausgabeiteratorausdruck *`i` = `x` für eine allgemeine Einfügung zu implementieren.|
|[Operator++](#op_add_add)|Inkrementiert `insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.|
|[Operator=](#op_eq)|Der Zuweisungsoperator, der verwendet wird, um den Ausgabeiteratorausdruck *`i` = `x` für eine allgemeine Einfügung zu implementieren.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile**: \<Iterator>

**Namespace:** std

## <a name="insert_iteratorcontainer_type"></a><a name="container_type"></a>insert_iterator::container_type

Ein Typ, der den Container darstellt, in dem eine allgemeine Einfügung vorgenommen werden soll.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist synonym mit dem Vorlagenparameter *Container*.

### <a name="example"></a>Beispiel

```cpp
// insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   insert_iterator<list<int> >::container_type L2 = L1;
   inserter ( L2, L2.end ( ) ) = 20;
   inserter ( L2, L2.end ( ) ) = 10;
   inserter ( L2, L2.begin ( ) ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 20 10 ).
*/
```

## <a name="insert_iteratorinsert_iterator"></a><a name="insert_iterator"></a>insert_iterator::insert_iterator

Erstellt einen `insert_iterator`, der ein Element an einer bestimmten Position in einen Container einfügt.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>Parameter

*_Cont*\
Der Container, in den `insert_iterator` Elemente einfügen soll.

*_It*\
Die Position, an der eingefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Für alle Container wird die Memberfunktion zum Einfügen von `insert_iterator` aufgerufen. Für zugehörige Container ist der Positionsparameter nur ein Vorschlag. Mit der Funktion zum Einfügen können Sie bequem Werte einfügen.

### <a name="example"></a>Beispiel

```cpp
// insert_iterator_insert_iterator.cpp
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
   for (i = 1 ; i < 4 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   inserter ( L, L.begin ( ) ) = 2;

   // Alternatively, you may use the template version
   insert_iterator< list < int> > Iter(L, L.end ( ) );
*Iter = 300;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( 10 20 30 ).
After the insertions, the list L is:
( 2 10 20 30 300 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_star"></a>insert_iterator::Operator*

Dereferenziert den Iterator zum Einfügen, und gibt das Element zurück, das es adressiert.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt den Wert des adressierten Elements zurück

### <a name="remarks"></a>Bemerkungen

Wird verwendet, um den Ausgabeiteratorausdruck =  ** \*Iter-Wert**zu implementieren.**value** Wenn `Iter` es sich um einen Iterator handelt, der ein Element in einer Sequenz adressiert, ersetzt ** \*der Iter-Wert** = **value** dieses Element durch einen Wert und ändert nicht die Gesamtzahl der Elemente in der Sequenz.

### <a name="example"></a>Beispiel

```cpp
// insert_iterator_op_deref.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_add_add"></a>insert_iterator::operator++

Inkrementiert `insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>Parameter

Ein `insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.

### <a name="remarks"></a>Bemerkungen

Sowohl der Prä- als auch der Postinkrement-Operator geben das gleichen Ergebnis zurück.

### <a name="example"></a>Beispiel

```cpp
// insert_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 5 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   insert_iterator<vector<int> > ii ( vec, vec.begin ( ) );
*ii = 30;
   ii++;
*ii = 40;
   ii++;
*ii = 50;

   cout << "After the insertions, the vector vec becomes:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The vector vec is:
( 1 2 3 4 ).
After the insertions, the vector vec becomes:
( 30 40 50 1 2 3 4 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_eq"></a>insert_iterator::operator=

Fügt einen Wert in einen Container ein, und gibt den Iterator, der aktualisiert wurde, um auf das neue Element zu verweisen.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>Parameter

*Val*\
Der Wert, der dem Container zugewiesen werden soll

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das in den Container eingefügte Element.

### <a name="remarks"></a>Bemerkungen

Der erster Memberoperator wertet Folgendes aus:

`Iter = container->insert(Iter, val)`;

`++Iter;`

danach gibt er `*this` zurück.

Der zweite Memberoperator wertet Folgendes aus:

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

danach gibt er `*this` zurück.

### <a name="example"></a>Beispiel

```cpp
// insert_iterator_op_assign.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratorreference"></a><a name="reference"></a>insert_iterator::Referenz

Ein Typ, der einen Verweis auf ein Element in einer Sequenz enthält, die durch den zugehörigen Container gesteuert wird.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Bemerkungen

Ein Typ beschreibt den Verweis auf ein Element in der Sequenz, die durch den zugehörigen Container gesteuert wird.

### <a name="example"></a>Beispiel

```cpp
// insert_iterator_container_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   insert_iterator<list<int> > iivIter( L , L.begin ( ) );
*iivIter = 10;
*iivIter = 20;
*iivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++ )
      cout << *LIter << " ";
   cout << ")." << endl;

   insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*/
```

## <a name="see-also"></a>Siehe auch

[\<iterator>](../standard-library/iterator.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)
