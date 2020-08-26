---
title: '&lt;array&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- array/std::array::get
- array/std::get
- array/std::swap
ms.assetid: e0700a33-a833-4655-8735-16e71175efc8
helpviewer_keywords:
- std::array [C++], get
- std::get [C++]
- std::swap [C++]
ms.openlocfilehash: 3389ba769d6b61a363e8cbfcf5f6a4e9ec679469
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844703"
---
# <a name="ltarraygt-functions"></a>&lt;array&gt;-Funktionen

Der \<array> -Header enthält zwei nicht-Member-Funktionen, `get` und `swap` , die auf **Array** -Objekten angewendet werden.

[Erhalten](#get)\
[swap](#swap)

## <a name="get"></a><a name="get"></a> Erhalten

Gibt einen Verweis auf das angegebene Element des Arrays zurück.

```cpp
template <int Index, class T, size_t N>
constexpr T& get(array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr const T& get(const array<T, N>& arr) noexcept;

template <int Index, class T, size_t N>
constexpr T&& get(array<T, N>&& arr) noexcept;
```

### <a name="parameters"></a>Parameter

*Index*\
Der Offset des Elements.

*Bund*\
Der Typ eines Elements.

*Nr*\
Die Anzahl der Elemente im Array.

*r*\
Das Array, aus dem die Auswahl erfolgt.

### <a name="example"></a>Beispiel

```cpp
#include <array>
#include <iostream>

using namespace std;

typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& e : c0)
    {
        cout << " " << e;
    }
    cout << endl;

    // display odd elements " 1 3"
    cout << " " << get<1>(c0);
    cout << " " << get<3>(c0) << endl;
}
```

```Output
0 1 2 3
1 3
```

## <a name="swap"></a><a name="swap"></a> Wechsel

Eine nicht-Member-Vorlagen Spezialisierung von `std::swap` , die zwei **Array** Objekte tauscht.

```cpp
template <class Ty, std::size_t N>
void swap(array<Ty, N>& left, array<Ty, N>& right);
```

### <a name="parameters"></a>Parameter

*Genossenschaft*\
Der Typ eines Elements.

*Nr*\
Die Größe des Arrays.

*linken*\
Das erste auszutauschende Array.

*Richting*\
Das zweite auszutauschende Array.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion führt `left.swap(right)` aus.

### <a name="example"></a>Beispiel

```cpp
// std__array__swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="see-also"></a>Weitere Informationen

[\<array>](../standard-library/array.md)
