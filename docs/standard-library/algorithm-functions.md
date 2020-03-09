---
title: '&lt;Algorithmusfunktionen&gt;'
ms.date: 11/04/2016
f1_keywords:
- algorithm/std::adjacent_find
- algorithm/std::all_of
- algorithm/std::any_of
- algorithm/std::binary_search
- algorithm/std::copy
- algorithm/std::copy_backward
- algorithm/std::copy_if
- algorithm/std::copy_n
- algorithm/std::equal
- algorithm/std::equal_range
- algorithm/std::fill
- algorithm/std::fill_n
- algorithm/std::find
- algorithm/std::find_end
- algorithm/std::find_first_of
- algorithm/std::find_if
- algorithm/std::find_if_not
- algorithm/std::for_each
- algorithm/std::generate
- algorithm/std::generate_n
- algorithm/std::includes
- algorithm/std::inplace_merge
- algorithm/std::is_heap
- algorithm/std::is_heap_until
- algorithm/std::is_partitioned
- algorithm/std::is_permutation
- algorithm/std::is_sorted
- algorithm/std::is_sorted_until
- algorithm/std::iter_swap
- algorithm/std::lexicographical_compare
- algorithm/std::lower_bound
- algorithm/std::make_heap
- algorithm/std::max
- algorithm/std::max_element
- algorithm/std::merge
- algorithm/std::min
- algorithm/std::minmax
- algorithm/std::minmax_element
- algorithm/std::min_element
- algorithm/std::mismatch
- algorithm/std::move
- algorithm/std::move_backward
- algorithm/std::next_permutation
- algorithm/std::none_of
- algorithm/std::nth_element
- algorithm/std::partial_sort
- algorithm/std::partial_sort_copy
- algorithm/std::partition
- algorithm/std::partition_point
- algorithm/std::pop_heap
- algorithm/std::prev_permutation
- algorithm/std::push_heap
- algorithm/std::random_shuffle
- algorithm/std::remove
- algorithm/std::remove_copy
- algorithm/std::remove_copy_if
- algorithm/std::remove_if
- algorithm/std::replace
- algorithm/std::replace_copy
- algorithm/std::replace_copy_if
- algorithm/std::replace_if
- algorithm/std::reverse
- algorithm/std::reverse_copy
- algorithm/std::rotate
- algorithm/std::rotate_copy
- algorithm/std::search
- algorithm/std::search_n
- algorithm/std::set_difference
- algorithm/std::set_intersection
- algorithm/std::set_symmetric_difference
- algorithm/std::set_union
- algorithm/std::shuffle
- algorithm/std::sort
- algorithm/std::sort_heap
- algorithm/std::stable_partition
- algorithm/std::stable_sort
- algorithm/std::swap_ranges
- algorithm/std::transform
- algorithm/std::unique
- algorithm/std::unique_copy
- algorithm/std::upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
helpviewer_keywords:
- std::adjacent_find [C++]
- std::all_of [C++]
- std::any_of [C++]
- std::binary_search [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_if [C++]
- std::copy_n [C++]
- std::equal [C++]
- std::equal_range [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::find_end [C++]
- std::find_first_of [C++]
- std::find_if [C++]
- std::find_if_not [C++]
- std::for_each [C++]
- std::generate [C++]
- std::generate_n [C++]
- std::includes [C++]
- std::inplace_merge [C++]
- std::is_heap [C++]
- std::is_heap_until [C++]
- std::is_partitioned [C++]
- std::is_permutation [C++]
- std::is_sorted [C++]
- std::is_sorted_until [C++]
- std::iter_swap [C++]
- std::lexicographical_compare [C++]
- std::lower_bound [C++]
- std::make_heap [C++]
- std::max [C++]
- std::max_element [C++]
- std::merge [C++]
- std::min [C++]
- std::minmax [C++]
- std::minmax_element [C++]
- std::min_element [C++]
- std::mismatch [C++]
- std::move [C++]
- std::move_backward [C++]
- std::next_permutation [C++]
- std::none_of [C++]
- std::nth_element [C++]
- std::partial_sort [C++]
- std::partial_sort_copy [C++]
- std::partition [C++]
- std::partition_point [C++]
- std::pop_heap [C++]
- std::prev_permutation [C++]
- std::push_heap [C++]
- std::random_shuffle [C++]
- std::remove [C++]
- std::remove_copy [C++]
- std::remove_copy_if [C++]
- std::remove_if [C++]
- std::replace [C++]
- std::replace_copy [C++]
- std::replace_copy_if [C++]
- std::replace_if [C++]
- std::reverse [C++]
- std::reverse_copy [C++]
- std::rotate [C++]
- std::rotate_copy [C++]
- std::search [C++]
- std::search_n [C++]
- std::set_difference [C++]
- std::set_intersection [C++]
- std::set_symmetric_difference [C++]
- std::set_union [C++]
- std::shuffle [C++]
- std::sort [C++]
- std::sort_heap [C++]
- std::stable_partition [C++]
- std::stable_sort [C++]
- std::swap_ranges [C++]
- std::transform [C++]
- std::unique [C++]
- std::unique_copy [C++]
- std::upper_bound [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_n [C++]
- std::count [C++]
- std::equal [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::is_permutation [C++]
- std::lexicographical_compare [C++]
- std::move [C++]
- std::move_backward [C++]
- std::reverse [C++]
- std::rotate [C++]
- std::count_if [C++]
- std::partition_copy [C++]
- std::swap [C++]
ms.openlocfilehash: 199634997397cca0008c60843b5d977633277331
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854860"
---
# <a name="ltalgorithmgt-functions"></a>&lt;Algorithmusfunktionen&gt;

## <a name="adjacent_find"></a>adjacent_find

Sucht zwei benachbarte Elemente, die entweder gleich sind oder eine angegebene Bedingung erfüllen.

```cpp
template<class ForwardIterator>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator , class BinaryPredicate>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*pred-* \
Das binäre Prädikat, das die Bedingung vorgibt, mithilfe der Werte der benachbarten Elemente im zu durchsuchenden Bereich erfüllt zu werden.

### <a name="return-value"></a>Rückgabewert

Ein forward-Iterator zum ersten der angrenzenden Elemente, die entweder gleich sind (in der ersten Version) oder die die durch das binäre Prädikat angegebene Bedingung erfüllen (in der zweiten Version), vorausgesetzt, dass ein solches Paar von Elementen gefunden wird. Andernfalls wird ein Iterator zurückgegeben, der auf den *letzten* zeigt.

### <a name="remarks"></a>Bemerkungen

Der `adjacent_find`-Algorithmus ist ein Algorithmus, der keine Änderungen bezüglich der Abfolge bewirkt. Der zu durchsuchende Bereich muss gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position ist von der Ersten durch Zunahme erreichbar. Die Zeitkomplexität des Algorithmus ist linear zur Anzahl der im Bereich enthaltenen Elemente.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

### <a name="example"></a>Beispiel

```cpp
// alg_adj_fnd.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

// Returns whether second element is twice the first
bool twice (int elem1, int elem2 )
{
    return elem1 * 2 == elem2;
}

int main()
{
    using namespace std;
    list<int> L;
    list<int>::iterator Iter;
    list<int>::iterator result1, result2;

    L.push_back( 50 );
    L.push_back( 40 );
    L.push_back( 10 );
    L.push_back( 20 );
    L.push_back( 20 );

    cout << "L = ( " ;
    for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )
        cout << *Iter << " ";
    cout << ")" << endl;

    result1 = adjacent_find( L.begin( ), L.end( ) );
    if ( result1 == L.end( ) )
        cout << "There are not two adjacent elements that are equal."
            << endl;
    else
        cout << "There are two adjacent elements that are equal.\n"
            << "They have a value of "
            << *( result1 ) << "." << endl;

    result2 = adjacent_find( L.begin( ), L.end( ), twice );
    if ( result2 == L.end( ) )
        cout << "There are not two adjacent elements where the "
            << "second is twice the first." << endl;
    else
    {
        cout << "There are two adjacent elements where "
            << "the second is twice the first.\n"
            << "They have values of " << *(result2++)
            << " & " << *result2 << "." << endl;
    }
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a>all_of

Gibt **true** zurück, wenn eine Bedingung bei jedem Element im angegebenen Bereich vorhanden ist.

```cpp
template<class InputIterator, class UnaryPredicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool all_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabe-Iterator, der angibt, ab wo nach Bedingungen gesucht werden soll. Der Iterator zeigt an, an welcher Stelle ein Bereich von Elementen beginnt.

*Letzter*\
Ein Eingabe-Iterator, der angibt, an welcher Stelle ein Bereich von Elementen endet, in dem nach einer Bedingung gesucht werden soll.

*pred-* \
Eine Bedingung, auf die geprüft werden soll. Hierbei handelt es sich um ein benutzerdefiniertes Prädikatfunktionsobjekt, das die Bedingung definiert, die vom zu prüfenden Element erfüllt werden muss. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Gibt " **true** " zurück, wenn die Bedingung bei jedem Element im angegeben Bereich erkannt wird oder wenn der Bereich leer ist, andernfalls " **false** ".

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt nur **dann true** zurück, wenn für jede `N` im Bereich `[0, last - first)`das Prädikat `pred(*(first + N))` **true**ist.

### <a name="example"></a>Beispiel

```cpp
// alg_all_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 50, 40, 10, 20, 20 };
    list<int>::iterator iter;

    cout << "li = ( ";
    for (iter = li.begin(); iter != li.end(); iter++)
        cout << *iter << " ";
    cout << ")" << endl;

    // Check if all elements in li are even.
    auto is_even = [](int elem){ return !(elem % 2); };
    if (all_of(li.begin(), li.end(), is_even))
        cout << "All the elements are even numbers.\n";
    else
        cout << "Not all the elements are even numbers.\n";
}
```

```Output
li = ( 50 40 10 20 20 )
All the elements are even numbers.
```

## <a name="any_of"></a>any_of

Gibt **true** zurück, wenn eine Bedingung mindestens einmal im angegebenen Bereich von Elementen vorhanden ist.

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool any_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabe-Iterator, der angibt, ab wo ein Bereich von Elementen auf eine Bedingung überprüft werden soll.

*Letzter*\
Ein Eingabe-Iterator, der angibt, an welcher Stelle ein Bereich von Elementen endet, in dem nach einer Bedingung gesucht werden soll.

*pred-* \
Eine Bedingung, auf die geprüft werden soll. Diese wird von einem benutzerdefinierten Prädikatfunktionsobjekt bereitgestellt. Das Prädikat definiert die Bedingung, die das zu prüfende Element erfüllen muss. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Gibt **true** zurück, wenn die Bedingung mindestens einmal im festgelegten Bereich erkannt wird, **false** , wenn die Bedingung niemals erkannt wird.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt nur **dann true** zurück, wenn für einige `N` im Bereich

`[0, last - first)`wird das Prädikat `pred(*(first + N))` "true".

### <a name="example"></a>Beispiel

```cpp
// alg_any_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 51, 41, 11, 21, 20 };

    cout << "li = ( ";
    for (auto const& el : li)
        cout << el << " ";
    cout << ")" << endl;

    // Check if there is an even elememt in li.
    auto is_even = [](int const elem){ return !(elem % 2); };
    if (any_of(li.begin(), li.end(), is_even))
        cout << "There's an even element in li.\n";
    else
        cout << "There are no even elements in li.\n";
}
```

```Output
li = ( 51 41 11 21 20 )
There's an even element in li.
```

## <a name="binary_search"></a>binary_search

Testet, ob ein Element in einem sortierten Bereich einem angegebenen Wert entspricht oder ihm auf eine von einem binären Prädikat angegebene Weise gleicht.

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*value*\
Der Wert, mit dem vom Wert des Elements eine Übereinstimmung erzielt werden muss oder der die Bedingung mit dem vom binären Prädikat angegebenen Elementwert erfüllen muss.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

**true** , wenn ein Element im Bereich gefunden wird, der gleich dem angegebenen Wert ist oder diesem entspricht. andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Der sortierte Quellbereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position muss der innerhalb der Reihenfolge vom ersten von der ersten Position aus durch Zunahme erreichbar sein.

Jeder sortierte Bereich muss als Vorbedingung zur Anwendung des `binary_search`-Algorithmus entsprechend der gleichen Reihenfolge sortiert werden, die vom Algorithmus für die Sortierung der kombinierten Bereiche verwendet wird.

Die Quellbereiche werden von `binary_search` nicht geändert.

Die Werttypen der Forward-Iteratoren müssen weniger als vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig bestimmt werden (in dem Sinne, dass keins geringer als das Andere ist), oder dass eins geringer als das Andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen.

Die Komplexität des Algorithmus ist für Random-Access-Iteratoren logarithmisch und andernfalls linear, wobei die Anzahl von Schritten proportional zu (`last` - `first`) ist.

### <a name="example"></a>Beispiel

```cpp
// alg_bin_srch.cpp
// compile with: /EHsc
#include <list>
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    list<int> List1;

    List1.push_back( 50 );
    List1.push_back( 10 );
    List1.push_back( 30 );
    List1.push_back( 20 );
    List1.push_back( 25 );
    List1.push_back( 5 );

    List1.sort();

    cout << "List1 = ( " ;
    for ( auto Iter : List1 )
        cout << Iter << " ";
    cout << ")" << endl;

    // default binary search for 10
    if ( binary_search(List1.begin(), List1.end(), 10) )
        cout << "There is an element in list List1 with a value equal to 10."
        << endl;
    else
        cout << "There is no element in list List1 with a value equal to 10."
        << endl;

    // a binary_search under the binary predicate greater
    List1.sort(greater<int>());
    if ( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )
        cout << "There is an element in list List1 with a value greater than 10 "
        << "under greater than." << endl;
    else
        cout << "No element in list List1 with a value greater than 10 "
        << "under greater than." << endl;

    // a binary_search under the user-defined binary predicate mod_lesser
    vector<int> v1;

    for ( auto i = -2; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    sort(v1.begin(), v1.end(), mod_lesser);

    cout << "Ordered using mod_lesser, vector v1 = ( " ;
    for ( auto Iter : v1 )
        cout << Iter << " ";
    cout << ")" << endl;

    if ( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )
        cout << "There is an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
    else
        cout << "There is not an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
}
```

```Output
List1 = ( 5 10 20 25 30 50 )
There is an element in list List1 with a value equal to 10.
There is an element in list List1 with a value greater than 10 under greater than.
Ordered using mod_lesser, vector v1 = ( 0 -1 1 -2 2 3 4 )
There is an element with a value equivalent to -3 under mod_lesser.
```

## <a name="clamp"></a>gekl

Vergleicht einen Wert mit einer oberen und unteren Grenze und gibt einen Verweis auf den Wert zurück, wenn er zwischen den Begrenzungen liegt, oder einen Verweis auf die obere oder untere Grenze, wenn der Wert oberhalb oder unterhalb der Grenze liegt.

```cpp
template<class Type>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper);

template<class Type, class Compare>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*value*\
Der Wert, der mit dem *oberen* und *unteren*Wert verglichen werden soll.

*untere*\
Die untere Grenze von Werten, auf die der *Wert* fixiert werden soll.

*obere*\
Die obere Grenze von Werten, auf die der *Wert* fixiert werden soll.

*pred-* \
Ein Prädikat, das zum Vergleichen des Werts mit dem *unteren* oder *oberen* *Wert* verwendet wird. Ein Vergleichs Prädikat nimmt zwei Argumente an und gibt **true** zurück, wenn der erste Wert kleiner als der zweite ist, andernfalls **false**.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf einen *niedrigeren* Wert zurück, wenn `value < lower`, oder einen Verweis auf den *oberen* Wert, wenn `upper < value`. Andernfalls wird ein Verweis auf den *Wert*zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Das Verhalten ist nicht definiert, wenn *Upper* kleiner als *niedriger*ist.

## <a name="copy"></a>skopie

Weist die Werte von Elementen aus einem Quellbereich einem Zielbereich zu, durchläuft die Quellelementsequenz und weist ihnen vorwärts neue Positionen zu.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements im Quellbereich adressiert.

*Letzter*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im Quellbereich adressiert.

*destbeg* -\
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Element im Zielbereich adressiert, d. h., der Iterator adressiert `result` + (*Letztes* - *zuerst*).

### <a name="remarks"></a>Bemerkungen

Der Quellbereich muss gültig sein, und es muss genügend Speicherplatz am Ziel zur Verfügung stehen, um alle kopierten Elemente aufzunehmen.

Da der Algorithmus die Quell Elemente mit dem ersten Element beginnend kopiert, kann sich der Zielbereich mit dem Quellbereich überschneiden, vorausgesetzt, die *Letzte* Position des Quell Bereichs ist nicht im Zielbereich enthalten. `copy` können zum Verschieben von Elementen nach links, aber nicht nach rechts verwendet werden, es sei denn, es gibt keine Überlappung zwischen den Quell-und Zielbereichen. Verwenden Sie den [copy_backward](../standard-library/algorithm-functions.md#copy_backward)-Algorithmus, um Elemente um beliebig viele Positionen nach rechts zu verschieben.

Mit dem `copy`-Algorithmus werden nur die Werte geändert, auf die Iteratoren zeigen. Elementen im Zielbereich werden neuen Werte zugewiesen. Es können keine neuen Elemente erstellt und keine Elemente direkt in einen leeren Container eingefügt werden.

### <a name="example"></a>Beispiel

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1.push_back( 10 * i );

    int ii;
    for ( ii = 0 ; ii <= 10 ; ii++ )
        v2.push_back( 3 * ii );

    cout << "v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To copy the first 3 elements of v1 into the middle of v2
    copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );

    cout << "v2 with v1 insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To shift the elements inserted into v2 two positions
    // to the left
    copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );

    cout << "v2 with shifted insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )
```

## <a name="copy_backward"></a>copy_backward

Weist die Werte von Elementen aus einem Quellbereich einem Zielbereich zu, durchläuft die Quellelementsequenz und weist ihnen rückwärts neue Positionen zu.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein bidirektionaler Iterator, der die Position des ersten Elements im Quellbereich adressiert.

*Letzter*\
Ein bidirektionaler Iterator, der die Position hinter dem letzten Element im Quellbereich adressiert.

*DestEnd* -\
Ein bidirektionaler Iterator, der die Position hinter dem letzten Element im Zielbereich adressiert.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Element im Zielbereich adressiert, d. h., der Iterator adressiert *-(* *Letzter* - *zuerst*).

### <a name="remarks"></a>Bemerkungen

Der Quellbereich muss gültig sein, und es muss genügend Speicherplatz am Ziel zur Verfügung stehen, um alle kopierten Elemente aufzunehmen.

Der `copy_backward`-Algorithmus erzwingt strengere Anforderungen als der `copy` Algorithmus. Eingabe- und Ausgabeiteratoren von beiden müssen bidirektional sein.

Die Algorithmen `copy_backward` und [move_backward](../standard-library/algorithm-functions.md#move_backward) sind die einzigen Algorithmen der C++-Standardbibliothek, die den Ausgabebereich mit einem auf das Ende des Zielbereichs weisenden Iterator festlegen.

Da der Algorithmus die Quell Elemente mit dem letzten Element beginnend kopiert, kann sich der Zielbereich mit dem Quellbereich überschneiden, vorausgesetzt, die *erste* Position des Quell Bereichs ist nicht im Zielbereich enthalten. `copy_backward` kann verwendet werden, um Elemente nach rechts aber nicht nach links zu verschieben, es sei denn, es gibt keine Überlappung zwischen Quell und Zielbereich. Verwenden Sie den [copy](../standard-library/algorithm-functions.md#copy)-Algorithmus, um ein Element beliebig viele Positionen nach links zu verschieben.

Mit dem `copy_backward`-Algorithmus werden nur die Werte geändert, auf die Iteratoren zeigen. Elementen im Zielbereich werden neuen Werte zugewiesen. Es können keine neuen Elemente erstellt und keine Elemente direkt in einen leeren Container eingefügt werden.

### <a name="example"></a>Beispiel

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 5 ; ++i )
        v1.push_back( 10 * i );

    int ii;
    for ( ii = 0 ; ii <= 10 ; ++ii )
        v2.push_back( 3 * ii );

    cout << "v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To copy_backward the first 3 elements of v1 into the middle of v2
    copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );

    cout << "v2 with v1 insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To shift the elements inserted into v2 two positions
    // to the right
    copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );

    cout << "v2 with shifted insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 6 9 0 10 0 10 20 27 30 )
```

## <a name="copy_if"></a>copy_if

Kopiert in einem Bereich von Elementen die Elemente, die für die angegebene Bedingung **true** sind.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der den Beginn eines Bereichs angibt, der auf die Bedingung geprüft werden soll.

*Letzter*\
Ein Eingabeiterator, der das Ende des Bereichs angibt.

*dest* -\
Ein Ausgabeiterator, der das Ziel der kopierten Elemente angibt.

*pred-* \
Die Bedingung, auf die jedes Element im Bereich geprüft wird. Diese Bedingung wird von einem benutzerdefinierten Prädikatfunktionsobjekt bereitgestellt. Ein unäres Prädikat nimmt ein Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator , der für jedes Element, das die Bedingung erfüllt Anders ausgedrückt: der Rückgabewert minus *dest* gleicht der Anzahl der kopierten Elemente.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion wertet aus.

`if (pred(*first + N)) * dest++ = *(first + N))`

einmal für jedes `N` im Bereich `[0, last - first)`, für streng zunehmende Werte von `N`, beginnend mit dem niedrigsten Wert. Wenn " *dest* " und das *erste* Speicherbereich angeben, darf " *dest* " nicht im Bereich `[ first, last )`liegen.

### <a name="example"></a>Beispiel

```cpp
// alg_copy_if.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

void listlist(std::list<int> l)
{
    std::cout << "( ";
    for (auto const& el : l)
        std::cout << el << " ";
    std::cout << ")" << std::endl;
}

int main()
{
    using namespace std;
    list<int> li{ 46, 59, 88, 72, 79, 71, 60, 5, 40, 84 };
    list<int> le(li.size()); // le = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
    list<int> lo(li.size()); // lo = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    cout << "li = ";
    listlist(li);

    // is_even checks if the element is even.
    auto is_even = [](int const elem) { return !(elem % 2); };
    // use copy_if to select only even elements from li 
    // and copy them to le, starting from le's begin position
    auto ec = copy_if(li.begin(),li.end(), le.begin(), is_even);
    le.resize(std::distance(le.begin(), ec));  // shrink le to new size

    cout << "Even numbers are le = ";
    listlist(le);

    // is_odd checks if the element is odd.
    auto is_odd = [](int const elem) { return (elem % 2); };
    // use copy_if to select only odd elements from li
    // and copy them to lo, starting from lo's begin position
    auto oc = copy_if(li.begin(), li.end(), lo.begin(), is_odd);
    lo.resize(std::distance(lo.begin(), oc));  // shrink lo to new size

    cout << "Odd numbers are lo = ";
    listlist(lo);
}
```

```Output
li = ( 46 59 88 72 79 71 60 5 40 84 )
Even numbers are le = ( 46 88 72 60 40 84 )
Odd numbers are lo = ( 59 79 71 5 )
```

## <a name="copy_n"></a>copy_n

Kopiert eine angegebene Anzahl von Elementen.

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class Size, class ForwardIterator2>
ForwardIterator2 copy_n(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    Size count,
    ForwardIterator2 dest);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Eine Eingabeiterator, der angibt, von welcher Position die Elemente kopiert werden.

*Anzahl*\
Ein Ganzzahltyp mit oder ohne Vorzeichen, der die Anzahl der zu kopierenden Elemente angibt.

*dest* -\
Eine Ausgabeiterator, der angibt, wohin die Elemente kopiert werden.

### <a name="return-value"></a>Rückgabewert

Gibt einen Ausgabeiterator zurück, in den Elemente kopiert wurden. Dies entspricht dem zurückgegebenen Wert des *dest* -Parameters.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion wertet `*(dest + N) = *(first + N))` einmal für jede `N` im Bereich `[0, count)`aus, um genau höhere Werte `N` zu erhalten, die mit dem niedrigsten Wert beginnen. Dann wird `dest + N` zurückgegeben. Wenn " *dest* " und das *erste* Speicherbereich angeben, darf " *dest* " nicht im Bereich `[first, last)`liegen.

### <a name="example"></a>Beispiel

```cpp
// alg_copy_n.cpp
// compile with: cl /EHsc /W4 alg_copy_n.cpp
#include <algorithm>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    string s1{"dandelion"};
    string s2{"badger"};

    cout << s1 << " + " << s2 << " = ";

    // Copy the first 3 letters from s1
    // to the first 3 positions in s2
    copy_n(s1.begin(), 3, s2.begin());

    cout << s2 << endl;
}
```

```Output
dandelion + badger = danger
```

## <a name="count"></a>Countdown

Gibt die Anzahl von Elementen in einem Bereich zurück, dessen Werte mit einem angegebenen Wert übereinstimmen.

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
typename iterator_traits<ForwardIterator>::difference_type
count(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*value*\
Der Wert der zu zählenden Elemente.

### <a name="return-value"></a>Rückgabewert

Der Unterschiedstyp der `InputIterator`, die die Anzahl der Elemente im Bereich [*First*, *Last*] mit dem Wert *Wert*zählt.

### <a name="remarks"></a>Bemerkungen

Der zur Bestimmung des Gleichheitszustands zwischen einem Element und dem angegebenen Wert verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Dieser Algorithmus wird so generalisiert, dass er Elemente zählt, die das Prädikat der Vorlagenfunktion [count_if](../standard-library/algorithm-functions.md#count_if) erfüllen.

### <a name="example"></a>Beispiel

```cpp
// alg_count.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result;
    result = count(v1.begin(), v1.end(), 10);
    cout << "The number of 10s in v2 is: " << result << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of 10s in v2 is: 3.
```

## <a name="count_if"></a>count_if

Gibt die Anzahl von Elementen in einem Bereich zurück, dessen Werte eine angegebene Bedingung erfüllen.

```cpp
template<class InputIterator, class UnaryPredicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
typename iterator_traits<ForwardIterator>::difference_type
count_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die Bedingung definiert, die erfüllt werden muss, wenn ein Element gezählt werden soll. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen, die die vom Prädikat angegebenen Bedingungen erfüllen.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion ist eine Generalisierung des Algorithmus [count](../standard-library/algorithm-functions.md#count) und ersetzt das Prädikat „entspricht einem bestimmten Wert“ durch ein beliebiges Prädikat.

### <a name="example"></a>Beispiel

```cpp
// alg_count_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater10(int value)
{
    return value > 10;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greater10);
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of elements in v1 greater than 10 is: 2.
```

## <a name="equal"></a>hoch

Vergleicht zwei Bereiche elementweise auf Gleichheit oder Äquivalenz in dem durch ein binäres Prädikat angegebenen Sinn.

Verwenden Sie `std::equal` beim Vergleichen von Elementen in verschiedenen Containertypen (z.B. `vector` und `list`), beim Vergleichen von verschiedenen Elementtypen oder wenn Teilbereiche von Containern verglichen werden sollen. Ansonsten verwenden Sie den Nicht-Member `operator==` beim Vergleichen von Elementen des gleichen Typen im gleichen Containertypen.

Verwenden Sie die Überladungen mit zwei Bereichen im C++14-Code, da die Überladungen, die nur einen einzigen Iterator für den zweiten Bereich nutzen, keine Unterschiede erkennen, wenn der zweite Bereich länger als der erste Bereich ist. Darüber hinaus führt dies zu einem nicht definierten Verhalten, wenn der zweite Bereich kürzer als der erste Bereich ist.

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten zu testenden Bereich adressiert.

*Last1*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im ersten zu testenden Bereich adressiert.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten zu testenden Bereich adressiert.

*Last2*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zweiten zu testenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die zu erfüllende Bedingung definiert, wenn zwei Elemente als gleichwertig akzeptiert werden. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Bereiche unter dem binären Prädikat beim Vergleichen von Elementen identisch oder ähnlich sind; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der zu durchsuchende Bereich muss gültig sein. Alle Iteratoren müssen dereferenzierbar sein, und die letzte Position ist von der Ersten durch Zunahme erreichbar.

Wenn die beiden Bereich die gleiche Länge aufweisen, ist die Zeitkomplexität des Algorithmus linear zur Anzahl der im Bereich enthaltenen Elemente. Andernfalls gibt die Funktion sofort **false**zurück.

Weder das `operator==` noch das benutzerdefinierte Prädikat ist erforderlich, um eine Äquivalenzbeziehung vorzugeben, die zwischen den dazugehörigen Operanden symmetrisch, reflexiv und transitiv ist.

### <a name="example"></a>Beispiel

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };

    // Using range-and-a-half equal:
    bool b = equal(v1.begin(), v1.end(), v2.begin());
    cout << "v1 and v2 are equal: "
       << b << endl; // true, as expected

    b = equal(v1.begin(), v1.end(), v3.begin());
    cout << "v1 and v3 are equal: "
       << b << endl; // true, surprisingly

    // Using dual-range equal:
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());
    cout << "v1 and v3 are equal with dual-range overload: "
       << b << endl; // false

    return 0;
}
```

## <a name="equal_range"></a>equal_range

Bei einem sortierten Bereich wird der Unterbereich gesucht, in dem alle Elemente einem angegebenen Wert entsprechen.

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*value*\
Der Wert, nach dem im sortierten Bereich gesucht wird.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt bei **Erfüllung true** zurück und **false** , wenn es nicht erfüllt wird.

### <a name="return-value"></a>Rückgabewert

Ein paar von Forward-Iteratoren, die einen Unterbereich angeben, der in dem durchsuchten Bereich enthalten ist, in dem alle Elemente dem *Wert* in dem vom verwendeten binären Prädikat definierten Sinn entsprechen (entweder *pred* oder der Standardwert, kleiner als).

Wenn keine Elemente im Bereich dem *Wert*entsprechen, sind die Forward-Iteratoren im zurückgegebenen Paar gleich und geben den Punkt an, an dem der *Wert* eingefügt werden kann, ohne die Reihenfolge des Bereichs zu beeinträchtigen.

### <a name="remarks"></a>Bemerkungen

Der erste Iterator des vom Algorithmus zurückgegebenen Paars ist [lower_bound](../standard-library/algorithm-functions.md#lower_bound), der zweite Iterator ist [upper_bound](../standard-library/algorithm-functions.md#upper_bound).

Der Bereich muss dem für `equal_range` bereitgestellten Prädikat entsprechend sortiert werden. Wenn Sie z. B: das Prädikat "größer als" verwenden, muss der Bereich in absteigender Reihenfolge sortiert werden.

Elemente im möglicherweise leeren Unterbereich, der durch das Iteratorpaar definiert wird, das von `equal_range` zurückgegeben wird, entsprechen dem *Wert* in dem vom verwendeten Prädikat definierten Sinn.

Die Komplexität des Algorithmus ist für Random-Access-Iteratoren logarithmisch und andernfalls linear, wobei die Anzahl von Schritten proportional zu (*Letztes* - *zuerst*) ist.

### <a name="example"></a>Beispiel

```cpp
// alg_equal_range.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>()
#include <iostream>
#include <string>
using namespace std;

template<class T> void dump_vector( const vector<T>& v, pair<typename vector<T>::iterator, typename vector<T>::iterator> range )
{
    // prints vector v with range delimited by [ and ]

    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        if ( i == range.first )
        {
            cout << "[ ";
        }
        if ( i == range.second )
        {
            cout << "] ";
        }

        cout << *i << " ";
    }
    cout << endl;
}

template<class T> void equal_range_demo( const vector<T>& original_vector, T value )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end() );
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';
    for ( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<vector<T>::iterator, vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T value, F pred, string predname )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end(), pred );
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';
    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<typename vector<T>::iterator, typename vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value, pred );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

// Return whether absolute value of elem1 is less than absolute value of elem2
bool abs_lesser( int elem1, int elem2 )
{
    return abs(elem1) < abs(elem2);
}

// Return whether string l is shorter than string r
bool shorter_than(const string& l, const string& r)
{
    return l.size() < r.size();
}

int main()
{
    vector<int> v1;

    // Constructing vector v1 with default less than ordering
    for ( int i = -1; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    for ( int i =-3; i <= 0; ++i )
    {
        v1.push_back( i );
    }

    equal_range_demo( v1, 3 );
    equal_range_demo( v1, 3, greater<int>(), "greater" );
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );

    vector<string> v2;

    v2.push_back("cute");
    v2.push_back("fluffy");
    v2.push_back("kittens");
    v2.push_back("fun");
    v2.push_back("meowmeowmeow");
    v2.push_back("blah");

    equal_range_demo<string>( v2, "fred" );
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );
}
```

## <a name="fill"></a>erfüllen

Weist den gleichen neuen Wert jedem Element in einem angegebenen Bereich zu.

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void fill(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Forward-Iterator, der die Position direkt hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*value*\
Der Wert, der Elementen im Bereich [*First*, *Last*] zugewiesen werden soll.

### <a name="remarks"></a>Bemerkungen

Der Zielbereich muss gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position ist von der Ersten durch Zunahme erreichbar. Die Komplexität ist mit der Größe des Bereichs linear.

### <a name="example"></a>Beispiel

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Fill the last 5 positions with a value of 2
    fill( v1.begin( ) + 5, v1.end( ), 2 );

    cout << "Modified v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )
```

## <a name="fill_n"></a>fill_n

Weist einer angegebenen Anzahl von Elementen in einem Bereich, der mit einem bestimmten Element beginnt, einen neuen Wert zu.

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator first,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator fill_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    const Type& value);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Ausgabeiterator, der die Position des ersten Elements im Bereich adressiert, dem der *Wert Wert zugewiesen werden soll.*

*Anzahl*\
Ein Ganzzahltyp mit oder ohne Vorzeichen, der die Anzahl der dem Wert zuzuweisenden Elemente angibt.

*value*\
Der Wert, der Elementen im Bereich [*First*, *First + count*) zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Iterator für das Element, das dem letzten ausgefüllten Element folgt, wenn *count* > 0 (null) ist, andernfalls das erste Element.

### <a name="remarks"></a>Bemerkungen

Der Zielbereich muss gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position ist von der Ersten durch Zunahme erreichbar. Die Komplexität ist mit der Größe des Bereichs linear.

### <a name="example"></a>Beispiel

```cpp
// alg_fill_n.cpp
// compile using /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << " vector v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the first 3 positions with a value of 1, saving position.
    auto pos = fill_n( v.begin(), 3, 1 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the next 3 positions with a value of 2, using last position.
    fill_n( pos, 3, 2 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the last 3 positions with a value of 3, using relative math.
    fill_n( v.end()-3, 3, 3 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;
}
```

## <a name="find"></a>sich

Sucht die Position des ersten Vorkommens eines Elements in einem Bereich, der einen angegebenen Wert enthält.

```cpp
template<class InputIterator, class Type>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements im nach dem angegebenen Wert zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Eingabeiterator, der die Position eine Stelle hinter dem letzten Element im nach dem angegebenen Wert zu durchsuchenden Bereich adressiert.

*value*\
Der zu suchende Wert.

### <a name="return-value"></a>Rückgabewert

Ein Eingabeiterator, der das erste Vorkommen des angegebenen Werts im zu durchsuchenden Bereich adressiert. Wenn kein Element mit einem äquivalenten Wert gefunden wird, wird *zuletzt*zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Der zur Bestimmung des Gleichheitszustands zwischen einem Element und dem angegebenen Wert verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Ein Codebeispiel mit `find()` finden Sie unter [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="find_end"></a>find_end

Sucht in einem Bereich nach der letzten Untersequenz, die mit einer angegebenen Sequenz identisch ist oder die in durch ein binäres Prädikat angegebenen Sinne äquivalent ist.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Pred pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*First1*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Last1*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*First2*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Last2*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die zu erfüllende Bedingung definiert, wenn zwei Elemente als gleichwertig akzeptiert werden. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

Ein forward-Iterator, der die Position des ersten Elements der letzten unter Sequenz in [First1, Last1) adressiert, die der angegebenen Sequenz [First2, Last2) entspricht.

### <a name="remarks"></a>Bemerkungen

Der zur Bestimmung des Gleichheitszustands zwischen einem Element und dem angegebenen Wert verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Bereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

### <a name="example"></a>Beispiel

```cpp
// alg_find_end.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for a match to L1 under identity
    vector<int>::iterator result1;
    result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a match of L1 in v1 that begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent to those\n in v2 under the binary "
            << "predicate twice and that begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 5 10 15 20 )
Vector v2 = ( 20 30 40 )
There is a match of L1 in v1 that begins at position 7.
There is a sequence of elements in v1 that are equivalent to those
in v2 under the binary predicate twice and that begins at position 8.
```

## <a name="find_first_of"></a>find_first_of

Sucht das erste Vorkommen mehrerer Werte innerhalb eines Zielbereichs oder das erste Vorkommen mehrerer Elemente, die wie durch ein binäres Prädikat angegeben mit einem angegebenen Satz der Elemente äquivalent sind.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*First1*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Last1*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*First2*\
Ein Forward-Iterator, der die Position des ersten Elements im abzugleichenden Bereich adressiert.

*Last2*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im abzugleichenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die zu erfüllende Bedingung definiert, wenn zwei Elemente als gleichwertig akzeptiert werden. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator, der die Position des ersten Elements der ersten Untersequenz adressiert, die der angegebenen Sequenz entspricht oder die wie von einem binären Prädikat angegeben äquivalent ist.

### <a name="remarks"></a>Bemerkungen

Der zur Bestimmung des Gleichheitszustands zwischen einem Element und dem angegebenen Wert verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Bereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

### <a name="example"></a>Beispiel

```cpp
// alg_find_first_of.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 3 ; ii <= 4 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for first match to L1 under identity
    vector<int>::iterator result1;
    result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent\n to those in v2 under the binary "
            << "predicate twice\n and the first one begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 15 20 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 3.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="find_if"></a>find_if

Sucht die Position des ersten Vorkommens eines Elements in einem Bereich, der eine bestimmte Bedingung erfüllt.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt oder [Lambdaausdruck](../cpp/lambda-expressions-in-cpp.md), das bzw. der die Bedingung definiert, die vom zu suchenden Element erfüllt wird. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt bei **Erfüllung true** zurück, oder **false** , wenn es nicht erfüllt wird. Die Signatur von *pred* muss effektiv `bool pred(const T& arg);`sein, wobei `T` ein Typ ist, zu dem `InputIterator` bei Dereferenzierung implizit konvertiert werden kann. Das Schlüsselwort " **Konstanten** " wird nur angezeigt, um zu veranschaulichen, dass das Funktions Objekt oder Lambda das Argument nicht ändern sollte.

### <a name="return-value"></a>Rückgabewert

Ein eingabeiterator, der auf das erste Element im Bereich verweist, das die vom Prädikat angegebene Bedingung erfüllt (das Prädikat ergibt **true**). Wenn kein Element gefunden wird, das das Prädikat erfüllt, wird der Wert von zurück *gegeben.*

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion ist eine Generalisierung des Algorithmus [find](../standard-library/algorithm-functions.md#find) und ersetzt das Prädikat „entspricht einem bestimmten Wert“ durch ein beliebiges Prädikat. Das logische Gegenstück (Suchen des ersten Elements, das das Prädikat nicht erfüllt) finden Sie unter [find_if_not](../standard-library/algorithm-functions.md#find_if_not).

### <a name="example"></a>Beispiel

```cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <vector>
#include <algorithm>
#include <iostream>
#include <string>

using namespace std;

template <typename S> void print(const S& s) {
for (const auto& p : s) {
        cout << "(" << p << ") ";
    }
    cout << endl;
}

// Test std::find()
template <class InputIterator, class T>
void find_print_result(InputIterator first, InputIterator last, const T& value) {

    // call <algorithm> std::find()
    auto p = find(first, last, value);

    cout << "value " << value;
    if (p == last) {
        cout << " not found." << endl;
    } else {
        cout << " found." << endl;
    }
}

// Test std::find_if()
template <class InputIterator, class Predicate>
void find_if_print_result(InputIterator first, InputIterator last,
    Predicate Pred, const string& Str) {

    // call <algorithm> std::find_if()
    auto p = find_if(first, last, Pred);

    if (p == last) {
        cout << Str << " not found." << endl;
    } else {
        cout << "first " << Str << " found: " << *p << endl;
    }
}

// Function to use as the UnaryPredicate argument to find_if() in this example
bool is_odd_int(int i) {
    return ((i % 2) != 0);
}

int main()
{
    // Test using a plain old array.
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    cout << "array x[] contents: ";
    print(x);
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.
    cout << "Test std::find() with array..." << endl;
    find_print_result(begin(x), end(x), 10);
    find_print_result(begin(x), end(x), 42);
    cout << "Test std::find_if() with array..." << endl;
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name
    find_if_print_result(begin(x), end(x), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");

    // Test using a vector.
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back((i + 1) * 10);
    }
    cout << endl << "vector v contents: ";
    print(v);
    cout << "Test std::find() with vector..." << endl;
    find_print_result(v.begin(), v.end(), 20);
    find_print_result(v.begin(), v.end(), 12);
    cout << "Test std::find_if() with vector..." << endl;
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");
    find_if_print_result(v.begin(), v.end(), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");
}
```

## <a name="find_if_not"></a>find_if_not

Gibt das erste Element im angegebenen Bereich zurück, der eine Bedingung nicht erfüllt.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if_not(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt oder [Lambdaausdruck](../cpp/lambda-expressions-in-cpp.md), das bzw. der die Bedingung definiert, die nicht vom zu suchenden Element erfüllt wird. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt bei **Erfüllung true** zurück, oder **false** , wenn es nicht erfüllt wird. Die Signatur von *pred* muss effektiv `bool pred(const T& arg);`sein, wobei `T` ein Typ ist, zu dem `InputIterator` bei Dereferenzierung implizit konvertiert werden kann. Das Schlüsselwort " **Konstanten** " wird nur angezeigt, um zu veranschaulichen, dass das Funktions Objekt oder Lambda das Argument nicht ändern sollte.

### <a name="return-value"></a>Rückgabewert

Ein eingabeiterator, der auf das erste Element im Bereich verweist, das die vom Prädikat angegebene Bedingung nicht erfüllt (das Prädikat ergibt **false**). Wenn alle Elemente das Prädikat erfüllen (das Prädikat ergibt für jedes Element **true** ), gibt den *letzten*zurück.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion ist eine Generalisierung des Algorithmus [find](../standard-library/algorithm-functions.md#find) und ersetzt das Prädikat „entspricht einem bestimmten Wert“ durch ein beliebiges Prädikat. Das logische Gegenstück (Suchen des ersten Elements, das das Prädikat erfüllt) finden Sie unter [find_if](../standard-library/algorithm-functions.md#find_if).

Ein Codebeispiel, das problemlos für `find_if_not()` angepasst werden kann, finden Sie unter [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each"></a>for_each

Wendet ein angegebenes Funktionsobjekt auf jedes Element in einer Vorwärtsreihenfolge innerhalb eines Bereichs an und gibt das Funktionsobjekt zurück.

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);

template<class ExecutionPolicy, class ForwardIterator, class Function>
void for_each(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Function func);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements im zu verarbeitenden Bereich adressiert.

*Letzter*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zu verarbeitenden Bereich adressiert.

*Func* -\
Ein benutzerdefiniertes Funktionsobjekt, das auf jedes Element im Bereich angewendet wird.

### <a name="return-value"></a>Rückgabewert

Eine Kopie des Funktionsobjekts, nachdem es auf alle Elemente im Bereich angewendet wurde.

### <a name="remarks"></a>Bemerkungen

Der Algorithmus `for_each` ist hoch flexibel, sodass die benutzerdefinierte Änderung jedes einzelnen Elements eines Bereichs möglich sind. Vorlagenbasierte Funktionen, die möglicherweise in veränderter Form erneut verwendet werden, indem sie unterschiedliche Parameter erfüllen. Benutzerdefinierte Funktionen sammeln möglicherweise Informationen innerhalb eines internen Zustands, die der Algorithmus möglicherweise zurückgibt, nachdem er alle Elemente im Bereich verarbeitet hat.

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb der Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Die Komplexität ist linear mit höchstens (*Last* - *First*)-vergleichen.

### <a name="example"></a>Beispiel

```cpp
// alg_for_each.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
    Type Factor;   // The value to multiply by
public:
    // Constructor initializes the value to multiply by
    MultValue ( const Type& value ) : Factor ( value ) {
    }

    // The function call for the element to be multiplied
    void operator( ) ( Type& elem ) const
    {
        elem *= Factor;
    }
};

// The function object to determine the average
class Average
{
private:
    long num;      // The number of elements
    long sum;      // The sum of the elements
public:
    // Constructor initializes the value to multiply by
    Average( ) : num ( 0 ) , sum ( 0 )
    {
    }

    // The function call to process the next elment
    void operator( ) ( int elem )
    {
        num++;      // Increment the element count
        sum += elem;   // Add the value to the partial sum
    }

    // return Average
    operator double( )
    {
        return static_cast<double> (sum) /
            static_cast<double> (num);
    }
};

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using for_each to multiply each element by a Factor
    for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

    cout << "Multiplying the elements of the vector v1\n "
            << "by the factor -2 gives:\n v1mod1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The function object is templatized and so can be
    // used again on the elements with a different Factor
    for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 gives:\n v1mod2 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The local state of a function object can accumulate
    // information about a sequence of actions that the
    // return value can make available, here the Average
    double avemod2 = for_each ( v1.begin( ), v1.end( ),
        Average( ) );
    cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "
            << avemod2 << "." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="for_each_n"></a>for_each_n

```cpp
template<class InputIterator, class Size, class Function>
InputIterator for_each_n(
    InputIterator first,
    Size n,
    Function f);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Function>
ForwardIterator for_each_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size n,
    Function f);
```

## <a name="generate"></a>verursachen

Weist die Werte, die von einem Funktionsobjekt generiert werden, jedem Element in einem Bereich zu.

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Generator>
void generate(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    Generator gen);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im Bereich, dem Werte zugeordnet werden, adressiert.

*Letzter*\
Ein Forward-Iterator, der die Position des ersten Elements direkt hinter dem letzten Element im Bereich, dem Werte zugeordnet werden, adressiert.

*gen* -\
Ein Funktionsobjekt, das ohne Argumente aufgerufen und verwendet wird, um die Werte zu generieren, die jedem der Elemente im Bereich zugeordnet werden sollen.

### <a name="remarks"></a>Bemerkungen

Das Funktionsobjekt wird jedem Element im Bereich zugeordnet und muss nicht bei jedem Aufruf denselben Wert zurückgeben. Es kann z, B. aus einer Datei lesen oder auf einen lokalen Zustand verweisen und diesen ändern. Der Ergebnistyp des Generators muss in den Wertetyp des Vorwärtsiterators für den Bereich konvertierbar sein.

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb der Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Die Komplexität ist linear, wobei genau (`last` - `first`) Aufrufe des Generators erforderlich sind.

### <a name="example"></a>Beispiel

```cpp
// alg_generate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

int main()
{
    using namespace std;

    // Assigning random values to vector integer elements
    vector<int> v1 ( 5 );
    vector<int>::iterator Iter1;
    deque<int> deq1 ( 5 );
    deque<int>::iterator d1_Iter;

    generate ( v1.begin( ), v1.end( ), rand );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Assigning random values to deque integer elements
    generate ( deq1.begin( ), deq1.end( ), rand );

    cout << "Deque deq1 is ( " ;
    for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )
        cout << *d1_Iter << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 41 18467 6334 26500 19169 ).
Deque deq1 is ( 15724 11478 29358 26962 24464 ).
```

## <a name="generate_n"></a>generate_n

Weist die Werte, die von einem Funktionsobjekt generiert werden, einer angegebenen Anzahl von Elementen eines Bereichs zu und kehrt zu der Position zurück, die direkt nach dem letzten zugewiesenen Wert liegt.

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator first,
    Diff count,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Generator>
ForwardIterator generate_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    Generator gen);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Ausgabeiterator für die Position des ersten Elements im Bereich, dem Werte zugeordnet werden.

*Anzahl*\
Ein Ganzzahltyp mit oder ohne Vorzeichen, der die Anzahl der dem Wert durch die Generatorfunktion zuzuweisenden Elemente angibt.

*gen* -\
Ein Funktionsobjekt, das ohne Argumente aufgerufen und verwendet wird, um die Werte zu generieren, die jedem der Elemente im Bereich zugeordnet werden sollen.

### <a name="remarks"></a>Bemerkungen

Das Funktionsobjekt wird jedem Element im Bereich zugeordnet und muss nicht bei jedem Aufruf denselben Wert zurückgeben. Es kann z, B. aus einer Datei lesen oder auf einen lokalen Zustand verweisen und diesen ändern. Der Ergebnistyp des Generators muss in den Wertetyp des Vorwärtsiterators für den Bereich konvertierbar sein.

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb der Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Die Komplexität ist linear, wobei exakt `count` Aufrufe des Generators erforderlich sind.

### <a name="example"></a>Beispiel

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <deque>
#include <iostream>
#include <string>
#include <algorithm>
#include <random>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const int elemcount = 5;
    vector<int> v(elemcount);
    deque<int> dq(elemcount);

    // Set up random number distribution
    random_device rd;
    mt19937 engine(rd());
    uniform_int_distribution<int> dist(-9, 9);

    // Call generate_n, using a lambda for the third parameter
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });
    print("vector v is: ", v);

    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });
    print("deque dq is: ", dq);
}
```

## <a name="includes"></a>schließt

Testet, ob ein sortierter Bereich alle Elemente enthält, die in einem zweiten sortierten Bereich enthalten sind, wobei das Sortier- oder Äquivalenzkriterium für die Elemente durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class Compare>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten der beiden sortierten Quellbereiche adressiert, die darauf geprüft werden, ob alle Elemente des zweiten Bereichs auch im ersten Bereich enthalten sind.

*Last1*\
Ein Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im ersten der beiden sortierten Quellbereiche adressiert, die darauf geprüft werden, ob alle Elemente des zweiten Bereichs auch im ersten Bereich enthalten sind.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die darauf geprüft werden, ob alle Elemente des zweiten Bereichs auch im ersten Bereich enthalten sind.

*Last2*\
Ein Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die darauf geprüft werden, ob alle Elemente des zweiten Bereichs auch im ersten Bereich enthalten sind.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt bei **Erfüllung true** zurück und **false** , wenn es nicht erfüllt wird.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn der erste sortierte Bereich alle Elemente des zweiten Bereichs enthält; ansonsten **FALSE**.

### <a name="remarks"></a>Bemerkungen

Anders ausgedrückt bedeutet dies, dass dieser Test feststellt, ob der zweite Quellbereich eine Teilmenge des ersten Quellbereichs ist.

Die sortierten Quellbereiche, auf die verwiesen wird, müssen gültig sein; alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb jeder Sequenz muss von der ersten Position durch Zunahme erreichbar sein.

Die sortierten Quellbereiche müssen als Vorbedingung zur Anwendung des Algorithmus entsprechend der gleichen Reihenfolge sortiert werden, die vom Algorithmus für die Sortierung der kombinierten Bereiche verwendet wird.

Die Quellbereiche werden nicht durch den Algorithmus `merge`geändert.

Die Werttypen der Eingabeiteratoren müssen mit „kleiner als“ vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig (in dem Sinne, dass keines kleiner als das andere ist) oder eines als kleiner als das andere bestimmt werden können. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Dies bedeutet, dass der Algorithmus überprüft, ob alle Elemente im an erster Stelle aufgelisteten Bereich unter einem angegebenen binären Prädikat genauso wie die Elemente des an zweiter Stelle aufgelisteten Bereichs sortiert sind.

Die Komplexität des Algorithmus ist bei höchstens `2 * ((last1 - first1) - (last2 - first2)) - 1` vergleichen für nicht leere Quellbereiche linear.

### <a name="example"></a>Beispiel

```cpp
// alg_includes.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b;
    vector<int>::iterator Iter1a, Iter1b;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -2 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-2 ; ii <= 3 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b );
    vector<int>::iterator Iter2a, Iter2b;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
    v2a.pop_back( );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) ;
    vector<int>::iterator Iter3a, Iter3b;
    reverse (v3a.begin( ), v3a.end( ) );
    v3a.pop_back( );
    v3a.pop_back( );
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To test for inclusion under an asscending order
    // with the default binary predicate less<int>( )
    bool Result1;
    Result1 = includes ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ) );
    if ( Result1 )
        cout << "All the elements in vector v1b are "
            << "contained in vector v1a." << endl;
    else
        cout << "At least one of the elements in vector v1b "
            << "is not contained in vector v1a." << endl;

    // To test for inclusion under descending
    // order specify binary predicate greater<int>( )
    bool Result2;
    Result2 = includes ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ), greater<int>( ) );
    if ( Result2 )
        cout << "All the elements in vector v2b are "
            << "contained in vector v2a." << endl;
    else
        cout << "At least one of the elements in vector v2b "
            << "is not contained in vector v2a." << endl;

    // To test for inclusion under a user
    // defined binary predicate mod_lesser
    bool Result3;
    Result3 = includes ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), mod_lesser );
    if ( Result3 )
        cout << "All the elements in vector v3b are "
            << "contained under mod_lesser in vector v3a."
            << endl;
    else
        cout << "At least one of the elements in vector v3b is "
            << " not contained under mod_lesser in vector v3a."
            << endl;
}
```

```Output
Original vector v1a with range sorted by the
binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).
Original vector v1b with range sorted by the
binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).
Original vector v2a with range sorted by the
binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).
Original vector v2b with range sorted by the
binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).
Original vector v3a with range sorted by the
binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).
Original vector v3b with range sorted by the
binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).
All the elements in vector v1b are contained in vector v1a.
At least one of the elements in vector v2b is not contained in vector v2a.
At least one of the elements in vector v3b is not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a>inplace_merge

Kombiniert die Elemente von zwei aufeinander folgenden sortierten Bereichen in einen einzelnen sortierten Bereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Compare>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);

template<class ExecutionPolicy, class BidirectionalIterator>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator, class Compare>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein bidirektionaler Eingabeiterator, der die Position des ersten Elements im ersten der beiden nacheinander sortierten Bereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen.

*mittlere*\
Ein bidirektionaler Eingabeiterator, der die Position des ersten Elements im zweiten der beiden nacheinander sortierten Bereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen.

*Letzter*\
Ein bidirektionaler Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im zweiten der beiden nacheinander sortierten Bereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das Vergleichs Prädikat übernimmt zwei Argumente und sollte **true** zurückgeben, wenn das erste Element kleiner als das zweite Element ist, andernfalls **false** .

### <a name="remarks"></a>Bemerkungen

Die sortierten aufeinanderfolgenden Quellbereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb jeder Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Die sortierten aufeinanderfolgenden Bereiche müssen als Vorbedingung zur Anwendung des `inplace_merge`-Algorithmus entsprechend der gleichen Reihenfolge sortiert werden, die vom Algorithmus für die Sortierung der kombinierten Bereiche verwendet wird. Der Vorgang ist stabil, da die relative Reihenfolge der Elemente innerhalb jedes Bereichs beibehalten wird. Wenn in beiden Quellbereichen äquivalente Elemente vorhanden sind, stehen im kombinierten Bereich das Element aus dem ersten Bereich vor dem Element aus dem zweiten Bereich.

Die Komplexität hängt davon ab, wie viel Speicher verfügbar ist, während der Algorithmus dem temporären Puffer Speicher zuweist. Wenn genügend Arbeitsspeicher verfügbar ist, ist der beste Fall mit `(last - first) - 1` vergleichen linear; Wenn kein Zusatz Speicher verfügbar ist, ist der schlechteste Fall `N log(N)`, wobei *N* = *zuletzt* -  *.*

### <a name="example"></a>Beispiel

```cpp
// alg_inplace_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      //For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, Iter3;

    // Constructing vector v1 with default less-than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
    {
        v1.push_back( ii );
    }

    cout << "Original vector v1 with subranges sorted by the\n "
            << "binary predicate less than is v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2 ( v1 );
    vector<int>::iterator break2;
    break2 = find ( v2.begin( ), v2.end( ), -5 );
    sort ( v2.begin( ), break2 , greater<int>( ) );
    sort ( break2 , v2.end( ), greater<int>( ) );
    cout << "Original vector v2 with subranges sorted by the\n "
            << "binary predicate greater is v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3 ( v1 );
    vector<int>::iterator break3;
    break3 = find ( v3.begin( ), v3.end( ), -5 );
    sort ( v3.begin( ), break3 , mod_lesser );
    sort ( break3 , v3.end( ), mod_lesser );
    cout << "Original vector v3 with subranges sorted by the\n "
            << "binary predicate mod_lesser is v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;

    vector<int>::iterator break1;
    break1 = find (v1.begin( ), v1.end( ), -5 );
    inplace_merge ( v1.begin( ), break1, v1.end( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Applying a user defined (UD) binary predicate mod_lesser
    inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 with subranges sorted by the
binary predicate less than is v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
Original vector v2 with subranges sorted by the
binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Original vector v3 with subranges sorted by the
binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )
Merged inplace with default order,
vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )
Merged inplace with binary predicate greater specified,
vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Merged inplace with binary predicate mod_lesser specified,
vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )
```

## <a name="is_heap"></a>is_heap

Gibt **true** zurück, wenn die Elemente im angegebenen Bereich einen Heap bilden.

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein zufälliger direkter Iterator, der den Beginn eines Bereichs angibt, der auf einen Heap geprüft werden soll.

*Letzter*\
Ein zufälliger direkter Iterator, der das Ende des Bereichs angibt.

*pred-* \
Eine zu prüfende Bedingung, um Elemente zu sortieren. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Gibt **true** zurück, wenn die Elemente im angegebenen Bereich einen Heap bilden, andernfalls **false** .

### <a name="remarks"></a>Bemerkungen

Die erste Vorlagen Funktion gibt [is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)`(first , last) == last`zurück.

Die zweite Vorlagen Funktion gibt zurück.

[https://login.microsoftonline.com/consumers/](`is_heap_until(first, last, pred) == last`).

## <a name="is_heap_until"></a>is_heap_until

Gibt einen Iterator zurück, der am ersten Element im Bereich [`first`, `last`) positioniert ist, der die Heap sortierungsbedingung nicht erfüllt, oder *endet* , wenn der Bereich einen Heap bildet.

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Iterator mit wahlfreiem Zugriff, der das erste Element eines Bereichs angibt, um nach einem Heap zu suchen.

*Letzter*\
Ein Iterator mit wahlfreiem Zugriff, der das Ende des Bereichs angibt, um nach einem Heap zu suchen.

*pred-* \
Ein binäres Prädikat, das die Bedingung der strengen schwachen Sortierung angibt, die einen Heap definiert. Das Standard Prädikat wird `std::less<>`, wenn *pred* nicht angegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt den *letzten* zurück, wenn der angegebene Bereich einen Heap bildet oder ein oder weniger Elemente enthält. Gibt andernfalls einen Iterator für das erste Elemente zurück, das die Heap-Bedingung nicht erfüllt.

### <a name="remarks"></a>Bemerkungen

Die erste Vorlagen Funktion gibt den letzten Iterator `next` in `[first, last)` zurück, wobei `[first, next)` ein Heap ist, der vom Funktions Objekt `std::less<>`geordnet ist. Wenn die Entfernungs `last - first` kleiner als 2 ist, gibt die Funktion *Last*zurück.

Die zweite Vorlagen Funktion verhält sich wie die erste, mit der Ausnahme, dass Sie das Prädikat *präd* anstelle von `std::less<>` als Heap Anordnungs Bedingung verwendet.

## <a name="is_partitioned"></a>is_partitioned

Gibt **true** zurück, wenn alle Elemente im angegebenen Bereich, die für eine Bedingung **true** testen, vor allen Elementen stehen, die **false**testen.

```cpp
template<class InputIterator, class UnaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool is_partitioned(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der den Beginn des Bereichs angibt, ab wo nach Bedingungen gesucht werden soll.

*Letzter*\
Ein Eingabeiterator, der das Ende eines Bereichs angibt.

*pred-* \
Eine Bedingung, auf die geprüft werden soll. Dies wird von einem benutzerdefinierten Prädikatfunktionsobjekt bereitgestellt, das bzw. der die Bedingung definiert, die vom zu suchenden Element erfüllt wird. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Gibt **true** zurück, wenn alle Elemente im angegebenen Bereich, die für eine Bedingung **true** testen, vor allen Elementen stehen, die **false**testen; andernfalls wird **false**zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt nur **dann true** zurück, wenn alle Elemente in `[first, last)` durch *pred*partitioniert sind. Das heißt, alle Elemente, die in `[first, last)` `X`, für die `pred (X)` true ist, treten vor allen Elementen `Y`, für die `pred (Y)` **false**ist.

## <a name="is_permutation"></a>is_permutation

Gibt „true“ zurück, wenn beide Bereiche dieselben Elemente enthalten, und zwar unabhängig davon, ob sich die Elemente in derselben Reihenfolge befinden. Verwenden Sie die Überladungen mit zwei Bereichen im C++14-Code, da die Überladungen, die nur einen einzigen Iterator für den zweiten Bereich nutzen, keine Unterschiede erkennen, wenn der zweite Bereich länger als der erste Bereich ist. Darüber hinaus führt dies zu einem nicht definierten Verhalten, wenn der zweite Bereich kürzer als der erste Bereich ist.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*First1*\
Ein forward-Iterator, der auf das erste Element des Bereichs verweist.

*Last1*\
Ein forward-Iterator, der auf eine Stelle hinter dem letzten Element des Bereichs verweist.

*First2*\
Ein forward-Iterator, der für den Vergleich auf das erste Element eines zweiten Bereichs verweist.

*Last2*\
Ein forward-Iterator, der für den Vergleich auf eine Stelle hinter dem letzten Element eines zweiten Bereichs verweist.

*pred-* \
Ein Prädikat, das auf Äquivalenz prüft und einen **booleschen**Wert zurückgibt.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Bereiche neu angeordnet werden können, sodass Sie gemäß dem Vergleichs Prädikat identisch sind. andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

`is_permutation` verfügt im schlimmsten Fall über die quadratische Komplexität.

Die erste Vorlagen Funktion geht davon aus, dass es so viele Elemente im Bereich gibt, beginnend bei *First2* , da der von `[first1, last1)`festgelegte Bereich vorhanden ist. Wenn es weitere Elemente im zweiten Bereich gibt, werden sie ignoriert; wenn es weniger sind, hat das ein undefiniertes Verhalten zur Folge. Die dritte Vorlagenfunktion (C++14 und höher) macht diese Annahme nicht. Beide geben nur **dann true** zurück, wenn für jedes Element X im Bereich, der durch `[first1, last1)` festgelegt ist, so viele Elemente Y im selben Bereich vorhanden sind, für den X = = Y vorhanden ist, wie im Bereich, beginnend bei *First2* oder `[first2, last2)`. Hier muss `operator==` einen paar weisen Vergleich zwischen seinen Operanden durchführen.

Die zweiten und vierten Vorlagenfunktionen verhalten sich identisch, jedoch mit der Ausnahme, dass sie `operator==(X, Y)` durch `Pred(X, Y)` ersetzen. Für das ordnungsgemäße Verhalten muss das Prädikat symmetrisch, reflexiv und transitiv sein.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `is_permutation`:

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
#include <string>

using namespace std;

int main()
{
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };

    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };

    cout << "(1) Compare using built-in == operator: ";
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // true

    cout << "(2) Compare after modifying vec_2: ";
    vec_2[0] = 6;
    cout << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // false

    // Define equivalence as "both are odd or both are even"
    cout << "(3) vec_3 is a permutation of vec_4: ";
    cout << is_permutation(vec_3.begin(), vec_3.end(),
        vec_4.begin(), vec_4.end(),
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true

    // Initialize a vector using the 's' string literal to specify a std::string
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };

    // Define equivalence as "first letters are equal":
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),
        [](const string& lhs, const string& rhs)
    {
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator
    });

    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true

    cout << "Press a letter" << endl;
    char c;
    cin >> c;

    return 0;
}
```

## <a name="is_sorted"></a>is_sorted

Gibt **true** zurück, wenn die Elemente im angegebenen Bereich in sortierter Reihenfolge angeordnet sind.

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der angibt, wo der zu prüfende Bereich beginnt.

*Letzter*\
Ein Forward-Iterator, der das Ende eines Bereichs angibt.

*pred-* \
Eine Bedingung, auf die geprüft werden soll, um eine Reihenfolge zwischen zwei Elementen festzulegen. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt " **true** " oder " **false**" zurück. Dies führt den gleichen Task wie `operator<` aus.

### <a name="remarks"></a>Bemerkungen

Die erste Vorlagen Funktion gibt [is_sorted_until](#is_sorted_until)`( first, last ) == last`zurück. Die `operator<`-Funktion führt den Auftrags Vergleich aus.

Die zweite Vorlagen Funktion gibt `is_sorted_until( first, last , pred ) == last`zurück. Die *pred* -Prädikat Funktion führt den Auftrags Vergleich aus.

## <a name="is_sorted_until"></a>is_sorted_until

Gibt ein `ForwardIterator` zurück, das auf das letzte Element festgelegt ist, das in der Sortierreihenfolge eines angegebenen Bereichs ist.

Die zweite Version ermöglicht Ihnen die Bereitstellung eines Vergleichs Funktions Objekts, das **true** zurückgibt, wenn zwei angegebene Elemente in sortierter Reihenfolge vorliegen, andernfalls **false** .

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der angibt, wo der zu prüfende Bereich beginnt.

*Letzter*\
Ein Forward-Iterator, der das Ende eines Bereichs angibt.

*pred-* \
Eine Bedingung, auf die geprüft werden soll, um eine Reihenfolge zwischen zwei Elementen festzulegen. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Gibt ein `ForwardIterator` zurück, das auf das letzte Element in der Sortierreihenfolge festgelegt ist. Die sortierte Sequenz beginnt *zunächst*mit dem ersten.

### <a name="remarks"></a>Bemerkungen

Die erste Vorlagen Funktion gibt den letzten Iterator `next` in `[first, last]` zurück, sodass `[first, next)` eine sortierte Sequenz ist, geordnet nach `operator<`. Wenn `distance()` kleiner als 2 ist, gibt die Funktion *Last*zurück.

Die zweite Vorlagenfunktion verhält sich genauso; der einzige Unterschied ist, dass sie `operator<(X, Y)` durch `pred(X, Y)` ersetzt.

## <a name="iter_swap"></a>iter_swap

Tauscht zwei Werte aus, auf die durch ein Paar angegebener Iteratoren verwiesen wird.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );
```

### <a name="parameters"></a>Parameter

*Linker*\
Einer der Forward-Iteratoren, dessen Wert ausgetauscht werden soll.

*Rechte*\
Der zweite der Forward-Iteratoren, dessen Wert ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

`swap` sollten im bevorzugten **iter_swap**verwendet werden, das im Standard für die C++ Abwärtskompatibilität enthalten war. Wenn `Fit1` und `Fit2` Forward-Iteratoren sind, entspricht `iter_swap( Fit1, Fit2 )`, `swap( *Fit1, *Fit2 )`.

Die Werttypen der Forward-Eingabeiteratoren müssen den gleichen Wert haben.

### <a name="example"></a>Beispiel

```cpp
// alg_iter_swap.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) { m_nVal =
    rhs.m_nVal; return *this; }
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt(" << rhs.m_nVal << ")";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    CInt c1 = 5, c2 = 1, c3 = 10;
    deque<CInt> deq1;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Exchanging first and last elements with iter_swap
    iter_swap ( deq1.begin( ), --deq1.end( ) );

    cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping back first and last elements with swap
    swap ( *deq1.begin( ), *(deq1.end( ) -1 ) );

    cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping a vector element with a deque element
    vector<int> v1;
    vector<int>::iterator Iter1;
    deque<int> deq2;
    deque<int>::iterator d2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 4 ; ii <= 5 ; ii++ )
    {
        deq2.push_back( ii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque deq2 is ( " ;
    for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
        cout << *d2_Iter << " ";
    cout << ")." << endl;

    iter_swap ( v1.begin( ), deq2.begin( ) );

    cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << " & deque deq2 is: deq2 = ( ";
    for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
        cout << *d2_Iter << " ";
    cout << ")." << endl;
}
```

```Output
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).
The deque of CInts with first & last elements swapped is:
deq1 = ( CInt(10), CInt(1), CInt(5) ).
The deque of CInts with first & last elements swapped back is:
deq1 = ( CInt(5), CInt(1), CInt(10) ).
Vector v1 is ( 0 1 2 3 ).
Deque deq2 is ( 4 5 ).
After exchanging first elements,
vector v1 is: v1 = ( 4 1 2 3 ).
& deque deq2 is: deq2 = ( 0 5 ).
```

## <a name="lexicographical_compare"></a>lexicographical_compare

Vergleicht zwei Sequenzen elementweise, um zu bestimmen, welche der beiden kleiner ist.

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class Compare>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten zu vergleichenden Bereich adressiert.

*Last1*\
Ein Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im ersten zu vergleichenden Bereich adressiert.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten zu vergleichenden Bereich adressiert.

*Last2*\
Ein Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im zweiten zu vergleichenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt bei **Erfüllung true** zurück und **false** , wenn es nicht erfüllt wird.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn der erste Bereich lexikographisch kleiner als der zweite Bereich ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Ein lexikographischer Vergleich zweier Sequenzen vergleicht diese elementweise bis:

- es zwei korrespondierende ungleiche Elemente findet, und deren Vergleich als Ergebnis des Vergleichs zweier Sequenzen genommen wird.

- keine Ungleichungen gefunden werden, aber eine Sequenz mehr Elemente als eine andere hat, und die kürzere Sequenz als kleiner als die längere Sequenz angesehen wird.

- Es wurden keine Ungleichheiten gefunden, und die Sequenzen haben die gleiche Anzahl von Elementen, sodass die Sequenzen gleich sind und das Ergebnis des Vergleichs **false**ist.

### <a name="example"></a>Beispiel

```cpp
// alg_lex_comp.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    int ii;
    for ( ii = 0 ; ii <= 6 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Self lexicographical_comparison of v1 under identity
    bool result1;
    result1 = lexicographical_compare (v1.begin( ), v1.end( ),
                    v1.begin( ), v1.end( ) );
    if ( result1 )
        cout << "Vector v1 is lexicographically_less than v1." << endl;
    else
        cout << "Vector v1 is not lexicographically_less than v1." << endl;

    // lexicographical_comparison of v1 and L2 under identity
    bool result2;
    result2 = lexicographical_compare (v1.begin( ), v1.end( ),
                    L1.begin( ), L1.end( ) );
    if ( result2 )
        cout << "Vector v1 is lexicographically_less than L1." << endl;
    else
        cout << "Vector v1 is lexicographically_less than L1." << endl;

    bool result3;
    result3 = lexicographical_compare (v1.begin( ), v1.end( ),
                    v2.begin( ), v2.end( ), twice );
    if ( result3 )
        cout << "Vector v1 is lexicographically_less than v2 "
            << "under twice." << endl;
    else
        cout << "Vector v1 is not lexicographically_less than v2 "
            << "under twice." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 )
List L1 = ( 0 5 10 15 20 25 30 )
Vector v2 = ( 0 10 20 30 40 50 )
Vector v1 is not lexicographically_less than v1.
Vector v1 is lexicographically_less than L1.
Vector v1 is not lexicographically_less than v2 under twice.
```

## <a name="lower_bound"></a>lower_bound

Sucht die Position des ersten Elements in einem sortierten Bereich, der über einen Wert größer als oder gleich einem angegebenen Wert verfügt. Dabei wird das Sortierkriterium möglicherweise von einen binären Prädikat bestimmt.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value );

template<class ForwardIterator, class Type, class BinaryPredicate>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred );
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*value*\
Der Wert, dessen erste Position oder mögliche erste Position in dem sortierten Bereich gesucht wird.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator an der Position des ersten Elements in einem sortierten Bereich mit einem Wert, der größer als oder gleich einem angegebenen Wert ist, wobei die Äquivalenz von einem binären Prädikat angegeben wird.

### <a name="remarks"></a>Bemerkungen

Der sortierte Quellbereich, auf den verwiesen wird, muss gültig sein. Alle Iteratoren müssen dereferenzierbar sein und die letzte Position muss der innerhalb der Reihenfolge vom ersten von der ersten Position aus durch Zunahme erreichbar sein.

Ein sortierter Bereich ist eine Vorbedingung für die Verwendung von `lower_bound` und wann immer die Reihenfolge mit der vom binärem Prädikat angegebenen identisch ist.

Der Bereich wird vom Algorithmus `lower_bound` nicht geändert.

Die Werttypen der Forward-Iteratoren müssen weniger als vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig bestimmt werden (in dem Sinne, dass keins geringer als das Andere ist), oder dass eins geringer als das Andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen.

Die Komplexität dieses Algorithmus ist bei Zufallszugriffsiteratoren logarithmisch und andernfalls linear. Dabei ist eine Anzahl von Schritten proportional zu (`last - first`).

### <a name="example"></a>Beispiel

```cpp
// alg_lower_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate lower_bound

    vector<int>::iterator Result;

    // lower_bound of 3 in v1 with default binary predicate less<int>()
    Result = lower_bound(v1.begin(), v1.end(), 3);
    cout << "The lower_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The lower_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v3 with the binary predicate mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="make_heap"></a>make_heap

Konvertiert Elemente aus einem angegebenen Bereich in einen Heap, in dem das erste Element das größte ist und für den ein Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class RandomAccessIterator>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred );
```

### <a name="parameters"></a>Parameter

*erste*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der in einen Heap konvertiert werden soll.

*Letzter*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der in einen Heap konvertiert werden soll.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="remarks"></a>Bemerkungen

Heaps haben zwei Eigenschaften:

- Das erste Element ist immer das größte.

- Elemente können in logarithmischer Zeit hinzugefügt oder entfernt werden.

Heaps sind ideal zum Implementieren von Vorrangwarteschlangen. Sie werden beim Implementieren des C++-Standardbibliothekadapters [priority_queue-Klasse](../standard-library/priority-queue-class.md) verwendet.

Die Komplexität ist linear und erfordert `3 * (last - first)` Vergleiche.

### <a name="example"></a>Beispiel

```cpp
// alg_make_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with default less than ordering
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with greater than ordering
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater-than heaped version of v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="max"></a>Max

Vergleicht zwei Objekte und gibt das größere der beiden zurück, wobei das Sortierkriterium möglicherweise von einem binären Prädikat angegeben wird.

```cpp
template<class Type>
constexpr Type& max(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr Type& max(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);
template<class Type>
constexpr Type& max (
    initializer_list<Type> ilist);
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das erste der beiden Objekte, die verglichen werden.

*Rechte*\
Das zweite der beiden Objekte, die verglichen werden.

*pred-* \
Ein binäres Prädikat, das zum Vergleichen der beiden Objekte verwendet wird.

*InList* -\
Die Initializerliste, die die zu vergleichenden Objekte enthält.

### <a name="return-value"></a>Rückgabewert

Das größere der beiden Objekte, es sei denn, keins ist größer als das andere. In diesem Fall wird das erste der beiden Objekte zurückgegeben. Bei einem initializer_list-Element wird das größere der Objekte in der Liste zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Der `max`-Algorithmus ist ungewöhnlich, denn er weist Objekte auf, die als Parameter übergeben werden. Die meisten C++-Algorithmen der Standardbibliothek werden auf einem Elementbereich ausgeführt, dessen Position von als Parameter übergebenen Iteratoren angegeben wird. Wenn Sie eine Funktion benötigen, die einen Elementbereich bearbeitet, verwenden Sie stattdessen [max_element](../standard-library/algorithm-functions.md#max_element). Visual Studio 2017 aktiviert **constexpr** für die über Ladungen, die eine initializer_list nehmen.

### <a name="example"></a>Beispiel

```cpp
// alg_max.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether absolute value of elem1 is greater than
// absolute value of elem2
bool abs_greater ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = -elem1;
    if ( elem2 < 0 )
        elem2 = -elem2;
    return elem1 < elem2;
};

int main()
{
    int a = 6, b = -7;
    // Return the integer with the larger absolute value
    const int& result1 = max(a, b, abs_greater);
    // Return the larger integer
    const int& result2 = max(a, b);

    cout << "Using integers 6 and -7..." << endl;
    cout << "The integer with the greater absolute value is: "
            << result1 << "." << endl;
    cout << "The integer with the greater value is: "
            << result2 << "." << endl;
    cout << endl;

    // Comparing the members of an initializer_list
    const int& result3 = max({ a, b });
    const int& result4 = max({ a, b }, abs_greater);

    cout << "Comparing the members of an initializer_list..." << endl;
    cout << "The member with the greater value is: " << result3 << endl;
    cout << "The integer with the greater absolute value is: " << result4 << endl;

    // Comparing set containers with elements of type CInt
    // using the max algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = max ( s1, s2 );
    cout << "s3 = max ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using the max algorithm
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = max ( v1, v2 );
    v5 = max ( v1, v3 );

    cout << "Vector v4 = max (v1,v2) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = max (v1,v3) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
Using integers 6 and -7...
The integer with the greater absolute value is: -7
The integer with the greater value is: 6.
Comparing the members of an initializer_list...The member with the greater value is: 6The integer with the greater absolute value is: -7
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = max (v1,v2) is ( 0 1 2 ).
Vector v5 = max (v1,v3) is ( 0 2 4 ).
```

## <a name="max_element"></a>max_element

Sucht das erste Vorkommen des größten Elements in einem angegebenen Bereich, in dem das Sortierkriterium möglicherweise von einem binären Prädikat angegeben wird.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Vorwärtsiterator, der die Position des ersten Elements im nach dem größten Element zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Vorwärtsiterator, der die Position direkt hinter dem letzten Elements im nach dem größten Element zu durchsuchenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das Vergleichs Prädikat übernimmt zwei Argumente und sollte **true** zurückgeben, wenn das erste Element kleiner als das zweite Element ist, andernfalls **false** .

### <a name="return-value"></a>Rückgabewert

Ein Vorwärtsiterator, der die Position des ersten Vorkommen des größten Elements im zu durchsuchenden Bereich adressiert.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Komplexität ist linear: `(last - first) - 1` Vergleiche sind für einen nicht leeren Bereich erforderlich.

### <a name="example"></a>Beispiel

```cpp
// alg_max_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<(ostream& osIn, const CInt& rhs)
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is greater than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Searching a set container with elements of type CInt
    // for the maximum element
    CInt c1 = 1, c2 = 2, c3 = -3;
    set<CInt> s1;
    set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s1.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    s1_R1_Iter = max_element ( s1.begin( ), s1.end( ) );

    cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        v1.push_back( - 2 * ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
        cout << *v1_Iter << " ";
    cout << ")." << endl;

    v1_R1_Iter = max_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = max_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The largest element in v1 under the mod_lesser"
            << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

## <a name="merge"></a>Merge

Kombiniert alle Elemente aus zwei sortierten Quellbereichen zu einem einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen.

*Last1*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten der beiden nacheinander sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen.

*Last2*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zweiten der beiden nacheinander sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements im ersten Zielbereich adressiert, in dem die beiden Quellbereiche kombiniert und zu einem einzelnen Bereich sortiert werden sollen.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das Vergleichs Prädikat übernimmt zwei Argumente und sollte **true** zurückgeben, wenn das erste Element kleiner als das zweite Element ist, andernfalls **false** .

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Element im sortierten Zielbereich adressiert.

### <a name="remarks"></a>Bemerkungen

Die sortierten Quellbereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb jeder Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Der Zielbereich sollte keinen der Quellbereiche überlappen und groß genug sein, um den Zielbereich zu enthalten.

Die sortierten Quellbereiche müssen als Vorbedingung zur Anwendung des `merge` -Algorithmus entsprechend der gleichen Reihenfolge sortiert werden, die vom Algorithmus für die Sortierung der kombinierten Bereiche verwendet wird.

Der Vorgang ist stabil, da die relative Reihenfolge der Elemente innerhalb jedes Bereichs im Zielbereich beibehalten wird. Die Quellbereiche werden nicht durch den Algorithmus `merge`geändert.

Die Werttypen der Eingabeiteratoren müssen mit „kleiner als“ vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig (in dem Sinne, dass keines kleiner als das andere ist) oder eines als kleiner als das andere bestimmt werden können. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Wenn in beiden Quellbereichen äquivalente Elemente vorhanden sind, stehen im Zielbereich die Elemente aus dem ersten Bereich vor den Elementen aus dem zweiten Bereich.

Die Komplexität des Algorithmus ist mit höchstens `(last1 - first1) - (last2 - first2) - 1` vergleichen linear.

Die [-list-Klasse](../standard-library/list-class.md) stellt eine Memberfunktion „merge“ bereit, um die Elemente zweier Listen zusammenzuführen.

### <a name="example"></a>Beispiel

```cpp
// alg_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 ) {
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main() {
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1;

    // Constructing vector v1a and v1b with default less than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3a( v1a ), v3b( v1b ) , v3( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To merge inplace in ascending order with default binary
    // predicate less<int>( )
    merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
        v2.begin( ), greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // Applying A user-defined (UD) binary predicate mod_lesser
    merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
        v3.begin( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="min"></a>man

Vergleicht zwei Objekte und gibt das kleinere der beiden zurück, wobei das Sortierkriterium möglicherweise von einem binären Prädikat angegeben wird.

```cpp
template<class Type>
constexpr const Type& min(
    const Type& left,
    const Type& right);

template<class Type, class Pr>
constexpr const Type& min(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr Type min(
    initializer_list<Type> ilist);

template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das erste der beiden Objekte, die verglichen werden.

*Rechte*\
Das zweite der beiden Objekte, die verglichen werden.

*pred-* \
Ein binäres Prädikat, das zum Vergleichen der beiden Objekte verwendet wird.

*InList* -\
Der `initializer_list`, der die zu vergleichenden Member enthält.

### <a name="return-value"></a>Rückgabewert

Das kleinere der beiden Objekte, es sei denn, keins ist geringer als das andere. In diesem Fall wird das erste der beiden Objekte zurückgegeben. Im Fall einer `initializer_list`werden die geringsten Objekte in der Liste zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Der `min`-Algorithmus ist ungewöhnlich, denn er weist Objekte auf, die als Parameter übergeben werden. Die meisten C++-Algorithmen der Standardbibliothek werden auf einem Elementbereich ausgeführt, dessen Position von als Parameter übergebenen Iteratoren angegeben wird. Wenn Sie eine Funktion benötigen, die einen Elementbereich nutzt, verwenden Sie [min_element](../standard-library/algorithm-functions.md#min_element). [constexpr](../cpp/constexpr-cpp.md) wurde auf den `initializer_list` Überladungen in Visual Studio 2017 aktiviert.

### <a name="example"></a>Beispiel

```cpp
// alg_min.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Comparing integers directly using the min algorithm with
    // binary predicate mod_lesser & with default less than
    int a = 6, b = -7, c = 7 ;
    const int& result1 = min ( a, b, mod_lesser );
    const int& result2 = min ( b, c );

    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result1 << "." << endl;
    cout << "The lesser of the integers -7 & 7 is: "
        << result2 << "." << endl;
    cout << endl;

    // Comparing the members of an initializer_list
    const int& result3 = min({ a, c });
    const int& result4 = min({ a, b }, mod_lesser);

    cout << "The lesser of the integers 6 & 7 is: "
        << result3 << "." << endl;
    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result4 << "." << endl;
    cout << endl;

    // Comparing set containers with elements of type CInt
    // using the min algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
        cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = min ( s1, s2 );
    cout << "s3 = min ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using min algorithm
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = min ( v1, v2 );
    v5 = min ( v1, v3 );

    cout << "Vector v4 = min ( v1,v2 ) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = min ( v1,v3 ) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
The mod_lesser of the integers 6 & -7 is: 6.
The lesser of the integers -7 & 7 is: -7.
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).
```

## <a name="min_element"></a>min_element

Sucht das erste Vorkommen des kleinsten Elements in einem angegebenen Bereich, in dem das Sortierkriterium von einem binären Prädikat angegeben werden kann.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im nach dem kleinsten Element zu durchsuchenden Bereich adressiert.

*Letzter*\
Ein Forward-Iterator, der die Position des ersten Elements direkt hinter dem letzten Element im nach dem kleinsten Element zu durchsuchenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das Vergleichs Prädikat übernimmt zwei Argumente und sollte **true** zurückgeben, wenn das erste Element kleiner als das zweite Element ist, andernfalls **false** .

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator, der die Position des ersten Vorkommen des kleinsten Elements im zu durchsuchenden Bereich adressiert.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Komplexität ist linear: `(last - first) - 1` Vergleiche sind für einen nicht leeren Bereich erforderlich.

### <a name="example"></a>Beispiel

```cpp
// alg_min_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Searching a set container with elements of type CInt
    // for the minimum element
    CInt c1 = 1, c2 = 2, c3 = -3;
    set<CInt> s1;
    set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s1.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    s1_R1_Iter = min_element ( s1.begin( ), s1.end( ) );

    cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        v1.push_back( - 2 * ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
        cout << *v1_Iter << " ";
    cout << ")." << endl;

    v1_R1_Iter = min_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = min_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The smallest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

```Output
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).
The smallest element in s1 is: CInt( -3 )

Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).
The smallest element in v1 is: -8
The smallest element in v1 under the mod_lesser
binary predicate is: 0
```

## <a name="minmax_element"></a>minmax_element

Führt die Aufgaben aus, die von `min_element` und `max_element` in einem Aufruf erledigt werden.

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der das Beginn eines Bereichs angibt.

*Letzter*\
Ein Forward-Iterator, der das Ende eines Bereichs angibt.

*pred-* \
Ein benutzerdefiniertes Prädikat Funktions Objekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das Vergleichs Prädikat übernimmt zwei Argumente und sollte **true** zurückgeben, wenn die erste kleiner als die zweite ist, andernfalls **false** .

### <a name="return-value"></a>Rückgabewert

Rückgabe

[https://login.microsoftonline.com/consumers/](`pair<ForwardIterator, ForwardIterator>( min_element(first, last), max_element(first, last))`).

### <a name="remarks"></a>Bemerkungen

Die erste Vorlagenfunktion gibt Folgendes zurück:

[https://login.microsoftonline.com/consumers/](`pair<ForwardIterator,ForwardIterator>(min_element(first,last), max_element(first,last))`).

Die zweite Vorlagenfunktion verhält sich genauso; der einzige Unterschied ist, dass sie `operator<(X, Y)` durch `pred(X, Y)` ersetzt.

Wenn die Sequenz nicht leer ist, führt die Funktion höchstens `3 * (last - first - 1) / 2` Vergleiche aus.

## <a name="minmax"></a>MinMax

Vergleicht zwei Eingabeparameter und gibt diese als Paar, in der Reihenfolge "kleiner zu größer" zurück.

```cpp
template<class Type>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right);

template<class Type, class BinaryPredicate>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist);

template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das erste der beiden Objekte, die verglichen werden.

*Rechte*\
Das zweite der beiden Objekte, die verglichen werden.

*pred-* \
Ein binäres Prädikat, das zum Vergleichen der beiden Objekte verwendet wird.

*InList* -\
Der `initializer_list`, der die zu vergleichenden Member enthält.

### <a name="remarks"></a>Bemerkungen

Die erste Vorlagen Funktion gibt `pair<const Type&, const Type&>( right, left )` zurück, wenn *Rechts* kleiner als *Links*ist. Andernfalls wird `pair<const Type&, const Type&>( left, right )`zurückgegeben.

Die zweite Member-Funktion gibt ein paar zurück, bei dem das erste Element das kleinere und das zweite das größere ist, wenn es durch das Prädikat *Prädikat*verglichen wird.

Die übrigen Vorlagen Funktionen Verhalten sich identisch, mit dem Unterschied, dass Sie die *linken* und *rechten* Parameter durch *InList*ersetzen.

Die Funktion führt genau einen Vergleich aus.

## <a name="mismatch"></a>Konflikt

Vergleicht zwei Bereiche elementweise und findet die e erste Position mit einem Unterschied.

Verwenden Sie die Überladungen mit zwei Bereichen im C++14-Code, da die Überladungen, die nur einen einzigen Iterator für den zweiten Bereich nutzen, keine Unterschiede erkennen, wenn der zweite Bereich länger als der erste Bereich ist. Darüber hinaus führt dies zu einem nicht definierten Verhalten, wenn der zweite Bereich kürzer als der erste Bereich ist.

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

//C++17
template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten zu testenden Bereich adressiert.

*Last1*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im ersten zu testenden Bereich adressiert.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten zu testenden Bereich adressiert.

*Last2*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zweiten zu testenden Bereich adressiert.

*pred-* \
Das benutzerdefinierte Prädikatfunktionsobjekt vergleicht die aktuellen Elemente in jedem Bereich und bestimmt, ob sie gleich sind. Gibt **TRUE** zurück, wenn erfüllt und **FALSE**, wenn nicht erfüllt.

### <a name="return-value"></a>Rückgabewert

Ein Paar von Iteratoren zu den Positionen des Konflikts in zwei Bereichen, der erste Komponenteniterator an die Position im ersten Bereich und der zweite Komponenteniterator an die Position im zweiten Bereich. Wenn es im Vergleich zwischen den Elementen keinen Unterschied gibt oder das binäre Prädikat in der zweiten Version durch alle Elementpaare aus den beiden Bereichen erfüllt wird, verweist der erste Komponenteniterator auf die erste Position hinter dem letzten Element in den ersten Bereich und der zweite Komponenteniterator auf die Position eine Stelle nach dem letzten Element im zweiten Bereich.

### <a name="remarks"></a>Bemerkungen

Die erste Vorlagenfunktion geht davon aus, dass im Bereich beginnend mit beginnend mit first2 so viele Elemente vorhanden sind, wie es im Bereich [first1, last1) der Fall ist. Wenn es mehr im zweiten Bereich gibt, werden Sie ignoriert. Wenn weniger vorhanden ist, ergibt sich ein nicht definiertes Verhalten.

Der zu durchsuchende Bereich muss gültig sein. Alle Iteratoren müssen dereferenzierbar sein, und die letzte Position ist von der Ersten durch Zunahme erreichbar.

Die Zeitkomplexität des Algorithmus ist linear zur Anzahl der im kürzeren Bereich enthaltenen Elemente.

Das benutzerdefinierte Prädikat ist nicht erforderlich, um eine Äquivalenzbeziehung vorzugeben, die zwischen den dazugehörigen Operanden symmetrisch, reflexiv und transitiv ist.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird dein Konflikt verwendet werden kann. Die C ++ 03 Überlastung wird nur zum Veranschaulichen des Erzeugens eines unerwarteten Ergebnisses dargestellt.

```cpp
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>
#include <string>
#include <utility>

using namespace std;

// Return whether first element is twice the second
// Note that this is not a symmetric, reflexive and transitive equivalence.
// mismatch and equal accept such predicates, but is_permutation does not.
bool twice(int elem1, int elem2)
{
    return elem1 == elem2 * 2;
}

void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,
    const vector<int>& left, const vector<int>& right)
{
    // If either iterator stops before reaching the end of its container,
    // it means a mismatch was detected.
    if (result.first != left.end() || result.second != right.end())
    {
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));
        cout << msg << "mismatch. Left iterator at " << leftpos
            << " right iterator at " << rightpos << endl;
    }
    else
    {
        cout << msg << " match." << endl;
    }
}

int main()
{

    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };

    // Testing different length vectors for mismatch (C++03)
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());
    bool is_mismatch = match_vecs.first != vec_1.end();
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;

    // Using dual-range overloads:

    // Testing different length vectors for mismatch (C++14)
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);

    // Identify point of mismatch between vec_1 and modified vec_2.
    vec_2[3] = 42;
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);

    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);

    vec_4[5] = 31;
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);

    // Compare a vector<int> to a list<int>
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;

    char c;
    cout << "Press a key" << endl;
    cin >> c;

}
```

```Output
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred: match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
```

## <a name="alg_move"></a>&lt;ALG&gt; verschieben

Verschiebt Elemente, die einem angegebenen Bereich zugeordnet sind.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 move(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Eine Eingabeiterator, der angibt, ab welcher Position die Elemente kopiert werden sollen.

*Letzter*\
Eine Eingabeiterator, der angibt, bis zu welcher Position die Elemente kopiert werden sollen.

*dest* -\
Der Ausgabeiterator, der die zu verschiebenden Elemente enthalten soll.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion wertet `*(dest + N) = move(*(first + N))` einmal für jede `N` im Bereich `[0, last - first)`aus, um genau höhere Werte `N` zu erhalten, die mit dem niedrigsten Wert beginnen. Dann wird `dest + N` zurückgegeben. Wenn `dest` und *zuerst* Speicherbereiche festlegen, darf " *dest* " nicht im Bereich `[first, last)`liegen.

## <a name="move_backward"></a>move_backward

Verschiebt die Elemente eines Iterators in einen anderen. Die Verschiebung beginnt mit dem letzten Element in einem angegebenen Bereich und endet mit dem ersten Element in diesem Bereich.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 move_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Iterator, der den Beginn eines Bereichs angibt, aus dem Elemente verschoben werden.

*Letzter*\
Ein Iterator, der das Ende eines Bereichs angibt, aus dem Elemente verschoben werden. Dieses Element wird nicht verschoben.

*DestEnd* -\
Ein bidirektionaler Iterator, der die Position hinter dem letzten Element im Zielbereich adressiert.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion wertet `*(destEnd - N - 1) = move(*(last - N - 1))` einmal für jede `N` im Bereich `[0, last - first)`aus, um genau höhere Werte `N` zu erhalten, die mit dem niedrigsten Wert beginnen. Dann wird `destEnd - (last - first)` zurückgegeben. Wenn " *DestEnd* " und " *First* " Speicherbereiche angeben, darf " *DestEnd* " nicht im Bereich `[first, last)`liegen.

`move` und `move_backward` entsprechen funktional der Verwendung von `copy` und `copy_backward` mit einem Verschiebeiterator.

## <a name="next_permutation"></a>next_permutation

Ordnet die Elemente in einem Bereich neu, damit die ursprüngliche Reihenfolge von der lexikografisch nächsthöheren Permutation ersetzt wird, falls vorhanden, wobei die Bedeutung von „nächsthöher“ durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class BidirectionalIterator>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein bidirektionaler Iterator, der auf die Position des ersten Elements im zu permutierenden Bereich zeigt.

*Letzter*\
Ein bidirektionaler Iterator, der auf die Position des ersten Elements direkt hinter dem letzten Element im zu permutierenden Bereich zeigt.

*pred-* \
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das von aufeinanderfolgenden Elementen in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die lexikographisch nächste Permutation beendet wird und die ursprüngliche Reihenfolge des Bereichs ersetzt hat; andernfalls **FALSE**. In diesem Fall wird die Reihenfolge in die lexikographisch kleinste Permutation umgewandelt.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Das binäre Standard Prädikat ist kleiner als, und die Elemente im Bereich müssen kleiner als vergleichbar sein, um sicherzustellen, dass die nächste permutations gut definiert ist.

Die Komplexität ist mit höchstens `(last - first) / 2` Austausch Vorgängen linear.

### <a name="example"></a>Beispiel

```cpp
// alg_next_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ) {}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ) {}
    CInt& operator=( const CInt& rhs ) {m_nVal =
        rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal ); }
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Reordering the elements of type CInt in a deque
    // using the prev_permutation algorithm
    CInt c1 = 5, c2 = 1, c3 = 10;
    bool deq1Result;
    deque<CInt> deq1, deq2, deq3;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    deq1Result = next_permutation ( deq1.begin( ), deq1.end( ) );

    if ( deq1Result )
        cout << "The lexicographically next permutation "
            << "exists and has\nreplaced the original "
            << "ordering of the sequence in deq1." << endl;
    else
        cout << "The lexicographically next permutation doesn't "
            << "exist\n and the lexicographically "
            << "smallest permutation\n has replaced the "
            << "original ordering of the sequence in deq1." << endl;

    cout << "After one application of next_permutation,\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl << endl;

    // Permuting vector elements with binary function mod_lesser
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    next_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        next_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another next_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).
The lexicographically next permutation exists and has
replaced the original ordering of the sequence in deq1.
After one application of next_permutation,
deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first next_permutation, vector v1 is:
v1 = ( -3 -2 -1 0 1 3 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 1 3 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 3 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 1 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 2 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 1 0 2 3 ).
```

## <a name="nth_element"></a>nth_element

Partitioniert einen Bereich von Elementen und ermittelt das *n*-te Element der Sequenz im Bereich, sodass alle Elemente davor kleiner oder gleich sind und alle Elemente, die in der Sequenz folgen, größer oder gleich sind.

```cpp
template<class RandomAccessIterator>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der partitioniert werden soll.

*ten* -\
Ein zufälliger Eingabeiterator, der die Position des Elements, das auf der Grenze der Partition korrekt sortiert werden soll, adressiert.

*Letzter*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der partitioniert werden soll.

*pred-* \
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das von aufeinanderfolgenden Elementen in der Reihenfolge erfüllt werden soll. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt bei **Erfüllung true** zurück und **false** , wenn es nicht erfüllt wird.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Der `nth_element`-Algorithmus garantiert nicht, dass Elemente in den untergeordneten Bereichen des *n*-ten Elements sortiert werden. Deshalb gibt es weniger Garantien als `partial_sort`, das Elemente in einem Bereich unter ausgewählten Elementen ordnet, und das möglicherweise als schnellere Alternative zu `partial_sort` verwendet werden kann, wenn eine Sortierung des niedrigeren Bereichs nicht erforderlich ist.

Wenn keins kleiner als das andere ist, sind Elemente äquivalent, aber nicht unbedingt gleich.

Der Durchschnitt einer Sortier Komplexität ist in Bezug auf *Last-First*linear.

### <a name="example"></a>Beispiel

```cpp
// alg_nth_elem.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 ) {
    return elem1 > elem2;
}

int main() {
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1.push_back( 3 * i );

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
        v1.push_back( 3 * ii + 1 );

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
        v1.push_back( 3 * iii +2 );

    cout << "Original vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );
    cout << "Position 3 partitioned vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order, specify binary predicate
    nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),
            greater<int>( ) );
    cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    random_shuffle( v1.begin( ), v1.end( ) );
    cout << "Shuffled vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );
    cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

## <a name="none_of"></a>none_of

Gibt **true** zurück, wenn eine Bedingung nicht zwischen Elementen im angegebenen Bereich vorhanden ist.

```cpp
template<class InputIterator, class UnaryPredicate>
bool none_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool none_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabe-Iterator, der angibt, ab wo ein Bereich von Elementen auf eine Bedingung überprüft werden soll.

*Letzter*\
Eine Eingabeiterator, das Ende eines Bereichs von Elementen angibt.

*pred-* \
Eine Bedingung, auf die geprüft werden soll. Diese Bedingung wird von einem benutzerdefinierten Prädikatfunktionsobjekt bereitgestellt. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Gibt **true** zurück, wenn die Bedingung nicht mindestens einmal im festgelegten Bereich erkannt wird, und **false** , wenn die Bedingung erkannt wird.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt nur **dann true** zurück, wenn das Prä`pred(*(first + N))` dikat für einige `N` im Bereich `[0, last - first)`immer **false**ist.

## <a name="partial_sort"></a>partial_sort

Ordnet eine bestimmte Anzahl von kleineren Elementen in einem Bereich in einer aufsteigenden Reihenfolge oder gemäß eines Sortierkriteriums an, das von einem binären Prädikat angegeben wird.

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*sortend* -\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Unterbereich adressiert, der sortiert werden soll.

*Letzter*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der teilweise sortiert werden soll.

*pred-* \
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das von aufeinanderfolgenden Elementen in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Wenn keins kleiner als das andere ist, sind Elemente äquivalent, aber nicht unbedingt gleich. Der `sort`-Algorithmus ist nicht stabil und stellt nicht sicher, dass die relative Reihenfolge der äquivalenten Elemente beibehalten wird. Der Algorithmus `stable_sort` behält diese ursprüngliche Sortierung bei.

Die durchschnittliche Teil Sortier Komplexität ist *O*((`last`- `first`) log (`sortEnd`- `first`)).

### <a name="example"></a>Beispiel

```cpp
// alg_partial_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
    {
        v1.push_back( 2 * ii +1 );
    }

    cout << "Original vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );
    cout << "Partially sorted vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To partially sort in descending order, specify binary predicate
    partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );
    cout << "Partially resorted (greater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ), UDgreater );
    cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector:
v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Partially sorted vector:
v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )
Partially resorted (greater) vector:
v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )
Partially resorted (UDgreater) vector:
v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )
```

## <a name="partial_sort_copy"></a>partial_sort_copy

Kopiert Elemente aus einem Quellbereich in einen Zielbereich, in dem die Quellelemente entweder durch kleiner als oder durch ein anderes festgelegtes binäres Prädikat sortiert werden.

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im Quellbereich adressiert.

*Last1*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im Quellbereich adressiert.

*First2*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements im sortierten Zielbereich adressiert.

*Last2*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im sortierten Zielbereich adressiert.

*pred-* \
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das von aufeinanderfolgenden Elementen in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

Ein zufälliger Eingabeiterator, der Elemente im Zielbereich, die direkt hinter dem letzten aus dem Quellbereich eingefügten Element liegen, adressiert.

### <a name="remarks"></a>Bemerkungen

Die Quell- und Zielbereiche dürfen sich nicht überlappen und müssen gültig sein: Alle Zeiger müssen dereferenzierbar sein; die letzte Position innerhalb jeder Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Das binäre Prädikat muss eine strikte schwache Sortierung bereitstellen, sodass Elemente, die nicht äquivalent sind, sortiert werden, aber Elemente, die äquivalent sind, nicht sortiert werden. Wenn keins kleiner als das andere ist, sind Elemente äquivalent, aber nicht unbedingt gleich.

### <a name="example"></a>Beispiel

```cpp
// alg_partial_sort_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    list<int> list1;
    vector<int>::iterator iter1, iter2;
    list<int>::iterator list1_Iter, list1_inIter;

    int i;
    for (i = 0; i <= 9; i++)
        v1.push_back(i);

    random_shuffle(v1.begin(), v1.end());

    list1.push_back(60);
    list1.push_back(50);
    list1.push_back(20);
    list1.push_back(30);
    list1.push_back(40);
    list1.push_back(10);

    cout << "Vector v1 = ( " ;
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;

    cout << "List list1 = ( " ;
    for (list1_Iter = list1.begin();
         list1_Iter!= list1.end();
         list1_Iter++)
        cout << *list1_Iter << " ";
    cout << ")" << endl;

    // Copying a partially sorted copy of list1 into v1
    vector<int>::iterator result1;
    result1 = partial_sort_copy(list1.begin(), list1.end(),
             v1.begin(), v1.begin() + 3);

    cout << "List list1 Vector v1 = ( " ;
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;
    cout << "The first v1 element one position beyond"
         << "\n the last L 1 element inserted was " << *result1
         << "." << endl;

    // Copying a partially sorted copy of list1 into v2
    int ii;
    for (ii = 0; ii <= 9; ii++)
        v2.push_back(ii);

    random_shuffle(v2.begin(), v2.end());
    vector<int>::iterator result2;
    result2 = partial_sort_copy(list1.begin(), list1.end(),
             v2.begin(), v2.begin() + 6);

    cout << "List list1 into Vector v2 = ( " ;
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)
        cout << *iter2 << " ";
    cout << ")" << endl;
    cout << "The first v2 element one position beyond"
         << "\n the last L 1 element inserted was " << *result2
         << "." << endl;
}
```

## <a name="partition"></a>spaltet

Klassifiziert Elemente in einem Bereich in zwei zusammenhanglose Sätze, wenn diese Elemente ein unäres Prädikat erfüllen, das denen direkt vorausgeht, die es nicht erfüllen können.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator partition(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein bidirektionaler Iterator, der die Position des ersten Elements in dem Bereich adressiert, der partitioniert werden soll.

*Letzter*\
Ein bidirektionaler Iterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der partitioniert werden soll.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die Bedingung definiert, die erfüllt werden muss, wenn ein Element eingeordnet werden soll. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der die Position des ersten Elements in dem Bereich adressiert, das die Prädikatbedingung nicht erfüllt.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Elemente *a* und *b* sind äquivalent, aber nicht unbedingt gleich, wenn beide `pred( a, b )` false sind und `pred( b, a )` false ist, wobei *pred* das vom Parameter angegebene Prädikat ist. Der `partition`-Algorithmus ist nicht stabil und stellt nicht sicher, dass die relative Reihenfolge der äquivalenten Elemente beibehalten wird. Der Algorithmus `stable_partition` behält diese ursprüngliche Sortierung bei.

Die Komplexität ist linear: Es gibt `(last - first)` Anwendungen von *pred* und höchstens `(last - first)/2` tauschen.

### <a name="example"></a>Beispiel

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 10 ; i++ )
    {
        v1.push_back( i );
    }
    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Partition the range with predicate greater10
    partition ( v1.begin( ), v1.end( ), greater5 );
    cout << "The partitioned set of elements in v1 is: ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="partition_copy"></a>partition_copy

Kopiert Elemente, für die eine Bedingung **true** ist, in ein Ziel, für das die Bedingung **false** ist. Die Elemente müssen von einem angegebenen Bereich stammen.

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class UnaryPredicate>
pair<OutputIterator1, OutputIterator2> partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
pair<ForwardIterator1, ForwardIterator2> partition_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    ForwardIterator1 out_true,
    ForwardIterator2 out_false,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der den Beginn eines Bereichs angibt, der auf eine Bedingung geprüft werden soll.

*Letzter*\
Ein Eingabeiterator, der das Ende eines Bereichs angibt.

*dest1*\
Ein Ausgabeiterator, der verwendet wird, um Elemente zu kopieren, die für eine mit *pred*getestete Bedingung true zurückgeben

*dest2*\
Ein Ausgabeiterator, der verwendet wird, um Elemente zu kopieren, die für eine mit *pred*getestete Bedingung false zurückgeben

*pred-* \
Eine Bedingung, auf die geprüft werden soll. Diese Bedingung wird von einem benutzerdefinierten Prädikatfunktionsobjekt bereitgestellt, das die zu prüfende Bedingung definiert. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion kopiert jedes Element `X` in `[first,last)` auf `*dest1++`, wenn `pred(X)` true ist, oder `*dest2++`, wenn dies nicht der Fall ist. Er gibt `pair<OutputIterator1, OutputIterator2>(dest1, dest2)` zurück.

## <a name="partition_point"></a>partition_point

Gibt das erste Element im angegebenen Bereich zurück, der die Bedingung nicht erfüllt. Die Elemente werden so sortiert, dass die, die die Bedingung erfüllen, vor denen angeordnet werden, die die Bedingung nicht erfüllen.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein `ForwardIterator`, der den Beginn eines Bereichs angibt, der auf eine Bedingung geprüft werden soll.

*Letzter*\
Ein `ForwardIterator`, der das Ende eines Bereichs angibt.

*pred-* \
Eine Bedingung, auf die geprüft werden soll. Dies wird von einem benutzerdefinierten Prädikatfunktionsobjekt bereitgestellt, das bzw. der die Bedingung definiert, die vom zu suchenden Element erfüllt wird. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt " **true** " oder " **false**" zurück.

### <a name="return-value"></a>Rückgabewert

Gibt einen `ForwardIterator` zurück, der auf das erste Element verweist, das die von der *pred*getestete Bedingung nicht erfüllt, oder gibt den *letzten* zurück, wenn nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion findet den ersten Iterator `it` in `[first, last)`, für den `pred(*it)` **false**ist. Die Sequenz muss nach *pred*geordnet werden.

## <a name="pop_heap"></a>pop_heap

Entfernt das größte Element von der Vorderseite eines Heaps und fügt es in die vorletzte Position des Bereichs ein und bildet dann einen neuen Heap aus den übrigen Elementen.

```cpp
template<class RandomAccessIterator>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements im Heap adressiert.

*Letzter*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im Heap adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="remarks"></a>Bemerkungen

Der Algorithmus `pop_heap` ist die Umkehrung des Vorgangs, der vom push_heap-Algorithmus durchgeführt wird. In diesem Vorgang wird das vorletzte Element eines Bereichs einem Heap hinzugefügt, der aus den vorherigen Elementen des Bereichs besteht, wenn das hinzuzufügende Element größer als alle anderen Elemente des Heaps sind.

Heaps haben zwei Eigenschaften:

- Das erste Element ist immer das größte.

- Elemente können in logarithmischer Zeit hinzugefügt oder entfernt werden.

Heaps sind ideal zum Implementieren von Vorrangwarteschlangen. Sie werden beim Implementieren des C++-Standardbibliothekadapters [priority_queue-Klasse](../standard-library/priority-queue-class.md) verwendet.

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Der Bereich, ohne das neu am Ende hinzugefügte Element, muss ein Heap sein.

Die Komplexität ist logarithmisch und erfordert höchstens `log (last - first)` Vergleiche.

### <a name="example"></a>Beispiel

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 1 ; i <= 9 ; i++ )
        v1.push_back( i );

    // Make v1 a heap with default less than ordering
    random_shuffle( v1.begin( ), v1.end( ) );
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Add an element to the back of the heap
    v1.push_back( 10 );
    push_heap( v1.begin( ), v1.end( ) );
    cout << "The reheaped v1 with 10 added is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove the largest element from the heap
    pop_heap( v1.begin( ), v1.end( ) );
    cout << "The heap v1 with 10 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << endl;

    // Make v1 a heap with greater-than ordering with a 0 element
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    v1.push_back( 0 );
    push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The 'greater than' reheaped v1 puts the smallest "
        << "element first:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Application of pop_heap to remove the smallest element
    pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The 'greater than' heaped v1 with the smallest element\n "
        << "removed from the heap is: ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="prev_permutation"></a>prev_permutation

Ordnet die Elemente in einem Bereich neu, damit die ursprüngliche Reihenfolge von der lexikografisch vorherigen höheren Permutation ersetzt wird, falls vorhanden, wobei die Bedeutung von „vorherige“ durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class BidirectionalIterator>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein bidirektionaler Iterator, der auf die Position des ersten Elements im zu permutierenden Bereich zeigt.

*Letzter*\
Ein bidirektionaler Iterator, der auf die Position des ersten Elements direkt hinter dem letzten Element im zu permutierenden Bereich zeigt.

*pred-* \
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das von aufeinanderfolgenden Elementen in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die lexikografisch vorherige permutations vorhanden ist und die ursprüngliche Reihenfolge des Bereichs ersetzt hat. andernfalls " **false**". in diesem Fall wird die Reihenfolge in die lexikografisch größte Permutation umgewandelt.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Das binäre Standard Prädikat ist kleiner als, und die Elemente im Bereich müssen kleiner als vergleichbar sein, um sicherzustellen, dass die vorherige permutations gut definiert ist.

Die Komplexität ist linear, wobei höchstens (`last` - `first`)/2 getauscht werden.

### <a name="example"></a>Beispiel

```cpp
// alg_prev_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt {
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Reordering the elements of type CInt in a deque
    // using the prev_permutation algorithm
    CInt c1 = 1, c2 = 5, c3 = 10;
    bool deq1Result;
    deque<CInt> deq1, deq2, deq3;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    deq1Result = prev_permutation ( deq1.begin( ), deq1.end( ) );

    if ( deq1Result )
        cout << "The lexicographically previous permutation "
            << "exists and has \nreplaced the original "
            << "ordering of the sequence in deq1." << endl;
    else
        cout << "The lexicographically previous permutation doesn't "
            << "exist\n and the lexicographically "
            << "smallest permutation\n has replaced the "
            << "original ordering of the sequence in deq1." << endl;

    cout << "After one application of prev_permutation,\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl << endl;

    // Permutating vector elements with binary function mod_lesser
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
        v1.push_back( i );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).
The lexicographically previous permutation doesn't exist
and the lexicographically smallest permutation
has replaced the original ordering of the sequence in deq1.
After one application of prev_permutation,
deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first prev_permutation, vector v1 is:
v1 = ( -3 -2 0 3 2 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 2 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 1 2 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 3 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 3 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 1 3 ).
```

## <a name="push_heap"></a>push_heap

Fügt ein Element hinzu, das sich am Ende eines Bereichs in einem vorhandenen Heap befindet, der aus den vorherigen Elementen im Bereich besteht.

```cpp
template<class RandomAccessIterator>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements im Heap adressiert.

*Letzter*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der in einen Heap konvertiert werden soll.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="remarks"></a>Bemerkungen

Zunächst muss das Element ans Ende eines vorhandenen Heaps bewegt werden; danach kann der Algorithmus verwendet werden, um das Element dem vorhanden Heap hinzuzufügen.

Heaps haben zwei Eigenschaften:

- Das erste Element ist immer das größte.

- Elemente können in logarithmischer Zeit hinzugefügt oder entfernt werden.

Heaps sind ideal zum Implementieren von Vorrangwarteschlangen. Sie werden beim Implementieren des C++-Standardbibliothekadapters [priority_queue-Klasse](../standard-library/priority-queue-class.md) verwendet.

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Der Bereich, ohne das neu am Ende hinzugefügte Element, muss ein Heap sein.

Die Komplexität ist logarithmisch und erfordert höchstens `log(last - first)` Vergleiche.

### <a name="example"></a>Beispiel

```cpp
// alg_push_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 1 ; i <= 9 ; i++ )
        v1.push_back( i );

    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with default less than ordering
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Add an element to the heap
    v1.push_back( 10 );
    cout << "The heap v1 with 10 pushed back is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    push_heap( v1.begin( ), v1.end( ) );
    cout << "The reheaped v1 with 10 added is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << endl;

    // Make v1 a heap with greater than ordering
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater-than heaped version of v1 is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    v1.push_back(0);
    cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater than reheaped v1 with 11 added is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="random_shuffle"></a>random_shuffle

Die Std:: Random_shuffle ()-Funktion ist veraltet, ersetzt durch [Std:: shuffle](../standard-library/algorithm-functions.md#shuffle). Ein Codebeispiel und weitere Informationen finden Sie unter [\<Random >](../standard-library/random.md) und im Stack Overflow Beitrag [Warum sind Std:: random_shuffle-Methoden in c++ 14 veraltet?](https://go.microsoft.com/fwlink/p/?linkid=397954).

## <a name="remove"></a>aufgeh

Eliminiert einen angegebenen Wert von einem angegebenen Bereich, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen und das Ende eines neuen Bereichs zurückzugeben, der den angegebenen Wert nicht enthält.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator remove(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Vorwärtsiterator zur Position des ersten Elements in dem Bereich, aus dem Elemente entfernt werden.

*Letzter*\
Ein Vorwärtsiterator zur ersten Position hinter dem letzten Element in dem Bereich, aus dem Elemente entfernt werden.

*value*\
Der Wert, der aus dem Bereich entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Vorwärtsiterator für die neue Endposition des veränderten Bereichs, eine Position hinter dem letzten Element der verbleibenden Sequenz, die den angegebenen Wert nicht enthält.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Reihenfolge der nicht entfernten Elemente bleibt bestehen.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Komplexität ist linear; Es gibt (`last` - `first`) Vergleiche auf Gleichheit.

Die [List-Klasse](../standard-library/list-class.md) verfügt über eine effizientere Member-Funktions Version `remove`, die auch Zeiger neu verknüpft.

### <a name="example"></a>Beispiel

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value of 7
    new_end = remove ( v1.begin( ), v1.end( ), 7 );

    cout << "Vector v1 with value 7 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To change the sequence size, use erase
    v1.erase (new_end, v1.end( ) );

    cout << "Vector v1 resized with value 7 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_copy"></a>remove_copy

Kopiert Elemente aus einem Quellbereich in einen Zielbereich, ohne dass Elemente eines angegebenen Werts kopiert werden und ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen und das Ende eines neuen Zielbereichs zurückzugeben.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 remove_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& value);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, aus dem Elemente entfernt werden.

*Letzter*\
Ein Eingabeiterator, der die Position hinter dem letzten Element in dem Bereich adressiert, aus dem Elemente entfernt werden.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements in dem Zielbereich adressiert, in den Elemente entfernt werden.

*value*\
Der Wert, der aus dem Bereich entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator, der die neue Endposition des Zielbereichs adressiert, sprich eine Position hinter dem letzten Element der Kopie der verbleibenden Sequenz, die den angegebenen Wert nicht enthält.

### <a name="remarks"></a>Bemerkungen

Die Quell- und Zielbereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Der Zielbereich muss über ausreichend Platz verfügen, um die verbleibenden Elemente zu enthalten, die nach dem Entfernen von Elementen des angegebenen Werts kopiert werden.

Die Reihenfolge der nicht entfernten Elemente bleibt bestehen.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Komplexität ist linear; Es gibt (`last` - `first`) Vergleiche auf Gleichheit und höchstens (`last` - `first`) Zuweisungen.

### <a name="example"></a>Beispiel

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle (v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:     ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value of 7
    new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );

    cout << "Vector v1 is left unchanged as ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_copy_if"></a>remove_copy_if

Kopiert Elemente aus einem Quellbereich in einen Zielbereich, ausgenommen Elemente, die ein Prädikat erfüllen. Elemente werden kopiert, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen. Gibt das Ende eines neuen Zielbereichs zurück.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator remove_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 remove_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, aus dem Elemente entfernt werden.

*Letzter*\
Ein Eingabeiterator, der die Position hinter dem letzten Element in dem Bereich adressiert, aus dem Elemente entfernt werden.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements in dem Zielbereich adressiert, in den Elemente entfernt werden.

*pred-* \
Das unäre Prädikat, das erfüllt werden muss, ist der Wert eines zu ersetzenden Elements.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator, der die neue Endposition des Zielbereichs adressiert, sprich eine Position hinter dem letzten Element der verbleibenden Sequenz, die die Elemente nicht enthält, die das Prädikat erfüllen.

### <a name="remarks"></a>Bemerkungen

Der Quellbereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Der Zielbereich muss über ausreichend Platz verfügen, um die verbleibenden Elemente zu enthalten, die nach dem Entfernen von Elementen des angegebenen Werts kopiert werden.

Die Reihenfolge der nicht entfernten Elemente bleibt bestehen.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Komplexität ist linear: Es gibt (`last` - `first`) Vergleiche auf Gleichheit und höchstens (`last` - `first`) Zuweisungen.

Informationen über das Verhalten dieser Funktionen finden Sie unter [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Beispiel

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:      ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value greater than 6
    new_end = remove_copy_if ( v1.begin( ), v1.end( ),
        v2.begin( ), greater6 );

    cout << "After the appliation of remove_copy_if to v1,\n "
         << "vector v1 is left unchanged as ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is a copy of v1 with values greater "
         << "than 6 removed:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_if"></a>remove_if

Eliminiert Elemente, die ein Prädikat aus einem angegebenen Bereich erfüllen, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen und das Ende eines neuen Bereichs zurückzugeben, der den angegebenen Wert nicht enthält.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der auf die Position des ersten Elements in dem Bereich verweist, aus dem Elemente entfernt werden.

*Letzter*\
Ein Forward-Iterator, der auf die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich verweist, aus dem Elemente entfernt werden.

*pred-* \
Das unäre Prädikat, das erfüllt werden muss, ist der Wert eines zu ersetzenden Elements.

### <a name="return-value"></a>Rückgabewert

Ein Vorwärtsiterator für die neue Endposition des veränderten Bereichs, eine Position hinter dem letzten Element der verbleibenden Sequenz, die den angegebenen Wert nicht enthält.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Reihenfolge der nicht entfernten Elemente bleibt bestehen.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Komplexität ist linear: Es gibt (`last` - `first`) Vergleiche auf Gleichheit.

List hat eine effizientere Memberfunktion von remove, durch die Zeiger neu verlinkt werden.

### <a name="example"></a>Beispiel

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements satisfying predicate greater6
    new_end = remove_if (v1.begin( ), v1.end( ), greater6 );

    cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To change the sequence size, use erase
    v1.erase (new_end, v1.end( ) );

    cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace"></a>Stelle

Überprüft jedes Element in einem Bereich und ersetzt es, sofern es einem angegebenen Wert entspricht.

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void replace(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der auf die Position des ersten Elements in dem Bereich verweist, aus dem Elemente ersetzt werden.

*Letzter*\
Ein Forward-Iterator, der auf die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich verweist, aus dem Elemente ersetzt werden.

*OLDVAL* -\
Der alte Wert der ersetzten Elemente.

*NewVal* -\
Der neue Wert, der den Elementen mit dem alten Wert zugewiesen wird.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Reihenfolge der nicht ersetzten Elemente bleibt bestehen.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Komplexität ist linear; Es gibt (`last` - `first`) Vergleiche auf Gleichheit und höchstens (`last` - `first`) Zuweisungen von neuen Werten.

### <a name="example"></a>Beispiel

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle (v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements with a value of 7 with a value of 700
    replace (v1.begin( ), v1.end( ), 7 , 700);

    cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_copy"></a>replace_copy

Überprüft jedes Element in einem Quellbereich und ersetzt es, sofern es einem angegebenen Wert entspricht, während das Ergebnis in einen neuen Zielbereich kopiert wird.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 replace_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der auf die Position des ersten Elements in dem Bereich verweist, aus dem Elemente ersetzt werden.

*Letzter*\
Ein Eingabeiterator, der auf die Position hinter dem letzten Element in dem Bereich verweist, aus dem Elemente ersetzt werden.

*Ergebnis*\
Ein Ausgabeiterator, der auf das erste Element im Zielbereich verweist, in den die geänderte Sequenz von Elementen kopiert wird.

*OLDVAL* -\
Der alte Wert der ersetzten Elemente.

*NewVal* -\
Der neue Wert, der den Elementen mit dem alten Wert zugewiesen wird.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die Position hinter dem letzten Element im Zielbereich verweist, in den die geänderte Sequenz von Elementen kopiert wird.

### <a name="remarks"></a>Bemerkungen

Die Quell- und Zielbereiche, auf die verwiesen wird, dürfen sich nicht überlappen und müssen gültig sein: Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Reihenfolge der nicht ersetzten Elemente bleibt bestehen.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Komplexität ist linear: Es gibt (`last` - `first`) Vergleiche auf Gleichheit und höchstens (`last` - `first`) Zuweisungen von neuen Werten.

### <a name="example"></a>Beispiel

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (15);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );

    int iii;
    for ( iii = 0 ; iii <= 15 ; iii++ )
        v1.push_back( 1 );

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in one part of a vector with a value of 7
    // with a value of 70 and copy into another part of the vector
    replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);

    cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in a vector with a value of 70
    // with a value of 1 and copy into a list
    replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);

    cout << "The list copy L1 of v1 with the value 0 replacing "
            << "that of 7 is:\n ( " ;
    for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
        cout << *L_Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_copy_if"></a>replace_copy_if

Überprüft jedes Element in einem Quellbereich und ersetzt es, sofern es ein angegebenes Prädikat erfüllt, während das Ergebnis in einen neuen Zielbereich kopiert wird.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate, class Type>
ForwardIterator2 replace_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Eingabeiterator, der auf die Position des ersten Elements in dem Bereich verweist, aus dem Elemente ersetzt werden.

*Letzter*\
Ein Eingabeiterator, der auf die Position hinter dem letzten Element in dem Bereich verweist, aus dem Elemente ersetzt werden.

*Ergebnis*\
Ein Ausgabeiterator, der auf die Position des ersten Elements in dem Zielbereich verweist, in den Elemente kopiert werden.

*pred-* \
Das unäre Prädikat, das erfüllt werden muss, ist der Wert eines zu ersetzenden Elements.

*value*\
Der neue Wert, der den Elementen zugewiesen wird, deren alter Wert das Prädikat erfüllt.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die Position hinter dem letzten Element im Zielbereich verweist, in den die geänderte Sequenz von Elementen kopiert wird.

### <a name="remarks"></a>Bemerkungen

Die Quell- und Zielbereiche, auf die verwiesen wird, dürfen sich nicht überlappen und müssen gültig sein: Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Reihenfolge der nicht ersetzten Elemente bleibt bestehen.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Komplexität ist linear; Es gibt (`last` - `first`) Vergleiche auf Gleichheit und höchstens (`last` - `first`) Zuweisungen von neuen Werten.

### <a name="example"></a>Beispiel

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (13);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );

    int iii;
    for ( iii = 0 ; iii <= 13 ; iii++ )
        v1.push_back( 1 );

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements with a value of 7 in the 1st half of a vector
    // with a value of 70 and copy it into the 2nd half of the vector
    replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,
        greater6 , 70);

    cout << "The vector v1 with values of 70 replacing those greater"
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in a vector with a value of 70
    // with a value of 1 and copy into a list
    replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),
        greater6 , -1 );

    cout << "A list copy of vector v1 with the value -1\n replacing "
        << "those greater than 6 is:\n ( " ;
    for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
        cout << *L_Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_if"></a>replace_if

Überprüft jedes Element in einem Bereich und ersetzt es, sofern es das angegebene Prädikat erfüllt.

```cpp
template<class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der auf die Position des ersten Elements in dem Bereich verweist, aus dem Elemente ersetzt werden.

*Letzter*\
Ein Iterator, der auf die Position hinter dem letzten Element in dem Bereich verweist, aus dem Elemente ersetzt werden.

*pred-* \
Das unäre Prädikat, das erfüllt werden muss, ist der Wert eines zu ersetzenden Elements.

*value*\
Der neue Wert, der den Elementen zugewiesen wird, deren alter Wert das Prädikat erfüllt.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Reihenfolge der nicht ersetzten Elemente bleibt bestehen.

Der Algorithmus `replace_if` ist eine Generalisierung des Algorithmus `replace`und ermöglicht das Angeben eines beliebigen Prädikats anstelle von Gleichheit mit einem angegebenen konstanten Wert.

Der zur Bestimmung des Gleichheitszustands zwischen Elementen verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Komplexität ist linear: Es gibt (`last` - `first`) Vergleiche auf Gleichheit und höchstens (`last` - `first`) Zuweisungen von neuen Werten.

### <a name="example"></a>Beispiel

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements satisfying the predicate greater6
    // with a value of 70
    replace_if ( v1.begin( ), v1.end( ), greater6 , 70);

    cout << "The vector v1 with a value 70 replacing those\n "
         << "elements satisfying the greater6 predicate is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="reverse"></a>umgekehr

Kehrt die Reihenfolge der Elemente innerhalb eines Bereichs um.

```cpp
template<class BidirectionalIterator>
void reverse(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator>
void reverse(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein bidirektionaler Iterator, der auf die Position des ersten Elements im Bereich verweist, in dem die Elemente permutiert werden.

*Letzter*\
Ein bidirektionaler Iterator, der auf die Position hinter dem letzten Element im Bereich verweist, in dem die Elemente permutiert werden.

### <a name="remarks"></a>Bemerkungen

Der Quellbereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

### <a name="example"></a>Beispiel

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Reverse the elements in the vector
    reverse (v1.begin( ), v1.end( ) );

    cout << "The modified vector v1 with values reversed is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 0 1 2 3 4 5 6 7 8 9 ).
The modified vector v1 with values reversed is:
( 9 8 7 6 5 4 3 2 1 0 ).
```

## <a name="reverse_copy"></a>reverse_copy

Kehrt die Reihenfolge der Elemente in einem Quellbereich beim Kopieren in einen Zielbereich um.

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator last,
    OutputIterator result);

template<class ExecutionPolicy, class BidirectionalIterator, class ForwardIterator>
ForwardIterator reverse_copy(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    ForwardIterator result);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein bidirektionaler Iterator, der auf die Position des ersten Elements im Quellbereich verweist, in dem die Elemente permutiert werden.

*Letzter*\
Ein bidirektionaler Iterator, der auf die Position hinter dem letzten Element im Quellbereich verweist, in dem die Elemente permutiert werden.

*Ergebnis*\
Ein Ausgabeiterator, der auf die Position des ersten Elements in dem Zielbereich verweist, in den Elemente kopiert werden.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der auf die Position hinter dem letzten Element im Zielbereich verweist, in den die geänderte Sequenz von Elementen kopiert wird.

### <a name="remarks"></a>Bemerkungen

Die Quell- und Zielbereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

### <a name="example"></a>Beispiel

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2( 10 );
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Reverse the elements in the vector
    reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );

    cout << "The copy v2 of the reversed vector v1 is:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "The original vector v1 remains unmodified as:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="rotate"></a>Controller

Vertauscht die Elemente in zwei benachbarten Bereichen.

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator rotate(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im zu rotierenden Bereich adressiert.

*mittlere*\
Ein Forward-Iterator, der die Grenzen innerhalb des Bereichs definiert, der die Position des ersten Elements im zweiten Teil des Bereichs adressiert und dessen Elemente mit denen im ersten Teil des Bereichs ausgetauscht werden sollen.

*Letzter*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu rotierenden Bereich adressiert.

### <a name="remarks"></a>Bemerkungen

Die Bereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Komplexität ist linear, wobei höchstens (`last` - `first`) ausgetauscht werden.

### <a name="example"></a>Beispiel

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
    deque<int>::iterator d1Iter1;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
    {
        d1.push_back( ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
    cout << "After rotating, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) ) {
        rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
        cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
        for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
            cout << *d1Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).
The original deque d1 is ( 0 1 2 3 4 5 ).
After the rotation of a single deque element to the back,
d1 is   ( 1 2 3 4 5 0 ).
After the rotation of a single deque element to the back,
d1 is   ( 2 3 4 5 0 1 ).
After the rotation of a single deque element to the back,
d1 is   ( 3 4 5 0 1 2 ).
After the rotation of a single deque element to the back,
d1 is   ( 4 5 0 1 2 3 ).
After the rotation of a single deque element to the back,
d1 is   ( 5 0 1 2 3 4 ).
After the rotation of a single deque element to the back,
d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="rotate_copy"></a>rotate_copy

Vertauscht die Elemente in zwei benachbarten Bereiche innerhalb eines Quellbereichs und kopiert das Ergebnis in einen Zielbereich.

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 rotate_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 middle,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im zu rotierenden Bereich adressiert.

*mittlere*\
Ein Forward-Iterator, der die Grenzen innerhalb des Bereichs definiert, der die Position des ersten Elements im zweiten Teil des Bereichs adressiert und dessen Elemente mit denen im ersten Teil des Bereichs ausgetauscht werden sollen.

*Letzter*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu rotierenden Bereich adressiert.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Element im Zielbereich adressiert.

### <a name="remarks"></a>Bemerkungen

Die Bereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Komplexität ist linear, wobei höchstens (`last` - `first`) ausgetauscht werden.

### <a name="example"></a>Beispiel

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1 , v2 ( 9 );
    deque<int> d1 , d2 ( 6 );
    vector<int>::iterator v1Iter , v2Iter;
    deque<int>::iterator d1Iter , d2Iter;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
        d1.push_back( ii );

    cout << "Vector v1 is ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
    cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
    for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
        cout << *v2Iter << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
        cout << *d1Iter << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) )
    {
        rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
        cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
        for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
            cout << *d2Iter << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

## <a name="sample"></a>Blutprobe

```cpp
template<class PopulationIterator, class SampleIterator, class Distance, class UniformRandomBitGenerator>
SampleIterator sample(
    PopulationIterator first,
    PopulationIterator last,
    SampleIterator out,
    Distance n,
    UniformRandomBitGenerator&& g);
```

## <a name="search"></a>Such

Sucht das erste Vorkommen einer Sequenz in einem Zielbereich, dessen Elemente gleich den Elementen in einer bestimmten Elementsequenz sind oder dessen Elemente äquivalent sind mit den Elementen in der angegebenen Sequenz, wie durch ein binäres Prädikat festgelegt.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template <class ForwardIterator, class Searcher>
ForwardIterator search(
    ForwardIterator first,
    ForwardIterator last,
    const Searcher& searcher);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Last1*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*First2*\
Ein Forward-Iterator, der die Position des ersten Elements im abzugleichenden Bereich adressiert.

*Last2*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im abzugleichenden Bereich adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die zu erfüllende Bedingung definiert, wenn zwei Elemente als gleichwertig akzeptiert werden. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

*Searcher* -\
Der Searcher, der das zu suchende Muster und den zu verwendenden Suchalgorithmus kapselt. Weitere Informationen zu searchern finden Sie unter [default_searcher Klasse](default-searcher-class.md), [boyer_moore_horspool_searcher Klasse](boyer-moore-horspool-searcher-class.md)und [boyer_moore_searcher Klasse](boyer-moore-searcher-class.md).

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator, der die Position des ersten Elements der ersten Untersequenz adressiert, die der angegebenen Sequenz entspricht oder die wie von einem binären Prädikat angegeben äquivalent ist.

### <a name="remarks"></a>Bemerkungen

Der zur Bestimmung des Gleichheitszustands zwischen einem Element und dem angegebenen Wert verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Die Bereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die durchschnittliche Komplexität ist bezüglich der Größe des durchsuchten Bereichs linear; im schlimmsten Fall ist die Komplexität auch bezüglich der Größe der zu suchenden Sequenz linear.

### <a name="example"></a>Beispiel

```cpp
// alg_search.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice (int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 4 ; ii <= 5 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for first match to L1 under identity
    vector<int>::iterator result1;
    result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = search (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent\n to those in v2 under the binary "
            << "predicate twice\n and the first one begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 20 25 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 4.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="search_n"></a>search_n

Sucht nach der ersten Untersequenz in einem Bereich, der aus einer angegebenen Anzahl von Elementen besteht, die einen bestimmten Wert oder eine Beziehung zu diesem durch ein binäres Prädikat angegebenen Wert haben.

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type, class BinaryPredicate>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Forward-Iterator, der die Position des ersten Elements im zu durchsuchenden Bereich adressiert.

*Last1*\
Ein Forward-Iterator, der die Position hinter dem letzten Element im zu durchsuchenden Bereich adressiert.

*Anzahl*\
Die Größe der zu suchenden Untersequenz.

*value*\
Der Wert der Elemente in der durchsuchten Sequenz.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die zu erfüllende Bedingung definiert, wenn zwei Elemente als gleichwertig akzeptiert werden. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator, der die Position des ersten Elements der ersten Untersequenz adressiert, die der angegebenen Sequenz entspricht oder die wie von einem binären Prädikat angegeben äquivalent ist.

### <a name="remarks"></a>Bemerkungen

Der zur Bestimmung des Gleichheitszustands zwischen einem Element und dem angegebenen Wert verwendete `operator==` muss eine Äquivalenzrelation zwischen zwei Operanden vorgeben.

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Komplexität ist bezüglich der Größe des Gesuchten linear.

### <a name="example"></a>Beispiel

```cpp
// alg_search_n.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is 1/2 of the first
bool one_half ( int elem1, int elem2 )
{
    return elem1 == 2 * elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 5 );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 10 );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Searching v1 for first match to (5 5 5) under identity
    vector<int>::iterator result1;
    result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

    if ( result1 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1."
            << endl;
    else
        cout << "There is at least one match of a sequence ( 5 5 5 )"
            << "\n in v1 and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for first match to (5 5 5) under one_half
    vector<int>::iterator result2;
    result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );

    if ( result2 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1"
            << " under the equivalence predicate one_half." << endl;
    else
        cout << "There is a match of a sequence ( 5 5 5 ) "
            << "under the equivalence\n predicate one_half "
            << "in v1 and the first one begins at "
            << "position "<< result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )
There is at least one match of a sequence ( 5 5 5 )
in v1 and the first one begins at position 6.
There is a match of a sequence ( 5 5 5 ) under the equivalence
predicate one_half in v1 and the first one begins at position 15.
```

## <a name="set_difference"></a>set_difference

Vereinigt alle Elemente, die zu dem einen, jedoch nicht zu einem anderen sortierten Quellbereich gehören, in einen einzelnen, sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der den Unterschied der beiden Quellbereiche repräsentiert.

*Last1*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der den Unterschied der beiden Quellbereiche repräsentiert.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der den Unterschied der beiden Quellbereiche repräsentiert.

*Last2*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der den Unterschied der beiden Quellbereiche repräsentiert.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert, in den die beiden Quellbereiche kombiniert werden sollen. Dieser Zielbereich wird sortiert und repräsentiert den Unterschied der beiden Quellbereiche.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das binäre Prädikat akzeptiert zwei Argumente und sollte **true** zurückgeben, wenn das erste Element kleiner als das zweite Element ist, andernfalls wird **false** zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Element im sortierten Zielbereich adressiert, der den Unterschied der beiden Quellbereiche repräsentiert.

### <a name="remarks"></a>Bemerkungen

Die sortierten Quellbereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb jeder Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Der Zielbereich sollte keinen der Quellbereiche überlappen und groß genug sein, um den ersten Quellbereich zu enthalten.

Die sortierten Quellbereiche müssen als Vorbedingung zur Anwendung des `set_difference` -Algorithmus entsprechend der gleichen Reihenfolge sortiert werden, die vom Algorithmus für die Sortierung der kombinierten Bereiche verwendet wird.

Der Vorgang ist stabil, da die relative Reihenfolge der Elemente innerhalb jedes Bereichs im Zielbereich beibehalten wird. Die Quellbereiche werden nicht durch den merge-Algorithmus geändert.

Die Werttypen der Eingabeiteratoren müssen mit „kleiner als“ vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig (in dem Sinne, dass keines kleiner als das andere ist) oder eines als kleiner als das andere bestimmt werden können. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Wenn in beiden Quellbereichen äquivalente Elemente vorhanden sind, stehen im Zielbereich die Elemente aus dem ersten Bereich vor den Elementen aus dem zweiten Bereich. Wenn die Quellbereiche Duplikate eines Elements enthalten, sodass sich im ersten Quellbereich mehr Elemente befinden als im zweiten, enthält der Zielbereich die Zahl, um die die Vorkommen dieser Elemente im ersten Quellbereich die Vorkommen dieser Elemente im zweiten Quellbereich übersteigen.

Die Komplexität des Algorithmus ist bei höchstens `2 * ((last1 - first1) - (last2 - first2)) - 1` vergleichen für nicht leere Quellbereiche linear.

### <a name="example"></a>Beispiel

```cpp
// alg_set_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a difference in asscending
    // order with the default binary predicate less<int>( )
    Result1 = set_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a difference in descending
    // order specify binary predicate greater<int>( )
    Result2 = set_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_intersection"></a>set_intersection

Vereinigt alle Elemente, die zu beiden sortierten Quellbereichen gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result);

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der die Schnittmenge der beiden Quellbereiche repräsentiert.

*Last1*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der die Schnittmenge der beiden Quellbereiche repräsentiert.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der die Schnittmenge der beiden Quellbereiche repräsentiert.

*Last2*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der die Schnittmenge der beiden Quellbereiche repräsentiert.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert, zu dem die beiden Quellbereiche kombiniert werden sollen. Dieser Zielbereich wird sortiert und repräsentiert die Schnittmenge der beiden Quellbereiche.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das binäre Prädikat akzeptiert zwei Argumente und sollte **true** zurückgeben, wenn das erste Element kleiner als das zweite Element ist, andernfalls wird **false** zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Element im sortierten Zielbereich adressiert, der die Schnittmenge der beiden Quellbereiche repräsentiert.

### <a name="remarks"></a>Bemerkungen

Die sortierten Quellbereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb jeder Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Der Zielbereich sollte keinen der Quellbereiche überlappen und groß genug sein, um den Zielbereich zu enthalten.

Die sortierten Quellbereiche müssen als Vorbedingung zur Anwendung des merge-Algorithmus entsprechend der gleichen Reihenfolge sortiert werden, die vom Algorithmus für die Sortierung der kombinierten Bereiche verwendet wird.

Der Vorgang ist stabil, da die relative Reihenfolge der Elemente innerhalb jedes Bereichs im Zielbereich beibehalten wird. Die Quellbereiche werden durch den Algorithmus nicht geändert.

Die Werttypen der Eingabeiteratoren müssen mit „kleiner als“ vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig (in dem Sinne, dass keines kleiner als das andere ist) oder eines als kleiner als das andere bestimmt werden können. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Wenn in beiden Quellbereichen äquivalente Elemente vorhanden sind, stehen im Zielbereich die Elemente aus dem ersten Bereich vor den Elementen aus dem zweiten Bereich. Wenn die Quellbereiche Duplikate eines Element enthalten, wird der Zielbereich die maximale Anzahl dieser Elemente enthalten, die in beiden Quellbereichen auftreten.

Die Komplexität des Algorithmus ist bei höchstens `2 * ((last1 - first1) + (last2 - first2)) - 1` vergleichen für nicht leere Quellbereiche linear.

### <a name="example"></a>Beispiel

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into an intersection in asscending order with the
    // default binary predicate less<int>( )
    Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Intersection of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into an intersection in descending order, specify
    // binary predicate greater<int>( )
    Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Intersection of source ranges with binary predicate"
            << " greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into an intersection applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Intersection of source ranges with binary predicate "
            << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a>set_symmetric_difference

Vereinigt alle Elemente, die zu einem, jedoch nicht zu beiden sortierten Quellbereichen gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der den symmetrischen Unterschied der beiden Quellbereiche repräsentiert.

*Last1*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der den symmetrischen Unterschied der beiden Quellbereiche repräsentiert.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der den symmetrischen Unterschied der beiden Quellbereiche repräsentiert.

*Last2*\
Ein Eingabeiterator, der die Position hinter den letzten Element im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der den symmetrischen Unterschied der beiden Quellbereiche repräsentiert.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert, zu dem die beiden Quellbereiche kombiniert werden sollen. Dieser Zielbereich wird sortiert und repräsentiert den symmetrischen Unterschied der beiden Quellbereiche.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das binäre Prädikat akzeptiert zwei Argumente und sollte **true** zurückgeben, wenn das erste Element kleiner als das zweite Element ist, andernfalls wird **false** zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Element im sortierten Zielbereich adressiert, der den symmetrischen Unterschied der beiden Quellbereiche repräsentiert.

### <a name="remarks"></a>Bemerkungen

Die sortierten Quellbereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb jeder Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Der Zielbereich sollte keinen der Quellbereiche überlappen und groß genug sein, um den Zielbereich zu enthalten.

Die sortierten Quellbereiche müssen als Vorbedingung zur Anwendung des `merge*` -Algorithmus entsprechend der gleichen Reihenfolge sortiert werden, die vom Algorithmus für die Sortierung der kombinierten Bereiche verwendet wird.

Der Vorgang ist stabil, da die relative Reihenfolge der Elemente innerhalb jedes Bereichs im Zielbereich beibehalten wird. Die Quellbereiche werden nicht durch den merge-Algorithmus geändert.

Die Werttypen der Eingabeiteratoren müssen mit „kleiner als“ vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig (in dem Sinne, dass keines kleiner als das andere ist) oder eines als kleiner als das andere bestimmt werden können. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Wenn in beiden Quellbereichen äquivalente Elemente vorhanden sind, stehen im Zielbereich die Elemente aus dem ersten Bereich vor den Elementen aus dem zweiten Bereich. Wenn die Quellbereiche Duplikate eines Elements enthalten, enthält der Zielbereich den absoluten Wert der Zahl, um die die Vorkommen jener Elemente in einem der Quellbereich die Vorkommen dieser Elemente im zweiten Quellbereich übersteigen.

Die Komplexität des Algorithmus ist bei höchstens `2 * ((last1 - first1) - (last2 - first2)) - 1` vergleichen für nicht leere Quellbereiche linear.

### <a name="example"></a>Beispiel

```cpp
// alg_set_sym_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in ascending
    // order with the default binary predicate less<int>( )
    Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_symmetric_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in descending
    // order, specify binary predicate greater<int>( )
    Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_symmetric_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_symmetric_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_union"></a>set_union

Vereinigt alle Elemente, die mindestens zu einem der beiden sortierten Quellbereiche gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der die Verbindung der beiden Quellbereiche repräsentiert.

*Last1*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im ersten der beiden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der die Verbindung der beiden Quellbereiche repräsentiert.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der die Verbindung der beiden Quellbereiche repräsentiert.

*Last2*\
Ein Eingabeiterator, der die Position hinter dem letzten Element im zweiten der beiden aufeinanderfolgenden sortierten Quellbereiche adressiert, die kombiniert und zu einem einzelnen Bereich sortiert werden sollen, der die Verbindung der beiden Quellbereiche repräsentiert.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert, zu dem die beiden Quellbereiche kombiniert werden sollen. Dieser Zielbereich wird sortiert und repräsentiert die Verbindung der beiden Quellbereiche.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Das binäre Prädikat akzeptiert zwei Argumente und sollte **true** zurückgeben, wenn das erste Element kleiner als das zweite Element ist, andernfalls wird **false** zurückgegeben.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Element im sortierten Zielbereich adressiert, der die Verbindung der beiden Quellbereiche repräsentiert.

### <a name="remarks"></a>Bemerkungen

Die sortierten Quellbereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb jeder Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Der Zielbereich sollte keinen der Quellbereiche überlappen und groß genug sein, um den Zielbereich zu enthalten.

Die sortierten Quellbereiche müssen als Vorbedingung zur Anwendung des `merge` -Algorithmus entsprechend der gleichen Reihenfolge sortiert werden, die vom Algorithmus für die Sortierung der kombinierten Bereiche verwendet wird.

Der Vorgang ist stabil, da die relative Reihenfolge der Elemente innerhalb jedes Bereichs im Zielbereich beibehalten wird. Die Quellbereiche werden nicht durch den Algorithmus `merge`geändert.

Die Werttypen der Eingabeiteratoren müssen mit „kleiner als“ vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig (in dem Sinne, dass keines kleiner als das andere ist) oder eines als kleiner als das andere bestimmt werden können. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen. Wenn in beiden Quellbereichen äquivalente Elemente vorhanden sind, stehen im Zielbereich die Elemente aus dem ersten Bereich vor den Elementen aus dem zweiten Bereich. Wenn die Quellbereiche Duplikate eines Element enthalten, wird der Zielbereich die maximale Anzahl dieser Elemente enthalten, die in beiden Quellbereichen auftreten.

Die Komplexität des Algorithmus ist mit höchstens `2 * ((last1 - first1) - (last2 - first2)) - 1` vergleichen linear.

### <a name="example"></a>Beispiel

```cpp
// alg_set_union.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a union in ascending order with the default
        // binary predicate less<int>( )
    Result1 = set_union ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Union of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a union in descending order, specify binary
    // predicate greater<int>( )
    Result2 = set_union ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Union of source ranges with binary predicate greater "
         << "specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a union applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_union ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Union of source ranges with binary predicate "
         << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="shuffle"></a>Gedicht

Mischt (ordnet) Elemente für einen gegebenen Bereich mithilfe eines Zufallszahlengenerators.

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(
    RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein Iterator für das erste Element im zu mischenden Bereich, inklusiv. Muss die Anforderungen von `RandomAccessIterator` und `ValueSwappable` erfüllen.

*Letzter*\
Ein Iterator für das letzte Element im zu mischenden Bereich, exklusiv. Muss die Anforderungen von `RandomAccessIterator` und `ValueSwappable` erfüllen.

*gen* -\
Der Zufallszahlengenerator, den die `shuffle()`-Funktion für den Vorgang verwendet. Muss die Anforderungen eines `UniformRandomNumberGenerator` erfüllen.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen und ein Codebeispiel mit `shuffle()` finden Sie unter [\<random>](../standard-library/random.md).

## <a name="sort"></a>Gefährtin

Ordnet die Elemente in einem angegebenen Bereich in einer aufsteigenden Reihenfolge oder gemäß eines Sortierkriteriums an, das von einem binären Prädikat angegeben wird.

```cpp
template<class RandomAccessIterator>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*Letzter*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der sortiert werden soll.

*pred-* \
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das von aufeinanderfolgenden Elementen in der Reihenfolge erfüllt werden soll. Dieses binäre Prädikat übernimmt zwei Argumente und gibt **true** zurück, wenn die beiden Argumente in der richtigen Reihenfolge vorliegen, andernfalls **false** . Diese Vergleichoperatorfunktion muss eine strikte schwache Sortierung auf Elementenpaare der Sequenz anwenden. Weitere Informationen finden Sie unter [Algorithmen](../standard-library/algorithms.md).

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Wenn keins kleiner als das andere ist, sind Elemente äquivalent, aber nicht unbedingt gleich. Der Algorithmus `sort` ist nicht stabil und stellt deshalb nicht sicher, dass die relative Sortierung equivalenter Elemente beibehalten wird. Der Algorithmus `stable_sort` behält diese ursprüngliche Sortierung bei.

Der Durchschnitt einer Sortier Komplexität ist `O( N log N )`, wobei *N* = *zuletzt* -  *.*

### <a name="example"></a>Beispiel

```cpp
// alg_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
    {
        v1.push_back( 2 * ii + 1 );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    sort( v1.begin( ), v1.end( ) );
    cout << "Sorted vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order. specify binary predicate
    sort( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "Resorted (greater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    sort( v1.begin( ), v1.end( ), UDgreater );
    cout << "Resorted (UDgreater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
```

## <a name="sort_heap"></a>sort_heap

Konvertiert einen Heap in einen sortierten Bereich.

```cpp
template<class RandomAccessIterator>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements im Zielheap adressiert.

*Letzter*\
Ein zufälliger Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im Zielheap adressiert.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt bei **Erfüllung true** zurück und **false** , wenn es nicht erfüllt wird.

### <a name="remarks"></a>Bemerkungen

Heaps haben zwei Eigenschaften:

- Das erste Element ist immer das größte.

- Elemente können in logarithmischer Zeit hinzugefügt oder entfernt werden.

Nach der Anwendung dieses Logarithmus ist der Bereich, auf den er angewendet wurde, kein Heap mehr.

Dies ist keine stabile Sortierung, da die relative Reihenfolge äquivalenter Elemente nicht unbedingt beibehalten wird.

Heaps sind ideal zum Implementieren von Vorrangwarteschlangen. Sie werden beim Implementieren des C++-Standardbibliothekadapters [priority_queue-Klasse](../standard-library/priority-queue-class.md) verwendet.

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Komplexität ist höchstens `N log N`, bei dem *N* = *zuletzt* -  *.*

### <a name="example"></a>Beispiel

```cpp
// alg_sort_heap.cpp
// compile with: /EHsc
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>
#include <string>
#include <vector>
using namespace std;

void print(const string& s, const vector<int>& v)
{
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i)
    {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main()
{
    vector<int> v;
    for (int i = 1; i <= 9; ++i)
    {
        v.push_back(i);
    }
    print("Initially", v);

    random_shuffle(v.begin(), v.end());
    print("After random_shuffle", v);

    make_heap(v.begin(), v.end());
    print("     After make_heap", v);

    sort_heap(v.begin(), v.end());
    print("     After sort_heap", v);

    random_shuffle(v.begin(), v.end());
    print("             After random_shuffle", v);

    make_heap(v.begin(), v.end(), greater<int>());
    print("After make_heap with greater<int>", v);

    sort_heap(v.begin(), v.end(), greater<int>());
    print("After sort_heap with greater<int>", v);
}
```

## <a name="stable_partition"></a>stable_partition

Klassifiziert Elemente in einem Bereich in zwei zusammenhanglose Sätze, wobei die Elemente, die ein unäres Prädikat erfüllen, direkt den Elementen vorausgehen, die es nicht erfüllen können. Die relative Reihenfolge der äquivalenten Elemente wird dabei beibehalten.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred );

template<class ExecutionPolicy, class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein bidirektionaler Iterator, der die Position des ersten Elements in dem Bereich adressiert, der partitioniert werden soll.

*Letzter*\
Ein bidirektionaler Iterator, der die Position des ersten Elements direkt hinter dem letzten Element in dem Bereich adressiert, der partitioniert werden soll.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die Bedingung definiert, die erfüllt werden muss, wenn ein Element eingeordnet werden soll. Ein unäres Prädikat nimmt ein einzelnes Argument an und gibt bei **Erfüllung true** zurück, oder **false** , wenn es nicht erfüllt wird.

### <a name="return-value"></a>Rückgabewert

Ein bidirektionaler Iterator, der die Position des ersten Elements in dem Bereich adressiert, das die Prädikatbedingung nicht erfüllt.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Die Elemente *a* und *b* sind äquivalent, aber nicht unbedingt gleich, wenn beide `pred( a, b )` false sind und `pred( b, a )` false ist, wobei *pred* das vom Parameter angegebene Prädikat ist. Der `stable_partition` Algorithmus ist stabil und stellt sicher, dass die relative Reihenfolge der äquivalenten Elemente beibehalten wird. Der Algorithmus `partition` behält diese ursprüngliche Reihenfolge nicht unbedingt bei.

### <a name="example"></a>Beispiel

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

    int i;
    for ( i = 0 ; i <= 10 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 4 ; ii++ )
        v1.push_back( 5 );

    random_shuffle(v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Partition the range with predicate greater10
    result = stable_partition (v1.begin( ), v1.end( ), greater5 );
    cout << "The partitioned set of elements in v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "The first element in v1 to fail to satisfy the"
         << "\n predicate greater5 is: " << *result << "." << endl;
}
```

## <a name="stable_sort"></a>stable_sort

Ordnet die Elemente in einem angegebenen Bereich in einer aufsteigenden Reihenfolge oder gemäß eines Sortierkriteriums an, das von einem binären Prädikat angegeben wird, und behält die relative Reihenfolge der äquivalenten Elemente bei.

```cpp
template<class BidirectionalIterator>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last );

template<class BidirectionalIterator, class Compare>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Compare pred );

template<class ExecutionPolicy, class RandomAccessIterator>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein bidirektionaler Iterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*Letzter*\
Ein bidirektionaler Iterator, der die Position des ersten Elements in dem Bereich adressiert, der sortiert werden soll.

*pred-* \
Ein benutzerdefiniertes Prädikatfunktionsobjekt, das das Vergleichskriterium definiert, das von aufeinanderfolgenden Elementen in der Reihenfolge erfüllt werden soll. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="remarks"></a>Bemerkungen

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar.

Wenn keins kleiner als das andere ist, sind Elemente äquivalent, aber nicht unbedingt gleich. Der `sort` Algorithmus ist stabil und stellt sicher, dass die relative Reihenfolge der äquivalenten Elemente beibehalten wird.

Die Lauf Zeit Komplexität `stable_sort` hängt von der Menge des verfügbaren Arbeitsspeichers *ab. der*beste Fall (bei ausreichendem Arbeitsspeicher) ist jedoch `O(N log N)`, und der schlechteste Fall ist `O(N (log N)^2)`, bei dem *N* = *zuletzt* - . Normalerweise ist der `sort` Algorithmus deutlich schneller als `stable_sort`.

### <a name="example"></a>Beispiel

```cpp
// alg_stable_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater (int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    stable_sort(v1.begin( ), v1.end( ) );
    cout << "Sorted vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order, specify binary predicate
    stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "Resorted (greater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    stable_sort(v1.begin( ), v1.end( ), UDgreater );
    cout << "Resorted (UDgreater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
```

## <a name="swap"></a>Wechsel

Das erste Überschreiben tauscht die Werte zweier Objekte aus. Das zweite Überschreiben tauscht die Werte zwischen zwei Arrays von Objekten aus.

```cpp
template<class Type>
void swap(
    Type& left,
    Type& right);
template<class Type, size_t N>
void swap(
    Type (& left)[N],
    Type (& right)[N]);
```

### <a name="parameters"></a>Parameter

*Linker*\
Das erste Objekt, dessen Inhalte beim ersten Überschreiben ausgetauscht werden soll. Das erste Array von Objekten, dessen Inhalte beim zweiten Überschreiben ausgetauscht werden soll.

*Rechte*\
Das zweite Objekt, dessen Inhalt beim ersten Überschreiben ausgetauscht werden soll. Das zweite Array von Objekten, dessen Inhalte beim zweiten Überschreiben ausgetauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Die erste Überladung wurde dafür entwickelt, einzelne Objekte zu verarbeiten. Die zweite Überladung tauscht die Inhalte von Objekten zwischen zwei Arrays aus.

### <a name="example"></a>Beispiel

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

    for ( int i = 0 ; i <= 10 ; i++ )
    {
        v1.push_back( i );
    }

    for ( int ii = 0 ; ii <= 4 ; ii++ )
    {
        v2.push_back( 5 );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    swap( v1, v2 );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
Vector v2 is ( 5 5 5 5 5 ).
Vector v1 is ( 5 5 5 5 5 ).
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
```

## <a name="swap_ranges"></a>swap_ranges

Vertauscht die Elemente eines Bereichs mit den Elementen eines anderen gleich großen Bereichs.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Forward-Iterator, der die erste Position des ersten Bereichs anzeigt, dessen Elemente ausgetauscht werden sollen.

*Last1*\
Ein Forward-Iterator, der die erste Position direkt hinter der letzten Position des ersten Bereichs anzeigt, dessen Elemente ausgetauscht werden sollen.

*First2*\
Ein Forward-Iterator, der die erste Position des zweiten Bereichs anzeigt, dessen Elemente ausgetauscht werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator, der die erste Position direkt hinter der letzten Position des zweiten Bereichs anzeigt, dessen Elemente ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Bereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar. Der zweite Bereich muss so groß wie der erste Bereich sein.

Die Komplexität ist linear mit *Last1* - ausgeführten *First1* -Austausch Vorgängen. Wenn Elemente von Containern des selben Typen ausgetauscht werden, sollte die `swap`-Memberfunktion dieses Containers verwendet werden, da die Memberfunktion typischerweise eine konstante Komplexität hat.

### <a name="example"></a>Beispiel

```cpp
// alg_swap_ranges.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
    deque<int>::iterator d1Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =4 ; ii <= 9 ; ii++ )
    {
        d1.push_back( 6 );
    }

    cout << "Vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque d1 is  ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    swap_ranges ( v1.begin( ), v1.end( ), d1.begin( ) );

    cout << "After the swap_range, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "After the swap_range deque d1 is   ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 ).
Deque d1 is  ( 6 6 6 6 6 6 ).
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="transform"></a>Sin

Wendet ein angegebenes Funktionsobjekt auf jedes Element in einem Quellbereich oder auf ein Elementpaar aus zwei Quellbereichen an und kopiert die Rückgabewerte des Funktionsobjekts in einen Zielbereich.

```cpp
template<class InputIterator, class OutputIterator, class UnaryFunction>
OutputIterator transform(
    InputIterator first1,
    InputIterator last1,
    OutputIterator result,
    UnaryFunction func );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>
OutputIterator transform(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    OutputIterator result,
    BinaryFunction func );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryOperation>
ForwardIterator2 transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryOperation op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class BinaryOperation>
ForwardIterator transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*First1*\
Ein Eingabeiterator, der die Position des ersten Elements im ersten Quellbereich adressiert.

*Last1*\
Ein Eingabeiterator, der die Position des ersten Elements direkt hinter dem letzten Element im ersten bearbeiteten Quellbereich adressiert.

*First2*\
Ein Eingabeiterator, der die Position des ersten Elements im zweiten Quellbereich adressiert.

*Ergebnis*\
Ein Ausgabeiterator, der die Position des ersten Elements im Zielbereich adressiert.

*Func* -\
Ein benutzerdefiniertes unäres Objekt, das in der ersten Version des Algorithmus verwendet wird, die auf jedes Element im ersten Bereich angewendet wird, oder ein benutzerdefiniertes binäres Funktionsobjekt, das in der zweiten Version des Algorithmus verwendet wird, die paarweise in aufsteigender Reihenfolge auf die zwei Quellbereiche angewendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position direkt hinter dem letzten Element im Zielbereich adressiert, der die vom Funktionsobjekt umgewandelten Ausgabeelemente erhält.

### <a name="remarks"></a>Bemerkungen

Die Bereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb jeder Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein. Der Zielbereich muss groß genug sein, damit er den umgewandelten Quellbereich aufnehmen kann.

Wenn *Result* auf *First1* in der ersten Version des Algorithmus festgelegt wird, sind die Quell-und Zielbereiche identisch, und die Sequenz wird direkt geändert. Das *Ergebnis* adressiert jedoch möglicherweise nicht eine Position innerhalb des Bereichs [`first1` + 1, `last1`).

Die Komplexität ist linear, wobei höchstens (`last1` - `first1`) Vergleiche erfolgt.

### <a name="example"></a>Beispiel

```cpp
// alg_transform.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
    Type Factor;   // The value to multiply by
public:
    // Constructor initializes the value to multiply by
    MultValue ( const Type& value ) : Factor ( value ) { }

    // The function call for the element to be multiplied
    Type operator( ) ( Type& elem ) const
    {
        return elem * Factor;
    }
};

int main()
{
    using namespace std;
    vector<int> v1, v2 ( 7 ), v3 ( 7 );
    vector<int>::iterator Iter1, Iter2 , Iter3;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Modifying the vector v1 in place
    transform (v1.begin( ), v1.end( ), v1.begin( ), MultValue<int> ( 2 ) );
    cout << "The elements of the vector v1 multiplied by 2 in place gives:"
            << "\n v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using transform to multiply each element by a factor of 5
    transform ( v1.begin( ), v1.end( ), v2.begin( ), MultValue<int> ( 5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // The second version of transform used to multiply the
    // elements of the vectors v1mod & v2 pairwise
    transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin( ),
        multiplies<int>( ) );

    cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
            << "gives:\n v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a>gem

Entfernt doppelte Elemente, die in einem angegebenen Bereich nebeneinander angeordnet sind.

```cpp
template<class ForwardIterator>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Forward-Iterator, der die Position des ersten Elements im Bereich adressiert, der zum Entfernen von doppelten Elementen durchsucht werden soll.

*Letzter*\
Ein Forward-Iterator, der die Position des ersten Elements direkt hinter dem letzten Element im Bereich adressiert, der zum Entfernen von doppelten Elementen durchsucht werden soll.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die zu erfüllende Bedingung definiert, wenn zwei Elemente als gleichwertig akzeptiert werden. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator am neuen Ende der veränderten Sequenz, die keine aufeinanderfolgenden doppelten Elemente enthält, adressiert die Position direkt hinter dem letzten Element, das nicht entfernt wurde.

### <a name="remarks"></a>Bemerkungen

Beide Formen des Algorithmus entfernen das zweite Duplikat eines aufeinanderfolgenden Paars gleicher Elemente.

Der Vorgang des Algorithmus ist stabil, sodass die relative Reihenfolge der nicht gelöschten Elemente nicht geändert wird.

Der Bereich, auf den verwiesen wird, muss gültig sein. Alle Zeiger müssen dereferenzierbar sein und die letzte Position innerhalb der Sequenz ist von der ersten Position aus durch Zunahme erreichbar. die Anzahl der Elemente in der Sequenz wird vom Algorithmus nicht geändert `unique` und die Elemente hinter dem Ende der geänderten Sequenz sind dereferenzierbar, aber nicht angegeben.

Die Komplexität ist linear und erfordert `(last - first) - 1` Vergleiche.

List stellt die effizientere Memberfunktion „unique“ bereit, die möglicherweise besser funktioniert.

Diese Algorithmen können nicht auf einen assoziativen Container angewendet werden.

### <a name="example"></a>Beispiel

```cpp
// alg_unique.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 == elem2;
};

int main()
{
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
            v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( 5 );
        v1.push_back( -5 );
    }

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
    {
        v1.push_back( 4 );
    }
    v1.push_back( 7 );

    cout << "Vector v1 is ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates
    v1_NewEnd1 = unique ( v1.begin( ), v1.end( ) );

    cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique ( v1.begin( ), v1_NewEnd1 , mod_equal );

    cout << "Removing adjacent duplicates from vector v1 under the\n "
            << " binary predicate mod_equal gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;

    // Remove elements if preceded by an element that was greater
    v1_NewEnd3 = unique ( v1.begin( ), v1_NewEnd2, greater<int>( ) );

    cout << "Removing adjacent elements satisfying the binary\n "
            << " predicate mod_equal from vector v1 gives ( " ;
    for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )
        cout << *v1_Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).
Removing adjacent duplicates from vector v1 gives
( 5 -5 5 -5 5 -5 5 -5 4 7 ).
Removing adjacent duplicates from vector v1 under the
  binary predicate mod_equal gives
( 5 4 7 ).
Removing adjacent elements satisfying the binary
  predicate mod_equal from vector v1 gives ( 5 7 ).
```

## <a name="unique_copy"></a>unique_copy

Kopiert Elemente aus einem Quellbereich in einen Zielbereich mit Ausnahmen von doppelten Elementen, die nebeneinander angeordnet sind.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 unique_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryPredicate>
ForwardIterator2 unique_copy(ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parameter

*exec* -\
Die zu verwendende Ausführungs Richtlinie.

*erste*\
Ein Vorwärtsiterator, der die Position des ersten Elements im zu kopierenden Quellbereich adressiert.

*Letzter*\
Ein Vorwärtsiterator, der die Position hinter dem letzten Element im zu kopierenden Quellbereich adressiert.

*Ergebnis*\
Ein Vorwärtsiterator, der die Position des ersten Elements im Zielbereich adressiert, der die Kopie erhält, aus der aufeinanderfolgende Duplikate entfernt wurden.

*pred-* \
Benutzerdefiniertes Prädikatfunktionsobjekt, das die zu erfüllende Bedingung definiert, wenn zwei Elemente als gleichwertig akzeptiert werden. Ein binäres Prädikat akzeptiert zwei Argumente und gibt bei Erfüllung **true** und bei Nichterfüllung **false** zurück.

### <a name="return-value"></a>Rückgabewert

Ein Ausgabeiterator, der die Position hinter dem letzten Elements im Zielbereich adressiert, der die Kopie erhält, aus der aufeinanderfolgende Duplikate entfernt wurden.

### <a name="remarks"></a>Bemerkungen

Beide Formen des Algorithmus entfernen das zweite Duplikat eines aufeinanderfolgenden Paars gleicher Elemente.

Der Vorgang des Algorithmus ist stabil, sodass die relative Reihenfolge der nicht gelöschten Elemente nicht geändert wird.

Die Bereiche, auf die verwiesen wird, müssen gültig sein. Alle Zeiger müssen dereferenzierbar sein, und die letzte Position innerhalb einer Sequenz muss von der ersten Position aus durch Zunahme erreichbar sein.

Die Komplexität ist linear und erfordert (`last` - `first`)-Vergleiche.

### <a name="example"></a>Beispiel

```cpp
// alg_unique_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 ) {
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 == elem2;
};

int main() {
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2,
            v1_NewEnd1, v1_NewEnd2;

    int i;
    for ( i = 0 ; i <= 1 ; i++ ) {
        v1.push_back( 5 );
        v1.push_back( -5 );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
        v1.push_back( 4 );
    v1.push_back( 7 );

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
        v1.push_back( 10 );

    cout << "Vector v1 is\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Copy first half to second, removing consecutive duplicates
    v1_NewEnd1 = unique_copy ( v1.begin( ), v1.begin( ) + 8, v1.begin( ) + 8 );

    cout << "Copying the first half of the vector to the second half\n "
            << "while removing adjacent duplicates gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    int iv;
    for ( iv = 0 ; iv <= 7 ; iv++ )
        v1.push_back( 10 );

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique_copy ( v1.begin( ), v1.begin( ) + 14,
        v1.begin( ) + 14 , mod_equal );

    cout << "Copying the first half of the vector to the second half\n "
            << " removing adjacent duplicates under mod_equals gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="upper_bound"></a>upper_bound

Sucht die Position des ersten Elements in einem sortierten Bereich, der über einen Wert größer als einen angegebenen Wert verfügt. Dabei wird das Sortierkriterium möglicherweise von einen binären Prädikat bestimmt.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Parameter

*erste*\
Die Position des ersten Elements in dem zu durchsuchenden Bereich.

*Letzter*\
Die Position eine Stelle hinter dem letzten Element im zu durchsuchenden Bereich.

*value*\
Der Wert im sortierten Bereich, der vom Wert des vom zurückgegebenen Iterator adressierten Elements überschritten werden muss.

*pred-* \
Ein benutzerdefiniertes Vergleichs-Prädikat Funktions Objekt, das den Sinn definiert, in dem ein Element kleiner als ein anderes ist. Ein Vergleichs Prädikat übernimmt zwei Argumente und gibt bei **Erfüllung true** zurück und **false** , wenn es nicht erfüllt wird.

### <a name="return-value"></a>Rückgabewert

Ein Forward-Iterator zur Position des ersten Elements, das über einen Wert größer als den angegebenen Wert verfügt.

### <a name="remarks"></a>Bemerkungen

Der sortierte Quellbereich, auf den verwiesen wird, muss gültig sein. Alle Iteratoren müssen dereferenzierbar sein und die letzte Position muss der innerhalb der Reihenfolge vom ersten von der ersten Position aus durch Zunahme erreichbar sein.

Ein sortierter Bereich ist eine Vorbedingung für die Verwendung von `upper_bound`, wobei das Sortierkriterium mit dem vom Vergleichs Prädikat angegebenen übereinstimmt.

Der Bereich wird von `upper_bound` nicht geändert.

Die Werttypen der Forward-Iteratoren müssen weniger als vergleichbar sein, um sortiert zu werden, sodass zwei Elemente möglicherweise als gleichwertig bestimmt werden (in dem Sinne, dass keins geringer als das Andere ist), oder dass eins geringer als das Andere ist. Dies führt zu einer Sortierung zwischen den nicht gleichwertigen Elementen.

Die Komplexität dieses Algorithmus ist bei Zufallszugriffsiteratoren logarithmisch und andernfalls linear. Dabei ist eine Anzahl von Schritten proportional zu (`last - first`).

### <a name="example"></a>Beispiel

```cpp
// alg_upper_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate upper_bound

    vector<int>::iterator Result;

    // upper_bound of 3 in v1 with default binary predicate less<int>()
    Result = upper_bound(v1.begin(), v1.end(), 3);
    cout << "The upper_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The upper_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v3 with the binary predicate mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```
