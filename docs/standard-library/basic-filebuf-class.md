---
title: basic_filebuf-Klasse
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: ec6fced70a53d27fdb3312a5b349e9e653ccbd24
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79128425"
---
# <a name="basic_filebuf-class"></a>basic_filebuf-Klasse

Beschreibt einen Streampuffer, der die Übertragung von Elementen des Typs *Char_T*steuert, dessen Zeichen Merkmale durch die Klasse *TR*bestimmt werden, in eine und aus einer Sequenz von Elementen, die in einer externen Datei gespeichert sind.

## <a name="syntax"></a>Syntax

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>Parameter

*Char_T*\
Das grundlegende Element des Dateipuffers.

*TR* -\
Die Merkmale des grundlegenden Elements des Datei Puffers (in der Regel `char_traits<Char_T>`).

## <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage beschreibt einen Streampuffer, der die Übertragung von Elementen des Typs *Char_T*steuert, dessen Zeichen Merkmale durch die Klasse *TR*bestimmt werden, in eine und aus einer Sequenz von Elementen, die in einer externen Datei gespeichert sind.

> [!NOTE]
> Objekte vom Typ `basic_filebuf` werden mit einem internen Puffer des Typs __char\*__ erstellt, unabhängig von der `char_type`, die durch den Typparameter *Char_T*angegeben wird. Dies bedeutet, dass eine Unicode-Zeichenfolge (die **wchar_t** Zeichen enthält) in eine ANSI-Zeichenfolge (die **Zeichen enthält)** konvertiert wird, bevor Sie in den internen Puffer geschrieben wird. Erstellen Sie zum Speichern von Unicode-Zeichen folgen im Puffer einen neuen Puffer vom Typ **wchar_t** und legen Sie ihn mithilfe der [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf)`()`-Methode fest. Ein Beispiel, in dem dieses Verhalten veranschaulicht wird, finden Sie im Folgenden.

Ein Objekt der Klasse `basic_filebuf<Char_T, Tr>` speichert einen Dateizeiger, der das `FILE` Objekt festlegt, das den einer geöffneten Datei zugeordneten Stream steuert. Es speichert zudem Zeiger zu zwei Dateikonvertierungs-Facets für die Verwendung durch die geschützten Memberfunktionen [overflow](#overflow) und [underflow](#underflow). Weitere Informationen finden Sie unter [`basic_filebuf::open`](#open).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie ein Objekt des Typs `basic_filebuf<wchar_t>` gezwungen wird, Unicode-Zeichen in seinem internen Puffer durch den Aufruf der `pubsetbuf()`-Methode zu speichern.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_filebuf](#basic_filebuf)|Konstruiert ein Objekt vom Typ `basic_filebuf`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[char_type](#char_type)|Verknüpft einen Typnamen mit dem `Char_T`-Vorlagenparameter.|
|[int_type](#int_type)|Stellt den Typ im Bereich von `basic_filebuf` dem Typ desselben Namens im Bereich `Tr` gleich.|
|[off_type](#off_type)|Stellt den Typ im Bereich von `basic_filebuf` dem Typ desselben Namens im Bereich `Tr` gleich.|
|[pos_type](#pos_type)|Stellt den Typ im Bereich von `basic_filebuf` dem Typ desselben Namens im Bereich `Tr` gleich.|
|[traits_type](#traits_type)|Verknüpft einen Typnamen mit dem `Tr`-Vorlagenparameter.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[close](#close)|Schließt eine Datei.|
|[is_open](#is_open)|Gibt an, ob eine Datei geöffnet ist.|
|[open](#open)|Öffnet eine Datei.|
|[overflow](#overflow)|Eine geschützte virtuelle Funktion, die aufgerufen werden kann, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.|
|[pbackfail](#pbackfail)|Die geschützte virtuelle Memberfunktion versucht, ein Element zurück in den Eingabestream zu versetzen und es dann zum aktuellen Element zu ernennen (wird mit dem nächsten Zeiger darauf gezeigt).|
|[seekoff](#seekoff)|Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[seekpos](#seekpos)|Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[setbuf](#setbuf)|Die geschützte virtuelle Memberfunktion führt einen für jeden abgeleiteten Streampuffer bestimmten Vorgang aus.|
|[Swap](#swap)|Tauscht den `basic_filebuf`-Inhalt mit dem Inhalt des angegebenen `basic_filebuf`-Parameters.|
|[sync](#sync)|Die geschützte virtuelle Funktion versucht, die gesteuerten Streams mit zugehörigen externen Streams zu synchronisieren.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Die geschützte virtuelle Funktion versucht, das aktuelle Element aus dem Eingabestream zu extrahieren.|
|[underflow](#underflow)|Die geschützte virtuelle Funktion versucht, das aktuelle Element aus dem Eingabestream zu extrahieren.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<>

**Namespace:** std

## <a name="basic_filebuf"></a> basic_filebuf::basic_filebuf

Konstruiert ein Objekt vom Typ `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert einen NULL-Zeiger in allen Zeigern, die den Eingabe- und Ausgabepuffer steuern. Außerdem wird ein NULL-Zeiger im Dateizeiger gespeichert.

Der zweite Konstruktor initialisiert das-Objekt mit dem Inhalt von *right*, das als rvalue-Verweis behandelt wird.

## <a name="char_type"></a> basic_filebuf::char_type

Verknüpft einen Typnamen mit dem `Char_T`-Vorlagenparameter.

```cpp
typedef Char_T char_type;
```

## <a name="close"></a> basic_filebuf::close

Schließt eine Datei.

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt einen NULL-Zeiger zurück, wenn der Dateizeiger ein NULL-Zeiger ist.

### <a name="remarks"></a>Bemerkungen

`close` ruft `fclose(fp)` auf. Wenn diese Funktion einen Wert zurückgibt, der ungleich Null ist, gibt die Funktion einen NULL-Zeiger zurück. Andernfalls wird **this** zurückgegeben, um anzugeben, dass die Datei erfolgreich geschlossen wurde.

Wenn bei einem großen Stream Einfügungen seit dem Öffnen des Streams oder seit dem letzten Aufruf von `streampos`aufgetreten sind, ruft die Funktion [`overflow`](#overflow)auf. Außerdem wird eine beliebige Sequenz eingefügt `fac.unshift` `fac`, die zum Wiederherstellen des ursprünglichen Konvertierungs Zustands erforderlich ist Jedes erstellte Element `byte` vom Typ **char** wird in den zugeordneten Stream geschrieben, der durch den Dateizeiger festgelegt wird `fp` wie bei aufeinander folgenden Aufrufen der Form `fputc(byte, fp)`. Wenn der `fac.unshift`-oder Schreibvorgang fehlschlägt, kann die Funktion nicht erfolgreich ausgeführt werden.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird davon ausgegangen, dass sich zwei Dateien im aktuellen Verzeichnis befinden: *basic_filebuf_close. txt* ("testing" ist "testing") und *iotest. txt* (der Inhalt ist "ssss").

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="int_type"></a> basic_filebuf::int_type

Definiert diesen Typ in `basic_filebuf` Gültigkeitsbereich, der dem Typ desselben Namens im `Tr` Bereich entspricht.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="is_open"></a> basic_filebuf::is_open

Gibt an, ob eine Datei geöffnet ist.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Rückgabewert

**true** , wenn der Dateizeiger nicht NULL ist.

### <a name="example"></a>Beispiel

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="off_type"></a> basic_filebuf::off_type

Definiert diesen Typ in `basic_filebuf` Gültigkeitsbereich, der dem Typ desselben Namens im `Tr` Bereich entspricht.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="open"></a> basic_filebuf::open

Öffnet eine Datei.

```cpp
basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode);
```

### <a name="parameters"></a>Parameter

*Dateiname*\
Der Name der zu öffnenden Datei.

*Modus*\
Eine der Enumerationen in [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode).

*Schutz*\
Der standardmäßige Datei öffnende Schutz, der dem *shflag* -Parameter in [_fsopen entspricht, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Rückgabewert

Wenn der Puffer bereits geöffnet ist oder der Dateizeiger ein NULL-Zeiger ist, gibt die Funktion einen NULL-Zeiger zurück. Andernfalls wird **this** zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion öffnet die Datei mit dem Namen *filename*, indem [`fopen`](../c-runtime-library/reference/fopen-wfopen.md)`(filename, strmode)`aufgerufen wird. `strmode` wird von `mode & ~(`[`ate`](../standard-library/ios-base-class.md#openmode)` | `[`binary`](../standard-library/ios-base-class.md#openmode)`)`bestimmt:

- `ios_base::in` wird `"r"` (vorhandene Datei zum Lesen öffnen).

- [ios_base:: Out](../standard-library/ios-base-class.md#fmtflags) oder `ios_base::out | ios_base::trunc` wird `"w"` (vorhandene Datei abschneiden oder zum Schreiben erstellen).

- `ios_base::out | app` wird `"a"` (vorhandene Datei zum Anfügen aller Schreibvorgänge öffnen).

- `ios_base::in | ios_base::out` wird `"r+"` (Öffnen Sie eine vorhandene Datei zum Lesen und schreiben).

- `ios_base::in | ios_base::out | ios_base::trunc` wird `"w+"` (vorhandene Datei abschneiden oder zum Lesen und Schreiben erstellen).

- `ios_base::in | ios_base::out | ios_base::app` wird `"a+"` (vorhandene Datei zum Lesen und Anfügen aller Schreibvorgänge öffnen).

Wenn `mode & ios_base::binary` ungleich NULL ist, fügt die Funktion `b` an `strmode` an, um einen binären Stream anstelle eines Textstreams zu öffnen. Anschließend wird der Wert, der von `fopen` zurückgegeben wird, im Dateizeiger `fp`gespeichert. Wenn `mode & ios_base::ate` ungleich NULL ist und der Dateizeiger kein NULL-Zeiger ist, ruft die Funktion `fseek(fp, 0, SEEK_END)` auf, um den Stream am Dateiende zu positionieren. Wenn dieser Positionierungs Vorgang fehlschlägt, ruft die Funktion [`close`](#close)`(fp)` auf und speichert einen NULL-Zeiger im Dateizeiger.

Wenn der Dateizeiger kein NULL-Zeiger ist, bestimmt die Funktion den Dateikonvertierungs Aspekt: `use_facet<codecvt<Char_T, char, traits_type::`[`state_type`](../standard-library/char-traits-struct.md#state_type)`> >(`[`getloc`](../standard-library/basic-streambuf-class.md#getloc)`)`, die von [Unterlauf](#underflow) und [Überlauf](#overflow)verwendet werden.

Wenn der Dateizeiger ein NULL-Zeiger ist, gibt die Funktion einen NULL-Zeiger zurück. Andernfalls wird **this** zurückgegeben.

### <a name="example"></a>Beispiel

Ein Beispiel, in dem `open`verwendet wird, finden Sie unter [`basic_filebuf::close`](#close) .

## <a name="op_eq"></a> basic_filebuf::operator=

Weist den Inhalt dieses Streampufferobjekts zu. Dabei handelt es sich um eine Verschiebungs Zuweisung mit einem rvalue, der keine Kopie hinterlässt.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Ein rvalue-Verweis auf ein [basic_filebuf](../standard-library/basic-filebuf-class.md)-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt __* this__zurück.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator ersetzt den Inhalt des-Objekts, indem er den Inhalt von *right*verwendet, der als rvalue-Verweis behandelt wird. Weitere Informationen finden Sie unter [rvalue reference declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="overflow"></a> basic_filebuf::overflow

Wird aufgerufen, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder `traits_type::eof`.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich ausgeführt werden kann, wird `traits_type::eof`zurückgegeben. Andernfalls wird `traits_type::`[`not_eof`](../standard-library/char-traits-struct.md#not_eof)`(_Meta)`zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn `_Meta != traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof), versucht die geschützte virtuelle Member-Funktion, das Element `ch = traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(_Meta)` in den Ausgabepuffer einzufügen. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn eine Schreibposition verfügbar ist, kann das Element in der Schreibposition gespeichert werden, und der nächste Zeiger für den Ausgabepuffer kann inkrementiert werden.

- Eine Schreibposition kann verfügbar gemacht werden, indem neuer oder zusätzlicher Speicher für den Ausgabepuffer zugewiesen wird.

- Sie kann alle ausstehenden Ausgaben im Ausgabepuffer, gefolgt von `ch`, mithilfe der factoryumrechnungs-`fac` konvertieren, um `fac.out` bei Bedarf aufzurufen. Jedes erstellte Element `ch` vom Typ *char* wird in den zugeordneten Stream geschrieben, der durch den Dateizeiger festgelegt wird `fp` wie bei aufeinander folgenden Aufrufen der Form `fputc(ch, fp)`. Wenn bei einer Konvertierung oder einem Schreibvorgang ein Fehler auftritt, kann die Funktion nicht erfolgreich ausgeführt werden.

## <a name="pbackfail"></a> basic_filebuf::pbackfail

Versucht, ein Element zurück in den Eingabestream zu versetzen und es dann zum aktuellen Element zu ernennen (wird mit dem nächsten Zeiger darauf gezeigt).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder `traits_type::eof`.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich ausgeführt werden kann, wird `traits_type::eof`zurückgegeben. Andernfalls wird `traits_type::`[`not_eof`](../standard-library/char-traits-struct.md#not_eof)`(_Meta)`zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion versetzt ein Element zurück in den Eingabepuffer und ernennt es dann zum aktuellen Element (wird mit dem nächsten Zeiger darauf gezeigt). Wenn `_Meta == traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof), ist das Element, das zurück abgelegt werden soll, das Element, das sich bereits vor dem aktuellen Element im Stream befindet. Andernfalls wird dieses Element durch `ch = traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(_Meta)`ersetzt. Ein Element kann auf verschiedene Arten durch die Funktion wiederhergestellt werden:

- Wenn eine `putback` Position verfügbar ist und das Element, das dort gespeichert ist, gleich `ch`ist, kann der nächste Zeiger für den Eingabepuffer verringert werden.

- Wenn die Funktion eine `putback` Position verfügbar machen kann, kann dies geschehen, legen Sie den nächsten Zeiger auf den Punkt an dieser Position fest, und speichern Sie `ch` an dieser Position.

- Wenn die Funktion ein Element auf den Eingabestream zurücksetzen kann, ist dies möglich, z. b. durch Aufrufen von `ungetc` für ein Element des Typs **char**.

## <a name="pos_type"></a> basic_filebuf::pos_type

Definiert diesen Typ in `basic_filebuf` Gültigkeitsbereich, der dem Typ desselben Namens im `Tr` Bereich entspricht.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a> basic_filebuf::seekoff

Versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_Off*\
Die Position, die relativ zu *_Way*gesucht werden soll.

*_Way*\
Gibt den Startpunkt für Offsetvorgänge an. Mögliche Werte sind unter [seekdir](../standard-library/ios-base-class.md#seekdir) aufgeführt.

*_Which*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden.

### <a name="return-value"></a>Rückgabewert

Gibt die neue Position oder eine ungültige Streamposition zurück.

### <a name="remarks"></a>Bemerkungen

Die Funktion der geschützten virtuellen Member versucht, die aktuellen Positionen für die kontrollierten Streams zu ändern. Für ein Objekt der Klasse [`basic_filebuf`](../standard-library/basic-filebuf-class.md)`<Char_T, Tr>`kann eine Streamposition durch ein Objekt vom Typ `fpos_t`dargestellt werden, in dem ein Offset und alle Zustandsinformationen gespeichert werden, die zum Analysieren eines breiten Streams benötigt werden. Der Offset 0 (null) verweist auf das erste Element des Streams. (Ein Objekt vom Typ [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) speichert mindestens ein `fpos_t`-Objekt.)

Bei einer Datei, die sowohl zum Lesen als auch zum Schreiben geöffnet wird, werden sowohl die Eingabe- als auch Ausgabestreams zusammen positioniert. Um zwischen einfügen und extrahieren zu wechseln, müssen Sie entweder [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) oder [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)abrufen. Aufrufe von `pubseekoff` (und somit von `seekoff`) haben verschiedene Einschränkungen für [Textstreams](../c-runtime-library/text-and-binary-streams.md), [binäre Streams](../c-runtime-library/text-and-binary-streams.md) und [breite Streams](../c-runtime-library/byte-and-wide-streams.md).

Wenn der Dateizeiger `fp` ein NULL-Zeiger ist, schlägt die Funktion fehl. Andernfalls versucht Sie, die Streamposition zu ändern, indem `fseek(fp, _Off, _Way)`aufgerufen wird. Wenn diese Funktion erfolgreich ausgeführt wird und die resultierende Position `fposn` durch Aufrufen von `fgetpos(fp, &fposn)`bestimmt werden kann, ist die Funktion erfolgreich. Wenn die Funktion erfolgreich ausgeführt wird, gibt Sie einen Wert vom Typ `pos_type` mit `fposn`zurück. Andernfalls gibt sie eine ungültige Streamposition zurück.

## <a name="seekpos"></a> basic_filebuf::seekpos

Versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_Sp*\
Die Position, nach der gesucht werden soll.

*_Which*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden.

### <a name="return-value"></a>Rückgabewert

Wenn der Dateizeiger `fp` ein NULL-Zeiger ist, schlägt die Funktion fehl. Andernfalls versucht Sie, die Streamposition zu ändern, indem `fsetpos(fp, &fposn)`aufgerufen wird, wobei `fposn` das in `pos`gespeicherte `fpos_t`-Objekt ist. Wenn diese Funktion erfolgreich ausgeführt wurde, gibt die Funktion `pos` zurück. Andernfalls gibt sie eine ungültige Streamposition zurück. Vergleichen Sie den Rückgabewert mit `pos_type(off_type(-1))`, um festzustellen, ob die Streamposition ungültig ist.

### <a name="remarks"></a>Bemerkungen

Die Funktion der geschützten virtuellen Member versucht, die aktuellen Positionen für die kontrollierten Streams zu ändern. Für ein Objekt der Klasse [`basic_filebuf`](../standard-library/basic-filebuf-class.md)`<Char_T, Tr>`kann eine Streamposition durch ein Objekt vom Typ `fpos_t`dargestellt werden, in dem ein Offset und alle Zustandsinformationen gespeichert werden, die zum Analysieren eines breiten Streams benötigt werden. Der Offset 0 (null) verweist auf das erste Element des Streams. (Ein Objekt vom Typ `pos_type` speichert mindestens ein `fpos_t`-Objekt.)

Bei einer Datei, die sowohl zum Lesen als auch zum Schreiben geöffnet wird, werden sowohl die Eingabe- als auch Ausgabestreams zusammen positioniert. Um zwischen einfügen und extrahieren zu wechseln, müssen Sie entweder [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) oder [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)abrufen. Aufrufe von `pubseekoff` (und zu `seekoff`) weisen verschiedene Einschränkungen für Textstreams, binäre Streams und Breite Streams auf.

Bei einem breiten Stream ruft die Funktion `streampos`overflow[ auf, wenn seit der Öffnung des Streams oder des letzten Aufrufs von ](#overflow) Einfügungen vorgenommen wurden. Außerdem wird eine beliebige Sequenz eingefügt `fac.unshift` `fac`, die zum Wiederherstellen des ursprünglichen Konvertierungs Zustands erforderlich ist Jedes erstellte Element `byte` vom Typ **char** wird in den zugeordneten Stream geschrieben, der durch den Dateizeiger festgelegt wird `fp` wie bei aufeinander folgenden Aufrufen der Form `fputc(byte, fp)`. Wenn der `fac.unshift`-oder Schreibvorgang fehlschlägt, kann die Funktion nicht erfolgreich ausgeführt werden.

## <a name="setbuf"></a> basic_filebuf::setbuf

Führt einen für jeden abgeleiteten Streampuffer bestimmten Vorgang aus.

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*_Buffer*\
Ein Zeiger auf einen Puffer.

*Anzahl*\
Größe des Puffers.

### <a name="return-value"></a>Rückgabewert

Die geschützte Memberfunktion gibt Null zurück, wenn der Dateizeiger `fp` ein NULL-Zeiger ist.

### <a name="remarks"></a>Bemerkungen

`setbuf` ruft `setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))` auf, um das Array von `count` Elementen zu bieten, beginnend bei *_Buffer* als Puffer für den Datenstrom. Wenn diese Funktion einen Wert zurückgibt, der ungleich Null ist, gibt die Funktion einen NULL-Zeiger zurück. Andernfalls wird **this** zurückgegeben, um den Erfolg zu signalisieren.

## <a name="swap"></a> basic_filebuf::swap

Tauscht den Inhalt dieses `basic_filebuf`-Objekts gegen den Inhalt des bereitgestellten `basic_filebuf`-Objekts aus.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Ein Lvalue-Verweis auf einen anderen `basic_filebuf`.

## <a name="sync"></a> basic_filebuf::sync

Versucht, die gesteuerten Streams mit zugehörigen externen Streams zu synchronisieren.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück, wenn der Dateizeiger `fp` ein NULL-Zeiger ist. Andernfalls wird 0 (null) nur zurückgegeben, wenn Aufrufe von [Überlauf](#overflow) und `fflush(fp)` erfolgreich eine ausstehende Ausgabe in den Stream leeren.

## <a name="traits_type"></a> basic_filebuf::traits_type

Verknüpft einen Typnamen mit dem `Tr`-Vorlagenparameter.

```cpp
typedef Tr traits_type;
```

## <a name="underflow"></a> basic_filebuf::underflow

Extrahiert das aktuelle Element aus dem Eingabestream.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich ausgeführt werden kann, wird `traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)zurückgegeben. Andernfalls wird `ch`zurückgegeben, wie im Abschnitt "Hinweise" beschrieben.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion versucht, das aktuelle Element `ch` aus dem Eingabestream zu extrahieren, und gibt das Element als `traits_type::`[`to_int_type`](../standard-library/char-traits-struct.md#to_int_type)`(ch)`zurück. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn eine Lese Position verfügbar ist, wird `ch` als das in der Lese Position gespeicherte Element benötigt und der nächste Zeiger für den Eingabepuffer erhöht.

- Sie kann ein oder mehrere Elemente des Typs **char**lesen, wie bei aufeinander folgenden Aufrufen der Form `fgetc(fp)`, und Sie in ein Element `ch` vom Typ `Char_T` konvertieren, indem Sie die Facetten `fac` der Dateikonvertierung verwenden, um `fac.in` bei Bedarf aufzurufen. Wenn ein Lesevorgang oder eine Konvertierung fehlschlägt, kann die Funktion nicht erfolgreich ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen

[\<fstream>](../standard-library/fstream.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
