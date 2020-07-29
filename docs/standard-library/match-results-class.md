---
title: match_results-Klasse
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 8ce9ed987baf63f2cc9f095e2955a8165e977193
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212214"
---
# <a name="match_results-class"></a>match_results-Klasse

Enthält eine Sequenz von Teilübereinstimmungen.

## <a name="syntax"></a>Syntax

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Parameter

*Bidit*\
Der Itertatortyp für Teilübereinstimmungen.

*Zuordnungseinheits*\
Der Typ einer Zuweisung für die Speicherverwaltung.

## <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage beschreibt ein Objekt, das eine nicht änderbare Sequenz von Elementen vom Typ steuert, die `sub_match<BidIt>` durch eine Suche mit regulären Ausdrücken generiert wird. Jedes Element verweist auf die Untersequenz, die mit der Erfassungsgruppe übereinstimmt, die diesem Element entspricht.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[match_results](#match_results)|Erstellt das Objekt.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[allocator_type](#allocator_type)|Der Typ einer Zuweisung für die Speicherverwaltung.|
|[char_type](#char_type)|Der Typ eines Elements.|
|[const_iterator](#const_iterator)|Der Itertatortyp „const“ für Teilübereinstimmungen.|
|[const_reference](#const_reference)|Der Typ eines Konstantenverweises auf ein Element.|
|[difference_type](#difference_type)|Der Typ einer Iteratordifferenz.|
|[Iterator](#iterator)|Der Itertatortyp für Teilübereinstimmungen.|
|[Referenz](#reference)|Der Typ eines Elementverweises.|
|[size_type](#size_type)|Der Typ einer Teilübereinstimmungszählers.|
|[string_type](#string_type)|Der Typ einer Zeichenfolge.|
|[value_type](#value_type)|Der Typ einer Teilübereinstimmung.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[beginnen](#begin)|Kennzeichnet den Anfang einer Teilübereinstimmungssequenz.|
|[empty](#empty)|Testet, ob keine Teilübereinstimmungen vorliegen.|
|[end](#end)|Designates end of submatch sequence.|
|[format](#format)|Formatiert Teilübereinstimmungen.|
|[get_allocator](#get_allocator)|Gibt die gespeicherte Zuweisung zurück.|
|[length](#length)|Gibt die Länge einer Teilübereinstimmung zurück.|
|[max_size](#max_size)|Ruft die größte Anzahl von Teilübereinstimmungen ab.|
|[gebracht](#position)|Ruft das Startoffset einer Untergruppe ab.|
|[Präfix](#prefix)|Ruft die Sequenz vor der ersten Teilübereinstimmung ab.|
|[size](#size)|Zählt, wie viele Teilübereinstimmungen es gibt.|
|[str](#str)|Gibt eine Teilübereinstimmung zurück.|
|[Suffix](#suffix)|Ruft die Sequenz nach der letzten Teilübereinstimmung ab.|
|[swap](#swap)|Tauscht zwei match_results-Objekte.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator =](#op_eq)|Kopieren Sie ein match_results-Objekt.|
|[KOM\[\]](#op_at)|Zugriff auf ein Unterobjekt.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<regex>

**Namespace:** std

## <a name="example"></a>Beispiel

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="match_resultsallocator_type"></a><a name="allocator_type"></a>match_results:: allocator_type

Der Typ einer Zuweisung für die Speicherverwaltung.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Bemerkungen

Die TypeDef ist ein Synonym für das Vorlagen Argument " *Zuweisung*".

## <a name="match_resultsbegin"></a><a name="begin"></a>match_results:: begin

Kennzeichnet den Anfang einer Teilübereinstimmungssequenz.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Iterator mit wahlfreiem Zugriff zurück, der auf das erste Element der Sequenz zeigt (bzw. gerade über das Ende einer leeren Sequenz hinaus).

## <a name="match_resultschar_type"></a><a name="char_type"></a>match_results:: char_type

Der Typ eines Elements.

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Bemerkungen

Die Typdefinition (typedef) ist ein Synonym für den Typ `iterator_traits<BidIt>::value_type`, der der Elementtyp der Zeichenfolge ist, die durchsucht wurde.

## <a name="match_resultsconst_iterator"></a><a name="const_iterator"></a>match_results:: const_iterator

Der Itertatortyp „const“ für Teilübereinstimmungen.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Bemerkungen

Die Typdefinition beschreibt ein Objekt, das als Iterator für den konstanten zufälligen Zugriff für die kontrollierte Sequenz dienen kann.

## <a name="match_resultsconst_reference"></a><a name="const_reference"></a>match_results:: const_reference

Der Typ eines Konstantenverweises auf ein Element.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Bemerkungen

Die Typdef beschreibt ein Objekt, das als Konstantenverweis für ein Element der gesteuerten Sequenz fungieren kann.

## <a name="match_resultsdifference_type"></a><a name="difference_type"></a>match_results::d ifference_type

Der Typ einer Iteratordifferenz.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Bemerkungen

Typedef ist ein Synonym für den Typ `iterator_traits<BidIt>::difference_type`. Er beschreibt ein Objekt, das die Differenz zwischen zwei beliebigen Iteratoren darstellen kann, die auf Elemente der kontrollierten Sequenz verweisen.

## <a name="match_resultsempty"></a><a name="empty"></a>match_results:: Empty

Testet, ob keine Teilübereinstimmungen vorliegen.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt nur dann „true“, wenn die Suche mit regulärem Ausdruck fehlgeschlagen ist.

## <a name="match_resultsend"></a><a name="end"></a>match_results:: End

Designates end of submatch sequence.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Iterator zurück, der direkt hinter das Ende der Sequenz verweist.

## <a name="match_resultsformat"></a><a name="format"></a>match_results:: Format

Formatiert Teilübereinstimmungen.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Parameter

*OutIt*\
Der Ausgabeiteratortyp.

*vorgenommen*\
Der Ausgabestream, in den geschrieben werden soll.

*fmt*\
Die Formatzeichenfolge.

*fahren*\
Die Formatflags.

### <a name="remarks"></a>Bemerkungen

Jede Member-Funktion generiert formatierten Text unter der Steuerung des Formats *fmt*. Die erste Member-Funktion schreibt den formatierten Text in die Sequenz, die durch das Argument *out* definiert *ist, und gibt zurück*. Die zweite Member-Funktion gibt ein Zeichen folgen Objekt zurück, das eine Kopie des formatierten Texts enthält.

Um formatierten Text zu generieren, wird Literaltext in der Formatzeichenfolge einfach in die Zielsequenz kopiert. Jede Escapesequenz in der Formatzeichenfolge wird vom Text ersetzt, den sie darstellt. Die Details des Kopierens und Ersetzens werden durch die Formatflags gesteuert, die an die Funktion übergeben werden.

## <a name="match_resultsget_allocator"></a><a name="get_allocator"></a>match_results:: Get_allocator

Gibt die gespeicherte Zuweisung zurück.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt eine Kopie des allocator-Objekts zurück, das von verwendet wird **`*this`** , um die zugehörigen `sub_match` Objekte zuzuordnen.

## <a name="match_resultsiterator"></a><a name="iterator"></a>match_results:: Iterator

Der Itertatortyp für Teilübereinstimmungen.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das als Iterator für zufälligen Zugriff für die gesteuerte Sequenz fungieren kann.

## <a name="match_resultslength"></a><a name="length"></a>match_results:: length

Gibt die Länge einer Teilübereinstimmung zurück.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Parameter

*nationale*\
Der Index der Teilübereinstimmung.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `(*this)[sub].length()` zurück.

## <a name="match_resultsmatch_results"></a><a name="match_results"></a>match_results:: match_results

Erstellt das Objekt.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Parameter

*Zuordnungseinheits*\
Das zu speichernde Zuweisungsobjekt.

*Richting*\
Das zu kopierende match_results-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt ein `match_results`-Objekt, das keine Teilübereinstimmungen enthält. Mit dem zweiten Konstruktor wird ein- `match_results` Objekt erstellt, das eine Kopie von *right*ist.

## <a name="match_resultsmax_size"></a><a name="max_size"></a>match_results:: max_size

Ruft die größte Anzahl von Teilübereinstimmungen ab.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Länge der längsten Sequenz zurück, die das Objekt steuern kann.

## <a name="match_resultsoperator"></a><a name="op_eq"></a>match_results:: Operator =

Kopieren Sie ein match_results-Objekt.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Das zu kopierende match_results-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator ersetzt die durch gesteuerte Sequenz durch **`*this`** eine Kopie der von *right*kontrollierten Sequenz.

## <a name="match_resultsoperator"></a><a name="op_at"></a>match_results:: Operator []

Zugriff auf ein Unterobjekt.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Parameter

*Nr*\
Der Index der Teilübereinstimmung.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf das Element *n* der kontrollierten Sequenz oder einen Verweis auf ein leeres `sub_match` Objekt zurück, wenn oder, `size() <= n` Wenn die Erfassungs Gruppe *n* nicht Teil der Entsprechung war.

## <a name="match_resultsposition"></a><a name="position"></a>match_results::p osition

Ruft das Startoffset einer Untergruppe ab.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Parameter

*nationale*\
Der Index der Teilübereinstimmung.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `std::distance(prefix().first, (*this)[sub].first)`zurück, d. h. den Abstand vom ersten Zeichen in der Zielsequenz zum ersten Zeichen in der Teilübereinstimmung, auf die das `n` -Element der kontrollierten Sequenz verweist.

## <a name="match_resultsprefix"></a><a name="prefix"></a>match_results::p refix

Ruft die Sequenz vor der ersten Teilübereinstimmung ab.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Verweis auf ein Objekt des Typs `sub_match<BidIt>` zurück, das auf die Zeichenfolge zeigt, die am Anfang der Zielsequenz beginnt und am `(*this)[0].first`endet, d. h., das Objekt zeigt auf den Text, der der übereinstimmenden Untersequenz voransteht.

## <a name="match_resultsreference"></a><a name="reference"></a>match_results:: Reference

Der Typ eines Elementverweises.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Typ `const_reference`.

## <a name="match_resultssize"></a><a name="size"></a>match_results:: size

Zählt, wie viele Teilübereinstimmungen es gibt.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt entweder einen Wert zurück, der um eins größer ist als die Anzahl von Erfassungsgruppen im regulären Ausdruck, der für die Suche verwendet wurde, oder 0 (null), wenn keine Suche ausgeführt wurde.

## <a name="match_resultssize_type"></a><a name="size_type"></a>match_results:: size_type

Der Typ einer Teilübereinstimmungszählers.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Typ `Alloc::size_type`.

## <a name="match_resultsstr"></a><a name="str"></a>match_results:: Str

Gibt eine Teilübereinstimmung zurück.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Parameter

*nationale*\
Der Index der Teilübereinstimmung.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `string_type((*this)[sub])` zurück.

## <a name="match_resultsstring_type"></a><a name="string_type"></a>match_results:: string_type

Der Typ einer Zeichenfolge.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Typ `basic_string<char_type>`.

## <a name="match_resultssuffix"></a><a name="suffix"></a>match_results:: Suffix

Ruft die Sequenz nach der letzten Teilübereinstimmung ab.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt einen Verweis auf ein Objekt des Typs `sub_match<BidIt>` zurück, das auf die Zeichenfolge zeigt, die bei beginnt `(*this)[size() - 1].second` und am Ende der Zielsequenz endet, d. h., das Objekt zeigt auf den Text, der auf die übereinstimmende Untersequenz folgt.

## <a name="match_resultsswap"></a><a name="swap"></a>match_results:: Swap

Tauscht zwei match_results-Objekte.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Parameter

*Richting*\
Das match_results-Objekt, mit dem getauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion vertauscht den Inhalt von **`*this`** und *Recht* in konstanter Zeit und löst keine Ausnahmen aus.

## <a name="match_resultsvalue_type"></a><a name="value_type"></a>match_results:: value_type

Der Typ einer Teilübereinstimmung.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Bemerkungen

Die Typedef ist ein Synonym für den Typ `sub_match<BidIt>`.

## <a name="see-also"></a>Weitere Informationen

[\<regex>](../standard-library/regex.md)
