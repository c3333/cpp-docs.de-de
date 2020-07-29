---
title: '&lt;locale&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: a1e81fe28976e914f90a441ff97027f411b05738
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224811"
---
# <a name="ltlocalegt-functions"></a>&lt;locale&gt;-Funktionen

||||
|-|-|-|
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraph](#isgraph)|
|[islower](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|
|[ToLower](#tolower)|[ToUpper](#toupper)|[use_facet](#use_facet)|

## <a name="has_facet"></a><a name="has_facet"></a>has_facet

Testet, ob ein bestimmtes Facet in einem angegebenen Gebietsschema gespeichert wird.

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>Parameter

*A.a.o.*\
Das Gebietsschema, das auf das Vorhandensein eines Facets getestet werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn für das Gebiets Schema die Facette getestet wurde. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion eignet sich zum Prüfen, ob die nicht obligatorischen Facets in einem Gebietsschema aufgeführt sind, bevor `use_facet` aufgerufen wird, um die Ausnahme zu vermeiden, die ausgelöst werden würde, wenn es nicht vorhanden wäre.

### <a name="example"></a>Beispiel

```cpp
// locale_has_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result = has_facet <ctype<char> > ( loc );
   cout << result << endl;
}
```

```Output
1
```

## <a name="isalnum"></a><a name="isalnum"></a>isalnum

Testet, ob ein Element in einem Gebietsschema ein alphabetisches oder ein numerisches Zeichen ist.

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende alphanumerische Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende alphanumerische Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element alphanumerisch ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="example"></a>Beispiel

```cpp
// locale_isalnum.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalnum ( 'L', loc);
   bool result2 = isalnum ( '@', loc);
   bool result3 = isalnum ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphanumeric." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphanumeric." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphanumeric." << endl;
}
```

```Output
The character 'L' in the locale is alphanumeric.
The character '@' in the locale is  not alphanumeric.
The character '3' in the locale is alphanumeric.
```

## <a name="isalpha"></a><a name="isalpha"></a>isalpha

Testet, ob ein Element in einem Gebietsschema ein alphabetisches Zeichen ist.

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende alphabetische Element enthält, welches getestet werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element alphabetisch ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Alpha**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_isalpha.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalpha ( 'L', loc);
   bool result2 = isalpha ( '@', loc);
   bool result3 = isalpha ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphabetic." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphabetic." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphabetic." << endl;
}
```

## <a name="iscntrl"></a><a name="iscntrl"></a>iscntrl

Testet, ob ein Element in einem Gebietsschema ein Steuerzeichen ist.

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein Steuerzeichen ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **STRG**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_iscntrl.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = iscntrl ( 'L', loc );
   bool result2 = iscntrl ( '\n', loc );
   bool result3 = iscntrl ( '\t', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a control character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a control character." << endl;

   if ( result2 )
      cout << "The character-set 'backslash-n' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale\n is "
           << " not a control character." << endl;

   if ( result3 )
      cout << "The character-set 'backslash-t' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale \n is "
           << " not a control character." << endl;
}
```

## <a name="isdigit"></a><a name="isdigit"></a>IsDigit

Testet, ob ein Element in einem Gebietsschema ein numerisches Zeichen ist.

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein numerisches Zeichen ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Digit**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_is_digit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isdigit ( 'L', loc );
   bool result2 = isdigit ( '@', loc );
   bool result3 = isdigit ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a numeric character." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not a numeric character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a numeric character." << endl;
}
```

## <a name="isgraph"></a><a name="isgraph"></a>isgraph

Testet, ob ein Element in einem Gebietsschema ein alphanumerisches Zeichen oder ein Interpunktionszeichen ist.

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein alphanumerisches Zeichen oder ein Interpunktions Zeichen ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Graph**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_is_graph.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isgraph ( 'L', loc );
   bool result2 = isgraph ( '\t', loc );
   bool result3 = isgraph ( '.', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;

   if ( result2 )
      cout << "The character 'backslash-t' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is\n "
           << "not an alphanumeric or punctuation character." << endl;

   if ( result3 )
      cout << "The character '.' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character '.' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;
}
```

## <a name="islower"></a><a name="islower"></a>IsLower

Testet, ob ein Element in einem Gebietsschema kleingeschrieben ist.

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein Kleinbuchstabe ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Lower**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_islower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = islower ( 'L', loc );
   bool result2 = islower ( 'n', loc );
   bool result3 = islower ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a lowercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a lowercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a lowercase character." << endl;
}
```

## <a name="isprint"></a><a name="isprint"></a>isprint

Testet, ob ein Element in einem Gebietsschema ein druckbares Zeichen ist.

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein druckbares Element ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Print**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_isprint.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );

   bool result1 = isprint ( 'L', loc );
   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a printable character." << endl;

   bool result2 = isprint( '\t', loc );
   if ( result2 )
      cout << "The character 'backslash-t' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is "
           << " not a printable character." << endl;

   bool result3 = isprint( '\n', loc );
   if ( result3 )
      cout << "The character 'backslash-n' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a printable character." << endl;
}
```

## <a name="ispunct"></a><a name="ispunct"></a>Ispunct

Testet, ob ein Element in einem Gebietsschema ein Interpunktionszeichen ist.

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein Interpunktions Zeichen ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) `<` [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **punct**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_ispunct.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = ispunct ( 'L', loc );
   bool result2 = ispunct ( ';', loc );
   bool result3 = ispunct ( '*', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a punctuation character." << endl;

   if ( result2 )
      cout << "The character ';' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character ';' in the locale is "
           << " not a punctuation character." << endl;

   if ( result3 )
      cout << "The character '*' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character '*' in the locale is "
           << " not a punctuation character." << endl;
}
```

## <a name="isspace"></a><a name="isspace"></a>isspace

Testet, ob ein Element in einem Gebietsschema ein Leerzeichen ist.

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein Leerzeichen ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Space**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_isspace.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isspace ( 'L', loc );
   bool result2 = isspace ( '\n', loc );
   bool result3 = isspace ( ' ', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a whitespace character." << endl;

   if ( result2 )
      cout << "The character 'backslash-n' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a whitespace character." << endl;

   if ( result3 )
      cout << "The character ' ' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character ' ' in the locale is "
           << " not a whitespace character." << endl;
}
```

## <a name="isupper"></a><a name="isupper"></a>IsUpper

Testet, ob ein Element in einem Gebietsschema groß geschrieben ist.

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein Großbuchstabe ist. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Upper**, `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_isupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isupper ( 'L', loc );
   bool result2 = isupper ( 'n', loc );
   bool result3 = isupper ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a uppercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a uppercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a uppercase character." << endl;
}
```

## <a name="isxdigit"></a><a name="isxdigit"></a>isxdigit

Testet, ob ein Element in einem Gebietsschema ein Zeichen ist, mit dem eine Hexadezimalzahl dargestellt wird.

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das zu testende Element.

*A.a.o.*\
Das Gebietsschema, das das zu testende Element enthält.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das getestete Element ein Zeichen ist, mit dem eine hexadezimale Zahl dargestellt wird. **`false`** Wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ist](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **xdigit**, `Ch` ).

Hexadezimale Ziffern verwenden Basis 16 unter Verwendung der Zahlen 0 bis 9 sowie der Buchstaben A bis F (ohne Berücksichtigung der Groß-/Kleinschreibung) zur Darstellung von Zahlen, um die Dezimalzahlen 0 bis 15 darzustellen.

### <a name="example"></a>Beispiel

```cpp
// locale_isxdigit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isxdigit ( '5', loc );
   bool result2 = isxdigit ( 'd', loc );
   bool result3 = isxdigit ( 'q', loc );

   if ( result1 )
      cout << "The character '5' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character '5' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result2 )
      cout << "The character 'd' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'd' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result3 )
      cout << "The character 'q' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'q' in the locale is "
           << " not a hexidecimal digit-character." << endl;
}
```

## <a name="tolower"></a><a name="tolower"></a>ToLower

Konvertiert ein Zeichen in einen Kleinbuchstaben.

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das Zeichen, das in einen Kleinbuchstaben umgewandelt werden soll.

*A.a.o.*\
Das Gebietsschema, das das zu konvertierende Zeichen enthält.

### <a name="return-value"></a>Rückgabewert

Das Zeichen, das in einen Kleinbuchstaben umgewandelt wird.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ToLower](../standard-library/ctype-class.md#tolower)( `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = tolower ( 'H', loc );
   cout << "The lower case of 'H' in the locale is: "
        << result1 << "." << endl;
   char result2 = tolower ( 'h', loc );
   cout << "The lower case of 'h' in the locale is: "
        << result2 << "." << endl;
   char result3 = tolower ( '$', loc );
   cout << "The lower case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="toupper"></a><a name="toupper"></a>ToUpper

Konvertiert ein Zeichen in einen Großbuchstaben.

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parameter

*Ch*\
Das Zeichen, das in einen Großbuchstaben umgewandelt werden soll.

*A.a.o.*\
Das Gebietsschema, das das zu konvertierende Zeichen enthält.

### <a name="return-value"></a>Rückgabewert

Das Zeichen, das in einen Großbuchstaben konvertiert wurde.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt [Use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ) zurück. [ToUpper(](../standard-library/ctype-class.md#toupper) `Ch` ).

### <a name="example"></a>Beispiel

```cpp
// locale_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = toupper ( 'h', loc );
   cout << "The upper case of 'h' in the locale is: "
        << result1 << "." << endl;
   char result2 = toupper ( 'H', loc );
   cout << "The upper case of 'H' in the locale is: "
        << result2 << "." << endl;
   char result3 = toupper ( '$', loc );
   cout << "The upper case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="use_facet"></a><a name="use_facet"></a>use_facet

Gibt einen Verweis auf ein Facet eines angegebenen Typs zurück, der in einem Gebietsschema gespeichert wird.

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>Parameter

*A.a.o.*\
Das const-Gebietsschema, das den Typ des Facets enthält, auf den verwiesen wird.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das im Argumentgebietsschema enthaltene Facet der Klasse `Facet`.

### <a name="remarks"></a>Bemerkungen

Der Verweis auf das von der Vorlagenfunktion zurückgegebene Facet bleibt gültig, solange jede Kopie des enthaltenen Gebietsschemas vorhanden ist. Wenn kein solches Facetobjekt der Klasse `Facet` im Argument-Gebietsschema aufgeführt ist, löst die Funktion eine `bad_cast`-Ausnahme aus.

### <a name="example"></a>Beispiel

```cpp
// locale_use_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(
   ctype_base::alpha, 'a'
);
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'
   );

   if ( result1 )
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if ( result2 )
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;
}
```

```Output
The character 'a' in locale loc1 is alphabetic.
The character '!' in locale loc2 is not alphabetic.
```

## <a name="see-also"></a>Siehe auch

[\<locale>](../standard-library/locale.md)
