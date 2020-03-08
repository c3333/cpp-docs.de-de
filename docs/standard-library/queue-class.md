---
title: queue-Klasse
ms.date: 11/04/2016
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
ms.openlocfilehash: 512b9499e63933a71a27a87f91a3bef8a65339e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890857"
---
# <a name="queue-class"></a>queue-Klasse

Eine Vorlagencontainer-Adapterklasse, die die Funktionalität für einige zugrunde liegende Containertypen einschränkt, indem sie den Zugriff auf die vorderen und hinteren Elemente beschränkt. Elemente können an der Rückseite hinzugefügt oder an der Vorderseite entfernt und an beiden Enden der Warteschlange überprüft werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Parameter

*Typ*\
Der in der Warteschlange zu speichernde Elementdatentyp.

*Container*\
Der Typ des zugrunde liegenden Containers, der verwendet wird, um die Warteschlange zu implementieren.

## <a name="remarks"></a>Bemerkungen

Die Elemente der-`Type` Klasse, die im ersten Vorlagen Parameter eines Queue-Objekts festgelegt wurden, sind mit [value_type](#value_type) Synonym und müssen mit dem Typ des Elements in der zugrunde liegenden Container Klasse `Container`, das durch den zweiten Vorlagen Parameter festgelegt ist, identisch sein. Der `Type` muss zugewiesen werden können, sodass es möglich ist, Objekte dieses Typs zu kopieren und Variablen dieses Typs Werte zuzuweisen.

Geeignete zugrunde liegende Containerklassen für die Warteschlange sind [Deque](../standard-library/deque-class.md) und [List](../standard-library/list-class.md)oder ein beliebiger anderer Sequenz Container, der die Vorgänge von `front`, `back`, `push_back`und `pop_front`unterstützt. Die zugrunde liegende Containerklasse wird im Containeradapter gekapselt, der nur den begrenzten Satz der Memberfunktionen des Sequenzcontainers als öffentliche Schnittstelle verfügbar macht.

Die Warteschlangen Objekte sind bei und nur dann vergleichbar, wenn die Elemente der Klasse `Type` auf Gleichheit vergleichbar sind und kleiner als vergleichbar sind, wenn die Elemente der Klasse `Type` kleiner als vergleichbar sind.

Es gibt drei Arten von Containeradaptern, die von der C++-Standardbibliothek definiert werden: Stapel, Warteschlangen und Warteschlangen mit hoher Priorität. Jede schränkt die Funktionalität von einigen zugrunde liegenden Containerklassen ein, um eine präzise gesteuerte Oberfläche für eine Standarddatenstruktur anzubieten.

- Die [Stapelklasse](../standard-library/stack-class.md) unterstützt eine LIFO-Datenstruktur (Last In – First Out). Eine gute Analogie, um sich dies zu merken, ist ein Stapel von Tellern. Elemente (Teller) können eingefügt, überprüft oder nur vom Anfang des Stapels entnommen werden, was dem letzten Element am Ende des Basiscontainers entspricht. Die Beschränkung, nur auf das oberste Element zuzugreifen, ist der Grund für die Verwendung der stack-Klasse.

- Die queue-Klasse unterstützt eine FIFO-Datenstruktur (First In – First Out). Eine gute Analogie, um sich dies zu merken, sind Personen, die an einem Bankschalter anstehen. Elemente (Personen) können am Ende der Schlange hinzugefügt werden und vom Anfang der Schlange entfernt werden. Sowohl der Anfang als auch das Ende einer Schlange können überprüft werden. Die in dieser Weise umgesetzte Beschränkung, nur auf das vorderste und das hinterste Element zugreifen zu können, ist der Grund für das Verwenden der Warteschlangenklasse.

- In der [Warteschlangenklasse mit hoher Priorität](../standard-library/priority-queue-class.md) sind deren Elemente so sortiert, dass sich das größte Element immer an der obersten Position befindet. Die Klasse unterstützt Einfügen eines Elements sowie die Prüfung und Entfernung des obersten Elements. Eine gute Analogie, um sich dies zu merken, sind Personen, die in einer Schlange stehen, in der sie nach Alter, Größe oder einem anderen Kriterium angeordnet sind.

## <a name="members"></a>Members

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[queue](#queue)|Erstellt ein `queue`-Objekt, das leer oder eine Kopie eines Basiscontainerobjekts ist.|

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[container_type](#container_type)|Ein Typ, der den Basiscontainer bereitstellt, der durch `queue` angepasst werden soll.|
|[size_type](#size_type)|Eine Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in `queue` darstellen kann.|
|[value_type](#value_type)|Ein Typ, der den Typ des Objekts angibt, das in einem `queue`-Objekt als Element gespeichert wird.|

### <a name="functions"></a>Functions

|||
|-|-|
|[Rückseite](#back)|Gibt ein Verweis auf das letzte und das zuletzt hinzugefügte Element auf der Rückseite des `queue` zurück.|
|[empty](#empty)|Testet, ob das `queue`-Objekt ist leer.|
|[Vorderseite](#front)|Gibt einen Verweis auf das erste Element auf der Vorderseite von `queue` zurück.|
|[pop](#pop)|Entfernt ein Element vom Anfang der `queue`.|
|[push](#push)|Fügt am Ende der `queue` ein Element hinzu.|
|[size](#size)|Gibt die Anzahl von Elementen in der `queue` zurück.|

## <a name="back"></a>Zurück

Gibt einen Verweis auf das letzte und das zuletzt hinzugefügte Element auf der Rückseite der Warteschlange zurück.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Rückgabewert

Das letzte Element der Warteschlange. Wenn die Warteschlange leer ist, ist der Rückgabewert nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `back` einem `const_reference` zugewiesen wird, kann das Warteschlangenobjekt nicht geändert werden. Wenn der Rückgabewert von `back` einem `reference`zugewiesen wird, kann das Warteschlangen Objekt geändert werden.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element in einer leeren Warteschlange ein Laufzeitfehler auf.  Weitere Informationen finden Sie unter [Checked Iterators](../standard-library/checked-iterators.md) .

### <a name="example"></a>Beispiel

```cpp
// queue_back.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 11 );

   int& i = q1.back( );
   const int& ii = q1.front( );

   cout << "The integer at the back of queue q1 is " << i
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << ii
        << "." << endl;
}
```

## <a name="container_type"></a>container_type

Ein Typ, der den anzupassenden Basiscontainer bereitstellt.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Container`dar. Zwei Sequenzcontainerklassen der C++-Standardbibliothek — die Listklasse und die Standarddoppelschlangenklasse — erfüllen die Anforderungen, um als Basiscontainer für ein Warteschlangenobjekt verwendet zu werden. Benutzerdefinierte Typen, die diese Anforderung erfüllen, können auch verwendet werden.

Weitere Informationen zu `Container` finden Sie im Abschnitt „Hinweise“ des Themas [Warteschlangenklasse](../standard-library/queue-class.md).

### <a name="example"></a>Beispiel

Im Beispiel für [Warteschlange](#queue) wird verdeutlicht, wie ein `container_type` deklariert und verwendet wird.

## <a name="empty"></a>leer

Testet, ob eine Warteschlange leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Warteschlange leer ist; **FALSE**, wenn die Warteschlange nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// queue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The queue q1 is empty." << endl;
   else
      cout << "The queue q1 is not empty." << endl;

   if ( q2.empty( ) )
      cout << "The queue q2 is empty." << endl;
   else
      cout << "The queue q2 is not empty." << endl;
}
```

```Output
The queue q1 is not empty.
The queue q2 is empty.
```

## <a name="front"></a>Beifahrer

Gibt einen Verweis auf das erste Element auf der Vorderseite einer Warteschlange zurück.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Rückgabewert

Das erste Element der Warteschlange. Wenn die Warteschlange leer ist, ist der Rückgabewert nicht definiert.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `front` einem `const_reference` zugewiesen wird, kann das Warteschlangenobjekt nicht geändert werden. Wenn der Rückgabewert von `front` einem `reference`zugewiesen wird, kann das Warteschlangen Objekt geändert werden.

Die Member-Funktion gibt eine `reference` an das erste Element der kontrollierten Sequenz zurück, die nicht leer sein darf.

Wenn [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) beim Kompilieren als 1 oder 2 definiert ist, tritt beim Zugriff auf ein Element in einer leeren Warteschlange ein Laufzeitfehler auf.  Weitere Informationen finden Sie unter [Checked Iterators](../standard-library/checked-iterators.md) .

### <a name="example"></a>Beispiel

```cpp
// queue_front.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main() {
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   int& ii = q1.back( );
   int& iii = q1.front( );

   cout << "The integer at the back of queue q1 is " << ii
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << iii
        << "." << endl;
}
```

## <a name="pop"></a>Chor

Entfernt ein Element von der Vorderseite der Warteschlange.

```cpp
void pop();
```

### <a name="remarks"></a>Bemerkungen

Die Warteschlange darf nicht leer sein, damit die Memberfunktion angewendet wird. Am Anfang der Warteschlange befindet sich das zuletzt hinzugefügte Element und es ist das letzte Element am Ende des Containers.

### <a name="example"></a>Beispiel

```cpp
// queue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;

   q1.pop( );

   i = q1.size( );
   cout << "After a pop the queue length is "
        << i << "." << endl;

   i = q1. front ( );
   cout << "After a pop, the element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
After a pop the queue length is 2.
After a pop, the element at the front of the queue is 20.
```

## <a name="push"></a>Push

Fügt am Ende der Warteschlange ein Element hinzu.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parameter

*Val* -\
Das Element, das am Ende der Warteschlange hinzugefügt wird.

### <a name="remarks"></a>Bemerkungen

An der Rückseite der Warteschlange befinden sich die zuletzt hinzugefügten Elemente und das letzte Element am Ende des Containers.

### <a name="example"></a>Beispiel

```cpp
// queue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
```

## <a name="queue"></a>Ei

Erstellt eine Warteschlange, die leer oder eine Kopie eines Basiscontainerobjekts ist.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Der **const**-Container, dessen Kopie die erstellte Warteschlange sein soll.

### <a name="remarks"></a>Bemerkungen

Die Basisstandardcontainer für die Warteschlange ist die Doppelschlange. Sie können auch die Liste als Basiscontainer angeben, Sie können jedoch keinen Vektor angeben, da die erforderliche `pop_front`-Memberfunktion fehlt.

### <a name="example"></a>Beispiel

```cpp
// queue_queue.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queue with default deque base container
   queue <char> q1;

   // Explicitly declares a queue with deque base container
   queue <char, deque<char> > q2;

   // These lines don't cause an error, even though they
   // declares a queue with a vector base container
   queue <int, vector<int> > q3;
   q3.push( 10 );
   // but the following would cause an error because vector has
   // no pop_front member function
   // q3.pop( );

   // Declares a queue with list base container
   queue <int, list<int> > q4;

   // The second member function copies elements from a container
   list<int> li1;
   li1.push_back( 1 );
   li1.push_back( 2 );
   queue <int, list<int> > q5( li1 );
   cout << "The element at the front of queue q5 is "
        << q5.front( ) << "." << endl;
   cout << "The element at the back of queue q5 is "
        << q5.back( ) << "." << endl;
}
```

```Output
The element at the front of queue q5 is 1.
The element at the back of queue q5 is 2.
```

## <a name="size"></a>Größe

Gibt die Anzahl der Elemente in der Warteschlange zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge der Warteschlange.

### <a name="example"></a>Beispiel

```cpp
// queue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2;
   queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The queue length is now " << i << "." << endl;
}
```

```Output
The queue length is 1.
The queue length is now 2.
```

## <a name="size_type"></a>size_type

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einer Warteschlange darstellen kann.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für das `size_type` des Basiscontainers, der von der Warteschlange angepasst wurde.

### <a name="example"></a>Beispiel

Im Beispiel für [queue::front](#front) wird verdeutlicht, wie ein `size_type` deklariert und verwendet wird.

## <a name="value_type"></a>value_type

Ein Typ, der den Objekttyp angibt, der als Element in einer Warteschlange gespeichert wird.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für das `value_type` des Basiscontainers, der von der Warteschlange angepasst wurde.

### <a name="example"></a>Beispiel

```cpp
// queue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   queue<int> q1;
   q1.push(AnInt);
   cout << "The element at the front of the queue is "
        << q1.front( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the front of the queue is 69.
```

## <a name="see-also"></a>Weitere Informationen

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
