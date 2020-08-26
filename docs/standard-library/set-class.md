---
title: set-Klasse
ms.date: 11/04/2016
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
ms.openlocfilehash: e879e7ffd9f674769e32548195f5017e27e64576
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846237"
---
# <a name="set-class"></a>set-Klasse

Der Containerklassensatz der C++-Standardbibliothek wird zum Speichern und Abrufen von Daten aus einer Sammlung verwendet, in der die Werte der enthaltenen Elemente eindeutig sind und als Schlüsselwerte dienen, nach denen die Daten automatisch sortiert werden. Der Schlüsselwert eines Elements in einem Satz darf nicht direkt geändert werden. Stattdessen müssen Sie alte Werte löschen und Elemente mit neuen Werten einfügen.

## <a name="syntax"></a>Syntax

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>Parameter

*Wichtigen*\
Der in dem Satz zu speichernde Elementdatentyp.

*Aufweisen*\
Der Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in dem Satz zu bestimmen. Dieses Argument ist optional, und das binäre Prädikat **less** *\<Key>* ist der Standardwert.

In C ++ 14 können Sie heterogenes Nachschlagen durch Angabe des `std::less<>` oder `std::greater<>` Prädikats, das keine Typparameter aufweist, aktivieren. Weitere Informationen finden Sie unter [Heterogenes Nachschlagen in assoziativen Containern](../standard-library/stl-containers.md#sequence_containers).

*Allocator*\
Der Typ, der das gespeicherte Zuordnungsobjekt darstellt, das Details zum Belegen und Freigeben des Arbeitsspeichers des Satzes kapselt. Dieses Argument ist optional, und der Standardwert ist `allocator<Key>`.

## <a name="remarks"></a>Bemerkungen

Ein C++-Standardbibliothekssatz ist:

- Ein assoziativer Container, der ein Container variabler Größe ist, der den effizienten Abruf von Elementwerten auf Grundlage eines zugeordneten Schlüsselwert unterstützt. Darüber hinaus ist es ein einfacher assoziativer Container, da die Elementwerte den Schlüsselwerten entsprechen.

- Umkehrbar, da ein bidirektionaler Iterator für den Zugriff auf die Elemente bereitgestellt wird.

- Sortiert, da die Elemente anhand von Schlüsselwerten innerhalb des Containers mit einer angegebenen Vergleichsfunktion sortiert werden.

- Insofern eindeutig, da jedes der Elemente einen eindeutigen Schlüssel aufweisen muss. Da der Satz auch ein einfacher assoziativer Container ist, sind seine Elemente ebenfalls eindeutig.

Eine Menge wird auch als Klassen Vorlage beschrieben, da die von ihr bereitgestellte Funktionalität generisch und unabhängig von dem spezifischen Datentyp ist, der als Elemente enthalten ist. Der zu verwendende Datentyp wird stattdessen in der Klassenvorlage zusammen mit der Vergleichsfunktion und der Zuweisung als Parameter angegeben.

Die Auswahl des Containertyps sollte im Allgemeinen auf Grundlage des für die Anwendung erforderlichen Suchen und Einfügetyps erfolgen. Assoziative Container sind für Such-, Einfüge- und Entfernvorgänge optimiert. Die Memberfunktionen, die diese Vorgänge explizit unterstützen, sind effizient und führen sie in einer Zeit aus, die zum Logarithmus der Elementanzahl im Container im Durchschnitt proportional ist. Das Einfügen von Elementen führt nicht dazu, dass Iteratoren ungültig werden, und durch das Entfernen von Elementen werden nur solche Iteratoren ungültig, die speziell auf die entfernten Elemente gezeigt haben.

Der Satz sollte der ausgewählte assoziative Container sein, wenn die Bedingungen, mit denen die Werte von der Anwendung den Schlüsseln zugeordnet werden, erfüllt werden. Die Elemente eines Satzes sind eindeutig und dienen als eigene Sortierschlüssel. Ein Modell für diesen Typ der Struktur ist eine geordnete Liste von z. B. Wörtern, in denen die Wörter möglicherweise nur einmal auftreten. Wenn mehrfaches Vorkommen der Wörter zugelassen wird, ist eine Multimenge die geeignete Containerstruktur. Wenn Werte einer Liste von eindeutigen Schlüsselwörtern hinzugefügt werden müssen, ist eine Zuordnung eine äquivalente Struktur, um diese Daten zu enthalten. Wenn stattdessen die Schlüssel nicht eindeutig sind, ist eine Mehrfachzuordnung der geeignete Container.

Der Satz sortiert die von ihm gesteuerte Sequenz, indem ein gespeichertes Funktionsobjekt vom Typ [key_compare](#key_compare) aufgerufen wird. Bei diesem gespeicherten Objekt handelt es sich um eine Vergleichsfunktion, auf die durch Aufrufen der Memberfunktion [key_comp](#key_comp) zugegriffen werden kann. Im Allgemeinen müssen die Elemente etwas weniger als vergleichbar sein, um diese Sortierung zu erstellen, sodass für zwei Elemente bestimmt werden kann, dass sie gleichwertig sind (in dem Sinne, dass keins geringer als das andere ist) oder dass eins geringer als das andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Etwas technischer betrachtet ist die Vergleichsfunktion ein binäres Prädikat, das eine strenge schwache Sortierung im mathematischen Sinn verursacht. Bei einem binären *f*( *x, y*)-Prädikat handelt es sich um ein Funktions Objekt, das die zwei Argument Objekte *x* und *y* aufweist sowie einen Rückgabewert von **`true`** oder **`false`** . Eine Sortierung, die auf eine Menge angewendet wird, ist eine strenge schwache Sortierung, wenn das binäre Prädikat irreflexiv, antisymmetrisch und transitiv ist und wenn die Äquivalenz transitiv ist, wobei die beiden Objekte *x* und *y* als äquivalent definiert werden, wenn sowohl *f*( *x,y*) als auch *f*( *y,x*) FALSE sind. Wenn der stärkere Gleichheitszustand zwischen Schlüsseln die Äquivalenz ersetzt, erfolgt die Sortierung total (d. h., alle Elemente werden zueinander sortiert), und die verglichenen Schlüssel sind von den einander nicht mehr zu unterscheiden.

In C ++ 14 können Sie heterogenes Nachschlagen durch Angabe des `std::less<>` oder `std::greater<>` Prädikats, das keine Typparameter aufweist, aktivieren. Weitere Informationen finden Sie unter [Heterogenes Nachschlagen in assoziativen Containern](../standard-library/stl-containers.md#sequence_containers).

Der von einer Set-Klasse bereitgestellte Iterator ist ein bidirektionaler Iterator. Die Klassenmemberfunktionen [insert](#insert) und [set](#set) weisen allerdings Versionen auf, einen abgeschwächten Eingabeiterator als einen Vorlagenparameter akzeptieren, dessen Funktionalitätsanforderungen weniger umfangreich sind, als die von der Klasse bidirektionaler Iteratoren garantierten. Die verschiedenen Iteratorkonzepte bilden eine Family, die durch Verfeinerungen in ihrer Funktionen verknüpft ist. Jedes Iteratorkonzept weist einen eigenen Satz von Anforderungen auf, und die damit funktionierenden Algorithmen müssen die Annahmen hinsichtlich der von diesem Iteratortyp bereitgestellten Anforderungen begrenzen. Es kann davon ausgegangen werden, dass ein Eingabeiterator möglicherweise so dereferenziert wird, dass er auf ein Objekt verweist und dieses möglicherweise zum folgenden Iterator in der Sequenz erhöht. Obwohl es sich dabei nur um eine Mindestmenge von Funktionen handelt, reichen sie aus, um auf sinnvolle Weise über einen Bereich von Iteratoren [ `First`, `Last`) im Zusammenhang mit den Klassenmemberfunktionen zu sprechen.

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[set](#set)|Erstellt einen Satz, der leer oder die Kopie eines ganzen anderen Satzes oder eines Teils davon ist.|

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[allocator_type](#allocator_type)|Ein Typ, der die `allocator`-Klasse für das Set-Objekt darstellt.|
|[const_iterator](#const_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein- **`const`** Element im Satz gelesen werden kann.|
|[const_pointer](#const_pointer)|Ein Typ, der einen Zeiger auf ein- **`const`** Element in einem Satz bereitstellt.|
|[const_reference](#const_reference)|Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einem Satz zum Lesen und Ausführen von **`const`** Vorgängen gespeichert ist.|
|[const_reverse_iterator](#const_reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes beliebige **`const`** Element im Satz gelesen werden kann.|
|[difference_type](#difference_type)|Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen eines Satzes in einem Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.|
|[Iterator](#iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes Element in einem Satz gelesen oder geändert werden kann.|
|[key_compare](#key_compare)|Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen im Satz zu bestimmen.|
|[key_type](#key_type)|Der Typ beschreibt ein Objekt, das als Element eines Satzes in seiner Kapazität als Sortierschlüssel gespeichert wird.|
|[Zeichner](#pointer)|Ein Typ, der einen Zeiger auf ein Element in einem Satz bereitstellt.|
|[Referenz](#reference)|Ein Typ, der einen Verweis auf ein in einem Satz gespeichertes Element bereitstellt.|
|[reverse_iterator](#reverse_iterator)|Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einem umgekehrten Satz gelesen oder geändert werden kann.|
|[size_type](#size_type)|Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einem Satz darstellen kann.|
|[value_compare](#value_compare)|Der Typ, der ein Funktionsobjekt bereitstellt, das zwei Elemente vergleichen kann, um die relative Position im Satz zu bestimmen.|
|[value_type](#value_type)|Der Typ beschreibt ein Objekt, das als Element eines Satzes in seiner Kapazität als Wert gespeichert wird.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[beginnen](#begin)|Gibt einen Iterator zurück, der das erste Element im Satz adressiert.|
|[cbegin](#cbegin)|Gibt einen konstanten Iterator zurück, der das erste Element im Satz adressiert.|
|[cend](#cend)|Gibt einen konstanten Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines Satzes nachfolgt.|
|[Löschen](#clear)|Löscht alle Elemente eines Satzes.|
|[count](#count)|Gibt die Anzahl von Elementen in einem Satz zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.|
|[crbegin](#rbegin)|Gibt einen const-Iterator zurück, der das erste Element in einer umgekehrten Menge adressiert.|
|[crend](#rend)|Gibt einen const-Iterator zurück, der den Speicherort adressiert, der dem letzten Element einer umgekehrten Menge nachfolgt.|
|[emplace](#emplace)|Fügt ein Element, das vor Ort erstellt wird, in einen Satz ein.|
|[emplace_hint](#emplace_hint)|Fügt ein Element, das vor Ort erstellt wird, mit einem Platzierungshinweis in einen Satz ein.|
|[empty](#empty)|Testet, ob ein Satz leer ist.|
|[end](#end)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines Satzes nachfolgt.|
|[equal_range](#equal_range)|Gibt ein Iteratorpaar jeweils zum ersten Element in einem Satz mit einem Schlüssel zurück, der größer als ein bestimmter Schlüssel ist, bzw. zum ersten Element im Satz mit einem Schlüssel, der größer oder gleich dem Schlüssel ist.|
|[erase](#erase)|Es wird ein Element oder ein Bereich von Elementen in einem Satz von angegebenen Speicherorten entfernt, oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.|
|[find](#find)|Gibt einen Iterator zurück, der die Position eines Elements in einem Satz adressiert, das einen Schlüssel aufweist, der einem angegebenen Schlüssel entspricht.|
|[get_allocator](#get_allocator)|Gibt eine Kopie des zum Erstellen des Satzes verwendeten `allocator`-Objekts zurück.|
|[insert](#insert)|Fügt ein Element oder einen Elementbereich in einen Satz ein.|
|[key_comp](#key_comp)|Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in einem Satz verwendet wird.|
|[lower_bound](#lower_bound)|Gibt einen Iterator zum ersten Element in einem Satz mit einem Schlüssel zurück, der gleich oder größer als ein angegebener Schlüssel ist.|
|[max_size](#max_size)|Gibt die Maximallänge des Satzes zurück.|
|[rbegin](#rbegin)|Gibt einen Iterator zurück, der das erste Element in einem umgekehrten Satz adressiert.|
|[rend](#rend)|Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten Satzes nachfolgt.|
|[size](#size)|Gibt die Anzahl der Elemente im Satz zurück.|
|[swap](#swap)|Tauscht die Elemente zweier Sätze aus.|
|[upper_bound](#upper_bound)|Gibt einen Iterator zum ersten Element in einem Satz mit einem Schlüssel zurück, der größer als ein angegebener Schlüssel ist.|
|[value_comp](#value_comp)|Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Elementwerte in einem Satz verwendet wird.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator =](#op_eq)|Ersetzt die Elemente eines Satzes durch eine Kopie eines anderen Satzes.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

Ein Typ, der die Zuweisungsklasse für das Set-Objekt darstellt.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Bemerkungen

`allocator_type` ist ein Synonym für die Vorlagen Parameter [Zuweisung](../standard-library/set-class.md).

Gibt das Funktionsobjekt zurück, das dem Vorlagenparameter `Allocator` entspricht und von einer Multimenge verwendet wird, um die jeweiligen Elemente zu sortieren.

Weitere Informationen zu `Allocator` finden Sie im Abschnitt „Hinweise“ des Themas [set-Klasse](../standard-library/set-class.md).

### <a name="example"></a>Beispiel

In dem Beispiel für [get_allocator](#get_allocator) finden Sie ein Beispiel, in dem `allocator_type` verwendet wird.

## <a name="begin"></a><a name="begin"></a> beginnen

Gibt einen Iterator zurück, der das erste Element im Satz adressiert.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der das erste Element in der Menge adressiert oder auf den Speicherort hinweist, der auf eine leere Menge folgt.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert von `begin` einem zugewiesen wird `const_iterator` , können die Elemente im Set-Objekt nicht geändert werden. Wenn der Rückgabewert von `begin` einem zugewiesen wird `iterator` , können die Elemente im Set-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

Gibt einen **`const`** Iterator zurück, der das erste Element im Bereich adressiert.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** bidirektionaler-Access-Iterator, der auf das erste Element des Bereichs zeigt oder die Position direkt hinter dem Ende eines leeren Bereichs (für einen leeren Bereich `cbegin() == cend()` ).

### <a name="remarks"></a>Bemerkungen

Bei dem Rückgabewert `cbegin` können die Elemente im Bereich nicht geändert werden.

Sie können diese Memberfunktion anstelle der `begin()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollte `Container` ein änderbarer (nicht) Container sein, **`const`** der und unterstützt `begin()` `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> cend

Gibt einen **`const`** Iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** bidirektionaler-Access-Iterator, der direkt hinter das Ende des Bereichs zeigt.

### <a name="remarks"></a>Bemerkungen

`cend` wird verwendet, um zu testen, ob ein Iterator das Ende seines Bereichs übergeben hat.

Sie können diese Memberfunktion anstelle der `end()`-Memberfunktion verwenden, um sicherzustellen, dass der Rückgabewert `const_iterator` ist. Normalerweise wird sie zusammen mit dem [auto](../cpp/auto-cpp.md)-Typableitungs-Schlüsselwort verwendet, wie im folgenden Beispiel gezeigt. In diesem Beispiel sollte `Container` ein änderbarer (nicht) Container sein, **`const`** der und unterstützt `end()` `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="clear"></a><a name="clear"></a> Klartext

Löscht alle Elemente eines Satzes.

```cpp
void clear();
```

### <a name="example"></a>Beispiel

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein- **`const`** Element im Satz gelesen werden kann.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_iterator`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

### <a name="example"></a>Beispiel

In dem Beispiel für [begin](#begin) finden Sie ein Beispiel, das `const_iterator` verwendet.

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Ein Typ, der einen Zeiger auf ein- **`const`** Element in einem Satz bereitstellt.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_pointer`-Typ kann nicht zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [const_iterator](#const_iterator) für den Zugriff auf Elemente in einem Const-Set-Objekt verwendet werden.

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Ein Typ, der einen Verweis auf ein-Element bereitstellt, das **`const`** in einem Satz zum Lesen und Ausführen von **`const`** Vorgängen gespeichert ist.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Beispiel

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> const_reverse_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem jedes beliebige **`const`** Element im Satz gelesen werden kann.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `const_reverse_iterator`-Typ kann nicht den Wert eines Elements ändern und wird verwendet, um die Menge in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Im Beispiel für [rend](#rend) wird verdeutlicht, wie ein `const_reverse_iterator` deklariert und verwendet wird.

## <a name="count"></a><a name="count"></a> Countdown

Gibt die Anzahl von Elementen in einem Satz zurück, dessen Schlüssel dem von einem Parameter angegebenen Schlüssel entspricht.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Schlüssel der Elemente, die aus einem Satz abgeglichen werden.

### <a name="return-value"></a>Rückgabewert

1, wenn der Satz ein Element enthält, dessen Sortierschlüssel mit dem Parameterschlüssel übereinstimmt. 0, wenn der Satz kein Element mit einem übereinstimmenden Schlüssel enthält.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Anzahl der Elemente im folgenden Bereich zurück:

\[ lower_bound (*Schlüssel*), upper_bound (*Schlüssel*)).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung der Memberfunktion "set::count" gezeigt.

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a><a name="crbegin"></a> crbegin

Gibt einen const-Iterator zurück, der das erste Element in einer umgekehrten Menge adressiert.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein konstanter umgekehrter bidirektionaler Iterator, mit dem das erste Element in einer umgekehrten Menge adressiert wird (bzw. mit dem das ehemals letzte Element in der nicht umgekehrten Menge adressiert wird).

### <a name="remarks"></a>Bemerkungen

`crbegin` wird bei einer umgekehrten Menge auf die gleiche Weise verwendet, wie [begin](#begin) bei einer Menge verwendet wird.

Bei dem Rückgabewert `crbegin` kann das Set-Objekt nicht geändert werden.

### <a name="example"></a>Beispiel

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a><a name="crend"></a> crend

Gibt einen const-Iterator zurück, der den Speicherort adressiert, der dem letzten Element einer umgekehrten Menge nachfolgt.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler const_reverse-Iterator, der den Standort anspricht, der dem letzten Element in einer umgekehrten Menge nachfolgt (der Speicherort, der dem ersten Element in der nicht umgekehrten Menge vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`crend` wird bei einer umgekehrten Menge auf die gleiche Weise verwendet, wie [end](#end) bei einer Menge verwendet wird.

Bei dem Rückgabewert `crend` kann das Set-Objekt nicht geändert werden. Der von `crend` zurückgegebene Wert darf nicht dereferenziert werden.

`crend` kann verwendet werden, um zu testen, ob das Ende der Menge von einem umgekehrten Iterator erreicht wurde.

### <a name="example"></a>Beispiel

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Ein Ganzzahltyp mit Vorzeichen, der dazu verwendet werden kann, die Anzahl von Elementen eines Satzes in einem Bereich zwischen Elementen darzustellen, auf die von Iteratoren gezeigt wird.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

`difference_type` ist der Typ, der beim Subtrahieren oder Inkrementieren über Iteratoren des Containers zurückgegeben wird. `difference_type` wird normalerweise verwendet, um die Anzahl von Elementen im Bereich *(first, last)* zwischen den Iteratoren `first` und `last` darzustellen. Dazu gehört das Element, auf das durch `first` gezeigt wird und der Bereich von Elementen bis zu (aber nicht einschließlich) dem Element, auf das durch `last` gezeigt wird.

Bitte beachten Sie, dass die Subtraktion zwischen Iteratoren nur von Iteratoren mit zufälligem Zugriff unterstützt wird, die über einen Container mit zufälligem Zugriff wie „vector“ bereitgestellt werden. Dies gilt, obwohl `difference_type` für alle Iteratoren verfügbar ist, die die Anforderungen eines Eingabeiterators erfüllen. Hierzu zählt auch die Klasse bidirektionaler Iteratoren, die von umkehrbaren Containern wie „set“ unterstützt wird.

### <a name="example"></a>Beispiel

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a><a name="emplace"></a> emplace

Es wird ein Element eingefügt, das vor Ort konstruiert wird (keine Kopieren- oder Verschiebevorgänge werden ausgeführt).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parameter

*args*\
Die Argumente, die zum Erstellen eines in den Satz einzufügenden Elements weitergeleitet werden, es sei denn, es ist bereits ein Element enthalten, dessen Wert gleichwertig sortiert wird.

### <a name="return-value"></a>Rückgabewert

Ein [Paar](../standard-library/pair-structure.md), dessen boolesche Komponente TRUE zurückgibt, wenn eine Einfügung erfolgte, und FALSE, wenn die Zuordnung bereits ein Element enthielt, dessen Wert einen entsprechenden Wert in der Reihenfolge aufweist. Die Iteratorkomponente des Rückgabewertpaars gibt die Adresse zurück, an der ein neues Element eingefügt wurde (die boolesche Komponente ist "True"), oder wenn das Element bereits lokalisiert wurde (die boolesche Komponente ist "False").

### <a name="remarks"></a>Bemerkungen

Durch diese Funktion werden keine Iteratoren oder Verweise ungültig.

Wird während des Einbaus eine Ausnahme ausgelöst, wird der Zustand des Containers nicht geändert.

### <a name="example"></a>Beispiel

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a><a name="emplace_hint"></a> emplace_hint

Fügt ein Element mit einem Platzierungshinweis ein, das vor Ort erstellt wird (Es werden keine Kopier- oder Verschiebevorgänge ausgeführt).

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parameter

*args*\
Die zum Erstellen eines in den Satz einzufügenden Elements weitergeleiteten Argumente, es sei denn, der Satz enthält dieses Element bereits, oder üblicher, es sei denn, ein Element, dessen Wert gleichwertig sortiert wird, ist bereits enthalten.

*Was*\
Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Wenn dieser Punkt unmittelbar vor *dem*Speicherort von liegt, kann die Einfügung in amortisierter konstanter Zeit anstelle der logarithmischen Zeit erfolgen.)

### <a name="return-value"></a>Rückgabewert

Ein Iterator zum neu eingefügten Element.

Wenn die Einfügung fehlerhaft war, da das Element bereits vorhanden ist, wird ein Iterator an das vorhandene Element zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Durch diese Funktion werden keine Iteratoren oder Verweise ungültig.

Wird während des Einbaus eine Ausnahme ausgelöst, wird der Zustand des Containers nicht geändert.

### <a name="example"></a>Beispiel

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="empty"></a><a name="empty"></a> leer

Testet, ob ein Satz leer ist.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn der Satz leer ist. , **`false`** Wenn der Satz nicht leer ist.

### <a name="example"></a>Beispiel

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a><a name="end"></a> Schließlich

Gibt den "past-the-end"-Iterator zurück.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Rückgabewert

Der "past-the-end"-Iterator. Wenn der Satz leer ist, dann gilt `set::end() == set::begin()`.

### <a name="remarks"></a>Bemerkungen

**end** wird verwendet, um zu testen, ob ein Iterator das Ende einer Menge übergeben hat.

Der von **end** zurückgegebene Wert darf nicht dereferenziert werden.

Ein Codebeispiel finden Sie unter [set::find](#find).

## <a name="equal_range"></a><a name="equal_range"></a> equal_range

Gibt ein Iteratorpaar jeweils zum ersten set-Element mit einem Schlüssel zurück, der größer als oder gleich einem bestimmten Schlüssel ist, bzw. zum ersten set-Element mit einem Schlüssel, der größer als der Schlüssel ist.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der Menge verglichen wird, die durchsucht wird.

### <a name="return-value"></a>Rückgabewert

Ein Iteratorenpaar, bei der das Erste der [lower_bound](#lower_bound) des Schlüssels und das zweite Paar der [upper_bound](#upper_bound) des Schlüssels ist.

Sie können auf den ersten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **first**verwenden Sie zum Aufheben der Dereferenzierung des unteren gebundenen Iterators \* ( `pr` . **zuerst**). Sie können auf den zweiten Iterator eines von einer Memberfunktion zurückgegebenen Paars `pr` zugreifen, indem Sie `pr`. **Zweitens**: um den oberen gebundenen Iterator zu dereferenzieren, verwenden Sie \* ( `pr` . **Sekunde**).

### <a name="example"></a>Beispiel

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a><a name="erase"></a> Löschen

Es wird ein Element oder ein Bereich von Elementen in einem Satz von angegebenen Speicherorten entfernt, oder es werden die einem angegebenen Schlüssel entsprechenden Elemente entfernt.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
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

Bei den ersten beiden Memberfunktionen ist es ein bidirektionaler Iterator, der das erste über die entfernten Elemente hinaus verbliebe Element festlegt, oder ein Element, das das Ende des Satzes darstellt, wenn kein solches Element vorhanden ist.

Für die dritte Memberfunktion wird die Anzahl der vom Satz entfernten Elemente zurück gegeben.

### <a name="example"></a>Beispiel

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an initializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}
```

## <a name="find"></a><a name="find"></a> sich

Gibt einen Iterator zurück, der auf den Speicherort eines Elements in einem Satz verweist, der einen Schlüssel gleich einem angegebenen Schlüssel aufweist.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Schlüsselwert, der mit dem Sortierschlüssel eines Elements aus dem zu durchsuchenden Satz übereinstimmt.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Speicherort eines Elements mit einem angegebenen Schlüssel verweist, oder der Speicherort, der dem letzten Element im Satz (`set::end()`) nachfolgt, wenn keine Übereinstimmung für den Schlüssel gefunden wird.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Iterator zurück, der auf ein Element in der Menge verweist, dessen Schlüssel dem Argument *Schlüssel* in einem binären Prädikat entspricht, das eine Reihenfolge auf Grundlage einer weniger-als-Kompatibilitäts Beziehung auslöst.

Wenn der Rückgabewert von `find` einem zugewiesen wird `const_iterator` , kann das Set-Objekt nicht geändert werden. Wenn der Rückgabewert von `find` einem zugewiesen wird `iterator` , kann das Set-Objekt geändert werden.

### <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Gibt eine Kopie des allocator-Objekts zurück, das zum Erstellen der Menge verwendet wird.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zuweisung, die von „set“ zur Arbeitsspeicherverwaltung verwendet wird, die der Vorlagenparameter `Allocator` ist.

Weitere Informationen zu `Allocator` finden Sie im Abschnitt „Hinweise“ des Themas [set-Klasse](../standard-library/set-class.md).

### <a name="remarks"></a>Bemerkungen

Zuweisungen für Set-Klasse geben an, wie die Klasse einen Speicher verwaltet. Für die meisten Programmieranforderungen reichen die standardmäßigen allocator-Objekte mit Containerklassen der C++-Standardbibliothek aus. Schreiben und Verwenden Ihrer eigener Zuweisungsklasse ist ein C++ -Thema für Fortgeschrittene.

### <a name="example"></a>Beispiel

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a><a name="insert"></a> setze

Fügt ein Element oder einen Elementbereich in einen Satz ein.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parameter

*Ster*\
Der Wert eines in den Satz einzufügenden Elements, es sei denn, es ist bereits ein Element enthalten, dessen Wert gleichwertig sortiert wird.

*Was*\
Die Position, an dem mit der Suche nach dem richtigen Einfügepunkt begonnen wird. (Wenn dieser Punkt unmittelbar vor *dem*Speicherort von liegt, kann die Einfügung in amortisierter konstanter Zeit anstelle der logarithmischen Zeit erfolgen.)

*Valty*\
Ein Vorlagen Parameter, der den Argumenttyp angibt, mit dem der Satz ein Element [value_type](../standard-library/map-class.md#value_type)erstellen kann, und *perfekt als Argument* weiterleitet.

*Erstes*\
Die Position des ersten zu kopierenden Elements.

*Letzten*\
Die Position direkt über den letzten zu kopierenden Elements.

*InputIterator*\
Das Vorlagenfunktionsargument, das den Anforderungen eines [Eingabeiterators](../standard-library/input-iterator-tag-struct.md) erfüllt, der auf Elemente eines Typs zeigt, der zum Erstellen von [value_type](../standard-library/map-class.md#value_type)-Objekten verwendet werden kann.

*IList*\
Der [initializer_list](../standard-library/initializer-list.md) , aus dem die Elemente kopiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Einzelelement-Element Funktionen (1) und (2) geben ein [paar](../standard-library/pair-structure.md) zurück, dessen **`bool`** Komponente true ist, wenn eine Einfügung erfolgt ist, und false, wenn die Menge bereits ein Element eines äquivalenten Werts in der Reihenfolge enthielt. Die iteratorkomponente des Rückgabewert Paars zeigt auf das neu eingefügte Element, wenn die **`bool`** Komponente "true" ist, oder auf das vorhandene Element, wenn die **`bool`** Komponente "false" ist.

Die Einzelelement-Memberfunktionen mit Hinweis (3) und (4) geben einen Iterator zurück, der auf die Position zeigt, an der das neue Element in den Satz eingefügt wurde, oder, falls ein Element mit einem entsprechenden Schlüssel bereits vorhanden ist, auf das vorhandene Element.

### <a name="remarks"></a>Bemerkungen

Durch diese Funktion werden keine Iteratoren, Zeiger oder Verweise ungültig.

Wird beim Einfügen von nur einem Element eine Ausnahme ausgelöst, wird der Zustand des Containers nicht geändert. Wird beim Einfügen mehrerer Elementen eine Ausnahme ausgelöst, wird der Container in einem nicht angegebenen doch gültigen Zustand belassen.

Um auf die Iteratorkomponente eines `pair` `pr`-Elements zuzugreifen, das von den Einzelelement-Memberfunktionen zurückgegeben wird, verwenden Sie `pr.first`. Um den Iterator im zurückgegebenen Paar zu dereferenzieren, verwenden Sie `*pr.first`. Damit erhalten Sie ein Element. Um auf die- **`bool`** Komponente zuzugreifen, verwenden Sie `pr.second` . Eine Beispiel finden Sie unter Beispielcode weiter unten in diesem Artikel.

Das [value_type](../standard-library/map-class.md#value_type)-Element eines Containers ist eine Typedef, die dem Container angehört, und beim Satz ist `set<V>::value_type` vom Typ `const V`.

Die Bereichsmemberfunktion (5) fügt die Sequenz von Elementwerten in einen Satz ein, das jedem Element entspricht, das von einem Iterator im Bereich `[First, Last)` adressiert wird. Daher wird `Last` nicht eingefügt. Die Containermemberfunktion `end()` bezieht sich auf die Position direkt hinter dem letzten Element im Container. Z. B versucht die Anweisung `s.insert(v.begin(), v.end());` alle Elemente von `v` in `s` einzufügen. Nur Elemente, die eindeutige Werte im Bereich aufweisen werden eingefügt. Duplikate werden ignoriert. Um zu betrachten welche Elemente abgelehnt werden, verwenden Sie die Einzelelementversionen von `insert`.

Die Memberfunktion für die Initialisiererliste (6) verwendet eine [initializer_list](../standard-library/initializer-list.md), um Elemente in die Menge zu kopieren.

Für das Einfügen eines hier erstellten Elements. Das heißt, es wurden keine Kopier- oder Verschiebevorgänge ausgeführt. Siehe [set::emplace](#emplace) und [set::emplace_hint](#emplace_hint).

### <a name="example"></a>Beispiel

```cpp
// set_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> Iterator

Ein Typ, der einen konstanten [bidirektionalen Iterator](../standard-library/bidirectional-iterator-tag-struct.md) bereitstellt, mit dem jedes set-Element gelesen oder geändert werden kann.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Beispiel

Im Beispiel für [Begin](#begin) finden Sie ein Beispiel für das Deklarieren und Verwenden eines `iterator` .

## <a name="key_comp"></a><a name="key_comp"></a> key_comp

Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Schlüssel in einem Satz verwendet wird.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Funktionsobjekt zurück, das eine Menge verwendet, um ihre Elemente zu sortieren, und das der Vorlagenparameter `Traits` ist.

Weitere Informationen zu `Traits` finden Sie im Thema [set-Klasse](../standard-library/set-class.md).

### <a name="remarks"></a>Bemerkungen

Das gespeicherte Objekt definiert die Memberfunktion

**bool-Operator ()**(Konstante**Schlüssel&** `_xVal` , **Konstanten Schlüssel&** `_yVal` );

, der zurückgibt, **`true`** Wenn `_xVal` vorausgeht und `_yVal` in der Sortierreihenfolge nicht gleich ist.

[key_compare](#key_compare) und [value_compare](#value_compare) sind Synonyme für den Vorlagenparameter `Traits`. Beide Typen werden für den Satz und multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den Zuordnungs- und multimap-Klassen.

### <a name="example"></a>Beispiel

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a><a name="key_compare"></a> key_compare

Eine Typ, der ein Funktionsobjekt bereitstellt, das zwei Sortierschlüssel vergleichen kann, um die relative Position von zwei Elementen im Satz zu bestimmen.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Bemerkungen

`key_compare` ist ein Synonym für den Vorlagenparameter `Traits`.

Weitere Informationen zu `Traits` finden Sie im Thema [set-Klasse](../standard-library/set-class.md).

Beachten Sie, dass sowohl `key_compare` als auch [Value_compare](#value_compare) Synonyme für den Vorlagen Parameter sind `Traits` . Beide Typen werden für den Satz und multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den Zuordnungs- und multimap-Klassen.

### <a name="example"></a>Beispiel

Im Beispiel für [key_comp](#key_comp) wird verdeutlicht, wie ein `key_compare` deklariert und verwendet wird.

## <a name="key_type"></a><a name="key_type"></a> key_type

Ein Typ, der ein Objekt beschreibt, das als Element eines Set-Objekt in seiner Eigenschaft als Sortierschlüssel gespeichert wird.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Bemerkungen

`key_type` ist ein Synonym für den Vorlagenparameter `Key`.

Weitere Informationen zu `Key` finden Sie im Abschnitt „Hinweise“ des Themas [set-Klasse](../standard-library/set-class.md).

Beachten Sie, dass sowohl `key_type` als auch [value_type](#value_type) Synonyme für den Vorlagen Parameter sind `Key` . Beide Typen werden für den Satz und multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den Zuordnungs- und multimap-Klassen.

### <a name="example"></a>Beispiel

Im Beispiel für [value_type](#value_type) wird verdeutlicht, wie `key_type` deklariert und verwendet wird.

## <a name="lower_bound"></a><a name="lower_bound"></a> lower_bound

Gibt einen Iterator zum ersten Element in einem Satz mit einem Schlüssel zurück, der gleich oder größer als ein angegebener Schlüssel ist.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der Menge verglichen wird, die durchsucht wird.

### <a name="return-value"></a>Rückgabewert

Ein Iterator oder `const_iterator`, der den Speicherort eines set-Elements mit einem Schlüssel adressiert, der gleich oder größer als der Argumentschlüssel ist, oder der den Speicherort des folgenden letzten set-Elements adressiert, wenn kein Treffer für den Schlüssel gefunden wird.

### <a name="example"></a>Beispiel

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a><a name="max_size"></a> max_size

Gibt die Maximallänge des Satzes zurück.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die mögliche Maximallänge der Menge.

### <a name="example"></a>Beispiel

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_eq"></a> Operator =

Ersetzt die Elemente dieses `set` mithilfe von Elementen eines anderen `set`.

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die `set`, die neue, dieser `set` zuzuweisende Elemente bereitstellt.

### <a name="remarks"></a>Bemerkungen

In der ersten Version von `operator=` wird ein [Lvalue-Verweis](../cpp/lvalue-reference-declarator-amp.md) für *right*verwendet, um Elemente von *Rechts* nach zu kopieren `set` .

Die zweite Version verwendet einen [Rvalue-Verweis](../cpp/rvalue-reference-declarator-amp-amp.md) für rechts. Elemente werden von *rechts nach rechts* verschoben `set` .

Alle Elemente in dieser `set` werden verworfen, bevor die Operatorfunktion ausgeführt wird.

### <a name="example"></a>Beispiel

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
   }
```

## <a name="pointer"></a><a name="pointer"></a>-Zeiger

Ein Typ, der einen Zeiger auf ein Element in einem Satz bereitstellt.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Bemerkungen

Ein **pointer**-Typ kann zum Ändern des Werts eines Elements verwendet werden.

In den meisten Fällen sollte ein [Iterator](#iterator) für den Zugriff auf Elemente in einem Set-Objekt verwendet werden.

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

Gibt einen Iterator zurück, der das erste Element in einem umgekehrten Satz adressiert.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, mit dem das erste Element in einer umgekehrten Menge adressiert wird, bzw. mit dem das ehemals letzte Element in der nicht umgekehrten Menge adressiert wird.

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einer umgekehrten Menge auf die gleiche Weise verwendet, wie [begin](#begin) bei einer Menge verwendet wird.

Wenn der Rückgabewert von `rbegin` einem `const_reverse_iterator` zugewiesen wird, kann das Set-Objekt nicht geändert werden. Wenn der Rückgabewert von `rbegin` einem `reverse_iterator`zugewiesen wird, kann das Set-Objekt geändert werden.

Mit `rbegin` kann eine Menge rückwärts durchlaufen werden.

### <a name="example"></a>Beispiel

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a><a name="reference"></a> Angabe

Ein Typ, der einen Verweis auf ein in einem Satz gespeichertes Element bereitstellt.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Beispiel

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a><a name="rend"></a> rend

Gibt einen Iterator zurück, der den Speicherort adressiert, der dem letzten Element eines umgekehrten Satzes nachfolgt.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Rückgabewert

Ein umgekehrter bidirektionaler Iterator, der den Standort anspricht, der dem letzten Element in einer umgekehrten Menge nachfolgt (der Speicherort, der dem ersten Element in der nicht umgekehrten Menge vorangegangen war).

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einer umgekehrten Menge auf die gleiche Weise verwendet, wie [end](#end) bei einer Menge verwendet wird.

Wenn der Rückgabewert von `rend` einem `const_reverse_iterator` zugewiesen wird, kann das Set-Objekt nicht geändert werden. Wenn der Rückgabewert von `rend` einem `reverse_iterator`zugewiesen wird, kann das Set-Objekt geändert werden. Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

`rend` kann verwendet werden, um zu testen, ob das Ende der Menge von einem umgekehrten Iterator erreicht wurde.

### <a name="example"></a>Beispiel

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator

Ein Typ, der einen bidirektionalen Iterator bereitstellt, mit dem ein Element in einem umgekehrten Satz gelesen oder geändert werden kann.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Bemerkungen

Ein `reverse_iterator`-Typ wird verwendet, um die Menge in umgekehrter Reihenfolge zu durchlaufen.

### <a name="example"></a>Beispiel

Im Beispiel für [rbegin](#rbegin) wird verdeutlicht, wie ein `reverse_iterator` deklariert und verwendet wird.

## <a name="set"></a><a name="set"></a> Set

Erstellt einen Satz, der leer oder die Kopie eines ganzen anderen Satzes oder eines Teils davon ist.

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parameter

*Irdische*\
Die für dieses Set-Objekt zu verwendende Speicher zuordnerklasse, deren Standard ist `Allocator` .

*Zuschreiben*\
Die Vergleichsfunktion vom Typ `const Traits`, die verwendet wird, um die Elemente in dem Satz zu sortieren, dessen Standard `Compare` ist.

*Rght*\
Der Satz, dessen Kopie der erstellte Satz sein soll.

*Erstes*\
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*Letzten*\
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*IList*\
Das initializer_list-Element, aus dem die Elemente kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

In allen Konstruktoren wird ein Zuweisungsobjekttyp gespeichert, mit dem der Arbeitsspeicher für die Menge verwaltet wird und der später zurückgegeben werden kann, indem [get_allocator](#get_allocator) aufgerufen wird. Der Zuweisungsparameter wird häufig aus den Klassendeklarationen und den Vorverarbeitungsmakros weggelassen, die zum Ersetzen alternativer Zuweisungen verwendet werden.

Alle Konstruktoren initialisieren die Sätze.

Alle Konstruktoren speichern ein Funktions Objekt vom Typ `Traits` , das verwendet wird, um eine Bestellung zwischen den Schlüsseln des Satzes herzustellen, und die später durch Aufrufen von [key_comp](#key_comp)zurückgegeben werden kann.

Die ersten drei Konstruktoren geben einen leeren ursprünglichen Satz an. Dabei gibt der Zweite den Typ der Vergleichsfunktion (`comp`) an, die zum Angeben der Reihenfolge der Elemente verwendet wird, und der Dritte gibt explizit den zu verwendenden Zuweisungstyp (`al`) an. Mit dem-Schlüsselwort werden **`explicit`** bestimmte Arten automatischer Typkonvertierungen unterdrückt.

Der vierte Konstruktor gibt eine Kopie des `right`-Satzes an.

Die folgenden drei Konstruktoren verwenden ein initializer_list-Element, um Elemente anzugeben.

Mit den nächsten drei Konstruktoren wird der Bereich [ `first` ,) einer Menge kopiert, `last` wobei sich die Explizitheit bei der Angabe des Typs der Vergleichsfunktion der Klasse `Traits` und der **Zuweisung**erhöht.

Der achte Konstruktor gibt eine Kopie des Satzes an, indem `right` verschoben wird.

### <a name="example"></a>Beispiel

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}
```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a><a name="size"></a> Größe

Gibt die Anzahl der Elemente im Satz zurück.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Länge der Menge.

### <a name="example"></a>Beispiel

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Ein Ganzzahltyp ohne Vorzeichen, der die Anzahl von Elementen in einem Satz darstellen kann.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Beispiel

Im Beispiel für [size](#size) wird verdeutlicht, wie ein `size_type` deklariert und verwendet wird.

## <a name="swap"></a><a name="swap"></a> Wechsel

Tauscht die Elemente zweier Sätze aus.

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Das set-Argument, das die Elemente bereitstellt, die mit der Zielmenge getauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion macht keine Verweise, Zeiger oder Iteratoren ungültig, die Elemente in zwei Mengen bezeichnet, deren Elemente ausgetauscht werden.

### <a name="example"></a>Beispiel

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a><a name="upper_bound"></a> upper_bound

Gibt einen Iterator zum ersten set-Element mit einem Schlüssel zurück, der größer ist als ein angegebener Schlüssel.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parameter

*wichtigen*\
Der Argumentschlüssel, der mit dem Sortierschlüssel eines Elements aus der Menge verglichen wird, die durchsucht wird.

### <a name="return-value"></a>Rückgabewert

Ein `iterator` oder ein `const_iterator` , der den Speicherort eines Elements in einem Satz adressiert, der größer ist als der Argument Schlüssel, oder der den Speicherort adressiert, der dem letzten Element in der Menge nachfolgt, wenn keine Entsprechung für den Schlüssel gefunden wird.

### <a name="example"></a>Beispiel

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a><a name="value_comp"></a> value_comp

Ruft eine Kopie des Vergleichsobjekts ab, das zum Sortieren der Elementwerte in einem Satz verwendet wird.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Funktionsobjekt zurück, das eine Menge verwendet, um ihre Elemente zu sortieren, und das der Vorlagenparameter `Traits` ist.

Weitere Informationen zu `Traits` finden Sie im Thema [set-Klasse](../standard-library/set-class.md).

### <a name="remarks"></a>Bemerkungen

Das gespeicherte Objekt definiert die Memberfunktion

**bool-Operator**(Konstante**Schlüssel&** `_xVal` , **Konstanten Schlüssel&** `_yVal` );

, der zurückgibt, **`true`** Wenn `_xVal` vorausgeht und `_yVal` in der Sortierreihenfolge nicht gleich ist.

Beachten Sie, dass sowohl [value_compare](#value_compare) als auch [key_compare](#key_compare) Synonyme für den Vorlagenparameter `Traits` sind. Beide Typen werden für den Satz und multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den Zuordnungs- und multimap-Klassen.

### <a name="example"></a>Beispiel

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a><a name="value_compare"></a> value_compare

Der Typ, der ein Funktionsobjekt bereitstellt, das zwei Elemente vergleichen kann, um die relative Position in der Menge zu bestimmen.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Bemerkungen

`value_compare` ist ein Synonym für den Vorlagenparameter `Traits`.

Weitere Informationen zu `Traits` finden Sie im Thema [set-Klasse](../standard-library/set-class.md).

Beachten Sie, dass sowohl [key_compare](#key_compare) als auch `value_compare` Synonyme für den Vorlagen Parameter sind `Traits` . Beide Typen werden für den Satz und multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den Zuordnungs- und multimap-Klassen.

### <a name="example"></a>Beispiel

Im Beispiel für [value_comp](#value_comp) wird verdeutlicht, wie `value_compare` deklariert und verwendet wird.

## <a name="value_type"></a><a name="value_type"></a> value_type

Ein Typ, der ein Objekt beschreibt, das als Element einer Menge in seiner Eigenschaft als Wert gespeichert wird.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Bemerkungen

`value_type` ist ein Synonym für den Vorlagenparameter `Key`.

Weitere Informationen zu `Key` finden Sie im Abschnitt „Hinweise“ des Themas [set-Klasse](../standard-library/set-class.md).

Beachten Sie, dass sowohl [key_type](#key_type) als auch `value_type` Synonyme für den Vorlagen Parameter sind `Key` . Beide Typen werden für den Satz und multiset-Klassen bereitgestellt, in der sie identisch sind. Sie sind unterschiedlich in der Kompatibilität mit den Zuordnungs- und multimap-Klassen.

### <a name="example"></a>Beispiel

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```
