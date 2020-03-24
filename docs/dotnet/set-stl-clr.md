---
title: set (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::set::begin
- cliext::set::clear
- cliext::set::const_iterator
- cliext::set::const_reference
- cliext::set::const_reverse_iterator
- cliext::set::count
- cliext::set::difference_type
- cliext::set::empty
- cliext::set::end
- cliext::set::equal_range
- cliext::set::erase
- cliext::set::find
- cliext::set::generic_container
- cliext::set::generic_iterator
- cliext::set::generic_reverse_iterator
- cliext::set::generic_value
- cliext::set::insert
- cliext::set::iterator
- cliext::set::key_comp
- cliext::set::key_compare
- cliext::set::key_type
- cliext::set::lower_bound
- cliext::set::make_value
- cliext::set::operator=
- cliext::set::rbegin
- cliext::set::reference
- cliext::set::rend
- cliext::set::reverse_iterator
- cliext::set::set
- cliext::set::size
- cliext::set::size_type
- cliext::set::swap
- cliext::set::to_array
- cliext::set::upper_bound
- cliext::set::value_comp
- cliext::set::value_compare
- cliext::set::value_type
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
- operator!= (set) member [STL/CLR]
- operator< (set) member [STL/CLR]
- operator<= (set) member [STL/CLR]
- operator== (set) member [STL/CLR]
- operator> (set) member [STL/CLR]
- operator>= (set) member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- set member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
ms.openlocfilehash: a5e98a9fe32c71e87f80c2cfc2e733a5d0fe5c94
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208337"
---
# <a name="set-stlclr"></a>set (STL/CLR)

Die Vorlagen Klasse beschreibt ein Objekt, das eine Sequenz von Elementen variabler Länge steuert, die bidirektionalen Zugriff hat. Sie verwenden den Container `set`, um eine Sequenz von Elementen als (fast) ausgeglichene geordnete Struktur von Knoten zu verwalten, von denen jeweils ein Element gespeichert wird.

In der folgenden Beschreibung ist `GValue` identisch mit `GKey`, das wiederum mit *Key* identisch ist, sofern es sich nicht um einen Verweistyp handelt. in diesem Fall handelt es sich um `Key^`.

## <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    ref class set
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parameter

*Schlüssel*<br/>
Der Typ der Schlüsselkomponente eines Elements in der kontrollierten Sequenz.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<cliext/Set >

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[set::const_iterator (STL/CLR)](#const_iterator)|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|[set::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.|
|[set::difference_type (STL/CLR)](#difference_type)|Der Typ einer (möglicherweise mit Vorzeichen signierten) Entfernung zwischen zwei Elementen.|
|[set::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container.|
|[set::generic_iterator (STL/CLR)](#generic_iterator)|Der Typ eines Iterators für die generische Schnittstelle für den Container.|
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Der Typ eines umgekehrten Iterators für die generische Schnittstelle für den Container.|
|[set::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container.|
|[set::iterator (STL/CLR)](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[set::key_compare (STL/CLR)](#key_compare)|Der Bestell Delegat für zwei Schlüssel.|
|[set::key_type (STL/CLR)](#key_type)|Der Typ eines Sortierschlüssels.|
|[set::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.|
|[set::size_type (STL/CLR)](#size_type)|Der Typ einer (nicht negativen) Entfernung zwischen zwei Elementen.|
|[set::value_compare (STL/CLR)](#value_compare)|Der Bestell Delegat für zwei Element Werte.|
|[set::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[set::begin (STL/CLR)](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[set::clear (STL/CLR)](#clear)|Entfernt alle Elemente.|
|[set::count (STL/CLR)](#count)|Zählt Elemente, die mit einem angegebenen Schlüssel übereinstimmen.|
|[set::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[set::end (STL/CLR)](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[set::equal_range (STL/CLR)](#equal_range)|Sucht den Bereich, der einem angegebenen Schlüssel entspricht.|
|[set::erase (STL/CLR)](#erase)|Entfernt Elemente an den angegebenen Positionen.|
|[set::find (STL/CLR)](#find)|Sucht ein Element, das einem angegebenen Schlüssel entspricht.|
|[set::insert (STL/CLR)](#insert)|Fügt Elemente hinzu.|
|[set::key_comp (STL/CLR)](#key_comp)|Kopiert den Bestell Delegaten für zwei Schlüssel.|
|[set::lower_bound (STL/CLR)](#lower_bound)|Sucht den Anfang des Bereichs, der einem angegebenen Schlüssel entspricht.|
|[set::make_value (STL/CLR)](#make_value)|Erstellt ein Wertobjekt.|
|[set::rbegin (STL/CLR)](#rbegin)|Legt den Anfang der umgekehrten kontrollierten Sequenz fest.|
|[set::rend (STL/CLR)](#rend)|Legt das Ende der umgekehrten kontrollierten Sequenz fest.|
|[set::set (STL/CLR)](#set)|Erstellt ein container-Objekt.|
|[set::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[set::swap (STL/CLR)](#swap)|Vertauscht den Inhalt von zwei Containern.|
|[set::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|
|[set::upper_bound (STL/CLR)](#upper_bound)|Findet das Ende des Bereichs, der einem angegebenen Schlüssel entspricht.|
|[set::value_comp (STL/CLR)](#value_comp)|Kopiert den Bestell Delegaten für zwei Element Werte.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[set::operator= (STL/CLR)](#op_as)|Ersetzt die kontrollierte Sequenz.|
|[operator!= (set) (STL/CLR)](#op_neq)|Bestimmt, ob ein `set` Objekt nicht gleich einem anderen `set` Objekt ist.|
|[operator< (set) (STL/CLR)](#op_lt)|Bestimmt, ob ein `set` Objekt kleiner als ein anderes `set`-Objekt ist.|
|[operator<= (set) (STL/CLR)](#op_lteq)|Bestimmt, ob ein `set`-Objekt kleiner als oder gleich einem anderen `set`-Objekt ist.|
|[operator== (set) (STL/CLR)](#op_eq)|Bestimmt, ob ein `set` Objekt gleich einem anderen `set`-Objekt ist.|
|[operator> (set) (STL/CLR)](#op_gt)|Bestimmt, ob ein `set` Objekt größer als ein anderes `set`-Objekt ist.|
|[operator>= (set) (STL/CLR)](#op_gteq)|Bestimmt, ob ein `set` Objekt größer als oder gleich einem anderen `set` Objekt ist.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren eines Objekts.|
|<xref:System.Collections.IEnumerable>|Sequenzieren Sie Elemente.|
|<xref:System.Collections.ICollection>|Die Gruppe von Elementen wird beibehalten.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sequenz durch typisierte-Elemente.|
|<xref:System.Collections.Generic.ICollection%601>|Verwaltet eine Gruppe von typisierten Elementen.|
|ITree\<Schlüssel, Wert >|Verwalten Sie einen generischen Container.|

## <a name="remarks"></a>Bemerkungen

Das-Objekt ordnet Speicher für die Sequenz zu, die er als einzelne Knoten steuert, und gibt diesen frei. Sie fügt Elemente in eine (fast) ausgeglichene Struktur ein, die durch Ändern der Verknüpfungen zwischen den Knoten geändert wird, ohne den Inhalt eines Knotens auf einen anderen zu kopieren. Dies bedeutet, dass Sie Elemente ohne Beeinträchtigung der restlichen Elemente frei einfügen und entfernen können.

Das Objekt sortiert die Sequenz, die es steuert, indem ein gespeichertes Delegatobjekt vom Typ [Set:: key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)aufgerufen wird. Beim Erstellen des Satzes können Sie das gespeicherte Delegatobjekt angeben. Wenn Sie kein Delegatobjekt angeben, ist der Standardwert der Vergleichs `operator<(key_type, key_type)`. Sie greifen auf dieses gespeicherte Objekt zu, indem Sie den Member Function [Set:: key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`aufrufen.

Ein solches Delegatobjekt muss eine strikte schwache Reihenfolge für Schlüssel vom Typ [Set:: key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)erzwingen. Dies bedeutet, dass für alle zwei Schlüssel `X` und `Y`:

`key_comp()(X, Y)` gibt bei jedem-Rückruf dasselbe boolesche Ergebnis zurück.

Wenn `key_comp()(X, Y)` true ist, muss `key_comp()(Y, X)` den Wert false aufweisen.

Wenn `key_comp()(X, Y)` den Wert true hat, wird `X` vor dem `Y`als geordnet bezeichnet.

Wenn `!key_comp()(X, Y) && !key_comp()(Y, X)` true ist, werden `X` und `Y` als äquivalente Reihenfolge bezeichnet.

Für alle Element `X`, das `Y` in der gesteuerten Sequenz vorangeht, ist `key_comp()(Y, X)` false. (Für das standarddelegatobjekt verringern Schlüssel niemals den Wert.) Im Gegensatz zum Vorlagen Klassen [Satz](../dotnet/set-stl-clr.md)erfordert ein Objekt der Vorlagen Klasse `set` nicht, dass Schlüssel für alle Elemente eindeutig sind. (Zwei oder mehr Schlüssel können eine entsprechende Reihenfolge aufweisen.)

Jedes Element dient sowohl als EY-als auch als-Wert. Die Sequenz wird so dargestellt, dass die Suche, das Einfügen und das Entfernen eines beliebigen Elements mit einer Reihe von Vorgängen, die proportional zum Logarithmus der Anzahl von Elementen in der Sequenz sind (logarithmische Zeit), ermöglicht wird. Darüber hinaus führt das Einfügen eines Elements nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen eines Elements werden nur solche Iteratoren ungültig, die auf das entfernte Element gezeigt haben.

Eine Menge unterstützt Bidirektionale Iteratoren, was bedeutet, dass Sie bei einem Iterator, der ein Element in der gesteuerten Sequenz festlegt, zu angrenzenden Elementen wechseln können. Ein spezieller Haupt Knoten entspricht dem Iterator, der von [Set:: End (STL/CLR)-](../dotnet/set-end-stl-clr.md)`()`zurückgegeben wurde. Sie können diesen Iterator verringern, um das letzte Element in der kontrollierten Sequenz zu erreichen, falls vorhanden. Sie können einen Set-Iterator erhöhen, um den Head-Knoten zu erreichen, und dann wird gleich `end()`verglichen. Sie können jedoch nicht den von `end()`zurückgegebenen Iterator dereferenzieren.

Beachten Sie, dass Sie nicht direkt auf ein Set-Element verweisen können, das die numerische Position erhält, die einen Random-Access-Iterator erfordert.

Ein Set-Iterator speichert ein Handle für den zugeordneten Mengen Knoten, der wiederum ein Handle für den zugehörigen Container speichert. Iteratoren können nur mit den zugehörigen Container Objekten verwendet werden. Ein Set-Iterator bleibt gültig, solange der zugehörige Mengen Knoten einem Satz zugeordnet ist. Außerdem ist ein gültiger Iterator dereferencable--Sie können ihn verwenden, um auf den von ihm festgelegt-Elementwert zuzugreifen oder ihn zu ändern, solange er nicht gleich `end()`ist.

Durch das Löschen oder Entfernen eines Elements wird der Dekonstruktor für den gespeicherten Wert aufgerufen. Wenn Sie den Container zerstören, werden alle Elemente gelöscht. Daher stellt ein Container, dessen Elementtyp eine Verweis Klasse ist, sicher, dass keine Elemente den Container überdauern. Beachten Sie jedoch, dass ein Container von Handles seine Elemente *nicht* zerstört.

## <a name="members"></a>Members

## <a name="setbegin-stlclr"></a><a name="begin"></a>Set:: begin (STL/CLR)

Legt den Anfang der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator begin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen bidirektionalen Iterator zurück, der das erste Element der kontrollierten Sequenz festlegt, oder direkt hinter das Ende einer leeren Sequenz. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::iterator it = c1.begin();
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

## <a name="setclear-stlclr"></a><a name="clear"></a>Set:: Clear (STL/CLR)

Entfernt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft effektiv [Set:: Erase (STL/CLR)-](../dotnet/set-erase-stl-clr.md)`(` [Set:: begin (STL/CLR)](../dotnet/set-begin-stl-clr.md)`(),` [Set:: End (STL/CLR)-](../dotnet/set-end-stl-clr.md)`())`auf. Sie verwenden ihn, um sicherzustellen, dass die gesteuerte Sequenz leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

// add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

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

## <a name="setconst_iterator-stlclr"></a><a name="const_iterator"></a>Set:: const_iterator (STL/CLR)

Der Typ eines konstanten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T2`, das als konstanter bidirektionaler Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setconst_reference-stlclr"></a><a name="const_reference"></a>Set:: const_reference (STL/CLR)

Der Typ eines konstanten Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen konstanten Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>Set:: const_reverse_iterator (STL/CLR)

Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T4`, das als konstanter umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="setcount-stlclr"></a><a name="count"></a>Set:: count (STL/CLR)

Sucht die Anzahl von Elementen, die einem angegebenen Schlüssel entsprechen.

### <a name="syntax"></a>Syntax

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt die Anzahl der Elemente in der gesteuerten Sequenz zurück, die eine äquivalente Reihenfolge mit dem *Schlüssel*aufweisen. Damit können Sie die Anzahl der Elemente in der kontrollierten Sequenz ermitteln, die derzeit einem angegebenen Schlüssel entsprechen.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="setdifference_type-stlclr"></a><a name="difference_type"></a>Set::d ifference_type (STL/CLR)

Die Typen eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine möglicherweise negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="setempty-stlclr"></a><a name="empty"></a>Set:: Empty (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Dies entspricht [Set:: Size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`. Sie verwenden es, um zu testen, ob der Satz leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

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

## <a name="setend-stlclr"></a><a name="end"></a>Set:: End (STL/CLR)

Legt das Ende der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator end();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen bidirektionalen Iterator zurück, der direkt hinter das Ende der kontrollierten Sequenz verweist. Sie verwenden Sie, um einen Iterator abzurufen, der das Ende der kontrollierten Sequenz festlegt. der Status ändert sich nicht, wenn sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    Myset::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="setequal_range-stlclr"></a><a name="equal_range"></a>Set:: equal_range (STL/CLR)

Sucht den Bereich, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein paar von Iteratoren zurück `cliext::pair<iterator, iterator>(` [Set:: lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)`(key),` [Set:: upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`. Sie verwenden Sie, um den Bereich der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entsprechen.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_iter Pairii;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

// display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="seterase-stlclr"></a><a name="erase"></a>Set:: Erase (STL/CLR)

Entfernt Elemente an den angegebenen Positionen.

### <a name="syntax"></a>Syntax

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>Parameter

*first*<br/>
Anfang des Bereichs, der gelöscht werden soll.

*key*<br/>
Schlüsselwert, der gelöscht werden soll.

*last*<br/>
Das Ende des zu löschenden Bereichs.

*where*<br/>
Zu Lösch Endes Element.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion entfernt das-Element der kontrollierten Sequenz, auf die von *Where*verwiesen wird, und gibt einen Iterator zurück, der das erste über das entfernte Element hinausgehende Element festlegt, oder [Set:: End (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`, wenn kein solches Element vorhanden ist. Sie verwenden es, um ein einzelnes Element zu entfernen.

Die zweite Member-Funktion entfernt die Elemente der kontrollierten Sequenz im Bereich [`first``last`) und gibt einen Iterator zurück, der das erste Element festlegt, das über alle entfernten Elemente hinausgeht, oder `end()`, wenn kein solches Element vorhanden ist. Sie verwenden Sie, um 0 (null) oder mehrere zusammenhängende Elemente zu entfernen.

Die dritte Member-Funktion entfernt alle Elemente der kontrollierten *Sequenz, deren Schlüssel die entsprechende*Reihenfolge hat, und gibt die Anzahl der entfernten Elemente zurück. Sie verwenden Sie, um alle Elemente zu entfernen und zu zählen, die einem angegebenen Schlüssel entsprechen.

Jede Element Löschung benötigt Zeit proportional zum Logarithmus der Anzahl von Elementen in der gesteuerten Sequenz.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

// add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase all but end
    Myset::iterator it = c1.end();
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

## <a name="setfind-stlclr"></a><a name="find"></a>Set:: Find (STL/CLR)

Sucht ein Element, das einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Wenn mindestens ein Element in der kontrollierten Sequenz eine äquivalente Reihenfolge mit *Key*aufweist, gibt die Member-Funktion einen Iterator zurück, der eines dieser Elemente festlegt. Andernfalls wird [Set:: End (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`zurückgegeben. Sie verwenden Sie, um ein Element zu suchen, das sich derzeit in der kontrollierten Sequenz befindet, die einem angegebenen Schlüssel entspricht.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="setgeneric_container-stlclr"></a><a name="generic_container"></a>Set:: generic_container (STL/CLR)

Der Typ der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt die generische Schnittstelle für diese Vorlagen Container Klasse.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
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

## <a name="setgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>Set:: generic_iterator (STL/CLR)

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
// cliext_set_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="setgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>Set:: generic_reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators, der mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen generischen umgekehrten Iterator, der mit der generischen-Schnittstelle für diese Vorlagen Container Klasse verwendet werden kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_reverse_iterator gcit = gc1->rbegin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="setgeneric_value-stlclr"></a><a name="generic_value"></a>Set:: generic_value (STL/CLR)

Der Typ eines Elements, das mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt vom Typ `GValue`, das den gespeicherten Elementwert zur Verwendung mit der generischen-Schnittstelle für diese Vorlagen Container Klasse beschreibt.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    Myset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get an element and display it
    Myset::generic_iterator gcit = gc1->begin();
    Myset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="setinsert-stlclr"></a><a name="insert"></a>Set:: Insert (STL/CLR)

Fügt Elemente hinzu.

### <a name="syntax"></a>Syntax

```cpp
cliext::pair<iterator, bool> insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>Parameter

*first*<br/>
Anfang des einzufügenden Bereichs.

*last*<br/>
Das Ende des einzufügenden Bereichs.

*right*<br/>
Enumeration, die eingefügt werden soll.

*val*<br/>
Der einzufügende Schlüsselwert.

*where*<br/>
WHERE in Container zum Einfügen (nur Hinweis).

### <a name="remarks"></a>Bemerkungen

Jede der Member-Funktionen fügt eine Sequenz ein, die von den verbleibenden Operanden angegeben wird.

Die erste Member-Funktion versucht, ein Element mit dem Wert *Val*einzufügen, und gibt ein `X`paar Werte zurück. Wenn `X.second` true ist, wird `X.first` das neu eingefügte Element festlegen. Andernfalls `X.first` ein Element mit entsprechender Reihenfolge festgelegt, die bereits vorhanden ist, und es wird kein neues Element eingefügt. Sie verwenden es, um ein einzelnes Element einzufügen.

Die zweite Member-Funktion fügt ein Element mit *dem* Wert *Val*ein, wobei als Hinweis verwendet wird (um die Leistung zu verbessern), und gibt einen Iterator zurück, der das neu eingefügte Element festlegt. Sie verwenden es, um ein einzelnes Element einzufügen, das möglicherweise an ein Element angrenzt, das Sie kennen.

Die dritte Member-Funktion fügt die Sequenz [`first``last`) ein. Sie verwenden Sie, um NULL oder mehr Elemente einzufügen, die aus einer anderen Sequenz kopiert wurden.

Die vierte Member-Funktion fügt die von der *rechten Seite*festgelegte Sequenz ein. Sie verwenden Sie zum Einfügen einer Sequenz, die von einem Enumerator beschrieben wird.

Jede Element Einfügung nimmt Zeit proportional zum Logarithmus der Anzahl von Elementen in der gesteuerten Sequenz auf. Die Einfügung kann in amortisierter konstanter Zeit auftreten, bei Angabe eines Hinweises, der ein Element angibt, das sich neben der Einfügemarke befindet.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
typedef Myset::pair_iter_bool Pairib;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value, unique and duplicate
    Pairib pair1 = c1.insert(L'x');
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",
        *pair1.first, pair1.second);

    pair1 = c1.insert(L'b');
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",
        *pair1.first, pair1.second);

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an iterator range
    Myset c2;
    Myset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an enumeration
    Myset c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = [x True]
insert(L'b') = [b False]
a b c x
insert(begin(), L'y') = y
a b c x y
a b c x
a b c x y
```

## <a name="setiterator-stlclr"></a><a name="iterator"></a>Set:: Iterator (STL/CLR)

Der Typ eines Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T1`, das als bidirektionaler Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setkey_comp-stlclr"></a><a name="key_comp"></a>Set:: key_comp (STL/CLR)

Kopiert den Bestell Delegaten für zwei Schlüssel.

### <a name="syntax"></a>Syntax

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Sortier Delegaten zurück, der zum Sortieren der kontrollierten Sequenz verwendet wird. Damit können Sie zwei Schlüssel vergleichen.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
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

## <a name="setkey_compare-stlclr"></a><a name="key_compare"></a>Set:: key_compare (STL/CLR)

Der Bestell Delegat für zwei Schlüssel.

### <a name="syntax"></a>Syntax

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Delegaten, der die Reihenfolge seiner Schlüssel Argumente bestimmt.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

// test a different ordering rule
    Myset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
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

## <a name="setkey_type-stlclr"></a><a name="key_type"></a>Set:: key_type (STL/CLR)

Der Typ eines Sortierschlüssels.

### <a name="syntax"></a>Syntax

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter *Schlüssel*.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using key_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setlower_bound-stlclr"></a><a name="lower_bound"></a>Set:: lower_bound (STL/CLR)

Sucht den Anfang des Bereichs, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion bestimmt das erste Element `X` in der gesteuerten *Sequenz, das*eine entsprechende Reihenfolge aufweist. Wenn kein solches Element vorhanden ist, wird [Set:: End (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; zurückgegeben. Andernfalls wird ein Iterator zurückgegeben, der `X`festlegt. Sie verwenden Sie, um den Anfang einer Sequenz von Elementen zu suchen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entsprechen.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="setmake_value-stlclr"></a><a name="make_value"></a>Set:: make_value (STL/CLR)

Erstellt ein Wertobjekt.

### <a name="syntax"></a>Syntax

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu verwendende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein `value_type` Objekt zurück, *dessen Schlüssel Key ist.* Sie verwenden es, um ein Objekt zu verfassen, das für die Verwendung mit mehreren anderen Element Funktionen geeignet ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(Myset::make_value(L'a'));
    c1.insert(Myset::make_value(L'b'));
    c1.insert(Myset::make_value(L'c'));

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setoperator-stlclr"></a><a name="op_as"></a>Set:: Operator = (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
set<Key>% operator=(set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Der zu kopierende Container.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann `*this`zurück. Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (Myset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="setrbegin-stlclr"></a><a name="rbegin"></a>Set:: rbegin (STL/CLR)

Legt den Anfang der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen reverse-Iterator zurück, der das letzte Element der kontrollierten Sequenz festlegt, oder direkt hinter dem Anfang einer leeren Sequenz. Demzufolge wird der `beginning` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    Myset::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="setreference-stlclr"></a><a name="reference"></a>Set:: Reference (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    Myset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="setrend-stlclr"></a><a name="rend"></a>Set:: rend (STL/CLR)

Legt das Ende der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen reverse-Iterator zurück, der direkt hinter den Anfang der kontrollierten Sequenz verweist. Demzufolge wird der `end` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der das `current` Ende der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    Myset::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="setreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>Set:: reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T3`, das als umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" reversed
    Myset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="setset-stlclr"></a><a name="set"></a>Set:: Set (STL/CLR)

Erstellt ein container-Objekt.

### <a name="syntax"></a>Syntax

```cpp
set();
explicit set(key_compare^ pred);
set(set<Key>% right);
set(set<Key>^ right);
template<typename InIter>
    setset(InIter first, InIter last);
template<typename InIter>
    set(InIter first, InIter last,
        key_compare^ pred);
set(System::Collections::Generic::IEnumerable<GValue>^ right);
set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>Parameter

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

`set();`

Initialisiert die gesteuerte Sequenz ohne Elemente, wobei das standardmäßige Reihen folgen Prädikat `key_compare()`ist. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem Standard Reihen folgen Prädikat anzugeben.

Der Konstruktor:

`explicit set(key_compare^ pred);`

Initialisiert die gesteuerte Sequenz ohne Elemente mit dem *Prädikat pred*für die Reihenfolge. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem angegebenen Reihen folgen Prädikat anzugeben.

Der Konstruktor:

`set(set<Key>% right);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`right.begin()``right.end()`) mit dem Standard Reihen folgen Prädikat. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, bei der es sich um eine Kopie der Sequenz handelt, die vom Set-Objekt *Rechts*gesteuert wird, mit dem Standard Reihen folgen Prädikat.

Der Konstruktor:

`set(set<Key>^ right);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`right->begin()``right->end()`) mit dem Standard Reihen folgen Prädikat. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, bei der es sich um eine Kopie der Sequenz handelt, die vom Set-Objekt *Rechts*gesteuert wird, mit dem Standard Reihen folgen Prädikat.

Der Konstruktor:

`template<typename InIter> set(InIter first, InIter last);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`first``last`) mit dem Standard Reihen folgen Prädikat. Sie verwenden es, um die gesteuerte Sequenz mit dem Standard Reihen folgen Prädikat zu einer Kopie einer anderen Sequenz zu machen.

Der Konstruktor:

`template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`first``last`) mit dem *Prädikat pred*für die Reihenfolge. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz mit dem angegebenen Reihen folgen Prädikat zu machen.

Der Konstruktor:

`set(System::Collections::Generic::IEnumerable<Key>^ right);`

Initialisiert die gesteuerte Sequenz mit der durch den enumeratorrecht bezeichneten *right*Sequenz mit dem Standard Reihen folgen Prädikat. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator mit dem Standard Reihen folgen Prädikat beschrieben wird.

Der Konstruktor:

`set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Initialisiert die gesteuerte Sequenz mit der durch den enumeratorrecht bezeichneten *right*Sequenz mit dem *Prädikat pred*für die Reihenfolge. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator mit dem angegebenen Reihen folgen Prädikat beschrieben wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
// construct an empty container
    Myset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an ordering rule
    Myset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    Myset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range and an ordering rule
    Myset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    Myset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration and an ordering rule
    Myset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct from a generic container
    Myset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Myset c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
c b a
a b c
c b a
a b c
c b a
c b a
a b c
```

## <a name="setsize-stlclr"></a><a name="size"></a>Set:: Size (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden Sie, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden. Wenn Sie nur für Sie wichtig sind, ob die Sequenz eine Größe ungleich NULL aufweist, finden Sie weitere Informationen unter [Set:: Empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

// add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
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

## <a name="setsize_type-stlclr"></a><a name="size_type"></a>Set:: size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Myset::size_type diff = 0;
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="setswap-stlclr"></a><a name="swap"></a>Set:: Swap (STL/CLR)

Vertauscht den Inhalt von zwei Containern.

### <a name="syntax"></a>Syntax

```cpp
void swap(set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Container für den Tausch von Inhalten.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht die kontrollierten Sequenzen zwischen `this` und *Rechts*aus. Dies erfolgt in konstanter Zeit und löst keine Ausnahmen aus. Sie verwenden Sie als schnelle Möglichkeit, um den Inhalt von zwei Containern auszutauschen.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    Myset c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
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
d e f
d e f
a b c
```

## <a name="setto_array-stlclr"></a><a name="to_array"></a>Set:: to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein Array mit der kontrollierten Sequenz zurück. Sie verwenden Sie, um eine Kopie der kontrollierten Sequenz in Array Form abzurufen.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
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

## <a name="setupper_bound-stlclr"></a><a name="upper_bound"></a>Set:: upper_bound (STL/CLR)

Findet das Ende des Bereichs, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion bestimmt das letzte Element `X` in der gesteuerten *Sequenz, das*eine entsprechende Reihenfolge aufweist. Wenn kein solches Element vorhanden ist oder `X` das letzte Element in der kontrollierten Sequenz ist, wird [Set:: End (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; zurückgegeben. Andernfalls wird ein Iterator zurückgegeben, der das erste Element über `X`hinaus festlegt. Sie verwenden es, um das Ende einer Sequenz von Elementen zu suchen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entspricht.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="setvalue_comp-stlclr"></a><a name="value_comp"></a>Set:: value_comp (STL/CLR)

Kopiert den Bestell Delegaten für zwei Element Werte.

### <a name="syntax"></a>Syntax

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Sortier Delegaten zurück, der zum Sortieren der kontrollierten Sequenz verwendet wird. Sie verwenden Sie, um zwei Element Werte zu vergleichen.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="setvalue_compare-stlclr"></a><a name="value_compare"></a>Set:: Value_compare (STL/CLR)

Der Bestell Delegat für zwei Element Werte.

### <a name="syntax"></a>Syntax

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Delegaten, der die Reihenfolge seiner Wert Argumente bestimmt.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    Myset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="setvalue_type-stlclr"></a><a name="value_type"></a>Set:: value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `generic_value`.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c" using value_type
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operator-set-stlclr"></a><a name="op_neq"></a>Operator! = (Set) (STL/CLR)

Die Liste entspricht nicht dem Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator!=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt `!(left == right)`zurück. Sie verwenden es, um zu testen, ob *left* nicht denselben Wert hat wie *Rechts* , wenn die beiden Mengen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="operatorlt-set-stlclr"></a><a name="op_lt"></a>Operator&lt; (Set) (STL/CLR)

Liste kleiner als-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator<(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt true zurück, wenn für die niedrigste Position `i` für die `!(right[i] < left[i])` auch true ist, dass `left[i] < right[i]`. Andernfalls wird zurückgegeben, `left->size() < right->size()` Sie es verwenden, um zu testen, ob *left* vor *Rechts* geordnet ist, wenn die beiden Mengen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="operatorlt-set-stlclr"></a><a name="op_lteq"></a>Operator&lt;= (Set) (STL/CLR)

Liste kleiner oder gleich-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator<=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt `!(right < left)`zurück. Sie verwenden es, um zu testen, ob *left* nach *Rechts* nicht geordnet ist, wenn die beiden Mengen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="operator-set-stlclr"></a><a name="op_eq"></a>Operator = = (Set) (STL/CLR)

Auflisten des gleichen Vergleichs.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator==(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt nur dann true zurück, wenn die von *Links* und *Rechts* gesteuerten Sequenzen die gleiche Länge aufweisen und für jede Position `i``left[i] ==` `right[i]`. Sie verwenden es, um zu überprüfen, ob *Links* mit *right* dem Element by-Element verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="operatorgt-set-stlclr"></a><a name="op_gt"></a>Operator&gt; (Set) (STL/CLR)

Die Liste ist größer als der Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator>(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt `right` `<` `left`zurück. Sie verwenden es, um zu überprüfen, ob *Links* nach *Rechts* angeordnet ist, wenn die beiden Mengen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="operatorgt-set-stlclr"></a><a name="op_gteq"></a>Operator&gt;= (Set) (STL/CLR)

Liste größer oder gleich-Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator>=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*left*<br/>
Linker zu vergleichender Container.

*right*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operator-Funktion gibt `!(left < right)`zurück. Sie verwenden es, um zu testen, ob *left* nicht vor *Rechts* geordnet ist, wenn die beiden Mengen Element Weise verglichen werden.

### <a name="example"></a>Beispiel

```cpp
// cliext_set_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::set<wchar_t> Myset;
int main()
    {
    Myset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Myset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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
