---
title: ISchedulerProxy-Struktur
ms.date: 11/04/2016
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
ms.openlocfilehash: 776f70f9b93eb2e38151ceb5e84b4664420cf954
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854159"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy-Struktur

Die Schnittstelle, über die Planer mit dem Ressourcen-Manager der Concurrency Runtime kommunizieren, um die Ressourcenzuordnung auszuhandeln.

## <a name="syntax"></a>Syntax

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ISchedulerProxy:: BindContext](#bindcontext)|Ordnet einen Ausführungs Kontext einem Thread Proxy zu, wenn dieser nicht bereits mit einem verknüpft ist.|
|[ISchedulerProxy:: kreateoversubscriber](#createoversubscriber)|Erstellt einen neuen virtuellen Prozessor Stamm auf dem Hardware Thread, der einer vorhandenen Ausführungs Ressource zugeordnet ist.|
|[ISchedulerProxy:: requestinitialvirtualprozessoren](#requestinitialvirtualprocessors)|Fordert eine anfängliche Zuordnung von virtuellen Prozessor Stämmen an. Jeder virtuelle Prozessor Stamm stellt die Möglichkeit dar, einen Thread auszuführen, der Aufgaben für den Scheduler ausführen kann.|
|[ISchedulerProxy:: Shutdown](#shutdown)|Benachrichtigt den Ressourcen-Manager, dass der Scheduler heruntergefahren wird. Dies bewirkt, dass der Ressourcen-Manager sofort alle dem Scheduler gewährten Ressourcen zurückgibt.|
|[ISchedulerProxy:: Abonnement-CurrentThread](#subscribecurrentthread)|Registriert den aktuellen Thread beim Ressourcen-Manager, wobei dieser diesem Scheduler zugeordnet wird.|
|[ISchedulerProxy:: UnbindContext](#unbindcontext)|Trennt einen Thread Proxy von dem Ausführungs Kontext, der durch den `pContext`-Parameter angegeben wird, und gibt ihn an den freien Pool der Thread proxyfactory zurück. Diese Methode kann nur für einen Ausführungs Kontext aufgerufen werden, der über die [ISchedulerProxy:: BindContext](#bindcontext) -Methode gebunden wurde und noch nicht über den `pContext`-Parameter eines [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) -Methoden Aufrufs gestartet wurde.|

## <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager übergibt eine `ISchedulerProxy` Schnittstelle an jeden Scheduler, der sich mit der [IResourceManager:: RegisterScheduler](iresourcemanager-structure.md#registerscheduler) -Methode bei der Anwendung registriert.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ISchedulerProxy`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concrtrm. h

**Namespace:** Parallelität

## <a name="bindcontext"></a>ISchedulerProxy:: BindContext-Methode

Ordnet einen Ausführungs Kontext einem Thread Proxy zu, wenn dieser nicht bereits mit einem verknüpft ist.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Eine Schnittstelle zum Ausführungs Kontext, die einem Thread Proxy zugeordnet werden soll.

### <a name="remarks"></a>Bemerkungen

Normalerweise bindet die [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) -Methode einen Thread Proxy bei Bedarf an einen Ausführungs Kontext. Es gibt jedoch Situationen, in denen es erforderlich ist, einen Kontext im Voraus zu binden, um sicherzustellen, dass die `SwitchTo`-Methode zu einem bereits gebundenen Kontext wechselt. Dies ist bei einem ums-Planungs Kontext der Fall, da er keine Methoden aufruft, die Arbeitsspeicher belegen. das Binden eines Thread Proxys kann eine Speicher Belegung beinhalten, wenn ein Thread Proxy nicht im freien Pool der Thread Proxy-Factory nicht verfügbar ist.

`invalid_argument` wird ausgelöst, wenn der Parameter `pContext` den Wert `NULL`hat.

## <a name="createoversubscriber"></a>ISchedulerProxy:: kreateoversubscriber-Methode

Erstellt einen neuen virtuellen Prozessor Stamm auf dem Hardware Thread, der einer vorhandenen Ausführungs Ressource zugeordnet ist.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parameter

*pexecutionresource*<br/>
Eine `IExecutionResource`-Schnittstelle, die den Hardware Thread darstellt, den Sie überschreiben möchten.

### <a name="return-value"></a>Rückgabewert

Eine `IVirtualProcessorRoot`-Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, wenn Ihr Scheduler einen bestimmten Hardware Thread für einen begrenzten Zeitraum über abonnieren möchte. Wenn Sie den Stamm des virtuellen Prozessors erreicht haben, sollten Sie ihn an den Ressourcen-Manager zurückgeben, indem Sie die [Remove](iexecutionresource-structure.md#remove) -Methode für die `IVirtualProcessorRoot`-Schnittstelle aufrufen.

Sie können sogar einen vorhandenen virtuellen Prozessor Stamm überschreiben, da die `IVirtualProcessorRoot`-Schnittstelle von der `IExecutionResource`-Schnittstelle erbt.

## <a name="requestinitialvirtualprocessors"></a>ISchedulerProxy:: requestinitialvirtualprocessor-Methode

Fordert eine anfängliche Zuordnung von virtuellen Prozessor Stämmen an. Jeder virtuelle Prozessor Stamm stellt die Möglichkeit dar, einen Thread auszuführen, der Aufgaben für den Scheduler ausführen kann.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parameter

*doabonbecurrentthread*<br/>
Gibt an, ob der aktuelle Thread und das Konto während der Ressourcen Zuordnung abonniert werden sollen.

### <a name="return-value"></a>Rückgabewert

Die `IExecutionResource`-Schnittstelle für den aktuellen Thread, wenn der Parameter `doSubscribeCurrentThread` den Wert **true**aufweist. Wenn der Wert **false**ist, gibt die Methode NULL zurück.

### <a name="remarks"></a>Bemerkungen

Bevor ein Scheduler eine beliebige Arbeit ausführt, sollte er diese Methode verwenden, um virtuelle Prozessor Stämme von der Ressourcen-Manager anzufordern. Der Ressourcen-Manager greift mithilfe von [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) auf die Richtlinie des Planers zu und verwendet die Werte für die Richtlinien Schlüssel `MinConcurrency`, `MaxConcurrency` und `TargetOversubscriptionFactor`, um zu bestimmen, wie viele Hardwarethreads zunächst dem Scheduler zugewiesen werden und wie viele virtuelle Prozessor Stämme für jeden Hardware Thread erstellt werden. Weitere Informationen zur Verwendung von Scheduler-Richtlinien, um die anfängliche Zuordnung eines Planers zu bestimmen, finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

Der Ressourcen-Manager gewährt einem Scheduler Ressourcen durch Aufrufen der-Methode [IScheduler:: addvirtualprozessoren](ischeduler-structure.md#addvirtualprocessors) mit einer Liste virtueller Prozessor Stämme. Die-Methode wird als Rückruf in den Scheduler aufgerufen, bevor diese Methode zurückgegeben wird.

Wenn das Zeit Planungs Modul ein Abonnement für den aktuellen Thread angefordert hat, indem der Parameter `doSubscribeCurrentThread` auf **true**festgelegt wurde, gibt die Methode eine `IExecutionResource` Schnittstelle zurück. Das Abonnement muss zu einem späteren Zeitpunkt mit der [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) -Methode beendet werden.

Wenn Sie bestimmen, welche Hardwarethreads ausgewählt werden, versucht der Ressourcen-Manager, die Prozessor Knoten Affinität zu optimieren. Wenn das Abonnement für den aktuellen Thread angefordert wird, ist dies ein Hinweis darauf, dass der aktuelle Thread an der Arbeit teilnehmen möchte, die diesem Scheduler zugewiesen ist. In einem solchen Fall befinden sich die zugewiesenen virtuellen Prozessor Stämme auf dem Prozessor Knoten, auf dem der aktuelle Thread ausgeführt wird (sofern möglich).

Durch das Abonnieren eines Threads wird die Abonnement Ebene des zugrunde liegenden Hardware Threads um 1 erhöht. Die Abonnement Ebene wird um eins reduziert, wenn das Abonnement beendet wird. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="shutdown"></a>ISchedulerProxy:: Shutdown-Methode

Benachrichtigt den Ressourcen-Manager, dass der Scheduler heruntergefahren wird. Dies bewirkt, dass der Ressourcen-Manager sofort alle dem Scheduler gewährten Ressourcen zurückgibt.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Bemerkungen

Alle `IExecutionContext` Schnittstellen, die der Scheduler als Ergebnis eines Abonnierung eines externen Threads mithilfe der Methoden `ISchedulerProxy::RequestInitialVirtualProcessors` oder `ISchedulerProxy::SubscribeCurrentThread` empfangen hat, müssen mithilfe `IExecutionResource::Remove` an die Ressourcen-Manager zurückgegeben werden, bevor ein Scheduler wieder heruntergefahren wird.

Wenn Ihr Scheduler über deaktivierte virtuelle Prozessor Stämme verfügt, müssen Sie diese mithilfe von [IVirtualProcessorRoot:: Aktivierung](ivirtualprocessorroot-structure.md#activate)aktivieren. wenn die Thread Proxys darauf ausgeführt werden, verlassen Sie die `Dispatch`-Methode der Ausführungs Kontexte, die Sie weiterleiten, bevor Sie `Shutdown` auf einem Scheduler-Proxy aufrufen.

Es ist nicht erforderlich, dass der Scheduler einzeln alle virtuellen Prozessor Stämme zurückgibt, die der Ressourcen-Manager ihm über Aufrufe der `Remove`-Methode erteilt wurde, da alle virtuellen Prozessoren Stämme beim Herunterfahren an die Ressourcen-Manager zurückgegeben werden.

## <a name="subscribecurrentthread"></a>ISchedulerProxy:: abonkurcurrentthread-Methode

Registriert den aktuellen Thread beim Ressourcen-Manager, wobei dieser diesem Scheduler zugeordnet wird.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die `IExecutionResource`-Schnittstellen, die den aktuellen Thread in der Laufzeit darstellt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, wenn das Ressourcen-Manager den aktuellen Thread berücksichtigen soll, während dem Scheduler und anderen Zeit Planungs Modulen Ressourcen zugeordnet werden. Dies ist besonders nützlich, wenn der Thread plant, an der Arbeit, die dem Scheduler in die Warteschlange eingereiht ist, zusammen mit den virtuellen Prozessor Stämme, die der Planer vom Ressourcen-Manager empfängt, an der Arbeit teilnimmt. Der Ressourcen-Manager verwendet Informationen, um unnötige über Abonnements von Hardwarethreads auf dem System zu verhindern.

Die über diese Methode empfangene Ausführungs Ressource sollte mithilfe der [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) -Methode an den Ressourcen-Manager zurückgegeben werden. Der Thread, der die `Remove`-Methode aufruft, muss derselbe Thread sein, der zuvor die `SubscribeCurrentThread`-Methode aufgerufen hat.

Durch das Abonnieren eines Threads wird die Abonnement Ebene des zugrunde liegenden Hardware Threads um 1 erhöht. Die Abonnement Ebene wird um eins reduziert, wenn das Abonnement beendet wird. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="unbindcontext"></a>ISchedulerProxy:: UnbindContext-Methode

Trennt einen Thread Proxy von dem Ausführungs Kontext, der durch den `pContext`-Parameter angegeben wird, und gibt ihn an den freien Pool der Thread proxyfactory zurück. Diese Methode kann nur für einen Ausführungs Kontext aufgerufen werden, der über die [ISchedulerProxy:: BindContext](#bindcontext) -Methode gebunden wurde und noch nicht über den `pContext`-Parameter eines [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) -Methoden Aufrufs gestartet wurde.

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Der Ausführungs Kontext, dessen Zuordnung zum zugehörigen Thread Proxy aufgehoben werden soll.

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IScheduler-Struktur](ischeduler-structure.md)<br/>
[IThreadProxy-Struktur](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager-Struktur](iresourcemanager-structure.md)
