---
title: reader_writer_lock-Klasse
ms.date: 11/04/2016
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 13b44387f3e9489090ec31345fe4347ff5f205ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376242"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock-Klasse

Eine im Writer festgelegte, warteschlangenbasierte Lese-/Schreibsperre mit ausschließlich lokalem Spinning. Die Sperre gewährt "First In, First Out"-Zugriff (FIFO-Zugriff) auf Writer und blockiert Reader unter einer fortlaufenden Last von Writern.

## <a name="syntax"></a>Syntax

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Member

### <a name="public-classes"></a>Öffentliche Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[reader_writer_lock::scoped_lock-Klasse](#scoped_lock_class)|Ein ausnahmesicherer RAII-Wrapper, der `reader_writer_lock` zum Abrufen von Sperrobjekten als Writer verwendet werden kann.|
|[reader_writer_lock::scoped_lock_read-Klasse](#scoped_lock_read_class)|Ein ausnahmesicherer RAII-Wrapper, der `reader_writer_lock` zum Abrufen von Sperrobjekten als Reader verwendet werden kann.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Erstellt ein neues `reader_writer_lock`-Objekt.|
|[Reader_writer_lock Destruktor](#dtor)|Zerstört das `reader_writer_lock`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Sperren](#lock)|Erwirbt die Leser-Schreiber-Sperre als Autor.|
|[lock_read](#lock_read)|Erwirbt die Reader-Writer-Sperre als Leser. Wenn es Autoren gibt, müssen aktive Leser warten, bis sie fertig sind. Der Leser registriert einfach ein Interesse an der Sperre und wartet darauf, dass Autoren sie freigeben.|
|[try_lock](#try_lock)|Versucht, die Reader-Writer-Sperre als Writer ohne Blockierung zu erwerben.|
|[try_lock_read](#try_lock_read)|Versucht, die Reader-Writer-Sperre als Reader ohne Blockierung zu erwerben.|
|[Entsperren](#unlock)|Entsperrt die Reader-Writer-Sperre basierend darauf, wer sie gesperrt, leser- oder writer-gesperrt hat.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Synchronisierungsdatenstrukturen](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`reader_writer_lock`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

**Namespace:** Parallelität

## <a name="lock"></a><a name="lock"></a>Sperren

Erwirbt die Leser-Schreiber-Sperre als Autor.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Es ist oft sicherer, das [scoped_lock-Konstrukt](#scoped_lock_class) zu nutzen, um ein `reader_writer_lock` Objekt als Writer auf eine Ausnahmesichere Weise zu erwerben und freizugeben.

Nachdem ein Writer versucht, die Sperre zu erwerben, werden alle zukünftigen Leser blockieren, bis die Autoren die Sperre erfolgreich erworben und freigegeben haben. Diese Sperre ist voreingenommen gegenüber Schriftstellern und kann Leser unter einer kontinuierlichen Last von Schriftstellern verhungern lassen.

Writer sind so angekettet, dass ein Writer, der die Sperre verlässt, den nächsten Schreiber in der Zeile freigibt.

Wenn die Sperre bereits vom aufrufenden Kontext gehalten wird, wird eine [improper_lock](improper-lock-class.md) Ausnahme ausgelöst.

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

Erwirbt die Reader-Writer-Sperre als Leser. Wenn es Autoren gibt, müssen aktive Leser warten, bis sie fertig sind. Der Leser registriert einfach ein Interesse an der Sperre und wartet darauf, dass Autoren sie freigeben.

```cpp
void lock_read();
```

### <a name="remarks"></a>Bemerkungen

Es ist oft sicherer, das [scoped_lock_read-Konstrukt](#scoped_lock_read_class) zu nutzen, um ein `reader_writer_lock` Objekt als Lesegerät auf eine Ausnahmesichere Weise zu erwerben und freizugeben.

Wenn Autoren auf die Sperre warten, wartet der Leser, bis alle Schreiber in der Zeile die Sperre erworben und freigegeben haben. Diese Sperre ist voreingenommen gegenüber Schriftstellern und kann Leser unter einer kontinuierlichen Last von Schriftstellern verhungern lassen.

## <a name="reader_writer_lock"></a><a name="ctor"></a>Reader_writer_lock

Erstellt ein neues `reader_writer_lock`-Objekt.

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>€reader_writer_lock

Zerstört das `reader_writer_lock`-Objekt.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Bemerkungen

Es wird erwartet, dass die Sperre nicht mehr gehalten wird, wenn der Destruktor ausgeführt wird. Wenn Sie zulassen, dass die Readerwritersperre mit der noch gehaltenen Sperre zerstört wird, führt dies zu einem undefinierten Verhalten.

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>reader_writer_lock::scoped_lock Klasse

Ein ausnahmesicherer RAII-Wrapper, der `reader_writer_lock` zum Abrufen von Sperrobjekten als Writer verwendet werden kann.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock::scoped_lock

Erstellt ein `scoped_lock` Objekt und `reader_writer_lock` ruft das `_Reader_writer_lock` Objekt ab, das im Parameter als Writer übergeben wird. Wenn die Sperre von einem anderen Thread gehalten wird, wird dieser Aufruf blockiert.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parameter

*_Reader_writer_lock*<br/>
Das `reader_writer_lock` Objekt, das als Writer erworben werden soll.

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock::scoped_lock

Zerstört ein `reader_writer_lock` Objekt und gibt die in seinem Konstruktor angegebene Sperre frei.

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>reader_writer_lock::scoped_lock_read Klasse

Ein ausnahmesicherer RAII-Wrapper, der `reader_writer_lock` zum Abrufen von Sperrobjekten als Reader verwendet werden kann.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read::scoped_lock_read

Erstellt ein `scoped_lock_read` Objekt und `reader_writer_lock` ruft das `_Reader_writer_lock` im Parameter übergebene Objekt als Reader ab. Wenn die Sperre von einem anderen Thread als Writer gehalten wird oder ausstehende Writer vorhanden sind, wird dieser Aufruf blockiert.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parameter

*_Reader_writer_lock*<br/>
Das `reader_writer_lock` Objekt, das als Leser erworben werden soll.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock::scoped_lock_read::scoped_lock_read Destruktor

Zerstört ein `scoped_lock_read` Objekt und gibt die in seinem Konstruktor angegebene Sperre frei.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>Try_lock

Versucht, die Reader-Writer-Sperre als Writer ohne Blockierung zu erwerben.

### <a name="syntax"></a>Syntax

```cpp
bool try_lock();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Sperre erworben wurde, **true**der Wert; Andernfalls wird der Wert **false**.

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

Versucht, die Reader-Writer-Sperre als Reader ohne Blockierung zu erwerben.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Sperre erworben wurde, **true**der Wert; Andernfalls wird der Wert **false**.

## <a name="unlock"></a><a name="unlock"></a>Entsperren

Entsperrt die Reader-Writer-Sperre basierend darauf, wer sie gesperrt, leser- oder writer-gesperrt hat.

```cpp
void unlock();
```

### <a name="remarks"></a>Bemerkungen

Wenn Autoren auf die Sperre warten, wird die Freigabe der Sperre immer an den nächsten Writer in FIFO-Reihenfolge gehen. Diese Sperre ist voreingenommen gegenüber Schriftstellern und kann Leser unter einer kontinuierlichen Last von Schriftstellern verhungern lassen.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[critical_section-Klasse](critical-section-class.md)
