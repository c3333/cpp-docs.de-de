---
title: IUMSScheduler-Struktur
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 70954906122c048e5199a801632626d35a8e3f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368093"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler-Struktur

Eine Schnittstelle zu der Abstraktion eines Arbeitsplaners, der planbare Threads vom Ressourcen-Manager der Concurrency Runtime im Benutzermodus erwartet. Der Ressourcen-Manager verwendet diese Schnittstelle für die Kommunikation mit UMS-Threadplanern. Die `IUMSScheduler` -Schnittstelle erbt von der `IScheduler` -Schnittstelle.

## <a name="syntax"></a>Syntax

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Weist einem `IUMSCompletionList` UMS-Threadplaner eine Schnittstelle zu.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie einen benutzerdefinierten Planer implementieren, der mit dem Ressourcen-Manager kommuniziert, und Sie möchten, dass UMS-Threads anstelle gewöhnlicher Win32-Threads an Ihren Planer übergeben werden, sollten Sie eine Implementierung der `IUMSScheduler` Schnittstelle bereitstellen. Darüber hinaus sollten Sie den Richtlinienwert für `SchedulerKind` den `UmsThreadDefault`Planerrichtlinienschlüssel als festlegen. Wenn die Richtlinie umS-Thread `IScheduler` angibt, muss die Schnittstelle, die als Parameter an die `IUMSScheduler` [IResourceManager::RegisterScheduler-Methode](iresourcemanager-structure.md#registerscheduler) übergeben wird, eine Schnittstelle sein.

Der Ressourcen-Manager kann Ihnen UMS-Threads nur auf Betriebssystemen mit der UMS-Funktion übergeben. 64-Bit-Betriebssysteme mit Version Windows 7 und höher unterstützen UMS-Threads. Wenn Sie eine Planerrichtlinie `SchedulerKind` mit dem Schlüssel `UmsThreadDefault` erstellen, der auf den Wert festgelegt `SchedulerKind` ist, und die zugrunde liegende `ThreadScheduler`Plattform UMS nicht unterstützt, wird der Wert des Schlüssels in dieser Richtlinie in den Wert geändert. Sie sollten diesen Richtlinienwert immer zurücklesen, bevor Sie erwarten, UMS-Threads zu erhalten.

Die `IUMSScheduler` Schnittstelle ist ein Ende eines zweiseitigen Kommunikationskanals zwischen einem Planer und dem Ressourcen-Manager. Das andere Ende wird `IResourceManager` `ISchedulerProxy` durch die und Schnittstellen dargestellt, die vom Ressourcen-Manager implementiert werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Ischeduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a>IUMSScheduler::SetCompletionList-Methode

Weist einem `IUMSCompletionList` UMS-Threadplaner eine Schnittstelle zu.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parameter

*pCompletionList*<br/>
Die Abschlusslistenschnittstelle für den Planer. Es gibt eine einzelne Liste pro Scheduler.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager ruft diese Methode auf einem Planer auf, der angibt, dass umS-Threads gewünscht werden sollen, nachdem der Planer eine anfängliche Zuweisung von Ressourcen angefordert hat. Der Planer kann `IUMSCompletionList` die Schnittstelle verwenden, um zu bestimmen, wann UMS-Threadproxys die Blockblockierten aufgehoben haben. Es ist nur gültig, über einen Threadproxy, der auf einem virtuellen Prozessorstamm ausgeführt wird, der dem UMS-Planer zugewiesen ist, auf diese Schnittstelle zuzugreifen.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler-Struktur](ischeduler-structure.md)<br/>
[IUMSCompletionList-Struktur](iumscompletionlist-structure.md)<br/>
[IResourceManager-Struktur](iresourcemanager-structure.md)
