---
title: EventSource-Klasse
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: bb9151e55d133e3e5d8bf10baeb8448101ad6ce0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371543"
---
# <a name="eventsource-class"></a>EventSource-Klasse

Stellt ein nicht agiles Ereignis dar. `EventSource`-Memberfunktionen fügen Ereignishandler hinzu, entfernen sie und rufen sie auf. Verwenden Sie für agile Ereignisse [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Syntax

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parameter

*TDelegateInterface*<br/>
Die Schnittstelle zu einem Delegaten, der einen Ereignishandler darstellt.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

| Name                                     | BESCHREIBUNG                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource::EventSource](#eventsource) | Initialisiert eine neue Instanz der Klasse `EventSource`. |

### <a name="public-methods"></a>Öffentliche Methoden

| Name                                 | BESCHREIBUNG                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::Hinzufügen](#add)             | Fügt den Ereignishandler, der durch die angegebene Delegatschnittstelle `EventSource` dargestellt wird, an den Satz von Ereignishandlern für das aktuelle Objekt an.                     |
| [EventSource::GetSize](#getsize)     | Ruft die Anzahl der Ereignishandler ab, die dem aktuellen `EventSource` Objekt zugeordnet sind.                                                                         |
| [EventSource::InvokeAll](#invokeall) | Ruft jeden Ereignishandler auf, der dem aktuellen `EventSource` Objekt mit den angegebenen Argumenttypen und Argumenten zugeordnet ist.                                      |
| [EventSource::Entfernen](#remove)       | Löscht den Ereignishandler, der durch das angegebene Ereignisregistrierungstoken dargestellt wird, aus dem Satz von Ereignishandlern, die dem aktuellen `EventSource` Objekt zugeordnet sind. |

### <a name="protected-data-members"></a>Geschützte Datenmember

| Name                                                    | BESCHREIBUNG                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | Synchronisiert den Zugriff auf das [targets_-Array](#targets) beim Hinzufügen, Entfernen oder Aufrufen von Ereignishandlern.                          |
| [EventSource::targets_](#targets)                       | Ein Array von einem oder mehreren Ereignishandlern.                                                                                           |
| [EventSource::targetsPointerLock_](#targetspointerlock) | Synchronisiert den Zugriff auf interne Datenmember, auch wenn Ereignishandler für diese EventSource hinzugefügt, entfernt oder aufgerufen werden. |

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`EventSource`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** event.h

**Namespace:** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a>EventSource::Hinzufügen

Fügt den Ereignishandler, der durch die angegebene Delegatschnittstelle `EventSource` dargestellt wird, an den Satz von Ereignishandlern für das aktuelle Objekt an.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parameter

*delegateSchnittstelle*<br/>
Die Schnittstelle zu einem Delegatenobjekt, das einen Ereignishandler darstellt.

*Token*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Handle, der das Ereignis darstellt, behandelt. Verwenden Sie dieses Token als Parameter für die [Remove()-Methode,](#remove) um den Ereignishandler zu verwerfen.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a>EventSource::addRemoveLock_

Synchronisiert den Zugriff auf das [targets_-Array](#targets) beim Hinzufügen, Entfernen oder Aufrufen von Ereignishandlern.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a>EventSource::EventSource

Initialisiert eine neue Instanz der Klasse `EventSource`.

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a>EventSource::GetSize

Ruft die Anzahl der Ereignishandler ab, die dem aktuellen `EventSource` Objekt zugeordnet sind.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ereignishandler in [targets_](#targets).

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a>EventSource::InvokeAll

Ruft jeden Ereignishandler auf, der dem aktuellen `EventSource` Objekt mit den angegebenen Argumenttypen und Argumenten zugeordnet ist.

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>Parameter

*T0*<br/>
Der Typ des Arguments zeroth-Ereignishandler.

*T1*<br/>
Der Typ des ersten Ereignishandlerarguments.

*T2*<br/>
Der Typ des zweiten Ereignishandlerarguments.

*T3*<br/>
Der Typ des dritten Ereignishandlerarguments.

*T4*<br/>
Der Typ des vierten Ereignishandlerarguments.

*T5*<br/>
Der Typ des fünften Ereignishandlerarguments.

*T6*<br/>
Der Typ des sechsten Ereignishandlerarguments.

*T7*<br/>
Der Typ des siebten Ereignishandlerarguments.

*T8*<br/>
Der Typ des achten Ereignishandlerarguments.

*T9*<br/>
Der Typ des neunten Ereignishandlerarguments.

*arg0*<br/>
Das Argument des Zeroth-Ereignishandlers.

*arg1*<br/>
Das erste Ereignishandlerargument.

*arg2*<br/>
Das zweite Ereignishandlerargument.

*arg3*<br/>
Das dritte Ereignishandlerargument.

*arg4*<br/>
Das vierte Ereignishandlerargument.

*arg5*<br/>
Das fünfte Argument für den Ereignishandler.

*arg6*<br/>
Das sechste Argument für den Ereignishandler.

*arg7*<br/>
Das siebte Ereignishandlerargument.

*arg8*<br/>
Das achte Argument für den Ereignishandler.

*arg9*<br/>
Das neunte Ereignishandlerargument.

## <a name="eventsourceremove"></a><a name="remove"></a>EventSource::Entfernen

Löscht den Ereignishandler, der durch das angegebene Ereignisregistrierungstoken dargestellt wird, aus dem Satz von Ereignishandlern, die dem aktuellen `EventSource` Objekt zugeordnet sind.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parameter

*Token*<br/>
Ein Handle, das einen Ereignishandler darstellt. Dieses Token wurde zurückgegeben, als der Ereignishandler von der [Add()-Methode](#add) registriert wurde.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur `EventRegistrationToken` Struktur finden Sie im Thema **Windows::Foundation::EventRegistrationToken Structure** in der **Windows-Runtime-Referenzdokumentation.**

## <a name="eventsourcetargets_"></a><a name="targets"></a>EventSource::targets_

Ein Array von einem oder mehreren Ereignishandlern.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Bemerkungen

Wenn das Ereignis auftritt, `EventSource` das durch das aktuelle Objekt dargestellt wird, werden die Ereignishandler aufgerufen.

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a>EventSource::targetsPointerLock_

Synchronisiert den Zugriff auf interne Datenmember, `EventSource` auch wenn Ereignishandler dazu hinzugefügt, entfernt oder aufgerufen werden.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
