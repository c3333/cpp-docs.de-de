---
title: recursive_timed_mutex-Klasse
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.openlocfilehash: 15517425f3d81bc3798df2e42f39ac0b0d32ba31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217596"
---
# <a name="recursive_timed_mutex-class"></a>recursive_timed_mutex-Klasse

Stellt einen Zeit *gesteuerten Mutex-Typ*dar. Objekte dieses Typs werden verwendet, um den gegenseitigen Ausschluss durch zeitlich begrenzte Blockierung innerhalb eines Programms zu erzwingen. Im Gegensatz zu Objekten des Typs [timed_mutex](../standard-library/timed-mutex-class.md), sind die Auswirkungen von aufrufenden Sperrmethoden für `recursive_timed_mutex`-Objekte klar definiert.

## <a name="syntax"></a>Syntax

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Erstellt ein `recursive_timed_mutex`-Objekt, das nicht gesperrt ist.|
|[~ recursive_timed_mutex-Dekonstruktor](#dtorrecursive_timed_mutex_destructor)|Gibt alle Ressourcen frei, die vom `recursive_timed_mutex`-Objekt verwendet werden.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[lock](#lock)|Blockiert den aufrufenden Thread, bis der Thread in den Besitz von `mutex` gelangt.|
|[try_lock](#try_lock)|Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.|
|[try_lock_for](#try_lock_for)|Versucht, den Besitz von `mutex` für ein angegebenes Zeitintervall zu erlangen.|
|[try_lock_until](#try_lock_until)|Versucht, den Besitz von `mutex` bis zu einem angegebenen Zeitpunkt zu erlangen.|
|[Entsperren](#unlock)|Gibt den Besitz von `mutex` frei.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<mutex>

**Namespace:** std

## <a name="lock"></a><a name="lock"></a>Sperre

Blockiert den aufrufenden Thread, bis der Thread in den Besitz von `mutex` gelangt.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread bereits im Besitz von `mutex` ist, wird die Methode sofort zurückgegeben, und die vorherige Sperre bleibt in Kraft.

## <a name="recursive_timed_mutex-constructor"></a><a name="recursive_timed_mutex"></a>recursive_timed_mutex-Konstruktor

Erstellt ein `recursive_timed_mutex`-Objekt, das nicht gesperrt ist.

```cpp
recursive_timed_mutex();
```

## <a name="recursive_timed_mutex-destructor"></a><a name="dtorrecursive_timed_mutex_destructor"></a> ~recursive_timed_mutex-Destruktor

Gibt alle Ressourcen frei, die vom `recursive_timed_mutex`-Objekt verwendet werden.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt gesperrt ist, wenn der Destruktor ausgeführt wird, ist das Verhalten nicht definiert.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode den Besitz von erfolgreich abgerufen `mutex` hat, oder, wenn der aufrufenden Thread bereits den besitzt, `mutex` andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufenden Thread bereits im Besitz von `mutex` ist, gibt die Funktion sofort zurück **`true`** , und die vorherige Sperre bleibt in Kraft.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parameter

*Rel_time*\
Ein [chrono::duration](../standard-library/duration-class.md)-Objekt, das angibt, wie lange die Methode höchstens versucht, in den Besitz des `mutex` zu gelangen.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` , oder, wenn der aufrufenden Thread bereits im Besitz von `mutex` ist, andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufenden Thread bereits im Besitz von `mutex` ist, gibt die Methode sofort zurück **`true`** , und die vorherige Sperre bleibt in Kraft.

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parameter

*Abs_time*\
Ein Zeitpunkt, der den Schwellenwert angibt, nach dem die Methode nicht mehr versucht, in den Besitz von `mutex` zu gelangen.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` , oder, wenn der aufrufenden Thread bereits im Besitz von `mutex` ist, andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufenden Thread bereits im Besitz von `mutex` ist, gibt die Methode sofort zurück **`true`** , und die vorherige Sperre bleibt in Kraft.

## <a name="unlock"></a><a name="unlock"></a>Entsperren

Gibt den Besitz von `mutex` frei.

```cpp
void unlock();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt den Besitz der `mutex` erst frei, wenn sie so oft aufgerufen wurde, wie [lock](#lock), [try_lock](#try_lock)[try_lock_for](#try_lock_for), und [try_lock_until](#try_lock_until) erfolgreich im `recursive_timed_mutex`-Objekt aufgerufen wurden.

Wenn der aufrufende Thread nicht im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
