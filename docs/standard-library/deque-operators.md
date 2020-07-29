---
title: '&lt;deque&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: d91fe64e7d06a80402a0a540be8f63d98ea96d37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222484"
---
# <a name="ltdequegt-operators"></a>&lt;deque&gt;-Operatoren

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Überprüft, ob das deque-Objekt links vom Operator ungleich dem deque-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `deque`.

*Richting*\
Ein Objekt des Typs `deque`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Doppel Schlange-Objekte nicht gleich sind. , wenn die Doppel Schlange- **`false`** Objekte gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den deque-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei deque-Objekte sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// deque_op_ne.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 2 );

   if ( c1 != c2 )
      cout << "The deques are not equal." << endl;
   else
      cout << "The deques are equal." << endl;
}
```

```Output
The deques are not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Überprüft, ob das deque-Objekt links vom Operator kleiner als das deque-Objekt rechts vom Operator ist.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `deque`.

*Richting*\
Ein Objekt des Typs `deque`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Doppel Schlange Links vom Operator kleiner als und nicht gleich der Doppel Schlange rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den deque-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "kleiner als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// deque_op_lt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "Deque c1 is less than deque c2." << endl;
   else
      cout << "Deque c1 is not less than deque c2." << endl;
}
```

```Output
Deque c1 is less than deque c2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Überprüft, ob das deque-Objekt links vom Operator kleiner gleich dem deque-Objekt rechts vom Operator ist.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `deque`.

*Richting*\
Ein Objekt des Typs `deque`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Doppel Schlange Links vom Operator kleiner als oder gleich der Doppel Schlange rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den deque-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "kleiner als oder gleich" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// deque_op_le.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "Deque c1 is less than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is greater than deque c2." << endl;
}
```

```Output
Deque c1 is less than or equal to deque c2.
```

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Überprüft, ob das deque-Objekt links vom Operator gleich dem deque-Objekt rechts vom Operator ist.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `deque`.

*Richting*\
Ein Objekt des Typs `deque`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Doppel Schlange Links vom Operator gleich der Doppel Schlange rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den deque-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Doppelschlangen sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// deque_op_eq.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;

   c1.push_back( 1 );
   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;
}
```

```Output
The deques are equal.
The deques are not equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Überprüft, ob das deque-Objekt links vom Operator größer als das deque-Objekt rechts vom Operator ist.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `deque`.

*Richting*\
Ein Objekt des Typs `deque`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Doppel Schlange Links vom Operator größer als die Doppel Schlange rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den deque-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "größer als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// deque_op_gt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "Deque c1 is greater than deque c2." << endl;
   else
      cout << "Deque c1 is not greater than deque c2." << endl;
}
```

```Output
Deque c1 is greater than deque c2.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Überprüft, ob das deque-Objekt links vom Operator größer gleich dem deque-Objekt rechts vom Operator ist.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `deque`.

*Richting*\
Ein Objekt des Typs `deque`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Doppel Schlange Links vom Operator größer als oder gleich der Doppel Schlange rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den deque-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "größer als oder gleich" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// deque_op_ge.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "Deque c1 is greater than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is less than deque c2." << endl;
}
```

```Output
Deque c1 is greater than or equal to deque c2.
```
