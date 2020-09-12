---
title: basic_string_view-Klasse
description: Die API-Referenz für `basic_string_view` bezieht sich auf eine Konstante zusammenhängende Sequenz von char-like-Objekten.
ms.date: 9/8/2020
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::ends_with
- xstring/std::basic_string_view::starts_with
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, ends_with
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, starts_with
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 8eddf4bc6aae0338dc2e914aa57e6c1e7cc5c912
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040209"
---
# <a name="basic_string_view-class"></a>basic_string_view-Klasse

Die Klassen Vorlage `basic_string_view<charT>` wurde in c++ 17 hinzugefügt und dient als sichere und effiziente Möglichkeit für eine Funktion, verschiedene nicht verknüpfte Zeichen folgen Typen zu akzeptieren, ohne dass die Funktion für diese Typen Vorlagen Ativ sein muss. Die-Klasse enthält einen nicht besitzenden Zeiger auf eine zusammenhängende Sequenz von Zeichendaten und eine Länge, die die Anzahl der Zeichen in der Sequenz angibt. Es wird davon ausgegangen, ob die Sequenz NULL-terminierte Sequenz hat.

Die Standardbibliothek definiert verschiedene Spezialisierungs Elemente basierend auf dem Typ der Elemente:

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

In diesem Dokument bezieht sich der Begriff "string_view" in der Regel auf diese Typedefs.

Ein string_view der die für das Lesen von Zeichen folgen Daten erforderliche minimale allgemeine Schnittstelle beschreibt. Er bietet Konstanten Zugriff auf die zugrunde liegenden Daten. Es werden keine Kopien erstellt (außer der- `copy` Funktion). Die Daten können an beliebiger Position NULL-Werte ("\ 0") enthalten. Ein string_view hat keine Kontrolle über die Lebensdauer des Objekts. Es liegt in der Verantwortung des Aufrufers, sicherzustellen, dass die zugrunde liegenden Zeichen folgen Daten gültig sind.

Eine Funktion, die einen Parameter vom Typ akzeptiert string_view kann so erstellt werden, dass Sie mit einem beliebigen Zeichen folgen ähnlichen Typ funktioniert, ohne die Funktion in einer Vorlage zu erstellen oder die Funktion auf eine bestimmte Teilmenge von Zeichen folgen Typen einzuschränken. Die einzige Anforderung besteht darin, dass eine implizite Konvertierung vom Zeichen Folgentyp in string_view vorhanden ist. Alle Standard Zeichen folgen Typen können implizit in eine string_view konvertiert werden, die denselben Elementtyp enthält. Anders ausgedrückt: ein kann in `std::string` einen, aber nicht in einen konvertierbar sein `string_view` `wstring_view` .

Das folgende Beispiel zeigt eine nicht-Vorlagen Funktion `f` , die einen Parameter vom Typ annimmt `wstring_view` . Sie kann mit Argumenten vom Typ `std::wstring` , und aufgerufen werden `wchar_t*` `winrt::hstring` .

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>Syntax

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>Parameter

*CharType*\
Der Typ der Zeichen, die im string_view gespeichert werden. Die C++-Standard Bibliothek stellt die folgenden Typedefs für Spezialisierungs Informationen dieser Vorlage bereit.

- [string_view](../standard-library/string-view-typedefs.md#string_view) für Elemente des Typs **`char`**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), für **`wchar_t`**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) für **`char16_t`**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) für **`char32_t`** .

*Aufweisen*\
Standardmäßig [Char_traits](char-traits-struct.md) < *CharType* ->.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_string_view](#basic_string_view)|Erstellt eine string_view, die leer ist, oder verweist auf die Daten eines anderen Zeichen folgen Objekts oder auf ein Zeichen Array im C-Stil.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|**const_iterator**|Random-Access-Iterator, der **`const`** Elemente lesen kann.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**Zeichner**|`using pointer = value_type*;`|
|**Referenz**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Member-Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator =](#op_eq)|Weist einem anderen string_view ein string_view oder konvertierbares Zeichen folgen Objekt zu.|
|[KOM\[\]](#op_at)|Gibt das Element am angegebenen Index zurück.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[at](#at)|Gibt eine const_reference an einem angegebenen Speicherort an das Element zurück.|
|[Zurück](#back)|Gibt eine const_reference an das letzte Element zurück.|
|[beginnen](#begin)|Gibt einen konstanten Iterator zurück, der das erste Element adressiert. (string_views sind unveränderlich.)|
|[cbegin](#cbegin)|Identisch mit [Begin](#begin).|
|[cend](#cend)|Gibt einen konstanten Iterator zurück, der auf eine Stelle hinter dem letzten Element zeigt.|
|[copy](#copy)|Kopiert höchstens eine angegebene Anzahl von Zeichen aus einer indizierten Position in einer Quell string_view in ein Ziel Zeichen Array. (Nicht empfohlen. Verwenden Sie stattdessen _Copy_s.)|
|[_Copy_s](#_copy_s)|Secure CRT-Kopierfunktion.|
|[vergleichbar](#compare)|Vergleicht eine string_view mit einem angegebenen string_view, um zu bestimmen, ob Sie gleich sind, oder ob eine lexikografisch kleiner als die andere ist.|
|[crbegin](#crbegin)|Identisch mit [rbegin](#rbegin).|
|[crend](#crend)|Identisch mit [rend](#rend).|
|[data](#data)|Gibt einen unformatierten, nicht besitzenden Zeiger auf die Zeichenfolge zurück.|
|[empty](#empty)|Testet, ob die string_view Zeichen enthält.|
|[end](#end)|Identisch mit [cend](#cend).|
|[ends_with](#ends_with)<sup>c++ 20</sup>|Überprüfen Sie, ob eine Zeichen folgen Ansicht mit einem angegebenen Suffix endet.|
|[find](#find)|Sucht in Vorwärtsrichtung nach dem ersten Vorkommen einer Teil Zeichenfolge, die mit einer angegebenen Zeichenfolge übereinstimmt.|
|[find_first_not_of](#find_first_not_of)|Sucht nach dem ersten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts ist.|
|[find_first_of](#find_first_of)|Sucht nach dem ersten Zeichen, das mit einem beliebigen Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts übereinstimmt.|
|[find_last_not_of](#find_last_not_of)|Sucht nach dem letzten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts ist.|
|[find_last_of](#find_last_of)|Sucht nach dem letzten Zeichen, das ein Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts ist.|
|[Beifahrer](#front)|Gibt eine const_reference an das erste Element zurück.|
|[length](#length)|Gibt die aktuelle Anzahl von Elementen zurück.|
|[max_size](#max_size)|Gibt die maximale Anzahl von Zeichen zurück, die ein string_view enthalten könnte.|
|[rbegin](#rbegin)|Gibt einen konstanten Iterator zurück, der das erste Element in einem umgekehrten string_view adressiert.|
|[remove_prefix](#remove_prefix)|Verschiebt den Zeiger um die angegebene Anzahl von Elementen vorwärts.|
|[remove_suffix](#remove_suffix)|Verringert die Größe der Ansicht um die angegebene Anzahl von Elementen, beginnend bei der Rückseite.|
|[rend](#rend)|Gibt einen konstanten Iterator zurück, der auf eine Stelle hinter dem letzten Element in einem umgekehrten string_view zeigt.|
|[rfind](#rfind)|Durchsucht eine string_view in umgekehrter Reihenfolge nach dem ersten Vorkommen einer Teil Zeichenfolge, die mit einer angegebenen Zeichenfolge übereinstimmt.|
|[size](#size)|Gibt die aktuelle Anzahl von Elementen zurück.|
|[starts_with](#starts_with)<sup>c++ 20</sup>|Überprüfen Sie, ob eine Zeichen folgen Ansicht mit einem angegebenen Präfix beginnt.|
|[substr](#substr)|Gibt eine Teil Zeichenfolge mit einer angegebenen Länge zurück, beginnend bei einem angegebenen Index.|
|[swap](#swap)|Tauschen Sie den Inhalt von zwei string_views.|

## <a name="remarks"></a>Bemerkungen

Wenn eine Funktion aufgefordert wird, eine Sequenz zu generieren, die länger als [max_size](#max_size)-Elemente ist, wird von der Funktion ein Längenfehler gemeldet, indem ein Objekt des Typs [length_error](../standard-library/length-error-class.md) ausgelöst wird.

## <a name="requirements"></a>Requirements (Anforderungen)

[Std: c++ 17](../build/reference/std-specify-language-standard-version.md) oder höher.

**Header:**\<string_view>

**Namespace:** std

## <a name="basic_string_viewat"></a><a name="at"></a> basic_string_view:: at

Gibt eine const_reference auf das Zeichen am angegebenen Null basierten Index zurück.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parameter

*kompensieren*\
Der Index des Elements, auf das verwiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Eine const_reference auf das Zeichen an der Position, die durch den Parameter Index angegeben wird.

### <a name="remarks"></a>Bemerkungen

Das erste Element weist einen Index von NULL auf, und die folgenden Elemente werden nacheinander durch die positiven ganzen Zahlen indiziert, sodass ein string_view der Länge *n* über ein *n*-te Element verfügt, das von der Zahl *n-* 1 indiziert wird. **bei** wird eine Ausnahme für ungültige Indizes ausgelöst, anders als bei [Operator \[ \] ](#op_at).

Im Allgemeinen wird empfohlen, **bei** für Sequenzen wie z `std::vector` . b. und string_view nie zu verwenden. Ein ungültiger Index, der an eine Sequenz übermittelt wird, ist ein logischer Fehler, der während der Entwicklung erkannt und korrigiert werden sollte. Wenn ein Programm nicht sicher ist, dass die Indizes gültig sind, sollten Sie es testen, nicht unter () anrufen und auf Ausnahmen zurückgreifen, um die unvorsichtige Programmierung zu verteidigen.

Weitere Informationen finden Sie unter [basic_string_view:: Operator \[ \] ](#op_at) .

### <a name="example"></a>Beispiel

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="basic_string_viewback"></a><a name="back"></a> basic_string_view:: Back

Gibt eine const_reference an das letzte Element zurück.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Rückgabewert

Eine const_reference zum letzten Element in der string_view.

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme aus, wenn die string_view leer ist.

Beachten Sie, dass `remove_suffix` das Element, das von dieser Funktion zurückgegeben wird, nicht mehr das letzte Element in den zugrunde liegenden Daten ist, nachdem ein string_view geändert wurde (z. b. durch Aufrufen von).

### <a name="example"></a>Beispiel

Ein `string_view` , das mit einem C-Zeichenfolgenliterals erstellt wird, enthält nicht das abschließende Null-Zeichen Im folgenden Beispiel `back` gibt `'p'` und nicht zurück `'\0'` .

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

Eingebettete Nullen werden als beliebiges anderes Zeichen behandelt:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a> basic_string_view:: basic_string_view

Erstellt eine string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parameter

*SRT*\
Der Zeiger auf die Zeichen Werte.

*Nest*\
Die Anzahl der Zeichen, die in der Ansicht enthalten sein sollen.

### <a name="remarks"></a>Bemerkungen

Bei den Konstruktoren mit einem charT *-Parameter wird davon ausgegangen, dass die Eingabe NULL-terminiert ist, aber der abschließende NULL-Wert ist nicht in der string_view enthalten.

Sie können auch einen string_view mit einem literalen erstellen. Siehe [Operator "" SV](string-view-operators.md#op_sv).

## <a name="basic_string_viewbegin"></a><a name="begin"></a> basic_string_view:: begin

Identisch mit [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen const_iterator zurück, der das erste Element adressiert.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a> basic_string_view:: cbegin

Gibt einen const_iterator zurück, der das erste Element im Bereich adressiert.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** Random-Access-Iterator, der auf das erste Element des Bereichs zeigt oder die Position direkt hinter dem Ende eines leeren Bereichs (für einen leeren Bereich `cbegin() == cend()` ).

## <a name="basic_string_viewcend"></a><a name="cend"></a> basic_string_view:: cend

Gibt einen const_iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein **`const`** Random-Access-Iterator, der auf eine beliebige Breite hinter das Ende des Bereichs verweist.

### <a name="remarks"></a>Bemerkungen

Der von zurückgegebene Wert `cend` darf nicht dereferenziert werden.

## <a name="basic_string_viewcompare"></a><a name="compare"></a> basic_string_view:: Compare

Führt einen Vergleich mit einem angegebenen string_view (oder einem konvertierbaren Zeichen folgertyp) mit Berücksichtigung der Groß-/Kleinschreibung durch, um zu bestimmen, ob die beiden Objekte gleich sind, oder ob eine lexikografisch kleiner als die andere ist Die [ \<string_view> Operatoren](string-view-operators.md) verwenden diese Member-Funktion, um Vergleiche durchzuführen.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parameter

*VV*\
Der string_view, der mit diesem string_view verglichen werden soll.

*POS*\
Der Index dieses string_view, an dem der Vergleich beginnt.

*NUM*\
Die maximale Anzahl von Zeichen aus diesem string_view, die verglichen werden sollen.

*num2*\
Die maximale *Anzahl von Zeichen aus dem* zu vergleichenden Zeichen.

*kompensieren*\
Der Index von " *strauv* ", bei dem der Vergleich beginnt.

*PTR*\
Die C-Zeichenfolge, die mit diesem string_view verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

- Ein negativer Wert, wenn dieser `string_view` kleiner als " *strauv* " oder " *ptr* " ist.
- NULL, wenn die beiden Zeichen folgen gleich sind.
- Ein positiver Wert, wenn dieser `string_view` größer als " *strauv* " oder " *ptr* " ist.

### <a name="remarks"></a>Bemerkungen

Bei den Element Funktionen wird die `compare` Groß-/Kleinschreibung entweder ganz oder teilweise für jede Zeichenfolge verglichen.

### <a name="example"></a>Beispiel

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are"
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are"
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a)
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="basic_string_viewcopy"></a><a name="copy"></a> basic_string_view:: Copy

Kopiert höchstens eine angegebene Anzahl von Zeichen aus einer indizierten Position in einer Quell string_view in ein Ziel Zeichen Array. Es wird empfohlen, stattdessen die Secure-Funktion [basic_string_view:: _Copy_s](#_copy_s) zu verwenden.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*PTR*\
Das Zielzeichenarray, in das die Elemente kopiert werden sollen.

*Countdown*\
Die Anzahl der Zeichen, die höchstens aus der Quell string_view kopiert werden sollen.

*kompensieren*\
Die Anfangsposition im Quell string_view, von der Kopien erstellt werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von kopierten Zeichen.

### <a name="remarks"></a>Bemerkungen

Es wird kein NULL-Zeichen ans Ende der Kopie angefügt.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a> basic_string_view:: _Copy_s

Sichere CRT-Kopierfunktion, die anstelle von [Copy](#copy)verwendet werden soll.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parameter

*dest*\
Das Zielzeichenarray, in das die Elemente kopiert werden sollen.

*dest_size*\
Die Größe von *dest*.

_ *Zählt* die Anzahl der zu kopierenden Zeichen, höchstens aus der Quell Zeichenfolge.

*_Off*\
Die Anfangsposition in der Quellzeichenfolge, ab der Kopien erstellt werden dürfen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von kopierten Zeichen.

### <a name="remarks"></a>Bemerkungen

Es wird kein NULL-Zeichen ans Ende der Kopie angefügt.

Weitere Informationen finden Sie unter [c-Runtime-Library/Security-Features-in-the-CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a> basic_string_view:: crbegin

Gibt einen const_reverse_iterator zurück, der das erste Element in einem umgekehrten string_view adressiert.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein-const_reverse_iterator, der das erste Element in einem umgekehrten string_view adressiert.

## <a name="basic_string_viewcrend"></a><a name="crend"></a> basic_string_view:: crend

Identisch mit [rend](#rend).

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen const_reverse_iterator zurück, der einen hinter dem Ende eines umgekehrten string_view adressiert.

## <a name="basic_string_viewdata"></a><a name="data"></a> basic_string_view::d ATA

Gibt einen unformatierten, nicht besitzenden Zeiger auf die Konstante Zeichen Sequenz des-Objekts zurück, das zum Erstellen des string_view verwendet wurde.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Konstanten zum ersten Element der Zeichen Sequenz.

### <a name="remarks"></a>Bemerkungen

Der Zeiger kann die Zeichen nicht ändern.

Eine Sequenz von string_view Zeichen wird nicht notwendigerweise mit Null beendet. Der Rückgabetyp für `data` ist keine gültige C-Zeichenfolge, da kein NULL-Zeichen angehängt wird. Das NULL-Zeichen "\ 0" hat keine besondere Bedeutung in einem Objekt vom Typ string_view und kann wie jedes andere Zeichen ein Teil des string_view Objekts sein.

## <a name="basic_string_viewempty"></a><a name="empty"></a> basic_string_view:: Empty

Testet, ob das string_view Zeichen enthält oder nicht.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn das string_view-Objekt keine Zeichen enthält. , **`false`** Wenn Sie über mindestens ein Zeichen verfügt.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entspricht [size](#size)() = = 0.

## <a name="basic_string_viewend"></a><a name="end"></a> basic_string_view:: End

Gibt einen const_iterator mit zufälligem Zugriff zurück, der auf eine Stelle hinter dem letzten Element zeigt.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen const_iterator mit zufälligem Zugriff zurück, der auf eine Stelle hinter dem letzten Element zeigt.

### <a name="remarks"></a>Bemerkungen

`end` wird verwendet, um zu testen, ob ein Const_iterator das Ende seines string_view erreicht hat. Der von zurückgegebene Wert `end` darf nicht dereferenziert werden.

## <a name="basic_string_viewends_with"></a><a name="ends_with"></a> basic_string_view:: ends_with

Überprüfen Sie, ob die Zeichen folgen Ansicht mit dem angegebenen Suffix endet.

```cpp
bool ends_with(const CharType c) const noexcept;
bool ends_with(const CharType* const x) const noexcept;
bool ends_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>Parameter

*scher*\
Das einzelne Zeichen Suffix, nach dem gesucht werden soll.

*SV*\
Eine Zeichen folgen Ansicht mit dem Suffix, nach dem gesucht werden soll. \
Sie können einen übergeben `std::basic_string` , der in eine Zeichen folgen Ansicht konvertiert.

*Stuben*\
Mit NULL beendete Zeichenfolge, die das zu suchende Suffix enthält.

### <a name="return-value"></a>Rückgabewert

`true` , wenn die Zeichen folgen Ansicht mit dem angegebenen Suffix endet. `false` andernfalls.

### <a name="remarks"></a>Bemerkungen

`ends_with()` ist neu in c++ 20. Um es zu verwenden, geben Sie die [/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md) -Compileroption an.

Siehe [starts_with](#starts_with) , um zu überprüfen, ob eine Zeichen folgen Ansicht mit dem angegebenen Präfix beginnt.

### <a name="example"></a>Beispiel

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::cout << std::boolalpha; // so booleans show as 'true'/'false'  
    std::cout << std::string_view("abcdefg").ends_with('g') << '\n';
    std::cout << std::string_view("abcdefg").ends_with("eFg") << '\n';

    std::basic_string<char> str2 = "efg";
    std::cout << std::string_view("abcdefg").ends_with(str2);

    return 0;
}
```

```Output
true
false
true
```

## <a name="basic_string_viewfind"></a><a name="find"></a> basic_string_view:: Find

Durchsucht eine `string_view` Vorwärtsrichtung nach dem ersten Vorkommen eines Zeichens oder einer Teil Zeichenfolge, die mit einer angegebenen Sequenz von Zeichen übereinstimmt.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*SRT*\
Der, `string_view` für den die Member-Funktion durchsucht werden soll.

*Chval*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*kompensieren*\
Der Index, an dem die Suche beginnen soll.

*PTR*\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Countdown*\
Die Anzahl der Zeichen in *ptr*, die nach vorne vom ersten Zeichen gezählt werden.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a> basic_string_view:: find_first_not_of

Sucht nach dem ersten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts ist.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*SRT*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

*Chval*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*kompensieren*\
Der Index, an dem die Suche beginnen soll.

*PTR*\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Countdown*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in der C-Zeichenfolge, für die die Element Funktion durchsucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a> basic_string_view:: find_first_of

Sucht nach dem ersten Zeichen, das mit einem beliebigen Element eines angegebenen string_view übereinstimmt.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*Chval*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*kompensieren*\
Der Index, an dem die Suche beginnen soll.

*PTR*\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Countdown*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in der C-Zeichenfolge, für die die Element Funktion durchsucht werden soll.

*SRT*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a> basic_string_view:: find_last_not_of

Sucht nach dem letzten Zeichen, das kein Element eines angegebenen string_view ist.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*SRT*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

*Chval*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*kompensieren*\
Der Index, an dem die Suche abgeschlossen werden soll.

*PTR*\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Countdown*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in *ptr*.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `string_view::npos`.

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a> basic_string_view:: find_last_of

Sucht nach dem letzten Zeichen, das mit einem Element eines angegebenen string_view übereinstimmt.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*SRT*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

*Chval*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*kompensieren*\
Der Index, an dem die Suche abgeschlossen werden soll.

*PTR*\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Countdown*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in der C-Zeichenfolge, für die die Element Funktion durchsucht werden soll.

### <a name="return-value"></a>Rückgabewert

Falls erfolgreich, der Index des letzten Zeichens der gesuchten Teilzeichenfolge, andernfalls `npos`.

## <a name="basic_string_viewfront"></a><a name="front"></a> basic_string_view:: Front

Gibt eine const_reference an das erste Element zurück.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Rückgabewert

Eine const_reference auf das erste Element.

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme aus, wenn die string_view leer ist.

## <a name="basic_string_viewlength"></a><a name="length"></a> basic_string_view:: length

Gibt die aktuelle Anzahl von Elementen zurück.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ist identisch mit [size](#size).

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a> basic_string_view:: max_size

Gibt die maximale Anzahl von Zeichen zurück, die ein string_view enthalten kann.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Zeichen, die ein string_view enthalten kann.

### <a name="remarks"></a>Bemerkungen

Eine Ausnahme vom Typ " [length_error](../standard-library/length-error-class.md) " wird ausgelöst, wenn ein Vorgang eine string_view mit einer Länge größer als erzeugt `max_size()` .

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a> basic_string_view:: Operator =

Weist einem anderen string_view ein string_view oder konvertierbares Zeichen folgen Objekt zu.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Beispiel

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a> basic_string_view:: Operator []

Stellt ein const_reference für das Zeichen mit einem angegebenen Index bereit.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parameter

*kompensieren*\
Der Index des Elements, auf das verwiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Eine const_reference auf das Zeichen an der Position, die durch den Parameter Index angegeben wird.

### <a name="remarks"></a>Bemerkungen

Das erste Element weist einen Index von NULL auf, und die folgenden Elemente werden nacheinander durch die positiven ganzen Zahlen indiziert, sodass ein string_view der Länge *n* über ein *n*-te Element verfügt, das von der Zahl *n* -1 indiziert wird.

`operator[]` ist schneller als die Member-Funktion [an](#at) , um Lesezugriff auf die Elemente einer string_view bereitzustellen.

`operator[]` überprüft nicht, ob der als Argument übergebenen Index gültig ist. Ein ungültiger Index, der an das-Ergebnis übermittelt wird, `operator[]` führt

Der zurückgegebene Verweis kann ungültig werden, wenn die zugrunde liegenden Zeichen folgen Daten vom besitzenden Objekt geändert oder gelöscht werden.

Beim Kompilieren mit der [ \_ \_ iteratordebugebene \_ ](../standard-library/iterator-debug-level.md) , die auf 1 oder 2 festgelegt ist, tritt ein Laufzeitfehler auf, wenn Sie versuchen, auf ein Element außerhalb der Grenzen des string_view zuzugreifen. Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md).

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a> basic_string_view:: rbegin

Gibt einen konstanten Iterator zum ersten Element in einem umgekehrten string_view zurück.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Iterator mit zufälligem Zugriff auf das erste Element in einem umgekehrten string_view zurück, wobei das, was das letzte Element in der entsprechenden nicht umgekehrten string_view ist, adressiert wird.

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einer umgekehrten string_view genauso verwendet, wie [Begin](#begin) bei einer string_view verwendet wird. `rbegin` kann verwendet werden, um eine Iterations rückwärts zu initialisieren.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a> basic_string_view:: remove_prefix

Verschiebt den Zeiger um die angegebene Anzahl von Elementen vorwärts.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Bemerkungen

Lässt die zugrunde liegenden Daten unverändert. Verschiebt den string_view Zeiger um n Elemente vorwärts und legt den privaten `size` Datenmember auf size-n fest.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a> basic_string_view:: remove_suffix

Verringert die Größe der Ansicht um die angegebene Anzahl von Elementen, beginnend bei der Rückseite.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Bemerkungen

Die zugrunde liegenden Daten und der Zeiger bleiben unverändert. Legt den privaten `size` Datenmember auf size-n fest.

## <a name="basic_string_viewrend"></a><a name="rend"></a> basic_string_view:: rend

Gibt einen konstanten Iterator zurück, der auf eine Stelle hinter dem letzten Element in einem umgekehrten string_view zeigt.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein konstanter umgekehrter Random-Access-Iterator, der auf eine Stelle hinter dem letzten Element in einem umgekehrten string_view zeigt.

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einer umgekehrten string_view genauso verwendet, wie [End](#end) bei einer string_view verwendet wird. `rend` kann verwendet werden, um zu testen, ob ein umgekehrter Iterator das Ende seiner string_view erreicht hat. Der von zurückgegebene Wert `rend` darf nicht dereferenziert werden.

## <a name="basic_string_viewrfind"></a><a name="rfind"></a> basic_string_view:: rfind

Durchsucht eine string_view in umgekehrter Reihenfolge nach einer Teil Zeichenfolge, die einer angegebenen Zeichenfolge entspricht.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*Chval*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*kompensieren*\
Der Index, an dem die Suche beginnen soll.

*PTR*\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Countdown*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in der C-Zeichenfolge, für die die Element Funktion durchsucht werden soll.

*SRT*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teil Zeichenfolge, wenn erfolgreich. andernfalls `npos` .

## <a name="basic_string_viewsize"></a><a name="size"></a> basic_string_view:: size

Gibt die Anzahl der Elemente in der string_view zurück.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Die Länge der string_view.

### <a name="remarks"></a>Bemerkungen

Ein-string_view kann seine Länge ändern, z `remove_prefix` . b `remove_suffix` . durch und. Da dadurch die zugrunde liegenden Zeichen folgen Daten nicht geändert werden, ist die Größe eines string_view nicht notwendigerweise die Größe der zugrunde liegenden Daten.

## <a name="basic_string_viewstarts_with"></a><a name="starts_with"></a> basic_string_view:: starts_with

Überprüfen Sie, ob die Zeichen folgen Ansicht mit dem angegebenen Präfix beginnt.

```cpp
bool starts_with(const CharType c) const noexcept;
bool starts_with(const CharType* const x) const noexcept;
bool starts_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>Parameter

*scher*\
Das einzelne Zeichen Präfix, nach dem gesucht werden soll.

*SV*\
Eine Zeichen folgen Ansicht, die das Präfix enthält, das gesucht werden soll.
Sie können einen übergeben `std::basic_string` , der in eine Zeichen folgen Ansicht konvertiert.

*Stuben*\
Mit NULL beendete Zeichenfolge, die das zu suchende Präfix enthält.

### <a name="return-value"></a>Rückgabewert

`true` , wenn die Zeichenfolge mit dem angegebenen Präfix beginnt. `false` andernfalls.

### <a name="remarks"></a>Bemerkungen

`starts_with()` ist neu in c++ 20. Um es zu verwenden, geben Sie die [/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md) -Compileroption an.

Weitere Informationen finden Sie unter [ends_with](#ends_with) , ob eine Zeichenfolge mit einem Suffix endet.

### <a name="example"></a>Beispiel

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::cout << std::boolalpha; // so booleans show as 'true'/'false'  
    std::cout << std::string_view("abcdefg").starts_with('b') << '\n';
    std::cout << std::string_view("abcdefg").starts_with("aBc") << '\n';

    std::basic_string<char> str2 = "abc";
    std::cout << std::string_view("abcdefg").starts_with(str2);

    return 0;
}
```

```Output
false
false
true
```

## <a name="basic_string_viewsubstr"></a><a name="substr"></a> basic_string_view:: substr

Gibt einen string_view zurück, der (höchstens) die angegebene Anzahl von Zeichen aus einer angegebenen Position darstellt.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parameter

*kompensieren*\
Ein Index, der das Element an der Position, von der aus die Kopie erstellt wird, mit einem Standardwert von 0 (null) ermittelt.

*Countdown*\
Die Anzahl der in die Teil Zeichenfolge einzuschließenden Zeichen, wenn diese vorhanden sind.

### <a name="return-value"></a>Rückgabewert

Ein string_view-Objekt, das die angegebene unter Sequenz von Elementen darstellt.

## <a name="basic_string_viewswap"></a><a name="swap"></a> basic_string_view:: Swap

Tauscht zwei string_views aus, d. h. die Zeiger auf die zugrunde liegenden Zeichen folgen Daten und die Größen Werte.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parameter

*SV*\
Der Quell string_view, dessen Zeiger-und Größen Werte mit dem des Ziel string_view ausgetauscht werden sollen.

## <a name="see-also"></a>Weitere Informationen

[\<string_view>](../standard-library/string-view.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
