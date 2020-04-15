---
title: Erstellen der Bildliste
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 440ab6fdfe7663557f6c6a6607e617c793d26674
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371574"
---
# <a name="creating-the-image-lists"></a>Erstellen der Bildliste

Das Erstellen von Bildlisten ist identisch, unabhängig davon, ob Sie [CListView](../mfc/reference/clistview-class.md) oder [CListCtrl](../mfc/reference/clistctrl-class.md)verwenden.

> [!NOTE]
> Sie benötigen Bildlisten nur, wenn `LVS_ICON` das Listensteuerelement den Stil enthält.

Verwenden `CImageList` Sie die Klasse, um eine oder mehrere Bildlisten zu erstellen (für Symbole in voller Größe, kleine Symbole und Zustände). Siehe [CImageList](../mfc/reference/cimagelist-class.md), und siehe [Listenansicht S/D.A.](/windows/win32/Controls/using-list-view-controls) im Windows SDK.

Rufen Sie [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) für jede Bildliste auf; einen Zeiger auf das `CImageList` entsprechende Objekt übergeben.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](../mfc/using-clistctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
