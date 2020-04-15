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
ms.openlocfilehash: e3a943ed52ce9653086203713bb98331f809314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372725"
---
# <a name="concurrency-namespace-enums"></a>concurrency-Namespace-Enumerationen

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status-enumeration"></a><a name="agent_status"></a>agent_status-Enumeration

Die gültigen Zustände für einen `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`agent_canceled`|Das `agent` wurde abgebrochen.|
|`agent_created`|Der `agent` wurde erstellt, aber nicht gestartet.|
|`agent_done`|Die `agent` beendete, ohne abgebrochen zu werden.|
|`agent_runnable`|Der `agent` wurde gestartet, aber `run` nicht in seine Methode eingegeben.|
|`agent_started`|Der `agent` hat begonnen.|

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Asynchrone Agenten](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a>Agents_EventType-Enumeration

Die Typen von Ereignissen, die mit der von der Agents Library angebotenen Ablaufverfolgungsfunktionalität aufgezeichnet werden können

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Ein Ereignistyp, der die Erstellung eines Objekts darstellt|
|`AGENTS_EVENT_DESTROY`|Ein Ereignistyp, der das Löschen eines Objekts darstellt|
|`AGENTS_EVENT_END`|Ein Ereignistyp, der den Abschluss einer Verarbeitung darstellt|
|`AGENTS_EVENT_LINK`|Ein Ereignistyp, der die Verknüpfung von Nachrichtenblöcken darstellt|
|`AGENTS_EVENT_NAME`|Ein Ereignistyp, der den Namen für ein Objekt darstellt|
|`AGENTS_EVENT_SCHEDULE`|Ein Ereignistyp, der die Planung eines Prozesses darstellt|
|`AGENTS_EVENT_START`|Ein Ereignistyp, der die Einleitung einer Verarbeitung darstellt|
|`AGENTS_EVENT_UNLINK`|Ein Ereignistyp, der das Auflinken von Nachrichtenblöcken darstellt|

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a>ConcRT_EventType-Enumeration

Die Typen von Ereignissen, die mit der von der Concurrency Runtime angebotenen Ablaufverfolgungsfunktionalität aufgezeichnet werden können.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Ein Ereignistyp, der den Akt eines Anfügens an einen Planer darstellt.|
|`CONCRT_EVENT_BLOCK`|Ein Ereignistyp, der den Akt einer Kontextblockierung darstellt.|
|`CONCRT_EVENT_DETACH`|Ein Ereignistyp, der den Akt einer Trennung von einem Planer darstellt.|
|`CONCRT_EVENT_END`|Ein Ereignistyp, der den Anfang eines Start-End-Ereignispaars markiert.|
|`CONCRT_EVENT_GENERIC`|Ein Ereignistyp, der für verschiedene Ereignisse verwendet wird.|
|`CONCRT_EVENT_IDLE`|Ein Ereignistyp, der den Akt eines Kontexts darstellt, der untätig wird.|
|`CONCRT_EVENT_START`|Ein Ereignistyp, der den Anfang eines Start-End-Ereignispaars markiert.|
|`CONCRT_EVENT_UNBLOCK`|Ein Ereignistyp, der den Akt der Freigabe des Blockierens eines Kontexts darstellt.|
|`CONCRT_EVENT_YIELD`|Ein Ereignistyp, der den Akt eines Kontexts darstellt, der nachgibt.|

### <a name="requirements"></a>Anforderungen

**Header:** concrt.h **Namespace:** Parallelität

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a>Concrt_TraceFlags-Enumeration

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

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a>CriticalRegionType-Enumeration

Der Typ eines kritischen Bereichs, in dem sich ein Kontext befindet.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`InsideCriticalRegion`|Gibt an, dass sich der Kontext in einem kritischen Bereich befindet. Wenn sie sich in einem kritischen Bereich befinden, werden asynchrone Aufhängungen vor dem Planer ausgeblendet. Sollte eine solche Aussetzung eintreten, wartet der Ressourcen-Manager, bis der Thread ausgeführt werden kann, und setzt ihn einfach fort, anstatt den Planer erneut aufzubeschwören. Alle Schlösser, die in einer solchen Region genommen werden, müssen mit äußerster Sorgfalt behandelt werden.|
|`InsideHyperCriticalRegion`|Gibt an, dass sich der Kontext in einem hyperkritischen Bereich befindet. Wenn sie sich in einem hyperkritischen Bereich befinden, werden sowohl synchrone als auch asynchrone Suspensionen vor dem Planer ausgeblendet. Sollte eine solche Sperrung oder Blockierung auftreten, wartet der Ressourcen-Manager, bis der Thread ausgeführt werden kann, und setzt ihn einfach fort, anstatt den Planer erneut aufzubeschwören. Sperren, die in einer solchen Region übernommen werden, dürfen niemals mit Code geteilt werden, der außerhalb einer solchen Region ausgeführt wird. Dies führt zu einem unvorhersehbaren Stillstand.|
|`OutsideCriticalRegion`|Gibt an, dass sich der Kontext außerhalb einer kritischen Region befindet.|

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrtrm.h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a>DynamicProgressFeedbackType-Enumeration

Wird von der `DynamicProgressFeedback`-Richtlinie verwendet, um zu beschreiben, ob Ressourcen für den Planer anhand statistischer Informationen neu verteilt werden, die vom Planer oder nur auf Grundlage virtueller Prozessoren erfasst wurden, die wegen der Aufrufe der `Activate`-Methode und der `Deactivate`-Methode für die `IVirtualProcessorRoot`-Schnittstelle in den und aus dem Leerlauf wechseln. Weitere Informationen zu verfügbaren Planerrichtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Der Planer sammelt keine Fortschrittsinformationen. Die Neugewichtung erfolgt ausschließlich auf der Abonnementebene des zugrunde liegenden Hardwarethreads. Weitere Informationen zu Abonnementebenen finden Sie unter [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Dieser Wert ist für die Verwendung durch die Laufzeit reserviert.|
|`ProgressFeedbackEnabled`|Der Planer sammelt Fortschrittsinformationen und übergibt sie an den Ressourcen-Manager. Der Ressourcen-Manager verwendet diese statistischen Informationen, um Ressourcen im Namen des Planers zusätzlich zur Abonnementebene des zugrunde liegenden Hardwarethreads neu auszubalancieren. Weitere Informationen zu Abonnementebenen finden Sie unter [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).|

## <a name="join_type-enumeration"></a><a name="join_type"></a>join_type-Enumeration

Der Typ eines `join`-Meldungsblocks.

```cpp
enum join_type;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`greedy`|Gierige `join` Messaging-Blöcke akzeptieren sofort eine Nachricht bei der Verbreitung. Dies ist effizienter, hat aber die Möglichkeit für Live-Lock, abhängig von der Netzwerkkonfiguration.|
|`non_greedy`|Nicht gierige `join` Nachrichtenblöcke verschieben Nachrichten und versuchen, sie zu konsumieren, nachdem alles angekommen ist. Diese funktionieren garantiert, aber langsamer.|

### <a name="requirements"></a>Anforderungen

**Header:** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a>message_status-Enumeration

Die gültigen Antworten für das Angebot eines `message`-Objekts für einen Block.

```cpp
enum message_status;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`accepted`|Das Ziel hat die Nachricht akzeptiert.|
|`declined`|Das Ziel hat die Nachricht nicht akzeptiert.|
|`missed`|Das Ziel hat versucht, die Nachricht zu akzeptieren, aber sie war nicht mehr verfügbar.|
|`postponed`|Das Ziel hat die Nachricht verschoben.|

### <a name="requirements"></a>Anforderungen

**Header:** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a>PolicyElementKey-Enumeration

Richtlinienschlüssel, die Aspekte des Planerverhaltens beschreiben. Jedes Richtlinienelement wird mit einem Schlüssel-Wert-Paar beschrieben. Weitere Informationen zu Planerrichtlinien und deren Auswirkungen auf Planer finden Sie unter [TaskPlaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`ContextPriority`|Die Betriebssystemthreadpriorität jedes Kontexts im Planer. Wenn dieser Schlüssel auf `INHERIT_THREAD_PRIORITY` den Wert festgelegt ist, erben die Kontexte im Planer die Priorität des Threads, der den Planer erstellt hat.<br /><br /> Gültige Werte : Jeder der gültigen `SetThreadPriority` Werte für die Windows-Funktion und den Sonderwert`INHERIT_THREAD_PRIORITY`<br /><br /> Standardwert :`THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Die reservierte Stapelgröße jedes Kontexts im Planer in Kilobyte.<br /><br /> Gültige Werte : Positive ganze Zahlen<br /><br /> Standardwert `0`: , was darauf hinweist, dass der Standardwert des Prozesses für die Stapelgröße verwendet wird.|
|`DynamicProgressFeedback`|Legt fest, ob die Ressourcen für den Planer gemäß den vom Planer gesammelten statistischen Informationen oder nur basierend auf der Abonnementebene der zugrunde liegenden Hardwarethreads neu ausbalanciert werden. Weitere Informationen finden Sie unter [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Gültige Werte : Ein `DynamicProgressFeedbackType` Member der Enumeration, entweder `ProgressFeedbackEnabled` oder`ProgressFeedbackDisabled`<br /><br /> Standardwert :`ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Wenn `SchedulingProtocol` der Richtlinienschlüssel auf `EnhanceScheduleGroupLocality`den Wert festgelegt ist, gibt dies die maximale Anzahl von ausfetzbaren Kontexten an, die in lokalen Warteschlangen pro virtuellem Prozessor zwischengespeichert werden dürfen. Solche Kontexte werden in der Regel in LIFO-Reihenfolge (Last-in-First-Out) auf dem virtuellen Prozessor ausgeführt, wodurch sie auslauffähig wurden. Beachten Sie, dass dieser Richtlinienschlüssel keine Bedeutung hat, wenn der `SchedulingProtocol` Schlüssel auf den Wert `EnhanceForwardProgress`festgelegt ist.<br /><br /> Gültige Werte : Nicht negative ganze Zahlen<br /><br /> Standardwert :`8`|
|`MaxConcurrency`|Die maximale Parallelitätsstufe, die vom Planer gewünscht wird. Der Ressourcen-Manager versucht zunächst, diese vielen virtuellen Prozessoren zuzuweisen. Der spezielle Wert [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) gibt an, dass die gewünschte Parallelitätsstufe mit der Anzahl der Hardwarethreads auf dem Computer identisch ist. Wenn der angegebene `MinConcurrency` Wert größer als die Anzahl der `MaxConcurrency` Hardwarethreads `MaxExecutionResources`auf dem `MaxConcurrency` Computer ist und als `MinConcurrency`angegeben ist, wird der Wert für so erhöht, dass er mit dem übereinstimmt, was für festgelegt ist.<br /><br /> Gültige Werte : Positive Ganze Zahlen und der Sonderwert`MaxExecutionResources`<br /><br /> Standardwert :`MaxExecutionResources`|
|`MaxPolicyElementKey`|Der maximale Schlüssel für das Richtlinienelement. Kein gültiger Elementschlüssel.|
|`MinConcurrency`|Die Mindestparallelitätsebene, die dem Planer vom Ressourcen-Manager bereitgestellt werden muss. Die Anzahl der virtuellen Prozessoren, die einem Planer zugewiesen sind, wird nie unter das Minimum gehen. Der spezielle Wert [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) gibt an, dass die Mindestparallelitätsstufe mit der Anzahl der Hardwarethreads auf dem Computer identisch ist. Wenn der angegebene `MaxConcurrency` Wert kleiner als die Anzahl der `MinConcurrency` Hardwarethreads `MaxExecutionResources`auf dem `MinConcurrency` Computer ist und als `MaxConcurrency`angegeben ist, wird der Wert für so abgesenkt, dass er mit dem übereinstimmt, was für festgelegt ist.<br /><br /> Gültige Werte : Nicht negative ganze Zahlen `MaxExecutionResources`und der Sonderwert . Beachten Sie, dass für Planerrichtlinien, die für die Erstellung `0` von Concurrency Runtime-Planern verwendet werden, der Wert ungültig ist.<br /><br /> Standardwert :`1`|
|`SchedulerKind`|Der Typ der Threads, die der Planer für zugrunde liegende Ausführungskontexte verwendet. Weitere Informationen finden Sie unter [SchedulerType](#schedulertype).<br /><br /> Gültige Werte : Ein `SchedulerType` Member der Enumeration, z. B.`ThreadScheduler`<br /><br /> Standardwert `ThreadScheduler`: . Dies bedeutet Win32-Threads auf allen Betriebssystemen.|
|`SchedulingProtocol`|Beschreibt, welcher Planungsalgorithmus vom Planer verwendet wird. Weitere Informationen finden Sie unter [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Gültige Werte : Ein `SchedulingProtocolType` Member der Enumeration, entweder `EnhanceScheduleGroupLocality` oder`EnhanceForwardProgress`<br /><br /> Standardwert :`EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Vorläufige Anzahl virtueller Prozessoren pro Hardwarethread. Der Zielüberzeichnungsfaktor kann ggf. vom Ressourcen-Manager `MaxConcurrency` erhöht werden, um die Hardwarethreads auf dem Computer zu erfüllen.<br /><br /> Gültige Werte : Positive ganze Zahlen<br /><br /> Standardwert :`1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a>SchedulerType-Enumeration

Wird von der `SchedulerKind`-Richtlinie verwendet, um den Typ der Threads zu beschreiben, die der Planer für zugrunde liegende Ausführungskontexte verwenden soll. Weitere Informationen zu verfügbaren Planerrichtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`ThreadScheduler`|Gibt eine explizite Anforderung von regulären Win32-Threads an.|
|`UmsThreadDefault`|UMS-Threads (User Mode Schedulable) werden in der Concurrency Runtime in Visual Studio 2013 nicht unterstützt. Das Verwenden von `UmsThreadDefault` als ein Wert für die `SchedulerType`-Richtlinie führt zu keinem Fehler. Ein Planer, der mit dieser Richtlinie erstellt wurde, wird jedoch standardmäßig Win32-Threads verwenden.|

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a>SchedulingProtocolType-Enumeration

Wird von der `SchedulingProtocol`-Richtlinie verwendet, um zu beschreiben, welcher Planungsalgorithmus für den Planer verwendet wird. Weitere Informationen zu verfügbaren Planerrichtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`EnhanceForwardProgress`|Der Planer zieht es vor, Nachbereitung der einzelnen Aufgaben durch Zeitplangruppen zu runden. Nicht blockierte Kontexte werden in der Regel in fiFO-Manier (First-in-First-Out) geplant. Virtuelle Prozessoren speichern nicht ungeblockte Kontexte zwischen.|
|`EnhanceScheduleGroupLocality`|Der Planer zieht es vor, weiterhin an Vorgängen innerhalb der aktuellen Zeitplangruppe zu arbeiten, bevor er zu einer anderen Zeitplangruppe wechselt. Nicht blockierte Kontexte werden pro virtuellem Prozessor zwischengespeichert und in der Regel in einer LIFO-Art und Weise (Last-in-First-Out) vom virtuellen Prozessor geplant, der sie entsperrt hat.|

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a>SwitchingProxyState-Enumeration

Wird verwendet, um den Zustand zu bezeichnen, in dem sich ein Threadproxy befindet, wenn er einen kooperativen Kontextwechsel zu einem anderen Threadproxy ausführt.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`Blocking`|Gibt an, dass der aufrufende Thread kooperativ blockiert ist und ausschließlich im Besitz des Aufrufers sein sollte, bis er anschließend erneut ausgeführt wird und andere Aktionen ausführt.|
|`Idle`|Gibt an, dass der aufrufende Thread vom Planer nicht mehr benötigt wird und an den Ressourcen-Manager zurückgegeben wird. Der Kontext, der ausgelöst wurde, kann vom Ressourcen-Manager nicht mehr verwendet werden.|
|`Nesting`|Gibt an, dass der aufrufende Thread einen untergeordneten Planer verschachtelt und vom Aufrufer benötigt wird, um an einen anderen Planer anzuhängen.|

### <a name="remarks"></a>Bemerkungen

Ein Typparameter `SwitchingProxyState` wird an die `IThreadProxy::SwitchTo` Methode übergeben, um den Ressourcen-Manager anzuweisen, wie der Threadproxy behandelt wird, der den Aufruf ausführt.

Weitere Informationen zur Verwendung dieses Typs finden Sie unter [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a>task_group_status-Enumeration

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

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** pplinterface.h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a>WinRTInitializationType-Enumeration

Wird von der `WinRTInitialization`-Richtlinie verwendet, um zu beschreiben, ob und wie die Windows Runtime auf Planerthreads für eine Anwendung initialisiert wird, die auf Windows-Betriebssystemen ab Version 8 ausgeführt wird. Weitere Informationen zu verfügbaren Planerrichtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`DoNotInitializeWinRT`|Wenn die Anwendung auf Windows 8 oder neueren Betriebssystemen ausgeführt wird, initialisieren Threads innerhalb des Planers nicht Windows-Runtime.|
|`InitializeWinRTAsMTA`|Wenn die Anwendung unter Windows 8 oder neueren Betriebssystemen ausgeführt wird, initialisiert jeder Thread innerhalb des Planers Windows-Runtime und deklariert, dass er Teil des Multithread-Apartments ist.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** concrt.h

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
