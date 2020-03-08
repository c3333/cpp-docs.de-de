---
title: IExecutionResource-Struktur
ms.date: 11/04/2016
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
ms.openlocfilehash: 40799d1ed6e21e6932f1adfbad117c436918b792
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854161"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource-Struktur

Eine Abstraktion für einen Hardwarethread.

## <a name="syntax"></a>Syntax

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IExecutionResource:: currentabonneptionlevel](#currentsubscriptionlevel)|Gibt die Anzahl der aktivierten virtuellen Prozessor Stämme und abonnierten externen Threads zurück, die derzeit dem zugrunde liegenden Hardware Thread zugeordnet sind, den diese Ausführungs Ressource darstellt.|
|[IExecutionResource:: GetExecutionResourceId](#getexecutionresourceid)|Gibt einen eindeutigen Bezeichner für den Hardware Thread zurück, den diese Ausführungs Ressource darstellt.|
|[IExecutionResource:: GetNodeID](#getnodeid)|Gibt einen eindeutigen Bezeichner für den Prozessor Knoten zurück, zu dem diese Ausführungs Ressource gehört.|
|[IExecutionResource:: Remove](#remove)|Gibt diese Ausführungs Ressource an den Ressourcen-Manager zurück.|

## <a name="remarks"></a>Bemerkungen

Ausführungs Ressourcen können eigenständig oder mit virtuellen Prozessor Stämmen verknüpft werden. Eine eigenständige Ausführungs Ressource wird erstellt, wenn ein Thread in der Anwendung ein Thread Abonnement erstellt. Die Methoden [ISchedulerProxy:: abonnementthread](ischedulerproxy-structure.md#subscribecurrentthread) und [ISchedulerProxy:: requestinitialvirtualprocessor](ischedulerproxy-structure.md#requestinitialvirtualprocessors) erstellen Thread Abonnements und geben eine `IExecutionResource`-Schnittstelle zurück, die das Abonnement repräsentiert. Das Erstellen eines Thread Abonnements ist eine Möglichkeit, die Ressourcen-Manager zu informieren, dass ein bestimmter Thread zusammen mit den virtuellen Prozessor Stämme, die dem Scheduler zugewiesen Ressourcen-Manager, an die Arbeit in einem Zeit Planungs Modul teilnimmt. Der Ressourcen-Manager verwendet die Informationen, um das Überschreiben von Hardwarethreads zu vermeiden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IExecutionResource`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concrtrm. h

**Namespace:** Parallelität

## <a name="currentsubscriptionlevel"></a>IExecutionResource:: currentabonneptionlevel-Methode

Gibt die Anzahl der aktivierten virtuellen Prozessor Stämme und abonnierten externen Threads zurück, die derzeit dem zugrunde liegenden Hardware Thread zugeordnet sind, den diese Ausführungs Ressource darstellt.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Abonnement Ebene.

### <a name="remarks"></a>Bemerkungen

Die Abonnement Ebene gibt Aufschluss darüber, wie viele laufende Threads dem Hardware Thread zugeordnet sind. Dies schließt nur Threads ein, die der Ressourcen-Manager in Form von abonnierten Threads kennt, und virtuelle Prozessor Stämme, die Thread Proxys aktiv ausführen.

Durch Aufrufen der [ISchedulerProxy:: abonnementthread](ischedulerproxy-structure.md#subscribecurrentthread)-Methode oder der [ISchedulerProxy:: requestinitialvirtualprocessor](ischedulerproxy-structure.md#requestinitialvirtualprocessors) -Methode, bei der der-Parameter `doSubscribeCurrentThread` auf den Wert **true** festgelegt ist, wird die Abonnement Ebene eines Hardware Threads um 1 erhöht. Sie geben auch eine `IExecutionResource`-Schnittstelle zurück, die das Abonnement darstellt. Durch einen entsprechenden Aufrufen von [IExecutionResource:: Remove](#remove) wird die Abonnement Ebene des Hardware Threads um 1 verringert.

Durch das Aktivieren eines virtuellen Prozessor Stamms mithilfe der Methode [IVirtualProcessorRoot::](ivirtualprocessorroot-structure.md#activate) Aktivierung wird die Abonnement Ebene eines Hardware Threads um 1 erhöht. Die Methoden [IVirtualProcessorRoot::D eaktivierungs](ivirtualprocessorroot-structure.md#deactivate)oder [IExecutionResource:: Remove](#remove) verringern die Abonnement Ebene um 1, wenn Sie für einen aktivierten Stamm des virtuellen Prozessors aufgerufen werden.

Der Ressourcen-Manager verwendet Informationen auf Abonnementebene als eine der Möglichkeiten, um zu bestimmen, wann Ressourcen Zwischenzeit Planungs Modulen verschoben werden.

## <a name="getexecutionresourceid"></a>IExecutionResource:: GetExecutionResourceId-Methode

Gibt einen eindeutigen Bezeichner für den Hardware Thread zurück, den diese Ausführungs Ressource darstellt.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für den Hardware Thread, der dieser Ausführungs Ressource zugrunde liegt.

### <a name="remarks"></a>Bemerkungen

Jedem Hardware Thread wird vom Concurrency Runtime ein eindeutiger Bezeichner zugewiesen. Wenn mehrere Ausführungs Ressourcen einem Hardware Thread zugeordnet sind, haben Sie alle denselben Ausführungs Ressourcen Bezeichner.

## <a name="getnodeid"></a>IExecutionResource:: GetNodeID-Methode

Gibt einen eindeutigen Bezeichner für den Prozessor Knoten zurück, zu dem diese Ausführungs Ressource gehört.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für einen Prozessor Knoten.

### <a name="remarks"></a>Bemerkungen

Der Concurrency Runtime stellt Hardwarethreads auf dem System in Gruppen von Prozessor Knoten dar. Knoten werden normalerweise von der Hardware Topologie des Systems abgeleitet. Beispielsweise können alle Prozessoren eines bestimmten Sockets oder eines bestimmten NUMA-Knotens zum gleichen Prozessor Knoten gehören. Der Ressourcen-Manager weist diesen Knoten, beginnend mit `0` bis einschließlich `nodeCount - 1`, eindeutige Bezeichner zu, wobei `nodeCount` die Gesamtzahl der Prozessor Knoten im System darstellt.

Die Anzahl der Knoten kann aus der Funktion " [getprocessornoentcount](concurrency-namespace-functions.md)" abgerufen werden.

## <a name="remove"></a>IExecutionResource:: Remove-Methode

Gibt diese Ausführungs Ressource an den Ressourcen-Manager zurück.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parameter

*pscheduler*<br/>
Eine Schnittstelle zum Scheduler, die die Anforderung zum Entfernen dieser Ausführungs Ressource sendet.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eigenständige Ausführungs Ressourcen und Ausführungs Ressourcen zurückzugeben, die mit den virtuellen Prozessor Stämmen der Ressourcen-Manager verknüpft sind.

Wenn es sich um eine eigenständige Ausführungs Ressource handelt, die Sie von einer der Methoden [ISchedulerProxy:: abonnementcurrentthread](ischedulerproxy-structure.md#subscribecurrentthread) oder [ISchedulerProxy:: requestinitialvirtualprozessoren](ischedulerproxy-structure.md#requestinitialvirtualprocessors)erhalten haben, wird beim Aufrufen der-Methode `Remove` das Thread Abonnement beendet, das von der Ressource für die Darstellung erstellt wurde. Vor dem Herunterfahren eines Scheduler-Proxys müssen Sie alle Thread Abonnements beenden und `Remove` aus dem Thread, der das Abonnement erstellt hat, abrufen.

Virtuelle Prozessor Stämme können auch an den Ressourcen-Manager zurückgegeben werden, indem die `Remove`-Methode aufgerufen wird, da die Schnittstelle `IVirtualProcessorRoot` von der `IExecutionResource` Schnittstelle erbt. Sie müssen möglicherweise einen virtuellen Prozessor Stamm entweder als Reaktion auf einen Aufrufen der [IScheduler:: removevirtualprocessor](ischeduler-structure.md#removevirtualprocessors) -Methode oder wenn Sie mit einem über abonnierten virtuellen Prozessor Stamm, den Sie aus der [ISchedulerProxy::](ischedulerproxy-structure.md#createoversubscriber) -Methode abgerufen haben, zurückgeben. Bei virtuellen Prozessor Stämmen gibt es keine Einschränkungen für den Thread, der die `Remove` Methode aufrufen kann.

`invalid_argument` wird ausgelöst, wenn der Parameter `pScheduler` auf `NULL`festgelegt ist.

`invalid_operation` wird ausgelöst, wenn der Parameter `pScheduler` nicht mit dem Planer identisch ist, für den diese Ausführungs Ressource erstellt wurde, oder mit einer eigenständigen Ausführungs Ressource, wenn sich der aktuelle Thread von dem Thread unterscheidet, der das Thread Abonnement erstellt hat.

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)
