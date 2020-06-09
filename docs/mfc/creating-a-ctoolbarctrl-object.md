---
title: Erstellen eines CToolBarCtrl-Objekts
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: 2627f9aaceeab7760e15b23435233e124c5ea6f0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619002"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Erstellen eines CToolBarCtrl-Objekts

[CToolBarCtrl](reference/ctoolbarctrl-class.md) -Objekte enthalten mehrere interne Datenstrukturen – eine Liste von Schaltflächen Bild-Bitmaps, eine Liste von Schaltflächen-Beschriftungs Zeichenfolgen und eine Liste von `TBBUTTON` Strukturen –, die ein Bild und/oder eine Zeichenfolge mit der Position, dem Stil, dem Zustand und der Befehls-ID der Schaltfläche verknüpfen. Auf jedes Element dieser Datenstrukturen wird durch einen NULL basierten Index verwiesen. Bevor Sie ein-Objekt verwenden können `CToolBarCtrl` , müssen Sie diese Datenstrukturen einrichten. Eine Liste der Datenstrukturen finden Sie unter Symbolleisten-Steuer [Elemente](controls-mfc.md) im Windows SDK. Die Liste der Zeichen folgen kann nur für Schaltflächen Beschriftungen verwendet werden. Zeichen folgen können nicht von der Symbolleiste abgerufen werden.

Um ein- `CToolBarCtrl` Objekt zu verwenden, führen Sie in der Regel die folgenden Schritte aus:

### <a name="to-use-a-ctoolbarctrl-object"></a>So verwenden Sie ein CToolBarCtrl-Objekt

1. Erstellen Sie das [CToolBarCtrl](reference/ctoolbarctrl-class.md) -Objekt.

1. Rufen Sie [Create](reference/ctoolbarctrl-class.md#create) auf, um das allgemeine Windows-Symbolleisten-Steuerelement zu erstellen, und fügen Sie es an `CToolBarCtrl` Wenn Sie Bitmap-Bilder für Schaltflächen verwenden möchten, fügen Sie der Symbolleiste die Schaltflächen Bitmaps hinzu, indem Sie [AddBitmap](reference/ctoolbarctrl-class.md#addbitmap)aufrufen. Wenn Sie Zeichen folgen Bezeichnungen für Schaltflächen verwenden möchten, fügen Sie die Zeichen folgen der Symbolleiste hinzu, indem Sie [AddString](reference/ctoolbarctrl-class.md#addstring) und/oder [AddStrings](reference/ctoolbarctrl-class.md#addstrings)aufrufen. Nach dem Aufrufen von `AddString` und/oder `AddStrings` sollten Sie [AutoSize](reference/ctoolbarctrl-class.md#autosize) aufrufen, um die Zeichenfolge oder die Zeichen folgen zu erhalten.

1. Fügen Sie der Symbolleiste Schaltflächen Strukturen hinzu, indem Sie [AddButtons](reference/ctoolbarctrl-class.md#addbuttons)aufrufen.

1. Wenn Sie Quick Infos wünschen, behandeln Sie **TTN_NEEDTEXT** Meldungen im Fenster "Besitzer" der Symbolleiste, wie unter Behandlung von QuickInfo- [Benachrichtigungen](handling-tool-tip-notifications.md)beschrieben.

1. Wenn Sie möchten, dass der Benutzer die Symbolleiste anpassen kann, behandeln Sie Anpassungs Benachrichtigungs Meldungen im Besitzer Fenster, wie unter [Behandeln von Anpassungs Benachrichtigungen](handling-customization-notifications.md)beschrieben.

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
