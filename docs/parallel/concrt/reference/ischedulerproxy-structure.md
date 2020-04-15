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
ms.openlocfilehash: f4a9e79c2da56406610ad6da08fb438e2f92923d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368164"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy-Struktur

Die Schnittstelle, über die Planer mit dem Ressourcen-Manager der Concurrency Runtime kommunizieren, um die Ressourcenzuordnung auszuhandeln.

## <a name="syntax"></a>Syntax

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ISchedulerProxy::BindContext](#bindcontext)|Ordnet einen Ausführungskontext einem Threadproxy zu, sofern er nicht bereits einem Threadproxy zugeordnet ist.|
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Erstellt einen neuen virtuellen Prozessorstamm auf dem Hardwarethread, der einer vorhandenen Ausführungsressource zugeordnet ist.|
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Fordert eine anfängliche Zuweisung virtueller Prozessorstämme an. Jeder virtuelle Prozessorstamm stellt die Möglichkeit dar, einen Thread auszuführen, der Arbeit für den Planer ausführen kann.|
|[ISchedulerProxy::Shutdown](#shutdown)|Benachrichtigt den Ressourcen-Manager, dass der Planer heruntergefahren wird. Dies führt dazu, dass der Ressourcen-Manager sofort alle dem Planer gewährten Ressourcen zurückgibt.|
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Registriert den aktuellen Thread beim Ressourcen-Manager und wird diesem Planer zugeordnet.|
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Trennt einen Threadproxy vom Ausführungskontext, der durch den `pContext` Parameter angegeben wird, und gibt ihn an den freien Pool der Threadproxyfactory zurück. Diese Methode kann nur für einen Ausführungskontext aufgerufen werden, der über die [ISchedulerProxy::BindContext-Methode](#bindcontext) gebunden wurde und noch nicht über den `pContext` Parameter eines [IThreadProxy::SwitchTo-Methodenaufrufs](ithreadproxy-structure.md#switchto) gestartet wurde.|

## <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager `ISchedulerProxy` übergibt jedem Planer, der sich mit der [IResourceManager::RegisterScheduler-Methode](iresourcemanager-structure.md#registerscheduler) registriert, eine Schnittstelle.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ISchedulerProxy`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>ISchedulerProxy::BindContext-Methode

Ordnet einen Ausführungskontext einem Threadproxy zu, sofern er nicht bereits einem Threadproxy zugeordnet ist.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Eine Schnittstelle zum Ausführungskontext, die einem Threadproxy zugeordnet werden soll.

### <a name="remarks"></a>Bemerkungen

Normalerweise bindet die [IThreadProxy::SwitchTo-Methode](ithreadproxy-structure.md#switchto) einen Threadproxy bei Bedarf an einen Ausführungskontext. Es gibt jedoch Umstände, in denen es notwendig ist, `SwitchTo` einen Kontext im Voraus zu binden, um sicherzustellen, dass die Methode in einen bereits gebundenen Kontext wechselt. Dies ist bei einem UMS-Planungskontext der Fall, da er keine Methoden aufrufen kann, die Speicher zuweisen, und das Binden eines Threadproxys kann eine Speicherzuweisung beinhalten, wenn ein Threadproxy im freien Pool der Threadproxyfactory nicht ohne weiteres verfügbar ist.

`invalid_argument`wird ausgelöst, `pContext` wenn der `NULL`Parameter den Wert hat.

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>ISchedulerProxy::CreateOversubscriber-Methode

Erstellt einen neuen virtuellen Prozessorstamm auf dem Hardwarethread, der einer vorhandenen Ausführungsressource zugeordnet ist.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parameter

*pExecutionResource*<br/>
Eine `IExecutionResource` Schnittstelle, die den Hardwarethread darstellt, den Sie überzeichnen möchten.

### <a name="return-value"></a>Rückgabewert

Eine `IVirtualProcessorRoot`-Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, wenn der Planer einen bestimmten Hardwarethread für einen begrenzten Zeitraum überzeichnen möchte. Sobald Sie mit dem Stamm des virtuellen Prozessors fertig sind, sollten Sie `IVirtualProcessorRoot` ihn an den Ressourcen-Manager zurückgeben, indem Sie die [Remove-Methode](iexecutionresource-structure.md#remove) auf der Schnittstelle aufrufen.

Sie können sogar einen vorhandenen virtuellen Prozessorstamm überzeichnen, da die `IVirtualProcessorRoot` Schnittstelle von der `IExecutionResource` Schnittstelle erbt.

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>ISchedulerProxy::RequestInitialVirtualProcessors-Methode

Fordert eine anfängliche Zuweisung virtueller Prozessorstämme an. Jeder virtuelle Prozessorstamm stellt die Möglichkeit dar, einen Thread auszuführen, der Arbeit für den Planer ausführen kann.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parameter

*doSubscribeCurrentThread*<br/>
Gibt an, ob der aktuelle Thread abonniert und während der Ressourcenzuordnung berücksichtigt werden soll.

### <a name="return-value"></a>Rückgabewert

Die `IExecutionResource` Schnittstelle für den aktuellen `doSubscribeCurrentThread` Thread, wenn der Parameter den Wert **true**hat. Wenn der Wert **false**ist, gibt die Methode NULL zurück.

### <a name="remarks"></a>Bemerkungen

Bevor ein Planer eine Arbeit ausführt, sollte er diese Methode verwenden, um virtuelle Prozessorwurzeln vom Ressourcen-Manager anzufordern. Der Ressourcen-Manager greift mithilfe von [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) auf die Richtlinie des `MinConcurrency` `MaxConcurrency` Planers zu und verwendet die Werte für die Richtlinienschlüssel , und `TargetOversubscriptionFactor` bestimmt, wie viele Hardwarethreads dem Planer ursprünglich zugewiesen werden sollen und wie viele virtuelle Prozessorwurzeln für jeden Hardwarethread erstellt werden sollen. Weitere Informationen dazu, wie Planerrichtlinien verwendet werden, um die anfängliche Zuordnung eines Planers zu bestimmen, finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

Der Ressourcen-Manager gewährt einem Planer Ressourcen, indem er die Methode [IScheduler::AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) mit einer Liste virtueller Prozessorwurzeln aufruft. Die Methode wird als Rückruf in den Planer aufgerufen, bevor diese Methode zurückgegeben wird.

Wenn der Planer ein Abonnement für den `doSubscribeCurrentThread` aktuellen Thread angefordert hat, indem er den Parameter auf **true**festlegt, gibt die Methode eine `IExecutionResource` Schnittstelle zurück. Das Abonnement muss zu einem späteren Zeitpunkt mit der [IExecutionResource::Remove-Methode](iexecutionresource-structure.md#remove) beendet werden.

Beim Bestimmen der ausgewählten Hardwarethreads versucht der Ressourcen-Manager, die Affinität des Prozessorknotens zu optimieren. Wenn ein Abonnement für den aktuellen Thread angefordert wird, ist dies ein Hinweis darauf, dass der aktuelle Thread beabsichtigt, an der diesem Planer zugewiesenen Arbeit teilzunehmen. In einem solchen Fall befinden sich die zugewiesenen virtuellen Prozessorwurzeln auf dem Prozessorknoten, auf dem der aktuelle Thread ausgeführt wird, wenn möglich.

Der Akt des Abonnierens eines Threads erhöht die Abonnementebene des zugrunde liegenden Hardwarethreads um eins. Die Abonnementstufe wird um eins reduziert, wenn das Abonnement gekündigt wird. Weitere Informationen zu Abonnementebenen finden Sie unter [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>ISchedulerProxy::Shutdown-Methode

Benachrichtigt den Ressourcen-Manager, dass der Planer heruntergefahren wird. Dies führt dazu, dass der Ressourcen-Manager sofort alle dem Planer gewährten Ressourcen zurückgibt.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Bemerkungen

Alle `IExecutionContext` Schnittstellen, die der Planer als Ergebnis des Abonnierens eines `ISchedulerProxy::RequestInitialVirtualProcessors` `ISchedulerProxy::SubscribeCurrentThread` externen Threads mit den `IExecutionResource::Remove` Methoden erhalten hat oder der an den Ressourcen-Manager zurückgegeben werden muss, bevor sich ein Planer selbst herunterfährt.

Wenn Ihr Planer über deaktivierte virtuelle Prozessorwurzeln verfügt, müssen Sie diese mit [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate)aktivieren und `Dispatch` die Threadproxys, die auf ihnen `Shutdown` ausgeführt werden, die Methode der Ausführungskontexte verlassen, die sie aussenden, bevor Sie sie auf einem Planerproxy aufrufen.

Es ist nicht erforderlich, dass der Planer alle virtuellen Prozessorwurzeln, die der `Remove` Ressourcen-Manager ihm über Aufrufe der Methode gewährt hat, einzeln zurückgibt, da alle Stammverzeichnisse virtueller Prozessoren beim Herunterfahren an den Ressourcen-Manager zurückgegeben werden.

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>ISchedulerProxy::SubscribeCurrentThread-Methode

Registriert den aktuellen Thread beim Ressourcen-Manager und wird diesem Planer zugeordnet.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die `IExecutionResource` Schnittstelle, die den aktuellen Thread in der Laufzeit darstellt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, wenn der Ressourcen-Manager den aktuellen Thread berücksichtigen soll, während Ressourcen dem Planer und anderen Planern zugewiesen werden. Dies ist besonders nützlich, wenn der Thread plant, an der Arbeit teilzunehmen, die an Ihrem Planer in der Warteschlange liegt, zusammen mit den virtuellen Prozessorwurzeln, die der Planer vom Ressourcen-Manager erhält. Der Ressourcen-Manager verwendet Informationen, um unnötige Überzeichnungen von Hardwarethreads auf dem System zu verhindern.

Die über diese Methode empfangene Ausführungsressource sollte mithilfe der [IExecutionResource::Remove-Methode](iexecutionresource-structure.md#remove) an den Ressourcen-Manager zurückgegeben werden. Der Thread, `Remove` der die Methode aufruft, `SubscribeCurrentThread` muss derselbe Thread sein, der zuvor die Methode aufgerufen hat.

Der Akt des Abonnierens eines Threads erhöht die Abonnementebene des zugrunde liegenden Hardwarethreads um eins. Die Abonnementstufe wird um eins reduziert, wenn das Abonnement gekündigt wird. Weitere Informationen zu Abonnementebenen finden Sie unter [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>ISchedulerProxy::UnbindContext-Methode

Trennt einen Threadproxy vom Ausführungskontext, der durch den `pContext` Parameter angegeben wird, und gibt ihn an den freien Pool der Threadproxyfactory zurück. Diese Methode kann nur für einen Ausführungskontext aufgerufen werden, der über die [ISchedulerProxy::BindContext-Methode](#bindcontext) gebunden wurde und noch nicht über den `pContext` Parameter eines [IThreadProxy::SwitchTo-Methodenaufrufs](ithreadproxy-structure.md#switchto) gestartet wurde.

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Der Ausführungskontext, der von seinem Threadproxy aufgelöst werden soll.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IScheduler-Struktur](ischeduler-structure.md)<br/>
[IThreadProxy-Struktur](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager-Struktur](iresourcemanager-structure.md)
