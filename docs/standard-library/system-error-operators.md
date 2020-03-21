---
title: '&lt;system_error&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 8631cae146a311f1890583900b564471d5a80958
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076261"
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

*Linker*\
Das Objekt, das auf Gleichheit getestet werden soll.

*Rechte*\
Das Objekt, das auf Gleichheit getestet werden soll.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Objekte gleich sind; **FALSE**, wenn die Objekte nicht gleich sind.

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

*Linker*\
Das Objekt, das auf Ungleichheit geprüft werden soll.

*Rechte*\
Das Objekt, das auf Ungleichheit geprüft werden soll.

### <a name="return-value"></a>Rückgabewert

**true** , wenn das von *Links* übergebenen-Objekt nicht gleich dem-Objekt ist, das *Rechts*übergangen ist; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Die Funktion gibt `!(left == right)`zurück.

## <a name="operatorlt"></a><a name="op_lt"></a>-Operator&lt;

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

*Linker*\
Das Objekt, das verglichen werden soll.

*Rechte*\
Das Objekt, das verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**true** , wenn das *Links* übergebenen Objekt kleiner ist als das Objekt, das in der *rechten*Ecke übergangen ist. Andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird die Fehlerreihenfolge getestet.

## <a name="operatorltlt"></a><a name="op_ostream"></a>Operator&lt;&lt;

```cpp
template <class charT, class traits>
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
