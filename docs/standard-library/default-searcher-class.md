---
title: default_searcher-Klasse
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 307fc6da3b383690e0b65bff2a72f386a37d6711
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039689"
---
# <a name="default_searcher-class"></a>default_searcher-Klasse

Ein `default_searcher` ist ein Funktions Objekttyp für Vorgänge, die nach einer im Konstruktor des Objekts angegebenen Sequenz suchen. Die Suche erfolgt innerhalb einer anderen Sequenz, die für den Funktions Aufrufoperator des Objekts bereitgestellt wird. `default_searcher`Ruft [Std:: Search](algorithm-functions.md#search) auf, um die Suche auszuführen.

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

| Member | BESCHREIBUNG |
| - | - |
| **Konstruktor** | |
| [default_searcher](#default-searcher-constructor) | Erstellt eine Searcher-Instanz. |
| **Operatoren** | |
| [Operator ()](#operator-call) | Ruft den Vorgang für die Sequenz auf. |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a> default_searcher-Konstruktor

Erstellt ein `default_searcher` Funktions Objekt, indem die zu suchende Sequenz und ein Gleichheits Prädikat verwendet werden.

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
Das ursprüngliche Element der Sequenz, nach der gesucht werden soll.

*pat_last*\
Das Ende der Sequenz, nach der gesucht werden soll.

*pred*\
Das optionale Gleichheits Vergleichs Prädikat für Sequenz Elemente. Wenn kein Gleichheits Vergleichstyp angegeben wird, ist der Standardwert `std::equal_to` .

### <a name="remarks"></a>Bemerkungen

Löst eine beliebige Ausnahme aus, die vom Kopierkonstruktor der Typen *BinaryPredicate* oder *ForwardIterator* ausgelöst wird.

Diese Klasse ist neu in c++ 17. C++ 20 hat den Konstruktor erstellt **`constexpr`** .

## <a name="operator"></a><a name="operator-call"></a> Operator ()

Der calloperator des Funktions Operators. Sucht innerhalb der Argument Sequenz `[first, last)` nach der Sequenz, die für den Konstruktor angegeben wird.

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

*erstes*\
Das ursprüngliche Element der Sequenz, in der gesucht werden soll.

*letzten*\
Das Ende der Sequenz, in der gesucht werden soll.

### <a name="remarks"></a>Bemerkungen

Gibt ein Paar von Iteratoren zurück. Der anfängliche Iterator *i* ist das effektive Ergebnis von:

`std::search( first, last, pat_first, pat_last, pred )`.

Der zweite Iterator des Paars ist " *Last* ", wenn " *i**" der *Letzte*Wert ist. Andernfalls ist dies das effektive Ergebnis von:

`std::next( i, std::distance( pat_first, pat_last ))`.

Diese Klasse ist neu in c++ 17. C++ 20 hat den-Operator aufgerufen **`constexpr`** .

## <a name="see-also"></a>Weitere Informationen

[\<functional>](functional.md)\
[algorithmusfunktionen](algorithm-functions.md)\
[Std:: Search](algorithm-functions.md#search)
