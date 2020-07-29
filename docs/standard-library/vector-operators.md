---
title: '&lt;vector&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: 6e3b78a7b7176be917da5a3e44e9bf54efc0b08c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224538"
---
# <a name="ltvectorgt-operators"></a>&lt;vector&gt;-Operatoren

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Testet, ob das Objekt links vom Operator ungleich dem Objekt rechts vom Operator ist.

```cpp
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `vector`.

*Richting*\
Ein Objekt des Typs `vector`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Vektoren nicht gleich sind. , **`false`** Wenn die Vektoren gleich sind.

### <a name="remarks"></a>Bemerkungen

Zwei Vektoren sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// vector_op_ne.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
     v2.push_back( 2 );

   if ( v1 != v2 )
      cout << "Vectors not equal." << endl;
   else
      cout << "Vectors equal." << endl;
}
```

```Output
Vectors not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob das Objekt links vom Operator kleiner als das Objekt auf der rechten Seite ist.

```cpp
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `vector`.

*Richting*\
Ein Objekt des Typs `vector`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Vektor Links vom Operator kleiner als der Vektor auf der rechten Seite des Operators ist. andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// vector_op_lt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 < v2 )
      cout << "Vector v1 is less than vector v2." << endl;
   else
      cout << "Vector v1 is not less than vector v2." << endl;
}
```

```Output
Vector v1 is less than vector v2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Testet, ob das Objekt links vom Operator kleiner oder gleich dem Objekt auf der rechten Seite ist.

```cpp
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `vector`.

*Richting*\
Ein Objekt des Typs `vector`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Vektor Links vom Operator kleiner als oder gleich dem Vektor rechts vom Operator ist. andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// vector_op_le.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 <= v2 )
      cout << "Vector v1 is less than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is greater than vector v2." << endl;
}
```

```Output
Vector v1 is less than or equal to vector v2.
```

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Testet, ob das Objekt links vom Operator gleich dem Objekt rechts vom Operator ist.

```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `vector`.

*Richting*\
Ein Objekt des Typs `vector`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Vektor Links vom Operator gleich dem Vektor rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Zwei Vektoren sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// vector_op_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v2.push_back( 1 );

   if ( v1 == v2 )
      cout << "Vectors equal." << endl;
   else
      cout << "Vectors not equal." << endl;
}
```

```Output
Vectors equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Testet, ob das Objekt links vom Operator größer als das Objekt auf der rechten Seite ist.

```cpp
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `vector`.

*Richting*\
Ein Objekt des Typs `vector`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Vektor Links vom Operator größer ist als der Vektor auf der rechten Seite des Operators. andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// vector_op_gt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

   v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 > v2 )
      cout << "Vector v1 is greater than vector v2." << endl;
   else
      cout << "Vector v1 is not greater than vector v2." << endl;
}
```

```Output
Vector v1 is greater than vector v2.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Testet, ob das Objekt links vom Operator größer oder gleich dem Objekt auf der rechten Seite ist.

```cpp
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `vector`.

*Richting*\
Ein Objekt des Typs `vector`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Vektor Links vom Operator größer als oder gleich dem Vektor rechts vom Vektor ist. andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// vector_op_ge.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

     v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 >= v2 )
      cout << "Vector v1 is greater than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is less than vector v2." << endl;
}
```

```Output
Vector v1 is greater than or equal to vector v2.
```
