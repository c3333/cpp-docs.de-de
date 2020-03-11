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
ms.openlocfilehash: 1a7386e527b5327d928bfdcb3281c88666f1b106
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867163"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock-Klasse

Eine im Writer festgelegte, warteschlangenbasierte Lese-/Schreibsperre mit ausschließlich lokalem Spinning. Die Sperre gewährt "First In, First Out"-Zugriff (FIFO-Zugriff) auf Writer und blockiert Reader unter einer fortlaufenden Last von Writern.

## <a name="syntax"></a>Syntax

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Members

### <a name="public-classes"></a>Öffentliche Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[reader_writer_lock:: scoped_lock-Klasse](#scoped_lock_class)|Ein Ausnahme sicherer RAII-Wrapper, der zum Abrufen `reader_writer_lock` Sperrobjekte als Writer verwendet werden kann.|
|[reader_writer_lock:: scoped_lock_read-Klasse](#scoped_lock_read_class)|Ein Ausnahme sicherer RAII-Wrapper, der zum Abrufen `reader_writer_lock` Sperrobjekte als Reader verwendet werden kann.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Erstellt ein neues `reader_writer_lock`-Objekt.|
|[~ reader_writer_lock-Dekonstruktor](#dtor)|Zerstört das `reader_writer_lock`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[lock](#lock)|Erhält die Reader-Writer-Sperre als Writer.|
|[lock_read](#lock_read)|Erhält die Reader-Writer-Sperre als Reader. Wenn Writer vorhanden sind, müssen aktive Leser warten, bis Sie abgeschlossen sind. Der Reader registriert lediglich ein Interesse an der Sperre und wartet darauf, dass Writer ihn freigeben.|
|[try_lock](#try_lock)|Versucht, die Reader-Writer-Sperre als Writer zu erhalten, ohne zu blockieren.|
|[try_lock_read](#try_lock_read)|Versucht, die Reader-Writer-Sperre als Reader zu erhalten, ohne zu blockieren.|
|[unlock](#unlock)|Entsperrt die Lese-/Schreibsperre basierend darauf, wer Sie gesperrt hat, Reader oder Writer.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Synchronisierungs Datenstrukturen](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`reader_writer_lock`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="lock"></a>Sperre

Erhält die Reader-Writer-Sperre als Writer.

```cpp
void lock();
```

### <a name="remarks"></a>Bemerkungen

Es ist oft sicherer, das [scoped_lock](#scoped_lock_class) Konstrukt zu verwenden, um ein `reader_writer_lock` Objekt als Writer auf sichere Weise zu erhalten und freizugeben.

Nachdem ein Writer versucht hat, die Sperre abzurufen, werden zukünftige Leser blockiert, bis die Writer die Sperre erfolgreich abgerufen und freigegeben haben. Diese Sperre ist auf Writer ausgerichtet und kann Leser bei einem kontinuierlichen Ladevorgang von Writern verhungern.

Writer werden verkettet, sodass ein Writer, der die Sperre verlässt, den nächsten Writer in der Zeile freigibt.

Wenn die Sperre bereits vom aufrufenden Kontext abgehalten wird, wird eine [Improper_lock](improper-lock-class.md) Ausnahme ausgelöst.

## <a name="lock_read"></a>lock_read

Erhält die Reader-Writer-Sperre als Reader. Wenn Writer vorhanden sind, müssen aktive Leser warten, bis Sie abgeschlossen sind. Der Reader registriert lediglich ein Interesse an der Sperre und wartet darauf, dass Writer ihn freigeben.

```cpp
void lock_read();
```

### <a name="remarks"></a>Bemerkungen

Es ist oft sicherer, das [scoped_lock_read](#scoped_lock_read_class) Konstrukt zu verwenden, um ein `reader_writer_lock` Objekt als Leser auf sichere Weise abzurufen und freizugeben.

Wenn Writer auf die Sperre warten, wartet der Reader, bis alle Writer in der Zeile die Sperre abgerufen und freigegeben haben. Diese Sperre ist auf Writer ausgerichtet und kann Leser bei einem kontinuierlichen Ladevorgang von Writern verhungern.

## <a name="ctor"></a>reader_writer_lock

Erstellt ein neues `reader_writer_lock`-Objekt.

```cpp
reader_writer_lock();
```

## <a name="dtor"></a>~ reader_writer_lock

Zerstört das `reader_writer_lock`-Objekt.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Bemerkungen

Es wird erwartet, dass die Sperre nicht mehr aufrechterhalten wird, wenn der Dekonstruktor ausgeführt wird. Das zulassen, dass die Sperre des Lese-Writer mit der Sperre weiterhin besteht, führt zu nicht definiertem Verhalten.

## <a name="scoped_lock_class"></a>reader_writer_lock:: scoped_lock-Klasse

Ein Ausnahme sicherer RAII-Wrapper, der zum Abrufen `reader_writer_lock` Sperrobjekte als Writer verwendet werden kann.

```cpp
class scoped_lock;
```

## <a name="scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Erstellt ein `scoped_lock` Objekt und ruft das `reader_writer_lock` Objekt ab, das als Writer im `_Reader_writer_lock`-Parameter übergeben wird. Wenn die Sperre von einem anderen Thread aufrechterhalten wird, wird dieser-Befehl blockiert.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parameter

*_Reader_writer_lock*<br/>
Das `reader_writer_lock` Objekt, das als Writer abgerufen werden soll.

## <a name="scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Zerstört ein `reader_writer_lock` Objekt und gibt die im Konstruktor angegebene Sperre frei.

```cpp
~scoped_lock();
```

## <a name="scoped_lock_read_class"></a>reader_writer_lock:: scoped_lock_read-Klasse

Ein Ausnahme sicherer RAII-Wrapper, der zum Abrufen `reader_writer_lock` Sperrobjekte als Reader verwendet werden kann.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_read_ctor"></a>scoped_lock_read:: scoped_lock_read

Erstellt ein `scoped_lock_read` Objekt und ruft das `reader_writer_lock` Objekt ab, das im `_Reader_writer_lock`-Parameter als Reader übergeben wird. Wenn die Sperre von einem anderen Thread als Writer gehalten wird oder ausstehende Writer vorhanden sind, wird dieser-Befehl blockiert.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parameter

*_Reader_writer_lock*<br/>
Das `reader_writer_lock` Objekt, das als Reader abgerufen werden soll.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor"> reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read Dekonstruktor

Zerstört ein `scoped_lock_read` Objekt und gibt die im Konstruktor angegebene Sperre frei.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a>try_lock

Versucht, die Reader-Writer-Sperre als Writer zu erhalten, ohne zu blockieren.

### <a name="syntax"></a>Syntax

```cpp
bool try_lock();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Sperre abgerufen wurde, ist der Wert **true**. Andernfalls ist der Wert **false**.

## <a name="try_lock_read"></a>try_lock_read

Versucht, die Reader-Writer-Sperre als Reader zu erhalten, ohne zu blockieren.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Rückgabewert

Wenn die Sperre abgerufen wurde, ist der Wert **true**. Andernfalls ist der Wert **false**.

## <a name="unlock"></a>Entsperren

Entsperrt die Lese-/Schreibsperre basierend darauf, wer Sie gesperrt hat, Reader oder Writer.

```cpp
void unlock();
```

### <a name="remarks"></a>Bemerkungen

Wenn Writer auf die Sperre warten, wird die Freigabe der Sperre immer an den nächsten Writer in der FIFO-Reihenfolge weitergeleitet. Diese Sperre ist auf Writer ausgerichtet und kann Leser bei einem kontinuierlichen Ladevorgang von Writern verhungern.

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[critical_section-Klasse](critical-section-class.md)
