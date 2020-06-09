---
title: Erstellen der Bildliste
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: bbba01a6a8e08ea53e164656733aa06e03dd87a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625948"
---
# <a name="creating-the-image-lists"></a>Erstellen der Bildliste

Das Erstellen von Image Listen ist identisch, unabhängig davon, ob Sie [CListView](reference/clistview-class.md) oder [CListCtrl](reference/clistctrl-class.md)verwenden.

> [!NOTE]
> Sie benötigen nur Bildlisten, wenn das Listen Steuerelement den `LVS_ICON` Stil enthält.

Verwenden `CImageList` Sie die-Klasse, um eine oder mehrere Bildlisten zu erstellen (für Symbole in voller Größe, kleine Symbole und Zustände). Weitere Informationen finden Sie unter [CImageList](reference/cimagelist-class.md)und [Bildlisten](/windows/win32/Controls/using-list-view-controls) der Listenansicht im Windows SDK.

[CListCtrl:: SetImageList](reference/clistctrl-class.md#setimagelist) für jede Bildliste abrufen übergeben Sie einen Zeiger auf das entsprechende- `CImageList` Objekt.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
