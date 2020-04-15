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
ms.openlocfilehash: 4305948aa4e5da36023c1d4fe8b0b84aa4d59e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377315"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource-Struktur

Eine Abstraktion für einen Hardwarethread.

## <a name="syntax"></a>Syntax

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IExecutionResource::CurrentSubscriptionLevel](#currentsubscriptionlevel)|Gibt die Anzahl der aktivierten virtuellen Prozessorwurzeln und abonnierten externen Threads zurück, die derzeit dem zugrunde liegenden Hardwarethread zugeordnet sind, den diese Ausführungsressource darstellt.|
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|Gibt einen eindeutigen Bezeichner für den Hardwarethread zurück, den diese Ausführungsressource darstellt.|
|[IExecutionResource::GetNodeId](#getnodeid)|Gibt einen eindeutigen Bezeichner für den Prozessorknoten zurück, zu dem diese Ausführungsressource gehört.|
|[IExecutionResource::Entfernen](#remove)|Gibt diese Ausführungsressource an den Ressourcen-Manager zurück.|

## <a name="remarks"></a>Bemerkungen

Ausführungsressourcen können eigenständig sein oder virtuellen Prozessorstämmen zugeordnet sein. Eine eigenständige Ausführungsressource wird erstellt, wenn ein Thread in Ihrer Anwendung ein Threadabonnement erstellt. Die Methoden [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) und [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) erstellen Threadabonnements und geben eine `IExecutionResource` Schnittstelle zurück, die das Abonnement darstellt. Das Erstellen eines Threadabonnements ist eine Möglichkeit, den Ressourcen-Manager darüber zu informieren, dass ein gegebener Thread an der Arbeit teilnimmt, die an einem Planer in die Warteschlange gestellt wird, zusammen mit den virtuellen Prozessorstämmen, die Resource Manager dem Planer zuweist. Der Ressourcen-Manager verwendet die Informationen, um zu vermeiden, dass Hardwarethreads dort überschreibt werden, wo dies möglich ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IExecutionResource`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="iexecutionresourcecurrentsubscriptionlevel-method"></a><a name="currentsubscriptionlevel"></a>IExecutionResource::CurrentSubscriptionLevel-Methode

Gibt die Anzahl der aktivierten virtuellen Prozessorwurzeln und abonnierten externen Threads zurück, die derzeit dem zugrunde liegenden Hardwarethread zugeordnet sind, den diese Ausführungsressource darstellt.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Abonnementstufe.

### <a name="remarks"></a>Bemerkungen

Die Abonnementebene gibt an, wie viele ausgeführte Threads dem Hardwarethread zugeordnet sind. Dies umfasst nur Threads, die dem Ressourcen-Manager in Form von abonnierten Threads bekannt sind, und virtuelle Prozessorwurzeln, die Threadproxys aktiv ausführen.

Wenn sie die Methode [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)oder die Methode [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) mit dem Parameter `doSubscribeCurrentThread` auf den Wert **true** setzt, wird die Abonnementebene eines Hardwarethreads um eins erhöht. Sie geben `IExecutionResource` auch eine Schnittstelle zurück, die das Abonnement darstellt. Ein entsprechender Aufruf der [IExecutionResource::Dekrementierungen](#remove) der Abonnementebene des Hardwarethreads um eins.

Der Akt der Aktivierung eines virtuellen Prozessorstamms mit der Methode [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate) erhöht die Abonnementebene eines Hardwarethreads um eins. Die Methoden [IVirtualProcessorRoot::Deactivate](ivirtualprocessorroot-structure.md#deactivate), oder [IExecutionResource::Dekrementierung](#remove) der Abonnementebene um eins, wenn sie auf einem aktivierten virtuellen Prozessorstamm aufgerufen wird.

Der Ressourcen-Manager verwendet Informationen auf Abonnementebene als eine der Möglichkeiten, wie bestimmt werden kann, wann Ressourcen zwischen Planern verschoben werden sollen.

## <a name="iexecutionresourcegetexecutionresourceid-method"></a><a name="getexecutionresourceid"></a>IExecutionResource::GetExecutionResourceId-Methode

Gibt einen eindeutigen Bezeichner für den Hardwarethread zurück, den diese Ausführungsressource darstellt.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für den Hardwarethread, der dieser Ausführungsressource zugrunde liegt.

### <a name="remarks"></a>Bemerkungen

Jedem Hardwarethread wird von der Concurrency Runtime ein eindeutiger Bezeichner zugewiesen. Wenn mehreren Ausführungsressourcen Hardwarethread zugeordnet sind, verfügen alle über denselben Ausführungsressourcenbezeichner.

## <a name="iexecutionresourcegetnodeid-method"></a><a name="getnodeid"></a>IExecutionResource::GetNodeId-Methode

Gibt einen eindeutigen Bezeichner für den Prozessorknoten zurück, zu dem diese Ausführungsressource gehört.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Bezeichner für einen Prozessorknoten.

### <a name="remarks"></a>Bemerkungen

Die Concurrency Runtime stellt Hardwarethreads auf dem System in Gruppen von Prozessorknoten dar. Knoten werden in der Regel von der Hardwaretopologie des Systems abgeleitet. Beispielsweise können alle Prozessoren auf einem bestimmten Socket oder einem bestimmten NUMA-Knoten zum gleichen Prozessorknoten gehören. Der Ressourcen-Manager weist diesen Knoten eindeutige `0` Bezeichner `nodeCount - 1`zu, beginnend mit bis zu und einschließlich , wobei `nodeCount` die Gesamtzahl der Prozessorknoten auf dem System angezeigt wird.

Die Anzahl der Knoten kann über die Funktion [GetProcessorNodeCount](concurrency-namespace-functions.md)abgerufen werden.

## <a name="iexecutionresourceremove-method"></a><a name="remove"></a>IExecutionResource::Remove-Methode

Gibt diese Ausführungsressource an den Ressourcen-Manager zurück.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parameter

*pScheduler*<br/>
Eine Schnittstelle zum Planer, die die Anforderung zum Entfernen dieser Ausführungsressource stellt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eigenständige Ausführungsressourcen sowie Ausführungsressourcen, die virtuellen Prozessorwurzeln zugeordnet sind, an den Ressourcen-Manager zurückzugeben.

Wenn es sich um eine eigenständige Ausführungsressource handelt, die Sie von einer der Methoden [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) oder [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)erhalten haben, beendet das Aufrufen der Methode `Remove` das Threadabonnement, für das die Ressource erstellt wurde. Sie müssen alle Threadabonnements beenden, bevor Sie einen Planerproxy herunterfahren, und Sie müssen vom Thread aufrufen, `Remove` der das Abonnement erstellt hat.

Auch virtuelle Prozessorwurzeln können an den Ressourcen-Manager zurückgegeben `Remove` werden, indem `IVirtualProcessorRoot` die Methode `IExecutionResource` aufruft, da die Schnittstelle von der Schnittstelle erbt. Möglicherweise müssen Sie einen virtuellen Prozessorstamm entweder als Reaktion auf einen Aufruf der [IScheduler::RemoveVirtualProcessors-Methode](ischeduler-structure.md#removevirtualprocessors) zurückgeben, oder wenn Sie mit einem überzeichneten virtuellen Prozessorstamm fertig sind, den Sie von der [ISchedulerProxy::CreateOversubscriber-Methode](ischedulerproxy-structure.md#createoversubscriber) erhalten haben. Für virtuelle Prozessorstammgibte gibt es keine `Remove` Einschränkungen, für welchen Thread die Methode aufrufen kann.

`invalid_argument`wird ausgelöst, `pScheduler` wenn der `NULL`Parameter auf gesetzt ist.

`invalid_operation`wird ausgelöst, `pScheduler` wenn sich der Parameter von dem Planer unterscheidet, für den diese Ausführungsressource erstellt wurde, oder mit einer eigenständigen Ausführungsressource, wenn sich der aktuelle Thread vom Thread unterscheidet, der das Threadabonnement erstellt hat.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)
