---
title: hash_set (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_set
- cliext::hash_set::begin
- cliext::hash_set::bucket_count
- cliext::hash_set::clear
- cliext::hash_set::const_iterator
- cliext::hash_set::const_reference
- cliext::hash_set::const_reverse_iterator
- cliext::hash_set::count
- cliext::hash_set::difference_type
- cliext::hash_set::empty
- cliext::hash_set::end
- cliext::hash_set::equal_range
- cliext::hash_set::erase
- cliext::hash_set::find
- cliext::hash_set::generic_container
- cliext::hash_set::generic_iterator
- cliext::hash_set::generic_reverse_iterator
- cliext::hash_set::generic_value
- cliext::hash_set::hash_delegate
- cliext::hash_set::hash_set
- cliext::hash_set::hasher
- cliext::hash_set::insert
- cliext::hash_set::iterator
- cliext::hash_set::key_comp
- cliext::hash_set::key_compare
- cliext::hash_set::key_type
- cliext::hash_set::load_factor
- cliext::hash_set::lower_bound
- cliext::hash_set::make_value
- cliext::hash_set::max_load_factor
- cliext::hash_set::operator=
- cliext::hash_set::rbegin
- cliext::hash_set::reference
- cliext::hash_set::rehash
- cliext::hash_set::rend
- cliext::hash_set::reverse_iterator
- cliext::hash_set::size
- cliext::hash_set::size_type
- cliext::hash_set::swap
- cliext::hash_set::to_array
- cliext::hash_set::upper_bound
- cliext::hash_set::value_comp
- cliext::hash_set::value_compare
- cliext::hash_set::value_type
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_set class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
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
- hash_delegate member [STL/CLR]
- hash_set member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: d110e356-ba3e-4e52-9e2d-d997bf975c96
ms.openlocfilehash: a2f7dafc99c8632f420bcd8119fe489353cf4b28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221379"
---
# <a name="hash_set-stlclr"></a>hash_set (STL/CLR)

Die Vorlagen Klasse beschreibt ein Objekt, das eine Sequenz von Elementen variabler Länge steuert, die bidirektionalen Zugriff hat. Sie verwenden den Container `hash_set` zum Verwalten einer Sequenz von Elementen als Hash Tabelle, wobei jeder Tabelleneintrag eine bidirektionale verknüpfte Liste von Knoten speichert, und jeder Knoten, der ein Element speichert. Der Wert jedes Elements wird als Schlüssel verwendet, um die Sequenz zu ordnen.

In der Beschreibung unten `GValue` ist das gleiche wie `GKey` , das wiederum mit *Key* identisch ist, sofern es sich nicht um einen Ref-Typ handelt. in diesem Fall ist es `Key^` .

## <a name="syntax"></a>Syntax

```cpp
template<typename Key>
    ref class hash_set
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parameter

*Schlüssel*<br/>
Der Typ der Schlüsselkomponente eines Elements in der kontrollierten Sequenz.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<cliext/hash_set>

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Typendefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[hash_set::const_iterator (STL/CLR)](#const_iterator)|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|[hash_set::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[hash_set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.|
|[hash_set::difference_type (STL/CLR)](#difference_type)|Der Typ einer (möglicherweise mit Vorzeichen signierten) Entfernung zwischen zwei Elementen.|
|[hash_set::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container.|
|[hash_set::generic_iterator (STL/CLR)](#generic_iterator)|Der Typ eines Iterators für die generische Schnittstelle für den Container.|
|[hash_set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Der Typ eines umgekehrten Iterators für die generische Schnittstelle für den Container.|
|[hash_set::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container.|
|[hash_set::hasher (STL/CLR)](#hasher)|Der Hash Delegat für einen Schlüssel.|
|[hash_set::iterator (STL/CLR)](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[hash_set::key_compare (STL/CLR)](#key_compare)|Der Bestell Delegat für zwei Schlüssel.|
|[hash_set::key_type (STL/CLR)](#key_type)|Der Typ eines Sortierschlüssels.|
|[hash_set::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[hash_set::reverse_iterator (STL/CLR)](#reverse_iterator)|Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.|
|[hash_set::size_type (STL/CLR)](#size_type)|Der Typ einer (nicht negativen) Entfernung zwischen zwei Elementen.|
|[hash_set::value_compare (STL/CLR)](#value_compare)|Der Bestell Delegat für zwei Element Werte.|
|[hash_set::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[hash_set::begin (STL/CLR)](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[hash_set::bucket_count (STL/CLR)](#bucket_count)|Zählt die Anzahl der Bucket.|
|[hash_set::clear (STL/CLR)](#clear)|Entfernt alle Elemente.|
|[hash_set::count (STL/CLR)](#count)|Zählt Elemente, die mit einem angegebenen Schlüssel übereinstimmen.|
|[hash_set::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[hash_set::end (STL/CLR)](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[hash_set::equal_range (STL/CLR)](#equal_range)|Sucht den Bereich, der einem angegebenen Schlüssel entspricht.|
|[hash_set::erase (STL/CLR)](#erase)|Entfernt Elemente an den angegebenen Positionen.|
|[hash_set::find (STL/CLR)](#find)|Sucht ein Element, das einem angegebenen Schlüssel entspricht.|
|[hash_set::hash_delegate (STL/CLR)](#hash_delegate)|Kopiert den Hash Delegaten für einen Schlüssel.|
|[hash_set::hash_set (STL/CLR)](#hash_set)|Erstellt ein container-Objekt.|
|[hash_set::insert (STL/CLR)](#insert)|Fügt Elemente hinzu.|
|[hash_set::key_comp (STL/CLR)](#key_comp)|Kopiert den Bestell Delegaten für zwei Schlüssel.|
|[hash_set::load_factor (STL/CLR)](#load_factor)|Zählt die durchschnittliche Anzahl von Elementen pro Bucket.|
|[hash_set::lower_bound (STL/CLR)](#lower_bound)|Sucht den Anfang des Bereichs, der einem angegebenen Schlüssel entspricht.|
|[hash_set::make_value (STL/CLR)](#make_value)|Erstellt ein Wertobjekt.|
|[hash_set::max_load_factor (STL/CLR)](#max_load_factor)|Ruft die maximale Anzahl von Elementen pro Bucket ab oder legt sie fest.|
|[hash_set::rbegin (STL/CLR)](#rbegin)|Legt den Anfang der umgekehrten kontrollierten Sequenz fest.|
|[hash_set::rehash (STL/CLR)](#rehash)|Erstellt die Hashtabelle neu.|
|[hash_set::rend (STL/CLR)](#rend)|Legt das Ende der umgekehrten kontrollierten Sequenz fest.|
|[hash_set::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[hash_set::swap (STL/CLR)](#swap)|Vertauscht den Inhalt von zwei Containern.|
|[hash_set::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|
|[hash_set::upper_bound (STL/CLR)](#upper_bound)|Findet das Ende des Bereichs, der einem angegebenen Schlüssel entspricht.|
|[hash_set::value_comp (STL/CLR)](#value_comp)|Kopiert den Bestell Delegaten für zwei Element Werte.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[hash_set::operator= (STL/CLR)](#op)|Ersetzt die kontrollierte Sequenz.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren eines Objekts.|
|<xref:System.Collections.IEnumerable>|Sequenzieren Sie Elemente.|
|<xref:System.Collections.ICollection>|Die Gruppe von Elementen wird beibehalten.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sequenz durch typisierte-Elemente.|
|<xref:System.Collections.Generic.ICollection%601>|Verwaltet eine Gruppe von typisierten Elementen.|
|IHash\<Key, Value>|Verwalten Sie einen generischen Container.|

## <a name="remarks"></a>Bemerkungen

Das-Objekt ordnet Speicher für die Sequenz zu, die er als einzelne Knoten in einer bidirektionalen verknüpften Liste steuert und freigibt. Um den Zugriff zu beschleunigen, behält das Objekt auch ein Array mit variabler Länge in der Liste (der Hash Tabelle) bei und verwaltet die gesamte Liste effektiv als Sequenz von Unterlisten oder Bucket. Elemente werden in einen Bucket eingefügt, der durch Ändern der Verknüpfungen zwischen den Knoten geändert wird, niemals durch Kopieren des Inhalts eines Knotens in einen anderen. Dies bedeutet, dass Sie Elemente ohne Beeinträchtigung der restlichen Elemente frei einfügen und entfernen können.

Das Objekt sortiert die einzelnen Bucket-Steuerelemente, indem ein gespeichertes Delegatobjekt vom Typ [hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)aufgerufen wird. Sie können das gespeicherte Delegatobjekt angeben, wenn Sie die hash_set erstellen; Wenn Sie kein Delegatobjekt angeben, ist der Standardwert der-Vergleich `operator<=(key_type, key_type)` .

Sie greifen auf das gespeicherte Delegatobjekt zu, indem Sie die Member-Funktion [hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)aufrufen `()` . Ein solches Delegatobjekt muss eine äquivalente Reihenfolge zwischen Schlüsseln vom Typ [hash_set:: key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)definieren. Dies bedeutet, dass für alle zwei Schlüssel `X` und `Y` :

`key_comp()(X, Y)`gibt bei jedem-Rückruf dasselbe boolesche Ergebnis zurück.

Wenn `key_comp()(X, Y) && key_comp()(Y, X)` den Wert true hat `X` , `Y` werden und als entsprechende Reihenfolge bezeichnet.

Eine beliebige Bestell Regel, die `operator<=(key_type, key_type)` sich wie verhält `operator>=(key_type, key_type)` oder die `operator==(key_type, key_type)` eqivalente Reihenfolge definiert.

Beachten Sie, dass der Container nur sicherstellt, dass Elemente, deren Schlüssel eine äquivalente Reihenfolge (und der Hash desselben ganzzahligen Werts) haben, in einem Bucket nebeneinander angeordnet sind. Im Gegensatz zur Vorlagen Klasse [Hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)stellt ein Objekt der Vorlagen Klasse `hash_set` sicher, dass die Schlüssel für alle Elemente eindeutig sind. (Zwei Schlüssel haben keine äquivalente Reihenfolge.)

Das-Objekt bestimmt, welcher Bucket einen angegebenen Bestell Schlüssel enthalten soll, indem er ein gespeichertes Delegatobjekt vom Typ [hash_set:: Hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)aufruft. Um einen ganzzahligen Wert zu erhalten, der vom Schlüsselwert abhängt, greifen Sie auf dieses gespeicherte Objekt zu, indem Sie die Member-Funktion [hash_set:: hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) aufrufen `()` . Sie können das gespeicherte Delegatobjekt angeben, wenn Sie die hash_set erstellen; Wenn Sie kein Delegatobjekt angeben, wird standardmäßig die-Funktion angegeben `System::Object::hash_value(key_type)` . Dies bedeutet, dass für alle Schlüssel `X` und `Y` :

`hash_delegate()(X)`gibt bei jedem-Rückruf dasselbe ganzzahlige Ergebnis zurück.

Wenn `X` und eine `Y` entsprechende Reihenfolge aufweisen, `hash_delegate()(X)` sollte das gleiche ganzzahlige Ergebnis wie zurückgeben `hash_delegate()(Y)` .

Jedes Element dient sowohl als Schlüssel als auch als Wert. Die Sequenz wird so dargestellt, dass die Suche, das Einfügen und das Entfernen eines beliebigen Elements mit einer Reihe von Vorgängen ermöglicht, die unabhängig von der Anzahl der Elemente in der Sequenz (Konstante Zeit) sind, zumindest in den meisten Fällen. Darüber hinaus führt das Einfügen eines Elements nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen eines Elements werden nur solche Iteratoren ungültig, die auf das entfernte Element gezeigt haben.

Wenn Hashwerte nicht gleichmäßig verteilt werden, kann eine Hash Tabelle jedoch degeneriert werden. In der äußersten-für eine Hash Funktion, die immer denselben Wert zurückgibt, sind Lookup-, Einfügungs-und Entfernungs Vorgänge proportional zur Anzahl der Elemente in der Sequenz (lineare Zeit). Der Container ist bestrebt, eine sinnvolle Hash Funktion, eine Mean Bucket-Größe und eine Hash Tabellengröße (Gesamtanzahl von Buchern) auszuwählen, aber Sie können eine beliebige oder alle dieser Optionen überschreiben. Siehe z. b. die Funktionen [hash_set:: max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) und [hash_set:: rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).

Ein hash_set unterstützt Bidirektionale Iteratoren. Dies bedeutet, dass Sie bei einem Iterator, der ein Element in der gesteuerten Sequenz festlegt, zu angrenzenden Elementen wechseln können. Ein spezieller Haupt Knoten entspricht dem Iterator, der von [hash_set:: End (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)zurückgegeben wurde `()` . Sie können diesen Iterator verringern, um das letzte Element in der kontrollierten Sequenz zu erreichen, falls vorhanden. Sie können einen hash_set Iterator Inkrement erhöhen, um den Head-Knoten zu erreichen, und dann wird gleich verglichen `end()` . Sie können jedoch nicht den von zurückgegebenen Iterator dereferenzieren `end()` .

Beachten Sie, dass Sie nicht direkt auf ein hash_set Element verweisen können, das die numerische Position erhält, die einen Random-Access-Iterator erfordert.

Ein hash_set Iterator speichert ein Handle für den zugehörigen hash_set Knoten, der wiederum ein Handle für den zugehörigen Container speichert. Iteratoren können nur mit den zugehörigen Container Objekten verwendet werden. Ein hash_set Iterator bleibt gültig, solange der zugeordnete hash_set Knoten mit einigen hash_set verknüpft ist. Außerdem ist ein gültiger Iterator dereferencable--Sie können ihn verwenden, um auf den Elementwert zuzugreifen, den er festlegt, sofern er nicht gleich ist `end()` .

Durch das Löschen oder Entfernen eines Elements wird der Dekonstruktor für den gespeicherten Wert aufgerufen. Wenn Sie den Container zerstören, werden alle Elemente gelöscht. Daher stellt ein Container, dessen Elementtyp eine Verweis Klasse ist, sicher, dass keine Elemente den Container überdauern. Beachten Sie jedoch, dass ein Container von Handles seine Elemente *nicht* zerstört.

## <a name="members"></a>Member

## <a name="hash_setbegin-stlclr"></a><a name="begin"></a>hash_set:: begin (STL/CLR)

Legt den Anfang der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator begin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen bidirektionalen Iterator zurück, der das erste Element der kontrollierten Sequenz festlegt, oder direkt hinter das Ende einer leeren Sequenz. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_begin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_set::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

## <a name="hash_setbucket_count-stlclr"></a><a name="bucket_count"></a>hash_set:: bucket_count (STL/CLR)

Zählt die Anzahl der Bucket.

### <a name="syntax"></a>Syntax

```cpp
int bucket_count();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktionen gibt die aktuelle Anzahl der Bucket zurück. Sie verwenden es, um die Größe der Hash Tabelle zu ermitteln.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_setclear-stlclr"></a><a name="clear"></a>hash_set:: Clear (STL/CLR)

Entfernt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft effektiv [hash_set:: Erase (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md) `(` [hash_set:: begin (STL/CLR)](../dotnet/hash-set-begin-stl-clr.md) `(),` [hash_set:: End (STL/CLR](../dotnet/hash-set-end-stl-clr.md)) auf `())` . Sie verwenden ihn, um sicherzustellen, dass die gesteuerte Sequenz leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_clear.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_setconst_iterator-stlclr"></a><a name="const_iterator"></a>hash_set:: const_iterator (STL/CLR)

Der Typ eines konstanten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T2` , das als konstanter bidirektionaler Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_set::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setconst_reference-stlclr"></a><a name="const_reference"></a>hash_set:: const_reference (STL/CLR)

Der Typ eines konstanten Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen konstanten Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_const_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_set::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_set::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>hash_set:: const_reverse_iterator (STL/CLR)

Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T4` , das als konstanter umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_set::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_setcount-stlclr"></a><a name="count"></a>hash_set:: count (STL/CLR)

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
// cliext_hash_set_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_setdifference_type-stlclr"></a><a name="difference_type"></a>hash_set::d ifference_type (STL/CLR)

Die Typen eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine möglicherweise negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_difference_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_set::difference_type diff = 0;
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_set::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="hash_setempty-stlclr"></a><a name="empty"></a>hash_set:: Empty (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Dies entspricht [hash_set:: Size (STL/CLR)](../dotnet/hash-set-size-stl-clr.md) `() == 0` . Sie verwenden es, um zu testen, ob das hash_set leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_empty.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_setend-stlclr"></a><a name="end"></a>hash_set:: End (STL/CLR)

Legt das Ende der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator end();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen bidirektionalen Iterator zurück, der direkt hinter das Ende der kontrollierten Sequenz verweist. Sie verwenden Sie, um einen Iterator abzurufen, der das Ende der kontrollierten Sequenz festlegt. der Status ändert sich nicht, wenn sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_end.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_set::iterator it = c1.end();
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

## <a name="hash_setequal_range-stlclr"></a><a name="equal_range"></a>hash_set:: equal_range (STL/CLR)

Sucht den Bereich, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein paar von Iteratoren zurück `cliext::pair<iterator, iterator>(` [hash_set:: lower_bound (STL/CLR)](../dotnet/hash-set-lower-bound-stl-clr.md) `(key),` [hash_set:: upper_bound (STL/CLR)](../dotnet/hash-set-upper-bound-stl-clr.md) `(key))` . Sie verwenden Sie, um den Bereich der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entsprechen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_equal_range.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
typedef Myhash_set::pair_iter_iter Pairii;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_seterase-stlclr"></a><a name="erase"></a>hash_set:: Erase (STL/CLR)

Entfernt Elemente an den angegebenen Positionen.

### <a name="syntax"></a>Syntax

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
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

Die erste Member-Funktion entfernt das-Element der kontrollierten Sequenz, auf die von *Where*verwiesen wird, und gibt einen Iterator zurück, der das erste Element festlegt, das hinter dem entfernten Element liegt, oder [hash_set:: End (STL/CLR)](../dotnet/hash-set-end-stl-clr.md) , `()` Wenn kein solches Element vorhanden ist. Sie verwenden es, um ein einzelnes Element zu entfernen.

Die zweite Member-Funktion entfernt die Elemente der kontrollierten Sequenz im Bereich [ `first` , `last` ) und gibt einen Iterator zurück, der das erste über die entfernten Elemente hinaus verbliebene Element festlegt, oder, `end()` Wenn kein solches Element vorhanden ist. Sie verwenden Sie, um 0 (null) oder mehrere zusammenhängende Elemente zu entfernen.

Die dritte Member-Funktion entfernt alle Elemente der kontrollierten *Sequenz, deren Schlüssel die entsprechende*Reihenfolge hat, und gibt die Anzahl der entfernten Elemente zurück. Sie verwenden Sie, um alle Elemente zu entfernen und zu zählen, die einem angegebenen Schlüssel entsprechen.

Jede Element Löschung benötigt Zeit proportional zum Logarithmus der Anzahl von Elementen in der gesteuerten Sequenz.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_erase.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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
    Myhash_set::iterator it = c1.end();
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

## <a name="hash_setfind-stlclr"></a><a name="find"></a>hash_set:: Find (STL/CLR)

Sucht ein Element, das einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Wenn mindestens ein Element in der kontrollierten Sequenz eine äquivalente Reihenfolge mit *Key*aufweist, gibt die Member-Funktion einen Iterator zurück, der eines dieser Elemente festlegt. Andernfalls wird [hash_set:: End (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)zurückgegeben `()` . Sie verwenden Sie, um ein Element zu suchen, das sich derzeit in der kontrollierten Sequenz befindet, die einem angegebenen Schlüssel entspricht.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_find.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_setgeneric_container-stlclr"></a><a name="generic_container"></a>hash_set:: generic_container (STL/CLR)

Der Typ der generischen Schnittstelle für den Container.

### <a name="syntax"></a>Syntax

```cpp
typedef Microsoft::VisualC::StlClr::
    IHash<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt die generische Schnittstelle für diese Vorlagen Container Klasse.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_generic_container.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_set::generic_container^ gc1 = %c1;
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

## <a name="hash_setgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>hash_set:: generic_iterator (STL/CLR)

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
// cliext_hash_set_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_set::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_set::generic_iterator gcit = gc1->begin();
    Myhash_set::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_setgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>hash_set:: generic_reverse_iterator (STL/CLR)

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
// cliext_hash_set_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_set::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_set::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_set::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="hash_setgeneric_value-stlclr"></a><a name="generic_value"></a>hash_set:: generic_value (STL/CLR)

Der Typ eines Elements, das mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt vom Typ `GValue` , das den gespeicherten Elementwert zur Verwendung mit der generischen-Schnittstelle für diese Vorlagen Container Klasse beschreibt.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_generic_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_set::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_set::generic_iterator gcit = gc1->begin();
    Myhash_set::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_sethash_delegate-stlclr"></a><a name="hash_delegate"></a>hash_set:: hash_delegate (STL/CLR)

Sucht ein Element, das einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Delegaten zurück, mit dem ein Schlüsselwert in eine Ganzzahl konvertiert wird. Sie verwenden Sie zum Hash eines Schlüssels.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_sethash_set-stlclr"></a><a name="hash_set"></a>hash_set:: hash_set (STL/CLR)

Erstellt ein container-Objekt.

### <a name="syntax"></a>Syntax

```cpp
hash_set();
explicit hash_set(key_compare^ pred);
hash_set(key_compare^ pred, hasher^ hashfn);
hash_set(hash_set<Key>% right);
hash_set(hash_set<Key>^ right);
template<typename InIter>
    hash_sethash_set(InIter first, InIter last);
template<typename InIter>
    hash_set(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_set(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred, hasher^ hashfn);
```

#### <a name="parameters"></a>Parameter

*first*<br/>
Anfang des einzufügenden Bereichs.

*hashfn*<br/>
Hash Funktion für die Zuordnung von Schlüsseln zu Bucket.

*last*<br/>
Das Ende des einzufügenden Bereichs.

*pred*<br/>
Das Anordnungs Prädikat für die gesteuerte Sequenz.

*Richting*<br/>
Einzufügendes Objekt bzw. einzufügender Bereich.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`hash_set();`

Initialisiert die gesteuerte Sequenz ohne Elemente, mit dem Standard Reihen folgen Prädikat `key_compare()` und mit der Standard Hash Funktion. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem standardmäßigen Reihen folgen Prädikat und der Hash Funktion anzugeben.

Der Konstruktor:

`explicit hash_set(key_compare^ pred);`

Initialisiert die gesteuerte Sequenz ohne Elemente, mit dem *Prädikat pred*für die Reihenfolge und mit der Standard Hash Funktion. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem angegebenen Reihen folgen Prädikat und der Standard Hash Funktion anzugeben.

Der Konstruktor:

`hash_set(key_compare^ pred, hasher^ hashfn);`

Initialisiert die gesteuerte Sequenz ohne Elemente, mit dem *Prädikat pred*für die Reihenfolge und mit der Hash Funktion *hashfn*. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem angegebenen Reihen folgen Prädikat und der angegebenen Hash Funktion anzugeben.

Der Konstruktor:

`hash_set(hash_set<Key>% right);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [ `right.begin()` , `right.end()` ), mit dem Standard Reihen folgen Prädikat und mit der Standard Hash Funktion. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, bei der es sich um eine Kopie der Sequenz handelt, die vom hash_set Objekt *Rechts*gesteuert wird, mit dem Standard Reihen folgen Prädikat und der Hash Funktion.

Der Konstruktor:

`hash_set(hash_set<Key>^ right);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [ `right->begin()` , `right->end()` ), mit dem Standard Reihen folgen Prädikat und mit der Standard Hash Funktion. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, bei der es sich um eine Kopie der Sequenz handelt, die vom hash_set Objekt *Rechts*gesteuert wird, mit dem Standard Reihen folgen Prädikat und der Hash Funktion.

Der Konstruktor:

`template<typename InIter> hash_set(InIter first, InIter last);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [ `first` , `last` ), mit dem Standard Reihen folgen Prädikat und mit der Standard Hash Funktion. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, wobei das standardmäßige Reihen folgen Prädikat und die Hash Funktion verwendet werden.

Der Konstruktor:

`template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [ `first` , `last` ), mit dem *Prädikat pred*für die Reihenfolge und mit der Standard Hash Funktion. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, wobei das angegebene Reihen folgen Prädikat und die Standard Hash Funktion verwendet werden.

Der Konstruktor:

`template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [ `first` , `last` ), mit dem *Prädikat pred*für die Reihenfolge und mit der Hash Funktion *hashfn*. Sie verwenden Sie, um die gesteuerte Sequenz mit dem angegebenen Reihen folgen Prädikat und der angegebenen Hash Funktion als Kopie einer anderen Sequenz festzulegen.

Der Konstruktor:

`hash_set(System::Collections::Generic::IEnumerable<Key>^ right);`

Initialisiert die gesteuerte Sequenz mit der durch den enumeratorrecht angegebenen *right*Sequenz, mit dem Standard Reihen folgen Prädikat und mit der Standard Hash Funktion. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen von einem Enumerator beschriebenen Sequenz zu machen, wobei das standardmäßige Reihen folgen Prädikat und die Hash Funktion verwendet werden.

Der Konstruktor:

`hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Initialisiert die gesteuerte Sequenz mit der durch den enumeratorrecht angegebenen *right*Sequenz, mit dem *Prädikat pred*für die Reihenfolge und mit der Standard Hash Funktion. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator mit dem angegebenen Reihen folgen Prädikat und der Standard Hash Funktion beschrieben wird.

Der Konstruktor:

`hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

Initialisiert die gesteuerte Sequenz mit der durch den enumeratorrecht angegebenen *right*Sequenz, mit dem *Prädikat pred*für die Reihenfolge und mit der Hash Funktion *hashfn*. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator mit dem angegebenen Reihen folgen Prädikat und der angegebenen Hash Funktion beschrieben wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_construct.cpp
// compile with: /clr
#include <cliext/hash_set>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
// construct an empty container
    Myhash_set c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_set c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_set c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_set::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_set c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_set c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_set c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_set::hasher(&myfun));
    for each (wchar_t elem in c4h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_set c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_set c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_set c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>(),
                gcnew Myhash_set::hasher(&myfun));
    for each (wchar_t elem in c6h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct from a generic container
    Myhash_set c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_set c8(%c3);
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
a b c
size() = 0
c b a

a b c
a b c
c b a

a b c
a b c
c b a

a b c
a b c
```

## <a name="hash_sethasher-stlclr"></a><a name="hasher"></a>hash_set:: Hasher (STL/CLR)

Der Hash Delegat für einen Schlüssel.

### <a name="syntax"></a>Syntax

```cpp
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>
    hasher;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Delegaten, der einen Schlüsselwert in eine ganze Zahl konvertiert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_hasher.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_setinsert-stlclr"></a><a name="insert"></a>hash_set:: Insert (STL/CLR)

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

*Richting*<br/>
Enumeration, die eingefügt werden soll.

*ster*<br/>
Der einzufügende Schlüsselwert.

*where*<br/>
WHERE in Container zum Einfügen (nur Hinweis).

### <a name="remarks"></a>Bemerkungen

Jede der Member-Funktionen fügt eine Sequenz ein, die von den verbleibenden Operanden angegeben wird.

Die erste Member-Funktion versucht, ein Element mit dem Wert *Val*einzufügen, und gibt ein paar von Werten zurück `X` . Wenn `X.second` true ist, wird `X.first` das neu eingefügte Element festgelegt `X.first` . andernfalls wird ein Element mit entsprechender Reihenfolge festgelegt, das bereits vorhanden ist, und es wird kein neues Element eingefügt. Sie verwenden es, um ein einzelnes Element einzufügen.

Die zweite Member-Funktion fügt ein Element mit *dem* Wert *Val*ein, wobei als Hinweis verwendet wird (um die Leistung zu verbessern), und gibt einen Iterator zurück, der das neu eingefügte Element festlegt. Sie verwenden es, um ein einzelnes Element einzufügen, das möglicherweise an ein Element angrenzt, das Sie kennen.

Die dritte Member-Funktion fügt die Sequenz [ `first` , `last` ) ein. Sie verwenden Sie, um NULL oder mehr Elemente einzufügen, die aus einer anderen Sequenz kopiert wurden.

Die vierte Member-Funktion fügt die von der *rechten Seite*festgelegte Sequenz ein. Sie verwenden Sie zum Einfügen einer Sequenz, die von einem Enumerator beschrieben wird.

Jede Element Einfügung nimmt Zeit proportional zum Logarithmus der Anzahl von Elementen in der gesteuerten Sequenz auf. Die Einfügung kann in amortisierter konstanter Zeit auftreten, bei Angabe eines Hinweises, der ein Element angibt, das sich neben der Einfügemarke befindet.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_insert.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
typedef Myhash_set::pair_iter_bool Pairib;
int main()
    {
    Myhash_set c1;
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
    Myhash_set c2;
    Myhash_set::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_set c3;
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

## <a name="hash_setiterator-stlclr"></a><a name="iterator"></a>hash_set:: Iterator (STL/CLR)

Der Typ eines Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T1` , das als bidirektionaler Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_set::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setkey_comp-stlclr"></a><a name="key_comp"></a>hash_set:: key_comp (STL/CLR)

Kopiert den Bestell Delegaten für zwei Schlüssel.

### <a name="syntax"></a>Syntax

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Sortier Delegaten zurück, der zum Sortieren der kontrollierten Sequenz verwendet wird. Damit können Sie zwei Schlüssel vergleichen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_set c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_setkey_comp-stlclr"></a><a name="key_comp"></a>hash_set:: key_comp (STL/CLR)

Kopiert den Bestell Delegaten für zwei Schlüssel.

### <a name="syntax"></a>Syntax

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Sortier Delegaten zurück, der zum Sortieren der kontrollierten Sequenz verwendet wird. Damit können Sie zwei Schlüssel vergleichen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_set c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_setkey_compare-stlclr"></a><a name="key_compare"></a>hash_set:: key_compare (STL/CLR)

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
// cliext_hash_set_key_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_set c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_setkey_type-stlclr"></a><a name="key_type"></a>hash_set:: key_type (STL/CLR)

Der Typ eines Sortierschlüssels.

### <a name="syntax"></a>Syntax

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter *Schlüssel*.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_key_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_set::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setload_factor-stlclr"></a><a name="load_factor"></a>hash_set:: load_factor (STL/CLR)

Zählt die durchschnittliche Anzahl von Elementen pro Bucket.

### <a name="syntax"></a>Syntax

```cpp
float load_factor();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt `(float)` [hash_set:: Size (STL/CLR)](../dotnet/hash-set-size-stl-clr.md) `() /` [hash_set:: bucket_count (STL/CLR)](../dotnet/hash-set-bucket-count-stl-clr.md)zurück `()` . Sie verwenden Sie, um die durchschnittliche Bucket-Größe zu bestimmen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_setlower_bound-stlclr"></a><a name="lower_bound"></a>hash_set:: lower_bound (STL/CLR)

Sucht den Anfang des Bereichs, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion bestimmt das erste Element `X` in der kontrollierten Sequenz, das einen Hashwert zum gleichen Bucket wie *Key* hat und eine *key*entsprechende Reihenfolge hat. Wenn kein solches Element vorhanden ist, wird [hash_set:: End (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)zurückgegeben `()` ; andernfalls wird ein Iterator zurückgegeben, der festlegt `X` . Sie verwenden Sie, um den Anfang einer Sequenz von Elementen zu suchen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entsprechen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_setmake_value-stlclr"></a><a name="make_value"></a>hash_set:: make_value (STL/CLR)

Erstellt ein Wertobjekt.

### <a name="syntax"></a>Syntax

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu verwendende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein-Objekt zurück, `value_type` dessen Schlüssel *Key*ist. Sie verwenden es, um ein Objekt zu verfassen, das für die Verwendung mit mehreren anderen Element Funktionen geeignet ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_make_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(Myhash_set::make_value(L'a'));
    c1.insert(Myhash_set::make_value(L'b'));
    c1.insert(Myhash_set::make_value(L'c'));

    // display contents " a b c"
    for each (Myhash_set::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setmax_load_factor-stlclr"></a><a name="max_load_factor"></a>hash_set:: max_load_factor (STL/CLR)

Ruft die maximale Anzahl von Elementen pro Bucket ab oder legt sie fest.

### <a name="syntax"></a>Syntax

```cpp
float max_load_factor();
void max_load_factor(float new_factor);
```

#### <a name="parameters"></a>Parameter

*new_factor*<br/>
Neuer maximaler Ladefaktor, der gespeichert werden soll.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion gibt den aktuell gespeicherten maximalen Lastfaktor zurück. Sie verwenden Sie, um die maximale durchschnittliche Bucket-Größe zu bestimmen.

Die zweite Member-Funktion ersetzt den maximalen Ladefaktor für den Speicher durch *new_factor*. Es erfolgt keine automatische Wiederholung bis zu einer nachfolgenden Einfügung.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

## <a name="hash_setoperator-stlclr"></a><a name="op"></a>hash_set:: Operator = (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
hash_set<Key>% operator=(hash_set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Der zu kopierende Container.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann zurück **`*this`** . Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_operator_as.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Myhash_set::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_set c2;
    c2 = c1;
// display contents " a b c"
    for each (Myhash_set::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="hash_setrbegin-stlclr"></a><a name="rbegin"></a>hash_set:: rbegin (STL/CLR)

Legt den Anfang der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen reverse-Iterator zurück, der das letzte Element der kontrollierten Sequenz festlegt, oder direkt hinter dem Anfang einer leeren Sequenz. Demzufolge wird der `beginning` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_rbegin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_set::reverse_iterator rit = c1.rbegin();
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

## <a name="hash_setreference-stlclr"></a><a name="reference"></a>hash_set:: Reference (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_set::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_set::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_setrehash-stlclr"></a><a name="rehash"></a>hash_set:: rehash (STL/CLR)

Erstellt die Hashtabelle neu.

### <a name="syntax"></a>Syntax

```cpp
void rehash();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion erstellt die Hash Tabelle neu und stellt sicher, dass [hash_set:: load_factor (STL/CLR)](../dotnet/hash-set-load-factor-stl-clr.md) `() <=` [hash_set:: max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)ist. Andernfalls erhöht sich die Größe der Hash Tabelle nach dem Einfügen nur nach Bedarf. (Die Größe wird nie automatisch verringert.) Sie verwenden Sie zum Anpassen der Größe der Hash Tabelle.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_rehash.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_setrend-stlclr"></a><a name="rend"></a>hash_set:: rend (STL/CLR)

Legt das Ende der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen reverse-Iterator zurück, der direkt hinter den Anfang der kontrollierten Sequenz verweist. Demzufolge wird der `end` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der das `current` Ende der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_rend.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_set::reverse_iterator rit = c1.rend();
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

## <a name="hash_setreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>hash_set:: reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T3` , das als umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_set::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_setsize-stlclr"></a><a name="size"></a>hash_set:: Size (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden Sie, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden. Wenn Sie nur für Sie wichtig sind, ob die Sequenz eine Größe ungleich NULL aufweist, finden Sie weitere Informationen unter [hash_set:: Empty (STL/CLR)](../dotnet/hash-set-empty-stl-clr.md) `()` .

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_size.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_setsize_type-stlclr"></a><a name="size_type"></a>hash_set:: size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_size_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_set::size_type diff = 0;
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="hash_setswap-stlclr"></a><a name="swap"></a>hash_set:: Swap (STL/CLR)

Vertauscht den Inhalt von zwei Containern.

### <a name="syntax"></a>Syntax

```cpp
void swap(hash_set<Key>% right);
```

#### <a name="parameters"></a>Parameter

*Richting*<br/>
Container für den Tausch von Inhalten.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht die kontrollierten Sequenzen zwischen **`this`** und *Rechts*aus. Dies erfolgt in konstanter Zeit und löst keine Ausnahmen aus. Sie verwenden Sie als schnelle Möglichkeit, um den Inhalt von zwei Containern auszutauschen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_swap.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_set c2;
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

## <a name="hash_setto_array-stlclr"></a><a name="to_array"></a>hash_set:: to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein Array mit der kontrollierten Sequenz zurück. Sie verwenden Sie, um eine Kopie der kontrollierten Sequenz in Array Form abzurufen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_to_array.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_setupper_bound-stlclr"></a><a name="upper_bound"></a>hash_set:: upper_bound (STL/CLR)

Findet das Ende des Bereichs, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion bestimmt das letzte Element `X` in der kontrollierten Sequenz, das einen Hashwert zum gleichen Bucket wie *Key* hat und eine *key*entsprechende Reihenfolge hat. Wenn kein solches Element vorhanden ist oder wenn `X` das letzte Element in der kontrollierten Sequenz ist, gibt es [hash_set:: End (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)zurück `()` . andernfalls gibt es einen Iterator zurück, der das erste Element über den Wert festlegt `X` . Sie verwenden es, um das Ende einer Sequenz von Elementen zu suchen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entspricht.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
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

## <a name="hash_setvalue_comp-stlclr"></a><a name="value_comp"></a>hash_set:: value_comp (STL/CLR)

Kopiert den Bestell Delegaten für zwei Element Werte.

### <a name="syntax"></a>Syntax

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Sortier Delegaten zurück, der zum Sortieren der kontrollierten Sequenz verwendet wird. Sie verwenden Sie, um zwei Element Werte zu vergleichen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_value_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_setvalue_compare-stlclr"></a><a name="value_compare"></a>hash_set:: Value_compare (STL/CLR)

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
// cliext_hash_set_value_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    Myhash_set::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_setvalue_type-stlclr"></a><a name="value_type"></a>hash_set:: value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `generic_value`.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_set_value_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_set<wchar_t> Myhash_set;
int main()
    {
    Myhash_set c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_set::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```
