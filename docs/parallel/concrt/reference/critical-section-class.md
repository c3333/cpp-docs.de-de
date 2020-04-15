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
ms.openlocfilehash: 24f96282a7728c6db6e0b05d36406f15383913f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372681"
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
|[critical_section::scoped_lock-Klasse](#critical_section__scoped_lock_class)|Ein ausnahmesicherer RAII-Wrapper für ein `critical_section` Objekt.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[critical_section](#ctor)|Erstellt einen neuen kritischen Abschnitt.|
|[Nr. critical_section Destruktor](#dtor)|Zerstört einen kritischen Abschnitt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Sperren](#lock)|Erwirbt diesen kritischen Abschnitt.|
|[native_handle](#native_handle)|Gibt ein plattformspezifisches systemisches Handle zurück, sofern vorhanden.|
|[try_lock](#try_lock)|Versucht, die Sperre ohne Blockierung zu erwerben.|
|[try_lock_for](#try_lock_for)|Versucht, die Sperre zu erhalten, ohne für eine bestimmte Anzahl von Millisekunden zu blockieren.|
|[Entsperren](#unlock)|Schaltet den kritischen Abschnitt frei.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Synchronisierungsdatenstrukturen](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`critical_section`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

**Namespace:** Parallelität

## <a name="critical_section"></a><a name="ctor"></a>Critical_section

Erstellt einen neuen kritischen Abschnitt.

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>€critical_section

Zerstört einen kritischen Abschnitt.

```cpp
~critical_section();
```

### <a name="remarks"></a>Bemerkungen

Es wird erwartet, dass die Sperre nicht mehr gehalten wird, wenn der Destruktor ausgeführt wird. Das Zulassen, dass der kritische Abschnitt mit der weiterhin gehaltenen Sperre zerstört wird, führt zu einem undefinierten Verhalten.

## <a name="lock"></a><a name="lock"></a>Sperren

Erwirbt diesen kritischen Abschnitt.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Es ist oft sicherer, das [scoped_lock-Konstrukt](#critical_section__scoped_lock_class) zu verwenden, um ein `critical_section` Objekt auf eine Ausnahmesichere Weise zu erwerben und freizugeben.

Wenn die Sperre bereits vom aufrufenden Kontext gehalten wird, wird eine [improper_lock](improper-lock-class.md) Ausnahme ausgelöst.

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

Gibt ein plattformspezifisches systemisches Handle zurück, sofern vorhanden.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf den kritischen Abschnitt.

### <a name="remarks"></a>Bemerkungen

Ein `critical_section` Objekt ist keinem plattformspezifischen systemeigenen Handle für das Windows-Betriebssystem zugeordnet. Die Methode gibt einfach einen Verweis auf das Objekt selbst zurück.

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section::scoped_lock Klasse

Ein ausnahmesicherer RAII-Wrapper für ein `critical_section` Objekt.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock

Erstellt ein `scoped_lock` Objekt und `critical_section` ruft das `_Critical_section` im Parameter übergebene Objekt ab. Wenn der kritische Abschnitt von einem anderen Thread gehalten wird, wird dieser Aufruf blockiert.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parameter

*_Critical_section*<br/>
Der zu sperrende kritische Abschnitt.

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock::scoped_lock

Zerstört ein `scoped_lock` Objekt und gibt den kritischen Abschnitt frei, der in seinem Konstruktor angegeben ist.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>Try_lock

Versucht, die Sperre ohne Blockierung zu erwerben.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Sperre erworben wurde, **true**der Wert; Andernfalls wird der Wert **false**.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Versucht, die Sperre zu erhalten, ohne für eine bestimmte Anzahl von Millisekunden zu blockieren.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parameter

*_Timeout*<br/>
Die Anzahl der Millisekunden, die vor dem Timeout gewartet werden soll.

### <a name="return-value"></a>Rückgabewert

Wenn die Sperre erworben wurde, **true**der Wert; Andernfalls wird der Wert **false**.

## <a name="unlock"></a><a name="unlock"></a>Entsperren

Schaltet den kritischen Abschnitt frei.

```cpp
void unlock();
```

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[reader_writer_lock-Klasse](reader-writer-lock-class.md)
