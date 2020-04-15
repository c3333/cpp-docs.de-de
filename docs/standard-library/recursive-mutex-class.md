---
title: recursive_mutex-Klasse
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 9ab7a96a7c07582450ab41b140dcc5494a63661f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320206"
---
# <a name="recursive_mutex-class"></a>recursive_mutex-Klasse

Stellt einen *Mutex-Typ*dar. Das Verhalten von aufrufenden Sperrmethoden für Objekte, die bereits gesperrt sind, ist im Gegensatz zu [mutex](../standard-library/mutex-class-stl.md) klar definiert.

## <a name="syntax"></a>Syntax

```cpp
class recursive_mutex;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Erstellt ein `recursive_mutex`-Objekt.|
|[~recursive_mutex-Destruktor](#dtorrecursive_mutex_destructor)|Gibt alle Ressourcen frei, die vom `recursive_mutex`-Objekt verwendet werden.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Sperren](#lock)|Blockiert den aufrufenden Thread, bis der Thread in den Besitz von mutex gelangt.|
|[try_lock](#try_lock)|Versucht, ohne Blockierung in den Besitz von mutex zu gelangen.|
|[Entsperren](#unlock)|Gibt den Besitz von mutex frei.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<mutex>

**Namespace:** std

## <a name="lock"></a><a name="lock"></a>Sperren

Blockiert den aufrufenden Thread, bis der Thread in den Besitz von `mutex` gelangt.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread bereits im Besitz von `mutex` ist, wird die Methode sofort zurückgegeben, und die vorherige Sperre bleibt in Kraft.

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a>recursive_mutex

Erstellt ein `recursive_mutex`-Objekt, das nicht gesperrt ist.

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a> ~recursive_mutex

Gibt alle Ressourcen frei, die vom Objekt verwendet werden.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt gesperrt ist, wenn der Destruktor ausgeführt wird, ist das Verhalten nicht definiert.

## <a name="try_lock"></a><a name="try_lock"></a>Try_lock

Versucht, ohne Blockierung in den Besitz von `mutex` zu gelangen.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn die Methode erfolgreich `mutex` den Besitz des oder `mutex**; otherwise, **false`wenn der aufrufende Thread bereits Eigentümer der .

### <a name="remarks"></a>Bemerkungen

Wenn der aufrufende Thread `mutex`bereits eigentümer ist, gibt die Funktion sofort **true**zurück, und die vorherige Sperre bleibt wirksam.

## <a name="unlock"></a><a name="unlock"></a>Entsperren

Gibt den Besitz von mutex frei.

```cpp
void unlock();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt den Besitz der `mutex` erst zurück, wenn sie so oft aufgerufen wurde, wie [lock](#lock) und [try_lock](#try_lock) erfolgreich im `recursive_mutex`-Objekt aufgerufen wurden.

Wenn der aufrufende Thread nicht im Besitz von `mutex` ist, so ist das Verhalten nicht definiert.

## <a name="see-also"></a>Siehe auch

[Header-Dateien-Referenz](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
