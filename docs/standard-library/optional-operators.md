---
title: '&lt;optionale &gt; Operatoren'
ms.date: 11/04/2016
f1_keywords:
- optional/std::operator!=
- optional/std::operator==
- optional/std::operatoroperator&gt;
- optional/std::operatoroperator&gt=;
- optional/std::operatoroperator&lt;
- optional/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (optional)
- std::operator== (optional)
- std::operatoroperator&gt; (optional)
- std::operatoroperator&gt=; (optional)
- std::operatoroperator&lt; (optional)
- std::operatoroperator&lt;= (optional)
ms.openlocfilehash: c7eca76f71f12e7f7fe0e60c0a4cfe456d54c374
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224681"
---
# <a name="ltoptionalgt-operators"></a>&lt;optionale &gt; Operatoren

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Testet, ob das `optional`-Objekt links vom Operator gleich dem `optional`-Objekt rechts vom Operator ist.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

*Richting*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Testet, ob das `optional`-Objekt links vom Operator ungleich dem `optional`-Objekt rechts vom Operator ist.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

*Richting*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(left == right)` zurück.

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob das `optional`-Objekt links vom Operator kleiner als das `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

*Richting*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Liste links vom Operator kleiner als, aber nicht gleich der Liste rechts vom Operator ist. andernfalls **`false`** .

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Testet, ob das `optional`-Objekt links vom Operator kleiner oder gleich dem `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

*Richting*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Liste links vom Operator kleiner als oder gleich der Liste rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(right < left)` zurück.

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Testet, ob das `optional`-Objekt links vom Operator größer als das `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

*Richting*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Liste links vom Operator größer als die Liste rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `right < left` zurück.

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Testet, ob das `optional`-Objekt links vom Operator größer oder gleich dem `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

*Richting*\
Ein Objekt vom Typ `optional` , `nullopt_t` oder `T` .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `optional` Links vom Operator größer als oder gleich dem `optional` auf der rechten Seite des Operators ist; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(left < right)` zurück.
