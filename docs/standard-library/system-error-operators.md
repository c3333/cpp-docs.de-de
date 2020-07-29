---
title: '&lt;system_error&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5ddd9135749c2dcfd40cd06a9b69cff65b1a8c8d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232871"
---
# <a name="ltsystem_errorgt-operators"></a>&lt;system_error&gt;-Operatoren

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Testet, ob das Objekt links vom Operator gleich dem Objekt rechts vom Operator ist.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das Objekt, das auf Gleichheit getestet werden soll.

*Richting*\
Das Objekt, das auf Gleichheit getestet werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Objekte gleich sind. , **`false`** Wenn Objekte nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Die Funktion gibt `left.category() == right.category() && left.value() == right.value()`zurück.

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Testet, ob das Objekt links vom Operator ungleich dem Objekt rechts vom Operator ist.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das Objekt, das auf Ungleichheit geprüft werden soll.

*Richting*\
Das Objekt, das auf Ungleichheit geprüft werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das von *Links* übergebenen-Objekt nicht mit dem-Objekt identisch ist, das *Rechts*übergebenen ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Die Funktion gibt `!(left == right)`zurück.

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob ein Objekt kleiner ist als das Objekt, das für den Vergleich übergeben wurde.

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>Parameter

*linken*\
Das Objekt, das verglichen werden soll.

*Richting*\
Das Objekt, das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das *Links* übergebenen Objekt kleiner ist als das Objekt, das in der *rechten*Ecke übergebenen ist. Andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird die Fehlerreihenfolge getestet.

## <a name="operatorltlt"></a><a name="op_ostream"></a>KOM&lt;&lt;

```cpp
template <class charT, class traits>
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
