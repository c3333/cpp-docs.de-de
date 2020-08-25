---
title: concurrency-Namespace-Enumerationen
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: 8b9aec0a3464b921ca80f731ac4a3c26e72ef34e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832242"
---
# <a name="concurrency-namespace-enums"></a>concurrency-Namespace-Enumerationen

:::row:::
   :::column span="":::
      [`agent_status`](#agent_status)\
      [`Agents_EventType`](#agents_eventtype)\
      [`ConcRT_EventType`](#concrt_eventtype)\
      [`Concrt_TraceFlags`](#concrt_traceflags)\
      [`CriticalRegionType`](#criticalregiontype)
   :::column-end:::
   :::column span="":::
      [`DynamicProgressFeedbackType`](#dynamicprogressfeedbacktype)\
      [`join_type`](#join_type)\
      [`message_status`](#message_status)\
      [`PolicyElementKey`](#policyelementkey)\
      [`SchedulerType`](#schedulertype)
   :::column-end:::
   :::column span="":::
      [`SchedulingProtocolType`](#schedulingprotocoltype)\
      [`SwitchingProxyState`](#switchingproxystate)\
      [`task_group_status`](#task_group_status)\
      [`WinRTInitializationType`](#winrtinitializationtype)
   :::column-end:::
:::row-end:::

## <a name="agent_status-enumeration"></a><a name="agent_status"></a> Agent_status-Enumeration

Die gültigen Zustände für einen `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`agent_canceled`|Das `agent` wurde abgebrochen.|
|`agent_created`|Der wurde `agent` erstellt, aber nicht gestartet.|
|`agent_done`|Der `agent` wurde beendet, ohne abgebrochen zu werden.|
|`agent_runnable`|Der wurde `agent` gestartet, aber seine-Methode wurde nicht eingegeben `run` .|
|`agent_started`|Der `agent` wurde gestartet.|

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [asynchrone Agents](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a> Agents_EventType-Enumeration

Die Typen von Ereignissen, die mit der von der Agents Library angebotenen Ablaufverfolgungsfunktionalität aufgezeichnet werden können

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Ein Ereignistyp, der die Erstellung eines Objekts darstellt.|
|`AGENTS_EVENT_DESTROY`|Ein Ereignistyp, der das Löschen eines Objekts darstellt.|
|`AGENTS_EVENT_END`|Ein Ereignistyp, der das Ende einer Verarbeitung darstellt.|
|`AGENTS_EVENT_LINK`|Ein Ereignistyp, der die Verknüpfung von Nachrichten Blöcken darstellt.|
|`AGENTS_EVENT_NAME`|Ein Ereignistyp, der den Namen für ein Objekt darstellt.|
|`AGENTS_EVENT_SCHEDULE`|Ein Ereignistyp, der die Planung eines Prozesses darstellt.|
|`AGENTS_EVENT_START`|Ein Ereignistyp, der die Initiierung einer Verarbeitung darstellt.|
|`AGENTS_EVENT_UNLINK`|Ein Ereignistyp, der das Aufheben der Verknüpfung von Nachrichten Blöcken darstellt.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a> ConcRT_EventType-Enumeration

Die Typen von Ereignissen, die mit der von der Concurrency Runtime angebotenen Ablaufverfolgungsfunktionalität aufgezeichnet werden können.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Ein Ereignistyp, der den Vorgang eines Anfügens an einen Planer darstellt.|
|`CONCRT_EVENT_BLOCK`|Ein Ereignistyp, der den Act einer Kontext Blockierung darstellt.|
|`CONCRT_EVENT_DETACH`|Ein Ereignistyp, der den Vorgang einer Trennung von einem Zeit Planungs Modul darstellt.|
|`CONCRT_EVENT_END`|Ein Ereignistyp, der den Anfang eines Start-/endereignispaars markiert.|
|`CONCRT_EVENT_GENERIC`|Ein Ereignistyp, der für verschiedene Ereignisse verwendet wird.|
|`CONCRT_EVENT_IDLE`|Ein Ereignistyp, der den Vorgang eines Kontexts darstellt, der sich im Leerlauf befindet.|
|`CONCRT_EVENT_START`|Ein Ereignistyp, der den Anfang eines Start-/endereignispaars markiert.|
|`CONCRT_EVENT_UNBLOCK`|Ein Ereignistyp, der den Vorgang der Aufhebung der Blockierung eines Kontexts darstellt.|
|`CONCRT_EVENT_YIELD`|Ein Ereignistyp, der den Act eines Kontexts darstellt, der ergibt.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h- **Namespace:** Parallelität

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a> Concrt_TraceFlags-Enumeration

Ablaufverfolgungskennzeichen für die Ereignistypen

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a> CriticalRegionType-Enumeration

Der Typ eines kritischen Bereichs, in dem sich ein Kontext befindet.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`InsideCriticalRegion`|Gibt an, dass sich der Kontext innerhalb eines kritischen Bereichs befindet. Wenn Sie sich innerhalb eines kritischen Bereichs befinden, werden asynchrone Suspendierungen im Scheduler ausgeblendet. Sollte eine solche Unterbrechung stattfinden, wartet der Ressourcen-Manager auf die Ausführung des Threads und setzt ihn einfach fort, anstatt den Scheduler erneut aufzurufen. Alle Sperren, die innerhalb einer solchen Region durchgeführt werden, müssen mit größter Sorgfalt durchgeführt werden.|
|`InsideHyperCriticalRegion`|Gibt an, dass sich der Kontext innerhalb eines hyperkritischen Bereichs befindet. Wenn Sie sich innerhalb eines hyperkritischen Bereichs befinden, werden sowohl synchrone als auch asynchrone Suspendierungen im Scheduler ausgeblendet. Sollte eine solche Unterbrechung oder Blockierung auftreten, wartet der Ressourcen-Manager, bis der Thread in die ausführbare Datei aufgenommen wird, und setzt ihn einfach fort, anstatt den Scheduler erneut aufzurufen. Innerhalb eines solchen Bereichs ergriffene Sperren dürfen niemals für Code freigegeben werden, der außerhalb einer solchen Region ausgeführt wird. Dies führt zu unvorhersehbarem Deadlock.|
|`OutsideCriticalRegion`|Gibt an, dass der Kontext außerhalb eines beliebigen kritischen Bereichs liegt.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concrtrm. h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a> DynamicProgressFeedbackType-Enumeration

Wird von der `DynamicProgressFeedback`-Richtlinie verwendet, um zu beschreiben, ob Ressourcen für den Planer anhand statistischer Informationen neu verteilt werden, die vom Planer oder nur auf Grundlage virtueller Prozessoren erfasst wurden, die wegen der Aufrufe der `Activate`-Methode und der `Deactivate`-Methode für die `IVirtualProcessorRoot`-Schnittstelle in den und aus dem Leerlauf wechseln. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Der Scheduler sammelt keine Statusinformationen. Der Ausgleich erfolgt ausschließlich basierend auf der Abonnement Ebene des zugrunde liegenden Hardware Threads. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](IExecutionResource-structure.md).<br /><br /> Dieser Wert ist für die Verwendung durch die Laufzeit reserviert.|
|`ProgressFeedbackEnabled`|Der Scheduler sammelt Statusinformationen und übergibt sie an den Ressourcen-Manager. Der Ressourcen-Manager verwendet diese statistischen Informationen, um die Ressourcen im Auftrag des Zeit Planungs Moduls zusätzlich zur Abonnement Ebene des zugrunde liegenden Hardware Threads auszugleichen. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](IExecutionResource-structure.md).|

## <a name="join_type-enumeration"></a><a name="join_type"></a> join_type-Enumeration

Der Typ eines `join`-Meldungsblocks.

```cpp
enum join_type;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`greedy`|Gierige `join` Messaging Blöcke akzeptieren sofort eine Nachricht bei der Propagierung. Dies ist effizienter, aber abhängig von der Netzwerkkonfiguration besteht die Möglichkeit, eine Live Sperre zu erhalten.|
|`non_greedy`|Nicht gierige `join` Messaging Blöcke verschieben Nachrichten und verwenden Sie, nachdem Sie alle angekommen sind. Diese werden garantiert funktionieren, aber langsamer.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a> Message_status-Enumeration

Die gültigen Antworten für das Angebot eines `message`-Objekts für einen Block.

```cpp
enum message_status;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`accepted`|Das Ziel hat die Nachricht akzeptiert.|
|`declined`|Das Ziel hat die Nachricht nicht akzeptiert.|
|`missed`|Das Ziel hat versucht, die Nachricht zu akzeptieren, war aber nicht mehr verfügbar.|
|`postponed`|Das Ziel hat die Nachricht verschoben.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a> PolicyElementKey-Enumeration

Richtlinienschlüssel, die Aspekte des Planerverhaltens beschreiben. Jedes Richtlinienelement wird mit einem Schlüssel-Wert-Paar beschrieben. Weitere Informationen zu planerrichtlinien und deren Auswirkungen auf Planer finden Sie unter [Taskplaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`ContextPriority`|Die Thread Priorität des Betriebssystems für jeden Kontext im Scheduler. Wenn dieser Schlüssel auf den Wert festgelegt ist, `INHERIT_THREAD_PRIORITY` erben die Kontexte im Scheduler die Priorität des Threads, der den Scheduler erstellt hat.<br /><br /> Gültige Werte: gültige Werte für die Windows `SetThreadPriority` -Funktion und den besonderen Wert `INHERIT_THREAD_PRIORITY`<br /><br /> Standardwert: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Die reservierte Stapelgröße jedes Kontexts im Scheduler in Kilobyte.<br /><br /> Gültige Werte: positive ganze Zahlen<br /><br /> Standardwert: `0` , gibt an, dass der Standardwert des Prozesses für die Stapelgröße verwendet werden soll.|
|`DynamicProgressFeedback`|Bestimmt, ob die Ressourcen für den Scheduler gemäß den statistischen Informationen, die vom Scheduler gesammelt werden, oder nur basierend auf der Abonnement Ebene der zugrunde liegenden Hardwarethreads ausgeglichen werden. Weitere Informationen finden Sie unter [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Gültige Werte: ein Member der- `DynamicProgressFeedbackType` Enumeration, entweder `ProgressFeedbackEnabled` oder. `ProgressFeedbackDisabled`<br /><br /> Standardwert: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Wenn der `SchedulingProtocol` Richtlinien Schlüssel auf den Wert festgelegt ist `EnhanceScheduleGroupLocality` , gibt dies die maximale Anzahl von ausführbaren Kontexten an, die in den lokalen Warteschlangen des virtuellen Prozessors zwischengespeichert werden dürfen. Diese Kontexte werden in der Regel in der LIFO-Reihenfolge (Last-in-First-Out) des virtuellen Prozessors ausgeführt, der bewirkt hat, dass Sie ausgeführt werden können. Beachten Sie, dass dieser Richtlinien Schlüssel keine Bedeutung hat, wenn der `SchedulingProtocol` Schlüssel auf den Wert festgelegt ist `EnhanceForwardProgress` .<br /><br /> Gültige Werte: nicht negative ganze Zahlen<br /><br /> Standardwert: `8`|
|`MaxConcurrency`|Die vom Planer gewünschte maximale Parallelitäts Ebene. Der Ressourcen-Manager versucht, diese vielen virtuellen Prozessoren anfänglich zuzuordnen. Der spezielle Wert [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) gibt an, dass die gewünschte Parallelitäts Ebene mit der Anzahl der Hardwarethreads auf dem Computer übereinstimmt. Wenn der für angegebene Wert `MinConcurrency` größer als die Anzahl der Hardwarethreads auf dem Computer ist und `MaxConcurrency` als angegeben wird `MaxExecutionResources` , wird der Wert für `MaxConcurrency` ausgelöst, um den für festgelegten Wert abzugleichen `MinConcurrency` .<br /><br /> Gültige Werte: positive ganze Zahlen und der besondere Wert `MaxExecutionResources`<br /><br /> Standardwert: `MaxExecutionResources`|
|`MaxPolicyElementKey`|Der maximale Richtlinien Element Schlüssel. Kein gültiger Element Schlüssel.|
|`MinConcurrency`|Die minimale Parallelitäts Ebene, die dem Scheduler vom Ressourcen-Manager bereitgestellt werden muss. Die Anzahl virtueller Prozessoren, die einem Scheduler zugewiesen sind, geht nie unter den Minimalwert über. Der spezielle Wert [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) gibt an, dass die minimale Parallelitäts Ebene der Anzahl der Hardwarethreads auf dem Computer entspricht. Wenn der für angegebene Wert `MaxConcurrency` kleiner als die Anzahl der Hardwarethreads auf dem Computer ist und `MinConcurrency` als angegeben wird `MaxExecutionResources` , wird der Wert für `MinConcurrency` gesenkt, damit er mit dem für festgelegten `MaxConcurrency` Wert identisch ist.<br /><br /> Gültige Werte: nicht negative ganze Zahlen und der spezielle Wert `MaxExecutionResources` . Beachten Sie, dass der Wert für Scheduler-Richtlinien, die für die Erstellung von Concurrency Runtime Schedulern verwendet werden, `0` ungültig ist.<br /><br /> Standardwert: `1`|
|`SchedulerKind`|Der Typ der Threads, die vom Scheduler für zugrunde liegende Ausführungs Kontexte verwendet werden. Weitere Informationen finden Sie unter [SchedulerType](#schedulertype).<br /><br /> Gültige Werte: ein Member der- `SchedulerType` Enumeration, z. b. `ThreadScheduler`<br /><br /> Standardwert: `ThreadScheduler` . Dies bedeutet, dass Win32-Threads auf allen Betriebssystemen ausgeführt werden.|
|`SchedulingProtocol`|Beschreibt den Zeit Planungs Algorithmus, der vom Scheduler verwendet wird. Weitere Informationen finden Sie unter [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Gültige Werte: ein Member der- `SchedulingProtocolType` Enumeration, entweder `EnhanceScheduleGroupLocality` oder. `EnhanceForwardProgress`<br /><br /> Standardwert: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Vorläufige Anzahl virtueller Prozessoren pro Hardware Thread. Der Faktor für das Ziel überschreitungs Ziel kann durch die Ressourcen-Manager erweitert werden, falls erforderlich, um `MaxConcurrency` die Hardware Threads auf dem Computer zu erfüllen.<br /><br /> Gültige Werte: positive ganze Zahlen<br /><br /> Standardwert: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a> SchedulerType-Enumeration

Wird von der `SchedulerKind`-Richtlinie verwendet, um den Typ der Threads zu beschreiben, die der Planer für zugrunde liegende Ausführungskontexte verwenden soll. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`ThreadScheduler`|Gibt eine explizite Anforderung von regulären Win32-Threads an.|
|`UmsThreadDefault`|In der Concurrency Runtime in Visual Studio 2013 werden im Benutzermodus planbare Threads (ums) nicht unterstützt. Das Verwenden von `UmsThreadDefault` als ein Wert für die `SchedulerType`-Richtlinie führt zu keinem Fehler. Ein Planer, der mit dieser Richtlinie erstellt wurde, wird jedoch standardmäßig Win32-Threads verwenden.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a> SchedulingProtocolType-Enumeration

Wird von der `SchedulingProtocol`-Richtlinie verwendet, um zu beschreiben, welcher Planungsalgorithmus für den Planer verwendet wird. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`EnhanceForwardProgress`|Nach dem Ausführen der einzelnen Aufgaben wird vom Scheduler vor dem Ausführen der einzelnen Aufgaben eine Roundrobin-Schleife durch geplant Nicht blockierte Kontexte werden in der Regel in einem FIFO-Prinzip (First-in-First-Out) geplant. Nicht blockierte Kontexte werden von virtuellen Prozessoren nicht zwischengespeichert.|
|`EnhanceScheduleGroupLocality`|Der Planer bevorzugt die Arbeit an Aufgaben innerhalb der aktuellen Zeit Plan Gruppe, bevor er zu einer anderen Zeit Plan Gruppe wechselt. Nicht blockierte Kontexte werden pro virtuellem Prozessor zwischengespeichert und in der Regel in der LIFO-Weise (Last-in-First-Out) des virtuellen Prozessors geplant, die die Blockierung aufgehoben hat.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a> SwitchingProxyState-Enumeration

Wird verwendet, um den Zustand zu bezeichnen, in dem sich ein Threadproxy befindet, wenn er einen kooperativen Kontextwechsel zu einem anderen Threadproxy ausführt.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`Blocking`|Gibt an, dass der aufrufende Thread kooperativ blockiert und ausschließlich im Besitz des Aufrufers sein sollte, bis er erneut ausgeführt und andere Aktionen ausführt.|
|`Idle`|Gibt an, dass der aufrufende Thread vom Scheduler nicht mehr benötigt wird und an den Ressourcen-Manager zurückgegeben wird. Der Kontext, der gesendet wurde, kann vom Ressourcen-Manager nicht mehr verwendet werden.|
|`Nesting`|Gibt an, dass der aufrufende Thread einen untergeordneten Planer verschachtelt und vom Aufrufer benötigt wird, um ihn an einen anderen Planer anzufügen.|

### <a name="remarks"></a>Bemerkungen

Ein Parameter vom Typ `SwitchingProxyState` wird an die-Methode übergeben `IThreadProxy::SwitchTo` , um den Ressourcen-Manager zu weisen, wie der Thread Proxy, der den-Befehl aufruft, behandelt werden soll.

Weitere Informationen zur Verwendung dieses Typs finden [Sie unter IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a> Task_group_status-Enumeration

Beschreibt den Ausführungsstatus eines `task_group`-Objekts oder eines `structured_task_group`-Objekts. Ein Wert dieses Typs wird von zahlreichen Methoden zurückgegeben, die auf den Abschluss von Aufgaben warten, die für eine Aufgabengruppe geplant wurden.

```cpp
enum task_group_status;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`canceled`|Das `task_group`- oder `structured_task_group`-Objekt wurde abgebrochen. Eine oder mehrere Aufgaben wurden möglicherweise nicht ausgeführt.|
|`completed`|Die für das `task_group`-Objekt oder das `structured_task_group`-Objekt in die Warteschlange gestellten Aufgaben wurden erfolgreich abgeschlossen.|
|`not_complete`|Die für das `task_group`-Objekt in die Warteschlange gestellten Aufgaben wurden nicht abgeschlossen. Beachten Sie, dass dieser Wert gegenwärtig von der Concurrency Runtime nicht zurückgegeben wird.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** pplinterface. h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a> Winrtinitializationtype-Enumeration

Wird von der `WinRTInitialization`-Richtlinie verwendet, um zu beschreiben, ob und wie die Windows Runtime auf Planerthreads für eine Anwendung initialisiert wird, die auf Windows-Betriebssystemen ab Version 8 ausgeführt wird. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`DoNotInitializeWinRT`|Wenn die Anwendung auf Windows 8 oder neueren Betriebssystemen ausgeführt wird, initialisieren Threads innerhalb des Planers nicht Windows-Runtime.|
|`InitializeWinRTAsMTA`|Wenn die Anwendung unter Windows 8 oder neueren Betriebssystemen ausgeführt wird, initialisiert jeder Thread innerhalb des Planers Windows-Runtime und deklariert, dass er Teil des Multithread-Apartments ist.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)
