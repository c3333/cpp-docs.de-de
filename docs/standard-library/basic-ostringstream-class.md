---
title: basic_ostringstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: 9e10474d3e4fb2a37e8ab52f77495758c37e8a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376783"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream-Klasse

Beschreibt ein Objekt, das das Einfügen von Elementen und codierten Objekten in `Alloc` einen Streampuffer der Klasse [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,> steuert.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Alloc*\
Die Zuweisungsklasse.

*Elem*\
Der Typ des grundlegenden Elements der Zeichenfolge.

*Tr*\
Die für das grundlegende Element der Zeichenfolge spezialisierten Zeichenmerkmale.

## <a name="remarks"></a>Bemerkungen

Die Klasse beschreibt ein Objekt, das das Einfügen von Elementen und codierten Objekten in einen Streampuffer steuert, mit Elementen vom Typ `Elem`, deren Zeichenzüge von der Klasse `Tr`bestimmt werden und deren Elemente von einem Zuweisungselement der Klasse `Alloc`zugewiesen werden. Das Objekt speichert ein Objekt der Klasse basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Konstruiert ein Objekt vom Typ `basic_ostringstream`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[allocator_type](#allocator_type)|Der Typ ist ein Synonym für den Vorlagenparameter *Alloc*.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[rdbuf](#rdbuf)|Gibt die Adresse des gespeicherten `pointer` Streampuffers `Alloc` vom Typ an [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> zurück.|
|[Str](#str)|Legt den Text in einem Zeichenfolgenpuffer fest, ohne die Schreibposition zu ändern, oder ruft ihn ab.|

## <a name="requirements"></a>Anforderungen

**Header:** \<sstream>

**Namespace:** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a>basic_ostringstream::allocator_type

Der Typ ist ein Synonym für den Vorlagenparameter *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream

Konstruiert ein Objekt vom Typ „basic_ostringstream“.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parameter

*_mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Ein Objekt des Typs `basic_string`.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse, indem `sb` er [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**) aufruft, wobei sich das gespeicherte Objekt der Klasse [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>. Er initialisiert außerdem **sb** durch Aufruf von basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`).

Der zweite Konstruktor initialisiert die Basisklasse durch Aufrufen von basic_ostream( **sb**). Es initialisiert `sb` sich auch durch Aufrufen basic_stringbuf `Alloc`< **Elem** `ios_base::out`, **Tr**,>(_ *Str*, `_Mode` &#124; ).

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a>basic_ostringstream::rdbuf

Gibt die Adresse des gespeicherten `pointer` Streampuffers vom `Alloc` Typ an [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,> zurück.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des `pointer` gespeicherten Streampuffers vom Typ basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Adresse des `pointer` gespeicherten Streampuffers vom `Alloc` Typ an basic_stringbuf< **Elem**, **Tr**,> zurück.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `rdbuf` verwendet wird, unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_ostringstreamstr"></a><a name="str"></a>basic_ostringstream::str

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
