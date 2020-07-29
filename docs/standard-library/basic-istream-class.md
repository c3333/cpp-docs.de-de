---
title: basic_istream-Klasse
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: da53db594e057449f2d227f57c902d26396000b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219247"
---
# <a name="basic_istream-class"></a>basic_istream-Klasse

Beschreibt ein Objekt, das das Extrahieren von Elementen und codierten Objekten aus einem Streampuffer mit Elementen des Typs `Char_T` steuert, der auch als [char_type](../standard-library/basic-ios-class.md#char_type) bekannt ist, und dessen Zeichenmerkmale durch die Klasse *Tr* bestimmt werden, die auch als [traits_type](../standard-library/basic-ios-class.md#traits_type) bekannt ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>Bemerkungen

Die meisten der Memberfunktionen, die [operator>>](#op_gt_gt) überladen, sind Funktionen für die formatierte Eingabe. Sie entsprechen dem folgenden Muster:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

Viele weitere Memberfunktionen sind Funktionen für unformatierte Eingabe. Sie entsprechen dem folgenden Muster:

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

Beide Gruppen von Funktionen werden aufgerufen, [`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` Wenn beim Extrahieren von Elementen das Ende der Datei auftritt.

Ein Objekt der Klassen `basic_istream<Char_T, Tr>` Speicher:

- Ein virtuelles öffentliches Basisobjekt der-Klasse [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>` .

- Eine Extraktions Anzahl für den letzten unformatierten Eingabevorgang ( `count` im vorherigen Code aufgerufen).

## <a name="example"></a>Beispiel

Weitere Informationen zu Eingabestreams finden Sie im Beispiel für die [basic_ifstream-Klasse](../standard-library/basic-ifstream-class.md).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_istream](#basic_istream)|Konstruiert ein Objekt vom Typ `basic_istream`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[gcount](#gcount)|Gibt die Anzahl von Zeichen zurück, die bei der letzten unformatierten Eingabe gelesen wurden.|
|[get](#get)|Liest mindestens ein Zeichen aus dem Eingabestream.|
|[getline](#getline)|Liest eine Zeile aus dem Eingabestream.|
|[lassen](#ignore)|Bewirkt, dass eine Anzahl von Elementen ab der aktuellen Leseposition übersprungen werden.|
|[Zam](#peek)|Gibt das nächste zu lesende Zeichen zurück.|
|[putback](#putback)|Schreibt ein angegebenes Zeichen in den Stream.|
|[dazu](#read)|Liest eine angegebene Anzahl von Zeichen aus dem Stream und speichert diese in einem Array.|
|[readsome](#readsome)|Liest nur aus dem Puffer.|
|[seekg](#seekg)|Verschiebt die Leseposition in einem Stream.|
|[sentry](#sentry)|Die geschachtelte Klasse beschreibt ein Objekt, dessen Deklaration die Funktionen für formatierte Eingabe und für unformatierte Eingabe strukturiert.|
|[swap](#swap)|Tauscht dieses `basic_istream`-Objekt gegen den bereitgestellten `basic_istream`-Objektparameter aus.|
|[PPEN](#sync)|Synchronisiert das zugeordnete Eingabegerät des Streams mit dem Puffer des Streams.|
|[tellg](#tellg)|Meldet die aktuelle Leseposition im Stream.|
|[unget](#unget)|Schreibt das zuletzt gelesene Zeichen zurück in den Stream.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator>>](#op_gt_gt)|Ruft eine Funktion für den Eingabestream auf oder liest formatierte Daten aus dem Eingabestream.|
|[Operator =](#op_eq)|Weist den `basic_istream` auf der rechten Seite des Operators diesem Objekt zu. Dabei handelt es sich um eine Verschiebungs Zuweisung mit einem `rvalue` Verweis, der keine Kopie hinterlässt.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<istream>

**Namespace:** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream:: basic_istream

Konstruiert ein Objekt vom Typ `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parameter

*strbuf*\
Ein Objekt vom Typ [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**`true`**, wenn es sich um einen Standardstream handelt. andernfalls **`false`** .

*Richting*\
Ein zu kopierendes `basic_istream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Basisklasse durch Aufrufen von [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)` . Außerdem wird null in der Extraktionsanzahl gespeichert. Weitere Informationen zu dieser Extraktions Anzahl finden Sie im Abschnitt "Hinweise" in der Übersicht über [basic_istream-Klasse](../standard-library/basic-istream-class.md) .

Der zweite Konstruktor initialisiert die Basisklasse durch Aufrufen von `move(right)`. Außerdem speichert Sie `right.gcount()` in der Extraktions Anzahl und speichert NULL in der Extraktions Anzahl für * Right * *.

### <a name="example"></a>Beispiel

Weitere Informationen zu Eingabestreams finden Sie im Beispiel für [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream).

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream:: Gcount

Gibt die Anzahl von Zeichen zurück, die bei der letzten unformatierten Eingabe gelesen wurden.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Extraktionsanzahl.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [basic_istream::get](#get), um nicht formatierte Zeichen zu lesen.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream:: Get

Liest mindestens ein Zeichen aus dem Eingabestream.

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl der zu lesenden Zeichen aus *strbuf*.

*Trennzeichen*\
Das Zeichen, das den Lesevorgang beenden soll, wenn es vor *count*gefunden wurde.

*SRT*\
Eine Zeichenfolge, in die geschrieben werden soll.

*Ch*\
Ein Zeichen, das abgerufen werden soll.

*strbuf*\
Ein Puffer, in den geschrieben werden soll.

### <a name="return-value"></a>Rückgabewert

Die parameterlose Form von „get“ gibt das gelesene Element als ganze Zahl oder Ende der Datei zurück. In den restlichen Formularen wird der Datenstrom (*) zurückgegeben **`this`** .

### <a name="remarks"></a>Bemerkungen

Die erste nicht formatierte Eingabe Funktion extrahiert ein Element, sofern möglich, wie bei der Rückgabe von `rdbuf->sbumpc` . Andernfalls wird zurückgegeben `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) . Wenn die Funktion kein Element extrahiert, ruft Sie auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` .

Die zweite Funktion extrahiert das [int_type](../standard-library/basic-ios-class.md#int_type)-Element `meta` auf die gleiche Weise. Wenn `meta` gleich `traits_type::eof` ist, ruft die-Funktion auf `setstate(failbit)` . Andernfalls speichert es `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` in *ch*. Die Funktion gibt __* this__zurück.

Die dritte Funktion gibt zurück `get(str, count, widen('\n'))` .

Die vierte Funktion extrahiert bis zu `count - 1` Elemente und speichert Sie in dem Array, beginnend bei *Str*. Sie speichert `char_type` immer nach den extrahierten Elementen, die sie speichert. In der Reihenfolge der Tests hält die Extrahierung hier an:

- Am Ende der Datei.

- Nachdem die Funktion ein Element extrahiert hat, das mit dem *Trenn*Zeichen identisch ist. In diesem Fall wird das Element wieder in die gesteuerte Sequenz eingefügt.

- Nachdem die Funktion Elemente extrahiert hat `count - 1` .

Wenn die Funktion keine Elemente extrahiert, ruft Sie auf `setstate(failbit)` . In jedem Fall wird __* this__zurückgegeben.

Die fünfte Funktion gibt zurück `get(strbuf, widen('\n'))` .

Die sechste Funktion extrahiert Elemente und fügt sie in *strbuf* ein. Die Extraktion wird am Dateiende oder auf einem Element beendet, das gleich dem *Trenn*Zeichen entspricht, das nicht extrahiert wird. Sie hält ebenfalls an, ohne die jeweiligen Elemente zu extrahieren, wenn bei einer Einfügung ein Fehler auftritt, oder löst eine Ausnahme aus (die aufgefangen, aber nicht erneut ausgelöst wird). Wenn die Funktion keine Elemente extrahiert, ruft Sie auf `setstate(failbit)` . In jedem Fall gibt die Funktion __* this__zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream:: getline

Ruft eine Zeile aus dem Eingabestream ab.

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl der zu lesenden Zeichen aus *strbuf*.

*Trennzeichen*\
Das Zeichen, das den Lesevorgang beenden soll, wenn es vor *count*gefunden wurde.

*SRT*\
Eine Zeichenfolge, in die geschrieben werden soll.

### <a name="return-value"></a>Rückgabewert

Der Stream (__* this__).

### <a name="remarks"></a>Bemerkungen

Die erste dieser nicht formatierten Eingabefunktionen gibt zurück `getline(str, count, widen('\n'))` .

Die zweite Funktion extrahiert bis zu `count - 1` Elemente und speichert Sie in dem Array, beginnend bei *Str*. Das Abschlusszeichen der Zeichenfolge wird immer nach jedem Element gespeichert, das sie speichert. In der Reihenfolge der Tests hält die Extrahierung hier an:

- Am Ende der Datei.

- Nachdem die Funktion ein Element extrahiert hat, das mit dem *Trenn*Zeichen identisch ist. In diesem Fall wird das Element nicht zurückgesetzt, und es wird nicht an die gesteuerte Sequenz angefügt.

- Nachdem die Funktion Elemente extrahiert hat `count - 1` .

Wenn die Funktion keine Elemente oder `count - 1` Elemente extrahiert, ruft Sie auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . In jedem Fall wird __* this__zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream:: Ignore

Bewirkt, dass eine Anzahl von Elementen ab der aktuellen Leseposition übersprungen werden.

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl von Elementen, die ab der aktuellen Leseposition übersprungen werden sollen.

*Trennzeichen*\
Das Element, das bei Auftreten vor count bewirkt, dass `ignore` zurückgegeben wird und zulässt, dass alle Elemente nach dem *Trenn* Zeichen gelesen werden.

### <a name="return-value"></a>Rückgabewert

Der Stream (__* this__).

### <a name="remarks"></a>Bemerkungen

Die nicht formatierte Eingabe Funktion extrahiert zum *zählen* von Elementen und verwirft Sie. Wenn *count* der Wert ist `numeric_limits<int>::max` , wird der Wert jedoch beliebig groß. Die Extraktion hält früh am Ende der Datei oder auf einem Element an `Ch` , das `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` gleich dem *Trenn* Zeichen entspricht (das ebenfalls extrahiert wird). Die Funktion gibt __* this__zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>grundlegender \_ IStream:: Operator>>

Ruft eine Funktion für den Eingabestream auf oder liest formatierte Daten aus dem Eingabestream.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>Parameter

*PFN*\
Ein Funktionszeiger.

*strbuf*\
Ein Objekt des Typs `stream_buf`.

*ster*\
Der Wert, der aus dem Stream gelesen werden soll.

### <a name="return-value"></a>Rückgabewert

Der Stream (__* this__).

### <a name="remarks"></a>Bemerkungen

Der Header \<istream> definiert außerdem mehrere globale Extraktionsoperatoren. Weitere Informationen finden Sie unter [Operator>>  ( \<istream> )](../standard-library/istream-operators.md#op_gt_gt).

Die erste Member-Funktion stellt sicher, dass ein Ausdruck des Formulars `istr >> ws` aufruft [`ws`](../standard-library/istream-functions.md#ws) `(istr)` , und gibt dann __* this__zurück. Mit den zweiten und dritten Funktionen wird sichergestellt, dass sich andere Manipulatoren wie [`hex`](../standard-library/ios-functions.md#hex) Verhalten ähnlich verhalten. Die verbleibenden Funktionen sind die formatierten Eingabefunktionen.

Die Funktion:

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

extrahiert Elemente, wenn der Wert von " *Unbuf* " kein NULL-Zeiger ist, und fügt Sie in " *strebuf*" ein Die Extrahierung hält am Ende der Datei an. Sie hält ebenfalls an, ohne die jeweiligen Elemente zu extrahieren, wenn eine Einfügung fehlschlägt, oder löst eine Ausnahme aus (die aufgefangen, aber nicht erneut ausgelöst wird). Wenn die Funktion keine Elemente extrahiert, ruft Sie auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . In jedem Fall gibt die Funktion __* this__zurück.

Die Funktion:

```cpp
basic_istream& operator>>(bool& val);
```

extrahiert ein Feld und konvertiert es in einen booleschen Wert, indem aufgerufen wird [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `), Init(0), *this, getloc, val)` . Hier `InIt` ist als definiert [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>` . Die Funktion gibt __* this__zurück.

Jede der Funktionen:

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

Extrahieren Sie ein Feld, und konvertieren Sie es in einen numerischen Wert, indem Sie aufrufen `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)` . Hier `InIt` ist als definiert `istreambuf_iterator<Char_T, Tr>` , und *Val* hat bei Bedarf den Typ **`long`** , **`unsigned long`** oder **`void`** <strong>\*</strong> .

Wenn der konvertierte Wert nicht als Typ von *Val*dargestellt werden kann, ruft die Funktion auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . In jedem Fall gibt die Funktion __* this__zurück.

Jede der Funktionen:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

Extrahieren Sie ein Feld, und konvertieren Sie es in einen numerischen Wert, indem Sie aufrufen `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)` . Hier `InIt` ist als definiert `istreambuf_iterator<Char_T, Tr>` , und *Val* hat den Typ **`double`** oder nach **`long double`** Bedarf.

Wenn der konvertierte Wert nicht als Typ von *Val*dargestellt werden kann, ruft die Funktion auf `setstate(failbit)` . In jedem Fall wird __* this__zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream:: Operator =

Weist den `basic_istream` auf der rechten Seite des Operators diesem Objekt zu. Dabei handelt es sich um eine Verschiebungs Zuweisung mit einem `rvalue` Verweis, der keine Kopie hinterlässt.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `rvalue`-Verweis auf ein `basic_ifstream`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt __* this__zurück.

### <a name="remarks"></a>Bemerkungen

Der Member-Operator Ruft auf `swap(right)` .

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream::p EEK

Gibt das nächste zu lesende Zeichen zurück.

```cpp
int_type peek();
```

### <a name="return-value"></a>Rückgabewert

Das nächste zu lesende Zeichen.

### <a name="remarks"></a>Bemerkungen

Die nicht formatierte Eingabe Funktion extrahiert, wenn möglich, ein Element, wie bei der Rückgabe von `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc) . Andernfalls wird zurückgegeben `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) .

### <a name="example"></a>Beispiel

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream::p utback

Schreibt ein angegebenes Zeichen in den Stream.

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parameter

*Ch*\
Ein Zeichen, das im Stream wiederhergestellt werden soll.

### <a name="return-value"></a>Rückgabewert

Der Stream (__* this__).

### <a name="remarks"></a>Bemerkungen

Die [nicht formatierte Eingabe Funktion](../standard-library/basic-istream-class.md) stellt, wenn *möglich, den zurück,* als ob durch Aufrufen von [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc) . Wenn `rdbuf` ein NULL-Zeiger ist oder wenn der Aufruf von `sputbackc` zurückgibt `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) , ruft die Funktion auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` . In jedem Fall wird __* this__zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream:: Read

Liest eine angegebene Anzahl von Zeichen aus dem Stream und speichert diese in einem Array.

Diese Methode ist potenziell unsicher, da sie darauf basiert, dass der Aufrufer überprüft, ob die übergebenen Werte korrekt sind.

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*SRT*\
Das Array, in dem die Zeichen gelesen werden sollen.

*Countdown*\
Die Anzahl der zu lesenden Zeichen.

### <a name="return-value"></a>Rückgabewert

Der Stream ( **`*this`** ).

### <a name="remarks"></a>Bemerkungen

Die nicht formatierte Eingabe Funktion extrahiert nach oben, um Elemente zu *zählen* , und speichert Sie in dem Array, beginnend bei *Str*. Die Extraktion hält früh am Ende der Datei an. in diesem Fall ruft die Funktion auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . In jedem Fall wird __* this__zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream:: Read some

Liest die angegebene Anzahl von Zeichenwerten.

Diese Methode ist potenziell unsicher, da sie darauf basiert, dass der Aufrufer überprüft, ob die übergebenen Werte korrekt sind.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*SRT*\
Das Array, in dem `readsome` die gelesenen Zeichen speichert.

*Countdown*\
Die Anzahl der zu lesenden Zeichen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der tatsächlich gelesenen Zeichen [`gcount`](#gcount) .

### <a name="remarks"></a>Bemerkungen

Diese nicht formatierte Eingabe Funktion extrahiert zum *zählen* von Elementen aus dem Eingabestream und speichert Sie im Array *Str*.

Diese Funktion wartet nicht auf Eingabe. Sie liest alle verfügbaren Daten.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream:: seekg

Verschiebt die Leseposition in einem Stream.

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parameter

*POS*\
Die absolute Position, an die der Lesezeiger verschoben werden soll.

*abgeschrieben*\
Ein Offset zum Verschieben des Lese Zeigers in Relation zur *Methode*.

*gewissermaßen*\
Eine der [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir)-Enumerationen.

### <a name="return-value"></a>Rückgabewert

Der Stream (__* this__).

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion führt eine absolute, die zweite Memberfunktion eine relative Suche durch.

> [!NOTE]
> Verwenden Sie die zweite Memberfunktion nicht mit Textdateien, da Standard C++ keine relativen Suchen in Textdateien unterstützt.

Wenn [`fail`](../standard-library/basic-ios-class.md#fail) false ist, ruft die erste Member-Funktion `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)` für ein `pos_type` temporäres Objekt auf `newpos` . Wenn `fail` false ist, ruft die zweite Funktion auf `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)` . In beiden Fällen, wenn `(off_type)newpos == (off_type)(-1)` (der Positionierungs Vorgang fehlschlägt), ruft die Funktion auf `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . Beide Funktionen geben __* this__zurück.

Wenn [`fail`](../standard-library/basic-ios-class.md#fail) den Wert true hat, führen die Element Funktionen keine Aktion aus.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream:: Sentry

Die geschachtelte Klasse beschreibt ein Objekt, dessen Deklaration die formatierte und unformatierte Eingabe strukturiert.

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>Bemerkungen

Wenn `_Istr.` [`good`](../standard-library/basic-ios-class.md#good) den Wert true hat, wird der Konstruktor:

- Ruft auf, `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) `->` [`flush`](../standard-library/basic-ostream-class.md#flush) Wenn `_Istr.tie` kein NULL-Zeiger ist.

- Ruft effektiv auf, [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` Wenn ungleich 0 ( `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) null) ist.

Wenn nach einer solchen Vorbereitung `_Istr.good` false ist, ruft der Konstruktor auf `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . In jedem Fall speichert der Konstruktor den von zurückgegebenen Wert `_Istr.good` in `status` . Ein späterer-Befehl, der `operator bool` diesen gespeicherten Wert übermittelt.

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream:: Swap

Tauscht den Inhalt von zwei `basic_istream`-Objekten aus.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein lvalue-Verweis auf ein `basic_istream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion Ruft auf [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)` . Außerdem wird die Extraktions Anzahl mit der Extraktions Anzahl für " *right*" ausgetauscht.

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream:: Sync

Synchronisiert das zugeordnete Eingabegerät des Streams mit dem Puffer des Streams.

```cpp
int sync();
```

### <a name="return-value"></a>Rückgabewert

Wenn [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) ein NULL-Zeiger ist, gibt die Funktion-1 zurück. Andernfalls wird aufgerufen `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync) . Wenn dieser Aufruf-1 zurückgibt, ruft die Funktion-1 auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` und gibt "-1" zurück. Andernfalls wird von der Funktion null zurückgegeben.

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream:: Tellg

Meldet die aktuelle Leseposition im Stream.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Position in dem Stream.

### <a name="remarks"></a>Bemerkungen

Wenn [`fail`](../standard-library/basic-ios-class.md#fail) false ist, gibt die Member-Funktion zurück [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)` . Andernfalls wird `pos_type(-1)`zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream:: unget

Schreibt das zuletzt gelesene Zeichen zurück in den Stream.

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>Rückgabewert

Der Stream (__* this__).

### <a name="remarks"></a>Bemerkungen

Die [nicht formatierte Eingabe Funktion](../standard-library/basic-istream-class.md) gibt das vorherige Element im Stream zurück, wenn dies möglich ist, als ob durch Aufrufen von `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc) . Wenn [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) ein NULL-Zeiger ist oder wenn der Aufruf von `sungetc` zurückgibt `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof) , ruft die Funktion auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` . In jedem Fall wird __* this__zurückgegeben.

Informationen dazu, wie `unget` fehlschlagen kann, finden Sie unter [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc) .

### <a name="example"></a>Beispiel

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
