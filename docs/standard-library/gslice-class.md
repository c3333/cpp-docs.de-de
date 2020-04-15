---
title: gslice-Klasse
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
ms.openlocfilehash: 07c987fb08a213bb66da628bec3021a3bf9ba24a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370626"
---
# <a name="gslice-class"></a>gslice-Klasse

Eine Hilfsprogrammklasse zu valarray, die zum Definieren von mehrdimensionaler Teilmengen von einem valarray verwendet wird. Wenn ein valarray als mehrdimensionale Matrix mit allen Elementen in einem Array angesehen wird, extrahiert das Segment einen Vektor aus dem mehrdimensionalen Array.

## <a name="remarks"></a>Bemerkungen

Die Klasse speichert die Parameter, die ein Objekt des Typs [gslice_array](../standard-library/gslice-array-class.md) charakterisieren. Die Teilmenge eines Valarrays wird indirekt erstellt, wenn ein Objekt der Klasse gslice als Argument für ein Objekt des [Klassen-Valarray-Typs](../standard-library/valarray-class.md#op_at)**\<>** angezeigt wird. Die gespeicherten Werte, die die aus dem übergeordneten valarray ausgewählte Teilmenge angeben, enthalten:

- Einen Startindex.

- Ein Längenvektor `valarray<size_t>`der Klasse .

- Ein Schrittvektor `valarray<size_t>`der Klasse .

Die beiden Vektoren müssen dieselbe Länge haben.

Wenn der von einem gslice festgelegte Teil eine Teilmenge eines konstanten valarray ist, ist das gslice ein neues valarray. Ist die durch ein Gslice definierte Menge die Teilmenge von einem nichtkonstanten valarray, hat das gslice Verweissemantik zum ursprünglichen valarray. Der Auswertungsmechanismus für nichtkonstante valarrays spart Zeit und Speicherplatz.

Vorgänge für valarrays sind nur garantiert, wenn die durch die gslices definierten Quell- und Zielteilmengen verschieden und alle Indizes gültig sind.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[gslice](#gslice)|Definiert eine Teilmenge von `valarray`, die aus mehreren Segmenten von `valarray` besteht, die alle bei einem angegebenen Element beginnen.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Größe](#size)|Sucht die Arraywerte durch Angabe der Anzahl von Elementen in einem allgemeinen Segment von `valarray`.|
|[Starten](#start)|Sucht den Startindex eines allgemeinen Segments von `valarray`.|
|[Schritt](#stride)|Sucht den Abstand zwischen Elementen in einem allgemeinen Segment von `valarray`.|

## <a name="requirements"></a>Anforderungen

**Header:** \<valarray>

**Namespace:** std

## <a name="gslicegslice"></a><a name="gslice"></a>gslice::gslice

Eine Hilfsklasse der valarray-Klasse, die zum Definieren von mehrdimensionalen Segmenten eines valarray-Objekts verwendet wird.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parameter

*_StartIndex*\
Der valarray-Index des ersten Elements der Teilmenge.

*_LenArray*\
Ein Array, das die Anzahl der Elemente in jedem Segment angibt.

*_IncArray*\
Ein Array, das die Sprünge in jedem Segment angibt.

### <a name="return-value"></a>Rückgabewert

Der Standardkonstruktor speichert 0 (null) für den Startindex und leere Vektoren für die Längen- und Sprungvektoren. Der zweite Konstruktor speichert *_StartIndex* für den Startindex, *_LenArray* für das Längenarray und *_IncArray* für das Schrittarray.

### <a name="remarks"></a>Bemerkungen

**gslice** definiert eine Teilmenge eines valarray, die aus mehreren Segmenten des valarray besteht, und die jeweils am gleichen angegebenen Element beginnen. Die Möglichkeit, Arrays zu verwenden, um mehrere Segmente zu definieren, ist der einzige Unterschied zwischen `gslice` und [slice:: slice](../standard-library/slice-class.md#slice). Das erste Slice hat ein erstes Element mit einem Index von *_StartIndex*, einer Reihe von Elementen, die durch das erste Element von *_LenArray*angegeben werden, und einem Schritt, der vom ersten Element *_IncArray*gegeben wird. Der erste Satz der orthogonalen Segmente hat erste Elemente, die durch das erste Segment angegeben wurden. Das zweite Element von *_LenArray* gibt die Anzahl der Elemente an. Der Schritt wird durch das zweite Element von *_IncArray*gegeben. Eine dritte Dimension der Segmente würde die Elemente des zweidimensionalen Arrays als Startelemente nehmen und analog verfahren.

### <a name="example"></a>Beispiel

```cpp
// gslice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:" << endl << "(";
   for ( i = 0 ; i < 20 ; i++ )
      cout << " " << va [ i ];
   cout << " )" << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];

   cout << "The valarray for vaGSlice is vaResult:" << endl
        << "va[vaGSlice] = (";

   for ( i = 0 ; i < 8 ; i++ )
      cout << " " << vaResult [ i ];
   cout << ")" << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)
```

## <a name="gslicesize"></a><a name="size"></a>gslice::Größe

Sucht die Arraywerte durch Angabe der Anzahl von Elementen in einem allgemeinen Segment eines valarray.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Rückgabewert

Ein valarray, das die Anzahl der Elemente in jedem Segment eines allgemeinen Segments eines valarray angibt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt die gespeicherten Segmentlängen zurück.

### <a name="example"></a>Beispiel

```cpp
// gslice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> sizeGS = vaGSlice.size ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The size of vaResult is:"
        << "\n vaGSlice.size ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << sizeGS[ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The size of the valarray is: 20.

The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The size of vaResult is:
vaGSlice.size ( ) = ( 4 4 ).
```

## <a name="gslicestart"></a><a name="start"></a>gslice::start

Sucht den Startindex eines allgemeinen Segments eines valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Rückgabewert

Der Startindex eines allgemeinen Segments eines valarray.

### <a name="example"></a>Beispiel

```cpp
// gslice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   size_t vaGSstart = vaGSlice.start ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The index of the first element of vaResult is: "
        << vaGSstart << "." << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The index of the first element of vaResult is: 0.
```

## <a name="gslicestride"></a><a name="stride"></a>gslice::stride

Sucht den Abstand zwischen Elementen in einem allgemeinen Segment eines valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Rückgabewert

Ein valarray, das die Entfernungen zwischen Elementen in jedem Segment eines allgemeinen Segments eines valarray angibt.

### <a name="example"></a>Beispiel

```cpp
// gslice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for (i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> strideGS = vaGSlice.stride ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The strides of vaResult are:"
        << "\n vaGSlice.stride ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << strideGS[ i ] << " ";
   cout << ")." << endl;

}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The strides of vaResult are:
vaGSlice.stride ( ) = ( 7 4 ).
```

## <a name="see-also"></a>Siehe auch

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
