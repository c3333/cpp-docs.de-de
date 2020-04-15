---
title: vector (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
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
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
ms.openlocfilehash: c6a001797e90bd7381358abb16612926442e8d9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371818"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

Die Vorlagenklasse beschreibt ein Objekt, das eine Sequenz unterschiedlicher Länge von Elementen mit zufälligem Zugriff steuert. Sie verwenden `vector` den Container, um eine Abfolge von Elementen als zusammenhängenden Speicherblock zu verwalten. Der Block wird als Array implementiert, das bei Bedarf wächst.

In der beschreibung `GValue` unten ist die gleiche wie *Wert,* es sei `Value^`denn, letztere ist ein ref-Typ, in diesem Fall ist es .

## <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    ref class vector
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IVector<GValue>
    { ..... };
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Der Typ eines Elements in der kontrollierten Sequenz.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<cliext/vector>

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|[vector::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.|
|[vector::difference_type (STL/CLR)](#difference_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[vector::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container.|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|Der Typ eines Iterators für die generische Schnittstelle für den Container.|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Der Typ eines umgekehrten Iterators für die generische Schnittstelle für den Container.|
|[vector::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container.|
|[vector::iterator (STL/CLR)](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[vector::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.|
|[vector::size_type (STL/CLR)](#size_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[vector::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[vector::assign (STL/CLR)](#assign)|Ersetzt alle Elemente.|
|[vector::at (STL/CLR)](#at)|Greift auf ein Element an einer angegebenen Position zu.|
|[vector::back (STL/CLR)](#back)|Greift auf das letzte Element zu.|
|[vector::begin (STL/CLR)](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[vector::capacity (STL/CLR)](#capacity)|Ermittelt die Größe des zugeordneten Speichers für den Container.|
|[vector::clear (STL/CLR)](#clear)|Entfernt alle Elemente.|
|[vector::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[vector::end (STL/CLR)](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[vector::erase (STL/CLR)](#erase)|Entfernt Elemente an den angegebenen Positionen.|
|[vector::front (STL/CLR)](#front)|Greift auf das erste Element zu.|
|[vector::insert (STL/CLR)](#insert)|Fügt Elemente an einer angegebenen Position hinzu.|
|[vector::pop_back (STL/CLR)](#pop_back)|Entfernt das letzte Element.|
|[vector::push_back (STL/CLR)](#push_back)|Fügt ein neues letztes Element hinzu.|
|[vector::rbegin (STL/CLR)](#rbegin)|Legt den Anfang der umgekehrten kontrollierten Sequenz fest.|
|[vector::rend (STL/CLR)](#rend)|Legt das Ende der umgekehrten kontrollierten Sequenz fest.|
|[vector::reserve (STL/CLR)](#reserve)|Gewährleistet eine minimale Wachstumskapazität für den Container.|
|[vector::resize (STL/CLR)](#resize)|Ändert die Anzahl der Elemente.|
|[vector::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[vector::swap (STL/CLR)](#swap)|Vertauscht den Inhalt von zwei Containern.|
|[vector::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|
|[vector::vector (STL/CLR)](#vector)|Erstellt ein container-Objekt.|

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|Greift auf das letzte Element zu.|
|[vector::front_item (STL/CLR)](#front_item)|Greift auf das erste Element zu.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|Ersetzt die kontrollierte Sequenz.|
|[vector::operator(STL/CLR)](#op)|Greift auf ein Element an einer angegebenen Position zu.|
|[Operator!= (Vektor) (STL/CLR)](#op_neq)|Bestimmt, `vector` ob ein Objekt `vector` nicht mit einem anderen Objekt gleich ist.|
|[Operator< (Vektor) (STL/CLR)](#op_lt)|Bestimmt, `vector` ob ein Objekt `vector` kleiner als ein anderes Objekt ist.|
|[Operator<= (Vektor) (STL/CLR)](#op_lteq)|Bestimmt, `vector` ob ein Objekt kleiner `vector` oder gleich einem anderen Objekt ist.|
|[Operator == (Vektor) (STL/CLR)](#op_eq)|Bestimmt, `vector` ob ein Objekt `vector` einem anderen Objekt gleich ist.|
|[Operator> (Vektor) (STL/CLR)](#op_gt)|Bestimmt, `vector` ob ein Objekt `vector` größer als ein anderes Objekt ist.|
|[operator>= (vector) (STL/CLR)](#op_gteq)|Bestimmt, `vector` ob ein Objekt größer `vector` oder gleich einem anderen Objekt ist.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren Sie ein Objekt.|
|<xref:System.Collections.IEnumerable>|Sequenz durch Elemente.|
|<xref:System.Collections.ICollection>|Verwalten Sie eine Gruppe von Elementen.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sequenz durch typisierte Elemente.|
|<xref:System.Collections.Generic.ICollection%601>|Verwalten Sie eine Gruppe typisierter Elemente.|
|<xref:System.Collections.Generic.IList%601>|Bestellte Gruppe von typisierten Elementen beibehalten.|
|IVector<Wert\>|Verwalten Sie generische Container.|

## <a name="remarks"></a>Bemerkungen

Das Objekt reserviert und gibt Speicher für die Sequenz frei, die es über ein gespeichertes Array von *Value-Elementen* steuert, das bei Bedarf wächst. Das Wachstum erfolgt so, dass die Kosten für das Anfügen eines neuen Elements konstante Zeit amortisiert werden. Mit anderen Worten, die Kosten für das Hinzufügen von Elementen am Ende steigen im Durchschnitt nicht, da die Länge der gesteuerten Sequenz größer wird. Daher ist ein Vektor ein guter Kandidat für den zugrunde liegenden Container für Template Class [Stack (STL/CLR)](../dotnet/stack-stl-clr.md).

A `vector` unterstützt Iteratoren mit zufälligem Zugriff, d. h., Sie können auf ein Element direkt `size() - 1` mit seiner numerischen Position verweisen, wobei von Null für das erste (vordere) Element bis zum letzten (Rücken-)Element gezählt werden kann. Es bedeutet auch, dass ein Vektor ein guter Kandidat für den zugrunde liegenden Container für die Vorlagenklasse [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)ist.

Ein Vektoriterator speichert ein Handle in seinem zugeordneten Vektorobjekt zusammen mit der Verzerrung des Elements, das er bestimmt. Sie können Iteratoren nur mit den zugehörigen Containerobjekten verwenden. Die Verzerrung eines Vektorelements ist die gleiche wie seine Position.

Das Einfügen oder Löschen von Elementen kann den an einer bestimmten Position gespeicherten Elementwert ändern, sodass sich auch der von einem Iterator angegebene Wert ändern kann. (Der Container muss möglicherweise Elemente nach oben oder unten kopieren, um eine Bohrung vor einem Einfügen zu erstellen oder eine Bohrung nach einem Löschen zu füllen.) Dennoch bleibt ein Vektoriterator gültig, solange seine `[0, size()]`Voreingenommenheit im Bereich liegt. Darüber hinaus bleibt ein gültiger Iterator dereferencable -- Sie können ihn verwenden, um auf den von `size()`ihm bezeichneten Elementwert zuzugreifen oder ihn zu ändern -- solange seine Verzerrung nicht gleich ist.

Durch das Löschen oder Entfernen eines Elements wird der Destruktor für seinen gespeicherten Wert aufgesucht. Durch das Zerstören des Containers werden alle Elemente ausdemaiert. Daher stellt ein Container, dessen Elementtyp eine ref-Klasse ist, sicher, dass keine Elemente den Container überdauern. Beachten Sie jedoch, dass ein Container mit Handles seine Elemente nicht zerstört.

## <a name="members"></a>Member

## <a name="vectorassign-stlclr"></a><a name="assign"></a>vektor::zuweisen (STL/CLR)

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
Ende des einzufügenden Bereichs.

*Richting*<br/>
Enumeration, die eingefügt werden soll.

*Val*<br/>
Wert des einzufügenden Elements.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion ersetzt die gesteuerte Sequenz durch eine Wiederholung von *Zählelementen* des *Werts val*. Sie verwenden es, um den Container mit Elementen zu füllen, die alle den gleichen Wert haben.

Wenn `InIt` es sich um einen ganzzahligen Typ handelt, `assign((size_type)first, (value_type)last)`verhält sich die zweite Memberfunktion wie . Andernfalls ersetzt es die gesteuerte Sequenz`first` `last`durch die Sequenz [ , ). Sie verwenden es, um die gesteuerte Sequenz zu einer anderen Sequenz zu machen.

Die dritte Memberfunktion ersetzt die gesteuerte Sequenz durch die *right*Sequenz, die vom Enumeratorrecht bestimmt wird. Sie verwenden sie, um die gesteuerte Sequenz zu einer Kopie einer Sequenz zu machen, die von einem Enumerator beschrieben wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_assign.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// assign a repetition of values
    cliext::vector<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an iterator range
    c2.assign(c1.begin(), c1.end() - 1);
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

## <a name="vectorat-stlclr"></a><a name="at"></a>vektor::at (STL/CLR)

Greift auf ein Element an einer angegebenen Position zu.

### <a name="syntax"></a>Syntax

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Parameter

*Pos*<br/>
Position des Elements, auf das zugegriffen wird

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Verweis auf das Element der gesteuerten Sequenz an position *pos zurück.* Sie verwenden es, um ein Element zu lesen oder zu schreiben, dessen Position Sie kennen.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_at.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using at
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// change an entry and redisplay
    c1.at(1) = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorback-stlclr"></a><a name="back"></a>Vektor::zurück (STL/CLR)

Greift auf das letzte Element zu.

### <a name="syntax"></a>Syntax

```cpp
reference back();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Verweis auf das letzte Element der gesteuerten Sequenz zurück, das nicht leer sein muss. Sie verwenden es, um auf das letzte Element zuzugreifen, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorback_item-stlclr"></a><a name="back_item"></a>Vektor::back_item (STL/CLR)

Greift auf das letzte Element zu.

### <a name="syntax"></a>Syntax

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Bemerkungen

Die Eigenschaft greift auf das letzte Element der gesteuerten Sequenz zu, das nicht leer sein muss. Sie verwenden es, um das letzte Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_back_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorbegin-stlclr"></a><a name="begin"></a>Vektor::begin (STL/CLR)

Legt den Anfang der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator begin();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Iterator mit zufälligem Zugriff zurück, der das erste Element der gesteuerten Sequenz oder knapp über das Ende einer leeren Sequenz hinaus bezeichnet. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_begin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::iterator it = c1.begin();
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

## <a name="vectorcapacity-stlclr"></a><a name="capacity"></a>Vektor::Kapazität (STL/CLR)

Ermittelt die Größe des zugeordneten Speichers für den Container.

### <a name="syntax"></a>Syntax

```cpp
size_type capacity();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt den Speicher zurück, der derzeit für die gesteuerte Sequenz reserviert ist, ein Wert, der mindestens so groß ist wie [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Sie verwenden ihn, um zu bestimmen, wie viel der Container wachsen kann, bevor er Speicher für die gesteuerte Sequenz neu zuordnen muss.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_capacity.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorclear-stlclr"></a><a name="clear"></a>Vektor::klar (STL/CLR)

Entfernt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft effektiv [vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)`())`auf. Sie verwenden es, um sicherzustellen, dass die gesteuerte Sequenz leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_clear.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorconst_iterator-stlclr"></a><a name="const_iterator"></a>Vektor::const_iterator (STL/CLR)

Der Typ eines konstanten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt `T2` unbestimmten Typs, das als konstanter Iterator mit zufälligem Zugriff für die gesteuerte Sequenz dienen kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_const_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reference-stlclr"></a><a name="const_reference"></a>Vektor::const_reference (STL/CLR)

Der Typ eines konstanten Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen konstanten Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_const_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::vector<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>Vektor::const_reverse_iterator (STL/CLR)

Der Typ eines konstanten Umgekehrtitators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt `T4` unbestimmten Typs, das als konstanter umgekehrter Iterator für die gesteuerte Sequenz dienen kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="vectordifference_type-stlclr"></a><a name="difference_type"></a>vektor::difference_type (STL/CLR)

Die Typen eines signierten Abstands zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine signierte Elementanzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_difference_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::difference_type diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorempty-stlclr"></a><a name="empty"></a>vektor::leer (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Es entspricht [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`. Sie verwenden es, um zu testen, ob der Vektor leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_empty.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorend-stlclr"></a><a name="end"></a>Vektor::End (STL/CLR)

Legt das Ende der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator end();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Iterator mit zufälligem Zugriff zurück, der direkt über das Ende der gesteuerten Sequenz zeigt. Sie können damit einen Iterator abrufen, der das `current` Ende der kontrollierten Sequenz bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_end.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorerase-stlclr"></a><a name="erase"></a>Vektor::löschen (STL/CLR)

Entfernt Elemente an den angegebenen Positionen.

### <a name="syntax"></a>Syntax

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parameter

*first*<br/>
Beginn des Bereichs zu löschen.

*last*<br/>
Ende des Bereichs zu löschen.

*where*<br/>
Element, das löscht werden soll.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion entfernt das Element der gesteuerten Sequenz, auf die von *where*verwiesen wird. Sie verwenden es, um ein einzelnes Element zu entfernen.

Die zweite Memberfunktion entfernt die Elemente der gesteuerten Sequenz im Bereich [`first`, `last`). Sie verwenden es, um null oder mehr zusammenhängende Elemente zu entfernen.

Beide Memberfunktionen geben einen Iterator zurück, der das erste Element angibt, das über alle entfernten Elemente hinaus bleibt, oder [vector::end (STL/CLR),](../dotnet/vector-end-stl-clr.md) `()` wenn kein solches Element vorhanden ist.

Beim Löschen von Elementen ist die Anzahl der Elementkopien linear in der Anzahl der Elemente zwischen dem Ende der Löschung und dem näheren Ende der Sequenz. (Beim Löschen eines oder mehrerer Elemente an beiden Enden der Sequenz treten keine Elementkopien auf.)

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_erase.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="vectorfront-stlclr"></a><a name="front"></a>Vektor::front (STL/CLR)

Greift auf das erste Element zu.

### <a name="syntax"></a>Syntax

```cpp
reference front();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Verweis auf das erste Element der gesteuerten Sequenz zurück, das nicht leer sein muss. Sie verwenden es, um das erste Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_front.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorfront_item-stlclr"></a><a name="front_item"></a>Vektor::front_item (STL/CLR)

Greift auf das erste Element zu.

### <a name="syntax"></a>Syntax

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Bemerkungen

Die Eigenschaft greift auf das erste Element der gesteuerten Sequenz zu, das nicht leer sein muss. Sie verwenden es, um das erste Element zu lesen oder zu schreiben, wenn Sie wissen, dass es vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_front_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorgeneric_container-stlclr"></a><a name="generic_container"></a>Vektor::generic_container (STL/CLR)

Der Typ der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt die generische Schnittstelle für diese Vorlagencontainerklasse.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_generic_container.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="vectorgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>Vektor::generic_iterator (STL/CLR)

Der Typ eines Iterators zur Verwendung mit der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen generischen Iterator, der mit der generischen Schnittstelle für diese Vorlagencontainerklasse verwendet werden kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_generic_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>Vektor::generic_reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators für die Verwendung mit der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen generischen Reverse-Iterator, der mit der generischen Schnittstelle für diese Vorlagencontainerklasse verwendet werden kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorgeneric_value-stlclr"></a><a name="generic_value"></a>Vektor::generic_value (STL/CLR)

Der Typ eines Elements für die Verwendung mit der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein `GValue` Objekt vom Typ, das den gespeicherten Elementwert für die Verwendung mit der generischen Schnittstelle für diese Vorlagencontainerklasse beschreibt.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_generic_value.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
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

## <a name="vectorinsert-stlclr"></a><a name="insert"></a>Vektor::einfügen (STL/CLR)

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
Ende des einzufügenden Bereichs.

*Richting*<br/>
Enumeration, die eingefügt werden soll.

*Val*<br/>
Wert des einzufügenden Elements.

*where*<br/>
Wo im Behälter vor einfügen.

### <a name="remarks"></a>Bemerkungen

Jede der Memberfunktionen fügt vor dem Element, auf das *in* der gesteuerten Sequenz angegeben wird, eine Sequenz ein, die von den verbleibenden Operanden angegeben wird.

Die erste Memberfunktion fügt ein Element mit dem Wert *val* ein und gibt einen Iterator zurück, der das neu eingefügte Element kennzeichnet. Sie verwenden es, um ein einzelnes Element vor einem Ort einzufügen, der von einem Iterator festgelegt wurde.

Die zweite Memberfunktion fügt eine Wiederholung von *Zählelementen* des Werts *val ein.* Sie verwenden es, um null oder mehr zusammenhängende Elemente einzufügen, die alle Kopien desselben Werts sind.

Wenn `InIt` ein Ganzzahltyp ist, verhält sich die dritte Memberfunktion genau wie `insert(where, (size_type)first, (value_type)last)`. Andernfalls wird die Sequenz`first`[ `last`, ) eingefügt. Sie verwenden es, um null oder mehr zusammenhängende Elemente einzufügen, die aus einer anderen Sequenz kopiert wurden.

Die vierte Memberfunktion fügt die von der *rechten*bezeichnete Sequenz ein. Sie verwenden es, um eine Sequenz einzufügen, die von einem Enumerator beschrieben wird.

Beim Einfügen eines einzelnen Elements ist die Anzahl der Elementkopien linear in der Anzahl der Elemente zwischen der Einfügemarke und dem näheren Ende der Sequenz. (Beim Einfügen eines oder mehrerer Elemente an beiden Enden der Sequenz werden keine Elementkopien ausgeführt.) Wenn `InIt` es sich um einen Eingabeiterator handelt, führt die dritte Memberfunktion effektiv eine einzelne Einfügung für jedes Element in der Sequenz aus. Andernfalls ist beim `N` Einfügen von Elementen die Anzahl `N` der Elementkopien linear in plus die Anzahl der Elemente zwischen der Einfügemarke und dem näheren Ende der Sequenz.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_insert.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value using iterator
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a repetition of values
    cliext::vector<wchar_t> c2;
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

## <a name="vectoriterator-stlclr"></a><a name="iterator"></a>Vektor::iterator (STL/CLR)

Der Typ eines Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt `T1` unbestimmten Typs, das als Iterator mit zufälligem Zugriff für die gesteuerte Sequenz dienen kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
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

## <a name="vectoroperator-stlclr"></a><a name="op_as"></a>Vektor::operator= (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Der zu kopierende Container.

### <a name="remarks"></a>Bemerkungen

Der Memberoperator kopiert *das Recht* `*this`auf das Objekt und gibt dann zurück. Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz *rechts*zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_operator_as.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="vectoroperatorstlclr"></a><a name="op"></a>Vektor::operator(STL/CLR)

Greift auf ein Element an einer angegebenen Position zu.

### <a name="syntax"></a>Syntax

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Parameter

*Pos*<br/>
Position des Elements, auf das zugegriffen wird

### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt einen Referenzauf e.A. auf das Element an position *pos zurück.* Sie verwenden es, um auf ein Element zuzugreifen, dessen Position Sie kennen.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_operator_sub.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using subscripting
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();

// change an entry and redisplay
    c1[1] = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="vectorpop_back-stlclr"></a><a name="pop_back"></a>vektor::pop_back (STL/CLR)

Entfernt das letzte Element.

### <a name="syntax"></a>Syntax

```cpp
void pop_back();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion entfernt das letzte Element der gesteuerten Sequenz, das nicht leer sein muss. Sie verwenden es, um den Vektor um ein Element auf der Rückseite zu verkürzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_pop_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorpush_back-stlclr"></a><a name="push_back"></a>vektor::push_back (STL/CLR)

Fügt ein neues letztes Element hinzu.

### <a name="syntax"></a>Syntax

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion fügt ein `val` Element mit Wert am Ende der gesteuerten Sequenz ein. Sie verwenden es, um ein anderes Element an den Vektor anzuhängen.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_push_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorrbegin-stlclr"></a><a name="rbegin"></a>Vektor::rbegin (STL/CLR)

Legt den Anfang der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen umgekehrten Iterator zurück, der das letzte Element der gesteuerten Sequenz oder knapp über den Anfang einer leeren Sequenz hinaus bezeichnet. Demzufolge wird der `beginning` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_rbegin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="vectorreference-stlclr"></a><a name="reference"></a>vektor::Referenz (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

// modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;

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

## <a name="vectorrend-stlclr"></a><a name="rend"></a>Vektor::rend (STL/CLR)

Legt das Ende der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen umgekehrten Iterator zurück, der direkt über den Anfang der gesteuerten Sequenz hinaus zeigt. Demzufolge wird der `end` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der das `current` Ende der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_rend.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="vectorreserve-stlclr"></a><a name="reserve"></a>Vektor::Reserve (STL/CLR)

Gewährleistet eine minimale Wachstumskapazität für den Container.

### <a name="syntax"></a>Syntax

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>Parameter

*count*<br/>
Neue Mindestkapazität des Containers.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `capacity()` stellt sicher, dass von nun an mindestens *die Anzahl*zurückgegeben wird. Sie verwenden es, um sicherzustellen, dass der Container den Speicher für die gesteuerte Sequenz erst neu zuordnen muss, wenn er auf die angegebene Größe angewachsen ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_reserve.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="vectorresize-stlclr"></a><a name="resize"></a>vektor::Größenänderung (STL/CLR)

Ändert die Anzahl der Elemente.

### <a name="syntax"></a>Syntax

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Parameter

*new_size*<br/>
Neue Größe der gesteuerten Sequenz.

*Val*<br/>
Wert des Auffüllungselements.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktionen stellen beide sicher, dass [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` fortan *new_size*zurückgibt. Wenn die gesteuerte Sequenz länger werden muss, fügt `value_type()`die erste Memberfunktion Elemente mit wert an, während die zweite Memberfunktion Elemente mit dem Wert *val*anfügt. Um die gesteuerte Sequenz zu verkürzen, löschen beide Memberfunktionen effektiv die letzten [Elementvektorzeiten::size (STL/CLR).](../dotnet/vector-size-stl-clr.md) `() -` `new_size` Sie verwenden es, um sicherzustellen, dass die gesteuerte Sequenz *größe new_size*hat, indem Sie entweder die aktuelle gesteuerte Sequenz trimmen oder auffüllen.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_resize.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container and pad with default values
    cliext::vector<wchar_t> c1;
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

## <a name="vectorreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>Vektor::reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt `T3` unbestimmten Typs, das als umgekehrter Iterator für die gesteuerte Sequenz dienen kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="vectorsize-stlclr"></a><a name="size"></a>Vektor::Größe (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden es, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der gesteuerten Sequenz befinden. Wenn Ihnen nur wichtig ist, ob die Sequenz eine Größe ungleich Null hat, siehe [vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_size.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorsize_type-stlclr"></a><a name="size_type"></a>Vektor::size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Elementanzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_size_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="vectorswap-stlclr"></a><a name="swap"></a>Vektor::swap (STL/CLR)

Vertauscht den Inhalt von zwei Containern.

### <a name="syntax"></a>Syntax

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Container für den Tausch von Inhalten.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion tauscht die `*this` gesteuerten Sequenzen zwischen und *rechts.* Es tut dies in konstanter Zeit und es löst keine Ausnahmen aus. Sie verwenden es als schnelle Möglichkeit, den Inhalt von zwei Containern auszutauschen.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_swap.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::vector<wchar_t> c2(5, L'x');
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

## <a name="vectorto_array-stlclr"></a><a name="to_array"></a>Vektor::to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt ein Array zurück, das die gesteuerte Sequenz enthält. Sie verwenden es, um eine Kopie der gesteuerten Sequenz in Array-Form zu erhalten.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_to_array.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
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

## <a name="vectorvalue_type-stlclr"></a><a name="value_type"></a>Vektor::value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter *Value*.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_value_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using value_type
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::vector<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vectorvector-stlclr"></a><a name="vector"></a>Vektor::Vektor (STL/CLR)

Erstellt ein container-Objekt.

### <a name="syntax"></a>Syntax

```cpp
vector();
vector(vector<Value>% right);
vector(vector<Value>^ right);
explicit vector(size_type count);
vector(size_type count, value_type val);
template<typename InIt>
    vector(InIt first, InIt last);
vector(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parameter

*count*<br/>
Die Anzahl einzufügender Elemente.

*first*<br/>
Anfang des einzufügenden Bereichs.

*last*<br/>
Ende des einzufügenden Bereichs.

*Richting*<br/>
Einzufügendes Objekt bzw. einzufügender Bereich.

*Val*<br/>
Wert des einzufügenden Elements.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`vector();`

initialisiert die gesteuerte Sequenz ohne Elemente. Sie verwenden es, um eine leere anfangs gesteuerte Sequenz anzugeben.

Der Konstruktor:

`vector(vector<Value>% right);`

initialisiert die gesteuerte Sequenz`right.begin()`mit `right.end()`der Sequenz [ , ). Sie verwenden es, um eine erste gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom Vektorobjekt *rechts*gesteuert wird.

Der Konstruktor:

`vector(vector<Value>^ right);`

initialisiert die gesteuerte Sequenz`right->begin()`mit `right->end()`der Sequenz [ , ). Sie verwenden es, um eine erste gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom Vektorobjekt gesteuert wird, dessen Handle *richtig*ist.

Der Konstruktor:

`explicit vector(size_type count);`

initialisiert die gesteuerte Sequenz mit `value_type()` *Zählelementen* mit jeweils einem Wert . Sie verwenden es, um den Container mit Elementen zu füllen, die alle den Standardwert haben.

Der Konstruktor:

`vector(size_type count, value_type val);`

initialisiert die gesteuerte Sequenz mit *Zählelementen* mit jeweils dem Wert *val*. Sie verwenden es, um den Container mit Elementen zu füllen, die alle den gleichen Wert haben.

Der Konstruktor:

`template<typename InIt>`

`vector(InIt first, InIt last);`

initialisiert die gesteuerte Sequenz`first`mit `last`der Sequenz [ , ). Sie verwenden es, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen.

Der Konstruktor:

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

initialisiert die gesteuerte Sequenz mit der Sequenz, die vom Enumerator *rechts*bezeichnet wird. Sie verwenden sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator beschrieben wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_construct.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct with a repetition of default values
    cliext::vector<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// construct with a repetition of values
    cliext::vector<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    cliext::vector<wchar_t>::iterator it = c3.end();
    cliext::vector<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    cliext::vector<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying a container handle
    cliext::vector<wchar_t> c8(%c3);
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

## <a name="operator-vector-stlclr"></a><a name="op_neq"></a>Operator!= (Vektor) (STL/CLR)

Vektor nicht gleich Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator!=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(left == right)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht rechts angeordnet *ist,* wenn die beiden Vektoren Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_operator_ne.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lt"></a>Operator&lt; (Vektor) (STL/CLR)

Vektor weniger als Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator<(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion gibt true zurück, `i` wenn `!(right[i] < left[i])` für die `left[i] < right[i]`niedrigste Position, für die es auch wahr ist, dass . Andernfalls wird `left->size() < right->size()` zurückgegeben Sie verwenden, um zu testen, ob *links* vor *rechts* angeordnet ist, wenn die beiden Vektoren Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_operator_lt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lteq"></a>Operator&lt;= (Vektor) (STL/CLR)

Vektor kleiner oder gleich Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator<=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(right < left)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht nach *rechts* sortiert ist, wenn die beiden Vektoren Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_operator_le.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operator-vector-stlclr"></a><a name="op_eq"></a>Operator == (Vektor) (STL/CLR)

Vektor-Gleicher Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator==(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion gibt true nur dann zurück, wenn die von *links* `i`und `left[i] ==` `right[i]` *rechts* gesteuerten Sequenzen die gleiche Länge haben und für jede Position . Sie verwenden es, um zu testen, ob *links* gleich *rechts* angeordnet ist, wenn die beiden Vektoren Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_operator_eq.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gt"></a>Operator&gt; (Vektor) (STL/CLR)

Vektor größer als Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator>(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `right` `<` `left`gibt zurück. Sie verwenden es, um zu testen, ob *links* nach *rechts* sortiert ist, wenn die beiden Vektoren Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_operator_gt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gteq"></a>Operator&gt;= (Vektor) (STL/CLR)

Vektor größer oder gleicher Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Value>
    bool operator>=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(left < right)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht vor *rechts* angeordnet ist, wenn die beiden Vektoren Element für Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_vector_operator_ge.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
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
