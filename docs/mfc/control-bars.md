---
title: Steuerleisten
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: ceae20c89d9a6d3f4393f838b3594938107785f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353570"
---
# <a name="control-bars"></a>Steuerleisten

"Steuerleiste" ist der allgemeine Name für Symbolleisten, Statusleisten und Dialogleisten. `CToolBar`MFC-Klassen `CStatusBar` `CDialogBar`, `COleResizeBar`, `CReBar` , und leiten von der Klasse [CControlBar](../mfc/reference/ccontrolbar-class.md)ab, die ihre gemeinsame Funktionalität implementiert.

Steuerleisten sind Fenster, in denen Zeilen mit Steuerelementen angezeigt werden, mit denen Benutzer Optionen auswählen, Befehle ausführen oder Programminformationen abrufen können. Zu den Typen von Steuerleisten gehören Symbolleisten, Dialogleisten und Statusleisten.

- Symbolleisten, Klasse [CToolBar](../mfc/reference/ctoolbar-class.md)

- Statusleisten in Klasse [CStatusBar](../mfc/reference/cstatusbar-class.md)

- Dialogleisten in Klasse [CDialogBar](../mfc/reference/cdialogbar-class.md)

- Bebars, Klasse [CReBar](../mfc/reference/crebar-class.md)

> [!IMPORTANT]
> Ab MFC Version 4.0 werden Symbolleisten, Statusleisten und Werkzeugtipps mithilfe der in *comctl32.dll* implementierten Systemfunktionalität anstelle der für MFC spezifischen Implementierung implementiert. In MFC Version 6.0, `CReBar`die auch comctl32.dll Funktionalität umschließt, wurde hinzugefügt.

Es folgen kurze Einführungen in die Steuerleistentypen. Weitere Informationen finden Sie unter den untenstehenden Links.

## <a name="control-bars"></a>Steuerleisten

Steuerleisten verbessern die Benutzerfreundlichkeit eines Programms erheblich, indem sie schnelle, einstufige Befehlsaktionen bereitstellen. Die `CControlBar` Klasse stellt die gemeinsame Funktionalität aller Symbolleisten, Statusleisten und Dialogleisten bereit. `CControlBar`bietet die Funktionalität zum Positionieren der Steuerleiste im übergeordneten Rahmenfenster. Da eine Steuerelementleiste in der Regel ein untergeordnetes Fenster eines übergeordneten Rahmenfensters ist, handelt es sich um ein "Geschwister" für die Clientansicht oder den MDI-Client des Rahmenfensters. Ein Steuerelementleistenobjekt verwendet Informationen über das Clientrechteck des übergeordneten Fensters, um sich selbst zu positionieren. Anschließend wird das verbleibende Clientfensterrechteck des übergeordneten Elements so geändert, dass die Clientansicht oder das MDI-Clientfenster den Rest des Clientfensters ausfüllt.

> [!NOTE]
> Wenn eine Schaltfläche auf der Steuerleiste keinen **COMMAND-** oder **UPDATE_COMMAND_UI-Handler** hat, deaktiviert das Framework die Schaltfläche automatisch.

## <a name="toolbars"></a>Symbolleisten

Eine Symbolleiste ist eine Steuerleiste, die eine Reihe von Bitmapping-Schaltflächen anzeigt, die Befehle ausführen. Das Drücken einer Symbolleistenschaltfläche entspricht der Auswahl eines Menüelements. Es ruft denselben Handler auf, der einem Menüelement zugeordnet ist, wenn dieses Menüelement dieselbe ID wie die Symbolleistenschaltfläche hat. Die Schaltflächen können so konfiguriert werden, dass sie als Drucktasten, Optionsfelder oder Kontrollkästchen angezeigt werden und sich verhalten. Eine Symbolleiste wird normalerweise am oberen Rand eines Rahmenfensters ausgerichtet, aber eine MFC-Symbolleiste kann an jede Seite des übergeordneten Fensters "docken" oder in einem eigenen Minirahmenfenster schweben. Eine Symbolleiste kann auch "schweben" und Sie können ihre Größe ändern und mit der Maus ziehen. Eine Symbolleiste kann auch Werkzeugspitzen anzeigen, wenn der Benutzer die Maus über die Schaltflächen der Symbolleiste bewegt. Ein QuickInfo ist ein kleines Popupfenster, das kurz den Zweck der Schaltfläche beschreibt.

> [!NOTE]
> Ab MFC Version 4.0 verwendet die Klasse [CToolBar](../mfc/reference/ctoolbar-class.md) die gemeinsame Windows-Symbolleiste. A `CToolBar` enthält eine [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Ältere Symbolleisten werden jedoch weiterhin unterstützt. Siehe den Artikel [ToolBars](../mfc/mfc-toolbar-implementation.md).

## <a name="status-bars"></a>Statusleisten

Eine Statusleiste ist eine Steuerleiste, die Textausgabebereiche oder "Indikatoren" enthält. Die Ausgabebereiche werden häufig als Nachrichtenlinien und als Statusindikatoren verwendet. Beispiele für Die Meldungszeilen umfassen die Befehlshilfe-Nachrichtenzeilen, die das ausgewählte Menü oder den Befehl der Symbolleiste im linken Bereich der vom MFC-Anwendungs-Assistenten erstellten Standardstatusleiste kurz erläutern. Statusindikatorbeispiele sind die SCROLL LOCK, NUM LOCK und andere Tasten. Statusleisten werden in der Regel am unteren Rand eines Rahmenfensters ausgerichtet. Siehe Klasse [CStatusBar](../mfc/reference/cstatusbar-class.md) und Klasse [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Dialogleisten

Eine Dialogleiste ist eine Steuerleiste, die auf einer Dialogvorlageressource basiert und die Funktionalität eines moduslosen Dialogfelds enthält. Dialogleisten können Windows-, benutzerdefinierte oder ActiveX-Steuerelemente enthalten. Wie in einem Dialogfeld kann der Benutzer unter den Steuerelementen ein Kreuzen. Dialogleisten können an der oberen, unteren, linken oder rechten Seite eines Rahmenfensters ausgerichtet und auch in ihrem eigenen Rahmenfenster schweben. Siehe Klasse [CDialogBar](../mfc/reference/cdialogbar-class.md).

## <a name="rebars"></a>Bewehrung

Eine [Bewehrung](../mfc/using-crebarctrl.md) ist eine Steuerleiste, die Docking-, Layout-, Status- und Persistenzinformationen für Bewehrungssteuerelemente bereitstellt. Ein Bewehrungsobjekt kann eine Vielzahl von untergeordneten Fenstern enthalten, in der Regel andere Steuerelemente, einschließlich Bearbeitungsfelder, Symbolleisten und Listenfelder. Ein Bewehrungsobjekt kann seine untergeordneten Fenster über einer angegebenen Bitmap anzeigen. Die Größe kann automatisch oder manuell geändert werden, indem Sie auf die Greiferleiste klicken oder ziehen. Siehe Klasse [CReBar](../mfc/reference/crebar-class.md).

## <a name="see-also"></a>Siehe auch

[Benutzeroberflächenelemente](../mfc/user-interface-elements-mfc.md)
