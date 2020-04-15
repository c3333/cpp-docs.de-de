---
title: hash_multiset-Klasse
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
ms.openlocfilehash: 8888f393e1058e3cd5ff968d9433b5306cac4949
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370656"
---
# <a name="hash_multiset-class"></a>hash_multiset-Klasse

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Die hash_multiset-Containerklasse ist eine Erweiterung der C++-Standardbibliothek und wird für das Speichern und schnelle Abrufen von Daten aus einer Auflistung verwendet, in der die Werte der enthaltenen Elemente als Schlüsselwerte fungieren und nicht eindeutig sein müssen.

## <a name="syntax"></a>Syntax

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der im hash_multiset-Objekt zu speichernde Elementdatentyp.

*Merkmale*\
Der Typ, der zwei Funktionsobjekte enthält, eines des Klassenvergleichs, das ein binäres Prädikat ist, das in der Lage ist, zwei Elementwerte als Sortierschlüssel zu vergleichen, um ihre relative Reihenfolge zu bestimmen, und eine Hashfunktion, die ein unäres Prädikat ist, das Schlüsselwerte der Elemente zu nicht signierten Ganzzahlen vom Typ `size_t`zuordnet. Das Argument ist optional und `hash_compare<Key, less<Key> >` ist der Standardwert.

*Zuweisung*\
Der Typ, der das gespeicherte Zuweisungsobjekt darstellt, mit dem Details zur Belegung und Freigabe von Arbeitsspeicher für das hash_multiset-Objekt gekapselt werden. Dieses Argument ist optional, und der Standardwert ist `allocator<Key>`.

## <a name="remarks"></a>Bemerkungen

Ein hash_multiset-Objekt ist:

- Ein assoziativer Container, der ein Container variabler Größe ist, der den effizienten Abruf von Elementwerten auf Grundlage eines zugeordneten Schlüsselwert unterstützt. Darüber hinaus ist es ein einfacher assoziativer Container, da die Elementwerte den Schlüsselwerten entsprechen.

- Umkehrbar, da ein bidirektionaler Iterator für den Zugriff auf die Elemente bereitgestellt wird.

- Gehasht, da die Elemente auf Grundlage des Werts einer Hashfunktion, die auf die Schlüsselwerte der Elemente angewendet wird, in Buckets gruppiert werden.

- Insofern eindeutig, da jedes der Elemente einen eindeutigen Schlüssel aufweisen muss. Da ein hash_multiset-Objekt auch ein einfacher assoziativer Container ist, sind seine Elemente ebenfalls eindeutig.

- Eine Klassenvorlage, da die bereitgestellte Funktionalität generisch ist und daher unabhängig vom spezifischen Datentyp ist, der als Elemente oder Schlüssel enthalten ist. Die für Elemente und Schlüssel zu verwendenden Datentypen werden stattdessen in der Klassenvorlage zusammen mit der Vergleichsfunktion und der Zuweisung als Parameter angegeben.

Der Hauptvorteil des Hashverfahrens gegenüber der Sortierung ist die größere Effizienz: Bei einem erfolgreichen Hashverfahren werden Einfüge-, Lösch- und Suchvorgänge in einer konstanten Durchschnittszeit durchgeführt, während die Zeit bei Sortiertechniken proportional zum Logarithmus der Anzahl von Elementen im Container ist. Der Schlüsselwert eines Elements in einem Satz darf nicht direkt geändert werden. Stattdessen müssen Sie alte Werte löschen und Elemente mit neuen Werten einfügen.

Die Auswahl des Containertyps sollte im Allgemeinen auf Grundlage des für die Anwendung erforderlichen Suchen und Einfügetyps erfolgen. Gehashte assoziative Container sind für Such-, Einfüge- und Entfernvorgänge optimiert. Die Memberfunktionen, die diese Vorgänge explizit unterstützen, sind effizient, wenn sie mit einer gut entworfenen Hashfunktion verwendet werden. Dann werden sie in einer Zeit ausgeführt, die im Durchschnitt konstant und nicht von der Anzahl von Elementen im Container abhängig ist. Eine ausgereifte Hashfunktion erzeugt eine vereinheitlichte Verteilung gehashter Werte und minimiert die Anzahl von Konflikten, bei denen ein Konflikt vorhergesagt wird, wenn unterschiedliche Schlüsselwerte dem gleichen gehashten Wert zugeordnet werden. Im schlimmsten Fall ist die Anzahl von Vorgängen bei der schlimmstmöglichen Hashfunktion zu der Anzahl von Elementen in der Sequenz proportional (lineare Zeit).

Ein hash_multiset-Objekt sollte der assoziative Container der Wahl sein, wenn die Bedingungen, mit denen die Werte den Schlüsseln zugeordnet werden, von der Anwendung erfüllt werden. Die Elemente eines hash_multiset-Objekts können Mehrfache sein und als eigene Sortierschlüssel dienen, sodass Schlüssel nicht eindeutig sind. Ein Modell für diesen Typ der Struktur ist eine geordnete Liste von z. B. Wörtern, in denen die Wörter möglicherweise mehrmals auftreten. Wenn mehrfaches Vorkommen der Wörter nicht zugelassen wurde, ist ein hash_set-Objekt die geeignete Containerstruktur. Wenn eindeutige Definitionen als Werte an die Liste von eindeutigen Schlüsselwörtern angefügt wurden, ist ein hash_map-Objekt eine äquivalente Struktur, um diese Daten zu enthalten. Wenn die Definitionen dagegen nicht eindeutig sind, ist ein hash_multimap-Objekt der geeignete Container.

Das hash_multiset-Objekt sortiert die gesteuerte Sequenz, indem ein gespeichertes Hashmerkmalsobjekt vom Typ [value_compare](#value_compare) aufgerufen wird. Auf das gespeicherte Objekt wird möglicherweise zugegriffen, indem die Memberfunktion [key_comp](#key_comp) aufrufen wird. Ein solches Funktionsobjekt muss sich wie ein `hash_compare<Key, less<Key> >`Objekt der Klasse verhalten. Insbesondere ergibt der Aufruf `Trait(Key)` `Key`für alle Werte *Schlüssel* des Typs eine Verteilung von Werten des Typs `size_t`.

Im Allgemeinen müssen die Elemente der Vorwärtsiteratoren etwas weniger als vergleichbar sein, um diese Sortierung zu erstellen, sodass beliebige zwei Elemente möglicherweise als gleichwertig bestimmt werden (in dem Sinne, dass keins geringer als das Andere ist), oder dass eins geringer als das Andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Etwas technischer betrachtet ist die Vergleichsfunktion ein binäres Prädikat, das eine strenge schwache Sortierung im mathematischen Sinn verursacht. Ein binäres Prädikat *f*( *x*, *y*) ist ein Funktionsobjekt, das zwei Argumentobjekte x und y und einen Rückgabewert von true oder false hat. Eine Sortierung, die auf ein hash_multiset-Objekt angewendet wird, ist eine strenge schwache Sortierung, wenn das binäre Prädikat irreflexiv, antisymmetrisch und transitiv und wenn die Äquivalenz transitiv ist, wobei die beiden Objekte x und y als äquivalent definiert sind, wenn sowohl *f*( *x*,*y*) als auch *f*( *y*, *x*) gleich FALSE sind. Wenn der stärkere Gleichheitszustand zwischen Schlüsseln die Äquivalenz ersetzt, erfolgt die Sortierung total (d. h., alle Elemente werden zueinander sortiert), und die verglichenen Schlüssel sind von den einander nicht mehr zu unterscheiden.

Die tatsächliche Reihenfolge der Elemente in der gesteuerten Sequenz hängt von der Hashfunktion, der Sortierfunktion und der aktuellen Größe der Hashtabelle ab, die im Containerobjekt gespeichert wird. Die aktuelle Größe der Hashtabelle kann nicht bestimmt werden. Deshalb kann die Reihenfolge der Elemente in der gesteuerten Sequenz im Allgemeinen nicht vorhergesagt werden. Das Einfügen von Elementen führt nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen von Elementen werden nur solche Iteratoren ungültig, die speziell auf die entfernten Elemente gezeigt haben.

Der von der hash_multiset-Klasse bereitgestellte Iterator ist ein bidirektionaler Iterator. Die Klassenmemberfunktionen „insert“ und „hash_multiset“ weisen allerdings Versionen auf, die als Vorlagenparameter einen abgeschwächten Eingabeiterator akzeptieren, dessen Funktionalitätsanforderungen weniger umfangreich sind als die von der Klasse bidirektionaler Iteratoren garantierten. Die verschiedenen Iteratorkonzepte bilden eine Family, die durch Verfeinerungen in ihrer Funktionen verknüpft ist. Jedes Iteratorkonzept hat sein eigenes hash_multiset-Objekt von Anforderungen, und die Annahmen der verwendenden Algorithmen müssen sich auf die von diesem Iteratortyp erfüllten Anforderungen beschränken. Es kann davon ausgegangen werden, dass ein Eingabeiterator möglicherweise so dereferenziert wird, dass er auf ein Objekt verweist und dieses möglicherweise zum folgenden Iterator in der Sequenz erhöht. Dies ist hinsichtlich der Funktionalität ein minimales hash_multiset-Objekt, allerdings genügt es, um sinnvoll über einen Bereich von Iteratoren [`first`, `last`] im Kontext der Klassenmemberfunktionen zu sprechen.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[hash_multiset](#hash_multiset)|Erstellt ein `hash_multiset`-Element, das leer oder die Kopie eines ganzen anderen `hash_multiset`-Elements oder eines Teils davon ist.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[allocator_type](#allocator_type)|Ein Typ, der die `allocator`-Klassentyp für das `hash_multiset`-Objekt darstellt.|
|[const_iterator](#const_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, der ein **const-Element** im lesen `hash_multiset`kann.|
|[const_pointer](#const_pointer)|Ein Typ, der einen Zeiger auf `hash_multiset`ein **const-Element** in einem bereitstellt.|
|[const_reference](#const_reference)|Ein Typ, der einen Verweis auf `hash_multiset` ein **const-Element** bereitstellt, das zum Lesen und Ausführen von **const-Vorgängen** in einem gespeichert ist.|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, der jedes **const-Element** im lesen `hash_multiset`kann.|
|[difference_type](#difference_type)|Ein ganzzahliger Typ mit Vorzeichen, der den Unterschied zwischen zwei Iteratoren bereitstellt, die auf Elemente im selben `hash_multiset`-Objekt verweisen.|
|[Iterator](#iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einer `hash_multiset` gelesen oder geändert werden kann.|
|[key_compare](#key_compare)|Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen im `hash_multiset`-Element zu bestimmen.|
|[key_type](#key_type)|Ein Typ, der ein Objekt beschreibt, das als Element eines `hash_set`-Objekts in seiner Kapazität als Sortierschlüssel gespeichert wird.|
|[Zeiger](#pointer)|Ein Typ, der einen Zeiger auf ein Element in einer `hash_multiset` bereitstellt.|
|[Verweis](#reference)|Ein Typ, der einen Verweis auf ein in einer `hash_multiset` gespeichertes Element bereitstellt.|
|[reverse_iterator](#reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einem umgekehrten `hash_multiset`-Element gelesen oder geändert werden kann.|
|[Size_type](#size_type)|Eine Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in `hash_multiset` darstellen kann.|
|[value_compare](#value_compare)|Ein Typ, der Folgendes bereitstellt: zwei Funktionsobjekte, ein binäres Prädikat der compare-Klasse, das zwei Elementwerte eines `hash_multiset`-Objekts vergleichen kann, um deren relative Reihenfolge zu bestimmen, und ein unäres Prädikat, das die Hashwerte der Elemente ermittelt.|
|[Value_type](#value_type)|Ein Typ, der ein Objekt beschreibt, das als Element eines `hash_multiset`-Objekts in seiner Kapazität als Wert gespeichert wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Beginnen](#begin)|Gibt einen Iterator zurück, der auf das erste Element im `hash_multiset`-Objekt verweist.|
|[cbegin](#cbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im `hash_multiset`-Element adressiert.|
|[cend](#cend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines `hash_multiset`-Elements nachfolgt.|
|[Klar](#clear)|Löscht alle Elemente einer `hash_multiset` auf.|
|[count](#count)|Gibt die Anzahl von Elementen in einem `hash_multiset`-Objekt zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.|
|[crbegin](#crbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im umgekehrten `hash_multiset`-Element adressiert.|
|[crend](#crend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten `hash_multiset`-Elements nachfolgt.|
|[emplace](#emplace)|Fügt ein Element ein, das vor Ort in ein `hash_multiset`-Element erstellt wird.|
|[emplace_hint](#emplace_hint)|Fügt ein Element ein, das vor Ort mit einem Platzierungshinweis in ein `hash_multiset`-Element erstellt wird.|
|[empty](#empty)|Testet, ob ein `hash_multiset`-Element leer ist.|
|[Ende](#end)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element einem `hash_multiset`-Element nachfolgt.|
|[equal_range](#equal_range)|Gibt ein Iteratorpaar jeweils bezogen auf das erste Element in einem `hash_multiset`-Objekt mit einem Schlüssel zurück, der größer als ein bestimmter Schlüssel ist, bzw. bezogen auf das erste Element im `hash_multiset`-Objekt mit einem Schlüssel, der größer oder gleich dem Schlüssel ist.|
|[erase](#erase)|Es wird ein Element oder ein Bereich von Elementen in einem `hash_multiset` von angegebenen Speicherorten entfernt, oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.|
|[find](#find)|Gibt einen Iterator zurück, der die Position eines Elements in einem `hash_multiset`-Element adressiert, das einen Schlüssel aufweist, der einen angegebenen Schlüssel entspricht.|
|[get_allocator](#get_allocator)|Gibt eine Kopie des zum Erstellen von `allocator` verwendeten `hash_multiset`-Objekts zurück.|
|[Einfügen](#insert)|Fügt ein Element oder einen Elementbereich in ein `hash_multiset`-Element ein.|
|[key_comp](#key_compare)|Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in `hash_multiset` verwendet wird.|
|[lower_bound](#lower_bound)|Gibt einen Iterator zum ersten Element in einem `hash_multiset`-Element mit einem Schlüssel zurück, der gleich oder größer ist, als ein angegebener Schlüssel.|
|[Max_size](#max_size)|Gibt die Maximallänge der `hash_multiset` zurück.|
|[rbegin](#rbegin)|Gibt einen Iterator zurück, der das erste Element in einem umgekehrten `hash_multiset`-Element adressiert.|
|[rend](#rend)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten `hash_multiset`-Elements nachfolgt.|
|[Größe](#size)|Gibt die Anzahl von Elementen in der `hash_multiset` zurück.|
|[swap](#swap)|Tauscht die Elemente zweier `hash_multiset`n.|
|[upper_bound](#upper_bound)|Gibt einen Iterator zum ersten Element in einem `hash_multiset`-Element mit einem Schlüssel zurück, der gleich oder größer ist als ein angegebener Schlüssel.|
|[value_comp](#value_comp)|Ruft eine Kopie des hash-traits-Objekts ab, das dazu verwendet wird, Elementschlüsselwerte in einem `hash_multiset`-Objekt zu hashen und zu sortieren.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[hash_multiset::operator=](#op_eq)|Ersetzt die Elemente des hash_multiset-Objekts durch eine Kopie eines anderen.|

## <a name="requirements"></a>Anforderungen

**Header:** \<hash_set>

**Namespace:** stdext

## <a name="hash_multisetallocator_type"></a><a name="allocator_type"></a>hash_multiset::allocator_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der die Zuweisungsklasse für das hash_multiset-Objekt darstellt.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Beispiel

In dem Beispiel für [get_allocator](#get_allocator) finden Sie ein Beispiel, das `allocator_type` verwendet.

## <a name="hash_multisetbegin"></a><a name="begin"></a>hash_multiset::begin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen Iterator zurück, der das erste Element im hash_multiset adressiert.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der das erste Element im hash_multiset adressiert oder auf den Speicherort hinweist, der auf einen leeren hash_multiset folgt.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `begin` `const_iterator`einem zugewiesen ist, können die Elemente im hash_multiset-Objekt nicht geändert werden. Wenn der Rückgabewert von `begin` `iterator`einem zugewiesen ist, können die Elemente im hash_multiset Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="hash_multisetcbegin"></a><a name="cbegin"></a>hash_multiset::cbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen const-Iterator zurück, der das erste Element im hash_multiset adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const-Iterator, der das erste Element in der [hash_multiset](../standard-library/hash-multiset-class.md) adressiert oder auf den Speicherort hinweist, der auf einer leeren `hash_multiset` folgt.

### <a name="remarks"></a>Bemerkungen

Bei dem Rückgabewert `cbegin` können die Elemente im `hash_multiset`-Objekt nicht geändert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="hash_multisetcend"></a><a name="cend"></a>hash_multiset::cend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der dem letzten Element einer hash_multiset nachfolgt.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const-Iterator, der den Speicherort adressiert, der dem letzten Element einer [hash_multiset](../standard-library/hash-multiset-class.md) nachfolgt. Wenn `hash_multiset` leer ist, gilt anschließend `hash_multiset::cend == hash_multiset::begin`.

### <a name="remarks"></a>Bemerkungen

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines `hash_multiset` erreicht hat. Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="hash_multisetclear"></a><a name="clear"></a>hash_multiset::klar

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Löscht alle Elemente eines hash_multiset.

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="hash_multisetconst_iterator"></a><a name="const_iterator"></a>hash_multiset::const_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein **const**-Element in der hash_multiset gelesen werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_iterator`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

In dem Beispiel für [begin](#begin) finden Sie ein Beispiel, das `const_iterator` verwendet.

## <a name="hash_multisetconst_pointer"></a><a name="const_pointer"></a>hash_multiset::const_pointer

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der einen Zeiger auf ein **const**-Element in einer hash_multiset bereitstellt.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_pointer`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [const_iterator](#const_iterator) für den Zugriff auf Elemente in einem **const** hash_multiset-Objekt verwendet werden.

## <a name="hash_multisetconst_reference"></a><a name="const_reference"></a>hash_multiset::const_reference

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der einen Verweis auf ein **const**-Element bereitstellt, das in einer hash_multiset zum Lesen und Ausführen von **const**-Vorgängen gespeichert ist.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="hash_multisetconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_multiset::const_reverse_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes **const**-Element im hash_multiset gelesen werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reverse_iterator`-Typ kann nicht den Wert eines Elements ändern und wird verwendet, um den hash_multiset in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Im Beispiel für [rend](#rend) wird verdeutlicht, wie ein `const_reverse_iterator` deklariert und verwendet wird.

## <a name="hash_multisetcount"></a><a name="count"></a>hash_multiset::zählen

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt die Anzahl von Elementen in einer hash_multiset-Klasse zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Schlüssel des Elements mit einem übereinstimmenden Schlüssel aus der hash_multiset-Klasse.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im hash_multiset mit dem von einem Parameter angegebenen Schlüssel.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Anzahl der Elemente im folgenden Bereich zurück:

\[lower_bound(*Taste*), upper_bound(*Taste*) ).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion „hash_multiset::count“ gezeigt.

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="hash_multisetcrbegin"></a><a name="crbegin"></a>hash_multiset::crbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen const-Iterator zurück, der das erste Element in einem umgekehrten hash_multiset adressiert.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler const-Iterator, mit dem das erste Element in einem umgekehrten [hash_multiset](../standard-library/hash-multiset-class.md) adressiert wird, bzw. mit dem das ehemals letzte Element im nicht umgekehrten `hash_multiset` adressiert wird.

### <a name="remarks"></a>Bemerkungen

`crbegin` wird bei einem umgekehrten `hash_multiset` auf die gleiche Weise verwendet wie [hash_multiset::begin](#begin) bei einem `hash_multiset`.

Bei dem Rückgabewert von `crbegin` kann das `hash_multiset`-Objekt nicht geändert werden.

Mit `crbegin` lässt sich eine `hash_multiset` rückwärts durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="hash_multisetcrend"></a><a name="crend"></a>hash_multiset::crend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten hash_multiset nachfolgt.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const_reverse-Iterator, der den Standort anspricht, der dem letzten Element in einem umgekehrten [hash_multiset](../standard-library/hash-multiset-class.md) nachfolgt (der Speicherort, der dem ersten Element im nicht umgekehrten `hash_multiset` vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einem umgekehrten `hash_multiset` auf die gleiche Weise verwendet wie [hash_multiset::end](#end) bei einem `hash_multiset`.

Bei dem Rückgabewert von `crend` kann das `hash_multiset`-Objekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob ein umgekehrter Iterator das Ende seines hash_multiset erreicht hat.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="hash_multisetdifference_type"></a><a name="difference_type"></a>hash_multiset::difference_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein ganzzahliger Typ mit Vorzeichen, der den Unterschied zwischen zwei Iteratoren bereitstellt, die auf Elemente im selben hash_multiset verweisen.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

`difference_type` ist der Typ, der beim Subtrahieren oder Inkrementieren über Iteratoren des Containers zurückgegeben wird. `difference_type` wird normalerweise verwendet, um die Anzahl von Elementen im Bereich [`first`, `last`) zwischen den Iteratoren `first` und `last` darzustellen. Dazu gehört das Element, auf das durch `first` gezeigt wird und der Bereich von Elementen bis zu (aber nicht einschließlich) dem Element, auf das durch `last` gezeigt wird.

Beachten Sie, dass, obwohl `difference_type` für alle Iteratoren verfügbar ist, die die Anforderungen für einen Eingabeiterator erfüllen, einschließlich der Klasse bidirektionaler Iteratoren, die von umkehrbaren Containern wie Satz unterstützt werden. Subtraktion zwischen Iteratoren wird nur von Iteratoren mit wahlfreiem Zugriff unterstützt, die von einem Container mit wahlfreiem Zugriff, z.B. Vektor oder Deque bereitgestellt werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="hash_multisetemplace"></a><a name="emplace"></a>hash_multiset::emplace

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Fügt ein Element, das vor Ort erstellt wird, in ein hash_multiset ein.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Val*|Der Wert eines in das [hash_multiset](../standard-library/hash-multiset-class.md) einzufügenden Elements, es sei denn, das `hash_multiset` enthält dieses Element bereits oder, üblicher, enthält ein Element, dessen Schlüssel gleichwertig sortiert wird.|

### <a name="return-value"></a>Rückgabewert

Die `emplace`-Memberfunktion gibt einen Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="hash_multisetemplace_hint"></a><a name="emplace_hint"></a>hash_multiset::emplace_hint

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Fügt ein Element ein, das vor Ort mit einem Platzierungshinweis in einem hash_multiset erstellt wird.

```cpp
template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& val);
```

### <a name="parameters"></a>Parameter

*Val*\
Der Wert eines in das [hash_multiset](../standard-library/hash-multiset-class.md) einzufügenden Elements, es sei denn, das `hash_multiset` enthält dieses Element bereits oder, üblicher, enthält ein Element, dessen Schlüssel gleichwertig sortiert wird.

*Wo*\
Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Einfügung kann in amortisierter konstanter Zeit anstelle der logarithmischen Zeit erfolgen, wenn die Einfügemarke unmittelbar *folgt, wo*.)

### <a name="return-value"></a>Rückgabewert

Die [hash_multiset::emplace](#emplace)-Memberfunktion gibt einen Iterator zurück, der auf die Position zeigt, in der das neue Element in das `hash_multiset` eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Das Einfügen kann in der amortisierten konstanten Zeit anstelle der logarithmischen Zeit erfolgen, wenn die Einfügemarke unmittelbar an *der folgt.*

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="hash_multisetempty"></a><a name="empty"></a>hash_multiset::leer

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Testet, ob ein hash_multiset leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das hash_multiset leer ist; **FALSE**, wenn es nicht leer ist.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="hash_multisetend"></a><a name="end"></a>hash_multiset::Ende

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines hash_set nachfolgt.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der den Speicherort adressiert, der dem letzten Element eines hash_multiset nachfolgt. Ist das hash_multiset leer, folgt anschließend „hash_multiset::end == hash_multiset::begin“.

### <a name="remarks"></a>Bemerkungen

`end`wird verwendet, um zu testen, ob ein Iterator das Ende seiner hash_multiset erreicht hat. Der von `end` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="hash_multisetequal_range"></a><a name="equal_range"></a>hash_multiset::equal_range

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt ein Iteratorpaar jeweils zum ersten Element in einem hash_multiset mit einem Schlüssel zurück, der größer als ein bestimmter Schlüssel ist, bzw. zum ersten Element in einem hash_multiset mit einem Schlüssel, der größer oder gleich dem Schlüssel ist.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden hash_multiset verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein Iteratorenpaar, bei der das Erste der [lower_bound](#lower_bound) des Schlüssels und das zweite Paar der [upper_bound](#upper_bound) des Schlüssels ist.

Sie können auf den ersten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **verwenden** Sie \*( `pr`. **zuerst**). Sie können auf den zweiten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **zweiten** und um den oberen gebundenen Iterator zu dereferenzieren, verwenden \*Sie ( `pr`. **zweitens**).

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="hash_multiseterase"></a><a name="erase"></a>hash_multiset::löschen

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Es wird ein Element oder ein Bereich von Elementen in einer hash_multiset von angegebenen Speicherorten entfernt oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.

```cpp
iterator erase(iterator where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parameter

*Wo*\
Die Position des aus der hash_multiset zu entfernenden Elements.

*Ersten*\
Die Position des ersten Elements, das aus der hash_multiset entfernt werden soll.

*letzte*\
Die Position direkt hinter dem letzten aus der hash_multiset entfernten Element.

*Schlüssel*\
Der Schlüssel des aus der hash_multiset zu entfernenden Elements.

### <a name="return-value"></a>Rückgabewert

Bei den ersten beiden Memberfunktionen ist es ein bidirektionaler Iterator, der das erste über die entfernten Elemente hinaus verbliebene Element festlegt, oder ein Zeiger auf das das Ende der hash_multiset, wenn kein solches Element vorhanden ist. Für die dritte Memberfunktion ist es die Anzahl der von hash_multiset entfernten Elemente.

### <a name="remarks"></a>Bemerkungen

Von der Memberfunktionen wird nie eine Ausnahme ausgelöst.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion „hash_multiset::erase“ gezeigt.

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="hash_multisetfind"></a><a name="find"></a>hash_multiset::finden

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen Iterator zurück, der die Position eines Elements in einem hash_set adressiert, das einen Schlüssel aufweist, der einem angegebenen Schlüssel entspricht.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden hash_multiset übereinstimmt.

### <a name="return-value"></a>Rückgabewert

Ein [Iterator](#iterator) oder [const_iterator](#const_iterator), der den ersten Speicherort eines Elements, das gleich dem eines angegebenen Schlüssel ist, adressiert, oder der Speicherort, der dem letzten Element in dem hash_multiset nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Iterator zurück, der ein `equivalent` Element in der hash_multiset anspricht, dessen Sortierschlüssel für den Argumentschlüssel unter einem binären Prädikat ist, das eine Reihenfolge auf der Grundlage einer weniger als Vergleichbarkeitsbeziehung induziert.

Wenn der Rückgabewert von `find` `const_iterator`einem zugewiesen ist, kann das hash_multiset Objekt nicht geändert werden. Wenn der Rückgabewert von `find` `iterator`einem zugewiesen ist, kann das hash_multiset Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="hash_multisetget_allocator"></a><a name="get_allocator"></a>hash_multiset::get_allocator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt eine Kopie des Zuweisungsobjekts zurück, das zum Erstellen des hash_multiset verwendet wird.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zuweisung, die von hash_multiset zur Arbeitsspeicherverwaltung verwendet wird, der der Vorlagenparameter `Allocator` der Klasse ist.

Weitere Informationen zu `Allocator` finden Sie im Abschnitt „Hinweise“ des Themas [hash_multiset-Klasse](../standard-library/hash-multiset-class.md).

### <a name="remarks"></a>Bemerkungen

Zuweisungen für das hash_multiset geben an, wie die Klasse einen Speicher verwaltet. Für die meisten Programmieranforderungen reichen die Standard-Zuweisungen aus C++-Standardbibliothek-Containerklassen aus. Schreiben und Verwenden Ihrer eigener Zuweisungsklasse ist ein C++ -Thema für Fortgeschrittene.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="hash_multisethash_multiset"></a><a name="hash_multiset"></a>hash_multiset::hash_multiset

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Erstellt ein `hash_multiset`-Element, das leer oder die Kopie eines ganzen anderen `hash_multiset`-Elements oder eines Teils davon ist.

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parameter

*Al*\
Die für dieses `hash_multiset`-Objekt zu verwendende Speicherzuweisungsklasse, dessen Standard `Allocator` ist.

*Comp*\
Die Vergleichsfunktion vom Typ `const Traits`, die verwendet wird, um die Elemente in `hash_multiset`, deren Standard `hash_compare` ist, zu sortieren.

*Richting*\
Das `hash_multiset`-Element, von dem das erstellte `hash_multiset`-Element eine Kopie sein soll.

*Ersten*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*letzte*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*Ilist*\
Das initializer_list-Element, das die zu kopierenden Elemente enthält.

### <a name="remarks"></a>Bemerkungen

In allen Konstruktoren wird Zuweisungsobjekttyp gespeichert, mit dem der Arbeitsspeicher für das `hash_multiset` verwaltet wird und das später zurückgegeben werden kann, indem [hash_multiset::get_allocator](#get_allocator) aufgerufen wird. Der Zuweisungsparameter wird häufig aus den Klassendeklarationen und den Vorverarbeitungsmakros weggelassen, die zum Ersetzen alternativer Zuweisungen verwendet werden.

Alle Konstruktoren initialisieren ihrer hash_multisets-Elemente.

In allen Konstruktoren wird ein Funktionsobjekt vom Typ `Traits` gespeichert, der verwendet wird, um unter den Schlüsseln des `hash_multiset` eine Sortierung vorzunehmen, und das später zurückgegeben werden kann, indem [hash_multiset::key_comp](#key_comp) aufgerufen wird. Weitere Informationen zu `Traits` finden Sie im Thema [hash_multiset-Klasse](../standard-library/hash-multiset-class.md).

Die ersten drei Konstruktoren `hash_multiset`geben einen leeren Anfangswert an, den zweiten, der den Typ der Vergleichsfunktion (*Comp*) angibt, die zum Festlegen der Reihenfolge der Elemente verwendet werden soll, und der dritte, der explizit den zu verwendenden Zuweisungstyp (*Al*) angibt. Mit dem Schlüsselwort **explicit** werden bestimmte Arten automatischer Typumwandlung unterdrückt.

Mit dem vierten Konstruktor wird `hash_multiset` `Right` verschoben.

Die fünften, sechsten und siebten Konstruktoren verwenden ein initializer_list-Element.

Mit den letzten drei Konstruktoren wird der Bereich [`first`, `last`]eines `hash_multiset` mit steigernder Explizitheit kopiert, indem der Typ der Vergleichsfunktion der Klasse „Compare“ und der „allocator“ angegeben werden.

Die tatsächliche Reihenfolge der Elemente in einem gehashten festgelegten Container hängt von der Hashfunktion, von der Sortierfunktion und der aktuellen Größe der Hashtabelle ab und kann im Allgemeinen nicht vorausgesagt werden, wie das beim festgelegten Container der Fall wäre, bei dem sie von der Sortierfunktion allein bestimmt würde.

## <a name="hash_multisetinsert"></a><a name="insert"></a>hash_multiset::einfügen

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Fügt ein Element oder einen Elementbereich in ein hash_multiset-Element ein.

```cpp
iterator insert(
    const Type& value);

iterator insert(
    iterator where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& value);

iterator insert(
    Iterator where,
    const Type& value);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
iterator insert(
    ValTy&& value);

template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& value);
```

### <a name="parameters"></a>Parameter

*Wert*\
Der Wert eines in das hash_multiset-Element einzufügenden Elements, es sei denn, das hash_multiset-Element enthält dieses Element bereits oder, üblicher, enthält ein Element, dessen Schlüssel gleichwertig sortiert wird.

*Wo*\
Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Einfügung kann in amortisierter konstanter Zeit anstelle der logarithmischen Zeit erfolgen, wenn die Einfügemarke unmittelbar *folgt, wo*.)

*Ersten*\
Die Position des ersten Elements, aus von einem hash_multiset-Element kopiert werden soll.

*letzte*\
Die Position direkt hinter den letzten Element, das aus einem hash_multiset-Element kopiert werden soll.

*Ilist*\
Das initializer_list-Element, das die zu kopierenden Elemente enthält.

### <a name="return-value"></a>Rückgabewert

Die ersten zwei Memberfunktionen geben ein Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element eingefügt wurde.

Die folgenden drei Memberfunktionen verwenden ein initializer_list-Element.

Die dritte Memberfunktion fügt die Sequenz von Elementwerten in ein hash_multiset-Element entsprechend jeden Elements ein, das von einem Iterator im Bereich [`first`, `last`) eines angegebenen hash_multiset-Elements adressiert wird.

### <a name="remarks"></a>Bemerkungen

Das Einfügen kann in der amortisierten konstanten Zeit für die Hinweisversion von insert anstelle der logarithmischen Zeit erfolgen, wenn die Einfügemarke unmittelbar *folgt, wo*.

## <a name="hash_multisetiterator"></a><a name="iterator"></a>hash_multiset::iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einem hash_multiset gelesen oder geändert werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `iterator` Typ kann verwendet werden, um den Wert eines Elements zu ändern.

### <a name="example"></a>Beispiel

Ein Beispiel [begin](#begin) für die Deklariieren `iterator`und Verwenden von .

## <a name="hash_multisetkey_comp"></a><a name="key_comp"></a>hash_multiset::key_comp

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in eines hash_multiset verwendet wird.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den hash_multiset Vorlagenparameter *Traits*zurück, der Funktionsobjekte enthält, die zum Hashen und Zuordnen der Elemente des Containers verwendet werden.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [hash_multiset Klasse.](../standard-library/hash-multiset-class.md)

### <a name="remarks"></a>Bemerkungen

Das gespeicherte Objekt definiert eine Memberfunktion

`bool operator<(const Key& _xVal, const Key& _yVal);`

die **TRUE** zurückgibt, wenn `_xVal` vorangestellt ist und nicht gleich `_yVal` in der Sortierreihenfolge ist.

Beachten Sie, dass sowohl [key_compare](#key_compare) als auch [value_compare](#value_compare) Synonyme für den Vorlagenparameter *Traits* sind. Beide Typen werden für die hash_multiset- und hash_multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den hash_map und hash_multimap-Klassen.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="hash_multisetkey_compare"></a><a name="key_compare"></a>hash_multiset::key_compare

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der Folgendes bereitstellt: zwei Funktionsobjekte, ein binäres Prädikat der compare-Klasse, das zwei Elementwerte eines hash_multiset vergleichen kann, um deren relative Reihenfolge zu bestimmen, und ein unäres Prädikat, das die Hashwerte der Elemente ermittelt.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Bemerkungen

`key_compare`ist ein Synonym für den Vorlagenparameter *Traits*.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [hash_multiset Klasse.](../standard-library/hash-multiset-class.md)

Beachten Sie, dass sowohl `key_compare` als auch value_compare Synonyme für den Vorlagenparameter *Traits* sind. Beide Typen werden für die hash_set und hash_multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den hash_map und hash_multimap-Klassen.

### <a name="example"></a>Beispiel

Im Beispiel für [key_comp](#key_comp) wird verdeutlicht, wie `key_compare` deklariert und verwendet wird.

## <a name="hash_multisetkey_type"></a><a name="key_type"></a>hash_multiset::key_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Eine Typ, der ein Funktionsobjekt bereitstellt, das Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen im hash_multiset zu bestimmen.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

`key_type`ist ein Synonym für den Vorlagenparameter *Key*.

Beachten Sie, dass sowohl `key_type` als auch [value_type](../standard-library/hash-set-class.md#value_type) Synonyme für den Vorlagenparameter *Key* sind. Beide Typen werden für den Satz und multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den Zuordnungs- und multimap-Klassen.

Weitere Informationen zu *Schlüssel*finden Sie im Abschnitt "Bemerkungen" des Themas [hash_multiset Klasse.](../standard-library/hash-multiset-class.md)

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie ein `key_type` deklariert und verwendet wird.

## <a name="hash_multisetlower_bound"></a><a name="lower_bound"></a>hash_multiset::lower_bound

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen Iterator zum ersten Element in einem hash_multiset mit einem Schlüssel zurück, der gleich oder größer als ein angegebener Schlüssel ist.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden hash_multiset verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein [Iterator](#iterator) oder [const_iterator](#const_iterator), der den Speicherort eines Elements in einem ersten hash_multiset mit einem Schlüssel adressiert, der gleich oder größer als der Argumentschlüssel ist, oder der den Speicherort des nachfolgenden letzten Elements im hash_multiset adressiert, wenn kein Treffer für den Schlüssen gefunden wird.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="hash_multisetmax_size"></a><a name="max_size"></a>hash_multiset::max_size

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt die Maximallänge des hash_multiset zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die mögliche Maximallänge des hash_multiset.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="hash_multisetoperator"></a><a name="op_eq"></a>hash_multiset::operator=

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ersetzt die Elemente des hash_multiset-Objekts durch eine Kopie eines anderen.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Richting*|Das [hash_multiset](../standard-library/hash-multiset-class.md), das in das `hash_multiset` kopiert wird.|

### <a name="remarks"></a>Bemerkungen

Nach dem Löschen vorhandener `hash_multiset`Elemente `operator=` in einem kopiert oder verschiebt sich der Inhalt von *rechts* in die `hash_multiset`.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="hash_multisetpointer"></a><a name="pointer"></a>hash_multiset::pointer

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der einen Zeiger auf ein Element in einem hash_multiset bereitstellt.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `pointer` Typ kann verwendet werden, um den Wert eines Elements zu ändern.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem multiset-Objekt verwendet werden.

## <a name="hash_multisetrbegin"></a><a name="rbegin"></a>hash_multiset::rbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen Iterator zurück, der das erste Element in einem umgekehrten hash_multiset adressiert.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, mit dem das erste Element in einem umgekehrten hash_multiset adressiert wird, bzw. mit dem das ehemals letzte Element im nicht umgekehrten hash_multiset adressiert wird.

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einem umgekehrten hash_multiset auf die gleiche Weise verwendet wie [begin](#begin) mit einem hash_multiset.

Wenn der Rückgabewert von `rbegin` einem `const_reverse_iterator` zugewiesen wird, kann das hash_multiset-Objekt nicht geändert werden. Wenn der Rückgabewert von `rbegin` einem `reverse_iterator` zugewiesen wird, kann das hash_multiset-Objekt geändert werden.

Mit `rbegin` kann ein hash_multiset rückwärts durchlaufen werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="hash_multisetreference"></a><a name="reference"></a>hash_multiset::Referenz

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der einen Verweis auf einem hash_multiset gespeichertes Element bereitstellt.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="hash_multisetrend"></a><a name="rend"></a>hash_multiset::rend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten hash_multiset nachfolgt.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der den Standort anspricht, der dem letzten Element in einem umgekehrten hash_multiset nachfolgt (der Speicherort, der dem ersten Element im nicht umgekehrten hash_multiset vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einem umgekehrten hash_multiset auf die gleiche Weise verwendet wie [end](#end) mit einem hash_multiset.

Wenn der Rückgabewert von `rend` einem `const_reverse_iterator` zugewiesen wird, kann das hash_multiset-Objekt nicht geändert werden. Wenn der Rückgabewert von `rend` einem `reverse_iterator` zugewiesen wird, kann das hash_multiset-Objekt geändert werden. Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

`rend` kann verwendet werden, um zu testen, ob ein umgekehrter Iterator das Ende seines hash_multiset erreicht hat.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="hash_multisetreverse_iterator"></a><a name="reverse_iterator"></a>hash_multiset::reverse_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einem umgekehrten hash_multiset gelesen oder geändert werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `reverse_iterator`-Typ wird verwendet, um den hash_multiset in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Im Beispiel für [rbegin](#rbegin) wird verdeutlicht, wie ein `reverse_iterator` deklariert und verwendet wird.

## <a name="hash_multisetsize"></a><a name="size"></a>hash_multiset::Größe

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt die Anzahl von Elementen in hash_multiset zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge von hash_multiset.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="hash_multisetsize_type"></a><a name="size_type"></a>hash_multiset::size_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einem hash_multiset darstellen kann.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im Beispiel für [size](#size) wird verdeutlicht, wie ein `size_type` deklariert und verwendet wird.

## <a name="hash_multisetswap"></a><a name="swap"></a>hash_multiset::swap

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Tauscht die Elemente zweier hash_multisets aus.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Das hash_multiset-Argument, das die Elemente bereitstellt mit der das Ziel-hash_multiset getauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion macht keine Verweise, Zeiger oder Iteratoren ungültig, die Elemente in zwei hash_multisets bezeichnet, dessen Elemente ausgetauscht werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="hash_multisetupper_bound"></a><a name="upper_bound"></a>hash_multiset::upper_bound

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Gibt einen Iterator zum ersten Element in einem hash_multiset mit einem Schlüssel zurück, der größer als ein angegebener Schlüssel ist.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden hash_multiset verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein [Iterator](#iterator) oder [const_iterator](#const_iterator), der den Speicherort eines Elements in einem ersten hash_multiset mit einem Schlüssel adressiert, der größer als der Argumentschlüssel ist, oder der den Speicherort des nachfolgenden letzten Elements im hash_multiset adressiert, wenn kein Treffer für den Schlüssen gefunden wird.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="hash_multisetvalue_comp"></a><a name="value_comp"></a>hash_multiset::value_comp

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Elementwerte in einem hash_mulltiset verwendet wird.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den hash_multiset Vorlagenparameter *Traits*zurück, der Funktionsobjekte enthält, die zum Hashen und Zuordnen von Elementen des Containers verwendet werden.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [hash_multiset Klasse.](../standard-library/hash-multiset-class.md)

### <a name="remarks"></a>Bemerkungen

Das gespeicherte Objekt definiert eine Memberfunktion

**bool operator**( **constKey&**`_xVal`, **const Key&** *_yVal*);

die **TRUE** zurückgibt, wenn `_xVal` vorangestellt ist und nicht gleich `_yVal` in der Sortierreihenfolge ist.

Beachten Sie, dass sowohl [key_compare](#key_compare) als auch [value_compare](#value_compare) Synonyme für den Vorlagenparameter *Traits* sind. Beide Typen werden für die hash_multiset- und hash_multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den hash_map und hash_multimap-Klassen.

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="hash_multisetvalue_compare"></a><a name="value_compare"></a>hash_multiset::value_compare

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der Folgendes bereitstellt: zwei Funktionsobjekte, ein binäres Prädikat der compare-Klasse, das zwei Elementwerte eines hash_multiset vergleichen kann, um deren relative Reihenfolge zu bestimmen, und ein unäres Prädikat, das die Hashwerte der Elemente ermittelt.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Bemerkungen

`value_compare`ist ein Synonym für den Vorlagenparameter *Traits*.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [hash_multiset Klasse.](../standard-library/hash-multiset-class.md)

Beachten Sie, `value_compare` dass sowohl [key_compare](#key_compare) als auch Synonyme für den Vorlagenparameter *Traits*sind. Beide Typen werden für die Klassen „set“ und „multiset“ bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den Klassen „map“ und „multimap“.

### <a name="example"></a>Beispiel

Im Beispiel für [value_comp](#value_comp) wird verdeutlicht, wie ein `value_compare` deklariert und verwendet wird.

## <a name="hash_multisetvalue_type"></a><a name="value_type"></a>hash_multiset::value_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multiset-Klasse](../standard-library/unordered-multiset-class.md).

Ein Typ, der ein Objekt beschreibt, das als Element eines hash_multiset in seiner Kapazität als Wert gespeichert wird.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Beispiel

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standardbibliotheksreferenz](../standard-library/cpp-standard-library-reference.md)
