---
title: event-Klasse
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 3f2ec71083f7a7905bad5cda014baba914e31e79
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215802"
---
# <a name="event-class"></a>event-Klasse

Ein Ereignis für manuelles Zurücksetzen, das explizit die Concurrency Runtime beachtet.

## <a name="syntax"></a>Syntax

```cpp
class event;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[~ ereignisdekonstruktor](#dtor)|Zerstört ein Ereignis.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[reset](#reset)|Setzt das Ereignis auf einen nicht signalisierten Zustand zurück.|
|[set](#set)|Signalisiert das Ereignis.|
|[Warte](#wait)|Wartet, bis das Ereignis signalisiert wird.|
|[wait_for_multiple](#wait_for_multiple)|Wartet, bis mehrere Ereignisse signalisiert werden.|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|Ein Wert, der angibt, dass ein Wartevorgang nie durch einen Timeout beendet werden sollte.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Synchronisierungs Datenstrukturen](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`event`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

**Namespace:** Parallelität

## <a name="event"></a><a name="ctor"></a> -Ereignis

Erstellt ein neues Ereignis.

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>Bemerkungen

## <a name="event"></a><a name="dtor"></a>~-Ereignis

Zerstört ein Ereignis.

```cpp
~event();
```

### <a name="remarks"></a>Bemerkungen

Es wird erwartet, dass keine Threads auf das Ereignis warten, wenn der Destruktor ausgeführt wird. Wenn das Ereignis zerstört wird, während Threads auf das Ereignis warten, kann dies zu einem nicht definiertem Verhalten führen.

## <a name="reset"></a><a name="reset"></a>Festlegen

Setzt das Ereignis auf einen nicht signalisierten Zustand zurück.

```cpp
void reset();
```

## <a name="set"></a><a name="set"></a>Set

Signalisiert das Ereignis.

```cpp
void set();
```

### <a name="remarks"></a>Bemerkungen

Das Signalisieren des Ereignisses kann möglicherweise dazu führen, dass eine beliebige Anzahl von Kontexten, die auf das Ereignis warten, ausführbar werden.

## <a name="timeout_infinite"></a><a name="timeout_infinite"></a>timeout_infinite

Ein Wert, der angibt, dass ein Wartevorgang nie durch einen Timeout beendet werden sollte.

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a><a name="wait"></a>Warte

Wartet, bis das Ereignis signalisiert wird.

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parameter

*_Timeout*<br/>
Gibt die Anzahl von Millisekunden vor dem Timeout an. Der Wert `COOPERATIVE_TIMEOUT_INFINITE` gibt an, dass kein Timeout vorliegt.

### <a name="return-value"></a>Rückgabewert

Wenn der Wartezustand erfüllt wurde, wird der Wert `0` zurückgegeben. Andernfalls gibt der Wert `COOPERATIVE_WAIT_TIMEOUT` an, dass der Wartezustand durch einen Timeout beendet wurde, ohne dass das Ereignis signalisiert wurde.

> [!IMPORTANT]
> Rufen Sie in einer universelle Windows-Plattform-app (UWP) nicht `wait` im Asta-Thread auf, da dieser-Befehl den aktuellen Thread blockieren kann und dazu führen kann, dass die APP nicht mehr reagiert.

## <a name="wait_for_multiple"></a><a name="wait_for_multiple"></a>wait_for_multiple

Wartet, bis mehrere Ereignisse signalisiert werden.

```cpp
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parameter

*_PPEvents*<br/>
Ein Array von Ereignissen, auf die gewartet werden soll. Die Anzahl der Ereignisse im Array wird durch den `count`-Parameter angegeben.

*count*<br/>
Die Anzahl von Ereignissen innerhalb des im `_PPEvents`-Parameter angegebenen Arrays.

*_FWaitAll*<br/>
Wenn der Wert auf festgelegt **`true`** ist, gibt der-Parameter an, dass alle Ereignisse innerhalb des Arrays, das im-Parameter bereitgestellt wird, `_PPEvents` signalisiert werden müssen, um die Wartezeit zu erfüllen. Wenn der Wert auf festgelegt **`false`** ist, wird festgelegt, dass jedes Ereignis innerhalb des Arrays, das im-Parameter bereitgestellt wird, in dem `_PPEvents` der-Parameter signalisiert wird

*_Timeout*<br/>
Gibt die Anzahl von Millisekunden vor dem Timeout an. Der Wert `COOPERATIVE_TIMEOUT_INFINITE` gibt an, dass kein Timeout vorliegt.

### <a name="return-value"></a>Rückgabewert

Wenn die Anforderungen des Wartevorgangs erfüllt wurden, ist dies der Index innerhalb des Arrays, das im `_PPEvents`-Parameter angegeben wurde und die Wartebedingung erfüllt hat. Andernfalls gibt der Wert `COOPERATIVE_WAIT_TIMEOUT` an, dass das Timeout für den Wartevorgang abgelaufen ist, ohne dass die Bedingung erfüllt wurde.

### <a name="remarks"></a>Bemerkungen

Wenn der-Parameter `_FWaitAll` auf den-Wert festgelegt wird, **`true`** um anzugeben, dass alle Ereignisse signalisiert werden müssen, um den warte Vorgang zu erfüllen, hat der von der Funktion zurückgegebene Index keine besondere Bedeutung, außer der Tatsache, dass es sich nicht um den Wert handelt `COOPERATIVE_WAIT_TIMEOUT` .

> [!IMPORTANT]
> Rufen Sie in einer universelle Windows-Plattform-app (UWP) nicht `wait_for_multiple` im Asta-Thread auf, da dieser-Befehl den aktuellen Thread blockieren kann und dazu führen kann, dass die APP nicht mehr reagiert.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)
