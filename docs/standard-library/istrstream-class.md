---
title: istrstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: d548a8c2c47a5a345be725afdedb47524344f720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337529"
---
# <a name="istrstream-class"></a>istrstream-Klasse

Beschreibt ein Objekt, das die Extraktion von Elementen und codierten Objekten aus einem Streampuffer der Klasse [strstreambuf](../standard-library/strstreambuf-class.md) steuert.

## <a name="syntax"></a>Syntax

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Bemerkungen

Das Objekt speichert ein Objekt der Klasse `strstreambuf`.

> [!NOTE]
> Diese Klasse ist veraltet. Verwenden Sie stattdessen [istringstream](../standard-library/sstream-typedefs.md#istringstream) oder [wistringstream](../standard-library/sstream-typedefs.md#wistringstream).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[istrstream](#istrstream)|Konstruiert ein Objekt vom Typ `istrstream`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[rdbuf](#rdbuf)|Gibt einen Zeiger auf das dem Stream zugeordnete `strstreambuf`-Objekt zurück.|
|[Str](#str)|Ruft [freeze](../standard-library/strstreambuf-class.md#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.|

## <a name="requirements"></a>Anforderungen

**Header:** \<strstream>

**Namespace:** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a>istrstream::istrstream

Konstruiert ein Objekt vom Typ `istrstream`.

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>Parameter

*Count*\
Die Länge des Puffers (*ptr*).

*Ptr*\
Der Inhalt, mit dem der Puffer initialisiert wird.

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren initialisieren die Basisklasse, indem sie `sb` [istream](../standard-library/istream-typedefs.md#istream)(**sb**) aufrufen, wobei sich das gespeicherte Objekt der Klasse [strstreambuf](../standard-library/strstreambuf-class.md)befindet. Die ersten beiden Konstruktoren `sb` initialisieren ebenfalls durch Aufrufen `strstreambuf`( **const** `char` \*) `ptr`, 0 ). Die verbleibenden beiden Konstruktoren rufen `strstreambuf`stattdessen auf ( **const** `char` *) `ptr`, `count` .

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a>istrstream::rdbuf

Gibt einen Zeiger auf das dem Stream zugeordneten strstreambuf-Objekt zurück.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das dem Stream zugeordnete strstreambuf-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die Adresse des gespeicherten Streampuffers des Typs Zeiger auf [strstreambuf](../standard-library/strstreambuf-class.md) zurück.

### <a name="example"></a>Beispiel

Ein Beispiel, das `rdbuf` verwendet, finden Sie unter [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="istrstreamstr"></a><a name="str"></a>istrstream::str

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

[Istream](../standard-library/istream-typedefs.md#istream)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
