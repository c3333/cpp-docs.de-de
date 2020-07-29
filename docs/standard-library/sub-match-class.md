---
title: sub_match-Klasse
ms.date: 09/10/2018
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
ms.openlocfilehash: 57aa4ec366588f71f41a747a2dc5127f87ea2e2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222198"
---
# <a name="sub_match-class"></a>sub_match-Klasse

Beschreibt eine Teilübereinstimmung.

## <a name="syntax"></a>Syntax

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Parameter

*Bidit*\
Der Itertatortyp für Teilübereinstimmungen.

## <a name="remarks"></a>Bemerkungen

In der Klassen Vorlage wird ein Objekt beschrieben, das eine Sequenz von Zeichen festlegt, die einer Erfassungs Gruppe in einem [regex_match](../standard-library/regex-functions.md#regex_match) -oder [regex_search](../standard-library/regex-functions.md#regex_search)-aufrufszeichen entsprach. Objekte des Typs [match_results Class](../standard-library/match-results-class.md) enthalten ein Array dieser Objekte, eines für jede Erfassungsgruppe im regulären Ausdruck, der in der Suche verwendet wurde.

Gab es keine Übereinstimmung mit der Erfassungsgruppe, ist das `matched` -Datenmember des Objekts gleich „false“, und die beiden Iteratoren `first` und `second` (geerbt von der Basisklasse `std::pair`) gleich sind. Gab es eine Übereinstimmung mit der Erfassungsgruppe, ist `matched` gleich „true“, der Iterator `first` zeigt auf das erste Zeichen in der Zielsequenz, die mit der Erfassungsgruppe übereinstimmte, und der Iterator `second` zeigt auf die erste Position hinter dem letzten Zeichen in der Zielsequenz, die mit der Erfassungsgruppe übereinstimmte. Für eine Übereinstimmung der Länge 0 (null) gilt Folgendes: Der Member `matched` enthält „true“, die beiden Iteratoren sind gleich, und beide zeigen auf die Position der Übereinstimmung.

Eine Übereinstimmung der Länge 0 (null) kann auftreten, wenn eine Erfassungsgruppe ausschließlich aus einer Assertion oder aus einer Wiederholung besteht, die 0 (null) Wiederholungen zulässt. Beispiel:

„^“ stimmt mit der Zielsequenz „a“ überein; das `sub_match` -Objekt, das der Erfassungsgruppe 0 entspricht, enthält Iteratoren, die beide auf das erste Zeichen in der Sequenz zeigen.

„b(a*)b“ stimmt mit der Zielsequenz „bb“ überein; das `sub_match` -Objekt, das der Erfassungsgruppe 1 entspricht, enthält Iteratoren, die beide auf das zweite Zeichen in der Sequenz zeigen.

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[difference_type](#difference_type)|Der Typ einer Iteratordifferenz.|
|[Iterator](#iterator)|Der Typ eines Iterators.|
|[value_type](#value_type)|Der Typ eines Elements.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[vergleichbar](#compare)|Vergleichen einer Teilübereinstimmung mit einer Sequenz.|
|[length](#length)|Gibt die Länge einer Teilübereinstimmung zurück.|
|[Kommunen](#matched)|Gibt an, ob eine Übereinstimmung erfolgreich war.|
|[str](#str)|Konvertiert eine Teilübereinstimmung in eine Zeichenfolge.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[der Operator basic_string<value_type>](#op_basic_string_lt_value_type_gt)|Wandelt eine Teilübereinstimmung in eine Zeichenfolge um.|

## <a name="example"></a>Beispiel

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<regex>

**Namespace:** std

## <a name="sub_matchcompare"></a><a name="compare"></a>sub_match:: Compare

Vergleichen einer Teilübereinstimmung mit einer Sequenz.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Die Teilübereinstimmung, mit der verglichen werden soll.

*SRT*\
Die Zeichenfolge, mit der verglichen wird.

*PTR*\
Die mit NULL endende Sequenz, mit der verglichen werden soll.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion vergleicht die passende Sequenz `[first, second)` mit der übereinstimmenden Sequenz `[right.first, right.second)`. Die zweite Memberfunktion vergleicht die passende Sequenz `[first, second)` mit der Zeichensequenz `[right.begin(), right.end())`. Die dritte Memberfunktion vergleicht die passende Sequenz `[first, second)` mit der Zeichensequenz `[right, right + std::char_traits<value_type>::length(right))`.

Jede Funktion gibt Folgendes zurück:

einen negativen Wert, wenn der erste abweichende Wert in der passenden Sequenz weniger als das entsprechende Element in der Operandensequenz vergleicht (wie von `std::char_traits<value_type>::compare` vorgegeben), oder wenn die beiden ein gemeinsames Präfix besitzen, die Zielsequenz jedoch länger ist

NULL, wenn die beiden Vergleichswerte elementweise identisch sind und die gleiche Länge haben

Andernfalls ein positiver Wert

## <a name="sub_matchdifference_type"></a><a name="difference_type"></a>sub_match::d ifference_type

Der Typ einer Iteratordifferenz.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

Die Typedef ist ein Synonym für `iterator_traits<BidIt>::difference_type`.

## <a name="sub_matchiterator"></a><a name="iterator"></a>sub_match:: Iterator

Der Typ eines Iterators.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Bemerkungen

Die Typedef stellt ein Synonym für das Vorlagentypargument `Bidit` dar.

## <a name="sub_matchlength"></a><a name="length"></a>sub_match:: length

Gibt die Länge einer Teilübereinstimmung zurück.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der übereinstimmenden Sequenz oder null zurück, wenn es keine passende Sequenz gab.

## <a name="sub_matchmatched"></a><a name="matched"></a>sub_match:: abgeglichen

Gibt an, ob eine Übereinstimmung erfolgreich war.

```cpp
bool matched;
```

### <a name="remarks"></a>Bemerkungen

Der Member **`true`** ist nur enthalten, wenn die zugeordnete **`*this`** Erfassungs Gruppe Teil der regulären Ausdrucks Übereinstimmung war.

## <a name="sub_matchoperator-basic_stringltvalue_typegt"></a><a name="op_basic_string_lt_value_type_gt"></a>sub_match:: Operator Basic_string &lt; value_type&gt;

Wandelt eine Teilübereinstimmung in eine Zeichenfolge um.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Bemerkungen

Der Memberoperator gibt `str()`zurück.

## <a name="sub_matchstr"></a><a name="str"></a>sub_match:: Str

Konvertiert eine Teilübereinstimmung in eine Zeichenfolge.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `basic_string<value_type>(first, second)` zurück.

## <a name="sub_matchvalue_type"></a><a name="value_type"></a>sub_match:: value_type

Der Typ eines Elements.

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Bemerkungen

Die Typedef ist ein Synonym für `iterator_traits<BidIt>::value_type`.

## <a name="see-also"></a>Siehe auch

[\<regex>](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)
