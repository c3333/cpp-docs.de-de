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
ms.openlocfilehash: 047b7e9d7fdece75137980b013d43abf1d5e3ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376620"
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

|Konstruktor|BESCHREIBUNG|
|-|-|
|[strstream](#strstream)|Konstruiert ein Objekt vom Typ `strstream`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Einfrieren](#freeze)|Bewirkt, dass ein Streampuffer durch Streampuffervorgänge nicht verfügbar ist.|
|[pcount](#pcount)|Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.|
|[rdbuf](#rdbuf)|Gibt einen Zeiger auf das dem Stream zugeordnete `strstreambuf`-Objekt zurück.|
|[Str](#str)|Ruft [freeze](../standard-library/strstreambuf-class.md#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.|

## <a name="requirements"></a>Anforderungen

**Header:** \<strstream>

**Namespace:** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>strstream::einfrieren

Bewirkt, dass ein Streampuffer durch Streampuffervorgänge nicht verfügbar ist.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parameter

*_Freezeit*\
Ein **Bool,** der angibt, ob der Stream eingefroren werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)auf (_ *Freezeit*).

### <a name="example"></a>Beispiel

Siehe [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) für ein `freeze`Beispiel, das verwendet.

## <a name="strstreampcount"></a><a name="pcount"></a>strstream::pCount

Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, die in die kontrollierte Sequenz geschrieben wurden.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)zurück.

### <a name="example"></a>Beispiel

Unter [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) finden Sie ein Beispiel, das pcount verwendet.

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>strstream::rdbuf

Gibt einen Zeiger auf das dem Stream zugeordneten strstreambuf-Objekt zurück.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das dem Stream zugeordnete strstreambuf-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Adresse des `pointer` gespeicherten Streampuffers vom Typ an [strstreambuf](../standard-library/strstreambuf-class.md)zurück.

### <a name="example"></a>Beispiel

Ein Beispiel, das `rdbuf` verwendet, finden Sie unter [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="strstreamstr"></a><a name="str"></a>strstream::str

Ruft [freeze](../standard-library/strstreambuf-class.md#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.

```cpp
char *str();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf den Anfang der kontrollierten Sequenz.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)zurück.

### <a name="example"></a>Beispiel

Siehe [strstreambuf::str](../standard-library/strstreambuf-class.md#str) für ein `str`Beispiel, das verwendet.

## <a name="strstreamstrstream"></a><a name="strstream"></a>strstream::strstream

Konstruiert ein Objekt vom Typ `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*Count*\
Die Größe des Puffers.

*_mode*\
Der Eingabe- und Ausgabemodus des Puffers. Weitere Informationen finden Sie unter [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Ptr*\
Der Puffer.

### <a name="remarks"></a>Bemerkungen

Beide Konstruktoren initialisieren die Basisklasse, indem sie `sb` [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**) aufrufen, wobei sich das gespeicherte Objekt der Klasse [strstreambuf](../standard-library/strstreambuf-class.md)befindet. Der erste Konstruktor initialisiert auch `sb` durch Aufrufen von [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Der zweite Konstruktor initialisiert die Basisklasse auf einer von zwei Arten:

- Wenn `_Mode`  &  **ios_base::app**== 0, muss *ptr* das erste `count` Element eines Arrays `strstreambuf` `ptr`von `count` `ptr`Elementen und den Konstruktoraufrufe ( , , ) angeben.

- Andernfalls muss *ptr* das erste Element eines Arrays von Zählelementen angeben, das eine C-Zeichenfolge enthält, `ptr`  +  `strlen`deren erstes Element von *ptr*festgelegt wird, und die Konstruktoraufrufe `strstreambuf`( `ptr`, `count`, ( `ptr`) ) .

## <a name="see-also"></a>Siehe auch

[Iostream](../standard-library/istream-typedefs.md#iostream)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
