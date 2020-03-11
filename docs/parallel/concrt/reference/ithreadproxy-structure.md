---
title: IThreadProxy-Struktur
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: b87694393af4634ec97d05070aa5513cd132098a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854162"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy-Struktur

Eine Abstraktion für einen Thread der Ausführung. Abhängig von dem von Ihnen erstellten `SchedulerType`-Richtlinienschlüssel des Planers, gewährt der Ressourcen-Manager eine Threadproxy, der entweder von einem regulären Win32-Thread oder einem im Benutzermodus planbaren (UMS) Thread unterstützt wird. UMS-Threads werden auf 64-Bit-Betriebssystemen mit Version Windows 7 und höher unterstützt.

## <a name="syntax"></a>Syntax

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IThreadProxy:: GetId](#getid)|Gibt einen eindeutigen Bezeichner für den Thread Proxy zurück.|
|[IThreadProxy:: SwitchOut](#switchout)|Hebt die Zuordnung des Kontexts vom zugrunde liegenden virtuellen Prozessorstamm auf.|
|[IThreadProxy:: SwitchTo](#switchto)|Führt einen kooperativen Kontextwechsel vom aktuell ausgeführten Kontext zu einem anderen aus.|
|[IThreadProxy:: yieldto System](#yieldtosystem)|Bewirkt, dass der aufrufende Thread die Ausführung an einen anderen Thread übergibt, der auf dem aktuellen Prozessor ausgeführt werden kann. Das Betriebssystem wählt den nächsten Thread aus, der ausgeführt werden soll.|

## <a name="remarks"></a>Bemerkungen

Thread Proxys werden mit Ausführungs Kontexten gekoppelt, die durch die-Schnittstelle dargestellt werden, um die Arbeit zu verteilen `IExecutionContext`.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IThreadProxy`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concrtrm. h

**Namespace:** Parallelität

## <a name="getid"></a>IThreadProxy:: GetId-Methode

Gibt einen eindeutigen Bezeichner für den Thread Proxy zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Eine eindeutige ganzzahlige Kennung.

## <a name="switchout"></a>IThreadProxy:: SwitchOut-Methode

Hebt die Zuordnung des Kontexts vom zugrunde liegenden virtuellen Prozessorstamm auf.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Parameter

*SwitchState*<br/>
Gibt den Zustand des Threadproxys an, der den Wechsel ausführt. Der Parameter ist vom Typ `SwitchingProxyState`.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `SwitchOut`, wenn Sie aus irgendeinem Grund die Zuordnung eines Kontexts zu einem virtuellen Prozessorstamm aufheben müssen, in dem dieser ausgeführt wird. Je nachdem, welchen Wert Sie an den `switchState`-Parameter übergeben, und abhängig von dessen Ausführung auf einem virtuellen Prozessorstamm, wird der Aufruf entweder sofort zurückgegeben oder der dem Kontext zugeordnete Threadproxy wird blockiert. Es ist nicht zulässig, `SwitchOut` aufzurufen, wenn der Parameter auf `Idle` festgelegt ist. Dies führt zu einer [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme.

`SwitchOut` ist nützlich, wenn Sie die Anzahl der Stämme virtueller Prozessoren für den Planer verringern möchten, da der Ressourcen-Manager Sie angewiesen hat, dies zu tun oder Sie den Stamm eines überzeichneten temporären virtuellen Prozessors angefordert haben und diesen nicht mehr benötigen. In diesem Fall sollten Sie die Methode [IVirtualProcessorRoot:: Remove](iexecutionresource-structure.md#remove) für den Stamm des virtuellen Prozessors aufrufen, bevor Sie einen Aufruf an `SwitchOut` ausführen, wobei der Parameter `switchState` auf `Blocking`festgelegt ist. Auf diese Weise wird der Threadproxy blockiert. Die Ausführung wird fortgesetzt, wenn im Planer ein anderer virtueller Prozessorstamm für die Ausführung verfügbar ist. Die Ausführung des blockierten Threadproxys kann fortgesetzt werden, indem die `SwitchTo`-Funktion aufgerufen wird, um zum Ausführungskontext dieses Threadproxys zu wechseln. Sie können den Threadproxy auch fortsetzen, indem Sie dessen zugeordneten Kontext verwenden, um den Stamm eines virtuellen Prozessors zu aktivieren. Weitere Informationen hierzu finden Sie unter [IVirtualProcessorRoot:: Aktivierung](ivirtualprocessorroot-structure.md#activate).

Sie können `SwitchOut` zudem verwenden, um den virtuellen Prozessor erneut zu initialisieren, damit dieser zukünftig aktiviert werden kann, wenn Sie den Threadproxy blockieren oder vorübergehend vom Stamm des virtuellen Prozessors, für den dieser ausgeführt wird, und vom Planer, für den er Arbeit verteilt, trennen möchten. Verwenden Sie `SwitchOut` mit dem auf `switchState` festgelegten `Blocking`-Parameter, wenn Sie den Threadproxy blockieren möchten. Wie oben beschrieben, kann er zu einem späteren Zeitpunkt mithilfe von `SwitchTo` oder `IVirtualProcessorRoot::Activate` fortgesetzt werden. Verwenden Sie `SwitchOut` mit dem auf `Nesting` festgelegten Parameter, wenn Sie diesen Threadproxy vorübergehend vom Stamm des virtuellen Prozessors, auf dem er ausgeführt wird, und vom Planer, dem der virtuelle Prozessor zugeordnet ist, trennen möchten. Das Aufrufen von `SwitchOut` mit dem auf `switchState` festgelegten `Nesting`-Parameter führt während dessen Ausführung auf einem virtuellen Prozessorstamm zu einer erneuten Initialisierung des Stamms und zur Fortsetzung des aktuellen Threadproxys, obwohl dieser nicht erforderlich ist. Der Thread Proxy hat den Scheduler verlassen, bis er die [IThreadProxy:: SwitchOut](#switchout) -Methode mit `Blocking` zu einem späteren Zeitpunkt aufruft. Der zweite Aufruf von `SwitchOut` mit dem auf `Blocking` festgelegten Parameter soll den Kontext in einen blockierten Zustand zurückversetzen, damit er im Planer, von dem er getrennt ist, mit `SwitchTo` oder `IVirtualProcessorRoot::Activate` fortgesetzt werden kann. Da die Ausführung nicht auf einem virtuellen Prozessorstamm erfolgt, findet keine erneute Initialisierung statt.

Ein erneut initialisierter virtueller Prozessorstamm unterscheidet sich nicht von einem neuen virtuellen Prozessorstamm, der dem Planer vom Ressourcen-Manager gewährt wurde. Sie können ihn für die Ausführung verwenden, indem Sie ihn mit `IVirtualProcessorRoot::Activate` in einem Ausführungskontext aktivieren.

`SwitchOut` muss für die `IThreadProxy`-Schnittstelle aufgerufen werden, die den gerade ausgeführten Thread darstellt, oder die Ergebnisse sind nicht definiert.

In den Bibliotheken und Headern, die mit Visual Studio 2010 geliefert wurden, weist diese Methode keinen Parameter auf, und der virtuelle Prozessorstamm wurde nicht initialisiert. Um altes Verhalten beizubehalten, wird der Standardparameterwert von `Blocking` angegeben.

## <a name="switchto"></a>IThreadProxy:: SwitchTo-Methode

Führt einen kooperativen Kontextwechsel vom aktuell ausgeführten Kontext zu einem anderen aus.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Der Ausführungs Kontext, zu dem kooperativ gewechselt werden soll.

*SwitchState*<br/>
Gibt den Zustand des Threadproxys an, der den Wechsel ausführt. Der Parameter ist vom Typ `SwitchingProxyState`.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um von der [IExecutionContext::D ispatch](iexecutioncontext-structure.md#dispatch) -Methode des ersten Ausführungs Kontexts aus einen Ausführungs Kontext zu einem anderen zu wechseln. Die-Methode ordnet den Ausführungs Kontext `pContext` einem Thread Proxy zu, wenn dieser nicht bereits mit einem verknüpft ist. Der Besitz des aktuellen Thread Proxys wird durch den Wert bestimmt, den Sie für das `switchState`-Argument angeben.

Verwenden Sie den Wert `Idle`, wenn Sie den derzeit ausgeführten Thread Proxy an den Ressourcen-Manager zurückgeben möchten. Das Aufrufen von `SwitchTo` mit dem-Parameter `switchState` auf `Idle` festgelegt, bewirkt, dass der Ausführungs Kontext `pContext` für die zugrunde liegende Ausführungs Ressource ausgeführt wird. Der Besitz dieses Thread Proxys wird an die Ressourcen-Manager übertragen, und Sie werden davon ausgehen, dass die `Dispatch`-Methode des Ausführungs Kontexts bald nach der Rückgabe `SwitchTo` zurückgegeben wird, um die Übertragung abzuschließen. Der Ausführungs Kontext, den der Thread Proxy weiterleitet, wird von dem Thread Proxy getrennt, und der Scheduler kann ihn wieder verwenden oder zerstören, wie er passt.

Verwenden Sie den Wert `Blocking`, wenn Sie möchten, dass dieser Thread Proxy in einen blockierten Zustand wechselt. Wenn Sie `SwitchTo` mit dem-Parameter aufrufen, `switchState` auf `Blocking` festgelegt ist, wird die Ausführung des Ausführungs Kontexts `pContext`, und der aktuelle Thread Proxy wird blockiert, bis die Wiederaufnahme erfolgt. Der Scheduler behält den Besitz des Thread Proxys bei, wenn sich der Thread Proxy im `Blocking` Zustand befindet. Die Ausführung des blockierten Threadproxys kann fortgesetzt werden, indem die `SwitchTo`-Funktion aufgerufen wird, um zum Ausführungskontext dieses Threadproxys zu wechseln. Sie können den Threadproxy auch fortsetzen, indem Sie dessen zugeordneten Kontext verwenden, um den Stamm eines virtuellen Prozessors zu aktivieren. Weitere Informationen hierzu finden Sie unter [IVirtualProcessorRoot:: Aktivierung](ivirtualprocessorroot-structure.md#activate).

Verwenden Sie den Wert `Nesting`, wenn Sie diesen Thread Proxy temporär vom Stamm des virtuellen Prozessors trennen möchten, auf dem er ausgeführt wird, und dem Scheduler, für den die Arbeit verteilt wird. Wenn Sie `SwitchTo` mit dem-Parameter aufrufen, `switchState` auf `Nesting` festgelegt ist, wird die Ausführung des Ausführungs Kontexts `pContext`, und der aktuelle Thread Proxy wird auch weiterhin ausgeführt, ohne dass ein virtueller Prozessor Stamm benötigt wird. Der Thread Proxy hat den Scheduler verlassen, bis die [IThreadProxy:: SwitchOut](#switchout) -Methode zu einem späteren Zeitpunkt aufgerufen wird. Die `IThreadProxy::SwitchOut`-Methode könnte den Thread Proxy blockieren, bis ein virtueller Prozessor Stamm verfügbar ist, um ihn erneut zu planen.

`SwitchTo` muss für die `IThreadProxy`-Schnittstelle aufgerufen werden, die den gerade ausgeführten Thread darstellt, oder die Ergebnisse sind nicht definiert. Die-Funktion löst `invalid_argument` aus, wenn der Parameter `pContext` auf `NULL`festgelegt ist.

## <a name="yieldtosystem"></a>IThreadProxy:: yielddesystem-Methode

Bewirkt, dass der aufrufende Thread die Ausführung an einen anderen Thread übergibt, der auf dem aktuellen Prozessor ausgeführt werden kann. Das Betriebssystem wählt den nächsten Thread aus, der ausgeführt werden soll.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie von einem Thread Proxy aufgerufen wird, der durch einen regulären Windows-Thread gesichert wird, verhält sich `YieldToSystem` genau wie die Windows-Funktion `SwitchToThread`. Beim Aufrufen aus dem Benutzermodus (ums)-Threads delegiert die `SwitchToThread`-Funktion jedoch den Task, der den nächsten Thread zur Laufzeit an den Benutzermodus-Scheduler, nicht das Betriebssystem, abwählt. Verwenden Sie `YieldToSystem`, um den gewünschten Effekt zu erzielen, wenn Sie zu einem anderen bereiten Thread im System wechseln.

`YieldToSystem` muss für die `IThreadProxy`-Schnittstelle aufgerufen werden, die den gerade ausgeführten Thread darstellt, oder die Ergebnisse sind nicht definiert.

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IExecutionContext-Struktur](iexecutioncontext-structure.md)<br/>
[IScheduler-Struktur](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)
