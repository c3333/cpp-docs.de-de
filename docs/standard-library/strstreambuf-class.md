---
title: strstreambuf-Klasse
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
ms.openlocfilehash: e6b4df60f4d28839419d02fd3ed6d7cbf73d327f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202193"
---
# <a name="strstreambuf-class"></a>strstreambuf-Klasse

Beschreibt einen Streampuffer, der die Übertragung von Elementen in eine und aus einer Sequenz von Elementen steuert, die in einem- **`char`** Array Objekt gespeichert sind.

## <a name="syntax"></a>Syntax

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Bemerkungen

Je nachdem, wie das Objekt aufgebaut ist, kann es nach Bedarf reserviert, erweitert und freigegeben werden, um Änderungen in der Sequenz zu berücksichtigen.

Ein aus der Klasse `strstreambuf` abgeleitetes Objekt speichert mehrere Bits mit Modusinformationen als seinen `strstreambuf`-Modus. Diese Bits geben an, ob Folgendes für die gesteuerte Sequenz zutrifft:

- Sie wurde reserviert und muss schließlich freigegeben werden.

- Sie kann geändert werden.

- Sie kann durch erneute Reservierung von Speicher erweitert werden.

- Sie wurde eingefroren und muss daher „aufgetaut“ werden, bevor das Objekt zerstört wird, oder sie muss (sofern reserviert) durch ein Element freigegeben werden, das nicht mit dem Objekt identisch ist.

Eine gesteuerte Sequenz, die eingefroren ist, kann weder geändert noch erweitert werden, unabhängig vom Status dieser einzelnen Modusbits.

Das Objekt speichert auch Zeiger auf zwei Funktionen, mit denen die `strstreambuf`-Speicherbelegung gesteuert wird. Sind diese Zeiger NULL-Zeiger, muss für das Objekt eine eigene Methode des Belegens und Freigebens von Speicher für die gesteuerte Sequenz formuliert sein.

> [!NOTE]
> Diese Klasse ist veraltet. Verwenden Sie stattdessen [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) oder [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf).

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[strstreambuf](#strstreambuf)|Konstruiert ein Objekt vom Typ `strstreambuf`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[ge](#freeze)|Bewirkt, dass ein Streampuffer durch Streampuffervorgänge nicht verfügbar ist.|
|[Läufen](#overflow)|Eine geschützte virtuelle Funktion, die aufgerufen werden kann, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.|
|[pbackfail](#pbackfail)|Eine geschützte virtuelle Memberfunktion, die versucht, ein Element in den Eingabestreams zurückzuschreiben, und es dann zum aktuellen Element macht (auf das der nächste Zeiger zeigt).|
|[pcount](#pcount)|Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.|
|[seekoff](#seekoff)|Eine geschützte virtuelle Memberfunktion, die versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[seekpos](#seekpos)|Eine geschützte virtuelle Memberfunktion, die versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.|
|[str](#str)|Ruft [freeze](#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.|
|[Unterlauf](#underflow)|Eine geschützte virtuelle Funktion zum Extrahieren des aktuellen Elements aus dem Eingabestream.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<strstream>

**Namespace:** std

## <a name="strstreambuffreeze"></a><a name="freeze"></a>strauf:: Freeze

Bewirkt, dass ein Streampuffer durch Streampuffervorgänge nicht verfügbar ist.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parameter

*_Freezeit*\
Ein Wert **`bool`** , der angibt, ob der Stream eingefroren werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn *_Freezeit* true ist, ändert die Funktion den gespeicherten `strstreambuf` Modus, damit die gesteuerte Sequenz fixiert wird. Andernfalls ist es die kontrollierte Sequenz nicht fixiert.

[str](#str) impliziert `freeze`.

> [!NOTE]
> Ein fixierter Puffer wird während der `strstreambuf`-Zerstörung nicht freigegeben. Sie müssen die Fixierung des Puffers aufheben, bevor er freigegeben wird, um einen Speicherverlust zu vermeiden.

### <a name="example"></a>Beispiel

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="strstreambufoverflow"></a><a name="overflow"></a>strauf:: overflow

Eine geschützte virtuelle Funktion, die aufgerufen werden kann, wenn ein neues Zeichen in einen vollen Puffer eingefügt wird.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder `EOF`.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich abgeschlossen werden kann, wird `EOF` zurückgegeben. Andernfalls wird bei * \_ Meta*  ==  `EOF` ein anderer Wert als zurückgegeben `EOF` . Andernfalls wird * \_ Meta*zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn * \_ Meta* ! = `EOF` , versucht die Funktion des geschützten virtuellen Members, das Element `(char)_Meta` in den Ausgabepuffer einzufügen. Hierfür gibt es verschiedene Möglichkeiten:

- Wenn eine Schreibposition verfügbar ist, kann das Element in der Schreibposition gespeichert werden, und der nächste Zeiger für den Ausgabepuffer kann inkrementiert werden.

- Wenn der gespeicherte strstreambuf Modus anzeigt, dass die kontrollierte Sequenz änderbar, erweiterbar und nicht fixiert ist, kann die Funktion eine Schreibposition verfügbar machen, indem für den Ausgabepuffer eine neue zugewiesen wird. Das Erweitern des Ausgabepuffers erweitert auf diese Weise auch alle zugewiesenen Eingabepuffer.

## <a name="strstreambufpbackfail"></a><a name="pbackfail"></a>strauf::p backfail

Eine geschützte virtuelle Memberfunktion, die versucht, ein Element in den Eingabestreams zurückzuschreiben, und es dann zum aktuellen Element macht (auf das der nächste Zeiger zeigt).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Parameter

*_Meta*\
Das Zeichen, das in den Puffer eingefügt werden soll, oder `EOF`.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich abgeschlossen werden kann, wird `EOF` zurückgegeben. Andernfalls wird bei * \_ Meta*  ==  `EOF` ein anderer Wert als zurückgegeben `EOF` . Andernfalls wird * \_ Meta*zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion versucht, ein Element im Eingabepuffer wiederherzustellen und es dann zum aktuellen Element zu machen (der nächste Zeiger zeigt auf das Element).

Wenn * \_ Meta*  ==  `EOF` , ist das Element, das zurück abgelegt werden soll, das, das sich bereits vor dem aktuellen Element im Stream befindet. Andernfalls wird dieses Element durch ersetzt `ch = (char)_Meta` . Ein Element kann auf verschiedene Arten durch die Funktion wiederhergestellt werden:

- Wenn eine rückgabeposition verfügbar ist und das Element, das dort gespeichert ist, gleich ist `ch` , kann der nächste Zeiger für den Eingabepuffer verringert werden.

- Wenn eine Position für die Wiederherstellung verfügbar ist und der Modus "straustreambuf" besagt, dass die gesteuerte Sequenz geändert werden kann, kann die Funktion `ch` in der Putback-Position speichern und den nächsten Zeiger für den Eingabepuffer verringern.

## <a name="strstreambufpcount"></a><a name="pcount"></a>strauf::p Anzahl

Gibt die Anzahl der Elemente zurück, die in die kontrollierte Sequenz geschrieben wurde.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zähler der Anzahl von Elementen, die in die kontrollierte Sequenz geschrieben wurden.

### <a name="remarks"></a>Bemerkungen

Wenn [pptr](../standard-library/basic-streambuf-class.md#pptr) ein NULL-Zeiger ist, gibt die Funktion null zurück. Andernfalls wird " `pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase)" zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="strstreambufseekoff"></a><a name="seekoff"></a>"strauf":: seekoff

Eine geschützte virtuelle Memberfunktion, die versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_Off*\
Die Position, die relativ zu *_Way*gesucht werden soll.

*_Way*\
Der Startpunkt für Offsetvorgänge. Mögliche Werte sind unter [seekdir](../standard-library/ios-base-class.md#seekdir) aufgeführt.

*_Which*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion eine der beiden Streampositionen erfolgreich ändert, gibt sie die resultierende Streamposition zurück. Andernfalls schlägt sie fehl und gibt eine ungültige Streamposition zurück.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern. Für ein Objekt der Klasse strstreambuf besteht eine Streamposition lediglich aus einem Streamoffset. Das Offset Null legt das erste Element der kontrollierten Sequenz fest.

Die neue Position wird wie folgt bestimmt:

- Wenn `_Way == ios_base::beg` der Wert ist, ist die neue Position der Anfang des Streams Plus *_Off*.

- Wenn `_Way == ios_base::cur` der Wert ist, ist die neue Position die aktuelle Streamposition Plus *_Off*.

- Wenn der Wert ist `_Way == ios_base::end` , ist die neue Position das Ende des Streams Plus *_Off*.

Wenn ungleich `_Which & ios_base::in` 0 (null) ist und der Eingabepuffer vorhanden ist, ändert die Funktion die nächste Position, die im Eingabepuffer gelesen werden soll. Wenn `_Which & ios_base::out` auch ungleich NULL ist, `_Way != ios_base::cur` und der Ausgabepuffer vorhanden ist, legt die Funktion auch die nächste zu schreibende Position fest, damit Sie der nächsten zu lesenden Position entspricht.

Ansonsten ändert die Funktion die nächste Position, die im Ausgabepuffer geschrieben werden soll, wenn `_Which & ios_base::out` ungleich null ist. Andernfalls schlägt der Positionierungsvorgang fehl. Damit eine Positionierung erfolgreich ist, muss die resultierende Streamposition innerhalb der gesteuerten Sequenz liegen.

## <a name="strstreambufseekpos"></a><a name="seekpos"></a>"strauf":: seekpos

Eine geschützte virtuelle Memberfunktion, die versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parameter

*_Sp*\
Die Position, nach der gesucht werden soll.

*_Which*\
Gibt den Modus für die Zeigerposition an. Standardmäßig können Lese- und Schreibpositionen geändert werden.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion eine der beiden Streampositionen erfolgreich ändert, gibt sie die resultierende Streamposition zurück. Andernfalls schlägt sie fehl und gibt eine ungültige Streamposition zurück. Vergleichen Sie den Rückgabewert mit `pos_type(off_type(-1))`, um festzustellen, ob die Streamposition ungültig ist.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Memberfunktion versucht, die aktuellen Positionen für die gesteuerten Streams zu ändern. Für ein Objekt der Klasse strstreambuf besteht eine Streamposition lediglich aus einem Streamoffset. Das Offset Null legt das erste Element der kontrollierten Sequenz fest. Die neue Position wird durch *_Sp*bestimmt.

Wenn `_Which` & **ios_base::in** ungleich null ist, ändert die Funktion die nächste Position, die im Eingabepuffer gelesen werden soll. Wenn `_Which` & `ios_base::out` ungleich null und der Ausgabepuffer vorhanden ist, legt die Funktion auch die nächste zu schreibende Position so fest, dass sie der nächsten zu lesenden Position entspricht. Ansonsten ändert die Funktion die nächste Position, die im Ausgabepuffer geschrieben werden soll, wenn `_Which` & `ios_base::out` ungleich null ist. Andernfalls schlägt der Positionierungsvorgang fehl. Damit eine Positionierung erfolgreich ist, muss die resultierende Streamposition innerhalb der gesteuerten Sequenz liegen.

## <a name="strstreambufstr"></a><a name="str"></a>strauf:: Str

Ruft [freeze](#freeze) auf und gibt anschließend einen Zeiger auf den Anfang der kontrollierten Sequenz zurück.

```cpp
char *str();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf den Anfang der kontrollierten Sequenz.

### <a name="remarks"></a>Bemerkungen

Kein abschließendes Null-Element vorhanden, sofern Sie nicht explizit ein Element einfügen.

### <a name="example"></a>Beispiel

Unter [strstreambuf::freeze](#freeze) finden Sie ein Beispiel, das **str** verwendet.

## <a name="strstreambufstrstreambuf"></a><a name="strstreambuf"></a>"Straub": "Strauch"

Konstruiert ein Objekt vom Typ `strstreambuf`.

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* alloc_func)(size_t),
    void (* free_func)(void*));

strstreambuf(char* getptr,
    streamsize count,
    char* putptr = 0);

strstreambuf(signed char* getptr,
    streamsize count,
    signed char* putptr = 0);

strstreambuf(unsigned char* getptr,
    streamsize count,
    unsigned char* putptr = 0);

strstreambuf(const char* getptr,
    streamsize count);

strstreambuf(const signed char* getptr,
    streamsize count);

strstreambuf(const unsigned char* getptr,
    streamsize count);
```

### <a name="parameters"></a>Parameter

*alloc_func*\
Funktion, mit der Speicher zugewiesen wird.

*Countdown*\
Bestimmt die Länge des Puffers, auf den von *GetPtr*verwiesen wird. Wenn *GetPtr* kein Argument (erstes konstruktorformular) ist, wird eine vorgeschlagene Zuordnungs Größe für die Puffer angezeigt.

*_Freefunc*\
Zum Freigeben von Pufferspeicher verwendete Funktion.

*GetPtr*\
Ein Puffer, der für die Eingabe verwendet wird.

*putptr*\
Ein Puffer, der für die Ausgabe verwendet wird.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert einen NULL-Zeiger in allen Zeigern, die den Eingabepuffer, den Ausgabepuffer und die strstreambuf-Zuweisung steuern. Legt den strstreambuf-Modus so fest, dass die kontrollierte Sequenz änderbar und erweiterbar ist. Außerdem wird die *Anzahl* als vorgeschlagene anfängliche Zuordnungs Größe akzeptiert.

Der zweite Konstruktor verhält sich wie der erste, mit der Ausnahme, dass er *alloc_func* als Zeiger auf die Funktion speichert, die aufgerufen werden soll, um Speicher zuzuweisen, und *free_func* als Zeiger auf die Funktion, die aufgerufen werden soll, um diesen Speicher freizugeben.

Die drei Konstruktoren:

```cpp
strstreambuf(char *getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

Verhalten sich auch wie das erste-Objekt, mit dem Unterschied, dass *GetPtr* das Array Objekt festlegt, das für die gesteuerte Sequenz verwendet wird. (Daher darf kein NULL-Zeiger sein.) Die Anzahl *der Elemente im* -Array wird wie folgt bestimmt:

- Wenn (*count* > 0), dann *N* ist N *count*.

- Wenn (*count* = = 0), dann *N* ist N `strlen((const char *) getptr )` .

- Wenn (*count* < 0), wird *N* **INT_MAX**.

Wenn *putptr* ein NULL-Zeiger ist, erstellt die Funktion nur einen Eingabepuffer, indem Folgendes ausgeführt wird:

```cpp
setg(getptr,
    getptr,
    getptr + N);
```

Andernfalls legt die Eingabe- und Ausgabepuffer fest, indem sie Folgendes ausführt:

```cpp
setg(getptr,
    getptr,
    putptr);

setp(putptr,
    getptr + N);
```

In diesem Fall muss *putptr* das Intervall [ *GetPtr*, *GetPtr*  +  *N*] aufweisen.

Die drei Konstruktoren:

```cpp
strstreambuf(const char *getptr,
    streamsize count);

strstreambuf(const signed char *getptr,
    streamsize count);

strstreambuf(const unsigned char *getptr,
    streamsize count);
```

verhalten sich wie:

```cpp
streambuf((char *)getptr, count);
```

abgesehen davon, dass der gespeicherte Modus die kontrollierte Sequenz weder änderbar noch erweiterbar macht.

## <a name="strstreambufunderflow"></a><a name="underflow"></a>"straustreambuf:: underflow"

Eine geschützte virtuelle Funktion zum Extrahieren des aktuellen Elements aus dem Eingabestream.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion nicht erfolgreich abgeschlossen werden kann, wird `EOF` zurückgegeben. Andernfalls wird das aktuelle Element, wie zuvor beschrieben, konvertiert in den Eingabestream zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die geschützte virtuelle Member-Funktion versucht, das aktuelle Element `ch` aus dem Eingabepuffer zu extrahieren, dann die aktuelle Streamposition fortzusetzen und das Element als zurückzugeben `(int)(unsigned char)ch` . Dies ist nur eine Möglichkeit: Wenn eine Lese Position verfügbar ist, wird Sie `ch` als das an der Lese Position gespeicherte Element benötigt und der nächste Zeiger für den Eingabepuffer erhöht.

## <a name="see-also"></a>Weitere Informationen

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
