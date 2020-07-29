---
title: '&lt;utility&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: 7146c31e33b514b20703b280a7194f639c387c26
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215456"
---
# <a name="ltutilitygt-operators"></a>&lt;utility&gt;-Operatoren

> [!NOTE]
> Operatoren, die verwenden, `Type&` sind unter enthalten `namespace rel_ops` .

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Testet, ob das pair-Objekt links vom Operator ungleich dem pair-Objekt rechts vom Operator ist.

```cpp
template <class Type>
    constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `pair`.

*Richting*\
Ein Objekt des Typs `pair`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Paare nicht gleich sind. , **`false`** Wenn die Paare gleich sind.

### <a name="remarks"></a>Bemerkungen

Ein Paar ist gleich einem anderen, wenn jedes ihrer entsprechenden Elemente gleich ist. Zwei Paare sind ungleich, wenn das erste oder das zweite Element eines Paars nicht gleich dem entsprechenden Element des anderen Paars ist.

### <a name="example"></a>Beispiel

```cpp
// utility_op_ne.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 != p2 )
      cout << "The pairs p1 and p2 are not equal." << endl;
   else
      cout << "The pairs p1 and p2 are equal." << endl;

   if ( p1 != p3 )
      cout << "The pairs p1 and p3 are not equal." << endl;
   else
      cout << "The pairs p1 and p3 are equal." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.111 ).
The pair p2 is: ( 1000, 0.00111 ).
The pair p3 is: ( 10, 0.111 ).

The pairs p1 and p2 are not equal.
The pairs p1 and p3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Testet, ob das pair-Objekt links vom Operator gleich dem pair-Objekt rechts vom Operator ist.

```cpp
template <class T, class U>
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `pair`.

*Richting*\
Ein Objekt des Typs `pair`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Paare gleich sind. , **`false`** Wenn die `pair` e nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Ein Paar ist gleich einem anderen, wenn jedes ihrer entsprechenden Elemente gleich ist. Die Funktion gibt `left` zurück. **zuerst**  ==  `right` . **zuerst**  &&  `left` . **Zweitens**  ==  `right` . **Zweitens**. Zwei Paare sind ungleich, wenn das erste oder das zweite Element eines Paars nicht gleich dem entsprechenden Element des anderen Paars ist.

### <a name="example"></a>Beispiel

```cpp
// utility_op_eq.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 == p2 )
      cout << "The pairs p1 and p2 are equal." << endl;
   else
      cout << "The pairs p1 and p2 are not equal." << endl;

   if ( p1 == p3 )
      cout << "The pairs p1 and p3 are equal." << endl;
   else
      cout << "The pairs p1 and p3 are not equal." << endl;
}
```

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob das pair-Objekt links vom Operator kleiner als das pair-Objekt rechts vom Operator ist.

```cpp
template <class T, class U>
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `pair` auf der linken Seite des Operators.

*Richting*\
Ein Objekt des Typs `pair` auf der rechten Seite des Operators.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `pair` Links vom Operator strikt kleiner als das `pair` auf der rechten Seite des Operators ist; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Das `left` `pair` -Objekt wird als strikt kleiner als das `right` `pair` -Objekt bezeichnet, wenn *left* kleiner als und ungleich *right*ist.

In einem Vergleich von Paaren haben die ersten Elemente der Werte der beiden Paare die höchste Priorität. Unterscheiden sie sich, wird das Ergebnis ihres Vergleichs als Ergebnis des Vergleichs des Paars verwendet. Sind die Werte der ersten Elemente nicht unterschiedlich, werden die Werte der zweiten Elemente verglichen, und das Ergebnis von deren Vergleich wird als Ergebnis des Vergleichs des Paars verwendet.

### <a name="example"></a>Beispiel

```cpp
// utility_op_lt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 < p2 )
      cout << "The pair p1 is less than the pair p2." << endl;
   else
      cout << "The pair p1 is not less than the pair p2." << endl;

   if ( p1 < p3 )
      cout << "The pair p1 is less than the pair p3." << endl;
   else
      cout << "The pair p1 is not less than the pair p3." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).

The pair p1 is less than the pair p2.
The pair p1 is not less than the pair p3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Testet, ob das pair-Objekt links vom Operator kleiner gleich dem pair-Objekt rechts vom Operator ist.

```cpp
template <class Type>
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `pair` auf der linken Seite des Operators.

*Richting*\
Ein Objekt des Typs `pair` auf der rechten Seite des Operators.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `pair` Links vom Operator kleiner als oder gleich dem `pair` auf der rechten Seite des Operators ist; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

In einem Vergleich von Paaren haben die ersten Elemente der Werte der beiden Paare die höchste Priorität. Unterscheiden sie sich, wird das Ergebnis ihres Vergleichs als Ergebnis des Vergleichs des Paars verwendet. Sind die Werte der ersten Elemente nicht unterschiedlich, werden die Werte der zweiten Elemente verglichen, und das Ergebnis von deren Vergleich wird als Ergebnis des Vergleichs des Paars verwendet.

### <a name="example"></a>Beispiel

```cpp
// utility_op_le.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 <= p2 )
      cout << "The pair p1 is less than or equal to the pair p2." << endl;
   else
      cout << "The pair p1 is greater than the pair p2." << endl;

   if ( p1 <= p3 )
      cout << "The pair p1 is less than or equal to the pair p3." << endl;
   else
      cout << "The pair p1 is greater than the pair p3." << endl;

   if ( p1 <= p4 )
      cout << "The pair p1 is less than or equal to the pair p4." << endl;
   else
      cout << "The pair p1 is greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than or equal to the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is less than or equal to the pair p4.
```

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Testet, ob das pair-Objekt links vom Operator größer als das pair-Objekt rechts vom Operator ist.

```cpp
template <class Type>
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `pair` auf der linken Seite des Operators.

*Richting*\
Ein Objekt des Typs `pair` auf der rechten Seite des Operators.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `pair` auf der linken Seite des Operators streng größer als das `pair` auf der rechten Seite des Operators ist; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Das `left` `pair` -Objekt wird als strikt größer als das `right` `pair` -Objekt bezeichnet, wenn *left* größer als und ungleich *Rechts*ist.

In einem Vergleich von Paaren haben die ersten Elemente der Werte der beiden Paare die höchste Priorität. Unterscheiden sie sich, wird das Ergebnis ihres Vergleichs als Ergebnis des Vergleichs des Paars verwendet. Sind die Werte der ersten Elemente nicht unterschiedlich, werden die Werte der zweiten Elemente verglichen, und das Ergebnis von deren Vergleich wird als Ergebnis des Vergleichs des Paars verwendet.

### <a name="example"></a>Beispiel

```cpp
// utility_op_gt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 > p2 )
      cout << "The pair p1 is greater than the pair p2." << endl;
   else
      cout << "The pair p1 is not greater than the pair p2." << endl;

   if ( p1 > p3 )
      cout << "The pair p1 is greater than the pair p3." << endl;
   else
      cout << "The pair p1 is not greater than the pair p3." << endl;

   if ( p1 > p4 )
      cout << "The pair p1 is greater than the pair p4." << endl;
   else
      cout << "The pair p1 is not greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is not greater than the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is not greater than the pair p4.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Testet, ob das pair-Objekt links vom Operator größer gleich dem pair-Objekt rechts vom Operator ist.

```cpp
template <class Type>
    constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `pair` auf der linken Seite des Operators.

*Richting*\
Ein Objekt des Typs `pair` auf der rechten Seite des Operators.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `pair` Links vom Operator größer als oder gleich dem `pair` auf der rechten Seite des Operators ist; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

In einem Vergleich von Paaren haben die ersten Elemente der Werte der beiden Paare die höchste Priorität. Unterscheiden sie sich, wird das Ergebnis ihres Vergleichs als Ergebnis des Vergleichs des Paars verwendet. Sind die Werte der ersten Elemente nicht unterschiedlich, werden die Werte der zweiten Elemente verglichen, und das Ergebnis von deren Vergleich wird als Ergebnis des Vergleichs des Paars verwendet.

### <a name="example"></a>Beispiel

```cpp
// utility_op_ge.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 >= p2 )
      cout << "Pair p1 is greater than or equal to pair p2." << endl;
   else
      cout << "The pair p1 is less than the pair p2." << endl;

   if ( p1 >= p3 )
      cout << "Pair p1 is greater than or equal to pair p3." << endl;
   else
      cout << "The pair p1 is less than the pair p3." << endl;

   if ( p1 >= p4 )
      cout << "Pair p1 is greater than or equal to pair p4." << endl;
   else
      cout << "The pair p1 is less than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than the pair p2.
Pair p1 is greater than or equal to pair p3.
Pair p1 is greater than or equal to pair p4.
```
