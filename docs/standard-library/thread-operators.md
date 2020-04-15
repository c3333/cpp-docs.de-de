---
title: '&lt;thread&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 6312d14dc681736ee396d5c7af6c50ba8d72cd3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375832"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt;-Operatoren

||||
|-|-|-|
|[Operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;&lt;](#op_lt_lt)|[Operator&lt;=](#op_lt_eq)|
|[Betreiber== Einzelnachweise ==](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operator&gt;=

Bestimmt, ob ein `thread::id`-Objekt größer als oder gleich einem anderen Objekt ist.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Left < Right)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operatorgt"></a><a name="op_gt"></a>Operator&gt;

Bestimmt, ob ein `thread::id`-Objekt größer als ein anderes Objekt ist.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`Right < Left`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operator&lt;=

Bestimmt, ob ein `thread::id`-Objekt kleiner als oder gleich einem anderen Objekt ist.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Right < Left)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operatorlt"></a><a name="op_lt"></a>Operator&lt;

Bestimmt, ob ein `thread::id`-Objekt kleiner als ein anderes Objekt ist.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

**true,** wenn *Links* in der Gesamtreihenfolge *rechts* vorangeht; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Der Operator definiert eine gesamte Sortierung für alle `thread::id`-Objekte. Diese Objekte können als Schlüssel in assoziativen Containern verwendet werden.

Diese Funktion löst keine Ausnahmen aus.

## <a name="operator"></a><a name="op_neq"></a>Operator!=

Überprüft zwei `thread::id`-Objekte auf Ungleichheit.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Left == Right)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operator"></a><a name="op_eq_eq"></a>Betreiber== Einzelnachweise ==

Überprüft zwei `thread::id`-Objekte auf Gleichheit.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

**true,** wenn die beiden Objekte denselben Ausführungsthread darstellen oder wenn keines der beiden Objekte einen Ausführungsthread darstellt; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Operator&lt;&lt;

Fügt eine Textdarstellung eines `thread::id`-Objekts in einen Stream ein.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parameter

*Ostr*\
Ein [basic_ostream](../standard-library/basic-ostream-class.md)-Objekt.

*Id*\
Ein `thread::id` -Objekt.

### <a name="return-value"></a>Rückgabewert

*Ostr*.

### <a name="remarks"></a>Bemerkungen

Diese Funktion fügt *Id* in *Ostr ein.*

Wenn zwei `thread::id`-Objekte gleich sind, sind die eingefügten Text-Darstellungen dieser Objekte gleich.

## <a name="see-also"></a>Siehe auch

[\<Gewinde>](../standard-library/thread.md)
