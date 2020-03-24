---
title: hash_map (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_map
- cliext::hash_map::begin
- cliext::hash_map::bucket_count
- cliext::hash_map::clear
- cliext::hash_map::const_iterator
- cliext::hash_map::const_reference
- cliext::hash_map::const_reverse_iterator
- cliext::hash_map::count
- cliext::hash_map::difference_type
- cliext::hash_map::empty
- cliext::hash_map::end
- cliext::hash_map::equal_range
- cliext::hash_map::erase
- cliext::hash_map::find
- cliext::hash_map::generic_container
- cliext::hash_map::generic_iterator
- cliext::hash_map::generic_reverse_iterator
- cliext::hash_map::generic_value
- cliext::hash_map::hash_delegate
- cliext::hash_map::hash_map
- cliext::hash_map::hasher
- cliext::hash_map::insert
- cliext::hash_map::iterator
- cliext::hash_map::key_comp
- cliext::hash_map::key_compare
- cliext::hash_map::key_type
- cliext::hash_map::load_factor
- cliext::hash_map::lower_bound
- cliext::hash_map::make_value
- cliext::hash_map::mapped_type
- cliext::hash_map::max_load_factor
- cliext::hash_map::operator=
- cliext::hash_map::operator
- cliext::hash_map::rbegin
- cliext::hash_map::reference
- cliext::hash_map::rehash
- cliext::hash_map::rend
- cliext::hash_map::reverse_iterator
- cliext::hash_map::size
- cliext::hash_map::size_type
- cliext::hash_map::swap
- cliext::hash_map::to_array
- cliext::hash_map::upper_bound
- cliext::hash_map::value_comp
- cliext::hash_map::value_compare
- cliext::hash_map::value_type
helpviewer_keywords:
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
- hash_map class [STL/CLR]
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
- hash_map member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- mapped_type member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
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
ms.assetid: c3cfc69b-04c6-42ae-a30e-0eda953fe883
ms.openlocfilehash: d87444fe5a62bac30d62cd7e44dfba7934083ef4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208740"
---
# <a name="hash_map-stlclr"></a>hash_map (STL/CLR)

Die Vorlagen Klasse beschreibt ein Objekt, das eine Sequenz von Elementen variabler Länge steuert, die bidirektionalen Zugriff hat. Sie verwenden den Container `hash_map`, um eine Sequenz von Elementen als Hash Tabelle zu verwalten, wobei jeder Tabelleneintrag eine bidirektionale verknüpfte Liste von Knoten speichert, und jeder Knoten, der ein Element speichert. Ein Element besteht aus einem Schlüssel, für die Reihenfolge der Sequenz und einem zugeordneten Wert, der für die Fahrt verläuft.

In der folgenden Beschreibung ist `GValue` identisch mit folgendem:

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

Dabei gilt:

`GKey` ist identisch mit `Key`, sofern es sich nicht um einen Ref-Typ handelt. in diesem Fall ist es `Key^`

`GMapped` ist identisch mit `Mapped`, sofern es sich nicht um einen Ref-Typ handelt. in diesem Fall ist es `Mapped^`

## <a name="syntax"></a>Syntax

```cpp
template<typename Key,
    typename Mapped>
    ref class hash_map
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        System::Collections::Generic::IDictionary<Gkey, GMapped>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parameter

*Schlüssel*<br/>
Der Typ der Schlüsselkomponente eines Elements in der kontrollierten Sequenz.

*Grafi*<br/>
Der Typ der zusätzlichen Komponente eines Elements in der kontrollierten Sequenz.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<cliext/hash_map >

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Typdefinition|BESCHREIBUNG|
|---------------------|-----------------|
|[hash_map::const_iterator (STL/CLR)](#const_iterator)|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|[hash_map::const_reference (STL/CLR)](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[hash_map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.|
|[hash_map::difference_type (STL/CLR)](#difference_type)|Der Typ einer (möglicherweise mit Vorzeichen signierten) Entfernung zwischen zwei Elementen.|
|[hash_map::generic_container (STL/CLR)](#generic_container)|Der Typ der generischen Schnittstelle für den Container.|
|[hash_map::generic_iterator (STL/CLR)](#generic_iterator)|Der Typ eines Iterators für die generische Schnittstelle für den Container.|
|[hash_map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Der Typ eines umgekehrten Iterators für die generische Schnittstelle für den Container.|
|[hash_map::generic_value (STL/CLR)](#generic_value)|Der Typ eines Elements für die generische Schnittstelle für den Container.|
|[hash_map::hasher (STL/CLR)](#hasher)|Der Hash Delegat für einen Schlüssel.|
|[hash_map::iterator (STL/CLR)](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[hash_map::key_compare (STL/CLR)](#key_compare)|Der Bestell Delegat für zwei Schlüssel.|
|[hash_map::key_type (STL/CLR)](#key_type)|Der Typ eines Sortierschlüssels.|
|[hash_map::mapped_type (STL/CLR)](#mapped_type)|Der Typ des zugeordneten Werts, der jedem Schlüssel zugeordnet ist.|
|[hash_map::reference (STL/CLR)](#reference)|Der Typ eines Verweises auf ein Element.|
|[hash_map::reverse_iterator (STL/CLR)](#reverse_iterator)|Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.|
|[hash_map::size_type (STL/CLR)](#size_type)|Der Typ einer (nicht negativen) Entfernung zwischen zwei Elementen.|
|[hash_map::value_compare (STL/CLR)](#value_compare)|Der Bestell Delegat für zwei Element Werte.|
|[hash_map::value_type (STL/CLR)](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|---------------------|-----------------|
|[hash_map::begin (STL/CLR)](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[hash_map::bucket_count (STL/CLR)](#bucket_count)|Zählt die Anzahl der Bucket.|
|[hash_map::clear (STL/CLR)](#clear)|Entfernt alle Elemente.|
|[hash_map::count (STL/CLR)](#count)|Zählt Elemente, die mit einem angegebenen Schlüssel übereinstimmen.|
|[hash_map::empty (STL/CLR)](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[hash_map::end (STL/CLR)](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[hash_map::equal_range (STL/CLR)](#equal_range)|Sucht den Bereich, der einem angegebenen Schlüssel entspricht.|
|[hash_map::erase (STL/CLR)](#erase)|Entfernt Elemente an den angegebenen Positionen.|
|[hash_map::find (STL/CLR)](#find)|Sucht ein Element, das einem angegebenen Schlüssel entspricht.|
|[hash_map::hash_delegate (STL/CLR)](#hash_delegate)|Kopiert den Hash Delegaten für einen Schlüssel.|
|[hash_map::hash_map (STL/CLR)](#hash_map)|Erstellt ein container-Objekt.|
|[hash_map::insert (STL/CLR)](#insert)|Fügt Elemente hinzu.|
|[hash_map::key_comp (STL/CLR)](#key_comp)|Kopiert den Bestell Delegaten für zwei Schlüssel.|
|[hash_map::load_factor (STL/CLR)](#load_factor)|Zählt die durchschnittliche Anzahl von Elementen pro Bucket.|
|[hash_map::lower_bound (STL/CLR)](#lower_bound)|Sucht den Anfang des Bereichs, der einem angegebenen Schlüssel entspricht.|
|[hash_map::make_value (STL/CLR)](#make_value)|Erstellt ein Wertobjekt.|
|[hash_map::max_load_factor (STL/CLR)](#max_load_factor)|Ruft die maximale Anzahl von Elementen pro Bucket ab oder legt sie fest.|
|[hash_map::rbegin (STL/CLR)](#rbegin)|Legt den Anfang der umgekehrten kontrollierten Sequenz fest.|
|[hash_map::rehash (STL/CLR)](#rehash)|Erstellt die Hashtabelle neu.|
|[hash_map::rend (STL/CLR)](#rend)|Legt das Ende der umgekehrten kontrollierten Sequenz fest.|
|[hash_map::size (STL/CLR)](#size)|Ermittelt die Anzahl von Elementen.|
|[hash_map::swap (STL/CLR)](#swap)|Vertauscht den Inhalt von zwei Containern.|
|[hash_map::to_array (STL/CLR)](#to_array)|Kopiert die gesteuerte Sequenz in ein neues Array.|
|[hash_map::upper_bound (STL/CLR)](#upper_bound)|Findet das Ende des Bereichs, der einem angegebenen Schlüssel entspricht.|
|[hash_map::value_comp (STL/CLR)](#value_comp)|Kopiert den Bestell Delegaten für zwei Element Werte.|

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[hash_map::operator= (STL/CLR)](#op_as)|Ersetzt die kontrollierte Sequenz.|
|[hash_map::operator(STL/CLR)](#op)|Ordnet dem zugeordneten zugeordneten Wert einen Schlüssel zu.|

## <a name="interfaces"></a>Schnittstellen

|Schnittstelle|BESCHREIBUNG|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplizieren eines Objekts.|
|<xref:System.Collections.IEnumerable>|Sequenzieren Sie Elemente.|
|<xref:System.Collections.ICollection>|Die Gruppe von Elementen wird beibehalten.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sequenz durch typisierte-Elemente.|
|<xref:System.Collections.Generic.ICollection%601>|Verwaltet eine Gruppe von typisierten Elementen.|
|<xref:System.Collections.Generic.IDictionary%602>|Behält die Gruppe von {Key, Value}-Paaren bei.|
|IHash < Key, Wert >|Verwalten Sie einen generischen Container.|

## <a name="remarks"></a>Bemerkungen

Das-Objekt ordnet Speicher für die Sequenz zu, die er als einzelne Knoten in einer bidirektionalen verknüpften Liste steuert und freigibt. Um den Zugriff zu beschleunigen, behält das Objekt auch ein Array mit variabler Länge in der Liste (der Hash Tabelle) bei und verwaltet die gesamte Liste effektiv als Sequenz von Unterlisten oder Bucket. Elemente werden in einen Bucket eingefügt, der durch Ändern der Verknüpfungen zwischen den Knoten geändert wird, niemals durch Kopieren des Inhalts eines Knotens in einen anderen. Dies bedeutet, dass Sie Elemente ohne Beeinträchtigung der restlichen Elemente frei einfügen und entfernen können.

Das Objekt sortiert die einzelnen Bucket-Steuerelemente, indem ein gespeichertes Delegatobjekt vom Typ [hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)aufgerufen wird. Sie können das gespeicherte Delegatobjekt angeben, wenn Sie die hash_set erstellen; Wenn Sie kein Delegatobjekt angeben, ist der Standardwert der Vergleichs `operator<=(key_type, key_type)`.

Sie greifen auf das gespeicherte Delegatobjekt zu, indem Sie die-Member-Funktion [hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`aufrufen. Ein solches Delegatobjekt muss eine äquivalente Reihenfolge zwischen Schlüsseln vom Typ [hash_set:: key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)definieren. Dies bedeutet, dass für alle zwei Schlüssel `X` und `Y`:

`key_comp()(X, Y)` gibt bei jedem-Rückruf dasselbe boolesche Ergebnis zurück.

Wenn `key_comp()(X, Y) && key_comp()(Y, X)` true ist, werden `X` und `Y` als äquivalente Reihenfolge bezeichnet.

Jede Bestell Regel, die sich wie `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` oder `operator==(key_type, key_type)` verhält, definiert die eqivalente Reihenfolge.

Beachten Sie, dass der Container nur sicherstellt, dass Elemente, deren Schlüssel eine äquivalente Reihenfolge (und der Hash desselben ganzzahligen Werts) haben, in einem Bucket nebeneinander angeordnet sind. Im Gegensatz zur Vorlagen Klasse [Hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)stellt ein Objekt der Vorlagen Klasse `hash_map` sicher, dass die Schlüssel für alle Elemente eindeutig sind. (Zwei Schlüssel haben keine äquivalente Reihenfolge.)

Das-Objekt bestimmt, welcher Bucket einen angegebenen Bestell Schlüssel enthalten soll, indem er ein gespeichertes Delegatobjekt vom Typ [hash_set:: Hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)aufruft. Sie greifen auf dieses gespeicherte Objekt zu, indem Sie die Element Funktion [hash_set:: hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md)`()` aufrufen, um einen ganzzahligen Wert zu erhalten, der vom Schlüsselwert abhängt. Sie können das gespeicherte Delegatobjekt angeben, wenn Sie die hash_set erstellen; Wenn Sie kein Delegatobjekt angeben, wird standardmäßig die-Funktion `System::Object::hash_value(key_type)`. Dies bedeutet, dass für alle Schlüssel `X` und `Y`:

`hash_delegate()(X)` gibt bei jedem-Rückruf dasselbe ganzzahlige Ergebnis zurück.

Wenn `X` und `Y` entsprechende Reihenfolge aufweisen, sollte `hash_delegate()(X)` dasselbe ganz Zahl Ergebnis wie `hash_delegate()(Y)`zurückgeben.

Jedes Element enthält einen separaten Schlüssel und einen zugeordneten Wert. Die Sequenz wird so dargestellt, dass die Suche, das Einfügen und das Entfernen eines beliebigen Elements mit einer Reihe von Vorgängen ermöglicht, die unabhängig von der Anzahl der Elemente in der Sequenz (Konstante Zeit) sind, zumindest in den meisten Fällen. Darüber hinaus führt das Einfügen eines Elements nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen eines Elements werden nur solche Iteratoren ungültig, die auf das entfernte Element gezeigt haben.

Wenn Hashwerte nicht gleichmäßig verteilt werden, kann eine Hash Tabelle jedoch degeneriert werden. In der äußersten-für eine Hash Funktion, die immer denselben Wert zurückgibt, sind Lookup-, Einfügungs-und Entfernungs Vorgänge proportional zur Anzahl der Elemente in der Sequenz (lineare Zeit). Der Container ist bestrebt, eine sinnvolle Hash Funktion, eine Mean Bucket-Größe und eine Hash Tabellengröße (Gesamtanzahl von Buchern) auszuwählen, aber Sie können eine beliebige oder alle dieser Optionen überschreiben. Siehe z. b. die Funktionen [hash_set:: max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) und [hash_set:: rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).

Ein hash_map unterstützt Bidirektionale Iteratoren. Dies bedeutet, dass Sie bei einem Iterator, der ein Element in der gesteuerten Sequenz festlegt, zu angrenzenden Elementen wechseln können. Ein spezieller Haupt Knoten entspricht dem Iterator, der von [hash_map:: End (STL/CLR)-](../dotnet/hash-map-end-stl-clr.md)`()`zurückgegeben wurde. Sie können diesen Iterator verringern, um das letzte Element in der kontrollierten Sequenz zu erreichen, falls vorhanden. Sie können einen hash_map Iterator Inkrement erhöhen, um den Haupt Knoten zu erreichen, und er vergleicht dann gleich `end()`. Sie können jedoch nicht den von `end()`zurückgegebenen Iterator dereferenzieren.

Beachten Sie, dass Sie nicht direkt auf ein hash_map Element verweisen können, das die numerische Position erhält, die einen Random-Access-Iterator erfordert.

Ein hash_map Iterator speichert ein Handle für den zugehörigen hash_map Knoten, der wiederum ein Handle für den zugehörigen Container speichert. Iteratoren können nur mit den zugehörigen Container Objekten verwendet werden. Ein hash_map Iterator bleibt gültig, solange der zugeordnete hash_map Knoten mit einigen hash_map verknüpft ist. Außerdem ist ein gültiger Iterator dereferencable--Sie können ihn verwenden, um auf den von ihm festgelegt-Elementwert zuzugreifen oder ihn zu ändern, solange er nicht gleich `end()`ist.

Durch das Löschen oder Entfernen eines Elements wird der Dekonstruktor für den gespeicherten Wert aufgerufen. Wenn Sie den Container zerstören, werden alle Elemente gelöscht. Daher stellt ein Container, dessen Elementtyp eine Verweis Klasse ist, sicher, dass keine Elemente den Container überdauern. Beachten Sie jedoch, dass ein Container von Handles seine Elemente *nicht* zerstört.

## <a name="members"></a>Members

## <a name="hash_mapbegin-stlclr"></a><a name="begin"></a>hash_map:: begin (STL/CLR)

Legt den Anfang der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator begin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen bidirektionalen Iterator zurück, der das erste Element der kontrollierten Sequenz festlegt, oder direkt hinter das Ende einer leeren Sequenz. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_begin.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_map::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*++begin() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*begin() = [a 1]
*++begin() = [b 2]
```

## <a name="hash_mapbucket_count-stlclr"></a><a name="bucket_count"></a>hash_map:: bucket_count (STL/CLR)

Zählt die Anzahl der Bucket.

### <a name="syntax"></a>Syntax

```cpp
int bucket_count();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktionen gibt die aktuelle Anzahl der Bucket zurück. Sie verwenden es, um die Größe der Hash Tabelle zu ermitteln.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1 = gcnew Myhash_map;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
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

## <a name="hash_mapclear-stlclr"></a><a name="clear"></a>hash_map:: Clear (STL/CLR)

Entfernt alle Elemente.

### <a name="syntax"></a>Syntax

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft effektiv [hash_map:: Erase (STL/CLR)-](../dotnet/hash-map-erase-stl-clr.md)`(` [hash_map:: begin (STL/CLR)](../dotnet/hash-map-begin-stl-clr.md)`(),` [hash_map:: End (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`())`auf. Sie verwenden ihn, um sicherzustellen, dass die gesteuerte Sequenz leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_clear.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2]
size() = 0
```

## <a name="hash_mapconst_iterator-stlclr"></a><a name="const_iterator"></a>hash_map:: const_iterator (STL/CLR)

Der Typ eines konstanten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T2`, das als konstanter bidirektionaler Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Myhash_map::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_mapconst_reference-stlclr"></a><a name="const_reference"></a>hash_map:: const_reference (STL/CLR)

Der Typ eines konstanten Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen konstanten Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_const_reference.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Myhash_map::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_map::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_mapconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>hash_map:: const_reverse_iterator (STL/CLR)

Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T4`, das als konstanter umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Myhash_map::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="hash_mapcount-stlclr"></a><a name="count"></a>hash_map:: count (STL/CLR)

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
// cliext_hash_map_count.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="hash_mapdifference_type-stlclr"></a><a name="difference_type"></a>hash_map::d ifference_type (STL/CLR)

Die Typen eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine möglicherweise negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_difference_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_map::difference_type diff = 0;
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_map::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
begin()-end() = -3
```

## <a name="hash_mapempty-stlclr"></a><a name="empty"></a>hash_map:: Empty (STL/CLR)

Testet, ob keine Elemente vorhanden sind.

### <a name="syntax"></a>Syntax

```cpp
bool empty();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück. Dies entspricht [hash_map:: Size (STL/CLR)-](../dotnet/hash-map-size-stl-clr.md)`() == 0`. Sie verwenden es, um zu testen, ob das hash_map leer ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_empty.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="hash_mapend-stlclr"></a><a name="end"></a>hash_map:: End (STL/CLR)

Legt das Ende der kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
iterator end();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen bidirektionalen Iterator zurück, der direkt hinter das Ende der kontrollierten Sequenz verweist. Sie verwenden Sie, um einen Iterator abzurufen, der das Ende der kontrollierten Sequenz festlegt. der Status ändert sich nicht, wenn sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_end.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_map::iterator it = c1.end();
    --it;
    --it;
    System::Console::WriteLine("*-- --end() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*--end() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --end() = [b 2]
*--end() = [c 3]
```

## <a name="hash_mapequal_range-stlclr"></a><a name="equal_range"></a>hash_map:: equal_range (STL/CLR)

Sucht den Bereich, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein paar von Iteratoren `cliext::pair<iterator, iterator>(lower_bound(key), upper_bound(key))`zurück. Sie verwenden Sie, um den Bereich der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entsprechen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_equal_range.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
typedef Myhash_map::pair_iter_iter Pairii;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("[{0} {1}] ",
            pair1.first->first, pair1.first->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
equal_range(L'x') empty = True
[b 2]
```

## <a name="hash_maperase-stlclr"></a><a name="erase"></a>hash_map:: Erase (STL/CLR)

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

Die erste Member-Funktion entfernt das-Element der kontrollierten Sequenz, auf die von *Where*verwiesen wird, und gibt einen Iterator zurück, der das erste Element festlegt, das hinter dem entfernten Element liegt, oder [hash_map:: End (STL/CLR)](../dotnet/hash-map-end-stl-clr.md) -`()`, wenn kein solches Element vorhanden ist. Sie verwenden es, um ein einzelnes Element zu entfernen.

Die zweite Member-Funktion entfernt die Elemente der kontrollierten Sequenz im Bereich [`first``last`) und gibt einen Iterator zurück, der das erste Element festlegt, das über alle entfernten Elemente hinausgeht, oder `end()`, wenn kein solches Element vorhanden ist. Sie verwenden Sie, um 0 (null) oder mehrere zusammenhängende Elemente zu entfernen.

Die dritte Member-Funktion entfernt alle Elemente der kontrollierten *Sequenz, deren Schlüssel die entsprechende*Reihenfolge hat, und gibt die Anzahl der entfernten Elemente zurück. Sie verwenden Sie, um alle Elemente zu entfernen und zu zählen, die einem angegebenen Schlüssel entsprechen.

Jede Element Löschung benötigt Zeit proportional zum Logarithmus der Anzahl von Elementen in der gesteuerten Sequenz.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_erase.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    cliext::hash_map<wchar_t, int> c1;
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::hash_map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::hash_map<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::hash_map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase all but end
    it = c1.end();
    it = c1.erase(c1.begin(), --it);
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",
        it->first, it->second);
    System::Console::WriteLine("size() = {0}", c1.size());

    // erase end
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
erase(begin()) = [b 2]
[b 2] [c 3] [d 4] [e 5]
erase(begin(), end()-1) = [e 5]
size() = 1
erase(L'x') = 0
erase(L'e') = 1
```

## <a name="hash_mapfind-stlclr"></a><a name="find"></a>hash_map:: Find (STL/CLR)

Sucht ein Element, das einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Wenn mindestens ein Element in der kontrollierten Sequenz eine äquivalente Reihenfolge mit *Key*aufweist, gibt die Member-Funktion einen Iterator zurück, der eines dieser Elemente festlegt. Andernfalls wird [hash_map:: End-`()`(STL/CLR)](../dotnet/hash-map-end-stl-clr.md) zurückgegeben. Sie verwenden Sie, um ein Element zu suchen, das sich derzeit in der kontrollierten Sequenz befindet, die einem angegebenen Schlüssel entspricht.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_find.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Myhash_map::iterator it = c1.find(L'b');
    System::Console::WriteLine("find {0} = [{1} {2}]",
        L'b', it->first, it->second);

    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
find A = False
find b = [b 2]
find C = False
```

## <a name="hash_mapgeneric_container-stlclr"></a><a name="generic_container"></a>hash_map:: generic_container (STL/CLR)

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
// cliext_hash_map_generic_container.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_map::generic_container^ gc1 = %c1;
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Myhash_map::make_value(L'd', 4));
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Myhash_map::make_value(L'e', 5));
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3] [d 4] [e 5]
```

## <a name="hash_mapgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>hash_map:: generic_iterator (STL/CLR)

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
// cliext_hash_map_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_map::generic_container^ gc1 = %c1;
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_map::generic_iterator gcit = gc1->begin();
    Myhash_map::generic_value gcval = *gcit;
    System::Console::Write("[{0} {1}] ", gcval->first, gcval->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="hash_mapgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>hash_map:: generic_reverse_iterator (STL/CLR)

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
// cliext_hash_map_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_map::generic_container^ gc1 = %c1;
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_map::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_map::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="hash_mapgeneric_value-stlclr"></a><a name="generic_value"></a>hash_map:: generic_value (STL/CLR)

Der Typ eines Elements, das mit der generischen-Schnittstelle für den Container verwendet werden soll.

### <a name="syntax"></a>Syntax

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt vom Typ `GValue`, das den gespeicherten Elementwert zur Verwendung mit der generischen-Schnittstelle für diese Vorlagen Container Klasse beschreibt.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_generic_value.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_map::generic_container^ gc1 = %c1;
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_map::generic_iterator gcit = gc1->begin();
    Myhash_map::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="hash_maphash_delegate-stlclr"></a><a name="hash_delegate"></a>hash_map:: hash_delegate (STL/CLR)

Sucht ein Element, das einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Delegaten zurück, mit dem ein Schlüsselwert in eine Ganzzahl konvertiert wird. Sie verwenden Sie zum Hash eines Schlüssels.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_maphash_map-stlclr"></a><a name="hash_map"></a>hash_map:: hash_map (STL/CLR)

Erstellt ein container-Objekt.

### <a name="syntax"></a>Syntax

```cpp
hash_map();
explicit hash_map(key_compare^ pred);
hash_map(key_compare^ pred, hasher^ hashfn);
hash_map(hash_map<Key, Mapped>% right);
hash_map(hash_map<Key, Mapped>^ right);
template<typename InIter>
    hash_maphash_map(InIter first, InIter last);
template<typename InIter>
    hash_map(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_map(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,
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

*right*<br/>
Einzufügendes Objekt bzw. einzufügender Bereich.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor:

`hash_map();`

Initialisiert die gesteuerte Sequenz ohne Elemente, mit dem Standard-Reihen folgen Prädikat `key_compare()`und mit der Standard Hash Funktion. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem standardmäßigen Reihen folgen Prädikat und der Hash Funktion anzugeben.

Der Konstruktor:

`explicit hash_map(key_compare^ pred);`

Initialisiert die gesteuerte Sequenz ohne Elemente, mit dem *Prädikat pred*für die Reihenfolge und mit der Standard Hash Funktion. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem angegebenen Reihen folgen Prädikat und der Standard Hash Funktion anzugeben.

Der Konstruktor:

`hash_map(key_compare^ pred, hasher^ hashfn);`

Initialisiert die gesteuerte Sequenz ohne Elemente, mit dem *Prädikat pred*für die Reihenfolge und mit der Hash Funktion *hashfn*. Sie verwenden es, um eine leere anfängliche gesteuerte Sequenz mit dem angegebenen Reihen folgen Prädikat und der angegebenen Hash Funktion anzugeben.

Der Konstruktor:

`hash_map(hash_map<Key, Mapped>% right);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`right.begin()``right.end()`), mit dem Standard Reihen folgen Prädikat und mit der Standard Hash Funktion. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, bei der es sich um eine Kopie der Sequenz handelt, die vom hash_map Objekt *Rechts*gesteuert wird, mit dem Standard Reihen folgen Prädikat und der Hash Funktion.

Der Konstruktor:

`hash_map(hash_map<Key, Mapped>^ right);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`right->begin()``right->end()`), mit dem Standard Reihen folgen Prädikat und mit der Standard Hash Funktion. Sie verwenden Sie, um eine anfängliche gesteuerte Sequenz anzugeben, bei der es sich um eine Kopie der Sequenz handelt, die vom hash_map Objekt *Rechts*gesteuert wird, mit dem Standard Reihen folgen Prädikat und der Hash Funktion.

Der Konstruktor:

`template<typename InIter> hash_map(InIter first, InIter last);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`first``last`), mit dem Standard Reihen folgen Prädikat und mit der Standard Hash Funktion. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, wobei das standardmäßige Reihen folgen Prädikat und die Hash Funktion verwendet werden.

Der Konstruktor:

`template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`first`, `last`), mit dem *Prädikat pred*für die Reihenfolge und mit der Standard Hash Funktion. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, wobei das angegebene Reihen folgen Prädikat und die Standard Hash Funktion verwendet werden.

Der Konstruktor:

`template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

Initialisiert die gesteuerte Sequenz mit der Sequenz [`first`, `last`), mit der *Prädikat-Prädikats-* Reihenfolge und mit der Hash Funktion *hashfn*. Sie verwenden Sie, um die gesteuerte Sequenz mit dem angegebenen Reihen folgen Prädikat und der angegebenen Hash Funktion als Kopie einer anderen Sequenz festzulegen.

Der Konstruktor:

`hash_map(System::Collections::Generic::IEnumerable<Key>^ right);`

Initialisiert die gesteuerte Sequenz mit der durch den enumeratorrecht angegebenen *right*Sequenz, mit dem Standard Reihen folgen Prädikat und mit der Standard Hash Funktion. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen von einem Enumerator beschriebenen Sequenz zu machen, wobei das standardmäßige Reihen folgen Prädikat und die Hash Funktion verwendet werden.

Der Konstruktor:

`hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Initialisiert die gesteuerte Sequenz mit der durch den enumeratorrecht angegebenen *right*Sequenz, mit dem *Prädikat pred*für die Reihenfolge und mit der Standard Hash Funktion. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator mit dem angegebenen Reihen folgen Prädikat und der Standard Hash Funktion beschrieben wird.

Der Konstruktor:

`hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

Initialisiert die gesteuerte Sequenz mit der durch den enumeratorrecht angegebenen *right*Sequenz, mit dem *Prädikat pred*für die Reihenfolge und mit der Hash Funktion *hashfn*. Sie verwenden Sie, um die gesteuerte Sequenz zu einer Kopie einer anderen Sequenz zu machen, die von einem Enumerator mit dem angegebenen Reihen folgen Prädikat und der angegebenen Hash Funktion beschrieben wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_construct.cpp
// compile with: /clr
#include <cliext/hash_map>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
// construct an empty container
    Myhash_map c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_map c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_map c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_map::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (Myhash_map::value_type elem in c2h)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_map c3(c1.begin(), c1.end());
    for each (Myhash_map::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_map c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Myhash_map::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_map c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_map::hasher(&myfun));
    for each (Myhash_map::value_type elem in c4h)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_map c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Myhash_map::value_type>^)%c3);
    for each (Myhash_map::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_map c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Myhash_map::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Myhash_map::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_map c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Myhash_map::value_type>^)%c3,
                cliext::greater_equal<wchar_t>(),
                gcnew Myhash_map::hasher(&myfun));
    for each (Myhash_map::value_type elem in c6h)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_map c7(c4);
    for each (Myhash_map::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Myhash_map c8(%c3);
    for each (Myhash_map::value_type elem in c8)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[c 3] [b 2] [a 1]

[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]

[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]

[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="hash_maphasher-stlclr"></a><a name="hasher"></a>hash_map:: Hasher (STL/CLR)

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
// cliext_hash_map_hasher.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_mapinsert-stlclr"></a><a name="insert"></a>hash_map:: Insert (STL/CLR)

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

Die erste Member-Funktion versucht, ein Element mit einem Wert `val`einzufügen, und gibt ein Werte Paar `X`zurück. Wenn `X.second` true ist, wird `X.first` das neu eingefügte Element festlegen. Andernfalls `X.first` ein Element mit entsprechender Reihenfolge festgelegt, die bereits vorhanden ist, und es wird kein neues Element eingefügt. Sie verwenden es, um ein einzelnes Element einzufügen.

Die zweite Member-Funktion fügt ein Element mit *dem* Wert *Val*ein, wobei als Hinweis verwendet wird (um die Leistung zu verbessern), und gibt einen Iterator zurück, der das neu eingefügte Element festlegt. Sie verwenden es, um ein einzelnes Element einzufügen, das möglicherweise an ein Element angrenzt, das Sie kennen.

Die dritte Member-Funktion fügt die Sequenz [`first``last`) ein. Sie verwenden Sie, um NULL oder mehr Elemente einzufügen, die aus einer anderen Sequenz kopiert wurden.

Die vierte Member-Funktion fügt die von der *rechten Seite*festgelegte Sequenz ein. Sie verwenden Sie zum Einfügen einer Sequenz, die von einem Enumerator beschrieben wird.

Jede Element Einfügung nimmt Zeit proportional zum Logarithmus der Anzahl von Elementen in der gesteuerten Sequenz auf. Die Einfügung kann in amortisierter konstanter Zeit auftreten, bei Angabe eines Hinweises, der ein Element angibt, das sich neben der Einfügemarke befindet.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_insert.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
typedef Myhash_map::pair_iter_bool Pairib;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    Pairib pair1 =
        c1.insert(Myhash_map::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}] {2}",
        pair1.first->first, pair1.first->second, pair1.second);

    pair1 = c1.insert(Myhash_map::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}] {2}",
        pair1.first->first, pair1.first->second, pair1.second);

    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    Myhash_map::iterator it =
        c1.insert(c1.begin(), Myhash_map::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Myhash_map c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_map c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Myhash_map::value_type>^)%c1);
    for each (Myhash_map::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [x 24] True
insert([L'b' 2]) = [b 2] False
[a 1] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [c 3] [x 24]
[a 1] [b 2] [c 3] [x 24] [y 25]
```

## <a name="hash_mapiterator-stlclr"></a><a name="iterator"></a>hash_map:: Iterator (STL/CLR)

Der Typ eines Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T1`, das als bidirektionaler Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Myhash_map::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_mapkey_comp-stlclr"></a><a name="key_comp"></a>hash_map:: key_comp (STL/CLR)

Kopiert den Bestell Delegaten für zwei Schlüssel.

### <a name="syntax"></a>Syntax

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Sortier Delegaten zurück, der zum Sortieren der kontrollierten Sequenz verwendet wird. Damit können Sie zwei Schlüssel vergleichen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_key_comp.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_map c2 = cliext::greater<wchar_t>();
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

## <a name="hash_mapkey_compare-stlclr"></a><a name="key_compare"></a>hash_map:: key_compare (STL/CLR)

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
// cliext_hash_map_key_compare.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_map c2 = cliext::greater<wchar_t>();
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

## <a name="hash_mapkey_type-stlclr"></a><a name="key_type"></a>hash_map:: key_type (STL/CLR)

Der Typ eines Sortierschlüssels.

### <a name="syntax"></a>Syntax

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagen Parameter *Schlüssel*.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_key_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_map::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_mapload_factor-stlclr"></a><a name="load_factor"></a>hash_map:: load_factor (STL/CLR)

Zählt die durchschnittliche Anzahl von Elementen pro Bucket.

### <a name="syntax"></a>Syntax

```cpp
float load_factor();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt `(float)`[hash_map:: Size (STL/CLR)](../dotnet/hash-map-size-stl-clr.md)`() /` [hash_map:: bucket_count (STL/CLR)-](../dotnet/hash-map-bucket-count-stl-clr.md)`()`zurück. Sie verwenden Sie, um die durchschnittliche Bucket-Größe zu bestimmen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_load_factor.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1 = gcnew Myhash_map;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
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

## <a name="hash_maplower_bound-stlclr"></a><a name="lower_bound"></a>hash_map:: lower_bound (STL/CLR)

Sucht den Anfang des Bereichs, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion bestimmt das erste Element, das in der gesteuerten Sequenz `X` wird, das einen Hashwert zum gleichen Bucket wie *Key* hat und die entsprechende Reihenfolge an *Key*hat. Wenn kein solches Element vorhanden ist, wird [hash_map:: End (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`; zurückgegeben. Andernfalls wird ein Iterator zurückgegeben, der `X`festlegt. Sie verwenden Sie, um den Anfang einer Sequenz von Elementen zu suchen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entsprechen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Myhash_map::iterator it = c1.lower_bound(L'a');
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.lower_bound(L'b');
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
lower_bound(L'x')==end() = True
*lower_bound(L'a') = [a 1]
*lower_bound(L'b') = [b 2]
```

## <a name="hash_mapmake_value-stlclr"></a><a name="make_value"></a>hash_map:: make_value (STL/CLR)

Erstellt ein Wertobjekt.

### <a name="syntax"></a>Syntax

```cpp
static value_type make_value(key_type key, mapped_type mapped);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu verwendende Schlüsselwert.

*Grafi*<br/>
Zugeordneter Wert, der gesucht werden soll.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein `value_type` Objekt zurück, dessen Schlüssel *Schlüssel* ist und dessen zugeordneter Wert *zugeordnet*ist. Sie verwenden es, um ein Objekt zu verfassen, das für die Verwendung mit mehreren anderen Element Funktionen geeignet ist.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_make_value.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_mapmapped_type-stlclr"></a><a name="mapped_type"></a>hash_map:: mapped_type (STL/CLR)

Der Typ eines zugeordneten Werts, der jedem Schlüssel zugeordnet ist.

### <a name="syntax"></a>Syntax

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `Mapped`dar.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_mapped_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Myhash_map::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="hash_mapmax_load_factor-stlclr"></a><a name="max_load_factor"></a>hash_map:: max_load_factor (STL/CLR)

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
// cliext_hash_map_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1 = gcnew Myhash_map;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
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

## <a name="hash_mapoperator-stlclr"></a><a name="op_as"></a>hash_map:: Operator = (STL/CLR)

Ersetzt die kontrollierte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
hash_map<Key, Mapped>% operator=(hash_map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Der zu kopierende Container.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator kopiert *direkt* in das-Objekt und gibt dann `*this`zurück. Sie verwenden es, um die gesteuerte Sequenz durch eine Kopie der kontrollierten Sequenz in der *rechten*Ecke zu ersetzen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_operator_as.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_map c2;
    c2 = c1;
// display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="hash_mapoperatorstlclr"></a><a name="op"></a>hash_map:: Operator (STL/CLR)

Ordnet dem zugeordneten zugeordneten Wert einen Schlüssel zu.

### <a name="syntax"></a>Syntax

```cpp
mapped_type operator[](key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktionen sind bestrebt, ein Element mit entsprechender Reihenfolge zum *Schlüssel*zu finden. Wenn ein solcher gefunden wird, wird der zugeordnete zugeordnete Wert zurückgegeben. Andernfalls wird `value_type(key, mapped_type())` eingefügt und der zugeordnete (standardmäßige) zugeordnete Wert zurückgegeben. Sie verwenden Sie, um einen zugeordneten Wert nach dem zugeordneten Schlüssel zu suchen oder um sicherzustellen, dass ein Eintrag für den Schlüssel vorhanden ist, wenn kein Wert gefunden wird.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_operator_sub.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("c1[{0}] = {1}",
        L'A', c1[L'A']);
    System::Console::WriteLine("c1[{0}] = {1}",
        L'b', c1[L'b']);

    // redisplay altered contents
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // alter mapped values and redisplay
    c1[L'A'] = 10;
    c1[L'c'] = 13;
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
c1[A] = 0
c1[b] = 2
[a 1] [A 0] [b 2] [c 3]
[a 1] [A 10] [b 2] [c 13]
```

## <a name="hash_maprbegin-stlclr"></a><a name="rbegin"></a>hash_map:: rbegin (STL/CLR)

Legt den Anfang der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen reverse-Iterator zurück, der das letzte Element der kontrollierten Sequenz festlegt, oder direkt hinter dem Anfang einer leeren Sequenz. Demzufolge wird der `beginning` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der den `current` Anfang der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_rbegin.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_map::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*rbegin() = [c 3]
*++rbegin() = [b 2]
```

## <a name="hash_mapreference-stlclr"></a><a name="reference"></a>hash_map:: Reference (STL/CLR)

Der Typ eines Verweises auf ein Element.

### <a name="syntax"></a>Syntax

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt einen Verweis auf ein Element.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_reference.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Myhash_map::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_map::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_maprehash-stlclr"></a><a name="rehash"></a>hash_map:: rehash (STL/CLR)

Erstellt die Hashtabelle neu.

### <a name="syntax"></a>Syntax

```cpp
void rehash();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion erstellt die Hash Tabelle neu und stellt sicher, dass [hash_map:: load_factor (STL/CLR)](../dotnet/hash-map-load-factor-stl-clr.md)`() <=` [hash_map:: max_load_factor (STL/CLR)](../dotnet/hash-map-max-load-factor-stl-clr.md)ist. Andernfalls erhöht sich die Größe der Hash Tabelle nach dem Einfügen nur nach Bedarf. (Die Größe wird nie automatisch verringert.) Sie verwenden Sie zum Anpassen der Größe der Hash Tabelle.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_rehash.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1 = gcnew Myhash_map;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
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

## <a name="hash_maprend-stlclr"></a><a name="rend"></a>hash_map:: rend (STL/CLR)

Legt das Ende der umgekehrten kontrollierten Sequenz fest.

### <a name="syntax"></a>Syntax

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen reverse-Iterator zurück, der direkt hinter den Anfang der kontrollierten Sequenz verweist. Demzufolge wird der `end` der umgekehrten Sequenz bestimmt. Sie können damit einen Iterator abrufen, der das `current` Ende der kontrollierten Sequenz in umgekehrter Reihenfolge bestimmt; der Zustand kann sich jedoch ändern, sobald sich die Länge der kontrollierten Sequenz ändert.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_rend.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_map::reverse_iterator rit = c1.rend();
    --rit;
    --rit;
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*--rend() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --rend() = [b 2]
*--rend() = [a 1]
```

## <a name="hash_mapreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>hash_map:: reverse_iterator (STL/CLR)

Der Typ eines umgekehrten Iterators für die gesteuerte Sequenz.

### <a name="syntax"></a>Syntax

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt des nicht angegebenen Typs `T3`, das als umgekehrter Iterator für die gesteuerte Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Myhash_map::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="hash_mapsize-stlclr"></a><a name="size"></a>hash_map:: Size (STL/CLR)

Ermittelt die Anzahl von Elementen.

### <a name="syntax"></a>Syntax

```cpp
size_type size();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück. Sie verwenden Sie, um die Anzahl der Elemente zu bestimmen, die sich derzeit in der kontrollierten Sequenz befinden. Wenn Sie nur für Sie wichtig sind, ob die Sequenz eine Größe ungleich NULL aufweist, finden Sie weitere Informationen unter [hash_map:: Empty (STL/CLR)](../dotnet/hash-map-empty-stl-clr.md)`()`.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_size.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Myhash_map::make_value(L'd', 4));
    c1.insert(Myhash_map::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="hash_mapsize_type-stlclr"></a><a name="size_type"></a>hash_map:: size_type (STL/CLR)

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

### <a name="syntax"></a>Syntax

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine nicht negative Element Anzahl.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_size_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_map::size_type diff = 0;
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="hash_mapswap-stlclr"></a><a name="swap"></a>hash_map:: Swap (STL/CLR)

Vertauscht den Inhalt von zwei Containern.

### <a name="syntax"></a>Syntax

```cpp
void swap(hash_map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parameter

*right*<br/>
Container für den Tausch von Inhalten.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht die kontrollierten Sequenzen zwischen `this` und *Rechts*aus. Dies erfolgt in konstanter Zeit und löst keine Ausnahmen aus. Sie verwenden Sie als schnelle Möglichkeit, um den Inhalt von zwei Containern auszutauschen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_swap.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_map c2;
    c2.insert(Myhash_map::make_value(L'd', 4));
    c2.insert(Myhash_map::make_value(L'e', 5));
    c2.insert(Myhash_map::make_value(L'f', 6));
    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[d 4] [e 5] [f 6]
[d 4] [e 5] [f 6]
[a 1] [b 2] [c 3]
```

## <a name="hash_mapto_array-stlclr"></a><a name="to_array"></a>hash_map:: to_array (STL/CLR)

Kopiert die gesteuerte Sequenz in ein neues Array.

### <a name="syntax"></a>Syntax

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt ein Array mit der kontrollierten Sequenz zurück. Sie verwenden Sie, um eine Kopie der kontrollierten Sequenz in Array Form abzurufen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_to_array.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Myhash_map::value_type>^ a1 = c1.to_array();

    c1.insert(Myhash_map::make_value(L'd', 4));
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Myhash_map::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="hash_mapupper_bound-stlclr"></a><a name="upper_bound"></a>hash_map:: upper_bound (STL/CLR)

Findet das Ende des Bereichs, der einem angegebenen Schlüssel entspricht.

### <a name="syntax"></a>Syntax

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion bestimmt das letzte Element, das in der kontrollierten Sequenz `X` wird, das einen Hashwert zum gleichen Bucket wie *Key* hat und die entsprechende Reihenfolge an *Key*hat. Wenn kein solches Element vorhanden ist oder `X` das letzte Element in der kontrollierten Sequenz ist, wird [hash_map:: End (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`zurückgegeben. Andernfalls wird ein Iterator zurückgegeben, der das erste Element über `X`hinaus festlegt. Sie verwenden es, um das Ende einer Sequenz von Elementen zu suchen, die sich derzeit in der kontrollierten Sequenz befinden, die einem angegebenen Schlüssel entspricht.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Myhash_map::iterator it = c1.upper_bound(L'a');
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.upper_bound(L'b');
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
upper_bound(L'x')==end() = True
*upper_bound(L'a') = [b 2]
*upper_bound(L'b') = [c 3]
```

## <a name="hash_mapvalue_comp-stlclr"></a><a name="value_comp"></a>hash_map:: value_comp (STL/CLR)

Kopiert den Bestell Delegaten für zwei Element Werte.

### <a name="syntax"></a>Syntax

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt den Sortier Delegaten zurück, der zum Sortieren der kontrollierten Sequenz verwendet wird. Sie verwenden Sie, um zwei Element Werte zu vergleichen.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_value_comp.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Myhash_map::make_value(L'a', 1),
            Myhash_map::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Myhash_map::make_value(L'a', 1),
            Myhash_map::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Myhash_map::make_value(L'b', 2),
            Myhash_map::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = True
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="hash_mapvalue_compare-stlclr"></a><a name="value_compare"></a>hash_map:: Value_compare (STL/CLR)

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
// cliext_hash_map_value_compare.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Myhash_map::make_value(L'a', 1),
            Myhash_map::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Myhash_map::make_value(L'a', 1),
            Myhash_map::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Myhash_map::make_value(L'b', 2),
            Myhash_map::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = True
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="hash_mapvalue_type-stlclr"></a><a name="value_type"></a>hash_map:: value_type (STL/CLR)

Der Typ eines Elements.

### <a name="syntax"></a>Syntax

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `generic_value`.

### <a name="example"></a>Beispiel

```cpp
// cliext_hash_map_value_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_map::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```
