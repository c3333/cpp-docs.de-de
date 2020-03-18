---
title: Initialisieren der Teile eines CStatusBarCtrl-Objekts
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: a5b65a2bbb68eaa7058f3514bb95a5209a0e5e71
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444451"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Initialisieren der Teile eines CStatusBarCtrl-Objekts

In einer Statusleiste werden standardmäßig Statusinformationen über separate Bereiche angezeigt. Diese Bereiche (auch als Teile bezeichnet) können entweder eine Text Zeichenfolge, ein Symbol oder beides enthalten.

Verwenden Sie [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) , um zu definieren, wie viele Teile und welche Länge die Statusleiste aufweisen soll. Nachdem Sie die Teile der Statusleiste erstellt haben, rufen Sie [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) und [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) auf, um den Text oder das Symbol für einen bestimmten Teil der Statusleiste festzulegen. Nachdem der Teil erfolgreich festgelegt wurde, wird das Steuerelement automatisch neu gezeichnet.

Im folgenden Beispiel wird ein vorhandenes `CStatusBarCtrl` Objekt (`m_StatusBarCtrl`) mit vier Bereichen initialisiert und anschließend ein Symbol (IDI_ICON1) und ein Text im zweiten Teil festgelegt.

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Weitere Informationen zum Festlegen des Modus eines `CStatusBarCtrl` Objekts auf "einfach" finden Sie unter [Festlegen des Modus eines cstatus-barctrl-Objekts](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
