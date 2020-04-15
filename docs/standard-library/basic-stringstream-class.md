---
title: basic_stringstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: f08689b1080837f042abfb3c4c52bb0ad558a448
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364868"
---
# <a name="basic_stringstream-class"></a>basic_stringstream-Klasse

Beschreibt ein Objekt, das das Einfügen und Extrahieren von Elementen und codierten Objekten `Alloc` mithilfe eines Streampuffers der Klasse [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,> steuert.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Alloc*\
Die Zuweisungsklasse.

*Elem*\
Der Typ des grundlegenden Elements der Zeichenfolge.

*Tr*\
Die für das grundlegende Element der Zeichenfolge spezialisierten Zeichenmerkmale.

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt ein Objekt, das das Einfügen und Extrahieren von Elementen und codierten `Alloc` Objekten mithilfe eines `Elem`Streampuffers der Klasse [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>, mit Elementen vom Typ steuert, deren Zeichenzüge von der Klasse `Tr`bestimmt werden und deren Elemente von einem Zuweisungspuffer der Klasse `Alloc`zugewiesen werden. Das Objekt speichert ein Objekt der Klasse basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_stringstream](#basic_stringstream)|Konstruiert ein Objekt vom Typ `basic_stringstream`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[allocator_type](#allocator_type)|Der Type stellt ein Synonym für den Vorlagenparameter `Alloc` dar.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[rdbuf](#rdbuf)|Gibt die Adresse des gespeicherten `pointer` Streampuffers `Alloc` vom Typ an [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> zurück.|
|[Str](#str)|Legt den Text in einem Zeichenfolgenpuffer fest, ohne die Schreibposition zu ändern, oder ruft ihn ab.|

## <a name="requirements"></a>Anforderungen

**Header:** \<sstream>

**Namespace:** std

## <a name="basic_stringstreamallocator_type"></a><a name="allocator_type"></a>basic_stringstream::allocator_type

Der Type stellt ein Synonym für den Vorlagenparameter `Alloc` dar.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstreambasic_stringstream"></a><a name="basic_stringstream"></a>basic_stringstream::basic_stringstream

Konstruiert ein Objekt vom Typ `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Ein Objekt des Typs `basic_string`.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse, indem `sb` er [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**) aufruft, wobei sich das gespeicherte Objekt der Klasse [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>. Es initialisiert `sb` sich auch durch Aufrufen basic_stringbuf `Alloc`< `_Mode` **Elem**, **Tr**,>( ).

Der zweite Konstruktor initialisiert die Basisklasse durch Aufruf von basic_iostream( **sb**). Es initialisiert `sb` sich auch, indem basic_stringbuf `Alloc`< **Elem** `_Mode`, **Tr**,>(_ *Str*, .

## <a name="basic_stringstreamrdbuf"></a><a name="rdbuf"></a>basic_stringstream::rdbuf

Gibt die Adresse des gespeicherten Streampuffers des Typs **pointer** zurück, die ein Zeiger auf [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> ist.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des gespeicherten `pointer` Streampuffers vom Typ, `Alloc` der< **Elem**, **Tr**,> basic_stringbuf.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `rdbuf` verwendet wird, unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_stringstreamstr"></a><a name="str"></a>basic_stringstream::str

Legt den Text in einem Zeichenfolgenpuffer fest, ohne die Schreibposition zu ändern, oder ruft ihn ab.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parameter

*_Newstr*\
Die neue Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Gibt ein Objekt [basic_string](../standard-library/basic-string-class.md)< der Klasse basic_string `Alloc` **Elem**, **Tr**,> zurück, dessen gesteuerte Sequenz eine Kopie der sequenziums ist, die von ** \*dieser**gesteuert wird.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion gibt [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)zurück. Die zweite Memberfunktion ruft `rdbuf`  ->  **str**auf ( `_Newstr`).

### <a name="example"></a>Beispiel

Ein Beispiel, das `str` [verwendet, finden Sie unter basic_stringbuf::str.](../standard-library/basic-stringbuf-class.md#str)

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
