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
ms.openlocfilehash: b52ba70607a5214a6aa28f04cdded0b19a56b2f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373542"
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
|[Einfrieren](#freeze)|Bewirkt, dass ein Streampuffer durch Streampuffervorgänge nicht verfügbar ist.|
|[pcount](#pcount)|Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.|
|[rdbuf](#rdbuf)|Gibt einen Zeiger auf das dem Stream zugeordnete `strstreambuf`-Objekt zurück.|
|[Str](#str)|Ruft [freeze](../standard-library/strstreambuf-class.md#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.|

## <a name="requirements"></a>Anforderungen

**Header:** \<strstream>

**Namespace:** std

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>ostrstream::einfrieren

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

Siehe [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) für ein `freeze`Beispiel, das verwendet.

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>ostrstream::ostrstream

Konstruiert ein Objekt vom Typ `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parameter

*Ptr*\
Der Puffer.

*Count*\
Die Größe des Puffers in Byte.

*_mode*\
Der Eingabe- und Ausgabemodus des Puffers. Weitere Informationen finden Sie unter [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="remarks"></a>Bemerkungen

Beide Konstruktoren initialisieren die Basisklasse, indem sie `sb` [ostream](../standard-library/ostream-typedefs.md#ostream)(**sb**) aufrufen, wobei sich das gespeicherte Objekt der Klasse [strstreambuf](../standard-library/strstreambuf-class.md)befindet. Der erste Konstruktor initialisiert auch `sb` durch Aufrufen `strstreambuf`von . Der zweite Konstruktor initialisiert die Basisklasse auf einer von zwei Arten:

- Wenn `_Mode`  &  **ios_base::app**== `ptr` 0, muss das erste `count` Element eines Arrays `strstreambuf`von`ptr` `count`Elementen `ptr`und der Konstruktor aufrufe ( , , ).

- Andernfalls `ptr` muss das erste Element eines Arrays von Zählelementen, das eine `ptr`C-Zeichenfolge enthält, `count`deren erstes Element von gekennzeichnet ist, und die Konstruktoraufrufe `ptr`  +  `strlen` `ptr` `strstreambuf`(`ptr`, ( ) ) festgelegt werden.

## <a name="ostrstreampcount"></a><a name="pcount"></a>ostrstream::pCount

Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, die in die kontrollierte Sequenz geschrieben wurden.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)zurück.

### <a name="example"></a>Beispiel

Siehe [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) für ein Beispiel, das `pcount` verwendet.

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>ostrstream::rdbuf

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

## <a name="ostrstreamstr"></a><a name="str"></a>ostrstream::str

Ruft [freeze](../standard-library/strstreambuf-class.md#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.

```cpp
char *str();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf den Anfang der kontrollierten Sequenz.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)zurück.

### <a name="example"></a>Beispiel

Siehe [strstream::str](../standard-library/strstreambuf-class.md#str) für ein `str`Beispiel, das verwendet.

## <a name="see-also"></a>Siehe auch

[Ostream](../standard-library/ostream-typedefs.md#ostream)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
