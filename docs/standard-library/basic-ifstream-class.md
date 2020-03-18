---
title: basic_ifstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
ms.openlocfilehash: 1e5e22c837ca2d6389591cec6d2cdd256ca50b1a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427236"
---
# <a name="basic_ifstream-class"></a>basic_ifstream-Klasse

Beschreibt ein Objekt, das das Extrahieren von Elementen und codierten Objekten aus einem Streampuffer der Klasse [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> mit Elementen des Typs `Elem` steuert, dessen Zeichenmerkmale von der Klasse `Tr` bestimmt werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Elem* -\
Das grundlegende Element des Dateipuffers.

*TR* -\
Die Merkmale des grundlegenden Elements des Dateipuffers (in der Regel `char_traits`< `Elem`>).

## <a name="remarks"></a>Hinweise

Das Objekt speichert ein Objekt der Klasse `basic_filebuf`< `Elem`, `Tr`>.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Text aus einer Datei gelesen wird.

```cpp
// basic_ifstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_class.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="input-basic_ifstream_classtxt"></a>Eingabe: basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>Ausgabe

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[basic_ifstream](#basic_ifstream)|Initialisiert eine neue Instanz eines `basic_ifstream`-Objekts.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|Beschreibung|
|-|-|
|[close](#close)|Schließt eine Datei.|
|[is_open](#is_open)|Ermittelt, ob eine Datei geöffnet ist.|
|[open](#open)|Öffnet eine Datei.|
|[rdbuf](#rdbuf)|Gibt die Adresse des gespeicherten Streampuffers zurück.|
|[swap](#swap)|Tauscht den Inhalt dieses `basic_ifstream`-Objekts mit dem Inhalt des bereitgestellten `basic_ifstream`-Objekts aus.|

### <a name="operators"></a>Operatoren

|Operator|Beschreibung|
|-|-|
|[operator=](#op_eq)|Weist den Inhalt dieses Streamobjekts zu. Dies ist eine Verschiebezuweisung über einen `rvalue`, die keine Kopie hinterlässt.|

## <a name="requirements"></a>Voraussetzungen

**Header:** \<>

**Namespace:** std

## <a name="basic_ifstream"></a> basic_ifstream::basic_ifstream

Konstruiert ein Objekt vom Typ `basic_ifstream`.

```cpp
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```

### <a name="parameters"></a>Parameter

*_FileName*\
Der Name der zu öffnenden Datei.

*_Mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Der Standardschutz bei der Dateiöffnung, die dem Parameter `shflag` in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) entspricht.

### <a name="remarks"></a>Hinweise

Der erste Konstruktor initialisiert die Basisklasse durch Aufruf von [basic_istream](../standard-library/basic-istream-class.md)( `sb`), bei der `sb` das gespeicherte Objekt der Klasse [basic_stringbuf>](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> ist. Er initialisiert zudem `sb` durch Aufrufen von `basic_filebuf`< `Elem`, `Tr`>.

Der zweite und dritte Konstruktor initialisiert die Basisklasse durch Aufrufen von `basic_istream`( `sb`). Er initialisiert außerdem `sb` durch Aufrufen von [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>, und anschließend `sb`. [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::in`). Wenn die letzte Funktion einen NULL-Zeiger zurückgibt, ruft der Konstruktor **setstate**( `failbit`auf.

Der vierte Konstruktor initialisiert das Objekt mit dem Inhalt von `right`, das als rvalue-Verweis behandelt wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Text aus einer Datei gelesen wird. Unter [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) finden Sie ein Beispiel zum Erstellen der Datei.

```cpp
// basic_ifstream_ctor.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_ctor.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="close"></a> basic_ifstream::close

Schließt eine Datei.

```cpp
void close();
```

### <a name="remarks"></a>Hinweise

Die Member-Funktion ruft [rdbuf](#rdbuf) auf, **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem [ verwendet wird, unter ](../standard-library/basic-filebuf-class.md#close)basic_filebuf::close`close`.

## <a name="is_open"></a> basic_ifstream::is_open

Ermittelt, ob eine Datei geöffnet ist.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Datei geöffnet ist; andernfalls **FALSE**.

### <a name="remarks"></a>Hinweise

Die Member-Funktion gibt [rdbuf](#rdbuf) - **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)zurück.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem [ verwendet wird, unter ](../standard-library/basic-filebuf-class.md#is_open)basic_filebuf::is_open`is_open`.

## <a name="open"></a> basic_ifstream::open

Öffnet eine Datei.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parameter

*_FileName*\
Der Name der zu öffnenden Datei.

*_Mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Der Standardschutz bei der Dateiöffnung, die dem Parameter `shflag` in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) entspricht.

### <a name="remarks"></a>Hinweise

Die Member-Funktion ruft [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, &#124; `_Mode` **ios_base:: in) auf**. Wenn das Öffnen fehlschlägt, ruft die Funktion [SetState](../standard-library/basic-ios-class.md#setstate)(`failbit`) auf, wodurch möglicherweise eine ios_base:: Failure-Ausnahme ausgelöst wird.

### <a name="example"></a>Beispiel

Ein Beispiel, in dem `open`verwendet wird, finden Sie unter [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) .

## <a name="op_eq"></a> basic_ifstream::operator=

Weist den Inhalt dieses Streamobjekts zu. Dies ist eine Verschiebezuweisung über einen rvalue, die keine Kopie hinterlässt.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Ein rvalue-Verweis auf ein `basic_ifstream`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt `*this` zurück.

### <a name="remarks"></a>Hinweise

Der Member-Operator ersetzt den Inhalt des-Objekts, indem er den Inhalt von *right*verwendet, der als rvalue-Verweis behandelt wird. Weitere Informationen finden Sie unter [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="rdbuf"></a> basic_ifstream::rdbuf

Gibt die Adresse des gespeicherten Streampuffers zurück.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [basic_filebuf](../standard-library/basic-filebuf-class.md)-Objekt, das den gespeicherten Streampuffer darstellt.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem [ verwendet wird, unter ](../standard-library/basic-filebuf-class.md#close)basic_filebuf::close`rdbuf`.

## <a name="swap"></a> basic_ifstream::swap

Tauscht den Inhalt von zwei `basic_ifstream`-Objekten aus.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Ein Verweis auf einen anderen Streampuffer.

### <a name="remarks"></a>Hinweise

Die Member-Funktion tauscht den Inhalt dieses-Objekts mit dem Inhalt von *right*aus.

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
