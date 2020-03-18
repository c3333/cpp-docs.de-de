---
title: basic_streambuf-Klasse
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
ms.openlocfilehash: 1b43c2291499af87f2be1e5bec25717a30c28bfd
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424026"
---
# <a name="basic_streambuf-class"></a>basic_streambuf-Klasse

Beschreibt eine abstrakte Basisklasse für das Ableiten eines Streampuffers, die die Übertragung von Elementen an eine bestimmte und von einer bestimmten Darstellung eines Streams steuert.

## <a name="syntax"></a>Syntax

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Parameter

*Elem* -\
Ein [char_type](#char_type).

*TR* -\
Der [traits_type](#traits_type) der Zeichen.

## <a name="remarks"></a>Hinweise

Die Klassen Vorlage beschreibt eine abstrakte Basisklasse für die Ableitung eines Streampuffers, der die Übertragung von Elementen in eine und aus einer bestimmten Darstellung eines Streams steuert. Ein Objekt der Klasse `basic_streambuf` unterstützt die Steuerung eines Streams mit Elementen des Typs *TR*, auch bekannt als [char_type](#char_type), dessen Zeichen Merkmale durch die Klasse [Char_traits](../standard-library/char-traits-struct.md)bestimmt werden, auch bekannt als [Traits_type](#traits_type).

Jeder Streampuffer steuert konzeptuell zwei unabhängige Streams: einen für Extraktionen (Eingabe) und einen für Einfügungen (Ausgabe). Eine bestimmte Darstellung kann jedoch den Zugriff auf einen oder beide Streams unmöglich machen. In der Regel besteht eine bestimmte Beziehung zwischen den beiden Streams. Was Sie in den Ausgabestream eines [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>-Objekts einfügen, extrahieren Sie beispielsweise später aus dem Eingabestream. Wenn Sie einen Stream eines [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>-Objekts positionieren, positionieren Sie den anderen Stream entsprechend.

Die öffentliche Schnittstelle zu Klassen Vorlagen `basic_streambuf` stellt die Vorgänge bereit, die für alle Streampuffer, jedoch spezialisiert, gemeinsam sind. Die geschützte Schnittstelle stellt die Vorgänge bereit, die für die Verwendung einer bestimmten Darstellung eines Streams benötigt werden. Über die geschützten virtuellen Memberfunktionen können Sie das Verhalten eines abgeleiteten Streampuffers für eine bestimmte Darstellung eines Streams anpassen. Jeder abgeleitete Streampuffer in dieser Bibliothek beschreibt, wie er das Verhalten seiner geschützten virtuellen Memberfunktionen spezialisiert. Das Standardverhalten für die Basisklasse, das häufig darin besteht, nichts zu tun, wird in diesem Thema beschrieben.

Die verbleibenden geschützten Memberfunktionen steuern das Kopieren in und aus Speicher, der zum Puffern von Übertragungen in und aus Streams bereitgestellt wird. Ein Eingabepuffer ist z. B. durch folgende Merkmale charakterisiert:

- [eback](#eback), einen Zeiger auf den Anfang des Puffers.

- [gptr](#gptr), einen Zeiger auf das nächste zu lesende Element.

- [egptr](#egptr), einen Zeiger knapp hinter das Ende des Puffers.

Entsprechend ist ein Ausgabepuffer gekennzeichnet durch:

- [pbase](#pbase), einen Zeiger auf den Anfang des Puffers.

- [pptr](#pptr), einen Zeiger auf das nächste zu schreibende Element.

- [epptr](#epptr), einen Zeiger hinter das Ende des Puffers.

Für alle Puffer wird das folgende Protokoll verwendet:

- Wenn der Zeiger für das nächste Element NULL ist, ist kein Puffer vorhanden. Ansonsten zeigen alle drei Zeiger in dieselbe Sequenz. Sie können problemlos in Bezug auf die Reihenfolge verglichen werden.

- Wenn bei einem Ausgabepuffer der Zeiger für das nächste Element kleiner als der Endzeiger ist, können Sie ein Element an der vom Zeiger für das nächste Element bezeichneten Schreibposition speichern.

- Wenn bei einem Eingabepuffer der Zeiger für das nächste Element kleiner als der Endzeiger ist, können Sie ein Element an der vom Zeiger für das nächste Element bezeichneten Leseposition lesen.

- Wenn bei einem Eingabepuffer der Startzeiger kleiner als der Zeiger für das nächste Element ist, können Sie ein Element an der vom verminderten Zeiger für das nächste Element bezeichneten Position wiederherstellen.

Jede geschützte virtuelle Memberfunktion, die Sie für eine von `basic_streambuf`< `Elem`, `Tr`> abgeleitete Klasse schreiben, muss zur Erfüllung dieses Protokolls beitragen.

Ein Objekt der Klasse `basic_streambuf`< `Elem`, `Tr`> speichert die zuvor beschriebenen sechs Zeiger. Außerdem speichert es ein Gebietsschemaobjekt in einem Objekt vom Typ [locale](../standard-library/locale-class.md) für die mögliche Verwendung durch einen abgeleiteten Streampuffer.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[basic_streambuf](#basic_streambuf)|Konstruiert ein Objekt vom Typ `basic_streambuf`.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Verknüpft einen Typnamen mit dem `Elem`-Vorlagenparameter.|
|[int_type](#int_type)|Verknüpft einen Typnamen im Geltungsbereich von `basic_streambuf` mit dem `Elem`-Vorlagenparameter.|
|[off_type](#off_type)|Verknüpft einen Typnamen im Geltungsbereich von `basic_streambuf` mit dem `Elem`-Vorlagenparameter.|
|[pos_type](#pos_type)|Verknüpft einen Typnamen im Geltungsbereich von `basic_streambuf` mit dem `Elem`-Vorlagenparameter.|
|[traits_type](#traits_type)|Verknüpft einen Typnamen mit dem `Tr`-Vorlagenparameter.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|Beschreibung|
|-|-|
|[eback](#eback)|Eine geschützte Funktion, die einen Zeiger auf den Anfang des Eingabepuffers zurückgibt.|
|[egptr](#egptr)|Eine geschützte Funktion, die einen Zeiger direkt hinter das Ende des Eingabepuffers zurückgibt.|
|[epptr](#epptr)|Eine geschützte Funktion, die einen Zeiger direkt hinter das Ende des Ausgabepuffers zurückgibt.|
|[gbump](#gbump)|Eine geschützte Funktion, die dem nächsten Zeiger für den Eingabepuffer `count` hinzufügt.|
|[getloc](#getloc)|Ruft das Gebietsschema des `basic_streambuf`-Objekts ab.|
|[gptr](#gptr)|Eine geschützte Funktion, die einen Zeiger auf das nächste Element des Eingabepuffers zurückgibt.|
|[imbue](#imbue)|Eine geschützte virtuelle Funktion, die von [pubimbue](#pubimbue) aufgerufen wird.|
|[in_avail](#in_avail)|Gibt die Anzahl von Elementen zurück, die aus dem Puffer gelesen werden können.|
|[overflow](#overflow)|Eine geschützte virtuelle Funktion, die aufgerufen werden kann, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.|
|[pbackfail](#pbackfail)|Eine geschützte virtuelle Memberfunktion, die versucht, ein Element zurück in den Eingabestream zu versetzen und es dann zum aktuellen Element zu ernennen (es wird mit dem Zeiger für das nächste Element darauf gezeigt).|
|[pbase](#pbase)|Eine geschützte Funktion, die einen Zeiger auf den Anfang des Ausgabepuffers zurückgibt.|
|[pbump](#pbump)|Eine geschützte Funktion, die dem nächsten Zeiger für den Ausgabepuffer `count` hinzufügt.|
|[pptr](#pptr)|Eine geschützte Funktion, die einen Zeiger auf das nächste Element des Ausgabepuffers zurückgibt.|
|[pubimbue](#pubimbue)|Legt das Gebietsschema des `basic_streambuf`-Objekts fest.|
|[pubseekoff](#pubseekoff)|Ruft [seekoff](#seekoff) auf, eine geschützte virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben wird.|
|[pubseekpos](#pubseekpos)|Ruft [seekpos](#seekpos) auf, eine geschützte virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben wird, und die aktuelle Zeigerposition zurücksetzt.|
|[pubsetbuf](#pubsetbuf)|Ruft [setbuf](#setbuf) auf, eine geschützte virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben wird.|
|[pubsync](#pubsync)|Ruft [sync](#sync) auf, eine geschützte virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben wird, und den externen Stream für diesen Puffer aktualisiert.|
|[sbumpc](#sbumpc)|Liest das aktuelle Element, gibt es zurück und bewegt den Streamzeiger.|
|[seekoff](#seekoff)|Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[seekpos](#seekpos)|Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[setbuf](#setbuf)|Die geschützte virtuelle Memberfunktion führt einen für jeden abgeleiteten Streampuffer bestimmten Vorgang aus.|
|[setg](#setg)|Eine geschützte Funktion, die `_Gbeg` im Startzeiger, `_Gnext` im nächssten Zeiger und `_Gend` im Endzeiger für den Eingabepuffer speichert.|
|[setp](#setp)|Eine geschützte Funktion, die `_Pbeg` im Startzeiger und `_Pend` im Endzeiger für den Ausgabepuffer speichert.|
|[sgetc](#sgetc)|Gibt das aktuelle Element ohne Änderung der Position im Stream zurück.|
|[sgetn](#sgetn)|Gibt die Anzahl der gelesenen Elemente zurück.|
|[showmanyc](#showmanyc)|Eine geschützte virtuelle Memberfunktion, die die Anzahl von Zeichen zurückgibt, die aus dem Eingabestream extrahiert werden können, und stellt sicher, dass das Programm keiner unbegrenzten Wartezeit unterliegt.|
|[snextc](#snextc)|Liest das aktuelle Element und gibt das folgende Element zurück.|
|[sputbackc](#sputbackc)|Schreibt einen `char_type` in den Stream.|
|[sputc](#sputc)|Setzt ein Zeichen in den Stream.|
|[sputn](#sputn)|Setzt eine Zeichenfolge in den Stream.|
|[stossc](#stossc)|Verschiebt den Zeiger hinter das aktuelle Element im Stream.|
|[sungetc](#sungetc)|Ruft ein Zeichen aus dem Stream ab.|
|[swap](#swap)|Tauscht die Werte in diesem Objekt mit den Werten im bereitgestellten `basic_streambuf`-Objektparameter.|
|[sync](#sync)|Eine geschützte virtuelle Funktion, die versucht, die gesteuerten Streams mit zugehörigen externen Streams zu synchronisieren.|
|[uflow](#uflow)|Eine geschützte virtuelle Funktion, die das aktuelle Element aus dem Eingabestream extrahiert.|
|[underflow](#underflow)|Eine geschützte virtuelle Funktion, die das aktuelle Element aus dem Eingabestream extrahiert.|
|[xsgetn](#xsgetn)|Eine geschützte virtuelle Funktion, die Elemente aus dem Eingabestream extrahiert.|
|[xsputn](#xsputn)|Eine geschützte virtuelle Funktion, die Elemente in den Ausgabestream einfügt.|

### <a name="operators"></a>Operatoren

|Operator|Beschreibung|
|-|-|
|[operator=](#op_eq)|Weist die Werte dieses Objekts aus einem anderen `basic_streambuf`-Objekt zu.|

## <a name="requirements"></a>Voraussetzungen

**Header:** \<streambuf >

**Namespace:** std

## <a name="basic_streambuf"></a> basic_streambuf::basic_streambuf

Konstruiert ein Objekt vom Typ `basic_streambuf`.

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Ein lvalue-Verweis auf das `basic_streambuf`-Objekt, das dazu verwendet wird, Werte für dieses `basic_streambuf`-Objekt festzulegen.

### <a name="remarks"></a>Hinweise

Der erste geschützte Konstruktor speichert einen NULL-Zeiger in allen Zeigern, die den Eingabe- und Ausgabepuffer steuern. Er speichert auch `locale::classic` im locale-Objekt. Weitere Informationen finden Sie unter [locale::classic](../standard-library/locale-class.md#classic).

Der zweite geschützte Konstruktor kopiert die Zeiger und das Gebiets Schema von *Rechts*.

## <a name="char_type"></a> basic_streambuf::char_type

Verknüpft einen Typnamen mit dem Vorlagenparameter **Elem**.

```cpp
typedef Elem char_type;
```

## <a name="eback"></a> basic_streambuf::eback

Eine geschützte Funktion, die einen Zeiger auf den Anfang des Eingabepuffers zurückgibt.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Anfang des Eingabepuffers.

## <a name="egptr"></a> basic_streambuf::egptr

Eine geschützte Funktion, die einen Zeiger direkt hinter das Ende des Eingabepuffers zurückgibt.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger hinter das Ende des Eingabepuffers.

## <a name="epptr"></a> basic_streambuf::epptr

Eine geschützte Funktion, die einen Zeiger direkt hinter das Ende des Ausgabepuffers zurückgibt.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger hinter das Ende des Ausgabepuffers.

## <a name="gbump"></a> basic_streambuf::gbump

Eine geschützte Funktion, die dem nächsten Zeiger für den Eingabepuffer *count* hinzufügt.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Parameter

*Anzahl*\
Der Betrag, um den der Zeiger nach vorne verschoben werden soll.

## <a name="getloc"></a> basic_streambuf::getloc

Ruft das Gebietsschema des Objekts „basic_streambuf“ ab.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Rückgabewert

Das gespeicherte Gebietsschemaobjekt.

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [ios_base::getloc](../standard-library/ios-base-class.md#getloc).

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_getloc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="gptr"></a> basic_streambuf::gptr

Eine geschützte Funktion, die einen Zeiger auf das nächste Element des Eingabepuffers zurückgibt.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Element des Eingabepuffers.

## <a name="imbue"></a> basic_streambuf::imbue

Eine geschützte virtuelle Funktion, die von [pubimbue](#pubimbue) aufgerufen wird.

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parameter

*_Loc*\
Ein Verweis auf ein Gebietsschema.

### <a name="remarks"></a>Hinweise

Standardmäßig wird nichts unternommen.

## <a name="in_avail"></a> basic_streambuf::in_avail

Gibt die Anzahl von Elementen zurück, die aus dem Puffer gelesen werden können.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen, die aus dem Puffer gelesen werden können.

### <a name="remarks"></a>Hinweise

Wenn eine [Lese Position](../standard-library/basic-streambuf-class.md) verfügbar ist, gibt die Member-Funktion [Egptr](#egptr) - [GPTR](#gptr)zurück. Andernfalls wird [showmanyc](#showmanyc) zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_in_avail.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   char c;
   // cin's buffer is empty, in_avail will return 0
   cout << cin.rdbuf( )->in_avail( ) << endl;
   cin >> c;
   cout << cin.rdbuf( )->in_avail( ) << endl;
}
```

## <a name="int_type"></a> basic_streambuf::int_type

Ordnet einen Typnamen innerhalb des Bereichs von „basic_streambuf“ einem der Typen in einem Vorlagenparameter zu.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a> basic_streambuf::off_type

Ordnet einen Typnamen innerhalb des Bereichs von „basic_streambuf“ einem der Typen in einem Vorlagenparameter zu.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a> basic_streambuf::operator=

Weist die Werte dieses Objekts aus einem anderen `basic_streambuf`-Objekt zu.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Ein lvalue-Verweis auf das `basic_streambuf`-Objekt, das dazu verwendet wird, diesem Objekt Werte zuzuweisen.

### <a name="remarks"></a>Hinweise

Der geschützte Member-Operator kopiert von *Rechts* die Zeiger, die den Eingabepuffer und den Ausgabepuffer steuern. Außerdem speichert er `right.`[getloc()](#getloc) im `locale object`. Er gibt `*this` zurück.

## <a name="overflow"></a> basic_streambuf::overflow

Eine geschützte virtuelle Funktion, die aufgerufen werden kann, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder **traits_type::** [eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich ausgeführt werden kann, wird **traits_type::eof** zurückgegeben oder eine Ausnahme ausgelöst. Andernfalls wird **traits_type::** [not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*) zurückgegeben. Das Standardverhalten ist, **traits_type::eof** zurückzugeben.

### <a name="remarks"></a>Hinweise

Wenn *\_Meta* nicht gleich **traits_type:: EOF**ist, versucht die geschützte Funktion des virtuellen Members, das Element **traits_type::** [To_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_Meta*) in den Ausgabestream einzufügen. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn `write position` verfügbar ist, kann das Element in der Schreibposition gespeichert werden, und der nächste Zeiger für den Ausgabepuffer kann inkrementiert werden.

- Eine Schreibposition kann verfügbar gemacht werden, indem neuer oder zusätzlicher Speicher für den Ausgabepuffer zugewiesen wird.

- Eine Schreibposition kann auch dadurch verfügbar gemacht werden, dass einige oder alle Elemente zwischen dem Anfangszeiger und den folgenden Zeigern für den Ausgabepuffer an ein externes Ziel geschrieben werden.

Die virtuellen Funktionen „overflow“ sowie [sync](#sync) und [underflow](#underflow) legen die Eigenschaften der von „streambuf“ abgeleiteten Klasse fest. Jede abgeleitete Klasse kann „overflow“ anders implementieren, die Schnittstelle mit der aufrufenden Streamklasse bleibt allerdings gleich.

Die Funktion `overflow` wird am häufigsten von öffentlichen `streambuf`-Funktionen, wie z.B. `sputc` und `sputn` aufgerufen, wenn der Eingabebereich voll ist. Andere Klassen, darunter Streamklassen, können `overflow` jederzeit aufrufen.

Die Funktion verarbeitet die Zeichen im Eingabebereich zwischen den Zeigern `pbase` und `pptr` und initialisiert anschließend den Eingabebereich erneut. `overflow` (wenn `nCh` nicht `nCh` ist) muss ebenfalls von der Funktion `EOF` verarbeitet werden. Andernfalls kann ein Zeichen in den neuen Eingabebereich gesetzt werden, damit es beim nächsten Aufruf verarbeitet wird.

Die Definition von „verarbeiten“ ist abhängig von den abgeleiteten Klassen. Die Klasse `filebuf` schreibt z.B. ihre Zeichen in eine Datei, während die Klasse `strstreambuf` sie in ihrem Puffer behält, und den Puffer erweitert (wenn der Puffer als dynamisch festgelegt ist), wenn „overflow“ aufgerufen wird. Diese Erweiterung erfolgt durch Freigeben des alten Puffers und Ersetzen durch einen neuen größeren Puffer. Die Zeiger werden nach Bedarf angepasst.

## <a name="pbackfail"></a> basic_streambuf::pbackfail

Eine geschützte virtuelle Memberfunktion, die versucht, ein Element zurück in den Eingabestream zu versetzen und es dann zum aktuellen Element zu ernennen (es wird mit dem Zeiger für das nächste Element darauf gezeigt).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder **traits_type::** [eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich ausgeführt werden kann, wird **traits_type::eof** zurückgegeben oder eine Ausnahme ausgelöst. Andernfalls wird einen anderer Wert zurückgegeben. Das Standardverhalten ist, **traits_type::eof** zurückzugeben.

### <a name="remarks"></a>Hinweise

Wenn *\_metavergleiche* gleich **traits_type:: EOF**sind, handelt es sich bei dem Element, das zurückgesendet werden soll, um das Element, das sich bereits vor dem aktuellen Element im Stream befindet. Andernfalls wird dieses Element durch **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_Meta*) ersetzt. Ein Element kann auf verschiedene Arten durch die Funktion wiederhergestellt werden:

- Wenn eine Position zur Wiederherstellung verfügbar ist, kann das Element in der Position zur Wiederherstellung gespeichert werden, und der nächste Zeiger für den Eingabepuffer kann verringert werden.

- Eine Position zur Wiederherstellung kann verfügbar gemacht werden, indem neuer oder zusätzlicher Speicher für den Eingabepuffer zugewiesen wird.

- Bei einem Streampuffer mit allgemeinen Eingabe- und Ausgabestreams kann eine Position zur Wiederherstellung auch dadurch verfügbar gemacht werden, dass einige oder alle Elemente zwischen dem Anfangszeiger und den folgenden Zeigern für den Ausgabepuffer an ein externes Ziel geschrieben werden.

## <a name="pbase"></a> basic_streambuf::pbase

Eine geschützte Funktion, die einen Zeiger auf den Anfang des Ausgabepuffers zurückgibt.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Anfang des Ausgabepuffers.

## <a name="pbump"></a> basic_streambuf::pbump

Eine geschützte Funktion, die dem nächsten Zeiger für den Ausgabepuffer *count* hinzufügt.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Parameter

*Anzahl*\
Die Anzahl der Zeichen, um die die Schreibposition nach vorne verschoben werden soll.

## <a name="pos_type"></a> basic_streambuf::pos_type

Ordnet einen Typnamen innerhalb des Bereichs von „basic_streambuf“ einem der Typen in einem Vorlagenparameter zu.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a> basic_streambuf::pptr

Eine geschützte Funktion, die einen Zeiger auf das nächste Element des Ausgabepuffers zurückgibt.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das nächste Element des Ausgabepuffers.

## <a name="pubimbue"></a> basic_streambuf::pubimbue

Legt das Gebietsschema des Objekts „basic_streambuf“ fest.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>Parameter

*_Loc*\
Ein Verweis auf ein Gebietsschema.

### <a name="return-value"></a>Rückgabewert

Der vorherige Wert, der im locale-Objekt gespeichert war.

### <a name="remarks"></a>Hinweise

Die Memberfunktion speichert _ *Loc* im locale-Objekt und ruft [imbue](#imbue) auf.

### <a name="example"></a>Beispiel

Ein Beispiel, in dem [ verwendet wird, finden Sie unter ](../standard-library/basic-ios-class.md#imbue)basic_ios::imbue`pubimbue`.

## <a name="pubseekoff"></a> basic_streambuf::pubseekoff

Ruft [seekoff](#seekoff) auf, eine geschützte virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben wird.

```cpp
pos_type pubseekoff(off_type _Off,
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

Gibt die neue Position oder eine ungültige Streamposition zurück ( [seekoff](#seekoff)(_ *Off*, `_Way`, `_Which`) ).

### <a name="remarks"></a>Hinweise

Verschiebt den Zeiger relativ zu *_Way*.

## <a name="pubseekpos"></a> basic_streambuf::pubseekpos

Ruft [seekpos](#seekpos) auf, eine geschützte virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben wird, und setzt die aktuelle Zeigerposition zurück.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_Sp*\
Die Position, nach der gesucht werden soll.

*_Which*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden.

### <a name="return-value"></a>Rückgabewert

Die neue Position oder eine ungültige Streamposition. Vergleichen Sie den Rückgabewert mit `pos_type(off_type(-1))`, um festzustellen, ob die Streamposition ungültig ist.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [seekpos](#seekpos)(_ *Sp*, `_Which`) zurück.

## <a name="pubsetbuf"></a> basic_streambuf::pubsetbuf

Ruft [setbuf](#setbuf) auf, eine geschützte virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben wird.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*_Buffer*\
Ein Zeiger auf `char_type` für diese Instanziierung.

*Anzahl*\
Die Größe des Puffers.

### <a name="return-value"></a>Rückgabewert

Gibt [setbuf](#setbuf)( `_Buffer`, `count`) zurück.

## <a name="pubsync"></a> basic_streambuf::pubsync

Ruft [sync](#sync) auf, eine geschützte virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben wird, und aktualisiert den externen Stream für diesen Puffer.

```cpp
int pubsync();
```

### <a name="return-value"></a>Rückgabewert

Gibt [Sync](#sync) oder-1 zurück, wenn ein Fehler auftritt.

## <a name="sbumpc"></a> basic_streambuf::sbumpc

Liest das aktuelle Element, gibt es zurück und bewegt den Streamzeiger.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Rückgabewert

Das aktuelle Element.

### <a name="remarks"></a>Hinweise

Wenn eine Leseposition verfügbar ist, gibt die Memberfunktion **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong>[gptr](#gptr)) zurück und erhöht den nächsten Zeiger für den Eingabespeicher. Andernfalls wird [uflow](#uflow) zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_sbumpc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->sbumpc( );
   cout << i << endl;
}
```

```Input
3
```

```Output
33
51
```

## <a name="seekoff"></a> basic_streambuf::seekoff

Eine geschützte virtuelle Memberfunktion, die versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

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

Gibt die neue Position oder eine ungültige Streamposition zurück ( `seekoff` (_ *Off*, `_Way`, `_Which`) ).

### <a name="remarks"></a>Hinweise

Die neue Position wird wie folgt bestimmt:

- Bei `_Way` == `ios_base::beg` ist die neue Position der Anfang des Streams plus _ *Off*.

- Bei `_Way` == `ios_base::cur` ist die neue Position die aktuelle Streamposition plus _ *Off*.

- Bei `_Way` == `ios_base::end` ist die neue Position das Ende des Streams plus _ *Off*.

In der Regel ist der Eingabestream betroffen, wenn **which & ios_base::in** ungleich null ist. Der Ausgabestream ist betroffen, wenn **which & ios_base::out** ungleich null ist. Die tatsächliche Verwendung dieses Parameters ist allerdings bei verschiedenen abgeleiteten Streampuffern unabhängig.

Wenn die Funktion erfolgreich die Streamposition oder -positionen verändert, gibt sie die resultierende Streamposition oder eine der resultierenden Streampositionen zurück. Andernfalls gibt sie eine ungültige Streamposition zurück. Standardmäßig wird eine ungültige Streamposition zurückgegeben.

## <a name="seekpos"></a> basic_streambuf::seekpos

Eine geschützte virtuelle Memberfunktion, die versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_Sp*\
Die Position, nach der gesucht werden soll.

*_Which*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden.

### <a name="return-value"></a>Rückgabewert

Die neue Position oder eine ungültige Streamposition. Vergleichen Sie den Rückgabewert mit `pos_type(off_type(-1))`, um festzustellen, ob die Streamposition ungültig ist.

### <a name="remarks"></a>Hinweise

Die neue Position ist _ *Sp*.

In der Regel ist der Eingabestream betroffen, wenn **which & ios_base::in** ungleich null ist. Der Ausgabestream ist betroffen, wenn **which & ios_base::out** ungleich null ist. Die tatsächliche Verwendung dieses Parameters ist allerdings bei verschiedenen abgeleiteten Streampuffern unabhängig.

Wenn die Funktion erfolgreich die Streamposition oder -positionen verändert, gibt sie die resultierende Streamposition oder eine der resultierenden Streampositionen zurück. Andernfalls gibt sie eine ungültige Streamposition zurück (-1). Standardmäßig wird eine ungültige Streamposition zurückgegeben.

## <a name="setbuf"></a> basic_streambuf::setbuf

Eine geschützte virtuelle Memberfunktion, die für jeden abgeleiteten Streampuffer einen bestimmten Vorgang ausführt.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*_Buffer*\
Ein Zeiger auf einen Puffer.

*Anzahl*\
Die Größe des Puffers.

### <a name="return-value"></a>Rückgabewert

Standardmäßig wird **this** zurückgegeben.

### <a name="remarks"></a>Hinweise

Siehe [basic_filebuf](../standard-library/basic-filebuf-class.md). `setbuf` stellt einen Speicherplatzbereich für die Nutzung durch das `streambuf`-Objekt zur Verfügung. Wie der Puffer verwendet wird, ist in den abgeleiteten Klassen festgelegt.

## <a name="setg"></a> basic_streambuf::setg

Eine geschützte Funktion, die *Gbeg* im Startzeiger, `_Gnext` im nächsten Zeiger und `_Gend` im Endzeiger für den Eingabepuffer speichert.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Parameter

*_Gbeg*\
Ein Zeiger auf den Anfang des Puffers.

*_Gnext*\
Ein Zeiger auf eine Position in der Mitte des Puffers.

*_Gend*\
Ein Zeiger auf das Ende des Puffers.

## <a name="setp"></a> basic_streambuf::setp

Eine geschützte Funktion, die *_Pbeg* im anfangs Zeiger speichert und im endzeiger für den Ausgabepuffer *_Pend* .

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Parameter

*_Pbeg*\
Ein Zeiger auf den Anfang des Puffers.

*_Pend*\
Ein Zeiger auf das Ende des Puffers.

## <a name="sgetc"></a> basic_streambuf::sgetc

Gibt das aktuelle Element ohne Änderung der Position im Stream zurück.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Rückgabewert

Das aktuelle Element.

### <a name="remarks"></a>Hinweise

Wenn eine Leseposition verfügbar ist, gibt die Memberfunktion **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr)) zurück. Andernfalls wird [underflow](#underflow) zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_sgetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );

   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
   i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sgetn"></a> basic_streambuf::sgetn

Extrahiert bis zum *zählen* von Zeichen aus dem Eingabepuffer und speichert diese im bereitgestellten Puffer *ptr*.

Diese Methode ist potenziell unsicher, da sie darauf basiert, dass der Aufrufer überprüft, ob die übergebenen Werte korrekt sind.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*ptr* -\
Der Puffer, der die extrahierten Zeichen enthalten soll.

*Anzahl*\
Die Anzahl der zu lesenden Elemente.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der gelesenen Elemente. Weitere Informationen finden Sie unter [streamsize](../standard-library/ios-typedefs.md#streamsize).

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [xsgetn](#xsgetn)( `ptr`, `count`) zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_sgetn.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);
    char a[10];

    // Extract 3 characters from myfile and store them in a.
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996
    a[i] = myfile.widen('\0');

    // Display the size and contents of the buffer passed to sgetn.
    cout << i << " " << a << endl;

    // Display the contents of the original input buffer.
    cout << myfile.rdbuf() << endl;
}
```

## <a name="showmanyc"></a> basic_streambuf::showmanyc

Eine geschützte virtuelle Memberfunktion, die die Anzahl von Zeichen zurückgibt, die aus dem Eingabestream extrahiert werden können, und sicherstellt, dass das Programm keiner unbegrenzten Wartezeit unterliegt.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Rückgabewert

Standardmäßig wird null zurückgegeben.

## <a name="snextc"></a> basic_streambuf::snextc

Liest das aktuelle Element und gibt das folgende Element zurück.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Rückgabewert

Das nächste Element im Stream.

### <a name="remarks"></a>Hinweise

Die Memberfunktion ruft [sbumpc](#sbumpc) auf, und gibt **traits_type::eof** zurück, wenn diese Funktion [traits_type::](../standard-library/char-traits-struct.md#eof)**eof** zurückgibt. Andernfalls wird [sgetc](#sgetc) zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_snextc.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->snextc( );
   // cout << ( int )char_traits<char>::eof << endl;
   cout << i << endl;
}
```

```Input
aa
```

```Output
aa97
```

## <a name="sputbackc"></a> basic_streambuf::sputbackc

Fügt char_type in den Stream ein.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Parameter

*_Ch*\
Das Zeichen.

### <a name="return-value"></a>Rückgabewert

Gibt das Zeichen oder einen Fehler zurück.

### <a name="remarks"></a>Hinweise

Wenn eine putbackposition verfügbar ist und *_Ch* mit dem an dieser Position gespeicherten Zeichen übereinstimmt, verringert die Member-Funktion den nächsten Zeiger für den Eingabepuffer und gibt **traits_type::** [To_int_type](../standard-library/char-traits-struct.md#to_int_type)(`_Ch`) zurück. Andernfalls wird [pbackfail](#pbackfail)( `_Ch`) zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_sputbackc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;

    ifstream myfile("basic_streambuf_sputbackc.txt",
        ios::in);

    int i = myfile.rdbuf()->sbumpc();
    cout << (char)i << endl;
    int j = myfile.rdbuf()->sputbackc('z');
    if (j == 'z')
    {
        cout << "it worked" << endl;
    }
    i = myfile.rdbuf()->sgetc();
    cout << (char)i << endl;
}
```

## <a name="sputc"></a> basic_streambuf::sputc

Setzt ein Zeichen in den Stream.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Parameter

*_Ch*\
Das Zeichen.

### <a name="return-value"></a>Rückgabewert

Gibt das Zeichen zurück, falls erfolgreich.

### <a name="remarks"></a>Hinweise

Wenn eine `write position` verfügbar ist, speichert die Element Funktion *_Ch* in der Schreibposition, Inkremente den nächsten Zeiger für den Ausgabepuffer und gibt **traits_type::** [To_int_type](../standard-library/char-traits-struct.md#to_int_type)(`_Ch`) zurück. Andernfalls wird [overflow](#overflow)( `_Ch`) zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_sputc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   int i = cout.rdbuf( )->sputc( 'a' );
   cout << endl << ( char )i << endl;
}
```

```Output
a
a
```

## <a name="sputn"></a> basic_streambuf::sputn

Setzt eine Zeichenfolge in den Stream.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parameter

*ptr* -\
Die Zeichenfolge.

*Anzahl*\
Die Anzahl der Zeichen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der tatsächlich in den Stream eingefügten Zeichen.

### <a name="remarks"></a>Hinweise

Die Memberfunktion gibt [xsputn](#xsputn)( `ptr`, `count`) zurück. Weitere Informationen finden Sie im Bereich „Hinweise“ dieses Members.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_sputn.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    streamsize i = cout.rdbuf()->sputn("test", 4);
    cout << endl << i << endl;
}
```

```Output
test
4
```

## <a name="stossc"></a> basic_streambuf::stossc

Verschiebt den Zeiger hinter das aktuelle Element im Stream.

```cpp
void stossc();
```

### <a name="remarks"></a>Hinweise

Die Memberfunktion ruft [sbumpc](#sbumpc) auf. Beachten Sie, dass keine Implementierung notwendig ist, um diese Memberfunktion bereitzustellen.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_stossc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );

   myfile.rdbuf( )->stossc( );
   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sungetc"></a> basic_streambuf::sungetc

Ruft ein Zeichen aus dem Stream ab.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Rückgabewert

Gibt entweder das Zeichen oder einen Fehler zurück.

### <a name="remarks"></a>Hinweise

Wenn eine Position zur Wiederherstellung verfügbar ist, erhöht die Memberfunktion den nächsten Zeiger für den Eingabespeicher, und gibt `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr)) zurück. Allerdings ist es nicht immer möglich, das letzte gelesene Zeichen zu bestimmen, sodass es möglicherweise im Status des aktuellen Puffers erfasst wird. Wenn dies zutrifft, gibt die Funktion [pbackfail](#pbackfail) zurück. Behalten Sie das letzte Zeichen im Blick, das Sie wiederherstellen möchten, und rufen Sie `sputbackc(ch)` auf, um diese Situation zu vermeiden. Dadurch wird kein Fehler verursacht, vorausgesetzt, Sie rufen die Funktion nicht zu Beginn eines Streams auf, oder versuchen, mehr als ein Zeichen wiederherzustellen.

### <a name="example"></a>Beispiel

```cpp
// basic_streambuf_sungetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );

   // Read and increment
   int i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Read and increment
   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Decrement, read, and do not increment
   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;
}
```

## <a name="swap"></a> basic_streambuf::swap

Tauscht die Werte in diesem Objekt gegen die Werte im bereitgestellten `basic_streambuf`-Objekt aus.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*right*|Einen lvalue-Verweis auf das `basic_streambuf`-Objekt, das zum Austauschen von Werten verwendet wird.|

### <a name="remarks"></a>Hinweise

Die geschützte Member-Funktion tauscht alle Zeiger, die die `input buffer` und die `output buffer`steuern, mit *rechten* aus. Außerdem tauscht sie `right.`[getloc()](#getloc) mit dem `locale`-Objekt aus.

## <a name="sync"></a> basic_streambuf::sync

Eine geschützte virtuelle Funktion, die versucht, die gesteuerten Streams mit zugehörigen externen Streams zu synchronisieren.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich abgeschlossen werden kann, wird -1 zurückgegeben. Standardmäßig wird null zurückgegeben.

### <a name="remarks"></a>Hinweise

`sync` umfasst das Schreiben von Elementen zwischen dem Anfang und den nächsten Zeigern für den Ausgabepuffer. Sie umfasst jedoch nicht das Wiederherstellen von Elementen zwischen den nächsten und den letzten Zeigern für den Eingabepuffer.

## <a name="traits_type"></a> basic_streambuf::traits_type

Verknüpft einen Typnamen mit dem **Tr**-Vorlagenparameter.

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a> basic_streambuf::uflow

Eine geschützte virtuelle Funktion, die das aktuelle Element aus dem Eingabestream extrahiert.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Rückgabewert

Das aktuelle Element.

### <a name="remarks"></a>Hinweise

Die geschützte virtuelle Memberfunktion versucht, das aktuelle Element **ch** aus dem Eingabestream zu extrahieren, anschließend die aktuelle Streamposition nach vorne zu verschieben, und das Element als **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**) zurückzugeben. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn eine Leseposition verfügbar ist, wird **ch** als das in der Leseposition gespeicherte Element verwendet, und der nächste Zeiger für den Eingabepuffer wird nach vorne verschoben.

- Ein Element kann auch direkt aus einer externen Quelle gelesen und als Wert **ch** bereitgestellt werden.

- Bei einem Streampuffer mit allgemeinen Eingabe- und Ausgabestreams kann eine Leseposition auch dadurch verfügbar gemacht werden, dass einige oder alle Elemente zwischen dem Anfangszeiger und den folgenden Zeigern für den Ausgabepuffer an ein externes Ziel geschrieben werden. Andernfalls kann neuer oder zusätzlicher Speicher für den Eingabepuffer zugewiesen werden. Die Funktion liest dann aus einer externen Quelle oder aus einem oder mehreren Elementen ein.

Wenn die Funktion nicht erfolgreich ausgeführt werden kann, wird **traits_type::** [eof](../standard-library/char-traits-struct.md#eof) zurückgegeben, oder eine Ausnahme ausgelöst. Andernfalls gibt sie das aktuelle `ch`-Element in den Eingabestream zurück, das wie oben beschrieben konvertiert wurde, und verschiebt den nächsten Zeiger für den Eingabepuffer nach vorne. Standardmäßig wird [underflow](#underflow) aufgerufen, wenn diese Funktion **traits_type::eof** zurückgibt, um **traits_type::eof** zurückzugeben. Andernfalls gibt die Funktion das aktuelle **ch**-Element in den Eingabestream zurück, das wie vorhin beschrieben konvertiert wurde, und verschiebt den nächsten Zeiger für den Eingabepuffer nach vorne.

## <a name="underflow"></a> basic_streambuf::underflow

Die geschützte virtuelle Funktion versucht, das aktuelle Element aus dem Eingabestream zu extrahieren.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Rückgabewert

Das aktuelle Element.

### <a name="remarks"></a>Hinweise

Die geschützte virtuelle Memberfunktion versucht, das aktuelle Element **ch** aus dem Eingabestream zu extrahieren, ohne die aktuelle Streamposition nach vorne zu verschieben und das Element als `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**) zurückzugeben. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn eine Leseposition verfügbar ist, ist **ch** das Element, das in der Leseposition gespeichert wird. Weitere Informationen hierzu finden Sie im Abschnitt „Hinweise“ unter [basic_streambuf-Klasse](../standard-library/basic-streambuf-class.md).

- Eine Leseposition kann verfügbar gemacht werden, indem die Funktion neuen oder zusätzlichen Speicher für den Eingabepuffer zuweist und anschließend aus einer externen Quelle oder einem oder mehreren Elementen einliest. Weitere Informationen hierzu finden Sie im Abschnitt „Hinweise“ unter [basic_streambuf-Klasse](../standard-library/basic-streambuf-class.md).

Wenn die Funktion nicht erfolgreich ausgeführt werden kann, wird `traits_type::`[eof](../standard-library/char-traits-struct.md#eof)`()` zurückgegeben, oder eine Ausnahme ausgelöst. Andernfalls wird das aktuelle Element konvertiert, wie zuvor beschrieben, in den Eingabestream zurückgegeben. Standardmäßig wird `traits_type::eof()` zurückgegeben.

Die virtuellen Funktionen `underflow` mit [sync](#sync) und [overflow](#overflow) legen die Eigenschaften der von `streambuf` abgeleiteten Klasse fest. Jede abgeleitete Klasse kann `underflow` anders implementieren, die Schnittstelle mit der aufrufenden Stream-Klasse bleibt allerdings gleich.

Die `underflow`-Funktion wird am häufigsten von öffentlichen `streambuf`-Funktionen, wie z.B. [sgetc](#sgetc) und [sgetn](#sgetn) aufgerufen, wenn der Abrufbereich leer ist. Andere Klassen, darunter stream-Klassen, können `underflow` jederzeit aufrufen.

Die Funktion `underflow` stellt dem Abrufbereich Zeichen aus der Eingabequelle bereit. Wenn der Abrufbereich Zeichen enthält, gibt `underflow` das erste Zeichen zurück. Wenn der Abrufbereich leer ist, füllt die Funktion den Abrufbereich und gibt das folgende Zeichen zurück (welches von der Funktion im Abrufbereich gelassen wird). Wenn keine weiteren Zeichen verfügbar sind, gibt `underflow``EOF` zurück und lässt den Abrufbereich leer.

In der `strstreambuf`-Klasse passt `underflow` den [egptr](#egptr)-Zeiger an, um auf den Speicher zuzugreifen, der dynamisch durch einen Aufruf an `overflow` zugewiesen wurde.

## <a name="xsgetn"></a> basic_streambuf::xsgetn

Eine geschützte virtuelle Funktion, um Elemente aus dem Eingabestream zu extrahieren.

Diese Methode ist potenziell unsicher, da sie darauf basiert, dass der Aufrufer überprüft, ob die übergebenen Werte korrekt sind.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*ptr* -\
Der Puffer, der die extrahierten Zeichen enthalten soll.

*Anzahl*\
Die Anzahl der zu extrahierenden Elemente.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der extrahierten Elemente.

### <a name="remarks"></a>Hinweise

Die geschützte virtuelle Member-Funktion extrahiert bis zu *count* -Elemente aus dem Eingabestream, wie bei wiederholten Aufrufen von [Sbumpc](#sbumpc), und speichert Sie in dem Array, beginnend bei *ptr*. Gibt die Anzahl der Elemente zurück, die tatsächlich extrahiert wurden.

## <a name="xsputn"></a> basic_streambuf::xsputn

Eine geschützte virtuelle Funktion, mit der Elemente in den Ausgabestream einfügt werden können.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parameter

*ptr* -\
Zeiger auf die einzufügenden Elemente.

*Anzahl*\
Die Anzahl einzufügender Elemente.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen, die tatsächlich in den Stream eingefügt werden.

### <a name="remarks"></a>Hinweise

Die Funktion der geschützten virtuellen Member *Fügt Elemente in* den Ausgabestream ein, wie dies bei wiederholten Aufrufen von [sputc](#sputc)aus dem Array ab *ptr*. Das Einfügen von Zeichen in den Ausgabestream wird beendet, sobald alle *zählungs* Zeichen geschrieben wurden, oder wenn der Aufruf von `sputc( count)` `traits::eof()`zurückgeben würde. Sie gibt die Anzahl der Elemente zurück, die tatsächlich eingefügt werden.

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
