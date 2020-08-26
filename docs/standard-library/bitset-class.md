---
title: bitset-Klasse
ms.date: 03/27/2019
f1_keywords:
- bitset/std::bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
helpviewer_keywords:
- std::bitset [C++]
- std::bitset [C++], element_type
- std::bitset [C++], all
- std::bitset [C++], any
- std::bitset [C++], count
- std::bitset [C++], flip
- std::bitset [C++], none
- std::bitset [C++], reset
- std::bitset [C++], set
- std::bitset [C++], size
- std::bitset [C++], test
- std::bitset [C++], to_string
- std::bitset [C++], to_ullong
- std::bitset [C++], to_ulong
- std::bitset [C++], reference
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
ms.openlocfilehash: 623593e723b26244cc82e9eeed3e32657cca0b94
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846484"
---
# <a name="bitset-class"></a>bitset-Klasse

Beschreibt einen Typ von Objekt, das eine Sequenz speichert, die aus einer festen Anzahl von Bits besteht, die eine kompakte Möglichkeit bieten, Flags für eine Menge von Elementen oder Bedingungen bereitzustellen. Die bitset-Klasse unterstützt Vorgänge für Objekte des Typs „bitset“, die eine Auflistung von Bits enthalten und zeitlich konstanten Zugriff auf jedes Bit ermöglichen.

## <a name="syntax"></a>Syntax

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>Parameter

*Nr*\
Gibt die Anzahl der Bits im bitset-Objekt mit einer Ganzzahl ungleich 0 (null) vom Typ an, die zum Zeitpunkt der `size_t` Kompilierung bekannt sein muss.

## <a name="remarks"></a>Bemerkungen

Anders als bei der ähnlichen [Vektor \<bool> Klasse](../standard-library/vector-bool-class.md)hat die Bitset-Klasse keine Iteratoren und ist kein C++-Standard Bibliotheks Container. Sie unterscheidet sich auch vom Vektor \<bool> durch eine bestimmte Größe, die zur Kompilierzeit in Übereinstimmung mit der Größe festgelegt wird, die durch den Vorlagen Parameter *N* beim Deklarieren des **Bitsets \<N\> ** festgelegt wird.

Ein Bit ist festgelegt, wenn es den Wert 1 hat, und zurückgesetzt, wenn es den Wert 0 hat. Ein Bit zu spiegeln oder umzukehren bedeutet, dass sein Wert von 1 in 0 oder von 0 in 1 geändert wird. Die *N* Bits in einem Bitset sind durch ganzzahlige Werte von 0 bis *N* - 1 indiziert, wobei 0 die erste Bitposition und *N* - 1 die letzte Bitposition indiziert.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[bitset](#bitset)|Erstellt ein `bitset\<N>`-Objekt und initialisiert die Bits mit 0 (Null), mit einem angegebenen Wert oder mit Werten, die aus Zeichen einer Zeichenfolge ermittelt wurden.|

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[element_type](#element_type)|Ein Typ, der ein Synonym für den-Datentyp ist **`bool`** und verwendet werden kann, um auf Element Bits in einem zu verweisen `bitset` .|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[allen](#all)|Testet alle Bits in dieser `bitset` , um zu bestimmen, ob Sie alle auf festgelegt sind **`true`** .|
|[irgendeiner](#any)|Die Memberfunktion überprüft, ob jedes Bit in der Sequenz auf 1 festgelegt ist.|
|[count](#count)|Die Memberfunktion gibt die Anzahl von Bits zurück, die in der Bitsequenz festgelegt sind.|
|[flip](#flip)|Kehrt den Wert aller Bits in einem `bitset` oder ein einzelnes Bit an einer angegebenen Position um.|
|[keine](#none)|Überprüft, ob keines der Bits in einem `bitset`-Objekt auf 1 festgelegt wurde.|
|[reset](#reset)|Setzt alle Bits in einem `bitset`-Objekt oder ein Bit an einer angegebenen Position auf 0 zurück.|
|[set](#set)|Legt alle Bits in einem `bitset`-Objekt oder ein Bit an einer angegebenen Position auf 1 fest.|
|[size](#size)|Gibt die Anzahl von Bits eines `bitset`-Objekts zurück.|
|[Test](#test)|Überprüft, ob das Bit an einer angegebenen Position in einem `bitset`-Objekt auf 1 festgelegt ist.|
|[to_string](#to_string)|Konvertiert ein `bitset`-Objekt in eine Zeichenfolgendarstellung.|
|[to_ullong](#to_ullong)|Gibt die Summe der Bitwerte in als zurück `bitset` **`unsigned long long`** .|
|[to_ulong](#to_ulong)|Konvertiert ein- `bitset` Objekt in das-Objekt **`unsigned long`** , das die in enthaltene Bits-Sequenz generiert, wenn zum Initialisieren von verwendet wird `bitset` .|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[Referenz](#reference)|Eine Proxyklasse, die Verweise auf Bits bereitstellt, die in einem `bitset`-Objekt enthalten sind, das als unterstützende Klasse für den `operator[]` der `bitset`-Klasse dazu verwendet wird, auf einzelne Bits zuzugreifen sowie einzelne Bits zu verarbeiten.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator! =](#op_neq)|Überprüft ein `bitset`-Zielobjekt auf Ungleichheit mit einem angegebenen `bitset`-Objekt.|
|[Operator&=](#op_and_eq)|Kombiniert zwei Bitmengen in einem logischen `AND`-Vorgang.|
|[Operator<<](#op_lshift)|Verschiebt die Bits in einem `bitset`-Objekt um eine angegebene Anzahl von Positionen nach links und gibt das Ergebnis in einem neuen `bitset`-Objekt zurück.|
|[Operator<<=](#op_lshift_eq)|Verschiebt die Bits in einem `bitset`-Objekt um eine angegebene Anzahl von Positionen nach links und gibt das Ergebnis im selben `bitset`-Objekt zurück.|
|[Operator = =](#op_eq_eq)|Überprüft ein `bitset`-Zielobjekt auf Gleichheit mit einem angegebenen `bitset`-Objekt.|
|[Operator>>](#op_rshift)|Verschiebt die Bits in einem `bitset`-Objekt um eine angegebene Anzahl von Positionen nach rechts und gibt das Ergebnis in einem neuen `bitset`-Objekt zurück.|
|[Operator>>=](#op_rshift_eq)|Verschiebt die Bits in einem `bitset`-Objekt um eine angegebene Anzahl von Positionen nach rechts und gibt das Ergebnis im selben `bitset`-Objekt zurück.|
|[operator&#91;&#93;](#op_at)|Gibt einen Verweis auf ein Bit an einer angegebenen Position eines `bitset`-Objekts zurück, wenn das `bitset` geändert werden kann. Gibt andernfalls den Wert zurück, den das Bit an dieser Position hat.|
|[Operator ^ =](#op_xor_eq)|Kombiniert zwei Bitmengen in einem Exklusiv-`OR`-Vorgang.|
|[Operator&#124;=](#op_or_eq)|Kombiniert zwei Bitmengen in einem Inklusiv-`OR`-Vorgang.|
|[Operator ~](#op_not)|Kehrt alle Bits in einem Ziel-`bitset` um, und gibt das Ergebnis zurück.|

### <a name="structures"></a>Strukturen

|Name|Beschreibung|
|-|-|
|[hash](#hash)||

### <a name="all"></a><a name="all"></a> allen

Testet alle Bits in diesem bitset-Objekt, um zu ermitteln, ob sie alle auf "true" festgelegt sind.

```cpp
bool all() const;
```

#### <a name="return-value"></a>Rückgabewert

Gibt "true" zurück, wenn alle Bits in diesem Satz gleich "true" sind. Gibt zurück, **`false`** Wenn mindestens ein Bit false ist.

### <a name="any"></a><a name="any"></a> irgendeiner

Überprüft, ob ein Bit in der Sequenz auf 1 gesetzt ist.

```cpp
bool any() const;
```

#### <a name="return-value"></a>Rückgabewert

**`true`** Wenn ein beliebiges Bit im Bitset auf 1 festgelegt ist; , **`false`** Wenn alle Bits 0 sind.

#### <a name="example"></a>Beispiel

```cpp
// bitset_any.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"
        << endl;

   b = b1.any ( );

   if ( b )
      cout << "At least one of the bits in bitset is set to 1."
           << endl;
   else
      cout << "None of the bits in bitset are set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );

   cout << "The reset bitset is: ( "<< b1 << " )"
        << endl;

   rb = rb1.any ( );

   if ( rb )
      cout << "At least one of the bits in the reset bitset "
           << "are set to 1." << endl;
   else
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
}
```

```Output
The original bitset b1( 6 ) is: ( 00110 )
At least one of the bits in bitset is set to 1.
The reset bitset is: ( 00000 )
None of the bits in bitset b1 are set to 1.
```

### <a name="bitset"></a><a name="bitset"></a> Bitset

Erstellt ein Objekt der Klasse `bitset\<N>`, und initialisiert die Bits mit 0 (null) oder mit einem angegebenen Wert oder mit Werten, die aus Zeichen einer Zeichenfolge ermittelt wurden.

```cpp
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,
    typename basic_string<CharType, Traits, Allocator>::size_type count,
    CharType _Zero = CharType ('0'),
    CharType _One = CharType ('1'));
```

#### <a name="parameters"></a>Parameter

*ster*\
Die ganze Zahl ohne Vorzeichen, deren Darstellung zur Basis 2 verwendet wird, um die Bits im zu erstellenden Bitset zu initialisieren.

*SRT*\
Die Zeichenfolge von Nullen und Einsen, die verwendet wird, um die Bitwerte des Bitsets zu initialisieren.

*_CStr*\
Eine Zeichenfolge von Nullen und Einsen im C-Format, die verwendet wird, um die Bitwerte des Bitsets zu initialisieren.

*_Pos*\
Die Position des Zeichens in der Zeichenfolge, von links nach rechts gezählt und beginnend mit 0 (null), die verwendet wird, um das erste Bit im Bitset zu initialisieren.

*Countdown*\
Die Anzahl der Zeichen in der Zeichenfolge, die verwendet wird, um Anfangswerte für die Bits im Bitset bereitzustellen.

*_Zero*\
Das Zeichen, das verwendet wird, um eine 0 (null) darzustellen. Standardmäßig ist dies '0'.

*_One*\
Das Zeichen, das verwendet wird, um eine Eins darzustellen. Standardmäßig ist dies '1'.

#### <a name="remarks"></a>Bemerkungen

Es können drei Konstruktoren verwendet werden, um Objekte der Klasse `bitset\<N>` zu erstellen:

- Der erste Konstruktor akzeptiert keine Parameter, erstellt ein Objekt der Klasse `bitset\<N>` und initialisiert alle N-Bits auf den Standardwert 0 (null).

- Der zweite Konstruktor erstellt ein Objekt der Klasse `bitset\<N>` und initialisiert die Bits mit dem einzelnen **`unsigned long long`** Parameter.

- Der dritte Konstruktor erstellt ein Objekt der Klasse `bitset\<N>` und initialisiert dabei die N-Bits auf Werte, die den Zeichen in einer Zeichenfolge von Nullen und Einsen im C-Format entsprechen. Sie rufen den Konstruktor auf, ohne die Zeichenfolge in einen Zeichenfolgentyp umzuwandeln: `bitset<5> b5("01011");`

Es werden auch zwei Konstruktorvorlagen bereitgestellt:

- Die erste Konstruktorvorlage erstellt ein Objekt der Klasse `bitset\<N>` und initialisiert Bits aus den Zeichen, die in einer Zeichenfolge von Nullen und Einsen bereitgestellt werden. Wenn Zeichen in der Zeichenfolge keine 0 oder 1 sind, löst der Konstruktor ein Objekt der Klasse [ungültiges Argument](../standard-library/invalid-argument-class.md) aus. Wenn die angegebene Position (*_Pos*) die Länge der Zeichenfolge überschreitet, löst der Konstruktor ein Objekt der Klasse [Out_of_range](../standard-library/out-of-range-class.md)aus. Der Konstruktor legt nur diejenigen Bits an Position *j* im Bitset fest, für die das Zeichen in der Zeichenfolge an der Position `_Pos + j` 1 ist. Standardmäßig ist *_Pos* 0.

- Die zweite konstruktorvorlage ähnelt der ersten, enthält jedoch einen zusätzlichen Parameter (*count*), der verwendet wird, um die Anzahl der zu initialisierenden Bits anzugeben. Es verfügt außerdem über zwei optionale Parameter: *_Zero* und *_One*, die angeben, welches Zeichen in *Str* so interpretiert werden soll, dass es ein 0-Bit und ein 1-Bit bedeutet.

#### <a name="example"></a>Beispiel

```cpp
// bitset_bitset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   // Using the default constructor
   using namespace std;
   bitset<2> b0;
   cout << "The set of bits in bitset<2> b0 is: ( "
        << b0 << " )." << endl;

   // Using the second member function
   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "
        << b1 << " )." << endl;

   // The template parameter N can be an expresssion
   bitset< 2 * sizeof ( int ) > b2;
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "
        << b2 << " )." << endl;

   // The base two representation will be truncated
   // if its length exceeds the size of the bitset
   bitset<3> b3 ( 6 );
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "
        << b3 << " )." << endl;

   // Using a c-style string to initialize the bitset
    bitset<7> b3andahalf ( "1001001" );
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"
         << " is ( " << b3andahalf << " )." << endl;

   // Using the fifth member function with the first parameter
   string bitval4 ( "10011" );
   bitset<5> b4 ( bitval4 );
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "
        << b4 << " )." << endl;

   // Only part of the string may be used for initialization

   // Starting at position 3 for a length of 6 (100110)
   string bitval5 ("11110011011");
   bitset<6> b5 ( bitval5, 3, 6 );
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "
        << b5 << " )." << endl;

   // The bits not initialized with part of the string
   // will default to zero
   bitset<11> b6 ( bitval5, 3, 5 );
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "
        << b6 << " )." << endl;

   // Starting at position 2 and continue to the end of the string
   bitset<9> b7 ( bitval5, 2 );
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "
        << b7 << " )." << endl;
}
```

```Output
The set of bits in bitset<2> b0 is: ( 00 ).
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).
The set of bits in bitset<3> b3( 6 ) is ( 110 ).
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).
```

### <a name="count"></a><a name="count"></a> Countdown

Gibt die Anzahl der Bit-Sätze in der Bitsequenz an.

```cpp
size_t count() const;
```

#### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bit-Sätze in der Bitsequenz.

#### <a name="example"></a>Beispiel

```cpp
// bitset_count.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
    using namespace std;

    bitset<5> b1(4);

    cout << "The collection of bits in the original bitset is: ( "
         << b1 << " )" << endl;

    size_t i;
    i = b1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << i << "." << endl;

    bitset<5> fb1;
    fb1 = b1.flip();

    cout << "The collection of flipped bits in the modified bitset "
         << "is: ( " << b1 << " )" << endl;

    size_t ii;
    ii = fb1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << ii << "." << endl;
}
```

```Output
The collection of bits in the original bitset is: ( 00100 )
The number of bits in the bitset set to 1 is: 1.
The collection of flipped bits in the modified bitset is: ( 11011 )
The number of bits in the bitset set to 1 is: 4.
```

### <a name="element_type"></a><a name="element_type"></a> element_type

Ein Typ, der ein Synonym für den-Datentyp ist **`bool`** und verwendet werden kann, um auf Element Bits in einem Bitset zu verweisen.

```cpp
typedef bool element_type;
```

#### <a name="example"></a>Beispiel

```cpp
// bitset_elem_type.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<3> b1 ( 2 );
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"
        << endl;

   //Compare two ways to reference bits in a bitset
   bool b;
   bitset<5>::element_type e;

   b = b1.test ( 2 );
   if ( b )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
   b1[2] = 1;
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"
        << endl;

   e = b1.test ( 2 );
   if ( e )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
}
```

```Output
Original bitset b1(6) is: ( 010 )
The bit at position 2 of bitset b1has a value of 0.
Bitset b1 modified by b1[2] = 1 is: ( 110 )
The bit at position 2 of bitset b1has a value of 1.
```

### <a name="flip"></a><a name="flip"></a> kte

Kehrt den Wert aller Bits in einem Bitset um oder kehrt ein einzelnes Bit an einer angegebenen Position um.

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Position des Bits, dessen Wert umgekehrt werden soll.

#### <a name="return-value"></a>Rückgabewert

Eine Kopie des geänderten Bitsets, für das die Memberfunktion aufgerufen wurde.

#### <a name="remarks"></a>Bemerkungen

Die zweite Member-Funktion löst eine [Out_of_range](../standard-library/out-of-range-class.md) Ausnahme aus, wenn die als Parameter angegebene Position größer als die Größe *N* des **Bitsets \<** *N* **> ** ist, dessen Bit invertiert wurde.

#### <a name="example"></a>Beispiel

```cpp
// bitset_flip.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 6 );

   cout << "The collection of bits in the original bitset is: ( "
        << b1 << " )" << endl;

   bitset<5> fb1;
   fb1 = b1.flip ( );

   cout << "After flipping all the bits, the bitset becomes: ( "
        << fb1 << " )" << endl;

   bitset<5> f3b1;
   f3b1 = b1.flip ( 3 );

   cout << "After flipping the fourth bit, the bitset becomes: ( "
        << f3b1 << " )" << endl << endl;

   bitset<5> b2;
   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b2.flip(i);
      cout << b2 << "  The bit flipped is in position "
           << i << ".\n";
   }
}
```

```Output
The collection of bits in the original bitset is: ( 00110 )
After flipping all the bits, the bitset becomes: ( 11001 )
After flipping the fourth bit, the bitset becomes: ( 10001 )

00001  The bit flipped is in position 0.
00011  The bit flipped is in position 1.
00111  The bit flipped is in position 2.
01111  The bit flipped is in position 3.
11111  The bit flipped is in position 4.
```

### <a name="hash"></a><a name="hash"></a> Hash

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a><a name="none"></a> gar

Überprüft, ob keines der Bits in einem bitset-Objekt auf 1 gesetzt wurde.

```cpp
bool none() const;
```

#### <a name="return-value"></a>Rückgabewert

**`true`** , wenn kein Bit im Bitset auf 1 festgelegt wurde. **`false`** Wenn mindestens ein Bit auf 1 festgelegt wurde.

#### <a name="example"></a>Beispiel

```cpp
// bitset_none.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "Original bitset b1(6) is: ( " << b1 << " )"
        << endl;

   b = b1.none ( );

   if ( b )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );
   rb = rb1.none ( );
   if ( rb )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;
}
```

```Output
Original bitset b1(6) is: ( 00110 )
At least one of the bits in bitset b1 is set to 1.
None of the bits in bitset b1 are set to 1.
```

### <a name="operator"></a><a name="op_neq"></a> Operator! =

Überprüft ein Zielbitset auf Ungleichheit mit einem angegebenen Bitset.

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Bitset, das mit dem Zielbitset auf Ungleichheit verglichen werden soll.

#### <a name="return-value"></a>Rückgabewert

**`true`** , wenn sich die Bitsets unterscheiden. **`false`** Wenn Sie identisch sind.

#### <a name="remarks"></a>Bemerkungen

Bitsets müssen dieselbe Größe haben, um von der Member-Operatorfunktion auf Ungleichheit getestet werden zu können.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_NE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 != b2 )
      cout << "Bitset b1 is different from bitset b2." << endl;
   else
      cout << "Bitset b1 is the same as bitset b2." << endl;

   if ( b1 != b3 )
      cout << "Bitset b1 is different from bitset b3." << endl;
   else
      cout << "Bitset b1 is the same as bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 != b4 )
   //   cout << "Bitset b1 is different from bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="operatoramp"></a><a name="op_and_eq"></a> KOM&amp;=

Kombiniert zwei Bitmengen in einem logischen `AND`-Vorgang.

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Bitset, das bitweise mit dem Zielbitset kombiniert werden soll.

#### <a name="return-value"></a>Rückgabewert

Das geänderte zielbitset, das sich aus der bitweisen `AND` Operation ergibt, wobei das Bitset als Parameter angegeben ist.

#### <a name="remarks"></a>Bemerkungen

Zwei Bits, die durch den Operator kombiniert werden `AND` , geben zurück **`true`** , wenn jedes Bit true ist; andernfalls gibt Ihre Kombination zurück **`false`** .

Bitsets müssen dieselbe Größe aufweisen, um bitweise mit dem `AND` Operator von der Member-Operator Funktion kombiniert zu werden.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_bitwise.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 &= b2;
   cout << "After bitwise AND combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset is unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 &= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise AND combination,
the target bitset b1 becomes:   ( 00011 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator"></a><a name="op_lshift"></a> KOM\<\<

Verschiebt die Bits in einem Bitset um eine angegebene Anzahl von Positionen nach links und gibt das Ergebnis in einem neuen Bitset zurück.

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Anzahl von Positionen, die Bits im Bitset nach links verschoben werden.

#### <a name="return-value"></a>Rückgabewert

Das geänderte Bitset mit den Bits, die um die erforderliche Anzahl von Positionen nach links verschoben wurden.

#### <a name="remarks"></a>Bemerkungen

Die Member-Operator Funktion gibt **Bitset**( ** \* this**) **<<= POS zurück,** wobei [<<=](#op_lshift_eq) die Bits in einem Bitset um eine angegebene Anzahl von Positionen nach links verschiebt und das Ergebnis an das zielbitset zurückgibt.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_LS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << " the bitset b2 is: ( "<< b2 << " )."
        << endl;

   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << " the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

### <a name="operatorltlt"></a><a name="op_lshift_eq"></a> KOM&lt;&lt;=

Verschiebt die Bits in einem Bitset um eine angegebene Anzahl von Positionen nach links und gibt das Ergebnis an das Zielbitset zurück.

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Anzahl der Positionen, um die die Bits im Bitset nach links verschoben werden sollen.

#### <a name="return-value"></a>Rückgabewert

Das Zielbitset, das so geändert wurde, dass die Bits um die erforderliche Anzahl von Positionen nach links verschoben wurden.

#### <a name="remarks"></a>Bemerkungen

Wenn kein Element vorhanden ist, das an die Position verschoben werden kann, löscht die Funktion das Bit auf einen Wert von 0.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_LSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;
   b1 <<= 2;
   cout << "After shifting the bits 2 positions to the left,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the target bitset b1 becomes: ( 11100 ).
```

### <a name="operator"></a><a name="op_eq_eq"></a> Operator = =

Überprüft ein Zielbitset auf Gleichheit mit einem angegebenen Bitset.

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Bitset, das mit dem Zielbitset auf Gleichheit verglichen werden soll.

#### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die Bitsets identisch sind. **`false`** Wenn Sie unterschiedlich sind.

#### <a name="remarks"></a>Bemerkungen

Bitsets müssen dieselbe Größe haben, um von der Member-Operatorfunktion auf Gleichheit getestet werden zu können.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_EQ.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 == b2 )
      cout << "Bitset b1 is the same as bitset b2." << endl;
   else
      cout << "Bitset b1 is different from bitset b2." << endl;

   if ( b1 == b3 )
      cout << "Bitset b1 is the same as bitset b3." << endl;
   else
      cout << "Bitset b1 is different from bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 == b4 )
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is different from bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="operatorgtgt"></a><a name="op_rshift"></a> KOM&gt;&gt;

Verschiebt die Bits in einem Bitset um eine angegebene Anzahl von Positionen nach rechts und gibt das Ergebnis in einem neuen Bitset zurück.

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Anzahl der Positionen, um die die Bits im Bitset nach rechts verschoben werden sollen.

#### <a name="return-value"></a>Rückgabewert

Ein neues Zielbitset, in dem die Bits um die erforderliche Anzahl von Positionen bezogen auf das Zielbitset nach rechts verschoben wurden.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_RS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << "the bitset b2 is: ( "<< b2 << " )."
        << endl;
   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << "the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

```Output
The bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the bitset b2 is: ( 11100 ).
After shifting the bits 1 position to the right,
the bitset b3 is: ( 01110 ).
```

### <a name="operatorgtgt"></a><a name="op_rshift_eq"></a> KOM&gt;&gt;=

Verschiebt die Bits in einem Bitset um eine angegebene Anzahl von Positionen nach rechts, und gibt das Ergebnis an das Zielbitset zurück.

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Anzahl der Positionen, um die die Bits im Bitset nach rechts verschoben werden sollen.

#### <a name="return-value"></a>Rückgabewert

Das Zielbitset, das so geändert wurde, dass die Bits um die erforderliche Anzahl von Positionen nach rechts verschoben wurden.

#### <a name="remarks"></a>Bemerkungen

Wenn kein Element vorhanden ist, das an die Position verschoben werden kann, löscht die Funktion das Bit auf einen Wert von 0.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_RSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 28 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;

   b1 >>= 2;
   cout << "After shifting the bits 2 positions to the right,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 11100 ).
After shifting the bits 2 positions to the right,
the target bitset b1 becomes: ( 00111 ).
```

### <a name="operator"></a><a name="op_at"></a> []-Operator

Gibt einen Verweis auf ein Bit an einer angegebenen Position eines Bitsets zurück, wenn das Bitset geändert werden kann. Gibt andernfalls den Wert des Bits an dieser Position zurück.

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Position des Bits innerhalb des Bitsets.

#### <a name="remarks"></a>Bemerkungen

Wenn Sie im Build die [ \_ \_ iteratordebugebene \_ ](../standard-library/iterator-debug-level.md) als 1 oder 2 definieren, tritt ein Laufzeitfehler in der ausführbaren Datei auf, wenn Sie versuchen, auf ein Element außerhalb der Grenzen des Bitsets zuzugreifen. Weitere Informationen finden Sie unter [Überprüfte Iteratoren](../standard-library/checked-iterators.md).

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_REF.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bool b;
   bitset<5> b1 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;

   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b = b1[ i ];
      cout << "  The bit in position "
           << i << " is " << b << ".\n";
   }
}
```

### <a name="operator"></a><a name="op_xor_eq"></a> Operator ^ =

Kombiniert zwei Bitmengen in einem Exklusiv-`OR`-Vorgang.

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Bitset, das bitweise mit dem Zielbitset kombiniert werden soll.

#### <a name="return-value"></a>Rückgabewert

Das geänderte Zielbitset, das aus dem bitweisen exklusiven `OR`-Vorgang resultiert, bei dem das Bitset als Parameter angegeben ist.

#### <a name="remarks"></a>Bemerkungen

Zwei Bits, die durch den exklusiven **or** -Operator kombiniert werden, geben zurück **`true`** , wenn mindestens ein, aber nicht beides der Bits ist **`true`** ; andernfalls gibt Ihre Kombination zurück **`false`** .

Bitsets müssen dieselbe Größe aufweisen, um bitweise von der Member-Operatorfunktion mit dem exklusiven `OR`-Operator kombiniert werden zu können.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_bitwiseOR.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 ^= b2;
   cout << "After bitwise exclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise exclusive OR combination,
the target bitset b1 becomes:   ( 01100 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator124"></a><a name="op_or_eq"></a> Operator&#124;=

Kombiniert zwei Bitmengen in einem Inklusiv-`OR`-Vorgang.

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parameter

*Richting*\
Das Bitset, das bitweise mit dem Zielbitset kombiniert werden soll.

#### <a name="return-value"></a>Rückgabewert

Das geänderte Zielbitset, das aus dem bitweisen inklusiven `OR`-Vorgang resultiert, bei dem das Bitset als Parameter angegeben ist.

#### <a name="remarks"></a>Bemerkungen

Zwei Bits, die durch den inklusiven `OR` Operator kombiniert werden, geben zurück, **`true`** Wenn mindestens eines der Bits ist **`true`** . wenn beide Bits sind **`false`** , gibt Ihre Kombination zurück **`false`** .

Bitsets müssen dieselbe Größe aufweisen, um bitweise von der Member-Operatorfunktion mit dem inklusiven `OR`-Operator kombiniert werden zu können.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_BIO.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 |= b2;
   cout << "After bitwise inclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise inclusive OR combination,
the target bitset b1 becomes:   ( 01111 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator"></a><a name="op_not"></a> Operator ~

Kehrt alle Bits in einem Zielbitset um und gibt das Ergebnis zurück.

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>Rückgabewert

Das Bitset mit allen Bits wird in Bezug auf die Zielbitset umgekehrt.

#### <a name="example"></a>Beispiel

```cpp
// bitset_op_invert.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <bitset>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2;
   b2 = ~b1;

   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;

   // These bits could also be flipped using the flip member function
   bitset<5> b3;
   b3 = b1.flip( );
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;
}
```

```Output
Bitset b1 is: ( 00111 ).
Bitset b2 = ~b1 is: ( 11000 ).
Bitset b3 = b1.flip( ) is: ( 11000 ).
```

### <a name="reference"></a><a name="reference"></a> Angabe

Eine Proxyklasse, die Verweise auf Bits bereitstellt, die in einem Bitset enthalten sind, das als unterstützende Klasse für den `operator[]` des Klassenbitsets dazu verwendet wird, um auf die einzelnen Bits zuzugreifen und sie zu verarbeiten.

```cpp
class reference {
   friend class bitset\<N>;
public:
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};
```

#### <a name="parameters"></a>Parameter

*ster*\
Der Wert des Objekts vom Typ **`bool`** , das einem Bit in einem Bitset zugewiesen werden soll.

*_Bitref*\
Ein Verweis im Format *x [ i ]* auf das Bit an Position *i* in Bitset *x*.

#### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Bit in dem Bitset, das von der Argument Position für die ersten, zweiten und fünften Element Funktionen des Klassen Verweises angegeben wird, und **`true`** oder **`false`** , um den Wert des geänderten Bits im Bitset für die dritten und vierten Element Funktionen des Klassen Verweises widerzuspiegeln.

#### <a name="remarks"></a>Bemerkungen

Die Klasse `reference` existiert nur als Hilfsprogrammklasse für das Bitset `operator[]`. Die Memberklasse beschreibt ein Objekt, das auf ein einzelnes Bit in einem Bitset zugreifen kann. Let *b* ist ein Objekt vom Typ **`bool`** , *x* -und *y* -Objekten vom Typ **Bitset \<** *N* **> **und *i* und *j* gültige Positionen innerhalb eines solchen Objekts. Die Notation *x [i]* verweist auf das Bit an Position *i* in Bitset *x*. Die Memberfunktionen der Klasse `reference` stellen in der genannten Reihenfolge die folgenden Vorgänge bereit:

|Vorgang|Definition|
|---------------|----------------|
|*x*[*i*] = *b*|Speichert **`bool`** Wert *b* an Bitposition *i* in Bitset *x*.|
|*x*[*i*] = *y*[*j*]|Speichert den Wert des Bits *y*[ *j*] an Bitposition *i* in Bitset *x*.|
|*b* = ~ *x*[*i*]|Speichert den gekippten Wert des Bits *x*[ *i*] in **`bool`** *b*.|
|*b*  =  *x*[*i*]|Speichert den Wert des Bits *x*[ *i*] in **`bool`** *b*.|
|*x*[*i*]. `flip`( )|Speichert den gespiegelten Wert des Bits *x*[ *i*] an der Bitposition *i* in *x* zurück.|

#### <a name="example"></a>Beispiel

```cpp
// bitset_reference.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 2 );
   bitset<5> b2 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."
        << endl;

   // Example of x [i] = b storing bool b at bit position i
   // in bitset x
   b1[ 0 ] = true;
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"
        << "is: ( "<< b1 << " )" << endl;

   // Example of x [i] = y [j] storing the bool value of the
   // bit at position j in bitset y at bit position i in bitset x
   b2 [4] = b1 [0];      // b1 [0] = true
   cout << "The bitset<5> b2 with the bit at position 4 set to the "
        << "value\nof the bit at position 0 of the bit in "
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;

   // Example of b = ~x [i] flipping the value of the bit at
   // position i of bitset x and storing the value in an
   // object b of type bool
   bool b = ~b2 [4];      // b2 [4] = false
   if ( b )
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is false." << endl;

   // Example of b = x [i] storing the value of the bit at
   // position i of bitset x in the object b of type bool
   b = b2 [4];
   if ( b )
      cout << "The value of the object b = b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = b2 [4] "
           << "of type bool is false." << endl;

   // Example of x [i] . flip ( ) toggling the value of the bit at
   // position i of bitset x
   cout << "Before flipping the value of the bit at position 4 in "
        << "bitset b2,\nit is ( "<<  b2  << " )." << endl;
   b2 [4].flip( );
   cout << "After flipping the value of the bit at position 4 in "
        << "bitset b2,\nit becomes ( "<<  b2  << " )." << endl;
   bool c;
   c = b2 [4].flip( );
   cout << "After a second flip, the value of the position 4 "
        << "bit in b2 is now: " << c << ".";
}
```

```Output
The initialized bitset<5> b1( 2 ) is: ( 00010 ).
The initialized bitset<5> b2( 6 ) is: ( 00110 ).
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )
The bitset<5> b2 with the bit at position 4 set to the value
of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )
The value of the object b = ~b2 [4] of type bool is false.
The value of the object b = b2 [4] of type bool is true.
Before flipping the value of the bit at position 4 in bitset b2,
it is ( 10110 ).
After flipping the value of the bit at position 4 in bitset b2,
it becomes ( 00110 ).
After a second flip, the value of the position 4 bit in b2 is now: 1.
```

### <a name="reset"></a><a name="reset"></a> Festlegen

Setzt alle Bits in einem Bitset auf 0 zurück, oder setzt ein Bit an einer angegebenen Position auf 0 zurück.

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Position des auf 0 zurückzusetzenden Bits im Bitset.

#### <a name="return-value"></a>Rückgabewert

Eine Kopie des Bitsets, für das die Memberfunktion aufgerufen wurde.

#### <a name="remarks"></a>Bemerkungen

Die zweite Memberfunktion löst eine [out_of_range](../standard-library/out-of-range-class.md)-Ausnahme aus, wenn die angegebene Position größer ist als die Größe des Bitsets.

#### <a name="example"></a>Beispiel

```cpp
// bitset_reset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 13 );
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1r3;
   b1r3 = b1.reset( 2 );
   cout << "The collecion of bits obtained from resetting the\n"
        << "third bit of bitset b1 is: ( "<< b1r3 << " )"
        << endl;

   bitset<5> b1r;
   b1r = b1.reset( );
   cout << "The collecion of bits obtained from resetting all\n"
        << "the elements of the bitset b1 is: ( "<< b1r << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(13) is: ( 01101 )
The collecion of bits obtained from resetting the
third bit of bitset b1 is: ( 01001 )
The collecion of bits obtained from resetting all
the elements of the bitset b1 is: ( 00000 )
```

### <a name="set"></a><a name="set"></a> Set

Setzt alle Bits in einem Bitset auf 1, oder setzt ein Bit an einer angegebenen Position auf 1.

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Position des Bits im Bitset, das auf einen zugewiesenen Wert gesetzt werden soll.

*ster*\
Der Wert, der dem Bit an der angegebenen Position zugewiesen werden soll.

#### <a name="return-value"></a>Rückgabewert

Eine Kopie des Bitsets, für das die Memberfunktion aufgerufen wurde.

#### <a name="remarks"></a>Bemerkungen

Die zweite Memberfunktion löst eine [out_of_range](../standard-library/out-of-range-class.md)-Ausnahme aus, wenn die angegebene Position größer ist als die Größe des Bitsets.

#### <a name="example"></a>Beispiel

```cpp
// bitset_set.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1s0;
   b1s0 = b1.set( 0 );
   cout << "The collecion of bits obtained from setting the\n"
        << "zeroth bit of bitset b1 is: ( "<< b1s0 << " )"
        << endl;

   bitset<5> bs1;
   bs1 = b1.set( );
   cout << "The collecion of bits obtained from setting all the\n"
        << "elements of the bitset b1 is: ( "<< bs1 << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(6) is: ( 00110 )
The collecion of bits obtained from setting the
zeroth bit of bitset b1 is: ( 00111 )
The collecion of bits obtained from setting all the
elements of the bitset b1 is: ( 11111 )
```

### <a name="size"></a><a name="size"></a> Größe

Gibt die Anzahl der Bits in einem bitset-Objekt zurück.

```cpp
size_t size() const;
```

#### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bits ( *N*) in einem Bitset \<N> .

#### <a name="example"></a>Beispiel

```cpp
// bitset_size.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main()
{
    using namespace std;

    bitset<5> b1(6);
    size_t i;

    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"
         << endl;

    i = b1.size();

    cout << "The number of bits in bitset b1 is: " << i << "."
         << endl;
}
```

```Output
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )
The number of bits in bitset b1 is: 5.
```

### <a name="test"></a><a name="test"></a> Test

Überprüft, ob das Bit an einer angegebenen Position in einem Bitset auf 1 gesetzt ist.

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>Parameter

*_Pos*\
Die Position des auf seinen Wert zu prüfenden Bits im Bitset.

#### <a name="return-value"></a>Rückgabewert

**`true`** , wenn das von der Argument Position angegebene Bit auf 1 festgelegt ist. andernfalls **`false`** .

#### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt [out_of_range](../standard-library/out-of-range-class.md) aus.

### <a name="to_string"></a><a name="to_string"></a> to_string

Konvertiert ein bitset-Objekt in eine Zeichen folgen Darstellung.

```cpp
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>Rückgabewert

Ein Zeichen folgen Objekt der-Klasse `basic_string` , bei dem jedes Bit, das im Bitset festgelegt ist, ein entsprechendes Zeichen von 1 und ein Zeichen 0 (null) ist, wenn das Bit nicht festgelegt ist.

#### <a name="example"></a>Beispiel

```cpp
// bitset_to_string.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   string s1;
   s1 =  b1.template to_string<char,
   char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n  by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The string returned from the bitset b1
  by the member function to_string( ) is: 00111.
```

### <a name="to_ullong"></a><a name="to_ullong"></a> to_ullong

Gibt einen- **`unsigned long long`** Wert zurück, der die gleichen Bits enthält, die für den Inhalt des Bitset-Objekts festgelegt sind.

```cpp
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>Rückgabewert

Gibt die Summe der Bitwerte in der Bitsequenz als zurück **`unsigned long long`** . **`unsigned long long`** Mit diesem Wert werden die gleichen Mengen Bits neu erstellt, wenn Sie verwendet werden, um ein Bitset zu initialisieren.

#### <a name="exceptions"></a>Ausnahmen

Löst ein [overflow_error](overflow-error-class.md) Objekt aus, wenn ein beliebiges Bit in der Bitsequenz einen Bitwert hat, der nicht als Wert des Typs dargestellt werden kann **`unsigned long long`** .

#### <a name="remarks"></a>Bemerkungen

Gibt die Summe der Bitwerte in der Bitsequenz als zurück **`unsigned long long`** .

### <a name="to_ulong"></a><a name="to_ulong"></a> to_ulong

Konvertiert ein bitset-Objekt in die ganze Zahl, die die enthaltene Bits-Sequenz generiert, wenn das Bitset initialisiert wird.

```cpp
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die die Bits in einem Bitset generiert, wenn diese bei der Initialisierung des Bitsets verwendet werden.

#### <a name="remarks"></a>Bemerkungen

Durch Anwenden der Member-Funktion wird die ganze Zahl zurückgegeben, die dieselbe Sequenz von 1 und 0 Ziffern hat, wie Sie in der im bitset enthaltenen Bits-Sequenz gefunden werden.

Die Member-Funktion löst ein [overflow_error](overflow-error-class.md) Objekt aus, wenn ein beliebiges Bit in der Bitsequenz einen Bitwert hat, der nicht als Wert des Typs dargestellt werden kann **`unsigned long`** .

#### <a name="example"></a>Beispiel

```cpp
// bitset_to_ulong.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   unsigned long int i;
   i = b1.to_ulong( );
   cout << "The integer returned from the bitset b1,"
        << "\n  by the member function to_long( ), that"
        << "\n  generated the bits as a base two number is: "
        << i << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The integer returned from the bitset b1,
  by the member function to_long( ), that
  generated the bits as a base two number is: 7.
```
