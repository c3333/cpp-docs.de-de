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
ms.openlocfilehash: 35bed08f2495c971df7f79f62e32b3ff68dfb3d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376885"
---
# <a name="basic_filebuf-class"></a>basic_filebuf-Klasse

Beschreibt einen Streampuffer, der die Übertragung von Elementen vom Typ *Char_T*steuert, deren Zeichenzüge durch die Klasse *Tr*bestimmt werden, an und aus einer Sequenz von Elementen, die in einer externen Datei gespeichert sind.

## <a name="syntax"></a>Syntax

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>Parameter

*Char_T*\
Das grundlegende Element des Dateipuffers.

*Tr*\
Die Merkmale des Basiselements des Dateipuffers (normalerweise `char_traits<Char_T>`).

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt einen Streampuffer, der die Übertragung von Elementen vom Typ *Char_T*steuert, deren Zeichenzüge durch die Klasse *Tr*bestimmt werden, an und aus einer Sequenz von Elementen, die in einer externen Datei gespeichert sind.

> [!NOTE]
> Objekte vom `basic_filebuf` Typ werden mit einem internen Puffer `char_type` vom Typ __char\* __ erstellt, unabhängig von dem, was durch den Typparameter *Char_T*angegeben wird. Dies bedeutet, dass eine Unicode-Zeichenfolge (die **wchar_t** Zeichen enthält) in eine ANSI-Zeichenfolge (mit **Zeichenzeichen)** konvertiert wird, bevor sie in den internen Puffer geschrieben wird. Um Unicode-Zeichenfolgen im Puffer zu speichern, erstellen Sie [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` einen neuen Puffer vom Typ **wchar_t** und legen Sie ihn mithilfe der Methode fest. Ein Beispiel, in dem dieses Verhalten veranschaulicht wird, finden Sie im Folgenden.

Ein Objekt `basic_filebuf<Char_T, Tr>` der Klasse speichert einen Dateizeiger, der das `FILE` Objekt bestimmt, das den Stream steuert, der einer geöffneten Datei zugeordnet ist. Es speichert zudem Zeiger zu zwei Dateikonvertierungs-Facets für die Verwendung durch die geschützten Memberfunktionen [overflow](#overflow) und [underflow](#underflow). Weitere Informationen finden [`basic_filebuf::open`](#open)Sie unter .

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
|[Schließen](#close)|Schließt eine Datei.|
|[is_open](#is_open)|Gibt an, ob eine Datei geöffnet ist.|
|[open](#open)|Öffnet eine Datei.|
|[Überlauf](#overflow)|Eine geschützte virtuelle Funktion, die aufgerufen werden kann, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.|
|[pbackfail](#pbackfail)|Die geschützte virtuelle Memberfunktion versucht, ein Element zurück in den Eingabestream zu versetzen und es dann zum aktuellen Element zu ernennen (wird mit dem nächsten Zeiger darauf gezeigt).|
|[seekoff](#seekoff)|Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[seekpos](#seekpos)|Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[setbuf](#setbuf)|Die geschützte virtuelle Memberfunktion führt einen für jeden abgeleiteten Streampuffer bestimmten Vorgang aus.|
|[Swap](#swap)|Tauscht den `basic_filebuf`-Inhalt mit dem Inhalt des angegebenen `basic_filebuf`-Parameters.|
|[Sync](#sync)|Die geschützte virtuelle Funktion versucht, die gesteuerten Streams mit zugehörigen externen Streams zu synchronisieren.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Die geschützte virtuelle Funktion versucht, das aktuelle Element aus dem Eingabestream zu extrahieren.|
|[Unterlauf](#underflow)|Die geschützte virtuelle Funktion versucht, das aktuelle Element aus dem Eingabestream zu extrahieren.|

## <a name="requirements"></a>Anforderungen

**Header:** \<fstream>

**Namespace:** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf::basic_filebuf

Konstruiert ein Objekt vom Typ `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert einen NULL-Zeiger in allen Zeigern, die den Eingabe- und Ausgabepuffer steuern. Außerdem wird ein NULL-Zeiger im Dateizeiger gespeichert.

Der zweite Konstruktor initialisiert das Objekt mit dem Inhalt von *right*, der als rvalue-Referenz behandelt wird.

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf::char_type

Verknüpft einen Typnamen mit dem `Char_T`-Vorlagenparameter.

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf::schließen

Schließt eine Datei.

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt einen NULL-Zeiger zurück, wenn der Dateizeiger ein NULL-Zeiger ist.

### <a name="remarks"></a>Bemerkungen

`close` ruft `fclose(fp)` auf. Wenn diese Funktion einen Wert zurückgibt, der ungleich Null ist, gibt die Funktion einen NULL-Zeiger zurück. Andernfalls wird **this** zurückgegeben, um anzugeben, dass die Datei erfolgreich geschlossen wurde.

Wenn bei einem breiten Stream seit dem Öffnen des Streams oder seit `streampos`dem letzten [`overflow`](#overflow)Aufruf von Einfügungen aufgetreten sind, ruft die Funktion auf. Außerdem wird eine beliebige Sequenz eingefügt, die zum Wiederherstellen des `fac` ursprünglichen `fac.unshift` Konvertierungsstatus erforderlich ist, indem die Facette der Dateikonvertierung verwendet wird, um bei Bedarf aufzurufen. Jedes `byte` erzeugte Element vom Typ **char** wird in den `fp` zugeordneten Stream geschrieben, `fputc(byte, fp)`der vom Dateizeiger wie durch aufeinander folgende Aufrufe des Formulars bezeichnet wird. Wenn der `fac.unshift` Aufruf oder ein Schreibvorgang fehlschlägt, ist die Funktion nicht erfolgreich.

### <a name="example"></a>Beispiel

Im folgenden Beispiel werden zwei Dateien im aktuellen Verzeichnis angenommen: *basic_filebuf_close.txt* (Inhalt ist "testing") und *iotest.txt* (Inhalt ist "ssss").

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

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf::int_type

Stellt diesen `basic_filebuf` Typ innerhalb eines Bereichs gleich dem `Tr` Typ desselben Namens im Bereich her.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf::is_open

Gibt an, ob eine Datei geöffnet ist.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn der Dateizeiger nicht null ist.

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

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf::off_type

Stellt diesen `basic_filebuf` Typ innerhalb eines Bereichs gleich dem `Tr` Typ desselben Namens im Bereich her.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf::öffnen

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
Eine der Aufzählungen [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode)in .

*Schutz*\
Der standardmäßige Dateiöffnungsschutz, der dem *shflag-Parameter* in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)entspricht.

### <a name="return-value"></a>Rückgabewert

Wenn der Puffer bereits geöffnet ist oder der Dateizeiger ein Nullzeiger ist, gibt die Funktion einen Nullzeiger zurück. Andernfalls wird **this** zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion öffnet die Datei mit [`fopen`](../c-runtime-library/reference/fopen-wfopen.md) `(filename, strmode)`dem Namen *filename*, indem sie aufruft. `strmode`wird bestimmt `mode & ~(` [`ate`](../standard-library/ios-base-class.md#openmode) `|` [`binary`](../standard-library/ios-base-class.md#openmode) `)`aus:

- `ios_base::in`(öffnen `"r"` Sie eine vorhandene Datei zum Lesen).

- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) `ios_base::out | ios_base::trunc` oder `"w"` wird (vorhandene Datei abschneiden oder zum Schreiben erstellen).

- `ios_base::out | app`(öffnen `"a"` Sie eine vorhandene Datei zum Anfügen aller Schreibvorgänge).

- `ios_base::in | ios_base::out`(offene `"r+"` vorhandene Datei zum Lesen und Schreiben).

- `ios_base::in | ios_base::out | ios_base::trunc`(vorhandene `"w+"` Datei abschneiden oder zum Lesen und Schreiben erstellen).

- `ios_base::in | ios_base::out | ios_base::app`(öffnen `"a+"` Sie eine vorhandene Datei zum Lesen und zum Anfügen aller Schreibvorgänge).

Wenn `mode & ios_base::binary` es sich um einen `b` `strmode` Wert ungleich Null handelt, wird die Funktion an die Option andas Öffnen eines Binärstreams anstelle eines Textstreams angehängt. Anschließend wird der im `fopen` Dateizeiger zurückgegebene Wert `fp`gespeichert. Wenn `mode & ios_base::ate` der Dateizeiger ungleich Null ist und der Dateizeiger `fseek(fp, 0, SEEK_END)` kein Nullzeiger ist, ruft die Funktion auf, den Stream am Ende der Datei zu positionieren. Wenn dieser Positionierungsvorgang fehlschlägt, ruft [`close`](#close) `(fp)` die Funktion einen Nullzeiger auf und speichert ihn im Dateizeiger.

Wenn der Dateizeiger kein Nullzeiger ist, bestimmt die Funktion die `use_facet<codecvt<Char_T, char, traits_type::` [`state_type`](../standard-library/char-traits-struct.md#state_type) `> >(` [`getloc`](../standard-library/basic-streambuf-class.md#getloc) `)`Facette der Dateikonvertierung: , für die Verwendung durch [Unter-](#underflow) und [Überlauf](#overflow).

Wenn der Dateizeiger ein NULL-Zeiger ist, gibt die Funktion einen NULL-Zeiger zurück. Andernfalls wird **this** zurückgegeben.

### <a name="example"></a>Beispiel

Ein [`basic_filebuf::close`](#close) Beispiel, das `open`verwendet, finden Sie unter .

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf::operator=

Weist den Inhalt dieses Streampufferobjekts zu. Dies ist eine Verschiebungszuweisung mit einem rvalue, der keine Kopie zurücklässt.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein rvalue-Verweis auf ein [basic_filebuf](../standard-library/basic-filebuf-class.md)-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt __*diese__zurück.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator ersetzt den Inhalt des Objekts durch den Inhalt von *right*, der als rvalue-Referenz behandelt wird. Weitere Informationen finden Sie unter [Rvalue reference declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf::Überlauf

Wird aufgerufen, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in `traits_type::eof`den Puffer oder eingefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich `traits_type::eof`ist, wird zurückgegeben. Andernfalls wird `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn `_Meta != traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof), versucht die geschützte virtuelle `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` Memberfunktion, das Element in den Ausgabepuffer einzufügen. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn eine Schreibposition verfügbar ist, kann das Element in der Schreibposition gespeichert werden, und der nächste Zeiger für den Ausgabepuffer kann inkrementiert werden.

- Eine Schreibposition kann verfügbar gemacht werden, indem neuer oder zusätzlicher Speicher für den Ausgabepuffer zugewiesen wird.

- Es kann jede ausstehende Ausgabe im `ch`Ausgabepuffer konvertieren, gefolgt `fac` von `fac.out` , indem die Facette der Dateikonvertierung verwendet wird, um bei Bedarf aufzurufen. Jedes `ch` erzeugte Element vom Typ *char* wird in den `fp` zugeordneten Stream geschrieben, `fputc(ch, fp)`der vom Dateizeiger wie durch aufeinander folgende Aufrufe des Formulars bezeichnet wird. Wenn bei einer Konvertierung oder einem Schreibvorgang ein Fehler auftritt, kann die Funktion nicht erfolgreich ausgeführt werden.

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf::pbackfail

Versucht, ein Element zurück in den Eingabestream zu versetzen und es dann zum aktuellen Element zu ernennen (wird mit dem nächsten Zeiger darauf gezeigt).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder `traits_type::eof`.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich `traits_type::eof`ist, wird zurückgegeben. Andernfalls wird `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion versetzt ein Element zurück in den Eingabepuffer und ernennt es dann zum aktuellen Element (wird mit dem nächsten Zeiger darauf gezeigt). Wenn `_Meta == traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof), ist das element, das zurückgedrängt werden soll, effektiv das Element, das sich bereits im Stream vor dem aktuellen Element befindet. Andernfalls wird dieses Element `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)`durch ersetzt. Ein Element kann auf verschiedene Arten durch die Funktion wiederhergestellt werden:

- Wenn `putback` eine Position verfügbar ist und das dort `ch`gespeicherte Element gleich vergleicht, kann der nächste Zeiger für den Eingabepuffer dekrementiert werden.

- Wenn die Funktion `putback` eine Position verfügbar machen kann, kann sie dies tun, `ch` den nächsten Zeiger auf diese Position setzen und an dieser Position speichern.

- Wenn die Funktion ein Element auf den Eingabestream zurückschieben kann, `ungetc` kann sie dies tun, z. B. indem sie ein Element vom Typ **char**aufruft.

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf::pos_type

Stellt diesen `basic_filebuf` Typ innerhalb eines Bereichs gleich dem `Tr` Typ desselben Namens im Bereich her.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf::seekoff

Versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_off*\
Die Position, die gesucht werden soll, relativ zu *_Way*.

*_Way*\
Der Startpunkt für Offsetvorgänge. Mögliche Werte sind unter [seekdir](../standard-library/ios-base-class.md#seekdir) aufgeführt.

*_Which*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden.

### <a name="return-value"></a>Rückgabewert

Gibt die neue Position oder eine ungültige Streamposition zurück.

### <a name="remarks"></a>Bemerkungen

Die geschützte funktion des virtuellen Elements versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern. Für ein Objekt [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`der Klasse kann eine Streamposition `fpos_t`durch ein Objekt vom Typ dargestellt werden, das einen Offset und alle Statusinformationen speichert, die zum Analysieren eines breiten Streams erforderlich sind. Versatz Null bezieht sich auf das erste Element des Streams. (Ein Objekt [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) vom Typ `fpos_t` speichert mindestens ein Objekt.)

Bei einer Datei, die sowohl zum Lesen als auch zum Schreiben geöffnet wird, werden sowohl die Eingabe- als auch Ausgabestreams zusammen positioniert. Um zwischen Einfügen und Extrahieren zu wechseln, müssen Sie entweder [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) oder [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)aufrufen. Aufrufe `pubseekoff` von (und `seekoff`damit ) haben verschiedene Einschränkungen für [Textstreams,](../c-runtime-library/text-and-binary-streams.md) [Binärstreams](../c-runtime-library/text-and-binary-streams.md)und [breite Streams](../c-runtime-library/byte-and-wide-streams.md).

Wenn der Dateizeiger `fp` ein Nullzeiger ist, schlägt die Funktion fehl. Andernfalls wird versucht, die Streamposition `fseek(fp, _Off, _Way)`durch Aufrufen von zu ändern. Wenn diese Funktion erfolgreich ist `fposn` und die `fgetpos(fp, &fposn)`resultierende Position durch Aufrufen bestimmt werden kann, ist die Funktion erfolgreich. Wenn die Funktion erfolgreich ist, gibt `pos_type` `fposn`sie einen Wert vom Typ zurück, der . Andernfalls gibt sie eine ungültige Streamposition zurück.

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf::seekpos

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

Wenn der Dateizeiger `fp` ein Nullzeiger ist, schlägt die Funktion fehl. Andernfalls wird versucht, die Streamposition `fsetpos(fp, &fposn)`durch `fposn` Aufrufen `fpos_t` von `pos`zu ändern, wobei das in gespeicherte Objekt gespeichert ist. Wenn diese Funktion erfolgreich ausgeführt wurde, gibt die Funktion `pos` zurück. Andernfalls gibt sie eine ungültige Streamposition zurück. Vergleichen Sie den Rückgabewert mit `pos_type(off_type(-1))`, um festzustellen, ob die Streamposition ungültig ist.

### <a name="remarks"></a>Bemerkungen

Die geschützte funktion des virtuellen Elements versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern. Für ein Objekt [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`der Klasse kann eine Streamposition `fpos_t`durch ein Objekt vom Typ dargestellt werden, das einen Offset und alle Statusinformationen speichert, die zum Analysieren eines breiten Streams erforderlich sind. Versatz Null bezieht sich auf das erste Element des Streams. (Ein Objekt vom Typ `pos_type` speichert mindestens ein `fpos_t`-Objekt.)

Bei einer Datei, die sowohl zum Lesen als auch zum Schreiben geöffnet wird, werden sowohl die Eingabe- als auch Ausgabestreams zusammen positioniert. Um zwischen Einfügen und Extrahieren zu wechseln, müssen Sie entweder [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) oder [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)aufrufen. Aufrufe `pubseekoff` von (und an `seekoff`) haben verschiedene Einschränkungen für Textstreams, Binärstreams und breite Streams.

Bei einem breiten Stream ruft die Funktion [overflow](#overflow) auf, wenn seit der Öffnung des Streams oder des letzten Aufrufs von `streampos` Einfügungen vorgenommen wurden. Außerdem wird eine beliebige Sequenz eingefügt, die zum Wiederherstellen des `fac` ursprünglichen `fac.unshift` Konvertierungsstatus erforderlich ist, indem die Facette der Dateikonvertierung verwendet wird, um bei Bedarf aufzurufen. Jedes `byte` erzeugte Element vom Typ **char** wird in den `fp` zugeordneten Stream geschrieben, `fputc(byte, fp)`der vom Dateizeiger wie durch aufeinander folgende Aufrufe des Formulars bezeichnet wird. Wenn der `fac.unshift` Aufruf oder ein Schreibvorgang fehlschlägt, ist die Funktion nicht erfolgreich.

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf::setbuf

Führt einen für jeden abgeleiteten Streampuffer bestimmten Vorgang aus.

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*_Buffer*\
Ein Zeiger auf einen Puffer.

*Count*\
Größe des Puffers.

### <a name="return-value"></a>Rückgabewert

Die geschützte Memberfunktion gibt Null zurück, wenn der Dateizeiger `fp` ein NULL-Zeiger ist.

### <a name="remarks"></a>Bemerkungen

`setbuf`fordert, `setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))` das Array `count` von Elementen, die bei *_Buffer* beginnen, als Puffer für den Stream anzubieten. Wenn diese Funktion einen Wert zurückgibt, der ungleich Null ist, gibt die Funktion einen NULL-Zeiger zurück. Andernfalls wird **this** zurückgegeben, um den Erfolg zu signalisieren.

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf::swap

Tauscht den Inhalt dieses `basic_filebuf`-Objekts gegen den Inhalt des bereitgestellten `basic_filebuf`-Objekts aus.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein lvalue-Verweis `basic_filebuf`auf eine andere .

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf::sync

Versucht, die gesteuerten Streams mit zugehörigen externen Streams zu synchronisieren.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Rückgabewert

Gibt Null zurück, `fp` wenn der Dateizeiger ein Nullzeiger ist. Andernfalls gibt er nur dann Null zurück, wenn es Aufrufen von [Überlauf](#overflow) und `fflush(fp)` beim Leeren einer ausstehenden Ausgabe für den Stream gelingt.

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf::traits_type

Verknüpft einen Typnamen mit dem `Tr`-Vorlagenparameter.

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic_filebuf::Unterfluss

Extrahiert das aktuelle Element aus dem Eingabestream.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)ist, wird zurückgegeben. Andernfalls wird `ch`zurückgegeben , konvertiert wie im Abschnitt "Bemerkungen" beschrieben.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion versucht, `ch` das aktuelle Element aus dem `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(ch)`Eingabestream zu extrahieren und das Element als zurückzugeben. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn eine Leseposition verfügbar `ch` ist, wird sie als das in der Leseposition gespeicherte Element verwendet und der nächste Zeiger für den Eingabepuffer voran.

- Es kann ein oder mehrere Elemente vom Typ **char**lesen, als ob durch `ch` aufeinander `Char_T` folgende Aufrufe des `fac` Formulars `fac.in` `fgetc(fp)`, und konvertieren sie in ein Element des Typs, indem die Dateikonvertierung Facette nach Bedarf aufrufen. Wenn ein Lesevorgang oder eine Konvertierung fehlschlägt, kann die Funktion nicht erfolgreich ausgeführt werden.

## <a name="see-also"></a>Siehe auch

[\<fstream>](../standard-library/fstream.md)\
[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
