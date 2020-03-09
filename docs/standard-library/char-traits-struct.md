---
title: char_traits-Struktur
ms.date: 05/07/2019
f1_keywords:
- iosfwd/std::char_traits
- iosfwd/std::char_traits::char_type
- iosfwd/std::char_traits::int_type
- iosfwd/std::char_traits::off_type
- iosfwd/std::char_traits::pos_type
- iosfwd/std::char_traits::state_type
- iosfwd/std::char_traits::assign
- iosfwd/std::char_traits::compare
- iosfwd/std::char_traits::copy
- iosfwd/std::char_traits::_Copy_s
- iosfwd/std::char_traits::eof
- iosfwd/std::char_traits::eq
- iosfwd/std::char_traits::eq_int_type
- iosfwd/std::char_traits::find
- iosfwd/std::char_traits::length
- iosfwd/std::char_traits::lt
- iosfwd/std::char_traits::move
- iosfwd/std::char_traits::_Move_s
- iosfwd/std::char_traits::not_eof
- iosfwd/std::char_traits::to_char_type
- iosfwd/std::char_traits::to_int_type
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
ms.openlocfilehash: efb926bc8c2ae55835391f884a0e3430e3da8aca
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856396"
---
# <a name="char_traits-struct"></a>char_traits-Struktur

Die char_traits-Struktur beschreibt die Attribute, die einem Zeichen zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>Parameter

*CharType* -\
Der Datentyp des Elements.

## <a name="remarks"></a>Bemerkungen

Die Vorlagen Struktur beschreibt verschiedene Zeichen Merkmale für den Typ `CharType`. Die Klassen Vorlage [basic_string](../standard-library/basic-string-class.md) und mehrere iostream-Klassen Vorlagen, einschließlich [basic_ios](../standard-library/basic-ios-class.md), verwenden diese Informationen zum Bearbeiten von Elementen des Typs `CharType`. Ein solcher Elementtyp darf weder explizite Erstellung noch explizite Zerstörung erfordern. Er muss einen Standardkonstruktor, einen Kopierkonstruktor und einen Zuweisungsoperator mit der erwarteten Semantik bereitstellen. Eine bitweise Kopie muss dieselbe Auswirkung wie eine Zuweisung haben. Keine der Memberfunktionen der char_traits-Struktur kann Ausnahmen auslösen.

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Ein Typ von Zeichen.|
|[int_type](#int_type)|Ein ganzzahliger Typ, der ein Zeichen des Typs `char_type` oder ein Dateiendezeichen (End-of-File, EOF) darstellen kann.|
|[off_type](#off_type)|Ein ganzzahliger Typ, der Offsets zwischen Positionen in einem Stream darstellen kann.|
|[pos_type](#pos_type)|Ein ganzzahliger Typ, der Positionen in einem Stream darstellen kann.|
|[state_type](#state_type)|Ein Typ, der den Konvertierungsstatus für Multibytezeichen in einem Stream darstellt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[assign](#assign)|Weist den Wert eines Zeichens einem anderen zu.|
|[compare](#compare)|Vergleicht zwei Zeichenfolgen bis zu einer angegebenen Anzahl von Zeichen.|
|[copy](#copy)|Kopiert eine angegebene Anzahl von Zeichen aus einer Zeichenfolge in eine andere. Veraltet. Verwenden Sie stattdessen [char_traits::_Copy_s](#copy_s).|
|[_Copy_s](#copy_s)|Kopiert eine angegebene Anzahl von Zeichen aus einer Zeichenfolge in eine andere.|
|[eof](#eof)|Gibt das Zeichen für Dateiende (End-of-File, EOF) zurück.|
|[eq](#eq)|Überprüft, ob zwei `char_type`-Zeichen gleich sind.|
|[eq_int_type](#eq_int_type)|Überprüft, ob zwei Zeichen, die als `int_type`s angegeben sind, gleich sind.|
|[find](#find)|Sucht nach dem ersten Vorkommen eines angegebenen Zeichens in einem Bereich von Zeichen.|
|[length](#length)|Gibt die Länge einer Zeichenfolge zurück.|
|[lt](#lt)|Überprüft, ob ein Zeichen kleiner als ein anderes ist.|
|[move](#move)|Kopiert eine angegebene Anzahl von Zeichen in einer Sequenz in eine andere, möglicherweise überlappende, Sequenz. Veraltet. Verwenden Sie stattdessen [char_traits::_Move_s](#move_s).|
|[_Move_s](#move_s)|Kopiert eine angegebene Anzahl von Zeichen in einer Sequenz in eine andere, möglicherweise überlappende, Sequenz.|
|[not_eof](#not_eof)|Überprüft, ob ein Zeichen das Zeichen für Dateiende (End-of-File, EOF) ist.|
|[to_char_type](#to_char_type)|Konvertiert ein `int_type`-Zeichen in das entsprechende `char_type`-Zeichen und gibt das Ergebnis zurück.|
|[to_int_type](#to_int_type)|Konvertiert ein `char_type`-Zeichen in das entsprechende `int_type`-Zeichen und gibt das Ergebnis zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<Zeichenfolge >

**Namespace:** std

## <a name="assign"></a> char_traits::assign

Weist einen Zeichenwert einem anderen Zeichenwert oder einem Bereich von Elementen in einer Zeichenfolge zu.

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>Parameter

**_** *Charfrom* das Zeichen, dessen Wert zugewiesen werden soll.

*_CharTo*\
Das Element, dem der Zeichenwert zugewiesen werden soll.

*\*
Das Zeichenfolgen- oder Zeichenarray, dessen ersten Elementen Zeichenwerte zugewiesen werden sollen.

*_Num*\
Die Anzahl der Elemente, denen Werte zugewiesen werden sollen.

### <a name="return-value"></a>Rückgabewert

Die zweite Member-Funktion gibt einen Zeiger auf die Zeichenfolge zurück, deren ersten *_Num* Elementen Werte *_CharFrom*zugewiesen wurden.

### <a name="example"></a>Beispiel

```cpp
// char_traits_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning
   // one character value to another character
   char ChTo = 't';
   const char ChFrom = 'f';
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl;
   char_traits<char>::assign ( ChTo , ChFrom );
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl << endl;

   // The second member function assigning
   // character values to initial part of a string
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type* result1;
   cout << "The target string s1 is: " << s1 << endl;
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "
        << result1 << endl;
}
```

```Output
The initial characters ( ChTo , ChFrom ) are: ( t , f ).
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).

The target string s1 is: abcd-1234-abcd
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd
```

## <a name="char_type"></a> char_traits::char_type

Ein Typ von Zeichen.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Bemerkungen

Der Type stellt ein Synonym für den Vorlagenparameter `CharType`dar.

### <a name="example"></a>Beispiel

Im Beispiel für [copy](#copy) wird verdeutlicht, wie `char_type` deklariert und verwendet wird.

## <a name="compare"></a> char_traits::compare

Vergleicht zwei Zeichenfolgen bis zu einer angegebenen Anzahl von Zeichen.

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>Parameter

*str1*\
Die erste von zwei Zeichenfolgen, die miteinander verglichen werden.

*str2*\
Die zweite von zwei Zeichenfolgen, die miteinander verglichen werden.

*_Num*\
Die Anzahl der Elemente in den Zeichenfolgen, die miteinander verglichen werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein negativer Wert, wenn die erste Zeichenfolge kleiner ist als die zweite Zeichenfolge; 0, wenn die beiden Zeichenfolgen gleich sind; oder ein positiver Wert, wenn die erste Zeichenfolge größer ist als die zweite Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Zeichenfolgen erfolgt elementweise, dabei wird zunächst auf Gleichheit geprüft. Wenn ein Elementpaar in der Sequenz nicht gleich ist, wird es auf „kleiner als“ geprüft.

Wenn zwei Zeichenfolgen über einen Bereich identisch sind, eine aber länger ist als die andere, dann ist die kürzere Zeichenfolge kleiner als die längere Zeichenfolge.

### <a name="example"></a>Beispiel

```cpp
// char_traits_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   char_traits<char>::char_type* s1 = "CAB";
   char_traits<char>::char_type* s2 = "ABC";
   char_traits<char>::char_type* s3 = "ABC";
   char_traits<char>::char_type* s4 = "ABCD";

   cout << "The string s1 is: " << s1 << endl;
   cout << "The string s2 is: " << s2 << endl;
   cout << "The string s3 is: " << s3 << endl;
   cout << "The string s4 is: " << s4 << endl;

   int comp1, comp2, comp3, comp4;
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;
}
```

## <a name="copy"></a> char_traits::copy

Kopiert eine angegebene Anzahl von Zeichen aus einer Zeichenfolge in eine andere.

Diese Methode ist potenziell unsicher, da sie darauf basiert, dass der Aufrufer überprüft, ob die übergebenen Werte korrekt sind. Verwenden Sie stattdessen [char_traits::_Copy_s](#copy_s).

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parameter

*_To*\
Das Element am Anfang des Zeichenfolgen- oder Zeichenarrays, das die kopierte Zeichenfolgensequenz empfangen soll.

*_FROM*\
Das Element am Anfang des Quellzeichenfolgen- oder -zeichenarrays, das kopiert werden soll.

*_Num*\
Die Anzahl der zu kopierenden Elemente.

### <a name="return-value"></a>Rückgabewert

Das erste Element, das in das Zeichenfolgen- oder Zeichenarray kopiert wird, das die kopierte Zeichenfolgensequenz empfangen soll.

### <a name="remarks"></a>Bemerkungen

Die Zeichenfolgensequenz für Quelle und Ziel dürfen sich nicht überschneiden.

### <a name="example"></a>Beispiel

```cpp
// char_traits_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type s2[] = "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string is: " << s1 << endl;
   cout << "The destination string is: " << s2 << endl;
   // Note: char_traits::copy is potentially unsafe, consider
   // using char_traits::_Copy_s instead.
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "
        << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd
```

## <a name="copy_s"></a> char_traits::_Copy_s

Kopiert eine angegebene Anzahl von Zeichen aus einer Zeichenfolge in eine andere.

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parameter

*dest* -\
Das Zeichenfolgen- oder Zeichenarray, das die kopierte Zeichenfolgensequenz empfangen soll.

*dest_size*\
Die Größe von *dest*. Wenn `char_type` **char**ist, wird diese Größe in Bytes angezeigt. Wenn `char_type` **wchar_t**ist, wird diese Größe in Wörtern angezeigt.

*_FROM*\
Das zu kopierende Quellzeichenfolgen- oder -zeichenarray.

*Anzahl*\
Die Anzahl der zu kopierenden Elemente.

### <a name="return-value"></a>Rückgabewert

Das Zeichenfolgen- oder Zeichenarray, das die kopierte Zeichenfolgensequenz empfangen soll.

### <a name="remarks"></a>Bemerkungen

Die Zeichenfolgensequenz für Quelle und Ziel dürfen sich nicht überschneiden.

### <a name="example"></a>Beispiel

```cpp
// char_traits__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type s1[] = "abcd-1234-abcd";
    char_traits<char>::char_type s2[] = "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string is: " << s1 << endl;
    cout << "The destination string is: " << s2 << endl;
    result1 = char_traits<char>::_Copy_s(s1,
        char_traits<char>::length(s1), s2, 4);
    cout << "The result1 = _Copy_s(s1, "
         << "char_traits<char>::length(s1), s2, 4) is: "
         << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd
```

## <a name="eof"></a> char_traits::eof

Gibt das Zeichen für Dateiende (End-of-File, EOF) zurück.

```cpp
static int_type eof();
```

### <a name="return-value"></a>Rückgabewert

Das EOF-Zeichen.

### <a name="remarks"></a>Bemerkungen

Ein-Wert, der das Ende der Datei darstellt (z. b. EOF oder WEOF).

Gemäß C++-Standard darf dieser Wert keinem gültigen `char_type`-Wert entsprechen. Der Microsoft C++ -Compiler erzwingt diese Einschränkung für Typ " **char**", aber nicht für den Typ " **wchar_t**". Das unten gezeigte Beispiel veranschaulicht dies.

### <a name="example"></a>Beispiel

```cpp
// char_traits_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::char_type ch1 = 'x';
    char_traits<char>::int_type int1;
    int1 = char_traits<char>::to_int_type(ch1);
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "
         << int1 << "." << endl << endl;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

```Output
char_type ch1 is 'x' and corresponds to int_type 120.

The eof marker for char_traits<char> is: -1
The eof marker for char_traits<wchar_t> is: 65535
```

## <a name="eq"></a> char_traits::eq

Überprüft, ob zwei `char_type`-Zeichen gleich sind.

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parameter

*_Ch1*\
Das erste von zwei Zeichen, die auf Gleichheit getestet werden.

*_Ch2*\
Das zweite von zwei Zeichen, die auf Gleichheit getestet werden.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das erste Zeichen gleich dem zweiten Zeichen ist; andernfalls **FALSE**.

### <a name="example"></a>Beispiel

```cpp
// char_traits_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Testing for equality
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is equal "
           << "to the character ch2." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch1 == ch3 )
      cout << "The character ch1 is equal "
           << "to the character ch3." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch3." << endl;
}
```

```Output
The character ch1 is not equal to the character ch2.
The character ch1 is equal to the character ch3.
```

## <a name="eq_int_type"></a> char_traits::eq_int_type

Prüft, ob zwei Zeichen, die als `int_type` dargestellt sind, gleich sind oder nicht.

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>Parameter

*_Ch1*\
Das erste der zwei Zeichen, die auf Gleichheit als `int_type`s getestet werden sollen.

*_Ch2*\
Das zweite der beiden zwei Zeichen, die auf Gleichheit als `int_type` getestet werden.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das erste Zeichen gleich dem zweiten Zeichen ist; andernfalls **FALSE**.

### <a name="example"></a>Beispiel

```cpp
// char_traits_eq_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Testing for equality of int_type representations
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );
   if ( b1 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch2."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch2."
           << endl;

   // An equivalent and alternatively test procedure
   if ( int1 == int3 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch3."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch3."
           << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = x corresponding to int1 = 120.
    ch2 = y corresponding to int1 = 121.
    ch3 = x corresponding to int1 = 120.

The int_type representation of character ch1
is not equal to the int_type representation of ch2.
The int_type representation of character ch1
is equal to the int_type representation of ch3.
```

## <a name="find"></a> char_traits::find

Sucht nach dem ersten Vorkommen eines angegebenen Zeichens in einem Bereich von Zeichen.

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>Parameter

*Str*\
Das erste zu suchende Zeichen in der Zeichenfolge.

*_Num*\
Die Anzahl von Positionen – beginnend ab der ersten – im zu durchsuchenden Bereich.

*_Ch*\
Das Zeichen, nach dem im Bereich gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das erste Vorkommen des angegebenen Zeichens im Bereich, wenn eine Übereinstimmung gefunden wird; andernfalls ein NULL-Zeiger.

### <a name="example"></a>Beispiel

```cpp
// char_traits_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   const char* s1 = "f2d-1234-abcd";
   const char* result1;
   cout << "The string to be searched is: " << s1 << endl;

   // Searching for a 'd' in the first 6 positions of string s1
   result1 = char_traits<char>::find ( s1 , 6 , 'd');
   cout << "The character searched for in s1 is: "
        << *result1 << endl;
   cout << "The string beginning with the first occurrence\n "
        << "of the character 'd' is: " << result1 << endl;

   // When no match is found the NULL value is returned
   const char* result2;
   result2 = char_traits<char>::find ( s1 , 3 , 'a');
   if ( result2 == NULL )
      cout << "The result2 of the search is NULL." << endl;
   else
      cout << "The result2 of the search  is: " << result1
           << endl;
}
```

```Output
The string to be searched is: f2d-1234-abcd
The character searched for in s1 is: d
The string beginning with the first occurrence
of the character 'd' is: d-1234-abcd
The result2 of the search is NULL.
```

## <a name="int_type"></a> char_traits::int_type

Ein ganzzahliger Typ, der ein Zeichen des Typs `char_type` oder ein Dateiendezeichen (End-of-File, EOF) darstellen kann.

```cpp
typedef long int_type;
```

### <a name="remarks"></a>Bemerkungen

Es muss möglich sein, einen Wert vom Typ "`CharType`" in "" zu `CharType` `int_type`, ohne den ursprünglichen Wert zu ändern.

### <a name="example"></a>Beispiel

Im Beispiel für [eq_int_type](#eq_int_type) wird verdeutlicht, wie `int_type` deklariert und verwendet wird.

## <a name="length"></a> char_traits::length

Gibt die Länge einer Zeichenfolge zurück.

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>Parameter

*Str*\
Die C-Zeichenfolge, deren Länge gemessen wird.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der Sequenz, die gemessen werden, ohne NULL-Terminator.

### <a name="example"></a>Beispiel

```cpp
// char_traits_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   const char* str1= "Hello";
   cout << "The C-string str1 is: " << str1 << endl;

   size_t lenStr1;
   lenStr1 = char_traits<char>::length ( str1 );
   cout << "The length of C-string str1 is: "
        << lenStr1 << "." << endl;
}
```

```Output
The C-string str1 is: Hello
The length of C-string str1 is: 5.
```

## <a name="lt"></a> char_traits::lt

Überprüft, ob ein Zeichen kleiner als ein anderes ist.

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parameter

*_Ch1*\
Das erste von zwei Zeichen, die auf „kleiner als“ geprüft werden.

*_Ch2*\
Das zweite von zwei Zeichen, die auf „kleiner als“ geprüft werden.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das erste Zeichen kleiner ist als das zweite Zeichen; andernfalls **FALSE**.

### <a name="example"></a>Beispiel

```cpp
// char_traits_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'z';

   // Testing for less than
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch1 is not less "
           << "than the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch3 <  ch2 )
      cout << "The character ch3 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch3 is not less "
           << "than the character ch2." << endl;
}
```

```Output
The character ch1 is less than the character ch2.
The character ch3 is not less than the character ch2.
```

## <a name="move"></a> char_traits::move

Kopiert eine angegebene Anzahl von Zeichen einer Sequenz in eine andere, möglicherweise überlappende, Sequenz.

Diese Methode ist potenziell unsicher, da sie darauf basiert, dass der Aufrufer überprüft, ob die übergebenen Werte korrekt sind. Verwenden Sie stattdessen [char_traits::_Move_s](#move_s).

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parameter

*_To*\
Das Element am Anfang des Zeichenfolgen- oder Zeichenarrays, das die kopierte Zeichenfolgensequenz empfangen soll.

*_FROM*\
Das Element am Anfang des Quellzeichenfolgen- oder -zeichenarrays, das kopiert werden soll.

*_Num*\
Die Anzahl von Elementen, die aus der Quellzeichenfolge kopiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Das erste Element, das in das Zeichen folgen-oder Zeichen Array kopiert *_To* , das die kopierte Zeichenfolge empfangen soll.

### <a name="remarks"></a>Bemerkungen

Quelle und Ziel können sich überschneiden.

### <a name="example"></a>Beispiel

```cpp
// char_traits_move.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string sFrom1 is: " << sFrom1 << endl;
   cout << "The destination stringsTo1 is: " << sTo1 << endl;
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "
        << result1 << endl << endl;

   // When source and destination overlap
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
   char_traits<char>::char_type* result2;
   cout << "The source/destination string sToFrom2 is: "
        << sToFrom2 << endl;
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "
        << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD
```

## <a name="move_s"></a> char_traits::_Move_s

Kopiert eine angegebene Anzahl von Zeichen einer Sequenz in eine andere, möglicherweise überlappende, Sequenz.

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parameter

*dest* -\
Das Element am Anfang des Zeichenfolgen- oder Zeichenarrays, das die kopierte Zeichenfolgensequenz empfangen soll.

*dest_size*\
Die Größe von *dest*. Wenn `char_type` **char**ist, wird dieser Wert in Bytes angezeigt. Wenn `char_type` **wchar_t**ist, wird dies in Wörtern angezeigt.

*_FROM*\
Das Element am Anfang des Quellzeichenfolgen- oder -zeichenarrays, das kopiert werden soll.

*Anzahl*\
Die Anzahl von Elementen, die aus der Quellzeichenfolge kopiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Das erste Element, das in das Zeichen folgen-oder Zeichen Array kopiert wird, das die *kopierte Zeichen* Folge empfangen soll.

### <a name="remarks"></a>Bemerkungen

Quelle und Ziel können sich überschneiden.

### <a name="example"></a>Beispiel

```cpp
// char_traits__Move_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string sFrom1 is: " << sFrom1 << endl;
    cout << "The destination stringsTo1 is: " << sTo1 << endl;
    result1 = char_traits<char>::_Move_s(sTo1,
        char_traits<char>::length(sTo1), sFrom1, 4);
    cout << "The result1 = _Move_s(sTo1, "
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "
         << result1 << endl << endl;

    // When source and destination overlap
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
    char_traits<char>::char_type* result2;
    cout << "The source/destination string sToFrom2 is: "
         << sToFrom2 << endl;
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');
    result2 = char_traits<char>::_Move_s(sToFrom2,
        char_traits<char>::length(sToFrom2), findc, 8);
    cout << "The result2 = _Move_s(sToFrom2, "
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "
         << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD
```

## <a name="not_eof"></a> char_traits::not_eof

Prüft, ob es sich bei einem Zeichen nicht um das Dateiendezeichen (End-of-File, EOF) handelt.

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>Parameter

*_Ch*\
Das als `int_type` dargestellte Zeichen, für das geprüft werden soll, ob es das EOF-Zeichen ist.

### <a name="return-value"></a>Rückgabewert

Die `int_type` Darstellung des getesteten Zeichens, wenn der `int_type` des Zeichens nicht gleich dem des EOF-Zeichens ist.

Wenn der `int_type`-Wert des Zeichens gleich dem EOF-`int_type`-Wert ist, dann **FALSE**.

### <a name="example"></a>Beispiel

```cpp
// char_traits_not_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::int_type int1;
   int1 = char_traits<char>:: to_int_type ( ch1 );
   cout << "The char_type ch1 is " << ch1
        << " corresponding to int_type: "
        << int1 << "." << endl;

   // EOF member function
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );
   cout << "The eofReturn is: " << int2 << endl;

   // Testing for EOF or another character
   char_traits <char>::int_type eofTest1, eofTest2;
   eofTest1 = char_traits<char>::not_eof ( int1 );
   if ( !eofTest1 )
      cout << "The eofTest1 indicates ch1 is an EOF character."
              << endl;
   else
      cout << "The eofTest1 returns: " << eofTest1
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest1 )
           << "." << endl;

   eofTest2 = char_traits<char>::not_eof ( int2 );
   if ( !eofTest2 )
      cout << "The eofTest2 indicates int2 is an EOF character."
           << endl;
   else
      cout << "The eofTest1 returns: " << eofTest2
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest2 )
           << "." << endl;
}
```

```Output
The char_type ch1 is x corresponding to int_type: 120.
The eofReturn is: -1
The eofTest1 returns: 120, which is the character: x.
The eofTest2 indicates int2 is an EOF character.
```

## <a name="off_type"></a> char_traits::off_type

Ein ganzzahliger Typ, der Offsets zwischen Positionen in einem Stream darstellen kann.

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist eine ganze Zahl mit Vorzeichen, die ein Objekt beschreibt, das einen Byte-Offset speichern kann, der an verschiedenen Streampositionierungsvorgängen beteiligt ist. In der Regel ist dies ein Synonym für [streamoff](../standard-library/ios-typedefs.md#streamoff), weist aber im Wesentlichen dieselben Eigenschaften auf wie dieser Typ.

## <a name="pos_type"></a> char_traits::pos_type

Ein ganzzahliger Typ, der Positionen in einem Stream darstellen kann.

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das alle Informationen speichern kann, die zum Wiederherstellen eines beliebigen Dateipositionsindikators innerhalb eines Streams erforderlich sind. In der Regel ist dies ein Synonym für [streampos](../standard-library/ios-typedefs.md#streampos), weist aber stets im Wesentlichen dieselben Eigenschaften auf wie dieser Typ.

## <a name="state_type"></a> char_traits::state_type

Ein Typ, der den Konvertierungsstatus für Multibytezeichen in einem Stream darstellt.

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt ein Objekt, das einen Konvertierungszustand repräsentieren kann. In der Regel ist dies ein Synonym für `mbstate_t`, weist aber stets im Wesentlichen dieselben Eigenschaften auf wie dieser Typ.

## <a name="to_char_type"></a> char_traits::to_char_type

Konvertiert ein `int_type`-Zeichen in das entsprechende `char_type`-Zeichen und gibt das Ergebnis zurück.

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>Parameter

*_Ch*\
Das `int_type`-Zeichen, das als `char_type` dargestellt werden soll.

### <a name="return-value"></a>Rückgabewert

Das `char_type`-Zeichen, das dem `int_type`-Zeichen entspricht.

Ein Wert *_Ch* , der nicht als solche dargestellt werden kann, ergibt ein nicht bestimmtes Ergebnis.

### <a name="remarks"></a>Bemerkungen

Die Konvertierungsvorgänge [to_int_type](#to_int_type) und `to_char_type` sind zueinander umgekehrt, was bedeutet:

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

für beliebige `int_type` *x* und

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

für beliebige `char_type` *x*.

### <a name="example"></a>Beispiel

```cpp
// char_traits_to_char_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'a';
   char_traits<char>::char_type ch2 =  'b';
   char_traits<char>::char_type ch3 =  'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="to_int_type"></a> char_traits::to_int_type

Konvertiert ein `char_type`-Zeichen in das entsprechende `int_type`-Zeichen und gibt das Ergebnis zurück.

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>Parameter

*_Ch*\
Das `char_type`-Zeichen, das als `int_type` dargestellt werden soll.

### <a name="return-value"></a>Rückgabewert

Das `int_type`-Zeichen, das dem `char_type`-Zeichen entspricht.

### <a name="remarks"></a>Bemerkungen

Die Konvertierungsvorgänge `to_int_type` und [to_char_type](#to_char_type) sind zueinander umgekehrt, was bedeutet:

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

für beliebige `int_type` *x*und

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

für beliebige `char_type` *x*.

### <a name="example"></a>Beispiel

```cpp
// char_traits_to_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 = 'a';
   char_traits<char>::char_type ch2 = 'b';
   char_traits<char>::char_type ch3 = 'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="see-also"></a>Weitere Informationen

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
