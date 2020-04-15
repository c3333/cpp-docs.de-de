---
title: Anpassen der Darstellung eines Symbolleisten-Steuerelements
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: 9f4f9d90113d5074555d1b0cc411f854abc67fe5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377462"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Anpassen der Darstellung eines Symbolleisten-Steuerelements

Die `CToolBarCtrl` Klasse stellt viele Stile bereit, die sich auf das Erscheinungsbild (und gelegentlich auch auf das Verhalten) des Symbolleistenobjekts auswirken. Ändern Sie das Symbolleistenobjekt, `CToolBarCtrl::Create` indem `CToolBar::CreateEx`Sie den `dwCtrlStyle` Parameter der Memberfunktion (oder ) festlegen, wenn Sie das Symbolleistensteuerelement zum ersten Mal erstellen.

Die folgenden Formatvorlagen wirken sich auf den "3D"-Aspekt der Symbolleistenschaltflächen und die Platzierung des Schaltflächentextes aus:

- **TBSTYLE_FLAT** Erstellt eine flache Symbolleiste, in der sowohl die Symbolleiste als auch die Schaltflächen transparent sind. Schaltflächentext wird unter Schaltflächenbitmaps angezeigt. Wenn dieser Stil verwendet wird, wird die Schaltfläche unter dem Cursor automatisch hervorgehoben.

- **TBSTYLE_TRANSPARENT** Erstellt eine transparente Symbolleiste. In einer transparenten Symbolleiste ist die Symbolleiste transparent, die Schaltflächen jedoch nicht. Schaltflächentext wird unter Schaltflächenbitmaps angezeigt.

- **TBSTYLE_LIST** Platziert Schaltflächentext rechts neben Schaltflächenbitmaps.

> [!NOTE]
> Um Neulackierungsprobleme zu vermeiden, sollten die **TBSTYLE_FLAT** und **TBSTYLE_TRANSPARENT** Stile festgelegt werden, bevor das Symbolleistenobjekt sichtbar ist.

Die folgenden Stile bestimmen, ob die Symbolleiste es einem Benutzer ermöglicht, einzelne Schaltflächen innerhalb eines Symbolleistenobjekts per Drag & Drop neu zu positionieren:

- **TBSTYLE_ALTDRAG** Ermöglicht es Benutzern, die Position einer Symbolleistenschaltfläche zu ändern, indem sie sie ziehen, während SIE ALT gedrückt hält. Wenn dieser Stil nicht angegeben ist, muss der Benutzer die UMSCHALTTASTE gedrückt halten, während er eine Schaltfläche zieht.

    > [!NOTE]
    >  Der **CCS_ADJUSTABLE-Stil** muss angegeben werden, damit Symbolleistenschaltflächen gezogen werden können.

- **TBSTYLE_REGISTERDROP** Generiert **TBN_GETOBJECT** Benachrichtigungen, um Dropzielobjekte anzufordern, wenn der Mauszeiger über Symbolleistenschaltflächen geht.

Die verbleibenden Stile wirken sich auf visuelle und nicht visuelle Aspekte des Symbolleistenobjekts aus:

- **TBSTYLE_WRAPABLE** Erstellt eine Symbolleiste mit mehreren Schaltflächenzeilen. Symbolleistenschaltflächen können in die nächste Zeile "umbrochen" werden, wenn die Symbolleiste zu schmal wird, um alle Schaltflächen in derselben Zeile einzuschließen. Das Umschließen erfolgt bei Trennungs- und Gruppengrenzen.

- **TBSTYLE_CUSTOMERASE** Generiert **NM_CUSTOMDRAW** Benachrichtigungen, wenn **nachrichtenWM_ERASEBKGND** verarbeitet werden.

- **TBSTYLE_TOOLTIPS** Erstellt ein QuickInfo-Steuerelement, mit dem eine Anwendung beschreibenden Text für die Schaltflächen in der Symbolleiste anzeigen kann.

Eine vollständige Liste der Symbolleistenstile und erweiterten Stile finden Sie unter [Symbolleistensteuerung und Schaltflächenstile](/windows/win32/Controls/toolbar-control-and-button-styles) und [erweiterte Formatvorlagen](/windows/win32/Controls/toolbar-extended-styles) der Symbolleiste im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
