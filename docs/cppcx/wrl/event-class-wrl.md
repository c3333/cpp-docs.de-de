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
ms.openlocfilehash: 85b4c2d1f1a27e90a65e47aa749e079f4aa08739
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371519"
---
# <a name="event-class-wrl"></a>Ereignisklasse (WRL)

Stellt ein Ereignis dar.

## <a name="syntax"></a>Syntax

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                   | BESCHREIBUNG
---------------------- | ------------------------------------------------
[Veranstaltung::Event](#event) | Initialisiert eine neue Instanz der Klasse `Event`.

### <a name="public-operators"></a>Öffentliche Operatoren

Name                                 | BESCHREIBUNG
------------------------------------ | ------------------------------------------------------------------------
[Ereignis::operator=](#operator-assign) | Weist der `Event` aktuellen `Event` Instanz den angegebenen Verweis zu.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`HandleT`

`Event`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="eventevent"></a><a name="event"></a>Veranstaltung::Event

Initialisiert eine neue Instanz der Klasse `Event`.

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Handle für ein Ereignis. Standardmäßig wird *h* in `nullptr`initialisiert.

## <a name="eventoperator"></a><a name="operator-assign"></a>Ereignis::operator=

Weist der `Event` aktuellen `Event` Instanz den angegebenen Verweis zu.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Ein rvalue-Verweis `Event` auf eine Instanz.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `Event` die aktuelle Instanz.
