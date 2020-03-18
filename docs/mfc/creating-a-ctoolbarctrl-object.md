---
title: Erstellen eines CToolBarCtrl-Objekts
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: cf1d2eeb9efd2f8a1e7b433c0e18dd868a8b9aca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445893"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Erstellen eines CToolBarCtrl-Objekts

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) -Objekte enthalten mehrere interne Datenstrukturen – eine Liste von Schaltflächen Bild-Bitmaps, eine Liste von Schaltflächen-Beschriftungs Zeichenfolgen und eine Liste mit `TBBUTTON` Strukturen –, die ein Bild und/oder eine Zeichenfolge mit der Position, dem Format, dem Zustand und der Befehls-ID der Schaltfläche verknüpfen. Auf jedes Element dieser Datenstrukturen wird durch einen NULL basierten Index verwiesen. Bevor Sie ein `CToolBarCtrl` Objekt verwenden können, müssen Sie diese Datenstrukturen einrichten. Eine Liste der Datenstrukturen finden Sie unter Symbolleisten-Steuer [Elemente](controls-mfc.md) im Windows SDK. Die Liste der Zeichen folgen kann nur für Schaltflächen Beschriftungen verwendet werden. Zeichen folgen können nicht von der Symbolleiste abgerufen werden.

Um ein `CToolBarCtrl` Objekt zu verwenden, führen Sie in der Regel die folgenden Schritte aus:

### <a name="to-use-a-ctoolbarctrl-object"></a>So verwenden Sie ein CToolBarCtrl-Objekt

1. Erstellen Sie das [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) -Objekt.

1. Rufen Sie [Create](../mfc/reference/ctoolbarctrl-class.md#create) auf, um das allgemeine Windows-Symbolleisten Steuerelement zu erstellen, und fügen Sie es an das `CToolBarCtrl` Wenn Sie Bitmap-Bilder für Schaltflächen verwenden möchten, fügen Sie der Symbolleiste die Schaltflächen Bitmaps hinzu, indem Sie [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap)aufrufen. Wenn Sie Zeichen folgen Bezeichnungen für Schaltflächen verwenden möchten, fügen Sie die Zeichen folgen der Symbolleiste hinzu, indem Sie [AddString](../mfc/reference/ctoolbarctrl-class.md#addstring) und/oder [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings)aufrufen. Nachdem Sie `AddString` und/oder `AddStrings`aufgerufen haben, sollten Sie [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) aufrufen, um die Zeichenfolge oder Zeichen folgen anzuzeigen.

1. Fügen Sie der Symbolleiste Schaltflächen Strukturen hinzu, indem Sie [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)aufrufen.

1. Wenn Sie Quick Infos wünschen, behandeln Sie **TTN_NEEDTEXT** Meldungen im Fenster "Besitzer" der Symbolleiste, wie unter Behandlung von QuickInfo- [Benachrichtigungen](../mfc/handling-tool-tip-notifications.md)beschrieben.

1. Wenn Sie möchten, dass der Benutzer die Symbolleiste anpassen kann, behandeln Sie Anpassungs Benachrichtigungs Meldungen im Besitzer Fenster, wie unter [Behandeln von Anpassungs Benachrichtigungen](../mfc/handling-customization-notifications.md)beschrieben.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
