---
title: Methoden zum Erstellen von QuickInfos
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 26f31705068df009e906d50451efa9ea6572d7e6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625456"
---
# <a name="methods-of-creating-tool-tips"></a>Methoden zum Erstellen von QuickInfos

MFC bietet drei Klassen zum Erstellen und Verwalten des QuickInfo-Steuer Elements: [CWnd](reference/cwnd-class.md), [CToolBarCtrl](reference/ctoolbarctrl-class.md), [CToolTipCtrl](reference/ctooltipctrl-class.md) und [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md). Die ToolTip-Member-Funktionen in diesen Klassen wrappen die Common Control API von Windows. Class `CToolBarCtrl` und Class `CToolTipCtrl` sind von der-Klasse abgeleitet `CWnd` .

`CWnd`bietet vier Member-Funktionen zum Erstellen und Verwalten von Quick Infos: [EnableToolTips](reference/cwnd-class.md#enabletooltips), [canceltooltips](reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](reference/cwnd-class.md#filtertooltipmessage)und [ontoolhittest](reference/cwnd-class.md#ontoolhittest). Weitere Informationen zur Implementierung von Quick Infos finden Sie in diesen einzelnen Element Funktionen.

Wenn Sie mithilfe von eine Symbolleiste erstellen `CToolBarCtrl` , können Sie Quick Infos für diese Symbolleiste direkt mithilfe der folgenden Member-Funktionen implementieren: [gettooltips](reference/ctoolbarctrl-class.md#gettooltips) und [SetToolTips](reference/ctoolbarctrl-class.md#settooltips). Weitere Informationen über die Implementierung von Quick Infos finden Sie in diesen einzelnen Element Funktionen und in der Behandlung von QuickInfo- [Benachrichtigungen](handling-tool-tip-notifications.md) .

Die- `CToolTipCtrl` Klasse stellt die Funktionalität des allgemeinen Windows-QuickInfo-Steuer Elements bereit. Ein einzelnes QuickInfo-Steuerelement kann Informationen für mehr als ein Tool bereitstellen. Ein Tool ist entweder ein Fenster, z. b. ein untergeordnetes Fenster oder Steuerelement, oder ein Anwendungs definierter rechteckiger Bereich im Client Bereich eines Fensters. Die [CMFCToolTipCtrl](reference/cmfctooltipctrl-class.md) -Klasse wird von abgeleitet `CToolTipCtrl` und stellt zusätzliche visuelle Stile und Funktionen bereit.

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolTipCtrl](using-ctooltipctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
