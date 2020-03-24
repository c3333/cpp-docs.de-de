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
ms.openlocfilehash: 9372fa884d75e10c1a0f2ec92d6cca9caa65808e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167614"
---
# <a name="raw_storage_iterator-class"></a>raw_storage_iterator-Klasse

Eine Adapterklasse, die bereitgestellt wird, um Algorithmen das Speichern ihrer Ergebnisse in nicht initialisiertem Speicher zu ermöglichen.

## <a name="syntax"></a>Syntax

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>Parameter

*OutputIterator* -\
Gibt den Ausgabeiterator für das Objekt an, das gespeichert wird.

*Typ*\
Der Typ des Objekts, dem Speicher zugeordnet wird.

## <a name="remarks"></a>Bemerkungen

Die Klasse beschreibt einen Ausgabeiterator, der Objekte des Typs `Type` in der generierten Sequenz konstruiert. Ein Objekt der Klasse `raw_storage_iterator`\< **ForwardIterator**, **Type**> greift über ein Forward-Iteratorobjekt der Klasse `ForwardIterator`auf den Speicher zu, den Sie beim Erstellen des Objekts angeben. Beim ersten Objekt der Klasse `ForwardIterator`muss der Ausdruck **&\*zuerst** den nicht erstellten Speicher für das nächste Objekt (des Typs `Type`) in der generierten Sequenz festlegen.

Diese Adapterklasse wird verwendet, wenn es erforderlich ist, Speicherbelegung und Objekterstellung zu trennen. `raw_storage_iterator` kann verwendet werden, um Objekte in nicht initialisierten Speicher zu kopieren, beispielsweise Arbeitsspeicher, der über die `malloc`-Funktion zugeordnet wurde.

## <a name="members"></a>Members

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
|[operator*](#op_star)|Ein Dereferenzierungsoperator, der zum Implementieren des ausgabeiteratorausdrucks \* `ii` = `x`verwendet wird.|
|[operator=](#op_eq)|Ein Zuweisungs Operator, der verwendet wird, um den unformatierten speicheriteratorausdruck \* `i` = `x` zum Speichern im Speicher zu implementieren.|
|[operator++](#op_add_add)|Inkrementoperatoren in Präfix- und Postfix-Notation für unformatierte Speicheriteratoren.|

### <a name="element_type"></a><a name="element_type"></a>element_type

Stellt einen Typ bereit, der ein Element beschreibt, das in einem unformatierten Speicheriterator gespeichert werden soll.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Raw_storage_iterator Klassen Vorlagen Parameter `Type`.

### <a name="iter_type"></a><a name="iter_type"></a>iter_type

Stellt einen Typ bereit, der einen Iterator beschreibt, der einem unformatierten Speicheriterator zugrunde liegt.

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `ForwardIterator`dar.

### <a name="operator"></a><a name="op_star"></a>-Operator\*

Ein Dereferenzierungsoperator, der verwendet wird, um den unformatierten speicheriteratorausdruck \* *II* = *x*zu implementieren.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>Rückgabewert

Ein Verweis auf den unformatierten Speicheriterator.

#### <a name="remarks"></a>Bemerkungen

Die Anforderungen für eine `ForwardIterator` bestehen darin, dass der unformatierte speicheriterator nur den Ausdruck erfordert, dass der Ausdruck \* *II* ist = *t* gültig ist, und dass er nichts über den **Operator** oder das `operator=` selbst sagt. Die Member-Operatoren in dieser Implementierung geben **\*this**zurück, sodass [Operator =](#op_eq)(**consttype**&) den tatsächlichen Speicher in einem Ausdruck ausführen kann, z. b. \* *ptr* - = `val`.

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

Der Zuweisungs Operator, der verwendet wird, um den unformatierten speicheriteratorausdruck \* *i* = *x* zum Speichern im Speicher zu implementieren

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>Parameter

*Val* -\
Der Wert des-Objekts vom Typ `Type`, der in den Arbeitsspeicher eingefügt werden soll.

#### <a name="return-value"></a>Rückgabewert

Der Operator fügt `val` in den Speicher ein, und gibt dann einen Verweis auf den unformatierten Speicheriterator zurück.

#### <a name="remarks"></a>Bemerkungen

Die Anforderungen für einen `ForwardIterator` Status, den der unformatierte speicheriterator erfüllen muss, erfordern nur den Ausdruck \* *II* = *t* gültig ist, und dass er nichts über den **Operator** oder das `operator=` selbst sagt. Diese Memberoperatoren geben beide **\*this** zurück.

Der Zuweisungs Operator erstellt das nächste Objekt in der Ausgabe Sequenz unter Verwendung des gespeicherten iteratorwerts zuerst, indem der Platzierungs New Expression **New** ((`void` \*) &\* **First**)- **Typ**(`val`) ausgewertet wird.

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

Der erste Preincrement-Operator erhöht das gespeicherte Ausgabeiteratorobjekt schrittweise, und gibt anschließend **\*this** zurück.

Der zweite Postinkrement-Operator erstellt eine Kopie von **\*this**, erhöht das gespeicherte Ausgabeiteratorobjekt und gibt dann die Kopie zurück.

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

*erste*\
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
