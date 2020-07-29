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
ms.openlocfilehash: f4f5ddd3d1c0c595dd1661fab73f5267fb161593
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219286"
---
# <a name="basic_ifstream-class"></a>basic_ifstream-Klasse

Beschreibt ein Objekt, das das Extrahieren von Elementen und codierten Objekten aus einem Streampuffer der Klasse [Basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`> mit Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` .

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Elem*\
Das grundlegende Element des Dateipuffers.

*Stadtrat*\
Die Merkmale des grundlegenden Elements des Dateipuffers (in der Regel `char_traits`< `Elem`>).

## <a name="remarks"></a>Bemerkungen

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

## <a name="output"></a>Output

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_ifstream](#basic_ifstream)|Initialisiert eine neue Instanz eines `basic_ifstream`-Objekts.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[ihrer](#close)|Schließt eine Datei.|
|[is_open](#is_open)|Ermittelt, ob eine Datei geöffnet ist.|
|[open](#open)|Öffnet eine Datei.|
|[rdbuf](#rdbuf)|Gibt die Adresse des gespeicherten Streampuffers zurück.|
|[swap](#swap)|Tauscht den Inhalt dieses `basic_ifstream`-Objekts mit dem Inhalt des bereitgestellten `basic_ifstream`-Objekts aus.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator =](#op_eq)|Weist den Inhalt dieses Streamobjekts zu. Dies ist eine Verschiebezuweisung über einen `rvalue`, die keine Kopie hinterlässt.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<fstream>

**Namespace:** std

## <a name="basic_ifstreambasic_ifstream"></a><a name="basic_ifstream"></a>Basic_ifstream:: basic_ifstream

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

*_Filename*\
Der Name der zu öffnenden Datei.

*_Mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Der Standardschutz bei der Dateiöffnung, der dem `shflag`-Parameter in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) entspricht.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse durch Aufrufen von [basic_istream](../standard-library/basic-istream-class.md)( `sb` ), wobei `sb` das gespeicherte Objekt der Klasse [Basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`> ist. Er initialisiert zudem `sb` durch Aufrufen von `basic_filebuf`< `Elem`, `Tr`>.

Der zweite und dritte Konstruktor initialisiert die Basisklasse durch Aufrufen von `basic_istream`( `sb`). Es wird auch initialisiert `sb` , indem [Basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf) <  `Elem` , `Tr`> und dann aufgerufen wird `sb` . [Öffnen](../standard-library/basic-filebuf-class.md#open)Sie ( `_Filename` , `_Mode` &#124; `ios_base::in` ). Wenn die letztere Funktion einen NULL-Zeiger zurückgibt, ruft der Konstruktor **SetState**( `failbit` ) auf.

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

## <a name="basic_ifstreamclose"></a><a name="close"></a>Basic_ifstream:: Close

Schließt eine Datei.

```cpp
void close();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft [rdbuf](#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close)auf.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `close` verwendet wird, unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_ifstreamis_open"></a><a name="is_open"></a>Basic_ifstream:: is_open

Ermittelt, ob eine Datei geöffnet ist.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Datei geöffnet ist, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [rdbuf](#rdbuf) - **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)zurück.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `is_open` verwendet wird, unter [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open).

## <a name="basic_ifstreamopen"></a><a name="open"></a>Basic_ifstream:: Open

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

*_Filename*\
Der Name der zu öffnenden Datei.

*_Mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Der Standardschutz bei der Dateiöffnung, der dem `shflag`-Parameter in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) entspricht.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` &#124; **ios_base:: in) auf**. Wenn das Öffnen fehlschlägt, ruft die Funktion [SetState](../standard-library/basic-ios-class.md#setstate)( `failbit` ) auf, wodurch möglicherweise eine ios_base:: Failure-Ausnahme ausgelöst wird.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) `open` .

## <a name="basic_ifstreamoperator"></a><a name="op_eq"></a>Basic_ifstream:: Operator =

Weist den Inhalt dieses Streamobjekts zu. Dies ist eine Verschiebezuweisung über einen rvalue, die keine Kopie hinterlässt.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein rvalue-Verweis auf ein `basic_ifstream`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt zurück **`*this`** .

### <a name="remarks"></a>Bemerkungen

Der Member-Operator ersetzt den Inhalt des-Objekts, indem er den Inhalt von *right*verwendet, der als rvalue-Verweis behandelt wird. Weitere Informationen finden Sie unter [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="basic_ifstreamrdbuf"></a><a name="rdbuf"></a>Basic_ifstream:: Rdbuf

Gibt die Adresse des gespeicherten Streampuffers zurück.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [basic_filebuf](../standard-library/basic-filebuf-class.md)-Objekt, das den gespeicherten Streampuffer darstellt.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `rdbuf` verwendet wird, unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_ifstreamswap"></a><a name="swap"></a>Basic_ifstream:: Swap

Tauscht den Inhalt von zwei `basic_ifstream`-Objekten aus.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein Verweis auf einen anderen Streampuffer.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht den Inhalt dieses-Objekts mit dem Inhalt von *right*aus.

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
