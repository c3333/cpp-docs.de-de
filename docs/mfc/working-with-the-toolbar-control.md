---
title: Arbeiten mit dem ToolBar-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 371f1944fae655556bbc9f89d7ffcce7cc326e5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365248"
---
# <a name="working-with-the-toolbar-control"></a>Arbeiten mit dem ToolBar-Steuerelement

In diesem Artikel wird erläutert, wie Sie auf das [CToolBarCtrl-Objekt](../mfc/reference/ctoolbarctrl-class.md) zugreifen können, das einer [CToolBar](../mfc/reference/ctoolbar-class.md) zugrunde liegt, um die Kontrolle über Ihre Symbolleisten zu erhalten. Dies ist ein fortgeschrittenes Thema.

## <a name="procedures"></a>Prozeduren

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>So greifen Sie auf das allgemeine Steuerelement der Symbolleiste zu, das Ihrem CToolBar-Objekt zugrunde liegt

1. Rufen Sie [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)auf.

`GetToolBarCtrl`gibt einen Verweis auf ein [CToolBarCtrl-Objekt](../mfc/reference/ctoolbarctrl-class.md) zurück. Sie können den Verweis verwenden, um Memberfunktionen der Symbolleistensteuerungsklasse aufzurufen.

> [!CAUTION]
> Während `CToolBarCtrl` das Aufrufen von **Get-Funktionen** sicher ist, sollten Sie vorsichtig sein, wenn Sie die **Set-Funktionen** aufrufen. Dies ist ein fortgeschrittenes Thema. Normalerweise sollten Sie nicht auf das zugrunde liegende Symbolleistensteuerelement zugreifen müssen.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Steuerelemente (allgemeine Windows-Steuerelemente)](../mfc/controls-mfc.md)

- [Toolbar-Grundlagen](../mfc/toolbar-fundamentals.md)

- [Docking und schwimmende Symbolleisten](../mfc/docking-and-floating-toolbars.md)

- [Dynamische Größenänderung der Symbolleiste](../mfc/docking-and-floating-toolbars.md)

- [QuickInfos für die Symbolleiste](../mfc/toolbar-tool-tips.md)

- [Flyby-Statusleisten-Updates](../mfc/toolbar-tool-tips.md)

- [Umgang mit Tool-Tipp-Benachrichtigungen](../mfc/handling-tool-tip-notifications.md)

- Die Klassen [CToolBar](../mfc/reference/ctoolbar-class.md) und [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Behandlung von Anpassungsbenachrichtigungen](../mfc/handling-customization-notifications.md)

- [Mehrere Symbolleisten](../mfc/toolbar-fundamentals.md)

- [Verwenden Ihrer alten Symbolleisten](../mfc/using-your-old-toolbars.md)

- [Steuerleisten](../mfc/control-bars.md)

Allgemeine Informationen zur Verwendung allgemeiner Windows-Steuerelemente finden Sie unter [Allgemeine Steuerelemente](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Siehe auch

[Implementieren der MFC-Symbolleiste](../mfc/mfc-toolbar-implementation.md)
