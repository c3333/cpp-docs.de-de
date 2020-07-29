---
title: packaged_task-Klasse
ms.date: 11/04/2016
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.openlocfilehash: d03fb128240c4e3e6bd48c3237d240afba946ad8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233027"
---
# <a name="packaged_task-class"></a>packaged_task-Klasse

Beschreibt einen *asynchronen Anbieter*, der ein Aufrufwrapper und dessen Aufrufsignatur `Ty(ArgTypes...)` ist. Der *zugehörige asynchrone Zustand* enthält zusätzlich zum möglichen Ergebnis eine Kopie des Aufruf baren Objekts.

## <a name="syntax"></a>Syntax

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[packaged_task](#packaged_task)|Erstellt ein `packaged_task`-Objekt.|
|[packaged_task:: ~ packaged_task-Dekonstruktor](#dtorpackaged_task_destructor)|Zerstört ein `packaged_task` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[get_future](#get_future)|Gibt ein [future](../standard-library/future-class.md)-Objekt zurück, das über den gleichen zugeordneten asynchronen Zustand verfügt.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Ruft das aufrufbare Objekt auf, das im zugeordneten asynchronen Zustand gespeichert ist und speichert automatisch den zurückgegebenen Wert.|
|[reset](#reset)|Ersetzt den zugeordneten asynchronen Zustand.|
|[swap](#swap)|Tauscht den zugeordneten asynchronen Zustand dieses Zusageobjekts mit dem eines angegebenen Objekts aus.|
|[gültigen](#valid)|Legt fest, ob das Objekt einen zugeordneten asynchronen Zustand hat.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[packaged_task:: Operator =](#op_eq)|Überträgt einen zugeordneten asynchronen Zustand aus einem angegebenen Objekt.|
|[packaged_task:: Operator ()](#op_call)|Ruft das aufrufbare Objekt auf, das im zugeordneten asynchronen Zustand gespeichert ist, speichert den zurückgegebenen Wert atomar und legt den Zustand auf *bereit* fest.|
|[packaged_task::operator bool](#op_bool)|Legt fest, ob das Objekt einen zugeordneten asynchronen Zustand hat.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<future>

**Namespace:** std

## <a name="packaged_taskget_future"></a><a name="get_future"></a>packaged_task:: get_future

Gibt ein `future<Ty>`-Objekt zurück, das über den gleichen *zugeordneten asynchronen Zustand* verfügt.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Bemerkungen

Wenn das `packaged_task`-Objekt über keinen zugeordneten asynchronen Zustand verfügt, löst diese Methode [future_error](../standard-library/future-error-class.md) mit einem Fehlercode von `no_state` aus.

Wenn diese Methode bereits für ein `packaged_task`-Objekt mit dem gleichen zugeordneten asynchronen Zustand aufgerufen wurde, löst die Methode ein `future_error` mit einem Fehlercode von `future_already_retrieved` aus.

## <a name="packaged_taskmake_ready_at_thread_exit"></a><a name="make_ready_at_thread_exit"></a>packaged_task:: make_ready_at_thread_exit

Ruft das aufrufbare Objekt auf, das im *zugeordneten asynchronen Zustand* gespeichert ist und den Rückgabewert atomar speichert.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Bemerkungen

Wenn das `packaged_task`-Objekt über keinen zugeordneten asynchronen Zustand verfügt, löst diese Methode [future_error](../standard-library/future-error-class.md) mit einem Fehlercode von `no_state` aus.

Wenn diese Methode oder [make_ready_at_thread_exit](#make_ready_at_thread_exit) bereits für ein `packaged_task`-Objekt mit dem gleichen zugeordneten asynchronen Zustand aufgerufen wurde, löst die Methode ein `future_error` mit einem Fehlercode von `promise_already_satisfied` aus.

Andernfalls ruft dieser Operator `INVOKE(fn, args..., Ty)` auf, in dem *fn* das aufrufbare Objekt ist, das im zugeordneten asynchronen Zustand gespeichert ist. Jeder Rückgabewert wird atomar als das zurückgegebene Ergebnis des assoziierten asynchronen Zustands gespeichert.

Im Gegensatz zu [packaged_task::operator()](#op_call), wird der zugeordnete asynchrone Zustand erst auf `ready` festgelegt, nachdem alle Objekte eines lokalen Threads im aktuellen Thread zerstört wurden. Normalerweise kann die Blockierung von Threads, die auf dem zugeordneten asynchronen Zustand blockiert werden, nicht aufgehoben werden, bis der aktuelle Thread beendet wird.

## <a name="packaged_taskoperator"></a><a name="op_eq"></a>packaged_task:: Operator =

Überträgt den *zugeordneten asynchronen Zustand* aus einem angegebenen-Objekt.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `packaged_task`-Objekt.

### <a name="return-value"></a>Rückgabewert

`*this`

### <a name="remarks"></a>Bemerkungen

Nach dem-Vorgang verfügt *right* nicht mehr über einen zugeordneten asynchronen Zustand.

## <a name="packaged_taskoperator"></a><a name="op_call"></a>packaged_task:: Operator ()

Ruft das Aufruf Bare Objekt auf, das im *zugeordneten asynchronen Zustand*gespeichert ist, speichert den zurückgegebenen Wert atomisch und legt den Zustand auf *Ready*fest.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Bemerkungen

Wenn das `packaged_task`-Objekt über keinen zugeordneten asynchronen Zustand verfügt, löst diese Methode [future_error](../standard-library/future-error-class.md) mit einem Fehlercode von `no_state` aus.

Wenn diese Methode oder [make_ready_at_thread_exit](#make_ready_at_thread_exit) bereits für ein `packaged_task`-Objekt mit dem gleichen zugeordneten asynchronen Zustand aufgerufen wurde, löst die Methode ein `future_error` mit einem Fehlercode von `promise_already_satisfied` aus.

Andernfalls ruft dieser Operator `INVOKE(fn, args..., Ty)` auf, in dem *fn* das aufrufbare Objekt ist, das im zugeordneten asynchronen Zustand gespeichert ist. Alle Rückgabewerte werden als das zurückgegebene Ergebnis des assoziierten asynchronen Zustands atomar gespeichert wird, und der Status wird auf bereit festgelegt. Deshalb wird die Blockierung aller Threads, die auf dem zugeordneten asynchronen Zustand blockiert werden, aufgehoben.

## <a name="packaged_taskoperator-bool"></a><a name="op_bool"></a>packaged_task:: Operator bool

Gibt an, ob das Objekt über `associated asynchronous state` verfügt.

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Objekt über einen zugeordneten asynchronen Zustand verfügt. andernfalls **`false`** .

## <a name="packaged_taskpackaged_task-constructor"></a><a name="packaged_task"></a>packaged_task::p ackaged_task-Konstruktor

Erstellt ein `packaged_task`-Objekt.

```cpp
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `packaged_task`-Objekt.

*Zuordnungseinheits*\
Eine Speicherbelegung. Weitere Informationen finden Sie unter [\<allocators>](../standard-library/allocators-header.md).

*Extreme*\
Ein Funktionsobjekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt ein- `packaged_task` Objekt, das über keinen *zugeordneten asynchronen Zustand*verfügt.

Der zweite Konstruktor erstellt ein `packaged_task` -Objekt und überträgt den zugeordneten asynchronen Zustand von *Rechts*. Nach dem-Vorgang verfügt *right* nicht mehr über einen zugeordneten asynchronen Zustand.

Mit dem dritten Konstruktor wird ein- `packaged_task` Objekt erstellt, das über eine in seinem zugeordneten asynchronen Zustand gespeicherte Kopie von *FN* verfügt.

Mit dem vierten Konstruktor `packaged_task` wird ein-Objekt erstellt, das über eine in seinem zugeordneten asynchronen Zustand gespeicherte Kopie von *FN* verfügt und `alloc` für die Speicher Belegung verwendet.

## <a name="packaged_taskpackaged_task-destructor"></a><a name="dtorpackaged_task_destructor"></a>packaged_task:: ~ packaged_task-Dekonstruktor

Zerstört ein `packaged_task` -Objekt.

```cpp
~packaged_task();
```

### <a name="remarks"></a>Bemerkungen

Wenn der *zugeordnete asynchrone Zustand* nicht *bereit* ist, speichert der Destruktor eine [future_error](../standard-library/future-error-class.md)-Ausnahme, die über den Fehlercode `broken_promise` als Ergebnis im zugeordneten asynchronen Zustand verfügt, und alle Threads, die auf dem zugeordneten asynchronen Zustand blockiert sind, werden aufgehoben.

## <a name="packaged_taskreset"></a><a name="reset"></a>packaged_task:: Reset

Verwendet einen neuen *zugeordneten asynchronen Zustand* zum Ersetzen des vorhandenen zugeordneten asynchronen Zustands.

```cpp
void reset();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode führt tatsächlich `*this = packaged_task(move(fn))` aus, wobei *fn* das Funktionsobjekt ist, das im zugeordneten asynchronen Zustand dieses Objekts gespeichert ist. Daher wird der Zustand des Objekts deaktiviert, und [get_future](#get_future), [operator()](#op_call) und [make_ready_at_thread_exit](#make_ready_at_thread_exit) können aufgerufen werden, als ob sie sich auf einem neu erstellten Objekt befinden würden.

## <a name="packaged_taskswap"></a><a name="swap"></a>packaged_task:: Swap

Tauscht den zugeordneten asynchronen Zustand dieses Zusageobjekts mit dem eines angegebenen Objekts aus.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein `packaged_task`-Objekt.

## <a name="packaged_taskvalid"></a><a name="valid"></a>packaged_task:: valid

Gibt an, ob das Objekt über `associated asynchronous state` verfügt.

```cpp
bool valid() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Objekt über einen zugeordneten asynchronen Zustand verfügt. andernfalls **`false`** .

## <a name="see-also"></a>Siehe auch

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
