---
title: raw_storage_iterator-Klasse
ms.date: 11/04/2016
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
ms.openlocfilehash: 062a3db5c28bc463d6346a26cf1385adecd41183
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217635"
---
# <a name="raw_storage_iterator-class"></a>raw_storage_iterator-Klasse

Eine Adapterklasse, die bereitgestellt wird, um Algorithmen das Speichern ihrer Ergebnisse in nicht initialisiertem Speicher zu ermöglichen.

## <a name="syntax"></a>Syntax

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>Parameter

*OutputIterator*\
Gibt den Ausgabeiterator für das Objekt an, das gespeichert wird.

*Sorte*\
Der Typ des Objekts, dem Speicher zugeordnet wird.

## <a name="remarks"></a>Bemerkungen

Die Klasse beschreibt einen Ausgabeiterator, der Objekte des Typs `Type` in der generierten Sequenz konstruiert. Ein Objekt der Klasse `raw_storage_iterator` \< **ForwardIterator**, **Type**> greift über ein Forward-Iteratorobjekt der Klasse, `ForwardIterator` die Sie beim Erstellen des Objekts angeben, auf den Speicher zu. Für ein Objekt `ForwardIterator` , das zuerst die Klasse ist, muss der Ausdruck ** & \* zuerst** den nicht erstellten Speicher für das nächste Objekt (des Typs `Type` ) in der generierten Sequenz festlegen.

Diese Adapterklasse wird verwendet, wenn es erforderlich ist, Speicherbelegung und Objekterstellung zu trennen. `raw_storage_iterator` kann verwendet werden, um Objekte in nicht initialisierten Speicher zu kopieren, beispielsweise Arbeitsspeicher, der über die `malloc`-Funktion zugeordnet wurde.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Erstellt einen unformatierten Speicheriterator mit einem angegebenen zugrunde liegenden Ausgabeiterator.|

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[element_type](#element_type)|Stellt einen Typ bereit, der ein Element beschreibt, das in einem unformatierten Speicheriterator gespeichert werden soll.|
|[iter_type](#iter_type)|Stellt einen Typ bereit, der einen Iterator beschreibt, der einem unformatierten Speicheriterator zugrunde liegt.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[KOM](#op_star)|Ein Dereferenzierungsoperator, der zum Implementieren des ausgabeiteratorausdrucks verwendet wird \* `ii`  =  `x` .|
|[Operator =](#op_eq)|Ein Zuweisungs Operator, mit dem der unformatierte speicheriteratorausdruck \* `i`  =  `x` zum Speichern im Arbeitsspeicher implementiert wird.|
|[Operator + +](#op_add_add)|Inkrementoperatoren in Präfix- und Postfix-Notation für unformatierte Speicheriteratoren.|

### <a name="element_type"></a><a name="element_type"></a>element_type

Stellt einen Typ bereit, der ein Element beschreibt, das in einem unformatierten Speicheriterator gespeichert werden soll.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Raw_storage_iterator Klassen Vorlagen Parameter `Type` .

### <a name="iter_type"></a><a name="iter_type"></a>iter_type

Stellt einen Typ bereit, der einen Iterator beschreibt, der einem unformatierten Speicheriterator zugrunde liegt.

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `ForwardIterator` dar.

### <a name="operator"></a><a name="op_star"></a>KOM\*

Ein Dereferenzierungsoperator, der verwendet wird, um den RAW-speicheriteratorausdruck \* *II*  =  *x*zu implementieren.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>Rückgabewert

Ein Verweis auf den unformatierten Speicheriterator.

#### <a name="remarks"></a>Bemerkungen

Die Anforderungen für einen `ForwardIterator` lauten, dass der unformatierte speicheriterator nur den \* gültigen Ausdruck *II*  =  *t* erfordern muss und dass er nichts über den **`operator`** oder den `operator=` selbst sagt. Die-Member-Operatoren in dieser Implementierung geben ** \* dieses**zurück, sodass [Operator =](#op_eq)(**consttype**&) den tatsächlichen Speicher in einem Ausdruck (z \* . b. *ptr*) ausführen kann  =  `val` .

#### <a name="example"></a>Beispiel

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
*pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="operator"></a><a name="op_eq"></a>Operator =

Der Zuweisungs Operator, der zum Implementieren des unformatierten Speicher-iteratorausdrucks \* *i*  =  *x* zum Speichern im Arbeitsspeicher verwendet

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>Parameter

*ster*\
Der Wert des Objekts vom Typ `Type` , der in den Arbeitsspeicher eingefügt werden soll.

#### <a name="return-value"></a>Rückgabewert

Der Operator fügt `val` in den Speicher ein, und gibt dann einen Verweis auf den unformatierten Speicheriterator zurück.

#### <a name="remarks"></a>Bemerkungen

Die Anforderungen für einen `ForwardIterator` Zustand, den der unformatierte speicheriterator erfüllen muss, erfordern nur den gültigen Ausdruck \* *II*  =  *t* , und es wird nichts über den **`operator`** oder den eigenen Text angezeigt `operator=` . Diese Member-Operatoren geben zurück **`*this`** .

Der Zuweisungs Operator erstellt das nächste Objekt in der Ausgabe Sequenz mit dem gespeicherten iteratorwert `first` , indem der Platzierungs New-Ausdruck ausgewertet wird `new ( (void*) & *first ) Type( val )` .

#### <a name="example"></a>Beispiel

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="operator"></a><a name="op_add_add"></a>Operator + +

Inkrementoperatoren in Präfix- und Postfix-Notation für unformatierte Speicheriteratoren.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

#### <a name="return-value"></a>Rückgabewert

Ein unformatierten Speicheriterator oder ein Verweis auf einen unformatierten Speicheriterator.

#### <a name="remarks"></a>Bemerkungen

Der erste Operator versucht schließlich, ein Objekt vom Typ `CharType` aus dem zugeordneten Eingabestream zu extrahieren und zu speichern. Der zweite Operator erstellt eine Kopie des Objekts, inkrementiert das Objekt und gibt dann die Kopie zurück.

Der erste preincrement-Operator erhöht das gespeicherte ausgabeiteratorobjekt und gibt ** \* dieses**zurück.

Der zweite postincrement-Operator erstellt eine Kopie ** \* dieses**, erhöht das gespeicherte ausgabeiteratorobjekt und gibt dann die Kopie zurück.

Der Konstruktor speichert `first` als ausgabeiteratorobjekt.

#### <a name="example"></a>Beispiel

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
      *it = 2 * i;
   };

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
```

```Output
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
```

### <a name="raw_storage_iterator"></a><a name="raw_storage_iterator"></a>raw_storage_iterator

Erstellt einen unformatierten Speicheriterator mit einem angegebenen zugrunde liegenden Ausgabeiterator.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

#### <a name="parameters"></a>Parameter

*erstes*\
Der Forward-Iterator, mit dem das `raw_storage_iterator`-Objekt erstellt wird.

#### <a name="example"></a>Beispiel

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
```

```Output
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
```
