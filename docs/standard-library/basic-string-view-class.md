---
title: basic_string_view-Klasse
ms.date: 04/20/2019
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
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
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: ac65dca931f821c717e9c081c8d3479fd0b3bb0e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364895"
---
# <a name="basic_string_view-class"></a>basic_string_view-Klasse

Die Klassenvorlage `basic_string_view<charT>` wurde in C++17 hinzugefügt, um eine sichere und effiziente Möglichkeit für eine Funktion zu sein, verschiedene nicht verwandte Zeichenfolgentypen zu akzeptieren, ohne dass die Funktion für diese Typen templatiert werden muss. Die Klasse enthält einen nicht besitzenden Zeiger auf eine zusammenhängende Sequenz von Zeichendaten und eine Länge, die die Anzahl der Zeichen in der Sequenz angibt. Es wird nicht davon ausgegangen, ob die Sequenz null-beendet ist.

Die Standardbibliothek definiert mehrere Spezialisierungen basierend auf dem Typ der Elemente:

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

In diesem Dokument bezieht sich der Begriff "string_view" im Allgemeinen auf eine dieser Artdefs.

Ein string_view beschreibt die allgemeine Mindestschnittstelle, die zum Lesen von Zeichenfolgendaten erforderlich ist. Es bietet const Zugriff auf die zugrunde liegenden Daten; es werden keine Kopien `copy` erstellt (außer der Funktion). Die Daten können an jeder Position NULL-Werte (''''') enthalten. Ein string_view hat keine Kontrolle über die Lebensdauer des Objekts. Es liegt in der Verantwortung des Aufrufers, sicherzustellen, dass die zugrunde liegenden Zeichenfolgendaten gültig sind.

Eine Funktion, die einen Parameter vom Typ string_view akzeptiert, kann so gemacht werden, dass sie mit einem beliebigen Zeichenfolgentyp funktioniert, ohne die Funktion in eine Vorlage zu verwandeln oder die Funktion auf eine bestimmte Teilmenge von Zeichenfolgentypen zu beschränken. Die einzige Voraussetzung ist, dass eine implizite Konvertierung vom Zeichenfolgentyp in string_view vorhanden ist. Alle Standardzeichenfolgentypen sind implizit in eine string_view, die denselben Elementtyp enthält. Mit anderen Worten, a `std::string` `string_view` ist in `wstring_view`eine, aber nicht in eine konvertierbar.

Das folgende Beispiel zeigt eine `f` Nicht-Vorlagenfunktion, `wstring_view`die einen Parameter vom Typ annimmt. Sie kann mit Argumenten `std::wstring` `wchar_t*`vom `winrt::hstring`Typ , und aufgerufen werden.

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

*Chartype*\
Der Typ der Zeichen, die im string_view gespeichert sind. Die C++-Standardbibliothek stellt die folgenden typdefs für Spezialisierungen dieser Vorlage bereit.

- [string_view](../standard-library/string-view-typedefs.md#string_view) für Elemente vom Typ **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)für **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) für **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) für **char32_t**.

*Merkmale*\
Standardmäßig [char_traits](char-traits-struct.md)<*CharType*>.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_string_view](#basic_string_view)|Erstellt eine string_view, die leer ist, oder zeigt auf alle oder einen Teil der Daten eines anderen Zeichenfolgenobjekts oder auf ein Zeichenarray im C-Stil.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|**const_iterator**|Iterator mit zufälligem Zugriff, der **const-Elemente** lesen kann.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**Zeiger**|`using pointer = value_type*;`|
|**Verweis**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**Size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**Value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Mitgliedsoperatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_eq)|Weist einem anderen string_view ein string_view oder konvertierbares Zeichenfolgenobjekt zu.|
|[Operator\[\]](#op_at)|Gibt das Element am angegebenen Index zurück.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Auf](#at)|Gibt eine const_reference an das Element an einer angegebenen Position zurück.|
|[back (Zurück)](#back)|Gibt eine const_reference an das letzte Element zurück.|
|[Beginnen](#begin)|Gibt einen const-Iterator zurück, der das erste Element adressiert. (string_views sind unveränderlich.)|
|[cbegin](#cbegin)|Genauso wie [begin](#begin).|
|[cend](#cend)|Gibt einen const-Iterator zurück, der auf ein über das letzte Element hinaus zeigt.|
|[Kopieren](#copy)|Kopiert höchstens eine angegebene Anzahl von Zeichen von einer indizierten Position in einer Quelle string_view in ein Zielzeichenarray. (Nicht empfohlen. Verwenden Sie stattdessen _Copy_s.)|
|[_Copy_s](#_copy_s)|Sichere CRT-Kopierfunktion.|
|[Vergleichen](#compare)|Vergleicht eine string_view mit einem angegebenen string_view, um zu bestimmen, ob sie gleich oder lexikographisch kleiner als das andere sind.|
|[crbegin](#crbegin)|Genauso wie [rbegin](#rbegin).|
|[crend](#crend)|Genauso wie [rend](#rend).|
|[Daten](#data)|Gibt einen unformatierten Zeiger ohne Besitz auf die Zeichensequenz zurück.|
|[empty](#empty)|Testet, ob die string_view Zeichen enthält.|
|[Ende](#end)|Genauso wie [cend](#cend).|
|[find](#find)|Sucht in Vorwärtsrichtung nach dem ersten Vorkommen einer Teilzeichenfolge, die einer angegebenen Zeichenfolge entspricht.|
|[find_first_not_of](#find_first_not_of)|Sucht nach dem ersten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichenfolgenobjekts ist.|
|[find_first_of](#find_first_of)|Sucht nach dem ersten Zeichen, das mit einem Element eines angegebenen string_view oder konvertierbaren Zeichenfolgenobjekts übereinstimmt.|
|[find_last_not_of](#find_last_not_of)|Sucht nach dem letzten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichenfolgenobjekts ist.|
|[find_last_of](#find_last_of)|Sucht nach dem letzten Zeichen, das ein Element eines angegebenen string_view oder konvertierbaren Zeichenfolgenobjekts ist.|
|[Vorder-](#front)|Gibt eine const_reference an das erste Element zurück.|
|[length](#length)|Gibt die aktuelle Anzahl von Elementen zurück.|
|[Max_size](#max_size)|Gibt die maximale Anzahl von Zeichen zurück, die ein string_view enthalten kann.|
|[rbegin](#rbegin)|Gibt einen const-Iterator zurück, der das erste Element in einem umgekehrten string_view adressiert.|
|[remove_prefix](#remove_prefix)|Verschiebt den Zeiger um die angegebene Anzahl von Elementen nach vorne.|
|[remove_suffix](#remove_suffix)|Reduziert die Größe der Ansicht um die angegebene Anzahl von Elementen, die von hinten beginnen.|
|[rend](#rend)|Gibt einen const-Iterator zurück, der auf ein Element nach dem letzten Element in einem umgekehrten string_view zeigt.|
|[rfind](#rfind)|Durchsucht eine string_view umgekehrt nach dem ersten Vorkommen einer Teilzeichenfolge, die einer angegebenen Zeichenfolge entspricht.|
|[Größe](#size)|Gibt die aktuelle Anzahl von Elementen zurück.|
|[substr](#substr)|Gibt eine Teilzeichenfolge einer angegebenen Länge zurück, die bei einem angegebenen Index beginnt.|
|[swap](#swap)|Tauschen Sie den Inhalt von zwei string_views aus.|

## <a name="remarks"></a>Bemerkungen

Wenn eine Funktion aufgefordert wird, eine Sequenz zu generieren, die länger als [max_size](#max_size)-Elemente ist, wird von der Funktion ein Längenfehler gemeldet, indem ein Objekt des Typs [length_error](../standard-library/length-error-class.md) ausgelöst wird.

## <a name="requirements"></a>Anforderungen

[std:c++17](../build/reference/std-specify-language-standard-version.md) oder höher

**Kopfzeile:** \<string_view>

**Namespace:** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view::at

Gibt eine const_reference für das Zeichen im angegebenen 0-basierten Index zurück.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parameter

*Offset*\
Der Index des Elements, auf das verwiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein const_reference an der vom Parameterindex angegebenen Position auf das Zeichen.

### <a name="remarks"></a>Bemerkungen

Das erste Element hat einen Index von Null, und die folgenden Elemente werden fortlaufend durch die positiven ganzen Zahlen indiziert, so dass ein string_view der Länge *n* ein *n*th Element hat, das durch die Zahl *n -* 1 indiziert wird. **at** löst im Gegensatz zum [Operator\[](#op_at)eine Ausnahme für ungültige Indizes aus.

Im Allgemeinen empfehlen wir, **dass** bei `std::vector` Sequenzen wie und string_view niemals verwendet werden sollte. Ein ungültiger Index, der an eine Sequenz übergeben wird, ist ein Logikfehler, der während der Entwicklung erkannt und behoben werden sollte. Wenn ein Programm nicht absolut sicher ist, dass seine Indizes gültig sind, sollte es sie testen, nicht aufrufen() und sich auf Ausnahmen verlassen, um sich gegen sorglose Programmierung zu verteidigen.

Weitere Informationen [finden\[ Sie unter basic_string_view::operator.](#op_at)

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

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view::zurück

Gibt eine const_reference an das letzte Element zurück.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Rückgabewert

Ein const_reference bis zum letzten Element in der string_view.

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme aus, wenn die string_view leer ist.

Beachten Sie, dass nach einer Änderung eines `remove_suffix`string_view, z. B. durch Aufrufen , das von dieser Funktion zurückgegebene Element nicht mehr das letzte Element in den zugrunde liegenden Daten ist.

### <a name="example"></a>Beispiel

Ein string_view, der mit einem C-Zeichenfolgenliteral erstellt wird, enthält `back` nicht die beendende NULL und gibt daher im folgenden Beispiel 'p' und nicht '''0' zurück.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

Eingebettete NULL-Werte werden wie jedes andere Zeichen behandelt:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view::basic_string_view

Erstellt eine string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parameter

*Str*\
Der Zeiger auf die Zeichenwerte.

*Len*\
Die Anzahl der Zeichen, die in die Ansicht aufgenommen werden sollen.

## <a name="remarks"></a>Bemerkungen

Die Konstruktoren mit einem charT*-Parameter gehen davon aus, dass die Eingabe null-terminiert ist, aber der beendende NULL-Wert ist nicht im string_view.

Sie können auch eine string_view mit einem Literal erstellen. Siehe [operator""sv](string-view-operators.md#op_sv).

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view::begin

Genauso wie [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt eine const_iterator das erste Element adressieren.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view::cbegin

Gibt eine const_iterator zurück, die das erste Element im Bereich adressiert.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein const-Random-Access-Iterator, der auf das erste Element des Bereichs oder die Position direkt `cbegin() == cend()`hinter dem Ende eines leeren Bereichs zeigt (für einen leeren Bereich, ). **const**

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view::cend

Gibt eine const_iterator zurück, die den Speicherort direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein **const** const-Random-Access-Iterator, der direkt über das Ende des Bereichs zeigt.

### <a name="remarks"></a>Bemerkungen

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view::vergleichen

Führt einen Groß-/Kleinschreibungsvergleich mit einem angegebenen string_view (oder einem konvertierbaren Zeichenfolgentyp) durch, um zu bestimmen, ob die beiden Objekte gleich oder eines lexikographisch kleiner als das andere ist. Die [ \<string_view>-Operatoren](string-view-operators.md) diese Memberfunktion verwenden, um Vergleiche durchzuführen.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parameter

*strv*\
Die string_view, die mit diesem string_view verglichen werden soll.

*Pos*\
Der Index dieser string_view, an dem der Vergleich beginnt.

*Num*\
Die maximale Anzahl von Zeichen aus diesem string_view verglichen werden.

*num2*\
Die maximale Anzahl von Zeichen aus *strv,* die verglichen werden sollen.

*Offset*\
Der Index von *strv,* an dem der Vergleich beginnt.

*Ptr*\
Die C-Zeichenfolge, die mit diesem string_view verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein negativer Wert, wenn dieser string_view kleiner als *strv* oder *ptr*ist; Null, wenn die beiden Zeichenfolgen gleich sind; oder ein positiver Wert, wenn dieser string_view größer als *strv* oder *ptr*ist.

### <a name="remarks"></a>Bemerkungen

Die `compare` Memberfunktionen führen einen Groß-/Kleinschreibungsvergleich durch, bei dem die gesamte oder ein Teil jeder Zeichensequenz berücksichtigt wird.

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

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view::kopie

Kopiert höchstens eine angegebene Anzahl von Zeichen von einer indizierten Position in einer Quelle string_view in ein Zielzeichenarray. Es wird empfohlen, stattdessen die sichere Funktion [basic_string_view::_Copy_s](#_copy_s) zu verwenden.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*Ptr*\
Das Zielzeichenarray, in das die Elemente kopiert werden sollen.

*Count*\
Die Anzahl der Zeichen, die höchstens aus der Quelle kopiert werden sollen, string_view.

*Offset*\
Die Anfangsposition in der Quelle string_view, aus der Kopien angefertigt werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der tatsächlich kopierten Zeichen.

### <a name="remarks"></a>Bemerkungen

Es wird kein NULL-Zeichen ans Ende der Kopie angefügt.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view::_Copy_s

Sichere CRT-Kopierfunktion, die anstelle von [copy](#copy)verwendet werden soll.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parameter

*Dest*\
Das Zielzeichenarray, in das die Elemente kopiert werden sollen.

*dest_size*\
Die Größe von *dest*.

_ *Zählen* Sie die Anzahl der Zeichen, die höchstens aus der Quellzeichenfolge kopiert werden sollen.

*_off*\
Die Anfangsposition in der Quellzeichenfolge, ab der Kopien erstellt werden dürfen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der tatsächlich kopierten Zeichen.

### <a name="remarks"></a>Bemerkungen

Es wird kein NULL-Zeichen ans Ende der Kopie angefügt.

Weitere Informationen finden Sie unter [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view::crbegin

Gibt einen const_reverse_iterator zurück, der das erste Element in einem umgekehrten string_view adressiert.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein const_reverse_iterator, der das erste Element in einem umgekehrten string_view adressiert.

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view::crend

Genauso wie [rend](#rend).

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt eine const_reverse_iterator zurück, die eine über das Ende eines umgekehrten string_view adressiert.

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view::data

Gibt einen unformatierten Zeiger ohne Besitz auf die const-Zeichensequenz des Objekts zurück, das zum Erstellen der string_view verwendet wurde.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Element der Zeichensequenz.

### <a name="remarks"></a>Bemerkungen

Der Zeiger kann die Zeichen nicht ändern.

Eine Sequenz von string_view Zeichen ist nicht notwendigerweise null-beendet. Der Rückgabetyp `data` für ist keine gültige C-Zeichenfolge, da kein NULL-Zeichen angehängt wird. Das Nullzeichen ''''''string_view string_view'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view::leer

Testet, ob die string_view Zeichen enthält oder nicht.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn das string_view-Objekt keine Zeichen enthält; **false,** wenn es mindestens ein Zeichen hat.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion entspricht [der Größe](#size)() == 0.

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view::Ende

Gibt einen const_iterator mit zufälligem Zugriff zurück, der auf ein element hinter dem letzten Element verweist.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen const_iterator mit zufälligem Zugriff zurück, der auf ein element hinter dem letzten Element verweist.

### <a name="remarks"></a>Bemerkungen

`end`wird verwendet, um zu testen, ob ein const_iterator das Ende seiner string_view erreicht hat. Der von `end` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view::finden

Durchsucht eine string_view in Vorwärtsrichtung nach dem ersten Vorkommen eines Zeichens oder einer Teilzeichenfolge, das einer angegebenen Folge von Zeichen/n entspricht.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*Str*\
Die string_view, nach der die Memberfunktion suchen soll.

*chVal*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Index, an dem die Suche beginnen soll.

*Ptr*\
Die C-Zeichenfolge, nach der die Memberfunktion suchen soll.

*Count*\
Die Anzahl der Zeichen in *ptr*, die vom ersten Zeichen nach vorne zählt.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view::find_first_not_of

Sucht nach dem ersten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichenfolgenobjekts ist.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*Str*\
Die string_view, nach der die Memberfunktion suchen soll.

*chVal*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Index, an dem die Suche beginnen soll.

*Ptr*\
Die C-Zeichenfolge, nach der die Memberfunktion suchen soll.

*Count*\
Die Anzahl der Zeichen, die vom ersten Zeichen nach vorne zählen, in der C-Zeichenfolge, nach der die Memberfunktion suchen soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view::find_first_of

Sucht nach dem ersten Zeichen, das mit einem Element eines angegebenen string_view übereinstimmt.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*chVal*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Index, an dem die Suche beginnen soll.

*Ptr*\
Die C-Zeichenfolge, nach der die Memberfunktion suchen soll.

*Count*\
Die Anzahl der Zeichen, die vom ersten Zeichen nach vorne zählen, in der C-Zeichenfolge, nach der die Memberfunktion suchen soll.

*Str*\
Die string_view, nach der die Memberfunktion suchen soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view::find_last_not_of

Sucht nach dem letzten Zeichen, das kein Element eines angegebenen string_view ist.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*Str*\
Die string_view, nach der die Memberfunktion suchen soll.

*chVal*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Index, an dem die Suche abgeschlossen werden soll.

*Ptr*\
Die C-Zeichenfolge, nach der die Memberfunktion suchen soll.

*Count*\
Die Anzahl der Zeichen, die vom ersten Zeichen nach vorne zählen, in *ptr*.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `string_view::npos`.

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view::find_last_of

Sucht nach dem letzten Zeichen, das mit einem Element eines angegebenen string_view übereinstimmt.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*Str*\
Die string_view, nach der die Memberfunktion suchen soll.

*chVal*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Index, an dem die Suche abgeschlossen werden soll.

*Ptr*\
Die C-Zeichenfolge, nach der die Memberfunktion suchen soll.

*Count*\
Die Anzahl der Zeichen, die vom ersten Zeichen nach vorne zählen, in der C-Zeichenfolge, nach der die Memberfunktion suchen soll.

### <a name="return-value"></a>Rückgabewert

Falls erfolgreich, der Index des letzten Zeichens der gesuchten Teilzeichenfolge, andernfalls `npos`.

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view::front

Gibt eine const_reference an das erste Element zurück.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Rückgabewert

Ein const_reference zum ersten Element.

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme aus, wenn die string_view leer ist.

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view::Länge

Gibt die aktuelle Anzahl von Elementen zurück.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ist identisch mit [size](#size).

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view::max_size

Gibt die maximale Anzahl von Zeichen zurück, die ein string_view enthalten kann.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Zeichen, die ein string_view enthalten kann.

### <a name="remarks"></a>Bemerkungen

Eine Ausnahme vom Typ [length_error](../standard-library/length-error-class.md) wird ausgelöst, wenn ein `max_size()`Vorgang einen string_view mit einer Länge von mehr als erzeugt.

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view::operator=

Weist einem anderen string_view ein string_view oder konvertierbares Zeichenfolgenobjekt zu.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Beispiel

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view::operator[]

Stellt dem Zeichen mit einem angegebenen Index eine const_reference zur Verfügung.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parameter

*Offset*\
Der Index des Elements, auf das verwiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein const_reference an der vom Parameterindex angegebenen Position auf das Zeichen.

### <a name="remarks"></a>Bemerkungen

Das erste Element hat einen Index von Null, und die folgenden Elemente werden fortlaufend durch die positiven ganzen Zahlen indiziert, so dass ein string_view der Länge *n* ein *n*th Element hat, das durch die Zahl *n* - 1 indiziert wird.

`operator[]`ist schneller als die [Memberfunktion,](#at) um Lesezugriff auf die Elemente eines string_view bereitzustellen.

`operator[]`überprüft nicht, ob der als Argument übergebene Index gültig ist. Ein ungültiger Index, der an `operator[]` das Ergebnis eines nicht definierten Verhaltens übergeben wird.

Der zurückgegebene Verweis kann ungültig werden, wenn die zugrunde liegenden Zeichenfolgendaten vom besitzenden Objekt geändert oder gelöscht werden.

Beim Kompilieren mit [ \_ITERATOR\_\_DEBUG LEVEL,](../standard-library/iterator-debug-level.md) das auf 1 oder 2 festgelegt ist, tritt ein Laufzeitfehler auf, wenn Sie versuchen, auf ein Element außerhalb der Grenzen der string_view zuzugreifen. Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md).

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view::rbegin

Gibt einen const-Iterator an das erste Element in einem umgekehrten string_view zurück.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Iterator mit zufälligem Zugriff auf das erste Element in einem umgekehrten string_view zurück und adressiert das letzte Element in der entsprechenden nicht umgekehrten string_view.

### <a name="remarks"></a>Bemerkungen

`rbegin`wird mit einem umgekehrten string_view genauso wie [begin](#begin) mit einem string_view verwendet wird. `rbegin`kann verwendet werden, um eine Iteration rückwärts zu initialisieren.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view::remove_prefix

Verschiebt den Zeiger um die angegebene Anzahl von Elementen nach vorne.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Bemerkungen

Lässt die zugrunde liegenden Daten unverändert. Verschiebt den string_view Zeiger um n-Elemente nach vorne und legt das private `size` Datenelement auf die Größe fest - n.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view::remove_suffix

Reduziert die Größe der Ansicht um die angegebene Anzahl von Elementen, die von hinten beginnen.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Bemerkungen

Lässt die zugrunde liegenden Daten und den Zeiger darauf unverändert. Legt den `size` privaten Datenmember auf Größe fest - n.

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view::rend

Gibt einen const-Iterator zurück, der auf ein Element nach dem letzten Element in einem umgekehrten string_view zeigt.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein const-Reverse-Random-Access-Iterator, der auf ein Element hinter dem letzten Element in einem umgekehrten string_view zeigt.

### <a name="remarks"></a>Bemerkungen

`rend`wird mit einem umgekehrten string_view genauso wie [End](#end) mit einem string_view verwendet wird. `rend`kann verwendet werden, um zu testen, ob ein umgekehrter Iterator das Ende seiner string_view erreicht hat. Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view::rfind

Durchsucht einen string_view umgekehrt nach einer Teilzeichenfolge, die einer angegebenen Zeichenfolge entspricht.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*chVal*\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Index, an dem die Suche beginnen soll.

*Ptr*\
Die C-Zeichenfolge, nach der die Memberfunktion suchen soll.

*Count*\
Die Anzahl der Zeichen, die vom ersten Zeichen nach vorne zählen, in der C-Zeichenfolge, nach der die Memberfunktion suchen soll.

*Str*\
Die string_view, nach der die Memberfunktion suchen soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, wenn er erfolgreich ist; andernfalls `npos`.

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view::Größe

Gibt die Anzahl der Elemente im string_view zurück.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Die Länge der string_view.

### <a name="remarks"></a>Bemerkungen

Ein string_view kann seine Länge `remove_prefix` ändern, z. B. durch und `remove_suffix`. Da dadurch die zugrunde liegenden Zeichenfolgendaten nicht geändert werden, ist die Größe eines string_view nicht unbedingt die Größe der zugrunde liegenden Daten.

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view::substr

Gibt einen string_view zurück, der (höchstens) die angegebene Anzahl von Zeichen von einer angegebenen Position darstellt.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parameter

*Offset*\
Ein Index, der das Element an der Position lokalisiert, von der aus die Kopie erstellt wird, mit dem Standardwert 0.

*Count*\
Die Anzahl der Zeichen, die in die Teilzeichenfolge aufgenommen werden sollen, sofern sie vorhanden sind.

### <a name="return-value"></a>Rückgabewert

Ein string_view Objekt, das die angegebene Untersequenz von Elementen darstellt.

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view::swap

Tauscht zwei string_views, d. h. die Zeiger auf die zugrunde liegenden Zeichenfolgendaten und die Größenwerte.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parameter

*Sv*\
Die Quelle string_view deren Zeiger- und Größenwerte mit denen des Ziels ausgetauscht werden sollen, string_view.

## <a name="see-also"></a>Siehe auch

[\<string_view>](../standard-library/string-view.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
