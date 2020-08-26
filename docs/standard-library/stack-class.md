---
title: stack-Klasse
ms.date: 11/04/2016
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
helpviewer_keywords:
- std::stack [C++], container_type
- std::stack [C++], size_type
- std::stack [C++], value_type
- std::stack [C++], empty
- std::stack [C++], pop
- std::stack [C++], push
- std::stack [C++], size
- std::stack [C++], top
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
ms.openlocfilehash: f1d44a4242542ac6856fd7208fe423c43ae79997
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844300"
---
# <a name="stack-class"></a>stack-Klasse

Eine Vorlagencontainer-Adapterklasse, die die Funktionalität einschränkt, indem sie den Zugriff auf das Element beschränkt, das zuletzt zu einem zugrunde liegenden Containertyp hinzugefügt wurde. Die stack-Klasse wird verwendet, wenn es unverzichtbar ist, dass Stapelvorgänge nur für den Container ausgeführt werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der Datentyp der Elemente, die im Stapel gespeichert werden sollen.

*Kum*\
Der Typ des zugrunde liegenden Containers, der verwendet wird, um den Stapel zu implementieren. Der Standardwert ist die-Klasse `deque` *\<Type>* .

## <a name="remarks"></a>Bemerkungen

Die Elemente der-Klasse, die `Type` im ersten Vorlagen Parameter eines Stack-Objekts festgelegt sind, entsprechen [value_type](#value_type) und müssen mit dem Typ des Elements in der zugrunde liegenden Container Klasse, `Container` die durch den zweiten Vorlagen Parameter festgelegt ist, identisch sein. `Type`Muss zugewiesen werden können, sodass es möglich ist, Objekte dieses Typs zu kopieren und Variablen dieses Typs Werte zuzuweisen.

Geeignete zugrunde liegende Containerklassen für Stack sind [Deque](../standard-library/deque-class.md), [List Class](../standard-library/list-class.md)und [Vector Class](../standard-library/vector-class.md), oder ein beliebiger anderer Sequenz Container, der die Vorgänge von `back` , und unterstützt `push_back` `pop_back` . Die zugrunde liegende Containerklasse wird im Containeradapter gekapselt, der nur den begrenzten Satz der Memberfunktionen des Sequenzcontainers als öffentliche Schnittstelle verfügbar macht.

Die Stapel Objekte sind auf Gleichheit vergleichbar, wenn die Elemente der Klasse `Type` gleich sind und nur dann kleiner als vergleichbar sind, wenn die Elemente der Klasse `Type` kleiner als vergleichbar sind.

- Die stack-Klasse unterstützt eine LIFO-Datenstruktur (Last In – First Out). Eine gute Analogie, um sich dies zu merken, ist ein Stapel von Tellern. Elemente (Teller) können eingefügt, überprüft oder nur vom Anfang des Stapels entnommen werden, was dem letzten Element am Ende des Basiscontainers entspricht. Die Beschränkung, nur auf das oberste Element zuzugreifen, ist der Grund für die Verwendung der stack-Klasse.

- Die [queue-Klasse](../standard-library/queue-class.md) unterstützt eine FIFO-Daten(First In – First Out). Eine gute Analogie, um sich dies zu merken, sind Personen, die an einem Bankschalter anstehen. Elemente (Personen) können am Ende der Schlange hinzugefügt werden und vom Anfang der Schlange entfernt werden. Sowohl der Anfang als auch das Ende einer Schlange können überprüft werden. Die in dieser Weise umgesetzte Beschränkung, nur auf das vorderste und das hinterste Element zugreifen zu können, ist der Grund für das Verwenden der queue-Klasse.

- In der [priority_queue-Klasse](../standard-library/priority-queue-class.md) sind deren Elemente so sortiert, dass sich das größte Element immer an der obersten Position befindet. Die Klasse unterstützt Einfügen eines Elements sowie die Prüfung und Entfernung des obersten Elements. Eine gute Analogie, um sich dies zu merken, sind Personen, die in einer Schlange stehen, in der sie nach Alter, Größe oder einem anderen Kriterium angeordnet sind.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[stack](#stack)|Erstellt ein `stack`-Objekt, das leer oder eine Kopie eines Basiscontainerobjekts ist.|

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[container_type](#container_type)|Ein Typ, der den Basiscontainer bereitstellt, der durch ein `stack`-Objekt übernommen werden soll.|
|[size_type](#size_type)|Eine Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in `stack` darstellen kann.|
|[value_type](#value_type)|Ein Typ, der den Typ des Objekts angibt, das in einem `stack`-Objekt als Element gespeichert wird.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[empty](#empty)|Testet, ob das `stack`-Objekt ist leer.|
|[Chor](#pop)|Entfernt das Element aus der obersten Position des `stack`-Objekts.|
|[push](#push)|Fügt ein Element an der obersten Position des `stack`-Objekts hinzu.|
|[size](#size)|Gibt die Anzahl von Elementen in der `stack` zurück.|
|[top](#top)|Gibt einen Verweis auf das Element in der obersten Position des `stack`-Objekts zurück.|

## <a name="container_type"></a><a name="container_type"></a> container_type

Ein Typ, der den anzupassenden Basiscontainer bereitstellt.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Container` dar. Die drei Sequenzcontainerklassen der C++-Standardbibliothek, d.h. die Vektorklasse, die list-Klasse und die Standardklasse Deque, erfüllen die Anforderungen, um als Basiscontainer für ein stack-Objekt verwendet zu werden. Benutzerdefinierte Typen, die diese Anforderung erfüllen, können auch verwendet werden.

Weitere Informationen zu `Container` finden Sie im Abschnitt „Hinweise“ des Themas [stack-Klasse](../standard-library/stack-class.md).

### <a name="example"></a>Beispiel

Im Beispiel für [stack::stack](#stack) wird verdeutlicht, wie ein `container_type` deklariert und verwendet wird.

## <a name="empty"></a><a name="empty"></a> leer

Testet, ob ein Stack leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn der Stapel leer ist. , **`false`** Wenn der Stapel nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// stack_empty.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack <int> s1, s2;

   s1.push( 1 );

   if ( s1.empty( ) )
      cout << "The stack s1 is empty." << endl;
   else
      cout << "The stack s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The stack s2 is empty." << endl;
   else
      cout << "The stack s2 is not empty." << endl;
}
```

```Output
The stack s1 is not empty.
The stack s2 is empty.
```

## <a name="pop"></a><a name="pop"></a> Chor

Entfernt das Element aus der obersten Position des Stacks.

```cpp
void pop();
```

### <a name="remarks"></a>Bemerkungen

Der Stack darf nicht leer sein, damit die Memberfunktion angewendet wird. Der Anfang des Stacks ist die Position des zuletzt hinzugefügten Elements und ist das letzte Element am Ende des Containers.

### <a name="example"></a>Beispiel

```cpp
// stack_pop.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;

   s1.pop( );

   i = s1.size( );
   cout << "After a pop, the stack length is "
        << i << "." << endl;

   i = s1.top( );
   cout << "After a pop, the element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
After a pop, the stack length is 2.
After a pop, the element at the top of the stack is 20.
```

## <a name="push"></a><a name="push"></a> Push

Fügt ein Element am Anfang des Stapels hinzu.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Das am Anfang des Stacks hinzugefügte Element.

### <a name="remarks"></a>Bemerkungen

Der Anfang des Stacks ist die Position des zuletzt hinzugefügten Elements und ist das letzte Element am Ende des Containers.

### <a name="example"></a>Beispiel

```cpp
// stack_push.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
```

## <a name="size"></a><a name="size"></a> Größe

Gibt die Anzahl der Elemente im Stack zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge des Stacks.

### <a name="example"></a>Beispiel

```cpp
// stack_size.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;
   stack <int>::size_type i;

   s1.push( 1 );
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   s1.push( 2 );
   i = s1.size( );
   cout << "The stack length is now " << i << "." << endl;
}
```

```Output
The stack length is 1.
The stack length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einem Stack darstellen kann.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `size_type` des Basiscontainers und vom Stack angepasst.

### <a name="example"></a>Beispiel

Im Beispiel für [size](#size) wird verdeutlicht, wie ein `size_type` deklariert und verwendet wird.

## <a name="stack"></a><a name="stack"></a> Heu

Erstellt ein einen Stack, der leer oder eine Kopie eines Basiscontainerobjekts ist.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Container, dessen Kopie der erstellte Stack sein soll.

### <a name="example"></a>Beispiel

```cpp
// stack_stack.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stack with default deque base container
   stack <char> dsc1;

   //Explicitly declares a stack with deque base container
   stack <char, deque<char> > dsc2;

   // Declares a stack with vector base containers
   stack <int, vector<int> > vsi1;

   // Declares a stack with list base container
   stack <int, list<int> > lsi;

   // The second member function copies elements from a container
   vector<int> v1;
   v1.push_back( 1 );
   stack <int, vector<int> > vsi2( v1 );
   cout << "The element at the top of stack vsi2 is "
        << vsi2.top( ) << "." << endl;
}
```

```Output
The element at the top of stack vsi2 is 1.
```

## <a name="top"></a><a name="top"></a> Nach oben

Gibt einen Verweis auf ein Element am Anfang des Stacks zurück.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das letzte Element im Container am Anfang des Stacks.

### <a name="remarks"></a>Bemerkungen

Der Stack darf nicht leer sein, damit die Memberfunktion angewendet wird. Der Anfang des Stacks ist die Position des zuletzt hinzugefügten Elements und ist das letzte Element am Ende des Containers.

Wenn der Rückgabewert von `top` einem zugewiesen wird `const_reference` , kann das Stapel Objekt nicht geändert werden. Wenn der Rückgabewert von `top` einem zugewiesen wird `reference` , kann das Stapel Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// stack_top.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 1 );
   s1.push( 2 );

   int& i = s1.top( );
   const int& ii = s1.top( );

   cout << "The top integer of the stack s1 is "
        << i << "." << endl;
   i--;
   cout << "The next integer down is "<< ii << "." << endl;
}
```

```Output
The top integer of the stack s1 is 2.
The next integer down is 1.
```

## <a name="value_type"></a><a name="value_type"></a> value_type

Ein Typ, der den Typ des Objekts angibt, das in einem Stack als Element gespeichert wird.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `value_type` des Basiscontainers und vom Stack angepasst.

### <a name="example"></a>Beispiel

```cpp
// stack_value_type.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   stack<int> s1;
   s1.push( AnInt );
   cout << "The element at the top of the stack is "
        << s1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the stack is 69.
```

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
