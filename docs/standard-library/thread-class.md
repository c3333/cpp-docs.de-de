---
title: thread-Klasse
ms.date: 11/04/2016
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
helpviewer_keywords:
- std::thread [C++]
- std::thread [C++], thread
- std::thread [C++], detach
- std::thread [C++], get_id
- std::thread [C++], hardware_concurrency
- std::thread [C++], join
- std::thread [C++], joinable
- std::thread [C++], native_handle
- std::thread [C++], swap
ms.openlocfilehash: 19f7ae1fc95f531f509273f0eb9998c73fe7d47b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215581"
---
# <a name="thread-class"></a>thread-Klasse

Definiert ein Objekt, das zum Überwachen und Verwalten eines Ausführungsthreads innerhalb einer Anwendung verwendet wird.

## <a name="syntax"></a>Syntax

```cpp
class thread;
```

## <a name="remarks"></a>Bemerkungen

Sie können ein `thread`-Objekt zum Überwachen und Verwalten eines Ausführungsthreads innerhalb einer Anwendung verwenden. Ein Threadobjekt, das mithilfe eines Standardkonstruktors erstellt wird, ist keinem Ausführungsthread zugeordnet. Mit einem Threadobjekt, das mithilfe eines aufrufbaren Objekts erstellt wird, wird ein neuer Ausführungsthread erstellt, und das aufrufbare Objekt in diesem Thread wird aufgerufen. Threadobjekte können verschoben aber nicht kopiert werden. Daher kann ein Ausführungsthread nur einem Threadobjekt zugeordnet werden.

Jeder Ausführungsthread besitzt einen eindeutigen Bezeichner des Typs `thread::id`. Die `this_thread::get_id`-Funktion gibt den Bezeichner des aufrufenden Threads zurück. Die `thread::get_id`-Memberfunktion gibt den Bezeichner des von einem Threadobjekt verwalteten Threads zurück. Ein nach Standard erstelltes Threadobjekt gibt die `thread::get_id`-Methode ein Objekt zurück, das über einen Wert verfügt, der für alle nach Standard erstellten Threadobjekte gleich ist und sich von dem von `this_thread::get_id` zurückgegebenen Wert für jeden Ausführungsthread, der zum Zeitpunkt des Aufrufs verknüpft werden kann, unterschiedet.

## <a name="members"></a>Member

### <a name="public-classes"></a>Öffentliche Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[thread::id-Klasse](#id_class)|Identifiziert den zugeordneten Thread eindeutig.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Thread](#thread)|Erstellt ein `thread`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Trennen](#detach)|Trennt den zugeordneten Thread vom `thread`-Objekt.|
|[get_id](#get_id)|Gibt den eindeutigen Bezeichner des zugeordneten Threads zurück.|
|[hardware_concurrency](#hardware_concurrency)|Statisch. Gibt eine Schätzung der Anzahl von Hardwarethreadkontexten zurück.|
|[join](#join)|Blockiert, bis der zugeordnete Thread abgeschlossen ist.|
|[beigetreten](#joinable)|Gibt an, ob dem zugehörigen Thread beigetreten werden kann.|
|[native_handle](#native_handle)|Gibt den implementierungsspezifischen Typ zurück, der das Threadhandle darstellt.|
|[swap](#swap)|Tauscht den Objektzustand mit einem angegebenen `thread`-Objekt aus.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Thread:: Operator =](#op_eq)|Weist einem Thread das aktuelle `thread`-Objekt zu.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<thread>

**Namespace:** std

## <a name="threaddetach"></a><a name="detach"></a>Thread::d Etach

Trennt den zugeordneten Thread. Das Betriebssystem wird zum Freigeben von Threadressourcen zuständig.

```cpp
void detach();
```

### <a name="remarks"></a>Bemerkungen

Nach einem Aufruf von `detach` geben nachfolgende Aufrufe von [Get_id](#get_id)[id](#id_class) zurück.

Wenn der Thread, der dem aufrufenden Objekt zugeordnet ist, nicht beitreten kann, löst die Funktion einen [system_error](../standard-library/system-error-class.md)-Fehler mit Fehlercode `invalid_argument` aus.

Wenn der Thread, der dem aufrufenden Objekt zugeordnet ist, ungültig ist, löst die Funktion einen `system_error` mit Fehlercode `no_such_process` aus.

## <a name="threadget_id"></a><a name="get_id"></a>Thread:: get_id

Gibt den eindeutigen Bezeichner für den zugeordneten Threads zurück.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein [thread::id](#id_class)-Objekt, das den zugeordneten Thread eindeutig ausweist, oder `thread::id()`, wenn kein Thread dem Objekt zugeordnet ist.

## <a name="threadhardware_concurrency"></a><a name="hardware_concurrency"></a>Thread:: hardware_concurrency

Statische Methode, diet eine Schätzung der Anzahl von Hardwarethreadkontexten zurückgibt.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Rückgabewert

Eine Schätzung der Anzahl von Hardwarethreadkontexten. Wenn der Wert nicht berechnet werden kann oder nicht klar definiert ist, gibt diese Methode 0 zurück.

## <a name="threadid-class"></a><a name="id_class"></a>Thread:: ID-Klasse

Stellt einen eindeutigen Bezeichner für jeden Thread der Ausführung im Prozess bereit.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor erstellt ein Objekt, das nicht gleich dem `thread::id`-Objekt für die vorhandenen Threads ist.

Alle mit dem Standwert konstruierten `thread::id`-Objekte gelten als gleich.

## <a name="threadjoin"></a><a name="join"></a>Thread:: Join

Blockiert, bis der Thread der Ausführung, der das aufrufende Objekt zugeordnet wurde, abgeschlossen ist.

```cpp
void join();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Aufruf erfolgreich ist, geben nachfolgende Aufrufe von [get_id](#get_id) für das aufrufende Objekt eine Standard-[Thread:: ID](#id_class) zurück, die nicht gleich `thread::id` eines beliebigen vorhandenen Threads ist. Wenn der Aufruf nicht erfolgreich ist, ist der Wert, der von `get_id` zurückgegeben wird, unverändert.

## <a name="threadjoinable"></a><a name="joinable"></a>Thread:: joinable

Gibt an, ob der zugeordnete Thread verknüpft werden *kann*.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der zugeordnete Thread verknüpft werden *kann*. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Einem Thread-Objekt kann *beigetreten* werden, wenn `get_id() != id()`.

## <a name="threadnative_handle"></a><a name="native_handle"></a>Thread:: native_handle

Gibt den implementierungsspezifischen Typ zurück, der das Threadhandle darstellt. Das Threadhandle kann je nach Implementierung auf die jeweils entsprechende Weise verwendet werden.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Rückgabewert

`native_handle_type` ist als Win32-`HANDLE` definiert, das als `void *` umgewandelt wird.

## <a name="threadoperator"></a><a name="op_eq"></a>Thread:: Operator =

Ordnet den Thread für das angegebene Objekt dem aktuellen Objekt zu.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*Außer*\
Ein `thread`-Objekt.

### <a name="return-value"></a>Rückgabewert

`*this`

### <a name="remarks"></a>Bemerkungen

Die Methodenaufrufe trennen, wenn dem aufrufenden Objekt beigetreten werden kann.

Nach dem Erstellen die Zuordnung wird `Other` auf einen standardmäßig konstruierten Zustand festgelegt.

## <a name="threadswap"></a><a name="swap"></a>Thread:: Swap

Tauscht den Objektzustand mit dem eines angegebenen `thread`-Objekts aus.

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*Außer*\
Ein `thread`-Objekt.

## <a name="threadthread-constructor"></a><a name="thread"></a>Thread:: Thread-Konstruktor

Erstellt ein `thread`-Objekt.

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parameter

*C*\
Eine anwendungsdefinierte Funktion, die vom Thread ausgeführt werden soll.

*Ein*\
Eine Liste von Argumenten, die an *F*übermittelt werden sollen.

*Außer*\
Ein vorhandenes `thread`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt ein Objekt, das nicht einem Thread der Ausführung zugeordnet ist. Der Wert, der durch einen Aufruf von `get_id` für das erstellte Objekt zurückgegeben wird, ist `thread::id()`.

Mit dem zweiten Konstruktor wird ein Objekt erstellt, das einem neuen Ausführungs Thread zugeordnet ist, und die in definierte Pseudo Funktion wird ausgeführt `INVOKE` [\<functional>](../standard-library/functional.md) . Wenn nicht genügend Ressourcen zum Starten eines neuen Threads verfügbar sind, löst die Funktion ein [system_error](../standard-library/system-error-class.md)-Objekt mit dem Fehlercode `resource_unavailable_try_again` aus. Wenn der Aufruf von *F* mit einer nicht abgefangenen Ausnahme beendet wird, wird [Beenden](../standard-library/exception-functions.md#terminate) aufgerufen.

Der dritte Konstruktor erstellt ein Objekt, das mit dem Thread verknüpft ist, der `Other` zugeordnet ist. `Other` wird dann auf einen standardmäßig konstruierten Zustand festgelegt.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<thread>](../standard-library/thread.md)
