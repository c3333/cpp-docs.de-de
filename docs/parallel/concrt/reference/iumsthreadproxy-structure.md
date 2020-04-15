---
title: IUMSThreadProxy-Struktur
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: 2e748b1da02394e1f70afd8b92947e1291957c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368085"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy-Struktur

Eine Abstraktion für einen Thread der Ausführung. Wenn dem Planer im Benutzermodus planbare (UMS) Threads gewährt werden sollen, legen Sie den Wert für das Planerrichtlinienelement `SchedulerKind` auf `UmsThreadDefault` fest, und implementieren Sie die `IUMSScheduler`-Schnittstelle. UMS-Threads werden nur unter 64-Bit-Betriebssystemen mit Version Windows 7 und höher unterstützt.

## <a name="syntax"></a>Syntax

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Wird aufgerufen, um in einen kritischen Bereich einzutreten. Wenn sich der Planer innerhalb eines kritischen Bereichs befindet, beachtet er keine asynchronen Blockierungsvorgänge, die während der Region auftreten. Dies bedeutet, dass der Scheduler nicht für Seitenfehler, Thread-Suspensionen, Kernel-asynchrone Prozeduraufrufe (APCs) usw. für einen UMS-Thread erneut eingegeben wird.|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Wird aufgerufen, um in eine hyperkritische Region einzutreten. Wenn sich der Planer in einer hyperkritischen Region befindet, beobachtet er keine Blockierungsvorgänge, die während der Region stattfinden. Dies bedeutet, dass der Scheduler nicht erneut für das Blockieren von Funktionsaufrufen, Sperrerfassungsversuche, die blockieren, Seitenfehler, Thread-Suspensionen, Kernel asynchrone Prozeduraufrufe (APCs) usw. für einen UMS-Thread eingegeben werden.|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Wird aufgerufen, um eine kritische Region zu verlassen.|
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|Wird aufgerufen, um eine hyperkritische Region zu verlassen.|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Gibt zurück, in welchem kritischen Bereich sich der Threadproxy befindet. Da hyperkritische Regionen eine Übermenge kritischer Regionen sind, wird zurückgegeben, `InsideHyperCriticalRegion` wenn Code in eine kritische Region und dann in eine hyperkritische Region eingegeben wurde.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Ithreadproxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>IUMSThreadProxy::EnterCriticalRegion-Methode

Wird aufgerufen, um in einen kritischen Bereich einzutreten. Wenn sich der Planer innerhalb eines kritischen Bereichs befindet, beachtet er keine asynchronen Blockierungsvorgänge, die während der Region auftreten. Dies bedeutet, dass der Scheduler nicht für Seitenfehler, Thread-Suspensionen, Kernel-asynchrone Prozeduraufrufe (APCs) usw. für einen UMS-Thread erneut eingegeben wird.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die neue Tiefe der kritischen Region. Kritische Regionen treten wieder auf.

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>IUMSThreadProxy::EnterHyperCriticalRegion-Methode

Wird aufgerufen, um in eine hyperkritische Region einzutreten. Wenn sich der Planer in einer hyperkritischen Region befindet, beobachtet er keine Blockierungsvorgänge, die während der Region stattfinden. Dies bedeutet, dass der Scheduler nicht erneut für das Blockieren von Funktionsaufrufen, Sperrerfassungsversuche, die blockieren, Seitenfehler, Thread-Suspensionen, Kernel asynchrone Prozeduraufrufe (APCs) usw. für einen UMS-Thread eingegeben werden.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die neue Tiefe der hyperkritischen Region. Hyperkritische Regionen treten wieder auf.

### <a name="remarks"></a>Bemerkungen

Der Planer muss außerordentlich vorsichtig sein, welche Methoden er nennt und welche Sperren er in solchen Regionen erwirbt. Wenn Code in einer solchen Region auf einer Sperre blockiert, die von etwas gehalten wird, das der Planer für die Planung verantwortlich ist, kann es zu einem Deadlock kommen.

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>IUMSThreadProxy::ExitCriticalRegion-Methode

Wird aufgerufen, um eine kritische Region zu verlassen.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die neue Tiefe der kritischen Region. Kritische Regionen treten wieder auf.

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>IUMSThreadProxy::ExitHyperCriticalRegion-Methode

Wird aufgerufen, um eine hyperkritische Region zu verlassen.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die neue Tiefe der hyperkritischen Region. Hyperkritische Regionen treten wieder auf.

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>IUMSThreadProxy::GetCriticalRegionType-Methode

Gibt zurück, in welchem kritischen Bereich sich der Threadproxy befindet. Da hyperkritische Regionen eine Übermenge kritischer Regionen sind, wird zurückgegeben, `InsideHyperCriticalRegion` wenn Code in eine kritische Region und dann in eine hyperkritische Region eingegeben wurde.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Der Typ des kritischen Bereichs, in dem sich der Threadproxy befindet.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IUMSScheduler-Struktur](iumsscheduler-structure.md)
