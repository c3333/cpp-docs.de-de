---
title: Benachrichtigungen von einem RichEdit-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: 206fc02088f6531338bf2aa4cf272a1da096bae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622226"
---
# <a name="notifications-from-a-rich-edit-control"></a>Benachrichtigungen von einem RichEdit-Steuerelement

Benachrichtigungs Meldungen melden Ereignisse, die ein Rich Edit-Steuerelement ([CRichEditCtrl](reference/cricheditctrl-class.md)) betreffen. Sie können vom übergeordneten Fenster oder mithilfe der Nachrichten Reflektion durch das Rich Edit-Steuerelement selbst verarbeitet werden. Rich Edit-Steuerelemente unterstützen alle Benachrichtigungs Meldungen, die mit Bearbeitungs Steuerelementen verwendet werden, sowie mehrere zusätzliche. Sie können bestimmen, welche Benachrichtigungs Meldungen von einem Rich-Edit-Steuerelement durch Festlegen der "Ereignis Maske" gesendet werden.

Um die Ereignis Maske für ein Rich-Edit-Steuerelement festzulegen, verwenden Sie die Member-Funktion [SetEventMask](reference/cricheditctrl-class.md#seteventmask) . Sie können die aktuelle Ereignis Maske für ein Rich Edit-Steuerelement mithilfe der [GetEventMask](reference/cricheditctrl-class.md#geteventmask) -Member-Funktion abrufen.

In den folgenden Abschnitten werden einige spezifische Benachrichtigungen und ihre Verwendungsmöglichkeiten aufgelistet:

- Wenn EN_MSGFILTER die EN_MSGFILTER Benachrichtigung verarbeitet, kann eine Klasse, entweder das Rich Edit-Steuerelement oder das übergeordnete Fenster, alle Tastatur-und Maus Eingaben für das Steuerelement filtern. Der Handler kann die Verarbeitung der Tastatur-oder Maus Meldung verhindern oder die Meldung ändern, indem er die angegebene [msgfilter](/windows/win32/api/richedit/ns-richedit-msgfilter) -Struktur ändert.

- EN_PROTECTED die EN_PROTECTED Benachrichtigungs Meldung behandeln, um zu ermitteln, wann der Benutzer versucht, geschützten Text zu ändern. Um einen Textbereich als geschützt zu markieren, können Sie den Effekt geschützter Zeichen festlegen. Weitere Informationen finden Sie unter [Zeichen Formatierung in Rich Edit](character-formatting-in-rich-edit-controls.md)-Steuerelementen.

- EN_DROPFILES Sie den Benutzer zum Ablegen von Dateien in einem Rich-Edit-Steuerelement aktivieren können, indem Sie die EN_DROPFILES Benachrichtigungs Meldung verarbeiten. Die angegebene [endropfiles](/windows/win32/api/richedit/ns-richedit-endropfiles) -Struktur enthält Informationen zu den Dateien, die gelöscht werden.

- EN_SELCHANGE eine Anwendung erkennen kann, wenn sich die aktuelle Auswahl ändert, indem die EN_SELCHANGE Benachrichtigungs Meldung verarbeitet wird. Die Benachrichtigungs Meldung gibt eine [selChange](/windows/win32/api/richedit/ns-richedit-selchange) -Struktur an, die Informationen über die neue Auswahl enthält.

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](using-cricheditctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
