---
title: Ereignisklasse (WRL)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: 27a90bb801d1b6869b2391227464bb215dd42538
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220482"
---
# <a name="event-class-wrl"></a>Ereignisklasse (WRL)

Stellt ein Ereignis dar.

## <a name="syntax"></a>Syntax

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

name                   | BESCHREIBUNG
---------------------- | ------------------------------------------------
[Event:: Event](#event) | Initialisiert eine neue Instanz der `Event`-Klasse.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                 | BESCHREIBUNG
------------------------------------ | ------------------------------------------------------------------------
[Event:: Operator =](#operator-assign) | Weist der `Event` aktuellen Instanz den angegebenen Verweis zu `Event` .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HandleT`

`Event`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrapper

## <a name="eventevent"></a><a name="event"></a>Event:: Event

Initialisiert eine neue Instanz der `Event`-Klasse.

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parameter

*h*<br/>
Handle für ein Ereignis. Standardmäßig wird *h* mit initialisiert **`nullptr`** .

## <a name="eventoperator"></a><a name="operator-assign"></a>Event:: Operator =

Weist der `Event` aktuellen Instanz den angegebenen Verweis zu `Event` .

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parameter

*h*<br/>
Ein rvalue-Verweis auf eine- `Event` Instanz.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die aktuelle- `Event` Instanz.
