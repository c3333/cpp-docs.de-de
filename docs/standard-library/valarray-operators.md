---
title: '&lt;valarray&gt;-Operatoren'
ms.date: 03/27/2019
f1_keywords:
- valarray/std::operator!=
- valarray/std::operator%
- valarray/std::operator&amp;
- valarray/std::operator&amp;&amp;
- valarray/std::operator&gt;
- valarray/std::operator&gt;&gt;
- valarray/std::operator&gt;=
- valarray/std::operator&lt;
- valarray/std::operator&lt;&lt;
- valarray/std::operator&lt;=
- valarray/std::operator*
- valarray/std::operator+
- valarray/std::operator-
- valarray/std::operator/
- valarray/std::operator==
- valarray/std::operator^
- valarray/std::operator|
- valarray/std::operator||
ms.assetid: 8a53562c-90ab-4eb3-85d3-ada5259d90b0
helpviewer_keywords:
- std::operator!= (valarray), std::operator&amp; (valarray)
- std::operator&amp;&amp; (valarray)
- std::operator&gt; (valarray)
- std::operator&gt;&gt; (valarray)
- std::operator&gt;= (valarray)
- std::operator&lt; (valarray)
- std::operator&lt;&lt; (valarray)
- std::operator&lt;= (valarray), std::operator== (valarray)
ms.openlocfilehash: 76eb3553090cd88cf0798b2b17bbd49906852e40
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212008"
---
# <a name="ltvalarraygt-operators"></a>&lt;valarray&gt;-Operatoren

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Überprüft, ob die entsprechenden Elemente von zwei gleich großen valarray-Objekten ungleich sind oder ob alle Elemente eines valarray-Objekts entsprechend einem angegebenen Wert ungleich sind.

```cpp
template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator!=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente auf Ungleichheit getestet werden sollen.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente auf Ungleichheit getestet werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein valarray-Objekt mit booleschen Werten, für die Folgendes gilt:

- **`true`**, wenn die entsprechenden Elemente ungleich sind.

- **`false`**, wenn die entsprechenden Elemente nicht ungleich sind.

### <a name="remarks"></a>Bemerkungen

Der erste Vorlagen Operator gibt ein Objekt der Klasse [Valarray \<bool> ](../standard-library/valarray-bool-class.md)zurück, dessen Elemente den Wert haben `I` `left[I] != right[I]` .

Der zweite Vorlagen Operator speichert im-Element `I` `left[I] != right` .

Der dritte Vorlagen Operator speichert im-Element `I` `left != right[I]` .

### <a name="example"></a>Beispiel

```cpp
// valarray_op_ne.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL != vaR );
   cout << "The element-by-element result of "
        << "the not equal comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the not equal comparison test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="operator"></a><a name="op_mod"></a>KOM

Ruft den Rest der Division der entsprechenden Elemente von zwei gleich großen valarray-Objekten oder der Division eines valarray-Objekts durch einen angegebenen Wert oder der Division eines angegebenen Werts durch ein valarray-Objekt ab.

```cpp
template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator%(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Wert oder ein valarray-Objekt, der bzw. das als Dividend dient, durch den ein anderer Wert oder ein anderes valarray-Objekt dividiert wird.

*Richting*\
Ein Wert oder ein valarray-Objekt, der bzw. das als Divisor dient und der einen anderen Wert oder ein anderes valarray-Objekt dividiert.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente die Element weisen restader von *Links* dividiert durch *right*sind.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   valarray<int> vaREM ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaREM = ( vaL % vaR );
   cout << "The remainders from the element-by-element "
        << "division is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaREM [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).
The initial Right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="operatoramp"></a><a name="op_amp"></a>KOM&amp;

Ruft das bitweise **AND** zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps ab.

```cpp
template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente jeweils mit dem bitweisen `AND`-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der bitweise mit den Elementen eines valarray-Objekts verknüpft werden soll.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente jeweils mit dem bitweisen `AND`-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der bitweise mit den Elementen eines valarray-Objekts verknüpft werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente die Element Weise Kombination der bitweisen and-Operation von *left* und *right*darstellen.

### <a name="remarks"></a>Bemerkungen

Eine bitweise Operation kann nur verwendet werden, um Bits in **`char`** -und- **`int`** Datentypen und-Varianten und nicht in **`float`** , **`double`** , **longdouble**, **`void`** **`bool`** oder anderen, komplexeren Datentypen zu bearbeiten.

Für die bitweise `AND`-Operation gilt dieselbe Wahrheitstabelle wie für die logische `AND`-Operation. Die bitweise OR-Operation wird jedoch nur auf den Datentyp auf der Ebene der Einzelbits angewendet. Der [operator&&](#op_amp_amp) wird auf Elementebene angewendet, wobei alle Werte, die nicht null sind, als TRUE zählen, und das Ergebnis ein valarray-Objekt mit booleschen Werten ist. Der bitweise `AND` [Operator&](#op_amp)hingegen in Abhängigkeit vom Ergebnis der bitweisen Operation ein Valarray-Element mit anderen Werten als 0 und 1 ergeben.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaBWA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i+1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaBWA = ( vaL & vaR );
   cout << "The element-by-element result of "
        << "the bitwise operator & is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaBWA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the bitwise operator & is the
valarray: ( 0 0 0 0 0 4 0 0 0 8 ).
```

## <a name="operatorampamp"></a><a name="op_amp_amp"></a>KOM&amp;&amp;

Ruft das logische **AND** zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps des valarray-Objekts ab.

```cpp
template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator&&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente jeweils mit dem logischen `AND`-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der mit den Elementen eines valarray-Objekts verknüpft werden soll.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente jeweils mit dem logischen `AND`-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der mit den Elementen eines valarray-Objekts verknüpft werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente vom Typ "bool" sind und die Element Weise Kombination der logischen Ausführung `AND` von " *Links* " und " *right*" sind.

### <a name="remarks"></a>Bemerkungen

Das logische `ANDoperator&&` gilt für eine Element Ebene, wobei alle Werte ungleich 0 als true gezählt werden und das Ergebnis ein Valarray-Wert von booleschen Werten ist. Die bitweise Version von `AND` [Operator&](#op_amp)kann dagegen je nach Ergebnis der bitweisen Operation ein Valarray-Element mit anderen Werten als 0 und 1 ergeben.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_logand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL && vaR );
   cout << "The element-by-element result of "
        << "the logical AND operator&& is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&& is the
valarray: ( 0 0 0 1 0 1 0 1 0 1 ).
```

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Überprüft, ob die Elemente eines valarray-Objekts größer sind als die Elemente eines gleich großen valarray-Objekts oder ob alle Elemente eines valarray-Objekts größer oder kleiner sind als ein angegebener Wert.

```cpp
template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente verglichen werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts verglichen werden sollen.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente verglichen werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts verglichen werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein valarray-Objekt mit booleschen Werten, für die Folgendes gilt:

- **`true`**, wenn das linke Element oder der *linke* Wert größer als das entsprechende Rechte Element oder der *Rechte* Wert ist.

- **`false`**, wenn das linke Element oder der *linke* Wert nicht größer als das entsprechende Rechte Element oder der *Rechte* Wert ist.

### <a name="remarks"></a>Bemerkungen

Wenn die Anzahl von Elementen in zwei valarray-Objekten nicht übereinstimmt, ist das Ergebnis nicht definiert.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_gt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL > vaR );
   cout << "The element-by-element result of "
        << "the greater than comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Überprüft, ob die Elemente eines valarray-Objekts größer gleich den Elementen eines gleich großen valarray-Objekts oder ob alle Elemente eines valarray-Objekts größer gleich oder kleiner gleich einem angegebenen Wert sind.

```cpp
template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente verglichen werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts verglichen werden sollen.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente verglichen werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts verglichen werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein valarray-Objekt mit booleschen Werten, für die Folgendes gilt:

- **`true`**, wenn das linke Element oder der *linke* Wert größer oder gleich dem entsprechenden *rechten* Element oder Wert ist.

- **`false`**, wenn das linke Element oder der *linke* Wert kleiner als das entsprechende Rechte Element oder der *Rechte* Wert ist.

### <a name="remarks"></a>Bemerkungen

Wenn die Anzahl von Elementen in zwei valarray-Objekten nicht übereinstimmt, ist das Ergebnis nicht definiert.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_ge.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >= vaR );
   cout << "The element-by-element result of "
        << "the greater than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than or equal test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>KOM&gt;&gt;

Verschiebt die Bits für jedes Element eines valarray-Objekts um eine angegebene Anzahl von Positionen oder um einen elementweisen Betrag, der durch ein zweites valarray-Objekt angegeben ist, nach rechts.

```cpp
template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator>>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Der Wert, der verschoben werden soll, oder das valarray-Objekt, dessen Elemente verschoben werden sollen.

*Richting*\
Der Wert, der den Betrag angibt, um den die Bits nach rechts verschoben werden, oder das valarray-Objekt, dessen Elemente den elementweisen Betrag angeben, um den die Bits nach rechts verschoben werden.

### <a name="return-value"></a>Rückgabewert

Ein valarray-Objekt, dessen Elemente um den angegebenen Betrag nach rechts verschoben wurden.

### <a name="remarks"></a>Bemerkungen

Bei Zahlen mit Vorzeichen bleiben die Vorzeichen erhalten.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >> vaR );
   cout << "The element-by-element result of "
        << "the right shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Überprüft, ob die Elemente eines valarray-Objekts kleiner sind als die Elemente eines gleich großen valarray-Objekts oder ob alle Elemente eines valarray-Objekts größer oder kleiner sind als ein angegebener Wert.

```cpp
template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente verglichen werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts verglichen werden sollen.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente verglichen werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts verglichen werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein valarray-Objekt mit booleschen Werten, für die Folgendes gilt:

- **`true`**, wenn das linke Element oder der *linke* Wert kleiner als das entsprechende Rechte Element oder der *Rechte* Wert ist.

- **`false`**, wenn das linke Element oder der *linke* Wert nicht kleiner als das entsprechende Rechte Element oder der *Rechte* Wert ist.

### <a name="remarks"></a>Bemerkungen

Wenn die Anzahl von Elementen in zwei valarray-Objekten nicht übereinstimmt, ist das Ergebnis nicht definiert.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_lt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL < vaR );
   cout << "The element-by-element result of "
        << "the less-than comparson test is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the less-than comparson test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Überprüft, ob die Elemente eines valarray-Objekts kleiner gleich den Elementen eines gleich großen valarray-Objekts oder ob alle Elemente eines valarray-Objekts größer gleich oder kleiner gleich einem angegebenen Wert sind.

```cpp
template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente verglichen werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts verglichen werden sollen.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente verglichen werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts verglichen werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein valarray-Objekt mit booleschen Werten, für die Folgendes gilt:

- **`true`**, wenn das linke Element oder der *linke* Wert kleiner oder gleich dem entsprechenden *rechten* Element oder Wert ist.

- **`false`**, wenn das linke Element oder der *linke* Wert größer als das entsprechende Rechte Element oder der *Rechte* Wert ist.

### <a name="remarks"></a>Bemerkungen

Wenn die Anzahl von Elementen in zwei valarray-Objekten nicht übereinstimmt, ist das Ergebnis nicht definiert.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_le.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL <= vaR );
   cout << "The element-by-element result of "
        << "the less than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the less than or equal test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>KOM&lt;&lt;

Verschiebt die Bits für jedes Element eines valarray-Objekts um eine angegebene Anzahl von Positionen oder um einen elementweisen Betrag, der durch ein zweites valarray-Objekt angegeben ist, nach links.

```cpp
template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator<<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Der Wert, der verschoben werden soll, oder das valarray-Objekt, dessen Elemente verschoben werden sollen.

*Richting*\
Der Wert, der den Betrag angibt, um den die Bits nach links verschoben werden, oder das valarray-Objekt, dessen Elemente den elementweisen Betrag angeben, um den die Bits nach links verschoben werden.

### <a name="return-value"></a>Rückgabewert

Ein valarray-Objekt, dessen Elemente um den angegebenen Betrag nach links verschoben wurden.

### <a name="remarks"></a>Bemerkungen

Bei Zahlen mit Vorzeichen bleiben die Vorzeichen erhalten.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL << vaR );
   cout << "The element-by-element result of "
        << "the left shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift is the
valarray: ( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="operator"></a><a name="op_star"></a>KOM

Ruft das elementweise Produkt zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert ab.

```cpp
template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator*(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente multipliziert werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts multipliziert werden sollen.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente multipliziert werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts multipliziert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente das Element Weise Produkt von *Links* und *Rechts*sind.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_eprod.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL * vaR );
   cout << "The element-by-element result of "
        << "the multiplication is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
```

## <a name="operator"></a><a name="op_add"></a>Operator +

Ruft die elementweise Summe zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert ab.

```cpp
template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator+(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente addiert werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts addiert werden sollen.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente addiert werden sollen, oder ein angegebener Wert, der mit den Elementen eines valarray-Objekts addiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente die Element Weise Summe von *Links* und *Rechts*sind.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_esum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL + vaR );
   cout << "The element-by-element result of "
        << "the sum is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a><a name="operator-"></a>KOM

Ruft die elementweise Differenz zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert ab.

```cpp
template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator-(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Wert oder ein valarray-Objekt, das als Minuend dient, von dem andere Werte oder valarray-Objekte subtrahiert werden und so eine Differenz ergeben.

*Richting*\
Ein Wert oder ein valarray-Objekt, das als Subtrahend dient, der von anderen Werten oder valarray-Objekten subtrahiert wird und so eine Differenz ergibt.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente die Element Weise Differenz von *Links* und *Rechts*sind.

### <a name="remarks"></a>Bemerkungen

Die arithmetische Terminologie, die zum Beschreiben einer Subtraktion verwendet wird:

Differenz = Minuend - Subtrahend

### <a name="example"></a>Beispiel

```cpp
// valarray_op_ediff.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL - vaR );
   cout << "The element-by-element result of "
        << "the difference is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="operator"></a><a name="op_div"></a>KOM

Ruft den elementweise Quotienten zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert ab.

```cpp
template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator/(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Wert oder ein valarray-Objekt, der bzw. das als Dividend dient, durch den ein anderer Wert oder ein anderes valarray-Objekt dividiert wird und so den Quotienten ergibt.

*Richting*\
Ein Wert oder ein valarray-Objekt, der bzw. das als Divisor dient und der einen anderen Wert oder ein anderes valarray-Objekt dividiert und so den Quotienten ergibt.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente der Element Weise Quotienten von *left* (dividiert durch *Rechts*) ist.

### <a name="remarks"></a>Bemerkungen

Die arithmetische Terminologie, die zum Beschreiben einer Division verwendet wird:

Quotient = Dividend/Divisor

### <a name="example"></a>Beispiel

```cpp
// valarray_op_equo.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   valarray<double> vaNE ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL / vaR );
   cout << "The element-by-element result of "
        << "the quotient is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Überprüft, ob die entsprechenden Elemente von zwei gleich großen valarray-Objekten gleich sind oder ob alle Elemente eines valarray-Objekts entsprechend einem angegebenen Wert gleich sind.

```cpp
template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator==(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente auf Gleichheit getestet werden sollen.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente auf Gleichheit getestet werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein valarray-Objekt mit booleschen Werten, für die Folgendes gilt:

- **`true`**, wenn die entsprechenden Elemente gleich sind.

- **`false`**, wenn die entsprechenden Elemente nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Der erste Vorlagen Operator gibt ein Objekt der Klasse [Valarray \<bool> ](../standard-library/valarray-bool-class.md)zurück, dessen Elemente den Wert haben `I` `left[I] == right[I]` . Der zweite Vorlagen Operator speichert im-Element `I` `left[I] == right` . Der dritte Vorlagen Operator speichert im-Element `I` `left == right[I]` .

### <a name="example"></a>Beispiel

```cpp
// valarray_op_eq.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL == vaR );
   cout << "The element-by-element result of "
        << "the equality comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the equality comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="operator"></a><a name="op_xor"></a>Operator ^

Ruft das bitweise exklusive `OR` ( **XOR**) zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps ab.

```cpp
template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator^(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente jeweils mit dem bitweisen **XOR**-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der bitweise mit den Elementen eines valarray-Objekts verknüpft werden soll.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente jeweils mit dem bitweisen **XOR**-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der bitweise mit den Elementen eines valarray-Objekts verknüpft werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente die Element Weise Kombination der bitweisen **Xor** -Operation von *Links* und *Rechts*darstellen.

### <a name="remarks"></a>Bemerkungen

Eine bitweise Operation kann nur verwendet werden, um Bits in **`char`** -und- **`int`** Datentypen und-Varianten und nicht in **`float`** ,,, **`double`** **`long double`** **`void`** **`bool`** oder anderen, komplexeren Datentypen zu bearbeiten.

Das bitweise exklusive `OR` ( **Xor**) verfügt über die folgende Semantik: bei den *Bits b*1 *und b*2 ist *b*1 **Xor** *b*2, **`true`** wenn genau eines der Bits true ist;, **`false`** Wenn beide Bits false sind oder wenn beide Bits true sind.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_xor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL ^ vaR );
   cout << "The element-by-element result of "
        << "the bitwise XOR operator^ is the\n"
        << "valarray: ( ";
           for ( i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^ is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="operator124"></a><a name="op_or"></a>Operator&#124;

Ruft das bitweise `OR` zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps ab.

```cpp
template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator|(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente jeweils mit dem bitweisen `OR`-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der bitweise mit den Elementen eines valarray-Objekts verknüpft werden soll.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente jeweils mit dem bitweisen `OR`-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der bitweise mit den Elementen eines valarray-Objekts verknüpft werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente die Element Weise Kombination der bitweisen `OR` -Operation von *Links* und *Rechts*darstellen.

### <a name="remarks"></a>Bemerkungen

Eine bitweise Operation kann nur verwendet werden, um Bits in **`char`** -und- **`int`** Datentypen und-Varianten und nicht in **`float`** , **`double`** , **longdouble**, **`void`** **`bool`** oder anderen, komplexeren Datentypen zu bearbeiten.

Für die bitweise OR-Operation gilt dieselbe Wahrheitstabelle wie für die logische `OR`-Operation. Die bitweise OR-Operation wird jedoch nur auf den Datentyp auf der Ebene der Einzelbits angewendet. Bei Bits *b*1 und *b*2 ist *b*1 `OR` *b*2, **`true`** Wenn mindestens eines der Bits true ist oder **`false`** beide Bits false sind. Der logische `OR` [Operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor) wird auf Element Ebene angewendet, wobei alle Werte ungleich NULL als gezählt **`true`** werden und das Ergebnis ein Valarray-Wert von booleschen Werten ist. Der bitweise OR `operator|` kann dagegen je nach dem Ergebnis der bitweisen Operation ein valarray-Objekt mit anderen Werten als 0 und 1 ergeben.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL | vaR );
   cout << "The element-by-element result of "
        << "the bitwise OR operator| is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise OR operator| is the
valarray: ( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="operator124124"></a><a name="op_lor"></a>Operator&#124;&#124;

Ruft das logische `OR` zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps des valarray-Objekts ab.

```cpp
template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator||(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das erste der beiden valarray-Objekte, deren Elemente jeweils mit dem logischen `OR`-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der mit den Elementen eines valarray-Objekts verknüpft werden soll.

*Richting*\
Das zweite der beiden valarray-Objekte, deren Elemente jeweils mit dem logischen `OR`-Operator verknüpft werden soll, oder ein angegebener Wert des Elementtyps, der mit den Elementen eines valarray-Objekts verknüpft werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Valarray-Element, dessen Elemente vom Typ **`bool`** und sind die Element Weise Kombination der logischen OR-Operation von *left* und *right*.

### <a name="remarks"></a>Bemerkungen

Das logische `OR` `operator||` gilt für eine Element Ebene, wobei alle Werte ungleich NULL als gezählt **`true`** werden, und das Ergebnis ein Valarray-Wert von booleschen Werten ist. Die bitweise Version von `OR`, [operator&#124;](../standard-library/valarray-operators.md#op_or) kann dagegen je nach dem Ergebnis der bitweisen Operation ein valarray-Objekt mit anderen Werten als 0 und 1 ergeben.

### <a name="example"></a>Beispiel

```cpp
// valarray_op_logor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLOR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLOR = ( vaL || vaR );
   cout << "The element-by-element result of "
        << "the logical OR operator|| is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaLOR [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).
The element-by-element result of the logical OR operator|| is the
valarray: ( 0 0 0 1 0 1 1 1 0 1 ).
```
