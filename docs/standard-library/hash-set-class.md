---
title: hash_set-Klasse
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
ms.openlocfilehash: becf038678f4abbe285e719e4d1cc1f3f12de982
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865130"
---
# <a name="hash_set-class"></a>hash_set-Klasse

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Die hash_set-Containerklasse ist eine Erweiterung der Standardvorlagenbibliothek und wird für das Speichern und schnelle Abrufen von Daten aus einer Auflistung verwendet, in der die Werte der enthaltenen Elemente eindeutig sind und als Schlüsselwerte fungieren.

## <a name="syntax"></a>Syntax

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der im hash_set-Objekt zu speichernde Elementdatentyp.

*Merkmale*\
Der Typ, der zwei Funktions Objekte enthält, einer der Klassen Vergleiche, bei dem es sich um ein binäres Prädikat handelt, das zwei Element Werte als Sortierschlüssel vergleichen kann, um ihre relative Position zu bestimmen, und eine Hash Funktion, bei der es sich um eine Zuordnung von unären Prädikats für die Elemente ohne Vorzeichen vom Typ `size_t`handelt. Das Argument ist optional und `hash_compare<Key, less<Key> >` ist der Standardwert.

*Zuordner\*
Der Typ, mit dem das gespeicherte allocator-Objekt dargestellt wird, mit dem Details zum Belegen und Freigeben von Arbeitsspeicher für das hash_set-Element gekapselt werden. Dieses Argument ist optional, und der Standardwert ist `allocator<Key>`.

## <a name="remarks"></a>Bemerkungen

Ein hash_set-Objekt ist:

- Ein assoziativer Container, der ein Container variabler Größe ist, der den effizienten Abruf von Elementwerten auf Grundlage eines zugeordneten Schlüsselwert unterstützt. Darüber hinaus ist es ein einfacher assoziativer Container, da die Elementwerte den Schlüsselwerten entsprechen.

- Umkehrbar, da ein bidirektionaler Iterator für den Zugriff auf die Elemente bereitgestellt wird.

- Gehasht, da die Elemente auf Grundlage des Werts einer Hashfunktion, die auf die Schlüsselwerte der Elemente angewendet wird, in Buckets gruppiert werden.

- Insofern eindeutig, da jedes der Elemente einen eindeutigen Schlüssel aufweisen muss. Da ein hash_set-Objekt auch ein einfacher assoziativer Container ist, sind seine Elemente ebenfalls eindeutig.

- Eine Klassen Vorlage, da die von ihr bereitgestellte Funktionalität generisch und daher unabhängig vom jeweiligen Typ der Daten ist, die als Elemente oder Schlüssel enthalten sind. Die für Elemente und Schlüssel zu verwendenden Datentypen werden stattdessen in der Klassenvorlage zusammen mit der Vergleichsfunktion und der Zuweisung als Parameter angegeben.

Der Hauptvorteil des Hashverfahrens gegenüber der Sortierung ist die größere Effizienz. Bei einem erfolgreichen Hashverfahren werden Einfüge-, Lösch- und Suchvorgänge, verglichen mit einer Zeit, die zum Logarithmus der Anzahl von Elementen im Container für Sortiertechniken proportional ist, in einer konstanten Durchschnittszeit durchgeführt. Der Schlüsselwert eines Elements in einem Satz darf nicht direkt geändert werden. Stattdessen müssen Sie alte Werte löschen und Elemente mit neuen Werten einfügen.

Die Auswahl des Containertyps sollte im Allgemeinen auf Grundlage des für die Anwendung erforderlichen Suchen und Einfügetyps erfolgen. Gehashte assoziative Container sind für Such-, Einfüge- und Entfernvorgänge optimiert. Die Memberfunktionen, die diese Vorgänge explizit unterstützen, sind effizient, wenn sie mit einer gut entworfenen Hashfunktion verwendet werden. Dann werden sie in einer Zeit ausgeführt, die im Durchschnitt konstant und nicht von der Anzahl von Elementen im Container abhängig ist. Eine ausgereifte Hashfunktion erzeugt eine vereinheitlichte Verteilung gehashter Werte und minimiert die Anzahl von Konflikten, bei denen ein Konflikt vorhergesagt wird, wenn unterschiedliche Schlüsselwerte dem gleichen gehashten Wert zugeordnet werden. Im schlimmsten Fall ist die Anzahl von Vorgängen bei der schlimmstmöglichen Hashfunktion zu der Anzahl von Elementen in der Sequenz proportional (lineare Zeit).

Die hash_set-Klasse sollte der ausgewählte assoziative Container sein, wenn die Bedingungen, mit denen die Werte von der Anwendung den Schlüsseln zugeordnet werden, erfüllt werden. Die Elemente eines hash_set-Objekts sind eindeutig und fungieren als ihre eigenen Sortierschlüssel. Ein Modell für diesen Typ der Struktur ist eine geordnete Liste von z. B. Wörtern, in denen die Wörter möglicherweise nur einmal auftreten. Wenn mehrfaches Vorkommen der Wörter zugelassen wird, ist ein hash_multiset-Element die geeignete Containerstruktur. Wenn Werte an eine Liste von eindeutigen Schlüsselwörtern angefügt werden müssen, ist ein hash_map-Objekt eine geeignete Struktur, um diese Daten zu enthalten. Wenn die Schlüssel dagegen nicht eindeutig sind, ist ein hash_multimap-Objekt der geeignete Container.

Der hash_set sortiert die Sequenz, die er steuert, indem er ein gespeichertes Hash `Traits` Objekt vom Typ [Value_compare](#value_compare)aufruft. Auf das gespeicherte Objekt kann möglicherweise zugegriffen werden, indem die Memberfunktion [key_comp](#key_comp) aufrufen wird. Ein solches Funktionsobjekt muss sich wie ein Objekt der Klasse *hash_compare<Key, less\<Key> >.* verhalten. Insbesondere für alle Werte `key` vom Typ Key ergibt die "calltrait" (`key`) eine Verteilung der Werte vom Typ "size_t".

Im Allgemeinen müssen die Elemente der Vorwärtsiteratoren etwas weniger als vergleichbar sein, um diese Sortierung zu erstellen, sodass beliebige zwei Elemente möglicherweise als gleichwertig bestimmt werden (in dem Sinne, dass keins geringer als das Andere ist), oder dass eins geringer als das Andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Etwas technischer betrachtet ist die Vergleichsfunktion ein binäres Prädikat, das eine strenge schwache Sortierung im mathematischen Sinn verursacht. Bei einem binären *f*(*x*,*y*)-Prädikat handelt es sich um ein Funktionsobjekt, das die zwei Argumentobjekte x und y aufweist sowie einen Rückgabewert von TRUE oder FALSE. Eine Sortierung, die auf ein hash_set-Objekt angewendet wird, ist eine strenge schwache Sortierung, wenn das binäre Prädikat irreflexiv, antisymmetrisch und transitiv ist, und wenn die Äquivalenz transitiv ist, wobei die beiden Objekte *x* und *y* als äquivalent definiert werden, wenn sowohl *f*(*x*,*y*) als auch *f*(*y*, *x*) gleich FALSE sind. Wenn der stärkere Gleichheitszustand zwischen Schlüsseln die Äquivalenz ersetzt, erfolgt die Sortierung total (d. h., alle Elemente werden zueinander sortiert), und die verglichenen Schlüssel sind von den einander nicht mehr zu unterscheiden.

Die tatsächliche Reihenfolge der Elemente in der gesteuerten Sequenz hängt von der Hashfunktion, der Sortierfunktion und der aktuellen Größe der Hashtabelle ab, die im Containerobjekt gespeichert wird. Die aktuelle Größe der Hashtabelle kann nicht bestimmt werden. Deshalb kann die Reihenfolge der Elemente in der gesteuerten Sequenz im Allgemeinen nicht vorhergesagt werden. Das Einfügen von Elementen führt nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen von Elementen werden nur solche Iteratoren ungültig, die speziell auf die entfernten Elemente gezeigt haben.

Der von der hash_set-Klasse bereitgestellte Iterator ist ein bidirektionaler Iterator. Die Klassenmemberfunktionen [insert](#insert) und [hash_set](#hash_set) haben allerdings Versionen, die einen abgeschwächten Eingabeiterator als Vorlagenparameter akzeptieren, dessen Funktionalitätsanforderungen weniger umfangreich sind als diejenigen, die von der Klasse bidirektionaler Iteratoren garantiert werden. Die verschiedenen Iteratorkonzepte bilden eine Family, die durch Verfeinerungen in ihrer Funktionen verknüpft ist. Jedes Iteratorkonzept weist einen eigenen Satz von Anforderungen auf, und die damit funktionierenden Algorithmen müssen die Annahmen hinsichtlich der von diesem Iteratortyp bereitgestellten Anforderungen begrenzen. Es kann davon ausgegangen werden, dass ein Eingabeiterator möglicherweise so dereferenziert wird, dass er auf ein Objekt verweist und dieses möglicherweise zum folgenden Iterator in der Sequenz erhöht. Das ist ein minimaler Funktionssatz, allerdings genügt er, um sinnvoll über einen Iteratorenbereich ( `first`, `last`) im Kontext der Klassenmemberfunktionen zu sprechen.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[hash_set](#hash_set)|Erstellt ein `hash_set`-Element, das leer oder die Kopie eines ganzen anderen `hash_set`-Elements oder eines Teils davon ist.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[allocator_type](#allocator_type)|Ein Typ, der die `allocator`-Klassentyp für das `hash_set`-Objekt darstellt.|
|[const_iterator](#const_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, der im `const`-Element ein `hash_set`-Element lesen kann.|
|[const_pointer](#const_pointer)|Ein Typ, der einen Zeiger auf ein **Konstanten** Element in einer `hash_set`bereitstellt.|
|[const_reference](#const_reference)|Ein Typ, der einen Verweis auf ein **Konstanten** Element bereitstellt, das in einem `hash_set` zum Lesen und Ausführen von **Konstanten** Vorgängen gespeichert ist.|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit **dem jedes Konstante** Element in der `hash_set`gelesen werden kann.|
|[difference_type](#difference_type)|Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen eines `hash_set`-Elements in einen Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.|
|[iterator](#iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einer `hash_set` gelesen oder geändert werden kann.|
|[key_compare](#key_compare)|Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen im `hash_set`-Element zu bestimmen.|
|[key_type](#key_type)|Ein Typ, der ein Objekt beschreibt, das als Element eines `hash_set`-Objekts in seiner Kapazität als Sortierschlüssel gespeichert wird.|
|[pointer](#pointer)|Ein Typ, der einen Zeiger auf ein Element in einer `hash_set` bereitstellt.|
|[Referenz](#reference)|Ein Typ, der einen Verweis auf ein in einer `hash_set` gespeichertes Element bereitstellt.|
|[reverse_iterator](#reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einem umgekehrten `hash_set`-Element gelesen oder geändert werden kann.|
|[size_type](#size_type)|Eine Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in `hash_set` darstellen kann.|
|[value_compare](#value_compare)|Ein Typ, der Folgendes bereitstellt: zwei Funktionsobjekte, ein binäres Prädikat der compare-Klasse, das zwei Elementwerte eines `hash_set`-Objekts vergleichen kann, um deren relative Reihenfolge zu bestimmen, und ein unäres Prädikat, das die Hashwerte der Elemente ermittelt.|
|[value_type](#value_type)|Ein Typ, der ein Objekt beschreibt, das als Element eines `hash_set`-Objekts in seiner Kapazität als Wert gespeichert wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[begin](#begin)|Gibt einen Iterator zurück, der auf das erste Element im `hash_set`-Objekt verweist.|
|[cbegin](#cbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im `hash_set`-Element adressiert.|
|[cend](#cend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines `hash_set`-Elements nachfolgt.|
|[Löschen](#clear)|Löscht alle Elemente einer `hash_set` auf.|
|[count](#count)|Gibt die Anzahl von Elementen in einem `hash_set`-Element zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.|
|[crbegin](#crbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im umgekehrten `hash_set`-Element adressiert.|
|[crend](#crend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten `hash_set`-Elements nachfolgt.|
|[emplace](#emplace)|Fügt ein Element ein, das vor Ort in ein `hash_set`-Element erstellt wird.|
|[emplace_hint](#emplace_hint)|Fügt ein Element ein, das vor Ort mit einem Platzierungshinweis in ein `hash_set`-Element erstellt wird.|
|[empty](#empty)|Testet, ob ein `hash_set`-Element leer ist.|
|[end](#end)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element einem `hash_set`-Element nachfolgt.|
|[equal_range](#equal_range)|Gibt ein Iteratorpaar jeweils bezogen auf das erste Element in einem `hash_set`-Objekt mit einem Schlüssel zurück, der größer als ein bestimmter Schlüssel ist, bzw. bezogen auf das erste Element im `hash_set`-Objekt mit einem Schlüssel, der größer oder gleich dem Schlüssel ist.|
|[erase](#erase)|Es wird ein Element oder ein Bereich von Elementen in einem `hash_set` von angegebenen Speicherorten entfernt, oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.|
|[find](#find)|Gibt einen Iterator zurück, der die Position eines Elements in einem `hash_set`-Element adressiert, das einen Schlüssel aufweist, der einen angegebenen Schlüssel entspricht.|
|[get_allocator](#get_allocator)|Gibt eine Kopie des zum Erstellen von `allocator` verwendeten `hash_set`-Objekts zurück.|
|[insert](#insert)|Fügt ein Element oder einen Elementbereich in ein `hash_set`-Element ein.|
|[key_comp](#key_comp)|Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in `hash_set` verwendet wird.|
|[lower_bound](#lower_bound)|Gibt einen Iterator zum ersten Element in einem `hash_set`-Element mit einem Schlüssel zurück, der gleich oder größer ist, als ein angegebener Schlüssel.|
|[max_size](#max_size)|Gibt die Maximallänge der `hash_set` zurück.|
|[rbegin](#rbegin)|Gibt einen Iterator zurück, der das erste Element in einem umgekehrten `hash_set`-Element adressiert.|
|[rend](#rend)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten `hash_set`-Elements nachfolgt.|
|[size](#size)|Gibt die Anzahl von Elementen in der `hash_set` zurück.|
|[swap](#swap)|Tauscht die Elemente zweier `hash_set`n.|
|[upper_bound](#upper_bound)|Gibt einen Iterator zum ersten Element in einem `hash_set`-Element mit einem Schlüssel zurück, der gleich oder größer ist als ein angegebener Schlüssel.|
|[value_comp](#value_comp)|Ruft eine Kopie des hash-traits-Objekts ab, das dazu verwendet wird, Elementschlüsselwerte in einem `hash_set`-Objekt zu hashen und zu sortieren.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[hash_set::operator=](#op_eq)|Ersetzt die Elemente eines `hash_set`-Elements durch eine Kopie eines anderen `hash_set`-Elements.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<hash_set >

**Namespace:** stdext

## <a name="allocator_type"></a> hash_set::allocator_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der die Zuweisungsklasse für das hash_set-Objekt darstellt.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Bemerkungen

`allocator_type` ist ein Synonym für die Vorlagen Parameter *Zuweisung*.

Weitere Informationen zur *Zuweisung*finden Sie im Abschnitt "Hinweise" des Themas [hash_set-Klasse](../standard-library/hash-set-class.md) .

### <a name="example"></a>Beispiel

In dem Beispiel für [get_allocator](#get_allocator) finden Sie ein Beispiel, das `allocator_type` verwendet.

## <a name="begin"></a> hash_set::begin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen Iterator zurück, der das erste Element im hash_set adressiert.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der das erste Element im hash_set adressiert oder auf den Speicherort hinweist, der auf einem leeren hash_set folgt.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `begin` einem `const_iterator`zugewiesen wird, können die Elemente im hash_set Objekt nicht geändert werden. Wenn der Rückgabewert von `begin` einem `iterator`zugewiesen wird, können die Elemente im hash_set Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_set_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.begin( );
   cout << "The first element of hs1 is " << *hs1_Iter << endl;

   hs1_Iter = hs1.begin( );
   hs1.erase( hs1_Iter );

   // The following 2 lines would err because the iterator is const
   // hs1_cIter = hs1.begin( );
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.begin( );
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
The first element of hs1 is now 2
```

## <a name="cbegin"></a> hash_set::cbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen konstanten Iterator zurück, der das erste Element im hash_set adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const-Iterator, der das erste Element in der [hash_set](../standard-library/hash-set-class.md) adressiert oder auf den Speicherort hinweist, der auf einer leeren `hash_set` folgt.

### <a name="remarks"></a>Bemerkungen

Bei dem Rückgabewert `cbegin` können die Elemente im `hash_set`-Objekt nicht geändert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_set_cbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_iterator hs1_cIter;

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

## <a name="cend"></a> hash_set::cend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines hash_set nachfolgt.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const-Iterator, der den Speicherort adressiert, der dem letzten Element eines [hash_set](../standard-library/hash-set-class.md) nachfolgt. Wenn die `hash_set` leer ist, gilt anschließend `hash_set::cend == hash_set::begin`.

### <a name="remarks"></a>Bemerkungen

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines `hash_set` erreicht hat. Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_set_cend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_cIter;

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

## <a name="clear"></a> hash_set::clear

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Löscht alle Elemente eines hash_set.

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 1 );
   hs1.insert( 2 );

   cout << "The size of the hash_set is initially " << hs1.size( )
        << "." << endl;

   hs1.clear( );
   cout << "The size of the hash_set after clearing is "
        << hs1.size( ) << "." << endl;
}
```

```Output
The size of the hash_set is initially 2.
The size of the hash_set after clearing is 0.
```

## <a name="const_iterator"></a> hash_set::const_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein **const**-Element im hash_set gelesen werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_iterator`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

In dem Beispiel für [begin](#begin) finden Sie ein Beispiel, das `const_iterator` verwendet.

## <a name="const_pointer"></a> hash_set::const_pointer

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der einen Zeiger auf ein **const**-Element im hash_set bereitstellt.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_pointer`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [const_iterator](#const_iterator) für den Zugriff auf Elemente in einem **const**-hash_set-Objekt verwendet werden.

## <a name="const_reference"></a> hash_set::const_reference

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der einen Verweis auf ein **const**-Element bereitstellt, das in einem hash_set zum Lesen und Ausführen von **const**-Vorgängen gespeichert ist.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_const_ref.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_set is 10.
```

## <a name="const_reverse_iterator"></a> hash_set::const_reverse_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes **const**-Element im hash_set gelesen werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reverse_iterator`-Typ kann nicht den Wert eines Elements ändern und wird verwendet, um das hash_set in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Im Beispiel für [rend](#rend) wird verdeutlicht, wie ein `const_reverse_iterator` deklariert und verwendet wird.

## <a name="count"></a> hash_set::count

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt die Anzahl von Elementen in einer hash_set-Klasse zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Schlüssel des Elements mit einem übereinstimmenden Schlüssel aus der hash_set-Klasse.

### <a name="return-value"></a>Rückgabewert

1, wenn hash_set ein Element enthält, dessen Sortierschlüssel mit dem Parameterschlüssel übereinstimmt.

0, wenn hash_set kein Element mit einem übereinstimmenden Schlüssel enthält.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Anzahl der Elemente im folgenden Bereich zurück:

\[ lower_bound (*Schlüssel*), upper_bound (*Schlüssel*)).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der „hash_set::count“-Memberfunktion gezeigt.

```cpp
// hash_set_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1;
    hash_set<int>::size_type i;

    hs1.insert(1);
    hs1.insert(1);

    // Keys must be unique in hash_set, so duplicates are ignored.
    i = hs1.count(1);
    cout << "The number of elements in hs1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hs1.count(2);
    cout << "The number of elements in hs1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hs1 with a sort key of 1 is: 1.
The number of elements in hs1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a> hash_set::crbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen const-Iterator zurück, der das erste Element in einem umgekehrten hash_set adressiert.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler const-Iterator, mit dem das erste Element in einem umgekehrten [hash_set](../standard-library/hash-set-class.md) adressiert wird (bzw. mit dem das ehemals letzte Element in der nicht umgekehrten `hash_set` adressiert wird).

### <a name="remarks"></a>Bemerkungen

`crbegin` wird bei einem umgekehrten hash_set auf die gleiche Weise verwendet wie [begin](#begin) mit einem hash_set.

Bei dem Rückgabewert von `crbegin` kann das `hash_set`-Objekt nicht geändert werden.

Mit `crbegin` lässt sich eine `hash_set` rückwärts durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// hash_set_crbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
```

## <a name="crend"></a> hash_set::crend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten hash_set nachfolgt.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler const-Iterator, der den Standort anspricht, der dem letzten Element in einem umgekehrten[hash_set](../standard-library/hash-set-class.md) nachfolgt (der Speicherort, der dem ersten Element im nicht umgekehrten `hash_set` vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einem umgekehrten `hash_set` auf die gleiche Weise verwendet, wie [hash_set::end](#end) bei einem `hash_set` verwendet wird.

Bei dem Rückgabewert von `crend` kann das `hash_set`-Objekt nicht geändert werden.

`crend` kann verwendet werden, um zu testen, ob das Ende der `hash_set` von einem umgekehrten Iterator erreicht wurde.

### <a name="example"></a>Beispiel

```cpp
// hash_set_crend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
```

## <a name="difference_type"></a> hash_set::difference_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen eines hash_set in einem Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

`difference_type` ist der Typ, der beim Subtrahieren oder Inkrementieren über Iteratoren des Containers zurückgegeben wird. `difference_type` wird normalerweise verwendet, um die Anzahl von Elementen im Bereich [ `first`, `last`) zwischen den Iteratoren `first` und `last` darzustellen. Dazu gehört das Element, auf das durch `first` gezeigt wird sowie der Bereich von Elementen bis zu (aber nicht einschließlich) dem Element, auf das durch `last` gezeigt wird.

Beachten Sie, dass, obwohl `difference_type` für alle Iteratoren verfügbar ist, die die Anforderungen für einen Eingabeiterator erfüllen, wozu auch die Klasse bidirektionaler Iteratoren gehört, die von umkehrbaren Containern wie Satz unterstützt wird, die Subtraktion zwischen Iteratoren nur von Iteratoren mit zufälligem Zugriff, die über einen Container mit zufälligem Zugriff bereitgestellt werden, beispielsweise „vector“ oder „deque“, unterstützt wird.

### <a name="example"></a>Beispiel

```cpp
// hash_set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;

   hs1.insert( 20 );
   hs1.insert( 10 );
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique

   hs1_bIter = hs1.begin( );
   hs1_eIter = hs1.end( );

   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );

   // The keys, and hence the elements, of a hash_set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_set hs1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_set hs1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_set hs1.\n";

   // Count the number of elements in a hash_set
   hash_set <int>::difference_type  df_count = 0;
   hs1_Iter = hs1.begin( );
   while ( hs1_Iter != hs1_eIter)
   {
      df_count++;
      hs1_Iter++;
   }

   cout << "The number of elements in the hash_set hs1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_set hs1.
The number '10' occurs 1 times in hash_set hs1.
The number '20' occurs 1 times in hash_set hs1.
The number of elements in the hash_set hs1 is: 2.
```

## <a name="emplace"></a> hash_set::emplace

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Fügt ein Element, das vor Ort erstellt wird, in ein hash_set ein.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*val*|Der Wert eines Elements, das in das [hash_set](../standard-library/hash-set-class.md) eingefügt werden soll, es sei denn, `hash_set` enthält dieses Element bereits oder, üblicher, ein Element, dessen Schlüssel gleichwertig sortiert wird.|

### <a name="return-value"></a>Rückgabewert

Die `emplace` Member-Funktion gibt ein paar zurück, dessen **boolesche** Komponente **true** zurückgibt, wenn eine Einfügung erfolgt ist, und **false** , wenn die `hash_set` bereits ein Element enthielt, dessen Schlüssel einen entsprechenden Wert in der Reihenfolge aufweist und dessen iteratorkomponente die Adresse zurückgibt, an der ein neues Element eingefügt wurde oder in dem sich das Element bereits befand.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.emplace(move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="emplace_hint"></a> hash_set::emplace_hint

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Fügt ein Element, das vor Ort erstellt wird, in ein hash_set ein.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*val*|Der Wert eines Elements, das in das [hash_set](../standard-library/hash-set-class.md) eingefügt werden soll, es sei denn, `hash_set` enthält dieses Element bereits oder, üblicher, ein Element, dessen Schlüssel gleichwertig sortiert wird.|
|*_Where*|Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Die Einfügung kann in amortisierter konstanter Zeit anstelle von logarithmischer Zeit erfolgen, wenn die Einfügemarke direkt auf *_Where*folgt.)|

### <a name="return-value"></a>Rückgabewert

Die [hash_set::emplace](#emplace)-Memberfunktion gibt einen Iterator zurück, der auf die Position zeigt, an der das neue Element in den `hash_set` eingefügt wurde, oder, in dem sich das vorhandene Element mit entsprechender Sortierung befindet.

### <a name="remarks"></a>Bemerkungen

Die Einfügung kann in amortisierter konstanter Zeit anstelle von logarithmischer Zeit erfolgen, wenn die Einfügemarke direkt auf *_Where*folgt.

### <a name="example"></a>Beispiel

```cpp
// hash_set_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.insert(hs3.begin(), move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="empty"></a> hash_set::empty

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Testet, ob ein hash_set-Element leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das hash_set-Element leer ist; **FALSE**, wenn es nicht leer ist.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2;
   hs1.insert ( 1 );

   if ( hs1.empty( ) )
      cout << "The hash_set hs1 is empty." << endl;
   else
      cout << "The hash_set hs1 is not empty." << endl;

   if ( hs2.empty( ) )
      cout << "The hash_set hs2 is empty." << endl;
   else
      cout << "The hash_set hs2 is not empty." << endl;
}
```

```Output
The hash_set hs1 is not empty.
The hash_set hs2 is empty.
```

## <a name="end"></a> hash_set::end

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines hash_set nachfolgt.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der den Speicherort adressiert, der dem letzten Element eines hash_set nachfolgt. Wenn das hash_set leer ist, folgt anschließend „hash_set::end == hash_set::begin“.

### <a name="remarks"></a>Bemerkungen

`end` wird verwendet, um zu testen, ob ein Iterator das Ende seiner hash_set erreicht hat. Der von `end` zurückgegebene Wert darf nicht dereferenziert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_set_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: iterator hs1_Iter;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.end( );
   hs1_Iter--;
   cout << "The last element of hs1 is " << *hs1_Iter << endl;

   hs1.erase( hs1_Iter );

   // The following 3 lines would err because the iterator is const:
   // hs1_cIter = hs1.end( );
   // hs1_cIter--;
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.end( );
   hs1_cIter--;
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
The last element of hs1 is now 2
```

## <a name="equal_range"></a> hash_set::equal_range

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt ein Iteratorpaar jeweils zum ersten Element in einem hash_set mit einem Schlüssel zurück, der gleich dem eines bestimmten Schlüssels ist, bzw. zum ersten Element im hash_set mit einem Schlüssel, der gleich dem Schlüssel ist.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden hash_set verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein Iteratorenpaar, bei der das erste der [lower_bound](../standard-library/set-class.md#lower_bound) des Schlüssels und das zweite Paar der [upper_bound](../standard-library/set-class.md#upper_bound) des Schlüssels ist.

Um auf den ersten Iterator einer paar-PR zuzugreifen, die von der-Member-Funktion zurückgegeben wird, verwenden Sie `pr`. **first** verwenden, und Sie können einen lower_bound-Iterator dereferenzieren, indem Sie \*( `pr`. **first**) verwenden. Sie können auf den zweiten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **second** verwenden, und Sie können einen upper_bound-Iterator dereferenzieren, indem Sie \*( `pr`. **second**) verwenden.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_set<int> IntHSet;
   IntHSet hs1;
   hash_set <int> :: const_iterator hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hs1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hs1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hs1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than or equal to 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.
```

## <a name="erase"></a> hash_set::erase

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Es wird ein Element oder ein Bereich von Elementen in einem hash_set von angegebenen Speicherorten entfernt oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parameter

*_Where*\
Die Position des aus hash_set zu entfernenden Elements.

*erste*\
Die Position des ersten Elements, das aus hash_set entfernt werden soll.

*Letzter*\
Die Position direkt hinter dem letzten aus hash_set entfernten Element.

*Schlüssel*\
Der Schlüssel des aus hash_set zu entfernenden Elements.

### <a name="return-value"></a>Rückgabewert

Bei den ersten beiden Memberfunktionen ist es ein bidirektionaler Iterator, der das erste über die entfernten Elemente hinaus verbliebene Element festlegt, oder ein Zeiger auf das Ende von hash_set, wenn kein solches Element vorhanden ist. Für die dritte Memberfunktion ist es die Anzahl der von hash_set entfernten Elemente.

### <a name="remarks"></a>Bemerkungen

Von der Memberfunktionen wird nie eine Ausnahme ausgelöst.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der „hash_set::erase“-Memberfunktion gezeigt.

```cpp
// hash_set_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1, hs2, hs3;
    hash_set<int>::iterator pIter, Iter1, Iter2;
    int i;
    hash_set<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hs1.insert (i);
        hs2.insert (i * i);
        hs3.insert (i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hs1.begin();
    hs1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_set hs1 is:";
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hs2.begin();
    Iter2 = --hs2.end();
    hs2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_set hs2 is:";
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hs3.erase(2);

    cout << "After the element with a key of 2 is deleted, "
         << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hs3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hs3.begin();
    hs3.erase(Iter1);

    cout << "After another element (unique for hash_set) with a key "
         << endl;
    cout  << "equal to that of the 2nd element is deleted, "
          << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.
After the middle two elements are deleted, the hash_set hs2 is: 16 4.
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.
The number of elements removed from hs3 is: 1.
After another element (unique for hash_set) with a key
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.
```

## <a name="find"></a> hash_set::find

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen Iterator zurück, der die Position eines Elements in einem hash_set adressiert, das einen Schlüssel aufweist, der einem angegebenen Schlüssel entspricht.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden hash_set übereinstimmt.

### <a name="return-value"></a>Rückgabewert

Ein `iterator` oder `const_iterator`, der den Speicherort eines Elements adressiert, das einem angegebenen Schlüssel entspricht, oder das den Speicherort adressiert, der dem letzten Element im hash_set nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Iterator zurück, der ein Element in der hash_set adressiert, dessen Sortierschlüssel `equivalent` dem Argument Schlüssel unter einem binären Prädikat ist, das eine Sortierung basierend auf einer kleiner-als-Kompatibilitäts Beziehung auslöst.

Wenn der Rückgabewert von `find` einem `const_iterator`zugewiesen wird, kann das hash_set Objekt nicht geändert werden. Wenn der Rückgabewert von `find` einem `iterator`zugewiesen wird, kann das hash_set Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// hash_set_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.find( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // The element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.find( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a> hash_set::get_allocator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt eine Kopie des Zuweisungsobjekts zurück, das zum Erstellen des hash_set verwendet wird.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zuweisung, die vom hash_set zum Verwalten des Arbeitsspeichers verwendet wird. Dies ist die Vorlagen Parameter *Zuweisung*.

Weitere Informationen zur *Zuweisung*finden Sie im Abschnitt "Hinweise" des Themas [hash_set-Klasse](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Bemerkungen

Zuweisungen für die hash_set-Klasse geben an, wie die Klasse einen Speicher verwaltet. Für die meisten Programmieranforderungen genügen die standardmäßigen Zuweisungen mit Containerklassen der C++-Standardbibliothek. Schreiben und Verwenden Ihrer eigener Zuweisungsklasse ist ein C++ -Thema für Fortgeschrittene.

### <a name="example"></a>Beispiel

```cpp
// hash_set_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_set <int, hash_compare <int, less<int> > > hs1;
   hash_set <int,  hash_compare <int, greater<int> > > hs2;
   hash_set <double, hash_compare <double,
      less<double> >, allocator<double> > hs3;

   hash_set <int, hash_compare <int,
      greater<int> > >::allocator_type hs2_Alloc;
   hash_set <double>::allocator_type hs3_Alloc;
   hs2_Alloc = hs2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs3.max_size( ) <<  "." << endl;

   // The following lines create a hash_set hs4
   // with the allocator of hash_set hs1.
   hash_set <int>::allocator_type hs4_Alloc;
   hash_set <int> hs4;
   hs4_Alloc = hs2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hs2_Alloc == hs4_Alloc )
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

## <a name="hash_set"></a> hash_set::hash_set

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Erstellt ein `hash_set`-Element, das leer oder die Kopie eines ganzen anderen `hash_set`-Elements oder eines Teils davon ist.

```cpp
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Irdische*|Die für dieses `hash_set`-Objekt zu verwendende Speicherzuweisungsklasse, dessen Standard `Allocator` ist.|
|*Zuschreiben*|Die Vergleichsfunktion vom Typ `const Traits`, die verwendet wird, um die Elemente in `hash_set`, deren Standard `hash_compare` ist, zu sortieren.|
|*Right*|Das `hash_set`-Element, von dem das erstellte `hash_set`-Element eine Kopie sein soll.|
|*First*|Die Position des ersten Elements in dem zu kopierenden Elementbereich.|
|*Last*|Die Position des ersten Elements nach dem zu kopierenden Elementbereich.|

### <a name="remarks"></a>Bemerkungen

In allen Konstruktoren wird Zuweisungsobjekttyp gespeichert, mit dem der Arbeitsspeicher für das `hash_set` verwaltet wird und das später zurückgegeben werden kann, indem [hash_set::get_allocator](#get_allocator) aufgerufen wird. Der Zuweisungsparameter wird häufig aus den Klassendeklarationen und den Vorverarbeitungsmakros weggelassen, die zum Ersetzen alternativer Zuweisungen verwendet werden.

Alle Konstruktoren initialisieren die hash_set-Elemente.

In allen Konstruktoren wird ein Funktionsobjekt vom Typ `Traits` gespeichert, der verwendet wird, um unter den Schlüsseln des `hash_set` eine Sortierung vorzunehmen, und das später zurückgegeben werden kann, indem [hash_set::key_comp](#key_comp) aufgerufen wird. Weitere Informationen zu `Traits` finden Sie im Thema [hash_set-Klasse](../standard-library/hash-set-class.md).

Der erste Konstruktor erstellt ein leeres ursprüngliches `hash_set`-Element. Der Zweite gibt den Typ der Vergleichsfunktion ( `Comp` ) an, die zum Angeben der Reihenfolge der Elemente verwendet wird, und der Dritte gibt explizit den zu verwendenden Zuweisungstyp ( `Al` ) an. Mit dem Schlüsselwort `explicit` werden bestimmte Arten automatischer Typumwandlung unterdrückt.

Der vierte und fünfte Konstruktor geben eine Kopie der `hash_set` `Right`an.

Der sechste, siebte und achte Konstruktor verwendet ein initializer_list-Element für die Elemente.

Mit dem letzten Konstruktor wird der Bereich (`First`, `Last`) eines `hash_set`-Elements kopiert, wobei sich die Explizitheit bei Angabe des Typs der Vergleichsfunktion der Klasse „Traits“ und „allocator“ erhöht.

Der achte Konstruktor verschiebt den `hash_set` `Right`.

Die tatsächliche Reihenfolge der Elemente in einem `hash_set`-Container hängt von der Hashfunktion, von der Sortierfunktion und der aktuellen Größe der Hashtabelle ab und kann im Allgemeinen nicht vorausgesagt werden, wie das beim festgelegten Container der Fall wäre, bei dem sie von der Sortierfunktion allein bestimmt würde.

## <a name="insert"></a> hash_set::insert

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Fügt ein Element oder einen Elementbereich in ein `hash_set`-Element ein.

```cpp
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*Ster*|Der Wert eines Elements, das in `hash_set` eingefügt werden soll, es sei denn, `hash_set` enthält dieses Element bereits oder, üblicher, ein Element, dessen Schlüssel gleichwertig sortiert wird.|
|*Where*|Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Einfügen kann in amortisierter konstanter Zeit, anstelle von logarithmischer Zeit erfolgen, wenn die Einfügemarke direkt `_Where` folgt.)|
|*First*|Die Position des ersten Elements, das aus `hash_set` kopiert werden soll.|
|*Last*|Die Position direkt über den letzten aus `hash_set` zu kopierenden Elements.|
|*IList*|Das initializer_list-Element, aus dem die Elemente kopiert werden sollen.|

### <a name="return-value"></a>Rückgabewert

Die erste `insert` Member-Funktion gibt ein paar zurück, dessen **boolesche** Komponente **true** zurückgibt, wenn eine Einfügung erfolgt ist, und **false** , wenn die `hash_set` bereits ein Element enthielt, dessen Schlüssel einen entsprechenden Wert in der Reihenfolge aufweist und dessen iteratorkomponente die Adresse zurückgibt, an der ein neues Element eingefügt wurde oder in dem sich das Element bereits befand.

Verwenden Sie `pr`, um auf die Iteratorkomponente eines `pr.first`-Paares zuzugreifen, das von dieser Memberfunktion zurückgegeben wird, und `*(pr.first)`, um es zu dereferenzieren. Verwenden Sie `pr.second`, um auf die **boolesche** Komponente eines Paars zuzugreifen, `pr` von dieser Member-Funktion zurückgegeben wird, und verwenden Sie zum Aufheben der Dereferenzierung `*(pr.second)`.

Die zweite `insert`-Memberfunktion gibt einen Iterator zurück, der auf den Speicherort zeigt, an dem das neue Element in `hash_set` eingefügt wurde.

### <a name="remarks"></a>Bemerkungen

Die dritte Memberfunktion fügt die Elemente in einem initializer_list-Element ein.

Die dritte Memberfunktion fügt die Sequenz von Elementwerten in `hash_set` entsprechend jeden Elements ein, das von einem Iterator im Bereich [`First`, `Last`) des angegebenen `hash_set`-Elements adressiert wird.

## <a name="iterator"></a> hash_set::iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einem hash_set gelesen oder geändert werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein Type-`iterator` kann verwendet werden, um den Wert eines Elements zu ändern.

### <a name="example"></a>Beispiel

Im Beispiel für [begin](#begin) wird verdeutlicht, wie ein `iterator` deklariert und verwendet wird.

## <a name="key_comp"></a> hash_set::key_comp

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ruft eine Kopie des hash-traits-Objekts ab, das dazu verwendet wird, Elementschlüsselwerte in einem hash_set zu hashen und zu sortieren.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Funktions Objekt zurück, das ein hash_set verwendet, um seine Elemente zu sortieren, d. h. die Vorlagen Parameter *Merkmale*.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [hash_set-Klasse](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Bemerkungen

Das gespeicherte Objekt definiert die Memberfunktion:

`bool operator( const Key& _xVal, const Key& _yVal );`

die **TRUE** zurückgibt, wenn `_xVal` vorangestellt ist und nicht gleich `_yVal` in der Sortierreihenfolge ist.

Beachten Sie, dass sowohl [key_compare](#key_compare) als auch [value_compare](#value_compare) Synonyme für den Vorlagenparameter *Traits* sind. Beide Typen werden für die hash_set und hash_multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den hash_map und hash_multimap-Klassen.

### <a name="example"></a>Beispiel

```cpp
// hash_set_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > >hs1;
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1
          = hs1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hs1."
        << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hs2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="key_compare"></a> hash_set::key_compare

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen im hash_set zu bestimmen.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Bemerkungen

`key_compare` ist ein Synonym für die Vorlagen Parameter *Merkmale*.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [hash_set-Klasse](../standard-library/hash-set-class.md) .

Beachten Sie, dass sowohl `key_compare` als auch [value_compare](#value_compare) Synonyme für den Vorlagenparameter *Traits* sind. Beide Typen werden für die set- und die multiset-Klasse bereitgestellt, wo sie identisch sind. Sie unterscheiden sich in Bezug auf die Kompatibilität mit der map- und der multimap-Klasse.

### <a name="example"></a>Beispiel

Im Beispiel für [key_comp](#key_comp) wird verdeutlicht, wie `key_compare` deklariert und verwendet wird.

## <a name="key_type"></a> hash_set::key_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der ein Objekt beschreibt, das als Element eines hash_set in seiner Kapazität als Sortierschlüssel gespeichert wird.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

`key_type` ist ein Synonym für den Vorlagen Parameter *Schlüssel*.

Weitere Informationen zu *Key*finden Sie im Abschnitt "Hinweise" des Themas [hash_set-Klasse](../standard-library/hash-set-class.md) .

Beachten Sie, dass sowohl `key_type` als auch [value_compare](#value_type) Synonyme für den Vorlagenparameter *Key* sind. Beide Typen werden für die hash_set und hash_multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den hash_map und hash_multimap-Klassen.

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie `key_type` deklariert und verwendet wird.

## <a name="lower_bound"></a> hash_set::lower_bound

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen Iterator zum ersten Element in ein hash_set mit einem Schlüssel zurück, der gleich oder größer als ein angegebener Schlüssel ist.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden hash_set verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein `iterator` oder `const_iterator`, der den Speicherort eines Elements in einem hash_set adressiert, der einen Schlüssel hat, der gleich oder größer als der Argument Schlüssel ist, oder der den Speicherort adressiert, der dem letzten Element im hash_set nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.lower_bound( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator that addresses the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a> hash_set::max_size

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt die Maximallänge des hash_set zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die mögliche Maximallänge des hash_set.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::size_type i;

   i = hs1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_set is " << i << "." << endl;
}
```

## <a name="op_eq"></a> hash_set::operator=

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ersetzt die Elemente des hash_set durch eine Kopie einer anderen.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|-|-|
|*right*|Das [hash_set](../standard-library/hash-set-class.md), das in das `hash_set` kopiert wird.|

### <a name="remarks"></a>Bemerkungen

Nachdem alle vorhandenen Elemente in einem `hash_set`gelöscht wurden, `operator=` entweder kopiert oder verschiebt den Inhalt von *right* in den `hash_set`.

### <a name="example"></a>Beispiel

```cpp
// hash_set_operator_as.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<int> v1, v2, v3;
   hash_set<int>::iterator iter;

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

## <a name="pointer"></a> hash_set::pointer

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der einen Zeiger auf ein Element in einem hash_set bereitstellt.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein Type-`pointer` kann verwendet werden, um den Wert eines Elements zu ändern.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem Listenobjekt verwendet werden.

## <a name="rbegin"></a> hash_set::rbegin

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen Iterator zurück, der das erste Element in einem umgekehrten hash_set adressiert.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, mit dem das erste Element in einem umgekehrten hash_set adressiert wird (bzw. mit dem das ehemals letzte Element im nicht umgekehrten hash_set adressiert wird).

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einem umgekehrten hash_set auf die gleiche Weise verwendet wie [begin](#begin) mit einem hash_set.

Wenn der Rückgabewert von `rbegin` einem `const_reverse_iterator` zugewiesen wird, kann das hash_set-Objekt nicht geändert werden. Wenn der Rückgabewert von `rbegin` einem `reverse_iterator` zugewiesen wird, kann das hash_set-Objekt geändert werden.

`rbegin` kann verwendet werden, um ein hash_set rückwärts zu durchlaufen.

### <a name="example"></a>Beispiel

```cpp
// hash_set_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << endl;

   // A hash_set element can be erased by dereferencing to its key
   hs1_rIter = hs1.rbegin( );
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_set is "<< *hs1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
The hash_set is: 10 20 30
The reversed hash_set is: 30 20 10
After the erasure, the first element in the reversed hash_set is 20.
```

## <a name="reference"></a> hash_set::reference

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der einen Verweis auf ein im hash_set gespeichertes Element bereitstellt.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_set can be changed
   // by operating on its (non-const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_set is now "
        << *hs1.begin() << "." << endl;
}
```

```Output
The first element in the hash_set is 10.
The first element in the hash_set is now 15.
```

## <a name="rend"></a> hash_set::rend

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten hash_set nachfolgt.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der den Standort anspricht, der dem letzten Element in einem umgekehrten hash_set nachfolgt (der Speicherort, der dem ersten Element im nicht umgekehrten hash_set vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einem umgekehrten hash_set auf die gleiche Weise verwendet wie [end](#end) mit einem hash_set.

Wenn der Rückgabewert von `rend` einem `const_reverse_iterator` zugewiesen wird, kann das hash_set-Objekt nicht geändert werden. Wenn der Rückgabewert von `rend` einem `reverse_iterator` zugewiesen wird, kann das hash_set-Objekt geändert werden. Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

`rend` kann verwendet werden, um zu testen, ob ein umgekehrter Iterator das Ende seines hash_set erreicht hat.

### <a name="example"></a>Beispiel

```cpp
// hash_set_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << "." << endl;

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_set is " << *hs1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
The hash_set is: 10 20 30 .
The reversed hash_set is: 30 20 10 .
After the erasure, the last element in the reversed hash_set is 20.
```

## <a name="reverse_iterator"></a> hash_set::reverse_iterator

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einem umgekehrten hash_set gelesen oder geändert werden kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `reverse_iterator`-Typ wird verwendet, um das hash_set in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Im Beispiel für [rbegin](#rbegin) wird verdeutlicht, wie `reverse_iterator` deklariert und verwendet wird.

## <a name="size"></a> hash_set::size

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt die Anzahl von Elementen im hash_set zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge des hash_set.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: size_type i;

   hs1.insert( 1 );
   i = hs1.size( );
   cout << "The hash_set length is " << i << "." << endl;

   hs1.insert( 2 );
   i = hs1.size( );
   cout << "The hash_set length is now " << i << "." << endl;
}
```

```Output
The hash_set length is 1.
The hash_set length is now 2.
```

## <a name="size_type"></a> hash_set::size_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einemhash_set darstellen kann.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im Beispiel für [size](#size) wird verdeutlicht, wie `size_type` deklariert und verwendet wird.

## <a name="swap"></a> hash_set::swap

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Tauscht die Elemente zweier hash_sets aus.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Das hash_set-Argument, das die Elemente bereitstellt mit der das Ziel-hash_set getauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion macht keine Verweise, Zeiger oder Iteratoren ungültig, die Elemente in zwei hash_sets bezeichnet, dessen Elemente ausgetauscht werden.

### <a name="example"></a>Beispiel

```cpp
// hash_set_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   hash_set <int>::iterator hs1_Iter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );
   hs2.insert( 100 );
   hs2.insert( 200 );
   hs3.insert( 300 );

   cout << "The original hash_set hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hs1.swap( hs2 );

   cout << "After swapping with hs2, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hs1, hs3 );

   cout << "After swapping with hs3, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_set hs1 is: 10 20 30.
After swapping with hs2, list hs1 is: 200 100.
After swapping with hs3, list hs1 is: 300.
```

## <a name="upper_bound"></a> hash_set::upper_bound

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Gibt einen Iterator zum ersten Element in ein hash_set mit einem Schlüssel zurück, der größer ist als ein angegebener Schlüssel.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden hash_set verglichen wird.

### <a name="return-value"></a>Rückgabewert

Ein `iterator` oder `const_iterator`, der den Speicherort eines Elements in einem hash_set adressiert, der einen Schlüssel hat, der gleich oder größer als der Argument Schlüssel ist, oder der den Speicherort adressiert, der dem letzten Element im hash_set nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

```cpp
// hash_set_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "The first element of hash_set hs1 with a key greater "
        << "than 20 is: " << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_set hs1 with a key > 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.begin( );
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );
   cout << "The first element of hs1 with a key greater than "
        << endl << "that of the initial element of hs1 is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The first element of hash_set hs1 with a key greater than 20 is: 30.
The hash_set hs1 doesn't have an element with a key greater than 30.
The first element of hs1 with a key greater than
that of the initial element of hs1 is: 20.
```

## <a name="value_comp"></a> hash_set::value_comp

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Elementwerte in einem hash_set verwendet wird.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Funktions Objekt zurück, das ein hash_set verwendet, um seine Elemente zu sortieren, d. h. der Vorlagen Parameter *Vergleich*.

Weitere Informationen zum *Vergleich*finden Sie im Abschnitt "Hinweise" des Themas [hash_set-Klasse](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Bemerkungen

Das gespeicherte Objekt definiert die Memberfunktion:

`bool operator( const Key& _xVal, const Key& _yVal );`

die **TRUE** zurückgibt, wenn `_xVal` vorangestellt ist und nicht gleich `_yVal` in der Sortierreihenfolge ist.

Beachten Sie, dass sowohl [Value_compare](../standard-library/set-class.md#value_compare) als auch [key_compare](../standard-library/set-class.md#key_compare) Synonyme für den Vorlagen Parameter *Compare*sind. Beide Typen werden für die hash_set und hash_multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den hash_map und hash_multimap-Klassen.

### <a name="example"></a>Beispiel

```cpp
// hash_set_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > > hs1;
   hash_set <int, hash_compare < int, less<int> >  >::value_compare
      vc1 = hs1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hs1."
           << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::value_compare
      vc2 = hs2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="value_compare"></a> hash_set::value_compare

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der Folgendes bereitstellt: zwei Funktionsobjekte, ein binäres Prädikat der compare-Klasse, das zwei Elementwerte eines hash_set vergleichen kann, um deren relative Reihenfolge zu bestimmen, und ein unäres Prädikat, das die Hashwerte der Elemente ermittelt.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Bemerkungen

`value_compare` ist ein Synonym für die Vorlagen Parameter *Merkmale*.

Weitere Informationen zu *Merkmalen* finden Sie im Thema [hash_set-Klasse](../standard-library/hash-set-class.md) .

Beachten Sie, dass sowohl [key_compare](#key_compare) als auch `value_compare` Synonyme für die Vorlagen Parameter *Merkmale*sind. Beide Typen werden für die hash_set und hash_multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den hash_map und hash_multimap-Klassen.

### <a name="example"></a>Beispiel

Im Beispiel für [value_comp](#value_comp) wird verdeutlicht, wie ein `value_compare` deklariert und verwendet wird.

## <a name="value_type"></a> hash_set::value_type

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist [unordered_set-Klasse](../standard-library/unordered-set-class.md).

Ein Typ, der ein Objekt beschreibt, das als Element eines hash_set in seiner Kapazität als Sortierschlüssel gespeichert wird.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Beispiel

```cpp
// hash_set_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;

   hash_set <int> :: value_type hsvt_Int;   // Declare value_type
   hsvt_Int = 10;             // Initialize value_type

   hash_set <int> :: key_type hskt_Int;   // Declare key_type
   hskt_Int = 20;             // Initialize key_type

   hs1.insert( hsvt_Int );         // Insert value into hs1
   hs1.insert( hskt_Int );         // Insert key into hs1

   // A hash_set accepts key_types or value_types as elements
   cout << "The hash_set has elements:";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)
      cout << " " << *hs1_Iter;
   cout << "." << endl;
}
```

```Output
The hash_set has elements: 10 20.
```

## <a name="see-also"></a>Weitere Informationen

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
