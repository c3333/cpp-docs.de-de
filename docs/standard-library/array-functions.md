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
ms.openlocfilehash: 61b5404d0f22cd902e35f6bee680df3c719804f2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875888"
---
# <a name="ltarraygt-functions"></a>&lt;array&gt;-Funktionen

Das \<Array >-Header enthält zwei nicht-Member-Funktionen, `get` und `swap`, die für **Array** Objekte verwendet werden.

|||
|-|-|
|[get](#get)|[swap](#swap)|

## <a name="get"></a> get

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

*T*\
Der Typ eines Elements.

*N*\
Die Anzahl der Elemente im Array.

*arr* -\
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

## <a name="swap"></a> swap

Eine nicht-Member-Vorlagen Spezialisierung von `std::swap`, die zwei **Array** Objekte tauscht.

```cpp
template <class Ty, std::size_t N>
void swap(array<Ty, N>& left, array<Ty, N>& right);
```

### <a name="parameters"></a>Parameter

*Ty* -\
Der Typ eines Elements.

*N*\
Die Größe des Arrays.

*Linker*\
Das erste auszutauschende Array.

*Rechte*\
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
