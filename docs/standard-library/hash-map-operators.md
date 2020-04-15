---
title: '&lt;hash_map&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: ed143349f3afc7a27ad565c1cc929c6ecb5f6ad8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375446"
---
# <a name="lthash_mapgt-operators"></a>&lt;hash_map&gt;-Operatoren

|||
|-|-|
|[Operator!=](#op_neq)|[Operator!= (Multimap)](#op_neq_mm)|
|[Betreiber== Einzelnachweise ==](#op_eq_eq)|[Operator== (Multimap)](#op_eq_eq_mm)|

## <a name="operator"></a><a name="op_neq"></a>Operator!=

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_map-Klasse](unordered-map-class.md).

Testet, ob das hash_map-Objekt links vom Operator ungleich dem hash_map-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt des Typs `hash_map`.

*Richting*\
Ein Objekt des Typs `hash_map`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die hash_maps ungleich sind; **FALSE**, wenn hash_maps gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den hash_map-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei hash_maps sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen, und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

Mitglieder der [<hash_map>](hash-map.md) und<hash_set hash_set [>](hash-set.md) Headerdateien im [stdext Namespace](stdext-namespace.md).

### <a name="example"></a>Beispiel

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>Betreiber== Einzelnachweise ==

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_map-Klasse](unordered-map-class.md).

Testet, ob das hash_map-Objekt links vom Operator gleich dem hash_map-Objekt rechts vom Operator ist.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt des Typs `hash_map`.

*Richting*\
Ein Objekt des Typs `hash_map`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die hash_map links vom Operator gleich der hash_map rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den hash_map-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei hash_maps sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen, und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator-hash_multimap"></a><a name="op_neq_mm"></a>Operator!= (hash_multimap)

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](unordered-multimap-class.md).

Überprüft, ob das hash_multimap-Objekt links vom Operator ungleich dem hash_multimap-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt des Typs `hash_multimap`.

*Richting*\
Ein Objekt des Typs `hash_multimap`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die hash_multimaps ungleich sind; **FALSE**, wenn hash_multimaps gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den hash_multimap-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei hash_multimaps sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="operator--hash_multimap"></a><a name="op_eq_eq_mm"></a>Operator== (hash_multimap)

> [!NOTE]
> Diese API ist veraltet. Die Alternative ist die [unordered_multimap-Klasse](unordered-multimap-class.md).

Überprüft, ob das hash_multimap-Objekt links vom Operator gleich dem hash_multimap-Objekt rechts vom Operator ist.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt des Typs `hash_multimap`.

*Richting*\
Ein Objekt des Typs `hash_multimap`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die hash_multimap links vom Operator gleich der hash_multimap rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Der Vergleich zwischen den hash_multimap-Objekten basiert auf einem paarweisen Vergleich der entsprechenden Elemente. Zwei hash_multimaps sind gleich, wenn sie über die gleiche Anzahl von Elementen verfügen und die entsprechenden Elemente dieselben Werte aufweisen. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>Siehe auch

[<hash_map>](hash-map.md)
