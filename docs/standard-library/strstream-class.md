---
title: strstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: 796bf1b3ac41a4b5a6ab5bc16239d50616f554df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224616"
---
# <a name="strstream-class"></a>strstream-Klasse

Beschreibt ein Objekt, das die Einfügung und Extraktion von Elementen und codierten Objekten mit einem Streampuffer der Klasse [strstreambuf](../standard-library/strstreambuf-class.md) steuert.

## <a name="syntax"></a>Syntax

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Bemerkungen

Das Objekt speichert ein Objekt der Klasse `strstreambuf`.

> [!NOTE]
> Diese Klasse ist veraltet. Verwenden Sie stattdessen [stringstream](../standard-library/sstream-typedefs.md#stringstream) oder [wstringstream](../standard-library/sstream-typedefs.md#wstringstream).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[Strstream](#strstream)|Konstruiert ein Objekt vom Typ `strstream`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[ge](#freeze)|Bewirkt, dass ein Streampuffer durch Streampuffervorgänge nicht verfügbar ist.|
|[pcount](#pcount)|Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.|
|[rdbuf](#rdbuf)|Gibt einen Zeiger auf das dem Stream zugeordnete `strstreambuf`-Objekt zurück.|
|[str](#str)|Ruft [freeze](../standard-library/strstreambuf-class.md#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<strstream>

**Namespace:** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>Strauch:: Einfrieren

Bewirkt, dass ein Streampuffer durch Streampuffervorgänge nicht verfügbar ist.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parameter

*_Freezeit*\
Ein Wert **`bool`** , der angibt, ob der Stream eingefroren werden soll.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft [rdbuf](#rdbuf)  ->  [Freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freizeit*) auf.

### <a name="example"></a>Beispiel

Unter " [straustreambuf:: Freeze](../standard-library/strstreambuf-class.md#freeze) " finden Sie ein Beispiel, das verwendet `freeze` .

## <a name="strstreampcount"></a><a name="pcount"></a>chanstream::p Anzahl

Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, die in die kontrollierte Sequenz geschrieben wurden.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [rdbuf](#rdbuf)  ->  [pcount](../standard-library/strstreambuf-class.md#pcount)zurück.

### <a name="example"></a>Beispiel

Unter [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) finden Sie ein Beispiel, das pcount verwendet.

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>"Strauch:: Rdbuf"

Gibt einen Zeiger auf das dem Stream zugeordneten strstreambuf-Objekt zurück.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das dem Stream zugeordnete strstreambuf-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt die Adresse des gespeicherten Streampuffers des Typs `pointer` in " [straustreambuf](../standard-library/strstreambuf-class.md)" zurück.

### <a name="example"></a>Beispiel

Ein Beispiel, das `rdbuf` verwendet, finden Sie unter [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="strstreamstr"></a><a name="str"></a>"strinstrestream:: str"

Ruft [freeze](../standard-library/strstreambuf-class.md#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.

```cpp
char *str();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf den Anfang der kontrollierten Sequenz.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [rdbuf](#rdbuf)  ->  [Str](../standard-library/strstreambuf-class.md#str)zurück.

### <a name="example"></a>Beispiel

Unter " [straustreambuf:: Str](../standard-library/strstreambuf-class.md#str) " finden Sie ein Beispiel, das verwendet `str` .

## <a name="strstreamstrstream"></a><a name="strstream"></a>"strinstrestream:: strinstream"

Konstruiert ein Objekt vom Typ `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Größe des Puffers.

*_Mode*\
Der Eingabe- und Ausgabemodus des Puffers. Weitere Informationen finden Sie unter [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*PTR*\
Der Puffer.

### <a name="remarks"></a>Bemerkungen

Beide Konstruktoren initialisieren die Basisklasse durch Aufrufen von [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **SB**), wobei `sb` das gespeicherte Objekt der Klasse "" von " [strauf](../standard-library/strstreambuf-class.md)" ist. Der erste Konstruktor `sb` wird auch durch Aufrufen von " [straustreambuf](../standard-library/strstreambuf-class.md#strstreambuf)" initialisiert. Der zweite Konstruktor initialisiert die Basisklasse auf einer von zwei Arten:

- Wenn `_Mode`  &  **ios_base:: App**= = 0, dann muss *ptr* das erste Element eines Arrays von Elementen festlegen `count` , und der Konstruktor ruft `strstreambuf` ( `ptr` , `count` ,) auf `ptr` .

- Andernfalls muss *ptr* das erste Element eines Arrays von count-Elementen festlegen, das eine C-Zeichenfolge enthält, deren erstes Element von *ptr*festgelegt wird, und der Konstruktor ruft `strstreambuf` ( `ptr` , `count` , `ptr`  +  `strlen` ( `ptr` )) auf.

## <a name="see-also"></a>Weitere Informationen

[iostream](../standard-library/istream-typedefs.md#iostream)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
