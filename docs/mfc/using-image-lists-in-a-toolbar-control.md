---
title: Verwenden von Bildlisten in einem Symbolleisten-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: 81468528c15300a7e9ace6b20fd9fb34818f1928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366494"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Verwenden von Bildlisten in einem Symbolleisten-Steuerelement

Standardmäßig werden die Bilder, die von den Schaltflächen in einem Symbolleistensteuerelement verwendet werden, als einzelne Bitmap gespeichert. Sie können jedoch auch Schaltflächenbilder in einer Reihe von Bildlisten speichern. Das Symbolleistensteuerelement kann bis zu drei separate Bildlisten verwenden:

- Aktivierte Bildliste Enthält Bilder für Symbolleistenschaltflächen, die derzeit aktiviert sind.

- Deaktivierte Bildliste Enthält Bilder für Symbolleistenschaltflächen, die derzeit deaktiviert sind.

- Hervorgehobene Bildliste Enthält Bilder für Symbolleistenschaltflächen, die derzeit hervorgehoben sind. Diese Bildliste wird nur verwendet, wenn die Symbolleiste den TBSTYLE_FLAT-Stil verwendet.

Diese Bildlisten werden vom Symbolleistensteuerelement verwendet, `CToolBarCtrl` wenn Sie sie dem Objekt zuordnen. Diese Zuordnung wird durch Aufrufe von [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)und [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist)erreicht.

Standardmäßig verwendet MFC `CToolBar` die Klasse, um MFC-Anwendungssymbolleisten zu implementieren. Die `GetToolBarCtrl` Memberfunktion kann jedoch verwendet werden, um das eingebettete `CToolBarCtrl` Objekt abzurufen. Sie können dann `CToolBarCtrl` mithilfe des zurückgegebenen Objekts Aufrufe von Memberfunktionen tätigen.

Im folgenden Beispiel wird diese Technik`m_ToolBarImages`veranschaulicht, indem`m_ToolBarDisabledImages`einem `CToolBarCtrl` Objekt eine`m_ToolBarCtrl`aktivierte ( ) und deaktivierte ( ) Bildliste zugewiesen wird ( ).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> Die vom Symbolleistenobjekt verwendeten Bildlisten müssen permanente Objekte sein. Aus diesem Grund sind sie häufig Datenmember einer MFC-Klasse. in diesem Beispiel die Hauptrahmenfensterklasse.

Sobald die Bildlisten dem `CToolBarCtrl` Objekt zugeordnet sind, zeigt das Framework automatisch das richtige Schaltflächenbild an.

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
