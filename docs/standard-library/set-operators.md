---
title: '&lt;Set&gt;-Operatoren'
ms.date: 03/27/2019
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: 4618030cf81f79a085e16052c8b9c547201e3577
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875765"
---
# <a name="ltsetgt-operators"></a>&lt;Set&gt;-Operatoren

## <a name="op_neq"></a>Operator! = (Set)

Testet, ob das Set-Objekt links vom Operator ungleich dem Set-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `set`.

*Rechte*\
Ein Objekt des Typs `set`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Sets ungleich sind, **FALSE**, wenn sie gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Set-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Sets sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// set_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The sets s1 and s2 are not equal." << endl;
   else
      cout << "The sets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The sets s1 and s3 are not equal." << endl;
   else
      cout << "The sets s1 and s3 are equal." << endl;
}
/* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*/
```

## <a name="op_lt"></a>Operator&lt; (Set)

Testet, ob das Set-Objekt links vom Operator kleiner als das Set-Objekt auf der rechten Seite ist.

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `set`.

*Rechte*\
Ein Objekt des Typs `set`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Set links vom Operator strikt kleiner als das Set rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Set-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "kleiner als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// set_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The set s1 is less than the set s2." << endl;
   else
      cout << "The set s1 is not less than the set s2." << endl;

   if ( s1 < s3 )
      cout << "The set s1 is less than the set s3." << endl;
   else
      cout << "The set s1 is not less than the set s3." << endl;
}
/* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*/
```

## <a name="op_lt_eq"></a>Operator&lt;= (Set)

Testet, ob das Set-Objekt links vom Operator kleiner als oder gleich dem Set-Objekt rechts vom Operator ist.

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `set`.

*Rechte*\
Ein Objekt des Typs `set`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Set links vom Operator kleiner oder gleich dem Set rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Set-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "kleiner als oder gleich" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// set_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "Set s1 is less than or equal to the set s2." << endl;
   else
      cout << "The set s1 is greater than the set s2." << endl;

   if ( s1 <= s3 )
      cout << "Set s1 is less than or equal to the set s3." << endl;
   else
      cout << "The set s1 is greater than the set s3." << endl;

   if ( s1 <= s4 )
      cout << "Set s1 is less than or equal to the set s4." << endl;
   else
      cout << "The set s1 is greater than the set s4." << endl;
}
```

```Output
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
```

## <a name="op_eq_eq"></a>Operator = = (Set)

Testet, ob das Set-Objekt links vom Operator gleich dem Set-Objekt rechts vom Operator ist.

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `set`.

*Rechte*\
Ein Objekt des Typs `set`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Set links vom Operator gleich dem Set rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Set-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Sets sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// set_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The sets s1 and s2 are equal." << endl;
   else
      cout << "The sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The sets s1 and s3 are equal." << endl;
   else
      cout << "The sets s1 and s3 are not equal." << endl;
}
```

```Output
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
```

## <a name="op_gt"></a>Operator&gt; (Set)

Testet, ob das Set-Objekt links vom Operator größer als das Set-Objekt auf der rechten Seite ist.

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `set`.

*Rechte*\
Ein Objekt des Typs `set`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Set links vom Operator größer als das Set rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Set-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "größer als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// set_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The set s1 is greater than the set s2." << endl;
   else
      cout << "The set s1 is not greater than the set s2." << endl;

   if ( s1 > s3 )
      cout << "The set s1 is greater than the set s3." << endl;
   else
      cout << "The set s1 is not greater than the set s3." << endl;
}
/* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*/
```

## <a name="op_gt_eq"></a>Operator&gt;= (Set)

Testet, ob das Set-Objekt links vom Operator größer als oder gleich dem Set-Objekt rechts vom Operator ist.

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `set`.

*Rechte*\
Ein Objekt des Typs `set`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Set links vom Operator größer als oder gleich dem Set rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Set-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "größer als oder gleich" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// set_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "Set s1 is greater than or equal to set s2." << endl;
   else
      cout << "The set s1 is less than the set s2." << endl;

   if ( s1 >= s3 )
      cout << "Set s1 is greater than or equal to set s3." << endl;
   else
      cout << "The set s1 is less than the set s3." << endl;

   if ( s1 >= s4 )
      cout << "Set s1 is greater than or equal to set s4." << endl;
   else
      cout << "The set s1 is less than the set s4." << endl;
}
```

```Output
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
```

## <a name="op_neq_multiset"></a>Operator! = (Multimenge)

Überprüft, ob das Multiset-Objekt links vom Operator ungleich dem Multiset-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `multiset`.

*Rechte*\
Ein Objekt des Typs `multiset`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Sets oder Multisets ungleich sind, **FALSE**, wenn die Sets oder Multisets gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Multiset-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Sets oder Multisets sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// multiset_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The multisets s1 and s2 are not equal." << endl;
   else
      cout << "The multisets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The multisets s1 and s3 are not equal." << endl;
   else
      cout << "The multisets s1 and s3 are equal." << endl;
}
```

```Output
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
```

## <a name="op_lt_multiset"></a>Operator&lt; (Multimenge)

Überprüft, ob das Set- oder Multiset-Objekt links vom Operator kleiner als das Set- oder Multiset-Objekt rechts vom Operator ist.

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `multiset`.

*Rechte*\
Ein Objekt des Typs `multiset`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Multiset links vom Operator strikt kleiner als das Multiset rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Multiset-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "kleiner als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// multiset_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s2." << endl;

   if ( s1 < s3 )
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s3." << endl;
}
```

```Output
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
```

## <a name="op_lt_eq_multiset"></a>Operator&lt;= (Multimenge)

Überprüft, ob das Multiset-Objekt links vom Operator kleiner oder gleich dem Multiset-Objekt rechts vom Operator ist.

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `multiset`.

*Rechte*\
Ein Objekt des Typs `multiset`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Multiset links vom Operator kleiner als oder gleich dem Multiset rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Multiset-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "kleiner als oder gleich" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// multiset_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;

   if ( s1 <= s3 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;

   if ( s1 <= s4 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s4." << endl;
}
```

```Output
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
```

## <a name="op_eq_eq_multiset"></a>Operator = = (Multimenge)

Überprüft, ob das Multiset-Objekt links vom Operator gleich dem Multiset-Objekt rechts vom Operator ist.

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `multiset`.

*Rechte*\
Ein Objekt des Typs `multiset`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Multiset links vom Operator gleich dem Multiset rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Multiset-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Sets oder Multisets sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// multiset_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The multisets s1 and s2 are equal." << endl;
   else
      cout << "The multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The multisets s1 and s3 are equal." << endl;
   else
      cout << "The multisets s1 and s3 are not equal." << endl;
}
```

```Output
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
```

## <a name="op_gt_multiset"></a>Operator&gt; (Multimenge)

Überprüft, ob das Multiset-Objekt links vom Operator größer als das Multiset-Objekt rechts vom Operator ist.

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `multiset`.

*Rechte*\
Ein Objekt des Typs `multiset`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Multiset links vom Operator größer als das Multiset rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Multiset-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "größer als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// multiset_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not greater "
           << "than the multiset s2." << endl;

   if ( s1 > s3 )
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not greater than "
           << "the multiset s3." << endl;
}
```

```Output
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
```

## <a name="op_gt_eq_multiset"></a>Operator&gt;= (Multimenge)

Überprüft, ob das Multiset-Objekt links vom Operator größer oder gleich dem Multiset-Objekt rechts vom Operator ist.

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `multiset`.

*Rechte*\
Ein Objekt des Typs `multiset`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das Multiset links vom Operator größer als oder gleich dem Multiset rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Multiset-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "größer als oder gleich" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// multiset_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;

   if ( s1 >= s3 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;

   if ( s1 >= s4 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s4." << endl;
}
```

```Output
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
```
