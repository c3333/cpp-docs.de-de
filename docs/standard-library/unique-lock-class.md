---
title: unique_lock-Klasse
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 189fd70ce10b6067646553f2b92a8fc09239d054
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212034"
---
# <a name="unique_lock-class"></a>unique_lock-Klasse

Stellt eine Vorlage dar, die zum Erstellen von Objekten instanziiert werden kann, die das Sperren und Entsperren von `mutex` verwalten.

## <a name="syntax"></a>Syntax

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Bemerkungen

Das Vorlagenargument `Mutex` muss einem *Mutex-Typ* benennen.

Intern speichert ein einen `unique_lock` Zeiger auf ein zugeordnetes `mutex` -Objekt und einen **`bool`** , der angibt, ob der aktuelle Thread den besitzt `mutex` .

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`mutex_type`|Synonym für das Vorlagenargument `Mutex`.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[unique_lock](#unique_lock)|Erstellt ein `unique_lock`-Objekt.|
|[~ unique_lock-Dekonstruktor](#dtorunique_lock_destructor)|Gibt alle Ressourcen frei, die dem `unique_lock`-Objekt zugeordnet sind.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[lock](#lock)|Blockiert den aufrufenden Thread, bis der Thread in den Besitz des zugeordneten `mutex` gelangt.|
|[Mutex](#mutex)|Ruft den gespeicherten Zeiger auf das zugeordnete `mutex` auf.|
|[owns_lock](#owns_lock)|Gibt an, ob der aufrufende Thread das zugeordnete `mutex` besitzt.|
|[Abgabe](#release)|Trennt das `unique_lock`-Objekt vom zugeordneten `mutex`-Objekt.|
|[swap](#swap)|Tauscht das zugeordnete `mutex` und den Besitzstatus mit dem eines angegebenen Objekts.|
|[try_lock](#try_lock)|Versucht, ohne Blockierung in den Besitz des verknüpften `mutex` zu gelangen.|
|[try_lock_for](#try_lock_for)|Versucht, ohne Blockierung in den Besitz des verknüpften `mutex` zu gelangen.|
|[try_lock_until](#try_lock_until)|Versucht, ohne Blockierung in den Besitz des verknüpften `mutex` zu gelangen.|
|[Entsperren](#unlock)|Gibt den Besitz des zugeordneten `mutex` frei.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator bool](#op_bool)|Gibt an, ob der anrufende Thread das zugeordnete `mutex` besitzt.|
|[Operator =](#op_eq)|Kopiert den gespeicherten `mutex`-Zeiger und den zugehörigen Besitzstatus aus einem angegebenen Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

*unique_lock*

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<mutex>

**Namespace:** std

## <a name="lock"></a><a name="lock"></a>Sperre

Blockiert den aufrufenden Thread, bis der Thread in den Besitz des zugeordneten `mutex` gelangt.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Wenn der gespeicherte `mutex` Zeiger NULL ist, löst diese Methode eine [System_Error](../standard-library/system-error-class.md) mit einem Fehlercode von aus `operation_not_permitted` .

Wenn der aufrufende Thread das zugeordnete `mutex` bereits besitzt, löst diese Methode einen `system_error` aus, der den Fehlercode `resource_deadlock_would_occur` hat.

Andernfalls ruft diese Methode `lock` für die zugeordnete auf `mutex` und legt das interne Thread Besitz-Flag auf fest **`true`** .

## <a name="mutex"></a><a name="mutex"></a>Mutex

Ruft den gespeicherten Zeiger auf das zugeordnete `mutex` auf.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="operator-bool"></a><a name="op_bool"></a>Operator bool

Gibt an, ob der aufrufende Thread das zugeordnete Mutex besitzt.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Thread dem Mutex gehört. andernfalls **`false`** .

## <a name="operator"></a><a name="op_eq"></a>Operator =

Kopiert den gespeicherten `mutex`-Zeiger und den zugehörigen Besitzstatus aus einem angegebenen Objekt.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*Außer*\
Ein `unique_lock`-Objekt.

### <a name="return-value"></a>Rückgabewert

`*this`

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread das zuvor zugeordnete `mutex` besitzt, weist diese Methode die neuen Werte zu, bevor sie `unlock` auf dem `mutex` aufruft.

Nach dem Kopieren legt diese Methode einen *anderen* auf einen standardmäßig konstruierten Zustand fest.

## <a name="owns_lock"></a><a name="owns_lock"></a>owns_lock

Gibt an, ob der aufrufende Thread das zugeordnete `mutex` besitzt.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Thread den besitzt, `mutex` andernfalls **`false`** .

## <a name="release"></a><a name="release"></a>Abgabe

Trennt das `unique_lock`-Objekt vom zugeordneten `mutex`-Objekt.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Rückgabewert

Der vorherige Wert des gespeicherten `mutex`-Zeigers.

### <a name="remarks"></a>Bemerkungen

Diese Methode legt den Wert des gespeicherten `mutex` Zeigers auf 0 fest und legt das interne `mutex` Besitz Kennzeichen auf fest **`false`** .

## <a name="swap"></a><a name="swap"></a>Wechsel

Tauscht das zugeordnete `mutex` und den Besitzstatus mit dem eines angegebenen Objekts.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*Außer*\
Ein `unique_lock`-Objekt.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Versucht, ohne Blockierung in den Besitz des verknüpften `mutex` zu gelangen.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` ; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der gespeicherte `mutex` Zeiger NULL ist, löst die Methode eine [System_Error](../standard-library/system-error-class.md) mit einem Fehlercode von aus `operation_not_permitted` .

Wenn der aufrufende Thread das `mutex` bereits besitzt, löst die Methode einen `system_error` aus, der den Fehlercode `resource_deadlock_would_occur` hat.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Versucht, ohne Blockierung in den Besitz des verknüpften `mutex` zu gelangen.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parameter

*Rel_time*\
Ein [chrono::duration](../standard-library/duration-class.md)-Objekt, das angibt, wie lange die Methode höchstens versucht, in den Besitz des `mutex` zu gelangen.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` ; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der gespeicherte `mutex` Zeiger NULL ist, löst die Methode eine [System_Error](../standard-library/system-error-class.md) mit einem Fehlercode von aus `operation_not_permitted` .

Wenn der aufrufende Thread das `mutex` bereits besitzt, löst die Methode einen `system_error` aus, der den Fehlercode `resource_deadlock_would_occur` hat.

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

Versucht, ohne Blockierung in den Besitz des verknüpften `mutex` zu gelangen.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parameter

*Abs_time*\
Ein Zeitpunkt, der den Schwellenwert angibt, nach dem die Methode nicht mehr versucht, in den Besitz von `mutex` zu gelangen.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` ; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der gespeicherte `mutex` Zeiger NULL ist, löst die Methode eine [System_Error](../standard-library/system-error-class.md) mit einem Fehlercode von aus `operation_not_permitted` .

Wenn der aufrufende Thread das `mutex` bereits besitzt, löst die Methode einen `system_error` aus, der den Fehlercode `resource_deadlock_would_occur` hat.

## <a name="unique_lock-constructor"></a><a name="unique_lock"></a>unique_lock-Konstruktor

Erstellt ein `unique_lock`-Objekt.

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>Parameter

*MTX*\
Ein Mutex-Typobjekt.

*Rel_time*\
Ein [chrono::duration](../standard-library/duration-class.md)-Objekt, das angibt, wie lange die Methode höchstens versucht, in den Besitz des `mutex` zu gelangen.

*Abs_time*\
Ein Zeitpunkt, der den Schwellenwert angibt, nach dem die Methode nicht mehr versucht, in den Besitz von `mutex` zu gelangen.

*Außer*\
Ein `unique_lock`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt ein Objekt, das den zugeordneten Mutexzeigerwert 0 hat.

Mit dem zweiten Konstruktor wird der zugehörige Mutex-Status von einem *anderen*verschoben. Nach dem Verschieben ist *andere* nicht mehr einem Mutex zugeordnet.

Die übrigen Konstruktoren speichern & *MTX* als gespeicherten `mutex` Zeiger. Der Besitz des `mutex` wird durch das zweite Argument bestimmt, falls vorhanden.

|||
|-|-|
|`No argument`|Der Besitz wird durch Aufrufen der `lock`-Methode auf dem zugeordneten `mutex`-Objekt erlangt.|
|`Adopt`|Der Besitz wird angenommen. `Mtx` muss gesperrt sein, wenn der Konstruktor aufgerufen wird.|
|`Defer`|Es wird davon ausgegangen, dass der aufrufende Thread das `mutex`-Objekt nicht besitzt. `Mtx` darf nicht gesperrt sein, wenn der Konstruktor aufgerufen wird.|
|`Try`|Der Besitz wird durch Aufrufen von `try_lock` auf dem zugeordneten `mutex`-Objekt bestimmt. Der Konstruktor löst nichts aus.|
|`Rel_time`|Der Besitz wird durch Aufrufen von `try_lock_for(Rel_time)` bestimmt.|
|`Abs_time`|Der Besitz wird durch Aufrufen von `try_lock_until(Abs_time)` bestimmt.|

## <a name="unique_lock-destructor"></a><a name="dtorunique_lock_destructor"></a> ~unique_lock-Destruktor

Gibt alle Ressourcen frei, die dem `unique_lock`-Objekt zugeordnet sind.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread das zugehörige `mutex` besitzt, gibt der Destruktor den Besitz durch Aufrufen von unlock auf dem `mutex`-Objekt frei.

## <a name="unlock"></a><a name="unlock"></a>Entsperren

Gibt den Besitz des zugeordneten `mutex` frei.

```cpp
void unlock();
```

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread das zugeordnete `mutex` nicht besitzt, löst diese Methode einen [system_error](../standard-library/system-error-class.md) aus, der den Fehlercode `operation_not_permitted` hat.

Andernfalls ruft diese Methode `unlock` für die zugeordnete auf `mutex` und legt das interne Thread Besitz-Flag auf fest **`false`** .

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
