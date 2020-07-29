---
title: concurrency-Namespace
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue/concurrency
- agents/concurrency
- concurrent_vector/concurrency
- concrt/concurrency
- internal_split_ordered_list/concurrency
- concurrent_queue/concurrency
- pplcancellation_token/concurrency
- pplinterface/concurrency
- ppltasks/concurrency
- ppl/concurrency
- concurrent_unordered_map/concurrency
- concrtrm/concurrency
- concurrent_unordered_set/concurrency
- pplconcrt/concurrency
- internal_concurrent_hash/concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
ms.openlocfilehash: f710ead679484c41b006566a711a03ba153201ec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230375"
---
# <a name="concurrency-namespace"></a>concurrency-Namespace

Der `Concurrency`-Namespace stellt Klassen und Funktionen bereit, die Ihnen den Zugriff auf die Concurrency Runtime ermöglichen, ein Framework zur parallelen Programmierung für C++. Weitere Informationen finden Sie unter [Concurrency Runtime](../../../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntax

```cpp
namespace concurrency;
```

## <a name="members"></a>Member

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|----------|-----------------|
|`runtime_object_identity`|Jede Meldungsinstanz verfügt über eine Identität, die ihr beim Klonen folgt und die zwischen Messagingkomponenten übergeben wird. Dies kann nicht die Adresse des Meldungsobjekts sein.|
|`task_status`|Ein Typ, der den abschließenden Zustand einer Aufgabe darstellt. Gültige Werte sind `completed` und `canceled`.|
|`TaskProc`|Eine elementare Abstraktion für eine Aufgabe, die definiert ist als `void (__cdecl * TaskProc)(void *)`. Ein `TaskProc` wird aufgerufen, um den Text einer Aufgabe aufzurufen.|
|`TaskProc_t`|Eine elementare Abstraktion für eine Aufgabe, die definiert ist als `void (__cdecl * TaskProc_t)(void *)`. Ein `TaskProc` wird aufgerufen, um den Text einer Aufgabe aufzurufen.|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|----------|-----------------|
|[affinity_partitioner-Klasse](affinity-partitioner-class.md)|Die `affinity_partitioner`-Klasse ist der `static_partitioner`-Klasse ähnlich, allerdings wird die Cacheaffinität dank der Auswahl, den Arbeitsthreads Unterbereiche zuzuordnen, verbessert. Sie kann die Leistung, bei erneutem Ausführen einer Schleife über dem gleichen Dataset, und wenn die Daten im Cache gespeichert werden können, erheblich verbessern. Beachten Sie, dass das gleiche `affinity_partitioner`-Objekt mit nachfolgenden Iterationen einer parallelen Schleife verwendet werden muss, die für ein bestimmtes Dataset ausgeführt wird, um vom Datenort zu profitieren.|
|[Agent-Klasse](agent-class.md)|Diese Klasse ist als Basisklasse für alle unabhängigen Agents vorgesehen. Sie wird verwendet, um den Zustand von anderen Agents auszublenden und mithilfe von Meldungsübergabe zu interagieren.|
|[auto_partitioner-Klasse](auto-partitioner-class.md)|Die `auto_partitioner`-Klasse stellt die Standardmethoden `parallel_for`, `parallel_for_each` und `parallel_transform` dar, die verwendet werden, um den Bereich zu partitionieren, den sie durchlaufen. Diese Partitionierungs Methode setzt den Bereichs Diebstahl für den Lastenausgleich und den Abbruch pro iterate ein.|
|[Bad_target-Klasse](bad-target-class.md)|Diese Klasse beschreibt eine Ausnahme, die dann ausgelöst wird, wenn einem Meldungsblock ein Zeiger auf ein Ziel zugeordnet wird, das für die auszuführende Operation ungültig ist.|
|[callclass](call-class.md)|Ein `call`-Meldungsblock ist ein geordneter `target_block` mit mehreren Quellen, der eine bestimmte Funktion aufruft, wenn eine Nachricht empfangen wird.|
|[cancellation_token-Klasse](cancellation-token-class.md)|Mit der `cancellation_token`-Klasse kann bestimmt werden, ob für einen Vorgang ein Abbruch angefordert wurde. Dem angegebenen Token kann `task_group`, `structured_task_group` oder `task` zugeordnet werden, um einen impliziten Abbruch bereitzustellen. Es kann auch zum Abbruch abgerufen oder für einen Rückruf registriert werden, wenn das zugeordnete `cancellation_token_source`-Element abgebrochen wird.|
|[cancellation_token_registration-Klasse](cancellation-token-registration-class.md)|Die `cancellation_token_registration`-Klasse stellt eine Rückrufbenachrichtigung von `cancellation_token` dar. Bei Verwendung der `register`-Methode auf `cancellation_token` zum Empfangen von Benachrichtigungen darüber, wann ein Abbruch auftritt, wird ein `cancellation_token_registration`-Objekt als Handle an den Rückruf zurückgegeben, damit der Aufrufer mithilfe der `deregister`-Methode anfordern kann, dass ein bestimmter Rückruf nicht mehr erfolgt.|
|[cancellation_token_source-Klasse](cancellation-token-source-class.md)|Mit der `cancellation_token_source` -Klasse kann ein abbrechbarer Vorgang abgebrochen werden.|
|[Choice-Klasse](choice-class.md)|Ein `choice`-Meldungsblock ist ein Block mit mehreren Quellen und einem einzelnen Ziel, der eine Kontrollflussinteraktion zwischen mehreren Quellen darstellt. Der Auswahlblock wartet, bis eine von mehreren Quellen eine Meldung erzeugt, und gibt den Index der Quelle, von der die Meldung erzeugt wurde, weiter.|
|[combinable-Klasse](combinable-class.md)|Das `combinable<T>`-Objekt ist dazu gedacht, threadprivate Kopien von Daten bereitzustellen, mit denen sperrenfreie, threadlokale Unterberechnungen in parallelen Algorithmen durchgeführt werden können. Am Ende des Parallelvorgangs können die threadprivaten Unterbrechungen in einem Endergebnis zusammengeführt werden. Diese Klasse kann anstelle einer freigegebenen Variable verwendet werden, und sie kann zu einer Leistungsverbesserung führen, wenn andernfalls Konflikte mit dieser freigegebenen Variable entstehen würden.|
|[concurrent_priority_queue-Klasse](concurrent-priority-queue-class.md)|Die `concurrent_priority_queue`-Klasse ist ein Container, der es mehreren Threads gleichzeitig ermöglicht, für Elemente die Vorgänge "push" und "pop" auszuführen. Elemente werden in Reihenfolge ihrer Priorität per pop ausgelesen, wenn die Priorität mit einem als Vorlagenargument angegebenen Funktionselement bestimmt wird.|
|[Concurrent_queue-Klasse](concurrent-queue-class.md)|Die `concurrent_queue`-Klasse ist eine Sequenzcontainerklasse, die "First In, First Out"-Zugriff auf ihre Elemente zulässt. Sie aktiviert einen beschränkten Satz von parallelitätssicheren Vorgängen, z. B. `push` und `try_pop`.|
|[concurrent_unordered_map-Klasse](concurrent-unordered-map-class.md)|Die `concurrent_unordered_map`- Klasse ist ein parallelitätssicherer Container, mit dem eine Folge von Elementen variierender Länge des Typs `std::pair<const K, _Element_type>` gesteuert wird. Die Sequenz wird so dargestellt, dass parallelitätssichere Vorgänge für Anfügen, Elementzugriff, Iteratorzugriff und Iteratordurchläufe ermöglicht werden.|
|[concurrent_unordered_multimap-Klasse](concurrent-unordered-multimap-class.md)|Die `concurrent_unordered_multimap`- Klasse ist ein parallelitätssicherer Container, mit dem eine Folge von Elementen variierender Länge des Typs `std::pair<const K, _Element_type>` steuert. Die Sequenz wird so dargestellt, dass parallelitätssichere Vorgänge für Anfügen, Elementzugriff, Iteratorzugriff und Iteratordurchläufe ermöglicht werden.|
|[concurrent_unordered_multiset-Klasse](concurrent-unordered-multiset-class.md)|Die `concurrent_unordered_multiset` -Klasse ist ein Parallelitäts sicherer Container, der eine Sequenz von Elementen vom Typ K variabler Länge steuert. Die Sequenz wird so dargestellt, dass Parallelitäts sicheres anfügen, Element Zugriff, iteratorzugriff und iteratortraversal-Vorgänge ermöglicht wird.|
|[concurrent_unordered_set-Klasse](concurrent-unordered-set-class.md)|Die `concurrent_unordered_set` -Klasse ist ein Parallelitäts sicherer Container, der eine Sequenz von Elementen vom Typ K variabler Länge steuert. Die Sequenz wird so dargestellt, dass Parallelitäts sicheres anfügen, Element Zugriff, iteratorzugriff und iteratortraversal-Vorgänge ermöglicht wird.|
|[concurrent_vector-Klasse](concurrent-vector-class.md)|Die `concurrent_vector`-Klasse ist eine Sequenzcontainerklasse, die zufälligen Zugriff auf jedes Element zulässt. Sie aktiviert parallelitätssichere Operationen für Anfügen, Elementzugriff, Iteratorzugriff und Iteratordurchlauf.|
|[Context-Klasse](context-class.md)|Stellt eine Abstraktion für einen Ausführungskontext dar.|
|[Context_self_unblock-Klasse](context-self-unblock-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn die `Unblock`-Methode für ein `Context`-Objekt aufgerufen wird, das im gleichen Kontext aufgerufen wird. Das würde den Versuch eines angegebenen Kontexts zum Aufheben der eigenen Blockierung angeben.|
|[context_unblock_unbalanced-Klasse](context-unblock-unbalanced-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn Aufrufe der `Block`-Methode und der `Unblock`-Methode eines `Context`-Objekts nicht ordnungsgemäß zugeordnet werden.|
|[critical_section-Klasse](critical-section-class.md)|Ein nicht wieder eintretender Mutex, der explizit die Concurrency Runtime beachtet.|
|[CurrentScheduler-Klasse](currentscheduler-class.md)|Stellt eine Abstraktion für den aktuellen Planer dar, der dem aufrufenden Kontext zugeordnet ist.|
|[default_scheduler_exists-Klasse](default-scheduler-exists-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, sobald die `Scheduler::SetDefaultSchedulerPolicy`-Methode aufgerufen wird, sofern ein Standardplaner bereits innerhalb des Prozesses vorhanden ist.|
|[Ereignisklasse](event-class.md)|Ein Ereignis für manuelles Zurücksetzen, das explizit die Concurrency Runtime beachtet.|
|[Improper_lock-Klasse](improper-lock-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn eine Sperre nicht ordnungsgemäß abgerufen wird.|
|[improper_scheduler_attach-Klasse](improper-scheduler-attach-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn die `Attach`-Methode für ein `Scheduler`-Objekt aufgerufen wird, das bereits an den aktuellen Kontext angefügt wurde.|
|[Improper_scheduler_detach-Klasse](improper-scheduler-detach-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn die `CurrentScheduler::Detach`-Methode für einen Kontext aufgerufen wird, der nicht mittels der `Attach`-Methode eines `Scheduler`-Objekts an einen Planer angefügt wurde.|
|[Improper_scheduler_reference-Klasse](improper-scheduler-reference-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn die `Reference`-Methode für ein `Scheduler`-Objekt aufgerufen wird, das aus einem Kontext heruntergefahren wird, der nicht Teil dieses Planers ist.|
|[Invalid_link_target-Klasse](invalid-link-target-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn die `link_target`-Methode eines Meldungsblocks aufgerufen wird und der Meldungsblock keine Verknüpfung mit dem Ziel erstellen kann. Dies kann das Ergebnis vom Überschreiten der Anzahl zulässiger Links für den Meldungsblock sein oder das Ergebnis von Versuchen, ein bestimmtes Ziel zweimal mit der gleichen Quelle zu verknüpfen.|
|[Invalid_multiple_scheduling-Klasse](invalid-multiple-scheduling-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn ein `task_handle`-Objekt mehrmals mittels der `run`-Methode eines `task_group`-Objekts oder `structured_task_group`-Objekts ohne einen zwischenzeitlichen Aufruf der `wait`-Methode oder `run_and_wait`-Methode geplant wird.|
|[Invalid_operation-Klasse](invalid-operation-class.md)|Diese Klasse beschreibt eine Ausnahme, die bei Ausführen einer ungültigen Operation ausgelöst wird, die nicht genauer von einem anderen von der Concurrency Runtime ausgelösten Ausnahmetyp beschrieben wird.|
|[Invalid_oversubscribe_operation-Klasse](invalid-oversubscribe-operation-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst `Context::Oversubscribe` wird, wenn die-Methode aufgerufen wird, wobei der- `_BeginOversubscription` Parameter auf festgelegt ist, **`false`** ohne dass ein vorheriger Aufruf der-Methode auf `Context::Oversubscribe` `_BeginOversubscription` festgelegt ist **`true`** .|
|[Invalid_scheduler_policy_key-Klasse](invalid-scheduler-policy-key-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn ein ungültiger oder unbekannter Schlüssel an einen `SchedulerPolicy`-Objektkonstruktor übergeben wird, oder wenn der `SetPolicyValue`-Methode eines `SchedulerPolicy`-Objekts ein Schlüssel übergeben wird, der auf andere Weise geändert werden muss, z. B. die `SetConcurrencyLimits`-Methode.|
|[invalid_scheduler_policy_thread_specification-Klasse](invalid-scheduler-policy-thread-specification-class.md)|Diese Klasse beschreibt eine Ausnahme, die bei dem Versuch ausgelöst wird, die Parallelitätsgrenzen eines `SchedulerPolicy`-Objekts so festzulegen, dass der Wert des `MinConcurrency`-Schlüssels kleiner ist, als der Wert des `MaxConcurrency`-Schlüssels.|
|[Invalid_scheduler_policy_value-Klasse](invalid-scheduler-policy-value-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn der Richtlinienschlüssel eines `SchedulerPolicy`-Objekts auf einen ungültigen Wert für diesen Schlüssel festgelegt wird.|
|[ISource-Klasse](isource-class.md)|Die `ISource`-Klasse ist die Schnittstelle für alle Quellblöcke. Quellblöcke geben Meldungen an `ITarget`-Blöcke weiter.|
|[ITarget-Klasse](itarget-class.md)|Die `ITarget`-Klasse ist die Schnittstelle für alle Zielblöcke. Zielblöcke nehmen Meldungen auf, die von `ISource`-Blöcken angeboten werden.|
|[Join-Klasse](join-class.md)|Ein `join`-Meldungsblock ist ein geordneter `propagator_block` mit mehreren Quellen und einem einzelnen Ziel, der Meldungen vom Typ `T` aus allen Quellen kombiniert.|
|[Location-Klasse](location-class.md)|Die Abstraktion eines physischen Speicherorts auf der Hardware.|
|[Message-Klasse](message-class.md)|Der grundlegende Nachrichtenumschlag, der die zwischen den Meldungsblöcken übergebene Datennutzlast enthält.|
|[message_not_found-Klasse](message-not-found-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn ein Meldungsblock keine angeforderte Meldung finden kann.|
|[Message_processor-Klasse](message-processor-class.md)|Die `message_processor`-Klasse ist die abstrakte Basisklasse für die Verarbeitung von `message`-Objekten. Für die Reihenfolge der Meldungen besteht keine Garantie.|
|[Missing_wait-Klasse](missing-wait-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn es Aufgaben gibt, die noch für ein `task_group`-Objekt oder `structured_task_group`-Objekt geplant sind, während der Destruktor des Objekts ausgeführt wird. Diese Ausnahme wird nie ausgelöst, wenn der Destruktor aufgrund einer Stapelentladung als Ergebnis einer Ausnahme erreicht wird.|
|[Multi_link_registry-Klasse](multi-link-registry-class.md)|Das `multi_link_registry`-Objekt ist eine `network_link_registry`, die mehrere Quellblöcke oder mehrere Zielblöcke verwaltet.|
|[multitype_join-Klasse](multitype-join-class.md)|Ein `multitype_join`-Meldungsblock ist ein Block mit mehreren Quellen und einem einzelnen Ziel, der Meldungen verschiedener Typen aus allen Quellen kombiniert und dem Ziel ein Tupel der kombinierten Meldungen bereitstellt.|
|[nested_scheduler_missing_detach-Klasse](nested-scheduler-missing-detach-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn die Concurrency Runtime erkennt, dass versäumt wurde, die `CurrentScheduler::Detach`-Methode für einen Kontext aufzurufen, der mittels der `Attach`-Methode des `Scheduler`-Objekts an einen zweiten Planer angefügt wurde.|
|[network_link_registry-Klasse](network-link-registry-class.md)|Die abstrakte `network_link_registry`-Basisklasse verwaltet die Verknüpfung zwischen Quell- und Zielblöcken.|
|[Operation_timed_out-Klasse](operation-timed-out-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn das Timeout einer Operation erreicht wurde.|
|[Ordered_message_processor-Klasse](ordered-message-processor-class.md)|Ein `ordered_message_processor` ist ein `message_processor`, mit dem Meldungsblöcke Meldungen in der Reihenfolge verarbeiten können, in der sie empfangen wurden.|
|[overwrite_buffer-Klasse](overwrite-buffer-class.md)|Ein `overwrite_buffer`-Meldungsblock ist ein geordneter `propagator_block` mit mehreren Zielen und mehreren Quellen, der jeweils eine einzelne Meldung speichern kann. Neue Meldungen überschreiben zuvor Gespeicherte.|
|[progress_reporter-Klasse](progress-reporter-class.md)|Die Status-Reporter-Klasse ermöglicht Benachrichtigungen zum Status der Berichterstellung eines bestimmten Typs. Jedes progress_reporter-Objekt ist an eine bestimmte asynchrone Aktion bzw. einen Vorgang gebunden.|
|[propagator_block-Klasse](propagator-block-class.md)|Die `propagator_block`-Klasse ist eine abstrakte Basisklasse für Meldungsblöcke, die sowohl Quelle als auch Ziel sind. Kombiniert die Funktion der `source_block`-Klasse mit der Funktion der `target_block`-Klasse.|
|[reader_writer_lock-Klasse](reader-writer-lock-class.md)|Eine im Writer festgelegte, warteschlangenbasierte Lese-/Schreibsperre mit ausschließlich lokalem Spinning. Die Sperre gewährt "First In, First Out"-Zugriff (FIFO-Zugriff) auf Writer und blockiert Reader unter einer fortlaufenden Last von Writern.|
|[ScheduleGroup-Klasse](schedulegroup-class.md)|Stellt die Abstraktion für eine Planungsgruppe dar. In Planungsgruppen werden Sätze verwandter Arbeitsaufgaben organisiert, die von einer gemeinsamen Planung profitieren. Die kann entweder zeitlich durch das Ausführen einer anderen Aufgabe in der gleichen Gruppe vor dem Wechsel in eine andere Gruppe, oder räumlich durch das Ausführen mehrerer Elemente innerhalb der gleichen Gruppe auf dem gleichen NUMA-Knoten oder physischem Socket geschehen.|
|[Scheduler-Klasse](scheduler-class.md)|Stellt eine Abstraktion für einen Concurrency Runtime-Planer dar.|
|[scheduler_not_attached-Klasse](scheduler-not-attached-class.md)|Diese Klasse beschreibt eine Ausnahme, die bei Ausführen eines Vorgangs ausgelöst wird, der erfordert, dass ein Planer an den aktuellen Kontext angefügt wird, und einer nicht.|
|[Scheduler_resource_allocation_error-Klasse](scheduler-resource-allocation-error-class.md)|Diese Klasse beschreibt eine Ausnahme, die aufgrund eines Fehlers ausgelöst wird, um in der Concurrency Runtime eine wichtige Ressource abzurufen.|
|[scheduler_worker_creation_error-Klasse](scheduler-worker-creation-error-class.md)|Diese Klasse beschreibt eine Ausnahme, die aufgrund eines Fehlers bei der Erstellung eines Workerausführungskontexts in der Concurrency Runtime ausgelöst wird.|
|[SchedulerPolicy-Klasse](schedulerpolicy-class.md)|Die `SchedulerPolicy`-Klasse enthält einen Satz von Schlüssel-Wert-Paaren. Einen für jedes Richtlinienelement, von dem das Verhalten einer Planerinstanz gesteuert wird.|
|[simple_partitioner-Klasse](simple-partitioner-class.md)|Die `simple_partitioner`-Klasse stellt eine statische Partitionierung des Bereichs dar, der von `parallel_for` durchlaufen wird. Mit dem Partitionierer wird der Bereich in Blöcke unterteilt, sodass jeder Block mindestens die von der Segmentgröße angegebene Anzahl von Iterationen enthält.|
|[Single_assignment-Klasse](single-assignment-class.md)|Ein `single_assignment`-Meldungsblock ist ein geordneter `propagator_block` mit mehreren Zielen und mehreren Quellen, der eine einzelne, einmal beschreibbare `message` speichern kann.|
|[Single_link_registry-Klasse](single-link-registry-class.md)|Das `single_link_registry`-Objekt ist eine `network_link_registry`, die nur eine einzige Quelle oder einen einzigen Zielblock verwaltet.|
|[source_block-Klasse](source-block-class.md)|Die `source_block`-Klasse ist eine abstrakte Basisklasse ausschließlich für Quellblöcke. Die Klasse stellt grundlegende Linkmanagementfunktionalität sowie allgemeine Fehlerüberprüfungen bereit.|
|[source_link_manager-Klasse](source-link-manager-class.md)|Das `source_link_manager`-Objekt verwaltet Meldungsblock-Netzwerklinks zu `ISource`-Blöcken.|
|[static_partitioner-Klasse](static-partitioner-class.md)|Die `static_partitioner`-Klasse stellt eine statische Partitionierung des Bereichs dar, der von `parallel_for` durchlaufen wird. Der Partitionierer dividiert den Bereich in so viele Blöcke, wie worker für den zugrunde liegenden Scheduler verfügbar sind.|
|[structured_task_group-Klasse](structured-task-group-class.md)|Die `structured_task_group`-Klasse stellt eine stark strukturierte Auflistung paralleler Arbeit dar. Sie können einzelne parallele Aufgaben mithilfe von `structured_task_group`-Objekten in eine `task_handle` stellen und warten, bis sie abgeschlossen werden, oder Sie können die Aufgabengruppe abbrechen, bevor deren Ausführung beendet wird, wodurch auch alle Aufgaben abgebrochen werden, deren Ausführung nicht gestartet wurde.|
|[target_block-Klasse](target-block-class.md)|Die `target_block`-Klasse ist eine abstrakte Basisklasse, mit der grundlegende Linkmanagementfunktionalität und Fehlerüberprüfung für Nur-Ziel-Blöcke bereitgestellt werden.|
|[Task-Klasse (Concurrency Runtime)](task-class.md)|Die Parallel Patterns Library (PPL) `task`-Klasse. Ein `task`-Objekt stellt Arbeit dar, die asynchron und übereinstimmend mit anderen Tasks und paralleler Arbeit , die von parallelen Algorithmen in der Concurrency Runtime erzeugt wird, ausgeführt werden kann. Es enthält bei erfolgreichem Abschluss ein Ergebnis vom Typ `_ResultType`. Tasks des Typs `task<void>` führen zu keinem Ergebnis. Eine Aufgabe kann erwartet und unabhängig von anderen Aufgaben abgebrochen werden. Er kann mit anderen Tasks mithilfe von Continuations (`then`) sowie Join-Muster (`when_all`) und Choise-Muster (`when_any`) erstellt werden.|
|[task_canceled-Klasse](task-canceled-class.md)|Diese Klasse beschreibt eine Ausnahme, die von den PPL-Aufgaben ausgelöst wird, um das Abbrechen der aktuellen Aufgabe zu erzwingen. Sie wird auch von der- `get()` Methode für den [Task](task-class.md)für eine abgebrochene Aufgabe ausgelöst.|
|[task_completion_event-Klasse](task-completion-event-class.md)|Mit der `task_completion_event`-Klasse können Sie die Ausführung einer Aufgabe verzögern, bis eine Bedingung erfüllt ist, oder eine Aufgabe als Reaktion auf ein externes Ereignis starten.|
|[task_continuation_context-Klasse](task-continuation-context-class.md)|Mit der `task_continuation_context`-Klasse können Sie angeben, an welcher Stelle eine Fortsetzung ausgeführt werden soll. Es ist nur nützlich, diese Klasse aus einer UWP-APP zu verwenden. Bei nicht-Windows-Runtime-apps wird der Ausführungs Kontext der Aufgaben Fortsetzung von der Laufzeit bestimmt und kann nicht konfiguriert werden.|
|[Task_group-Klasse](task-group-class.md)|Die `task_group`-Klasse stellt eine Auflistung der parallelen Arbeit dar, auf die gewartet oder die abgebrochen werden kann.|
|[task_handle-Klasse](task-handle-class.md)|Die `task_handle`-Klasse stellt ein einzelnes paralleles Arbeitselement dar. Sie kapselt die Anweisungen und die zum Ausführen eines Teils der Arbeit erforderlichen Daten.|
|[task_options-Klasse (Concurrency Runtime)](task-options-class-concurrency-runtime.md)|Stellt die zulässigen Optionen zum Erstellen einer Aufgabe dar|
|[Timer-Klasse](timer-class.md)|Ein `timer`-Meldungsblock ist ein `source_block` mit einem einzelnen Ziel, der nach Ablauf einer bestimmten Zeitspanne oder in bestimmten Intervallen eine Meldung an sein Ziel senden kann.|
|[Transformer-Klasse](transformer-class.md)|Ein `transformer`-Meldungsblock ist ein geordneter `propagator_block` mit einem einzelnen Ziel und mehreren Quellen, der Meldungen eines Typs akzeptieren und eine unbegrenzte Anzahl von Meldungen eines anderen Typs speichern kann.|
|[UNBOUNDED_BUFFER-Klasse](unbounded-buffer-class.md)|Ein `unbounded_buffer`-Meldungsblock ist ein geordneter `propagator_block` mit mehreren Zielen und mehreren Quellen, der eine unbegrenzte Anzahl von Meldungen speichern kann.|
|[Unsupported_os-Klasse](unsupported-os-class.md)|Diese Klasse beschreibt eine Ausnahme, die ausgelöst wird, wenn ein nicht unterstütztes Betriebssystem verwendet wird.|

### <a name="structures"></a>Strukturen

|Name|Beschreibung|
|----------|-----------------|
|[DispatchState-Struktur](dispatchstate-structure.md)|Die `DispatchState`-Struktur wird zur Zustandsübertragung auf die `IExecutionContext::Dispatch`-Methode verwendet. Sie beschreibt die Umstände, unter denen die `Dispatch`-Methode für eine `IExecutionContext`-Schnittstelle aufgerufen wird.|
|[IExecutionContext-Struktur](iexecutioncontext-structure.md)|Eine Schnittstelle zu einem Ausführungskontext, der auf einem angegebenen virtuellen Prozessor ausgeführt werden kann und einen gemeinsamen Kontextwechsel zulässt.|
|[IExecutionResource-Struktur](iexecutionresource-structure.md)|Eine Abstraktion für einen Hardwarethread.|
|[IResourceManager-Struktur](iresourcemanager-structure.md)|Eine Schnittstelle zum Ressourcen-Manager der Concurrency Runtime. Dies ist die Schnittstelle, über die Planer mit dem Ressourcen-Manager kommunizieren.|
|[IScheduler-Struktur](ischeduler-structure.md)|Eine Schnittstelle zu der Abstraktion eines Arbeitsplaners. Der Ressourcen-Manager der Concurrency Runtime kommuniziert mithilfe dieser Schnittstelle mit Arbeitsplanern.|
|[ISchedulerProxy-Struktur](ischedulerproxy-structure.md)|Die Schnittstelle, über die Planer mit dem Ressourcen-Manager der Concurrency Runtime kommunizieren, um die Ressourcenzuordnung auszuhandeln.|
|[IThreadProxy-Struktur](ithreadproxy-structure.md)|Eine Abstraktion für einen Thread der Ausführung. Abhängig von dem von Ihnen erstellten `SchedulerType`-Richtlinienschlüssel des Planers, gewährt der Ressourcen-Manager eine Threadproxy, der entweder von einem regulären Win32-Thread oder einem im Benutzermodus planbaren (UMS) Thread unterstützt wird. UMS-Threads werden auf 64-Bit-Betriebssystemen mit Version Windows 7 und höher unterstützt.|
|[ITopologyExecutionResource-Struktur](itopologyexecutionresource-structure.md)|Eine Schnittstelle zu einer vom Ressourcen-Manager definierten Ausführungsressource.|
|[ITopologyNode-Struktur](itopologynode-structure.md)|Eine Schnittstelle für einen vom Ressourcen-Manager definierten Topologieknoten. Ein Knoten enthält mindestens eine Ausführungsressource.|
|[IUMSCompletionList-Struktur](iumscompletionlist-structure.md)|Stellt eine UMS-Vervollständigungsliste dar. Wenn ein UMS-Thread blockiert wird, wird der festgelegte Planungskontext des Planers weitergeleitet, um zu entscheiden, was für den Stamm des zugrunde liegenden virtuellen Prozessors geplant werden soll, während der ursprüngliche Thread blockiert ist. Wenn die Blockierung des ursprünglichen Threads aufgehoben wird, stellt das Betriebssystem ihn in die Warteschlange für die Vervollständigungsliste, auf die über diese Schnittstelle zugegriffen werden kann. Der Planer kann die Vervollständigungsliste für den festgelegten Planungskontext oder eine beliebige andere Stelle abfragen, in der er nach Arbeit sucht.|
|[IUMSScheduler-Struktur](iumsscheduler-structure.md)|Eine Schnittstelle zu der Abstraktion eines Arbeitsplaners, der planbare Threads vom Ressourcen-Manager der Concurrency Runtime im Benutzermodus erwartet. Der Ressourcen-Manager verwendet diese Schnittstelle für die Kommunikation mit UMS-Threadplanern. Die `IUMSScheduler` -Schnittstelle erbt von der `IScheduler` -Schnittstelle.|
|[IUMSThreadProxy-Struktur](iumsthreadproxy-structure.md)|Eine Abstraktion für einen Thread der Ausführung. Wenn dem Planer im Benutzermodus planbare (UMS) Threads gewährt werden sollen, legen Sie den Wert für das Planerrichtlinienelement `SchedulerKind` auf `UmsThreadDefault` fest, und implementieren Sie die `IUMSScheduler`-Schnittstelle. UMS-Threads werden nur unter 64-Bit-Betriebssystemen mit Version Windows 7 und höher unterstützt.|
|[IUMSUnblockNotification-Struktur](iumsunblocknotification-structure.md)|Stellt eine Benachrichtigung vom Ressourcen-Manager darüber dar, dass ein Threadproxy, der blockiert und eine Rückkehr zum festgelegten Planungskontext des Planers ausgelöst hatte, die Blockierung aufgehoben hat und zum Planen bereit ist. Diese Schnittstelle ist ungültig, sobald der zugeordnete Ausführungskontext des Threadproxys, der von der `GetContext`-Methode zurückgegeben wurde, neu geplant wird.|
|[IVirtualProcessorRoot-Struktur](ivirtualprocessorroot-structure.md)|Eine Abstraktion für einen Hardwarethread, auf dem ein Threadproxy ausgeführt werden kann.|
|[scheduler_interface-Struktur](scheduler-interface-structure.md)|Planerschnittstelle|
|[scheduler_ptr-Struktur (Concurrency Runtime)](scheduler-ptr-structure-concurrency-runtime.md)|Stellt einen Zeiger auf einen Planer dar. Diese Klasse ist vorhanden, um die Angabe einer freigegebenen Lebensdauer mithilfe von shared_ptr oder nur eines einfachen Verweises mithilfe eines unformatierten Zeigers zuzulassen.|

### <a name="enumerations"></a>Enumerationen

|Name|Beschreibung|
|----------|-----------------|
|[agent_status](concurrency-namespace-enums.md#agent_status)|Die gültigen Zustände für einen `agent`.|
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Die Typen von Ereignissen, die mit der von der Agents Library angebotenen Ablaufverfolgungsfunktionalität aufgezeichnet werden können|
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Die Typen von Ereignissen, die mit der von der Concurrency Runtime angebotenen Ablaufverfolgungsfunktionalität aufgezeichnet werden können.|
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Ablaufverfolgungskennzeichen für die Ereignistypen|
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|Der Typ eines kritischen Bereichs, in dem sich ein Kontext befindet.|
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Wird von der `DynamicProgressFeedback`-Richtlinie verwendet, um zu beschreiben, ob Ressourcen für den Planer anhand statistischer Informationen neu verteilt werden, die vom Planer oder nur auf Grundlage virtueller Prozessoren erfasst wurden, die wegen der Aufrufe der `Activate`-Methode und der `Deactivate`-Methode für die `IVirtualProcessorRoot`-Schnittstelle in den und aus dem Leerlauf wechseln. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|
|[join_type](concurrency-namespace-enums.md#join_type)|Der Typ eines `join`-Meldungsblocks.|
|[message_status](concurrency-namespace-enums.md#message_status)|Die gültigen Antworten für das Angebot eines `message`-Objekts für einen Block.|
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|Richtlinienschlüssel, die Aspekte des Planerverhaltens beschreiben. Jedes Richtlinienelement wird mit einem Schlüssel-Wert-Paar beschrieben. Weitere Informationen zu planerrichtlinien und deren Auswirkungen auf Planer finden Sie unter [Taskplaner](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|Wird von der `SchedulerKind`-Richtlinie verwendet, um den Typ der Threads zu beschreiben, die der Planer für zugrunde liegende Ausführungskontexte verwenden soll. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|Wird von der `SchedulingProtocol`-Richtlinie verwendet, um zu beschreiben, welcher Planungsalgorithmus für den Planer verwendet wird. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|Wird verwendet, um den Zustand zu bezeichnen, in dem sich ein Threadproxy befindet, wenn er einen kooperativen Kontextwechsel zu einem anderen Threadproxy ausführt.|
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Beschreibt den Ausführungsstatus eines `task_group`-Objekts oder eines `structured_task_group`-Objekts. Ein Wert dieses Typs wird von zahlreichen Methoden zurückgegeben, die auf den Abschluss von Aufgaben warten, die für eine Aufgabengruppe geplant wurden.|
|[WinRTInitializationType](concurrency-namespace-enums.md#winrtinitializationtype)|Wird von der `WinRTInitialization`-Richtlinie verwendet, um zu beschreiben, ob und wie die Windows Runtime auf Planerthreads für eine Anwendung initialisiert wird, die auf Windows-Betriebssystemen ab Version 8 ausgeführt wird. Weitere Informationen zu verfügbaren Scheduler-Richtlinien finden Sie unter [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|----------|-----------------|
|[Alloc-Funktion](concurrency-namespace-functions.md#alloc)|Reserviert einen Speicherblock mit der in der Unterbelegungsfunktion für die Zwischenspeicherung der Concurrency Runtime angegebenen Größe.|
|[ASend-Funktion](concurrency-namespace-functions.md#asend)|Ist überladen. Ein asynchroner Sendevorgang, der eine Aufgabe zum Weitergeben der Daten an den Zielblock plant.|
|[cancel_current_task-Funktion](concurrency-namespace-functions.md#cancel_current_task)|Bricht die gerade ausgeführte Aufgabe ab. Diese Funktion kann aus dem Text einer Aufgabe aufgerufen werden, um die Ausführung der Aufgabe abzubrechen und ihn dabei in den `canceled` Zustand übergehen zu lassen.<br /><br /> Der Aufruf dieser Funktion, wenn Sie sich nicht innerhalb des Texts von einem `task` befinden, ist kein unterstütztes Szenario. Dies führt zu undefiniertem Verhalten, wie z. b. einem Absturz oder einer nicht Reaktionsfähigkeit in Ihrer Anwendung.|
|[create_async-Funktion](concurrency-namespace-functions.md#create_async)|Erstellt ein asynchrones Konstrukt der Windows Runtime auf einem vom Benutzer angegebenes Lambda oder Funktionsobjekt. Der Rückgabetyp von `create_async` ist entweder `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` oder `IAsyncOperationWithProgress<TResult, TProgress>^` auf Grundlage der Signatur des Lambda-Ausdrucks, der an die Methode übergeben wurde.|
|[create_task-Funktion](concurrency-namespace-functions.md#create_task)|Ist überladen. Erstellt ein ppl- [Aufgaben](task-class.md) Objekt. Das Element `create_task` kann überall dort verwendet werden, wo Sie einen Aufgabenkonstruktor verwendet hätten. Es wird hauptsächlich aus Gründen der praktische bereitgestellt, da es die Verwendung des- **`auto`** Schlüssel Worts beim Erstellen von Aufgaben ermöglicht.|
|[CreateResourceManager-Funktion](concurrency-namespace-functions.md#createresourcemanager)|Gibt eine Schnittstelle zurück, die die Singletoninstanz des Ressourcen-Managers der Concurrency Runtime darstellt. Der Ressourcen-Manager ist für das Zuweisen von Ressourcen für Planer, die miteinander kooperieren möchten, zuständig.|
|[DisableTracing-Funktion](concurrency-namespace-functions.md#disabletracing)|Deaktiviert die Ablaufverfolgung in der Concurrency Runtime. Diese Funktion ist veraltet, da die Registrierung der ETW-Ablaufverfolgung standardmäßig aufgehoben wird.|
|[EnableTracing-Funktion](concurrency-namespace-functions.md#enabletracing)|Aktiviert die Ablaufverfolgung in der Concurrency Runtime. Diese Funktion ist veraltet, da die Registrierung der ETW-Ablaufverfolgung jetzt standardmäßig erfolgt.|
|[Free-Funktion](concurrency-namespace-functions.md#free)|Gibt einen Speicherblock frei, der zuvor mit der `Alloc`-Methode der Unterbelegungsfunktion für die Zwischenspeicherung der Concurrency Runtime reserviert wurde.|
|[get_ambient_scheduler-Funktion (Concurrency Runtime)](concurrency-namespace-functions.md#get_ambient_scheduler)||
|[GetExecutionContextId-Funktion](concurrency-namespace-functions.md#getexecutioncontextid)|Gibt einen eindeutigen Bezeichner zurück, der einem Ausführungskontext zugewiesen werden kann, der die `IExecutionContext`-Schnittstelle implementiert.|
|[GetOSVersion-Funktion](concurrency-namespace-functions.md#getosversion)|Gibt die Betriebssystemversion zurück.|
|[GetProcessorCount-Funktion](concurrency-namespace-functions.md#getprocessorcount)|Gibt die Anzahl von Hardwarethreads des zugrunde liegenden Systems zurück.|
|[Getprocessornoentcount-Funktion](concurrency-namespace-functions.md#getprocessornodecount)|Gibt die Anzahl von NUMA-Knoten oder Prozessorpaketen des zugrunde liegenden Systems zurück.|
|[GetSchedulerId-Funktion](concurrency-namespace-functions.md#getschedulerid)|Gibt einen eindeutigen Bezeichner zurück, der einem Planer zugewiesen werden kann, der die `IScheduler`-Schnittstelle implementiert.|
|[interruption_point-Funktion](concurrency-namespace-functions.md#interruption_point)|Erstellt einen Unterbrechungspunkt für den Abbruch. Wenn ein Abbruch im Kontext, in dem diese Funktion aufgerufen wird, ausgeführt wird, löst diese eine interne Ausnahme aus, mit der die Ausführung der aktuell ausgeführten parallelen Verarbeitung abgebrochen wird. Wenn kein Abbruch ausgeführt wird, bleibt die Funktion untätig.|
|[Is_current_task_group_canceling-Funktion](concurrency-namespace-functions.md#is_current_task_group_canceling)|Gibt zurück, ob die Aufgabengruppe, die gerade inline auf dem aktuellen Kontext ausgeführt wird, in diesem Moment (oder in Kürze) einen Abbruch durchführt. Beachten Sie, dass zurückgegeben wird, wenn derzeit keine Aufgaben Gruppe im aktuellen Kontext Inline ausgeführt wird **`false`** .|
|[make_choice-Funktion](concurrency-namespace-functions.md#make_choice)|Ist überladen. Erstellt einen `choice`-Meldungsblock aus einem optionalen `Scheduler` oder einer `ScheduleGroup` und mindestens zwei Eingabequellen.|
|[Make_greedy_join-Funktion](concurrency-namespace-functions.md#make_greedy_join)|Ist überladen. Erstellt einen `greedy multitype_join`-Meldungsblock aus einem optionalen `Scheduler` oder einer `ScheduleGroup` und mindestens zwei Eingabequellen.|
|[make_join-Funktion](concurrency-namespace-functions.md#make_join)|Ist überladen. Erstellt einen `non_greedy multitype_join`-Meldungsblock aus einem optionalen `Scheduler` oder einer `ScheduleGroup` und mindestens zwei Eingabequellen.|
|[Make_task-Funktion](concurrency-namespace-functions.md#make_task)|Eine Factorymethode zum Erstellen eines `task_handle`-Objekts.|
|[parallel_buffered_sort-Funktion](concurrency-namespace-functions.md#parallel_buffered_sort)|Ist überladen. Ordnet die Elemente in einem angegebenen Bereich in einer nicht absteigenden Reihenfolge oder entsprechend einem Sortierkriterium an, das von einem binären Prädikat gleichzeitig angegeben wird. Diese Funktion entspricht `std::sort` semantisch darin, dass sie eine vergleichsbasierte, instabile, direkte Sortierung ist, abgesehen von den zusätzlich erforderlichen `O(n)`-Leerzeichen und er notwendigen Standardinitialisierung für die sortierten Elemente.|
|[parallel_for-Funktion](concurrency-namespace-functions.md#parallel_for)|Ist überladen. `parallel_for` durchläuft einen Bereich von Indizes und führt bei jeder Iteration parallel eine vom Benutzer bereitgestellte Funktion aus.|
|[parallel_for_each-Funktion](concurrency-namespace-functions.md#parallel_for_each)|Ist überladen. `parallel_for_each` wendet eine angegebene Funktion parallel auf jedes Element innerhalb eines Bereichs an. Sie entspricht semantisch der `for_each`-Funktion im `std`-Namespace, außer dass die Iteration über die Elemente parallel ausgeführt wird und die Reihenfolge der Iteration nicht angegeben ist. Das Argument `_Func` muss einen Funktionsaufrufoperator in der Form `operator()(T)` unterstützen, wobei der Parameter `T` der Elementtyp des durchlaufenen Containers ist.|
|[Parallel_invoke-Funktion](concurrency-namespace-functions.md#parallel_invoke)|Ist überladen. Führt die als Parameter angegebenen Funktionsobjekte parallel aus, und blockiert, bis die Ausführung beendet ist. Jedes Funktionsobjekt kann ein Lambdaausdruck, ein Zeiger auf eine Funktion oder ein anderes Objekt sein, das den Funktionsaufrufoperator mit der Signatur `void operator()()` unterstützt.|
|[parallel_radixsort-Funktion](concurrency-namespace-functions.md#parallel_radixsort)|Ist überladen. Ordnet Elemente in einem angegebenen Bereich mithilfe eines Basis-Sortieralgorithmus in einer absteigenden Reihenfolge an. Dies ist eine stabile Sortierfunktion, die eine Projektionsfunktion erfordert, mit der Elemente zur Sortierung in Schlüssel, die ganzen Zahlen ohne Vorzeichen ähneln, projiziert werden können. Standardinitialisierung ist für die zu sortierenden Elemente erforderlich.|
|[parallel_reduce-Funktion](concurrency-namespace-functions.md#parallel_reduce)|Ist überladen. Berechnet die Summe aller Elemente in einem angegebenen Bereich, indem aufeinander folgende Teilsummen berechnet werden, oder berechnet das Ergebnis der aufeinander folgenden Teilergebnisse, die auf ähnliche Weise mithilfe eines angegebenen binären Vorgangs (außer Summe) abgerufen werden parallel. `parallel_reduce` entspricht `std::accumulate` semantisch, außer dass der binäre Vorgang assoziativ sein muss und ein Identitätswert anstelle eines Anfangswerts erforderlich ist.|
|[parallel_sort-Funktion](concurrency-namespace-functions.md#parallel_sort)|Ist überladen. Ordnet die Elemente in einem angegebenen Bereich in einer nicht absteigenden Reihenfolge oder entsprechend einem Sortierkriterium an, das von einem binären Prädikat gleichzeitig angegeben wird. Diese Funktion entspricht `std::sort` semantisch insofern, dass sie eine vergleichsbasierte, instabile, direkte Sortierung ist.|
|[parallel_transform-Funktion](concurrency-namespace-functions.md#parallel_transform)|Ist überladen. Wendet ein angegebenes Funktionsobjekt auf jedes Element in einem Quellbereich oder auf ein Elementpaar aus zwei Quellbereichen an und kopiert die Rückgabewerte des Funktionsobjekts parallel in einen Zielbereich. Diese Funktion entspricht semantisch `std::transform`.|
|[Receive-Funktion](concurrency-namespace-functions.md#receive)|Ist überladen. Eine allgemeine Empfangsimplementierung, mit der ein Kontext auf Daten von genau einer Quelle warten und die akzeptierten Werte filtern kann.|
|[run_with_cancellation_token-Funktion](concurrency-namespace-functions.md#run_with_cancellation_token)|Führt sofort synchron ein Funktionsobjekt im Kontext eines angegebenen Abbruchtokens aus.|
|[send-Funktion](concurrency-namespace-functions.md#send)|Ist überladen. Ein synchroner Sendevorgang, der wartet, bis das Ziel die Meldung akzeptiert oder ablehnt.|
|[set_ambient_scheduler-Funktion (Concurrency Runtime)](concurrency-namespace-functions.md#set_ambient_scheduler)||
|[set_task_execution_resources-Funktion](concurrency-namespace-functions.md#set_task_execution_resources)|Ist überladen. Schränkt die Ausführungsressourcen, die von den internen Arbeitsthreads der Concurrency Runtime verwendet werden, auf den angegebenen Affinitätssatz ein.<br /><br /> Es ist nur gültig, diese Methode vor Erstellung des Ressourcen-Managers oder zwischen der Lebensdauer zweier Ressourcen-Manager aufzurufen. Sie kann mehrmals aufgerufen werden, solange der Ressourcen-Manager zum Zeitpunkt des Aufrufs nicht vorhanden ist. Nachdem eine Affinitätsgrenze eingerichtet wurde, bleibt diese bis zum nächsten gültigen Aufruf der `set_task_execution_resources`-Methode bestehen.<br /><br /> Die bereitgestellte Affinitätsmaske muss keine Teilmenge der Prozessaffinitätsmaske sein. Die Prozessaffinität wird bei Bedarf aktualisiert.|
|[Swap-Funktion](concurrency-namespace-functions.md#swap)|Tauscht die Elemente zweier `concurrent_vector`-Objekte.|
|[task_from_exception-Funktion (Concurrency Runtime)](concurrency-namespace-functions.md#task_from_exception)||
|[task_from_result-Funktion (Concurrency Runtime)](concurrency-namespace-functions.md#task_from_result)||
|[Trace_agents_register_name-Funktion](concurrency-namespace-functions.md#trace_agents_register_name)|Ordnet den angegebenen Namen dem Nachrichtenblock oder dem Agent in der ETW-Ablaufverfolgung zu.|
|[try_receive-Funktion](concurrency-namespace-functions.md#try_receive)|Ist überladen. Eine allgemeine try-receive-Implementierung, mit der ein Kontext Daten von genau einer Quelle suchen und die akzeptierten Werte filtern kann. Wenn die Daten nicht bereit sind, gibt die Methode "false" zurück.|
|[wait-Funktion](concurrency-namespace-functions.md#wait)|Hält den aktuellen Kontext für eine bestimmte Zeit an.|
|[when_all-Funktion](concurrency-namespace-functions.md#when_all)|Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn alle als Argumente angegeben Aufgaben erfolgreich abgeschlossen werden.|
|[when_any-Funktion](concurrency-namespace-functions.md#when_any)|Ist überladen. Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn eine der als Argumente angegeben Aufgaben erfolgreich abgeschlossen wird.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Operator! =](concurrency-namespace-operators.md#operator_neq)|Testet, ob das `concurrent_vector`-Objekt links vom Operator ungleich dem `concurrent_vector`-Objekt rechts vom Operator ist.|
|[Operator&&](concurrency-namespace-operators.md#operator_amp_amp)|Ist überladen. Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn beide Aufgaben, die als Argumente bereitgestellt werden, erfolgreich abgeschlossen werden.|
|[operator||](concurrency-namespace-operators.md#operator_lor)|Ist überladen. Erstellt eine Aufgabe, die erfolgreich abgeschlossen wird, wenn eine der als Argumente angegeben Aufgaben erfolgreich abgeschlossen wird.|
|[Operator<](concurrency-namespace-operators.md#operator_lt)|Testet, ob das `concurrent_vector`-Objekt links vom Operator kleiner als das `concurrent_vector`-Objekt auf der rechten Seite ist.|
|[Operator<=](concurrency-namespace-operators.md#operator_lt_eq)|Testet, ob das `concurrent_vector`-Objekt links vom Operator kleiner oder gleich dem `concurrent_vector`-Objekt auf der rechten Seite ist.|
|[Operator = =](concurrency-namespace-operators.md#operator_eq_eq)|Testet, ob das `concurrent_vector`-Objekt links vom Operator gleich dem `concurrent_vector`-Objekt rechts vom Operator ist.|
|[Operator>](concurrency-namespace-operators.md#operator_gt)|Testet, ob das `concurrent_vector`-Objekt links vom Operator größer als das `concurrent_vector`-Objekt auf der rechten Seite ist.|
|[Operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Testet, ob das `concurrent_vector`-Objekt links vom Operator größer oder gleich dem `concurrent_vector`-Objekt auf der rechten Seite ist.|

### <a name="constants"></a>Konstanten

|Name|Beschreibung|
|----------|-----------------|
|[AgentEventGuid](concurrency-namespace-constants1.md#agenteventguid)|Ein Kategorie-GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07}), die von der Agents Library in der Concurrency Runtime ausgelöste ETW-Ereignisse beschreibt.|
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf Arbeiten oder Aufgaben beziehen.|
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|Der ETW-Anbieter-GUID für die Concurrency Runtime.|
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Gibt die Unterstützung der in Visual Studio 2010 definierten Ressourcen-Manager-Schnittstelle an.|
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und nicht in eine der anderen Kategorien fallen.|
|[ContextEventGuid](concurrency-namespace-constants1.md#contexteventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf Kontexte beziehen.|
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Ein Wert, der angibt, dass ein Wartevorgang nie durch einen Timeout beendet werden sollte.|
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Ein Wert, der angibt, dass ein Wartevorgang durch einen Timeout beendet wurde.|
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Ein besonderer Wert für den Richtlinienschlüssel `ContextPriority`, der angibt, dass die Threadpriorität aller Kontexte im Planer die gleiche wie die des Threads sein sollte, der den Planer erstellt hat.|
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf Sperren beziehen.|
|[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)|Ein besonderer Wert für die Richtlinienschlüssel `MinConcurrency` und `MaxConcurrency`. Wird, falls keine anderen Einschränkungen vorliegen, standardmäßig auf die Anzahl von Hardwarethreads auf dem Computer festgelegt.|
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf die Verwendung der `parallel_for_each`-Funktion beziehen.|
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf die Verwendung der `parallel_for`-Funktion beziehen.|
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf die Verwendung der `parallel_invoke`-Funktion beziehen.|
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf den Ressourcen-Manager beziehen.|
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf Planungsgruppen beziehen.|
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf Planeraktivitäten beziehen.|
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Ein Kategorie-GUID, die ETW-Ereignisse beschreibt, die von der Concurrency Runtime ausgelöst werden und sich direkt auf virtuelle Prozessoren beziehen.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** "Agents. h", "ConcRT. h", "concrtrm. h", "concurrent_priority_queue. h", "Concurrent_queue. h", "concurrent_unordered_map. h", "concurrent_unordered_set. h", "Concurrent_vector. h", "internal_concurrent_hash. h", "internal_split_ordered_list. h", "ppl. h", "pplcancellation_token

## <a name="see-also"></a>Siehe auch

[Verweis](reference-concurrency-runtime.md)
