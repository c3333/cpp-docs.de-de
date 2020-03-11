---
title: slice-Klasse
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
ms.openlocfilehash: 830e345eb7522cef44dbf6e727a976fb79c1e081
ms.sourcegitcommit: 49cf365176557456f56c994e06ea1a38f73e938b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937450"
---
# <a name="slice-class"></a>slice-Klasse

Eine Hilfsklasse für valarray, die dazu verwendet wird, eindimensionale Teilmengen eines übergeordneten valarrays zu definieren. Wenn ein valarray als eine zweidimensionale Matrix mit allen Elementen in einem Array angesehen wird, extrahiert das slice-Objekt einen Vektor in einer Dimension aus dem zweidimensionalen Array.

## <a name="remarks"></a>Bemerkungen

Die Klasse speichert die Parameter, die ein Objekt des Typs [slice_array](../standard-library/slice-array-class.md) charakterisieren. Die Teilmenge eines valarray wird indirekt erstellt, wenn ein Objekt der slice-Klasse als Argument für ein Objekt der Klasse [valarray](../standard-library/valarray-class.md#op_at) **\<Typ>** verwendet wird. Die gespeicherten Werte, die die aus dem übergeordneten valarray ausgewählte Teilmenge angeben, enthalten:

- Den Anfangsindex im valarray

- Die Gesamtlänge oder die Anzahl der Elemente im Segment

- Den Schritt oder den Abstand zwischen aufeinander folgenden Indizes der Elemente im valarray

Wenn die durch ein slice-Objekt definierte Menge eine Teilmenge eines konstanten valarrays ist, ist das slice-Objekt ein neues valarray. Ist die durch ein slice-Objekt definierte Menge eine Teilmenge eines nichtkonstanten valarrays, hat das slice-Objekt Verweissemantik zum ursprünglichen valarray. Der Auswertungsmechanismus für nichtkonstante valarrays spart Zeit und Speicherplatz.

Vorgänge für valarrays sind nur garantiert, wenn die durch die slice-Objekte definierten Quell- und Zielteilmengen verschieden und alle Indizes gültig sind.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[slice](#slice)|Definiert eine Teilmenge eines `valarray`s, die aus einer Anzahl von Elementen besteht, die jeweils denselben Abstand zueinander haben, und die am angegebenen Element beginnt.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[size](#size)|Ermittelt die Anzahl von Elementen eines slice-Objekts von einem `valarray`.|
|[start](#start)|Ermittelt den Startindex eines slice-Objekts von einem `valarray`.|
|[stride](#stride)|Ermittelt den Abstand zwischen den Elementen eines slice-Objekts von einem `valarray`.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<Valarray->

**Namespace:** std

## <a name="size"></a> slice::size

Ermittelt die Anzahl von Elementen in einem Slice eines valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Rückgabewert

Ermittelt die Anzahl von Elementen in einem Slice eines valarray.

### <a name="example"></a>Beispiel

```cpp
// slice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA, sizeVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   sizeVAR = vaSlice.size ( );
   cout << "The size of slice vaSlice is: "
        << sizeVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The size of the valarray is: 20.

The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The size of slice vaSlice is: 6.
```

## <a name="slice"></a> slice::slice

Definiert eine Teilmenge eines valarray, die aus einer Anzahl von Elementen besteht, die jeweils denselben Abstand zueinander haben und am angegebenen Element beginnen.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Parameter

*_StartIndex*\
Der valarray-Index des ersten Elements der Teilmenge.

*_Len*\
Die Anzahl von Elementen in der Teilmenge.

*Stride* -\
Der Abstand zwischen Elementen in der Teilmenge.

### <a name="return-value"></a>Rückgabewert

Der Standardkonstruktor speichert Nullen für Startindex, Gesamtlänge und Segment. Der zweite Konstruktor speichert *_StartIndex* für den Start Index, für die Gesamtlänge *_Len* und für den Schritt " *Stride* ".

### <a name="remarks"></a>Bemerkungen

Das Segment kann negativ sein.

### <a name="example"></a>Beispiel

```cpp
// slice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  2 * (i + 1 );

   cout << "The operand valarray va is:\n( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 1 , 7 , 3 );
   vaResult = va [ vaSlice ];

   cout << "\nThe slice of valarray va is vaResult:"
        << "\nva[slice( 1, 7, 3)] = ( ";
      for ( i = 0 ; i < 7 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).

The slice of valarray va is vaResult:
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).
```

## <a name="start"></a> slice::start

Ermittelt den Startindex eines Segments eines valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Rückgabewert

Ermittelt den Startindex eines Segments eines valarray.

### <a name="example"></a>Beispiel

```cpp
// slice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t startVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] = i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   startVAR = vaSlice.start ( );
   cout << "The start index of slice vaSlice is: "
        << startVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The start index of slice vaSlice is: 3.
```

## <a name="stride"></a> slice::stride

Ermittelt den Abstand zwischen den Elementen in einem Segment eines valarray.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>Rückgabewert

Ermittelt den Abstand zwischen den Elementen in einem Segment eines valarray.

### <a name="example"></a>Beispiel

```cpp
// slice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t strideVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  3 * ( i + 1 );

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 4 , 5 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 4, 5, 3)] =\n ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   strideVAR = vaSlice.stride ( );
   cout << "The stride of slice vaSlice is: "
        << strideVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =
( 15 24 33 42 51 ).
The stride of slice vaSlice is: 3.
```

## <a name="see-also"></a>Weitere Informationen

[Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
