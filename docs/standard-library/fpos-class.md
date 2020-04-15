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
ms.openlocfilehash: 7d60a31e69e8a1ad82086f715cac6dde064d1fac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359202"
---
# <a name="fpos-class"></a>fpos-Klasse

Die Klassenvorlage beschreibt ein Objekt, das alle Informationen speichern kann, die zum Wiederherstellen eines beliebigen Dateipositionsindikators in einem beliebigen Stream erforderlich sind. Ein Objekt der Klasse fpos\< **St**> speichert effektiv mindestens zwei Memberobjekte:

- Ein Byteoffset vom Typ [streamoff](../standard-library/ios-typedefs.md#streamoff)

- Ein Konvertierungsstatus, der von einem Objekt `St`der `mbstate_t`Klasse basic_filebuf , vom Typ verwendet wird, in der Regel .

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
|[Staat](#state)|Legt den Konvertierungszustand fest oder gibt ihn zurück.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator!=](#op_neq)|Testet Dateipositionsindikatoren auf Ungleichheit.|
|[Operator+](#op_add)|Erhöht einen Dateipositionsindikator.|
|[Operator+=](#op_add_eq)|Erhöht einen Dateipositionsindikator.|
|[Betreiber-](#operator-)|Verringert einen Dateipositionsindikator.|
|[operator-=](#operator-_eq)|Verringert einen Dateipositionsindikator.|
|[Betreiber== Einzelnachweise ==](#op_eq_eq)|Testet Dateipositionsindikatoren auf Gleichheit.|
|[operator streamoff](#op_streamoff)|Wandelt ein Objekt vom Typ `fpos` in ein Objekt vom Typ `streamoff` um.|

## <a name="requirements"></a>Anforderungen

**Header:** \<ios>

**Namespace:** std

## <a name="fposfpos"></a><a name="fpos"></a>fpos::fpos

Erstellt ein Objekt, das Informationen zu einer Position (Offset) in einem Stream enthält.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parameter

*_off*\
Der Offset in den Stream

*_state*\
Der Startzustand des `fpos`-Objekts

*_Filepos*\
Der Offset in den Stream

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor speichert den *Offset-_Off*relativ zum Anfang der Datei und im ursprünglichen Konvertierungsstatus (falls das wichtig ist). Wenn *_Off* -1 ist, stellt das resultierende Objekt eine ungültige Streamposition dar.

Der zweite Konstruktor speichert einen Nulloffset, und das Objekt *_State*.

## <a name="fposoperator"></a><a name="op_neq"></a>fpos::operator!=

Testet Dateipositionsindikatoren auf Ungleichheit.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Dateipositionsindikator, gegen den verglichen werden soll

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Dateipositionsindikatoren nicht identisch sind, andernfalls **FALSE**

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

## <a name="fposoperator"></a><a name="op_add"></a>fpos::operator+

Erhöht einen Dateipositionsindikator.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parameter

*_off*\
Der Offset, um den der Dateipositionsindikator erhöht werden soll

### <a name="return-value"></a>Rückgabewert

Die Position in der Datei

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt „**fpos(\*this) +=** `_Off`“ zurück.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator+` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator"></a><a name="op_add_eq"></a>fpos::operator+=

Erhöht einen Dateipositionsindikator.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parameter

*_off*\
Der Offset, um den der Dateipositionsindikator erhöht werden soll

### <a name="return-value"></a>Rückgabewert

Die Position in der Datei

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion fügt *dem* gespeicherten Offsetelementobjekt _Off hinzu und ** \*gibt**diese dann zurück. Für die Positionierung innerhalb einer Datei ist das Ergebnis in der Regel nur für binäre Datenströme gültig, die über keine zustandsabhängige Codierung verfügen.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator+=` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator-"></a><a name="operator-"></a>fpos::operator-

Verringert einen Dateipositionsindikator.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Dateiposition

*_off*\
Streamoffset

### <a name="return-value"></a>Rückgabewert

Die erste Memberfunktion gibt `(streamoff)*this - (streamoff) right` zurück. Die zweite Memberfunktion gibt `fpos(*this) -= _Off` zurück.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator-` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator-"></a><a name="operator-_eq"></a>fpos::operator-=

Verringert einen Dateipositionsindikator.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parameter

*_off*\
Streamoffset

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt `fpos(*this) -= _Off` zurück.

### <a name="remarks"></a>Bemerkungen

Für die Positionierung innerhalb einer Datei ist das Ergebnis in der Regel nur für binäre Datenströme gültig, die über keine zustandsabhängige Codierung verfügen.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator-=` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator"></a><a name="op_eq_eq"></a>fpos::operator==

Testet Dateipositionsindikatoren auf Gleichheit.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Dateipositionsindikator, gegen den verglichen werden soll

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Dateipositionsindikatoren identisch sind, andernfalls **FALSE**

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `(streamoff)*this == (streamoff)right` zurück.

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `operator+=` finden Sie unter [operator!=](#op_neq).

## <a name="fposoperator-streamoff"></a><a name="op_streamoff"></a>fpos::Operator-Streamoff

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

## <a name="fposseekpos"></a><a name="seekpos"></a>fpos::seekpos

Diese Methode wird nur intern von der C++-Standardbibliothek verwendet. Rufen Sie diese Methode nicht aus Ihrem Code auf.

```cpp
fpos_t seekpos() const;
```

## <a name="fposstate"></a><a name="state"></a>fpos::Zustand

Legt den Konvertierungszustand fest oder gibt ihn zurück.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parameter

*_state*\
Der neue Konvertierungsstatus

### <a name="return-value"></a>Rückgabewert

Der Konvertierungsstatus

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion gibt den `St` im Memberobjekt gespeicherten Wert zurück. Die zweite Memberfunktion speichert `St` *_State* im Memberobjekt.

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

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream Programmierung](../standard-library/iostream-programming.md)\
[iostreams-Konventionen](../standard-library/iostreams-conventions.md)
