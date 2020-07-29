---
title: basic_ofstream-Klasse
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
ms.openlocfilehash: d825dbbe278325e755af6fdffe01a34ac0a4080d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219260"
---
# <a name="basic_ofstream-class"></a>basic_ofstream-Klasse

Beschreibt ein Objekt, das das Einfügen von Elementen und codierten Objekten in einen Streampuffer der Klasse [Basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`> mit Elementen des Typs steuert `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` .

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Elem*\
Das grundlegende Element des Dateipuffers.

*Stadtrat*\
Die Merkmale des grundlegenden Elements des Dateipuffers (in der Regel `char_traits`< `Elem`>).

## <a name="remarks"></a>Bemerkungen

Wenn die **`wchar_t`** Spezialisierung von `basic_ofstream` in die Datei schreibt und die Datei im Textmodus geöffnet ist, wird eine MBCS-Sequenz geschrieben. Die interne Darstellung verwendet einen Puffer von **`wchar_t`** Zeichen.

Das Objekt speichert ein Objekt der Klasse `basic_filebuf`< `Elem`, `Tr`>.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie ein `basic_ofstream`-Objekt erstellt und Text in dieses Objekt geschrieben wird.

```cpp
// basic_ofstream_class.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_ofstream](#basic_ofstream)|Erstellt ein Objekt vom Typ `basic_ofstream`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[ihrer](#close)|Schließt eine Datei.|
|[is_open](#is_open)|Ermittelt, ob eine Datei geöffnet ist.|
|[open](#open)|Öffnet eine Datei.|
|[rdbuf](#rdbuf)|Gibt die Adresse des gespeicherten Streampuffers zurück.|
|[swap](#swap)|Tauscht den Inhalt dieses `basic_ofstream`-Objekts gegen den Inhalt des bereitgestellten `basic_ofstream`-Objekts aus.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator =](#op_eq)|Weist den Inhalt dieses Streamobjekts zu. Dies ist eine Verschiebezuweisung über einen `rvalue reference`, die keine Kopie hinterlässt.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<fstream>

**Namespace:** std

## <a name="basic_ofstreambasic_ofstream"></a><a name="basic_ofstream"></a>Basic_ofstream:: basic_ofstream

Erstellt ein Objekt vom Typ `basic_ofstream`.

```cpp
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```

### <a name="parameters"></a>Parameter

*_Filename*\
Der Name der zu öffnenden Datei.

*_Mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Der Standardschutz bei der Dateiöffnung, der dem `shflag`-Parameter in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) entspricht.

*Richting*\
Der rvalue-Verweis auf das `basic_ofstream`-Objekt, das benutzt wird, um dieses `basic_ofstream`-Objekt zu initialisieren.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse durch Aufrufen von [basic_ostream](../standard-library/basic-ostream-class.md)( `sb` ), wobei `sb` das gespeicherte Objekt der Klasse [Basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`> ist. Er initialisiert zudem `sb` durch Aufrufen von `basic_filebuf`< `Elem`, `Tr`>.

Der zweite und dritte Konstruktor initialisiert die Basisklasse durch Aufrufen von `basic_ostream`( **sb**). Er initialisiert außerdem `sb` durch Aufrufen von `basic_filebuf` <  `Elem` , `Tr`> und dann `sb` . [Öffnen](../standard-library/basic-filebuf-class.md#open)Sie ( `_Filename` , `_Mode` &#124; `ios_base::out` ). Wenn die letztere Funktion einen NULL-Zeiger zurückgibt, ruft der Konstruktor [SetState](../standard-library/basic-ios-class.md#setstate)( `failbit` ) auf.

Der vierte Konstruktor ist eine Kopierfunktion. Er initialisiert das-Objekt mit dem Inhalt von *right*, das als rvalue-Verweis behandelt wird.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie ein `basic_ofstream`-Objekt erstellt und Text in dieses Objekt geschrieben wird.

```cpp
// basic_ofstream_ctor.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("C:\\ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

## <a name="basic_ofstreamclose"></a><a name="close"></a>Basic_ofstream:: Close

Schließt eine Datei.

```cpp
void close();
```

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close)auf.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `close` verwendet wird, unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_ofstreamis_open"></a><a name="is_open"></a>Basic_ofstream:: is_open

Gibt an, ob eine Datei geöffnet ist.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Datei geöffnet ist, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [rdbuf](#rdbuf) - **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ofstream_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   // Open and close with a basic_filebuf
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );
   file.close( );
   if (file.is_open())
      cout << "it's open" << endl;
   else
      cout << "it's closed" << endl;
}
```

## <a name="basic_ofstreamopen"></a><a name="open"></a>Basic_ofstream:: Open

Öffnet eine Datei.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
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

Die Member-Funktion ruft [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` &#124;) auf `ios_base::out` . Wenn diese Funktion einen NULL-Zeiger zurückgibt, ruft die Funktion [SetState](../standard-library/basic-ios-class.md#setstate)( `failbit` ) auf.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) `open` .

## <a name="basic_ofstreamoperator"></a><a name="op_eq"></a>Basic_ofstream:: Operator =

Weist den Inhalt dieses Streamobjekts zu. Dies ist eine Verschiebezuweisung über einen `rvalue reference`, die keine Kopie hinterlässt.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein rvalue-Verweis auf ein `basic_ofstream`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt zurück **`*this`** .

### <a name="remarks"></a>Bemerkungen

Der Member-Operator ersetzt den Inhalt des-Objekts, indem er den Inhalt von *right*verwendet, der als rvalue-Verweis behandelt wird.

## <a name="basic_ofstreamrdbuf"></a><a name="rdbuf"></a>Basic_ofstream:: Rdbuf

Gibt die Adresse des gespeicherten Streampuffers zurück.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Rückgabewert

Gibt die Adresse des gespeicherten Streampuffers zurück.

### <a name="example"></a>Beispiel

Sie finden ein Beispiel, in dem `rdbuf` verwendet wird, unter [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="basic_ofstreamswap"></a><a name="swap"></a>Basic_ofstream:: Swap

Tauscht den Inhalt von zwei `basic_ofstream`-Objekten aus.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `lvalue`-Verweis auf ein anderes `basic_ofstream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion tauscht den Inhalt dieses-Objekts mit dem Inhalt von *right*aus.

## <a name="see-also"></a>Weitere Informationen

[Basic_ostream-Klasse](../standard-library/basic-ostream-class.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
