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
ms.openlocfilehash: fd2ab79466c01343cbdadbcb649e3b05eee3c2a0
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561777"
---
# <a name="basic_istringstream-class"></a>basic_istringstream-Klasse

Beschreibt ein Objekt, das das Extrahieren von Elementen und codierten Objekten aus einem Streampuffer der Klasse [Basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **TR** `Alloc`> steuert.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Zuordnungseinheits*\
Die Zuweisungsklasse.

*Elem*\
Der Typ des grundlegenden Elements der Zeichenfolge.

*Stadtrat*\
Die für das grundlegende Element der Zeichenfolge spezialisierten Zeichenmerkmale.

## <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage beschreibt ein Objekt, das das Extrahieren von Elementen und codierten Objekten aus einem Streampuffer der Klasse [Basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **TR**, `Alloc`> mit Elementen des Typs *Elem*steuert, dessen Zeichen Merkmale durch die Klasse *TR*bestimmt sind und deren Elemente durch eine Zuweisung der Klasse " *Zuweisung*" zugeordnet sind. Das Objekt speichert ein Objekt der Klasse basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_istringstream](#basic_istringstream)|Konstruiert ein Objekt vom Typ `basic_istringstream`.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[allocator_type](#allocator_type)|Der Type stellt ein Synonym für den Vorlagenparameter `Alloc` dar.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[rdbuf](#rdbuf)|Gibt die Adresse des gespeicherten Streampuffers des Typs `pointer` zum [Basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` , `Tr` , `Alloc`> zurück.|
|[str](#str)|Legt den Text in einem Zeichenfolgenpuffer fest, ohne die Schreibposition zu ändern, oder ruft ihn ab.|
|[swap](#swap)|Tauscht die Werte in diesem `basic_istringstream`-Objekt gegen die Werte im bereitgestellten Objekt.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator =](#op_eq)|Weist die Werte aus dem Objektparameter diesem `basic_istringstream`-Objekt zu.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<sstream>

**Namespace:** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a> Basic_istringstream:: allocator_type

Der Type stellt ein Synonym für den Vorlagenparameter `Alloc` dar.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a> Basic_istringstream:: basic_istringstream

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

*_Mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*SRT*\
Ein Objekt vom Typ `basic_string`.

*Richting*\
Ein rvalue-Verweis auf ein `basic_istringstream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse durch Aufrufen von [basic_istream](../standard-library/basic-istream-class.md)( `sb` ), wobei `sb` das gespeicherte Objekt der Klasse [Basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` , `Tr`> ist `Alloc` . Er initialisiert zudem `sb`sb`basic_stringbuf` durch Aufrufen von < `Elem``Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`).

Der zweite Konstruktor initialisiert die Basisklasse durch Aufrufen von `basic_istream(sb)`. Er initialisiert zudem `sb` durch Aufrufen von `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`).

Der dritte Konstruktor initialisiert das-Objekt mit dem Inhalt von *right*, das als rvalue-Verweis behandelt wird.

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a> Basic_istringstream:: Operator =

Weist die Werte aus dem Objektparameter diesem `basic_istringstream`-Objekt zu.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein rvalue-Verweis auf ein `basic_istringstream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator ersetzt den Inhalt des Objekts durch den Inhalt von *right*, der als rvalue-Verweis Verschiebungs Zuweisung behandelt wird.

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a> Basic_istringstream:: Rdbuf

Gibt die Adresse des gespeicherten Streampuffers des Typs `pointer` zum [Basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **TR** `Alloc`> zurück.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des gespeicherten Streampuffers des Typs, der `pointer`< **Elem**, **TR**> Basic_stringbuf werden soll `Alloc` .

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `rdbuf` verwendet wird, unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_istringstreamstr"></a><a name="str"></a> Basic_istringstream:: Str

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

Gibt ein Objekt der Klasse [basic_string](../standard-library/basic-string-class.md) <  **Elem**, **TR** `Alloc`> zurück, dessen gesteuerte Sequenz eine Kopie der Sequenz ist, die von ** \* diesem**gesteuert wird.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion gibt [rdbuf](#rdbuf)  ->  [Str](../standard-library/basic-stringbuf-class.md#str)zurück. Die zweite Member-Funktion ruft `rdbuf`  ->  **Str**( `_Newstr` ) auf.

### <a name="example"></a>Beispiel

Unter [Basic_stringbuf:: Str](../standard-library/basic-stringbuf-class.md#str) finden Sie ein Beispiel, das verwendet `str` .

## <a name="basic_istringstreamswap"></a><a name="swap"></a> Basic_istringstream:: Swap

Tauscht die Werte zweier `basic_istringstream`-Objekte aus.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein lvalue-Verweis auf ein `basic_istringstream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht die Werte dieses-Objekts und die Werte von *right*aus.

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
