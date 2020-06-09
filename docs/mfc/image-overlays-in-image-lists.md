---
title: Overlaymasken in Bildlisten
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: 861bcd5165ad0938ae6bbd77fc4a9f09095ce789
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624480"
---
# <a name="image-overlays-in-image-lists"></a>Overlaymasken in Bildlisten

Jede Bildliste ([CImageList](reference/cimagelist-class.md)) enthält eine Liste von Bildern, die als Überlagerungs Masken verwendet werden sollen. Eine "Überlagerungs Maske" ist ein Bild, das transparent über ein anderes Bild gezeichnet wird. Alle Bilder können als Überlagerungs Maske verwendet werden. Sie können bis zu vier Überlagerungs Masken pro Bildliste angeben.

Sie fügen den Index eines Bilds der Liste der Überlagerungs Masken hinzu, indem Sie die Member-Funktion " [SetImage](reference/cimagelist-class.md#setoverlayimage) ", den Index eines Bilds und den Index einer Überlagerungs Maske verwenden. Beachten Sie, dass die Indizes für die Überlagerungs Masken jeweils einbasiert und nicht NULL basiert sind.

Sie zeichnen eine Überlagerungs Maske über ein Bild mithilfe eines einzelnen Aufrufens von `Draw` . Zu den Parametern gehören der Index des zu zeichnenden Bilds und der Index einer Überlagerungs Maske. Sie müssen das [indexyoverlaymask](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) -Makro verwenden, um den Index der Überlagerungs Maske anzugeben. Sie können auch ein Überlagerungs Bild angeben, wenn Sie die [DrawIndirect](reference/cimagelist-class.md#drawindirect) -Member-Funktion aufrufen.

## <a name="see-also"></a>Siehe auch

[Verwenden von CImageList](using-cimagelist.md)<br/>
[Steuerelemente](controls-mfc.md)
