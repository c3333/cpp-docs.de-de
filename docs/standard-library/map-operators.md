---
title: '&lt;map&gt;-Operatoren'
ms.date: 03/27/2019
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: 2c632966c9ac1264747568facd459a33d1e13338
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233079"
---
# <a name="ltmapgt-operators"></a>&lt;map&gt;-Operatoren

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Testet, ob das Zuordnungsobjekt links vom Operator ungleich dem Zuordnungsobjekt rechts vom Operator ist.

```cpp
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `map`.

*Richting*\
Ein Objekt des Typs `map`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Zuordnungen nicht gleich sind. , **`false`** Wenn Maps gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den map-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Zuordnungen sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// map_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The maps m1 and m2 are not equal." << endl;
   else
      cout << "The maps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The maps m1 and m3 are not equal." << endl;
   else
      cout << "The maps m1 and m3 are equal." << endl;
}
```

```Output
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob das Zuordnungsobjekt links vom Operator kleiner als das Zuordnungsobjekt auf der rechten Seite ist.

```cpp
bool operator<(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `map`.

*Richting*\
Ein Objekt des Typs `map`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Zuordnung Links vom Operator strikt kleiner als die Zuordnung rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den map-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "kleiner als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// map_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The map m1 is less than the map m2." << endl;
   else
      cout << "The map m1 is not less than the map m2." << endl;

   if ( m1 < m3 )
      cout << "The map m1 is less than the map m3." << endl;
   else
      cout << "The map m1 is not less than the map m3." << endl;
}
```

```Output
The map m1 is less than the map m2.
The map m1 is not less than the map m3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Testet, ob das map-Objekt links vom Operator kleiner als das map-Objekt oder gleich diesem Objekt auf der rechten Seite ist.

```cpp
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `map`.

*Richting*\
Ein Objekt des Typs `map`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Zuordnung Links vom Operator kleiner als oder gleich der Zuordnung auf der rechten Seite des Operators ist. andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// map_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "The map m1 is less than or equal to the map m2." << endl;
   else
      cout << "The map m1 is greater than the map m2." << endl;

   if ( m1 <= m3 )
      cout << "The map m1 is less than or equal to the map m3." << endl;
   else
      cout << "The map m1 is greater than the map m3." << endl;

   if ( m1 <= m4 )
      cout << "The map m1 is less than or equal to the map m4." << endl;
   else
      cout << "The map m1 is greater than the map m4." << endl;
}
```

```Output
The map m1 is less than or equal to the map m2.
The map m1 is greater than the map m3.
The map m1 is less than or equal to the map m4.
```

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Testet, ob das map-Objekt links vom Operator gleich dem map-Objekt rechts vom Operator ist.

```cpp
bool operator==(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `map`.

*Richting*\
Ein Objekt des Typs `map`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Zuordnung Links vom Operator gleich der Zuordnung auf der rechten Seite des Operators ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den map-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Zuordnungen sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// map_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 == m2 )
      cout << "The maps m1 and m2 are equal." << endl;
   else
      cout << "The maps m1 and m2 are not equal." << endl;

   if ( m1 == m3 )
      cout << "The maps m1 and m3 are equal." << endl;
   else
      cout << "The maps m1 and m3 are not equal." << endl;
}
```

```Output
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Testet, ob das map-Objekt links vom Operator größer als das map-Objekt auf der rechten Seite ist.

```cpp
bool operator>(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `map`.

*Richting*\
Ein Objekt des Typs `map`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Map Links vom Operator größer als die Zuordnung rechts vom Operator ist; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den map-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "größer als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// map_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The map m1 is greater than the map m2." << endl;
   else
      cout << "The map m1 is not greater than the map m2." << endl;

   if ( m1 > m3 )
      cout << "The map m1 is greater than the map m3." << endl;
   else
      cout << "The map m1 is not greater than the map m3." << endl;
}
/* Output:
The map m1 is not greater than the map m2.
The map m1 is greater than the map m3.
*/
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Testet, ob das map-Objekt links vom Operator größer als das map-Objekt auf der rechten Seite ist oder diesem entspricht.

```cpp
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `map`.

*Richting*\
Ein Objekt des Typs `map`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Zuordnung Links vom Operator größer oder gleich der Zuordnung auf der rechten Seite der Liste ist. andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// map_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "Map m1 is greater than or equal to map m2." << endl;
   else
      cout << "The map m1 is less than the map m2." << endl;

   if ( m1 >= m3 )
      cout << "Map m1 is greater than or equal to map m3." << endl;
   else
      cout << "The map m1 is less than the map m3." << endl;

   if ( m1 >= m4 )
      cout << "Map m1 is greater than or equal to map m4." << endl;
   else
      cout << "The map m1 is less than the map m4." << endl;
}
```

```Output
The map m1 is less than the map m2.
Map m1 is greater than or equal to map m3.
Map m1 is greater than or equal to map m4.
```

## <a name="operator-multimap"></a><a name="op_neq_multimap"></a>Operator! = (Multimap)

Überprüft, ob das multimap-Objekt links vom Operator ungleich dem multimap-Objekt rechts vom Operator ist.

```cpp
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `multimap`.

*Richting*\
Ein Objekt des Typs `multimap`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die mehrfach Zuordnungen nicht gleich sind. , **`false`** wenn mehrfach Zuordnungen gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den multimap-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Mehrfachzuordnungen sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// multimap_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The multimaps m1 and m2 are not equal." << endl;
   else
      cout << "The multimaps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The multimaps m1 and m3 are not equal." << endl;
   else
      cout << "The multimaps m1 and m3 are equal." << endl;
}
```

```Output
The multimaps m1 and m2 are not equal.
The multimaps m1 and m3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt_multimap"></a>KOM&lt;

Überprüft, ob das multimap-Objekt links vom Operator ungleich dem multimap-Objekt rechts vom Operator ist.

```cpp
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `multimap`.

*Richting*\
Ein Objekt des Typs `multimap`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die mehrfach Zuordnung Links vom Operator strikt kleiner als die mehrfach Zuordnung rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den multimap-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "kleiner als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// multimap_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The multimap m1 is less than the multimap m2." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m2." << endl;

   if ( m1 < m3 )
      cout << "The multimap m1 is less than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m3." << endl;
}
```

```Output
The multimap m1 is less than the multimap m2.
The multimap m1 is not less than the multimap m3.
```

## <a name="operatorlt"></a><a name="op_lt_eq_multimap"></a>KOM&lt;=

Überprüft, ob das multimap-Objekt links vom Operator kleiner als das multimap-Objekt rechts vom Operator ist oder diesem entspricht.

```cpp
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `multimap`.

*Richting*\
Ein Objekt des Typs `multimap`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die mehrfach Zuordnung Links vom Operator kleiner als oder gleich der Multimap auf der rechten Seite des Operators ist. andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// multimap_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "m1 is less than or equal to m2" << endl;
   else
      cout << "m1 is greater than m2" << endl;

   if ( m1 <= m3 )
      cout << "m1 is less than or equal to m3" << endl;
   else
      cout << "m1 is greater than m3" << endl;

   if ( m1 <= m4 )
      cout << "m1 is less than or equal to m4" << endl;
   else
      cout << "m1 is greater than m4" << endl;
}
```

```Output
m1 is less than or equal to m2
m1 is greater than m3
m1 is less than or equal to m4
```

## <a name="operator"></a><a name="op_eq_eq_multimap"></a>Operator = =

Überprüft, ob das multimap-Objekt links vom Operator dem multimap-Objekt rechts vom Operator entspricht.

```cpp
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `multimap`.

*Richting*\
Ein Objekt des Typs `multimap`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die mehrfach Zuordnung Links vom Operator gleich der Multimap auf der rechten Seite des Operators ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den multimap-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei Mehrfachzuordnungen sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// multimap_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      m1.insert(Int_Pair(i, i));
      m2.insert(Int_Pair(i, i*i));
      m3.insert(Int_Pair(i, i));
   }

   if ( m1 == m2 )
      cout << "m1 and m2 are equal" << endl;
   else
      cout << "m1 and m2 are not equal" << endl;

   if ( m1 == m3 )
      cout << "m1 and m3 are equal" << endl;
   else
      cout << "m1 and m3 are not equal" << endl;
}
```

```Output
m1 and m2 are not equal
m1 and m3 are equal
```

## <a name="operatorgt"></a><a name="op_gt_multimap"></a>KOM&gt;

Überprüft, ob das multimap-Objekt links vom Operator größer als das multimap-Objekt rechts vom Operator ist.

```cpp
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `multimap`.

*Richting*\
Ein Objekt des Typs `multimap`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die mehrfach Zuordnung Links vom Operator größer als die mehrfach Zuordnung rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den multimap-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Die Beziehung "größer als" zwischen zwei Objekten basiert auf einem Vergleich des ersten Paares mit ungleichen Elementen.

### <a name="example"></a>Beispiel

```cpp
// multimap_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The multimap m1 is greater than the multimap m2." << endl;
   else
      cout << "Multimap m1 is not greater than multimap m2." << endl;

   if ( m1 > m3 )
      cout << "The multimap m1 is greater than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not greater than the multimap m3." << endl;
}
```

```Output
Multimap m1 is not greater than multimap m2.
The multimap m1 is greater than the multimap m3.
```

## <a name="operatorgt"></a><a name="op_gt_eq_multimap"></a>KOM&gt;=

Überprüft, ob das multimap-Objekt links vom Operator größer als das multimap-Objekt rechts vom Operator ist oder diesem entspricht.

```cpp
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `multimap`.

*Richting*\
Ein Objekt des Typs `multimap`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die mehrfach Zuordnung Links vom Operator größer oder gleich der Multimap auf der rechten Seite der Liste ist. andernfalls **`false`** .

### <a name="example"></a>Beispiel

```cpp
// multimap_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;
   else
      cout << "The multimap m1 is less than the multimap m2." << endl;

   if ( m1 >= m3 )
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;
   else
      cout << "The multimap m1 is less than the multimap m3." << endl;

   if ( m1 >= m4 )
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;
   else
      cout << "The multimap m1 is less than the multimap m4." << endl;
}
```

```Output
The multimap m1 is less than the multimap m2.
The multimap m1 is greater than or equal to the multimap m3.
The multimap m1 is greater than or equal to the multimap m4.
```
