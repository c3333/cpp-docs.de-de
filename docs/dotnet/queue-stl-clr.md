---
title: queue (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::queue
- cliext::queue::assign
- cliext::queue::back
- cliext::queue::back_item
- cliext::queue::const_reference
- cliext::queue::container_type
- cliext::queue::difference_type
- cliext::queue::empty
- cliext::queue::front
- cliext::queue::front_item
- cliext::queue::generic_container
- cliext::queue::generic_value
- cliext::queue::get_container
- cliext::queue::operator=
- cliext::queue::pop
- cliext::queue::push
- cliext::queue::queue
- cliext::queue::reference
- cliext::queue::size
- cliext::queue::size_type
- cliext::queue::to_array
- cliext::queue::value_type
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- push member [STL/CLR]
- queue member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
ms.openlocfilehash: 5339472574bced99d833a0b60e8b72b10b0fa989
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208363"
---
# <a name="queue-stlclr"></a>queue (STL/CLR)

Die Vorlagen Klasse beschreibt ein Objekt, das eine Sequenz von Elementen mit variabler Länge steuert, die über den First-in-First-Out-Zugriff verfügt. Sie verwenden den Container Adapter `queue`, um einen zugrunde liegenden Container als Warteschlange zu verwalten.

In der folgenden Beschreibung ist `GValue` identisch mit dem *Wert* , es sei denn, der letztere ist ein Ref-Typ. in diesem Fall ist es `Value^`. Ebenso ist `GContainer` identisch mit dem *Container* , es sei denn, es handelt sich um einen Verweistyp. in diesem Fall ist es `Container^`.

## <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    ref class queue
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>
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
|[queue::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[queue::container_type (STL/CLR)](#container_type)|Der Typ des zugrunde liegenden Containers.|
|[queue::difference_type (STL/CLR)](#difference_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[queue::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container Adapter.|
|[queue::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container Adapter.|
|[queue::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[queue::size_type (STL/CLR)](#size_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[queue::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[queue::assign (STL/CLR)](#assign)|Ersetzt alle Elemente.|
|[queue::back (STL/CLR)](#back)|Greift auf das letzte Element zu.|
|[queue::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[queue::front (STL/CLR)](#front)|Greift auf das erste Element zu.|
|[queue::get_container (STL/CLR)](#get_container)|Greift auf den zugrunde liegenden Container zu.|
|[queue::pop (STL/CLR)](#pop)|Entfernt das erste Element.|
|[queue::push (STL/CLR)](#push)|Fügt ein neues letztes Element hinzu.|
|[queue::queue (STL/CLR)](#queue)|Erstellt ein container-Objekt.|
|[queue::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[queue::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|

|Eigenschaft|BESCHREIBUNG|
|--------------|-----------------|
|[queue::back_item (STL/CLR)](#back_item)|Greift auf das letzte Element zu.|
|[queue::front_item (STL/CLR)](#front_item)|Greift auf das erste Element zu.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[queue::operator= (STL/CLR)](#op_as)|Ersetzt die kontrollierte Sequenz.|
|[operator!= (queue) (STL/CLR)](#op_neq)|Bestimmt, ob ein `queue` Objekt nicht gleich einem anderen `queue` Objekt ist.|
|[operator< (queue) (STL/CLR)](#op_lt)|Bestimmt, ob ein `queue` Objekt kleiner als ein anderes `queue`-Objekt ist.|
|[operator<= (queue) (STL/CLR)](#op_lteq)|Bestimmt, ob ein `queue`-Objekt kleiner als oder gleich einem anderen `queue`-Objekt ist.|
|[operator== (queue) (STL/CLR)](#op_eq)|Bestimmt, ob ein `queue` Objekt gleich einem anderen `queue`-Objekt ist.|
|[operator> (queue) (STL/CLR)](#op_gt)|Bestimmt, ob ein `queue` Objekt größer als ein anderes `queue`-Objekt ist.|
|[operator>= (queue) (STL/CLR)](#op_gteq)|Bestimmt, ob ein `queue` Objekt größer als oder gleich einem anderen `queue` Objekt ist.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren eines Objekts.|
|IQueue\<Wert, Container >|Verwalten Sie einen generischen Container Adapter.|

## <a name="remarks"></a>Bemerkungen

Das-Objekt ordnet Speicher für die Sequenz zu, die er durch einen zugrunde liegenden Container (vom Typ "`Container`" steuert, der `Value` Elemente speichert und Bedarfs gesteuert wächst. Das-Objekt schränkt den Zugriff ein, um nur das erste Element per Push zu übertragen und das letzte Element zu pingen. dabei wird eine First-in-First-Out-Warteschlange implementiert (auch als FIFO-Warteschlange bezeichnet).

## <a name="members"></a>Members

## <a name="queueassign-stlclr"></a><a name="assign"></a>Queue:: Assign (STL/CLR)

Ersetzt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void assign(queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Der einzufügende Container Adapter.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion weist `right.get_container()` dem zugrunde liegenden Container zu. Sie verwenden Sie, um den gesamten Inhalt der Warteschlange zu ändern.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Myqueue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="queueback-stlclr"></a><a name="back"></a>Queue:: Back (STL/CLR)

Greift auf das letzte Element zu.

### <a name="syntax"></a>Syntax

```cpp
reference back();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf das letzte Element der kontrollierten Sequenz zurück, das nicht leer sein darf. Sie verwenden Sie, um auf das letzte Element zuzugreifen, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_back.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

// alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="queueback_item-stlclr"></a><a name="back_item"></a>Queue:: back_item (STL/CLR)

Greift auf das letzte Element zu.

### <a name="syntax"></a>Syntax

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Bemerkungen

Die-Eigenschaft greift auf das letzte Element der kontrollierten Sequenz zu, das nicht leer sein darf. Sie verwenden Sie, um das letzte Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_back_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

// alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="queueconst_reference-stlclr"></a><a name="const_reference"></a>Queue:: const_reference (STL/CLR)

Der Typ eines konstanten Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen konstanten Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Myqueue::const_reference cref = c1.front();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="queuecontainer_type-stlclr"></a><a name="container_type"></a>Queue:: container_type (STL/CLR)

Der Typ des zugrunde liegenden Containers.

### <a name="syntax"></a>Syntax

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Container`dar.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Myqueue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="queuedifference_type-stlclr"></a><a name="difference_type"></a>Queue::d ifference_type (STL/CLR)

Die Typen eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine möglicherweise negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute negative difference
    Myqueue::difference_type diff = c1.size();
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
a b c
pushing 2 = -2
popping 3 = 3
```

## <a name="queueempty-stlclr"></a><a name="empty"></a>Queue:: Empty (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Dies entspricht dem [Queue:: Size (STL/CLR)-](../dotnet/queue-size-stl-clr.md)`() == 0`. Sie verwenden es, um zu testen, ob die Warteschlange leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="queuefront-stlclr"></a><a name="front"></a>Queue:: Front (STL/CLR)

Greift auf das erste Element zu.

### <a name="syntax"></a>Syntax

```cpp
reference front();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf das erste Element der kontrollierten Sequenz zurück, das nicht leer sein darf. Sie verwenden Sie, um auf das erste Element zuzugreifen, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_front.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

// alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

## <a name="queuefront_item-stlclr"></a><a name="front_item"></a>Queue:: front_item (STL/CLR)

Greift auf das erste Element zu.

### <a name="syntax"></a>Syntax

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Bemerkungen

Die-Eigenschaft greift auf das erste Element der kontrollierten Sequenz zu, das nicht leer sein darf. Sie verwenden Sie, um das erste Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_front_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

// alter last item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

## <a name="queuegeneric_container-stlclr"></a><a name="generic_container"></a>Queue:: generic_container (STL/CLR)

Der Typ der generischen Schnittstelle für den Container Adapter.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::IQueue<Value>
    generic_container;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt die generische Schnittstelle für diese Vorlagen Container-Adapter Klasse.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myqueue::generic_container^ gc1 = %c1;
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
a b c
a b c
a b c d
a b c d e
```

## <a name="queuegeneric_value-stlclr"></a><a name="generic_value"></a>Queue:: generic_value (STL/CLR)

Der Typ eines Elements, das mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt vom Typ `GValue`, das den gespeicherten Elementwert zur Verwendung mit der generischen-Schnittstelle für diese Vorlagen Container Klasse beschreibt. (`GValue` ist entweder `value_type` oder `value_type^`, wenn `value_type` ein Ref-Typ ist.)

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Myqueue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Myqueue::generic_value elem = gc1->front();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c
```

## <a name="queueget_container-stlclr"></a><a name="get_container"></a>Queue:: get_container (STL/CLR)

Greift auf den zugrunde liegenden Container zu.

### <a name="syntax"></a>Syntax

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den zugrunde liegenden Container zurück. Sie verwenden Sie, um die Einschränkungen zu umgehen, die vom Container Wrapper auferlegt werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
```

## <a name="queueoperator-stlclr"></a><a name="op_as"></a>Queue:: Operator = (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
queue <Value, Container>% operator=(queue <Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Zu Kopier der Container Adapter.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann `*this`zurück. Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="queuepop-stlclr"></a><a name="pop"></a>Queue::p op (STL/CLR)

Entfernt das letzte Element.

### <a name="syntax"></a>Syntax

```cpp
void pop();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entfernt das letzte Element der kontrollierten Sequenz, das nicht leer sein darf. Sie verwenden Sie, um die Warteschlange um ein Element auf der Rückseite zu verkürzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
b c
```

## <a name="queuepush-stlclr"></a><a name="push"></a>Queue::p USH (STL/CLR)

Fügt ein neues letztes Element hinzu.

### <a name="syntax"></a>Syntax

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion fügt ein Element mit einem Wert `val` am Ende der Warteschlange hinzu. Sie verwenden es, um ein Element an die Warteschlange anzufügen.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
```

## <a name="queuequeue-stlclr"></a><a name="queue"></a>Queue:: Queue (STL/CLR)

Erstellt ein Container Adapter Objekt.

### <a name="syntax"></a>Syntax

```cpp
queue();
queue(queue<Value, Container>% right);
queue(queue<Value, Container>^ right);
explicit queue(container_type% wrapped);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Objekt, das kopiert werden soll.

*nür*<br/>
Der zu verwendende Container.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`queue();`

erstellt einen leeren umschließenen Container. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz anzugeben.

Der Konstruktor:

`queue(queue<Value, Container>% right);`

erstellt einen umschpackten Container, der eine Kopie von `right.get_container()`ist. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom Queue-Objekt *Rechts*gesteuert wird.

Der Konstruktor:

`queue(queue<Value, Container>^ right);`

erstellt einen umschpackten Container, der eine Kopie von `right->get_container()`ist. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom Warteschlangen Objekt `*right`gesteuert wird.

Der Konstruktor:

`explicit queue(container_type wrapped);`

verwendet den vorhandenen Container, der als umschließenden Container *umschließt* . Sie verwenden Sie, um eine Warteschlange aus einem vorhandenen Container zu erstellen.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/list>

typedef cliext::queue<wchar_t> Myqueue;
typedef cliext::list<wchar_t> Mylist;
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;
int main()
    {
// construct an empty container
    Myqueue c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct from an underlying container
    Mylist v2(5, L'x');
    Myqueue_list c2(v2);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myqueue_list c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Myqueue_list c4(%c2);
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
x x x x x
x x x x x
x x x x x
```

## <a name="queuereference-stlclr"></a><a name="reference"></a>Queue:: Reference (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify back of queue and redisplay
    Myqueue::reference ref = c1.back();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b x
```

## <a name="queuesize-stlclr"></a><a name="size"></a>Queue:: Size (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden Sie, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden. Wenn Sie nur sicher sind, ob die Sequenz eine Größe ungleich NULL aufweist, finden Sie weitere Informationen unter [Queue:: Empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)`()`.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="queuesize_type-stlclr"></a><a name="size_type"></a>Queue:: size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myqueue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
a b c
size difference = 2
```

## <a name="queueto_array-stlclr"></a><a name="to_array"></a>Queue:: to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein Array mit der kontrollierten Sequenz zurück. Sie verwenden Sie, um eine Kopie der kontrollierten Sequenz in Array Form abzurufen.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
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
a b c d
a b c
```

## <a name="queuevalue_type-stlclr"></a><a name="value_type"></a>Queue:: value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter *Wert*.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Myqueue::value_type val = c1.front();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-queue-stlclr"></a><a name="op_neq"></a>Operator! = (Queue) (STL/CLR)

Die Warteschlange entspricht nicht dem Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator!=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt `!(left == right)`zurück. Sie verwenden es, um zu testen, ob *left* nicht identisch ist *, wenn die* beiden Warteschlangen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_operator_ne.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-queue-stlclr"></a><a name="op_lt"></a>Operator&lt; (Warteschlange) (STL/CLR)

Warteschlange ist kleiner als der Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator<(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt true zurück, wenn für die niedrigste Position `i` für die `!(right[i] < left[i])` auch true ist, dass `left[i] < right[i]`. Andernfalls wird `left->`[Queue:: Size (STL/CLR)-](../dotnet/queue-size-stl-clr.md)`() <` zurückgegeben `right->size()` Sie verwenden Sie, um zu testen, ob *left* nach *Rechts* geordnet ist, wenn die beiden Warteschlangen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_operator_lt.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-queue-stlclr"></a><a name="op_lteq"></a>Operator&lt;= (Queue) (STL/CLR)

Warteschlange kleiner oder gleich-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator<=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt `!(right < left)`zurück. Sie verwenden es, um zu testen, ob *left* nach *Rechts* nicht geordnet ist, wenn die beiden Warteschlangen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_operator_le.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-queue-stlclr"></a><a name="op_eq"></a>Operator = = (Queue) (STL/CLR)

In Warteschlange gleicher Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator==(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt nur dann true zurück, wenn die von *Links* und *Rechts* gesteuerten Sequenzen die gleiche Länge aufweisen und für jede Position `i``left[i] ==` `right[i]`. Sie verwenden es, um zu überprüfen, ob *Links* mit dem Element nach dem Element überein *Stimmen* .

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_operator_eq.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-queue-stlclr"></a><a name="op_gt"></a>Operator&gt; (Warteschlange) (STL/CLR)

Warteschlange ist größer als der Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator>(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt `right` `<` `left`zurück. Sie verwenden es, um zu testen, ob *Links* nach *Rechts* angeordnet ist, wenn die beiden Warteschlangen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_operator_gt.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-queue-stlclr"></a><a name="op_gteq"></a>Operator&gt;= (Queue) (STL/CLR)

Warteschlangen Vergleich größer oder gleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator>=(queue<Value, Container>% left,
        queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt `!(left < right)`zurück. Sie verwenden es, um zu testen, ob *left* nicht vor *Rechts* geordnet ist, wenn die beiden Warteschlangen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_queue_operator_ge.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::queue<wchar_t> Myqueue;
int main()
    {
    Myqueue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myqueue c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
