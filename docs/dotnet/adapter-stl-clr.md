---
title: adapter (STL/CLR)
ms.date: 06/15/2018
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
ms.openlocfilehash: 7730b5a8dbb8c92d85b4c8c5732657d28bf5b229
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216439"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)

Der STL/CLR-Header `<cliext/adapter>` gibt zwei Vorlagen Klassen ( `collection_adapter` und `range_adapter` ) und die Vorlagen Funktion an `make_collection` .

## <a name="syntax"></a>Syntax

```cpp
#include <cliext/adapter>
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<cliext/adapter>

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|[collection_adapter (STL/CLR)](#collection_adapter)|Umschließt die BCL-Auflistung (Base Class Library) als Bereich.|
|[range_adapter (STL/CLR)](#range_adapter)|Umschließt den Bereich als BCL-Auflistung.|

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[make_collection (STL/CLR)](#make_collection)|Erstellt einen Bereichs Adapter mithilfe eines iteratorpaars.|

## <a name="members"></a>Member

## <a name="collection_adapter-stlclr"></a><a name="collection_adapter"></a>Collection_adapter (STL/CLR)

Umschließt eine .net-Auflistung, die als STL/CLR-Container verwendet werden soll. Eine `collection_adapter` ist eine Vorlagen Klasse, die ein einfaches STL/CLR-Container Objekt beschreibt. Er umschließt eine BCL-Schnittstelle (Base Class Library) und gibt ein Iteratorpaar zurück, das Sie verwenden, um die gesteuerte Sequenz zu bearbeiten.

### <a name="syntax"></a>Syntax

```cpp
template<typename Coll>
    ref class collection_adapter;

template<>
    ref class collection_adapter<
        System::Collections::ICollection>;
template<>
    ref class collection_adapter<
        System::Collections::IEnumerable>;
template<>
    ref class collection_adapter<
        System::Collections::IList>;
template<>
    ref class collection_adapter<
        System::Collections::IDictionary>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::ICollection<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IEnumerable<Value>>;
template<typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IList<Value>>;
template<typename Key,
    typename Value>
    ref class collection_adapter<
        System::Collections::Generic::IDictionary<Key, Value>>;
```

#### <a name="parameters"></a>Parameter

*Coll*<br/>
Der Typ der umschließenden Auflistung.

### <a name="specializations"></a>Spezialisierungen

|Spezialisierung|BESCHREIBUNG|
|--------------------|-----------------|
|IEnumerable|Sequenzen durch-Elemente.|
|ICollection|Verwaltet eine Gruppe von Elementen.|
|IList|Verwaltet eine geordnete Gruppe von Elementen.|
|IDictionary|Behalten Sie einen Satz von {Key, Value}-Paaren bei.|
|IEnumerable\<Value>|Sequenzen durch typisierte-Elemente.|
|ICollection\<Value>|Verwaltet eine Gruppe von typisierten Elementen.|
|IList\<Value>|Verwaltet eine geordnete Gruppe von typisierten Elementen.|
|IDictionary\<Value> |Verwaltet eine Menge typisierter {Key, value}-Paare.|

### <a name="members"></a>Member

|Typendefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[collection_adapter::iterator (STL/CLR)](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[collection_adapter::key_type (STL/CLR)](#key_type)|Der Typ eines Wörterbuch Schlüssels.|
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|Der Typ eines Wörterbuch Werts.|
|[collection_adapter::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[collection_adapter::size_type (STL/CLR)](#size_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[collection_adapter::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[collection_adapter::base (STL/CLR)](#base)|Gibt die umschließende BCL-Schnittstelle an.|
|[collection_adapter::begin (STL/CLR)](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|Erstellt ein Adapter Objekt.|
|[collection_adapter::end (STL/CLR)](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[collection_adapter::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[collection_adapter::swap (STL/CLR)](#swap)|Vertauscht den Inhalt von zwei Containern.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[collection_adapter::operator= (STL/CLR)](#op_eq)|Ersetzt das gespeicherte BCL-Handle.|

### <a name="remarks"></a>Bemerkungen

Sie verwenden diese Vorlagen Klasse, um einen BCL-Container als STL/CLR-Container zu bearbeiten. `collection_adapter`Speichert ein Handle für eine BCL-Schnittstelle, die wiederum eine Sequenz von Elementen steuert. Ein `collection_adapter` `X` -Objekt gibt ein paar von eingabeiteratoren zurück `X.begin()` `X.end()` , das Sie verwenden, um die Elemente in der richtigen Reihenfolge zu besuchen. Mit einigen der Spezialisierungs Informationen können Sie auch schreiben `X.size()` , um die Länge der kontrollierten Sequenz zu bestimmen.

## <a name="collection_adapterbase-stlclr"></a><a name="base"></a>collection_adapter:: base (STL/CLR)

Gibt die umschließende BCL-Schnittstelle an.

### <a name="syntax"></a>Syntax

```cpp
Coll^ base();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt das gespeicherte BCL-Schnittstellen Handle zurück.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_base.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);
    return (0);
    }
```

```Output
x x x x x x
base() same = True
```

## <a name="collection_adapterbegin-stlclr"></a><a name="begin"></a>collection_adapter:: begin (STL/CLR)

Legt den Anfang der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator begin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen eingabeiterator zurück, der das erste Element der kontrollierten Sequenz oder direkt hinter das Ende einer leeren Sequenz festlegt.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_begin.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mycoll::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
}
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="collection_adaptercollection_adapter-stlclr"></a><a name="collection_adapter_collection_adapter"></a>collection_adapter:: Collection_adapter (STL/CLR)

Erstellt ein Adapter Objekt.

### <a name="syntax"></a>Syntax

```cpp
collection_adapter();
collection_adapter(collection_adapter<Coll>% right);
collection_adapter(collection_adapter<Coll>^ right);
collection_adapter(Coll^ collection);
```

#### <a name="parameters"></a>Parameter

*Ausstellung*<br/>
BCL-Handle, das eingebunden werden soll.

*Richting*<br/>
Objekt, das kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`collection_adapter();`

Initialisiert das gespeicherte Handle mit **`nullptr`** .

Der Konstruktor:

`collection_adapter(collection_adapter<Coll>% right);`

Initialisiert das gespeicherte Handle mit `right.` [collection_adapter:: base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md) `()` .

Der Konstruktor:

`collection_adapter(collection_adapter<Coll>^ right);`

Initialisiert das gespeicherte Handle mit `right->` [collection_adapter:: base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md) `()` .

Der Konstruktor:

`collection_adapter(Coll^ collection);`

Initialisiert das gespeicherte Handle mit `collection` .

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');

    // construct an empty container
    Mycoll c1;
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);

    // construct with a handle
    Mycoll c2(%d6x);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mycoll c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mycoll c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
base() null = True
x x x x x x
x x x x x x
x x x x x x
```

## <a name="collection_adapterdifference_type-stlclr"></a><a name="difference_type"></a>collection_adapter::d ifference_type (STL/CLR)

Die Typen eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Anzahl von signierten Elementen.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_difference_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mycoll::difference_type diff = 0;
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
}
```

```Output
a b c
end()-begin() = 3
```

## <a name="collection_adapterend-stlclr"></a><a name="end"></a>collection_adapter:: End (STL/CLR)

Legt das Ende der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator end();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen eingabeiterator zurück, der direkt hinter das Ende der kontrollierten Sequenz verweist.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_end.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adapteriterator-stlclr"></a><a name="iterator"></a>collection_adapter:: Iterator (STL/CLR)

Der Typ eines Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T1` , das als eingabeiterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_iterator.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adapterkey_type-stlclr"></a><a name="key_type"></a>collection_adapter:: key_type (STL/CLR)

Der Typ eines Wörterbuch Schlüssels.

### <a name="syntax"></a>Syntax

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter `Key` in einer Spezialisierung für `IDictionary` oder `IDictionary<Value>` ; andernfalls ist er nicht definiert.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_key_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="collection_adaptermapped_type-stlclr"></a><a name="mapped_type"></a>collection_adapter:: mapped_type (STL/CLR)

Der Typ eines Wörterbuch Werts.

### <a name="syntax"></a>Syntax

```cpp
typedef Value mapped_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter `Value` in einer Spezialisierung für `IDictionary` oder `IDictionary<Value>` ; andernfalls ist er nicht definiert.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_mapped_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef cliext::collection_adapter<
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;
int main()
{
    Mymap d1;
    d1.insert(Mymap::make_value(L'a', 1));
    d1.insert(Mymap::make_value(L'b', 2));
    d1.insert(Mymap::make_value(L'c', 3));
    Mycoll c1(%d1);

    // display contents "[a 1] [b 2] [c 3] "
    for each (Mypair elem in c1)
    {
        Mycoll::key_type key = elem.Key;
        Mycoll::mapped_type value = elem.Value;
        System::Console::Write("[{0} {1}] ", key, value);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="collection_adapteroperator-stlclr"></a><a name="op_eq"></a>collection_adapter:: Operator = (STL/CLR)

Ersetzt das gespeicherte BCL-Handle.

### <a name="syntax"></a>Syntax

```cpp
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Adapter, der kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann zurück **`*this`** . Sie verwenden es, um das gespeicherte BCL-Handle durch eine Kopie des gespeicherten BCL-Handles in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mycoll c2;
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

## <a name="collection_adapterreference-stlclr"></a><a name="reference"></a>collection_adapter:: Reference (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_reference.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents "a b c "
    Mycoll::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
    {   // get a reference to an element
        Mycoll::reference ref = *it;
        System::Console::Write("{0} ", ref);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="collection_adaptersize-stlclr"></a><a name="size"></a>collection_adapter:: Size (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Er ist nicht in einer Spezialisierung für `IEnumerable` oder definiert `IEnumerable<Value>` .

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_size.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x "
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="collection_adaptersize_type-stlclr"></a><a name="size_type"></a>collection_adapter:: size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_size_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d6x(6, L'x');
    Mycoll c1(%d6x);

    // display initial contents "x x x x x x"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    Mycoll::size_type size = c1.size();
    System::Console::WriteLine("size() = {0}", size);
    return (0);
}
```

```Output
x x x x x x
size() = 6
```

## <a name="collection_adapterswap-stlclr"></a><a name="swap"></a>collection_adapter:: Swap (STL/CLR)

Vertauscht den Inhalt von zwei Containern.

### <a name="syntax"></a>Syntax

```cpp
void swap(collection_adapter<Coll>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Container für den Tausch von Inhalten.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht die gespeicherten BCL-Handles zwischen **`*this`** und *right*aus.

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
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

## <a name="collection_adaptervalue_type-stlclr"></a><a name="value_type"></a>collection_adapter:: value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter *Wert*, wenn er in der Spezialisierung vorhanden ist. andernfalls handelt es sich um ein Synonym für `System::Object^` .

### <a name="example"></a>Beispiel

```cpp
// cliext_collection_adapter_value_type.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

    // display contents "a b c" using value_type
    for (Mycoll::iterator it = c1.begin();
        it != c1.end(); ++it)
    {   // store element in value_type object
        Mycoll::value_type val = *it;

        System::Console::Write("{0} ", val);
    }
    System::Console::WriteLine();
    return (0);
}
```

```Output
a b c
```

## <a name="make_collection-stlclr"></a><a name="make_collection"></a>make_collection (STL/CLR)

Erstellen Sie `range_adapter` aus einem Iteratorpaar.

### <a name="syntax"></a>Syntax

```cpp
template<typename Iter>
    range_adapter<Iter> make_collection(Iter first, Iter last);
```

#### <a name="parameters"></a>Parameter

*Verstärkt*<br/>
Der Typ der umschließenden Iteratoren.

*first*<br/>
Der erste Iterator, der eingebunden werden soll.

*last*<br/>
Der zweite Iterator, der eingebunden werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `gcnew range_adapter<Iter>(first, last)` zurück. Sie verwenden Sie, um ein- `range_adapter<Iter>` Objekt aus einem Iteratorpaar zu erstellen.

### <a name="example"></a>Beispiel

```cpp
// cliext_make_collection.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in d1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Collections::ICollection^ p1 =
        cliext::make_collection(d1.begin(), d1.end());
    System::Console::WriteLine("Count = {0}", p1->Count);
    System::Console::WriteLine("IsSynchronized = {0}",
        p1->IsSynchronized);
    System::Console::WriteLine("SyncRoot not nullptr = {0}",
        p1->SyncRoot != nullptr);

    // copy the sequence
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);

    a1[0] = L'|';
    p1->CopyTo(a1, 1);
    a1[4] = L'|';
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
Count = 3
IsSynchronized = False
SyncRoot not nullptr = True
| a b c |
```

## <a name="range_adapter-stlclr"></a><a name="range_adapter"></a>range_adapter (STL/CLR)

Eine Vorlagen Klasse, die ein paar von Iteratoren umschließt, die zur Implementierung mehrerer Basisklassen Bibliothek-Schnittstellen (BCL) verwendet werden. Sie verwenden die range_adapter, um einen STL/CLR-Bereich so zu bearbeiten, als ob es sich um eine BCL-Auflistung handelt.

### <a name="syntax"></a>Syntax

```cpp
template<typename Iter>
    ref class range_adapter
        :   public
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<Value>,
        System::Collections::Generic::ICollection<Value>
    { ..... };
```

#### <a name="parameters"></a>Parameter

*Verstärkt*<br/>
Der Typ, der den umschließenen Iteratoren zugeordnet ist.

### <a name="members"></a>Member

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|Erstellt ein Adapter Objekt.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|Ersetzt das gespeicherte Iteratorpaar.|

### <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.Collections.IEnumerable>|Iteriert durch Elemente in der Auflistung.|
|<xref:System.Collections.ICollection>|Verwaltet eine Gruppe von Elementen.|
|<xref:System.Collections.Generic.IEnumerable%601>|Durchläuft typisierte-Elemente in der-Auflistung.|
|<xref:System.Collections.Generic.ICollection%601>|Verwaltet eine Gruppe von typisierten Elementen.|

### <a name="remarks"></a>Bemerkungen

Der range_adapter speichert ein paar von Iteratoren, die wiederum eine Sequenz von Elementen begrenzen. Das-Objekt implementiert vier BCL-Schnittstellen, mit denen Sie die Elemente in der richtigen Reihenfolge durchlaufen können. Sie verwenden diese Vorlagen Klasse, um STL/CLR-Bereiche ähnlich wie BCL-Container zu bearbeiten.

## <a name="range_adapteroperator-stlclr"></a><a name="range_adapter_op_eq"></a>range_adapter:: Operator = (STL/CLR)

Ersetzt das gespeicherte Iteratorpaar.

### <a name="syntax"></a>Syntax

```cpp
range_adapter<Iter>% operator=(range_adapter<Iter>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Adapter, der kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann zurück **`*this`** . Sie verwenden es, um das gespeicherte Iteratorpaar durch eine Kopie des gespeicherten iteratorpaars in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_range_adapter_operator_as.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Myrange c1(d1.begin(), d1.end());

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myrange c2;
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

## <a name="range_adapterrange_adapter-stlclr"></a><a name="range_adapter_range_adapter"></a>range_adapter:: range_adapter (STL/CLR)

Erstellt ein Adapter Objekt.

### <a name="syntax"></a>Syntax

```cpp
range_adapter();
range_adapter(range_adapter<Iter>% right);
range_adapter(range_adapter<Iter>^ right);
range_adapter(Iter first, Iter last);
```

#### <a name="parameters"></a>Parameter

*first*<br/>
Der erste Iterator, der eingebunden werden soll.

*last*<br/>
Der zweite Iterator, der eingebunden werden soll.

*Richting*<br/>
Objekt, das kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`range_adapter();`

Initialisiert das gespeicherte Iteratorpaar mit standardmäßig konstruierten Iteratoren.

Der Konstruktor:

`range_adapter(range_adapter<Iter>% right);`

Initialisiert das gespeicherte Iteratorpaar durch Kopieren des in *right*gespeicherten Paars.

Der Konstruktor:

`range_adapter(range_adapter<Iter>^ right);`

Initialisiert das gespeicherte Iteratorpaar durch Kopieren des in gespeicherten Paars `*right` .

Der Konstruktor:

`range_adapter(Iter^ first, last);`

Initialisiert das gespeicherte Iteratorpaar mit *First* und *Last*.

### <a name="example"></a>Beispiel

```cpp
// cliext_range_adapter_construct.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::deque<wchar_t> Mycont;
typedef cliext::range_adapter<Mycont::iterator> Myrange;
int main()
{
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');

    // construct an empty adapter
    Myrange c1;

    // construct with an iterator pair
    Myrange c2(d1.begin(), d1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another adapter
    Myrange c3(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying an adapter handle
    Myrange c4(%c3);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
}
```

```Output
a b c
a b c
a b c
```
