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
ms.openlocfilehash: 2f262ee238d8ee9b441f5bc1daebcf6a64f35a52
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445839"
---
# <a name="basic_string_view-class"></a>basic_string_view-Klasse

Die Klassen Vorlagen `basic_string_view<charT>` wurde in c++ 17 hinzugefügt und dient als sichere und effiziente Möglichkeit für eine Funktion, verschiedene nicht verknüpfte Zeichen folgen Typen zu akzeptieren, ohne dass die Funktion für diese Typen Vorlagen fähig sein muss. Die-Klasse enthält einen nicht besitzenden Zeiger auf eine zusammenhängende Sequenz von Zeichendaten und eine Länge, die die Anzahl der Zeichen in der Sequenz angibt. Es wird davon ausgegangen, ob die Sequenz NULL-terminierte Sequenz hat.

Die Standardbibliothek definiert verschiedene Spezialisierungs Elemente basierend auf dem Typ der Elemente:

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

In diesem Dokument bezieht sich der Begriff "string_view" in der Regel auf diese Typedefs.

Ein string_view der die für das Lesen von Zeichen folgen Daten erforderliche minimale allgemeine Schnittstelle beschreibt. Er bietet Konstanten Zugriff auf die zugrunde liegenden Daten. Es werden keine Kopien erstellt (außer der `copy`-Funktion). Die Daten können an beliebiger Position NULL-Werte ("\ 0") enthalten. Ein string_view hat keine Kontrolle über die Lebensdauer des Objekts. Es liegt in der Verantwortung des Aufrufers, sicherzustellen, dass die zugrunde liegenden Zeichen folgen Daten gültig sind.

Eine Funktion, die einen Parameter vom Typ akzeptiert string_view kann so erstellt werden, dass Sie mit einem beliebigen Zeichen folgen ähnlichen Typ funktioniert, ohne die Funktion in einer Vorlage zu erstellen oder die Funktion auf eine bestimmte Teilmenge von Zeichen folgen Typen einzuschränken. Die einzige Anforderung besteht darin, dass eine implizite Konvertierung vom Zeichen Folgentyp in string_view vorhanden ist. Alle Standard Zeichen folgen Typen können implizit in eine string_view konvertiert werden, die denselben Elementtyp enthält. Anders ausgedrückt: eine `std::string` kann in eine `string_view`, aber nicht in eine `wstring_view`konvertiert werden.

Das folgende Beispiel zeigt eine nicht-Vorlagen Funktion `f`, die einen Parameter vom Typ "`wstring_view`" annimmt. Sie kann mit Argumenten vom Typ `std::wstring`, `wchar_t*`und `winrt::hstring`aufgerufen werden.

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

*CharType* -\
Der Typ der Zeichen, die im string_view gespeichert werden. Die C++ Standard Bibliothek stellt die folgenden Typedefs für Spezialisierungs Informationen dieser Vorlage bereit.
- [string_view](../standard-library/string-view-typedefs.md#string_view) für Elemente vom Typ " **char** "
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)für **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) für **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) für **char32_t**.

*Merkmale*\
Standardmäßig [Char_traits](char-traits-struct.md)<*CharType*->.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_string_view](#basic_string_view)|Erstellt eine string_view, die leer ist, oder verweist auf die Daten eines anderen Zeichen folgen Objekts oder auf ein Zeichen Array im C-Stil.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|**const_iterator**|Random-Access-Iterator, der **Konstanten** Elemente lesen kann.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**Referenz**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Member-Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[operator=](#op_eq)|Weist einem anderen string_view ein string_view oder konvertierbares Zeichen folgen Objekt zu.|
|[operator\[\]](#op_at)|Gibt das Element am angegebenen Index zurück.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[at](#at)|Gibt eine const_reference an einem angegebenen Speicherort an das Element zurück.|
|[Rückseite](#back)|Gibt eine const_reference an das letzte Element zurück.|
|[begin](#begin)|Gibt einen konstanten Iterator zurück, der das erste Element adressiert. (string_views sind unveränderlich.)|
|[cbegin](#cbegin)|Identisch mit [Begin](#begin).|
|[cend](#cend)|Gibt einen konstanten Iterator zurück, der auf eine Stelle hinter dem letzten Element zeigt.|
|[copy](#copy)|Kopiert höchstens eine angegebene Anzahl von Zeichen aus einer indizierten Position in einer Quell string_view in ein Ziel Zeichen Array. (Nicht empfohlen. Verwenden Sie stattdessen _Copy_s.)|
|[_Copy_s](#_copy_s)|Secure CRT-Kopierfunktion.|
|[compare](#compare)|Vergleicht eine string_view mit einem angegebenen string_view, um zu bestimmen, ob Sie gleich sind, oder ob eine lexikografisch kleiner als die andere ist.|
|[crbegin](#crbegin)|Identisch mit [rbegin](#rbegin).|
|[crend](#crend)|Identisch mit [rend](#rend).|
|[data](#data)|Gibt einen unformatierten, nicht besitzenden Zeiger auf die Zeichenfolge zurück.|
|[empty](#empty)|Testet, ob die string_view Zeichen enthält.|
|[end](#end)|Identisch mit [cend](#cend).|
|[find](#find)|Sucht in Vorwärtsrichtung nach dem ersten Vorkommen einer Teil Zeichenfolge, die mit einer angegebenen Zeichenfolge übereinstimmt.|
|[find_first_not_of](#find_first_not_of)|Sucht nach dem ersten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts ist.|
|[find_first_of](#find_first_of)|Sucht nach dem ersten Zeichen, das mit einem beliebigen Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts übereinstimmt.|
|[find_last_not_of](#find_last_not_of)|Sucht nach dem letzten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts ist.|
|[find_last_of](#find_last_of)|Sucht nach dem letzten Zeichen, das ein Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts ist.|
|[Vorderseite](#front)|Gibt eine const_reference an das erste Element zurück.|
|[length](#length)|Gibt die aktuelle Anzahl von Elementen zurück.|
|[max_size](#max_size)|Gibt die maximale Anzahl von Zeichen zurück, die ein string_view enthalten könnte.|
|[rbegin](#rbegin)|Gibt einen konstanten Iterator zurück, der das erste Element in einem umgekehrten string_view adressiert.|
|[remove_prefix](#remove_prefix)|Verschiebt den Zeiger um die angegebene Anzahl von Elementen vorwärts.|
|[remove_suffix](#remove_suffix)|Verringert die Größe der Ansicht um die angegebene Anzahl von Elementen, beginnend bei der Rückseite.|
|[rend](#rend)|Gibt einen konstanten Iterator zurück, der auf eine Stelle hinter dem letzten Element in einem umgekehrten string_view zeigt.|
|[rfind](#rfind)|Durchsucht eine string_view in umgekehrter Reihenfolge nach dem ersten Vorkommen einer Teil Zeichenfolge, die mit einer angegebenen Zeichenfolge übereinstimmt.|
|[size](#size)|Gibt die aktuelle Anzahl von Elementen zurück.|
|[substr](#substr)|Gibt eine Teil Zeichenfolge mit einer angegebenen Länge zurück, beginnend bei einem angegebenen Index.|
|[swap](#swap)|Tauschen Sie den Inhalt von zwei string_views.|

## <a name="remarks"></a>Bemerkungen

Wenn eine Funktion aufgefordert wird, eine Sequenz zu generieren, die länger als [max_size](#max_size)-Elemente ist, wird von der Funktion ein Längenfehler gemeldet, indem ein Objekt des Typs [length_error](../standard-library/length-error-class.md) ausgelöst wird.

## <a name="requirements"></a>Requirements (Anforderungen)

[Std: c++ 17](../build/reference/std-specify-language-standard-version.md) oder höher

**Header:** \<string_view >

**Namespace:** std

## <a name="at"></a>basic_string_view:: at

Gibt eine const_reference auf das Zeichen am angegebenen Null basierten Index zurück.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parameter

*Offset*\
Der Index des Elements, auf das verwiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Eine const_reference auf das Zeichen an der Position, die durch den Parameter Index angegeben wird.

### <a name="remarks"></a>Bemerkungen

Das erste Element weist einen Index von NULL auf, und die folgenden Elemente werden nacheinander durch die positiven ganzen Zahlen indiziert, sodass ein string_view der Länge *n* über ein *n*-te Element verfügt, das von der Zahl *n-* 1 indiziert wird. **bei** wird eine Ausnahme für ungültige Indizes ausgelöst, anders als bei [Operator\[\]](#op_at). 

Im Allgemeinen wird empfohlen, bei für Sequenzen wie `std::vector` und string_view nie **zu** verwenden. Ein ungültiger Index, der an eine Sequenz übermittelt wird, ist ein logischer Fehler, der während der Entwicklung erkannt und korrigiert werden sollte. Wenn ein Programm nicht unbedingt sicher ist, dass die Indizes gültig sind, sollten Sie es testen, nicht bei () anrufen und auf Ausnahmen zurückgreifen, um die unvorsichtige Programmierung zu verteidigen.

Weitere Informationen finden Sie unter [basic_string_view:: Operator\[\]](#op_at) .

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

## <a name="back"></a>basic_string_view:: Back

Gibt eine const_reference an das letzte Element zurück.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Rückgabewert

Eine const_reference zum letzten Element in der string_view.

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme aus, wenn die string_view leer ist.

Beachten Sie, dass das Element, das von dieser Funktion zurückgegeben wird, nicht mehr das letzte Element in den zugrunde liegenden Daten ist, nachdem eine string_view geändert wurde, z. b. durch Aufrufen von `remove_suffix`.

### <a name="example"></a>Beispiel

Eine string_view, die mit einem C-Zeichenfolgenliterals erstellt wird, enthält nicht das abschließende Null-Zeichen, daher gibt `back` im folgenden Beispiel "p" und nicht "\ 0" zurück.

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

## <a name="basic_string_view"></a>basic_string_view:: basic_string_view

Erstellt eine string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parameter

*Str*\
Der Zeiger auf die Zeichen Werte.

*len* -\
Die Anzahl der Zeichen, die in der Ansicht enthalten sein sollen.

## <a name="remarks"></a>Bemerkungen

Bei den Konstruktoren mit einem charT *-Parameter wird davon ausgegangen, dass die Eingabe NULL-terminiert ist, aber der abschließende NULL-Wert ist nicht in der string_view enthalten.

Sie können auch einen string_view mit einem literalen erstellen. Siehe [Operator "" SV](string-view-operators.md#op_sv).

## <a name="begin"></a>basic_string_view:: begin

Identisch mit [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert
Gibt einen const_iterator zurück, der das erste Element adressiert.

## <a name="cbegin"></a>basic_string_view:: cbegin

Gibt einen const_iterator zurück, der das erste Element im Bereich adressiert.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein **konstanter** Random-Access-Iterator, der auf das erste Element des Bereichs zeigt oder die Position direkt hinter dem Ende eines leeren Bereichs (für einen leeren Bereich, `cbegin() == cend()`).

## <a name="cend"></a>basic_string_view:: cend

Gibt einen const_iterator zurück, der die Position direkt hinter dem letzten Element in einem Bereich adressiert.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein **konstanter** Random-Access-Iterator, der direkt hinter das Ende des Bereichs zeigt.

### <a name="remarks"></a>Bemerkungen

Der von `cend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="compare"></a>basic_string_view:: Compare

Führt einen Vergleich mit einem angegebenen string_view (oder einem konvertierbaren Zeichen folgertyp) durch, um zu bestimmen, ob die beiden Objekte gleich sind, oder ob eine lexikografisch kleiner als die andere ist. Die [\<string_view >-Operatoren](string-view-operators.md) verwenden diese Member-Funktion, um Vergleiche durchzuführen.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parameter

\ von *VV*
Der string_view, der mit diesem string_view verglichen werden soll.

*POS* -\
Der Index dieses string_view, an dem der Vergleich beginnt.

*NUM* -\
Die maximale Anzahl von Zeichen aus diesem string_view, die verglichen werden sollen.

*num2*\
Die maximale *Anzahl von Zeichen aus dem* zu vergleichenden Zeichen.

*Offset*\
Der Index von " *strauv* ", bei dem der Vergleich beginnt.

*ptr* -\
Die C-Zeichenfolge, die mit diesem string_view verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Ein negativer Wert, wenn dieser string_view kleiner als " *strauv* " oder " *ptr*" ist. 0 (null), wenn die beiden Zeichen folgen gleich sind. oder ein positiver Wert, wenn dieser string_view größer als " *strauv* " oder " *ptr*" ist.

### <a name="remarks"></a>Bemerkungen

Die `compare` Member-Funktionen führen einen Vergleich von ganz oder teilweise jeder Zeichen Sequenz mit Berücksichtigung der Groß-und Kleinschreibung durch. 

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

## <a name="copy"></a>basic_string_view:: Copy

Kopiert höchstens eine angegebene Anzahl von Zeichen aus einer indizierten Position in einer Quell string_view in ein Ziel Zeichen Array. Es wird empfohlen, stattdessen die Secure-Funktion [basic_string_view:: _Copy_s](#_copy_s) zu verwenden.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*ptr* -\
Das Zielzeichenarray, in das die Elemente kopiert werden sollen.

*Anzahl*\
Die Anzahl der Zeichen, die höchstens aus der Quell string_view kopiert werden sollen.

*Offset*\
Die Anfangsposition im Quell string_view, von der Kopien erstellt werden sollen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der tatsächlich kopierten Zeichen.

### <a name="remarks"></a>Bemerkungen

Es wird kein NULL-Zeichen ans Ende der Kopie angefügt.

## <a name="_copy_s"></a>basic_string_view:: _Copy_s

Sichere CRT-Kopierfunktion, die anstelle von [Copy](#copy)verwendet werden soll.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parameter

*dest* -\
Das Zielzeichenarray, in das die Elemente kopiert werden sollen.

*dest_size*\
Die Größe von *dest*.

_ *Zählt* die Anzahl der zu kopierenden Zeichen, höchstens aus der Quell Zeichenfolge.

*_Off*\
Die Anfangsposition in der Quellzeichenfolge, ab der Kopien erstellt werden dürfen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der tatsächlich kopierten Zeichen.

### <a name="remarks"></a>Bemerkungen

Es wird kein NULL-Zeichen ans Ende der Kopie angefügt.

Weitere Informationen finden Sie unter [c-Runtime-Library/Security-Features-in-the-CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="crbegin"></a>basic_string_view:: crbegin

Gibt einen const_reverse_iterator zurück, der das erste Element in einem umgekehrten string_view adressiert.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein-const_reverse_iterator, der das erste Element in einem umgekehrten string_view adressiert. 

## <a name="crend"></a>basic_string_view:: crend

Identisch mit [rend](#rend). 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen const_reverse_iterator zurück, der einen hinter dem Ende eines umgekehrten string_view adressiert.

## <a name="data"></a>basic_string_view::d ATA

Gibt einen unformatierten, nicht besitzenden Zeiger auf die Konstante Zeichen Sequenz des-Objekts zurück, das zum Erstellen des string_view verwendet wurde.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Konstanten zum ersten Element der Zeichen Sequenz.

### <a name="remarks"></a>Bemerkungen

Der Zeiger kann die Zeichen nicht ändern.

Eine Sequenz von string_view Zeichen wird nicht notwendigerweise mit Null beendet. Der Rückgabetyp für `data` ist keine gültige C-Zeichenfolge, da kein NULL-Zeichen angefügt wird. Das NULL-Zeichen "\ 0" hat keine besondere Bedeutung in einem Objekt vom Typ string_view und kann wie jedes andere Zeichen ein Teil des string_view Objekts sein.

## <a name="empty"></a>basic_string_view:: Empty

Testet, ob das string_view Zeichen enthält oder nicht.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

**true** , wenn das string_view-Objekt keine Zeichen enthält. **false** , wenn mindestens ein Zeichen enthält.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion entspricht [size](#size)() = = 0.

## <a name="end"></a>basic_string_view:: End

Gibt einen const_iterator mit zufälligem Zugriff zurück, der auf eine Stelle hinter dem letzten Element zeigt.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen const_iterator mit zufälligem Zugriff zurück, der auf eine Stelle hinter dem letzten Element zeigt.

### <a name="remarks"></a>Bemerkungen

`end` wird verwendet, um zu testen, ob ein Const_iterator das Ende seiner string_view erreicht hat. Der von `end` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="find"></a>basic_string_view:: Find

Durchsucht eine string_view Vorwärtsrichtung nach dem ersten Vorkommen eines Zeichens oder einer Teil Zeichenfolge, die mit einer angegebenen Zeichenfolge übereinstimmt.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*Str*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

*Chval* -\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Der Index, an dem die Suche beginnen soll.

*ptr* -\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Anzahl*\
Die Anzahl der Zeichen in *ptr*, die nach vorne vom ersten Zeichen gezählt werden.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="find_first_not_of"></a>basic_string_view:: find_first_not_of

Sucht nach dem ersten Zeichen, das kein Element eines angegebenen string_view oder konvertierbaren Zeichen folgen Objekts ist.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*Str*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

*Chval* -\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Der Index, an dem die Suche beginnen soll.

*ptr* -\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Anzahl*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in der C-Zeichenfolge, für die die Element Funktion durchsucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="find_first_of"></a>basic_string_view:: find_first_of

Sucht nach dem ersten Zeichen, das mit einem beliebigen Element eines angegebenen string_view übereinstimmt.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parameter

*Chval* -\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Der Index, an dem die Suche beginnen soll.

*ptr* -\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Anzahl*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in der C-Zeichenfolge, für die die Element Funktion durchsucht werden soll.

*Str*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `npos`.

## <a name="find_last_not_of"></a>basic_string_view:: find_last_not_of

Sucht nach dem letzten Zeichen, das kein Element eines angegebenen string_view ist.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*Str*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

*Chval* -\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Der Index, an dem die Suche abgeschlossen werden soll.

*ptr* -\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Anzahl*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in *ptr*.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teilzeichenfolge, nach der bei Erfolg gesucht wird; andernfalls `string_view::npos`.

## <a name="find_last_of"></a>basic_string_view:: find_last_of

Sucht nach dem letzten Zeichen, das mit einem Element eines angegebenen string_view übereinstimmt.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*Str*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

*Chval* -\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Der Index, an dem die Suche abgeschlossen werden soll.

*ptr* -\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Anzahl*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in der C-Zeichenfolge, für die die Element Funktion durchsucht werden soll.

### <a name="return-value"></a>Rückgabewert

Falls erfolgreich, der Index des letzten Zeichens der gesuchten Teilzeichenfolge, andernfalls `npos`.

## <a name="front"></a>basic_string_view:: Front

Gibt eine const_reference an das erste Element zurück.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Rückgabewert

Eine const_reference auf das erste Element.

### <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme aus, wenn die string_view leer ist.

## <a name="length"></a>basic_string_view:: length

Gibt die aktuelle Anzahl von Elementen zurück.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ist identisch mit [size](#size).

## <a name="max_size"></a>basic_string_view:: max_size

Gibt die maximale Anzahl von Zeichen zurück, die ein string_view enthalten kann.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Zeichen, die ein string_view enthalten kann.

### <a name="remarks"></a>Bemerkungen

Eine Ausnahme vom Typ [length_error](../standard-library/length-error-class.md) wird ausgelöst, wenn ein Vorgang eine string_view mit einer Länge größer als `max_size()`erzeugt.

## <a name="op_eq"></a>basic_string_view:: Operator =

Weist einem anderen string_view ein string_view oder konvertierbares Zeichen folgen Objekt zu.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Beispiel

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="op_at"></a>basic_string_view:: Operator []

Stellt ein const_reference für das Zeichen mit einem angegebenen Index bereit.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parameter

*Offset*\
Der Index des Elements, auf das verwiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Eine const_reference auf das Zeichen an der Position, die durch den Parameter Index angegeben wird.

### <a name="remarks"></a>Bemerkungen

Das erste Element weist einen Index von NULL auf, und die folgenden Elemente werden nacheinander durch die positiven ganzen Zahlen indiziert, sodass ein string_view der Länge *n* über ein *n*-te Element verfügt, das von der Zahl *n* -1 indiziert wird.

`operator[]` ist schneller als die Member-Funktion [an](#at) , um Lesezugriff auf die Elemente einer string_view bereitzustellen.

`operator[]` überprüft nicht, ob der als Argument übergebenen Index gültig ist. Ein ungültiger Index, der an `operator[]` übermittelt wird, führt zu einem nicht

Der zurückgegebene Verweis kann ungültig werden, wenn die zugrunde liegenden Zeichen folgen Daten vom besitzenden Objekt geändert oder gelöscht werden.

Beim Kompilieren mit [\_Iterator\_Debug\_Ebene](../standard-library/iterator-debug-level.md) auf 1 oder 2 festgelegt ist, tritt ein Laufzeitfehler auf, wenn Sie versuchen, auf ein Element außerhalb der Grenzen des string_view zuzugreifen. Weitere Informationen finden Sie unter [Checked Iterators (Überprüfte Iteratoren)](../standard-library/checked-iterators.md).

## <a name="rbegin"></a>basic_string_view:: rbegin

Gibt einen konstanten Iterator zum ersten Element in einem umgekehrten string_view zurück.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Iterator mit zufälligem Zugriff auf das erste Element in einem umgekehrten string_view zurück, wobei das, was das letzte Element in der entsprechenden nicht umgekehrten string_view ist, adressiert wird.

### <a name="remarks"></a>Bemerkungen

`rbegin` wird bei einem umgekehrten string_view verwendet, wie [Begin](#begin) bei einer string_view verwendet wird. `rbegin` kann verwendet werden, um eine Iterations rückwärts zu initialisieren.

## <a name="remove_prefix"></a>basic_string_view:: remove_prefix

Verschiebt den Zeiger um die angegebene Anzahl von Elementen vorwärts.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Bemerkungen

Lässt die zugrunde liegenden Daten unverändert. Verschiebt den string_view Zeiger um n Elemente vorwärts und legt den privaten `size` Datenmember auf size-n fest.

## <a name="remove_suffix"></a>basic_string_view:: remove_suffix

Verringert die Größe der Ansicht um die angegebene Anzahl von Elementen, beginnend bei der Rückseite.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Bemerkungen

Die zugrunde liegenden Daten und der Zeiger bleiben unverändert. Legt den privaten `size` Datenmember auf size-n fest.

## <a name="rend"></a>basic_string_view:: rend

Gibt einen konstanten Iterator zurück, der auf eine Stelle hinter dem letzten Element in einem umgekehrten string_view zeigt.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein konstanter umgekehrter Random-Access-Iterator, der auf eine Stelle hinter dem letzten Element in einem umgekehrten string_view zeigt.

### <a name="remarks"></a>Bemerkungen

`rend` wird bei einem umgekehrten string_view verwendet, wie [End](#end) bei einer string_view verwendet wird. `rend` kann verwendet werden, um zu testen, ob ein umgekehrter Iterator das Ende seiner string_view erreicht hat. Der von `rend` zurückgegebene Wert darf nicht dereferenziert werden.

## <a name="rfind"></a>basic_string_view:: rfind

Durchsucht eine string_view in umgekehrter Reihenfolge nach einer Teil Zeichenfolge, die einer angegebenen Zeichenfolge entspricht.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parameter

*Chval* -\
Der Zeichenwert, nach dem die Memberfunktion suchen soll.

*Offset*\
Der Index, an dem die Suche beginnen soll.

*ptr* -\
Die C-Zeichenfolge, für die die Member-Funktion durchsucht werden soll.

*Anzahl*\
Die Anzahl der Zeichen, beginnend beim ersten Zeichen in der C-Zeichenfolge, für die die Element Funktion durchsucht werden soll.

*Str*\
Der string_view, für den die Member-Funktion durchsucht werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten Zeichens der Teil Zeichenfolge, wenn erfolgreich. Andernfalls `npos`.

## <a name="size"></a>basic_string_view:: size

Gibt die Anzahl der Elemente in der string_view zurück.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Die Länge der string_view.

### <a name="remarks"></a>Bemerkungen

Ein string_view kann seine Länge ändern, z. b. durch `remove_prefix` und `remove_suffix`. Da dadurch die zugrunde liegenden Zeichen folgen Daten nicht geändert werden, ist die Größe eines string_view nicht notwendigerweise die Größe der zugrunde liegenden Daten.

## <a name="substr"></a>basic_string_view:: substr

Gibt einen string_view zurück, der (höchstens) die angegebene Anzahl von Zeichen aus einer angegebenen Position darstellt.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parameter

*Offset*\
Ein Index, der das Element an der Position, von der aus die Kopie erstellt wird, mit einem Standardwert von 0 (null) ermittelt.

*Anzahl*\
Die Anzahl der in die Teil Zeichenfolge einzuschließenden Zeichen, wenn diese vorhanden sind.

### <a name="return-value"></a>Rückgabewert

Ein string_view-Objekt, das die angegebene unter Sequenz von Elementen darstellt.

## <a name="swap"></a>basic_string_view:: Swap

Tauscht zwei string_views aus, d. h. die Zeiger auf die zugrunde liegenden Zeichen folgen Daten und die Größen Werte.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parameter

*SV* -\
Der Quell string_view, dessen Zeiger-und Größen Werte mit dem des Ziel string_view ausgetauscht werden sollen.

## <a name="see-also"></a>Weitere Informationen

[\<string_view >](../standard-library/string-view.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
