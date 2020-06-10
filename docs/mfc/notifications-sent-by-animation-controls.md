---
title: Von Animationssteuerelementen gesendete Benachrichtigungen
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: e9e5b94736de44d5cfeef81f5b78a759df3b8aa0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619907"
---
# <a name="notifications-sent-by-animation-controls"></a>Von Animationssteuerelementen gesendete Benachrichtigungen

Ein Animations Steuerelement ([CAnimateCtrl](reference/canimatectrl-class.md)) sendet zwei verschiedene Typen von Benachrichtigungs Meldungen. Die Benachrichtigungen werden in Form von [WM_COMMAND](/windows/win32/menurc/wm-command) -Nachrichten gesendet.

Die [ACN_START](/windows/win32/Controls/acn-start) Meldung wird gesendet, wenn das Animations Steuerelement mit der Wiedergabe eines Clips begonnen hat. Die [ACN_STOP](/windows/win32/Controls/acn-stop) Meldung wird gesendet, wenn das Animations Steuerelement beendet wurde oder die Wiedergabe eines Clips beendet hat.

## <a name="see-also"></a>Siehe auch

[Verwenden von CAnimateCtrl](using-canimatectrl.md)<br/>
[Steuerelemente](controls-mfc.md)
