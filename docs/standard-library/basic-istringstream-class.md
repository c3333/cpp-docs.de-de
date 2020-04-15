---
title: basic_istringstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
ms.openlocfilehash: 6a8ead5f1014e7f750e01988241ab020431312da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376801"
---
# <a name="basic_istringstream-class"></a>basic_istringstream-Klasse

Beschreibt ein Objekt, das die Extraktion von Elementen und codierten Objekten aus `Alloc` einem Streampuffer der Klasse [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,> steuert.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Alloc*\
Die Zuweisungsklasse.

*Elem*\
Der Typ des grundlegenden Elements der Zeichenfolge.

*Tr*\
Die für das grundlegende Element der Zeichenfolge spezialisierten Zeichenmerkmale.

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt ein Objekt, das die Extraktion von Elementen und codierten Objekten `Alloc` aus einem Streampuffer der Klasse [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>, mit Elementen des Typs *Elem*steuert, deren Zeichenzüge von der Klasse *Tr*bestimmt werden und deren Elemente von einem *Allocator*der Klasse Alloc zugewiesen werden. Das Objekt speichert ein Objekt der Klasse basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_istringstream](#basic_istringstream)|Konstruiert ein Objekt vom Typ `basic_istringstream`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[allocator_type](#allocator_type)|Der Type stellt ein Synonym für den Vorlagenparameter `Alloc` dar.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[rdbuf](#rdbuf)|Gibt die Adresse des gespeicherten `pointer` Streampuffers `Alloc` vom Typ an [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> zurück.|
|[Str](#str)|Legt den Text in einem Zeichenfolgenpuffer fest, ohne die Schreibposition zu ändern, oder ruft ihn ab.|
|[swap](#swap)|Tauscht die Werte in diesem `basic_istringstream`-Objekt gegen die Werte im bereitgestellten Objekt.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_eq)|Weist die Werte aus dem Objektparameter diesem `basic_istringstream`-Objekt zu.|

## <a name="requirements"></a>Anforderungen

**Header:** \<sstream>

**Namespace:** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a>basic_istringstream::allocator_type

Der Type stellt ein Synonym für den Vorlagenparameter `Alloc` dar.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a>basic_istringstream::basic_istringstream

Konstruiert ein Objekt vom Typ `basic_istringstream`.

```cpp
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```

### <a name="parameters"></a>Parameter

*_mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Ein Objekt des Typs `basic_string`.

*Richting*\
Ein rvalue-Verweis auf ein `basic_istringstream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse, indem [er basic_istream](../standard-library/basic-istream-class.md)(`sb`) aufruft, wobei `sb` sich das gespeicherte Objekt der Klasse [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>. `Alloc` Er initialisiert zudem `sb`sb`basic_stringbuf` durch Aufrufen von < `Elem``Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`).

Der zweite Konstruktor initialisiert die Basisklasse durch Aufrufen von `basic_istream(sb)`. Er initialisiert zudem `sb` durch Aufrufen von `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`).

Der dritte Konstruktor initialisiert das Objekt mit dem Inhalt von *right*, der als rvalue-Referenz behandelt wird.

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a>basic_istringstream::operator=

Weist die Werte aus dem Objektparameter diesem `basic_istringstream`-Objekt zu.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein rvalue-Verweis auf ein `basic_istringstream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Memberoperator ersetzt den Inhalt des Objekts durch den Inhalt von *right*, der als rvalue-Referenzverschiebungszuweisung behandelt wird.

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a>basic_istringstream::rdbuf

Gibt die Adresse des gespeicherten `pointer` Streampuffers vom `Alloc` Typ an [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,> zurück.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des gespeicherten `pointer` Streampuffers vom Typ, `Alloc` der< **Elem**, **Tr**,> basic_stringbuf.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `rdbuf` verwendet wird, unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_istringstreamstr"></a><a name="str"></a>basic_istringstream::str

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

## <a name="basic_istringstreamswap"></a><a name="swap"></a>basic_istringstream::swap

Tauscht die Werte zweier `basic_istringstream`-Objekte aus.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Richting*|Ein `lvalue`-Verweis auf ein `basic_istringstream`-Objekt.|

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion tauscht die Werte dieses Objekts und die Werte von *rechts*aus.

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
