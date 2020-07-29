---
title: Concurrency-Namespace-Operatoren (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: 03079f8899f3b13c8509e1affd10a82191b1817c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228478"
---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency-Namespace-Operatoren (AMP)

||||
|-|-|-|
|[Operator! =](#operator_neq)|[KOM](#operator_mod)|[KOM](#operator_star)|
|[Operator +](#operator_add)|[KOM](#operator-)|[KOM](#operator_div)|
|[Operator = =](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>Operator = =

Bestimmt, ob die angegebenen Argumente gleich sind.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang der Tupel-Argumente.

*_Lhs*<br/>
Eines der zu vergleichenden Tupel.

*_Rhs*<br/>
Eines der zu vergleichenden Tupel.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Tupel gleich sind. andernfalls **`false`** .

## <a name="operator"></a><a name="operator_neq"></a>Operator! =

Bestimmt, ob die angegebenen Argumente ungleich sind.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang der Tupel-Argumente.

*_Lhs*<br/>
Eines der zu vergleichenden Tupel.

*_Rhs*<br/>
Eines der zu vergleichenden Tupel.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Tupel nicht gleich sind. andernfalls **`false`** .

## <a name="operator"></a><a name="operator_add"></a>Operator +

Berechnet die komponentenbezogene Summe der angegebenen Argumente.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang der Tupel-Argumente.

*_Lhs*<br/>
Eines der hinzuzufügenden Argumente.

*_Rhs*<br/>
Eines der hinzuzufügenden Argumente.

### <a name="return-value"></a>Rückgabewert

Die komponentenbezogene Summe der angegebenen Argumente.

## <a name="operator-"></a><a name="operator-"></a>KOM

Berechnet die Differenz zwischen den angegebenen Argumenten pro Komponente.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang der Tupel-Argumente.

*_Lhs*<br/>
Das Argument, von dem subtrahiert werden soll.

*_Rhs*<br/>
Das zu subtrahierende Argument.

### <a name="return-value"></a>Rückgabewert

Die Differenz zwischen den angegebenen Argumenten pro Komponente.

## <a name="operator"></a><a name="operator_star"></a>KOM

Berechnet das komponentenbezogene Produkt der angegebenen Argumente.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang der Tupel-Argumente.

*_Lhs*<br/>
Eines der zu multiplizierenden Tupel.

*_Rhs*<br/>
Eines der zu multiplizierenden Tupel.

### <a name="return-value"></a>Rückgabewert

Das komponentenbezogene Produkt der angegebenen Argumente.

## <a name="operator"></a><a name="operator_div"></a>KOM

Berechnet den komponentenbezogenen Quotienten der angegebenen Argumente.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang der Tupel-Argumente.

*_Lhs*<br/>
Das zu dividierende Tupel.

*_Rhs*<br/>
Das Tupel für die Division.

### <a name="return-value"></a>Rückgabewert

Der komponentenbezogene Quotient der angegebenen Argumente.

## <a name="operator"></a><a name="operator_mod"></a>KOM

Berechnet den Modul des angegebenen ersten Arguments dividiert durch das zweite angegebene Argument.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang der Tupel-Argumente.

*_Lhs*<br/>
Das Tupel, auf dessen Basis das Modulo berechnet wird.

*_Rhs*<br/>
Das Tupel für die Modulo-Berechnung.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des ersten angegebenen Arguments ergibt das zweite angegebene Argument.

## <a name="see-also"></a>Siehe auch

[Parallelitäts Namespace](concurrency-namespace-cpp-amp.md)
