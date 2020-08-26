---
title: ios_base-Klasse
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::ios_base
- ios/std::ios_base::event_callback
- xiosbase/std::ios_base::fmtflags
- xiosbase/std::ios_base::iostate
- xiosbase/std::ios_base::openmode
- xiosbase/std::ios_base::seekdir
- xiosbase/std::ios_base::event
- xiosbase/std::ios_base::adjustfield
- xiosbase/std::ios_base::app
- xiosbase/std::ios_base::ate
- xiosbase/std::ios_base::badbit
- xiosbase/std::ios_base::basefield
- xiosbase/std::ios_base::beg
- xiosbase/std::ios_base::binary
- xiosbase/std::ios_base::boolalpha
- xiosbase/std::ios_base::cur
- xiosbase/std::ios_base::dec
- xiosbase/std::ios_base::end
- xiosbase/std::ios_base::eofbit
- xiosbase/std::ios_base::failbit
- xiosbase/std::ios_base::fixed
- xiosbase/std::ios_base::floatfield
- xiosbase/std::ios_base::goodbit
- xiosbase/std::ios_base::hex
- xiosbase/std::ios_base::in
- xiosbase/std::ios_base::internal
- xiosbase/std::ios_base::left
- xiosbase/std::ios_base::oct
- xiosbase/std::ios_base::out
- xiosbase/std::ios_base::right
- xiosbase/std::ios_base::scientific
- xiosbase/std::ios_base::showbase
- xiosbase/std::ios_base::showpoint
- xiosbase/std::ios_base::showpos
- xiosbase/std::ios_base::skipws
- xiosbase/std::ios_base::trunc
- xiosbase/std::ios_base::unitbuf
- xiosbase/std::ios_base::uppercase
- xiosbase/std::ios_base::failure
- xiosbase/std::ios_base::flags
- xiosbase/std::ios_base::getloc
- xiosbase/std::ios_base::imbue
- xiosbase/std::ios_base::Init
- xiosbase/std::ios_base::iword
- xiosbase/std::ios_base::precision
- xiosbase/std::ios_base::pword
- ios/std::ios_base::register_callback
- xiosbase/std::ios_base::setf
- xiosbase/std::ios_base::sync_with_stdio
- xiosbase/std::ios_base::unsetf
- xiosbase/std::ios_base::width
- xiosbase/std::ios_base::xalloc
helpviewer_keywords:
- std::ios_base [C++]
- std::ios_base [C++], event_callback
- std::ios_base [C++], fmtflags
- std::ios_base [C++], iostate
- std::ios_base [C++], openmode
- std::ios_base [C++], seekdir
- std::ios_base [C++], event
- std::ios_base [C++], adjustfield
- std::ios_base [C++], app
- std::ios_base [C++], ate
- std::ios_base [C++], badbit
- std::ios_base [C++], basefield
- std::ios_base [C++], beg
- std::ios_base [C++], binary
- std::ios_base [C++], boolalpha
- std::ios_base [C++], cur
- std::ios_base [C++], dec
- std::ios_base [C++], end
- std::ios_base [C++], eofbit
- std::ios_base [C++], failbit
- std::ios_base [C++], fixed
- std::ios_base [C++], floatfield
- std::ios_base [C++], goodbit
- std::ios_base [C++], hex
- std::ios_base [C++], in
- std::ios_base [C++], internal
- std::ios_base [C++], left
- std::ios_base [C++], oct
- std::ios_base [C++], out
- std::ios_base [C++], right
- std::ios_base [C++], scientific
- std::ios_base [C++], showbase
- std::ios_base [C++], showpoint
- std::ios_base [C++], showpos
- std::ios_base [C++], skipws
- std::ios_base [C++], trunc
- std::ios_base [C++], unitbuf
- std::ios_base [C++], uppercase
- std::ios_base [C++], failure
- std::ios_base [C++], flags
- std::ios_base [C++], getloc
- std::ios_base [C++], imbue
- std::ios_base [C++], Init
- std::ios_base [C++], iword
- std::ios_base [C++], precision
- std::ios_base [C++], pword
- std::ios_base [C++], register_callback
- std::ios_base [C++], setf
- std::ios_base [C++], sync_with_stdio
- std::ios_base [C++], unsetf
- std::ios_base [C++], width
- std::ios_base [C++], xalloc
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
ms.openlocfilehash: da7c8eee2653a34035f39fe272378ae63165bfc2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845496"
---
# <a name="ios_base-class"></a>ios_base-Klasse

Die Klasse beschreibt die Speicher- und Memberfunktionen, die Eingabe- und Ausgabestreams gemeinsam sind, die nicht von den Vorlagenparametern abhängen. (Die Klassen Vorlage [basic_ios](../standard-library/basic-ios-class.md) beschreibt, was üblich ist und von Vorlagen Parametern abhängig ist.)

Ein Objekt der ios_base-Klasse speichert Formatierungsinformationen, die aus Folgendem bestehen:

- Formatflags in einem Objekt vom Typ [`fmtflags`](#fmtflags) .

- Eine Ausnahme Maske in einem Objekt vom Typ [`iostate`](#iostate) .

- Eine Feldbreite in einem Objekt vom Typ **`int`** .

- Eine Anzeige Genauigkeit in einem Objekt vom Typ **`int`** .

- Ein Gebiets Schema Objekt in einem Objekt vom Typ `locale` .

- Zwei erweiterbare Arrays mit Elementen vom Typ **`long`** und **`void`** Zeiger.

Ein Objekt der Klasse ios_base speichert auch streamstatusinformationen in einem Objekt vom Typ [`iostate`](#iostate) und einen Rückruf Stapel.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[ios_base](#ios_base)|Erstellt `ios_base`-Objekte.|

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[event_callback](#event_callback)|Beschreibt eine Funktion, die an [register_call](#register_callback) übergeben wird.|
|[`fmtflags`](#fmtflags)|Konstanten, mit denen das Aussehen der Ausgabe angegeben wird.|
|[`iostate`](#iostate)|Definiert Konstanten, die den Zustand eines Streams beschreiben.|
|[openmode](#openmode)|Beschreibt, wie mit einem Stream interagiert wird.|
|[seekdir](#seekdir)|Gibt den Startpunkt für Offsetvorgänge an.|

### <a name="enums"></a>Enumerationen

|Name|Beschreibung|
|-|-|
|[event](#event)|Gibt Ereignistypen an.|

### <a name="constants"></a>Konstanten

|Name|Beschreibung|
|-|-|
|[adjustfield](#fmtflags)|Eine Bitmaske, die als `internal` &#124; `left` &#124; `right` definiert ist.|
|[app](#openmode)|Gibt an, dass vor jedem Einfügevorgang bis zum Ende eines Streams gesucht werden soll.|
|[ate](#openmode)|Gibt an, dass bis zum Ende eines Streams gesucht werden soll, wenn dessen steuerndes Objekt erstmalig erstellt wird.|
|[badbit](#iostate)|Protokolliert einen Verlust der Integrität des Streampuffers.|
|[basefield](#fmtflags)|Eine Bitmaske, die als `dec` &#124; `hex` &#124; `oct` definiert ist.|
|[beg](#seekdir)|Gibt an, dass relativ zum Anfang einer Sequenz gesucht werden soll.|
|[binary](#openmode)|Gibt an, dass eine Datei als binärer Stream und nicht als Textstream gelesen werden soll.|
|[boolalpha](#fmtflags)|Gibt an, dass Objekte vom Typ **`bool`** als Namen (z. b. **`true`** und **`false`** ) statt als numerische Werte eingefügt oder extrahiert werden.|
|[cur](#seekdir)|Gibt an, dass in einer Sequenz relativ zur aktuellen Position gesucht werden soll.|
|[31.12.2012](#fmtflags)|Gibt an, dass ganzzahlige Werte im Dezimalformat eingefügt oder extrahiert werden sollen.|
|[end](#seekdir)|Gibt an, dass relativ zum Ende einer Sequenz gesucht werden soll.|
|[eofbit](#iostate)|Protokolliert beim Extrahieren aus einem Stream das Dateiende.|
|[failbit](#iostate)|Protokolliert einen Fehler beim Extrahieren eines gültigen Felds aus einem Stream.|
|[fixed](#fmtflags)|Gibt an, dass Gleitkommawerte im Festkommaformat (ohne Exponentenfeld) eingefügt werden sollen.|
|[floatfield](#fmtflags)|Eine Bitmaske, die als `fixed` &#124; `scientific` definiert ist|
|[goodbit](#iostate)|Kein Zustandsbit ist gesetzt.|
|[hex](#fmtflags)|Gibt an, dass ganzzahlige Werte im Hexadezimalformat eingefügt oder extrahiert werden sollen.|
|[in](#openmode)|Gibt die Extraktion aus einem Stream an.|
|[internal](#fmtflags)|Füllt bis zu einer Feldbreite auf, indem Füllzeichen an einem Punkt eingefügt werden, der sich intern in einem generierten numerischen Feld befindet.|
|[linken](#fmtflags)|Gibt linksbündige Ausrichtung an.|
|[31.10](#fmtflags)|Gibt an, dass ganzzahlige Werte im Oktalformat eingefügt oder extrahiert werden sollen.|
|[out](#openmode)|Gibt die Einfügung in einen Stream an.|
|[Richting](#fmtflags)|Gibt rechtsbündige Ausrichtung an.|
|[wissenschaftlich](#fmtflags)|Gibt an, dass Gleitkommawerte im wissenschaftlichen Format (mit Exponentenfeld) eingefügt werden sollen.|
|[showbase](#fmtflags)|Gibt die Einfügung eines Präfixes an, das die Basis eines generierten ganzzahigen Felds angibt.|
|[showpoint](#fmtflags)|Gibt die unbedingte Einfügung eines Dezimaltrennzeichens in einem generierten Gleitkommafeld an.|
|[Showpos](#fmtflags)|Gibt die Einfügung eines Pluszeichens (+) in einem nicht negativen generierten numerischen Feld an.|
|[skipws](#fmtflags)|Gibt an, dass führende Leerzeichen vor bestimmten Extraktionen übersprungen werden sollen.|
|[trunc](#openmode)|Gibt an, dass der Inhalt einer vorhandenen Datei gelöscht werden soll, wenn deren steuerndes Objekt erstellt wird.|
|[Unitbuf](#fmtflags)|Bewirkt, dass die Ausgabe nach jeder Einfügung geleert wird.|
|[uppercase](#fmtflags)|Gibt an, dass bei bestimmten Einfügevorgängen die Großbuchstaben eingefügt werden, die den Kleinbuchstaben entsprechen.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[Fehler](#failure)|Die Member-Klasse dient als Basisklasse für alle Ausnahmen, die von der Element Funktion [Clear](../standard-library/basic-ios-class.md#clear) in class template [basic_ios](../standard-library/basic-ios-class.md)ausgelöst werden.|
|[flags](#flags)|Legt die aktuellen Flageinstellungen fest oder gibt sie zurück.|
|[getloc](#getloc)|Gibt das gespeicherte Gebietsschemaobjekt zurück.|
|[imbue](#imbue)|Ändert das Gebietsschema.|
|[Init](#init)|Erstellt die Standardobjekte, wenn Sie erstellt werden `iostream` .|
|[iword](#iword)|Weist einen als `iword` zu speichernden Wert zu.|
|[precision](#precision)|Gibt die Anzahl der anzuzeigenden Ziffern in einer Gleitkommazahl an.|
|[pword](#pword)|Weist einen als `pword` zu speichernden Wert zu.|
|[register_callback](#register_callback)|Gibt eine Rückruffunktion an.|
|[setf](#setf)|Legt die angegebenen Flags fest.|
|[sync_with_stdio](#sync_with_stdio)|Stellt sicher, dass `iostream` und C-Lauf Zeit Bibliotheks Vorgänge in der Reihenfolge auftreten, in der Sie im Quellcode angezeigt werden.|
|[unsetf](#unsetf)|Bewirkt, dass die angegebenen Flags deaktiviert werden.|
|[width](#width)|Legt die Länge des Ausgabestreams fest.|
|[xalloc](#xalloc)|Gibt an, dass eine Variable Teil des Streams sein soll.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator =](#op_eq)|Der Zuweisungsoperator für `ios_base`-Objekte.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<ios>

**Namespace:** std

## <a name="event"></a><a name="event"></a> -Ereignis

Gibt Ereignistypen an.

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Aufzählungstyp, der ein Objekt beschreibt, das ein Rückrufereignis speichern kann, das als Argument für eine Funktion verwendet wird, die mit [register_callback](#register_callback) registriert wurde. Die unterschiedlichen Ereigniswerte lauten:

- `copyfmt_event`zum Identifizieren eines Rückrufs, der am Ende eines Aufrufs von [Copyfmt](../standard-library/basic-ios-class.md#copyfmt)auftritt, kurz bevor die [Ausnahme Maske](../standard-library/ios-base-class.md) kopiert wird.

- `erase_event`, um einen Rückruf zu identifizieren, der am Anfang eines Aufrufs von [Copyfmt](../standard-library/basic-ios-class.md#copyfmt)oder am Anfang eines Aufrufs des Dekonstruktors für ** \* dieses**auftritt.

- `imbue_event`, um einen Rückruf zu identifizieren, der am Ende eines Aufrufs von [imbue](#imbue)auftritt, kurz bevor die Funktion zurückgegeben wird.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie unter [register_callback](#register_callback).

## <a name="event_callback"></a><a name="event_callback"></a> event_callback

Beschreibt eine Funktion, die an [register_call](#register_callback) übergeben wird.

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>Parameter

*_E*\
Das [Ereignis](#event).

*_Base*\
Der Stream, in dem das Ereignis aufgerufen wurde.

*_I*\
Eine benutzerdefinierte Nummer.

### <a name="remarks"></a>Bemerkungen

Der Typ definiert einen Zeiger auf eine Funktion, die mit [register_callback](#register_callback) registriert werden kann. Der Typ der Funktion darf keine Ausnahme auslösen.

### <a name="example"></a>Beispiel

Ein Beispiel, in dem `event_callback` verwendet wird, finden Sie unter [register_call](#register_callback).

## <a name="failure"></a><a name="failure"></a> Fehler

Die Klasse `failure` definiert die Basisklasse für alle Typen von Objekten, die von Funktionen in der `iostreams`-Bibliothek als Ausnahmen ausgelöst wurden, um Fehler zu melden, die während der Streampuffervorgänge erkannt wurden.

```cpp
namespace std {
    class failure : public system_error {
    public:
        explicit failure(
            const string& _Message,
            const error_code& _Code = io_errc::stream);

        explicit failure(
            const char* str,
            const error_code& _Code = io_errc::stream);
    };
}
```

### <a name="remarks"></a>Bemerkungen

Der von `what()` zurückgegebene Wer ist eine Kopie von `_Message`, die möglicherweise mit einem auf `_Code` basierten Test erweitert wurde. Wenn kein `_Code` angegeben wird, lautet der Standardwert `make_error_code(io_errc::stream)`.

### <a name="example"></a>Beispiel

```cpp
// ios_base_failure.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.exceptions(ios::failbit);
    try
    {
        file.open( "rm.txt", ios_base::in );
        // Opens nonexistent file for reading
    }
    catch( ios_base::failure f )
    {
        cout << "Caught an exception: " << f.what() << endl;
    }
}
```

```Output
Caught an exception: ios_base::failbit set
```

## <a name="flags"></a><a name="flags"></a> fahren

Legt die aktuellen Flageinstellungen fest oder gibt sie zurück.

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>Parameter

*"f"*\
Die neue Einstellung `fmtflags`.

### <a name="return-value"></a>Rückgabewert

Die vorherige oder aktuelle Einstellung `fmtflags`.

### <a name="remarks"></a>Bemerkungen

Eine Liste der Flags finden Sie unter [ios_base::fmtflags](#fmtflags).

Die erste Memberfunktion gibt die gespeicherten Formatflags zurück. Die zweite Member-Funktion speichert *Fmtfl* in den Formatflags und gibt ihren vorherigen gespeicherten Wert zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_base_flags.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    cout << cout.flags( ) << endl;
    cout.flags( ios::dec | ios::boolalpha );
    cout << cout.flags( );
}
```

```Output
513
16896
```

## <a name="fmtflags"></a><a name="fmtflags"></a> Fmtflags

Konstanten, mit denen das Aussehen der Ausgabe angegeben wird.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type fmtflags;
   static const fmtflags boolalpha;
   static const fmtflags dec;
   static const fmtflags fixed;
   static const fmtflags hex;
   static const fmtflags internal;
   static const fmtflags left;
   static const fmtflags oct;
   static const fmtflags right;
   static const fmtflags scientific;
   static const fmtflags showbase;
   static const fmtflags showpoint;
   static const fmtflags showpos;
   static const fmtflags skipws;
   static const fmtflags unitbuf;
   static const fmtflags uppercase;
   static const fmtflags adjustfield;
   static const fmtflags basefield;
   static const fmtflags floatfield;
   // ...
};
```

### <a name="remarks"></a>Bemerkungen

Unterstützt die Manipulatoren in [ios](../standard-library/ios.md).

Der Typ ist ein Bitmaskentyp, der ein Objekt beschreibt, das Formatflags speichern kann. Die unterschiedlichen Flagwerte (Elemente) sind:

- `dec`, um ganzzahlige Werte im Dezimalformat einzufügen oder zu extrahieren.

- `hex`, um ganzzahlige Werte im Hexadezimalformat einzufügen oder zu extrahieren.

- `oct`, um ganzzahlige Werte im Oktalformat einzufügen oder zu extrahieren.

- `showbase`, um ein Präfix einzufügen, das die Basis eines generierten ganzzahligen Felds angibt.

- `internal`, um nach Bedarf bis zu einer Feldbreite aufzufüllen, indem Füllzeichen an einem Punkt eingefügt werden, der sich intern in einem generierten numerischen Feld befindet. (Informationen zum Festlegen der Feldbreite finden Sie unter [`setw`](../standard-library/iomanip-functions.md#setw) ).

- `left`, um nach Bedarf bis zu einer Feldbreite aufzufüllen, indem Füllzeichen am Ende eines generierten Feld angefügt werden (linksbündig ausrichten).

- `right`, um nach Bedarf bis zu einer Feldbreite aufzufüllen, indem Füllzeichen am Anfang eines generierten Feld eingefügt werden (rechtsbündig ausrichten).

- `boolalpha`, um Objekte vom Typ **`bool`** als Namen (z. b. **`true`** und **`false`** ) statt als numerische Werte einzufügen oder zu extrahieren.

- `fixed`, um Gleitkommawerte im Festkommaformat (ohne Exponentenfeld) einzufügen.

- `scientific`, um Gleitkommawerte im wissenschaftlichen Format (mit Exponentenfeld) einzufügen.

- `showpoint`, um ein Dezimaltrennzeichen unbedingt in ein generiertes Gleitkommafeld einzufügen.

- `showpos`, um ein Pluszeichens in ein generiertes nicht negatives numerisches Feld einzufügen.

- `skipws`, um führende Leerzeichen vor bestimmten Extraktionen zu überspringen.

- `unitbuf`, um die Ausgabe nach jedem Einfügevorgang zu leeren.

- `uppercase`, um bei bestimmten Einfügevorgängen die Großbuchstaben einzufügen, die den Kleinbuchstaben entsprechen.

Zusätzlich gibt es weitere nützliche Werte:

- `adjustfield`, eine Bitmaske, die als `internal` &#124; `left` &#124; `right` definiert ist

- `basefield`, definiert als `dec` &#124; `hex` &#124; `oct`

- `floatfield`, definiert als `fixed` &#124; `scientific`

Beispiele für Funktionen, die diese Formatflags ändern, finden Sie unter [\<iomanip>](../standard-library/iomanip.md) .

## <a name="getloc"></a><a name="getloc"></a> getloc

Gibt das gespeicherte Gebietsschemaobjekt zurück.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Rückgabewert

Das gespeicherte Gebietsschemaobjekt.

### <a name="example"></a>Beispiel

```cpp
// ios_base_getlock.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << cout.getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="imbue"></a><a name="imbue"></a> imbue

Ändert das Gebietsschema.

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parameter

*_Loc*\
Die neue Benutzergebietsschema-Einstellung.

### <a name="return-value"></a>Rückgabewert

Das vorherige Gebietsschema.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion speichert *_Loc* im locale-Objekt und meldet dann das Rückruf Ereignis und `imbue_event` . Es gibt den zuletzt gespeicherten Wert zurück.

### <a name="example"></a>Beispiel

Ein Beispiel finden Sie unter [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue).

## <a name="init"></a><a name="init"></a> Init

Erstellt die Standardobjekte, wenn Sie erstellt werden `iostream` .

```cpp
class Init { };
```

### <a name="remarks"></a>Bemerkungen

Die-Klasse beschreibt ein Objekt, dessen Konstruktion sicherstellt, dass die Standard `iostream` Objekte ordnungsgemäß erstellt werden, sogar vor der Ausführung eines Konstruktors für ein beliebiges statisches Objekt.

## <a name="ios_base"></a><a name="ios_base"></a> ios_base

Konstruiert ios_base-Objekte.

```cpp
ios_base();
```

### <a name="remarks"></a>Bemerkungen

Der (geschützte) Konstruktor führt keine Aktion aus. Ein späterer Rückruf von `basic_ios::` [Init](../standard-library/basic-ios-class.md#init) muss das Objekt initialisieren, bevor es sicher zerstört werden kann. Daher ist die einzige sichere Verwendung für Class ios_base als Basisklasse für Klassen Vorlagen [basic_ios](../standard-library/basic-ios-class.md).

## <a name="iostate"></a><a name="iostate"></a> iostate

Der Typ der Konstanten, die den Zustand eines Streams beschreiben.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Bitmaskentyp, der ein Objekt beschreibt, das Informationen zum Streamzustand speichern kann. Die unterschiedlichen Flagwerte (Elemente) sind:

- `badbit` zur Protokollierung eines Verlusts der Integrität des Streampuffers.

- `eofbit` zur Protokollierung des Dateiendes beim Extrahieren aus einem Stream.

- `failbit` zur Protokollierung eines Fehlers beim Extrahieren eines gültigen Felds aus einem Stream.

Außerdem ist ein nützlicher Wert `goodbit` , bei dem keine der zuvor erwähnten Bits festgelegt ist ( `goodbit` garantiert NULL ist).

## <a name="iword"></a><a name="iword"></a> iword

Weist einen als `iword` zu speichernden Wert zu.

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>Parameter

*idx*\
Der Index des als `iword` zu speichernden Werts.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf das *IDX* -Element des erweiterbaren Arrays mit Elementen des Typs zurück **`long`** . Alle Elemente sind tatsächlich vorhanden und speichern zunächst den Wert 0. Der zurückgegebene Verweis ist nach dem nächsten-Rückruf `iword` für das-Objekt ungültig, nachdem das-Objekt durch einen `basic_ios::` [Copyfmt](../standard-library/basic-ios-class.md#copyfmt)-Befehl geändert wurde oder nachdem das Objekt zerstört wurde.

Wenn *IDX* negativ ist oder für das-Element ein eindeutiger Speicherplatz verfügbar ist, ruft die Funktion auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` und gibt einen Verweis zurück, der möglicherweise nicht eindeutig ist.

Zum Abrufen eines eindeutigen Indexes, der für alle Objekte vom Typ verwendet `ios_base` werden soll, rufen Sie auf [`xalloc`](#xalloc) .

### <a name="example"></a>Beispiel

[`xalloc`](#xalloc)Ein Beispiel für die Verwendung von finden Sie unter `iword` .

## <a name="openmode"></a><a name="openmode"></a> OpenMode

Beschreibt, wie mit einem Stream interagiert wird.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Bemerkungen

Der-Typ ist ein `bitmask type` , der ein Objekt beschreibt, das den Öffnungs Modus für mehrere-Objekte speichern kann `iostream` . Die unterschiedlichen Flagwerte (Elemente) sind:

- `app`, um vor jeder Einfügung bis zum Ende eines Streams zu suchen.

- `ate`, um das Ende eines Streams zu suchen, wenn das steuernde Objekt erstmalig erstellt wird.

- `binary`, wenn eine Datei als binärer Stream und nicht als Textstream gelesen werden soll.

- `in`, um die Extraktion aus einem Stream zuzulassen.

- `out`, um das Einfügen in einen Stream zuzulassen.

- `trunc`, wenn der Inhalt einer vorhandenen Datei gelöscht werden soll, wenn das steuernde Objekt erstellt wird.

### <a name="example"></a>Beispiel

```cpp
// ios_base_openmode.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
}
```

## <a name="operator"></a><a name="op_eq"></a> Operator =

Der Zuweisungsoperator für ios_base-Objekte.

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein Objekt vom Typ `ios_base`.

### <a name="return-value"></a>Rückgabewert

Das Objekt, an das zugewiesen wird.

### <a name="remarks"></a>Bemerkungen

Der Operator kopiert die gespeicherte Formatinformation und erstellt gleichzeitig eine Kopie von erweiterbaren Arrays. Anschließend wird ** \* diese**zurückgegeben. Bitte beachten Sie, dass die Aufrufliste nicht kopiert wird.

Dieser Operator wird nur von `ios_base` abgeleiteten Klassen verwendet.

## <a name="precision"></a><a name="precision"></a> präziser

Gibt die Anzahl der anzuzeigenden Ziffern in einer Gleitkommazahl an.

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>Parameter

*_Prec*\
Die Anzahl der anzuzeigenden signifikanten Stellen, oder die Anzahl der Stellen nach dem Komma bei fester Schreibweise.

### <a name="return-value"></a>Rückgabewert

Die erste Memberfunktion gibt die gespeicherte [Anzeigegenauigkeit](../standard-library/ios-base-class.md) zurück. Die zweite Element Funktion speichert *_Prec* in der Anzeige Genauigkeit und gibt ihren vorherigen gespeicherten Wert zurück.

### <a name="remarks"></a>Bemerkungen

Gleitkommazahlen werden mit festen Schreibweisen mit [fixed](../standard-library/ios-functions.md#fixed) angezeigt.

### <a name="example"></a>Beispiel

```cpp
// ios_base_precision.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    float i = 31.31234F;

    cout.precision( 3 );
    cout << i << endl;          // display three significant digits
    cout << fixed << i << endl; // display three digits after decimal
                                // point
}
```

```Output
31.3
31.312
```

## <a name="pword"></a><a name="pword"></a> pword

Weist einen als `pword` zu speichernden Wert zu.

```cpp
void *& pword(int index);
```

### <a name="parameters"></a>Parameter

*Sin*\
Der Index des als `pword` zu speichernden Werts.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt einen Verweis auf den Element *Index* des erweiterbaren Arrays mit Elementen des **`void`** typzeigers zurück. Alle Elemente sind tatsächlich vorhanden und speichern zunächst den NULL-Zeiger. Der zurückgegebene Verweis ist nach dem nächsten-Rückruf `pword` für das-Objekt ungültig, nachdem das-Objekt durch einen `basic_ios::` [Copyfmt](../standard-library/basic-ios-class.md#copyfmt)-Befehl geändert wurde oder nachdem das Objekt zerstört wurde.

Wenn der *Index* negativ ist oder für das Element ein eindeutiger Speicherplatz verfügbar ist, ruft die Funktion auf [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` und gibt einen Verweis zurück, der möglicherweise nicht eindeutig ist.

Zum Abrufen eines eindeutigen Indexes, der für alle Objekte vom Typ verwendet `ios_base` werden soll, rufen Sie auf [`xalloc`](#xalloc) .

### <a name="example"></a>Beispiel

Unter [`xalloc`](#xalloc) finden Sie ein Beispiel für die Verwendung von `pword`.

## <a name="register_callback"></a><a name="register_callback"></a> register_callback

Gibt eine Rückruffunktion an.

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>Parameter

*PFN*\
Ein Zeiger auf die Rückruffunktion.

*idx*\
Eine benutzerdefinierte Nummer.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion schiebt das Paar `{pfn, idx}` auf den gespeicherten Rückruf Stapel- [Rückruf Stapel](../standard-library/ios-base-class.md). Wenn ein Rückruf Ereignis ( **EV** ) gemeldet wird, werden die Funktionen durch den Ausdruck in umgekehrter Reihenfolge der Registrierung aufgerufen `(*pfn)(ev, *this, idx)` .

### <a name="example"></a>Beispiel

```cpp
// ios_base_register_callback.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void callback1( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback1" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

void callback2( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback2" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

int main( )
{
    // Make sure the imbue will not throw an exception
    // assert( setlocale( LC_ALL, "german" )!=NULL );

    cout.register_callback( callback1, 0 );
    cin.register_callback( callback2, 0 );

    try
    {
        // If no exception because the locale's not found,
        // generate an imbue_event on callback1
        cout.imbue(locale("german"));
    }
    catch(...)
    {
        cout << "exception" << endl;
    }

    // This will
    // (1) erase_event on callback1
    // (2) copyfmt_event on callback2
    cout.copyfmt(cin);

    // We get two erase events from callback2 at the end because
    // both cin and cout have callback2 registered when cin and cout
    // are destroyed at the end of program.
}
```

```Output
in callback1
an imbue event
in callback1
an erase event
in callback2
an copyfmt event
in callback2
an erase event
in callback2
an erase event
```

## <a name="seekdir"></a><a name="seekdir"></a> seekdir

Gibt den Startpunkt für Offsetvorgänge an.

```cpp
namespace std {
    class ios_base {
    public:
        typedef implementation-defined-enumerated-type seekdir;
        static const seekdir beg;
        static const seekdir cur;
        static const seekdir end;
        // ...
    };
}
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein enumerierter Typ, der ein Objekt beschreibt, das den Suchmodus speichern kann, der als Argument für die Member-Funktionen mehrerer Klassen verwendet wird `iostream` . Die unterschiedlichen Flagwerte sind:

- `beg`zum Suchen (Ändern der aktuellen Lese-oder Schreibposition) relativ zum Anfang einer Sequenz (Array, Stream oder Datei).

- `cur`, um relativ zur aktuellen Position innerhalb einer Sequenz zu suchen.

- `end`, wenn relativ zum Ende einer Sequenz gesucht werden soll.

### <a name="example"></a>Beispiel

```cpp
// ios_base_seekdir.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
    file.seekp( 0, ios_base::beg );
    file << "a";
    file.seekp( 0, ios_base::end );
    file << "a";
}
```

## <a name="setf"></a><a name="setf"></a> Setf

Legt die angegebenen Flags fest.

```cpp
fmtflags setf(
    fmtflags _Mask
);
fmtflags setf(
    fmtflags _Mask,
    fmtflags _Unset
);
```

### <a name="parameters"></a>Parameter

*_Mask*\
Die Flags, die eingeschaltet werden sollen.

*_Unset*\
Die Flags, die deaktiviert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die vorherigen Formatflags

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion ruft effektiv [Flags](#flags) auf `(_Mask | _Flags)` (legen Sie ausgewählte Bits fest) und gibt dann die vorherigen Formatflags zurück. Die zweite Member-Funktion ruft effektiv `flags(_Mask & fmtfl, flags & ~_Mask)` (ersetzen Sie die ausgewählten Bits unter einer Maske ab) und gibt dann die vorherigen Formatflags zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_base_setf.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    int i = 10;
    cout << i << endl;

    cout.unsetf( ios_base::dec );
    cout.setf( ios_base::hex );
    cout << i << endl;

    cout.setf( ios_base::dec );
    cout << i << endl;
    cout.setf( ios_base::hex, ios_base::dec );
    cout << i << endl;
}
```

## <a name="sync_with_stdio"></a><a name="sync_with_stdio"></a> sync_with_stdio

Stellt sicher, dass `iostream` und C-Lauf Zeit Bibliotheks Vorgänge in der Reihenfolge auftreten, in der Sie im Quellcode angezeigt werden.

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>Parameter

*_Sync*\
Gibt an, ob alle Streams mit synchronisiert sind `stdio` .

### <a name="return-value"></a>Rückgabewert

Vorherige Einstellung für diese Funktion.

### <a name="remarks"></a>Bemerkungen

Die statische Member-Funktion speichert ein `stdio` synchronisierungsflag, das anfänglich ist **`true`** . Wenn **`true`** , stellt dieses Flag sicher, dass Vorgänge in derselben Datei zwischen den [`iostreams`](../standard-library/iostreams-conventions.md) Funktionen und den in der C++-Standard Bibliothek definierten Funktionen ordnungsgemäß synchronisiert werden. Andernfalls ist die Synchronisierung möglicherweise nicht gewährleistet, aber die Leistung kann verbessert werden. Die Funktion speichert *_Sync* im `stdio` synchronisierungsflag und gibt ihren vorherigen gespeicherten Wert zurück. Sie können Sie nur zuverlässig anrufen, bevor Sie Vorgänge für die Standardstreams durchführen.

## <a name="unsetf"></a><a name="unsetf"></a> Unsetf

Bewirkt, dass die angegebenen Flags deaktiviert werden.

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>Parameter

*_Mask*\
Die Flags, die ausgeschaltet werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft effektiv [Flags](#flags)( `~` *_Mask* **& Flags**) auf (Löschen Sie ausgewählte Bits).

### <a name="example"></a>Beispiel

Unter [ios_base:: setf](#setf) finden Sie ein Beispiel für die Verwendung von `unsetf` .

## <a name="width"></a><a name="width"></a> Breite

Legt die Länge des Ausgabestreams fest.

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>Parameter

*_Wide*\
Die gewünschte Größe des Ausgabestreams.

### <a name="return-value"></a>Rückgabewert

Die Einstellung für die aktuelle Breite.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion gibt die Breite des gespeicherten Felds zurück. Die zweite Member-Funktion speichert *_Wide* in der Feldbreite und gibt ihren vorherigen gespeicherten Wert zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_base_width.cpp
// compile with: /EHsc
#include <iostream>

int main( ) {
    using namespace std;

    cout.width( 20 );
    cout << cout.width( ) << endl;
    cout << cout.width( ) << endl;
}
```

```Output
20
0
```

## <a name="xalloc"></a><a name="xalloc"></a> xalloc

Gibt an, dass eine Variable Teil des Streams ist.

```cpp
static int xalloc( );
```

### <a name="return-value"></a>Rückgabewert

Die statische Member-Funktion gibt einen gespeicherten statischen Wert zurück, der bei jedem-Rückruf Inkrementen erhöht wird.

### <a name="remarks"></a>Bemerkungen

Sie können den Rückgabewert als eindeutiges Index Argument verwenden, wenn Sie die Member-Funktionen [`iword`](#iword) oder aufrufen [`pword`](#pword) .

### <a name="example"></a>Beispiel

```cpp
// ios_base_xalloc.cpp
// compile with: /EHsc
// Lets you store user-defined information.
// iword, jword, xalloc
#include <iostream>

int main( )
{
    using namespace std;

    static const int i = ios_base::xalloc();
    static const int j = ios_base::xalloc();
    cout.iword( i ) = 11;
    cin.iword( i ) = 13;
    cin.pword( j ) = "testing";
    cout << cout.iword( i ) << endl;
    cout << cin.iword( i ) << endl;
    cout << ( char * )cin.pword( j ) << endl;
}
```

```Output
11
13
testing
```

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
