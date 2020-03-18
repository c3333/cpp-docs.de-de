---
title: Verwenden von CToolTipCtrl zum Erstellen und Bearbeiten eines CToolTipCtrl-Objekts
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: 37dc7bc5a411ebab3737b87fd6977b26cff68178
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442219"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Verwenden von CToolTipCtrl zum Erstellen und Bearbeiten eines CToolTipCtrl-Objekts

Im folgenden finden Sie ein Beispiel für die Verwendung von [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) :

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>So erstellen und bearbeiten Sie einen CToolTipCtrl

1. Erstellen Sie das `CToolTipCtrl`-Objekt.

1. Rufen Sie [Create](../mfc/reference/ctooltipctrl-class.md#create) auf, um das allgemeine Steuerelement für die Windows-ToolTip zu erstellen, und fügen Sie es dem `CToolTipCtrl`

1. Ruft [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) auf, um ein Tool mit dem QuickInfo-Steuerelement zu registrieren, sodass die in der QuickInfo gespeicherten Informationen angezeigt werden, wenn sich der Cursor auf dem Tool befindet.

1. Aufrufen von [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) , um die Informationen festzulegen, die eine QuickInfo für ein Tool beibehält.

1. Aufrufen von [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) zum Festlegen eines neuen umgebenden Rechtecks für ein Tool.

1. Rufen Sie [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) auf, um einen Punkt zu testen, um zu bestimmen, ob er sich innerhalb des umgebenden Rechtecks des angegebenen Tools befindet, und rufen Sie ggf. Informationen über das Tool ab.

1. Rufen Sie [gettoolcount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) auf, um die Anzahl der Tools abzurufen, die mit dem QuickInfo-Steuerelement registriert wurden.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
