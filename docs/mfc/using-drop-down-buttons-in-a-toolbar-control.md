---
title: Verwenden von DropDown-Schaltflächen in einem Symbolleisten-Steuerelement
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: 0bc4df4c07ec4b8bc5b488925cbb140609302186
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365070"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Verwenden von DropDown-Schaltflächen in einem Symbolleisten-Steuerelement

Zusätzlich zu den Standard-Drucktasten kann eine Symbolleiste auch Dropdown-Tasten haben. Eine Dropdown-Schaltfläche wird in der Regel durch das Vorhandensein eines angefügten Pfeils nach unten angezeigt.

> [!NOTE]
> Der angefügte Pfeil nach unten wird nur angezeigt, wenn der TBSTYLE_EX_DRAWDDARROWS erweiterten Stil festgelegt wurde.

Wenn der Benutzer auf diesen Pfeil (oder die Schaltfläche selbst, wenn kein Pfeil vorhanden ist) klickt, wird eine TBN_DROPDOWN Benachrichtigung an das übergeordnete Element des Symbolleistensteuerelements gesendet. Sie können diese Benachrichtigung dann behandeln und ein Popupmenü anzeigen. ähnlich dem Verhalten von Internet Explorer.

Das folgende Verfahren veranschaulicht, wie Sie eine Dropdown-Symbolleistenschaltfläche mit einem Popupmenü implementieren:

### <a name="to-implement-a-drop-down-button"></a>So implementieren Sie eine Dropdown-Schaltfläche

1. Nachdem `CToolBarCtrl` Das Objekt erstellt wurde, legen Sie den TBSTYLE_EX_DRAWDDARROWS Stil mithilfe des folgenden Codes fest:

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Legen Sie den TBSTYLE_DROPDOWN Stil für alle neuen ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) oder [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) oder vorhandenen ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) Schaltflächen fest, die Dropdown-Schaltflächen sind. Im folgenden Beispiel wird das Ändern `CToolBarCtrl` einer vorhandenen Schaltfläche in einem Objekt veranschaulicht:

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Fügen Sie der übergeordneten Klasse des Symbolleistenobjekts einen TBN_DROPDOWN-Handler hinzu.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. Zeigen Sie im neuen Handler das entsprechende Popupmenü an. Der folgende Code veranschaulicht eine Methode:

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
