---
title: stack (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::stack
- cliext::stack::assign
- cliext::stack::const_reference
- cliext::stack::container_type
- cliext::stack::difference_type
- cliext::stack::empty
- cliext::stack::generic_container
- cliext::stack::generic_value
- cliext::stack::get_container
- cliext::stack::operator=
- cliext::stack::pop
- cliext::stack::push
- cliext::stack::reference
- cliext::stack::size
- cliext::stack::size_type
- cliext::stack::stack
- cliext::stack::to_array
- cliext::stack::top
- cliext::stack::top_item
- cliext::stack::value_type
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
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
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- stack member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
ms.openlocfilehash: 5f5cfbb4f6125c1c72550018735b377e1507ab08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214885"
---
# <a name="stack-stlclr"></a>stack (STL/CLR)

Die Vorlagen Klasse beschreibt ein Objekt, das eine Sequenz von Elementen variabler Länge steuert, die über den letzten Zugriff verfügt. Sie verwenden den Container Adapter `stack` , um einen zugrunde liegenden Container als Push-Down-Stapel zu verwalten.

In der Beschreibung unten `GValue` ist mit dem *Wert* identisch, es sei denn, der letztere ist ein Ref-Typ. in diesem Fall ist es `Value^` . Ebenso `GContainer` ist identisch mit dem *Container* , es sei denn, der letztere ist ein Ref-Typ. in diesem Fall ist es `Container^` .

## <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    ref class stack
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Der Typ eines Elements in der kontrollierten Sequenz.

*Container*<br/>
Der Typ des zugrunde liegenden Containers.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<cliext/stack>

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Typendefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[stack::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[stack::container_type (STL/CLR)](#container_type)|Der Typ des zugrunde liegenden Containers.|
|[stack::difference_type (STL/CLR)](#difference_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[stack::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container Adapter.|
|[stack::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container Adapter.|
|[stack::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[stack::size_type (STL/CLR)](#size_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[stack::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[stack::assign (STL/CLR)](#assign)|Ersetzt alle Elemente.|
|[stack::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[stack::get_container (STL/CLR)](#get_container)|Greift auf den zugrunde liegenden Container zu.|
|[stack::pop (STL/CLR)](#pop)|Entfernt das letzte Element.|
|[stack::push (STL/CLR)](#push)|Fügt ein neues letztes Element hinzu.|
|[stack::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[stack::stack (STL/CLR)](#stack)|Erstellt ein container-Objekt.|
|[stack::top (STL/CLR)](#top)|Greift auf das letzte Element zu.|
|[stack::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|

|Eigenschaft|BESCHREIBUNG|
|--------------|-----------------|
|[stack::top_item (STL/CLR)](#top_item)|Greift auf das letzte Element zu.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[stack::operator= (STL/CLR)](#op_as)|Ersetzt die kontrollierte Sequenz.|
|[Operator! = (Stack) (STL/CLR)](#op_neq)|Bestimmt, ob ein-Objekt ungleich einem `stack` anderen `stack` Objekt ist.|
|[Operator< (Stapel) (STL/CLR)](#op_lt)|Bestimmt, ob ein- `stack` Objekt kleiner als ein anderes- `stack` Objekt ist.|
|[Operator<= (Stack) (STL/CLR)](#op_lteq)|Bestimmt, ob ein- `stack` Objekt kleiner als oder gleich einem anderen- `stack` Objekt ist.|
|[operator== (stack) (STL/CLR)](#op_eq)|Bestimmt, ob ein- `stack` Objekt gleich einem anderen- `stack` Objekt ist.|
|[Operator> (Stapel) (STL/CLR)](#op_gt)|Bestimmt, ob ein- `stack` Objekt größer als ein anderes- `stack` Objekt ist.|
|[Operator>= (Stack) (STL/CLR)](#op_gteq)|Bestimmt, ob ein- `stack` Objekt größer als oder gleich einem anderen- `stack` Objekt ist.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren eines Objekts.|
|IStack\<Value, Container>|Verwalten Sie einen generischen Container Adapter.|

## <a name="remarks"></a>Bemerkungen

Das-Objekt ordnet Speicher für die Sequenz zu, die er durch einen zugrunde liegenden Container (vom Typ *Container*) steuert und freigibt, der *Wert* Elemente speichert und Bedarfs gesteuert wächst. Das-Objekt schränkt den Zugriff auf Push und Pop nur das letzte Element ein und implementiert eine letzte in-Out-Warteschlange (auch als LIFO-Warteschlange oder Stapel bezeichnet).

## <a name="members"></a>Member

## <a name="stackassign-stlclr"></a><a name="assign"></a>Stack:: Assign (STL/CLR)

Ersetzt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void assign(stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Der einzufügende Container Adapter.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion weist `right.get_container()` den zugrunde liegenden Container zu. Sie verwenden Sie, um den gesamten Inhalt des Stapels zu ändern.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_assign.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Mystack c2;
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

## <a name="stackconst_reference-stlclr"></a><a name="const_reference"></a>Stack:: const_reference (STL/CLR)

Der Typ eines konstanten Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen konstanten Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_const_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mystack::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="stackcontainer_type-stlclr"></a><a name="container_type"></a>Stack:: container_type (STL/CLR)

Der Typ des zugrunde liegenden Containers.

### <a name="syntax"></a>Syntax

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist synonym mit dem Vorlagenparameter *Container*.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_container_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="stackdifference_type-stlclr"></a><a name="difference_type"></a>Stapel::d ifference_type (STL/CLR)

Die Typen eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine möglicherweise negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_difference_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute negative difference
    Mystack::difference_type diff = c1.size();
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

## <a name="stackempty-stlclr"></a><a name="empty"></a>Stack:: Empty (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Dies entspricht [Stack:: Size (STL/CLR)](../dotnet/stack-size-stl-clr.md) `() == 0` . Sie verwenden es, um zu testen, ob der Stapel leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_empty.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="stackgeneric_container-stlclr"></a><a name="generic_container"></a>Stack:: generic_container (STL/CLR)

Der Typ der generischen Schnittstelle für den Container Adapter.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::IStack<Value>
    generic_container;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt die generische Schnittstelle für diese Vorlagen Container-Adapter Klasse.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_generic_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
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

## <a name="stackgeneric_value-stlclr"></a><a name="generic_value"></a>Stack:: generic_value (STL/CLR)

Der Typ eines Elements, das mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt vom Typ `GValue` , das den gespeicherten Elementwert zur Verwendung mit der generischen-Schnittstelle für diese Vorlagen Container Klasse beschreibt. ( `GValue` ist entweder `value_type` oder, `value_type^` Wenn `value_type` ein Ref-Typ ist.)

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_generic_value.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in reverse using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mystack::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
c b a
```

## <a name="stackget_container-stlclr"></a><a name="get_container"></a>Stack:: get_container (STL/CLR)

Greift auf den zugrunde liegenden Container zu.

### <a name="syntax"></a>Syntax

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein Handle für den zugrunde liegenden Container zurück. Sie verwenden Sie, um die Einschränkungen zu umgehen, die vom Container Wrapper auferlegt werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_get_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="stackoperator-stlclr"></a><a name="op_as"></a>Stack:: Operator = (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
stack <Value, Container>% operator=(stack <Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Zu Kopier der Container Adapter.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann zurück **`*this`** . Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_operator_as.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="stackpop-stlclr"></a><a name="pop"></a>Stack::p op (STL/CLR)

Entfernt das letzte Element.

### <a name="syntax"></a>Syntax

```cpp
void pop();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entfernt das letzte Element der kontrollierten Sequenz, das nicht leer sein darf. Sie verwenden Sie, um den Stapel um ein Element auf der Rückseite zu verkürzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_pop.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b
```

## <a name="stackpush-stlclr"></a><a name="push"></a>Stack::p USH (STL/CLR)

Fügt ein neues letztes Element hinzu.

### <a name="syntax"></a>Syntax

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion fügt ein Element mit `val` dem Wert am Ende der kontrollierten Sequenz ein. Sie verwenden es, um ein weiteres Element an den Stapel anzufügen.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_push.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="stackreference-stlclr"></a><a name="reference"></a>Stack:: Reference (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify top of stack and redisplay
    Mystack::reference ref = c1.top();
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

## <a name="stacksize-stlclr"></a><a name="size"></a>Stack:: Size (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden Sie, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden. Wenn Sie nur für Sie wichtig sind, ob die Sequenz eine Größe ungleich NULL aufweist, finden Sie weitere Informationen unter [Stack:: Empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md) `()` .

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_size.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="stacksize_type-stlclr"></a><a name="size_type"></a>Stack:: size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_size_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Mystack::size_type diff = c1.size();
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

## <a name="stackstack-stlclr"></a><a name="stack"></a>Stack:: Stack (STL/CLR)

Erstellt ein Container Adapter Objekt.

### <a name="syntax"></a>Syntax

```cpp
stack();
stack(stack<Value, Container>% right);
stack(stack<Value, Container>^ right);
explicit stack(container_type% wrapped);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Objekt, das kopiert werden soll.

*nür*<br/>
Der zu verwendende Container.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`stack();`

erstellt einen leeren umschließenen Container. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz anzugeben.

Der Konstruktor:

`stack(stack<Value, Container>% right);`

erstellt einen umschpackten Container, der eine Kopie von ist `right.get_container()` . Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom Stapel Objekt *Rechts*gesteuert wird.

Der Konstruktor:

`stack(stack<Value, Container>^ right);`

erstellt einen umschpackten Container, der eine Kopie von ist `right->get_container()` . Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom Stapel Objekt gesteuert wird `*right` .

Der Konstruktor:

`explicit stack(container_type% wrapped);`

verwendet den vorhandenen Container, der als umschließenden Container *umschließt* . Sie verwenden Sie, um einen Stapel aus einem vorhandenen Container zu erstellen.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_construct.cpp
// compile with: /clr
#include <cliext/stack>
#include <cliext/vector>

typedef cliext::stack<wchar_t> Mystack;
typedef cliext::vector<wchar_t> Myvector;
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;
int main()
    {
// construct an empty container
    Mystack c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct from an underlying container
    Myvector v2(5, L'x');
    Mystack_vec c2(v2);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Mystack_vec c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Mystack_vec c4(%c2);
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

## <a name="stackto_array-stlclr"></a><a name="to_array"></a>Stack:: to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein Array mit der kontrollierten Sequenz zurück. Sie verwenden Sie, um eine Kopie der kontrollierten Sequenz in Array Form abzurufen.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_to_array.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

## <a name="stacktop-stlclr"></a><a name="top"></a>Stack:: Top (STL/CLR)

Greift auf das letzte Element zu.

### <a name="syntax"></a>Syntax

```cpp
reference top();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf das letzte Element der kontrollierten Sequenz zurück, das nicht leer sein darf. Sie verwenden Sie, um auf das letzte Element zuzugreifen, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_top.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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

```Output
a b c
top() = c
a b x
```

## <a name="stacktop_item-stlclr"></a><a name="top_item"></a>Stack:: top_item (STL/CLR)

Greift auf das letzte Element zu.

### <a name="syntax"></a>Syntax

```cpp
property value_type top_item;
```

### <a name="remarks"></a>Bemerkungen

Die-Eigenschaft greift auf das letzte Element der kontrollierten Sequenz zu, das nicht leer sein darf. Sie verwenden Sie, um das letzte Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_top_item.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
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
a b c
top_item = c
a b x
```

## <a name="stackvalue_type-stlclr"></a><a name="value_type"></a>Stack:: value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter *Wert*.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_value_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mystack::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="operator-stack-stlclr"></a><a name="op_neq"></a>Operator! = (Stack) (STL/CLR)

Der Stapel entspricht nicht dem Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator!=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator Funktion gibt zurück `!(left == right)` . Sie verwenden es, um zu testen, ob *left* nicht identisch ist *, wenn die* beiden Stapel Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_operator_ne.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operatorlt-stack-stlclr"></a><a name="op_lt"></a>Operator &lt; (Stapel) (STL/CLR)

Der Stapel ist kleiner als der Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator<(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt true zurück, wenn für die niedrigste Position, `i` für die `!(right[i] < left[i])` Sie ebenfalls true ist `left[i] < right[i]` . Andernfalls `left->` wird [Stack:: Size (STL/CLR)](../dotnet/stack-size-stl-clr.md) zurückgegeben, `() <` `right->size()` um zu testen, ob *left* nach *Rechts* geordnet ist, wenn die beiden Stapel Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_operator_lt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operatorlt-stack-stlclr"></a><a name="op_lteq"></a>Operator &lt; = (Stack) (STL/CLR)

Stapel kleiner oder gleich-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator<=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator Funktion gibt zurück `!(right < left)` . Sie verwenden es, um zu testen, ob *left* nach *Rechts* nicht geordnet ist, wenn die beiden Stapel Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_operator_le.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operator-stack-stlclr"></a><a name="op_eq"></a>Operator = = (Stack) (STL/CLR)

Stapel gleicher Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator==(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt nur dann true zurück, wenn die von *Links* und *Rechts* gesteuerten Sequenzen die gleiche Länge aufweisen und für jede Position `i` `left[i] ==` `right[i]` . Sie verwenden es, um zu überprüfen, ob *Links* mit *right* dem Element by-Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_operator_eq.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operatorgt-stack-stlclr"></a><a name="op_gt"></a>Operator &gt; (Stapel) (STL/CLR)

Der Stapel ist größer als der Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator>(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator Funktion gibt zurück `right` `<` `left` . Sie verwenden es, um zu testen, ob *Links* nach *Rechts* angeordnet ist, wenn die beiden Stapel Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_operator_gt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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

## <a name="operatorgt-stack-stlclr"></a><a name="op_gteq"></a>Operator &gt; = (Stack) (STL/CLR)

Stapel größer oder gleich-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value,
    typename Container>
    bool operator>=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator Funktion gibt zurück `!(left < right)` . Sie verwenden es, um zu testen, ob *left* nicht vor *Rechts* geordnet ist, wenn die beiden Stapel Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_stack_operator_ge.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
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
