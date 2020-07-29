---
title: ISource-Klasse
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: df592e965b436ed5a1d60702f9e57088887d5a94
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222705"
---
# <a name="isource-class"></a>ISource-Klasse

Die `ISource`-Klasse ist die Schnittstelle für alle Quellblöcke. Quellblöcke geben Meldungen an `ITarget`-Blöcke weiter.

## <a name="syntax"></a>Syntax

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Nutzlast in den Nachrichten, die vom Quell Block erzeugt werden.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`source_type`|Ein Typalias für `T` .|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[~ ISource-Dekonstruktor](#dtor)|Zerstört das `ISource`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[erst](#accept)|Akzeptiert beim Überschreiben in einer abgeleiteten Klasse eine Nachricht, die von diesem Block angeboten wurde `ISource` , und überträgt den Besitz an den Aufrufer.|
|[acquire_ref](#acquire_ref)|Ruft beim Überschreiben in einer abgeleiteten Klasse einen Verweis Zähler für diesen `ISource` Block ab, um das Löschen zu verhindern.|
|[Verzehr](#consume)|Verarbeitet beim Überschreiben in einer abgeleiteten Klasse eine Meldung, die zuvor von diesem `ISource` Block angeboten und erfolgreich vom Ziel reserviert wurde, und überträgt den Besitz an den Aufrufer.|
|[link_target](#link_target)|Verknüpft beim Überschreiben in einer abgeleiteten Klasse einen Zielblock mit diesem `ISource` Block.|
|[Abgabe](#release)|Gibt beim Überschreiben in einer abgeleiteten Klasse eine vorherige erfolgreiche Nachrichten Reservierung frei.|
|[release_ref](#release_ref)|Gibt beim Überschreiben in einer abgeleiteten Klasse einen Verweis Zähler für diesen `ISource` Block frei.|
|[Reserve](#reserve)|Reserviert beim Überschreiben in einer abgeleiteten Klasse eine Meldung, die zuvor von diesem Block angeboten wurde `ISource` .|
|[unlink_target](#unlink_target)|Beim Überschreiben in einer abgeleiteten Klasse wird ein Zielblock von diesem `ISource` Block entfernt, sofern dieser bereits verknüpft ist.|
|[unlink_targets](#unlink_targets)|Hebt beim Überschreiben in einer abgeleiteten Klasse die Verknüpfung aller Ziel Blöcke mit diesem `ISource` Block auf.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [asynchrone Nachrichten Blöcke](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ISource`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="accept"></a><a name="accept"></a>erst

Akzeptiert beim Überschreiben in einer abgeleiteten Klasse eine Nachricht, die von diesem Block angeboten wurde `ISource` , und überträgt den Besitz an den Aufrufer.

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des angebotenen `message` Objekts.

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der die- `accept` Methode aufgerufen hat.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Nachricht, für die der Aufrufer nun den Besitz hat.

### <a name="remarks"></a>Bemerkungen

Die- `accept` Methode wird von einem Ziel aufgerufen, während eine Nachricht von diesem Block angeboten wird `ISource` . Der zurückgegebene Meldungs Zeiger unterscheidet sich möglicherweise von dem, der an die- `propagate` Methode des-Blocks übertragen wird `ITarget` , wenn diese Quelle beschließt, eine Kopie der Nachricht zu erstellen.

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

Ruft beim Überschreiben in einer abgeleiteten Klasse einen Verweis Zähler für diesen `ISource` Block ab, um das Löschen zu verhindern.

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der diese Methode aufgerufen hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von einem `ITarget` Objekt aufgerufen, das während der-Methode mit dieser Quelle verknüpft wird `link_target` .

## <a name="consume"></a><a name="consume"></a>Verzehr

Verarbeitet beim Überschreiben in einer abgeleiteten Klasse eine Meldung, die zuvor von diesem `ISource` Block angeboten und erfolgreich vom Ziel reserviert wurde, und überträgt den Besitz an den Aufrufer.

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des reservierten `message` Objekts.

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der die- `consume` Methode aufgerufen hat.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `message` Objekt, für das der Aufrufer nun den Besitz hat.

### <a name="remarks"></a>Bemerkungen

Die- `consume` Methode ähnelt `accept` , muss jedoch immer durch einen-Rückruf vorangestellt werden, der `reserve` zurückgegeben wurde **`true`** .

## <a name="isource"></a><a name="dtor"></a>~ ISource

Zerstört das `ISource`-Objekt.

```cpp
virtual ~ISource();
```

## <a name="link_target"></a><a name="link_target"></a>link_target

Verknüpft beim Überschreiben in einer abgeleiteten Klasse einen Zielblock mit diesem `ISource` Block.

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der mit diesem `ISource` Block verknüpft wird.

## <a name="release"></a><a name="release"></a>Abgabe

Gibt beim Überschreiben in einer abgeleiteten Klasse eine vorherige erfolgreiche Nachrichten Reservierung frei.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des reservierten `message` Objekts.

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der die- `release` Methode aufgerufen hat.

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

Gibt beim Überschreiben in einer abgeleiteten Klasse einen Verweis Zähler für diesen `ISource` Block frei.

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der diese Methode aufgerufen hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von einem `ITarget` Objekt aufgerufen, das von dieser Quelle entfernt wird. Der Quell Block darf alle für den Zielblock reservierten Ressourcen freigeben.

## <a name="reserve"></a><a name="reserve"></a>Schutz

Reserviert beim Überschreiben in einer abgeleiteten Klasse eine Meldung, die zuvor von diesem Block angeboten wurde `ISource` .

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parameter

*_MsgId*<br/>
Der `runtime_object_identity` des angebotenen `message` Objekts.

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, der die- `reserve` Methode aufgerufen hat.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Nachricht erfolgreich reserviert wurde, **`false`** andernfalls. Reservierungen können aus vielen Gründen fehlschlagen, z.b.: die Nachricht wurde bereits von einem anderen Ziel reserviert oder akzeptiert, die Quelle könnte Reservierungen ablehnen usw.

### <a name="remarks"></a>Bemerkungen

Nachdem Sie aufgerufen `reserve` haben, müssen Sie, wenn dies erfolgreich ist, entweder oder ausführen, um `consume` `release` die Nachricht bzw. den Besitz der Nachricht zu übernehmen.

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

Beim Überschreiben in einer abgeleiteten Klasse wird ein Zielblock von diesem `ISource` Block entfernt, sofern dieser bereits verknüpft ist.

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parameter

*_PTarget*<br/>
Ein Zeiger auf den Zielblock, von dem die Verknüpfung mit diesem Block aufgehoben wird `ISource` .

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

Hebt beim Überschreiben in einer abgeleiteten Klasse die Verknüpfung aller Ziel Blöcke mit diesem `ISource` Block auf.

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[ITarget-Klasse](itarget-class.md)
