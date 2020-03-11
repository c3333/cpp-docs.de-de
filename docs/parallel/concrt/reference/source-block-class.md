---
title: source_block-Klasse
ms.date: 11/04/2016
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: 3a0d69bc2e2904b1dcf37a7e9891d95bd869a610
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866133"
---
# <a name="source_block-class"></a>source_block-Klasse

Die `source_block`-Klasse ist eine abstrakte Basisklasse ausschließlich für Quellblöcke. Die Klasse stellt grundlegende Linkmanagementfunktionalität sowie allgemeine Fehlerüberprüfungen bereit.

## <a name="syntax"></a>Syntax

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>Parameter

*_TargetLinkRegistry*<br/>
Link Registrierung, die zum Speichern der Ziel Verknüpfungen verwendet werden soll.

*_MessageProcessorType*<br/>
Der Prozessortyp für die Nachrichtenverarbeitung.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`target_iterator`|Der Iterator zum Durchlaufen der verbundenen Ziele.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[source_block](#ctor)|Erstellt ein `source_block`-Objekt.|
|[~ source_block-Dekonstruktor](#dtor)|Zerstört das `source_block`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[erst](#accept)|Akzeptiert eine Meldung, die von diesem `source_block` Objekt angeboten wurde, und überträgt den Besitz an den Aufrufer.|
|[acquire_ref](#acquire_ref)|Ruft einen Verweis Zähler für dieses `source_block` Objekt ab, um das Löschen zu verhindern.|
|[Nutzen](#consume)|Verarbeitet eine Meldung, die zuvor von diesem `source_block` Objekt bereitgestellt und vom Ziel erfolgreich reserviert wurde, und überträgt den Besitz an den Aufrufer.|
|[link_target](#link_target)|Verknüpft einen Zielblock mit diesem `source_block` Objekt.|
|[release](#release)|Gibt eine vorherige erfolgreiche Nachrichten Reservierung frei.|
|[release_ref](#release_ref)|Gibt einen Verweis Zähler für dieses `source_block` Objekt frei.|
|[reserve](#reserve)|Reserviert eine Meldung, die zuvor von diesem `source_block` Objekt angeboten wurde.|
|[unlink_target](#unlink_target)|Entbindet einen Zielblock von diesem `source_block` Objekt.|
|[unlink_targets](#unlink_targets)|Hebt die Verknüpfung aller Ziel Blöcke von diesem `source_block` Objekt auf. (Überschreibt [ISource:: unlink_targets](isource-class.md#unlink_targets).)|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[accept_message](#accept_message)|Akzeptiert beim Überschreiben in einer abgeleiteten Klasse eine angebotene Nachricht von der Quelle. Nachrichten Blöcke sollten diese Methode überschreiben, um die `_MsgId` zu überprüfen und eine Meldung zurückzugeben.|
|[async_send](#async_send)|Fügt Nachrichten asynchron in die Warteschlange ein und startet einen propagierungs Task, wenn dies noch nicht geschehen ist.|
|[consume_message](#consume_message)|Verarbeitet beim Überschreiben in einer abgeleiteten Klasse eine Nachricht, die zuvor reserviert war.|
|[enable_batched_processing](#enable_batched_processing)|Aktiviert die Batch Verarbeitung für diesen Block.|
|[initialize_source](#initialize_source)|Initialisiert die `message_propagator` in diesem `source_block`.|
|[link_target_notification](#link_target_notification)|Ein Rückruf, der benachrichtigt, dass ein neues Ziel mit diesem `source_block` Objekt verknüpft wurde.|
|[process_input_messages](#process_input_messages)|Verarbeiten von Eingabe Nachrichten. Dies ist nur für propagatorblöcke nützlich, die von abgeleitet werden source_block|
|[propagate_output_messages](#propagate_output_messages)|Weiterleiten von Nachrichten an Ziele.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Gibt beim Überschreiben in einer abgeleiteten Klasse die angegebene Nachricht an ein beliebiges oder alle verknüpften Ziele weiter. Dies ist die hauptpropagierungs Routine für Nachrichten Blöcke.|
|[release_message](#release_message)|Gibt beim Überschreiben in einer abgeleiteten Klasse eine vorherige Nachrichten Reservierung frei.|
|[remove_targets](#remove_targets)|Entfernt alle Ziel Verknüpfungen für diesen Quell Block. Dies sollte vom Dekonstruktor aufgerufen werden.|
|[reserve_message](#reserve_message)|Reserviert beim Überschreiben in einer abgeleiteten Klasse eine Meldung, die zuvor von diesem `source_block` Objekt bereitgestellt wurde.|
|[resume_propagation](#resume_propagation)|Setzt beim Überschreiben in einer abgeleiteten Klasse die Verteilung fort, nachdem eine Reservierung freigegeben wurde.|
|[sync_send](#sync_send)|Fügt Nachrichten synchron in die Warteschlange ein und startet einen propagierungs Task, wenn dies noch nicht geschehen ist.|
|[unlink_target_notification](#unlink_target_notification)|Ein Rückruf, der benachrichtigt, dass die Verknüpfung eines Ziels mit diesem `source_block` Objekt aufgehoben wurde.|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Wartet, bis alle asynchronen Propagierungen vollständig sind. Diese weiterverweiterungsspezifische Spin-Wartezeit wird in debugktoren von Nachrichten Blöcken verwendet, um sicherzustellen, dass alle asynchronen Weiterungen Zeit bis zum Ende haben, bevor der Block zerstört wird.|

## <a name="remarks"></a>Bemerkungen

Nachrichten Blöcke sollten von diesem Block abgeleitet werden, um die von dieser Klasse bereitgestellte Link Verwaltung und Synchronisierung zu nutzen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="accept"></a>erst

Akzeptiert eine Meldung, die von diesem `source_block` Objekt angeboten wurde, und überträgt den Besitz an den Aufrufer.

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Die `runtime_object_identity` des angebotenen `message` Objekts.

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der die `accept` Methode aufrufen.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `message` Objekt, für das der Aufrufer nun den Besitz hat.

### <a name="remarks"></a>Bemerkungen

Die-Methode löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn der Parameter `_PTarget` `NULL`ist.

Die `accept`-Methode wird von einem Ziel aufgerufen, während eine Nachricht von diesem `ISource` Block angeboten wird. Der zurückgegebene Meldungs Zeiger unterscheidet sich möglicherweise von dem, der an die `propagate`-Methode des `ITarget` Blocks übertragen wird, wenn diese Quelle beschließt, eine Kopie der Nachricht zu erstellen.

## <a name="accept_message"></a>accept_message

Akzeptiert beim Überschreiben in einer abgeleiteten Klasse eine angebotene Nachricht von der Quelle. Nachrichten Blöcke sollten diese Methode überschreiben, um die `_MsgId` zu überprüfen und eine Meldung zurückzugeben.

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Die Laufzeitobjekt Identität des `message` Objekts.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Nachricht, für die der Aufrufer nun den Besitz hat.

### <a name="remarks"></a>Bemerkungen

Um den Besitz zu übertragen, sollte der ursprüngliche Nachrichten Zeiger zurückgegeben werden. Um den Besitz aufrechtzuerhalten, muss eine Kopie der Nachrichten Nutzlast erstellt und zurückgegeben werden.

## <a name="acquire_ref"></a>acquire_ref

Ruft einen Verweis Zähler für dieses `source_block` Objekt ab, um das Löschen zu verhindern.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von einem `ITarget` Objekt aufgerufen, das während der `link_target` Methode mit dieser Quelle verknüpft wird.

## <a name="async_send"></a>async_send

Fügt Nachrichten asynchron in die Warteschlange ein und startet einen propagierungs Task, wenn dies noch nicht geschehen ist.

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parameter

*_Msg*<br/>
Ein Zeiger auf ein `message` Objekt, das asynchron gesendet werden soll.

## <a name="consume"></a>Verzehr

Verarbeitet eine Meldung, die zuvor von diesem `source_block` Objekt bereitgestellt und vom Ziel erfolgreich reserviert wurde, und überträgt den Besitz an den Aufrufer.

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Die `runtime_object_identity` des reservierten `message` Objekts.

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der die `consume` Methode aufrufen.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `message` Objekt, für das der Aufrufer nun den Besitz hat.

### <a name="remarks"></a>Bemerkungen

Die-Methode löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn der Parameter `_PTarget` `NULL`ist.

Die-Methode löst eine [Bad_target](bad-target-class.md) Ausnahme aus, wenn der Parameter `_PTarget` nicht das Ziel darstellt, das `reserve`aufgerufen hat.

Die `consume`-Methode ähnelt `accept`, aber muss immer ein `reserve` aufgerufen werden, der " **true**" zurückgegeben hat.

## <a name="consume_message"></a>consume_message

Verarbeitet beim Überschreiben in einer abgeleiteten Klasse eine Nachricht, die zuvor reserviert war.

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Die `runtime_object_identity` des verbrauchten `message` Objekts.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Nachricht, für die der Aufrufer nun den Besitz hat.

### <a name="remarks"></a>Bemerkungen

Ähnlich wie bei `accept`, dem aber immer ein Aufruf`reserve`vorangestellt ist.

## <a name="enable_batched_processing"></a>enable_batched_processing

Aktiviert die Batch Verarbeitung für diesen Block.

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a>initialize_source

Initialisiert die `message_propagator` in diesem `source_block`.

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parameter

*_PScheduler*<br/>
Der Planer, der zum Planen von Aufgaben verwendet werden soll.

*_PScheduleGroup*<br/>
Die Zeit Plan Gruppe, die zum Planen von Aufgaben verwendet werden soll.

## <a name="link_target"></a>link_target

Verknüpft einen Zielblock mit diesem `source_block` Objekt.

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Ein Zeiger auf einen `ITarget` Block, der mit diesem `source_block` Objekt verknüpft werden soll.

### <a name="remarks"></a>Bemerkungen

Die-Methode löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn der Parameter `_PTarget` `NULL`ist.

## <a name="link_target_notification"></a>link_target_notification

Ein Rückruf, der benachrichtigt, dass ein neues Ziel mit diesem `source_block` Objekt verknüpft wurde.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a>process_input_messages

Verarbeiten von Eingabe Nachrichten. Dies ist nur für propagatorblöcke nützlich, die von abgeleitet werden source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parameter

*_PMessage*<br/>
Ein Zeiger auf die Meldung, die verarbeitet werden soll.

## <a name="propagate_output_messages"></a>propagate_output_messages

Weiterleiten von Nachrichten an Ziele.

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Gibt beim Überschreiben in einer abgeleiteten Klasse die angegebene Nachricht an ein beliebiges oder alle verknüpften Ziele weiter. Dies ist die hauptpropagierungs Routine für Nachrichten Blöcke.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parameter

*_PMessage*<br/>
Ein Zeiger auf die Meldung, die weitergegeben werden soll.

## <a name="release"></a>Abgabe

Gibt eine vorherige erfolgreiche Nachrichten Reservierung frei.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Die `runtime_object_identity` des reservierten `message` Objekts.

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der die `release` Methode aufrufen.

### <a name="remarks"></a>Bemerkungen

Die-Methode löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn der Parameter `_PTarget` `NULL`ist.

Die-Methode löst eine [Bad_target](bad-target-class.md) Ausnahme aus, wenn der Parameter `_PTarget` nicht das Ziel darstellt, das `reserve`aufgerufen hat.

## <a name="release_message"></a>release_message

Gibt beim Überschreiben in einer abgeleiteten Klasse eine vorherige Nachrichten Reservierung frei.

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Die `runtime_object_identity` des `message` Objekts, das freigegeben wird.

## <a name="release_ref"></a>release_ref

Gibt einen Verweis Zähler für dieses `source_block` Objekt frei.

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der diese Methode aufgerufen hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von einem `ITarget` Objekt aufgerufen, das von dieser Quelle entfernt wird. Der Quell Block darf alle für den Zielblock reservierten Ressourcen freigeben.

## <a name="remove_targets"></a>remove_targets

Entfernt alle Ziel Verknüpfungen für diesen Quell Block. Dies sollte vom Dekonstruktor aufgerufen werden.

```cpp
void remove_targets();
```

## <a name="reserve"></a>Schutz

Reserviert eine Meldung, die zuvor von diesem `source_block` Objekt angeboten wurde.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Die `runtime_object_identity` des angebotenen `message` Objekts.

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der die `reserve` Methode aufrufen.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Nachricht erfolgreich reserviert wurde, andernfalls **false** . Reservierungen können aus vielen Gründen fehlschlagen, z.b.: die Nachricht wurde bereits von einem anderen Ziel reserviert oder akzeptiert, die Quelle könnte Reservierungen ablehnen usw.

### <a name="remarks"></a>Bemerkungen

Die-Methode löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn der Parameter `_PTarget` `NULL`ist.

Nachdem Sie `reserve`aufgerufen haben, müssen Sie bei erfolgreicher Ausführung entweder `consume` oder `release` abrufen, um die Nachricht bzw. den Besitz der Nachricht zu übernehmen.

## <a name="reserve_message"></a>reserve_message

Reserviert beim Überschreiben in einer abgeleiteten Klasse eine Meldung, die zuvor von diesem `source_block` Objekt bereitgestellt wurde.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Die `runtime_object_identity` des reservierten `message` Objekts.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Nachricht erfolgreich reserviert wurde, andernfalls **false** .

### <a name="remarks"></a>Bemerkungen

Wenn `reserve` aufgerufen wird, muss entweder `consume` oder `release` aufgerufen **werden, um**den Besitz der Nachricht zu übernehmen oder freizugeben.

## <a name="resume_propagation"></a>resume_propagation

Setzt beim Überschreiben in einer abgeleiteten Klasse die Verteilung fort, nachdem eine Reservierung freigegeben wurde.

```cpp
virtual void resume_propagation() = 0;
```

## <a name="ctor"></a>source_block

Erstellt ein `source_block`-Objekt.

```cpp
source_block();
```

## <a name="dtor"></a>~ source_block

Zerstört das `source_block`-Objekt.

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a>sync_send

Fügt Nachrichten synchron in die Warteschlange ein und startet einen propagierungs Task, wenn dies noch nicht geschehen ist.

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parameter

*_Msg*<br/>
Ein Zeiger auf ein `message` Objekt, das synchron gesendet werden soll.

## <a name="unlink_target"></a>unlink_target

Entbindet einen Zielblock von diesem `source_block` Objekt.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Ein Zeiger auf einen `ITarget` Block, um die Verknüpfung mit diesem `source_block`-Objekt aufzulösen.

### <a name="remarks"></a>Bemerkungen

Die-Methode löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn der Parameter `_PTarget` `NULL`ist.

## <a name="unlink_target_notification"></a>unlink_target_notification

Ein Rückruf, der benachrichtigt, dass die Verknüpfung eines Ziels mit diesem `source_block` Objekt aufgehoben wurde.

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Der `ITarget` Block, der nicht verknüpft wurde.

## <a name="unlink_targets"></a>unlink_targets

Hebt die Verknüpfung aller Ziel Blöcke von diesem `source_block` Objekt auf.

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends

Wartet, bis alle asynchronen Propagierungen vollständig sind. Diese weiterverweiterungsspezifische Spin-Wartezeit wird in debugktoren von Nachrichten Blöcken verwendet, um sicherzustellen, dass alle asynchronen Weiterungen Zeit bis zum Ende haben, bevor der Block zerstört wird.

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[ISource-Klasse](isource-class.md)
