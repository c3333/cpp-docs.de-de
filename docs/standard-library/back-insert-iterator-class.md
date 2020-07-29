---
title: back_insert_iterator-Klasse
ms.date: 11/04/2016
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
ms.openlocfilehash: 0a518253c28d89de6eeed51e152e11bfcb8bb969
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203880"
---
# <a name="back_insert_iterator-class"></a>back_insert_iterator-Klasse

Beschreibt einen Iteratoradapter, der den Anforderungen eines Ausgabeiterators entspricht. Er fügt Elemente in das Ende einer Sequenz ein, anstatt sie zu überschreiben, und bietet somit Semantik, die sich von der Semantik zum Überschreiben unterscheidet, die von den Iteratoren der C++-Sequenzcontainer bereitgestellt wird. Die `back_insert_iterator`-Klasse ist für den Typ des Containers vorlagenbasiert.

## <a name="syntax"></a>Syntax

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>Parameter

*Kum*\
Der Typ des Containers, an dessen Ende Elemente von einem `back_insert_iterator` eingefügt werden sollen.

## <a name="remarks"></a>Bemerkungen

Der Container muss den Anforderungen einer Sequenz zum Einfügen am Ende entsprechen, in der es möglich ist, die Elemente am Ende der Sequenz in amortisierter konstanter Zeit einzufügen. Die C++-Standardbibliothek-Sequenzcontainer, die von der [deque](../standard-library/deque-class.md)-Klasse, der [list](../standard-library/list-class.md)-Klasse und der [vector](../standard-library/vector-class.md)-Klasse definiert werden, stellen die erforderliche `push_back`-Memberfunktion bereit, und erfüllen diese Anforderungen. Diese drei Container sowie Zeichenfolgen werden jeweils für die Verwendung mit `back_insert_iterator` angepasst. Ein `back_insert_iterator` muss immer mit seinem Container initialisiert werden.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|Erstellt einen `back_insert_iterator`, der Elemente nach dem letzten Element in einen Container einfügt.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[container_type](#container_type)|Ein Typ, der einen Container für den `back_insert_iterator` bereitstellt.|
|[Referenz](#reference)|Ein Typ, der einen Verweis für den `back_insert_iterator` bereitstellt.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[KOM](#op_star)|Der Dereferenzierungsoperator, der zum Implementieren des ausgabeiteratorausdrucks \* `i`  =  `x` für eine Einfügung verwendet wird.|
|[Operator + +](#op_add_add)|Inkrementiert `back_insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.|
|[Operator =](#op_eq)|Der Zuweisungs Operator, der zum Implementieren des ausgabeiteratorausdrucks \* `i`  =  `x` für eine Einfügung verwendet wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**:\<iterator>

**Namespace:** std

## <a name="back_insert_iteratorback_insert_iterator"></a><a name="back_insert_iterator"></a>Back_insert_iterator:: Back_insert_iterator

Erstellt einen `back_insert_iterator`, der Elemente nach dem letzten Element in einen Container einfügt.

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parameter

*_Cont*\
Der Container, in den `back_insert_iterator` ein Element einfügen soll.

### <a name="return-value"></a>Rückgabewert

Ein `back_insert_iterator` für den Parametercontainer.

### <a name="example"></a>Beispiel

```cpp
// back_insert_iterator_back_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions with member function
   back_inserter ( vec ) = 40;
   back_inserter ( vec ) = 50;

   // Alternatively, insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 600;
   backiter++;
*backiter = 700;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 1 2 3 ).
After the insertions, the vector vec is: ( 1 2 3 40 50 600 700 ).
```

## <a name="back_insert_iteratorcontainer_type"></a><a name="container_type"></a>Back_insert_iterator:: container_type

Ein Typ, der einen Container für den `back_insert_iterator` bereitstellt.

```cpp
typedef Container
container_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist synonym mit dem Vorlagenparameter **Container**.

### <a name="example"></a>Beispiel

```cpp
// back_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The original vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::container_type vec1 = vec;
   back_inserter ( vec1 ) = 40;

   cout << "After the insertion, the vector is: ( ";
   for ( vIter = vec1.begin ( ) ; vIter != vec1.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector vec is: ( 1 2 3 ).
After the insertion, the vector is: ( 1 2 3 40 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_star"></a>Back_insert_iterator::-Operator\*

Der Dereferenzierungsoperator, der zum Implementieren des ausgabeiteratorausdrucks \* *i*  =  *x*verwendet wird.

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das am Ende des Containers eingefügte Element.

### <a name="remarks"></a>Bemerkungen

Wird verwendet, um den-ausgabeiteratorausdruck ** \* ITER**zu implementieren  =  **value**. Wenn **Iter** ein Iterator ist, der ein Element in einer Sequenz adressiert, dann ersetzt **\*Iter** = **value** das Element mit Wert, ohne dass die Gesamtzahl von Elementen in der Zeichenfolge geändert wird.

### <a name="example"></a>Beispiel

```cpp
// back_insert_iterator_back_insert.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
After the insertions, the vector vec becomes: ( 1 2 3 10 20 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_add_add"></a>Back_insert_iterator:: Operator + +

Inkrementiert `back_insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Ein `back_insert_iterator` zum folgenden Speicherort, an dem ein Wert gespeichert werden kann.

### <a name="remarks"></a>Bemerkungen

Sowohl der Prä- als auch der Postinkrement-Operator geben das gleichen Ergebnis zurück.

### <a name="example"></a>Beispiel

```cpp
// back_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 3 ; ++i )
   {
      vec.push_back ( 10 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;      // Increment to the next element
*backiter = 40;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 10 20 ).
After the insertions, the vector vec becomes: ( 10 20 30 40 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_eq"></a>Back_insert_iterator:: Operator =

Fügt einen Wert am Ende eines Containers ein, oder überträgt einen Wert dorthin.

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Der Wert, der in den Container eingefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das letzte am Ende des Containers eingefügte Element.

### <a name="remarks"></a>Bemerkungen

Der erste Memberoperator wertet `Container.push_back( val)` aus

dann wird zurückgegeben **`*this`** . Der zweite Memberoperator wertet Folgendes aus:

`container->push_back((typename Container::value_type&&)val)`,

dann wird zurückgegeben **`*this`** .

### <a name="example"></a>Beispiel

```cpp
// back_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

## <a name="back_insert_iteratorreference"></a><a name="reference"></a>Back_insert_iterator:: Reference

Ein Typ, der einen Verweis für den `back_insert_iterator` bereitstellt.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Bemerkungen

Ein Typ beschreibt den Verweis auf ein Element in der Sequenz, die durch den zugehörigen Container gesteuert wird.

### <a name="example"></a>Beispiel

```cpp
// back_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::reference
        RefLast = *(vec.end ( ) - 1 );
   cout << "The last element in the vector vec is: "
        << RefLast << "." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
The last element in the vector vec is: 3.
```

## <a name="see-also"></a>Weitere Informationen

[\<iterator>](../standard-library/iterator.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
