---
title: Definieren eines Meldungshandlers für eine reflektierte Meldung
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: f7f90d3347ac61abcfcb48e77ef39aa2626ae5c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365860"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definieren eines Meldungshandlers für eine reflektierte Meldung

Nachdem Sie eine neue MFC-Steuerelementklasse erstellt haben, können Sie Nachrichtenhandler dafür definieren. Reflektierte Nachrichtenhandler ermöglichen es der Steuerelementklasse, eigene Nachrichten zu verarbeiten, bevor die Nachricht vom übergeordneten Nachrichten empfangen wird. Sie können die Funktion MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) verwenden, um Nachrichten von Ihrem Steuerelement an ein übergeordnetes Fenster zu senden.

Mit dieser Funktion können Sie z. B. ein Listenfeld erstellen, das sich neu zeichnet, anstatt sich dabei auf das übergeordnete Fenster zu verlassen (Besitzer gezeichnet). Weitere Informationen zu reflektierten Nachrichten finden Sie [unter Behandeln von reflektierten Nachrichten](../../mfc/handling-reflected-messages.md).

Um ein [ActiveX-Steuerelement](../../mfc/activex-controls-on-the-internet.md) mit derselben Funktionalität zu erstellen, müssen Sie ein Projekt für das ActiveX-Steuerelement erstellen.

> [!NOTE]
> Sie können keine reflektierte Nachricht (OCM_*Nachricht*) für ein ActiveX-Steuerelement mithilfe des Klassen-Assistenten hinzufügen, wie unten beschrieben. Sie müssen diese Meldungen manuell hinzufügen.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>So definieren Sie einen Nachrichtenhandler für eine reflektierte Nachricht aus dem Klassen-Assistenten

1. Fügen Sie Ihrem MFC-Projekt ein Steuerelement hinzu, z. B. eine Liste, ein Bewehrungssteuerelement, eine Symbolleiste oder ein Struktursteuerelement.

1. Klicken Sie in der Klassenansicht auf den Namen der Steuerelementklasse.

1. Im [Klassen-Assistenten](mfc-class-wizard.md)wird der Name der Steuerelementklassen in der Liste **Klassenname** angezeigt.

1. Klicken Sie auf die Registerkarte **Nachrichten,** um die Windows-Meldungen anzuzeigen, die dem Steuerelement hinzugefügt werden können.

1. Wählen Sie die reflektierte Nachricht aus, für die Sie einen Handler definieren möchten. Reflektierte Nachrichten werden mit einem Gleichheitszeichen (=) gekennzeichnet.

1. Klicken Sie auf die Zelle in der rechten Spalte im \<Klassen-Assistenten, um den vorgeschlagenen Namen des Handlers als hinzufügen>*HandlerName*anzuzeigen. (Der **Nachrichtenhandler =WM_CTLCOLOR** schlägt \<z. B. vor,>**CtlColor**hinzuzufügen.

1. Klicken Sie auf den vorgeschlagenen Namen, der akzeptiert werden soll. Der Handler wird dem Projekt hinzugefügt.

1. Wiederholen Sie die Schritte 4 bis 7, um einen Nachrichtenhandler zu bearbeiten oder zu löschen. Klicken Sie auf die Zelle mit dem Handlernamen, um sie zu bearbeiten oder zu löschen, und klicken Sie auf die entsprechende Aufgabe.

## <a name="see-also"></a>Siehe auch

[Zuordnen von Meldungen zu Funktionen](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class (Hinzufügen einer Klasse)](../../ide/adding-a-class-visual-cpp.md)<br/>
[Hinzufügen einer Memberfunktion](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable (Hinzufügen einer Membervariablen)](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function (Überschreiben einer virtuellen Funktion)](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler (MFC-Meldungshandler)](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigating the Class Structure (Navigieren in der Klassenstruktur)](../../ide/navigate-code-cpp.md)
