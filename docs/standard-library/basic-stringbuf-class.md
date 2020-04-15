---
title: basic_stringbuf-Klasse
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringbuf
- sstream/std::basic_stringbuf::allocator_type
- sstream/std::basic_stringbuf::char_type
- sstream/std::basic_stringbuf::int_type
- sstream/std::basic_stringbuf::off_type
- sstream/std::basic_stringbuf::pos_type
- sstream/std::basic_stringbuf::traits_type
- sstream/std::basic_stringbuf::overflow
- sstream/std::basic_stringbuf::pbackfail
- sstream/std::basic_stringbuf::seekoff
- sstream/std::basic_stringbuf::seekpos
- sstream/std::basic_stringbuf::str
- sstream/std::basic_stringbuf::underflow
helpviewer_keywords:
- std::basic_stringbuf [C++]
- std::basic_stringbuf [C++], allocator_type
- std::basic_stringbuf [C++], char_type
- std::basic_stringbuf [C++], int_type
- std::basic_stringbuf [C++], off_type
- std::basic_stringbuf [C++], pos_type
- std::basic_stringbuf [C++], traits_type
- std::basic_stringbuf [C++], overflow
- std::basic_stringbuf [C++], pbackfail
- std::basic_stringbuf [C++], seekoff
- std::basic_stringbuf [C++], seekpos
- std::basic_stringbuf [C++], str
- std::basic_stringbuf [C++], underflow
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
ms.openlocfilehash: 578d0e31e08f3e077a908c4344f77da5495df40d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364886"
---
# <a name="basic_stringbuf-class"></a>basic_stringbuf-Klasse

Beschreibt einen die Übertragung zu und aus einer Sequenz von in einem Arrayobjekt gespeicherten Elementen von Elementen des Typs `Elem` steuernden Streampuffer, dessen Zeichenmerkmale durch die Klasse `Tr` ermittelt werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parameter

*Alloc*\
Die Zuweisungsklasse.

*Elem*\
Der Typ des grundlegenden Elements der Zeichenfolge.

*Tr*\
Die für das grundlegende Element der Zeichenfolge spezialisierten Zeichenmerkmale.

## <a name="remarks"></a>Bemerkungen

Das Objekt wird reserviert, erweitert und freigegeben, sofern erforderlich, um Änderungen in der Sequenz zu berücksichtigen.

Ein Objekt der Klasse basic_stringbuf< `Elem`, `Tr`, `Alloc`> speichert eine Kopie des Arguments `ios_base::`[openmode](../standard-library/ios-base-class.md#openmode) aus seinem Konstruktor als seinen `stringbuf`-Modus **mode**:

- Wenn `mode & ios_base::in` ungleich 0 ist, kann auf den Eingabepuffer zugegriffen werden. Weitere Informationen finden Sie unter [basic_streambuf-Klasse](../standard-library/basic-streambuf-class.md).

- Wenn `mode & ios_base::out` ungleich 0 ist, kann auf den Ausgabepuffer zugegriffen werden.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Konstruiert ein Objekt vom Typ `basic_stringbuf`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|BESCHREIBUNG|
|-|-|
|[allocator_type](#allocator_type)|Der Typ ist ein Synonym für den Vorlagenparameter *Alloc*.|
|[char_type](#char_type)|Verknüpft einen Typnamen mit dem Vorlagenparameter *Elem*.|
|[int_type](#int_type)|Stellt diesen `basic_filebuf`Typ innerhalb des Gültigkeitsbereichs von dem Typ desselben Namens im *Tr-Bereich* in die Höhe.|
|[off_type](#off_type)|Stellt diesen `basic_filebuf`Typ innerhalb des Gültigkeitsbereichs von dem Typ desselben Namens im *Tr-Bereich* in die Höhe.|
|[pos_type](#pos_type)|Stellt diesen `basic_filebuf`Typ innerhalb des Gültigkeitsbereichs von dem Typ desselben Namens im *Tr-Bereich* in die Höhe.|
|[traits_type](#traits_type)|Verknüpft einen Typnamen mit dem Vorlagenparameter *Tr*.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Überlauf](#overflow)|Eine geschützte virtuelle Funktion, die aufgerufen werden kann, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.|
|[pbackfail](#pbackfail)|Die geschützte virtuelle Memberfunktion versucht, ein Element zurück in den Eingabepuffer zu versetzen und es dann zum aktuellen Element zu ernennen (wird mit dem nächsten Zeiger darauf gezeigt).|
|[seekoff](#seekoff)|Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[seekpos](#seekpos)|Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[Str](#str)|Legt den Text in einem Zeichenfolgenpuffer fest, ohne die Schreibposition zu ändern, oder ruft ihn ab.|
|swap||
|[Unterlauf](#underflow)|Die geschützte virtuelle Memberfunktion versucht, das aktuelle Element aus dem Eingabestream zu extrahieren.|

## <a name="requirements"></a>Anforderungen

**Header:** \<sstream>

**Namespace:** std

## <a name="basic_stringbufallocator_type"></a><a name="allocator_type"></a>basic_stringbuf::allocator_type

Der Typ ist ein Synonym für den Vorlagenparameter *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbufbasic_stringbuf"></a><a name="basic_stringbuf"></a>basic_stringbuf::basic_stringbuf

Konstruiert ein Objekt vom Typ `basic_stringbuf`.

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_mode*\
Eine der Enumerationen in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Ein Objekt vom Typ [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert einen NULL-Zeiger in allen Zeigern, die den Eingabe- und Ausgabepuffer steuern. Weitere Informationen finden Sie im Abschnitt „Hinweise“ unter [basic_streambuf-Klasse](../standard-library/basic-streambuf-class.md). Es speichert auch *_Mode* als Stringbuf-Modus. Weitere Informationen finden Sie im Abschnitt „Hinweise“ unter [basic_stringbuf-Klasse](../standard-library/basic-stringbuf-class.md).

Der zweite Konstruktor weist eine Kopie der Sequenz zu, die vom Zeichenfolgenobjekt *str*gesteuert wird. Wenn `_Mode & ios_base::in` ungleich null ist, wird festgelegt, dass der Eingabepuffer den Lesevorgang am Anfang der Sequenz beginnt. Wenn `_Mode & ios_base::out` ungleich null ist, wird festgelegt, dass der Ausgabepuffer den Schreibvorgang am Anfang der Sequenz beginnt. Es speichert auch *_Mode* als Stringbuf-Modus. Weitere Informationen finden Sie im Abschnitt „Hinweise“ unter [basic_stringbuf-Klasse](../standard-library/basic-stringbuf-class.md).

## <a name="basic_stringbufchar_type"></a><a name="char_type"></a>basic_stringbuf::char_type

Verknüpft einen Typnamen mit dem Vorlagenparameter *Elem*.

```cpp
typedef Elem char_type;
```

## <a name="basic_stringbufint_type"></a><a name="int_type"></a>basic_stringbuf::int_type

Stellt diesen Typ innerhalb des Basic_filebuf-Bereichs dem Typ `Tr` desselben Namens im Bereich gleich.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_stringbufoff_type"></a><a name="off_type"></a>basic_stringbuf::off_type

Stellt diesen Typ innerhalb des Basic_filebuf-Bereichs dem Typ `Tr` desselben Namens im Bereich gleich.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_stringbufoverflow"></a><a name="overflow"></a>basic_stringbuf::Überlauf

Eine geschützte virtuelle Funktion, die aufgerufen werden kann, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder `traits_type::eof`.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich abgeschlossen werden kann, wird `traits_type::eof` zurückgegeben. Andernfalls wird **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*) zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn * \_Meta* nicht gleich **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)vergleicht, versucht die geschützte virtuelle Memberfunktion, das Element **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) in den Ausgabepuffer einzufügen. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn eine Schreibposition verfügbar ist, kann das Element in der Schreibposition gespeichert werden, und der nächste Zeiger für den Ausgabepuffer kann inkrementiert werden.

- Eine Schreibposition kann verfügbar gemacht werden, indem neuer oder zusätzlicher Speicher für den Ausgabepuffer zugewiesen wird. Das Erweitern des Ausgabepuffers erweitert auf diese Weise auch alle zugewiesenen Eingabepuffer.

## <a name="basic_stringbufpbackfail"></a><a name="pbackfail"></a>basic_stringbuf::pbackfail

Die geschützte virtuelle Memberfunktion versucht, ein Element im Eingabepuffer wiederherzustellen und es dann zum aktuellen Element zu machen (der nächste Zeiger zeigt auf das Element).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder `traits_type::eof`.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich abgeschlossen werden kann, wird `traits_type::eof` zurückgegeben. Andernfalls wird **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*) zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn *_Meta* gleich **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)vergleicht, ist das element, das zurückgedrängt werden soll, effektiv das Element, das sich bereits im Stream vor dem aktuellen Element befindet. Andernfalls wird dieses Element durch **Byte** = **ersetzt traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). Ein Element kann auf verschiedene Arten durch die Funktion wiederhergestellt werden:

- Wenn eine Position zur Wiederherstellung verfügbar ist, und das Element, das dort gespeichert ist, „byte“ entspricht, kann der nächste Zeiger für den Eingabepuffer verringert werden.

- Wenn eine Position zur Wiederherstellung verfügbar ist, und der stringbuf-Modus zulässt, dass die Sequenz geändert wird ( **mode & ios_base::out** ist ungleich null), kann „byte“ in der Position zur Wiederherstellung gespeichert werden und den nächsten Zeiger für den Eingabepuffer verringern.

## <a name="basic_stringbufpos_type"></a><a name="pos_type"></a>basic_stringbuf::pos_type

Stellt diesen Typ innerhalb des Basic_filebuf-Bereichs dem Typ `Tr` desselben Namens im Bereich gleich.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_stringbufseekoff"></a><a name="seekoff"></a>basic_stringbuf::seekoff

Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_off*\
Die Position, die gesucht werden soll, relativ zu *_Way*. Weitere Informationen finden Sie unter [basic_stringbuf::off_type](#off_type).

*_Way*\
Der Startpunkt für Offsetvorgänge. Mögliche Werte sind unter [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) aufgeführt.

*_mode*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden. Weitere Informationen finden Sie unter [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Rückgabewert

Gibt die neue Position oder eine ungültige Streamposition zurück.

### <a name="remarks"></a>Bemerkungen

Für ein Objekt der Klasse `basic_stringbuf<Elem, Tr, Alloc>` besteht eine Streamposition nur aus einem Streamoffset. Das Offset Null legt das erste Element der kontrollierten Sequenz fest.

Die neue Position wird wie folgt bestimmt:

- `_Way`  == Wenn `ios_base::beg`, ist die neue Position der Anfang des Streams plus *_Off*.

- `_Way`  == Wenn `ios_base::cur`, ist die neue Position die aktuelle Streamposition plus *_Off*.

- `_Way`  == Wenn `ios_base::end`, ist die neue Position das Ende des Streams plus *_Off*.

Wenn `_Mode & ios_base::in` ungleich null ist, ändert die Funktion die nächste Position, die im Eingabepuffer gelesen werden soll. Wenn `_Mode & ios_base::out` ungleich null ist, ändert die Funktion die nächste Position, die im Ausgabepuffer gelesen werden soll. Damit ein Stream betroffen wird, muss ein Puffer bestehen. Damit eine Positionierung erfolgreich ist, muss die resultierende Streamposition innerhalb der gesteuerten Sequenz liegen. Wenn sich die Funktion auf beide `ios_base::beg` `ios_base::end` Streampositionen auswirkt, muss *_Way* sein oder und beide Streams werden am gleichen Element positioniert. Andernfalls (oder wenn keine Position betroffen ist) tritt bei der Positionierung ein Fehler ein.

Wenn die Funktion erfolgreich eine der beiden Streampositionen ändern kann, gibt sie die resultierende Streamposition zurück. Andernfalls schlägt sie fehl und gibt eine ungültige Streamposition zurück.

## <a name="basic_stringbufseekpos"></a><a name="seekpos"></a>basic_stringbuf::seekpos

Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_Sp*\
Die Position, nach der gesucht werden soll.

*_mode*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich eine der beiden Streampositionen ändern kann, gibt sie die resultierende Streamposition zurück. Andernfalls schlägt sie fehl und gibt eine ungültige Streamposition zurück. Vergleichen Sie den Rückgabewert mit `pos_type(off_type(-1))`, um festzustellen, ob die Streamposition ungültig ist.

### <a name="remarks"></a>Bemerkungen

Für ein Objekt der Klasse basic_stringbuf< **Elem**, **Tr**, `Alloc`> besteht eine Streamposition bloß aus einem Streamoffset. Das Offset Null legt das erste Element der kontrollierten Sequenz fest. Die neue Position wird von _ *Sp* bestimmt.

Wenn **mode & ios_base::in** ungleich null ist, ändert die Funktion die nächste Position, die in den Eingabepuffer gelesen werden soll. Wenn **mode & ios_base::out** ungleich null ist, ändert die Funktion die nächste Position, die in den Ausgabepuffer geschrieben werden soll. Damit ein Stream betroffen wird, muss ein Puffer bestehen. Damit eine Positionierung erfolgreich ist, muss die resultierende Streamposition innerhalb der gesteuerten Sequenz liegen. Andernfalls (oder wenn keine Position betroffen ist) tritt bei der Positionierung ein Fehler ein.

## <a name="basic_stringbufstr"></a><a name="str"></a>basic_stringbuf::str

Legt den Text in einem Zeichenfolgenpuffer fest, ohne die Schreibposition zu ändern, oder ruft ihn ab.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parameter

*_Newstr*\
Die neue Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Gibt ein Objekt der Klasse [basic_string](../standard-library/basic-string-class.md)\< **Elem**, **Tr**, Alloc **>,** zurück, dessen gesteuerte Sequenz eine Kopie der von **\*this** gesteuerten Sequenz ist.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion gibt ein Objekt der Klasse basic_string< **Elem**, **Tr**, `Alloc`> zurück, dessen gesteuerte Sequenz eine Kopie der von **\*this** gesteuerten Sequenz ist. Die kopierte Sequenz ist vom Modus „stored stringbuf“ abhängig:

- Wenn **mode & ios_base::out** ungleich null ist, und ein Ausgabepuffer besteht, ist die Sequenz der gesamte Ausgabepuffer ( [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase)-Elemente, die mit `pbase` beginnen).

- Wenn **mode & ios_base::in** ungleich null ist, und ein Eingabepuffer besteht, ist die Sequenz der gesamte Eingabepuffer ( [egptr](../standard-library/basic-streambuf-class.md#egptr) - [back](../standard-library/basic-streambuf-class.md#eback)-Elemente, die mit `eback` beginnen).

- Andernfalls ist die kopierte Sequenz leer.

Die zweite Memberfunktion weist jede Sequenz ** \*** auf, die derzeit von dieser gesteuert wird. Anschließend wird eine Kopie der sequenziums zugewiesen, die von *_Newstr*gesteuert wird. Wenn **mode & ios_base::in** ungleich null ist, wird festgelegt, dass der Eingabepuffer den Lesevorgang am Anfang der Sequenz beginnt. Wenn **mode & ios_base::out** ungleich null ist, wird festgelegt, dass der Ausgabepuffer den Schreibvorgang am Anfang der Sequenz beginnt.

### <a name="example"></a>Beispiel

```cpp
// basic_stringbuf_str.cpp
// compile with: /EHsc
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   basic_string<char> i( "test" );
   stringstream ss;

   ss.rdbuf( )->str( i );
   cout << ss.str( ) << endl;

   ss << "z";
   cout << ss.str( ) << endl;

   ss.rdbuf( )->str( "be" );
   cout << ss.str( ) << endl;
}
```

```Output
test
zest
be
```

## <a name="basic_stringbuftraits_type"></a><a name="traits_type"></a>basic_stringbuf::traits_type

Verknüpft einen Typnamen mit dem Vorlagenparameter *Tr*.

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Bemerkungen

Der Typ stellt ein Synonym für den Vorlagenparameter *Tr* dar.

## <a name="basic_stringbufunderflow"></a><a name="underflow"></a>basic_stringbuf::Unterfluss

Die geschützte virtuelle Funktion versucht, das aktuelle Element aus dem Eingabestream zu extrahieren.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich sein kann, gibt sie **traits_type zurück::**[eof](../standard-library/char-traits-struct.md#eof). Andernfalls wird das aktuelle Element, das konvertiert wurde, in den Eingabestream zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion versucht, `byte` das aktuelle Element aus dem Eingabepuffer zu extrahieren, die aktuelle Streamposition vorzuverlegen und das Element als **traits_type zurück:**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **Byte**). Sie kann dies auf eine Weise tun: Wenn `byte` eine Leseposition verfügbar ist, nimmt sie als das in der Leseposition gespeicherte Element und den nächsten Zeiger für den Eingabepuffer voran.

## <a name="basic_streambufswap"></a><a name="swap"></a>basic_streambuf::swap

Vertauscht den Inhalt dieses Zeichenfolgenpuffers mit einem anderen Zeichenfolgenpuffer.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parameter

*Andere*\
Der „basic_stringbuf“, dessen Inhalt mit diesem „basic_stringbuf“ getauscht wird.

### <a name="remarks"></a>Bemerkungen

## <a name="basic_stringbufoperator"></a><a name="op_eq"></a>basic_stringbuf::operator=

Weist den Inhalt von basic_stringbuf auf der rechten Seite des Operators dem basic_stringbuf auf der linken Seite zu.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parameter

*Andere*\
Ein basic_stringbuf, dessen Inhalt, einschließlich Gebietsschema-Merkmalen, dem Stringbuf auf der linken Seite des Operators zugewiesen wird.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
