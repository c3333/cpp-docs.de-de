---
title: boyer_moore_horspool_searcher Klasse
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 4d404b414ad632e02be5f4e9fad0e22cefb86ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366775"
---
# <a name="boyer_moore_horspool_searcher-class"></a>boyer_moore_horspool_searcher Klasse

Die `boyer_moore_horspool_searcher` Klasse ist ein Funktionsobjekttyp, der den Boyer-Moore-Horspool-Algorithmus verwendet, um nach einer Sequenz zu suchen, die im Konstruktor des Objekts angegeben ist. Die Suche erfolgt in einer anderen Sequenz, die dem Funktionsaufrufoperator des Objekts bereitgestellt wird. Diese Klasse wird als Parameter an eine der Überladungen von [std::search](algorithm-functions.md#search)übergeben.

## <a name="syntax"></a>Syntax

```cpp
template <
    class RandomAccessIterator,
    class Hash = hash<typename iterator_traits<RandomAccessIterator>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_horspool_searcher
{
    boyer_moore_horspool_searcher(
        RandomAccessIterator pat_first,
        RandomAccessIterator pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>Member

| | |
| - | - |
| **Konstruktor** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | |
| **Operatoren** | |
| [Operator()](#operator-call) | |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a>boyer_moore_horspool_searcher Konstruktor

Erstellt ein `boyer_moore_horspool_searcher` Funktionsobjekt mithilfe der sequenziumsierenden Suche, eines Hashfunktionsobjekts und eines Gleichheitsprädikats.

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parameter

*pat_first*\
Das anfangse Element der Sequenz, nach der gesucht werden soll.

*pat_last*\
Das Ende der Sequenz, nach der gesucht werden soll.

*Hf*\
Ein aufrufbares Objekt, das zum Hashen der Sequenzelemente verwendet wird.

*Pred*\
Das optionale Gleichheitsvergleichsprädikat für Sequenzelemente. Wenn kein Gleichheitsvergleichstyp angegeben ist, `std::equal_to`lautet der Standardwert .

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme aus, die vom Kopierkonstruktor der *Typen BinaryPredicate*, *Hash*oder *RandomAccessIterator* oder vom Aufrufoperator von *BinaryPredicate* oder *Hash*ausgelöst wird.

Diese Klasse ist neu in C++17.

## <a name="operator"></a><a name="operator-call"></a>Operator()

Der Aufrufoperator des Funktionsobjekts. Sucht innerhalb der `[first, last)` Argumentsequenz nach der Sequenz, die dem Konstruktor angegeben ist.

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Parameter

*Ersten*\
Das anfangse Element der Sequenz, innerhalb der gesucht werden soll.

*letzte*\
Das Ende der Sequenz, innerhalb der gesucht werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn das `[pat_first, pat_last)` Suchmuster leer `make_pair(first, first)`ist, wird zurückgegeben. Wenn das Suchmuster nicht gefunden `make_pair(last, last)`wird, wird zurückgegeben. Andernfalls wird ein Paar von Iteratoren an den `[first, last)` Anfang und `[pat_first, pat_last)` das Ende einer Sequenz zurückgegeben, die gemäß dem Prädikat *sprädikats .*

Diese Klasse ist neu in C++17.

## <a name="see-also"></a>Siehe auch

[\<funktionale>](functional.md)\
[Algorithmusfunktionen](algorithm-functions.md)\
[boyer_moore_searcher Klasse](boyer-moore-searcher-class.md)\
[std::suchen](algorithm-functions.md#search)
