---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: 65a8ce08e4f8606f168b101aa4daba23ef541051
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168669"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`der Name der Funktion, die durch den zweiten Parameter des MESSAGE_HANDLER-Makros in der Meldungs Zuordnung identifiziert wird.

## <a name="syntax"></a>Syntax

```cpp
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parameter

*Umschlag*<br/>
Gibt die Meldung an.

*wParam*<br/>
Zusätzliche meldungsspezifische Informationen.

*lParam*<br/>
Zusätzliche meldungsspezifische Informationen.

*bHandled*<br/>
In der Meldungs Zuordnung wird *bbehandelte* auf `MessageHandler` true festgelegt, bevor aufgerufen wird. Wenn `MessageHandler` die Nachricht nicht vollständig verarbeitet, sollte *bbehandelte* auf false festgelegt werden, um anzugeben, dass die Nachricht weiterverarbeitet werden muss.

## <a name="return-value"></a>Rückgabewert

Das Ergebnis der Nachrichtenverarbeitung. 0, wenn erfolgreich.

## <a name="remarks"></a>Bemerkungen

Ein Beispiel für die Verwendung dieses Nachrichten Handlers in einer Meldungs Zuordnung finden Sie unter [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler).

## <a name="see-also"></a>Weitere Informationen:

[Implementieren eines Fensters](../atl/implementing-a-window.md)<br/>
[Meldungs Zuordnungen](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
