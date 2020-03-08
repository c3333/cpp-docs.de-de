---
title: '&lt;stack&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- stack/std::operator!=
- stack/std::operator&gt;
- stack/std::operator&gt;=
- stack/std::operator&lt;
- stack/std::operator&lt;=
- stack/std::operator==
ms.assetid: 9c1fc282-2f61-4727-9e80-84ea5d4934a2
helpviewer_keywords:
- std::operator!= (stack)
- std::operator&gt; (stack)
- std::operator&gt;= (stack)
- std::operator&lt; (stack)
- std::operator&lt;= (stack)
- std::operator== (stack)
ms.openlocfilehash: 169698d30edd4a7995cb05e1909c1ffc38b0b6ef
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865898"
---
# <a name="ltstackgt-operators"></a>&lt;stack&gt;-Operatoren

## <a name="op_neq"></a>Operator! =

Testet, ob das Stack-Objekt links vom Operator ungleich dem Stack-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const stack <Type, Container>& left, const stack <Type, Container>& right,);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `stack`.

*Rechte*\
Ein Objekt des Typs `stack`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn Stacks oder Stacks ungleich sind, **FALSE**, wenn Stacks oder Stacks gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Stapel-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Stacks sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// stack_op_me.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> >  s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 != s2 )
      cout << "The stacks s1 and s2 are not equal." << endl;
   else
      cout << "The stacks s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The stacks s1 and s3 are not equal." << endl;
   else
      cout << "The stacks s1 and s3 are equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_lt"></a>-Operator&lt;

Testet, ob das Stapelobjekt links vom Operator kleiner als das Stapelobjekt rechts vom Operator ist.

```cpp
bool operator<(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `stack`.

*Rechte*\
Ein Objekt des Typs `stack`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn der Stack links vom Operator kleiner als und ungleich dem Stack rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Stack-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung „kleiner als“ zwischen zwei Stack-Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// stack_op_lt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 2 );
   s1.push( 4 );
   s1.push( 6 );
   s1.push( 8 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 2 );
   s3.push( 4 );
   s3.push( 6 );
   s3.push( 8 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;

   // to print out the stack s1 ( by unstacking the elements):
   stack <int>::size_type i_size_s1 = s1.size( );
   cout << "The stack s1 from the top down is: ( ";
   unsigned int i;
   for ( i = 1 ; i <= i_size_s1 ; i++ )
   {
      cout << s1.top( ) << " ";
      s1.pop( );
   }
   cout << ")." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
The stack s1 from the top down is: ( 8 6 4 2 ).
```

## <a name="op_lt_eq"></a>Operator&lt;=

Testet, ob das Stapelobjekt links vom Operator kleiner gleich dem Stapelobjekt rechts vom Operator ist.

```cpp
bool operator<=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `stack`.

*Rechte*\
Ein Objekt des Typs `stack`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn der Stack links vom Operator kleiner als oder gleich dem Stack rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Stack-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung „kleiner als oder gleich“ zwischen zwei Stack-Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// stack_op_le.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with default deque base container
   stack <int> s1, s2, s3;

   s1.push( 5 );
   s1.push( 10 );
   s2.push( 1 );
   s2.push( 2 );
   s3.push( 5 );
   s3.push( 10 );

   if ( s1 <= s2 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;

   if ( s1 <= s3 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is greater than the stack s2.
The stack s1 is less than or equal to the stack s3.
```

## <a name="op_eq_eq"></a>Operator = =

Testet, ob das Stack-Objekt links vom Operator gleich dem Stack-Objekt rechts vom Operator ist.

```cpp
bool operator==(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `stack`.

*Rechte*\
Ein Objekt des Typs `stack`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn Stacks oder Stacks gleich sind, **FALSE**, wenn Stacks oder Stacks ungleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Stack-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Stacks sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// stack_op_eq.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> > s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 == s2 )
      cout << "The stacks s1 and s2 are equal." << endl;
   else
      cout << "The stacks s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The stacks s1 and s3 are equal." << endl;
   else
      cout << "The stacks s1 and s3 are not equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_gt"></a>-Operator&gt;

Testet, ob das Stapelobjekt links vom Operator größer als das Stapelobjekt rechts vom Operator ist.

```cpp
bool operator>(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `stack`.

*Rechte*\
Ein Objekt des Typs `stack`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn der Stack links vom Operator größer als oder gleich dem Stack rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Stack-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung „größer als“ zwischen zwei Stack-Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// stack_op_gt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s1.push( 3 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 > s2 )
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s2." << endl;

   if ( s1> s3 )
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is not greater than the stack s2.
The stack s1 is greater than the stack s3.
```

## <a name="op_gt_eq"></a>Operator&gt;=

Testet, ob das Stapelobjekt links vom Operator größer gleich dem Stapelobjekt rechts vom Operator ist.

```cpp
bool operator>=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `stack`.

*Rechte*\
Ein Objekt des Typs `stack`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn der Stack links vom Operator strikt kleiner als der Stack rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den Stack-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung „größer als oder gleich“ zwischen zwei Stack-Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// stack_op_ge.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
```
