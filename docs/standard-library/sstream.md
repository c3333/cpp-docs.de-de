---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 6ab2164e4969a2320f67d479062808b33b0869f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212136"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

Definiert mehrere Klassen Vorlagen, die Iostreams-Vorgänge für Sequenzen unterstützen, die in einem zugeordneten Array Objekt gespeichert sind. Solche Sequenzen können problemlos in und aus Objekten der Klassen Vorlagen [basic_string](../standard-library/basic-string-class.md)konvertiert werden.

## <a name="syntax"></a>Syntax

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*linken*|Ein Verweis auf ein `sstream`-Objekt.|
|*Richting*|Ein Verweis auf ein `sstream`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Objekte des Typs `char *` können die-Funktion in [\<strstream>](../standard-library/strstream.md) für das Streaming verwenden. Da \<strstream> veraltet ist, wird jedoch die Verwendung von \<sstream> empfohlen.

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|Erstellt einen Typ, `basic_istringstream` der auf einen **`char`** Vorlagen Parameter spezialisiert ist.|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|Erstellt einen Typ, `basic_ostringstream` der auf einen **`char`** Vorlagen Parameter spezialisiert ist.|
|[Stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|Erstellt einen Typ, `basic_stringbuf` der auf einen **`char`** Vorlagen Parameter spezialisiert ist.|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|Erstellt einen Typ, `basic_stringstream` der auf einen **`char`** Vorlagen Parameter spezialisiert ist.|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|Erstellt einen Typ, `basic_istringstream` der auf einen **`wchar_t`** Vorlagen Parameter spezialisiert ist.|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|Erstellt einen Typ, `basic_ostringstream` der auf einen **`wchar_t`** Vorlagen Parameter spezialisiert ist.|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|Erstellt einen Typ, `basic_stringbuf` der auf einen **`wchar_t`** Vorlagen Parameter spezialisiert ist.|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|Erstellt einen Typ, `basic_stringstream` der auf einen **`wchar_t`** Vorlagen Parameter spezialisiert ist.|

### <a name="manipulators"></a>Manipulatoren

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Tauscht die Werte zwischen zwei `sstream`-Objekten aus.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|Beschreibt einen die Übertragung zu und aus einer Sequenz von in einem Arrayobjekt gespeicherten Elementen von Elementen des Typs `Elem` steuernden Streampuffer, dessen Zeichenmerkmale durch die Klasse `Tr` ermittelt werden.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Beschreibt ein Objekt, das das Extrahieren von Elementen und codierten Objekten aus einem Streampuffer der Klasse [Basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **TR**, `Alloc`> mit Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` und deren Elemente durch eine Zuweisung der Klasse zugeordnet werden `Alloc` .|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Beschreibt ein Objekt, das das Einfügen von Elementen und codierten Objekten in einen Streampuffer der Klasse [Basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **TR**, `Alloc`> mit Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` und deren Elemente durch eine Zuweisung der Klasse zugeordnet werden `Alloc` .|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Beschreibt ein Objekt, das das Einfügen und Extrahieren von Elementen und codierten Objekten mit einem Streampuffer der Klasse [Basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **TR**, `Alloc`> mit Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` und deren Elemente durch eine Zuweisung der Klasse zugeordnet werden `Alloc` .|

## <a name="requirements"></a>Requirements (Anforderungen)

- **Header:**\<sstream>

- **Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
