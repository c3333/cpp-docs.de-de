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
ms.openlocfilehash: bd099a67d9f11cc3657a91b4141d3f18c6fa719d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621650"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Initialisieren der Teile eines CStatusBarCtrl-Objekts

In einer Statusleiste werden standardmäßig Statusinformationen über separate Bereiche angezeigt. Diese Bereiche (auch als Teile bezeichnet) können entweder eine Text Zeichenfolge, ein Symbol oder beides enthalten.

Verwenden Sie [SetParts](reference/cstatusbarctrl-class.md#setparts) , um zu definieren, wie viele Teile und welche Länge die Statusleiste aufweisen soll. Nachdem Sie die Teile der Statusleiste erstellt haben, rufen Sie [SetText](reference/cstatusbarctrl-class.md#settext) und [SetIcon](reference/cstatusbarctrl-class.md#seticon) auf, um den Text oder das Symbol für einen bestimmten Teil der Statusleiste festzulegen. Nachdem der Teil erfolgreich festgelegt wurde, wird das Steuerelement automatisch neu gezeichnet.

Im folgenden Beispiel wird ein vorhandenes `CStatusBarCtrl` -Objekt () mit vier Bereichen initialisiert, `m_StatusBarCtrl` und anschließend wird ein Symbol (IDI_ICON1) und ein Text im zweiten Teil festgelegt.

[!code-cpp[NVC_MFCControlLadenDialog#31](codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Weitere Informationen zum Festlegen des Modus eines- `CStatusBarCtrl` Objekts auf "einfach" finden Sie unter [Festlegen des Modus eines cstatus-barctrl-Objekts](setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Siehe auch

[Verwenden von CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
