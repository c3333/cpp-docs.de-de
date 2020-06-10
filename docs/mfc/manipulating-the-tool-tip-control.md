---
title: Bearbeiten des QuickInfo-Steuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: 61bc35e8b19ba7645736b939acac6cdaa6cb7316
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622422"
---
# <a name="manipulating-the-tool-tip-control"></a>Bearbeiten des QuickInfo-Steuerelements

Die `CToolTipCtrl` -Klasse stellt eine Gruppe von Element Funktionen bereit, mit denen die verschiedenen Attribute des `CToolTipCtrl` -Objekts und des QuickInfo-Fensters gesteuert werden.

Die Anfangs-, Popup-und neueinblenden Dauer für die QuickInfo-Fenster können mit Aufrufen von [getdelta aytime](reference/ctooltipctrl-class.md#getdelaytime) und [setdelta Time](reference/ctooltipctrl-class.md#setdelaytime)festgelegt und abgerufen werden.

Ändern Sie die Darstellung der QuickInfo-Fenster mit den folgenden Funktionen:

- [GetMargin](reference/ctooltipctrl-class.md#getmargin) und [setMargin](reference/ctooltipctrl-class.md#setmargin) rufen die Breite zwischen dem QuickInfo-Rahmen und dem QuickInfo-Text ab und legt diese fest.

- [GetMaxTipWidth](reference/ctooltipctrl-class.md#getmaxtipwidth) und [SetMaxTipWidth](reference/ctooltipctrl-class.md#setmaxtipwidth) Ruft die maximale Breite des QuickInfo-Fensters ab und legt diese fest.

- [Gettipbkcolor](reference/ctooltipctrl-class.md#gettipbkcolor) und [settipbkcolor](reference/ctooltipctrl-class.md#settipbkcolor) Ruft die Hintergrundfarbe des QuickInfo-Fensters ab und legt diese fest.

- [Gettiptextcolor](reference/ctooltipctrl-class.md#gettiptextcolor) und [SetTipTextColor](reference/ctooltipctrl-class.md#settiptextcolor) Ruft die Textfarbe des QuickInfo-Fensters ab und legt diese fest.

Damit das QuickInfo-Steuerelement über wichtige Meldungen, z. b. WM_LBUTTONXXX Meldungen, benachrichtigt werden kann, müssen Sie die Nachrichten an das QuickInfo-Steuerelement weiterleiten. Die beste Methode für dieses Relay besteht darin, einen [CToolTipCtrl:: relayevent](reference/ctooltipctrl-class.md#relayevent)-Befehl in der- `PreTranslateMessage` Funktion des Besitzer Fensters aufzurufen. Das folgende Beispiel veranschaulicht eine mögliche Methode (vorausgesetzt, das QuickInfo-Steuerelement wird aufgerufen `m_ToolTip` ):

[!code-cpp[NVC_MFCControlLadenDialog#41](codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

Zum sofortigen Entfernen eines QuickInfo-Fensters müssen Sie die [Pop](reference/ctooltipctrl-class.md#pop) -Member-Funktion aufzurufen.

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolTipCtrl](using-ctooltipctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
