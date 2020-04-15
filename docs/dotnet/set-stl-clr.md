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
ms.openlocfilehash: 38b0a3278efd10ef5cc989a5fc900bf82d377eae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320307"
---
# <a name="set-stlclr"></a>set (STL/CLR)

Die Vorlagenklasse beschreibt ein Objekt, das eine Sequenz unterschiedlicher Länge von Elementen mit bidirektionadem Zugriff steuert. Sie verwenden `set` den Container, um eine Sequenz von Elementen als (fast) ausgeglichenen geordneten Knotenbaum zu verwalten, in dem jeweils ein Element gespeichert wird.

In der beschreibung `GValue` unten ist `GKey`die gleiche wie , die wiederum ist die gleiche wie *Key,* es sei denn, letztere ist ein ref-Typ, in diesem Fall ist `Key^`es .

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

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<cliext/set>

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[set::const_iterator (STL/CLR)](#const_iterator)|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|[set::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.|
|[set::difference_type (STL/CLR)](#difference_type)|Der Typ eines (möglicherweise signierten) Abstands zwischen zwei Elementen.|
|[set::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container.|
|[set::generic_iterator (STL/CLR)](#generic_iterator)|Der Typ eines Iterators für die generische Schnittstelle für den Container.|
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Der Typ eines umgekehrten Iterators für die generische Schnittstelle für den Container.|
|[set::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container.|
|[set::iterator (STL/CLR)](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[set::key_compare (STL/CLR)](#key_compare)|Der Stellvertretung für zwei Schlüssel.|
|[set::key_type (STL/CLR)](#key_type)|Der Typ eines Sortierschlüssels.|
|[set::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.|
|[set::size_type (STL/CLR)](#size_type)|Der Typ eines (nicht negativen) Abstands zwischen zwei Elementen.|
|[set::value_compare (STL/CLR)](#value_compare)|Der Stellvertretung für zwei Elementwerte.|
|[set::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[set::begin (STL/CLR)](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[set::clear (STL/CLR)](#clear)|Entfernt alle Elemente.|
|[set::count (STL/CLR)](#count)|Zählt Elemente, die einem angegebenen Schlüssel entsprechen.|
|[set::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[set::end (STL/CLR)](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[set::equal_range (STL/CLR)](#equal_range)|Sucht den Bereich, der einem angegebenen Schlüssel entspricht.|
|[set::erase (STL/CLR)](#erase)|Entfernt Elemente an den angegebenen Positionen.|
|[set::find (STL/CLR)](#find)|Sucht ein Element, das einem angegebenen Schlüssel entspricht.|
|[set::insert (STL/CLR)](#insert)|Fügt Elemente hinzu.|
|[set::key_comp (STL/CLR)](#key_comp)|Kopiert den Stellvertretung für zwei Schlüssel.|
|[set::lower_bound (STL/CLR)](#lower_bound)|Sucht den Anfang des Bereichs, der mit einem angegebenen Schlüssel übereinstimmt.|
|[set::make_value (STL/CLR)](#make_value)|Erstellt ein Wertobjekt.|
|[set::rbegin (STL/CLR)](#rbegin)|Legt den Anfang der umgekehrten kontrollierten Sequenz fest.|
|[set::rend (STL/CLR)](#rend)|Legt das Ende der umgekehrten kontrollierten Sequenz fest.|
|[set::set (STL/CLR)](#set)|Erstellt ein container-Objekt.|
|[set::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[set::swap (STL/CLR)](#swap)|Vertauscht den Inhalt von zwei Containern.|
|[set::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|
|[set::upper_bound (STL/CLR)](#upper_bound)|Sucht das Ende des Bereichs, der mit einem angegebenen Schlüssel übereinstimmt.|
|[set::value_comp (STL/CLR)](#value_comp)|Kopiert den Stellvertretung für zwei Elementwerte.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[set::operator= (STL/CLR)](#op_as)|Ersetzt die kontrollierte Sequenz.|
|[Operator!= (Set) (STL/CLR)](#op_neq)|Bestimmt, `set` ob ein Objekt `set` nicht mit einem anderen Objekt gleich ist.|
|[Operator< (Set) (STL/CLR)](#op_lt)|Bestimmt, `set` ob ein Objekt `set` kleiner als ein anderes Objekt ist.|
|[Operator<= (Set) (STL/CLR)](#op_lteq)|Bestimmt, `set` ob ein Objekt kleiner `set` oder gleich einem anderen Objekt ist.|
|[operator== (set) (STL/CLR)](#op_eq)|Bestimmt, `set` ob ein Objekt `set` einem anderen Objekt gleich ist.|
|[Operator> (Set) (STL/CLR)](#op_gt)|Bestimmt, `set` ob ein Objekt `set` größer als ein anderes Objekt ist.|
|[Operator>= (Set) (STL/CLR)](#op_gteq)|Bestimmt, `set` ob ein Objekt größer `set` oder gleich einem anderen Objekt ist.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren Sie ein Objekt.|
|<xref:System.Collections.IEnumerable>|Sequenz durch Elemente.|
|<xref:System.Collections.ICollection>|Verwalten Sie eine Gruppe von Elementen.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sequenz durch typisierte Elemente.|
|<xref:System.Collections.Generic.ICollection%601>|Verwalten Sie eine Gruppe typisierter Elemente.|
|ITree-Schlüssel,\<>|Verwalten Sie generische Container.|

## <a name="remarks"></a>Bemerkungen

Das Objekt reserviert und gibt Speicher für die Sequenz frei, die es als einzelne Knoten steuert. Es fügt Elemente in einen (fast) ausgeglichenen Baum ein, den es sortiert hält, indem die Verknüpfungen zwischen Knoten geändert werden, niemals durch Kopieren des Inhalts eines Knotens in einen anderen. Das bedeutet, dass Sie Elemente frei einfügen und entfernen können, ohne die verbleibenden Elemente zu stören.

Das Objekt ordnet die Sequenz an, die es steuert, indem es ein gespeichertes Delegatobjekt vom Typ [set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)aufruft. Sie können das gespeicherte Delegatobjekt angeben, wenn Sie den Satz erstellen. Wenn Sie kein Delegatobjekt angeben, ist der Standardwert der Vergleich `operator<(key_type, key_type)`. Sie greifen auf dieses gespeicherte Objekt zu, indem Sie den Memberfunktionssatz::key_comp [(STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`aufrufen.

Ein solches Delegatobjekt muss Schlüsseln vom Typ [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)eine strikt schwache Reihenfolge auferlegen. Das bedeutet für zwei `X` `Y`beliebige Schlüssel und:

`key_comp()(X, Y)`gibt bei jedem Anruf dasselbe boolesche Ergebnis zurück.

Wenn `key_comp()(X, Y)` wahr ist, dann `key_comp()(Y, X)` muss falsch sein.

Wenn `key_comp()(X, Y)` wahr ist, dann `X` wird `Y`gesagt, vor bestellt werden .

Wenn `!key_comp()(X, Y) && !key_comp()(Y, X)` wahr ist, dann `X` und `Y` sollen gleichwertige Bestellung haben.

Für jedes `X` Element, `Y` das in der `key_comp()(Y, X)` gesteuerten Sequenz vorangeht, ist false. (Für das Standarddelegatobjekt verringern Schlüssel nie den Wert.) Im Gegensatz zum Vorlagenklassensatz `set` erfordert ein Objekt der Vorlagenklasse nicht, dass Schlüssel für alle Elemente eindeutig sind. [set](../dotnet/set-stl-clr.md) (Zwei oder mehr Schlüssel können eine gleichwertige Bestellung haben.)

Jedes Element dient sowohl als Ey als auch als Wert. Die Sequenz wird so dargestellt, dass das Suchen, Einfügen und Entfernen eines beliebigen Elements mit einer Anzahl von Operationen proportional zum Logarithmus der Anzahl der Elemente in der Sequenz (logarithmische Zeit) ermöglicht wird. Darüber hinaus führt das Einfügen eines Elements nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen eines Elements werden nur solche Iteratoren ungültig, die auf das entfernte Element gezeigt haben.

Ein Satz unterstützt bidirektionale Iteratoren, d. h., Sie können zu benachbarten Elementen schritt, wenn Sie einen Iterator erhalten, der ein Element in der gesteuerten Sequenz bezeichnet. Ein spezieller Kopfknoten entspricht dem iterator, der von [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`zurückgegeben wird. Sie können diesen Iterator dekrementieren, um das letzte Element in der gesteuerten Sequenz zu erreichen, falls vorhanden. Sie können einen festgelegten Iterator in den Kopfknoten erhöhen `end()`und dann gleich vergleichen. Sie können jedoch den von `end()`zurückgegebenen Iterator nicht dereferenzieren.

Beachten Sie, dass Sie nicht direkt auf ein set-Element verweisen können, da es seine numerische Position hat , die einen Iterator mit zufälligem Zugriff erfordert.

Ein Set-Iterator speichert ein Handle in seinem zugeordneten Satzknoten, der wiederum ein Handle in seinem zugeordneten Container speichert. Sie können Iteratoren nur mit den zugehörigen Containerobjekten verwenden. Ein Set-Iterator bleibt gültig, solange der zugehörige Satzknoten mit einem Satz verknüpft ist. Darüber hinaus ist ein gültiger Iterator dereferencable -- Sie können ihn verwenden, um auf den `end()`von ihm bezeichneten Elementwert zuzugreifen oder ihn zu ändern -- solange er nicht gleich ist.

Durch das Löschen oder Entfernen eines Elements wird der Destruktor für seinen gespeicherten Wert aufgesucht. Durch das Zerstören des Containers werden alle Elemente ausdemaiert. Daher stellt ein Container, dessen Elementtyp eine ref-Klasse ist, sicher, dass keine Elemente den Container überdauern. Beachten Sie jedoch, dass ein Container mit Handles seine Elemente *nicht* zerstört.

## <a name="members"></a>Member

## <a name="setbegin-stlclr"></a><a name="begin"></a>eingestellt::begin (STL/CLR)

Legt den Anfang der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator begin();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen bidirektionalen Iterator zurück, der das erste Element der gesteuerten Sequenz oder knapp über das Ende einer leeren Sequenz hinaus bezeichnet. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

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

## <a name="setclear-stlclr"></a><a name="clear"></a>eingestellt::klar (STL/CLR)

Entfernt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft [set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`())`effektiv auf. Sie verwenden es, um sicherzustellen, dass die gesteuerte Sequenz leer ist.

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

## <a name="setconst_iterator-stlclr"></a><a name="const_iterator"></a>eingestellt::const_iterator (STL/CLR)

Der Typ eines konstanten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt `T2` unbestimmten Typs, das als konstanter bidirektionaler Iterator für die gesteuerte Sequenz dienen kann.

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

## <a name="setconst_reference-stlclr"></a><a name="const_reference"></a>eingestellt::const_reference (STL/CLR)

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

## <a name="setconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>eingestellt::const_reverse_iterator (STL/CLR)

Der Typ eines konstanten Umgekehrtitators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt `T4` unbestimmten Typs, das als konstanter umgekehrter Iterator für die gesteuerte Sequenz dienen kann.

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

## <a name="setcount-stlclr"></a><a name="count"></a>eingestellt::anzahl (STL/CLR)

Sucht die Anzahl von Elementen, die einem angegebenen Schlüssel entsprechen.

### <a name="syntax"></a>Syntax

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Anzahl der Elemente in der gesteuerten Reihenfolge zurück, die eine entsprechende Reihenfolge mit *Key*aufweisen. Damit können Sie die Anzahl der Elemente in der kontrollierten Sequenz ermitteln, die derzeit einem angegebenen Schlüssel entsprechen.

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

## <a name="setdifference_type-stlclr"></a><a name="difference_type"></a>satz::difference_type (STL/CLR)

Die Typen eines signierten Abstands zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine möglicherweise negative Elementanzahl.

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

## <a name="setempty-stlclr"></a><a name="empty"></a>eingestellt::leer (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Es entspricht [set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`. Sie verwenden es, um zu testen, ob der Satz leer ist.

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

## <a name="setend-stlclr"></a><a name="end"></a>eingestellt::end (STL/CLR)

Legt das Ende der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator end();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen bidirektionalen Iterator zurück, der direkt über das Ende der gesteuerten Sequenz zeigt. Sie verwenden es, um einen Iterator zu erhalten, der das Ende der gesteuerten Sequenz bezeichnet. sein Status ändert sich nicht, wenn sich die Länge der gesteuerten Sequenz ändert.

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

## <a name="setequal_range-stlclr"></a><a name="equal_range"></a>eingestellt::equal_range (STL/CLR)

Sucht den Bereich, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt ein Paar `cliext::pair<iterator, iterator>(` von Iteratoren [zurück: lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`. Sie verwenden es, um den Bereich der Elemente zu bestimmen, die derzeit in der gesteuerten Sequenz sind, die mit einem angegebenen Schlüssel übereinstimmen.

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

## <a name="seterase-stlclr"></a><a name="erase"></a>eingestellt::löschen (STL/CLR)

Entfernt Elemente an den angegebenen Positionen.

### <a name="syntax"></a>Syntax

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>Parameter

*first*<br/>
Beginn des Bereichs zu löschen.

*key*<br/>
Schlüsselwert zum Löschen.

*last*<br/>
Ende des Bereichs zu löschen.

*where*<br/>
Element, das löscht werden soll.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion entfernt das Element der gesteuerten Sequenz, auf die von *where*verwiesen wird, und gibt einen Iterator zurück, der das erste Element angibt, das über das entfernte Element hinaus verbleibt, oder [set::end (STL/CLR),](../dotnet/set-end-stl-clr.md) `()` wenn kein solches Element vorhanden ist. Sie verwenden es, um ein einzelnes Element zu entfernen.

Die zweite Memberfunktion entfernt die Elemente der gesteuerten Sequenz im Bereich [`first`, `last`und gibt einen Iterator `end()` zurück, der das erste Element angibt, das über alle entfernten Elemente hinaus bleibt, oder wenn kein solches Element vorhanden ist. Sie verwenden es, um null oder mehr zusammenhängende Elemente zu entfernen.

Die dritte Memberfunktion entfernt jedes Element der gesteuerten Sequenz, dessen Schlüssel eine entsprechende Reihenfolge wie *Key*aufweist, und gibt eine Anzahl der entfernten Elemente zurück. Sie verwenden es, um alle Elemente zu entfernen und zu zählen, die mit einem angegebenen Schlüssel übereinstimmen.

Jede Elementlöschung nimmt Zeit in Anspruch, proportional zum Logarithmus der Anzahl der Elemente in der gesteuerten Sequenz.

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

## <a name="setfind-stlclr"></a><a name="find"></a>eingestellt::find (STL/CLR)

Sucht ein Element, das einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Wenn mindestens ein Element in der gesteuerten Sequenz eine gleichwertige Reihenfolge mit *Key*aufweist, gibt die Memberfunktion einen Iterator zurück, der eines dieser Elemente angibt. Andernfalls wird [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`zurückgegeben. Sie verwenden es, um ein Element zu suchen, das sich derzeit in der gesteuerten Sequenz befindet, das mit einem angegebenen Schlüssel übereinstimmt.

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

## <a name="setgeneric_container-stlclr"></a><a name="generic_container"></a>eingestellt::generic_container (STL/CLR)

Der Typ der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt die generische Schnittstelle für diese Vorlagencontainerklasse.

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

## <a name="setgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>eingestellt::generic_iterator (STL/CLR)

Der Typ eines Iterators zur Verwendung mit der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen generischen Iterator, der mit der generischen Schnittstelle für diese Vorlagencontainerklasse verwendet werden kann.

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

## <a name="setgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>eingestellt::generic_reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators für die Verwendung mit der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen generischen Reverse-Iterator, der mit der generischen Schnittstelle für diese Vorlagencontainerklasse verwendet werden kann.

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

## <a name="setgeneric_value-stlclr"></a><a name="generic_value"></a>eingestellt::generic_value (STL/CLR)

Der Typ eines Elements für die Verwendung mit der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein `GValue` Objekt vom Typ, das den gespeicherten Elementwert für die Verwendung mit der generischen Schnittstelle für diese Vorlagencontainerklasse beschreibt.

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

## <a name="setinsert-stlclr"></a><a name="insert"></a>eingestellt::einfügen (STL/CLR)

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
Ende des einzufügenden Bereichs.

*Richting*<br/>
Enumeration, die eingefügt werden soll.

*Val*<br/>
Schlüsselwert, den eingefügt werden soll.

*where*<br/>
Wo im Behälter eingefügt werden soll (nur Hinweis).

### <a name="remarks"></a>Bemerkungen

Jede der Memberfunktionen fügt eine Sequenz ein, die von den verbleibenden Operanden angegeben wird.

Die erste Memberfunktion versucht, ein *val*Element mit dem Wert `X`val einzufügen, und gibt ein Paar von Werten zurück. Wenn `X.second` true `X.first` ist, bezeichnet das neu eingefügte Element. bestimmt `X.first` andernfalls ein Element mit einer entsprechenden Reihenfolge, das bereits vorhanden ist, und es wird kein neues Element eingefügt. Sie verwenden es, um ein einzelnes Element einzufügen.

Die zweite Memberfunktion fügt ein Element mit dem Wert *val*ein, wobei *sie als* Hinweis verwendet wird (zur Verbesserung der Leistung), und einen Iterator zurückgibt, der das neu eingefügte Element kennzeichnet. Sie verwenden es, um ein einzelnes Element einzufügen, das an ein Element angrenzt, das Sie kennen.

Die dritte Memberfunktion fügt`first`die `last`Sequenz [ , . Sie verwenden es, um null oder mehr Elemente einzufügen, die aus einer anderen Sequenz kopiert wurden.

Die vierte Memberfunktion fügt die von der *rechten*bezeichnete Sequenz ein. Sie verwenden es, um eine Sequenz einzufügen, die von einem Enumerator beschrieben wird.

Jede Elementeinfügung nimmt Zeit in Derproportional zum Logarithmus der Anzahl der Elemente in der gesteuerten Sequenz. Das Einfügen kann jedoch in der amortisierten konstanten Zeit erfolgen, wenn ein Hinweis gegeben wird, der ein Element neben der Einfügemarke bezeichnet.

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

## <a name="setiterator-stlclr"></a><a name="iterator"></a>eingestellt::iterator (STL/CLR)

Der Typ eines Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt `T1` unbestimmten Typs, das als bidirektionaler Iterator für die gesteuerte Sequenz dienen kann.

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

## <a name="setkey_comp-stlclr"></a><a name="key_comp"></a>eingestellt::key_comp (STL/CLR)

Kopiert den Stellvertretung für zwei Schlüssel.

### <a name="syntax"></a>Syntax

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt den Sortierstellatlegor zurück, der zum Bestellen der gesteuerten Sequenz verwendet wird. Damit können Sie zwei Schlüssel vergleichen.

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

## <a name="setkey_compare-stlclr"></a><a name="key_compare"></a>eingestellt::key_compare (STL/CLR)

Der Stellvertretung für zwei Schlüssel.

### <a name="syntax"></a>Syntax

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Delegaten, der die Reihenfolge seiner Hauptargumente bestimmt.

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

## <a name="setkey_type-stlclr"></a><a name="key_type"></a>eingestellt::key_type (STL/CLR)

Der Typ eines Sortierschlüssels.

### <a name="syntax"></a>Syntax

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter *Key*.

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

## <a name="setlower_bound-stlclr"></a><a name="lower_bound"></a>eingestellt::lower_bound (STL/CLR)

Sucht den Anfang des Bereichs, der mit einem angegebenen Schlüssel übereinstimmt.

### <a name="syntax"></a>Syntax

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bestimmt `X` das erste Element in der gesteuerten Sequenz, das eine entsprechende Reihenfolge wie *Key*aufweist. Wenn kein solches Element vorhanden ist, gibt es [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`zurück; Andernfalls wird ein Iterator `X`zurückgegeben, der bezeichnet. Sie verwenden es, um den Anfang einer Sequenz von Elementen zu finden, die sich derzeit in der gesteuerten Sequenz befinden, die mit einem angegebenen Schlüssel übereinstimmen.

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

## <a name="setmake_value-stlclr"></a><a name="make_value"></a>eingestellt::make_value (STL/CLR)

Erstellt ein Wertobjekt.

### <a name="syntax"></a>Syntax

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Schlüsselwert, der verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `value_type` gibt ein Objekt zurück, dessen Schlüssel *der Schlüssel*ist. Sie verwenden es, um ein Objekt zu verfassen, das für die Verwendung mit mehreren anderen Memberfunktionen geeignet ist.

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

## <a name="setoperator-stlclr"></a><a name="op_as"></a>eingestellt::operator= (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
set<Key>% operator=(set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Der zu kopierende Container.

### <a name="remarks"></a>Bemerkungen

Der Memberoperator kopiert *das Recht* `*this`auf das Objekt und gibt dann zurück. Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz *rechts*zu ersetzen.

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

## <a name="setrbegin-stlclr"></a><a name="rbegin"></a>eingestellt::rbegin (STL/CLR)

Legt den Anfang der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen umgekehrten Iterator zurück, der das letzte Element der gesteuerten Sequenz oder knapp über den Anfang einer leeren Sequenz hinaus bezeichnet. Demzufolge wird der `beginning` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

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

## <a name="setreference-stlclr"></a><a name="reference"></a>eingestellt::Referenz (STL/CLR)

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

## <a name="setrend-stlclr"></a><a name="rend"></a>eingestellt::rend (STL/CLR)

Legt das Ende der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen umgekehrten Iterator zurück, der direkt über den Anfang der gesteuerten Sequenz hinaus zeigt. Demzufolge wird der `end` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der das `current` Ende der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

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

## <a name="setreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>eingestellt::reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt `T3` unbestimmten Typs, das als umgekehrter Iterator für die gesteuerte Sequenz dienen kann.

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

## <a name="setset-stlclr"></a><a name="set"></a>eingestellt::set (STL/CLR)

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
Ende des einzufügenden Bereichs.

*Pred*<br/>
Bestellprädikat für die kontrollierte Sequenz.

*Richting*<br/>
Einzufügendes Objekt bzw. einzufügender Bereich.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`set();`

initialisiert die gesteuerte Sequenz ohne Elemente, mit `key_compare()`dem Standard-Bestellprädikat . Sie verwenden es, um eine leere anfangs gesteuerte Sequenz mit dem Standard-Sortierprädikat anzugeben.

Der Konstruktor:

`explicit set(key_compare^ pred);`

initialisiert die gesteuerte Sequenz ohne Elemente, mit dem Bestellprädikat *vor*. Sie verwenden es, um eine leere anfangsgesteuerte Sequenz mit dem angegebenen Sortierprädikat anzugeben.

Der Konstruktor:

`set(set<Key>% right);`

initialisiert die gesteuerte Sequenz`right.begin()`mit `right.end()`der Sequenz [ , ) mit dem Standard-Sordenprädikat. Sie verwenden es, um eine erste gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom set object *right*gesteuert wird, mit dem Standard-Sortierprädikat.

Der Konstruktor:

`set(set<Key>^ right);`

initialisiert die gesteuerte Sequenz`right->begin()`mit `right->end()`der Sequenz [ , ) mit dem Standard-Sordenprädikat. Sie verwenden es, um eine erste gesteuerte Sequenz anzugeben, die eine Kopie der Sequenz ist, die vom set object *right*gesteuert wird, mit dem Standard-Sortierprädikat.

Der Konstruktor:

`template<typename InIter> set(InIter first, InIter last);`

initialisiert die gesteuerte Sequenz`first`mit `last`der Sequenz [ , ) mit dem Standard-Sordenprädikat. Sie verwenden es, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz mit dem Standard-Bestellprädikat zu machen.

Der Konstruktor:

`template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`

initialisiert die gesteuerte Sequenz`first`mit `last`der Sequenz [ , ), mit dem Bestellprädikat *vor .* Sie verwenden es, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz mit dem angegebenen Sortierprädikat zu machen.

Der Konstruktor:

`set(System::Collections::Generic::IEnumerable<Key>^ right);`

initialisiert die gesteuerte Sequenz mit der sequenz, *right*die vom Enumeratorrecht mit dem Standard-Bestellprädikat bezeichnet wird. Sie verwenden sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator mit dem Standard-Bestellprädikat beschrieben wird.

Der Konstruktor:

`set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

initialisiert die gesteuerte Sequenz mit der sequenziums, die vom Enumerator *recht*bezeichnet wird, mit dem Bestellprädikat *pred*. Sie verwenden sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator mit dem angegebenen Sortierprädikat beschrieben wird.

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

## <a name="setsize-stlclr"></a><a name="size"></a>eingestellt::Größe (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden es, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der gesteuerten Sequenz befinden. Wenn Ihnen nur wichtig ist, ob die Sequenz eine Größe ungleich Null hat, siehe [set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`.

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

## <a name="setsize_type-stlclr"></a><a name="size_type"></a>eingestellt::size_type (STL/CLR)

Der Typ eines signierten Abstands zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Elementanzahl.

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

## <a name="setswap-stlclr"></a><a name="swap"></a>eingestellt::swap (STL/CLR)

Vertauscht den Inhalt von zwei Containern.

### <a name="syntax"></a>Syntax

```cpp
void swap(set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Container für den Tausch von Inhalten.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion tauscht die `this` gesteuerten Sequenzen zwischen und *rechts.* Es tut dies in konstanter Zeit und es löst keine Ausnahmen aus. Sie verwenden es als schnelle Möglichkeit, den Inhalt von zwei Containern auszutauschen.

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

## <a name="setto_array-stlclr"></a><a name="to_array"></a>eingestellt::to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt ein Array zurück, das die gesteuerte Sequenz enthält. Sie verwenden es, um eine Kopie der gesteuerten Sequenz in Array-Form zu erhalten.

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

## <a name="setupper_bound-stlclr"></a><a name="upper_bound"></a>eingestellt::upper_bound (STL/CLR)

Sucht das Ende des Bereichs, der mit einem angegebenen Schlüssel übereinstimmt.

### <a name="syntax"></a>Syntax

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bestimmt `X` das letzte Element in der gesteuerten Sequenz, das eine entsprechende Reihenfolge wie *Key*aufweist. Wenn kein solches Element `X` vorhanden ist oder wenn es das letzte Element in der gesteuerten Sequenz ist, gibt es [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`zurück; Andernfalls wird ein Iterator zurückgegeben, der `X`das erste Element über bezeichnet. Sie verwenden es, um das Ende einer Sequenz von Elementen zu finden, die sich derzeit in der gesteuerten Sequenz befinden, die mit einem angegebenen Schlüssel übereinstimmen.

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

## <a name="setvalue_comp-stlclr"></a><a name="value_comp"></a>eingestellt::value_comp (STL/CLR)

Kopiert den Stellvertretung für zwei Elementwerte.

### <a name="syntax"></a>Syntax

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt den Sortierstellatlegor zurück, der zum Bestellen der gesteuerten Sequenz verwendet wird. Sie verwenden es, um zwei Elementwerte zu vergleichen.

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

## <a name="setvalue_compare-stlclr"></a><a name="value_compare"></a>eingestellt::value_compare (STL/CLR)

Der Stellvertretung für zwei Elementwerte.

### <a name="syntax"></a>Syntax

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Delegaten, der die Reihenfolge seiner Wertargumente bestimmt.

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

## <a name="setvalue_type-stlclr"></a><a name="value_type"></a>eingestellt::value_type (STL/CLR)

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

## <a name="operator-set-stlclr"></a><a name="op_neq"></a>Operator!= (Set) (STL/CLR)

Liste nicht gleich Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator!=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(left == right)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht gleich *rechts* angeordnet ist, wenn die beiden Sätze Element für Element verglichen werden.

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

Liste kleiner als Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator<(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion gibt true zurück, `i` wenn `!(right[i] < left[i])` für die `left[i] < right[i]`niedrigste Position, für die es auch wahr ist, dass . Andernfalls wird `left->size() < right->size()` zurückgegeben Sie verwenden, um zu testen, ob *links* vor *rechts* angeordnet ist, wenn die beiden Sätze Element für Element verglichen werden.

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

Liste kleiner oder gleich Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator<=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(right < left)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht nach *rechts* sortiert ist, wenn die beiden Sätze Element für Element verglichen werden.

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

## <a name="operator-set-stlclr"></a><a name="op_eq"></a>Operator == (Set) (STL/CLR)

Listen gleiche Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator==(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion gibt true nur dann zurück, wenn die von *links* `i`und `left[i] ==` `right[i]` *rechts* gesteuerten Sequenzen die gleiche Länge haben und für jede Position . Sie verwenden es, um zu testen, ob *links* gleich *rechts* angeordnet ist, wenn die beiden Sätze Element für Element verglichen werden.

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

Liste größer als Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator>(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `right` `<` `left`gibt zurück. Sie verwenden es, um zu testen, ob *links* nach *rechts* sortiert ist, wenn die beiden Sätze Element für Element verglichen werden.

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

Liste größer als oder gleich Vergleich.

### <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    bool operator>=(set<Key>% left,
        set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Links*<br/>
Linker zu vergleichender Container.

*Richting*<br/>
Rechter zu vergleichender Container.

### <a name="remarks"></a>Bemerkungen

Die Operatorfunktion `!(left < right)`gibt zurück. Sie verwenden es, um zu testen, ob *links* nicht vorher *rechts* angeordnet ist, wenn die beiden Sätze Element für Element verglichen werden.

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
