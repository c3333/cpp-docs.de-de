---
title: Verwenden von QuickInfos in einem CStatusBarCtrl-Objekt
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: a607a5fb8c9470df42d12c771865b924891b2dac
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442543"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Verwenden von QuickInfos in einem CStatusBarCtrl-Objekt

Um Quick Infos für ein StatusBar-Steuerelement zu aktivieren, erstellen Sie das `CStatusBarCtrl`-Objekt mit der SBT_TOOLTIPS-Formatvorlage.

> [!NOTE]
>  Wenn Sie ein `CStatusBar` Objekt zum Implementieren der Statusleiste verwenden, verwenden Sie die `CStatusBar::CreateEx`-Funktion. Sie ermöglicht es Ihnen, zusätzliche Stile für das eingebettete `CStatusBarCtrl` Objekt anzugeben.

Nachdem das `CStatusBarCtrl`-Objekt erfolgreich erstellt wurde, verwenden Sie [cstatus barctrl:: SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) und [cstatus-barstrg:: GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) , um den QuickInfo-Text für einen bestimmten Bereich festzulegen und abzurufen.

Nachdem die QuickInfo festgelegt wurde, wird Sie nur angezeigt, wenn der Teil ein Symbol und keinen Text enthält, oder wenn der gesamte Text nicht innerhalb des Teils angezeigt werden kann. Quick Infos werden im einfachen Modus nicht unterstützt.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
