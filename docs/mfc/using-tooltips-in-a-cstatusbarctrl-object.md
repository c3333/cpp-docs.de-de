---
title: Verwenden von QuickInfos in einem CStatusBarCtrl-Objekt
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 29d326c708743424686d616bbaf172ccd72481ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374696"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Verwenden von QuickInfos in einem CStatusBarCtrl-Objekt

Um QuickInfos für ein Statusleistensteuerelement zu aktivieren, erstellen Sie das `CStatusBarCtrl` Objekt mit dem Stil SBT_TOOLTIPS.

> [!NOTE]
> Wenn Sie ein `CStatusBar` Objekt zum Implementieren der `CStatusBar::CreateEx` Statusleiste verwenden, verwenden Sie die Funktion. Sie können zusätzliche Stile für `CStatusBarCtrl` das eingebettete Objekt angeben.

Nachdem `CStatusBarCtrl` das Objekt erfolgreich erstellt wurde, verwenden Sie [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) und [CStatusBarCtrl::GetTipText,](../mfc/reference/cstatusbarctrl-class.md#gettiptext) um den Tipptext für einen bestimmten Bereich festzulegen und abzurufen.

Sobald die QuickInfo festgelegt wurde, wird sie nur angezeigt, wenn das Teil ein Symbol und keinen Text enthält oder wenn der gesamte Text nicht innerhalb des Teils angezeigt werden kann. Tool-Tipps werden im einfachen Modus nicht unterstützt.

## <a name="see-also"></a>Siehe auch

[Verwenden von CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
