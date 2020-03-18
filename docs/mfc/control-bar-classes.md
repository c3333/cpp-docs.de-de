---
title: Klassen für Steuerleisten
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: a050c5d2f7396324c2c380a03fc28e01ab992208
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440961"
---
# <a name="control-bar-classes"></a>Klassen für Steuerleisten

Steuer leisten werden an ein Rahmen Fenster angefügt. Sie enthalten Schaltflächen, Status Bereiche oder eine Dialogfeld Vorlage. Freie, Gleit Komma Steuer leisten, auch als Tool Paletten bezeichnet, werden implementiert, indem Sie an ein [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) -Objekt angefügt werden.

## <a name="framework-control-bars"></a>Frameworksteuerleisten

Diese Steuer leisten sind ein wesentlicher Bestandteil des MFC-Frameworks. Sie sind einfacher zu verwenden und leistungsfähiger als die Windows-Steuer leisten, da Sie in das Framework integriert sind. Die meisten MFC-Anwendungen verwenden diese Steuer leisten anstelle der Windows-Steuerleiste.

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
Die Basisklasse für MFC-Steuer leisten, die in diesem Abschnitt aufgeführt sind. Eine Steuerleiste ist ein Fenster, das am Rand eines Rahmen Fensters ausgerichtet ist. Die Steuerleiste enthält entweder `HWND`-basierte untergeordnete Steuerelemente oder Steuerelemente, die nicht auf einem `HWND`basieren, z. b. Symbolleisten Schaltflächen

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Eine Steuerleiste, die auf einer Dialogfeld Vorlage basiert.

[CReBar](../mfc/reference/crebar-class.md)<br/>
Unterstützt eine Symbolleiste, die zusätzliche untergeordnete Fenster in Form von Steuerelementen enthalten kann.

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
Symbolleisten-Steuerelemente, die Bitmap-Befehls Schaltflächen enthalten, die nicht auf einem `HWND`basieren Die meisten MFC-Anwendungen verwenden diese Klasse anstelle `CToolBarCtrl`.

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
Die Basisklasse für StatusBar-Steuerelement Fenster. Die meisten MFC-Anwendungen verwenden diese Klasse anstelle `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Windows-Steuer leisten

Diese Steuer leisten sind schmale Wrapper für die entsprechenden Windows-Steuerelemente. Da Sie nicht in das Framework integriert sind, sind Sie schwieriger zu verwenden als die zuvor aufgelisteten Steuer leisten. Die meisten MFC-Anwendungen verwenden die zuvor aufgelisteten Steuer leisten.

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implementiert das interne Steuerelement des `CRebar` Objekts.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Ein horizontales Fenster, das normalerweise in Bereiche unterteilt ist, in denen eine Anwendung Statusinformationen anzeigen kann.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Stellt die Funktionalität des allgemeinen Windows-Symbolleisten-Steuerelements bereit.

## <a name="related-classes"></a>Verwandte Klassen

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Ein kleines Popup Fenster, das eine einzelne Textzeile anzeigt, die den Zweck eines Tools in einer Anwendung beschreibt.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Behandelt persistente Speicherung von Andock Zustandsdaten für Steuer leisten.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
