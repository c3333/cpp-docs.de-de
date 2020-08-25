---
title: Globale Funktionen zur Ereignis Behandlung
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: fde93415640ef7fa460bb363af4c3cb14b356061
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833451"
---
# <a name="event-handling-global-functions"></a>Globale Funktionen zur Ereignis Behandlung

Diese Funktion stellt einen Ereignishandler bereit.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführte Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|Name|Beschreibung|
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Wartet darauf, dass ein Objekt signalisiert wird, während gleichzeitig Fenster Meldungen nach Bedarf verteilt werden.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a> Atlwaitwithmessageloop

Wartet auf die Signalisierung des Objekts und leitet unterdessen Fenstermeldungen nach Bedarf weiter.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parameter

*hevent*<br/>
in Das Handle des Objekts, auf das gewartet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt "true" zurück, wenn das Objekt signalisiert wurde.

### <a name="remarks"></a>Bemerkungen

Dies ist hilfreich, wenn Sie warten möchten, bis das Ereignis eines Objekts auftritt und benachrichtigt wird, während Sie darauf warten, dass Fenster Meldungen gesendet werden.

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)
