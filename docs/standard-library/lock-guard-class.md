---
title: lock_guard-Klasse
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 989c1e368e95fc0009f0c3f1c71af0bdba20609d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351721"
---
# <a name="lock_guard-class"></a>lock_guard-Klasse

Stellt eine Vorlage dar, die zum Erstellen eines Objekts instanziiert werden kann, dessen Destruktor ein `mutex`-Objekt entsperrt.

## <a name="syntax"></a>Syntax

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Bemerkungen

Das Vorlagenargument `Mutex` muss einem *Mutex-Typ* benennen.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonym für das Vorlagenargument `Mutex`.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[lock_guard](#lock_guard)|Erstellt ein `lock_guard`-Objekt.|
|[lock_guard::lock_guard Destruktor](#dtorlock_guard_destructor)|Entsperrt das `mutex`-Objekt, das an den Konstruktor übergeben wurde.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** \<mutex>

**Namespace:** std

## <a name="lock_guardlock_guard-constructor"></a><a name="lock_guard"></a>lock_guard::lock_guard Konstruktor

Erstellt ein `lock_guard`-Objekt.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parameter

*Mtx*\
Ein *mutex type*-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt ein `lock_guard` Objekt vom Typ und sperrt *Mtx*. Wenn *Mtx* kein rekursiver Mutex ist, muss er entsperrt werden, wenn dieser Konstruktor aufgerufen wird.

Der zweite Konstruktor sperrt *Mtx*nicht . *Mtx* muss gesperrt werden, wenn dieser Konstruktor aufgerufen wird. Der Konstruktor löst keine Ausnahmen aus.

## <a name="lock_guardlock_guard-destructor"></a><a name="dtorlock_guard_destructor"></a>lock_guard::lock_guard Destruktor

Entsperrt das `mutex`-Objekt, das an den Konstruktor übergeben wurde.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Bemerkungen

Wenn das `mutex`-Objekt nicht vorhanden ist, wenn der Destruktor ausgeführt wird, ist das Verhalten nicht definiert.

## <a name="see-also"></a>Siehe auch

[Header-Dateien-Referenz](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
