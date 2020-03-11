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
ms.openlocfilehash: 716c2d03e6d1ff67566bd28e5931996ea2d400af
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854160"
---
# <a name="concurrency-namespace-enums"></a>concurrency-Namespace-Enumerationen

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status"></a>Agent_status-Enumeration

Die gültigen Zustände für einen `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`agent_canceled`|Das `agent` wurde abgebrochen.|
|`agent_created`|Der `agent` wurde erstellt, aber nicht gestartet.|
|`agent_done`|Die `agent` beendet, ohne abgebrochen zu werden.|
|`agent_runnable`|Der `agent` wurde gestartet, aber seine `run`-Methode wurde nicht eingegeben.|
|`agent_started`|Der `agent` wurde gestartet.|

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [asynchrone Agents](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="agents_eventtype"></a>Agents_EventType-Enumeration

Die Typen von Ereignissen, die mit der von der Agents Library angebotenen Ablaufverfolgungsfunktionalität aufgezeichnet werden können

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
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

## <a name="concrt_eventtype"></a>ConcRT_EventType-Enumeration

Die Typen von Ereignissen, die mit der von der Concurrency Runtime angebotenen Ablaufverfolgungsfunktionalität aufgezeichnet werden können.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
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

## <a name="concrt_traceflags"></a>Concrt_TraceFlags-Enumeration

Ablaufverfolgungskennzeichen für die Ereignistypen

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
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

## <a name="criticalregiontype"></a>CriticalRegionType-Enumeration

Der Typ eines kritischen Bereichs, in dem sich ein Kontext befindet.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`InsideCriticalRegion`|Gibt an, dass sich der Kontext innerhalb eines kritischen Bereichs befindet. Wenn Sie sich innerhalb eines kritischen Bereichs befinden, werden asynchrone Suspendierungen im Scheduler ausgeblendet. Sollte eine solche Unterbrechung stattfinden, wartet der Ressourcen-Manager auf die Ausführung des Threads und setzt ihn einfach fort, anstatt den Scheduler erneut aufzurufen. Alle Sperren, die innerhalb einer solchen Region durchgeführt werden, müssen mit größter Sorgfalt durchgeführt werden.|
|`InsideHyperCriticalRegion`|Gibt an, dass sich der Kontext innerhalb eines hyperkritischen Bereichs befindet. Wenn Sie sich innerhalb eines hyperkritischen Bereichs befinden, werden sowohl synchrone als auch asynchrone Suspendierungen im Scheduler ausgeblendet. Sollte eine solche Unterbrechung oder Blockierung auftreten, wartet der Ressourcen-Manager, bis der Thread in die ausführbare Datei aufgenommen wird, und setzt ihn einfach fort, anstatt den Scheduler erneut aufzurufen. Innerhalb eines solchen Bereichs ergriffene Sperren dürfen niemals für Code freigegeben werden, der außerhalb einer solchen Region ausgeführt wird. Dies führt zu unvorhersehbarem Deadlock.|
|`OutsideCriticalRegion`|Gibt an, dass der Kontext außerhalb eines beliebigen kritischen Bereichs liegt.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concrtrm. h

## <a name="dynamicprogressfeedbacktype"></a>DynamicProgressFeedbackType-Enumeration

Wird von der `DynamicProgressFeedback`-Richtlinie verwendet, um zu beschreiben, ob Ressourcen für den Planer anhand statistischer Informationen neu verteilt werden, die vom Planer oder nur auf Grundlage virtueller Prozessoren erfasst wurden, die wegen der Aufrufe der `Activate`-Methode und der `Deactivate`-Methode für die `IVirtualProcessorRoot`-Schnittstelle in den und aus dem Leerlauf wechseln. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Der Scheduler sammelt keine Statusinformationen. Der Ausgleich erfolgt ausschließlich basierend auf der Abonnement Ebene des zugrunde liegenden Hardware Threads. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](IExecutionResource-structure.md).<br /><br /> Dieser Wert ist für die Verwendung durch die Laufzeit reserviert.|
|`ProgressFeedbackEnabled`|Der Scheduler sammelt Statusinformationen und übergibt sie an den Ressourcen-Manager. Der Ressourcen-Manager verwendet diese statistischen Informationen, um die Ressourcen im Auftrag des Zeit Planungs Moduls zusätzlich zur Abonnement Ebene des zugrunde liegenden Hardware Threads auszugleichen. Weitere Informationen zu Abonnement Ebenen finden Sie unter [IExecutionResource:: currentabonneptionlevel](IExecutionResource-structure.md).|

## <a name="join_type"></a>join_type-Enumeration

Der Typ eines `join`-Meldungsblocks.

```cpp
enum join_type;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`greedy`|Gierige `join` Messaging Blöcke akzeptieren sofort eine Nachricht bei der Propagierung. Dies ist effizienter, aber abhängig von der Netzwerkkonfiguration besteht die Möglichkeit, eine Live Sperre zu erhalten.|
|`non_greedy`|Nicht gierige `join` Messaging blockiert das Verschieben von Nachrichten und den Versuch, Sie zu verarbeiten, nachdem alle angekommen sind. Diese werden garantiert funktionieren, aber langsamer.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

## <a name="message_status"></a>Message_status-Enumeration

Die gültigen Antworten für das Angebot eines `message`-Objekts für einen Block.

```cpp
enum message_status;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`accepted`|Das Ziel hat die Nachricht akzeptiert.|
|`declined`|Das Ziel hat die Nachricht nicht akzeptiert.|
|`missed`|Das Ziel hat versucht, die Nachricht zu akzeptieren, war aber nicht mehr verfügbar.|
|`postponed`|Das Ziel hat die Nachricht verschoben.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

## <a name="policyelementkey"></a>PolicyElementKey-Enumeration

Richtlinienschlüssel, die Aspekte des Planerverhaltens beschreiben. Jedes Richtlinienelement wird mit einem Schlüssel-Wert-Paar beschrieben. Weitere Informationen zu planerrichtlinien und deren Auswirkungen auf Planer finden Sie unter [Taskplaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`ContextPriority`|Die Thread Priorität des Betriebssystems für jeden Kontext im Scheduler. Wenn dieser Schlüssel auf den Wert festgelegt ist `INHERIT_THREAD_PRIORITY` werden die Kontexte im Scheduler die Priorität des Threads erben, der den Scheduler erstellt hat.<br /><br /> Gültige Werte: gültige Werte für die Windows `SetThreadPriority`-Funktion und den besonderen Wert `INHERIT_THREAD_PRIORITY`<br /><br /> Standardwert: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Die reservierte Stapelgröße jedes Kontexts im Scheduler in Kilobyte.<br /><br /> Gültige Werte: positive ganze Zahlen<br /><br /> Standardwert: `0`, das angibt, dass der Standardwert des Prozesses für die Stapelgröße verwendet werden soll.|
|`DynamicProgressFeedback`|Bestimmt, ob die Ressourcen für den Scheduler gemäß den statistischen Informationen, die vom Scheduler gesammelt werden, oder nur basierend auf der Abonnement Ebene der zugrunde liegenden Hardwarethreads ausgeglichen werden. Weitere Informationen finden Sie unter [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Gültige Werte: ein Member der `DynamicProgressFeedbackType`-Enumeration, entweder `ProgressFeedbackEnabled` oder `ProgressFeedbackDisabled`<br /><br /> Standardwert: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Wenn der `SchedulingProtocol` Richtlinien Schlüssel auf den Wert `EnhanceScheduleGroupLocality`festgelegt ist, gibt dies die maximale Anzahl von ausführbaren Kontexten an, die in den lokalen Warteschlangen des virtuellen Prozessors zwischengespeichert werden dürfen. Diese Kontexte werden in der Regel in der LIFO-Reihenfolge (Last-in-First-Out) des virtuellen Prozessors ausgeführt, der bewirkt hat, dass Sie ausgeführt werden können. Beachten Sie, dass dieser Richtlinien Schlüssel keine Bedeutung hat, wenn der `SchedulingProtocol` Schlüssel auf den Wert `EnhanceForwardProgress`festgelegt ist.<br /><br /> Gültige Werte: nicht negative ganze Zahlen<br /><br /> Standardwert: `8`|
|`MaxConcurrency`|Die vom Planer gewünschte maximale Parallelitäts Ebene. Der Ressourcen-Manager versucht, diese vielen virtuellen Prozessoren anfänglich zuzuordnen. Der spezielle Wert [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) gibt an, dass die gewünschte Parallelitäts Ebene mit der Anzahl der Hardwarethreads auf dem Computer übereinstimmt. Wenn der für `MinConcurrency` angegebene Wert größer als die Anzahl der Hardwarethreads auf dem Computer und `MaxConcurrency` als `MaxExecutionResources`angegeben ist, wird der Wert für `MaxConcurrency` entsprechend der Einstellung für `MinConcurrency`ausgelöst.<br /><br /> Gültige Werte: positive ganze Zahlen und der besondere Wert `MaxExecutionResources`<br /><br /> Standardwert: `MaxExecutionResources`|
|`MaxPolicyElementKey`|Der maximale Richtlinien Element Schlüssel. Kein gültiger Element Schlüssel.|
|`MinConcurrency`|Die minimale Parallelitäts Ebene, die dem Scheduler vom Ressourcen-Manager bereitgestellt werden muss. Die Anzahl virtueller Prozessoren, die einem Scheduler zugewiesen sind, geht nie unter den Minimalwert über. Der spezielle Wert [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) gibt an, dass die minimale Parallelitäts Ebene der Anzahl der Hardwarethreads auf dem Computer entspricht. Wenn der für `MaxConcurrency` angegebene Wert kleiner als die Anzahl der Hardwarethreads auf dem Computer und `MinConcurrency` als `MaxExecutionResources`angegeben ist, wird der Wert für `MinConcurrency` verringert, damit er mit dem für `MaxConcurrency`festgelegten Wert identisch ist.<br /><br /> Gültige Werte: nicht negative ganze Zahlen und der besondere Wert `MaxExecutionResources`. Beachten Sie, dass der Wert `0` für Scheduler-Richtlinien, die für die Erstellung von Concurrency Runtime Schedulern verwendet werden, ungültig ist.<br /><br /> Standardwert: `1`|
|`SchedulerKind`|Der Typ der Threads, die vom Scheduler für zugrunde liegende Ausführungs Kontexte verwendet werden. Weitere Informationen finden Sie unter [SchedulerType](#schedulertype).<br /><br /> Gültige Werte: ein Member der `SchedulerType`-Enumeration, z. b. `ThreadScheduler`<br /><br /> Standardwert: `ThreadScheduler`. Dies bedeutet, dass Win32-Threads auf allen Betriebssystemen ausgeführt werden.|
|`SchedulingProtocol`|Beschreibt den Zeit Planungs Algorithmus, der vom Scheduler verwendet wird. Weitere Informationen finden Sie unter [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Gültige Werte: ein Member der `SchedulingProtocolType`-Enumeration, entweder `EnhanceScheduleGroupLocality` oder `EnhanceForwardProgress`<br /><br /> Standardwert: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Vorläufige Anzahl virtueller Prozessoren pro Hardware Thread. Der Faktor für den Ziel überabonnementfaktor kann bei Bedarf durch den Ressourcen-Manager angehoben werden, um `MaxConcurrency` mit den Hardwarethreads auf dem Computer zu erfüllen.<br /><br /> Gültige Werte: positive ganze Zahlen<br /><br /> Standardwert: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="schedulertype"></a>SchedulerType-Enumeration

Wird von der `SchedulerKind`-Richtlinie verwendet, um den Typ der Threads zu beschreiben, die der Planer für zugrunde liegende Ausführungskontexte verwenden soll. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`ThreadScheduler`|Gibt eine explizite Anforderung von regulären Win32-Threads an.|
|`UmsThreadDefault`|In der Concurrency Runtime in Visual Studio 2013 werden im Benutzermodus planbare Threads (ums) nicht unterstützt. Das Verwenden von `UmsThreadDefault` als ein Wert für die `SchedulerType`-Richtlinie führt zu keinem Fehler. Ein Planer, der mit dieser Richtlinie erstellt wurde, wird jedoch standardmäßig Win32-Threads verwenden.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="schedulingprotocoltype"></a>SchedulingProtocolType-Enumeration

Wird von der `SchedulingProtocol`-Richtlinie verwendet, um zu beschreiben, welcher Planungsalgorithmus für den Planer verwendet wird. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`EnhanceForwardProgress`|Nach dem Ausführen der einzelnen Aufgaben wird vom Scheduler vor dem Ausführen der einzelnen Aufgaben eine Roundrobin-Schleife durch geplant Nicht blockierte Kontexte werden in der Regel in einem FIFO-Prinzip (First-in-First-Out) geplant. Nicht blockierte Kontexte werden von virtuellen Prozessoren nicht zwischengespeichert.|
|`EnhanceScheduleGroupLocality`|Der Planer bevorzugt die Arbeit an Aufgaben innerhalb der aktuellen Zeit Plan Gruppe, bevor er zu einer anderen Zeit Plan Gruppe wechselt. Nicht blockierte Kontexte werden pro virtuellem Prozessor zwischengespeichert und in der Regel in der LIFO-Weise (Last-in-First-Out) des virtuellen Prozessors geplant, die die Blockierung aufgehoben hat.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="switchingproxystate"></a>SwitchingProxyState-Enumeration

Wird verwendet, um den Zustand zu bezeichnen, in dem sich ein Threadproxy befindet, wenn er einen kooperativen Kontextwechsel zu einem anderen Threadproxy ausführt.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`Blocking`|Gibt an, dass der aufrufende Thread kooperativ blockiert und ausschließlich im Besitz des Aufrufers sein sollte, bis er erneut ausgeführt und andere Aktionen ausführt.|
|`Idle`|Gibt an, dass der aufrufende Thread vom Scheduler nicht mehr benötigt wird und an den Ressourcen-Manager zurückgegeben wird. Der Kontext, der gesendet wurde, kann vom Ressourcen-Manager nicht mehr verwendet werden.|
|`Nesting`|Gibt an, dass der aufrufende Thread einen untergeordneten Planer verschachtelt und vom Aufrufer benötigt wird, um ihn an einen anderen Planer anzufügen.|

### <a name="remarks"></a>Bemerkungen

Ein Parameter vom Typ `SwitchingProxyState` wird an die-`IThreadProxy::SwitchTo` Methode übergeben, um den Ressourcen-Manager anzuweisen, wie der Thread Proxy, der den-Befehl aufruft, behandelt werden soll.

Weitere Informationen zur Verwendung dieses Typs finden [Sie unter IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status"></a>Task_group_status-Enumeration

Beschreibt den Ausführungsstatus eines `task_group`-Objekts oder eines `structured_task_group`-Objekts. Ein Wert dieses Typs wird von zahlreichen Methoden zurückgegeben, die auf den Abschluss von Aufgaben warten, die für eine Aufgabengruppe geplant wurden.

```cpp
enum task_group_status;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`canceled`|Das `task_group`- oder `structured_task_group`-Objekt wurde abgebrochen. Eine oder mehrere Aufgaben wurden möglicherweise nicht ausgeführt.|
|`completed`|Die für das `task_group`-Objekt oder das `structured_task_group`-Objekt in die Warteschlange gestellten Aufgaben wurden erfolgreich abgeschlossen.|
|`not_complete`|Die für das `task_group`-Objekt in die Warteschlange gestellten Aufgaben wurden nicht abgeschlossen. Beachten Sie, dass dieser Wert gegenwärtig von der Concurrency Runtime nicht zurückgegeben wird.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** pplinterface. h

## <a name="winrtinitializationtype"></a>Winrtinitializationtype-Enumeration

Wird von der `WinRTInitialization`-Richtlinie verwendet, um zu beschreiben, ob und wie die Windows Runtime auf Planerthreads für eine Anwendung initialisiert wird, die auf Windows-Betriebssystemen ab Version 8 ausgeführt wird. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`DoNotInitializeWinRT`|Wenn die Anwendung auf Windows 8 oder neueren Betriebssystemen ausgeführt wird, initialisieren Threads innerhalb des Planers nicht Windows-Runtime.|
|`InitializeWinRTAsMTA`|Wenn die Anwendung unter Windows 8 oder neueren Betriebssystemen ausgeführt wird, initialisiert jeder Thread innerhalb des Planers Windows-Runtime und deklariert, dass er Teil des Multithread-Apartments ist.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ConcRT. h

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)
