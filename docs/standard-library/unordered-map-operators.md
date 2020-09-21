---
title: '&lt;unordered_map&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: 2c09fa0070151f7cdd502e8f5583645110e91c5b
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741956"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;unordered_map&gt;-Operatoren

[unordered_map:: Operator! =](#op_neq)\
[unordered_map:: Operator = =](#op_eq_eq)\
[unordered_multimap:: Operator! =](#op_neq_multimap)\
[unordered_multimap:: Operator = =](#op_eq_eq_multimap)

## <a name="operator"></a><a name="op_neq"></a> Operator! =

Testet, ob das [unordered_map](../standard-library/unordered-map-class.md)-Objekt links vom Operator ungleich dem unordered_map-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `unordered_map`.

*Richting*\
Ein Objekt vom Typ `unordered_map`.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die unordered_maps nicht gleich sind. , **`false`** Wenn Sie gleich sind.

### <a name="remarks"></a>Bemerkungen

Die beliebige Reihenfolge, in der unordered_map-Objekte ihre Elemente speichern, hat keine Auswirkungen auf den Vergleich der Objekte. Zwei unordered_map-Objekte sind gleich, wenn sie dieselbe Anzahl von Elementen aufweisen und die Elemente in einem Container eine Permutation der Elemente im anderen Container sind. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// unordered_map_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}

/* Output:
um1 != um2: true
um1 != um3: false
um2 != um3: true
*/
```

## <a name="operator"></a><a name="op_eq_eq"></a> Operator = =

Testet, ob das [unordered_map](../standard-library/unordered-map-class.md)-Objekt links vom Operator gleich dem unordered_map-Objekt rechts vom Operator ist.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `unordered_map`.

*Richting*\
Ein Objekt vom Typ `unordered_map`.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die unordered_maps gleich sind. , **`false`** Wenn Sie nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Die beliebige Reihenfolge, in der unordered_map-Objekte ihre Elemente speichern, hat keine Auswirkungen auf den Vergleich der Objekte. Zwei unordered_map-Objekte sind gleich, wenn sie dieselbe Anzahl von Elementen aufweisen und die Elemente in einem Container eine Permutation der Elemente im anderen Container sind. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// unordered_map_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}

/* Output:
um1 == um2: false
um1 == um3: true
um2 == um3: false
*/
```

## <a name="operator-multimap"></a><a name="op_neq_multimap"></a> Operator! = (Multimap)

Überprüft, ob das [unordered_multimap](../standard-library/unordered-multimap-class.md)-Objekt links vom Operator ungleich dem unordered_multimap-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `unordered_multimap`.

*Richting*\
Ein Objekt vom Typ `unordered_multimap`.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die unordered_multimaps nicht gleich sind. , **`false`** Wenn Sie gleich sind.

### <a name="remarks"></a>Bemerkungen

Die beliebige Reihenfolge, in der unordered_multimap-Objekte ihre Elemente speichern, hat keine Auswirkungen auf den Vergleich der Objekte. Zwei unordered_multimap-Objekte sind gleich, wenn sie dieselbe Anzahl von Elementen aufweisen und die Elemente in einem Container eine Permutation der Elemente im anderen Container sind. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// unordered_multimap_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}

/* Output:
um1 != um2: true
um1 != um3: false
um2 != um3: true
*/
```

## <a name="operator-multimap"></a><a name="op_eq_eq_multimap"></a> Operator = = (Multimap)

Überprüft, ob das [unordered_multimap](../standard-library/unordered-multimap-class.md)-Objekt links vom Operator gleich dem unordered_multimap-Objekt rechts vom Operator ist.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `unordered_multimap`.

*Richting*\
Ein Objekt vom Typ `unordered_multimap`.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die unordered_multimaps gleich sind. , **`false`** Wenn Sie nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Die beliebige Reihenfolge, in der unordered_multimap-Objekte ihre Elemente speichern, hat keine Auswirkungen auf den Vergleich der Objekte. Zwei unordered_multimap-Objekte sind gleich, wenn sie dieselbe Anzahl von Elementen aufweisen und die Elemente in einem Container eine Permutation der Elemente im anderen Container sind. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// unordered_multimap_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}

/* Output:
um1 == um2: false
um1 == um3: true
um2 == um3: false
*/
```

## <a name="see-also"></a>Weitere Informationen

[<unordered_map>](../standard-library/unordered-map.md)
