---
title: Verarbeiten von Benachrichtigungsmeldungen in erweiterten Kombinationsfeld-Steuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 58a7c5ec36807489d24014055c39775b4552be03
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620983"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Verarbeiten von Benachrichtigungsmeldungen in erweiterten Kombinationsfeld-Steuerelementen

Wenn Benutzer mit dem erweiterten Kombinationsfeld interagieren, sendet das Steuerelement (`CComboBoxEx`) Benachrichtigungen an sein übergeordnetes Fenster, normalerweise ein Ansichts- oder Dialogfeldobjekt. Behandeln Sie diese Nachrichten, wenn Sie darauf reagieren möchten. Wenn der Benutzer z. B. die Dropdownliste aktiviert oder in das Editierfeld des Steuerelements klickt, wird die Benachrichtigung CBEN_BEGINEDIT gesendet.

Verwenden Sie den [Klassen-Assistenten](reference/mfc-class-wizard.md) , um der übergeordneten Klasse Benachrichtigungs Handler für die Nachrichten hinzuzufügen, die Sie implementieren möchten.

In der folgenden Liste sind die verschiedenen Benachrichtigungen beschrieben, die vom erweiterten Kombinationsfeld-Steuerelement gesendet werden.

- CBEN_BEGINEDIT Wird gesendet, wenn der Benutzer die Dropdownliste aktiviert oder in das Editierfeld des Steuerelements klickt.

- CBEN_DELETEITEM Wird gesendet, wenn ein Element gelöscht wurde.

- CBEN_DRAGBEGIN Wird gesendet, wenn der Benutzer beginnt, das Bild des angezeigten Elements auf den Editierteil des Steuerelements zu ziehen.

- CBEN_ENDEDIT Wird gesendet, wenn der Benutzer einen Vorgang im Editierfeld abgeschlossen oder ein Element in der Dropdownliste des Steuerelements ausgewählt hat.

- CBEN_GETDISPINFO Wird gesendet, um Anzeigeinformationen zu einem Rückrufelement abzurufen.

- CBEN_INSERTITEM Wird gesendet, wenn ein neues Element in das Steuerelement eingefügt wurde.

## <a name="see-also"></a>Siehe auch

[Verwenden von CComboBoxEx](using-ccomboboxex.md)<br/>
[Steuerelemente](controls-mfc.md)
