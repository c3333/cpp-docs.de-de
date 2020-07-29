---
title: unbounded_buffer-Klasse
ms.date: 11/04/2016
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: e02fa1ffbf4c3e2c7d17dfe2d6ae66758945d9de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219519"
---
# <a name="unbounded_buffer-class"></a>unbounded_buffer-Klasse

Ein `unbounded_buffer`-Meldungsblock ist ein geordneter `propagator_block` mit mehreren Zielen und mehreren Quellen, der eine unbegrenzte Anzahl von Meldungen speichern kann.

## <a name="syntax"></a>Syntax

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>Parameter

*_Type*<br/>
Der Nutz Lasttyp der Nachrichten, die vom Puffer gespeichert und weitergegeben werden.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Ist überladen. Erstellt einen `unbounded_buffer` Messaging Block.|
|[~ UNBOUNDED_BUFFER-Dekonstruktor](#dtor)|Zerstört den `unbounded_buffer` Messaging-Block.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Dequeue](#dequeue)|Entfernt ein Element aus dem `unbounded_buffer` Messaging Block.|
|[einreihen](#enqueue)|Fügt dem Messaging Block ein Element hinzu `unbounded_buffer` .|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[accept_message](#accept_message)|Akzeptiert eine Meldung, die von diesem `unbounded_buffer` Messaging Block angeboten wurde, und überträgt den Besitz an den Aufrufer.|
|[consume_message](#consume_message)|Verarbeitet eine Meldung, die zuvor vom `unbounded_buffer` Messaging Block angeboten und vom Ziel reserviert wurde, und überträgt den Besitz an den Aufrufer.|
|[link_target_notification](#link_target_notification)|Ein Rückruf, der benachrichtigt, dass ein neues Ziel mit diesem `unbounded_buffer` Messaging Block verknüpft wurde.|
|[process_input_messages](#process_input_messages)|Platziert den `message` `_PMessage` in diesem `unbounded_buffer` Messaging Block und versucht, ihn für alle verknüpften Ziele anzubieten.|
|[propagate_message](#propagate_message)|Übergibt eine Nachricht asynchron von einem- `ISource` Block an diesen `unbounded_buffer` Messaging Block. Sie wird von der- `propagate` Methode aufgerufen, wenn Sie von einem Quell Block aufgerufen wird.|
|[propagate_output_messages](#propagate_output_messages)|Platziert den `message` `_PMessage` in diesem `unbounded_buffer` Messaging Block und versucht, ihn für alle verknüpften Ziele anzubieten. (Überschreibt [source_block::p ropagate_output_messages](source-block-class.md#propagate_output_messages).)|
|[release_message](#release_message)|Gibt eine vorherige Nachrichten Reservierung frei. (Überschreibt [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Reserviert eine Meldung, die zuvor von diesem `unbounded_buffer` Messaging Block angeboten wurde. (Überschreibt [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Setzt die Verteilung fort, nachdem eine Reservierung freigegeben wurde. (Überschreibt [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Übergibt eine Nachricht synchron von einem- `ISource` Block an diesen `unbounded_buffer` Messaging Block. Sie wird von der- `send` Methode aufgerufen, wenn Sie von einem Quell Block aufgerufen wird.|
|[supports_anonymous_source](#supports_anonymous_source)|Überschreibt die- `supports_anonymous_source` Methode, um anzugeben, dass dieser Block Nachrichten akzeptieren kann, die ihm von einer nicht verknüpften Quelle angeboten werden. (Überschreibt [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

Weitere Informationen finden Sie unter [asynchrone Nachrichten Blöcke](../asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Akzeptiert eine Meldung, die von diesem `unbounded_buffer` Messaging Block angeboten wurde, und überträgt den Besitz an den Aufrufer.

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des angebotenen `message` Objekts.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `message` Objekt, für das der Aufrufer nun den Besitz hat.

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Verarbeitet eine Meldung, die zuvor vom `unbounded_buffer` Messaging Block angeboten und vom Ziel reserviert wurde, und überträgt den Besitz an den Aufrufer.

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des `message` Objekts, das verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `message` Objekt, für das der Aufrufer nun den Besitz hat.

### <a name="remarks"></a>Bemerkungen

Ähnlich wie `accept` , ist jedoch immer ein-Rückruf vorangestellt `reserve` .

## <a name="dequeue"></a><a name="dequeue"></a>Dequeue

Entfernt ein Element aus dem `unbounded_buffer` Messaging Block.

```cpp
_Type dequeue();
```

### <a name="return-value"></a>Rückgabewert

Die Nutzlast der Nachricht, die aus der entfernt wurde `unbounded_buffer` .

## <a name="enqueue"></a><a name="enqueue"></a>einreihen

Fügt dem Messaging Block ein Element hinzu `unbounded_buffer` .

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Parameter

*_Item*<br/>
Das Element, das hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das Element akzeptiert wurde, **`false`** andernfalls.

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Ein Rückruf, der benachrichtigt, dass ein neues Ziel mit diesem `unbounded_buffer` Messaging Block verknüpft wurde.

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Ein Zeiger auf das neu verknüpfte Ziel.

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

Übergibt eine Nachricht asynchron von einem- `ISource` Block an diesen `unbounded_buffer` Messaging Block. Sie wird von der- `propagate` Methode aufgerufen, wenn Sie von einem Quell Block aufgerufen wird.

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parameter

*_PMessage*<br/>
Ein Zeiger auf das `message`-Objekt.

*_PSource*<br/>
Ein Zeiger auf den Quell Block, der die Nachricht anbietet.

### <a name="return-value"></a>Rückgabewert

Eine [Message_status](concurrency-namespace-enums.md#message_status) , die angibt, wie sich das Ziel für die Nachricht entschieden hat.

## <a name="propagate_output_messages"></a><a name="propagate_output_messages"></a>propagate_output_messages

Platziert den `message` `_PMessage` in diesem `unbounded_buffer` Messaging Block und versucht, ihn für alle verknüpften Ziele anzubieten.

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Bemerkungen

Wenn in der bereits eine andere Nachricht vorhanden ist, erfolgt die Weitergabe `unbounded_buffer` an verknüpfte Ziele erst, wenn frühere Nachrichten akzeptiert oder verarbeitet wurden. Das erste verknüpfte Ziel für `accept` `consume` war erfolgreich, oder die Nachricht übernimmt den Besitz, und kein anderes Ziel kann dann die Nachricht erhalten.

## <a name="process_input_messages"></a><a name="process_input_messages"></a>process_input_messages

Platziert den `message` `_PMessage` in diesem `unbounded_buffer` Messaging Block und versucht, ihn für alle verknüpften Ziele anzubieten.

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Parameter

*_PMessage*<br/>
Ein Zeiger auf die Meldung, die verarbeitet werden soll.

## <a name="release_message"></a><a name="release_message"></a>release_message

Gibt eine vorherige Nachrichten Reservierung frei.

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des `message` Objekts, das freigegeben wird.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Reserviert eine Meldung, die zuvor von diesem `unbounded_buffer` Messaging Block angeboten wurde.

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des `message` Objekts, das reserviert wird.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Nachricht erfolgreich reserviert wurde, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Nachdem `reserve` aufgerufen wurde, muss, wenn zurückgegeben wird **`true`** , entweder `consume` oder `release` aufgerufen werden, um den Besitz der Nachricht zu übernehmen oder freizugeben.

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

Setzt die Verteilung fort, nachdem eine Reservierung freigegeben wurde.

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a><a name="send_message"></a>send_message

Übergibt eine Nachricht synchron von einem- `ISource` Block an diesen `unbounded_buffer` Messaging Block. Sie wird von der- `send` Methode aufgerufen, wenn Sie von einem Quell Block aufgerufen wird.

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parameter

*_PMessage*<br/>
Ein Zeiger auf das `message`-Objekt.

*_PSource*<br/>
Ein Zeiger auf den Quell Block, der die Nachricht anbietet.

### <a name="return-value"></a>Rückgabewert

Eine [Message_status](concurrency-namespace-enums.md#message_status) , die angibt, wie sich das Ziel für die Nachricht entschieden hat.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

Überschreibt die- `supports_anonymous_source` Methode, um anzugeben, dass dieser Block Nachrichten akzeptieren kann, die ihm von einer nicht verknüpften Quelle angeboten werden.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Rückgabewert

**`true`**, da angebotene Nachrichten durch den-Block nicht verschoben werden.

## <a name="unbounded_buffer"></a><a name="ctor"></a>unbounded_buffer

Erstellt einen `unbounded_buffer` Messaging Block.

```cpp
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>Parameter

*_Filter*<br/>
Eine Filterfunktion, die bestimmt, ob angebotene Nachrichten akzeptiert werden sollen.

*_PScheduler*<br/>
Das `Scheduler` -Objekt, in dem die Weiterleitungsaufgabe für den `unbounded_buffer` -Meldungsblock geplant ist.

*_PScheduleGroup*<br/>
Das `ScheduleGroup` -Objekt, in dem die Weiterleitungsaufgabe für den `unbounded_buffer` -Meldungsblock geplant ist. Das verwendete `Scheduler` -Objekt wird von der Planungsgruppe impliziert.

### <a name="remarks"></a>Bemerkungen

Die Runtime verwendet das Standardplanungsprogramm, wenn Sie den `_PScheduler` -Parameter oder den `_PScheduleGroup` -Parameter nicht angeben.

Der Typ `filter_method` ist ein Funktor mit einer Signatur `bool (_Type const &)` , die von diesem `unbounded_buffer` Messaging Block aufgerufen wird, um zu bestimmen, ob er eine angebotene Nachricht akzeptieren soll.

## <a name="unbounded_buffer"></a><a name="dtor"></a>~ UNBOUNDED_BUFFER

Zerstört den `unbounded_buffer` Messaging-Block.

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[overwrite_buffer-Klasse](overwrite-buffer-class.md)<br/>
[Single_assignment-Klasse](single-assignment-class.md)
