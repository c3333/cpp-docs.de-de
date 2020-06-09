---
title: Verarbeiten von Benachrichtigungsmeldungen in einem Grundleisten-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: e1e1aaa5056b43f0dd23976fead94bc800163613
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625188"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Verarbeiten von Benachrichtigungsmeldungen in einem Grundleisten-Steuerelement

Erstellen Sie in der übergeordneten Klasse des Grund leisten-Steuer Elements eine `OnChildNotify` Handlerfunktion mit einer Switch-Anweisung für alle Benachrichtigungs Meldungen von Grund leisten-Control ( `CReBarCtrl` ), die Sie behandeln möchten. Benachrichtigungen werden an das übergeordnete Fenster gesendet, wenn der Benutzer Objekte über das Grund leisten-Steuerelement zieht, das Layout der Grund leisten Bänder ändert, Bänder aus dem Grund leisten-Steuerelement löscht usw.

Die folgenden Benachrichtigungs Meldungen können vom Info leisten-Steuerelement Objekt gesendet werden:

- RBN_AUTOSIZE von einem Grund leisten-Steuerelement gesendet (erstellt mit dem RBS_AUTOSIZE Format), wenn sich die Größe der Grund Leiste automatisch ändert.

- RBN_BEGINDRAG von einem Grund leisten-Steuerelement gesendet, wenn der Benutzer mit dem Ziehen eines Bands beginnt.

- RBN_CHILDSIZE von einem Grund leisten-Steuerelement gesendet, wenn die Größe des untergeordneten Fensters eines Bands geändert wird.

- RBN_DELETEDBAND, die von einem Grund leisten-Steuerelement gesendet werden, nachdem ein Band gelöscht wurde.

- RBN_DELETINGBAND von einem Grund leisten-Steuerelement gesendet, wenn ein Band im Begriff ist, gelöscht zu werden.

- RBN_ENDDRAG von einem Grund leisten-Steuerelement gesendet, wenn der Benutzer das Ziehen eines Bands beendet.

- RBN_GETOBJECT von einem Grund leisten-Steuerelement gesendet (erstellt mit dem RBS_REGISTERDROP Format), wenn ein Objekt über ein Band im-Steuerelement gezogen wird.

- RBN_HEIGHTCHANGE von einem Grund leisten-Steuerelement gesendet, wenn sich die Höhe geändert hat.

- RBN_LAYOUTCHANGED von einem Grund leisten-Steuerelement gesendet, wenn der Benutzer das Layout der Bänder eines Steuer Elements ändert.

Weitere Informationen zu diesen Benachrichtigungen finden Sie Untergrund leisten- [Steuerelement Verweis](/windows/win32/controls/rebar-control-reference) in der Windows SDK.

## <a name="see-also"></a>Siehe auch

[Verwenden von CReBarCtrl](using-crebarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
