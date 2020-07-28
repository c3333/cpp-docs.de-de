---
title: fpos-Klasse
ms.date: 03/27/2019
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
ms.openlocfilehash: 37536443455ca4ddc40568e15951b814982d4ad9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193301"
---
# <a name="fpos-class"></a>fpos-Klasse

Die Klassen Vorlage beschreibt ein Objekt, das alle Informationen speichern kann, die zum Wiederherstellen eines beliebigen Datei Positions Indikators innerhalb eines Streams benötigt werden. Ein Objekt der Klasse fpos \< **St**> speichert effektiv mindestens zwei Member-Objekte:

- Ein Byteoffset vom Typ [streamoff](../standard-library/ios-typedefs.md#streamoff)

- Ein Konvertierungs Zustand, der in der Regel von einem Objekt der Klasse Basic_filebuf vom Typ verwendet wird `St` `mbstate_t` .

Es kann auch eine beliebige Dateiposition speichern, die von einem Objekt der Klasse [basic_filebuf](../standard-library/basic-filebuf-class.md) und vom Typ `fpos_t` verwendet werden kann. In einer Umgebung mit begrenzter Dateigröße werden `streamoff` und `fpos_t` jedoch manchmal synonym verwendet. In einer Umgebung ohne Streams, mit zustandsabhängiger Codierung, wird `mbstate_t` möglicherweise nicht verwendet. Daher kann die Anzahl der gespeicherten Memberobjekte variieren.

## <a name="syntax"></a>Syntax

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parameter

*Statetype*\
Zustandsinformationen.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[fpos](#fpos)|Erstellt ein Objekt, das Informationen zu einer Position (Offset) in einem Stream enthält.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[seekpos](#seekpos)|Wird nur intern von der C++-Standardbibliothek verwendet. Rufen Sie diese Methode nicht aus Ihrem Code auf.|
|[state](#state)|Legt den Konvertierungszustand fest oder gibt ihn zurück.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator! =](#op_neq)|Testet Dateipositionsindikatoren auf Ungleichheit.|
|[Operator +](#op_add)|Erhöht einen Dateipositionsindikator.|
|[Operator + =](#op_add_eq)|Erhöht einen Dateipositionsindikator.|
|[KOM](#operator-)|Verringert einen Dateipositionsindikator.|
|[Operator-=](#operator-_eq)|Verringert einen Dateipositionsindikator.|
|[Operator = =](#op_eq_eq)|Testet Dateipositionsindikatoren auf Gleichheit.|
|[operator streamoff](#op_streamoff)|Wandelt ein Objekt vom Typ `fpos` in ein Objekt vom Typ `streamoff` um.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<ios>

**Namespace:** std

## <a name="fposfpos"></a><a name="fpos"></a>Fehler beim Ausführen von "f"::

Erstellt ein Objekt, das Informationen zu einer Position (Offset) in einem Stream enthält.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parameter

*_Off*\
Der Offset in den Stream

*_State*\
Der Startzustand des `fpos`-Objekts

*_Filepos*\
Der Offset in den Stream

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert den Offset *_Off*relativ zum Anfang der Datei und im ursprünglichen Konvertierungs Zustand (falls dies wichtig ist). Wenn *_Off* -1 ist, stellt das resultierende Objekt eine ungültige Streamposition dar.

Der zweite Konstruktor speichert einen Offset von 0 (null) und das-Objekt *_State*.

## <a name="fposoperator"></a><a name="op_neq"></a>"f POS:: Operator! ="

Testet Dateipositionsindikatoren auf Ungleichheit.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Dateipositionsindikator, gegen den verglichen werden soll

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Datei positionsindikatoren nicht gleich sind, andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `!(*this == right)` zurück.

### <a name="example"></a>Beispiel

```cpp
// fpos_op_neq.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;

   fpos<int> pos1, pos2;
   ifstream file;
   char c;

   // Compare two fpos object
   if ( pos1 != pos2 )
      cout << "File position pos1 and pos2 are not equal" << endl;
   else
      cout << "File position pos1 and pos2 are equal" << endl;

   file.open( "fpos_op_neq.txt" );
   file.seekg( 0 );   // Goes to a zero-based position in the file
   pos1 = file.tellg( );
   file.get( c);
   cout << c << endl;

   // Increment pos1
   pos1 += 1;
   file.get( c );
   cout << c << endl;

   pos1 = file.tellg( ) - fpos<int>( 2);
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   // Increment pos1
   pos1 = pos1 + fpos<int>( 1 );
   file.get(c);
   cout << c << endl;

   pos1 -= fpos<int>( 2 );
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   file.close( );
}
```

## <a name="fposoperator"></a><a name="op_add"></a>f POS:: Operator +

Erhöht einen Dateipositionsindikator.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parameter

*_Off*\
Der Offset, um den der Dateipositionsindikator erhöht werden soll

### <a name="return-value"></a>Rückgabewert

Die Position in der Datei

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „**fpos(\*this) +=** `_Off`“ zurück.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator+` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator"></a><a name="op_add_eq"></a>f POS:: Operator + =

Erhöht einen Dateipositionsindikator.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parameter

*_Off*\
Der Offset, um den der Dateipositionsindikator erhöht werden soll

### <a name="return-value"></a>Rückgabewert

Die Position in der Datei

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion fügt dem gespeicherten Offset-Member-Objekt *_Off* hinzu und gibt ** \* dieses**zurück. Für die Positionierung innerhalb einer Datei ist das Ergebnis in der Regel nur für binäre Datenströme gültig, die über keine zustandsabhängige Codierung verfügen.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator+=` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator-"></a><a name="operator-"></a>"f POS:: Operator"-

Verringert einen Dateipositionsindikator.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Dateiposition

*_Off*\
Streamoffset

### <a name="return-value"></a>Rückgabewert

Die erste Memberfunktion gibt `(streamoff)*this - (streamoff) right` zurück. Die zweite Memberfunktion gibt `fpos(*this) -= _Off` zurück.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator-` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator-"></a><a name="operator-_eq"></a>f POS:: Operator-=

Verringert einen Dateipositionsindikator.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parameter

*_Off*\
Streamoffset

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt `fpos(*this) -= _Off` zurück.

### <a name="remarks"></a>Bemerkungen

Für die Positionierung innerhalb einer Datei ist das Ergebnis in der Regel nur für binäre Datenströme gültig, die über keine zustandsabhängige Codierung verfügen.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator-=` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator"></a><a name="op_eq_eq"></a>"f POS:: Operator = ="

Testet Dateipositionsindikatoren auf Gleichheit.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Dateipositionsindikator, gegen den verglichen werden soll

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Datei positionsindikatoren gleich sind. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `(streamoff)*this == (streamoff)right` zurück.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator+=` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator-streamoff"></a><a name="op_streamoff"></a>fpos:: Operator streamoff

Wandelt ein Objekt vom Typ `fpos` in ein Objekt vom Typ `streamoff` um

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt das gespeicherte Offset-Memberobjekt und alle zusätzlichen Offsets zurück, die als Teil des `fpos_t`-Memberobjekts gespeichert sind.

### <a name="example"></a>Beispiel

```cpp
// fpos_op_streampos.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   streamoff s;
   ofstream file( "rdbuf.txt");

   fpos<mbstate_t> f = file.tellp( );
   // Is equivalent to ..
   // streampos f = file.tellp( );
   s = f;
   cout << s << endl;
}
```

```Output
0
```

## <a name="fposseekpos"></a><a name="seekpos"></a>"f":: seekpos

Diese Methode wird nur intern von der C++-Standardbibliothek verwendet. Rufen Sie diese Methode nicht aus Ihrem Code auf.

```cpp
fpos_t seekpos() const;
```

## <a name="fposstate"></a><a name="state"></a>"f POS:: State"

Legt den Konvertierungszustand fest oder gibt ihn zurück.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parameter

*_State*\
Der neue Konvertierungsstatus

### <a name="return-value"></a>Rückgabewert

Der Konvertierungsstatus

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion gibt den im Member-Objekt gespeicherten Wert zurück `St` . Die zweite Member-Funktion speichert *_State* im `St` Member-Objekt.

### <a name="example"></a>Beispiel

```cpp
// fpos_state.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main() {
   using namespace std;
   streamoff s;
   ifstream file( "fpos_state.txt" );

   fpos<mbstate_t> f = file.tellg( );
   char ch;
   while ( !file.eof( ) )
      file.get( ch );
   s = f;
   cout << f.state( ) << endl;
   f.state( 9 );
   cout << f.state( ) << endl;
}
```

## <a name="see-also"></a>Weitere Informationen

[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
