---
title: '&lt;unordered_set&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 59a7154ed46ac788516bc9f42c3385ec8f07dcf1
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427686"
---
# <a name="ltunordered_setgt-operators"></a>&lt;unordered_set&gt;-Operatoren

## <a name="op_neq"></a>Operator! =

Testet, ob das [unordered_set](../standard-library/unordered-set-class.md)-Objekt links vom Operator ungleich dem unordered_set-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `unordered_set`.

*Rechte*\
Ein Objekt des Typs `unordered_set`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die unordered_sets nicht gleich sind. **false** , wenn Sie gleich sind.

### <a name="remarks"></a>Hinweise

Die beliebige Reihenfolge, in der unordered_set-Objekte ihre Elemente speichern, hat keine Auswirkungen auf den Vergleich der Objekte. Zwei unordered_set-Objekte sind gleich, wenn sie dieselbe Anzahl von Elementen aufweisen und die Elemente in einem Container eine Permutation der Elemente im anderen Container sind. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// unordered_set_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

**Ausgabe:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq"></a>Operator = =

Testet, ob das [unordered_set](../standard-library/unordered-set-class.md)-Objekt links vom Operator gleich dem unordered_set-Objekt rechts vom Operator ist.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `unordered_set`.

*Rechte*\
Ein Objekt des Typs `unordered_set`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die unordered_sets gleich sind. **false** , wenn Sie nicht gleich sind.

### <a name="remarks"></a>Hinweise

Die beliebige Reihenfolge, in der unordered_set-Objekte ihre Elemente speichern, hat keine Auswirkungen auf den Vergleich der Objekte. Zwei unordered_set-Objekte sind gleich, wenn sie dieselbe Anzahl von Elementen aufweisen und die Elemente in einem Container eine Permutation der Elemente im anderen Container sind. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// unordered_set_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```

## <a name="op_neq_unordered_multiset"></a>Operator! =

Überprüft, ob das [unordered_multiset](../standard-library/unordered-multiset-class.md)-Objekt links vom Operator ungleich dem unordered_multiset-Objekt rechts vom Operator ist.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `unordered_multiset`.

*Rechte*\
Ein Objekt des Typs `unordered_multiset`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die unordered_multisets nicht gleich sind. **false** , wenn Sie gleich sind.

### <a name="remarks"></a>Hinweise

Die beliebige Reihenfolge, in der unordered_multiset-Objekte ihre Elemente speichern, hat keine Auswirkungen auf den Vergleich der Objekte. Zwei unordered_multiset-Objekte sind gleich, wenn sie dieselbe Anzahl von Elementen aufweisen und die Elemente in einem Container eine Permutation der Elemente im anderen Container sind. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// unordered_multiset_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

```Output
c1 != c2: true
c1 != c3: false
c2 != c3: true
```

## <a name="op_eq_eq_unordered_multiset"></a>Operator = =

Überprüft, ob das [unordered_multiset](../standard-library/unordered-multiset-class.md)-Objekt links vom Operator gleich dem unordered_multiset-Objekt rechts vom Operator ist.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `unordered_multiset`.

*Rechte*\
Ein Objekt des Typs `unordered_multiset`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die unordered_multisets gleich sind. **false** , wenn Sie nicht gleich sind.

### <a name="remarks"></a>Hinweise

Die beliebige Reihenfolge, in der unordered_multiset-Objekte ihre Elemente speichern, hat keine Auswirkungen auf den Vergleich der Objekte. Zwei unordered_multiset-Objekte sind gleich, wenn sie dieselbe Anzahl von Elementen aufweisen und die Elemente in einem Container eine Permutation der Elemente im anderen Container sind. Andernfalls sind sie ungleich.

### <a name="example"></a>Beispiel

```cpp
// unordered_multiset_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```
