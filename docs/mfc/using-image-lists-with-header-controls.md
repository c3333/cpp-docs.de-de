---
title: Verwenden von Bildlisten in Headersteuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 8002c16d1cdf5e0683b642001409b6da9c260660
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366468"
---
# <a name="using-image-lists-with-header-controls"></a>Verwenden von Bildlisten in Headersteuerelementen

Kopfzeilenelemente können ein Bild innerhalb eines Kopfelements anzeigen. Dieses Bild, das in einer zugeordneten Bildliste gespeichert ist, hat 16 x 16 Pixel und hat die gleichen Eigenschaften wie die Symbolbilder, die in einem Listenansichtssteuerelement verwendet werden. Um dieses Verhalten erfolgreich zu implementieren, müssen Sie zuerst die Bildliste erstellen und initialisieren, die Liste dem Kopfkopfsteuerelement zuordnen und dann die Attribute des Kopfelements ändern, das das Bild anzeigt.

Das folgende Verfahren veranschaulicht die Details mithilfe eines Zeigers auf ein Headersteuerelement`m_pHdrCtrl`(`m_pHdrImages`) und eines Zeigers auf eine Bildliste ( ).

### <a name="to-display-an-image-in-a-header-item"></a>So zeigen Sie ein Bild in einem Kopfelement an

1. Erstellen Sie eine neue Bildliste (oder verwenden Sie ein vorhandenes Bildlistenobjekt) mit dem [CImageList-Konstruktor,](../mfc/reference/cimagelist-class.md) in dem der resultierende Zeiger gespeichert wird.

1. Initialisieren Sie das neue Bildlistenobjekt, indem Sie [CImageList::Create](../mfc/reference/cimagelist-class.md#create)aufrufen. Der folgende Code ist ein Beispiel für diesen Aufruf.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Fügen Sie die Bilder für jedes Kopfelement hinzu. Der folgende Code fügt zwei vordefinierte Bilder hinzu.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Ordnen Sie die Bildliste dem Headersteuerelement einem Aufruf von [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist)zu.

1. Ändern Sie das Kopfelement, um ein Bild aus der zugeordneten Bildliste anzuzeigen. Im folgenden Beispiel wird das `m_phdrImages`erste Bild von dem `m_pHdrCtrl`dem ersten Kopfelement zugewiesen.

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Ausführliche Informationen zu den verwendeten Parameterwerten finden Sie im entsprechenden [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
> Es ist möglich, mehrere Steuerelemente mit derselben Bildliste zu verwenden. In einem Standardlistenansichtssteuerelement kann z. B. eine Bildliste (mit 16 x 16 Pixel-Bildern) sowohl von der kleinen Symbolansicht eines Listenansichtssteuerelements als auch von den Kopfzeilenelementen des Listenansichtssteuerelements verwendet werden.

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](../mfc/using-cheaderctrl.md)
