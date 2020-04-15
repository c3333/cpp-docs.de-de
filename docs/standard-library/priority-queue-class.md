---
title: priority_queue-Klasse
ms.date: 11/04/2016
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
ms.openlocfilehash: cef85eafaa3aab1c448234399f146191de957b8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323014"
---
# <a name="priority_queue-class"></a>priority_queue-Klasse

Eine Vorlagencontainer-Adapterklasse, die die Funktionalität einschränkt, indem sie den Zugriff auf das oberste Element eines zugrunde liegenden Containertyps beschränkt, das immer das größte oder wichtigste Element ist. Der Warteschlange mit hoher Priorität können neue Elemente hinzugefügt werden, und das oberste Element der Warteschlange mit hoher Priorität kann überprüft oder entfernt werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parameter

*Typ*\
Der in der Warteschlange mit hoher Priorität zu speichernde Elementdatentyp.

*Container*\
Der Typ des zugrunde liegenden Containers, der verwendet wird, um die Warteschlange mit hoher Priorität zu implementieren.

*Vergleichen*\
Der Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Warteschlange mit hoher Priorität zu bestimmen. Dieses Argument ist optional, und das binäre Prädikat `less<typename Container::value_type>` ist der Standardwert.

## <a name="remarks"></a>Bemerkungen

Die Im `Type` ersten Vorlagenparameter eines Warteschlangenobjekts festgelegten Klassenelemente sind synonym [für value_type](#value_type) und müssen `Container` mit dem Elementtyp in der zugrunde liegenden Containerklasse übereinstimmen, die durch den zweiten Vorlagenparameter festgelegt wird. Der `Type` muss zuweisbar sein, damit Objekte dieses Typs kopiert und Variablen dieses Typs Werte zugewiesen werden können.

Der priority_queue ordnet die Sequenz an, die `Traits`er steuert, indem er ein gespeichertes Funktionsobjekt der Klasse aufruft. Im Allgemeinen müssen die Elemente der Vorwärtsiteratoren etwas weniger als vergleichbar sein, um diese Sortierung zu erstellen, sodass beliebige zwei Elemente möglicherweise als gleichwertig bestimmt werden (in dem Sinne, dass keins geringer als das Andere ist), oder dass eins geringer als das Andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Etwas technischer betrachtet ist die Vergleichsfunktion ein binäres Prädikat, das eine strenge schwache Sortierung im mathematischen Sinn verursacht.

Geeignete zugrunde liegende Containerklassen für die Warteschlangenklasse mit hoher Priorität sind [deque-Klasse](../standard-library/deque-class.md) und die Standard-[vector-Klasse](../standard-library/vector-class.md) oder ein beliebiger Sequenzcontainer, der die Vorgänge von `front`, `push_back` und `pop_back` und einen Random-Access-Iterator unterstützt. Die zugrunde liegende Containerklasse wird im Containeradapter gekapselt, der nur den begrenzten Satz der Memberfunktionen des Sequenzcontainers als öffentliche Schnittstelle verfügbar macht.

Hinzufügen und Entfernen von Elementen aus einem `priority_queue`; beide haben logarithmische Komplexität. Zugreifen auf Elemente in einem `priority_queue` mit konstanter Komplexität.

Es gibt drei Arten von Containeradaptern, die von der C++-Standardbibliothek definiert werden: Stapel, Warteschlangen und Warteschlangen mit hoher Priorität. Jede schränkt die Funktionalität von einigen zugrunde liegenden Containerklassen ein, um eine präzise gesteuerte Oberfläche für eine Standarddatenstruktur anzubieten.

- Die [Stack-Klasse](../standard-library/stack-class.md) unterstützt eine LIFO-Datenstruktur (Last-In, First-Out). Eine gute Analogie, um sich dies zu merken, ist ein Stapel von Tellern. Elemente (Teller) können eingefügt, überprüft oder nur vom Anfang des Stapels entnommen werden, was dem letzten Element am Ende des Basiscontainers entspricht. Die Beschränkung, nur auf das oberste Element zuzugreifen, ist der Grund für die Verwendung der stack-Klasse.

- Die [Warteschlangenklasse](../standard-library/queue-class.md) unterstützt eine FIFO-Datenstruktur (First-In, First-Out). Eine gute Analogie, um sich dies zu merken, sind Personen, die an einem Bankschalter anstehen. Elemente (Personen) können am Ende der Schlange hinzugefügt werden und vom Anfang der Schlange entfernt werden. Sowohl der Anfang als auch das Ende einer Schlange können überprüft werden. Die in dieser Weise umgesetzte Beschränkung, nur auf das vorderste und das hinterste Element zugreifen zu können, ist der Grund für das Verwenden der Warteschlangenklasse.

- In der Warteschlangenklasse mit hoher Priorität sortiert ihre Elemente so, dass sich das größte Element immer an der obersten Position befindet. Die Klasse unterstützt Einfügen eines Elements sowie die Prüfung und Entfernung des obersten Elements. Eine gute Analogie, um sich dies zu merken, sind Personen, die in einer Schlange stehen, in der sie nach Alter, Größe oder einem anderen Kriterium angeordnet sind.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[priority_queue](#priority_queue)|Erstellt ein `priority_queue`-Objekt, das leer oder eine Kopie eines Basiscontainerobjekts oder eines anderen `priority_queue` ist.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[container_type](#container_type)|Ein Typ, der den Basiscontainer bereitstellt, der durch ein `priority_queue`-Objekt übernommen werden soll.|
|[Size_type](#size_type)|Eine Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in `priority_queue` darstellen kann.|
|[Value_type](#value_type)|Ein Typ, der den Typ des Objekts angibt, das in einem `priority_queue`-Objekt als Element gespeichert wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[empty](#empty)|Testet, ob das `priority_queue`-Objekt ist leer.|
|[Pop](#pop)|Entfernt das größte Element der `priority_queue` von der obersten Position.|
|[push](#push)|Fügt ein Element zur Warteschlange mit hoher Priorität anhand der Priorität des Elements des operator< hinzu.|
|[Größe](#size)|Gibt die Anzahl von Elementen in der `priority_queue` zurück.|
|[top](#top)|Gibt einen konstanten Verweis auf das größte Element am oberen Rand von `priority_queue` zurück.|

## <a name="requirements"></a>Anforderungen

**Header:** \<queue>

**Namespace:** std

## <a name="priority_queuecontainer_type"></a><a name="container_type"></a>priority_queue::container_type

Ein Typ, der den anzupassenden Basiscontainer bereitstellt.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Container` dar. Die Sequenzcontainerklassen der C++-Standardbibliothek `deque` und die Standardklasse `vector` erfüllen die Anforderungen, um als Basiscontainer für ein priority_queue-Objekt verwendet zu werden. Benutzerdefinierte Typen, die diese Anforderung erfüllen, können auch verwendet werden.

Weitere Informationen zu `Container` finden Sie im Abschnitt „Hinweise“ des Themas [priority_queue-Klasse](../standard-library/priority-queue-class.md).

### <a name="example"></a>Beispiel

Im Beispiel für [priority_queue](#priority_queue) wird verdeutlicht, wie `container_type` deklariert und verwendet wird.

## <a name="priority_queueempty"></a><a name="empty"></a>priority_queue::leer

Testet, ob eine priority_queue leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die priority_queue leer ist. **FALSE**, wenn die Priority_queue nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// pqueue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue <int> q1, s2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The priority_queue q1 is empty." << endl;
   else
      cout << "The priority_queue q1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The priority_queue s2 is empty." << endl;
   else
      cout << "The priority_queue s2 is not empty." << endl;
}
```

```Output
The priority_queue q1 is not empty.
The priority_queue s2 is empty.
```

## <a name="priority_queuepop"></a><a name="pop"></a>priority_queue::pop

Entfernt das größte Element der priority_queue von der obersten Position.

```cpp
void pop();
```

### <a name="remarks"></a>Bemerkungen

Priority_queue darf nicht leer sein, damit die Memberfunktion angewendet wird. Der Anfang der Warteschlange mit hoher Priorität wird immer von dem größten Element im Container belegt.

### <a name="example"></a>Beispiel

```cpp
// pqueue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   priority_queue <int>::size_type i, iii;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;

   q1.pop( );

   iii = q1.size( );
   cout << "After a pop, the priority_queue length is "
        << iii << "." << endl;

   const int& iv = q1.top( );
   cout << "After a pop, the element at the top of the "
        << "priority_queue is " << iv << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
After a pop, the priority_queue length is 2.
After a pop, the element at the top of the priority_queue is 20.
```

## <a name="priority_queuepriority_queue"></a><a name="priority_queue"></a>priority_queue::priority_queue

Erstellt eine Warteschlange mit hoher Priorität, die leer ist oder eine Kopie eines Bereichs eines Basiscontainerobjekt oder einer anderen Warteschlange mit hoher Priorität ist.

```cpp
priority_queue();

explicit priority_queue(const Traits& _comp);

priority_queue(const Traits& _comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp, const container_type& _Cont);
```

### <a name="parameters"></a>Parameter

*_comp*\
Die Vergleichsfunktion des Typs **constTraits** wird verwendet, um Elemente in der priority_queue zu sortieren, deren Standard die Vergleichsfunktion des Basiscontainer ist.

*_Cont*\
Der Basiscontainer, dessen Kopie die Warteschlange mit hoher Priorität sein soll.

*Richting*\
Die Warteschlange mit hoher Priorität, deren Kopie der erstellte Satz sein soll.

*Ersten*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*letzte*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

### <a name="remarks"></a>Bemerkungen

Jeder der ersten drei Konstruktoren gibt einen leeren anfangs priority_queue an, der`comp`zweite gibt auch den Typ der Vergleichsfunktion ( `container_type` `_Cont`) an, die zum Festlegen der Reihenfolge der Elemente verwendet werden soll, und der dritte gibt explizit die zu verwendende ( ) an. Mit dem Schlüsselwort **explicit** werden bestimmte Arten automatischer Typumwandlung unterdrückt.

Der vierte Konstruktor gibt eine Kopie des priority_queue *rechts*an.

Die letzten drei Konstruktoren \[kopieren den Bereich *zuerst*, *zuletzt*) eines Containers und verwenden die Werte, um `Traits` eine `container_type`priority_queue mit zunehmender Explizitheit bei der Angabe des Typs der Vergleichsfunktion von Class und zu initialisieren.

### <a name="example"></a>Beispiel

```cpp
// pqueue_ctor.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <deque>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function declares priority_queue
   // with a default vector base container
   priority_queue <int> q1;
   cout << "q1 = ( ";
   while ( !q1.empty( ) )
   {
      cout << q1.top( ) << " ";
      q1.pop( );
   }
   cout << ")" << endl;

   // Explicitly declares a priority_queue with nondefault
   // deque base container
   priority_queue <int, deque <int> > q2;
   q2.push( 5 );
   q2.push( 15 );
   q2.push( 10 );
   cout << "q2 = ( ";
   while ( !q2.empty( ) )
   {
      cout << q2.top( ) << " ";
      q2.pop( );
   }
   cout << ")" << endl;

   // This method of printing out the elements of a priority_queue
   // removes the elements from the priority queue, leaving it empty
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;

   // The third member function declares a priority_queue
   // with a vector base container and specifies that the comparison
   // function greater is to be used for ordering elements
   priority_queue <int, vector<int>, greater<int> > q3;
   q3.push( 2 );
   q3.push( 1 );
   q3.push( 3 );
   cout << "q3 = ( ";
   while ( !q3.empty( ) )
   {
      cout << q3.top( ) << " ";
      q3.pop( );
   }
   cout << ")" << endl;

   // The fourth member function declares a priority_queue and
   // initializes it with elements copied from another container:
   // first, inserting elements into q1, then copying q1 elements into q4
   q1.push( 100 );
   q1.push( 200 );
   priority_queue <int> q4( q1 );
   cout << "q4 = ( ";
   while ( !q4.empty( ) )
   {
      cout << q4.top( ) << " ";
      q4.pop( );
   }
   cout << ")" << endl;

   // Creates an auxiliary vector object v5 to be used to initialize q5
   vector <int> v5;
   vector <int>::iterator v5_Iter;
   v5.push_back( 10 );
   v5.push_back( 30 );
   v5.push_back( 20 );
   cout << "v5 = ( " ;
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )
      cout << *v5_Iter << " ";
   cout << ")" << endl;

   // The fifth member function declares and
   // initializes a priority_queue q5 by copying the
   // range v5[ first,  last) from vector v5
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );
   cout << "q5 = ( ";
   while ( !q5.empty( ) )
   {
      cout << q5.top( ) << " ";
      q5.pop( );
   }
   cout << ")" << endl;

   // The sixth member function declares a priority_queue q6
   // with a comparison function greater and initializes q6
   // by copying the range v5[ first,  last) from vector v5
   priority_queue <int, vector<int>, greater<int> >
      q6( v5.begin( ), v5.begin( ) + 2 );
   cout << "q6 = ( ";
   while ( !q6.empty( ) )
   {
      cout << q6.top( ) << " ";
      q6.pop( );
   }
   cout << ")" << endl;
}
```

## <a name="priority_queuepush"></a><a name="push"></a>priority_queue::push

Fügt ein Element zur Warteschlange mit hoher Priorität anhand der Priorität des Elements des operator< hinzu.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parameter

*Val*\
Das am Anfang zur Warteschlange mit hoher Priorität hinzugefügte Element.

### <a name="remarks"></a>Bemerkungen

Am Anfang der Warteschlange mit hoher Priorität befindet sich das größte Element im Container.

### <a name="example"></a>Beispiel

```cpp
// pqueue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="priority_queuesize"></a><a name="size"></a>priority_queue::größe

Gibt die Anzahl der Elemente in der Warteschlange mit hoher Priorität zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge der Warteschlange mit hoher Priorität.

### <a name="example"></a>Beispiel

```cpp
// pqueue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, q2;
   priority_queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The priority_queue length is now " << i << "." << endl;
}
```

```Output
The priority_queue length is 1.
The priority_queue length is now 2.
```

## <a name="priority_queuesize_type"></a><a name="size_type"></a>priority_queue::size_type

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einer Warteschlange mit hoher Priorität darstellen kann.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für das `size_type` des Basiscontainers, der von der Warteschlange mit hoher Priorität angepasst wurde.

### <a name="example"></a>Beispiel

Im Beispiel für [size](#size) wird verdeutlicht, wie ein `size_type` deklariert und verwendet wird.

## <a name="priority_queuetop"></a><a name="top"></a>priority_queue::top

Gibt einen konstanten Verweis auf das größte Element am oberen Rand von priority_queue.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das größte Element, wie durch die `Traits` Funktion, das Objekt des priority_queue bestimmt.

### <a name="remarks"></a>Bemerkungen

Priority_queue darf nicht leer sein, damit die Memberfunktion angewendet wird.

### <a name="example"></a>Beispiel

```cpp
// pqueue_top.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="priority_queuevalue_type"></a><a name="value_type"></a>priority_queue::value_type

Ein Typ, der den Typ des Objekts angibt, das als Element in einer Warteschlange mit hoher Priorität gespeichert wird.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für das `value_type` des Basiscontainers, der von der Warteschlange mit hoher Priorität angepasst wurde.

### <a name="example"></a>Beispiel

```cpp
// pqueue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   priority_queue<int> q1;
   q1.push( AnInt );
   cout << "The element at the top of the priority_queue is "
        << q1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the priority_queue is 69.
```

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)
