---
title: '&lt;unordered_map&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: f062c4fd0332525a8b8940d2d93df41df56d2baa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373123"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;unordered_map&gt;-Operatoren

|||||
|-|-|-|-|
|[Operator!=](#op_neq)|[Betreiber== Einzelnachweise ==](#op_eq_eq)|[Operator!=](#op_neq_multimap)|[Betreiber== Einzelnachweise ==](#op_eq_eq_multimap)|

## <a name="operator"></a><a name="op_neq"></a>Operator!=

Testet, ob das [unordered_map](../standard-library/unordered-map-class.md)-Objekt links vom Operator ungleich dem unordered_map-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt des Typs `unordered_map`.

*Richting*\
Ein Objekt des Typs `unordered_map`.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn die unordered_maps nicht gleich sind; **falsch,** wenn sie gleich sind.

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
```

**Ausgabe:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="operator"></a><a name="op_eq_eq"></a>Betreiber== Einzelnachweise ==

Testet, ob das [unordered_map](../standard-library/unordered-map-class.md)-Objekt links vom Operator gleich dem unordered_map-Objekt rechts vom Operator ist.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt des Typs `unordered_map`.

*Richting*\
Ein Objekt des Typs `unordered_map`.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn die unordered_maps gleich sind; **falsch,** wenn sie nicht gleich sind.

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
```

**Ausgabe:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="operator"></a><a name="op_neq_multimap"></a>Operator!=

Überprüft, ob das [unordered_multimap](../standard-library/unordered-multimap-class.md)-Objekt links vom Operator ungleich dem unordered_multimap-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt des Typs `unordered_multimap`.

*Richting*\
Ein Objekt des Typs `unordered_multimap`.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn die unordered_multimaps nicht gleich sind; **falsch,** wenn sie gleich sind.

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
```

**Ausgabe:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="operator"></a><a name="op_eq_eq_multimap"></a>Betreiber== Einzelnachweise ==

Überprüft, ob das [unordered_multimap](../standard-library/unordered-multimap-class.md)-Objekt links vom Operator gleich dem unordered_multimap-Objekt rechts vom Operator ist.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt des Typs `unordered_multimap`.

*Richting*\
Ein Objekt des Typs `unordered_multimap`.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn die unordered_multimaps gleich sind; **falsch,** wenn sie nicht gleich sind.

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
```

**Ausgabe:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>Siehe auch

[<unordered_map>](../standard-library/unordered-map.md)
