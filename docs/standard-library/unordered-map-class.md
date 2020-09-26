---
title: unordered_map-Klasse
description: API-Referenz für die Container Klasse der C++ `unordered_map` -Standard Bibliothek, die eine Sequenz von Elementen variabler Länge steuert.
ms.date: 9/9/2020
f1_keywords:
- unordered_map/std::unordered_map
- unordered_map/std::unordered_map::allocator_type
- unordered_map/std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_reference
- unordered_map/std::unordered_map::difference_type
- unordered_map/std::unordered_map::hasher
- unordered_map/std::unordered_map::iterator
- unordered_map/std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_type
- unordered_map/std::unordered_map::local_iterator
- unordered_map/std::unordered_map::mapped_type
- unordered_map/std::unordered_map::pointer
- unordered_map/std::unordered_map::reference
- unordered_map/std::unordered_map::size_type
- unordered_map/std::unordered_map::value_type
- unordered_map/std::unordered_map::at
- unordered_map/std::unordered_map::begin
- unordered_map/std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_size
- unordered_map/std::unordered_map::cbegin
- unordered_map/std::unordered_map::cend
- unordered_map/std::unordered_map::clear
- unordered_map/std::unordered_map::contains
- unordered_map/std::unordered_map::count
- unordered_map/std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::empty
- unordered_map/std::unordered_map::end
- unordered_map/std::unordered_map::equal_range
- unordered_map/std::unordered_map::erase
- unordered_map/std::unordered_map::find
- unordered_map/std::unordered_map::get_allocator
- unordered_map/std::unordered_map::hash
- unordered_map/std::unordered_map::insert
- unordered_map/std::unordered_map::key_eq
- unordered_map/std::unordered_map::load_factor
- unordered_map/std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_size
- unordered_map/std::unordered_map::rehash
- unordered_map/std::unordered_map::size
- unordered_map/std::unordered_map::swap
- unordered_map/std::unordered_map::unordered_map
- unordered_map/std::unordered_map::hash_function
helpviewer_keywords:
- std::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::contains
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
- std::unordered_map::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash_function
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
ms.openlocfilehash: 2f30b5683d8487830d596fc8185430c8a4c4c7b0
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352413"
---
# <a name="unordered_map-class"></a>unordered_map-Klasse

In der Klassen Vorlage wird ein Objekt beschrieben, das eine Sequenz von Elementen variabler Länge vom Typ steuert `std::pair<const Key, Ty>` . Die Sequenz wird grob durch eine Hashfunktion sortiert, die die Sequenz in eine geordnete Gruppe von Untersequenzen, so genannte Buckets, unterteilt. Innerhalb jedes Buckets bestimmt eine Vergleichsfunktion, ob ein Elementpaar eine entsprechende Reihenfolge hat. Jedes Element speichert zwei Objekte, einen Sortierschlüssel und einen Wert. Die Sequenz wird so dargestellt, dass die Suche, das Einfügen und das Entfernen eines beliebigen Elements mit einer Reihen von Vorgängen möglich ist, die unabhängig von der Anzahl von Elementen in der Sequenz (konstante Zeit) sein können, zumindest, wenn alle Buckets von ungefähr gleicher Länge sind. Im schlimmsten Fall, d. h., wenn sich alle Elemente in einem Bucket befinden, ist die Anzahl von Vorgängen proportional zur Anzahl von Elementen in der Sequenz (lineare Zeit). Darüber hinaus führt das Einfügen eines Elements nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen eines Elements werden nur solche Iteratoren ungültig, die auf das entfernte Element gezeigt haben.

## <a name="syntax"></a>Syntax

```cpp
template <class Key,
    class Ty,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<std::pair<const Key, Ty>>>
class unordered_map;
```

### <a name="parameters"></a>Parameter

*Wichtigen*\
Der Schlüsseltyp.

*Genossenschaft*\
Der zugeordnete Typ.

*Hash*\
Der Hashfunktionsobjekttyp.

*Pred*\
Der Gleichheitsvergleich-Funktionsobjekttyp.

*Zuordnungseinheits*\
Die Zuweisungsklasse.

## <a name="members"></a>Member

|Typendefinition|Beschreibung|
|-|-|
|[allocator_type](#allocator_type)|Der Typ einer Zuweisung für die Speicherverwaltung.|
|[const_iterator](#const_iterator)|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|[const_local_iterator](#const_local_iterator)|Der Typ eines konstanten Bucketiterators für die gesteuerte Sequenz.|
|[const_pointer](#const_pointer)|Der Typ eines konstanten Zeigers auf ein Element.|
|[const_reference](#const_reference)|Der Typ eines konstanten Verweises auf ein Element.|
|[difference_type](#difference_type)|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|[Hasher](#hasher)|Der Typ der Hashfunktion.|
|[Iterator](#iterator)|Der Typ eines Iterators für die gesteuerte Sequenz.|
|[key_equal](#key_equal)|Der Typ der Vergleichsfunktion.|
|[key_type](#key_type)|Der Typ eines Sortierschlüssels.|
|[local_iterator](#local_iterator)|Der Typ eines Bucketiterators für die gesteuerte Sequenz.|
|[mapped_type](#mapped_type)|Der Typ eines zugeordneten Werts, der jedem Schlüssel zugeordnet ist.|
|[Zeichner](#pointer)|Der Typ eines Zeigers auf ein Element.|
|[Referenz](#reference)|Der Typ eines Verweises auf ein Element.|
|[size_type](#size_type)|Der Typ eines Abstands ohne Vorzeichen zwischen zwei Elementen.|
|[value_type](#value_type)|Der Typ eines Elements.|

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[at](#at)|Sucht ein Element mit dem angegebenen Schlüssel.|
|[beginnen](#begin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[bucket](#bucket)|Ruft die Bucketnummer für einen Schlüsselwert ab.|
|[bucket_count](#bucket_count)|Ruft die Anzahl von Buckets ab.|
|[bucket_size](#bucket_size)|Ruft die Größe eines Buckets ab.|
|[cbegin](#cbegin)|Legt den Anfang der kontrollierten Sequenz fest.|
|[cend](#cend)|Legt das Ende der kontrollierten Sequenz fest.|
|[Löschen](#clear)|Entfernt alle Elemente.|
|[count](#count)|Sucht die Anzahl von Elementen, die einem angegebenen Schlüssel entsprechen.|
|[enthält](#contains)<sup>c++ 20</sup>|Überprüfen Sie, ob ein Element mit dem angegebenen Schlüssel in vorhanden ist `unordered_map` .|
|[emplace](#emplace)|Fügt ein Element hinzu, das direkt erstellt wird.|
|[emplace_hint](#emplace_hint)|Fügt ein Element hinzu, das direkt mit Hinweis erstellt wird.|
|[empty](#empty)|Testet, ob keine Elemente vorhanden sind.|
|[end](#end)|Legt das Ende der kontrollierten Sequenz fest.|
|[equal_range](#equal_range)|Sucht den Bereich, der einem angegebenen Schlüssel entspricht.|
|[erase](#erase)|Entfernt Elemente an den angegebenen Positionen.|
|[find](#find)|Sucht ein Element, das einem angegebenen Schlüssel entspricht.|
|[get_allocator](#get_allocator)|Ruft das gespeicherte Zuweisungsobjekt ab.|
|[hash_function](#hash)|Ruft das gespeicherte Hashfunktionsobjekt ab.|
|[insert](#insert)|Fügt Elemente hinzu.|
|[key_eq](#key_eq)|Ruft das gespeicherte Vergleichsfunktionsobjekt ab.|
|[load_factor](#load_factor)|Zählt die durchschnittliche Anzahl von Elementen pro Bucket.|
|[max_bucket_count](#max_bucket_count)|Ruft die maximale Anzahl von Buckets ab.|
|[max_load_factor](#max_load_factor)|Ruft die maximale Anzahl von Elementen pro Bucket ab oder legt sie fest.|
|[max_size](#max_size)|Ruft die maximale Größe der gesteuerten Sequenz ab.|
|[rehash](#rehash)|Erstellt die Hashtabelle neu.|
|[size](#size)|Ermittelt die Anzahl von Elementen.|
|[swap](#swap)|Vertauscht den Inhalt von zwei Containern.|
|[unordered_map](#unordered_map)|Erstellt ein container-Objekt.|

|Operator|BESCHREIBUNG|
|-|-|
|[unordered_map::operator[]](#op_at)|Sucht ein Element mit dem angegebenen Schlüssel oder fügt es ein.|
|[unordered_map:: Operator =](#op_eq)|Kopiert eine Hashtabelle.|

## <a name="remarks"></a>Hinweise

Das Objekt sortiert die Sequenz, die es steuert, indem es zwei gespeicherte Objekte aufruft, ein Vergleichsfunktionsobjekt des Typs [unordered_map::key_equal](#key_equal) und ein Hashfunktionsobjekt des Typs [unordered_map::hasher](#hasher). Sie greifen auf das erste gespeicherte Objekt zu, indem Sie die Member-Funktion [unordered_map:: key_eq](#key_eq) `()` ; aufrufen und auf das zweite gespeicherte Objekt zugreifen, indem Sie die Member-Funktion [unordered_map:: hash_function](#hash)aufrufen `()` . Insbesondere für alle Werte `X` und `Y` vom Typ `Key` gibt der Aufruf von `key_eq()(X, Y)` nur "true" zurück, wenn die beiden Argumentwerte die entsprechende Reihenfolge aufweisen. Der Aufruf von `hash_function()(keyval)` ergibt eine Verteilung von Werten des Typs `size_t`. Anders als Klassen Vorlagen [unordered_multimap Klasse](../standard-library/unordered-multimap-class.md)stellt ein Objekt vom Typ `unordered_map` sicher, dass `key_eq()(X, Y)` für zwei Elemente der gesteuerten Sequenz immer false ist. (Schlüssel sind eindeutig.)

Das Objekt speichert auch einen Höchstlastfaktor, der die maximal erwünschte durchschnittliche Anzahl von Elementen pro Bucket angibt. Wenn das Einfügen eines Elements bewirkt, dass [unordered_map:: load_factor](#load_factor) `()` den maximalen Lastfaktor überschreitet, erhöht der Container die Anzahl der Bucket und erstellt die Hash Tabelle nach Bedarf neu.

Die tatsächliche Reihenfolge der Elemente in der gesteuerten Sequenz hängt von der Hashfunktion, von der Vergleichsfunktion, von der Einfügereihenfolge, vom Höchstlastfaktor und von der aktuellen Anzahl von Buckets ab. Sie können die Reihenfolge der Elemente in der gesteuerten Sequenz im Allgemeinen nicht vorhersagen. Sie können allerdings sicher sein, dass jede Teilmenge von Elementen, die die entsprechende Reihenfolge aufweisen, in der gesteuerten Sequenz benachbart sind.

Das Objekt belegt Speicher und gibt Speicher für die gesteuerte Sequenz durch ein gespeichertes Zuweisungsobjekt des Typs [unordered_map::allocator_type](#allocator_type) frei. Ein solches zuordnerobjekt muss dieselbe externe Schnittstelle wie ein Objekt vom Typ aufweisen `allocator` . Beachten Sie, dass das gespeicherte Zuweisungsobjekt nicht kopiert wird, wenn das Containerobjekt zugewiesen wird.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<unordered_map>

**Namespace:** std

## <a name="unordered_mapallocator_type"></a><a name="allocator_type"></a> unordered_map:: allocator_type

Der Typ einer Zuweisung für die Speicherverwaltung.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Hinweise

Der Type stellt ein Synonym für den Vorlagenparameter `Alloc` dar.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_allocator_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_mapat"></a><a name="at"></a> unordered_map:: at

Verwendet einen angegebenen Schlüsselwert, um in einem unordered_map-Objekt nach einem Element zu suchen.

```cpp
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Schlüsselwert, das gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf den Datenwert des gefundenen Elements.

### <a name="remarks"></a>Hinweise

Wird der als Argument angegebene Schlüsselwert nicht gefunden, löst die Funktion ein Objekt der `out_of_range`-Klasse aus.

### <a name="example"></a>Beispiel

```cpp
// unordered_map_at.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
}
```

## <a name="unordered_mapbegin"></a><a name="begin"></a> unordered_map:: begin

Kennzeichnet den Anfang der kontrollierten Sequenz oder eines Buckets.

```cpp
iterator begin();
const_iterator begin() const;
local_iterator begin(size_type nbucket);
const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>Parameter

*nbucket*\
Die Bucketnummer.

### <a name="remarks"></a>Hinweise

Die beiden ersten Memberfunktionen geben einen Vorwärtsiterator zurück, der auf das erste Element der Sequenz zeigt (bzw. unmittelbar hinter das Ende einer leeren Sequenz). Die letzten zwei Member-Funktionen geben einen forward-Iterator zurück, der auf das erste Element des Bucket *nbucket* zeigt (oder direkt hinter dem Ende eines leeren Bucket).

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_begin.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

#typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[c, 3] [b, 2]
[a, 1]
```

## <a name="unordered_mapbucket"></a><a name="bucket"></a> unordered_map:: Bucket

Ruft die Bucketnummer für einen Schlüsselwert ab.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>Parameter

*keyVal*\
Der zuzuordnende Schlüsselwert.

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt die Bucket-Nummer zurück, die dem Schlüsselwert *keyVal*derzeit entspricht.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_bucket.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapbucket_count"></a><a name="bucket_count"></a> unordered_map:: bucket_count

Ruft die Anzahl von Buckets ab.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt die aktuelle Anzahl von Buckets zurück.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3][b, 2][a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapbucket_size"></a><a name="bucket_size"></a> unordered_map:: Bucket_size

Ruft die Größe eines Buckets ab.

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>Parameter

*nbucket*\
Die Bucketnummer.

### <a name="remarks"></a>Hinweise

Die Member-Funktionen gibt die Größe der Bucket-Nummer *nbucket*zurück.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_bucket_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="unordered_mapcbegin"></a><a name="cbegin"></a> unordered_map:: cbegin

Gibt einen **`const`** Iterator zurück, der das erste Element im Bereich adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** Forward-Access-Iterator, der auf das erste Element des Bereichs zeigt oder die Position direkt hinter dem Ende eines leeren Bereichs (für einen leeren Bereich `cbegin() == cend()` ).

### <a name="remarks"></a>Hinweise

Bei dem Rückgabewert `cbegin` können die Elemente im Bereich nicht geändert werden.

Sie können diese Memberfunktion anstelle der `begin()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollte `Container` ein änderbarer (nicht) Container sein, **`const`** der und unterstützt `begin()` `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="unordered_mapcend"></a><a name="cend"></a> unordered_map:: cend

Gibt einen **`const`** Iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** Forward-Access-Iterator, der direkt hinter das Ende des Bereichs zeigt.

### <a name="remarks"></a>Hinweise

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines Bereichs übergeben hat.

Sie können diese Memberfunktion anstelle der `end()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollte `Container` ein änderbarer (nicht) Container sein, **`const`** der und unterstützt `end()` `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();
// i2 is Container<T>::const_iterator
```

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="unordered_mapclear"></a><a name="clear"></a> unordered_map:: Clear

Entfernt alle Elemente.

```cpp
void clear();
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion ruft [unordered_map::erase](#erase)`(` [unordered_map::begin](#begin)`(),` [unordered_map::end](#end)`())` auf.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_clear.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapconst_iterator"></a><a name="const_iterator"></a> unordered_map:: const_iterator

Der Typ eines konstanten Iterators für die gesteuerte Sequenz.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Objekt, das als konstanter Forward-Iterator für die gesteuerte Sequenz fungieren kann. Er wird hier als Synonym für einen durch Implementierung definierten `T1`-Typ beschrieben.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_const_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_local_iterator"></a><a name="const_local_iterator"></a> unordered_map:: const_local_iterator

Der Typ eines konstanten Bucketiterators für die gesteuerte Sequenz.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Objekt, das als konstanter Vorwärtsiterator für ein Bucket dienen kann. Er wird hier als Synonym für einen durch Implementierung definierten `T5`-Typ beschrieben.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapconst_pointer"></a><a name="const_pointer"></a> unordered_map:: const_pointer

Der Typ eines konstanten Zeigers auf ein Element.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Objekt, das als konstanter Zeiger für ein Element der gesteuerten Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_const_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapconst_reference"></a><a name="const_reference"></a> unordered_map:: const_reference

Der Typ eines konstanten Verweises auf ein Element.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Objekt, das als Konstantenverweis für ein Element der gesteuerten Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_const_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapcontains"></a><a name="contains"></a> unordered_map:: enthält

Überprüft, ob ein-Element `unordered_map` mit dem angegebenen Schlüssel vorhanden ist.
Eingeführt in c++ 20.

```cpp
bool contains(const Key& key) const;
<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>Parameter

*Km*\
Der Typ des Schlüssels.

*wichtigen*\
Der Schlüsselwert des Elements, nach dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

`true` , wenn sich das Element im Container befindet. `false` andernfalls. 

### <a name="remarks"></a>Hinweise

`contains()` ist neu in c++ 20. Um es zu verwenden, geben Sie die [/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md) -Compileroption an.

`template<class K> bool contains(const K& key) const` ist nur an der Überladungs Auflösung beteiligt, wenn `key_compare` transparent ist.

### <a name="example"></a>Beispiel

```cpp
// Requires /std:c++latest
#include <unordered_map>
#include <iostream>

int main()
{
    std::unordered_map<int, bool> theUnorderedMap = {{0, false}, {1,true}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theUnorderedMap.contains(1) << '\n';
    std::cout << theUnorderedMap.contains(2) << '\n';
    
    return 0;
}
```

```Output
true
false
```

## <a name="unordered_mapcount"></a><a name="count"></a> unordered_map:: count

Sucht die Anzahl von Elementen, die einem angegebenen Schlüssel entsprechen.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>Parameter

*keyVal*\
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt die Anzahl der Elemente im Bereich zurück, der durch [unordered_map:: equal_range](#equal_range)begrenzt ist `(keyval)` .

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="unordered_mapdifference_type"></a><a name="difference_type"></a> unordered_map::d ifference_type

Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Hinweise

Der Ganzzahltyp mit Vorzeichen beschreibt ein Objekt, das die Differenz zwischen den Adressen von zwei beliebigen Elementen in der gesteuerten Sequenz darstellen kann. Er wird hier als Synonym für einen durch Implementierung definierten `T3`-Typ beschrieben.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_difference_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
end()-begin() == 3
begin()-end() == -3
```

## <a name="unordered_mapemplace"></a><a name="emplace"></a> unordered_map:: emplace

Fügt ein Element, das vor Ort erstellt wird (es werden keine Kopier- oder Verschiebevorgänge ausgeführt), in ein unordered_map-Element.

```cpp
template <class... Args>
pair<iterator, bool>  emplace( Args&&... args);
```

### <a name="parameters"></a>Parameter

*args*\
Die Argumente, die zum Erstellen eines in das einzufügenden Elements weitergeleitet werden, es `unordered_map` sei denn, es enthält bereits ein Element, dessen Wert gleichwertig geordnet ist.

### <a name="return-value"></a>Rückgabewert

Eine, `pair` deren **`bool`** Komponente true zurückgibt, wenn eine Einfügung erfolgt ist, und false, wenn das `unordered_map` bereits ein Element enthält, dessen Schlüssel einen entsprechenden Wert in der Reihenfolge aufweist und dessen iteratorkomponente die Adresse zurückgibt, an der ein neues Element eingefügt wurde oder in dem sich das Element bereits befand.

Um auf die Iteratorkomponente eines `pr`-Paares zuzugreifen, das von dieser Memberfunktion zurückgegeben wird, verwenden Sie `pr.first` und `*(pr.first)`, um es zu dereferenzieren. Um auf die- **`bool`** Komponente eines `pr` von dieser Member-Funktion zurückgegebenen Paars zuzugreifen, verwenden Sie `pr.second` .

### <a name="remarks"></a>Hinweise

Durch diese Funktion werden keine Iteratoren oder Verweise ungültig.

Wird bei der Einfügung eine Ausnahme ausgelöst, die aber in der Hashfunktion des Containers nicht auftritt, wird der Container nicht geändert. Wenn die Ausnahme in der Hashfunktion ausgelöst wird, ist das Ergebnis nicht definiert.

Ein Codebeispiel finden Sie unter [map::emplace](../standard-library/map-class.md#emplace).

## <a name="unordered_mapemplace_hint"></a><a name="emplace_hint"></a> unordered_map:: emplace_hint

Fügt ein Element mit einem Platzierungshinweis ein, das vor Ort erstellt wird (Es werden keine Kopier- oder Verschiebevorgänge ausgeführt).

```cpp
template <class... Args>
iterator emplace_hint(const_iterator where, Args&&... args);
```

### <a name="parameters"></a>Parameter

*args*\
Die Argumente, die weitergeleitet werden, um ein Element zu erstellen, das in das unordered_set-Element eingefügt werden soll, es sei denn, das unordened_set-Element erhält bereits das Element, oder allgemeiner: ein Element, dessen Schlüssel gleichwertig sortiert wird, ist bereits erhalten.

*Was*\
Ein Hinweis bezüglich des Platzes, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird.

### <a name="return-value"></a>Rückgabewert

Ein Iterator zum neu eingefügten Element.

Wenn die Einfügung fehlerhaft war, da das Element bereits vorhanden ist, wird ein Iterator an das vorhandene Element zurückgegeben.

### <a name="remarks"></a>Hinweise

Durch diese Funktion werden keine Verweise ungültig.

Wird bei der Einfügung eine Ausnahme ausgelöst, die aber in der Hashfunktion des Containers nicht auftritt, wird der Container nicht geändert. Wenn die Ausnahme in der Hashfunktion ausgelöst wird, ist das Ergebnis nicht definiert.

Der [value_type](../standard-library/map-class.md#value_type) eines Elements wird paarweise angegeben, sodass der Wert eines Elements ein geordnetes Paar ist, bei dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

Ein Codebeispiel finden Sie unter [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="unordered_mapempty"></a><a name="empty"></a> unordered_map:: Empty

Testet, ob keine Elemente vorhanden sind.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt „true“ für eine leere gesteuerte Sequenz zurück.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_empty.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapend"></a><a name="end"></a> unordered_map:: End

Legt das Ende der kontrollierten Sequenz fest.

```cpp
iterator end();
const_iterator end() const;
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>Parameter

*nbucket*\
Die Bucketnummer.

### <a name="remarks"></a>Hinweise

Die ersten beiden Memberfunktionen geben einen Vorwärtsiterator zurück, der direkt hinter das Ende der Sequenz verweist. Die letzten zwei Member-Funktionen geben einen forward-Iterator zurück, der direkt hinter das Ende des Bucket *nbucket*zeigt.

## <a name="unordered_mapequal_range"></a><a name="equal_range"></a> unordered_map:: equal_range

Sucht den Bereich, der einem angegebenen Schlüssel entspricht.

```cpp
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>Parameter

*keyVal*\
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt ein paar von Iteratoren zurück `X` , die `[X.first, X.second)` nur die Elemente der kontrollierten Sequenz begrenzt, die eine äquivalente Reihenfolge mit *keyVal*aufweisen. Wenn keine solchen Elemente vorhanden sind, sind beide Iteratoren `end()`.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_equal_range.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
equal_range('x'):
equal_range('b'): [b, 2]
```

## <a name="unordered_maperase"></a><a name="erase"></a> unordered_map:: Erase

Es wird ein Element oder ein Elementbereich in einem unordered_map-Element von angegebenen Speicherorten entfernt oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.

```cpp
iterator erase(const_iterator Where);
iterator erase(const_iterator First, const_iterator Last);
size_type erase(const key_type& Key);
```

### <a name="parameters"></a>Parameter

*Was*\
Die Position des zu entfernenden Elements.

*Erstes*\
Die Position des ersten zu entfernenden Elements.

*Letzten*\
Die Position direkt hinter dem letzten zu entfernenden Element.

*Wichtigen*\
Der Schlüsselwert der zu entfernenden Elemente.

### <a name="return-value"></a>Rückgabewert

Bei den ersten beiden Memberfunktionen ist es ein bidirektionaler Iterator, der das erste über die entfernten Elemente hinaus verbliebe Element festlegt, oder ein Element, das das Ende der Zuordnung darstellt, wenn kein solches Element vorhanden ist.

Für die dritte Memberfunktion wird die Anzahl der aus dem unordered_map-Element entfernten Elemente zurück gegeben.

### <a name="remarks"></a>Hinweise

Ein Codebeispiel finden Sie unter [map::erase](../standard-library/map-class.md#erase).

## <a name="unordered_mapfind"></a><a name="find"></a> unordered_map:: Find

Sucht ein Element, das einem angegebenen Schlüssel entspricht.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>Parameter

*keyVal*\
Der zu suchende Schlüsselwert.

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt [unordered_map:: equal_range](#equal_range)zurück `(keyval).first` .

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_find.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
find('A') == false
find('b') == true: [b, 2]
```

## <a name="unordered_mapget_allocator"></a><a name="get_allocator"></a> unordered_map:: Get_allocator

Ruft das gespeicherte Zuweisungsobjekt ab.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt das gespeicherte Zuweisungsobjekt zurück.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_get_allocator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="unordered_maphash_function"></a><a name="hash"></a> unordered_map:: hash_function

Ruft das gespeicherte Hashfunktionsobjekt ab.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt das gespeicherte Hashfunktionsobjekt zurück.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_hash_function.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_maphasher"></a><a name="hasher"></a> unordered_map:: Hasher

Der Typ der Hashfunktion.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Hinweise

Der Type stellt ein Synonym für den Vorlagenparameter `Hash` dar.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_hasher.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="unordered_mapinsert"></a><a name="insert"></a> unordered_map:: INSERT

Fügt ein Element oder einen Bereich von Elementen in ein unordered_map-Element ein.

```cpp
// (1) single element
pair<iterator, bool> insert(    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(    ValTy&& Val);

// (3) single element with hint
iterator insert(    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parameter

*Ster*\
Der Wert eines in das unordered_map-Element einzufügenden Elements, es sei denn, es ist bereits ein Element enthalten, dessen Schlüssel gleichwertig sortiert wird.

*Was*\
Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird.

*Valty*\
Ein Vorlagen Parameter, der den Argumenttyp angibt, mit dem der unordered_map ein Element [value_type](../standard-library/map-class.md#value_type)erstellen kann, und *perfekt als Argument* weiterleitet.

*Erstes*\
Die Position des ersten zu kopierenden Elements.

*Letzten*\
Die Position direkt über den letzten zu kopierenden Elements.

*InputIterator*\
Das Vorlagenfunktionsargument, das den Anforderungen eines [Eingabeiterators](../standard-library/input-iterator-tag-struct.md) erfüllt, der auf Elemente eines Typs zeigt, der zum Erstellen von [value_type](../standard-library/map-class.md#value_type)-Objekten verwendet werden kann.

*IList*\
Der [initializer_list](../standard-library/initializer-list.md) , aus dem die Elemente kopiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Einzelelement-Element Funktionen (1) und (2) geben ein [paar](../standard-library/pair-structure.md) zurück, dessen **`bool`** Komponente true ist, wenn eine Einfügung erfolgt ist, und false, wenn das unordered_map bereits ein Element enthält, dessen Schlüssel einen entsprechenden Wert in der Reihenfolge aufweist. Die iteratorkomponente des Rückgabewert Paars zeigt auf das neu eingefügte Element, wenn die **`bool`** Komponente "true" ist, oder auf das vorhandene Element, wenn die **`bool`** Komponente "false" ist.

Die Einzelelement-Memberfunktionen mit Hinweis (3) und (4) geben einen Iterator zurück, der auf die Position zeigt, an der das neue Element in das unordered_map-Element eingefügt wurde, oder, falls ein Element mit einem entsprechenden Schlüssel bereits vorhanden ist, auf das vorhandene Element.

### <a name="remarks"></a>Hinweise

Durch diese Funktion werden keine Iteratoren, Zeiger oder Verweise ungültig.

Wird beim Einfügen von nur einem Element eine Ausnahme ausgelöst, die jedoch nicht in der Hashfunktion des Containers auftritt, wird der Zustand des Containers nicht geändert. Wenn die Ausnahme in der Hashfunktion ausgelöst wird, ist das Ergebnis nicht definiert. Wird beim Einfügen mehrerer Elementen eine Ausnahme ausgelöst, wird der Container in einem nicht angegebenen doch gültigen Zustand belassen.

Um auf die Iteratorkomponente eines `pair` `pr`-Elements zuzugreifen, das von den Einzelelement-Memberfunktionen zurückgegeben wird, verwenden Sie `pr.first`. Um den Iterator im zurückgegebenen Paar zu dereferenzieren, verwenden Sie `*pr.first`. Damit erhalten Sie ein Element. Um auf die- **`bool`** Komponente zuzugreifen, verwenden Sie `pr.second` . Eine Beispiel finden Sie unter Beispielcode weiter unten in diesem Artikel.

Das [value_type](../standard-library/map-class.md#value_type)-Element eines Containers ist eine Typedef, die dem Container angehört. Bei einer Zuordnung ist `map<K, V>::value_type``pair<const K, V>`. Der Wert eines Elements ist ein sortiertes Paar, in dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

Die Bereichsmemberfunktion fügt die Sequenz von Elementwerten in ein unordered_map-Element ein, das jedem Element entspricht, das von einem Iterator im Bereich `[First, Last)` adressiert wird. Daher wird `Last` nicht eingefügt. Die Containermemberfunktion `end()` bezieht sich auf die Position direkt hinter dem letzten Element im Container. Z. B versucht die Anweisung `m.insert(v.begin(), v.end());` alle Elemente von `v` in `m` einzufügen. Nur Elemente, die eindeutige Werte im Bereich aufweisen werden eingefügt. Duplikate werden ignoriert. Um zu betrachten welche Elemente abgelehnt werden, verwenden Sie die Einzelelementversionen von `insert`.

Die Memberfunktion für die Initialisiererliste (6) verwendet eine [initializer_list](../standard-library/initializer-list.md), um Elemente in das unordered_map-Element zu kopieren.

Zum Einfügen eines lokal erstellten Elements. Das heißt, es wurden keine Kopier- oder Verschiebevorgänge ausgeführt. Informationen hierzu finden Sie unter [unordered_map::emplace](#emplace) und [unordered_map::emplace_hint](#emplace_hint).

Ein Codebeispiel finden Sie unter [map::insert](../standard-library/map-class.md#insert).

## <a name="unordered_mapiterator"></a><a name="iterator"></a> unordered_map:: Iterator

Der Typ eines Iterators für die gesteuerte Sequenz.

```cpp
typedef T0 iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Objekt, das als Forward-Iterator für die gesteuerte Sequenz fungieren kann. Er wird hier als Synonym für einen durch Implementierung definierten `T0`-Typ beschrieben.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapkey_eq"></a><a name="key_eq"></a> unordered_map:: key_eq

Ruft das gespeicherte Vergleichsfunktionsobjekt ab.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt das gespeicherte Vergleichsfunktionsobjekt zurück.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_key_eq.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="unordered_mapkey_equal"></a><a name="key_equal"></a> unordered_map:: key_equal

Der Typ der Vergleichsfunktion.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Hinweise

Der Type stellt ein Synonym für den Vorlagenparameter `Pred` dar.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_key_equal.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="unordered_mapkey_type"></a><a name="key_type"></a> unordered_map:: key_type

Der Typ eines Sortierschlüssels.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Hinweise

Der Type stellt ein Synonym für den Vorlagenparameter `Key` dar.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_key_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapload_factor"></a><a name="load_factor"></a> unordered_map:: load_factor

Zählt die durchschnittliche Anzahl von Elementen pro Bucket.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt `(float)` [unordered_map:: size](#size) `() / (float)` [unordered_map:: bucket_count](#bucket_count)zurück `()` , die durchschnittliche Anzahl von Elementen pro Bucket.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_maplocal_iterator"></a><a name="local_iterator"></a> unordered_map:: local_iterator

Der Typ eines Bucketiterators.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Objekt, das als ein Vorwärtsiterator für ein Bucket dienen kann. Er wird hier als Synonym für einen durch Implementierung definierten `T4`-Typ beschrieben.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect bucket containing 'a'
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="unordered_mapmapped_type"></a><a name="mapped_type"></a> unordered_map:: mapped_type

Der Typ eines zugeordneten Werts, der jedem Schlüssel zugeordnet ist.

```cpp
typedef Ty mapped_type;
```

### <a name="remarks"></a>Hinweise

Der Type stellt ein Synonym für den Vorlagenparameter `Ty` dar.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_mapped_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapmax_bucket_count"></a><a name="max_bucket_count"></a> unordered_map:: max_bucket_count

Ruft die maximale Anzahl von Buckets ab.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt die maximale Anzahl von Buckets zurück, die derzeit zulässig ist.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapmax_load_factor"></a><a name="max_load_factor"></a> unordered_map:: max_load_factor

Ruft die maximale Anzahl von Elementen pro Bucket ab oder legt sie fest.

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>Parameter

*gebend*\
Der neue maximale Lastfaktor.

### <a name="remarks"></a>Hinweise

Die erste Memberfunktion gibt den gespeicherten maximalen Lastfaktor zurück. Die zweite Member-Funktion ersetzt den gespeicherten maximalen Lastfaktor durch den *Faktor*.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="unordered_mapmax_size"></a><a name="max_size"></a> unordered_map:: max_size

Ruft die maximale Größe der gesteuerten Sequenz ab.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt die Länge der längsten Sequenz zurück, die das Objekt steuern kann.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_max_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
    }
```

```Output
max_size() == 536870911
```

## <a name="unordered_mapoperator"></a><a name="op_at"></a> unordered_map:: Operator []

Sucht ein Element mit dem angegebenen Schlüssel oder fügt es ein.

```cpp
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```

### <a name="parameters"></a>Parameter

*KeyVal*\
Der zu suchende oder einzufügende Schlüsselwert.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf den Datenwert des eingefügten Elements.

### <a name="remarks"></a>Hinweise

Wenn der Argumentschlüsselwert nicht gefunden wird, wird er zusammen mit dem Standardwert des Datentyps eingefügt.

`operator[]` kann zum Einfügen von Elementen in eine Zuordnung *m* mit *m*[*Key*] = verwendet werden `DataValue` , wobei `DataValue` der Wert des `mapped_type` Elements mit dem Schlüsselwert *Key*ist.

Wenn `operator[]` zum Einfügen von Elementen verwendet wird, gibt der zurückgegebene Verweis nicht an, ob eine Einfügung ein bereits vorhandenes Element ändert oder ein neues erstellt. Die Memberfunktionen [find](../standard-library/map-class.md#find) und [insert](../standard-library/map-class.md#insert) können verwendet werden, um zu bestimmen, ob ein Element mit einem bestimmten Schlüssel vor einer Einfügung bereits vorhanden ist.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_operator_sub.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <string>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// try to find and fail
    std::cout << "c1['A'] == " << c1['A'] << std::endl;

// try to find and succeed
    std::cout << "c1['a'] == " << c1['a'] << std::endl;

// redisplay contents
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// insert by moving key
    std::unordered_map<string, int> c2;
    std::string str("abc");
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
c1['A'] == 0
c1['a'] == 1
[c, 3] [b, 2] [A, 0] [a, 1]
c2[move(str)] == 0
c2["abc"] == 1
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion bestimmt den Iterator `where` als Rückgabewert von [unordered_map::insert](#insert)`(` [unordered_map::value_type](#value_type)`(keyval, Ty())`. (Sie fügt ein Element mit dem angegebenen Schlüssel ein, wenn kein solches Element vorhanden ist.) Anschließend wird ein Verweis auf zurückgegeben `(*where).second` .

## <a name="unordered_mapoperator"></a><a name="op_eq"></a> unordered_map:: Operator =

Ersetzt die Elemente für dieses „unordered_map“ mithilfe der Elemente aus einem anderen „unordered_map“.

```cpp
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Das „unordered_map“, von dem die Operatorfunktion Inhalte zuweist.

### <a name="remarks"></a>Hinweise

Die erste Version kopiert alle Elemente von *Rechts* in diese unordered_map.

Die zweite Version verschiebt alle Elemente von *Rechts* in diese unordered_map.

Alle Elemente, die in diesem unordered_map vor `operator=` ausgeführt werden, werden verworfen.

### <a name="example"></a>Beispiel

```cpp
// unordered_map_operator_as.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

int main( )
   {
   using namespace std;
   unordered_map<int, int> v1, v2, v3;
   unordered_map<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="unordered_mappointer"></a><a name="pointer"></a> unordered_map::p

Der Typ eines Zeigers auf ein Element.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Objekt, das als Zeiger auf ein Element der gesteuerten Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapreference"></a><a name="reference"></a> unordered_map:: Reference

Der Typ eines Verweises auf ein Element.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Objekt, das als Verweis auf ein Element der gesteuerten Sequenz fungieren kann.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_maprehash"></a><a name="rehash"></a> unordered_map:: rehash

Erstellt die Hashtabelle neu.

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>Parameter

*nbucket*\
Die angeforderte Anzahl von Buckets.

### <a name="remarks"></a>Hinweise

Die Member-Funktion ändert die Anzahl von Buchern in mindestens *nbucket* und erstellt die Hash Tabelle nach Bedarf neu.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_rehash.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="unordered_mapsize"></a><a name="size"></a> unordered_map:: size

Ermittelt die Anzahl von Elementen.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt die Länge der gesteuerten Sequenz zurück.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

// display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="unordered_mapsize_type"></a><a name="size_type"></a> unordered_map:: size_type

Der Typ eines Abstands ohne Vorzeichen zwischen zwei Elementen.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Hinweise

Der unsignierte Ganzzahltyp beschreibt ein Objekt, das die Länge jeder kontrollierten Sequenz darstellen kann. Er wird hier als Synonym für einen durch Implementierung definierten `T2`-Typ beschrieben.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_size_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
    }
```

```Output
size == 0
```

## <a name="unordered_mapswap"></a><a name="swap"></a> unordered_map:: Swap

Vertauscht den Inhalt von zwei Containern.

```cpp
void swap(unordered_map& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Container für den Tauschvorgang.

### <a name="remarks"></a>Hinweise

Die Member-Funktion tauscht die kontrollierten Sequenzen zwischen **`*this`** und *Rechts*aus. Wenn [unordered_map:: Get_allocator](#get_allocator) `() == right.get_allocator()` , erfolgt dies in konstanter Zeit, es wird nur dann eine Ausnahme ausgelöst, wenn das Objekt mit den gespeicherten Merkmalen des Typs kopiert `Tr` wird, und es werden keine Verweise, Zeiger oder Iteratoren ungültig, die Elemente in den beiden kontrollierten Sequenzen bestimmen. Andernfalls führt Sie proportional zur Anzahl der Elemente in den beiden kontrollierten Sequenzen eine Reihe von Elementzuweisungen und Konstruktoraufrufe aus.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }
```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_mapunordered_map"></a><a name="unordered_map"></a> unordered_map:: unordered_map

Erstellt ein container-Objekt.

```cpp
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& Equal
    const Allocator& Al);

template <class InIt>
unordered_map(
    InputIterator First,
    InputIterator Last,
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>Parameter

*Irdische*\
Das zu speichernde Zuweisungsobjekt.

*Zuschreiben*\
Das zu speichernde Vergleichsfunktionsobjekt.

*Hash*\
Das zu speichernde Hashfunktionsobjekt.

*Bucket_count*\
Die Mindestanzahl von Buckets.

*Richting*\
Der zu kopierende Container.

*Erstes*\
Die Position des ersten zu kopierenden Elements.

*Letzten*\
Die Position direkt über den letzten zu kopierenden Elements.

*IList*\
Das initializer_list-Element, das die zu kopierenden Elemente enthält.

### <a name="remarks"></a>Hinweise

Mit dem ersten Konstruktor wird eine Kopie der Sequenz angegeben, die von `right` gesteuert wird. Mit dem zweiten Konstruktor wird eine leere gesteuerte Sequenz angegeben. Mit dem dritten Konstruktor wird die Elementwertesequenz `[first, last)` eingefügt. Mit dem vierten Konstruktor wird eine Kopie der Sequenz angegeben, indem `right` verschoben wird.

Alle Konstruktoren initialisieren auch einige gespeicherte Werte. Für den Kopierkonstruktor werden die Werte von *Rechts*abgerufen. Andernfalls:

die Mindestanzahl von Buchern ist das Argument *Bucket_count*, falls vorhanden. Andernfalls ist es ein Standardwert, der hier als durch die Implementierung definierter Wert beschrieben wird `N0` .

Das Hash Funktions Objekt ist der Argument *Hash*, falls vorhanden. Andernfalls ist der Wert `Hash()` .

Das Vergleichs Funktions Objekt ist das Argument *Comp*, falls es vorhanden ist. Andernfalls ist der Wert `Pred()` .

Das *Zuordnungs*Objekt ist das Argument Al, falls es vorhanden ist. Andernfalls ist der Wert `Alloc()` .

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_construct.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <initializer_list>

using namespace std;

using Mymap = unordered_map<char, int>;

int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c2(8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    // display contents " [f 6] [e 5] [d 4]"
    for (const auto& c : c2) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c3(c1.begin(),
        c1.end(),
        8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c3) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c4(move(c3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c4) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Construct with an initializer_list
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });
    for (const auto& c : c5) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Initializer_list plus size and hash
    unordered_map<int, char, hash<char>> c7(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, and key_equal
    unordered_map<int, char, hash<char>, equal_to<char>> c8(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, key_equal, and allocator
    unordered_map<int, char, hash<char>, equal_to<char>> c9(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
}
```

```Output
[a, 1] [b, 2] [c, 3]
[d, 4] [e, 5] [f, 6]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]

[5, g] [6, h] [7, i] [8, j]
[a, 1] [b, 2] [c, 3]

[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
```

## <a name="unordered_mapvalue_type"></a><a name="value_type"></a> unordered_map:: value_type

Der Typ eines Elements.

```cpp
typedef std::pair<const Key, Ty> value_type;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt ein Element der gesteuerten Sequenz.

### <a name="example"></a>Beispiel

```cpp
// std__unordered_map__unordered_map_value_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>Weitere Informationen

[<unordered_map>](../standard-library/unordered-map.md)\
[Schütt](./stl-containers.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
