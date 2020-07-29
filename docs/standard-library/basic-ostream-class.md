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
ms.openlocfilehash: 972c21feec805e4c1032f0ebad1e3ac0d7daa7dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219234"
---
# <a name="basic_ostream-class"></a>basic_ostream-Klasse

Diese Klassen Vorlage beschreibt ein Objekt, das das Einfügen von Elementen und codierten Objekten in einen Streampuffer mit Elementen des Typs steuert `Elem` , der auch als " [char_type](../standard-library/basic-ios-class.md#char_type)" bezeichnet wird, dessen Zeichen Merkmale von der Klasse bestimmt werden `Tr` , die auch als [Traits_type](../standard-library/basic-ios-class.md#traits_type)bezeichnet wird.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Elem*\
Ein `char_type`.

*Stadtrat*\
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

Beide Gruppen von Funktionen aufrufen [SetState](../standard-library/basic-ios-class.md#setstate)(**Badbit**), wenn beim Einfügen von Elementen ein Fehler auftritt.

Ein Objekt der Klasse basic_istream \< **Elem**, **Tr**> speichert nur ein virtuelles öffentliches Basisobjekt der Klasse [basic_ios](../standard-library/basic-ios-class.md) **\<Elem**, **Tr>** .

## <a name="example"></a>Beispiel

Weitere Informationen zu Ausgabestreams finden Sie im Beispiel für die [basic_ofstream-Klasse](../standard-library/basic-ofstream-class.md).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_ostream](#basic_ostream)|Erstellt ein `basic_ostream`-Objekt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Flächen](#flush)|Leert den Puffer.|
|[stellte](#put)|Schreibt ein Zeichen in einen Stream.|
|[seekp](#seekp)|Setzt die Position im Ausgabestream zurück.|
|[sentry](#sentry)|Die geschachtelte Klasse beschreibt ein Objekt, dessen Deklaration die Funktionen für formatierte Ausgabe und für unformatierte Ausgabe strukturiert.|
|[swap](#swap)|Tauscht die Werte dieses `basic_ostream`-Objekts gegen die Werte des bereitgestellten `basic_ostream`-Objekts aus.|
|[tellp](#tellp)|Meldet die Position im Ausgabestream.|
|[Schreibung](#write)|Schreibt Zeichen in einen Stream.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator =](#op_eq)|Weist diesem Objekt den Wert des bereitgestellten `basic_ostream`-Objektparameters zu.|
|[Operator<<](#basic_ostream_operator_lt_lt)|Schreibt in den Stream.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<ostream>

**Namespace:** std

## <a name="basic_ostreambasic_ostream"></a><a name="basic_ostream"></a>basic_ostream:: basic_ostream

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
**`true`**, wenn es sich um einen Standardstream handelt. andernfalls **`false`** .

*Richting*\
Ein rvalue-Verweis auf ein Objekt des Typs `basic_ostream`.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse durch Aufrufen von [Init](../standard-library/basic-ios-class.md#init)( `strbuf` ). Der zweite Konstruktor initialisiert die Basisklasse durch Aufrufen von [basic_ios:: Move](../standard-library/basic-ios-class.md#move) `(right)` .

### <a name="example"></a>Beispiel

Weitere Informationen zu Ausgabestreams finden Sie im Beispiel für [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

## <a name="basic_ostreamflush"></a><a name="flush"></a>basic_ostream:: Flush

Leert den Puffer.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Wenn [rdbuf](../standard-library/basic-ios-class.md#rdbuf) kein NULL-Zeiger ist, ruft die Funktion **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#pubsync) auf. Wenn -1 zurückgegeben wird, ruft die Funktion [setstate](../standard-library/basic-ios-class.md#setstate) ( **badbit**) auf. ** \* Dies**wird zurückgegeben.

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

## <a name="basic_ostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt"></a>basic_ostream::-Operator&lt;&lt;

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

*PFN*\
Ein Funktionszeiger.

*strbuf*\
Ein Zeiger auf ein `stream_buf`-Objekt.

*ster*\
Ein Element, das in den Stream geschrieben werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Header \<ostream> definiert außerdem mehrere globale Einfügeoperatoren. Weitere Informationen finden Sie unter [Operator<<](../standard-library/ostream-operators.md#op_lt_lt).

Die erste Member-Funktion stellt sicher, dass ein Ausdruck der Form " `ostr << endl` [Endl](../standard-library/ostream-functions.md#endl)**(Ostr)**" aufruft, und gibt ** \* diesen**zurück. Die zweiten und dritten Funktionen stellen sicher, dass andere Manipulatoren, z.B. [hex](../standard-library/ios-functions.md#hex), sich ähnlich verhalten. Die übrigen Funktionen sind alle formatierte Ausgabefunktionen.

Die Funktion

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

extrahiert Elemente aus " *strinbuf*", wenn " *strinbuf* " kein NULL-Zeiger ist, und fügt Sie ein. Die Extrahierung hält am Ende der Datei an, oder wenn eine Extrahierung eine Ausnahme auslöst (die erneut ausgelöst wird). Sie hält ebenfalls an, ohne das jeweilige Element zu extrahieren, wenn bei einer Einfügung ein Fehler auftritt. Wenn die Funktion kein Element einfügt, oder wenn eine Extahierung eine Ausnahme auslöst, ruft die Funktion [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**) aus. In jedem Fall gibt die Funktion ** \* diesen**Wert zurück.

Die Funktion

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

konvertiert `_Val` in ein boolesches Feld und fügt es durch Aufrufen von [Use_facet](../standard-library/basic-filebuf-class.md#open) **<\<Elem, OutIt> Num_put** `(` [getloc](../standard-library/ios-base-class.md#getloc)) ein. [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**). Hier `OutIt` ist als ostreambuf_iterator definiert [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md) **\<Elem, Tr>** . Die-Funktion gibt ** \* dieses**zurück.

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

jede konvertiert das *Val* in ein numerisches Feld und fügt es durch Aufrufen von **Use_facet<\<Elem, OutIt> Num_put**() ein `getloc` . **Put**(**outit**( `rdbuf` ), ** \* this**, `getloc` , **Val**). Hier ist **outit** als **ostreambuf_iterator \<Elem, Tr> **definiert. Die-Funktion gibt ** \* dieses**zurück.

Die Funktionen

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

jede konvertiert das *Val* in ein numerisches Feld und fügt es durch Aufrufen von **Use_facet<Num_put \<Elem, OutIt> **( `getloc` )**. Put**(**outit**( `rdbuf` ), ** \* this**, `getloc` , **Val**) ein. Hier ist **outit** als **ostreambuf_iterator \<Elem, Tr> **definiert. Die-Funktion gibt ** \* dieses**zurück.

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

## <a name="basic_ostreamoperator"></a><a name="op_eq"></a>basic_ostream:: Operator =

Weist diesem Objekt Werte für den bereitgestellten `basic_ostream`-Objektparameter zu.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `rvalue`-Verweis auf ein `basic_ostream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Memberoperator ruft swap `(right)` auf.

## <a name="basic_ostreamput"></a><a name="put"></a>basic_ostream::p UT

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

Die nicht formatierte Ausgabefunktion fügt das Element *_Ch*ein. ** \* Dies**wird zurückgegeben.

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

## <a name="basic_ostreamseekp"></a><a name="seekp"></a>basic_ostream:: Seekp

Setzt die Position im Ausgabestream zurück.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parameter

*_Pos*\
Die Position im Stream.

*_Off*\
Der Offset relativ zu *_Way*.

*_Way*\
Eine der [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir)-Enumerationen.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Wenn [Fail](../standard-library/basic-ios-class.md#fail) ist **`false`** , ruft die erste Member-Funktion **Newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [Pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*) für ein `pos_type` temporäres Objekt auf `newpos` . Wenn `fail` false ist, ruft die zweite Funktion **Newpos = Rdbuf-#b0** [Pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off, _Way*) auf. In jedem Fall `off_type` Ruft die Funktion ISTR auf, wenn ()**Newpos = =** ( `off_type` ) (-1) (die Positionierung schlägt fehl) **.** [SetState](../standard-library/basic-ios-class.md#setstate)(**Failbit**). Beide Funktionen geben ** \* diesen**Wert zurück.

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

## <a name="basic_ostreamsentry"></a><a name="sentry"></a>basic_ostream:: Sentry

Die geschachtelte Klasse beschreibt ein Objekt, dessen Deklaration die Funktionen für formatierte Ausgabe und für unformatierte Ausgabe strukturiert.

Class Sentry {public: Explizites Sentry (basic_ostream \<Elem, Tr>& _Ostr); Operator bool () Konstanten; ~ Sentry ();};

### <a name="remarks"></a>Bemerkungen

Die geschachtelte Klasse beschreibt ein Objekt, dessen Deklaration die Funktionen für formatierte Ausgabe und für unformatierte Ausgabe strukturiert. Wenn **Ostr.** [gut](../standard-library/basic-ios-class.md#good) **`true`** und **Ostr.** " [Tie](../standard-library/basic-ios-class.md#tie) " ist kein NULL-Zeiger, der Konstruktor ruft " **Ostr. Tie-#b0 ** [Flush](#flush)" auf. Der-Konstruktor speichert dann den von zurückgegebenen Wert `ostr.good` in `status` . Ein späterer-Befehl, der `operator bool` diesen gespeicherten Wert übermittelt.

Wenn `uncaught_exception` Returns **`false`** und [Flags](../standard-library/ios-base-class.md#flags) **&** [Unitbuf](../standard-library/ios-functions.md#unitbuf) ungleich NULL ist, ruft der debugtor [Flush](#flush)auf.

## <a name="basic_ostreamswap"></a><a name="swap"></a>basic_ostream:: Swap

Tauscht die Werte dieses `basic_ostream`-Objekts gegen die Werte des bereitgestellten `basic_ostream`-Objekts aus.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein Verweis auf ein `basic_ostream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft [basic_ios:: Swap](../standard-library/basic-ios-class.md#swap) `(right)` auf, um den Inhalt dieses Objekts für den Inhalt von *right*auszutauschen.

## <a name="basic_ostreamtellp"></a><a name="tellp"></a>basic_ostream:: tellp

Meldet die Position im Ausgabestream.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Rückgabewert

Position im Ausgabestream.

### <a name="remarks"></a>Bemerkungen

Wenn [Fail](../standard-library/basic-ios-class.md#fail) ist **`false`** , gibt die Member-Funktion [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [Pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur` , **in**) zurück. Andernfalls wird `pos_type`(-1) zurückgegeben.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `tellp` finden Sie unter [seekp](#seekp).

## <a name="basic_ostreamwrite"></a><a name="write"></a>basic_ostream:: Write

Schreibt Zeichen in einen Stream.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl der Zeichen, die in den Stream geschrieben werden sollen.

*SRT*\
Die Zeichen, die in den Stream geschrieben werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das basic_ostream-Objekt.

### <a name="remarks"></a>Bemerkungen

Die [nicht formatierte Ausgabefunktion](../standard-library/basic-ostream-class.md) fügt die Sequenz der *count* -Elemente ein, beginnend bei *Str*.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `write` finden Sie unter [streamsize](../standard-library/ios-typedefs.md#streamsize).

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
