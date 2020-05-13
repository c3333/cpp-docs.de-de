---
title: IExecutionContext-Struktur
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 532247ca1776452ad32476d2bcdfafcee3481058
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358803"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext-Struktur

Eine Schnittstelle zu einem Ausführungskontext, der auf einem angegebenen virtuellen Prozessor ausgeführt werden kann und einen gemeinsamen Kontextwechsel zulässt.

## <a name="syntax"></a>Syntax

```cpp
struct IExecutionContext;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IExecutionContext::Dispatch](#dispatch)|Die Methode, die aufgerufen wird, wenn ein Threadproxy mit der Ausführung eines bestimmten Ausführungskontexts beginnt. Dies sollte die Hauptarbeitsroutine für Ihren Planer sein.|
|[IExecutionContext::GetId](#getid)|Gibt einen eindeutigen Bezeichner für den Ausführungskontext zurück.|
|[IExecutionContext::GetProxy](#getproxy)|Gibt eine Schnittstelle an den Threadproxy zurück, der diesen Kontext ausführt.|
|[IExecutionContext::GetScheduler](#getscheduler)|Gibt eine Schnittstelle an den Planer zurück, zu der dieser Ausführungskontext gehört.|
|[IExecutionContext::SetProxy](#setproxy)|Ordnet diesem Ausführungskontext einen Threadproxy zu. Der zugeordnete Threadproxy ruft diese Methode auf, bevor `Dispatch` er mit der Ausführung der Kontextmethode beginnt.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie einen benutzerdefinierten Planer implementieren, der mit dem Ressourcen-Manager der Concurrency `IExecutionContext` Runtime in Verbindung steht, müssen Sie die Schnittstelle implementieren. Die vom Ressourcen-Manager erstellten Threads führen die Arbeit `IExecutionContext::Dispatch` im Auftrag Desplaners durch Ausführen der Methode aus.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IExecutionContext`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="iexecutioncontextdispatch-method"></a><a name="dispatch"></a>IExecutionContext::Dispatch-Methode

Die Methode, die aufgerufen wird, wenn ein Threadproxy mit der Ausführung eines bestimmten Ausführungskontexts beginnt. Dies sollte die Hauptarbeitsroutine für Ihren Planer sein.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parameter

*pDispatchState*<br/>
Ein Zeiger auf den Status, unter dem dieser Ausführungskontext ausgelöst wird. Weitere Informationen zum Dispatchstatus finden Sie unter [DispatchState](dispatchstate-structure.md).

## <a name="iexecutioncontextgetid-method"></a><a name="getid"></a>IExecutionContext::GetId-Methode

Gibt einen eindeutigen Bezeichner für den Ausführungskontext zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Ganzzahlbezeichner.

### <a name="remarks"></a>Bemerkungen

Sie sollten die `GetExecutionContextId` Methode verwenden, um einen eindeutigen `IExecutionContext` Bezeichner für das Objekt zu erhalten, das die Schnittstelle implementiert, bevor Sie die Schnittstelle als Parameter für Methoden verwenden, die vom Ressourcen-Manager bereitgestellt werden. Es wird erwartet, dass Sie `GetId` denselben Bezeichner zurückgeben, wenn die Funktion aufgerufen wird.

Ein Bezeichner, der aus einer anderen Quelle abgerufen wird, kann zu einem undefinierten Verhalten führen.

## <a name="iexecutioncontextgetproxy-method"></a><a name="getproxy"></a>IExecutionContext::GetProxy-Methode

Gibt eine Schnittstelle an den Threadproxy zurück, der diesen Kontext ausführt.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine `IThreadProxy`-Schnittstelle. Wenn der Threadproxy des Ausführungskontexts nicht mit `SetProxy`einem Aufruf `NULL`von initialisiert wurde, muss die Funktion zurückgeben.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Manager `SetProxy` ruft die Methode in `IThreadProxy` einem Ausführungskontext mit einer `Dispatch` Schnittstelle als Parameter auf, bevor die Methode im Kontext eingegeben wird. Es wird erwartet, dass Sie dieses `GetProxy()`Argument speichern und bei Aufrufen an zurückgeben.

## <a name="iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a>IExecutionContext::GetScheduler-Methode

Gibt eine Schnittstelle an den Planer zurück, zu der dieser Ausführungskontext gehört.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine `IScheduler`-Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Sie müssen den Ausführungskontext mit `IScheduler` einer gültigen Schnittstelle initialisieren, bevor Sie ihn als Parameter für Methoden verwenden, die vom Ressourcen-Manager bereitgestellt werden.

## <a name="iexecutioncontextsetproxy-method"></a><a name="setproxy"></a>IExecutionContext::SetProxy-Methode

Ordnet diesem Ausführungskontext einen Threadproxy zu. Der zugeordnete Threadproxy ruft diese Methode auf, bevor `Dispatch` er mit der Ausführung der Kontextmethode beginnt.

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parameter

*pThreadProxy*<br/>
Eine Schnittstelle zum Threadproxy, die `Dispatch` im Begriff ist, die Methode in diesem Ausführungskontext einzugeben.

### <a name="remarks"></a>Bemerkungen

Es wird erwartet, `pThreadProxy` dass Sie den Parameter `GetProxy` speichern und bei einem Aufruf der Methode zurückgeben. Der Ressourcen-Manager stellt sicher, dass sich der dem Ausführungskontext zugeordnete Threadproxy nicht ändert, während der Threadproxy die `Dispatch` Methode ausführt.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IScheduler-Struktur](ischeduler-structure.md)<br/>
[IThreadProxy-Struktur](ithreadproxy-structure.md)
