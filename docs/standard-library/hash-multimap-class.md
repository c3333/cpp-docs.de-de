---
title: hash_multimap-Klasse
ms.date: 10/18/2018
f1_keywords:
- hash_map/stdext::hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
helpviewer_keywords:
- stdext::hash_multimap
- stdext::hash_multimap::allocator_type
- stdext::hash_multimap::const_iterator
- stdext::hash_multimap::const_pointer
- stdext::hash_multimap::const_reference
- stdext::hash_multimap::const_reverse_iterator
- stdext::hash_multimap::difference_type
- stdext::hash_multimap::iterator
- stdext::hash_multimap::key_compare
- stdext::hash_multimap::key_type
- stdext::hash_multimap::mapped_type
- stdext::hash_multimap::pointer
- stdext::hash_multimap::reference
- stdext::hash_multimap::reverse_iterator
- stdext::hash_multimap::size_type
- stdext::hash_multimap::value_type
- stdext::hash_multimap::begin
- stdext::hash_multimap::cbegin
- stdext::hash_multimap::cend
- stdext::hash_multimap::clear
- stdext::hash_multimap::count
- stdext::hash_multimap::crbegin
- stdext::hash_multimap::crend
- stdext::hash_multimap::emplace
- stdext::hash_multimap::emplace_hint
- stdext::hash_multimap::empty
- stdext::hash_multimap::end
- stdext::hash_multimap::equal_range
- stdext::hash_multimap::erase
- stdext::hash_multimap::find
- stdext::hash_multimap::get_allocator
- stdext::hash_multimap::insert
- stdext::hash_multimap::key_comp
- stdext::hash_multimap::lower_bound
- stdext::hash_multimap::max_size
- stdext::hash_multimap::rbegin
- stdext::hash_multimap::rend
- stdext::hash_multimap::size
- stdext::hash_multimap::swap
- stdext::hash_multimap::upper_bound
- stdext::hash_multimap::value_comp
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
ms.openlocfilehash: 089204ac77403923d38f198d53b3ff711e6a4963
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560821"
---
# <a name="hash_multimap-class"></a>hash_multimap-Klasse

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Die Containerklasse „hash_multimap“ ist eine Erweiterung der C++-Standardbibliothek und wird für das Speichern und schnelle Abrufen von Daten aus einer Auflistung verwendet, in der jedes Element ein Paar mit einem Sortierschlüssel, dessen Wert nicht eindeutig sein muss und einem zugeordneten Datenwert ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parameter

*Wichtigen*\
Der im hash_multimap-Element zu speichernde Schlüsseldatentyp.

*Sorte*\
Der im hash_multimap-Element zu speichernde Elementdatentyp.

*Aufweisen*\
Der Typ, der zwei Funktions Objekte enthält, einer der Klassen *Merkmale* , der zwei Element Werte als Sortierschlüssel vergleichen kann, um ihre relative Position zu bestimmen, und eine Hash Funktion, bei der es sich um ein unäres Prädikat für die Zuordnung der Elemente ohne Vorzeichen vom Typ handelt `size_t` . Das Argument ist optional und `hash_compare<Key, less<Key>>` ist der Standardwert.

*Allocator*\
Der Typ, mit dem das gespeicherte Zuordnungsobjekt darstellt wird, mit dem Details zum Belegen und Freigeben des Arbeitsspeichers des hash_multimap-Elements gekapselt werden. Dieses Argument ist optional, und der Standardwert ist `allocator<pair <const Key, Type>>`.

## <a name="remarks"></a>Bemerkungen

Das hash_multimap-Element ist:

- Ein assoziativer Container, der ein Container variabler Größe ist, der den effizienten Abruf von Elementwerten auf Grundlage eines zugeordneten Schlüsselwert unterstützt.

- Umkehrbar, da ein bidirektionaler Iterator für den Zugriff auf die Elemente bereitgestellt wird.

- Gehasht, da die Elemente auf Grundlage des Werts einer Hashfunktion, die auf die Schlüsselwerte der Elemente angewendet wird, in Buckets gruppiert werden.

- Mehrfach, da die Elemente keine eindeutige Schlüssel aufweisen müssen, damit ein Schlüsselwert über viele zugeordnete Elementdatenwerte verfügen kann.

- Ein Paar assoziativer Container, da sich die Elementwerte von den Schlüsselwerten unterscheiden.

- Eine Klassen Vorlage, da die von ihr bereitgestellte Funktionalität generisch und daher unabhängig vom jeweiligen Typ der Daten ist, die als Elemente oder Schlüssel enthalten sind. Die für Elemente und Schlüssel zu verwendenden Datentypen werden stattdessen in der Klassenvorlage zusammen mit der Vergleichsfunktion und der Zuweisung als Parameter angegeben.

Der Hauptvorteil des Hashverfahrens gegenüber der Sortierung ist die größere Effizienz. Bei einem erfolgreichen Hashverfahren werden Einfüge-, Lösch- und Suchvorgänge, verglichen mit einer Zeit, die zum Logarithmus der Anzahl von Elementen im Container für Sortiertechniken proportional ist, in einer konstanten Durchschnittszeit durchgeführt. Der Wert eines Elements in einem hash_multimap-Element, aber nicht der zugehörige Schlüsselwert, werden möglicherweise direkt geändert. Stattdessen müssen die Schlüsselwerte, die alten Elementen zugeordnet sind, gelöscht, und stattdessen neuen Schlüsselwerten für neue Elemente zugeordnet werden.

Die Auswahl des Containertyps sollte im Allgemeinen auf Grundlage des für die Anwendung erforderlichen Suchen und Einfügetyps erfolgen. Gehashte assoziative Container sind für Such-, Einfüge- und Entfernvorgänge optimiert. Die Memberfunktionen, die diese Vorgänge explizit unterstützen, sind effizient, wenn sie mit einer gut entworfenen Hashfunktion verwendet werden. Dann werden sie in einer Zeit ausgeführt, die im Durchschnitt konstant und nicht von der Anzahl von Elementen im Container abhängig ist. Eine ausgereifte Hashfunktion erzeugt eine vereinheitlichte Verteilung gehashter Werte und minimiert die Anzahl von Konflikten, bei denen ein Konflikt vorhergesagt wird, wenn unterschiedliche Schlüsselwerte dem gleichen gehashten Wert zugeordnet werden. Im schlimmsten Fall ist die Anzahl von Vorgängen bei der schlimmstmöglichen Hashfunktion zu der Anzahl von Elementen in der Sequenz proportional (lineare Zeit).

Das hash_multimap-Element sollte der ausgewählte assoziative Container sein, wenn die Bedingungen, mit denen die Werte von der Anwendung den Schlüsseln zugeordnet werden, erfüllt werden. Ein Modell für diesen Strukturtyp ist eine sortierte Liste von Schlüsselwörtern mit zugeordneten Zeichenfolgewerten, die, sagen wir, Definitionen bereitstellen, in denen die Wörter nicht immer eindeutig definiert wurden. Wenn die Schlüsselwörter stattdessen eindeutig definiert werden, damit die Schlüssel eindeutig sind, ist ein hash_map-Element der gewählte Container. Wenn hingegen nur die Wortliste gespeichert wurden, ist ein hash_set-Element der richtige Container. Wenn mehrfaches Vorkommen der Wörter zugelassen wird, ist ein hash_multiset-Element die geeignete Containerstruktur.

Das hash_multimap-Element sortiert die gesteuerte Sequenz, indem ein gespeichertes `Traits`-Hashobjekt des Objekts [value_compare](../standard-library/value-compare-class.md) aufgerufen wird. Auf das gespeicherte Objekt wird möglicherweise zugegriffen, indem die Memberfunktion [key_comp](../standard-library/hash-map-class.md#key_comp) aufrufen wird. Ein solches Funktions Objekt muss sich wie ein Objekt der Klasse Hash_compare Verhalten [hash_compare](../standard-library/hash-compare-class.md) `<Key, less<Key>>` . Insbesondere für alle `Key`-Werte des Typs `Key`, erreicht der `Traits (Key)`-Aufruf eine Verteilung der Werte vom Typ `size_t`.

Im Allgemeinen müssen die Elemente der Vorwärtsiteratoren etwas weniger als vergleichbar sein, um diese Sortierung zu erstellen, sodass beliebige zwei Elemente möglicherweise als gleichwertig bestimmt werden (in dem Sinne, dass keins geringer als das Andere ist), oder dass eins geringer als das Andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Etwas technischer betrachtet ist die Vergleichsfunktion ein binäres Prädikat, das eine strenge schwache Sortierung im mathematischen Sinn verursacht. Bei einem binären f (x, y)-Prädikat handelt es sich um ein Funktions Objekt, das zwei Argument Objekte `x` und `y` und einen Rückgabewert von **`true`** oder aufweist **`false`** . Eine für einen Hash_multimap vorgegebene Reihenfolge ist eine strikte schwache Reihenfolge, wenn das binäre Prädikat unreflexiv, antisymmetrisch und transitiv ist und wenn die Äquivalenz transitiv ist, wobei zwei Objekte `x` und `y` als Äquivalent definiert werden, wenn sowohl f (x, y) als auch f (y, x) sind **`false`** . Wenn der stärkere Gleichheitszustand zwischen Schlüsseln die Äquivalenz ersetzt, erfolgt die Sortierung total (d. h., alle Elemente werden zueinander sortiert), und die verglichenen Schlüssel sind von den einander nicht mehr zu unterscheiden.

Die tatsächliche Reihenfolge der Elemente in der gesteuerten Sequenz hängt von der Hashfunktion, der Sortierfunktion und der aktuellen Größe der Hashtabelle ab, die im Containerobjekt gespeichert wird. Die aktuelle Größe der Hashtabelle kann nicht bestimmt werden. Deshalb kann die Reihenfolge der Elemente in der gesteuerten Sequenz im Allgemeinen nicht vorhergesagt werden. Das Einfügen von Elementen führt nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen von Elementen werden nur solche Iteratoren ungültig, die speziell auf die entfernten Elemente gezeigt haben.

Der von einer hash_multimap-Klasse bereitgestellte Iterator ist ein bidirektionaler Iterator. Die Klassenmemberfunktionen [insert](#insert) und [hash_multimap](#hash_multimap) weisen allerdings Versionen auf, die einen abgeschwächten Eingabeiterator als Vorlagenparameter akzeptieren, dessen Funktionalitätsanforderungen weniger umfangreich sind, als die von der Klasse bidirektionaler Iteratoren garantierten. Die verschiedenen Iteratorkonzepte bilden eine Family, die durch Verfeinerungen in ihrer Funktionen verknüpft ist. Jedes Iteratorkonzept weist einen eigenes hash_multimap-Element von Anforderungen auf, und die damit funktionierenden Algorithmen müssen die Annahmen hinsichtlich der von diesem Iteratortyp bereitgestellten Anforderungen begrenzen. Es kann davon ausgegangen werden, dass ein Eingabeiterator möglicherweise so dereferenziert wird, dass er auf ein Objekt verweist und dieses möglicherweise zum folgenden Iterator in der Sequenz erhöht. Das ist eine minimaler hash_multimap-Funktion, allerdings genügt sie, um sinnvoll über einen Bereich von `[First, Last)`-Iteratoren im Kontext der Klassenmemberfunktionen zu sprechen.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[hash_multimap](#hash_multimap)|Erstellt eine Liste einer bestimmten Größe bzw. mit Elementen eines bestimmten Werts oder mit einem bestimmten `allocator`-Element oder als vollständige bzw. teilweise Kopie eines anderen `hash_multimap`-Elements.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[allocator_type](#allocator_type)|Ein Typ, der die `allocator`-Klassentyp für das `hash_multimap`-Objekt darstellt.|
|[const_iterator](#const_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein-Element im gelesen werden kann **`const`** `hash_multimap` .|
|[const_pointer](#const_pointer)|Ein Typ, der einen Zeiger auf ein- **`const`** Element in einem bereitstellt `hash_multimap` .|
|[const_reference](#const_reference)|Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einem `hash_multimap` zum Lesen und Ausführen von **`const`** Vorgängen gespeichert ist|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes beliebige-Element gelesen werden kann **`const`** `hash_multimap` .|
|[difference_type](#difference_type)|Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen eines `hash_multimap`-Elements in einen Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.|
|[Iterator](#iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einer `hash_multimap` gelesen oder geändert werden kann.|
|[key_compare](#key_compare)|Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen im `hash_multimap`-Element zu bestimmen.|
|[key_type](#key_type)|Ein Typ, mit dem das Sortierschlüsselobjekt beschrieben wird, das jedes Element von `hash_multimap` bildet.|
|[mapped_type](#mapped_type)|Ein Typ, der den in einer `hash_multimap` gespeicherten Datentyp darstellt.|
|[Zeichner](#pointer)|Ein Typ, der einen Zeiger auf ein Element in einer `hash_multimap` bereitstellt.|
|[Referenz](#reference)|Ein Typ, der einen Verweis auf ein in einer `hash_multimap` gespeichertes Element bereitstellt.|
|[reverse_iterator](#reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einem umgekehrten `hash_multimap`-Element gelesen oder geändert werden kann.|
|[size_type](#size_type)|Eine Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in `hash_multimap` darstellen kann.|
|[value_type](#value_type)|Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Elemente als Sortierschlüssel vergleichen kann, um die relative Position im `hash_multimap`-Element zu bestimmen.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[beginnen](#begin)|Gibt ein Iterator zurück, der das erste Element im `hash_multimap`-Element adressiert.|
|[cbegin](#cbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im `hash_multimap`-Element adressiert.|
|[cend](#cend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines `hash_multimap`-Elements nachfolgt.|
|[Löschen](#clear)|Löscht alle Elemente einer `hash_multimap` auf.|
|[count](#count)|Gibt die Anzahl von Elementen in einem `hash_multimap`-Element zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.|
|[crbegin](#crbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im umgekehrten `hash_multimap`-Element adressiert.|
|[crend](#crend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten `hash_multimap`-Elements nachfolgt.|
|[emplace](#emplace)|Fügt ein Element ein, das vor Ort in ein `hash_multimap`-Element erstellt wird.|
|[emplace_hint](#emplace_hint)|Fügt ein Element ein, das vor Ort mit einem Platzierungshinweis in ein `hash_multimap`-Element erstellt wird.|
|[empty](#empty)|Testet, ob ein `hash_multimap`-Element leer ist.|
|[end](#end)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element einem `hash_multimap`-Element nachfolgt.|
|[equal_range](#equal_range)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element einem `hash_multimap`-Element nachfolgt.|
|[erase](#erase)|Entfernt ein Element oder eine Reihe von Elementen in einer `hash_multimap` aus angegebenen Speicherorten.|
|[find](#find)|Gibt einen Iterator zurück, der die Position eines Elements in einem `hash_multimap`-Element adressiert, das einen Schlüssel aufweist, der einen angegebenen Schlüssel entspricht.|
|[get_allocator](#get_allocator)|Gibt eine Kopie des zum Erstellen von `allocator` verwendeten `hash_multimap`-Objekts zurück.|
|[insert](#insert)|Fügt ein Element oder einen Elementbereich an einer angegebenen Position in das `hash_multimap`-Element ein.|
|[key_comp](#key_comp)|Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in `hash_multimap` verwendet wird.|
|[lower_bound](#lower_bound)|Gibt einen Iterator zum ersten Element in einem `hash_multimap`-Element mit einem Schlüsselwert zurück, der gleich oder größer ist, als ein angegebener Schlüssel.|
|[max_size](#max_size)|Gibt die Maximallänge der `hash_multimap` zurück.|
|[rbegin](#rbegin)|Gibt einen Iterator zurück, der das erste Element in einem umgekehrten `hash_multimap`-Element adressiert.|
|[rend](#rend)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten `hash_multimap`-Elements nachfolgt.|
|[size](#size)|Gibt eine neue Größe für eine `hash_multimap` an.|
|[swap](#swap)|Tauscht die Elemente zweier `hash_multimap`n.|
|[upper_bound](#upper_bound)|Gibt einen Iterator zum ersten Element in einem `hash_multimap`-Element mit einem Schlüsselwert zurück, der größer ist, als ein angegebener Schlüssel.|
|[value_comp](#value_comp)|Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Elementwerte in `hash_multimap` verwendet wird.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[hash_multimap::operator=](#op_eq)|Ersetzt die Elemente eines `hash_multimap`-Elements durch eine Kopie eines anderen `hash_multimap`-Elements.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<hash_map>

**Namespace:** stdext

## <a name="hash_multimapallocator_type"></a><a name="allocator_type"></a> hash_multimap:: allocator_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der die Zuweisungsklasse für das hash_multimap-Objekt darstellt.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Bemerkungen

`allocator_type` ist ein Synonym für den Vorlagenparameter `Allocator`.

Weitere Informationen zu `Allocator` finden Sie im Abschnitt „Hinweise“ des Themas [hash_multimap-Klasse](../standard-library/hash-multimap-class.md).

### <a name="example"></a>Beispiel

In dem Beispiel für [get_allocator](#get_allocator) finden Sie ein Beispiel, das `allocator_type` verwendet.

## <a name="hash_multimapbegin"></a><a name="begin"></a> hash_multimap:: begin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen Iterator zurück, der das erste Element im hash_multimap-Element adressiert.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der das erste Element in der hash_multimap adressiert oder auf den Speicherort hinweist, der auf eine leere hash_multimap folgt.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `begin` einem zugewiesen wird `const_iterator` , können die Elemente im Hash_multimap Objekt nicht geändert werden. Wenn der Rückgabewert von `begin` einem zugewiesen wird `iterator` , können die Elemente im Hash_multimap Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is " << hm1_cIter -> first
        << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now " << hm1_cIter -> first
        << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="hash_multimapcbegin"></a><a name="cbegin"></a> hash_multimap:: cbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen const-Iterator zurück, der das erste Element in der hash_multimap adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const-Iterator, der das erste Element in der [hash_multimap](../standard-library/hash-multimap-class.md) adressiert oder auf den Speicherort hinweist, der auf eine leere `hash_multimap` folgt.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_cbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.cbegin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;
   }
```

```Output
The first element of hm1 is 2.
```

## <a name="hash_multimapcend"></a><a name="cend"></a> hash_multimap:: cend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der auf das letzte Element einer hash_multimap folgt.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const-Iterator, der den Speicherort adressiert, der auf das letzte Element einer [hash_multimap](../standard-library/hash-multimap-class.md) folgt. Wenn `hash_multimap` leer ist, gilt anschließend `hash_multimap::cend == hash_multimap::begin`.

### <a name="remarks"></a>Bemerkungen

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seiner hash_multimap erreicht hat.

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_cend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.cend( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;
   }
```

```Output
The value of last element of hm1 is 30.
```

## <a name="hash_multimapclear"></a><a name="clear"></a> hash_multimap:: Clear

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Löscht alle Elemente einer hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der hash_multimap::clear-Memberfunktion gezeigt.

```cpp
// hash_multimap_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_multimap is initially "
         << i  << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_multimap after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_multimap is initially 2.
The size of the hash_multimap after clearing is 0.
```

## <a name="hash_multimapconst_iterator"></a><a name="const_iterator"></a> hash_multimap:: const_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, **`const`** mit dem ein-Element im Hash_multimap gelesen werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_iterator`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

Der `const_iterator` , der durch Hash_multimap definiert wird, zeigt auf Objekte [value_type](#value_type)vom Typ `pair<const Key, Type>` . Der Wert des Schlüssels ist durch das erste Memberpaar verfügbar, und der Wert des zugeordneten Elements ist durch das zweite Memberpaar verfügbar.

Um einen zu dereferenzieren, `const_iterator` `cIter` der auf ein Element in einem Hash_multimap zeigt, verwenden Sie den- `->` Operator.

Um auf den Wert des Schlüssels für das Element zuzugreifen, verwenden Sie `cIter->first` , das entspricht `(*cIter).first` . Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `cIter->second` , das entspricht `(*cIter).second` .

### <a name="example"></a>Beispiel

Im Beispiel für [begin](#begin) finden Sie ein Beispiel mit `const_iterator`.

## <a name="hash_multimapconst_pointer"></a><a name="const_pointer"></a> hash_multimap:: const_pointer

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der einen Zeiger auf ein- **`const`** Element in einem Hash_multimap bereitstellt.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_pointer`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem hash_multimap-Objekt verwendet werden.

## <a name="hash_multimapconst_reference"></a><a name="const_reference"></a> hash_multimap:: const_reference

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einem Hash_multimap zum Lesen und Ausführen von **`const`** Vorgängen gespeichert ist.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin() -> second );

   cout << "The data value of 1st element in the hash_multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of 1st element in the hash_multimap is 10.
```

## <a name="hash_multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> hash_multimap:: const_reverse_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes **`const`** Element in der Hash_multimap gelesen werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reverse_iterator`-Typ kann nicht den Wert eines Elements ändern und wird verwendet, um die hash_multimap in umgekehrter Reihenfolge zu durchlaufen.

Der `const_reverse_iterator` , der durch Hash_multimap definiert wird, zeigt auf Objekte [value_type](#value_type)vom Typ `pair<const Key, Type>` , deren erster Member der Schlüssel zum Element und dessen zweiter Member das zugeordnete Datum ist, das vom Element gehalten wird.

Um einen zu dereferenzieren, `const_reverse_iterator` `crIter` der auf ein Element in einem Hash_multimap zeigt, verwenden Sie den- `->` Operator.

Um auf den Wert des Schlüssels für das Element zuzugreifen, verwenden Sie `crIter->first` , das entspricht `(*crIter).first` . Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `crIter->second` , das entspricht `(*crIter).second` .

### <a name="example"></a>Beispiel

Im Beispiel für [rend](#rend) wird verdeutlicht, wie ein `const_reverse_iterator` deklariert und verwendet wird.

## <a name="hash_multimapcount"></a><a name="count"></a> hash_multimap:: count

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt die Anzahl von Elementen in einer hash_multimap-Klasse zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Schlüssel des Elements mit einem übereinstimmenden Schlüssel aus der hash_multimap-Klasse.

### <a name="return-value"></a>Rückgabewert

1, wenn die hash_multimap-Klasse ein Element enthält, dessen Sortierungsschlüssel dem Parameterschlüssel entspricht; 0, wenn die hash_multimap-Klasse kein Element mit einem übereinstimmenden Schlüssel enthält.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Anzahl der Elemente im Bereich zurück.

**[lower_bound (** `key` **), upper_bound (** `key` **) )**

mit einem Schlüsselwert *Schlüssel*.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion „hash_multimap::count“ gezeigt.

```cpp
// hash_multimap_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 1));
    hm1.insert(Int_Pair(1, 4));
    hm1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in hash_multimap,
    // so duplicates are allowed and counted
    i = hm1.count(1);
    cout << "The number of elements in hm1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hm1.count(2);
    cout << "The number of elements in hm1 with a sort key of 2 is: "
         << i << "." << endl;

    i = hm1.count(3);
    cout << "The number of elements in hm1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hm1 with a sort key of 1 is: 2.
The number of elements in hm1 with a sort key of 2 is: 2.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="hash_multimapcrbegin"></a><a name="crbegin"></a> hash_multimap:: crbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen const-Iterator zurück, der das erste Element in einer umgekehrten hash_multimap adressiert.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler const-Iterator, mit dem das erste Element in einer umgekehrten [hash_multimap](../standard-library/hash-multimap-class.md) adressiert wird (bzw. mit dem das ehemals letzte Element in der nicht umgekehrten `hash_multimap` adressiert wird).

### <a name="remarks"></a>Bemerkungen

`crbegin` wird bei einer umgekehrten hash_multimap auf die gleiche Weise verwendet wie [hash_multimap::begin](#begin) mit einer `hash_multimap`.

Bei dem Rückgabewert von `crbegin` kann das `hash_multimap`-Objekt nicht geändert werden.

Mit `crbegin` lässt sich eine `hash_multimap` rückwärts durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_crbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
```

## <a name="hash_multimapcrend"></a><a name="crend"></a> hash_multimap:: crend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der auf das letzte Element einer umgekehrten hash_multimap folgt.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const_reverse-Iterator, der den Standort anspricht, der dem letzten Element in einer umgekehrten [hash_multimap](../standard-library/hash-multimap-class.md) nachfolgt (der Speicherort, der dem ersten Element in der nicht umgekehrten `hash_multimap` vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einer umgekehrten hash_multimap auf die gleiche Weise verwendet wie [hash_multimap::end](#end) mit einer hash_multimap.

Bei dem Rückgabewert von `crend` kann das `hash_multimap`-Objekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob ein umgekehrter Iterator das Ende seiner hash_multimap erreicht hat.

Der von `crend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_crend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 3.
```

## <a name="hash_multimapdifference_type"></a><a name="difference_type"></a> hash_multimap::d ifference_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen einer hash_multimap in einem Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

`difference_type` ist der Typ, der beim Subtrahieren oder Inkrementieren über Iteratoren des Containers zurückgegeben wird. `difference_type` wird normalerweise verwendet, um die Anzahl von Elementen im Bereich *(first, last)* zwischen den Iteratoren `first` und `last` darzustellen. Dazu gehört das Element, auf das durch `first` gezeigt wird und der Bereich von Elementen bis zu (aber nicht einschließlich) dem Element, auf das durch `last` gezeigt wird.

Bitte beachten Sie, dass die Subtraktion zwischen Iteratoren nur von Iteratoren mit zufälligem Zugriff unterstützt wird, die über einen Container mit zufälligem Zugriff wie „vector“ bereitgestellt werden. Dies gilt, obwohl `difference_type` für alle Iteratoren verfügbar ist, die die Anforderungen eines Eingabeiterators erfüllen. Hierzu zählt auch die Klasse bidirektionaler Iteratoren, die von umkehrbaren Containern wie „set“ unterstützt wird.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_difference_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(3, 20));

    // The following will insert, because map keys
    // do not need to be unique
    hm1.insert(Int_Pair(2, 30));

    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
    hm1_bIter = hm1.begin();
    hm1_eIter = hm1.end();

    // Count the number of elements in a hash_multimap
    hash_multimap<int, int>::difference_type df_count = 0;
    hm1_Iter = hm1.begin();
    while (hm1_Iter != hm1_eIter)
    {
        df_count++;
        hm1_Iter++;
    }

    cout << "The number of elements in the hash_multimap hm1 is: "
         << df_count << "." << endl;

    cout << "The keys of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> first;
    cout << "." << endl;

    cout << "The values of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> second;
    cout << "." << endl;
}
```

```Output
The number of elements in the hash_multimap hm1 is: 4.
The keys of the mapped elements are: 1 2 2 3.
The values of the mapped elements are: 10 20 30 20.
```

## <a name="hash_multimapemplace"></a><a name="emplace"></a> hash_multimap:: emplace

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Fügt ein Element, das vor Ort erstellt wird, in einer hash_multimap ein.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Der Wert, der verwendet wird, um das einzufügende Element per Verschiebung in die [hash_multimap](../standard-library/hash-multimap-class.md) zu erstellen.

### <a name="return-value"></a>Rückgabewert

Die `emplace`-Memberfunktion gibt einen Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Der [hash_multimap::value_type](#value_type) eines Elements wird paarweise angegeben, sodass der Wert eines Elements ein geordnetes Paar ist, bei dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_emplace.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
    cout << "After the emplace, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_multimapemplace_hint"></a><a name="emplace_hint"></a> hash_multimap:: emplace_hint

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Fügt ein Element ein, das vor Ort mit einem Platzierungshinweis in einer hash_multimap erstellt wird.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parameter

*ster*\
Der Wert verwendet normalerweise ein Bewegungskonstrukt, um ein Element in eine [hash_multimap](../standard-library/hash-multimap-class.md) einzufügen, außer `hash_multimap` hat bereits das Element (oder, allgemeiner gesagt, ein Element, dessen Schlüssel gleichwertig sortiert wird).

*_Where*\
Ein Hinweis bezüglich des Platzes, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird.

### <a name="return-value"></a>Rückgabewert

Die [hash_multimap::emplace](#emplace)-Memberfunktion gibt einen Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element in `hash_multimap` eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Der [hash_multimap::value_type](#value_type) eines Elements wird paarweise angegeben, sodass der Wert eines Elements ein geordnetes Paar ist, bei dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

Die Einfügung kann in amortisierter konstanter Zeit anstelle von logarithmischer Zeit erfolgen, wenn die Einfügemarke direkt auf *_Where*folgt.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_emplace_hint.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
    cout << "After the emplace insertion, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_multimapempty"></a><a name="empty"></a> hash_multimap:: Empty

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Testet, ob ein hash_multimap-Element leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn das Hash_multimap leer ist. , **`false`** Wenn der Hash_multimap nicht leer ist.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_multimap hm1 is empty." << endl;
   else
      cout << "The hash_multimap hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_multimap hm2 is empty." << endl;
   else
      cout << "The hash_multimap hm2 is not empty." << endl;
}
```

```Output
The hash_multimap hm1 is not empty.
The hash_multimap hm2 is empty.
```

## <a name="hash_multimapend"></a><a name="end"></a> hash_multimap:: End

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen Iterator zurück, der den Speicherort adressiert, der auf das letzte Element einer hash_multimap folgt.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der den Speicherort adressiert, der auf das letzte Element einer hash_multimap folgt. Ist die hash_multimap leer, folgt anschließend „hash_multimap::end == hash_multimap::begin“.

### <a name="remarks"></a>Bemerkungen

`end` wird verwendet, um zu testen, ob ein Iterator das Ende seiner hash_multimap erreicht hat.

Der von `end` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;

   hm1_Iter = hm1.end( );
   hm1_Iter--;
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.end ( );
   // hm1_cIter--;
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is now "
        << hm1_cIter -> second << "." << endl;
}
```

```Output
The value of last element of hm1 is 30.
The value of last element of hm1 is now 20.
```

## <a name="hash_multimapequal_range"></a><a name="equal_range"></a> hash_multimap:: equal_range

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt ein Iteratorpaar jeweils zum ersten Element in einer hash_multimap mit einem Schlüssel zurück, der größer als ein bestimmter Schlüssel ist, bzw. zum ersten Element in einer hash_multimap mit einem Schlüssel, der größer oder gleich dem Schlüssel ist.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden hash_multimap verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein Iteratorenpaar, bei dem der erste Iterator der [lower_bound](#lower_bound) des Schlüssels und der zweite Iterator der [upper_bound](#upper_bound) des Schlüssels ist.

Sie können auf den ersten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **first** verwenden Sie zum Aufheben der Dereferenzierung des unteren gebundenen Iterators \* ( `pr` . **zuerst**). Sie können auf den zweiten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **second** verwenden Sie zum Aufheben der Dereferenzierung des oberen gebundenen Iterators \* ( `pr` . **Sekunde**).

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multimap <int, int> IntMMap;
   IntMMap hm1;
   hash_multimap <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2
in the hash_multimap hm1 is: 20.
The upper bound of the element with a key of 2
in the hash_multimap hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_multimap hm1 doesn't have an element with a key less than 4.
```

## <a name="hash_multimaperase"></a><a name="erase"></a> hash_multimap:: Erase

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Es wird ein Element oder ein Bereich von Elementen in einer hash_multimap von angegebenen Speicherorten entfernt oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parameter

*_Where*\
Die Position des aus der hash_multimap zu entfernenden Elements.

*erstes*\
Die Position des ersten Elements, das aus der hash_multimap entfernt werden soll.

*letzten*\
Die Position direkt hinter dem letzten aus der hash_multimap entfernten Element.

*wichtigen*\
Der Schlüssel des aus der hash_multimap zu entfernenden Elements.

### <a name="return-value"></a>Rückgabewert

Bei den ersten beiden Memberfunktionen ist es ein bidirektionaler Iterator, der das erste über die entfernten Elemente hinaus verbliebene Element festlegt, oder ein Zeiger auf das das Ende der hash_multimap, wenn kein solches Element vorhanden ist.

Für die dritte Memberfunktion wird die Anzahl der von der hash_multimap entfernten Elemente zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Von der Memberfunktionen wird nie eine Ausnahme ausgelöst.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion "hash_multimap::erase" gezeigt.

```cpp
// hash_multimap_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2, hm3;
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multimap<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i) );
        hm2.insert(Int_Pair (i, i*i) );
        hm3.insert(Int_Pair (i, i-1) );
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, "
         << "the hash_multimap hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_multimap hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    hm3.insert(Int_Pair (2, 5));
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that of the"
         << endl;
    cout  << "2nd element is deleted, "
          << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_multimap hm3 is: 0 2 3.
The number of elements removed from hm3 is: 2.
After another element with a key equal to that of the
2nd element is deleted, the hash_multimap hm3 is: 0 3.
```

## <a name="hash_multimapfind"></a><a name="find"></a> hash_multimap:: Find

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen Iterator zurück, der die erste Position eines Elements in einer hash_multimap adressiert, das einen Schlüssel aufweist, der einem angegebenen Schlüssel entspricht.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Schlüssel, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden hash_multimap übereinstimmt.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der den ersten Speicherort eines Elements mit einem angegebenen Schlüssel adressiert, oder der Speicherort, der dem letzten Element in der hash_multimap nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Iterator zurück, der ein Element in der Hash_multimap adressiert, dessen Sortierschlüssel `equivalent` dem Argument Schlüssel unter einem binären Prädikat entspricht, das eine Sortierung basierend auf einer kleiner-als-Kompatibilitäts Beziehung auslöst.

Wenn der Rückgabewert `find` einem `const_iterator` zugewiesen wird, kann das hash_multimap-Objekt nicht geändert werden. Wenn der Rückgabewert von `find` einem zugewiesen wird `iterator` , kann das Hash_multimap Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_find.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 20));
    hm1.insert(Int_Pair(3, 30));

    hm1_RcIter = hm1.find(2);
    cout << "The element of hash_multimap hm1 with a key of 2 is: "
          << hm1_RcIter -> second << "." << endl;

    hm1_RcIter = hm1.find(3);
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "
          << hm1_RcIter -> second << "." << endl;

    // If no match is found for the key, end() is returned
    hm1_RcIter = hm1.find(4);

    if (hm1_RcIter == hm1.end())
        cout << "The hash_multimap hm1 doesn't have an element "
             << "with a key of 4." << endl;
    else
        cout << "The element of hash_multimap hm1 with a key of 4 is: "
             << hm1_RcIter -> second << "." << endl;

    // The element at a specific location in the hash_multimap can be
    // found using a dereferenced iterator addressing the location
    hm1_AcIter = hm1.end();
    hm1_AcIter--;
    hm1_RcIter = hm1.find(hm1_AcIter -> first);
    cout << "The first element of hm1 with a key matching"
         << endl << "that of the last element is: "
         << hm1_RcIter -> second << "." << endl;

    // Note that the first element with a key equal to
    // the key of the last element is not the last element
    if (hm1_RcIter == --hm1.end())
        cout << "This is the last element of hash_multimap hm1."
             << endl;
    else
        cout << "This is not the last element of hash_multimap hm1."
             << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="hash_multimapget_allocator"></a><a name="get_allocator"></a> hash_multimap:: Get_allocator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt eine Kopie des Zuweisungsobjekts zurück, das zum Erstellen der hash_multimap verwendet wird.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Die von der hash_multimap verwendete Zuweisung.

### <a name="remarks"></a>Bemerkungen

Zuweisungen für die hash_multimap-Klasse geben an, wie die Klasse einen Speicher verwaltet. Für die meisten Programmieranforderungen reichen die Standard-Zuweisungen aus C++-Standardbibliothek-Containerklassen aus. Schreiben und Verwenden Ihrer eigener Zuweisungsklasse ist ein C++ -Thema für Fortgeschrittene.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int>::allocator_type hm1_Alloc;
   hash_multimap <int, int>::allocator_type hm2_Alloc;
   hash_multimap <int, double>::allocator_type hm3_Alloc;
   hash_multimap <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> hm2;
   hash_multimap <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_multimap hm4
   // with the allocator of hash_multimap hm1.
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hm1_Alloc == hm4_Alloc )
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

## <a name="hash_multimaphash_multimap"></a><a name="hash_multimap"></a> hash_multimap:: Hash_multimap

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Erstellt ein hash_multimap-Element, das leer oder eine Kopie eines anderen vollständigen hash_multimap-Elements oder eines Teils davon ist.

```cpp
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parameter

*Irdische*\
Die für dieses hash_multimap-Objekt zu verwendende Speicherreservierungsklasse, dessen Standard `Allocator` ist.

*Zuschreiben*\
Die Vergleichsfunktion vom Typ `const Traits`, die verwendet wird, um die Elemente in der Zuordnung zu sortieren, deren Standard `Traits` ist.

*Richting*\
Die Zuordnung, deren Kopie der erstellte Satz sein soll.

*Erstes*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*Letzten*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*IList*\
Das initializer_list-Element, aus dem kopiert wird.

### <a name="remarks"></a>Bemerkungen

In allen Konstruktoren wird ein Zuweisungsobjekttyp gespeichert, mit dem der Arbeitsspeicher für das hash_multimap-Element verwaltet wird, und das später zurückgegeben werden kann, indem [get_allocator](#get_allocator) aufgerufen wird. Der Zuweisungsparameter wird häufig aus den Klassendeklarationen und den Vorverarbeitungsmakros weggelassen, die zum Ersetzen alternativer Zuweisungen verwendet werden.

Alle Konstruktoren initialisieren ihrer hash_multimap-Elemente.

In allen Konstruktoren wird ein Funktionsobjekt vom Typ `Traits` gespeichert, der verwendet wird, um unter den Schlüsseln des hash_multimap-Elements eine Sortierung vorzunehmen, und das später zurückgegeben werden kann, indem [key_comp](#key_comp) aufgerufen wird.

Die ersten drei Konstruktoren geben eine leere anfängliche Hash_multimap an. der zweite gibt den Typ der Vergleichsfunktion (*Comp*) an, die zum Festlegen der Reihenfolge der Elemente verwendet werden soll, und der dritte gibt explizit den zu verwendenden zuordnertyp ( `_Al` ) an. Mit dem-Schlüsselwort werden **`explicit`** bestimmte Arten automatischer Typkonvertierungen unterdrückt.

Der vierte Konstruktor gibt eine Kopie des `Right`-hash_multimap-Elements an.

Mit den nächsten drei Konstruktoren wird der `First, Last)`-Bereich, einer Zuordnung kopiert, wobei sich die Explizitheit bei Angabe des Typs der Vergleichsfunktion der Klasse `Traits` und "Allocator" erhöht.

Der achte Konstruktor verschiebt das hash_multimap-Element `Right`.

Die letzten drei Konstruktoren verwenden ein initializer_list-Element.

## <a name="hash_multimapinsert"></a><a name="insert"></a> hash_multimap:: INSERT

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Fügt ein Element oder einen Elementbereich in ein hash_multimap-Element ein.

```cpp
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>Parameter

*Ster*\
Der Wert eines in das hash_multimap-Element einzufügenden Elements, es sei denn, das Element ist bereits enthalten oder, üblicher, es sei denn, ein Element, dessen Schlüssel gleichwertig sortiert wird, ist bereits enthalten.

*Was*\
Ein Hinweis darüber, wo mit der Suche nach den richtigen Einfügepunkt begonnen wird.

*Erstes*\
Die Position des ersten Elements, das aus einer Zuordnung kopiert werden soll.

*Letzten*\
Die Position direkt über den letzten aus einer Zuordnung zu kopierenden Elements.

### <a name="return-value"></a>Rückgabewert

Die ersten zwei `insert` -Memberfunktionen geben ein Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element eingefügt wurde.

Die dritte Memberfunktion verwendet ein initializer_list-Element, damit die Elemente eingefügt werden können.

Die vierte Memberfunktion fügt die Sequenz von Elementwerten in eine Zuordnung ein, die jedem Element entspricht, das von einem Iterator im `[First, Last)` -Bereich einer bestimmten Gruppe adressiert wird.

Die letzten zwei `insert` -Memberfunktionen verhalten sich identisch zu den ersten beiden, außer dass der eingefügte Wert durch Verschiebung erstellt wird.

### <a name="remarks"></a>Bemerkungen

Der [value_type](#value_type) eines Elements wird paarweise angegeben, sodass der Wert eines Elements ein sortiertes Paar ist, in dem die erste Komponente gleich dem Schlüsselwert und die zweite Komponente gleich dem Datenwert des Elements ist.

Die Einfügung kann in amortisierter konstanter Zeit für die Hinweis Version von `insert` statt logarithmischer Zeit erfolgen, wenn die Einfügemarke direkt auf *Where*folgt.

## <a name="hash_multimapiterator"></a><a name="iterator"></a> hash_multimap:: Iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einer hash_multimap gelesen oder geändert werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Bemerkungen

Der `iterator` , der durch Hash_multimap definiert wird, zeigt auf Objekte [value_type](#value_type)vom Typ `pair` \< **const Key, Type**> , deren erster Member der Schlüssel zum Element und dessen zweiter Member das zugeordnete Datum ist, das vom Element gehalten wird.

Um einen Iterator mit dem Namen zu dereferenzieren, `Iter` der auf ein Element in einem Hash_multimap verweist, verwenden Sie den- `->` Operator.

Um auf den Wert des Schlüssels für das Element zuzugreifen, verwenden Sie `Iter->first` , das entspricht `(*Iter).first` . Um auf den Wert des zugeordneten Datums für das Element zuzugreifen, verwenden Sie `Iter->second` , das entspricht `(*Iter).first` .

Ein-Typ `iterator` kann zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

Im Beispiel für [begin](#begin) wird verdeutlicht, wie ein `iterator` deklariert und verwendet wird.

## <a name="hash_multimapkey_comp"></a><a name="key_comp"></a> hash_multimap:: key_comp

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in einer hash_multimap verwendet wird.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Funktionsobjekt zurück, das ein hash_multimap-Element zum Sortieren seiner Elemente verwendet.

### <a name="remarks"></a>Bemerkungen

Das gespeicherte Objekt definiert die Memberfunktion

`bool operator( const Key& left, const Key& right );`

, der zurückgibt, **`true`** Wenn `left` vorausgeht und `right` in der Sortierreihenfolge nicht gleich ist.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::key_compare kc1 = hm1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }

   hash_multimap <int, int, hash_compare<int, greater<int>>> hm2;
   hash_multimap <int, int, hash_compare<int, greater<int>>
      >::key_compare kc2 = hm2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
}
```

## <a name="hash_multimapkey_compare"></a><a name="key_compare"></a> hash_multimap:: key_compare

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen in der multi_map zu bestimmen.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Bemerkungen

`key_compare` ist ein Synonym für die Vorlagen Parameter *Merkmale*.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [Hash_multimap-Klasse](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Beispiel

Im Beispiel für [key_comp](#key_comp) wird verdeutlicht, wie ein `key_compare` deklariert und verwendet wird.

## <a name="hash_multimapkey_type"></a><a name="key_type"></a> hash_multimap:: key_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, mit dem das Sortierschlüsselobjekt beschrieben wird, das jedes Element der hash_multimap bildet.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

`key_type` ist ein Synonym für den Vorlagen Parameter *Schlüssel*.

Weitere Informationen zu *Key*finden Sie im Abschnitt "Hinweise" des Themas [Hash_multimap-Klasse](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie `key_compare` deklariert und verwendet wird.

## <a name="hash_multimaplower_bound"></a><a name="lower_bound"></a> hash_multimap:: lower_bound

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen Iterator zum ersten Element in einer hash_multimap mit einem Schlüssel zurück, der gleich oder größer als ein angegebener Schlüssel ist.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden hash_multimap verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein [Iterator](#iterator) oder [const_iterator](#const_iterator), der den Speicherort eines Elements in einer hash_multimap mit einem Schlüssel adressiert, der gleich oder größer als der Argumentschlüssel ist, oder der den Speicherort des nachfolgenden letzten Elements in der hash_multimap adressiert, wenn kein Treffer für den Schlüssel gefunden wird.

Wenn der Rückgabewert `lower_bound` einem `const_iterator` zugewiesen wird, kann das hash_multimap-Objekt nicht geändert werden. Wenn der Rückgabewert von `lower_bound` einem zugewiesen wird `iterator` , kann das Hash_multimap Objekt geändert werden.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter,
      hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The element of hash_multimap hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.lower_bound( 3 );
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key matching"
        << endl << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( hm1_RcIter == --hm1.end( ) )
      cout << "This is the last element of hash_multimap hm1."
           << endl;
   else
      cout << "This is not the last element of hash_multimap hm1."
           << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="hash_multimapmapped_type"></a><a name="mapped_type"></a> hash_multimap:: mapped_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der den in einer hash_multimap gespeicherten Datentyp darstellt.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Bemerkungen

`mapped_type` ist ein Synonym für den Vorlagenparameter *type*.

Weitere Informationen zum *Typ* finden Sie im Thema [Hash_multimap-Klasse](../standard-library/hash-multimap-class.md) .

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie `key_type` deklariert und verwendet wird.

## <a name="hash_multimapmax_size"></a><a name="max_size"></a> hash_multimap:: max_size

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt die Maximallänge der hash_multimap zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die mögliche Maximallänge der hash_multimap.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multimap is " << i << "." << endl;
}
```

## <a name="hash_multimapoperator"></a><a name="op_eq"></a> hash_multimap:: Operator =

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ersetzt die Elemente der hash_multimap durch eine Kopie einer anderen.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die [hash_multimap](../standard-library/hash-multimap-class.md), die in die `hash_multimap` kopiert wird.

### <a name="remarks"></a>Bemerkungen

Nachdem ein vorhandenes Element in einem gelöscht `hash_multimap` wurde, `operator=` kopiert oder verschiebt den Inhalt von *direkt* in den `hash_multimap` .

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_operator_as.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> v1, v2, v3;
   hash_multimap<int, int>::iterator iter;

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

## <a name="hash_multimappointer"></a><a name="pointer"></a> hash_multimap::p

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der einen Zeiger auf ein Element in einer hash_multimap bereitstellt.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein-Typ `pointer` kann zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem hash_multimap-Objekt verwendet werden.

## <a name="hash_multimaprbegin"></a><a name="rbegin"></a> hash_multimap:: rbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen Iterator zurück, der das erste Element in einer umgekehrten hash_multimap adressiert.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, mit dem das erste Element in einer umgekehrten hash_multimap adressiert wird, bzw. mit dem das ehemals letzte Element in der nicht umgekehrten hash_multimap adressiert wird.

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einer umgekehrten hash_multimap auf die gleiche Weise verwendet wie [begin](#begin) mit einer hash_multimap.

Wenn der Rückgabewert `rbegin` einem `const_reverse_iterator` zugewiesen wird, kann das hash_multimap-Objekt anschließend nicht geändert werden. Wenn der Rückgabewert `rbegin` einem `reverse_iterator` zugewiesen wird, kann das hash_multimap-Objekt anschließend geändert werden.

`rbegin` kann verwendet werden, um eine hash_multimap rückwärts zu durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element\n"
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the first element
in the reversed hash_multimap is 2.
```

## <a name="hash_multimapreference"></a><a name="reference"></a> hash_multimap:: Reference

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der einen Verweis auf einer hash_multimap gespeichertes Element bereitstellt.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_multimap is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The modified data value of first element is 15.
```

## <a name="hash_multimaprend"></a><a name="rend"></a> hash_multimap:: rend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen Iterator zurück, der den Speicherort adressiert, der auf das letzte Element einer umgekehrten hash_multimap folgt.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der den Standort anspricht, der auf das letzte Element in einer umgekehrten hash_multimap folgt (der Speicherort, der dem ersten Element in der nicht umgekehrten hash_multimap vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einer umgekehrten hash_multimap auf die gleiche Weise verwendet wie [end](#end) mit einer hash_multimap.

Wenn der Rückgabewert von `rend` einem [const_reverse_iterator](#const_reverse_iterator) zugewiesen wird, kann das hash_multimap-Objekt anschließend nicht geändert werden. Wenn der Rückgabewert von `rend` einem [reverse_iterator](#reverse_iterator) zugewiesen wird, kann das hash_multimap-Objekt anschließend geändert werden.

`rend` kann verwendet werden, um zu testen, ob ein umgekehrter Iterator das Ende seiner hash_multimap erreicht hat.

Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 1.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the last element in the reversed hash_multimap is 2.
```

## <a name="hash_multimapreverse_iterator"></a><a name="reverse_iterator"></a> hash_multimap:: reverse_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einer umgekehrten hash_multimap gelesen oder geändert werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `reverse_iterator`-Typ wird verwendet, um die multi_map in umgekehrter Reihenfolge zu durchlaufen.

Der `reverse_iterator` , der durch Hash_multimap definiert wird, zeigt auf Objekte [value_type](#value_type)vom Typ `pair` \< **const Key, Type**> . Der Wert des Schlüssels ist durch das erste Memberpaar verfügbar, und der Wert des zugeordneten Elements durch das zweite Memberpaar.

### <a name="example"></a>Beispiel

Im Beispiel für [rbegin](#rbegin) wird verdeutlicht, wie ein `reverse_iterator` deklariert und verwendet wird.

## <a name="hash_multimapsize"></a><a name="size"></a> hash_multimap:: size

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt die Anzahl von Elementen in hash_multimap zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge von hash_multimap.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion „hash_multimap::size“ gezeigt.

```cpp
// hash_multimap_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_multimap length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_multimap length is now " << i << "." << endl;
}
```

```Output
The hash_multimap length is 1.
The hash_multimap length is now 2.
```

## <a name="hash_multimapsize_type"></a><a name="size_type"></a> hash_multimap:: size_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einer hash_multimap zählt.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im Beispiel für [size](#size) wird verdeutlicht, wie ein `size_type` deklariert und verwendet wird.

## <a name="hash_multimapswap"></a><a name="swap"></a> hash_multimap:: Swap

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Tauscht die Elemente zweier hash_multimaps aus.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die hash_multimap, in der die auszutauschenden Elemente bereitgestellt werden, oder die hash_multimap, deren Elemente mit denen der hash_multimap ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion macht keine Verweise, Zeiger oder Iteratoren ungültig, die Elemente in zwei hash_multimaps bezeichnen, deren Elemente ausgetauscht werden.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   hash_multimap <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_multimap hm1 is: 10 20 30.
After swapping with hm2, hash_multimap hm1 is: 100 200.
After swapping with hm3, hash_multimap hm1 is: 300.
```

## <a name="hash_multimapupper_bound"></a><a name="upper_bound"></a> hash_multimap:: upper_bound

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Gibt einen Iterator zum ersten Element in einer hash_multimap mit einem Schlüssel zurück, der größer als ein angegebener Schlüssel ist.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der zu durchsuchenden hash_multimap verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein [Iterator](#iterator) oder [const_iterator](#const_iterator), der den Speicherort eines Elements in einer hash_multimap mit einem Schlüssel adressiert, der größer als der Argumentschlüssel ist, oder der den Speicherort des nachfolgenden letzten Elements in der hash_multimap adressiert, wenn kein Treffer für den Schlüssel gefunden wird.

Wenn der Rückgabewert `upper_bound` einem `const_iterator` zugewiesen wird, kann das hash_multimap-Objekt nicht geändert werden. Wenn der Rückgabewert von `upper_bound` einem zugewiesen wird `iterator` , kann das Hash_multimap Objekt geändert werden.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm1.insert ( Int_Pair ( 3, 40 ) );

   hm1_RcIter = hm1.upper_bound( 1 );
   cout << "The 1st element of hash_multimap hm1 with "
        << "a key greater than 1 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_multimap hm1\n"
        << "with a key greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key greater than"
        << endl << "that of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.
The first element of hash_multimap hm1
with a key  greater than 2 is: 30.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key greater than
that of the initial element of hm1 is: 20.
```

## <a name="hash_multimapvalue_comp"></a><a name="value_comp"></a> hash_multimap:: value_comp

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Die Memberfunktion gibt ein Funktionsobjekt zurück, das die Reihenfolge der Elemente in einer hash_multimap bestimmt, indem ihre Schlüsselwerte verglichen werden.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Vergleichsfunktionsobjekt zurück, das ein hash_multimap-Element zum Sortieren seiner Elemente verwendet.

### <a name="remarks"></a>Bemerkungen

Wenn bei einer Hash_multimap *m*die zwei Elemente *E1* (*K1*, *D1*) und *E2*(*K2*, *D2*) Objekte vom Typ [value_type](#value_type)sind, wobei *K1* und *K2* Ihre Schlüssel vom Typ sind [key_type](#key_type) und *D1* und *D2* Ihre Daten vom Typ [mapped_type](#mapped_type)sind, `m.value_comp()(e1, e2)` entspricht `m.key_comp()(k1, k2)` . Ein gespeicherte Objekt definiert die Memberfunktion

`bool operator( value_type& left, value_type& right);`

, der zurückgibt, **`true`** Wenn der Schlüsselwert von `left` vor und nicht gleich dem Schlüsselwert von `right` in der Sortierreihenfolge ist.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::value_compare vc1 = hm1.value_comp( );
   hash_multimap <int,int>::iterator Iter1, Iter2;

   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="hash_multimapvalue_type"></a><a name="value_type"></a> hash_multimap:: value_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](../standard-library/unordered-multimap-class.md).

Ein Typ, der den Typ des Objekts angibt, das in einer hash_multimap gespeichert wird.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Bemerkungen

`value_type` wird als Paar \<const [key_type](#key_type), [mapped_type](#mapped_type)> und nicht paarweise deklariert, \<key_type, mapped_type> weil die Schlüssel eines assoziativen Containers nicht mit einem nicht konstanten Iterator oder Verweis geändert werden dürfen.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: key_type key1;
   hash_multimap <int, int> :: mapped_type mapped1;
   hash_multimap <int, int> :: value_type value1;
   hash_multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   hm1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
