---
title: mutex-Klasse (C++-Standardbibliothek)| Microsoft-Dokumentation
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 20e2165a70dec8a3d3918eece6cb78057ac19138
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233040"
---
# <a name="mutex-class-c-standard-library"></a>mutex-Klasse (C++-Standardbibliothek)

Stellt einen *Mutex-Typ*dar. Objekte dieses Typs können dazu verwendet werden, den gegenseitigen Ausschluss innerhalb eines Programms zu erzwingen.

## <a name="syntax"></a>Syntax

```cpp
class mutex;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Mutex](#mutex)|Erstellt ein `mutex`-Objekt.|
|[Mutex:: ~ Mutex-Dekonstruktor](#dtormutex_destructor)|Gibt alle Ressourcen frei, die vom `mutex`-Objekt verwendet wurden.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[lock](#lock)|Blockiert den aufrufenden Thread, bis der Thread in den Besitz von `mutex` gelangt.|
|[native_handle](#native_handle)|Gibt den implementierungsspezifischen Typ zurück, der das Mutexhandle darstellt.|
|[try_lock](#try_lock)|Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.|
|[Entsperren](#unlock)|Gibt den Besitz von `mutex` frei.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<mutex>

**Namespace:** std

## <a name="mutexlock"></a><a name="lock"></a>Mutex:: Lock

Blockiert den aufrufenden Thread, bis der Thread in den Besitz von `mutex` gelangt.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread bereits im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="mutexmutex-constructor"></a><a name="mutex"></a>Mutex:: Mutex-Konstruktor

Erstellt ein `mutex`-Objekt, das nicht gesperrt ist.

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a>Mutex:: ~ Mutex-Dekonstruktor

Gibt alle Ressourcen frei, die vom `mutex`-Objekt verwendet werden.

```cpp
~mutex();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt gesperrt ist, wenn der Destruktor ausgeführt wird, ist das Verhalten nicht definiert.

## <a name="mutexnative_handle"></a><a name="native_handle"></a>Mutex:: native_handle

Gibt den implementierungsspezifischen Typ zurück, der das Mutexhandle darstellt. Das Mutexhandle kann je nach Implementierung auf die jeweils entsprechende Weise verwendet werden.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Rückgabewert

`native_handle_type` ist als `Concurrency::critical_section *` definiert, das als `void *` umgewandelt wird.

## <a name="mutextry_lock"></a><a name="try_lock"></a>Mutex:: try_lock

Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Methode erfolgreich in den Besitz von gelangt `mutex` ; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread bereits im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="mutexunlock"></a><a name="unlock"></a>Mutex:: Unlock

Gibt den Besitz von `mutex` frei.

```cpp
void unlock();
```

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread nicht im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="see-also"></a>Siehe auch

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
