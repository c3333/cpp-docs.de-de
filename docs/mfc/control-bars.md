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
ms.openlocfilehash: a2d3683b744493bb5566456b9e1358c1ddc418d4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615974"
---
# <a name="control-bars"></a>Steuerleisten

"Steuerleiste" ist der allgemeine Name für Symbolleisten, Status leisten und Dialog leisten. MFC `CToolBar` -Klassen, `CStatusBar` ,, und werden `CDialogBar` `COleResizeBar` `CReBar` von der [CControlBar](reference/ccontrolbar-class.md)-Klasse abgeleitet, die ihre gemeinsame Funktionalität implementiert.

Steuer leisten sind Fenster, in denen Zeilen von Steuerelementen angezeigt werden, mit denen Benutzeroptionen auswählen, Befehle ausführen oder Programminformationen abrufen können. Zu den Steuer leisten Typen zählen Symbolleisten, Dialog leisten und Status leisten.

- Symbolleisten in der Klasse [CToolBar](reference/ctoolbar-class.md)

- Status leisten in der Klasse [CStatusBar](reference/cstatusbar-class.md)

- Dialog leisten in der Klasse [CDialogBar](reference/cdialogbar-class.md)

- Rebars, in Klassen- [krebar](reference/crebar-class.md)

> [!IMPORTANT]
> Ab MFC-Version 4,0 werden Symbolleisten, Status leisten und Quick Infos mithilfe der in *Comctl32. dll* implementierten Systemfunktionalität implementiert, anstelle der vorherigen für MFC spezifischen Implementierung. In MFC, Version 6,0, `CReBar` wurde hinzugefügt, das auch die Comctl32. dll-Funktionalität umschließt.

Es folgen kurze Einführungen in die Steuer leisten Typen. Weitere Informationen finden Sie unter den folgenden Links.

## <a name="control-bars"></a>Steuerleisten

Steuer leisten verbessern die Benutzerfreundlichkeit eines Programms erheblich, indem schnelle, einstufige Befehls Aktionen bereitgestellt werden. Die-Klasse `CControlBar` stellt die allgemeine Funktionalität aller Symbolleisten, Status leisten und Dialog leisten bereit. `CControlBar`stellt die Funktionalität zum Positionieren der Steuerleiste in ihrem übergeordneten Rahmen Fenster bereit. Da es sich bei einer Steuerleiste normalerweise um ein untergeordnetes Fenster eines übergeordneten Rahmen Fensters handelt, handelt es sich um ein "gleich geordnetes Element" für die Client Ansicht oder den MDI-Client des Rahmen Fensters. Ein Steuer leisten Objekt verwendet Informationen über das Client Rechteck des übergeordneten Fensters, um sich selbst zu positionieren. Anschließend wird das verbleibende Client Fenster Rechteck des übergeordneten Elements geändert, sodass die Client Ansicht oder das MDI-Client Fenster den Rest des Client Fensters ausfüllt.

> [!NOTE]
> Wenn eine Schaltfläche auf der Steuerleiste keinen **Befehl** oder **UPDATE_COMMAND_UI** Handler enthält, wird die Schaltfläche automatisch deaktiviert.

## <a name="toolbars"></a>Symbolleisten

Eine Symbolleiste ist eine Steuerleiste, auf der eine Zeile mit Bitmapschaltflächen angezeigt wird, die Befehle ausführen. Das Drücken einer Symbolleisten-Schaltfläche entspricht der Auswahl eines Menü Elements. Er ruft denselben Handler auf, der einem Menü Element zugeordnet ist, wenn dieses Menü Element dieselbe ID wie die Symbolleisten-Schaltfläche aufweist. Die Schaltflächen können so konfiguriert werden, dass Sie als Pushbuttons, Options Felder oder Kontrollkästchen angezeigt werden und sich Verhalten. Eine Symbolleiste wird normalerweise am oberen Rand eines Rahmen Fensters ausgerichtet, aber eine MFC-Symbolleiste kann an einer beliebigen Seite des übergeordneten Fensters oder in einem eigenen Mini Rahmen Fenster "andocken". Eine Symbolleiste kann auch "float" sein, und Sie können ihre Größe ändern und mit der Maus ziehen. Eine Symbolleiste kann auch Quick Infos anzeigen, während der Benutzer die Maus über die Schaltflächen der Symbolleiste bewegt. Eine QuickInfo ist ein kleines Popup Fenster, in dem der Zweck der Schaltfläche kurz beschrieben wird.

> [!NOTE]
> Ab MFC-Version 4,0 verwendet Class [CToolBar](reference/ctoolbar-class.md) das allgemeine Windows-Symbolleisten-Steuerelement. Ein `CToolBar` enthält ein [CToolBarCtrl](reference/ctoolbarctrl-class.md). Ältere Symbolleisten werden jedoch weiterhin unterstützt. Weitere Informationen finden Sie im Artikel [Symbolleisten](mfc-toolbar-implementation.md).

## <a name="status-bars"></a>Statusleisten

Eine Statusleiste ist eine Steuerleiste, die Textausgabe Bereiche oder "Indikatoren" enthält. Die Ausgabe Bereiche werden normalerweise als Nachrichtenzeilen und als Status Indikatoren verwendet. Zu den Nachrichtenzeilen Beispielen zählen die Befehlszeilen Hilfe-Nachrichtenzeilen, in denen der ausgewählte Menü-oder Symbolleisten Befehl im linken Bereich der Standardstatus Leiste, die vom MFC-Anwendungs-Assistenten erstellt wurde, kurz erläutert werden. Beispiele für die Status Anzeige sind Scrollsperre, num-Sperre und andere Schlüssel. Status leisten werden normalerweise am unteren Rand eines Rahmen Fensters ausgerichtet. Weitere Informationen finden Sie Unterklasse [CStatusBar](reference/cstatusbar-class.md) und Klasse [CStatusBarCtrl](reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Dialogleisten

Eine Dialog Leiste ist eine Steuerleiste, die auf einer Dialogfeld Vorlagen-Ressource basiert und über die Funktionalität eines nicht modaldialog Felds verfügt. Dialog leisten können Windows-, benutzerdefinierte oder ActiveX-Steuerelemente enthalten. Wie in einem Dialogfeld kann der Benutzer zwischen den Steuerelementen eine Registerkarte auswählen. Dialog leisten können an der oberen, unteren, linken oder rechten Seite eines Rahmen Fensters ausgerichtet werden und können auch in einem eigenen Rahmen Fenster angezeigt werden. Weitere Informationen finden Sie unter Class [CDialogBar](reference/cdialogbar-class.md).

## <a name="rebars"></a>Releisten

Eine Grund [Leiste](using-crebarctrl.md) ist eine Steuerleiste, die Andock-, Layout-, Zustands-und Persistenzinformationen für Grund leisten-Steuerelemente bereitstellt. Ein Grund leisten-Objekt kann eine Vielzahl von untergeordneten Fenstern enthalten, normalerweise andere Steuerelemente, einschließlich Bearbeitungs Feldern, Symbolleisten und Listenfelder. Ein Grund leisten-Objekt kann seine untergeordneten Fenster über einer angegebenen Bitmap anzeigen. Die Größe kann automatisch oder manuell geändert werden, indem Sie auf die Zieh Punkt Leiste klicken oder Sie ziehen. Siehe Klassen- [krebar](reference/crebar-class.md).

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)
