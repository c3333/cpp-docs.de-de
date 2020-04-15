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
ms.openlocfilehash: fc2fb2df06225a5c963fe39178c1b4a10f77953d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368132"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy-Struktur

Eine Abstraktion für einen Thread der Ausführung. Abhängig von dem von Ihnen erstellten `SchedulerType`-Richtlinienschlüssel des Planers, gewährt der Ressourcen-Manager eine Threadproxy, der entweder von einem regulären Win32-Thread oder einem im Benutzermodus planbaren (UMS) Thread unterstützt wird. UMS-Threads werden auf 64-Bit-Betriebssystemen mit Version Windows 7 und höher unterstützt.

## <a name="syntax"></a>Syntax

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IThreadProxy::GetId](#getid)|Gibt einen eindeutigen Bezeichner für den Threadproxy zurück.|
|[IThreadProxy::SwitchOut](#switchout)|Hebt die Zuordnung des Kontexts vom zugrunde liegenden virtuellen Prozessorstamm auf.|
|[IThreadProxy::SwitchTo](#switchto)|Führt einen kooperativen Kontextwechsel aus dem aktuell ausgeführten Kontext zu einem anderen Kontext aus.|
|[IThreadProxy::YieldToSystem](#yieldtosystem)|Bewirkt, dass der aufrufende Thread die Ausführung an einen anderen Thread übergibt, der auf dem aktuellen Prozessor ausgeführt werden kann. Das Betriebssystem wählt den nächsten auszuführenden Thread aus.|

## <a name="remarks"></a>Bemerkungen

Threadproxys werden an Ausführungskontexte gekoppelt, die von der Schnittstelle `IExecutionContext` als Mittel zum Dispatchen von Arbeit dargestellt werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IThreadProxy`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

**Namespace:** Parallelität

## <a name="ithreadproxygetid-method"></a><a name="getid"></a>IThreadProxy::GetId-Methode

Gibt einen eindeutigen Bezeichner für den Threadproxy zurück.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein eindeutiger Ganzzahlbezeichner.

## <a name="ithreadproxyswitchout-method"></a><a name="switchout"></a>IThreadProxy::SwitchOut-Methode

Hebt die Zuordnung des Kontexts vom zugrunde liegenden virtuellen Prozessorstamm auf.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Parameter

*switchState*<br/>
Gibt den Zustand des Threadproxys an, der den Wechsel ausführt. Der Parameter ist vom Typ `SwitchingProxyState`.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `SwitchOut`, wenn Sie aus irgendeinem Grund die Zuordnung eines Kontexts zu einem virtuellen Prozessorstamm aufheben müssen, in dem dieser ausgeführt wird. Je nachdem, welchen Wert Sie an den `switchState`-Parameter übergeben, und abhängig von dessen Ausführung auf einem virtuellen Prozessorstamm, wird der Aufruf entweder sofort zurückgegeben oder der dem Kontext zugeordnete Threadproxy wird blockiert. Es ist nicht zulässig, `SwitchOut` aufzurufen, wenn der Parameter auf `Idle` festgelegt ist. Dies führt zu einer [invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme.

`SwitchOut` ist nützlich, wenn Sie die Anzahl der Stämme virtueller Prozessoren für den Planer verringern möchten, da der Ressourcen-Manager Sie angewiesen hat, dies zu tun oder Sie den Stamm eines überzeichneten temporären virtuellen Prozessors angefordert haben und diesen nicht mehr benötigen. In diesem Fall sollten Sie die Methode [IVirtualProcessorRoot::Remove](iexecutionresource-structure.md#remove) auf dem `SwitchOut` virtuellen Prozessorstamm aufrufen, bevor Sie einen Aufruf mit dem Parameter `switchState` auf `Blocking`. Auf diese Weise wird der Threadproxy blockiert. Die Ausführung wird fortgesetzt, wenn im Planer ein anderer virtueller Prozessorstamm für die Ausführung verfügbar ist. Die Ausführung des blockierten Threadproxys kann fortgesetzt werden, indem die `SwitchTo`-Funktion aufgerufen wird, um zum Ausführungskontext dieses Threadproxys zu wechseln. Sie können den Threadproxy auch fortsetzen, indem Sie dessen zugeordneten Kontext verwenden, um den Stamm eines virtuellen Prozessors zu aktivieren. Weitere Informationen hierzu finden Sie unter [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

Sie können `SwitchOut` zudem verwenden, um den virtuellen Prozessor erneut zu initialisieren, damit dieser zukünftig aktiviert werden kann, wenn Sie den Threadproxy blockieren oder vorübergehend vom Stamm des virtuellen Prozessors, für den dieser ausgeführt wird, und vom Planer, für den er Arbeit verteilt, trennen möchten. Verwenden Sie `SwitchOut` mit dem auf `switchState` festgelegten `Blocking`-Parameter, wenn Sie den Threadproxy blockieren möchten. Wie oben beschrieben, kann er zu einem späteren Zeitpunkt mithilfe von `SwitchTo` oder `IVirtualProcessorRoot::Activate` fortgesetzt werden. Verwenden Sie `SwitchOut` mit dem auf `Nesting` festgelegten Parameter, wenn Sie diesen Threadproxy vorübergehend vom Stamm des virtuellen Prozessors, auf dem er ausgeführt wird, und vom Planer, dem der virtuelle Prozessor zugeordnet ist, trennen möchten. Das Aufrufen von `SwitchOut` mit dem auf `switchState` festgelegten `Nesting`-Parameter führt während dessen Ausführung auf einem virtuellen Prozessorstamm zu einer erneuten Initialisierung des Stamms und zur Fortsetzung des aktuellen Threadproxys, obwohl dieser nicht erforderlich ist. Der Threadproxy wird als verlassen der Scheduler betrachtet, bis er die `Blocking` [IThreadProxy::SwitchOut-Methode](#switchout) mit einem späteren Zeitpunkt aufruft. Der zweite Aufruf von `SwitchOut` mit dem auf `Blocking` festgelegten Parameter soll den Kontext in einen blockierten Zustand zurückversetzen, damit er im Planer, von dem er getrennt ist, mit `SwitchTo` oder `IVirtualProcessorRoot::Activate` fortgesetzt werden kann. Da die Ausführung nicht auf einem virtuellen Prozessorstamm erfolgt, findet keine erneute Initialisierung statt.

Ein erneut initialisierter virtueller Prozessorstamm unterscheidet sich nicht von einem neuen virtuellen Prozessorstamm, der dem Planer vom Ressourcen-Manager gewährt wurde. Sie können ihn für die Ausführung verwenden, indem Sie ihn mit `IVirtualProcessorRoot::Activate` in einem Ausführungskontext aktivieren.

`SwitchOut` muss für die `IThreadProxy`-Schnittstelle aufgerufen werden, die den gerade ausgeführten Thread darstellt, oder die Ergebnisse sind nicht definiert.

In den Bibliotheken und Headern, die mit Visual Studio 2010 geliefert wurden, weist diese Methode keinen Parameter auf, und der virtuelle Prozessorstamm wurde nicht initialisiert. Um altes Verhalten beizubehalten, wird der Standardparameterwert von `Blocking` angegeben.

## <a name="ithreadproxyswitchto-method"></a><a name="switchto"></a>IThreadProxy::SwitchTo-Methode

Führt einen kooperativen Kontextwechsel aus dem aktuell ausgeführten Kontext zu einem anderen Kontext aus.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Parameter

*pContext*<br/>
Der Ausführungskontext, zu dem kooperativ gewechselt werden soll.

*switchState*<br/>
Gibt den Zustand des Threadproxys an, der den Wechsel ausführt. Der Parameter ist vom Typ `SwitchingProxyState`.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um von einem Ausführungskontext zu einem anderen zu wechseln, von der [IExecutionContext::Dispatch-Methode](iexecutioncontext-structure.md#dispatch) des ersten Ausführungskontexts. Die Methode ordnet `pContext` den Ausführungskontext einem Threadproxy zu, wenn er nicht bereits einem Threadproxy zugeordnet ist. Der Besitz des aktuellen Threadproxys wird durch `switchState` den Wert bestimmt, den Sie für das Argument angeben.

Verwenden Sie `Idle` den Wert, wenn Sie den aktuell ausgeführten Threadproxy an den Ressourcen-Manager zurückgeben möchten. Wenn `SwitchTo` der `switchState` Aufruf `Idle` mit dem Parameter `pContext` set to erfolgt, wird der Ausführungskontext für die zugrunde liegende Ausführungsressource ausgeführt. Der Besitz dieses Threadproxys wird an den Ressourcen-Manager übertragen, und `Dispatch` es `SwitchTo` wird erwartet, dass Sie kurz nach der Rückgabe von der Ausführungskontextmethode zurückkehren, um die Übertragung abzuschließen. Der Ausführungskontext, den der Threadproxy ausgelöst hat, wird vom Threadproxy getrennt, und der Planer kann ihn nach Belieben wiederverwenden oder zerstören.

Verwenden Sie `Blocking` den Wert, wenn dieser Threadproxy in einen blockierten Zustand gelangen soll. Wenn `SwitchTo` der `switchState` Aufruf `Blocking` mit dem Parameter `pContext` set to erfolgt, wird der Ausführungskontext ausgeführt und der aktuelle Threadproxy blockiert, bis er fortgesetzt wird. Der Planer behält den Besitz des Threadproxys bei, wenn sich der Threadproxy im `Blocking` Status befindet. Die Ausführung des blockierten Threadproxys kann fortgesetzt werden, indem die `SwitchTo`-Funktion aufgerufen wird, um zum Ausführungskontext dieses Threadproxys zu wechseln. Sie können den Threadproxy auch fortsetzen, indem Sie dessen zugeordneten Kontext verwenden, um den Stamm eines virtuellen Prozessors zu aktivieren. Weitere Informationen hierzu finden Sie unter [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

Verwenden Sie `Nesting` den Wert, wenn Sie diesen Threadproxy vorübergehend vom Stamm des virtuellen Prozessors trennen möchten, auf dem er ausgeführt wird, und den Planer, für den er Arbeit auslöst. Wenn `SwitchTo` der `switchState` Aufruf `Nesting` mit dem Parameter `pContext` set to erfolgt, wird der Ausführungskontext ausgeführt, und der aktuelle Threadproxy wird ebenfalls ausgeführt, ohne dass ein virtueller Prozessorstamm erforderlich ist. Der Threadproxy wird als verlassen, bis er die [IThreadProxy::SwitchOut-Methode](#switchout) zu einem späteren Zeitpunkt aufruft. Die `IThreadProxy::SwitchOut` Methode kann den Threadproxy blockieren, bis ein virtueller Prozessorstamm verfügbar ist, um ihn neu zu planen.

`SwitchTo` muss für die `IThreadProxy`-Schnittstelle aufgerufen werden, die den gerade ausgeführten Thread darstellt, oder die Ergebnisse sind nicht definiert. Die Funktion `invalid_argument` wird `pContext` ausgelöst, `NULL`wenn der Parameter auf festgelegt ist.

## <a name="ithreadproxyyieldtosystem-method"></a><a name="yieldtosystem"></a>IThreadProxy::YieldToSystem-Methode

Bewirkt, dass der aufrufende Thread die Ausführung an einen anderen Thread übergibt, der auf dem aktuellen Prozessor ausgeführt werden kann. Das Betriebssystem wählt den nächsten auszuführenden Thread aus.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Bemerkungen

Wenn sie von einem Threadproxy aufgerufen `YieldToSystem` werden, der von einem `SwitchToThread`regulären Windows-Thread unterstützt wird, verhält es sich genau wie die Windows-Funktion . Wenn die `SwitchToThread` Funktion jedoch von UMS-Threads (User-Mode schedulable) aufgerufen wird, delegiert sie die Aufgabe, den nächsten Thread auszuwählen, der an den Benutzermodusplaner und nicht an das Betriebssystem ausgeführt werden soll. Um den gewünschten Effekt des Umschaltens auf einen `YieldToSystem`anderen bereiten Faden im System zu erzielen, verwenden Sie .

`YieldToSystem` muss für die `IThreadProxy`-Schnittstelle aufgerufen werden, die den gerade ausgeführten Thread darstellt, oder die Ergebnisse sind nicht definiert.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[IExecutionContext-Struktur](iexecutioncontext-structure.md)<br/>
[IScheduler-Struktur](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)
