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
ms.openlocfilehash: 3875a6931b4380f0531e4c1786de6dddfccb76ca
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625472"
---
# <a name="message-categories"></a>Meldungskategorien

Welche Arten von Nachrichten Sie für die Erstellung von Handlern verwenden, besteht aus drei Hauptkategorien:

1. Windows-Meldungen

   Dies schließt primär die Nachrichten ein, die mit dem Präfix **WM_** beginnen, mit Ausnahme von WM_COMMAND. Windows-Meldungen werden von Windows und Ansichten verarbeitet. Diese Nachrichten enthalten häufig Parameter, die verwendet werden, um zu bestimmen, wie die Nachricht behandelt werden soll.

1. Steuerelementbenachrichtigungen

   Dies umfasst WM_COMMAND Benachrichtigungs Meldungen von Steuerelementen und anderen untergeordneten Fenstern an die übergeordneten Fenster. Beispielsweise sendet ein Bearbeitungs Steuerelement eine WM_COMMAND Nachricht, die den EN_CHANGE Steuerelement-Benachrichtigungs Code enthält, wenn der Benutzer eine Aktion durchgeführt hat, die möglicherweise Text im Bearbeitungs Steuerelement geändert hat. Der Handler des Fensters für die Meldung antwortet auf eine angemessene Weise auf die Benachrichtigungs Meldung, wie z. b. das Abrufen des Texts im Steuerelement.

   Das Framework leitet Steuerelement Benachrichtigungs Meldungen wie andere **WM_** Nachrichten weiter. Eine Ausnahme ist jedoch die BN_CLICKED Steuerelement Benachrichtigungs Meldung, die von Schaltflächen gesendet wird, wenn der Benutzer darauf klickt. Diese Meldung wird vor allem als Befehls Meldung behandelt und wie andere Befehle weitergeleitet.

1. Befehls Meldungen

   Dies umfasst WM_COMMAND Benachrichtigungs Meldungen von Benutzeroberflächen Objekten: Menüs, Symbolleisten-Schaltflächen und Tastenkombinationen. Das Framework verarbeitet Befehle anders als andere Nachrichten, und Sie können von mehreren Arten von Objekten verarbeitet werden, wie in den [Befehls Zielen](command-targets.md)erläutert.

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Windows-Meldungen und Steuerelement Benachrichtigungs Meldungen

Nachrichten in den Kategorien 1 und 2 – Windows-Meldungen und Steuerelement Benachrichtigungen – werden von Windows behandelt: Objekte von Klassen, die von der-Klasse abgeleitet werden `CWnd` . Dies umfasst `CFrameWnd` , `CMDIFrameWnd` , `CMDIChildWnd` , `CView` , `CDialog` und ihre eigenen Klassen, die von diesen Basisklassen abgeleitet werden. Solche Objekte Kapseln eine `HWND` , ein Handle für ein Windows-Fenster.

## <a name="command-messages"></a><a name="_core_command_messages"></a>Befehls Meldungen

Nachrichten in den Befehlen der Kategorie 3 – – können von einer breiteren Vielzahl von Objekten behandelt werden: Dokumente, Dokumentvorlagen und das Anwendungs Objekt selbst zusätzlich zu Fenstern und Ansichten. Wenn ein Befehl direkt auf ein bestimmtes Objekt wirkt, ist es sinnvoll, dass dieses Objekt den Befehl verarbeitet. Beispielsweise ist der Befehl Öffnen im Menü Datei logisch mit der Anwendung verknüpft: die Anwendung öffnet beim Empfang des Befehls ein angegebenes Dokument. Daher ist der-Handler für den Open-Befehl eine Member-Funktion der-Anwendungsklasse. Weitere Informationen zu Befehlen und deren Weiterleitung an Objekte finden Sie unter [So ruft das Framework einen Handler](how-the-framework-calls-a-handler.md)auf.

## <a name="see-also"></a>Siehe auch

[Meldungen und Befehle im Framework](messages-and-commands-in-the-framework.md)
