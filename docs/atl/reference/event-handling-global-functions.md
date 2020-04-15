---
title: Globale Funktionen für die Ereignisbehandlung
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: f2f8269dcf0f59a5d0794d3f16d4c4f85d8841ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330136"
---
# <a name="event-handling-global-functions"></a>Globale Funktionen für die Ereignisbehandlung

Diese Funktion stellt einen Ereignishandler bereit.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführte Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Wartet, bis ein Objekt signalisiert wird, und sendet bei Bedarf Fensternachrichten.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop

Wartet auf die Signalisierung des Objekts und leitet unterdessen Fenstermeldungen nach Bedarf weiter.

> [!IMPORTANT]
> Diese Funktion kann nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parameter

*hEvent*<br/>
[in] Das Handle des zu wartenden Objekts.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Objekt signalisiert wurde.

### <a name="remarks"></a>Bemerkungen

Dies ist nützlich, wenn Sie warten möchten, bis das Ereignis eines Objekts eintritt und darüber benachrichtigt werden, aber zulassen, dass Fensternachrichten während des Wartens gesendet werden.

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)
