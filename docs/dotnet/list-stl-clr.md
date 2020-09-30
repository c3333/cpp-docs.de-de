---
title: list (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
ms.openlocfilehash: 9ef9f68c6bef72bf251d270b3bc8142448016a11
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508731"
---
# <a name="list-stlclr"></a>list (STL/CLR)

Die Vorlagen Klasse beschreibt ein Objekt, das eine Sequenz von Elementen variabler Länge steuert, die bidirektionalen Zugriff hat. Sie verwenden den Container `list` zum Verwalten einer Sequenz von Elementen als bidirektionale verknüpfte Liste von Knoten, die jeweils ein Element speichern.

In der Beschreibung unten `GValue` ist mit dem *Wert* identisch, es sei denn, der letztere ist ein Ref-Typ. in diesem Fall ist es `Value^` .

## <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    ref class list
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        Microsoft::VisualC::StlClr::IList<GValue>
    { ..... };
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Der Typ eines Elements in der kontrollierten Sequenz.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<cliext/list>

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Typendefinition|Beschreibung|
|---------------------|-----------------|
|[list::const_iterator (STL/CLR)](#const_iterator)|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|[list::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.|
|[list::difference_type (STL/CLR)](#difference_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[list::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container.|
|[list::generic_iterator (STL/CLR)](#generic_iterator)|Der Typ eines Iterators für die generische Schnittstelle für den Container.|
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Der Typ eines umgekehrten Iterators für die generische Schnittstelle für den Container.|
|[list::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container.|
|[list::iterator (STL/CLR)](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[list::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.|
|[list::size_type (STL/CLR)](#size_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[list::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|Beschreibung|
|---------------------|-----------------|
|[list::assign (STL/CLR)](#assign)|Ersetzt alle Elemente.|
|[list::back (STL/CLR)](#back)|Greift auf das letzte Element zu.|
|[list::begin (STL/CLR)](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[list::clear (STL/CLR)](#clear)|Entfernt alle Elemente.|
|[list::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[list::end (STL/CLR)](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[list::erase (STL/CLR)](#erase)|Entfernt Elemente an den angegebenen Positionen.|
|[list::front (STL/CLR)](#front)|Greift auf das erste Element zu.|
|[list::insert (STL/CLR)](#insert)|Fügt Elemente an einer angegebenen Position hinzu.|
|[list::list (STL/CLR)](#list)|Erstellt ein container-Objekt.|
|[list::merge (STL/CLR)](#merge)|Führt zwei geordnete kontrollierte Sequenzen zusammen.|
|[list::pop_back (STL/CLR)](#pop_back)|Entfernt das letzte Element.|
|[list::pop_front (STL/CLR)](#pop_front)|Entfernt das erste Element.|
|[list::push_back (STL/CLR)](#push_back)|Fügt ein neues letztes Element hinzu.|
|[list::push_front (STL/CLR)](#push_front)|Fügt ein neues erstes Element hinzu.|
|[list::rbegin (STL/CLR)](#rbegin)|Legt den Anfang der umgekehrten kontrollierten Sequenz fest.|
|[list::remove (STL/CLR)](#remove)|Entfernt ein Element mit einem angegebenen Wert.|
|[list::remove_if (STL/CLR)](#remove_if)|Entfernt Elemente, die einen angegebenen Test bestehen.|
|[list::rend (STL/CLR)](#rend)|Legt das Ende der umgekehrten kontrollierten Sequenz fest.|
|[list::resize (STL/CLR)](#resize)|Ändert die Anzahl der Elemente.|
|[list::reverse (STL/CLR)](#reverse)|Kehrt die gesteuerte Sequenz um.|
|[list::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[list::sort (STL/CLR)](#sort)|Sortiert die kontrollierte Sequenz.|
|[list::splice (STL/CLR)](#splice)|Erneuert Links zwischen Knoten.|
|[list::swap (STL/CLR)](#swap)|Vertauscht den Inhalt von zwei Containern.|
|[list::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|
|[list::unique (STL/CLR)](#unique)|Entfernt benachbarte Elemente, die einen angegebenen Test bestehen.|

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|[list::back_item (STL/CLR)](#back_item)|Greift auf das letzte Element zu.|
|[list::front_item (STL/CLR)](#front_item)|Greift auf das erste Element zu.|

|Operator|Beschreibung|
|--------------|-----------------|
|[list::operator= (STL/CLR)](#op_as)|Ersetzt die kontrollierte Sequenz.|
|[operator!= (list) (STL/CLR)](#op_neq)|Bestimmt, ob ein-Objekt ungleich einem `list` anderen `list` Objekt ist.|
|[Operator< (Liste) (STL/CLR)](#op_lt)|Bestimmt, ob ein- `list` Objekt kleiner als ein anderes- `list` Objekt ist.|
|[Operator<= (List) (STL/CLR)](#op_lteq)|Bestimmt, ob ein- `list` Objekt kleiner als oder gleich einem anderen- `list` Objekt ist.|
|[Operator = = (List) (STL/CLR)](#op_eq)|Bestimmt, ob ein- `list` Objekt gleich einem anderen- `list` Objekt ist.|
|[Operator> (Liste) (STL/CLR)](#op_gt)|Bestimmt, ob ein- `list` Objekt größer als ein anderes- `list` Objekt ist.|
|[Operator>= (List) (STL/CLR)](#op_gteq)|Bestimmt, ob ein- `list` Objekt größer als oder gleich einem anderen- `list` Objekt ist.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|Beschreibung|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren eines Objekts.|
|<xref:System.Collections.IEnumerable>|Sequenzieren Sie Elemente.|
|<xref:System.Collections.ICollection>|Die Gruppe von Elementen wird beibehalten.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sequenz durch typisierte-Elemente.|
|<xref:System.Collections.Generic.ICollection%601>|Verwaltet eine Gruppe von typisierten Elementen.|
|IList\<Value>|Verwalten Sie einen generischen Container.|

## <a name="remarks"></a>Bemerkungen

Das-Objekt ordnet Speicher für die Sequenz zu, die er als einzelne Knoten in einer bidirektionalen Linkliste steuert und freigibt. Sie ordnet Elemente neu an, indem die Verknüpfungen zwischen den Knoten geändert werden, nie durch Kopieren des Inhalts eines Knotens in einen anderen. Dies bedeutet, dass Sie Elemente ohne Beeinträchtigung der restlichen Elemente frei einfügen und entfernen können. Daher ist eine Liste ein guter Kandidat für den zugrunde liegenden Container für die Vorlagen Klassen [Warteschlange (STL/CLR)](../dotnet/queue-stl-clr.md) oder den Vorlagen Klassen [Stapel (STL/CLR)](../dotnet/stack-stl-clr.md).

Ein- `list` Objekt unterstützt Bidirektionale Iteratoren. Dies bedeutet, dass Sie bei einem Iterator, der ein Element in der gesteuerten Sequenz festlegt, zu angrenzenden Elementen wechseln können. Ein spezieller Haupt Knoten entspricht dem Iterator, der von [List:: End (STL/CLR)](#end)zurückgegeben wurde `()` . Sie können diesen Iterator verringern, um das letzte Element in der kontrollierten Sequenz zu erreichen, falls vorhanden. Sie können einen Listeniterator erhöhen, um den Head-Knoten zu erreichen, und dann wird gleich verglichen `end()` . Sie können jedoch nicht den von zurückgegebenen Iterator dereferenzieren `end()` .

Beachten Sie, dass Sie nicht direkt mit der numerischen Position auf ein Listenelement verweisen können, das einen Iterator mit zufälligem Zugriff erfordert. Eine Liste kann daher *nicht* als zugrunde liegender Container für die Vorlagen Klasse [Priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)verwendet werden.

Ein Listeniterator speichert ein Handle für den zugeordneten Listen Knoten, der wiederum ein Handle für den zugehörigen Container speichert. Iteratoren können nur mit den zugehörigen Container Objekten verwendet werden. Ein Listeniterator bleibt gültig, solange der zugehörige Listen Knoten mit einer Liste verknüpft ist. Außerdem ist ein gültiger Iterator dereferencable--Sie können ihn verwenden, um auf den Elementwert zuzugreifen, den er festlegt, sofern er nicht gleich ist `end()` .

Durch das Löschen oder Entfernen eines Elements wird der Dekonstruktor für den gespeicherten Wert aufgerufen. Wenn Sie den Container zerstören, werden alle Elemente gelöscht. Daher stellt ein Container, dessen Elementtyp eine Verweis Klasse ist, sicher, dass keine Elemente den Container überdauern. Beachten Sie jedoch, dass ein Container von Handles seine Elemente *nicht* zerstört.

## <a name="members"></a>Members

## <a name="listassign-stlclr"></a><a name="assign"></a> List:: Assign (STL/CLR)

Ersetzt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parameter

*count*<br/>
Die Anzahl einzufügender Elemente.

*first*<br/>
Anfang des einzufügenden Bereichs.

*last*<br/>
Das Ende des einzufügenden Bereichs.

*Richting*<br/>
Enumeration, die eingefügt werden soll.

*ster*<br/>
Der Wert des einzufügenden Elements.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion ersetzt die gesteuerte Sequenz durch eine Wiederholung der *count* -Elemente des Werts *Val*. Sie verwenden Sie, um den Container mit Elementen auszufüllen, die alle denselben Wert aufweisen.

Wenn `InIt` ein ganzzahliger Typ ist, verhält sich die zweite Member-Funktion wie `assign((size_type)first, (value_type)last)` . Andernfalls wird die gesteuerte Sequenz durch die Sequenz [ `first` ,) ersetzt `last` . Damit wird die gesteuerte Sequenz zum Kopieren einer weiteren Sequenz verwendet.

Die dritte Element Funktion ersetzt die kontrollierte Sequenz durch die vom enumeratorrecht angegebene Sequenz *right*. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer Sequenz zu machen, die von einem Enumerator beschrieben wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_assign.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::list<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an iterator range
    cliext::list<wchar_t>::iterator it = c1.end();
    c2.assign(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="listback-stlclr"></a><a name="back"></a> List:: Back (STL/CLR)

Greift auf das letzte Element zu.

### <a name="syntax"></a>Syntax

```cpp
reference back();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf das letzte Element der kontrollierten Sequenz zurück, das nicht leer sein darf. Sie verwenden Sie, um auf das letzte Element zuzugreifen, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

    // alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
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

## <a name="listback_item-stlclr"></a><a name="back_item"></a> List:: back_item (STL/CLR)

Greift auf das letzte Element zu.

### <a name="syntax"></a>Syntax

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Bemerkungen

Die-Eigenschaft greift auf das letzte Element der kontrollierten Sequenz zu, das nicht leer sein darf. Sie verwenden Sie, um das letzte Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_back_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

    // alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
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

## <a name="listbegin-stlclr"></a><a name="begin"></a> List:: begin (STL/CLR)

Legt den Anfang der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator begin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Iterator mit zufälligem Zugriff zurück, der das erste Element der kontrollierten Sequenz oder direkt hinter das Ende einer leeren Sequenz festlegt. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_begin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="listclear-stlclr"></a><a name="clear"></a> List:: Clear (STL/CLR)

Entfernt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft effektiv [List:: Erase (STL/CLR)](#erase) `(` [List:: begin (STL/CLR)](#begin) `(),` [List:: End (STL/CLR)](#end)auf `())` . Sie verwenden ihn, um sicherzustellen, dass die gesteuerte Sequenz leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_clear.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="listconst_iterator-stlclr"></a><a name="const_iterator"></a> List:: const_iterator (STL/CLR)

Der Typ eines konstanten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T2` , das als konstanter Random-Access-Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_const_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listconst_reference-stlclr"></a><a name="const_reference"></a> List:: const_reference (STL/CLR)

Der Typ eines konstanten Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen konstanten Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_const_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::list<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a> List:: const_reverse_iterator (STL/CLR)

Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T4` , das als konstanter umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="listdifference_type-stlclr"></a><a name="difference_type"></a> List::d ifference_type (STL/CLR)

Die Typen eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Anzahl von signierten Elementen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_difference_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::difference_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="listempty-stlclr"></a><a name="empty"></a> List:: Empty (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Dies entspricht [List:: Size (STL/CLR)](#size) `() == 0` . Sie verwenden es, um zu testen, ob die Liste leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_empty.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.clear();
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

## <a name="listend-stlclr"></a><a name="end"></a> List:: End (STL/CLR)

Legt das Ende der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator end();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Iterator mit zufälligem Zugriff zurück, der auf das Ende der kontrollierten Sequenz verweist. Sie verwenden Sie, um einen Iterator abzurufen, der das Ende der kontrollierten Sequenz festlegt. der Status ändert sich nicht, wenn sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_end.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::list<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

    // alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="listerase-stlclr"></a><a name="erase"></a> List:: Erase (STL/CLR)

Entfernt Elemente an den angegebenen Positionen.

### <a name="syntax"></a>Syntax

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parameter

*first*<br/>
Anfang des Bereichs, der gelöscht werden soll.

*last*<br/>
Das Ende des zu löschenden Bereichs.

*where*<br/>
Zu Lösch Endes Element.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion entfernt das-Element der kontrollierten Sequenz, auf die von *Where*verwiesen wird. Sie verwenden es, um ein einzelnes Element zu entfernen.

Die zweite Memberfunktion entfernt die Elemente der gesteuerten Sequenz im Bereich [`first`, `last`). Sie verwenden Sie, um 0 (null) oder mehrere zusammenhängende Elemente zu entfernen.

Beide Member-Funktionen geben einen Iterator zurück, der das erste über die entfernten Elemente hinaus verbliebene Element festlegt, oder [List:: End (STL/CLR)](#end) , `()` Wenn kein solches Element vorhanden ist.

Beim Löschen von Elementen ist die Anzahl der Element Kopien in der Anzahl der Elemente zwischen dem Ende der Löschung und dem engeren Ende der Sequenz linear. (Wenn ein oder mehrere Elemente an beiden Enden der Sequenz gelöscht werden, treten keine Element Kopien auf.)

### <a name="example"></a>Beispiel

```cpp
// cliext_list_erase.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    cliext::list<wchar_t>::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="listfront-stlclr"></a><a name="front"></a> List:: Front (STL/CLR)

Greift auf das erste Element zu.

### <a name="syntax"></a>Syntax

```cpp
reference front();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf das erste Element der kontrollierten Sequenz zurück, das nicht leer sein darf. Sie verwenden Sie, um das erste Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

    // alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
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

## <a name="listfront_item-stlclr"></a><a name="front_item"></a> List:: front_item (STL/CLR)

Greift auf das erste Element zu.

### <a name="syntax"></a>Syntax

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Bemerkungen

Die-Eigenschaft greift auf das erste Element der kontrollierten Sequenz zu, das nicht leer sein darf. Sie verwenden Sie, um das erste Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_front_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

    // alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
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

## <a name="listgeneric_container-stlclr"></a><a name="generic_container"></a> List:: generic_container (STL/CLR)

Der Typ der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::
    IList<generic_value>
    generic_container;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt die generische Schnittstelle für diese Vorlagen Container Klasse.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_generic_container.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
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

## <a name="listgeneric_iterator-stlclr"></a><a name="generic_iterator"></a> List:: generic_iterator (STL/CLR)

Der Typ eines Iterators, der mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen generischen Iterator, der mit der generischen-Schnittstelle für diese Vorlagen Container Klasse verwendet werden kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_generic_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="listgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a> List:: generic_reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators, der mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen generischen umgekehrten Iterator, der mit der generischen-Schnittstelle für diese Vorlagen Container Klasse verwendet werden kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="listgeneric_value-stlclr"></a><a name="generic_value"></a> List:: generic_value (STL/CLR)

Der Typ eines Elements, das mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt vom Typ `GValue` , das den gespeicherten Elementwert zur Verwendung mit der generischen-Schnittstelle für diese Vorlagen Container Klasse beschreibt.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_generic_value.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="listinsert-stlclr"></a><a name="insert"></a> List:: Insert (STL/CLR)

Fügt Elemente an einer angegebenen Position hinzu.

### <a name="syntax"></a>Syntax

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parameter

*count*<br/>
Die Anzahl einzufügender Elemente.

*first*<br/>
Anfang des einzufügenden Bereichs.

*last*<br/>
Das Ende des einzufügenden Bereichs.

*Richting*<br/>
Enumeration, die eingefügt werden soll.

*ster*<br/>
Der Wert des einzufügenden Elements.

*where*<br/>
WHERE in Container, der vor eingefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Jede der Member-Funktionen fügt vor dem Element, auf das von *Where* in der gesteuerten Sequenz verwiesen wird, eine Sequenz ein, die von den verbleibenden Operanden angegeben wird.

Die erste Member-Funktion fügt ein Element mit dem Wert *Val* ein und gibt einen Iterator zurück, der das neu eingefügte Element festlegt. Sie verwenden es, um ein einzelnes Element vor einem von einem Iterator festgelegten Speicherort einzufügen.

Die zweite Member-Funktion fügt eine Wiederholung der *count* -Elemente des Werts *Val*ein. Sie verwenden Sie, um 0 (null) oder mehrere zusammenhängende Elemente einzufügen, die alle Kopien desselben Werts sind.

Wenn `InIt` ein Ganzzahltyp ist, verhält sich die dritte Memberfunktion genau wie `insert(where, (size_type)first, (value_type)last)`. Andernfalls wird die Sequenz [ `first` ,) eingefügt `last` . Sie verwenden Sie, um NULL oder mehrere zusammenhängende Elemente einzufügen, die aus einer anderen Sequenz kopiert werden.

Die vierte Member-Funktion fügt die von der *rechten Seite*festgelegte Sequenz ein. Sie verwenden Sie zum Einfügen einer Sequenz, die von einem Enumerator beschrieben wird.

Beim Einfügen eines einzelnen Elements ist die Anzahl der Element Kopien in der Anzahl der Elemente zwischen der Einfügemarke und dem engeren Ende der Sequenz linear. (Beim Einfügen eines oder mehrerer Elemente an beiden Enden der Sequenz werden keine Element Kopien durchzuführen.) Wenn `InIt` ein eingabeiterator ist, führt die dritte Member-Funktion für jedes Element in der Sequenz eine einzelne Einfügung aus. Andernfalls ist beim Einfügen `N` von Elementen die Anzahl der Element Kopien linear in `N` zuzüglich der Anzahl der Elemente zwischen der Einfügemarke und dem engeren Ende der Sequenz.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_insert.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::list<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using index
    it = c2.begin();
    ++it, ++it, ++it;
    c2.insert(it, L'z');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="listiterator-stlclr"></a><a name="iterator"></a> List:: Iterator (STL/CLR)

Der Typ eines Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T1` , das als Iterator mit zufälligem Zugriff für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

    // alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="listlist-stlclr"></a><a name="list"></a> List:: List (STL/CLR)

Erstellt ein container-Objekt.

### <a name="syntax"></a>Syntax

```cpp
list();
list(list<Value>% right);
list(list<Value>^ right);
explicit list(size_type count);
list(size_type count, value_type val);
template<typename InIt>
    list(InIt first, InIt last);
list(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parameter

*count*<br/>
Die Anzahl einzufügender Elemente.

*first*<br/>
Anfang des einzufügenden Bereichs.

*last*<br/>
Das Ende des einzufügenden Bereichs.

*Richting*<br/>
Einzufügendes Objekt bzw. einzufügender Bereich.

*ster*<br/>
Der Wert des einzufügenden Elements.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`list();`

Initialisiert die gesteuerte Sequenz ohne Elemente. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz anzugeben.

Der Konstruktor:

`list(list<Value>% right);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [ `right.begin()` , `right.end()` ). Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom Listen Objekt *Rechts*gesteuert wird.

Der Konstruktor:

`list(list<Value>^ right);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [ `right->begin()` , `right->end()` ). Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom Listen Objekt gesteuert wird, dessen Handle *richtig*ist.

Der Konstruktor:

`explicit list(size_type count);`

Initialisiert die gesteuerte Sequenz mit *count* -Elementen, die jeweils den Wert haben `value_type()` . Sie verwenden Sie, um den Container mit Elementen auszufüllen, die alle den Standardwert aufweisen.

Der Konstruktor:

`list(size_type count, value_type val);`

Initialisiert die gesteuerte Sequenz mit *count* -Elementen mit dem Wert *Val*. Sie verwenden Sie, um den Container mit Elementen auszufüllen, die alle denselben Wert aufweisen.

Der Konstruktor:

`template<typename InIt>`

`list(InIt first, InIt last);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [ `first` , `last` ). Sie verwenden ihn, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen.

Der Konstruktor:

`list(System::Collections::Generic::IEnumerable<Value>^ right);`

Initialisiert die gesteuerte Sequenz mit der vom enumeratorrecht angegebenen Sequenz *right*. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator beschrieben wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_construct.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::list<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::list<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::list<wchar_t>::iterator it = c3.end();
    cliext::list<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::list<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::list<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="listmerge-stlclr"></a><a name="merge"></a> List:: Merge (STL/CLR)

Führt zwei geordnete kontrollierte Sequenzen zusammen.

### <a name="syntax"></a>Syntax

```cpp
void merge(list<Value>% right);
template<typename Pred2>
    void merge(list<Value>% right, Pred2 pred);
```

#### <a name="parameters"></a>Parameter

*pred*<br/>
Vergleich für Element Paare.

*Richting*<br/>
Container für die Zusammenführung

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion entfernt alle Elemente aus der von *right* kontrollierten Sequenz und fügt Sie in die gesteuerte Sequenz ein. Beide Sequenzen müssen zuvor nach geordnet werden,- `operator<` -Elemente dürfen den Wert nicht verringern, während Sie durch eine der beiden Sequenzen fortgeführt werden. Die resultierende Sequenz wird auch nach geordnet `operator<` . Mit dieser Member-Funktion können Sie zwei Sequenzen zusammenführen, die den Wert in eine Sequenz vergrößern, die ebenfalls den Wert erhöht.

Die zweite Member-Funktion verhält sich wie die erste, mit der Ausnahme, dass die Sequenzen nach dem-Element `pred`  --  `pred(X, Y)` `X` `Y` in der Sequenz nach "false" lauten müssen. Sie verwenden Sie, um zwei Sequenzen zu zusammenführen, die nach einer Prädikat Funktion oder einem von Ihnen angegebenen Delegaten geordnet sind.

Beide Funktionen führen einen stabilen Merge aus. es werden keine Element Paare in einer der ursprünglich kontrollierten Sequenzen in der resultierenden gesteuerten Sequenz umgekehrt. Wenn ein paar von Elementen `X` und `Y` in der resultierenden gesteuerten Sequenz eine entsprechende Reihenfolge aufweist, wird `!(X < Y) && !(X < Y)` ein Element aus der ursprünglichen kontrollierten Sequenz vor einem Element aus der Sequenz angezeigt, die von *Rechts*gesteuert wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_merge.cpp
// compile with: /clr
#include <cliext/list>

typedef cliext::list<wchar_t> Mylist;
int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'c');
    c1.push_back(L'e');

    // display initial contents " a c e"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    cliext::list<wchar_t> c2;
    c2.push_back(L'b');
    c2.push_back(L'd');
    c2.push_back(L'f');

    // display initial contents " b d f"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // merge and display
    cliext::list<wchar_t> c3(c1);
    c3.merge(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());

    // sort descending, merge descending, and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.merge(c1, cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    return (0);
    }
```

```Output
a c e
b d f
a b c d e f
c2.size() = 0
e c a
f e d c b a
f e e d c c b a a
c1.size() = 0
```

## <a name="listoperator-stlclr"></a><a name="op_as"></a> List:: Operator = (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```
list<Value>% operator=(list<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Der zu kopierende Container.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann zurück **`*this`** . Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_operator_as.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="listpop_back-stlclr"></a><a name="pop_back"></a> List::p op_back (STL/CLR)

Entfernt das letzte Element.

### <a name="syntax"></a>Syntax

```cpp
void pop_back();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entfernt das letzte Element der kontrollierten Sequenz, das nicht leer sein darf. Sie verwenden Sie, um die Liste um ein Element auf der Rückseite zu verkürzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_pop_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="listpop_front-stlclr"></a><a name="pop_front"></a> List::p op_front (STL/CLR)

Entfernt das erste Element.

### <a name="syntax"></a>Syntax

```cpp
void pop_front();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entfernt das erste Element der kontrollierten Sequenz, das nicht leer sein darf. Sie verwenden Sie, um die Liste um ein Element im Vordergrund zu verkürzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_pop_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_front();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="listpush_back-stlclr"></a><a name="push_back"></a> List::p ush_back (STL/CLR)

Fügt ein neues letztes Element hinzu.

### <a name="syntax"></a>Syntax

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion fügt ein Element mit `val` dem Wert am Ende der kontrollierten Sequenz ein. Sie verwenden es, um ein weiteres Element an die Liste anzufügen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_push_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="listpush_front-stlclr"></a><a name="push_front"></a> List::p ush_front (STL/CLR)

Fügt ein neues erstes Element hinzu.

### <a name="syntax"></a>Syntax

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion fügt ein Element mit einem Wert `val` am Anfang der kontrollierten Sequenz ein. Sie verwenden Sie, um der Liste ein weiteres Element hinzufügen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_push_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_front(L'a');
    c1.push_front(L'b');
    c1.push_front(L'c');

    // display contents " c b a"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="listrbegin-stlclr"></a><a name="rbegin"></a> List:: rbegin (STL/CLR)

Legt den Anfang der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen reverse-Iterator zurück, der das letzte Element der kontrollierten Sequenz festlegt, oder direkt hinter dem Anfang einer leeren Sequenz. Demzufolge wird der `beginning` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_rbegin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="listreference-stlclr"></a><a name="reference"></a> List:: Reference (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="listremove-stlclr"></a><a name="remove"></a> List:: Remove (STL/CLR)

Entfernt ein Element mit einem angegebenen Wert.

### <a name="syntax"></a>Syntax

```cpp
void remove(value_type val);
```

#### <a name="parameters"></a>Parameter

*ster*<br/>
Der Wert des zu entfernenden Elements.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entfernt ein Element in der kontrollierten Sequenz, für das `((System::Object^)val)->Equals((System::Object^)x)` true ist (sofern vorhanden). Sie verwenden Sie zum Löschen eines beliebigen Elements mit dem angegebenen Wert.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_remove.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove(L'A');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove(L'b');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c
```

## <a name="listremove_if-stlclr"></a><a name="remove_if"></a> List:: remove_if (STL/CLR)

Entfernt Elemente, die einen angegebenen Test bestehen.

### <a name="syntax"></a>Syntax

```cpp
template<typename Pred1>
    void remove_if(Pred1 pred);
```

#### <a name="parameters"></a>Parameter

*pred*<br/>
Testet, welche Elemente entfernt werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entfernt alle Elemente aus der kontrollierten Sequenz (erases) `X` , für die " `pred(X)` true" ist. Sie verwenden Sie, um alle Elemente zu entfernen, die eine Bedingung erfüllen, die Sie als Funktion oder Delegat angeben.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_remove_if.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b b b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(
        cliext::equal_to<wchar_t>(), L'd'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(
        cliext::not_equal_to<wchar_t>(), L'b'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b b b c
a b b b c
b b b
```

## <a name="listrend-stlclr"></a><a name="rend"></a> List:: rend (STL/CLR)

Legt das Ende der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen reverse-Iterator zurück, der direkt hinter den Anfang der kontrollierten Sequenz verweist. Demzufolge wird der `end` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der das `current` Ende der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_rend.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

    // alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="listresize-stlclr"></a><a name="resize"></a> List:: Resize (STL/CLR)

Ändert die Anzahl der Elemente.

### <a name="syntax"></a>Syntax

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Parameter

*new_size*<br/>
Die neue Größe der kontrollierten Sequenz.

*ster*<br/>
Der Wert des Auffüllung-Elements.

### <a name="remarks"></a>Bemerkungen

Mit den Element Funktionen wird sichergestellt, dass [List:: Size (STL/CLR)](#size) nach wie vor `()` *new_size*zurückgibt. Wenn die gesteuerte Sequenz länger dauern muss, fügt die erste Member-Funktion Elemente mit einem Wert an `value_type()` , während die zweite Element Funktion Elemente mit dem Wert *Val*anfügt. Damit die gesteuerte Sequenz kürzer wird, löschen beide Element Funktionen die letzten Elemente der [Liste:: Size (STL/CLR)](#size) `() -` `new_size` . Sie verwenden diese Option, um sicherzustellen, dass die Größe der kontrollierten Sequenz *new_size*ist, indem Sie die aktuelle gesteuerte Sequenz kürzen oder Auffüllen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_resize.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container and pad with default values
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

    // resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="listreverse-stlclr"></a><a name="reverse"></a> List:: Reverse (STL/CLR)

Kehrt die gesteuerte Sequenz um.

### <a name="syntax"></a>Syntax

```cpp
void reverse();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion kehrt die Reihenfolge aller Elemente in der gesteuerten Sequenz um. Sie verwenden Sie, um eine Liste von Elementen widerzuspiegeln.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_reverse.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // reverse and redisplay
    c1.reverse();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
```

## <a name="listreverse_iterator-stlclr"></a><a name="reverse_iterator"></a> List:: reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T3` , das als umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

    // alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="listsize-stlclr"></a><a name="size"></a> List:: Size (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden Sie, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden. Wenn Sie nur für Sie wichtig sind, ob die Sequenz eine Größe ungleich NULL aufweist, finden Sie weitere Informationen unter [List:: Empty (STL/CLR)](#empty) `()` .

### <a name="example"></a>Beispiel

```cpp
// cliext_list_size.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="listsize_type-stlclr"></a><a name="size_type"></a> List:: size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_size_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::size_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="listsort-stlclr"></a><a name="sort"></a> List:: Sort (STL/CLR)

Sortiert die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
void sort();
template<typename Pred2>
    void sort(Pred2 pred);
```

#### <a name="parameters"></a>Parameter

*pred*<br/>
Vergleich für Element Paare.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion ordnet die Elemente in der gesteuerten Sequenz so an, dass Sie nach `operator<` ---Elementen nicht in den Wert sinken, wenn Sie durch die Sequenz fortgeführt werden. Mit dieser Member-Funktion Sortieren Sie die Sequenz in aufsteigender Reihenfolge.

Die zweite Member-Funktion verhält sich wie die erste, mit der Ausnahme, dass die Sequenz nach dem-Element `pred`  --  `pred(X, Y)` false ist, wenn es sich um ein beliebiges Element handelt, `X` das `Y` in der resultierenden Sequenz auf Sie verwenden Sie, um die Sequenz in einer Reihenfolge zu sortieren, die Sie durch eine Prädikat Funktion oder einen Delegaten angeben.

Beide Funktionen führen eine stabile Sortierung durch. in der resultierenden gesteuerten Sequenz wird kein Element Paar in der ursprünglichen gesteuerten Sequenz umgekehrt.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_sort.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort descending and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort ascending and redisplay
    c1.sort();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
a b c
```

## <a name="listsplice-stlclr"></a><a name="splice"></a> List:: splice (STL/CLR)

Verknüpfungen zwischen Knoten neu anheften.

### <a name="syntax"></a>Syntax

```cpp
void splice(iterator where, list<Value>% right);
void splice(iterator where, list<Value>% right,
    iterator first);
void splice(iterator where, list<Value>% right,
    iterator first, iterator last);
```

#### <a name="parameters"></a>Parameter

*first*<br/>
Anfang des Bereichs, der zusammengeführt werden soll.

*last*<br/>
Das Ende des Bereichs, der zusammengeführt werden soll.

*Richting*<br/>
Der Container, von dem aus ein Splice-

*where*<br/>
WHERE in Container to splice before.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion fügt die Sequenz, die von gesteuert wird, vor dem Element in der kontrollierten Sequenz ein, auf das von *Where* *verwiesen wird.* Außerdem werden alle Elemente von *Rechts*entfernt. ( `%right` darf nicht gleich sein **`this`** .) Sie verwenden Sie, um alle Listen in eine andere Liste aufzurufenden.

Die zweite Member-Funktion entfernt das Element, auf das *zuerst* in der von *right* kontrollierten Sequenz verwiesen wird, und fügt es vor dem Element in der kontrollierten Sequenz ein, auf das von *Where*verwiesen wird. (Wenn `where` `==` `first` `||` `where` `== ++first`, es findet keine Änderung statt.) Sie verwenden Sie, um ein einzelnes Element einer Liste in eine andere Liste aufzurufenden.

Die dritte Member-Funktion fügt den von [,) festgelegten durch [ `first` , `last` ) aus der *right* Sequenz ein, die von der Sequenz gesteuert wird, die *where*von der-Position gesteuert wird. Außerdem wird der ursprüngliche Unterbereich aus der von *Rechts*kontrollierten Sequenz entfernt. (Wenn `right == this` , darf der Bereich [ `first` , `last` ) nicht das Element enthalten, auf das von *Where*verwiesen wird.) Sie verwenden Sie, um eine unter Sequenz von NULL oder mehr Elementen aus einer Liste in eine andere aufzurufenden.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_splice.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // splice to a new list
    cliext::list<wchar_t> c2;
    c2.splice(c2.begin(), c1);
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return one element
    c1.splice(c1.end(), c2, c2.begin());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return remaining elements
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());
    return (0);
    }
```

```Output
a b c
c1.size() = 0
a b c
a
b c
b c a
c2.size() = 0
```

## <a name="listswap-stlclr"></a><a name="swap"></a> List:: Swap (STL/CLR)

Vertauscht den Inhalt von zwei Containern.

### <a name="syntax"></a>Syntax

```cpp
void swap(list<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Container für den Tausch von Inhalten.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht die kontrollierten Sequenzen zwischen **`*this`** und *Rechts*aus. Dies erfolgt in konstanter Zeit und löst keine Ausnahmen aus. Sie verwenden Sie als schnelle Möglichkeit, um den Inhalt von zwei Containern auszutauschen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_swap.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::list<wchar_t> c2(5, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="listto_array-stlclr"></a><a name="to_array"></a> List:: to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein Array mit der kontrollierten Sequenz zurück. Sie verwenden Sie, um eine Kopie der kontrollierten Sequenz in Array Form abzurufen.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_to_array.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
    for each (wchar_t elem in c1)
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

## <a name="listunique-stlclr"></a><a name="unique"></a> List:: Unique (STL/CLR)

Entfernt benachbarte Elemente, die einen angegebenen Test bestehen.

### <a name="syntax"></a>Syntax

```cpp
void unique();
template<typename Pred2>
    void unique(Pred2 pred);
```

#### <a name="parameters"></a>Parameter

*pred*<br/>
Vergleich für Element Paare.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion entfernt jedes Element aus der kontrollierten Sequenz (erases), das mit dem vorangehenden Element übereinstimmt, `X` `Y` und `X == Y` die Element Funktion entfernt `Y` . Sie verwenden Sie, um alle bis auf eine Kopie jeder unter Sequenz benachbarter Elemente zu entfernen, die gleich sind. Beachten Sie Folgendes: Wenn die gesteuerte Sequenz sortiert ist, z. b. durch Aufrufen von [List:: Sort (STL/CLR)](#sort) `()` , gibt die Member-Funktion nur Elemente mit eindeutigen Werten aus. (Sie beenden – englisch: to terminate – die Abfrage, daher der Name.)

Die zweite Member-Funktion verhält sich wie die erste, mit der Ausnahme, dass Sie jedes Element `Y` nach einem Element entfernt, `X` für das `pred(X, Y)` . Sie verwenden Sie, um alle bis auf eine Kopie jeder unter Sequenz angrenzender Elemente zu entfernen, die eine Prädikat Funktion oder einen von Ihnen angegebenen Delegaten erfüllen. Beachten Sie Folgendes: Wenn die gesteuerte Sequenz geordnet ist, z. b. durch Aufrufen von, gibt die Member-Funktion nur Elemente aus, für die keine `sort(pred)` äquivalente Reihenfolge mit anderen Elementen vorliegt.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_unique.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique
    cliext::list<wchar_t> c2(c1);
    c2.unique();
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique(not_equal_to)
    c2 = c1;
    c2.unique(cliext::not_equal_to<wchar_t>());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a a b c
a b c
a a
```

## <a name="listvalue_type-stlclr"></a><a name="value_type"></a> List:: value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter *Wert*.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_value_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::list<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-list-stlclr"></a><a name="op_neq"></a> Operator! = (List) (STL/CLR)

Die Liste entspricht nicht dem Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator!=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator Funktion gibt zurück `!(left == right)` . Sie verwenden es, um zu testen, ob *left* nicht identisch ist *, wenn die* beiden Listenelement Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_operator_ne.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
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

## <a name="operatorlt-list-stlclr"></a><a name="op_lt"></a> Operator &lt; (List) (STL/CLR)

Liste kleiner als-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator<(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt true zurück, wenn für die niedrigste Position, `i` für die `!(right[i] < left[i])` Sie ebenfalls true ist `left[i] < right[i]` . Andernfalls wird zurückgegeben, `left->size() < right->size()` um zu testen, ob *left* nach *Rechts* geordnet ist, wenn die beiden Listenelement Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_operator_lt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
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

## <a name="operatorlt-list-stlclr"></a><a name="op_lteq"></a> Operator &lt; = (List) (STL/CLR)

Liste kleiner oder gleich-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator<=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator Funktion gibt zurück `!(right < left)` . Sie verwenden es, um zu testen, ob *left* nach *Rechts* nicht geordnet ist, wenn die beiden Listenelement Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_operator_le.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
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

## <a name="operator-list-stlclr"></a><a name="op_eq"></a> Operator = = (List) (STL/CLR)

Auflisten des gleichen Vergleichs.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator==(list<Value>% left,
        list<Value>% right);
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
// cliext_list_operator_eq.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
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

## <a name="operatorgt-list-stlclr"></a><a name="op_gt"></a> Operator &gt; (List) (STL/CLR)

Die Liste ist größer als der Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator>(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator Funktion gibt zurück `right` `<` `left` . Sie verwenden es, um zu testen, ob *Links* nach *Rechts* angeordnet ist, wenn die beiden Listenelement Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_operator_gt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
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

## <a name="operatorgt-list-stlclr"></a><a name="op_gteq"></a> Operator &gt; = (List) (STL/CLR)

Liste größer oder gleich-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator>=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parameter

*linken*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator Funktion gibt zurück `!(left` `<` `right)` . Sie verwenden es, um zu testen, ob *left* nicht vor *Rechts* geordnet ist, wenn die beiden Listenelement Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_list_operator_ge.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

    // display contents " a b d"
    for each (wchar_t elem in c2)
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
