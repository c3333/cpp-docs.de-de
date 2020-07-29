---
title: '&lt;string_view- &gt; Operatoren'
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: 39727177ff0fe88e2fcc105a6cee49711b36de6e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222236"
---
# <a name="ltstring_viewgt-operators"></a>&lt;string_view- &gt; Operatoren

Verwenden Sie diese Operatoren zum Vergleichen von zwei string_view Objekten oder einer string_view und eines anderen Zeichen folgen Objekts (z. b. " [Std:: String](basic-string-class.md)" oder " **Char \* **"), für das eine implizite Konvertierung bereitgestellt wird.

||||
|-|-|-|
|[Operator! =](#op_neq)|[KOM&gt;](#op_gt)|[KOM&gt;=](#op_gt_eq)|
|[KOM&lt;](#op_lt)|[KOM&lt;&lt;](#op_lt_lt)|[KOM&lt;=](#op_lt_eq)|
|[Operator = =](#op_eq_eq)|[Operator "" SV](#op_sv)|

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Testet, ob das Objekt links vom Operator ungleich dem Objekt rechts vom Operator ist.

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

*Richting*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Objekt links vom Operator nicht lexikografisch gleich dem Objekt rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Es muss eine implizite Konvertierung von *convertible_string_type* zum string_view auf der anderen Seite vorhanden sein.

Der Vergleich basiert auf einem Paar weisen lexikografischen Vergleich der Zeichen folgen. Wenn Sie die gleiche Anzahl von Elementen aufweisen und die Elemente alle gleich sind, sind die beiden Objekte gleich. Andernfalls sind sie ungleich.

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Testet, ob das Objekt links vom Operator gleich dem Objekt rechts vom Operator ist.

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

*Richting*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Objekt links vom Operator lexikografisch gleich dem Objekt auf der rechten Seite ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Es muss eine implizite Konvertierung von *convertible_string_type* zum string_view auf der anderen Seite vorhanden sein.

Der Vergleich basiert auf einem Paar weisen lexikografischen Vergleich der Zeichen folgen. Wenn Sie die gleiche Anzahl von Elementen aufweisen und die Elemente alle gleich sind, sind die beiden Objekte gleich.

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob das Objekt links vom Operator kleiner als das Objekt auf der rechten Seite ist sidestring_view

```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

*Richting*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Objekt links vom Operator lexikografisch kleiner ist als das Objekt auf der rechten Seite. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Es muss eine implizite Konvertierung von *convertible_string_type* zum string_view auf der anderen Seite vorhanden sein.

Der Vergleich basiert auf einem Paar weisen lexikografischen Vergleich der Zeichen folgen. Wenn das erste ungleiche paar von Zeichen gefunden wird, wird das Ergebnis dieses Vergleichs zurückgegeben. Wenn keine ungleichen Zeichen gefunden werden, aber eine Sequenz kürzer ist, ist die kürzere Sequenz kleiner als die längere Sequenz. Mit anderen Worten: "Cat" ist kleiner als "Katzen".

### <a name="example"></a>Beispiel

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Testet, ob das Objekt links vom Operator kleiner oder gleich dem Objekt auf der rechten Seite ist.

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

*Richting*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Objekt links vom Operator lexikografisch kleiner als oder gleich dem Objekt rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Siehe [Operator &lt; ](#op_lt).

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>KOM&lt;&lt;

Schreibt eine string_view in einen Ausgabestream.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Parameter

*Ostr*\
ein Ausgabestream, in den geschrieben wird.

*SRT*\
Der string_view, der in einen Ausgabestream eingegeben werden soll.

### <a name="return-value"></a>Rückgabewert

ein Ausgabestream, in den geschrieben wird.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Operator, um den Inhalt einer string_view in einen Ausgabestream einzufügen, z. b. mit [Std:: cout](iostream.md#cout).

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Testet, ob das Objekt links vom Operator größer als das Objekt auf der rechten Seite ist.

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

*Richting*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Objekt links vom Operator lexikografisch größer als das string_view Objekt rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Siehe [Operator &lt; ](#op_lt).

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Testet, ob das Objekt links vom Operator größer oder gleich dem Objekt auf der rechten Seite ist.

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

*Richting*\
Alle konvertierbaren Zeichen folgen Typen oder ein Objekt vom Typ `basic_string_view` , das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das-Objekt links vom Operator lexikografisch größer als oder gleich dem-Objekt rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Siehe [Operator &lt; ](#op_lt).

## <a name="operator-sv-string_view-literal"></a><a name="op_sv"></a>Operator "" SV (string_view Literale)

Erstellt eine string_view aus einem Zeichenfolgenliteral. Erfordert Namespace `std::literals::string_view_literals` .

### <a name="example"></a>Beispiel

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>Weitere Informationen

[\<string_view>](../standard-library/string-view.md)
