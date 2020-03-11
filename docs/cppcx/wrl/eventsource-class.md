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
ms.openlocfilehash: 1350e51ff609a888b6a8ad6841be6856b68c7994
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865729"
---
# <a name="eventsource-class"></a>EventSource-Klasse

Stellt ein nicht agiles Ereignis dar. `EventSource`-Memberfunktionen fügen Ereignishandler hinzu, entfernen sie und rufen sie auf. Verwenden Sie für Agile-Ereignisse [agileeventsource](agileeventsource-class.md).

## <a name="syntax"></a>Syntax

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parameter

*Tdelegateingeterface*<br/>
Die-Schnittstelle zu einem Delegaten, der einen Ereignishandler darstellt.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

| Name                                     | BESCHREIBUNG                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource:: eventSource](#eventsource) | Initialisiert eine neue Instanz der Klasse `EventSource`. |

### <a name="public-methods"></a>Öffentliche Methoden

| Name                                 | BESCHREIBUNG                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: Add](#add)             | Fügt den Ereignishandler, der durch die angegebene delegatschnittstelle dargestellt wird, an den Satz von Ereignis Handlern für das aktuelle `EventSource`-Objekt an.                     |
| [EventSource:: GetSize](#getsize)     | Ruft die Anzahl der Ereignishandler ab, die dem aktuellen `EventSource`-Objekt zugeordnet sind.                                                                         |
| [EventSource:: InvokeAll](#invokeall) | Ruft jeden Ereignishandler auf, der mit den angegebenen Argument Typen und Argumenten mit dem aktuellen `EventSource`-Objekt verknüpft ist.                                      |
| [EventSource:: Remove](#remove)       | Löscht den Ereignishandler, der durch das angegebene Ereignis Registrierungs Token dargestellt wird, aus dem Satz von Ereignis Handlern, die dem aktuellen `EventSource`-Objekt zugeordnet sind. |

### <a name="protected-data-members"></a>Geschützte Datenelemente

| Name                                                    | BESCHREIBUNG                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: addRemoveLock_](#addremovelock)           | Synchronisiert den Zugriff auf das [targets_](#targets) Array beim Hinzufügen, entfernen oder Aufrufen von Ereignis Handlern.                          |
| [EventSource:: targets_](#targets)                       | Ein Array von einem oder mehreren Ereignis Handlern.                                                                                           |
| [EventSource:: targetsPointerLock_](#targetspointerlock) | Synchronisiert den Zugriff auf interne Datenmember, auch wenn Ereignishandler für diese eventSource hinzugefügt, entfernt oder aufgerufen werden. |

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`EventSource`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Event. h

**Namespace:** Microsoft::WRL

## <a name="add"></a>EventSource:: Add

Fügt den Ereignishandler, der durch die angegebene delegatschnittstelle dargestellt wird, an den Satz von Ereignis Handlern für das aktuelle `EventSource`-Objekt an.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parameter

*delegateingangs Gesicht*<br/>
Die-Schnittstelle zu einem Delegatobjekt, das einen Ereignishandler darstellt.

*token*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Handle, das das Ereignis darstellt. Verwenden Sie dieses Token als Parameter für die [Remove ()](#remove) -Methode, um den Ereignishandler zu verwerfen.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="addremovelock"></a>EventSource:: addRemoveLock_

Synchronisiert den Zugriff auf das [targets_](#targets) Array beim Hinzufügen, entfernen oder Aufrufen von Ereignis Handlern.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource:: eventSource

Initialisiert eine neue Instanz der Klasse `EventSource`.

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource:: GetSize

Ruft die Anzahl der Ereignishandler ab, die dem aktuellen `EventSource`-Objekt zugeordnet sind.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Ereignis Handlern in [targets_](#targets).

## <a name="invokeall"></a>EventSource:: InvokeAll

Ruft jeden Ereignishandler auf, der mit den angegebenen Argument Typen und Argumenten mit dem aktuellen `EventSource`-Objekt verknüpft ist.

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
Der Typ des nullten ereignishandlerarguments.

*T1*<br/>
Der Typ des ersten ereignishandlerarguments.

*T2*<br/>
Der Typ des zweiten ereignishandlerarguments.

*Übte*<br/>
Der Typ des dritten ereignishandlerarguments.

*T4*<br/>
Der Typ des vierten ereignishandlerarguments.

*T5*<br/>
Der Typ des fünften ereignishandlerarguments.

*T6*<br/>
Der Typ des sechsten ereignishandlerarguments.

*T7*<br/>
Der Typ des siebten ereignishandlerarguments.

*T8*<br/>
Der Typ des achten ereignishandlerarguments.

*T9*<br/>
Der Typ des neunten ereignishandlerarguments.

*arg0*<br/>
Das Nuller-ereignishandlerargument.

*arg1*<br/>
Das erste ereignishandlerargument.

*arg2*<br/>
Das zweite ereignishandlerargument.

*arg3*<br/>
Das dritte ereignishandlerargument.

*arg4*<br/>
Das vierte ereignishandlerargument.

*arg5*<br/>
Das fünfte ereignishandlerargument.

*arg6*<br/>
Das sechste ereignishandlerargument.

*arg7*<br/>
Das siebte ereignishandlerargument.

*arg8*<br/>
Das achte ereignishandlerargument.

*arg9*<br/>
Das neunte ereignishandlerargument.

## <a name="remove"></a>EventSource:: Remove

Löscht den Ereignishandler, der durch das angegebene Ereignis Registrierungs Token dargestellt wird, aus dem Satz von Ereignis Handlern, die dem aktuellen `EventSource`-Objekt zugeordnet sind.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parameter

*token*<br/>
Ein Handle, das einen Ereignishandler darstellt. Dieses Token wurde zurückgegeben, als der Ereignishandler von der [Add ()](#add) -Methode registriert wurde.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur `EventRegistrationToken` Struktur finden Sie im Thema **Windows:: Foundation:: eventregistrationtoken-Struktur** in der **Windows-Runtime** Referenz Dokumentation.

## <a name="targets"></a>EventSource:: targets_

Ein Array von einem oder mehreren Ereignis Handlern.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Bemerkungen

Wenn das Ereignis, das durch das aktuelle `EventSource`-Objekt dargestellt wird, auftritt, werden die Ereignishandler aufgerufen.

## <a name="targetspointerlock"></a>EventSource:: targetsPointerLock_

Synchronisiert den Zugriff auf interne Datenmember, auch wenn Ereignishandler für diese `EventSource` hinzugefügt, entfernt oder aufgerufen werden.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
