---
title: ostrstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: f17d8006aea6c5467f8de270318386bb12df264a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222224"
---
# <a name="ostrstream-class"></a>ostrstream-Klasse

Beschreibt ein Objekt, das das Einfügen von Elementen und programmierten Objekten in einen Streampuffer der Klasse [strstreambuf](../standard-library/strstreambuf-class.md) steuert.

## <a name="syntax"></a>Syntax

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Bemerkungen

Das Objekt speichert ein Objekt der Klasse `strstreambuf`.

> [!NOTE]
> Diese Klasse ist veraltet. Verwenden Sie stattdessen [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) oder [wostringstream](../standard-library/sstream-typedefs.md#wostringstream).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[ostrstream](#ostrstream)|Konstruiert ein Objekt vom Typ `ostrstream`.|

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

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>Ostrstream:: Freeze

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

Ein Beispiel, in dem verwendet wird, finden Sie unter " [stranstream:: Freeze](../standard-library/strstreambuf-class.md#freeze) " `freeze`

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>Ostrstream:: Ostrstream

Konstruiert ein Objekt vom Typ `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parameter

*PTR*\
Der Puffer.

*Countdown*\
Die Größe des Puffers in Byte.

*_Mode*\
Der Eingabe- und Ausgabemodus des Puffers. Weitere Informationen finden Sie unter [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="remarks"></a>Bemerkungen

Beide Konstruktoren initialisieren die Basisklasse durch Aufrufen von [ostream](../standard-library/ostream-typedefs.md#ostream)(**SB**), wobei `sb` das gespeicherte Objekt der Klasse [strstreambuf](../standard-library/strstreambuf-class.md)"". Der erste Konstruktor wird auch initialisiert, `sb` indem aufgerufen wird `strstreambuf` . Der zweite Konstruktor initialisiert die Basisklasse auf einer von zwei Arten:

- Wenn `_Mode`  &  **ios_base:: App**= = 0 ist, `ptr` muss das erste Element eines Arrays von Elementen festlegen `count` , und der Konstruktor ruft `strstreambuf` ( `ptr` , `count` ,) auf `ptr` .

- Andernfalls `ptr` muss das erste Element eines Arrays von count-Elementen festlegen, das eine C-Zeichenfolge enthält, deren erstes Element von bestimmt wird `ptr` , und der Konstruktor ruft `strstreambuf` ( `ptr` , `count` , `ptr`  +  `strlen` ( `ptr` )) auf.

## <a name="ostrstreampcount"></a><a name="pcount"></a>Ostrstream::p Anzahl

Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, die in die kontrollierte Sequenz geschrieben wurden.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [rdbuf](#rdbuf)  ->  [pcount](../standard-library/strstreambuf-class.md#pcount)zurück.

### <a name="example"></a>Beispiel

Siehe [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) für ein Beispiel, das `pcount` verwendet.

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>Ostrstream:: Rdbuf

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

## <a name="ostrstreamstr"></a><a name="str"></a>Ostrstream:: Str

Ruft [freeze](../standard-library/strstreambuf-class.md#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.

```cpp
char *str();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf den Anfang der kontrollierten Sequenz.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [rdbuf](#rdbuf)  ->  [Str](../standard-library/strstreambuf-class.md#str)zurück.

### <a name="example"></a>Beispiel

Ein Beispiel, das verwendet, finden Sie unter [strinstream:: Str](../standard-library/strstreambuf-class.md#str) `str` .

## <a name="see-also"></a>Weitere Informationen

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
