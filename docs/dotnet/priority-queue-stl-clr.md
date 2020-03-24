---
title: priority_queue (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
ms.openlocfilehash: e21e7ba4dc3a4ed270548506ac1a9e37a2c1a23a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208467"
---
# <a name="priority_queue-stlclr"></a>priority_queue (STL/CLR)

Die Vorlagen Klasse beschreibt ein Objekt, das eine geordnete Sequenz von Elementen variabler Länge steuert, die nur begrenzten Zugriff hat. Sie verwenden den Container Adapter `priority_queue`, um einen zugrunde liegenden Container als Prioritäts Warteschlange zu verwalten.

In der folgenden Beschreibung ist `GValue` identisch mit dem *Wert* , es sei denn, der letztere ist ein Ref-Typ. in diesem Fall ist es `Value^`. Ebenso ist `GContainer` identisch mit dem *Container* , es sei denn, es handelt sich um einen Verweistyp. in diesem Fall ist es `Container^`.

## <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    ref class priority_queue
        System::ICloneable,
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Der Typ eines Elements in der kontrollierten Sequenz.

*Container*<br/>
Der Typ des zugrunde liegenden Containers.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<cliext/Queue >

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[priority_queue::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[priority_queue::container_type (STL/CLR)](#container_type)|Der Typ des zugrunde liegenden Containers.|
|[priority_queue::difference_type (STL/CLR)](#difference_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[priority_queue::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container Adapter.|
|[priority_queue::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container Adapter.|
|[priority_queue::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[priority_queue::size_type (STL/CLR)](#size_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[priority_queue::value_compare (STL/CLR)](#value_compare)|Der Bestell Delegat für zwei-Elemente.|
|[priority_queue::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[priority_queue::assign (STL/CLR)](#assign)|Ersetzt alle Elemente.|
|[priority_queue::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[priority_queue::get_container (STL/CLR)](#get_container)|Greift auf den zugrunde liegenden Container zu.|
|[priority_queue::pop (STL/CLR)](#pop)|Entfernt das hghest-Priority-Element.|
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|Erstellt ein container-Objekt.|
|[priority_queue::push (STL/CLR)](#push)|Fügt ein neues Element hinzu.|
|[priority_queue::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[priority_queue::top (STL/CLR)](#top)|Greift auf das Element mit der höchsten Priorität zu.|
|[priority_queue::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|
|[priority_queue::value_comp (STL/CLR)](#value_comp)|Kopiert den Delegaten für die Sortierung für zwei Elemente.|

|Eigenschaft|BESCHREIBUNG|
|--------------|-----------------|
|[priority_queue::top_item (STL/CLR)](#top_item)|Greift auf das Element mit der höchsten Priorität zu.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[priority_queue::operator= (STL/CLR)](#op_as)|Ersetzt die kontrollierte Sequenz.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren eines Objekts.|
|IPriorityQueue\<Wert, Container >|Verwalten Sie einen generischen Container Adapter.|

## <a name="remarks"></a>Bemerkungen

Das-Objekt ordnet Speicher für die Sequenz zu, die er durch einen zugrunde liegenden Container (vom Typ "`Container`" steuert, der `Value` Elemente speichert und Bedarfs gesteuert wächst. Die Sequenz wird als Heap angeordnet, wobei das Element mit der höchsten Priorität (das oberste Element) leicht zugänglich ist und entfernt werden kann. Das-Objekt schränkt den Zugriff auf das übertragen neuer Elemente ein und Pop nur das Element mit der höchsten Priorität durch und implementiert eine Prioritäts Warteschlange

Das Objekt sortiert die Sequenz, die es steuert, indem es ein gespeichertes Delegatobjekt vom Typ [priority_queue:: Value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)aufruft. Sie können das gespeicherte Delegatobjekt angeben, wenn Sie die Priority_queue erstellen; Wenn Sie kein Delegatobjekt angeben, ist der Standardwert der Vergleichs `operator<(value_type, value_type)`. Sie greifen auf dieses gespeicherte Objekt zu, indem Sie die-Member-Funktion [priority_queue:: value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`aufrufen.

Ein solches Delegatobjekt muss eine strikte schwache Reihenfolge für Werte des Typs [priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)erzwingen. Dies bedeutet, dass für alle zwei Schlüssel `X` und `Y`:

`value_comp()(X, Y)` gibt bei jedem-Rückruf dasselbe boolesche Ergebnis zurück.

Wenn `value_comp()(X, Y)` true ist, muss `value_comp()(Y, X)` den Wert false aufweisen.

Wenn `value_comp()(X, Y)` den Wert true hat, wird `X` vor dem `Y`als geordnet bezeichnet.

Wenn `!value_comp()(X, Y) && !value_comp()(Y, X)` true ist, werden `X` und `Y` als äquivalente Reihenfolge bezeichnet.

Für alle Element `X`, das `Y` in der gesteuerten Sequenz vorangeht, ist `key_comp()(Y, X)` false. (Für das standarddelegatobjekt verringern Schlüssel niemals den Wert.)

Das Element mit der höchsten Priorität ist daher eines der-Elemente, das nicht vor einem anderen Element geordnet ist.

Da der zugrunde liegende Container Elemente als Heap angeordnet hält:

Der Container muss Iteratoren mit zufälligem Zugriff unterstützen.

Elemente, die gleichwertig sortiert werden, können in einer anderen Reihenfolge als per Pushvorgang gerenppt werden. (Die Reihenfolge ist nicht stabil.)

Folglich enthalten Kandidaten für den zugrunde liegenden Container Doppel Schlange [(STL/CLR)](../dotnet/deque-stl-clr.md) und [Vector (STL/CLR)](../dotnet/vector-stl-clr.md).

## <a name="members"></a>Members

## <a name="priority_queueassign-stlclr"></a><a name="assign"></a>priority_queue:: Assign (STL/CLR)

Ersetzt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void assign(priority_queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Der einzufügende Container Adapter.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion weist `right.get_container()` dem zugrunde liegenden Container zu. Sie verwenden Sie, um den gesamten Inhalt der Warteschlange zu ändern.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign a repetition of values
    Mypriority_queue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queueconst_reference-stlclr"></a><a name="const_reference"></a>priority_queue:: const_reference (STL/CLR)

Der Typ eines konstanten Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen konstanten Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mypriority_queue::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="priority_queuecontainer_type-stlclr"></a><a name="container_type"></a>priority_queue:: container_type (STL/CLR)

Der Typ des zugrunde liegenden Containers.

### <a name="syntax"></a>Syntax

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Container`dar.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c" using container_type
    Mypriority_queue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuedifference_type-stlclr"></a><a name="difference_type"></a>priority_queue::d ifference_type (STL/CLR)

Die Typen eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine möglicherweise negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute negative difference
    Mypriority_queue::difference_type diff = c1.size();
    c1.push(L'd');
    c1.push(L'e');
    diff -= c1.size();
    System::Console::WriteLine("pushing 2 = {0}", diff);

    // compute positive difference
    diff = c1.size();
    c1.pop();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("popping 3 = {0}", diff);
    return (0);
    }
```

```Output
c a b
pushing 2 = -2
popping 3 = 3
```

## <a name="priority_queueempty-stlclr"></a><a name="empty"></a>priority_queue:: Empty (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Dies entspricht [priority_queue:: Size (STL/CLR)-](../dotnet/priority-queue-size-stl-clr.md)`() == 0`. Sie verwenden es, um zu testen, ob das Priority_queue leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.pop();
    c1.pop();
    c1.pop();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
c a b
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="priority_queuegeneric_container-stlclr"></a><a name="generic_container"></a>priority_queue:: generic_container (STL/CLR)

Der Typ der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>
    generic_container;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt die generische Schnittstelle für diese Vorlagen Container-Adapter Klasse.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
d c b a
e d b a c
```

## <a name="priority_queuegeneric_value-stlclr"></a><a name="generic_value"></a>priority_queue:: generic_value (STL/CLR)

Der Typ eines Elements, das mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt vom Typ `GValue`, das den gespeicherten Elementwert zur Verwendung mit der generischen-Schnittstelle für diese Vorlagen Container Klasse beschreibt. (`GValue` ist entweder `value_type` oder `value_type^`, wenn `value_type` ein Ref-Typ ist.)

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get interface to container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display in priority order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mypriority_queue::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
c b a
```

## <a name="priority_queueget_container-stlclr"></a><a name="get_container"></a>priority_queue:: get_container (STL/CLR)

Greift auf den zugrunde liegenden Container zu.

### <a name="syntax"></a>Syntax

```cpp
container_type get_container();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den zugrunde liegenden Container zurück. Sie verwenden Sie, um die Einschränkungen zu umgehen, die vom Container Wrapper auferlegt werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queueoperator-stlclr"></a><a name="op_as"></a>priority_queue:: Operator = (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Zu Kopier der Container Adapter.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann `*this`zurück. Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mypriority_queue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queuepop-stlclr"></a><a name="pop"></a>priority_queue::p op (STL/CLR)

Entfernt das-Element mit dem höchsten Proirity-Element.

### <a name="syntax"></a>Syntax

```cpp
void pop();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entfernt das Element mit der höchsten Priorität der kontrollierten Sequenz, das nicht leer sein darf. Sie verwenden Sie, um die Warteschlange um ein Element auf der Rückseite zu verkürzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
b a
```

## <a name="priority_queuepriority_queue-stlclr"></a><a name="priority_queue"></a>priority_queue::p riority_queue (STL/CLR)

Erstellt ein Container Adapter Objekt.

### <a name="syntax"></a>Syntax

```cpp
priority_queue();
priority_queue(priority_queue<Value, Container> right);
priority_queue(priority_queue<Value, Container> right);
explicit priority_queue(value_compare^ pred);
priority_queue(value_compare^ pred, container_type% cont);
template<typename InIt>
    priority_queue(InIt first, InIt last);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred, container_type% cont);
```

#### <a name="parameters"></a>Parameter

*Continuous*<br/>
Der zu kopierende Container.

*first*<br/>
Anfang des einzufügenden Bereichs.

*last*<br/>
Das Ende des einzufügenden Bereichs.

*pred*<br/>
Das Anordnungs Prädikat für die gesteuerte Sequenz.

*right*<br/>
Einzufügendes Objekt bzw. einzufügender Bereich.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`priority_queue();`

erstellt einen leeren umschließenen Container mit dem Standard Reihenfolge Prädikat. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem Standard Reihen folgen Prädikat anzugeben.

Der Konstruktor:

`priority_queue(priority_queue<Value, Container>% right);`

erstellt einen umschpackten Container, bei dem es sich um eine Kopie `right.get_container()`handelt, wobei das Bestell Prädikat `right.value_comp()`ist. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, bei der es sich um eine Kopie der Sequenz handelt, die vom Warteschlangen Objekt *direkt*mit dem gleichen Reihen folgen Prädikat gesteuert wird.

Der Konstruktor:

`priority_queue(priority_queue<Value, Container>^ right);`

erstellt einen umschpackten Container, bei dem es sich um eine Kopie `right->get_container()`handelt, wobei das Bestell Prädikat `right->value_comp()`ist. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, bei der es sich um eine Kopie der Sequenz handelt, die vom Warteschlangen Objekt `*right`und desselben Reihen folgen Prädikats gesteuert wird.

Der Konstruktor:

`explicit priority_queue(value_compare^ pred);`

erstellt einen leeren umschließenen Container mit dem *pred-Prädikat*für die Reihenfolge. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem angegebenen Reihen folgen Prädikat anzugeben.

Der Konstruktor:

`priority_queue(value_compare^ pred, container_type cont);`

erstellt einen leeren umschließenden Container mit dem Bestellungs Prädikat *pred*und legt dann alle Elemente *von der* Verwendung per Push, um eine anfängliche gesteuerte Sequenz von einem vorhandenen Container mit dem angegebenen Reihen folgen Prädikat anzugeben.

Der Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last);`

erstellt einen leeren umschließenen Container mit dem Standard Reihen folgen Prädikat und überträgt dann die Sequenz [`first``last`). Sie verwenden es, um eine anfängliche gesteuerte Sequenz von einem angegebenen eqeuence mit dem angegebenen Reihen folgen Prädikat anzugeben.

Der Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`

erstellt einen leeren umschließenen Container mit dem *pred-Prädikat*für die Reihenfolge und überträgt dann die Sequenz [`first``last`). Sie verwenden es, um eine anfängliche gesteuerte Sequenz von einem angegebenen Seqeuence mit dem angegebenen Reihen folgen Prädikat anzugeben.

Der Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`

erstellt einen leeren Container mit dem Bestellungs Prädikat *pred*und überträgt dann alle Elemente von " *EST* " plus die Sequenz [`first``last`). Sie verwenden es, um eine anfängliche gesteuerte Sequenz aus einem vorhandenen Container und einen angegebenen Seqeuence mit dem angegebenen Reihen folgen Prädikat anzugeben.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/deque>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
typedef cliext::deque<wchar_t> Mydeque;
int main()
    {
// construct an empty container
    Mypriority_queue c1;
    Mypriority_queue::container_type^ wc1 = c1.get_container();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    for each (wchar_t elem in wc1)
        c2.push(elem);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule by copying an underlying container
    Mypriority_queue c2x =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
   for each (wchar_t elem in c2x.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mypriority_queue c3(wc1->begin(), wc1->end());
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mypriority_queue c4(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>());
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range, another container, and an ordering rule
    Mypriority_queue c5(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c5.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mypriority_queue c6(c3);
    for each (wchar_t elem in c6.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mypriority_queue c7(%c3);
    for each (wchar_t elem in c7.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule, by copying an underlying container
    Mypriority_queue c8 =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c8.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
c a b
size() = 0
a c b
a c b
c a b
a c b
a a b c c b
c a b
c a b
a c b
```

## <a name="priority_queuepush-stlclr"></a><a name="push"></a>priority_queue::p USH (STL/CLR)

Fügt ein neues Element hinzu.

### <a name="syntax"></a>Syntax

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion fügt ein Element mit einem Wert `val` in die gesteuerte Sequenz ein und ordnet die gesteuerte Sequenz neu an, um die Heap Disziplin aufrechtzuerhalten. Sie verwenden Sie, um der Warteschlange ein weiteres Element hinzuzufügen.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuereference-stlclr"></a><a name="reference"></a>priority_queue:: Reference (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify top of priority_queue and redisplay
    Mypriority_queue::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
x a b
```

## <a name="priority_queuesize-stlclr"></a><a name="size"></a>priority_queue:: Size (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden Sie, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden. Wenn Sie nur für Sie wichtig sind, ob die Sequenz eine Größe ungleich NULL aufweist, finden Sie weitere Informationen unter [priority_queue:: Empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // pop an item and reinspect
    c1.pop();
    System::Console::WriteLine("size() = {0} after popping", c1.size());

    // add two elements and reinspect
    c1.push(L'a');
    c1.push(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
c a b
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="priority_queuesize_type-stlclr"></a><a name="size_type"></a>priority_queue:: size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mypriority_queue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
c a b
size difference = 2
```

## <a name="priority_queueto_array-stlclr"></a><a name="to_array"></a>priority_queue:: to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein Array mit der kontrollierten Sequenz zurück. Sie verwenden Sie, um eine Kopie der kontrollierten Sequenz in Array Form abzurufen.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
d c b a
c a b
```

## <a name="priority_queuetop-stlclr"></a><a name="top"></a>priority_queue:: Top (STL/CLR)

Greift auf das Element mit der höchsten Priorität zu.

### <a name="syntax"></a>Syntax

```cpp
reference top();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf das oberste Element (höchste Priorität) der kontrollierten Sequenz zurück, das nicht leer sein darf. Sie verwenden Sie, um auf das Element mit der höchsten Priorität zuzugreifen, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_top.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top() = {0}", c1.top());

    // alter last item and reinspect
    c1.top() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

## <a name="priority_queuetop_item-stlclr"></a><a name="top_item"></a>priority_queue:: top_item (STL/CLR)

Greift auf das Element mit der höchsten Priorität zu.

### <a name="syntax"></a>Syntax

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Bemerkungen

Die-Eigenschaft greift auf das oberste Element (höchste Priorität) der kontrollierten Sequenz zu, das nicht leer sein darf. Sie verwenden Sie, um das Element mit der höchsten Priorität zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_top_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top_item = {0}", c1.top_item);

    // alter last item and reinspect
    c1.top_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
top_item = c
x a b
```

## <a name="priority_queuevalue_comp-stlclr"></a><a name="value_comp"></a>priority_queue:: value_comp (STL/CLR)

Kopiert den Delegaten für die Sortierung für zwei Elemente.

### <a name="syntax"></a>Syntax

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Sortier Delegaten zurück, der zum Sortieren der kontrollierten Sequenz verwendet wird. Damit können Sie zwei Werte vergleichen.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_value_comp.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="priority_queuevalue_compare-stlclr"></a><a name="value_compare"></a>priority_queue:: Value_compare (STL/CLR)

Der Bestell Delegat für zwei-Werte.

### <a name="syntax"></a>Syntax

```cpp
binary_delegate<value_type, value_type, int> value_compare;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Delegaten, der bestimmt, ob das erste Argument vor dem zweiten Argument geordnet ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_value_compare.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="priority_queuevalue_type-stlclr"></a><a name="value_type"></a>priority_queue:: value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter *Wert*.

### <a name="example"></a>Beispiel

```cpp
// cliext_priority_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mypriority_queue::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```
