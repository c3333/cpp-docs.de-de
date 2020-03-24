---
title: '&lt;ios&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::defaultfloat
- xiosbase/std::boolalpha
- xiosbase/std::dec
- ios/std::fixed
- ios/std::hex
- ios/std::internal
- ios/std::left
- ios/std::noboolalpha
- ios/std::noshowbase
- ios/std::noshowpoint
- ios/std::noshowpos
- ios/std::noskipws
- ios/std::nounitbuf
- ios/std::nouppercase
- ios/std::oct
- ios/std::right
- ios/std::scientific
- ios/std::showbase
- ios/std::showpoint
- ios/std::showpos
- ios/std::skipws
- ios/std::unitbuf
- ios/std::uppercase
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::hexfloat [C++]
- std::io_errc [C++]
- std::internal [C++]
- std::iostream_category [C++]
- std::is_error_code_enum [C++]
- std::left [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::noboolalpha [C++]
- std::noshowbase [C++]
- std::noshowpoint [C++]
- std::noshowpos [C++]
- std::noskipws [C++]
- std::nounitbuf [C++]
- std::nouppercase [C++]
- std::oct [C++]
- std::right [C++]
- std::scientific [C++]
- std::showbase [C++]
- std::showpoint [C++]
- std::showpos [C++]
- std::skipws [C++]
- std::unitbuf [C++]
- std::uppercase [C++]
ms.openlocfilehash: 3ba2ba463bbd59bd8febccb73c37cc3b79a4c75b
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150628"
---
# <a name="ltiosgt-functions"></a>&lt;ios&gt;-Funktionen

## <a name="boolalpha"></a><a name="boolalpha"></a>boolalpha

Gibt an, dass Variablen des Typs [bool](../cpp/bool-cpp.md) im Stream als **TRUE** oder **FALSE** angezeigt werden.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Standardmäßig werden Variablen vom Typ **bool** als 1 oder 0 angezeigt.

`boolalpha` effektiv `str.`[Setf](../standard-library/ios-base-class.md#setf)(`ios_base::boolalpha`) aufruft, und gibt dann *Str*zurück.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) kehrt den Effekt von `boolalpha` um.

### <a name="example"></a>Beispiel

```cpp
// ios_boolalpha.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   bool b = true;
   cout << b << endl;
   boolalpha( cout );
   cout << b << endl;
   noboolalpha( cout );
   cout << b << endl;
   cout << boolalpha << b << endl;
}
```

```Output
1
true
1
true
```

## <a name="dec"></a><a name="dec"></a>31.12.2012

Gibt an, dass ganzzahlige Variablen in Basis-10-Schreibweise angezeigt werden.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Standardmäßig werden Ganzzahlvariablen in Basis-10-Schreibweise angezeigt.

`dec` effektiv `str.`[Setf](../standard-library/ios-base-class.md#setf)(`ios_base::dec`, `ios_base::basefield`) aufruft, und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_dec.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 100;

   cout << i << endl;   // Default is base 10
   cout << hex << i << endl;
   dec( cout );
   cout << i << endl;
   oct( cout );
   cout << i << endl;
   cout << dec << i << endl;
}
```

```Output
100
64
100
144
100
```

## <a name="ltiosgt-defaultfloat"></a><a name="ios_defaultfloat"></a>&lt;IOS-&gt; DefaultFloat

Konfiguriert die Flags eines `ios_base`-Objekts, sodass ein Standard-Anzeigeformat für Floatwerte verwendet wird.

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>Parameter

*_Iosbase*\
Ein `ios_base`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Manipulator ruft `iosbase.`[ios_base:: unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`auf und gibt dann *iosbase*zurück.

## <a name="fixed"></a><a name="fixed"></a>festen

Gibt an, dass eine Gleitkommazahl in fester Dezimalschreibweise angezeigt wird.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

`fixed` ist die Standard Anzeige Notation für Gleit Komma Zahlen. [scientific](../standard-library/ios-functions.md#scientific) bewirkt, dass Gleitkommazahlen in wissenschaftlicher Schreibweise angezeigt werden.

Der Manipulator ruft *Str*auf. [Setf](../standard-library/ios-base-class.md#setf)(`ios_base::fixed`, `ios_base::floatfield`) und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_fixed.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 1.1F;

   cout << i << endl;   // fixed is the default
   cout << scientific << i << endl;
   cout.precision( 1 );
   cout << fixed << i << endl;
}
```

```Output
1.1
1.100000e+000
1.1
```

## <a name="hex"></a><a name="hex"></a>dchen

Gibt an, dass ganzzahlige Variablen in Basis-16-Schreibweise angezeigt werden soll.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Standardmäßig werden Ganzzahlvariablen in Basis-10-Schreibweise angezeigt. Ebenfalls verändern [dec](../standard-library/ios-functions.md#dec) und [oct](../standard-library/ios-functions.md#oct) die Anzeige von Ganzzahlvariablen.

Der Manipulator ruft `str`effektiv auf **.** [Setf](../standard-library/ios-base-class.md#setf)(`ios_base::hex`, `ios_base::basefield`) und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

Unter [Dec](../standard-library/ios-functions.md#dec) finden Sie ein Beispiel für die Verwendung von `hex`.

## <a name="hexfloat"></a><a name="hexfloat"></a>hexfloat

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a><a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a><a name="internal"></a>Verbrennungs

Bewirkt, dass ein Nummernzeichen linksbündig und die Zahl rechtsbündig ausgerichtet wird.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Durch [showpos](../standard-library/ios-functions.md#showpos) zeigt das Nummernzeichen für positive Zahlen an.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(`[ios_base:: Internal](../standard-library/ios-base-class.md#fmtflags)`,` [ios_base::-Feld](../standard-library/ios-base-class.md#fmtflags)`)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_internal.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( void )
{
   using namespace std;
   float i = -123.456F;
   cout.fill( '.' );
   cout << setw( 10 ) << i << endl;
   cout << setw( 10 ) << internal << i << endl;
}
```

```Output
..-123.456
-..123.456
```

## <a name="is_error_code_enum"></a><a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a><a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a><a name="left"></a>linken

Bewirkt, dass Text, der nicht so breit ist wie die Ausgabebreite, im Stream linksbündig angezeigt wird.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(ios_base::left, ios_base::adjustfield)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_left.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout.width( 20 );
   cout << f1 << endl;
   cout << left << f1 << endl;
}
```

```Output
5
        5
```

## <a name="make_error_code"></a><a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a><a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a><a name="noboolalpha"></a>noboolalpha

Gibt an, dass Variablen des Typs [bool](../cpp/bool-cpp.md) im Stream als 1 oder 0 angezeigt werden.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

In der Standardeinstellung ist `noboolalpha` aktiviert.

`noboolalpha` `str.`[Unsetf](../standard-library/ios-base-class.md#unsetf) -`(ios_base::boolalpha)`effektiv aufruft, und gibt dann *Str*zurück.

[boolalpha](../standard-library/ios-functions.md#boolalpha) kehrt den Effekt von `noboolalpha` um.

### <a name="example"></a>Beispiel

Unter [boolalpha](../standard-library/ios-functions.md#boolalpha) finden Sie ein Beispiel für die Verwendung von `noboolalpha`.

## <a name="noshowbase"></a><a name="noshowbase"></a>noshowbase

Deaktiviert die Angabe der Schreibweisenbasis, mit der eine Zahl angezeigt wird.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

`noshowbase` ist standardmäßig aktiviert. Verwenden Sie [showbase](../standard-library/ios-functions.md#showbase), um die Schreibweisenbasis von Zahlen zu kennzeichnen.

Der Manipulator ruft `str.`[Unsetf](../standard-library/ios-base-class.md#unsetf) -`(ios_base::showbase)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

Unter [showbase](../standard-library/ios-functions.md#showbase) finden Sie ein Beispiel zur Verwendung von `noshowbase`.

## <a name="noshowpoint"></a><a name="noshowpoint"></a>noshowpoint

Zeigt nur den ganzzahligen Teil von Gleitkommazahlen an, dessen Bruchteil null ist.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

`noshowpoint` ist standardmäßig aktiviert; verwenden Sie [showpoint](../standard-library/ios-functions.md#showpoint) und [precision](../standard-library/ios-base-class.md#precision), um Nullen hinter dem Dezimaltrennzeichen angezeigt zu bekommen.

Der Manipulator ruft `str.`[Unsetf](../standard-library/ios-base-class.md#unsetf) -`(ios_base::showpoint)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_noshowpoint.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.000;
   cout << f1 << endl;   // noshowpoint is default
   cout.precision( 4 );
   cout << showpoint << f1 << endl;
   cout << noshowpoint << f1 << endl;
}
```

```Output
5
5.000
5
```

## <a name="noshowpos"></a><a name="noshowpos"></a>noshowpos

Bewirkt, dass positive Zahlen nicht explizit signiert werden.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

`noshowpos` ist standardmäßig aktiviert.

Der Manipulator ruft `str.`[Unsetf](../standard-library/ios-base-class.md#unsetf) -`(ios_base::showps)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

Unter [showpos](../standard-library/ios-functions.md#showpos) finden Sie ein Beispiel für die Verwendung von `noshowpos`.

## <a name="noskipws"></a><a name="noskipws"></a>Noskipws

Bewirkt, dass Leerzeichen vom Eingabestream gelesen werden.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

In der Standardeinstellung ist [skipws](../standard-library/ios-functions.md#skipws) aktiviert. Wenn im Eingabestream ein Leerzeichen erkannt wird, wird dadurch das Ende des Puffers markiert.

Der Manipulator ruft `str.`[Unsetf](../standard-library/ios-base-class.md#unsetf) -`(ios_base::skipws)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_noskipws.cpp
// compile with: /EHsc
#include <iostream>
#include <string>

int main() {
   using namespace std;
   string s1, s2, s3;
   cout << "Enter three strings: ";
   cin >> noskipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

## <a name="nounitbuf"></a><a name="nounitbuf"></a>nounitbuf

Bewirkt, dass die Ausgabe gepuffert und verarbeitet wird, wenn der Puffer voll ist.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

[unitbuf](../standard-library/ios-functions.md#unitbuf) bewirkt, dass der Puffer verarbeitet wird, wenn dieser nicht leer ist.

Der Manipulator ruft `str.`[Unsetf](../standard-library/ios-base-class.md#unsetf) -`(ios_base::unitbuf)`auf und gibt dann *Str*zurück.

## <a name="nouppercase"></a><a name="nouppercase"></a>nouppercase

Gibt an, dass hexadezimale Ziffern und der Exponent in wissenschaftlicher Schreibweise in Kleinbuchstaben angezeigt werden.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Der Manipulator ruft `str.`[Unsetf](../standard-library/ios-base-class.md#unsetf) -`(ios_base::uppercase)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

Unter [uppercase](../standard-library/ios-functions.md#uppercase) finden Sie ein Beispiel für die Verwendung von `nouppercase`.

## <a name="oct"></a><a name="oct"></a>31.10

Gibt an, dass ganzzahlige Variablen in Basis-8-Schreibweise angezeigt werden.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Standardmäßig werden Ganzzahlvariablen in Basis-10-Schreibweise angezeigt. Ebenfalls verändern [dec](../standard-library/ios-functions.md#dec) und [hex](../standard-library/ios-functions.md#hex) die Anzeige von Ganzzahlvariablen.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(ios_base::oct, ios_base::basefield)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

Unter [Dec](../standard-library/ios-functions.md#dec) finden Sie ein Beispiel für die Verwendung von `oct`.

## <a name="right"></a><a name="right"></a>Richting

Bewirkt, dass Text, der nicht so breit ist wie die Ausgabebreite, im Stream rechtsbündig angezeigt wird.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

[left](../standard-library/ios-functions.md#left) modifiziert auch die Textausrichtung.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(ios_base::right, ios_base::adjustfield)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_right.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << left << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << right << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
}
```

```Output
5
                   5
5
5
                   5
                   5
```

## <a name="scientific"></a><a name="scientific"></a>wissenschaftlich

Bewirkt, dass Gleitkommazahlen in wissenschaftlicher Schreibweise angezeigt werden.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Für Gleitkommazahlen ist die [fixed](../standard-library/ios-functions.md#fixed)-Schreibweise standardmäßig aktiviert.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(ios_base::scientific, ios_base::floatfield)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_scientific.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 100.23F;

   cout << i << endl;
   cout << scientific << i << endl;
}
```

```Output
100.23
1.002300e+002
```

## <a name="showbase"></a><a name="showbase"></a>Showbase

Gibt die Schreibweisenbasis an, mit der eine Zahl angezeigt wird.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Die Schreibweisenbasis einer Zahl kann mit [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct) und [hex](../standard-library/ios-functions.md#hex) geändert werden.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(ios_base::showbase)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_showbase.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int j = 100;

   cout << showbase << j << endl;   // dec is default
   cout << hex << j << showbase << endl;
   cout << oct << j << showbase << endl;

   cout << dec << j << noshowbase << endl;
   cout << hex << j << noshowbase << endl;
   cout << oct << j << noshowbase << endl;
}
```

```Output
100
0x64
0144
100
64
144
```

## <a name="showpoint"></a><a name="showpoint"></a>showpoint

Zeigt den ganzzahligen Teil einer Gleitkommazahl und Ziffern rechts vom Dezimaltrennzeichen an, selbst wenn der Bruchteil null ist.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

[noshowpoint](../standard-library/ios-functions.md#noshowpoint) ist standardmäßig aktiviert.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(ios_base::showpoint)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

Unter [noshowpoint](../standard-library/ios-functions.md#noshowpoint) finden Sie ein Beispiel für die Verwendung von `showpoint`.

## <a name="showpos"></a><a name="showpos"></a>Showpos

Bewirkt, dass positive Zahlen explizit signiert werden.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

[noshowpos](../standard-library/ios-functions.md#noshowpos) ist die Standardeinstellung.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(ios_base::showpos)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_showpos.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 1;

   cout << noshowpos << i << endl;   // noshowpos is default
   cout << showpos << i << endl;
}
```

```Output
1
+1
```

## <a name="skipws"></a><a name="skipws"></a>skipws

Bewirkt, dass Leerzeichen nicht vom Eingabestream gelesen werden.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

In der Standardeinstellung ist `skipws` aktiviert. [noskipws](../standard-library/ios-functions.md#noskipws) bewirkt, dass Leerzeichen aus Eingabestream gelesen werden.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(ios_base::skipws)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   char s1, s2, s3;
   cout << "Enter three characters: ";
   cin >> skipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

```Input
1 2 3
```

```Output
Enter three characters: 1 2 3
.1.
.2.
.3.
```

## <a name="unitbuf"></a><a name="unitbuf"></a>Unitbuf

Bewirkt, dass die Ausgabe verarbeitet wird, wenn der Puffer nicht leer ist.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Bitte beachten Sie, dass `endl` auch den Puffer leert.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) ist standardmäßig aktiviert.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(`[ios_base:: Unitbuf](../standard-library/ios-base-class.md#fmtflags) -`)`auf und gibt dann *Str*zurück.

## <a name="uppercase"></a><a name="uppercase"></a> uppercase

Gibt an, dass hexadezimale Ziffern und der Exponent in wissenschaftlicher Schreibweise in Großbuchstaben angezeigt werden.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parameter

*Str*\
Ein Verweis auf ein [ios_base](../standard-library/ios-base-class.md)-Objekt oder auf einen Typ, der von `ios_base` erbt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das-Objekt, von dem *Str* abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

[nouppercase](../standard-library/ios-functions.md#nouppercase) ist standardmäßig aktiviert.

Der Manipulator ruft `str.`[Setf](../standard-library/ios-base-class.md#setf) -`(`[ios_base:: Großbuchstaben](../standard-library/ios-base-class.md#fmtflags)`)`auf und gibt dann *Str*zurück.

### <a name="example"></a>Beispiel

```cpp
// ios_uppercase.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
   using namespace std;

   double i = 1.23e100;
   cout << i << endl;
   cout << uppercase << i << endl;

   int j = 10;
   cout << hex << nouppercase << j << endl;
   cout << hex << uppercase << j << endl;
}
```

```Output
1.23e+100
1.23E+100
a
A
```
