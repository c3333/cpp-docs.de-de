---
title: join-Klasse
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: c65eed8abafe424fa27c5b9a72d3c73b7127b68e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219585"
---
# <a name="join-class"></a>join-Klasse

Ein `join`-Meldungsblock ist ein geordneter `propagator_block` mit mehreren Quellen und einem einzelnen Ziel, der Meldungen vom Typ `T` aus allen Quellen kombiniert.

## <a name="syntax"></a>Syntax

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Nutz Lasttyp der Nachrichten, die dem-Block hinzugefügt und weitergegeben werden.

*_Jtype*<br/>
Die Art von `join` Block this ist, entweder `greedy` oder.`non_greedy`

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[join](#ctor)|Ist überladen. Erstellt einen `join` -Meldungsblock.|
|[~ Join-Dekonstruktor](#dtor)|Zerstört den- `join` Block.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[accept_message](#accept_message)|Akzeptiert eine Meldung, die von diesem `join` Messaging Block angeboten wurde, und überträgt den Besitz an den Aufrufer.|
|[consume_message](#consume_message)|Verarbeitet eine Meldung, die zuvor vom `join` Messaging Block angeboten und vom Ziel reserviert wurde, und überträgt den Besitz an den Aufrufer.|
|[link_target_notification](#link_target_notification)|Ein Rückruf, der benachrichtigt, dass ein neues Ziel mit diesem `join` Messaging Block verknüpft wurde.|
|[propagate_message](#propagate_message)|Übergibt eine Nachricht asynchron von einem- `ISource` Block an diesen `join` Messaging Block. Sie wird von der- `propagate` Methode aufgerufen, wenn Sie von einem Quell Block aufgerufen wird.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Erstellt eine Ausgabe Nachricht, die eine Eingabe Nachricht aus jeder Quelle enthält, wenn alle eine Nachricht weitergegeben haben. Sendet diese Ausgabe Nachricht an jedes ihrer Ziele.|
|[release_message](#release_message)|Gibt eine vorherige Nachrichten Reservierung frei. (Überschreibt [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Reserviert eine Meldung, die zuvor von diesem `join` Messaging Block angeboten wurde. (Überschreibt [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Setzt die Verteilung fort, nachdem eine Reservierung freigegeben wurde. (Überschreibt [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [asynchrone Nachrichten Blöcke](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Akzeptiert eine Meldung, die von diesem `join` Messaging Block angeboten wurde, und überträgt den Besitz an den Aufrufer.

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des angebotenen `message` Objekts.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `message` Objekt, für das der Aufrufer nun den Besitz hat.

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Verarbeitet eine Meldung, die zuvor vom `join` Messaging Block angeboten und vom Ziel reserviert wurde, und überträgt den Besitz an den Aufrufer.

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des `message` Objekts, das verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `message` Objekt, für das der Aufrufer nun den Besitz hat.

### <a name="remarks"></a>Bemerkungen

Ähnlich wie `accept` , ist jedoch immer ein-Rückruf vorangestellt `reserve` .

## <a name="join"></a><a name="ctor"></a>Join

Erstellt einen `join` -Meldungsblock.

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parameter

*_NumInputs*<br/>
Die Anzahl der Eingaben, die dieser `join` Block zulässt.

*_Filter*<br/>
Eine Filterfunktion, die bestimmt, ob angebotene Nachrichten akzeptiert werden sollen.

*_PScheduler*<br/>
Das `Scheduler` -Objekt, in dem die Weiterleitungsaufgabe für den `join` -Meldungsblock geplant ist.

*_PScheduleGroup*<br/>
Das `ScheduleGroup` -Objekt, in dem die Weiterleitungsaufgabe für den `join` -Meldungsblock geplant ist. Das verwendete `Scheduler` -Objekt wird von der Planungsgruppe impliziert.

### <a name="remarks"></a>Bemerkungen

Die Runtime verwendet das Standardplanungsprogramm, wenn Sie den `_PScheduler` -Parameter oder den `_PScheduleGroup` -Parameter nicht angeben.

Der Typ `filter_method` ist ein Funktor mit einer Signatur `bool (T const &)` , die von diesem `join` Messaging Block aufgerufen wird, um zu bestimmen, ob er eine angebotene Nachricht akzeptieren soll.

## <a name="join"></a><a name="dtor"></a>~ Join

Zerstört den- `join` Block.

```cpp
~join();
```

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Ein Rückruf, der benachrichtigt, dass ein neues Ziel mit diesem `join` Messaging Block verknüpft wurde.

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

Übergibt eine Nachricht asynchron von einem- `ISource` Block an diesen `join` Messaging Block. Sie wird von der- `propagate` Methode aufgerufen, wenn Sie von einem Quell Block aufgerufen wird.

```cpp
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parameter

*_PMessage*<br/>
Ein Zeiger auf das `message`-Objekt.

*_PSource*<br/>
Ein Zeiger auf den Quell Block, der die Nachricht anbietet.

### <a name="return-value"></a>Rückgabewert

Eine [Message_status](concurrency-namespace-enums.md) , die angibt, wie sich das Ziel für die Nachricht entschieden hat.

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

Erstellt eine Ausgabe Nachricht, die eine Eingabe Nachricht aus jeder Quelle enthält, wenn alle eine Nachricht weitergegeben haben. Sendet diese Ausgabe Nachricht an jedes ihrer Ziele.

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```

## <a name="release_message"></a><a name="release_message"></a>release_message

Gibt eine vorherige Nachrichten Reservierung frei.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des `message` Objekts, das freigegeben wird.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Reserviert eine Meldung, die zuvor von diesem `join` Messaging Block angeboten wurde.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des angebotenen `message` Objekts.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Nachricht erfolgreich reserviert wurde, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Nachdem `reserve` aufgerufen wurde, muss, wenn zurückgegeben wird **`true`** , entweder `consume` oder `release` aufgerufen werden, um den Besitz der Nachricht zu übernehmen oder freizugeben.

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

Setzt die Verteilung fort, nachdem eine Reservierung freigegeben wurde.

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[Choice-Klasse](choice-class.md)<br/>
[multitype_join-Klasse](multitype-join-class.md)
