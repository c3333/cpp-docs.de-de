---
title: basic_fstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
ms.openlocfilehash: 80992430d6bef6fc46106452dfaa44cc0ed9e71c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376858"
---
# <a name="basic_fstream-class"></a>basic_fstream-Klasse

Beschreibt ein Objekt, das das Einfügen und Extrahieren von Elementen und `Tr` codierten Objekten mithilfe `Elem`eines Streampuffers der Klasse `Tr` [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`> mit Elementen vom Typ steuert, deren Zeichenzüge von der Klasse bestimmt werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Elem*\
Das grundlegende Element des Dateipuffers.

*Tr*\
Die Merkmale des grundlegenden Elements des Dateipuffers (in der Regel `char_traits`< `Elem`>).

## <a name="remarks"></a>Bemerkungen

Das Objekt speichert ein Objekt der Klasse `basic_filebuf`< `Elem`, `Tr`>.

> [!NOTE]
> Der Lesezeiger (get-Zeiger) und der Schreibzeiger (put-Zeiger) eines fstream-Objekts sind **NICHT** unabhängig voneinander. Wenn der get-Zeiger verschoben wird, wird auch der put-Zeiger verschoben.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht, wie ein `basic_fstream`-Objekt erstellt wird, aus dem gelesen und in das geschrieben werden kann.

```cpp
// basic_fstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);
    if (!fs.bad())
    {
        // Write to the file.
        fs << "Writing to a basic_fstream object..." << endl;
        fs.close();

        // Dump the contents of the file to cout.
        fs.open("fstream.txt", ios::in);
        cout << fs.rdbuf();
        fs.close();
    }
}
```

```Output
Writing to a basic_fstream object...
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_fstream](#basic_fstream)|Konstruiert ein Objekt vom Typ `basic_fstream`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Schließen](#close)|Schließt eine Datei.|
|[is_open](#is_open)|Ermittelt, ob eine Datei geöffnet ist.|
|[open](#open)|Öffnet eine Datei.|
|[rdbuf](#rdbuf)|Gibt die Adresse des gespeicherten Streampuffers vom `Tr` Typzeiger an [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`zurück,>.|
|[swap](#swap)|Tauscht den Inhalt dieses Objekts gegen den Inhalt eines anderen `basic_fstream`-Objekts.|

## <a name="requirements"></a>Anforderungen

**Header:** \<fstream>

**Namespace:** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a>basic_fstream::basic_fstream

Konstruiert ein Objekt vom Typ `basic_fstream`.

```cpp
basic_fstream();

explicit basic_fstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```

### <a name="parameters"></a>Parameter

*_Filename*\
Der Name der zu öffnenden Datei.

*_mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Der standardmäßige Dateiöffnungsschutz, der dem *shflag-Parameter* in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)entspricht.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse, `sb` indem er [basic_iostream](../standard-library/basic-iostream-class.md)(`sb`) aufruft, wobei sich das gespeicherte Objekt der Klasse [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>. Es initialisiert `sb` sich `basic_filebuf` \< auch, indem **Es elem**, **Tr**>.

Der zweite und dritte Konstruktor initialisiert die Basisklasse durch Aufrufen von `basic_iostream`( **sb**). Es initialisiert `sb` sich `basic_filebuf` auch, indem \< **Elem**, **Tr**> und dann `_Mode` **sb.**[open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, ). Wenn die letztgenannte Funktion einen Nullzeiger zurückgibt,`failbit`ruft der Konstruktor [setstate](../standard-library/basic-ios-class.md#setstate)( ) auf.

Der vierte Konstruktor initialisiert das Objekt mit dem Inhalt von `right`, das als rvalue-Verweis behandelt wird.

### <a name="example"></a>Beispiel

Ein Beispiel, in dem `basic_fstream` verwendet wird, finden Sie unter [streampos](../standard-library/ios-typedefs.md#streampos).

## <a name="basic_fstreamclose"></a><a name="close"></a>basic_fstream::schließen

Schließt eine Datei.

```cpp
void close();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close)auf.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel zur Verwendung von `close` unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_fstreamis_open"></a><a name="is_open"></a>basic_fstream::is_open

Ermittelt, ob eine Datei geöffnet ist.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Datei geöffnet ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open)zurück.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel zur Verwendung von `is_open` unter [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open).

## <a name="basic_fstreamopen"></a><a name="open"></a>basic_fstream::öffnen

Öffnet eine Datei.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parameter

*_Filename*\
Der Name der zu öffnenden Datei.

*_mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Der standardmäßige Dateiöffnungsschutz, der dem *shflag-Parameter* in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)entspricht.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)auf (_ *Filename*, `_Mode`). Wenn diese Funktion einen Nullzeiger zurückgibt, `failbit`ruft die Funktion [setstate](../standard-library/basic-ios-class.md#setstate)( auf.

### <a name="example"></a>Beispiel

Ein [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) Beispiel für die Verwendung von `open`basic_filebuf .

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a>basic_fstream::operator=

Weist diesem Objekt den Inhalt eines angegebenen Streamobjekts zu. Dies ist eine Verschiebezuweisung mit einem rvalue, der keine Kopie hinterlässt.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein lvalue-Verweis auf ein `basic_fstream`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt `*this` zurück.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator ersetzt den Inhalt des Objekts durch den Inhalt von *right*, der als rvalue-Referenz behandelt wird.

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a>basic_fstream::rdbuf

Gibt die Adresse des gespeicherten Streampuffers zurück, die ein Zeiger auf [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**> ist.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Rückgabewert

Die Adresse des gespeicherten Streampuffers.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel zur Verwendung von `rdbuf` unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_fstreamswap"></a><a name="swap"></a>basic_fstream::swap

Tauscht den Inhalt von zwei `basic_fstream`-Objekten aus.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `lvalue`-Verweis auf ein `basic_fstream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion tauscht den Inhalt dieses Objekts und den Inhalt von *rechts*aus.

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
