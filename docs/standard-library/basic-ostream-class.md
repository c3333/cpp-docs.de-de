---
title: basic_ostream-Klasse
ms.date: 03/27/2019
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
ms.openlocfilehash: e074eb30d31c316411dd43f9a7a019defb64e9fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376765"
---
# <a name="basic_ostream-class"></a>basic_ostream-Klasse

Diese Klassenvorlage beschreibt ein Objekt, das das Einfügen von Elementen und `Elem`codierten Objekten in einen Streampuffer mit Elementen `Tr`vom Typ , auch bekannt als [char_type](../standard-library/basic-ios-class.md#char_type), steuert, deren Zeichenzüge durch die Klasse bestimmt werden, auch als [traits_type](../standard-library/basic-ios-class.md#traits_type)bezeichnet.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Elem*\
Ein `char_type`.

*Tr*\
Der `traits_type` eines Zeichens.

## <a name="remarks"></a>Bemerkungen

Die meisten der Memberfunktionen, die [operator<<](#basic_ostream_operator_lt_lt) überladen, sind Funktionen für die formatierte Ausgabe. Sie entsprechen dem folgenden Muster:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{try
{<convert and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
width(0);
// Except for operator<<(Elem)
setstate(state);

return (*this);
```

Zwei weitere Memberfunktionen sind Funktionen für unformatierte Ausgabe. Sie entsprechen dem folgenden Muster:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (!ok)
    state |= badbit;
else
{try
{<obtain and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
setstate(state);

return (*this);
```

Beide Gruppen von Funktionen rufen [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**) auf, wenn beim Einfügen von Elementen ein Fehler auftritt.

Ein Objekt der Klasse basic_istream \< **Elem**, **Tr**> speichert nur ein virtuelles öffentliches Basisobjekt der Klasse [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>**.

## <a name="example"></a>Beispiel

Weitere Informationen zu Ausgabestreams finden Sie im Beispiel für die [basic_ofstream-Klasse](../standard-library/basic-ofstream-class.md).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_ostream](#basic_ostream)|Erstellt ein `basic_ostream`-Objekt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Flush](#flush)|Leert den Puffer.|
|[setzen](#put)|Schreibt ein Zeichen in einen Stream.|
|[seekp](#seekp)|Setzt die Position im Ausgabestream zurück.|
|[sentry](#sentry)|Die geschachtelte Klasse beschreibt ein Objekt, dessen Deklaration die Funktionen für formatierte Ausgabe und für unformatierte Ausgabe strukturiert.|
|[swap](#swap)|Tauscht die Werte dieses `basic_ostream`-Objekts gegen die Werte des bereitgestellten `basic_ostream`-Objekts aus.|
|[tellp](#tellp)|Meldet die Position im Ausgabestream.|
|[Schreiben](#write)|Schreibt Zeichen in einen Stream.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_eq)|Weist diesem Objekt den Wert des bereitgestellten `basic_ostream`-Objektparameters zu.|
|[Betreiber<<](#basic_ostream_operator_lt_lt)|Schreibt in den Stream.|

## <a name="requirements"></a>Anforderungen

**Header:** \<ostream>

**Namespace:** std

## <a name="basic_ostreambasic_ostream"></a><a name="basic_ostream"></a>basic_ostream::basic_ostream

Erstellt ein `basic_ostream`-Objekt.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Parameter

*strbuf*\
Ein Objekt vom Typ [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**true,** wenn dies ein Standardstream ist; andernfalls **false**.

*Richting*\
Ein rvalue-Verweis auf ein Objekt des Typs `basic_ostream`.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse,`strbuf`indem er [init](../standard-library/basic-ios-class.md#init)( ) aufruft. Der zweite Konstruktor initialisiert die Basisklasse, indem [er basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`aufruft.

### <a name="example"></a>Beispiel

Weitere Informationen zu Ausgabestreams finden Sie im Beispiel für [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

## <a name="basic_ostreamflush"></a><a name="flush"></a>basic_ostream::Flush

Leert den Puffer.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Wenn [rdbuf](../standard-library/basic-ios-class.md#rdbuf) kein NULL-Zeiger ist, ruft die Funktion **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#pubsync) auf. Wenn -1 zurückgegeben wird, ruft die Funktion [setstate](../standard-library/basic-ios-class.md#setstate) ( **badbit**) auf. Es gibt ** \*diese**zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "test";
   cout.flush();
}
```

```Output
test
```

## <a name="basic_ostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt"></a>basic_ostream::Operator&lt;&lt;

Schreibt in den Stream.

```cpp
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

### <a name="parameters"></a>Parameter

*Pfn*\
Ein Funktionszeiger.

*strbuf*\
Ein Zeiger auf ein `stream_buf`-Objekt.

*Val*\
Ein Element, das in den Stream geschrieben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Der \<ostream>-Header definiert auch mehrere globale Einfügeoperatoren. Weitere Informationen finden Sie unter [Operator<<](../standard-library/ostream-operators.md#op_lt_lt).

Die erste Memberfunktion stellt sicher, `ostr << endl` dass ein Ausdruck des Formulars [endl](../standard-library/ostream-functions.md#endl)**(ostr)** aufruft und dann ** \*diese**zurückgibt. Die zweiten und dritten Funktionen stellen sicher, dass andere Manipulatoren, z.B. [hex](../standard-library/ios-functions.md#hex), sich ähnlich verhalten. Die übrigen Funktionen sind alle formatierte Ausgabefunktionen.

Die Funktion

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

extrahiert Elemente aus *strbuf*, wenn *strbuf* kein Nullzeiger ist, und fügt sie ein. Die Extrahierung hält am Ende der Datei an, oder wenn eine Extrahierung eine Ausnahme auslöst (die erneut ausgelöst wird). Sie hält ebenfalls an, ohne das jeweilige Element zu extrahieren, wenn bei einer Einfügung ein Fehler auftritt. Wenn die Funktion kein Element einfügt, oder wenn eine Extahierung eine Ausnahme auslöst, ruft die Funktion [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**) aus. In jedem Fall gibt die Funktion ** \*diese**zurück.

Die Funktion

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

konvertiert `_Val` in ein boolesches Feld und fügt es ein, indem [es use_facet<](../standard-library/basic-filebuf-class.md#open)<num_put `(`** \<Elem, OutIt>** [getloc](../standard-library/ios-base-class.md#getloc)) aufgerufen wird. [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**). Hier `OutIt` wird definiert als [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr>**. Die Funktion gibt ** \*diese**zurück.

Die Funktionen

```cpp
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

beide *val* in ein numerisches Feld konvertieren und einfügen, indem`getloc`Sie use_facet<**num_put\<Elem aufrufen, OutIt>**( ). **put**(**OutIt**`rdbuf`( `getloc`), ** \*this**, , **val**). Hier ist **OutIt** als **ostreambuf_iterator\<Elem, Tr>** definiert. Die Funktion gibt ** \*diese**zurück.

Die Funktionen

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

beide konvertieren *val* in ein numerisches Feld und fügen es ein, indem sie use_facet`rdbuf`<`getloc` **\<num_put Elem aufrufen, OutIt>**(`getloc`**. put**(**OutIt**( ), ** \*this**, , **val**). Hier ist **OutIt** als **ostreambuf_iterator\<Elem, Tr>** definiert. Die Funktion gibt ** \*diese**zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ostream_op_write.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```

## <a name="basic_ostreamoperator"></a><a name="op_eq"></a>basic_ostream::operator=

Weist diesem Objekt Werte für den bereitgestellten `basic_ostream`-Objektparameter zu.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `rvalue`-Verweis auf ein `basic_ostream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Memberoperator ruft swap `(right)` auf.

## <a name="basic_ostreamput"></a><a name="put"></a>basic_ostream::put

Schreibt ein Zeichen in einen Stream.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parameter

*_Ch*\
Ein Zeichen.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Die unformatierte Ausgabefunktion fügt das Element *_Ch*ein. Es gibt ** \*diese**zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ostream_put.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout.put( 'v' );
   cout << endl;
   wcout.put( L'l' );
}
```

```Output
v
l
```

## <a name="basic_ostreamseekp"></a><a name="seekp"></a>basic_ostream::seekp

Setzt die Position im Ausgabestream zurück.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parameter

*_pos*\
Die Position im Stream.

*_off*\
Der Offset relativ zu *_Way*.

*_Way*\
Eine der [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir)-Enumerationen.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Wenn [fail](../standard-library/basic-ios-class.md#fail) **false**ist, ruft die erste Memberfunktion **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*) für ein `pos_type` temporäres Objekt `newpos`auf. Wenn `fail` false ist, ruft die zweite Funktion **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)auf (*_Off, _Way*). In beiden Fällen,`off_type`wenn (`off_type`)**newpos ==** ( )(-1) (der Positionierungsvorgang schlägt fehl), ruft die Funktion **istr auf.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Beide Funktionen geben ** \*diese**zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ostream_seekp.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main()
{
    using namespace std;
    ofstream x("basic_ostream_seekp.txt");
    streamoff i = x.tellp();
    cout << i << endl;
    x << "testing";
    i = x.tellp();
    cout << i << endl;
    x.seekp(2);   // Put char in third char position in file
    x << " ";

    x.seekp(2, ios::end);   // Put char two after end of file
    x << "z";
}
```

```Output
0
7
```

## <a name="basic_ostreamsentry"></a><a name="sentry"></a>basic_ostream::sentry

Die geschachtelte Klasse beschreibt ein Objekt, dessen Deklaration die Funktionen für formatierte Ausgabe und für unformatierte Ausgabe strukturiert.

Klassenwächter - öffentlich: explizite\<Wächter(basic_ostream Elem, Tr>& _Ostr); operator bool() const; sentry();

### <a name="remarks"></a>Bemerkungen

Die geschachtelte Klasse beschreibt ein Objekt, dessen Deklaration die Funktionen für formatierte Ausgabe und für unformatierte Ausgabe strukturiert. Wenn **ostr.**[good](../standard-library/basic-ios-class.md#good)**TRUE** ist, und **ostr.**[tie](../standard-library/basic-ios-class.md#tie) kein NULL-Zeiger ist, ruft der Konstruktor **ostr.tie->**[flush](#flush) auf. Der Konstruktor speichert dann `ostr.good` den `status`Von in zurückgegebenen Wert. Ein späterer `operator bool` Aufruf, um diesen gespeicherten Wert zu liefern.

Wenn `uncaught_exception`**FALSE** zurückgibt, und [flags](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) ungleich null ist, ruft der Destruktor [flush](#flush) auf.

## <a name="basic_ostreamswap"></a><a name="swap"></a>basic_ostream::swap

Tauscht die Werte dieses `basic_ostream`-Objekts gegen die Werte des bereitgestellten `basic_ostream`-Objekts aus.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein Verweis auf ein `basic_ostream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft [basic_ios::swap](../standard-library/basic-ios-class.md#swap) `(right)` auf, um den Inhalt dieses Objekts gegen den Inhalt von *right*auszutauschen.

## <a name="basic_ostreamtellp"></a><a name="tellp"></a>basic_ostream::tellp

Meldet die Position im Ausgabestream.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Rückgabewert

Position im Ausgabestream.

### <a name="remarks"></a>Bemerkungen

Wenn [fail](../standard-library/basic-ios-class.md#fail) **false**ist, gibt die Memberfunktion [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**) zurück. Andernfalls wird `pos_type`(-1) zurückgegeben.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `tellp` finden Sie unter [seekp](#seekp).

## <a name="basic_ostreamwrite"></a><a name="write"></a>basic_ostream::schreiben

Schreibt Zeichen in einen Stream.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parameter

*Count*\
Die Anzahl der Zeichen, die in den Stream geschrieben werden sollen.

*Str*\
Die Zeichen, die in den Stream geschrieben werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Die [unformatierte Ausgabefunktion](../standard-library/basic-ostream-class.md) fügt die Reihenfolge der *Zählelemente* ein, die bei *str*beginnen.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `write` finden Sie unter [streamsize](../standard-library/ios-typedefs.md#streamsize).

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
