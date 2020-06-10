---
title: Verarbeiten von Benachrichtigungen des Headersteuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: c313382b8be7538ba5bb465c6ba383955e414662
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619795"
---
# <a name="processing-header-control-notifications"></a>Verarbeiten von Benachrichtigungen des Headersteuerelements

Verwenden Sie in ihrer Ansicht oder Dialogfeld Klasse [den Klassen-Assistenten](reference/mfc-class-wizard.md) , um eine [OnChildNotify](reference/cwnd-class.md#onchildnotify) -Handlerfunktion mit einer Switch-Anweisung für alle Header Steuerelemente ([CHeaderCtrl](reference/cheaderctrl-class.md)) zu erstellen, die Sie behandeln möchten (Weitere Informationen finden Sie [unter Mapping messages to Functions](reference/mapping-messages-to-functions.md)). Benachrichtigungen werden an das übergeordnete Fenster gesendet, wenn der Benutzer auf ein Header Element klickt oder doppelklickt, einen unter Teiler zwischen Elementen zieht usw.

Die einem Header Steuerelement zugeordneten Benachrichtigungs Meldungen werden in der Windows SDK des [Header Steuer](/windows/win32/controls/header-control-reference) Elements aufgeführt.

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](using-cheaderctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
