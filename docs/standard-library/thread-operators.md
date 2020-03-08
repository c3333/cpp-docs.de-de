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
ms.openlocfilehash: c0593b8016cf45abe64114958ccda84eb3704844
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876169"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt;-Operatoren

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a>operator&gt;=

Bestimmt, ob ein `thread::id`-Objekt größer als oder gleich einem anderen Objekt ist.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `thread::id`-Objekt.

*Rechte*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Left < Right)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_gt"></a> operator&gt;

Bestimmt, ob ein `thread::id`-Objekt größer als ein anderes Objekt ist.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `thread::id`-Objekt.

*Rechte*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`Right < Left`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_lt_eq"></a>operator&lt;=

Bestimmt, ob ein `thread::id`-Objekt kleiner als oder gleich einem anderen Objekt ist.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `thread::id`-Objekt.

*Rechte*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Right < Left)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_lt"></a> operator&lt;

Bestimmt, ob ein `thread::id`-Objekt kleiner als ein anderes Objekt ist.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `thread::id`-Objekt.

*Rechte*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

**true** , wenn *left* in der Gesamt Reihenfolge *direkt* vorangestellt ist. andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Der Operator definiert eine gesamte Sortierung für alle `thread::id`-Objekte. Diese Objekte können als Schlüssel in assoziativen Containern verwendet werden.

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_neq"></a> operator!=

Überprüft zwei `thread::id` -Objekte auf Ungleichheit.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `thread::id`-Objekt.

*Rechte*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Left == Right)`

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_eq_eq"></a> operator==

Überprüft zwei `thread::id`-Objekte auf Gleichheit.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `thread::id`-Objekt.

*Rechte*\
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die beiden-Objekte denselben Ausführungs Thread darstellen, oder wenn keines der Objekte einen Ausführungs Thread darstellt. andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_lt_lt"></a>operator&lt;&lt;

Fügt eine Textdarstellung eines `thread::id`-Objekts in einen Stream ein.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parameter

*Ostr* -\
Ein [basic_ostream](../standard-library/basic-ostream-class.md)-Objekt.

*ID* -\
Ein `thread::id` -Objekt.

### <a name="return-value"></a>Rückgabewert

*Ostr*.

### <a name="remarks"></a>Bemerkungen

Diese Funktion fügt *ID* in *Ostr*ein.

Wenn zwei `thread::id`-Objekte gleich sind, sind die eingefügten Text-Darstellungen dieser Objekte gleich.

## <a name="see-also"></a>Weitere Informationen

[\<thread>](../standard-library/thread.md)
