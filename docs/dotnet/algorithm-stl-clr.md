---
title: algorithm (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
- cliext::adjacent_find
- cliext::binary_search
- cliext::copy
- cliext::copy_backward
- cliext::count
- cliext::count_if
- cliext::equal
- cliext::equal_range
- cliext::fill
- cliext::fill_n
- cliext::find
- cliext::find_end
- cliext::find_first_of
- cliext::find_if
- cliext::for_each
- cliext::generate
- cliext::generate_n
- cliext::includes
- cliext::inplace_merge
- cliext::iter_swap
- cliext::lexicographical_compare
- cliext::lower_bound
- cliext::make_heap
- cliext::max
- cliext::max_element
- cliext::merge
- cliext::min
- cliext::min_element
- cliext::mismatch
- cliext::next_permutation
- cliext::nth_element
- cliext::partial_sort
- cliext::partial_sort_copy
- cliext::partition
- cliext::pop_heap
- cliext::prev_permutation
- cliext::push_heap
- cliext::random_shuffle
- cliext::remove
- cliext::remove_copy
- cliext::remove_copy_if
- cliext::remove_if
- cliext::replace
- cliext::replace_copy
- cliext::replace_copy_if
- cliext::replace_if
- cliext::reverse
- cliext::reverse_copy
- cliext::rotate
- cliext::rotate_copy
- cliext::search
- cliext::search_n
- cliext::set_difference
- cliext::set_intersection
- cliext::set_symmetric_difference
- cliext::set_union
- cliext::sort
- cliext::sort_heap
- cliext::stable_partition
- cliext::stable_sort
- cliext::swap
- cliext::swap_ranges
- cliext::transform
- cliext::unique
- cliext::unique_copy
- cliext::upper_bound
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
- adjacent_find function
- binary_search function [STL/CLR]
- copy function [STL/CLR]
- copy_backward function [STL/CLR]
- count function [STL/CLR]
- count_if function [STL/CLR]
- equal function [STL/CLR]
- equal_range function [STL/CLR]
- fill function
- fill_n function
- find function [STL/CLR]
- find_end function [STL/CLR]
- find_first_of function [STL/CLR]
- find_if function [STL/CLR]
- for_each function [STL/CLR]
- generate function [STL/CLR]
- generate_n function [STL/CLR]
- includes function [STL/CLR]
- inplace_merge function [STL/CLR]
- iter_swap function [STL/CLR]
- lexicographical_compare function [STL/CLR]
- lower_bound function [STL/CLR]
- make_heap function [STL/CLR]
- max function [STL/CLR]
- max_element function [STL/CLR]
- merge function [STL/CLR]
- min function [STL/CLR]
- min_element function [STL/CLR]
- mismatch function [STL/CLR]
- next_permutation function [STL/CLR]
- nth_element function [STL/CLR]
- partial_sort function [STL/CLR]
- partial_sort_copy function [STL/CLR]
- partition function [STL/CLR]
- pop_heap function [STL/CLR]
- prev_permutation function [STL/CLR]
- push_heap function [STL/CLR]
- random_shuffle function [STL/CLR]
- remove function [STL/CLR]
- remove_copy function [STL/CLR]
- remove_copy_if function [STL/CLR]
- remove_if function [STL/CLR]
- replace function [STL/CLR]
- replace_copy function [STL/CLR]
- replace_copy_if function [STL/CLR]
- replace_if function [STL/CLR]
- reverse function [STL/CLR]
- reverse_copy function [STL/CLR]
- rotate function [STL/CLR]
- rotate_copy function [STL/CLR]
- search function [STL/CLR]
- search_n function [STL/CLR]
- set_difference function [STL/CLR]
- set_intersection function [STL/CLR]
- set_symmetric_difference function [STL/CLR]
- set_union function [STL/CLR]
- sort function [STL/CLR]
- sort_heap function [STL/CLR]
- stable_partition function [STL/CLR]
- stable_sort function [STL/CLR]
- swap function [STL/CLR]
- swap_ranges function [STL/CLR]
- transform function [STL/CLR]
- unique function [STL/CLR]
- unique_copy function [STL/CLR]
- upper_bound function [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
ms.openlocfilehash: 4abd7eaa640bb89fd97c1787bf2fd692610212fb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208950"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)

Definiert STL/CLR-Container Vorlagen Funktionen, die Algorithmen ausführen.

## <a name="syntax"></a>Syntax

```cpp
#include <cliext/algorithm>
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<cliext/Algorithmus >

**Namespace:** cliext

## <a name="declarations"></a>Deklarationen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[adjacent_find (STL/CLR)](#adjacent_find)|Sucht zwei angrenzende Elemente, die gleich sind.|
|[binary_search (STL/CLR)](#binary_search)|Testet, ob eine sortierte Sequenz einen angegebenen Wert enthält.|
|[copy (STL/CLR)](#copy)|Kopiert Werte aus einem Quellbereich in einen Zielbereich und Iteration in Vorwärtsrichtung.|
|[copy_backward (STL/CLR)](#copy_backward)|Kopiert Werte aus einem Quellbereich in einen Zielbereich und Iteration in umgekehrter Richtung.|
|[count (STL/CLR)](#count)|Gibt die Anzahl von Elementen in einem Bereich zurück, dessen Werte mit einem angegebenen Wert übereinstimmen.|
|[count_if (STL/CLR)](#count_if)|Gibt die Anzahl von Elementen in einem Bereich zurück, dessen Werte mit einer angegebenen Bedingung übereinstimmen.|
|[equal (STL/CLR)](#equal)|Vergleicht zwei Bereiche, Element Weise Element.|
|[equal_range (STL/CLR)](#equal_range)|Durchsucht eine geordnete Sequenz von Werten und gibt zwei Positionen zurück, die eine unter Sequenz von Werten trennen, die alle einem angegebenen Element entsprechen.|
|[fill (STL/CLR)](#fill)|Weist den gleichen neuen Wert jedem Element in einem angegebenen Bereich zu.|
|[fill_n (STL/CLR)](#fill_n)|Weist einer angegebenen Anzahl von Elementen in einem Bereich, der mit einem bestimmten Element beginnt, einen neuen Wert zu.|
|[find (STL/CLR)](#find)|Gibt die Position des ersten Vorkommens eines angegebenen Werts zurück.|
|[find_end (STL/CLR)](#find_end)|Gibt die letzte unter Sequenz in einem Bereich zurück, der mit einer angegebenen Sequenz identisch ist.|
|[find_first_of (STL/CLR)](#find_first_of)|Durchsucht einen Bereich nach dem ersten Vorkommen eines bestimmten Bereichs von Elementen.|
|[find_if (STL/CLR)](#find_if)|Gibt die Position des ersten Elements in einer Sequenz von-Werten zurück, in der das Element eine angegebene Bedingung erfüllt.|
|[for_each (STL/CLR)](#for_each)|Wendet ein angegebenes Funktions Objekt auf jedes Element in einer Sequenz von Werten an und gibt das Funktions Objekt zurück.|
|[generate (STL/CLR)](#generate)|Weist die Werte, die von einem Funktions Objekt generiert werden, jedem Element in einer Sequenz von Werten zu.|
|[generate_n (STL/CLR)](#generate_n)|Weist die Werte, die von einem Funktions Objekt generiert werden, einer angegebenen Anzahl von Elementen zu.|
|[includes (STL/CLR)](#includes)|Testet, ob ein sortierter Bereich alle Elemente in einem zweiten sortierten Bereich enthält.|
|[inplace_merge (STL/CLR)](#inplace_merge)|Kombiniert die Elemente von zwei aufeinander folgenden sortierten Bereichen in einen einzelnen sortierten Bereich.|
|[iter_swap (STL/CLR)](#iter_swap)|Tauscht zwei Werte aus, auf die durch ein Paar angegebener Iteratoren verwiesen wird.|
|[lexicographical_compare (STL/CLR)](#lexicographical_compare)|Vergleicht zwei Sequenzen, Element Weise Element und identifiziert, welche Sequenz das kleinere der beiden Sequenzen ist.|
|[lower_bound (STL/CLR)](#lower_bound)|Sucht die Position des ersten Elements in einer geordneten Sequenz von Werten, die einen Wert größer oder gleich einem angegebenen Wert aufweist.|
|[make_heap (STL/CLR)](#make_heap)|Konvertiert Elemente aus einem angegebenen Bereich in einen Heap, in dem das erste Element im Heap das größte ist.|
|[Max (STL/CLR)](#max))|Vergleicht zwei-Objekte und gibt den größeren der beiden-Objekte zurück.|
|[max_element (STL/CLR)](#max_element)|Sucht das größte Element in einer angegebenen Sequenz von Werten.|
|[Merge (STL/CLR)](#merge))|Kombiniert alle Elemente aus zwei sortierten Quell Bereichen zu einem einzelnen sortierten Zielbereich.|
|[min (STL/CLR)](#min)|Vergleicht zwei-Objekte und gibt das kleinere der beiden-Objekte zurück.|
|[min_element (STL/CLR)](#min_element)|Sucht das kleinste Element in einer angegebenen Sequenz von Werten.|
|[mismatch (STL/CLR)](#mismatch)|Vergleicht zwei Bereiche Element Weise und gibt die erste Position zurück, an der ein Unterschied auftritt.|
|[next_permutation (STL/CLR)](#next_permutation)|Ordnet die Elemente in einem Bereich neu, damit die ursprüngliche Reihenfolge durch die lexikografisch nächste größere permutations ersetzt wird, falls vorhanden.|
|[nth_element (STL/CLR)](#nth_element)|Partitioniert eine Sequenz von Elementen, wobei das `n`th-Element der Sequenz ordnungsgemäß gefunden wird, sodass alle Elemente davor kleiner oder gleich sind und alle nachfolgenden Elemente größer oder gleich sind.|
|[partial_sort (STL/CLR)](#partial_sort)|Ordnet eine angegebene Anzahl von kleineren Elementen in einem Bereich in einer nicht absteigenden Reihenfolge an.|
|[partial_sort_copy (STL/CLR)](#partial_sort_copy)|Kopiert Elemente aus einem Quellbereich in einen Zielbereich, sodass die Elemente aus dem Quellbereich geordnet sind.|
|[partition (STL/CLR)](#partition)|Ordnet Elemente in einem Bereich so an, dass die Elemente, die ein unäres Prädikat erfüllen, vor denen stehen, die diese nicht erfüllen können.|
|[pop_heap (STL/CLR)](#pop_heap)|Verschiebt das größte Element von der Vorderseite eines Heaps bis zum Ende und bildet dann einen neuen Heap aus den übrigen Elementen.|
|[prev_permutation (STL/CLR)](#prev_permutation)|Ordnet eine Sequenz von Elementen so an, dass die ursprüngliche Reihenfolge durch die lexikografisch vorangehende höhere permutations ersetzt wird, falls vorhanden.|
|[push_heap (STL/CLR)](#push_heap)|Fügt ein Element hinzu, das sich am Ende eines Bereichs in einem vorhandenen Heap befindet, der aus den vorherigen Elementen im Bereich besteht.|
|[random_shuffle (STL/CLR)](#random_shuffle)|Ordnet eine Sequenz von `N` Elementen in einem Bereich in einer `N`an. möglichen per Zufall ausgewählten Anordnungen neu.|
|[remove (STL/CLR)](#remove)|Löscht einen angegebenen Wert aus einem angegebenen Bereich, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen, und gibt das Ende eines neuen Bereichs zurück, der vom angegebenen Wert frei ist.|
|[remove_copy (STL/CLR)](#remove_copy)|Kopiert Elemente aus einem Quellbereich in einen Zielbereich, mit dem Unterschied, dass Elemente eines angegebenen Werts nicht kopiert werden, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen.|
|[remove_copy_if (STL/CLR)](#remove_copy_if)|Kopiert Elemente aus einem Quellbereich in einen Zielbereich, mit Ausnahme derjenigen, die ein Prädikat erfüllen, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen.|
|[remove_if (STL/CLR)](#remove_if)|Löscht Elemente, die ein Prädikat aus einem angegebenen Bereich erfüllen, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen. erforderlich.|
|[replace (STL/CLR)](#replace)|Ersetzt Elemente in einem Bereich, der einem angegebenen Wert entspricht, durch einen neuen Wert.|
|[replace_copy (STL/CLR)](#replace_copy)|Kopiert Elemente aus einem Quellbereich in einen Zielbereich und ersetzt Elemente, die einem angegebenen Wert entsprechen, durch einen neuen Wert.|
|[replace_copy_if (STL/CLR)](#replace_copy_if)|Überprüft jedes Element in einem Quellbereich und ersetzt es, sofern es ein angegebenes Prädikat erfüllt, während das Ergebnis in einen neuen Zielbereich kopiert wird.|
|[replace_if (STL/CLR)](#replace_if)|Überprüft jedes Element in einem Bereich und ersetzt es, sofern es das angegebene Prädikat erfüllt.|
|[reverse (STL/CLR)](#reverse)|Kehrt die Reihenfolge der Elemente innerhalb eines Bereichs um.|
|[reverse_copy (STL/CLR)](#reverse_copy)|Kehrt die Reihenfolge der Elemente in einem Quellbereich beim Kopieren in einen Zielbereich um.|
|[rotate (STL/CLR)](#rotate)|Vertauscht die Elemente in zwei benachbarten Bereichen.|
|[rotate_copy (STL/CLR)](#rotate_copy)|Vertauscht die Elemente in zwei benachbarten Bereiche innerhalb eines Quellbereichs und kopiert das Ergebnis in einen Zielbereich.|
|[search (STL/CLR)](#search_)|Sucht das erste Vorkommen einer Sequenz in einem Zielbereich, dessen Elemente gleich den Elementen in einer bestimmten Elementsequenz sind oder dessen Elemente äquivalent sind mit den Elementen in der angegebenen Sequenz, wie durch ein binäres Prädikat festgelegt.|
|[search_n (STL/CLR)](#search_n)|Sucht nach der ersten Untersequenz in einem Bereich, der aus einer angegebenen Anzahl von Elementen besteht, die einen bestimmten Wert oder eine Beziehung zu diesem durch ein binäres Prädikat angegebenen Wert haben.|
|[set_difference (STL/CLR)](#set_difference)|Vereinigt alle Elemente, die zu dem einen, jedoch nicht zu einem anderen sortierten Quellbereich gehören, in einen einzelnen, sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.|
|[set_intersection (STL/CLR)](#set_intersection)|Vereinigt alle Elemente, die zu beiden sortierten Quellbereichen gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.|
|[set_symmetric_difference (STL/CLR)](#set_symmetric_difference)|Vereinigt alle Elemente, die zu einem, jedoch nicht zu beiden sortierten Quellbereichen gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.|
|[set_union (STL/CLR)](#set_union))|Vereinigt alle Elemente, die mindestens zu einem der beiden sortierten Quellbereiche gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.|
|[sort (STL/CLR)](#sort)|Ordnet die Elemente in einem angegebenen Bereich in einer aufsteigenden Reihenfolge oder gemäß eines Sortierkriteriums an, das von einem binären Prädikat angegeben wird.|
|[sort_heap (STL/CLR)](#sort_heap)|Konvertiert einen Heap in einen sortierten Bereich.|
|[stable_partition (STL/CLR)](#stable_partition)|Klassifiziert Elemente in einem Bereich in zwei zusammenhanglose Sätze, wobei die Elemente, die ein unäres Prädikat erfüllen, direkt den Elementen vorausgehen, die es nicht erfüllen können. Die relative Reihenfolge der äquivalenten Elemente wird dabei beibehalten.|
|[stable_sort (STL/CLR)](#stable_sort)|Ordnet die Elemente in einem angegebenen Bereich in einer aufsteigenden Reihenfolge oder gemäß eines Sortierkriteriums an, das von einem binären Prädikat angegeben wird, und behält die relative Reihenfolge der äquivalenten Elemente bei.|
|[swap (STL/CLR)](#swap)|Vertauscht die Werte der Elemente von zwei Objekttypen und weist den Inhalt des ersten Objekts dem zweiten Objekt und den Inhalt des zweiten dem ersten zu.|
|[swap_ranges (STL/CLR)](#swap_ranges)|Vertauscht die Elemente eines Bereichs mit den Elementen eines anderen gleich großen Bereichs.|
|[transform (STL/CLR)](#transform)|Wendet ein angegebenes Funktionsobjekt auf jedes Element in einem Quellbereich oder auf ein Elementpaar aus zwei Quellbereichen an und kopiert die Rückgabewerte des Funktionsobjekts in einen Zielbereich.|
|[unique (STL/CLR)](#unique)|Entfernt doppelte Elemente, die in einem angegebenen Bereich nebeneinander angeordnet sind.|
|[unique_copy (STL/CLR)](#unique_copy)|Kopiert Elemente aus einem Quellbereich in einen Zielbereich mit Ausnahmen von doppelten Elementen, die nebeneinander angeordnet sind.|
|[upper_bound (STL/CLR)](#upper_bound)|Sucht die Position des ersten Elements in einem sortierten Bereich, der über einen Wert größer als einen angegebenen Wert verfügt. Dabei wird das Sortierkriterium möglicherweise von einen binären Prädikat bestimmt.|

## <a name="members"></a>Members

## <a name="adjacent_find-stlclr"></a><a name="adjacent_find"></a>adjacent_find (STL/CLR)

Sucht zwei benachbarte Elemente, die entweder gleich sind oder eine angegebene Bedingung erfüllen.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `adjacent_find`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [adjacent_find](../standard-library/algorithm-functions.md#adjacent_find).

## <a name="binary_search-stlclr"></a><a name="binary_search"></a>binary_search (STL/CLR)

Testet, ob ein Element in einem sortierten Bereich einem angegebenen Wert entspricht oder ihm auf eine von einem binären Prädikat angegebene Weise gleicht.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Ty> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `binary_search`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [binary_search](../standard-library/algorithm-functions.md#binary_search).

## <a name="copy-stlclr"></a><a name="copy"></a>Kopieren (STL/CLR)

Weist die Werte von Elementen aus einem Quellbereich einem Zielbereich zu, durchläuft die Quellelementsequenz und weist ihnen vorwärts neue Positionen zu.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `copy`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Copy](../standard-library/algorithm-functions.md#copy).

## <a name="copy_backward-stlclr"></a><a name="copy_backward"></a>copy_backward (STL/CLR)

Weist die Werte von Elementen aus einem Quellbereich einem Zielbereich zu, durchläuft die Quellelementsequenz und weist ihnen rückwärts neue Positionen zu.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt1, class _BidIt2> inline
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,
        _BidIt2 _Dest);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `copy_backward`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [copy_backward](../standard-library/algorithm-functions.md#copy_backward).

## <a name="count-stlclr"></a><a name="count"></a>count (STL/CLR)

Gibt die Anzahl von Elementen in einem Bereich zurück, dessen Werte mit einem angegebenen Wert übereinstimmen.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _Ty> inline
    typename iterator_traits<_InIt>::difference_type
        count(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `count`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [count](../standard-library/algorithm-functions.md#count).

## <a name="count_if-stlclr"></a><a name="count_if"></a>count_if (STL/CLR)

Gibt die Anzahl von Elementen in einem Bereich zurück, dessen Werte mit einer angegebenen Bedingung übereinstimmen.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _Pr> inline
    typename iterator_traits<_InIt>::difference_type
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `count_if`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [count_if](../standard-library/algorithm-functions.md#count_if).

## <a name="equal-stlclr"></a><a name="equal"></a>EQUAL (STL/CLR)

Vergleicht zwei Bereiche elementweise entweder auf Gleichheit oder Äquivalenz in dem durch ein binäres Prädikat angegebenen Sinn.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `equal`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [gleich](../standard-library/algorithm-functions.md#equal).

## <a name="equal_range-stlclr"></a><a name="equal_range"></a>equal_range (STL/CLR)

Sucht ein Paar Positionen in einem sortierten Bereich, wobei die erste Position kleiner als oder gleich der Position eines bestimmten Elements und die zweite Position größer als die Position des Elements ist. Die Äquivalenz oder Sortierung zur Festlegung der Positionen in der Sequenz kann durch ein binäres Prädikat angegeben werden.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Ty> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `equal_range`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [equal_range](../standard-library/algorithm-functions.md#equal_range).

## <a name="fill-stlclr"></a><a name="fill"></a>Fill (STL/CLR)

Weist den gleichen neuen Wert jedem Element in einem angegebenen Bereich zu.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Ty> inline
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `fill`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Fill](../standard-library/algorithm-functions.md#fill).

## <a name="fill_n-stlclr"></a><a name="fill_n"></a>fill_n (STL/CLR)

Weist einer angegebenen Anzahl von Elementen in einem Bereich, der mit einem bestimmten Element beginnt, einen neuen Wert zu.

### <a name="syntax"></a>Syntax

```cpp
template<class _OutIt, class _Diff, class _Ty> inline
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `fill_n`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [fill_n](../standard-library/algorithm-functions.md#fill_n).

## <a name="find-stlclr"></a><a name="find"></a>Suchen (STL/CLR)

Sucht die Position des ersten Vorkommens eines Elements in einem Bereich, der einen angegebenen Wert enthält.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _Ty> inline
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `find`C++ der Standard Bibliotheksfunktion. Weitere Informationen [finden](../standard-library/algorithm-functions.md#find)Sie untersuchen.

## <a name="find_end-stlclr"></a><a name="find_end"></a>find_end (STL/CLR)

Sucht in einem Bereich nach der letzten Untersequenz, die mit einer angegebenen Sequenz identisch ist oder die in durch ein binäres Prädikat angegebenen Sinne äquivalent ist.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `find_end`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [find_end](../standard-library/algorithm-functions.md#find_end).

## <a name="find_first_of-stlclr"></a><a name="find_first_of"></a>find_first_of (STL/CLR)

Sucht das erste Vorkommen mehrerer Werte innerhalb eines Zielbereichs oder das erste Vorkommen mehrerer Elemente, die wie durch ein binäres Prädikat angegeben mit einem angegebenen Satz der Elemente äquivalent sind.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `find_first_of`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [find_first_of](../standard-library/algorithm-functions.md#find_first_of).

## <a name="find_if-stlclr"></a><a name="find_if"></a>find_if (STL/CLR)

Sucht die Position des ersten Vorkommens eines Elements in einem Bereich, der eine bestimmte Bedingung erfüllt.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _Pr> inline
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `find_if`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each-stlclr"></a><a name="for_each"></a>for_each (STL/CLR)

Wendet ein angegebenes Funktionsobjekt auf jedes Element in einer Vorwärtsreihenfolge innerhalb eines Bereichs an und gibt das Funktionsobjekt zurück.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _Fn1> inline
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `for_each`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [for_each](../standard-library/algorithm-functions.md#for_each).

## <a name="generate-stlclr"></a><a name="generate"></a>Generate (STL/CLR)

Weist die Werte, die von einem Funktionsobjekt generiert werden, jedem Element in einem Bereich zu.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Fn0> inline
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `generate`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [generieren](../standard-library/algorithm-functions.md#generate)von.

## <a name="generate_n-stlclr"></a><a name="generate_n"></a>generate_n (STL/CLR)

Weist die Werte, die von einem Funktionsobjekt generiert werden, einer angegebenen Anzahl von Elementen eines Bereichs zu und kehrt zu der Position zurück, die direkt nach dem letzten zugewiesenen Wert liegt.

### <a name="syntax"></a>Syntax

```cpp
template<class _OutIt, class _Diff, class _Fn0> inline
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `generate_n`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="includes-stlclr"></a><a name="includes"></a>Includes (STL/CLR)

Testet, ob ein sortierter Bereich alle Elemente enthält, die in einem zweiten sortierten Bereich enthalten sind, wobei das Sortier- oder Äquivalenzkriterium für die Elemente durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `includes`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [enthält](../standard-library/algorithm-functions.md#includes).

## <a name="inplace_merge-stlclr"></a><a name="inplace_merge"></a>Inplace_merge (STL/CLR)

Kombiniert die Elemente von zwei aufeinander folgenden sortierten Bereichen in einen einzelnen sortierten Bereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die C++ Standard Bibliotheksfunktion `inplace_merge` Weitere Informationen finden Sie unter [Inplace_merge](../standard-library/algorithm-functions.md#inplace_merge).

## <a name="iter_swap-stlclr"></a><a name="iter_swap"></a>iter_swap (STL/CLR)

Tauscht zwei Werte aus, auf die durch ein Paar angegebener Iteratoren verwiesen wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `iter_swap`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [iter_swap](../standard-library/algorithm-functions.md#iter_swap).

## <a name="lexicographical_compare-stlclr"></a><a name="lexicographical_compare"></a>lexicographical_compare (STL/CLR)

Vergleicht zwei Sequenzen elementweise, um zu bestimmen, welche der beiden kleiner ist.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `lexicographical_compare`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare).

## <a name="lower_bound-stlclr"></a><a name="lower_bound"></a>lower_bound (STL/CLR)

Sucht die Position des ersten Elements in einem sortierter Bereich, dessen Wert kleiner als oder gleich einem angegebenen Wert ist, wobei das Bestell Kriterium durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `lower_bound`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [lower_bound](../standard-library/algorithm-functions.md#lower_bound).

## <a name="make_heap-stlclr"></a><a name="make_heap"></a>Make_heap (STL/CLR)

Konvertiert Elemente aus einem angegebenen Bereich in einen Heap, in dem das erste Element das größte ist und für den ein Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _RanIt> inline
    void make_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `make_heap`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Make_heap](../standard-library/algorithm-functions.md#make_heap).

## <a name="max-stlclr"></a><a name="max"></a>Max (STL/CLR)

Vergleicht zwei Objekte und gibt das größere der beiden zurück, wobei das Sortierkriterium möglicherweise von einem binären Prädikat angegeben wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _Ty> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `max`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Max](../standard-library/algorithm-functions.md#max).

## <a name="max_element-stlclr"></a><a name="max_element"></a>max_element (STL/CLR)

Sucht das erste Vorkommen des größten Elements in einem angegebenen Bereich, in dem das Sortierkriterium möglicherweise von einem binären Prädikat angegeben wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `max_element`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [max_element](../standard-library/algorithm-functions.md#max_element).

## <a name="merge-stlclr"></a><a name="merge"></a>Merge (STL/CLR)

Kombiniert alle Elemente von zwei sortierten Quellbereichen in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `merge`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Merge](../standard-library/algorithm-functions.md#merge).

## <a name="min-stlclr"></a><a name="min"></a>min (STL/CLR)

Vergleicht zwei Objekte und gibt das kleinere der beiden zurück, wobei das Sortierkriterium möglicherweise von einem binären Prädikat angegeben wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _Ty> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `min`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Min](../standard-library/algorithm-functions.md#min).

## <a name="min_element-stlclr"></a><a name="min_element"></a>min_element (STL/CLR)

Sucht das erste Vorkommen des kleinsten Elements in einem angegebenen Bereich, in dem das Sortierkriterium von einem binären Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `min_element`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [min_element](../standard-library/algorithm-functions.md#min_element).

## <a name="mismatch-stlclr"></a><a name="mismatch"></a>nicht übereinstimmende (STL/CLR)

Vergleicht zwei Bereiche elementweise entweder auf Gleichheit oder Äquivalenz, wie von einem binären Prädikat angegeben, und sucht die erste Position, an der ein Unterschied auftritt.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
            _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `mismatch`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter nicht [Übereinstimmung](../standard-library/algorithm-functions.md#mismatch).

## <a name="next_permutation-stlclr"></a><a name="next_permutation"></a>Next_permutation (STL/CLR)

Ordnet die Elemente in einem Bereich neu, damit die ursprüngliche Reihenfolge von der lexikografisch nächsthöheren Permutation ersetzt wird, falls vorhanden, wobei die Bedeutung von „nächsthöher“ durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt> inline
    bool next_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `next_permutation`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [next_permutation](../standard-library/algorithm-functions.md#next_permutation).

## <a name="nth_element-stlclr"></a><a name="nth_element"></a>nth_element (STL/CLR)

Partitioniert einen Bereich von Elementen, wobei das `n`th-Element der Sequenz im Bereich ordnungsgemäß gefunden wird, sodass alle Elemente davor kleiner oder gleich sind und alle Elemente, die in der Sequenz folgen, größer oder gleich sind.

### <a name="syntax"></a>Syntax

```cpp
template<class _RanIt> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `nth_element`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [nth_element](../standard-library/algorithm-functions.md#nth_element).

## <a name="partial_sort-stlclr"></a><a name="partial_sort"></a>Partial_sort (STL/CLR)

Ordnet eine bestimmte Anzahl von kleineren Elementen in einem Bereich in einer aufsteigenden Reihenfolge oder gemäß eines Sortierkriteriums an, das von einem binären Prädikat angegeben wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _RanIt> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `partial_sort`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [partial_sort](../standard-library/algorithm-functions.md#partial_sort).

## <a name="partial_sort_copy-stlclr"></a><a name="partial_sort_copy"></a>Partial_sort_copy (STL/CLR)

Kopiert Elemente aus einem Quellbereich in einen Zielbereich, in dem die Quellelemente entweder durch kleiner als oder durch ein anderes festgelegtes binäres Prädikat sortiert werden.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _RanIt> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2);
template<class _InIt, class _RanIt, class _Pr> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `partial_sort_copy`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy).

## <a name="partition-stlclr"></a><a name="partition"></a>Partition (STL/CLR)

Klassifiziert Elemente in einem Bereich in zwei zusammenhanglose Sätze, wenn diese Elemente ein unäres Prädikat erfüllen, das denen direkt vorausgeht, die es nicht erfüllen können.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `partition`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Partition](../standard-library/algorithm-functions.md#partition).

## <a name="pop_heap-stlclr"></a><a name="pop_heap"></a>pop_heap (STL/CLR)

Entfernt das größte Element von der Vorderseite eines Heaps und fügt es in die vorletzte Position des Bereichs ein und bildet dann einen neuen Heap aus den übrigen Elementen.

### <a name="syntax"></a>Syntax

```cpp
template<class _RanIt> inline
    void pop_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `pop_heap`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [pop_heap](../standard-library/algorithm-functions.md#pop_heap).

## <a name="prev_permutation-stlclr"></a><a name="prev_permutation"></a>Prev_permutation (STL/CLR)

Ordnet die Elemente in einem Bereich neu, damit die ursprüngliche Reihenfolge von der lexikografisch nächsthöheren Permutation ersetzt wird, falls vorhanden, wobei die Bedeutung von „nächsthöher“ durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `prev_permutation`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Prev_permutation](../standard-library/algorithm-functions.md#prev_permutation).

## <a name="push_heap-stlclr"></a><a name="push_heap"></a>Push_heap (STL/CLR)

Fügt ein Element hinzu, das sich am Ende eines Bereichs in einem vorhandenen Heap befindet, der aus den vorherigen Elementen im Bereich besteht.

### <a name="syntax"></a>Syntax

```cpp
template<class _RanIt> inline
    void push_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `push_heap`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Push_heap](../standard-library/algorithm-functions.md#push_heap).

## <a name="random_shuffle-stlclr"></a><a name="random_shuffle"></a>Random_shuffle (STL/CLR)

Ordnet eine Sequenz von `N` Elementen in einem Bereich in einer `N`an. möglichen per Zufall ausgewählten Anordnungen neu.

### <a name="syntax"></a>Syntax

```cpp
template<class _RanIt> inline
    void random_shuffle(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Fn1> inline
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `random_shuffle`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle).

## <a name="remove-stlclr"></a><a name="remove"></a>Remove (STL/CLR)

Eliminiert einen angegebenen Wert von einem angegebenen Bereich, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen und das Ende eines neuen Bereichs zurückzugeben, der den angegebenen Wert nicht enthält.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `remove`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Remove](../standard-library/algorithm-functions.md#remove).

## <a name="remove_copy-stlclr"></a><a name="remove_copy"></a>remove_copy (STL/CLR)

Kopiert Elemente aus einem Quellbereich in einen Zielbereich, ohne dass Elemente eines angegebenen Werts kopiert werden und ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen und das Ende eines neuen Zielbereichs zurückzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt remove_copy(_InIt _First, _InIt _Last,
        _OutIt _Dest, const _Ty% _Val);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `remove_copy`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [remove_copy](../standard-library/algorithm-functions.md#remove_copy).

## <a name="remove_copy_if-stlclr"></a><a name="remove_copy_if"></a>remove_copy_if (STL/CLR)

Kopiert Elemente aus einem Quellbereich in einen Zielbereich, ohne dass Elemente, die ein Prädikat erfüllen, kopiert werden und ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen und das Ende eines neuen Zielbereichs zurückzugeben.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `remove_copy_if`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).

## <a name="remove_if-stlclr"></a><a name="remove_if"></a>remove_if (STL/CLR)

Eliminiert Elemente, die ein Prädikat aus einem angegebenen Bereich erfüllen, ohne die Reihenfolge der restlichen Elemente zu beeinträchtigen und das Ende eines neuen Bereichs zurückzugeben, der den angegebenen Wert nicht enthält.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Pr> inline
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `remove_if`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [remove_if](../standard-library/algorithm-functions.md#remove_if).

## <a name="replace-stlclr"></a><a name="replace"></a>Replace (STL/CLR)

Überprüft jedes Element in einem Bereich und ersetzt es, sofern es einem angegebenen Wert entspricht.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Ty> inline
    void replace(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `replace`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Replace](../standard-library/algorithm-functions.md#replace).

## <a name="replace_copy-stlclr"></a><a name="replace_copy"></a>replace_copy (STL/CLR)

Überprüft jedes Element in einem Quellbereich und ersetzt es, sofern es einem angegebenen Wert entspricht, während das Ergebnis in einen neuen Zielbereich kopiert wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `replace_copy`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [replace_copy](../standard-library/algorithm-functions.md#replace_copy).

## <a name="replace_copy_if-stlclr"></a><a name="replace_copy_if"></a>replace_copy_if (STL/CLR)

Überprüft jedes Element in einem Quellbereich und ersetzt es, sofern es ein angegebenes Prädikat erfüllt, während das Ergebnis in einen neuen Zielbereich kopiert wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred, const _Ty% _Val);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `replace_copy_if`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if).

## <a name="replace_if-stlclr"></a><a name="replace_if"></a>replace_if (STL/CLR)

Überprüft jedes Element in einem Bereich und ersetzt es, sofern es das angegebene Prädikat erfüllt.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Pr, class _Ty> inline
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,
        const _Ty% _Val);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `replace_if`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [replace_if](../standard-library/algorithm-functions.md#replace_if).

## <a name="reverse-stlclr"></a><a name="reverse"></a>Reverse (STL/CLR)

Kehrt die Reihenfolge der Elemente innerhalb eines Bereichs um.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt> inline
    void reverse(_BidIt _First, _BidIt _Last);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `reverse`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [umkehren](../standard-library/algorithm-functions.md#reverse).

## <a name="reverse_copy-stlclr"></a><a name="reverse_copy"></a>reverse_copy (STL/CLR)

Kehrt die Reihenfolge der Elemente in einem Quellbereich beim Kopieren in einen Zielbereich um.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt, class _OutIt> inline
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `reverse_copy`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy).

## <a name="rotate-stlclr"></a><a name="rotate"></a>Drehen (STL/CLR)

Vertauscht die Elemente in zwei benachbarten Bereichen.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt> inline
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `rotate`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Rotation](../standard-library/algorithm-functions.md#rotate).

## <a name="rotate_copy-stlclr"></a><a name="rotate_copy"></a>rotate_copy (STL/CLR)

Vertauscht die Elemente in zwei benachbarten Bereiche innerhalb eines Quellbereichs und kopiert das Ergebnis in einen Zielbereich.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _OutIt> inline
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,
        _OutIt _Dest);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `rotate_copy`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [rotate_copy](../standard-library/algorithm-functions.md#rotate_copy).

## <a name="search-stlclr"></a><a name="search_"></a>Suchen (STL/CLR)

Sucht das erste Vorkommen einer Sequenz in einem Zielbereich, dessen Elemente gleich den Elementen in einer bestimmten Elementsequenz sind oder dessen Elemente äquivalent sind mit den Elementen in der angegebenen Sequenz, wie durch ein binäres Prädikat festgelegt.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `search`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Search](../standard-library/algorithm-functions.md#search).

## <a name="search_n-stlclr"></a><a name="search_n"></a>search_n (STL/CLR)

Sucht nach der ersten Untersequenz in einem Bereich, der aus einer angegebenen Anzahl von Elementen besteht, die einen bestimmten Wert oder eine Beziehung zu diesem durch ein binäres Prädikat angegebenen Wert haben.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt1, class _Diff2, class _Ty> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val);
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `search_n`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [search_n](../standard-library/algorithm-functions.md#search_n).

## <a name="set_difference-stlclr"></a><a name="set_difference"></a>set_difference (STL/CLR)

Vereinigt alle Elemente, die zu dem einen, jedoch nicht zu einem anderen sortierten Quellbereich gehören, in einen einzelnen, sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `set_difference`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [set_difference](../standard-library/algorithm-functions.md#set_difference).

## <a name="set_intersection-stlclr"></a><a name="set_intersection"></a>set_intersection (STL/CLR)

Vereinigt alle Elemente, die zu beiden sortierten Quellbereichen gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `set_intersection`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [set_intersection](../standard-library/algorithm-functions.md#set_intersection).

## <a name="set_symmetric_difference-stlclr"></a><a name="set_symmetric_difference"></a>set_symmetric_difference (STL/CLR)

Vereinigt alle Elemente, die zu einem, jedoch nicht zu beiden sortierten Quellbereichen gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `set_symmetric_difference`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference).

## <a name="set_union-stlclr"></a><a name="set_union"></a>set_union (STL/CLR)

Vereinigt alle Elemente, die mindestens zu einem der beiden sortierten Quellbereiche gehören, in einen einzelnen sortierten Zielbereich, wobei das Sortierkriterium durch ein binäres Prädikat angegeben werden kann.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `set_union`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [set_union](../standard-library/algorithm-functions.md#set_union).

## <a name="sort-stlclr"></a><a name="sort"></a>Sort (STL/CLR)

Ordnet die Elemente in einem angegebenen Bereich in einer aufsteigenden Reihenfolge oder gemäß eines Sortierkriteriums an, das von einem binären Prädikat angegeben wird.

### <a name="syntax"></a>Syntax

```cpp
template<class _RanIt> inline
    void sort(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `sort`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Sortieren](../mfc/reference/cmfclistctrl-class.md#sort).

## <a name="sort_heap-stlclr"></a><a name="sort_heap"></a>sort_heap (STL/CLR)

Konvertiert einen Heap in einen sortierten Bereich.

### <a name="syntax"></a>Syntax

```cpp
template<class _RanIt> inline
    void sort_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `sort_heap`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [sort_heap](../standard-library/algorithm-functions.md#sort_heap).

## <a name="stable_partition-stlclr"></a><a name="stable_partition"></a>stable_partition (STL/CLR)

Klassifiziert Elemente in einem Bereich in zwei zusammenhanglose Sätze, wobei die Elemente, die ein unäres Prädikat erfüllen, direkt den Elementen vorausgehen, die es nicht erfüllen können. Die relative Reihenfolge der äquivalenten Elemente wird dabei beibehalten.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `stable_partition`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [stable_partition](../standard-library/algorithm-functions.md#stable_partition).

## <a name="stable_sort-stlclr"></a><a name="stable_sort"></a>stable_sort (STL/CLR)

Ordnet die Elemente in einem angegebenen Bereich in einer aufsteigenden Reihenfolge oder gemäß eines Sortierkriteriums an, das von einem binären Prädikat angegeben wird, und behält die relative Reihenfolge der äquivalenten Elemente bei.

### <a name="syntax"></a>Syntax

```cpp
template<class _BidIt> inline
    void stable_sort(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `stable_sort`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [stable_sort](../standard-library/algorithm-functions.md#stable_sort).

## <a name="swap-stlclr"></a><a name="swap"></a>Swap (STL/CLR)

Vertauscht die Werte der Elemente von zwei Objekttypen und weist den Inhalt des ersten Objekts dem zweiten Objekt und den Inhalt des zweiten dem ersten zu.

### <a name="syntax"></a>Syntax

```cpp
<class _Ty> inline
    void swap(_Ty% _Left, _Ty% _Right);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `swap`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Swap](../standard-library/algorithm-functions.md#swap).

## <a name="swap_ranges-stlclr"></a><a name="swap_ranges"></a>swap_ranges (STL/CLR)

Vertauscht die Elemente eines Bereichs mit den Elementen eines anderen gleich großen Bereichs.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `swap_ranges`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [swap_ranges](../standard-library/algorithm-functions.md#swap_ranges).

## <a name="transform-stlclr"></a><a name="transform"></a>Transformation (STL/CLR)

Wendet ein angegebenes Funktionsobjekt auf jedes Element in einem Quellbereich oder auf ein Elementpaar aus zwei Quellbereichen an und kopiert die Rückgabewerte des Funktionsobjekts in einen Zielbereich.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt, class _Fn1> inline
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Fn1 _Func);
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `transform`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Transformation](../standard-library/algorithm-functions.md#transform).

## <a name="unique-stlclr"></a><a name="unique"></a>eindeutig (STL/CLR)

Entfernt doppelte Elemente, die in einem angegebenen Bereich nebeneinander angeordnet sind.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `unique`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [Unique](../standard-library/algorithm-functions.md#unique).

## <a name="unique_copy-stlclr"></a><a name="unique_copy"></a>unique_copy (STL/CLR)

Kopiert Elemente aus einem Quellbereich in einen Zielbereich mit Ausnahmen von doppelten Elementen, die nebeneinander angeordnet sind.

### <a name="syntax"></a>Syntax

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `unique_copy`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [unique_copy](../standard-library/algorithm-functions.md#unique_copy).

## <a name="upper_bound-stlclr"></a><a name="upper_bound"></a>upper_bound (STL/CLR)

Sucht die Position des ersten Elements in einem sortierten Bereich, der über einen Wert größer als einen angegebenen Wert verfügt. Dabei wird das Sortierkriterium möglicherweise von einen binären Prädikat bestimmt.

### <a name="syntax"></a>Syntax

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verhält sich wie die `upper_bound`C++ der Standard Bibliotheksfunktion. Weitere Informationen finden Sie unter [upper_bound](../standard-library/algorithm-functions.md#upper_bound).
