---
title: Meldungskategorien
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: 686d5eef4aaa67785aa56133d820b637fbf4bb86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364754"
---
# <a name="message-categories"></a>Meldungskategorien

Welche Arten von Nachrichten schreiben Sie Handler für Es gibt drei Hauptkategorien:

1. Windows-Meldungen

   Dies schließt in erster Linie die Nachrichten ein, die mit dem **Präfix WM_** beginnen, mit Ausnahme WM_COMMAND. Windows-Nachrichten werden von Fenstern und Ansichten verarbeitet. Diese Meldungen verfügen häufig über Parameter, die zum Bestimmen der Verarbeitung der Nachricht verwendet werden.

1. Steuerelementbenachrichtigungen

   Dazu gehören WM_COMMAND Benachrichtigungen von Steuerelementen und anderen untergeordneten Fenstern an die übergeordneten Fenster. Beispielsweise sendet ein Bearbeitungssteuerelement seinem übergeordneten Element eine WM_COMMAND Nachricht, die den EN_CHANGE-Kontrollbenachrichtigungscode enthält, wenn der Benutzer eine Aktion ausgeführt hat, die möglicherweise Text im Bearbeitungssteuerelement geändert hat. Der Handler des Fensters für die Nachricht reagiert auf die Benachrichtigung auf eine angemessene Weise, z. B. das Abrufen des Texts im Steuerelement.

   Das Framework leitet Steuerbenachrichtigungen wie andere **WM_** Nachrichten. Eine Ausnahme bildet jedoch die BN_CLICKED-Steuerbenachrichtigung, die von Schaltflächen gesendet wird, wenn der Benutzer darauf klickt. Diese Meldung wird speziell als Befehlsnachricht behandelt und wie andere Befehle weitergeleitet.

1. Befehlsmeldungen

   Dazu gehören WM_COMMAND Benachrichtigungen von Benutzeroberflächenobjekten: Menüs, Symbolleistenschaltflächen und Beschleunigertasten. Das Framework verarbeitet Befehle anders als andere Nachrichten und kann von mehr Arten von Objekten verarbeitet werden, wie unter [Befehlsziele](../mfc/command-targets.md)erläutert.

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Windows-Nachrichten und Control-Notification-Nachrichten

Nachrichten in den Kategorien 1 und 2 – Windows-Meldungen und Steuerbenachrichtigungen `CWnd`– werden von Windows verarbeitet: Objekte von Klassen, die von der Klasse abgeleitet sind. Dazu `CFrameWnd`gehören `CMDIFrameWnd` `CMDIChildWnd`, `CView` `CDialog`, , , und Ihre eigenen Klassen, die von diesen Basisklassen abgeleitet sind. Solche Objekte kapseln `HWND`ein , ein Handle in einem Windows-Fenster.

## <a name="command-messages"></a><a name="_core_command_messages"></a>Befehlsmeldungen

Nachrichten in Kategorie 3 – Befehle – können von einer größeren Vielfalt von Objekten verarbeitet werden: Dokumente, Dokumentvorlagen und das Anwendungsobjekt selbst zusätzlich zu Fenstern und Ansichten. Wenn ein Befehl direkt auf ein bestimmtes Objekt wirkt, ist es sinnvoll, dass dieses Objekt den Befehl behandelt. Beispielsweise ist der Befehl Öffnen im Menü Datei logisch mit der Anwendung verknüpft: Die Anwendung öffnet ein angegebenes Dokument, wenn sie den Befehl empfängt. Der Handler für den Befehl Open ist also eine Memberfunktion der Anwendungsklasse. Weitere Informationen zu Befehlen und deren Weiterleitung an Objekte finden Sie unter [Wie das Framework einen Handler aufruft.](../mfc/how-the-framework-calls-a-handler.md)

## <a name="see-also"></a>Siehe auch

[Meldungen und Befehle im Framework](../mfc/messages-and-commands-in-the-framework.md)
