---
title: timed_mutex-Klasse
ms.date: 11/04/2016
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.openlocfilehash: 3329c46f0760a13693507de18a09b974b6b646e2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212097"
---
# <a name="timed_mutex-class"></a>timed_mutex-Klasse

Stellt einen Zeit *gesteuerten Mutex-Typ*dar. Objekte dieses Typs werden verwendet, um den gegenseitigen Ausschluss durch zeitlich begrenzte Blockierung innerhalb eines Programms zu erzwingen.

## <a name="syntax"></a>Syntax

```cpp
class timed_mutex;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Erstellt ein `timed_mutex`-Objekt, das nicht gesperrt ist.|
|[timed_mutex:: ~ timed_mutex-Dekonstruktor](#dtortimed_mutex_destructor)|Gibt alle Ressourcen frei, die vom `timed_mutex`-Objekt verwendet werden.|

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

## <a name="timed_mutexlock"></a><a name="lock"></a>timed_mutex:: Lock

Blockiert den aufrufenden Thread, bis der Thread in den Besitz von `mutex` gelangt.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread bereits im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="timed_mutextimed_mutex-constructor"></a><a name="timed_mutex"></a>timed_mutex:: timed_mutex-Konstruktor

Erstellt ein `timed_mutex`-Objekt, das nicht gesperrt ist.

```cpp
timed_mutex();
```

## <a name="timed_mutextimed_mutex-destructor"></a><a name="dtortimed_mutex_destructor"></a>timed_mutex:: ~ timed_mutex-Dekonstruktor

Gibt alle Ressourcen frei, die vom `mutex`-Objekt verwendet werden.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt gesperrt ist, wenn der Destruktor ausgeführt wird, ist das Verhalten nicht definiert.

## <a name="timed_mutextry_lock"></a><a name="try_lock"></a>timed_mutex:: try_lock

Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` ; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread bereits im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="timed_mutextry_lock_for"></a><a name="try_lock_for"></a>timed_mutex:: try_lock_for

Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parameter

*Rel_time*\
Ein [chrono::duration](../standard-library/duration-class.md)-Objekt, das angibt, wie lange die Methode höchstens versucht, in den Besitz des `mutex` zu gelangen.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` ; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread bereits im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="timed_mutextry_lock_until"></a><a name="try_lock_until"></a>timed_mutex:: try_lock_until

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

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` ; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread bereits im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="timed_mutexunlock"></a><a name="unlock"></a>timed_mutex:: Unlock

Gibt den Besitz von `mutex` frei.

```cpp
void unlock();
```

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread nicht im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
