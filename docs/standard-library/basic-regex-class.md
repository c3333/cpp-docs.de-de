---
title: basic_regex-Klasse
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 74a8684c619e2cfbd5417950aa6108ad93511bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376745"
---
# <a name="basic_regex-class"></a>basic_regex-Klasse

Umschließt einen regulären Ausdruck.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>Parameter

*Elem*\
Der zu entsprechende Elementtyp.

*RXtraits*\
Merkmalklasse für Elemente.

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt ein Objekt, das einen regulären Ausdruck enthält. Objekte dieser Klassenvorlage können an die Vorlagenfunktionen [regex_match ,](../standard-library/regex-functions.md#regex_match) [regex_search](../standard-library/regex-functions.md#regex_search)und [regex_replace](../standard-library/regex-functions.md#regex_replace)sowie an geeignete Textzeichenfolgenargumente übergeben werden, um nach Text zu suchen, der dem regulären Ausdruck entspricht. Es gibt zwei Spezialisierungen dieser Klassenvorlage mit den Typdefinitionen [regex](../standard-library/regex-typedefs.md#regex) für Elemente vom Typ **char**und [wregex](../standard-library/regex-typedefs.md#wregex) für Elemente vom Typ **wchar_t**.

Das Vorlagenargument *RXtraits* beschreibt verschiedene wichtige Eigenschaften der Syntax der regulären Ausdrücke, die von der Klassenvorlage unterstützt werden. Eine Klasse, die diese Eigenschaften für reguläre Ausdrücke angibt, muss dieselbe externe Schnittstelle wie ein Objekt vom Typ [regex_traits Klasse](../standard-library/regex-traits-class.md)aufweisen.

Einige Funktionen akzeptieren eine Operandensequenz, die einen regulären Ausdruck definiert. Sie können eine solche Operandensequenz wie folgt angeben:

`ptr`-- eine null-terminierte Sequenz (z. B. eine C-Zeichenfolge, für *Elem* vom Typ **char**), beginnend `ptr` bei `value_type()` (die kein Nullzeiger sein darf), wobei das beendende Element der Wert ist und nicht Teil der Operandensequenz ist

`ptr`, `count` – eine Sequenz von `count`-Elementen, die bei `ptr` (darf kein NULL-Zeiger sein) beginnen

`str` – die vom `basic_string`-Objekt `str` angegebene Sequenz

`first`, `last` – eine Sequenz von Elementen, die durch die Iteratoren `first` und `last` im Bereich `[first, last)` abgegrenzt werden

`right` – das `basic_regex`-Objekt `right`

Diese Memberfunktionen verwenden `flags` auch ein Argument, das verschiedene Optionen für die Interpretation des regulären Ausdrucks zusätzlich zu den vom *Typ RXtraits* beschriebenen Optionen angibt.

### <a name="members"></a>Member

|Member|Standardwert|
|-|-|
|öffentliche statische const flag_type icase|regex_constants::icase|
|öffentliche statische const flag_type nosubs|regex_constants::nosubs|
|öffentliche statische const flag_type optimieren|regex_constants::optimieren|
|öffentliche statische const flag_type kollat|regex_constants::collate|
|öffentliche statische const flag_type ECMAScript|regex_constants::ECMAScript|
|öffentliche statische const flag_type basis|regex_constants::basic|
|öffentliche statische const flag_type erweitert|regex_constants::erweitert|
|öffentliche statische const flag_type awk|regex_constants::awk|
|öffentliche statische const flag_type grep|regex_constants::grep|
|öffentliche statische const flag_type egrep|regex_constants::egrep|
|private RXtraits-Eigenschaften||

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_regex](#basic_regex)|Konstruiert das reguläre Ausdrucksobjekt.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[flag_type](#flag_type)|Der Typ der Syntaxoptionsflags.|
|[locale_type](#locale_type)|Der Typ des gespeicherten Gebietsschemaobjekts.|
|[Value_type](#value_type)|Der Elementtyp.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Zuweisen](#assign)|Weist dem Objekt für einen regulären Ausdruck einen Wert zu.|
|[Flaggen](#flags)|Gibt Syntaxoptionsflags zurück.|
|[getloc](#getloc)|Gibt das gespeicherte Gebietsschemaobjekt zurück.|
|[imbue](#imbue)|Ändert das gespeicherte Gebietsschemaobjekt.|
|[mark_count](#mark_count)|Gibt die Anzahl der übereinstimmenden Teilausdrücke zurück.|
|[swap](#swap)|Tauscht zwei Objekte mit regulärem Ausdruck.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_eq)|Weist dem Objekt für einen regulären Ausdruck einen Wert zu.|

## <a name="requirements"></a>Anforderungen

**Header:** \<regex >

**Namespace:** std

## <a name="example"></a>Beispiel

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="basic_regexassign"></a><a name="assign"></a>basic_regex::zuweisen

Weist dem Objekt für einen regulären Ausdruck einen Wert zu.

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>Parameter

*STtraits*\
Merkmalklasse für eine Zeichenfolgequelle.

*STalloc*\
Zuweisungsklasse für eine Zeichenfolgequelle.

*Init*\
Eingabeiteratortyp für eine Bereichsquelle.

*Richting*\
Zu kopierende RegEx-Quelle.

*Ptr*\
Zeiger zum Anfang der zu kopierenden Sequenz.

*Flaggen*\
Syntaxoptionsflags, die beim Kopieren hinzugefügt werden.

*len/TD>*\
Länge der zu kopierenden Sequenz.

*Str*\
Zu kopierende Zeichenfolge.

*Ersten*\
Anfang der zu kopierenden Sequenz.

*letzte*\
Ende der zu kopierenden Sequenz.

*Ilist*\
Das zu kopierende initializer_list-Element.

### <a name="remarks"></a>Bemerkungen

Jede Memberfunktion ersetzt den regulären Ausdruck, der in `*this` enthalten ist durch den regulären Ausdruck, der in der Operandensequenz enthalten ist und gibt dann `*this` zurück.

## <a name="basic_regexbasic_regex"></a><a name="basic_regex"></a>basic_regex::basic_regex

Konstruiert das reguläre Ausdrucksobjekt.

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>Parameter

*STtraits*\
Merkmalklasse für eine Zeichenfolgequelle.

*STalloc*\
Zuweisungsklasse für eine Zeichenfolgequelle.

*Init*\
Eingabeiteratortyp für eine Bereichsquelle.

*Richting*\
Zu kopierende RegEx-Quelle.

*Ptr*\
Zeiger zum Anfang der zu kopierenden Sequenz.

*Flaggen*\
Syntaxoptionsflags, die beim Kopieren hinzugefügt werden.

*len/TD>*\
Länge der zu kopierenden Sequenz.

*Str*\
Zu kopierende Zeichenfolge.

*Ersten*\
Anfang der zu kopierenden Sequenz.

*letzte*\
Ende der zu kopierenden Sequenz.

*Ilist*\
Das zu kopierende initializer_list-Element.

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren speichern ein standardmäßig erstelltes Objekt vom Typ `RXtraits`.

Der erste Konstruktor erstellt ein leeres `basic_regex`-Objekt. Die anderen Konstruktoren erstellen ein `basic_regex`-Objekt, das den regulären Ausdruck enthält, der von der Operandensequenz beschrieben wird.

Ein `basic_regex` leeres Objekt stimmt mit keiner Zeichensequenz überein, wenn es an [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)oder [regex_replace](../standard-library/regex-functions.md#regex_replace)übergeben wird.

## <a name="basic_regexflag_type"></a><a name="flag_type"></a>basic_regex::flag_type

Der Typ der Syntaxoptionsflags.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="basic_regexflags"></a><a name="flags"></a>basic_regex::Flaggen

Gibt Syntaxoptionsflags zurück.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt den Wert des `flag_type`-Arguments zurück, das an den letzten Aufruf einer der [basic_regex::assign](#assign)-Memberfunktionen übergeben wurde. Wenn kein Aufruf erfolgt ist, wird der an den Konstruktor übergebene Wert zurückgegeben.

## <a name="basic_regexgetloc"></a><a name="getloc"></a>basic_regex::getloc

Gibt das gespeicherte Gebietsschemaobjekt zurück.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `traits.`gibt [regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`zurück.

## <a name="basic_regeximbue"></a><a name="imbue"></a>basic_regex::imbue

Ändert das gespeicherte Gebietsschemaobjekt.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parameter

*Loc*\
Das zu speichernde Gebietsschemaobjekt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `*this` leert `traits.`sich und gibt [regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`zurück.

## <a name="basic_regexlocale_type"></a><a name="locale_type"></a>basic_regex::locale_type

Der Typ des gespeicherten Gebietsschemaobjekts.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="basic_regexmark_count"></a><a name="mark_count"></a>basic_regex::mark_count

Gibt die Anzahl der übereinstimmenden Teilausdrücke zurück.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Anzahl der Erfassungsgruppen im regulären Ausdruck zurück.

## <a name="basic_regexoperator"></a><a name="op_eq"></a>basic_regex::operator=

Weist dem Objekt für einen regulären Ausdruck einen Wert zu.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parameter

*STtraits*\
Merkmalklasse für eine Zeichenfolgequelle.

*STalloc*\
Zuweisungsklasse für eine Zeichenfolgequelle.

*Richting*\
Zu kopierende RegEx-Quelle.

*Str*\
Zu kopierende Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Jeder Operator ersetzt den regulären Ausdruck, der in `*this` enthalten ist, durch den regulären Ausdruck, der in der Operandensequenz enthalten ist, und gibt dann `*this`zurück.

## <a name="basic_regexswap"></a><a name="swap"></a>basic_regex::swap

Tauscht zwei Objekte mit regulärem Ausdruck.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parameter

*Richting*\
Das Objekt mit regulärem Ausdruck, gegen das getauscht werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion tauscht die `*this` regulären Ausdrücke zwischen und *rechts*aus. Die Funktion führt dies in konstanter Zeit aus und löst keine Ausnahmen aus.

## <a name="basic_regexvalue_type"></a><a name="value_type"></a>basic_regex::value_type

Der Elementtyp.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für den Vorlagenparameter *Elem*.

## <a name="see-also"></a>Siehe auch

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[Regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits-Klasse](../standard-library/regex-traits-class.md)
