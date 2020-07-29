---
title: basic_ios-Klasse
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: b730933879df04d2455b5eae6fc5abf16bbf4484
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219273"
---
# <a name="basic_ios-class"></a>basic_ios-Klasse

Die Klassen Vorlage beschreibt die Speicher-und Element Funktionen, die sowohl für die Eingabedaten Ströme (von Klassen Vorlagen [basic_istream](../standard-library/basic-istream-class.md)) als auch für die Ausgabestreams (der Klassen Vorlage [basic_ostream](../standard-library/basic-ostream-class.md)), die von den Vorlagen Parametern abhängen, gemeinsam (In der Klasse [ios_base](../standard-library/ios-base-class.md) werden die allgemeinen und nicht von Vorlagen Parametern abhängigen Elemente beschrieben.) Ein Objekt der Klasse **basic_ios \<class Elem, class Traits> ** unterstützt die Steuerung eines Streams mit Elementen des Typs `Elem` , dessen Zeichen Merkmale von der Klasse bestimmt werden `Traits` .

## <a name="syntax"></a>Syntax

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Parameter

*Elem*\
Ein Typ.

*Aufweisen*\
Eine Variable des Typs `char_traits`.

## <a name="remarks"></a>Bemerkungen

Ein Objekt der Klasse **basic_ios \<class Elem, class Traits> ** Stores:

- Ein Tie-Zeiger auf ein Objekt vom Typ [basic_istream](../standard-library/basic-istream-class.md) **\<Elem, Traits>** .

- Ein streampufferzeiger auf ein Objekt vom Typ [basic_streambuf](../standard-library/basic-streambuf-class.md) **\<Elem, Traits >** .

- [Formatierungsinformationen](../standard-library/ios-base-class.md).

- [Streamzustandsinformationen](../standard-library/ios-base-class.md) in einem Basisobjekt des Typs [ios_base](../standard-library/ios-base-class.md).

- Ein Füllzeichen in einem Objekt des Typs `char_type`.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[basic_ios](#basic_ios)|Erstellt die `basic_ios`-Klasse.|

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[char_type](#char_type)|Ein Synonym für den Vorlagenparameter `Elem`.|
|[int_type](#int_type)|Ein Synonym für `Traits::int_type`.|
|[off_type](#off_type)|Ein Synonym für `Traits::off_type`.|
|[pos_type](#pos_type)|Ein Synonym für `Traits::pos_type`.|
|[traits_type](#traits_type)|Ein Synonym für den Vorlagenparameter `Traits`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Ungültig](#bad)|Kennzeichnet einen Verlust der Integrität des Streampuffers.|
|[Löschen](#clear)|Löscht alle Fehlerflags.|
|[copyfmt](#copyfmt)|Kopiert Flags aus einem Stream in einen anderen.|
|[EOF](#eof)|Gibt an, dass das Ende eines Streams erreicht wurde.|
|[exceptions](#exceptions)|Gibt an, welche Ausnahmen vom Datenstrom ausgelöst werden.|
|[UN](#fail)|Kennzeichnet einen Fehler beim Extrahieren eines gültigen Felds aus einem Stream.|
|[erfüllen](#fill)|Gibt das Zeichen an oder zurück, das verwendet wird, wenn der Text nicht so breit ist wie der Stream.|
|[Glück](#good)|Gibt an, dass der Stream in einem guten Zustand ist.|
|[imbue](#imbue)|Ändert das Gebietsschema.|
|[init](#init)|Wird von `basic_ios`-Konstruktoren aufgerufen.|
|[move](#move)|Verschiebt alle Werte, mit Ausnahme des Zeigers auf den Streampuffer, aus dem Parameter in das aktuelle Objekt.|
|[narrow](#narrow)|Sucht das entsprechende Zeichen zu einem angegebenen `char_type`.|
|[rdbuf](#rdbuf)|Leitet einen Stream in den angegebenen Puffer weiter.|
|[rdstate](#rdstate)|Liest den Status der Bits für Flags.|
|[set_rdbuf](#set_rdbuf)|Weist einen Streampuffer zu, der der Lesepuffer für dieses Streamobjekt sein soll.|
|[setstate](#setstate)|Legt zusätzliche Flags fest.|
|[swap](#swap)|Tauscht die Werte in diesem `basic_ios`-Objekt gegen die Werte eines anderen `basic_ios`-Objekts aus. Die Zeiger auf die Streampuffer werden nicht ausgetauscht.|
|[tie](#tie)|Stellt sicher, dass ein Stream vor einem anderen Stream verarbeitet wird.|
|[widen](#widen)|Sucht den entsprechenden `char_type` zu einem angegebenen Zeichen.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[explicit operator bool](#op_bool)|Ermöglicht die Verwendung eines- `basic_ios` Objekts als **`bool`** . Die automatische Typkonvertierung wird deaktiviert, um häufig vorkommende unbeabsichtigte Nebeneffekte zu verhindern.|
|[operator void *](#op_void_star)|Gibt an, ob der Stream weiterhin brauchbar ist.|
|[KOM!](#op_not)|Gibt an, ob der Stream nicht unbrauchbar ist.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<ios>

**Namespace:** std

## <a name="basic_iosbad"></a><a name="bad"></a>basic_ios:: Bad

Kennzeichnet einen Verlust der Integrität des Streampuffers.

```cpp
bool bad() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn ungleich `rdstate & badbit` NULL ist, andernfalls **`false`** .

Weitere Informationen zu `badbit` finden Sie unter [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Beispiel

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_iosbasic_ios"></a><a name="basic_ios"></a>basic_ios:: basic_ios

Erstellt die basic_ios-Klasse.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Parameter

*SB*\
Standardpuffer zum Speichern von Eingabe- oder Ausgabeelementen.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor initialisiert die Memberobjekte durch Aufrufen von [init](#init)(_ *Sb*). Der zweite (geschützte) Konstruktor initialisiert seine Memberobjekte nicht. Ein späterer-Rückruf `init` muss das-Objekt initialisieren, bevor es sicher zerstört werden kann.

## <a name="basic_ioschar_type"></a><a name="char_type"></a>basic_ios:: char_type

Ein Synonym für den Vorlagenparameter `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="basic_iosclear"></a><a name="clear"></a>basic_ios:: Clear

Löscht alle Fehlerflags.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Parameter

*Land*\
Optionale Die Flags, die Sie nach dem Löschen aller Flags festlegen möchten. Wird standardmäßig auf `goodbit` festgelegt.

*Reraise*\
Optionale Gibt an, ob die Ausnahme erneut ausgelöst werden soll. Der Standardwert ist **`false`** (die Ausnahme wird nicht erneut ausgelöst).

### <a name="remarks"></a>Bemerkungen

Die Flags lauten `goodbit` , `failbit` , `eofbit` und `badbit` . Testen Sie auf diese Flags mit [good](#good), [bad](#bad), [eof](#eof) und [fail](#fail).

Die Memberfunktion ersetzt die gespeicherten Informationen zum Streamstatus durch:

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

Wenn `state` **&** [Ausnahmen](#exceptions) ungleich NULL sind, wird ein Objekt der Klasse [Failure](../standard-library/ios-base-class.md#failure)ausgelöst.

### <a name="example"></a>Beispiel

Beispiele für die Verwendung von finden Sie unter [Rdstate](#rdstate) und [getline](../standard-library/string-functions.md#getline) `clear` .

## <a name="basic_ioscopyfmt"></a><a name="copyfmt"></a>basic_ios:: copyf

Kopiert Flags aus einem Stream in einen anderen.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Stream, dessen Flags Sie kopieren möchten.

### <a name="return-value"></a>Rückgabewert

Das- **`this`** Objekt für den Stream, in den die Flags kopiert werden.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion meldet das ** \_ Ereignis zum Löschen**von Rückruf Ereignissen. Anschließend werden Sie von *Rechts* in das Füll Zeichen, den Tie-Zeiger und die Formatierungsinformationen kopiert. ** \* ** Vor dem Ändern der Ausnahme Maske meldet Sie das Rückruf Ereignis `copyfmt_event` . Wenn **state &**[exceptions](#exceptions) nach Abschluss der Kopie ungleich null ist, ruft die Funktion effektiv [clear](#clear) mit dem Argument [rdstate](#rdstate) auf. ** \* Dies**wird zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}
```

## <a name="basic_ioseof"></a><a name="eof"></a>basic_ios:: EOF

Gibt an, dass das Ende eines Streams erreicht wurde.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Ende des Streams erreicht wurde, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt zurück, **`true`** Wenn [Rdstate](#rdstate) ungleich `& eofbit` 0 (null) ist. Weitere Informationen zu `eofbit` finden Sie unter [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Beispiel

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="basic_iosexceptions"></a><a name="exceptions"></a>basic_ios:: Exceptions

Gibt an, welche Ausnahmen vom Datenstrom ausgelöst werden.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Parameter

*"Netwexcept"*\
Die Flags, die eine Ausnahme auslösen sollen.

### <a name="return-value"></a>Rückgabewert

Die Flags, die aktuell angegeben sind, um eine Ausnahme für den Stream auszulösen.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion gibt die gespeicherte Ausnahmemaske zurück. Die zweite Memberfunktion speichert *_Except* in der Ausgabemaske und gibt den zuletzt gespeicherten Wert zurück. Beachten Sie, dass das Speichern einer neuen Ausgabemaske ebenso wie der Aufruf von [clear](#clear)( [rdstate](#rdstate) ) eine Ausnahme auslösen kann.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="basic_iosfail"></a><a name="fail"></a>basic_ios:: Fail

Kennzeichnet einen Fehler beim Extrahieren eines gültigen Felds aus einem Stream.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn [Rdstate](#rdstate) ungleich `& (badbit|failbit)` 0 (null) ist, andernfalls **`false`** .

Weitere Informationen zu `failbit` finden Sie unter [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Beispiel

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}
```

## <a name="basic_iosfill"></a><a name="fill"></a>basic_ios:: Fill

Gibt das Zeichen an oder zurück, das verwendet wird, wenn der Text nicht so breit ist wie der Stream.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Parameter

*Char*\
Das Zeichen, das als das Füllzeichen dienen soll.

### <a name="return-value"></a>Rückgabewert

Das aktuelle Füllzeichen.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion gibt die gespeicherten Füllzeichen zurück. Die zweite Member-Funktion speichert *char* im Füll Zeichen und gibt den vorherigen gespeicherten Wert zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="basic_iosgood"></a><a name="good"></a>basic_ios:: Good

Gibt an, dass der Stream in einem guten Zustand ist.

```cpp
bool good() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn [Rdstate](#rdstate) `== goodbit` (keine Statusflags festgelegt sind), andernfalls **`false`** .

Weitere Informationen zu `goodbit` finden Sie unter [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Beispiel

Unter [basic_ios::bad](#bad) finden Sie ein Beispiel für die Verwendung von `good`.

## <a name="basic_iosimbue"></a><a name="imbue"></a>basic_ios:: imbue

Ändert das Gebietsschema.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Parameter

*A.a.o.*\
Eine lokale Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Das vorherige Gebietsschema.

### <a name="remarks"></a>Bemerkungen

Wenn [rdbuf](#rdbuf) kein NULL-Zeiger ist, ruft die Memberfunktion Folgendes auf:

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

In jedem Fall gibt sie [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*) zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="basic_iosinit"></a><a name="init"></a>basic_ios:: init

Wird von basic_ios-Konstruktoren aufgerufen.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Parameter

*_Sb*\
Standardpuffer zum Speichern von Eingabe- oder Ausgabeelementen.

*_Isstd*\
Gibt an, ob es sich um einen Standardstream handelt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion speichert Werte in allen Memberobjekten, sodass:

- [rdbuf](#rdbuf)*_Sb.* zurückgibt.

- [tie](#tie) einen NULL-Zeiger zurückgibt.

- [Rdstate](#rdstate) gibt [Goodbit](../standard-library/ios-base-class.md#iostate) zurück, wenn *_Sb* nicht NULL ist. Andernfalls wird [Badbit](../standard-library/ios-base-class.md#iostate)zurückgegeben.

- [Ausnahmen](#exceptions) gibt zurück `goodbit` .

- [flags](../standard-library/ios-base-class.md#flags)[skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags) zurückgibt.

- [width](../standard-library/ios-base-class.md#width) 0 zurückgibt.

- [precision](../standard-library/ios-base-class.md#precision) 6 zurückgibt.

- [fill](#fill) das Leerzeichen zurückgibt.

- [getloc](../standard-library/ios-base-class.md#getloc)`locale::classic` zurückgibt.

- [iword](../standard-library/ios-base-class.md#iword) null zurückgibt, und [pword](../standard-library/ios-base-class.md#pword) einen NULL-Zeiger für alle Argumentwerte zurückgibt.

## <a name="basic_iosint_type"></a><a name="int_type"></a>basic_ios:: int_type

Ein Synonym für `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_iosmove"></a><a name="move"></a>basic_ios:: Move

Verschiebt alle Werte, mit Ausnahme des Zeigers auf den Streampuffer, aus dem Parameter in das aktuelle Objekt.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Das `ios_base`-Objekt, aus dem Werte verschoben werden sollen.

### <a name="remarks"></a>Bemerkungen

Die geschützte Member-Funktion verschiebt *alle in gespeicherten Werte mit* **`*this`** Ausnahme des gespeicherten `stream buffer pointer` , das in der *rechten* Ecke unverändert ist und auf einen NULL-Zeiger in festgelegt ist **`*this`** . Der gespeicherte `tie pointer` wird auf einen NULL-Zeiger in der *rechten*Ecke festgelegt.

## <a name="basic_iosnarrow"></a><a name="narrow"></a>basic_ios:: Narrow

Sucht das entsprechende Zeichen zu einem angegebenen `char_type`.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Parameter

*Char*\
Der **`char`** zu konvertierende.

*Vorgegebene*\
Das **`char`** , das zurückgegeben werden soll, wenn keine Entsprechung gefunden wird.

### <a name="return-value"></a>Rückgabewert

Das-Äquivalent **`char`** zu einem angegebenen `char_type` .

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [Use_facet](../standard-library/basic-filebuf-class.md#open) \<ctype\<E> > ( [getloc](../standard-library/ios-base-class.md#getloc)()) zurück. `narrow` ( `Char`, `Default`).

### <a name="example"></a>Beispiel

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="basic_iosoff_type"></a><a name="off_type"></a>basic_ios:: off_type

Ein Synonym für `traits_type::off_type`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_iosoperator-void-"></a><a name="op_void_star"></a>basic_ios:: Operator void *

Gibt an, ob der Stream weiterhin brauchbar ist.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Rückgabewert

Der Operator gibt nur bei [fail](#fail) einen NULL-Zeiger zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="basic_iosoperator"></a><a name="op_not"></a>basic_ios:: Operator!

Gibt an, ob der Stream nicht unbrauchbar ist.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt [fail](#fail) zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="basic_iosoperator-bool"></a><a name="op_bool"></a>basic_ios:: Operator bool

Ermöglicht die Verwendung eines- `basic_ios` Objekts als **`bool`** . Die automatische Typkonvertierung wird deaktiviert, um häufig vorkommende unbeabsichtigte Nebeneffekte zu verhindern.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Bemerkungen

Der-Operator gibt einen Wert zurück, der **`false`** nur bei konvertiert werden konnte `fail()` . Der Rückgabetyp kann nur zu konvertiert **`bool`** werden, nicht zu `void *` oder zu anderen bekannten skalaren Typen.

## <a name="basic_iospos_type"></a><a name="pos_type"></a>basic_ios::p os_type

Ein Synonym für `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_iosrdbuf"></a><a name="rdbuf"></a>basic_ios:: Rdbuf

Leitet einen Stream in den angegebenen Puffer weiter.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Parameter

*_Sb*\
Ein Stream

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion gibt den gespeicherten Streampufferzeiger zurück.

Die zweite Member-Funktion speichert *_Sb* im gespeicherten streampufferzeiger und gibt den zuvor gespeicherten Wert zurück.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="basic_iosrdstate"></a><a name="rdstate"></a>basic_ios:: Rdstate

Liest den Status der Bits für Flags.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Rückgabewert

Die gespeicherten Informationen zum Status des Streams.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="basic_iossetstate"></a><a name="setstate"></a>basic_ios:: SetState

Legt zusätzliche Flags fest.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Parameter

*_State*\
Zusätzlich festzulegende Flags.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft effektiv [clear](#clear)(_ *State* &#124; [rdstate](#rdstate)) auf.

### <a name="example"></a>Beispiel

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="basic_iosset_rdbuf"></a><a name="set_rdbuf"></a>basic_ios:: set_rdbuf

Weist einen Streampuffer zu, der der Lesepuffer für dieses Streamobjekt sein soll.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Parameter

*strbuf*\
Der Streampuffer, der zum Lesepuffer werden soll.

### <a name="remarks"></a>Bemerkungen

Die geschützte Member-Funktion speichert " *strinbuf* " in der `stream buffer pointer` . Es wird nicht aufgerufen `clear` .

## <a name="basic_iostie"></a><a name="tie"></a>basic_ios:: Tie

Stellt sicher, dass ein Stream vor einem anderen Stream verarbeitet wird.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Parameter

*SRT*\
Ein Stream

### <a name="return-value"></a>Rückgabewert

Die erste Memberfunktion gibt den gespeicherten tie-Zeiger zurück. Die zweite Member-Funktion speichert *Str* im Tie-Zeiger und gibt den vorherigen gespeicherten Wert zurück.

### <a name="remarks"></a>Bemerkungen

`tie` bewirkt, dass zwei Streams so synchronisiert werden, dass Vorgänge für einen Stream erst stattfinden, wenn sie für den anderen Stream abgeschlossen sind.

### <a name="example"></a>Beispiel

In diesem Beispiel wird durch Verbinden von „cin“ mit „cout“ sichergestellt, dass die Zeichenfolge „Enter a number:“ (Geben Sie eine Zahl ein) die Konsole erreicht, bevor die Zahl selbst aus „cin“ extrahiert wird. Dadurch wird ausgeschlossen, dass die Zeichenfolge „Enter a number:“ sich noch im Puffer befindet, wenn die Zahl gelesen wird, sodass wir sichergehen können, dass der Benutzer eine Eingabeaufforderung erhält, auf die er reagieren kann. Standardmäßig sind „cin“ und „cout“ verbunden.

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="basic_iostraits_type"></a><a name="traits_type"></a>basic_ios:: traits_type

Ein Synonym für den Vorlagenparameter `Traits`.

```cpp
typedef Traits traits_type;
```

## <a name="basic_ioswiden"></a><a name="widen"></a>basic_ios:: ausweiten

Sucht den entsprechenden `char_type` zu einem angegebenen **`char`** .

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Parameter

*Char*\
Das zu konvertierende Zeichen.

### <a name="return-value"></a>Rückgabewert

Sucht den entsprechenden `char_type` zu einem angegebenen **`char`** .

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt [Use_facet](../standard-library/basic-filebuf-class.md#open) <  **CType** - \< **E**> > ( [getloc](../standard-library/ios-base-class.md#getloc)) zurück. `widen`( `Char`).

### <a name="example"></a>Beispiel

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}
```

## <a name="basic_iosswap"></a><a name="swap"></a>basic_ios:: Swap

Tauscht die Werte in diesem `basic_ios`-Objekt gegen die Werte eines anderen `basic_ios`-Objekts aus. Die Zeiger auf die Streampuffer werden jedoch nicht ausgetauscht.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Das `basic_ios`-Objekt, das zum Austauschen von Werten verwendet wird.

### <a name="remarks"></a>Bemerkungen

Die geschützte Member-Funktion tauscht alle Werte, die *right* in gespeichert sind, mit **`*this`** Ausnahme der gespeicherten aus `stream buffer pointer` .

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
