---
title: ITarget-Klasse
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: 39aebd9d82f098225c1275ac6f43d64fc1ce3ba8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231714"
---
# <a name="itarget-class"></a>ITarget-Klasse

Die `ITarget`-Klasse ist die Schnittstelle für alle Zielblöcke. Zielblöcke nehmen Meldungen auf, die von `ISource`-Blöcken angeboten werden.

## <a name="syntax"></a>Syntax

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Nutzlast in den Nachrichten, die vom Zielblock akzeptiert werden.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`filter_method`|Die Signatur einer beliebigen Methode, die vom-Block verwendet wird, der einen Wert zurückgibt **`bool`** , um zu bestimmen, ob eine angebotene Nachricht akzeptiert werden soll.|
|`type`|Ein Typalias für `T` .|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[~ ITarget-Dekonstruktor](#dtor)|Zerstört das `ITarget`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Pixeln](#propagate)|Übergibt beim Überschreiben in einer abgeleiteten Klasse eine Nachricht asynchron von einem Quell Block an diesen Zielblock.|
|[send](#send)|Übergibt beim Überschreiben in einer abgeleiteten Klasse eine Nachricht synchron an den Zielblock.|
|[supports_anonymous_source](#supports_anonymous_source)|Gibt beim Überschreiben in einer abgeleiteten Klasse true oder false zurück, abhängig davon, ob der Nachrichtenblock von einer nicht verknüpften Quelle angebotene Nachrichten akzeptiert. Wenn die überschriebene Methode zurückgibt **`true`** , kann das Ziel eine angebotene Nachricht nicht verschieben, da für den Verbrauch einer verschobenen Nachricht zu einem späteren Zeitpunkt die Quelle in ihrer Quell Verknüpfungs Registrierung identifiziert werden muss.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[link_source](#link_source)|Verknüpft beim Überschreiben in einer abgeleiteten Klasse einen angegebenen Quell Block mit diesem `ITarget` Block.|
|[unlink_source](#unlink_source)|Entfernt beim Überschreiben in einer abgeleiteten Klasse die Verknüpfung eines angegebenen Quell Blocks mit diesem `ITarget` Block.|
|[unlink_sources](#unlink_sources)|Hebt beim Überschreiben in einer abgeleiteten Klasse die Verknüpfung aller Quell Blöcke mit diesem `ITarget` Block auf.|

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [asynchrone Nachrichten Blöcke](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ITarget`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** agents.h

**Namespace:** Parallelität

## <a name="itarget"></a><a name="dtor"></a>~ ITarget

Zerstört das `ITarget`-Objekt.

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a><a name="link_source"></a>link_source

Verknüpft beim Überschreiben in einer abgeleiteten Klasse einen angegebenen Quell Block mit diesem `ITarget` Block.

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parameter

*_PSource*<br/>
Der `ISource` Block, der mit diesem `ITarget` Block verknüpft wird.

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nicht direkt auf einem-Block aufgerufen werden `ITarget` . -Blöcke sollten mithilfe der- `link_target` Methode für- `ISource` Blöcke verbunden werden, die die- `link_source` Methode für das entsprechende Ziel aufrufen.

## <a name="propagate"></a><a name="propagate"></a>Pixeln

Übergibt beim Überschreiben in einer abgeleiteten Klasse eine Nachricht asynchron von einem Quell Block an diesen Zielblock.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parameter

*_PMessage*<br/>
Ein Zeiger auf das `message`-Objekt.

*_PSource*<br/>
Ein Zeiger auf den Quell Block, der die Nachricht anbietet.

### <a name="return-value"></a>Rückgabewert

Eine [Message_status](concurrency-namespace-enums.md) , die angibt, wie sich das Ziel für die Nachricht entschieden hat.

### <a name="remarks"></a>Bemerkungen

Die-Methode löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn der- `_PMessage` Parameter oder der- `_PSource` Parameter ist `NULL` .

## <a name="send"></a><a name="send"></a>Senden

Übergibt beim Überschreiben in einer abgeleiteten Klasse eine Nachricht synchron an den Zielblock.

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parameter

*_PMessage*<br/>
Ein Zeiger auf das `message`-Objekt.

*_PSource*<br/>
Ein Zeiger auf den Quell Block, der die Nachricht anbietet.

### <a name="return-value"></a>Rückgabewert

Eine [Message_status](concurrency-namespace-enums.md) , die angibt, wie sich das Ziel für die Nachricht entschieden hat.

### <a name="remarks"></a>Bemerkungen

Die-Methode löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn der- `_PMessage` Parameter oder der- `_PSource` Parameter ist `NULL` .

Die Verwendung der `send` Methode außerhalb der Nachrichten Initiierung und die Weitergabe von Nachrichten innerhalb eines Netzwerks ist gefährlich und kann zu einem Deadlock führen.

Wenn `send` zurückgibt, wurde die Nachricht entweder bereits akzeptiert und in den Zielblock übertragen, oder Sie wurde vom Ziel abgelehnt.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

Gibt beim Überschreiben in einer abgeleiteten Klasse true oder false zurück, abhängig davon, ob der Nachrichtenblock von einer nicht verknüpften Quelle angebotene Nachrichten akzeptiert. Wenn die überschriebene Methode zurückgibt **`true`** , kann das Ziel eine angebotene Nachricht nicht verschieben, da für den Verbrauch einer verschobenen Nachricht zu einem späteren Zeitpunkt die Quelle in der sourse-Link Registrierung identifiziert werden muss.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Block eine Nachricht von einer Quelle akzeptieren kann, die nicht mit diesem verknüpft ist, **`false`** andernfalls.

## <a name="unlink_source"></a><a name="unlink_source"></a>unlink_source

Entfernt beim Überschreiben in einer abgeleiteten Klasse die Verknüpfung eines angegebenen Quell Blocks mit diesem `ITarget` Block.

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parameter

*_PSource*<br/>
Der `ISource` Block, von dem die Verknüpfung mit diesem Block aufgehoben wird `ITarget` .

### <a name="remarks"></a>Bemerkungen

Diese Funktion sollte nicht direkt auf einem-Block aufgerufen werden `ITarget` . Blöcke sollten mithilfe der- `unlink_target` Methode oder der- `unlink_targets` Methode für-Blöcke getrennt werden `ISource` , die die- `unlink_source` Methode für das entsprechende Ziel aufrufen.

## <a name="unlink_sources"></a><a name="unlink_sources"></a>unlink_sources

Hebt beim Überschreiben in einer abgeleiteten Klasse die Verknüpfung aller Quell Blöcke mit diesem `ITarget` Block auf.

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[ISource-Klasse](isource-class.md)
