---
title: '&lt;tuple&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- tuple/std::get
- tuple/std::make_tuple
- tuple/std::tie
ms.assetid: bc6be38f-5258-4c14-b81b-63caa335fd44
helpviewer_keywords:
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
ms.openlocfilehash: 46c386ecffb8fbbf7c07d40b334afd91d261ebcf
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274514"
---
# <a name="lttuplegt-functions"></a>&lt;tuple&gt;-Funktionen

## <a name="apply"></a><a name="apply"></a> Apply

```cpp
template <class F, class Tuple> constexpr decltype(auto) apply(F&& f, Tuple&& t);
```

### <a name="remarks"></a>Bemerkungen

Ruft Funktion *F* mit einem Tupel *t*auf.

## <a name="forward_as_tuple"></a><a name="forward"></a> forward_as_tuple

```cpp
template <class... TTypes>
    constexpr tuple<TTypes&&...> forward_as_tuple(TTypes&&...) noexcept;
```

### <a name="return-value"></a>Rückgabewert

Gibt `tuple<TTypes&&...>(std::forward<TTypes>(t)...)`zurück.

### <a name="remarks"></a>Bemerkungen

Erstellt ein Tupel von Verweisen auf die Argumente in *t* , die für die Weiterleitung als Argumente an eine Funktion geeignet sind.

## <a name="get"></a><a name="get"></a> Erhalten

Ruft ein Element aus einem `tuple` -Objekt nach dem Index oder (in C++14) nach dem Typ ab.

```cpp
// by index:
// get reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>& get(tuple<Types...>& Tuple) noexcept;

// get const reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr const tuple_element_t<Index, tuple<Types...>>& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>&& get(tuple<Types...>&& Tuple) noexcept;

// (C++14) by type:
// get reference to T element of tuple
template <class T, class... Types>
   constexpr T& get(tuple<Types...>& Tuple) noexcept;

// get const reference to T element of tuple
template <class T, class... Types>
   constexpr const T& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to T element of tuple
template <class T, class... Types>
   constexpr T&& get(tuple<Types...>&& Tuple) noexcept;
```

### <a name="parameters"></a>Parameter

*Index*\
Der Index des abzurufenden Elements.

*Solche*\
Die Sequenz der im Tupel deklarierten Typen in der Deklarationsreihenfolge.

*Bund*\
Der Typ des abzurufenden Elements.

*Tupel*\
Eine `std::tuple` , die eine beliebige Anzahl von Elementen enthält.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktionen geben einen Verweis auf den Wert am Index *Index*oder vom Typ *T* im- `tuple` Objekt zurück.

Das Aufrufen von `get<T>(Tuple)` führt zu einem Compilerfehler, wenn das Tupel mehr oder weniger als ein Element vom Typ T enthält.

### <a name="example"></a>Beispiel

```cpp
#include <tuple>
#include <iostream>
#include <string>

using namespace std;

int main() {
    tuple<int, double, string> tup(0, 1.42, "Call me Tuple");

    // get elements by index
    cout << " " << get<0>(tup);
    cout << " " << get<1>(tup);
    cout << " " << get<2>(tup) << endl;

    // get elements by type
    cout << " " << get<int>(tup);
    cout << " " << get<double>(tup);
    cout << " " << get<string>(tup) << endl;
}
```

```Output
0 1.42 Call me Tuple
0 1.42 Call me Tuple
```

## <a name="make_from_tuple"></a><a name="make_from_tuple"></a> make_from_tuple

```cpp
template <class T, class Tuple> constexpr T make_from_tuple(Tuple&& t);
```

### <a name="remarks"></a>Bemerkungen

Wie in `return make_from_tuple_impl<T>(forward<Tuple>(t), make_index_sequence<tuple_size_v<decay_t<Tuple>>>{})`.

## <a name="make_tuple"></a><a name="make_tuple"></a> make_tuple

Erstellt eine `tuple` aus Elementwerten.

```cpp
template <class T1, class T2, ..., class TN>
   tuple<V1, V2, ..., VN> make_tuple(const T1& t1, const T2& t2, ..., const TN& tN);
```

### <a name="parameters"></a>Parameter

*TN*\
Der Typ des Parameters der Nth-Funktion.

*tN*\
Der Wert des Parameters der Nth-Funktion.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion gibt zurück `tuple<V1, V2, ..., VN>(t1, t2, ..., tN)` , wobei jeder Typ ist, `Vi` `X&` Wenn der entsprechende Typ `Ti` ist, `cv` `reference_wrapper<X>` und andernfalls `Ti` .

Ein Vorteil von `make_tuple` ist, dass die Typen von Objekten, die gespeichert werden, automatisch vom Compiler bestimmt werden und nicht explizit angegeben werden müssen. Verwenden Sie keine expliziten Vorlagenargumente wie `make_tuple<int, int>(1, 2)`, wenn Sie `make_tuple` verwenden, da dies unnötig detailliert ist und zu komplexen rvalue-Verweisproblemen führt, die möglicherweise Kompilierungsfehler verursachen.

### <a name="example"></a>Beispiel

```cpp
// std__tuple__make_tuple.cpp
// compile by using: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    c0 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
```

## <a name="swap"></a><a name="swap"></a> Wechsel

```cpp
template <class... Types>
    void swap(tuple<Types...>& x, tuple<Types...>& y) noexcept(see below );
```

## <a name="tie"></a><a name="tie"></a> Tie

Erstellt eine `tuple` aus Elementverweisen.

```cpp
template <class T1, class T2, ..., class TN>
tuple<T1&, T2&, ..., TN&> tie(T1& t1, T2& t2, ..., TN& tN);
```

### <a name="parameters"></a>Parameter

*TN*\
Der Basistyp des N-ten Tupelelements.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `tuple<T1&, T2&, ..., TN&>(t1, t2, ..., tN)` zurück.

### <a name="example"></a>Beispiel

```cpp
// std__tuple__tie.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    int v4 = 4;
    double v5 = 5;
    int v6 = 6;
    double v7 = 7;
    std::tie(v4, v5, v6, v7) = c0;

// display contents " 0 1 2 3"
    std::cout << " " << v4;
    std::cout << " " << v5;
    std::cout << " " << v6;
    std::cout << " " << v7;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="tuple_cat"></a><a name="tuple_cat"></a> tuple_cat

```cpp
template <class... Tuples> constexpr tuple<CTypes...> tuple_cat(Tuples&&...);
```

### <a name="return-value"></a>Rückgabewert

Ein tupelobjekt, das durch Initialisieren der einzelnen Type-Elemente erstellt wird.

## <a name="tuple_element_t"></a><a name="tuple_element_t"></a> tuple_element_t

```cpp
template <size_t I, class T>
    using tuple_element_t = typename tuple_element<I, T>::type;
```

## <a name="tuple_size_v"></a><a name="tuple_size_v"></a> tuple_size_v

```cpp
template <class T>
    inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```
