---
title: tile_barrier-Klasse
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: 757309a10da3e6d1c9c053430cce2cf603380b1f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855915"
---
# <a name="tile_barrier-class"></a>tile_barrier-Klasse

Synchronisiert die Ausführung von Threads, die in der Threadgruppe (die Kachel) mit `wait`-Methoden ausgeführt werden. Nur die Laufzeit kann diese Klasse instanziieren.

## <a name="syntax"></a>Syntax

```cpp
class tile_barrier;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[tile_barrier-Konstruktor](#ctor)|Initialisiert eine neue Instanz der Klasse `tile_barrier`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Warte](#wait)|Weist alle Threads in der Threadgruppe (Kachel) an, die Ausführung zu beenden, bis alle Threads in der Kachel den Wartevorgang beendet haben.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Blockiert die Ausführung aller Threads in einer Kachel, bis alle Speicherzugriffe abgeschlossen sind und alle Threads in der Kachel diesen Aufruf erreicht haben.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Blockiert die Ausführung aller Threads in einer Kachel, bis alle globalen Speicherzugriffe abgeschlossen sind und alle Threads in der Kachel diesen Aufruf erreicht haben.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Blockiert die Ausführung aller Threads in einer Kachel, bis alle `tile_static`-Speicherzugriffe abgeschlossen sind und alle Threads in der Kachel diesen Aufruf erreicht haben.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tile_barrier`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amp.h

**Namespace:** Parallelität

## <a name="ctor"></a>tile_barrier-Konstruktor

Initialisiert eine neue Instanz der-Klasse, indem ein vorhandenes kopiert wird.

### <a name="syntax"></a>Syntax

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das zu kopierende `tile_barrier`-Objekt.

## <a name="wait"></a>wait

Weist alle Threads in der Thread Gruppe (Kachel) an, die Ausführung zu beenden, bis alle Threads in der Kachel gewartet haben.

### <a name="syntax"></a>Syntax

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Blockiert die Ausführung aller Threads in einer Kachel, bis alle Threads in einer Kachel diesen Aufruf erreicht haben. Dadurch wird sichergestellt, dass alle Speicherzugriffe für andere Threads in der Threadkachel sichtbar sind und in der Programmreihenfolge ausgeführt wurden.

### <a name="syntax"></a>Syntax

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

Blockiert die Ausführung aller Threads in einer Kachel, bis alle Threads in einer Kachel diesen Aufruf erreicht haben. Dadurch wird sichergestellt, dass alle globalen Speicherzugriffe für andere Threads in der Threadkachel sichtbar sind und in der Programmreihenfolge ausgeführt wurden.

### <a name="syntax"></a>Syntax

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

Blockiert die Ausführung aller Threads in einer Kachel, bis alle Threads in einer Kachel diesen Aufruf erreicht haben. Dadurch wird sichergestellt, dass `tile_static` Speicherzugriffe für andere Threads in der Thread Kachel sichtbar sind und in der Programm Reihenfolge ausgeführt wurden.

### <a name="syntax"></a>Syntax

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace (C++ AMP)](concurrency-namespace-cpp-amp.md)
