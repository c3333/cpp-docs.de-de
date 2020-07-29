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
ms.openlocfilehash: e7321831b9356fdb9ae5ce147319726def69efc7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215568"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt;-Operatoren

||||
|-|-|-|
|[Operator! =](#op_neq)|[KOM&gt;](#op_gt)|[KOM&gt;=](#op_gt_eq)|
|[KOM&lt;](#op_lt)|[KOM&lt;&lt;](#op_lt_lt)|[KOM&lt;=](#op_lt_eq)|
|[Operator = =](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Bestimmt, ob ein `thread::id`-Objekt größer als oder gleich einem anderen Objekt ist.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linken*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Left < Right)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Bestimmt, ob ein `thread::id`-Objekt größer als ein anderes Objekt ist.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linken*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`Right < Left`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Bestimmt, ob ein `thread::id`-Objekt kleiner als oder gleich einem anderen Objekt ist.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linken*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Right < Left)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Bestimmt, ob ein `thread::id`-Objekt kleiner als ein anderes Objekt ist.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linken*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

**`true`**, *Wenn der* Wert in der Gesamt Reihenfolge in der *rechten Ecke liegt* . andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Der Operator definiert eine gesamte Sortierung für alle `thread::id`-Objekte. Diese Objekte können als Schlüssel in assoziativen Containern verwendet werden.

Diese Funktion löst keine Ausnahmen aus.

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Überprüft zwei `thread::id`-Objekte auf Ungleichheit.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linken*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Left == Right)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Überprüft zwei `thread::id`-Objekte auf Gleichheit.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linken*\
Das linke `thread::id`-Objekt.

*Richting*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die beiden-Objekte denselben Ausführungs Thread darstellen, oder wenn keines der Objekte einen Ausführungs Thread darstellt. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>KOM&lt;&lt;

Fügt eine Textdarstellung eines `thread::id`-Objekts in einen Stream ein.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parameter

*Ostr*\
Ein [basic_ostream](../standard-library/basic-ostream-class.md)-Objekt.

*Name*\
Ein `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

*Ostr*.

### <a name="remarks"></a>Bemerkungen

Diese Funktion fügt *ID* in *Ostr*ein.

Wenn zwei `thread::id`-Objekte gleich sind, sind die eingefügten Text-Darstellungen dieser Objekte gleich.

## <a name="see-also"></a>Weitere Informationen

[\<thread>](../standard-library/thread.md)
