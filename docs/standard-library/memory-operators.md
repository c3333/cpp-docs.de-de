---
title: '&lt;memory&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
ms.openlocfilehash: 661f1bb4c0f5734d88dd23f73c69b362f59a76c2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884071"
---
# <a name="ltmemorygt-operators"></a>&lt;memory&gt;-Operatoren

## <a name="op_neq"></a>Operator! =

Prüft auf Ungleichheit zwischen Objekten.

```cpp
template <class Type, class Other>
bool operator!=(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>
bool operator!=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator!=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Eines der Objekte, die auf Ungleichheit geprüft werden sollen.

*Rechte*\
Eines der Objekte, die auf Ungleichheit geprüft werden sollen.

*Ty1*\
Der vom linken gemeinsamen Zeiger gesteuerte Typ.

*Ty2*\
Der vom rechten gemeinsamen Zeiger gesteuerte Typ.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Objekte nicht gleich sind; **FALSE**, wenn die Objekte gleich sind.

### <a name="remarks"></a>Bemerkungen

Der erste Vorlagenoperator gibt "false" zurück. (Alle standardmäßigen allocator-Objekte sind gleich.)

Der zweite und der dritte Vorlagenoperator geben `!(left == right)` zurück.

### <a name="example"></a>Beispiel

```cpp
// memory_op_me.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<double> Alloc;
   vector <char>:: allocator_type v1Alloc;

   if ( Alloc != v1Alloc )
      cout << "The allocator objects Alloc & v1Alloc not are equal."
           << endl;
   else
      cout << "The allocator objects Alloc & v1Alloc are equal."
           << endl;
}
```

```Output
The allocator objects Alloc & v1Alloc are equal.
```

### <a name="example"></a>Beispiel

```cpp
// std__memory__operator_ne.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 != sp0 == " << std::boolalpha
        << (sp0 != sp0) << std::endl;
    std::cout << "sp0 != sp1 == " << std::boolalpha
        << (sp0 != sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 != sp0 == false
sp0 != sp1 == true
```

## <a name="op_eq_eq"></a>Operator = =

Prüft auf Gleichheit zwischen Objekten.

```cpp
template <class Type, class Other>
bool operator==(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>
bool operator==(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>
bool operator==(
    const shared_ptr<Ty1>& left;,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Eines der Objekte, die auf Gleichheit geprüft werden sollen.

*Rechte*\
Eines der Objekte, die auf Gleichheit geprüft werden sollen.

*Ty1*\
Der vom linken gemeinsamen Zeiger gesteuerte Typ.

*Ty2*\
Der vom rechten gemeinsamen Zeiger gesteuerte Typ.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Objekte gleich sind, **false** , wenn die Objekte nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Der erste Vorlagenoperator gibt "true" zurück. (Alle standardmäßigen allocator-Objekte sind gleich.)

Der zweite und der dritte Vorlagenoperator geben `left.get() ==  right.get()` zurück.

### <a name="example"></a>Beispiel

```cpp
// memory_op_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<char> Alloc;
   vector <int>:: allocator_type v1Alloc;

   allocator<char> cAlloc(Alloc);
   allocator<int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="example"></a>Beispiel

```cpp
// std__memory__operator_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 == sp0 == " << std::boolalpha
        << (sp0 == sp0) << std::endl;
    std::cout << "sp0 == sp1 == " << std::boolalpha
        << (sp0 == sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 == sp0 == true
sp0 == sp1 == false
```

## <a name="op_gt_eq"></a>Operator&gt;=

Testet, ob ein Objekt größer gleich einem zweiten Objekt ist.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator>=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>
bool operator>=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Eines der zu vergleichenden Objekte.

*Rechte*\
Eines der zu vergleichenden Objekte.

*Ty1*\
Der vom linken gemeinsamen Zeiger gesteuerte Typ.

*Ty2*\
Der vom rechten gemeinsamen Zeiger gesteuerte Typ.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Operatoren geben `left.get() >= right.get()`zurück.

## <a name="op_lt"></a>-Operator&lt;

Testet, ob ein Objekt kleiner als ein zweites Objekt ist.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Eines der zu vergleichenden Objekte.

*Rechte*\
Eines der zu vergleichenden Objekte.

*Ty1*\
Der vom linken Zeiger gesteuerte Typ.

*Ty2*\
Der vom rechten Zeiger gesteuerte Typ.

## <a name="op_lt_eq"></a>Operator&lt;=

Testet, ob ein Objekt kleiner gleich einem zweiten Objekt ist.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Eines der zu vergleichenden Objekte.

*Rechte*\
Eines der zu vergleichenden Objekte.

*Ty1*\
Der vom linken gemeinsamen Zeiger gesteuerte Typ.

*Ty2*\
Der vom rechten gemeinsamen Zeiger gesteuerte Typ.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Operatoren geben zurück `left.get() <= right.get()`

## <a name="op_gt"></a>-Operator&gt;

Testet, ob ein Objekt größer als ein zweites Objekt ist.

```cpp
template <class Ty1, class Del1, class Ty2, class Del2>
bool operator>(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>
bool operator>(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Eines der zu vergleichenden Objekte.

*Rechte*\
Eines der zu vergleichenden Objekte.

*Ty1*\
Der vom linken gemeinsamen Zeiger gesteuerte Typ.

*Ty2*\
Der vom rechten gemeinsamen Zeiger gesteuerte Typ.

## <a name="op_lt_lt"></a>Operator&lt;&lt;

Schreibt den freigegebenen Zeiger auf den Stream.

```cpp
template <class Elem, class Tr, class Ty>
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,
    shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parameter

*Elem* -\
Der Typ des Streamelements.

*TR* -\
Der Typ des Streamelements.

*Ty* -\
Der vom freigegebenen Zeiger gesteuerte Typ.

*out*\
Der Ausgabestream.

*SP* -\
Der freigegebene Zeiger.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion gibt `out << sp.get()` zurück.

### <a name="example"></a>Beispiel

```cpp
// std__memory__operator_sl.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;

    return (0);
    }
```

```Output
sp0 == 3f3040 (varies)
```
