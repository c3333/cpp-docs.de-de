---
title: optionale&gt; Operatoren &lt;
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
ms.openlocfilehash: c5d0de435180054b186400384fc0583df5b03246
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425286"
---
# <a name="ltoptionalgt-operators"></a>optionale&gt; Operatoren &lt;

## <a name="op_eq_eq"></a>Operator = =

Testet, ob das `optional`-Objekt links vom Operator gleich dem `optional`-Objekt rechts vom Operator ist.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

*Rechte*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

## <a name="op_neq"></a>Operator! =

Testet, ob das `optional`-Objekt links vom Operator ungleich dem `optional`-Objekt rechts vom Operator ist.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

*Rechte*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

### <a name="remarks"></a>Hinweise

Die dritte Vorlagenfunktion gibt `!(left == right)` zurück.

## <a name="op_lt"></a>-Operator&lt;

Testet, ob das `optional`-Objekt links vom Operator kleiner als das `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

*Rechte*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator kleiner als, aber ungleich der Liste rechts vom Operator ist; andernfalls **FALSE**.

## <a name="op_lt_eq"></a>operator&lt;=

Testet, ob das `optional`-Objekt links vom Operator kleiner oder gleich dem `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

*Rechte*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator kleiner als oder gleich der Liste rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Hinweise

Die dritte Vorlagenfunktion gibt `!(right < left)` zurück.

## <a name="op_gt"></a>-Operator&gt;

Testet, ob das `optional`-Objekt links vom Operator größer als das `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

*Rechte*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator größer als die Liste rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Hinweise

Die dritte Vorlagenfunktion gibt `right < left` zurück.

## <a name="op_gt_eq"></a>Operator&gt;=

Testet, ob das `optional`-Objekt links vom Operator größer oder gleich dem `optional`-Objekt auf der rechten Seite ist.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

*Rechte*\
Ein Objekt vom Typ `optional`, `nullopt_t`oder `T`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn das `optional`-Objekt links vom Operator größer gleich dem `optional`-Objekt rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Hinweise

Die Vorlagenfunktion gibt `!(left < right)` zurück.
