---
title: regex_iterator-Klasse
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
ms.openlocfilehash: 6bc57d6815fa6f30e26b22e9b7ab758a1ac20e16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374554"
---
# <a name="regex_iterator-class"></a>regex_iterator-Klasse

Iteratorklasse für Übereinstimmungen.

## <a name="syntax"></a>Syntax

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parameter

*BidIt*\
Der Itertatortyp für Teilübereinstimmungen.

*Elem*\
Der zu entsprechende Elementtyp.

*RXtraits*\
Merkmalklasse für Elemente.

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt ein konstantes Vorwärts-Iteratorobjekt. Anschließend extrahiert sie Objekte des Typs `match_results<BidIt>` durch wiederholtes Anwenden seines regulären Ausdrucksobjekts `*pregex` auf die vom Iteratorbereich `[begin, end)`definierte Zeichenfolge.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[regex_iterator](#regex_iterator)|Erstellt den Iterator.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[difference_type](#difference_type)|Der Typ einer Iteratordifferenz.|
|[Iterator_category](#iterator_category)|Der Typ der Iteratorkategorie.|
|[Zeiger](#pointer)|Der Typ eines Zeigers auf eine Übereinstimmung.|
|[Verweis](#reference)|Der Typ eines Verweises auf eine Übereinstimmung.|
|[regex_type](#regex_type)|Der Typ des regulären Ausdrucks, der übereinstimmen soll.|
|[Value_type](#value_type)|Der Typ einer Übereinstimmung.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator!=](#op_neq)|Vergleicht Iteratoren auf Ungleichheit.|
|[Operator*](#op_star)|Greift auf die gekennzeichnete Übereinstimmung zu.|
|[Operator++](#op_add_add)|Erhöht den Iterator.|
|[Operator=](#op_eq)|Vergleicht Iteratoren auf Gleichheit.|
|[Operator->](#op_arrow)|Greift auf die gekennzeichnete Übereinstimmung zu.|

## <a name="requirements"></a>Anforderungen

**Header:** \<regex >

**Namespace:** std

## <a name="examples"></a>Beispiele

Beispiele zu regulären Ausdrücken finden Sie in den folgenden Themen:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [swap](../standard-library/regex-functions.md#swap)

```cpp
// std__regex__regex_iterator.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "axayaz";
    Myiter::regex_type rx("a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == a
match == a
match == a
```

## <a name="regex_iteratordifference_type"></a><a name="difference_type"></a>regex_iterator::difference_type

Der Typ einer Iteratordifferenz.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `std::ptrdiff_t`.

## <a name="regex_iteratoriterator_category"></a><a name="iterator_category"></a>regex_iterator::iterator_category

Der Typ der Iteratorkategorie.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `std::forward_iterator_tag`.

## <a name="regex_iteratoroperator"></a><a name="op_neq"></a>regex_iterator::Operator!=

Vergleicht Iteratoren auf Ungleichheit.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Iterator für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `!(*this == right)` zurück.

## <a name="regex_iteratoroperator"></a><a name="op_star"></a>regex_iterator::Operator*

Greift auf die gekennzeichnete Übereinstimmung zu.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion gibt den gespeicherten Wert `match`zurück.

## <a name="regex_iteratoroperator"></a><a name="op_add_add"></a>regex_iterator::operator++

Erhöht den Iterator.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Bemerkungen

Wenn die aktuelle Übereinstimmung keine Zeichen enthält, ruft der erste Operator `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`auf. Andernfalls verschiebt er den gespeicherten Wert `begin` so, dass dieser auf das erste Zeichen nach der aktuellen Übereinstimmung zeigt, und ruft dann `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`auf. Schlägt die Suche fehl, legt der Operator in beiden Fällen das Objekt auf einen Sequenzende-Iterator fest. Der Operator gibt das Objekt zurück.

Der zweite Operator erstellt eine Kopie des Objekts, erhöht das Objekt und gibt dann die Kopie zurück.

## <a name="regex_iteratoroperator"></a><a name="op_eq"></a>regex_iterator::operator=

Vergleicht Iteratoren auf Gleichheit.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Iterator für den Vergleich.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `*this` true zurück, wenn und *rechts* beide End-of-Sequence-Iteratoren sind `begin == right.begin`oder `end == right.end` `pregex == right.pregex`wenn `flags == right.flags`keines der beiden Iterators am Ende der Sequenz und , , und , und . Andernfalls wird „false“ zurückgegeben.

## <a name="regex_iteratoroperator-gt"></a><a name="op_arrow"></a>regex_iterator::Operator-&gt;

Greift auf die gekennzeichnete Übereinstimmung zu.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Adresse des gespeicherten Werts `match`zurück.

## <a name="regex_iteratorpointer"></a><a name="pointer"></a>regex_iterator::pointer

Der Typ eines Zeigers auf eine Übereinstimmung.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `match_results<BidIt>*`, wobei `BidIt` der Vorlagenparameter ist.

## <a name="regex_iteratorreference"></a><a name="reference"></a>regex_iterator::Referenz

Der Typ eines Verweises auf eine Übereinstimmung.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `match_results<BidIt>&`, wobei `BidIt` der Vorlagenparameter ist.

## <a name="regex_iteratorregex_iterator"></a><a name="regex_iterator"></a>regex_iterator::regex_iterator

Erstellt den Iterator.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parameter

*Ersten*\
Anfang der Sequenz, die übereinstimmen soll.

*letzte*\
Ende der Sequenz, die übereinstimmen soll.

*Re*\
Regulärer Ausdruck für Übereinstimmungen.

*F*\
Flags für Übereinstimmungen.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt einen Sequenzende-Iterator. Der zweite Konstruktor initialisiert `begin` den gespeicherten Wert mit *first*, `pregex` `&re`dem gespeicherten `flags` Wert `end` mit *last*, dem gespeicherten Wert mit und dem gespeicherten Wert mit *f*. Anschließend wird `regex_search(begin, end, match, *pregex, flags)`aufgerufen. Wenn bei der Suche ein Fehler auftritt, legt der Konstruktor für das Objekt einen Sequenzende-Iterator fest.

## <a name="regex_iteratorregex_type"></a><a name="regex_type"></a>regex_iterator::regex_type

Der Typ des regulären Ausdrucks, der übereinstimmen soll.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Bemerkungen

Die Typedef ist ein Synonym für `basic_regex<Elem, RXtraits>`.

## <a name="regex_iteratorvalue_type"></a><a name="value_type"></a>regex_iterator::value_type

Der Typ einer Übereinstimmung.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für `match_results<BidIt>`, wobei `BidIt` der Vorlagenparameter ist.

## <a name="see-also"></a>Siehe auch

[\<regex>](../standard-library/regex.md)\
[regex_constants-Klasse](../standard-library/regex-constants-class.md)\
[regex_error-Klasse](../standard-library/regex-error-class.md)\
[\<regex> Funktionen](../standard-library/regex-functions.md)\
[regex_iterator-Klasse](../standard-library/regex-iterator-class.md)\
[\<regex> Operatoren](../standard-library/regex-operators.md)\
[regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md)\
[regex_traits-Klasse](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
