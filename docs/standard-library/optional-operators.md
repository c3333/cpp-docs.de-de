---
title: '&lt;optionale&gt; Operatoren'
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
ms.openlocfilehash: 9bdef0669f90da7865f7652ff4528e51e584e1a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373637"
---
# <a name="ltoptionalgt-operators"></a>&lt;optionale&gt; Operatoren

## <a name="operator"></a><a name="op_eq_eq"></a>Betreiber== Einzelnachweise ==

Testet, ob das `optional`-Objekt links vom Operator gleich dem `optional`-Objekt rechts vom Operator ist.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

*Richting*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

## <a name="operator"></a><a name="op_neq"></a>Operator!=

Testet, ob das `optional`-Objekt links vom Operator ungleich dem `optional`-Objekt rechts vom Operator ist.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

*Richting*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(left == right)` zurück.

## <a name="operatorlt"></a><a name="op_lt"></a>Operator&lt;

Testet, ob das `optional`-Objekt links vom Operator kleiner als das `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

*Richting*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator kleiner als, aber ungleich der Liste rechts vom Operator ist; andernfalls **FALSE**.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operator&lt;=

Testet, ob das `optional`-Objekt links vom Operator kleiner oder gleich dem `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

*Richting*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator kleiner als oder gleich der Liste rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(right < left)` zurück.

## <a name="operatorgt"></a><a name="op_gt"></a>Operator&gt;

Testet, ob das `optional`-Objekt links vom Operator größer als das `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

*Richting*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator größer als die Liste rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `right < left` zurück.

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operator&gt;=

Testet, ob das `optional`-Objekt links vom Operator größer oder gleich dem `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Links*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

*Richting*\
Ein Objekt `optional`vom `nullopt_t`Typ `T`, oder .

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das `optional`-Objekt links vom Operator größer gleich dem `optional`-Objekt rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(left < right)` zurück.
