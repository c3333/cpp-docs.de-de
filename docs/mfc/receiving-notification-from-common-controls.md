---
title: Empfangen von Benachrichtigungen von Standardsteuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- OnNotify method [MFC]
- common controls [MFC], notifications
- ON_NOTIFY macro [MFC]
- controls [MFC], notifications
- receiving notifications from common controls
- notifications [MFC], common controls
- Windows common controls [MFC], notifications
- WM_NOTIFY message
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
ms.openlocfilehash: 9205facb5ec4e2491308020d9667a27ab8deb96b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371781"
---
# <a name="receiving-notification-from-common-controls"></a>Empfangen von Benachrichtigungen von Standardsteuerelementen

Allgemeine Steuerelemente sind untergeordnete Fenster, die Benachrichtigungen an das übergeordnete Fenster senden, wenn Ereignisse, z. B. Eingaben des Benutzers, im Steuerelement auftreten.

Die Anwendung verwendet diese Benachrichtigungen, um zu bestimmen, welche Aktion der Benutzer ergreifen möchte. Die häufigsten Steuerelemente senden Benachrichtigungen als WM_NOTIFY Nachrichten. Windows-Steuerelemente senden die meisten Benachrichtigungen als WM_COMMAND Nachrichten. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) ist der Handler für die WM_NOTIFY Nachricht. Wie `CWnd::OnCommand`bei sendet `OnNotify` die Implementierung von `OnCmdMsg` Dispatchs die Benachrichtigung zur Behandlung in Nachrichtenzuordnungen. Der Nachrichtenzuordnungseintrag für die Behandlung von Benachrichtigungen ist ON_NOTIFY. Weitere Informationen finden Sie unter [Technische Anmerkung 61: ON_NOTIFY und WM_NOTIFY Nachrichten](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Alternativ kann eine abgeleitete Klasse ihre eigenen Benachrichtigungen mithilfe von "Nachrichtenreflektion" verarbeiten. Weitere Informationen finden Sie unter [Technical Note 62: Message Reflection for Windows Controls](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Abrufen der Cursorposition in einer Benachrichtigungsnachricht

Gelegentlich ist es nützlich, die aktuelle Position des Cursors zu bestimmen, wenn bestimmte Benachrichtigungen von einem gemeinsamen Steuerelement empfangen werden. Beispielsweise wäre es hilfreich, die aktuelle Cursorposition zu bestimmen, wenn ein allgemeines Steuerelement eine NM_RCLICK Benachrichtigung empfängt.

Es gibt eine einfache Möglichkeit, `CWnd::GetCurrentMessage`dies durch Aufrufen von zu erreichen. Diese Methode ruft jedoch nur die Cursorposition zum Zeitpunkt des Sendens der Nachricht ab. Da der Cursor möglicherweise seit dem Senden der `CWnd::GetCursorPos` Nachricht verschoben wurde, müssen Sie aufrufen, um die aktuelle Cursorposition abzurufen.

> [!NOTE]
> `CWnd::GetCurrentMessage`sollte nur innerhalb eines Nachrichtenhandlers aufgerufen werden.

Fügen Sie dem Hauptteil des Benachrichtigungsnachrichtenhandlers den folgenden Code hinzu (in diesem Beispiel NM_RCLICK):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

An diesem Punkt wird die Position `cursorPos` des Mauszeigers im Objekt gespeichert.

## <a name="see-also"></a>Siehe auch

[Erstellen und Verwenden von Steuerelementen](../mfc/making-and-using-controls.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
