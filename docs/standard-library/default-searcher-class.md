---
title: default_searcher Klasse
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 2c8b93b83b271f787c993f789e1a68f84a60f016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368925"
---
# <a name="default_searcher-class"></a>default_searcher-Klasse

A `default_searcher` ist ein Funktionsobjekttyp für Vorgänge, die nach einer sequenziumsierten Sequenz suchen, die im Konstruktor des Objekts angegeben ist. Die Suche erfolgt in einer anderen Sequenz, die dem Funktionsaufrufoperator des Objekts bereitgestellt wird. Der `default_searcher` ruft [std::search](algorithm-functions.md#search) auf, um die Suche durchzuführen.

## <a name="syntax"></a>Syntax

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>Member

| | |
| - | - |
| **Konstruktor** | |
| [default_searcher](#default-searcher-constructor) | |
| **Operatoren** | |
| [Operator()](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>default_searcher Konstruktor

Erstellt ein `default_searcher` Funktionsobjekt mithilfe der Sequenz zum Suchen und eines Gleichheitsprädikats.

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parameter

*pat_first*\
Das anfangse Element der Sequenz, nach der gesucht werden soll.

*pat_last*\
Das Ende der Sequenz, nach der gesucht werden soll.

*Pred*\
Das optionale Gleichheitsvergleichsprädikat für Sequenzelemente. Wenn kein Gleichheitsvergleichstyp angegeben ist, `std::equal_to`lautet der Standardwert .

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme aus, die vom Kopierkonstruktor der *BinaryPredicate-* oder *ForwardIterator-Typen* ausgelöst wird.

Diese Klasse ist neu in C++17. C++20 machte den `constexpr`Konstruktor .

## <a name="operator"></a><a name="operator-call"></a>Operator()

Der Aufrufoperator des Funktionsoperators. Sucht innerhalb der `[first, last)` Argumentsequenz nach der Sequenz, die dem Konstruktor angegeben ist.

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>Parameter

*Ersten*\
Das anfangse Element der Sequenz, innerhalb der gesucht werden soll.

*letzte*\
Das Ende der Sequenz, innerhalb der gesucht werden soll.

### <a name="remarks"></a>Bemerkungen

Gibt ein Paar von Iteratoren zurück. Der anfängliche Iterator *i* ist das effektive Ergebnis von:

`std::search( first, last, pat_first, pat_last, pred )`.

Der zweite Iterator des Paares ist *der letzte,* wenn *i** *der letzte*ist. Andernfalls ist es das effektive Ergebnis von:

`std::next( i, std::distance( pat_first, pat_last ))`.

Diese Klasse ist neu in C++17. C++20 hat den `constexpr`Anrufoperator gemacht.

## <a name="see-also"></a>Siehe auch

[\<funktionale>](functional.md)\
[Algorithmusfunktionen](algorithm-functions.md)\
[std::suchen](algorithm-functions.md#search)
