---
title: critical_section-Klasse
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: f7df639a879bad7af1b4de401460ff298e466c78
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215815"
---
# <a name="critical_section-class"></a>critical_section-Klasse

Ein nicht wieder eintretender Mutex, der explizit die Concurrency Runtime beachtet.

## <a name="syntax"></a>Syntax

```cpp
class critical_section;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`native_handle_type`|Ein Verweis auf ein `critical_section`-Objekt.|

### <a name="public-classes"></a>Öffentliche Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[critical_section::scoped_lock-Klasse](#critical_section__scoped_lock_class)|Ein Ausnahme sicherer RAII-Wrapper für ein- `critical_section` Objekt.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[critical_section](#ctor)|Erstellt einen neuen kritischen Abschnitt.|
|[~ CRITICAL_SECTION-Dekonstruktor](#dtor)|Zerstört einen kritischen Abschnitt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[lock](#lock)|Ruft diesen kritischen Abschnitt ab.|
|[native_handle](#native_handle)|Gibt einen plattformspezifischen systemeigenen Handle zurück, sofern vorhanden.|
|[try_lock](#try_lock)|Versucht, die Sperre abzurufen, ohne zu blockieren.|
|[try_lock_for](#try_lock_for)|Versucht, die Sperre abzurufen, ohne dass eine bestimmte Anzahl von Millisekunden blockiert wird.|
|[Entsperren](#unlock)|Entsperrt den kritischen Abschnitt.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Synchronisierungs Datenstrukturen](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`critical_section`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="critical_section"></a><a name="ctor"></a>critical_section

Erstellt einen neuen kritischen Abschnitt.

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>~ CRITICAL_SECTION

Zerstört einen kritischen Abschnitt.

```cpp
~critical_section();
```

### <a name="remarks"></a>Bemerkungen

Es wird erwartet, dass die Sperre nicht mehr aufrechterhalten wird, wenn der Dekonstruktor ausgeführt wird. Das zulassen, dass der kritische Abschnitt mit der gesperrten Sperre Zerstörung wird, führt zu nicht definiertem Verhalten.

## <a name="lock"></a><a name="lock"></a>Sperre

Ruft diesen kritischen Abschnitt ab.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Es ist oft sicherer, das [scoped_lock](#critical_section__scoped_lock_class) -Konstrukt zu verwenden, um ein- `critical_section` Objekt auf sichere Weise zu beschaffen und freizugeben.

Wenn die Sperre bereits vom aufrufenden Kontext abgehalten wird, wird eine [Improper_lock](improper-lock-class.md) Ausnahme ausgelöst.

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

Gibt einen plattformspezifischen systemeigenen Handle zurück, sofern vorhanden.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf den kritischen Abschnitt.

### <a name="remarks"></a>Bemerkungen

Ein- `critical_section` Objekt ist keinem plattformspezifischen systemeigenen Handle für das Windows-Betriebssystem zugeordnet. Die-Methode gibt einfach einen Verweis auf das-Objekt selbst zurück.

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>CRITICAL_SECTION:: scoped_lock-Klasse

Ein Ausnahme sicherer RAII-Wrapper für ein- `critical_section` Objekt.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Erstellt ein `scoped_lock` -Objekt und ruft das Objekt ab, das `critical_section` im-Parameter übergeben wird `_Critical_section` . Wenn der kritische Abschnitt von einem anderen Thread aufbewahrt wird, wird dieser-Befehl blockiert.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parameter

*_Critical_section*<br/>
Der zu Sperrungs kritische Abschnitt.

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Zerstört ein `scoped_lock` -Objekt und gibt den kritischen Abschnitt frei, der im Konstruktor bereitgestellt wird.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Versucht, die Sperre abzurufen, ohne zu blockieren.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Rückgabewert

Der Wert ist, wenn die Sperre abgerufen wurde, **`true`** andernfalls der Wert **`false`** .

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Versucht, die Sperre abzurufen, ohne dass eine bestimmte Anzahl von Millisekunden blockiert wird.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parameter

*_Timeout*<br/>
Die Anzahl der Millisekunden, die gewartet werden soll, bevor ein Timeout eintritt.

### <a name="return-value"></a>Rückgabewert

Der Wert ist, wenn die Sperre abgerufen wurde, **`true`** andernfalls der Wert **`false`** .

## <a name="unlock"></a><a name="unlock"></a>Entsperren

Entsperrt den kritischen Abschnitt.

```cpp
void unlock();
```

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[reader_writer_lock-Klasse](reader-writer-lock-class.md)
