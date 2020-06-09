---
title: Bildinformationen in Bildlisten
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: c12198c769585763095d22b73d11f7af3c9d6fc0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624496"
---
# <a name="image-information-in-image-lists"></a>Bildinformationen in Bildlisten

[CImageList](reference/cimagelist-class.md) enthält eine Reihe von Funktionen, mit denen Informationen aus einer Bildliste abgerufen werden. Die [getimageinfo](reference/cimagelist-class.md#getimageinfo) -Element Funktion füllt eine `IMAGEINFO` Struktur mit Informationen zu einem einzelnen Bild, einschließlich der Zieh Punkte der Bild-und Masken Bitmaps, der Anzahl von Farbebenen und Bits pro Pixel und des umgebenden Rechtecks des Bilds in der bildbitmap. Sie können diese Informationen verwenden, um die Bitmaps für das Image direkt zu bearbeiten.

Die [GetImageCount](reference/cimagelist-class.md#getimagecount) -Member-Funktion Ruft die Anzahl der Bilder in einer Bildliste ab.

Sie können ein Symbol auf der Grundlage eines Bilds und einer Maske in einer Bildliste erstellen, indem Sie die [ExtractIcon](reference/cimagelist-class.md#extracticon) -Member-Funktion verwenden. Die-Funktion gibt das Handle des neuen Symbols zurück.

## <a name="see-also"></a>Siehe auch

[Verwenden von CImageList](using-cimagelist.md)<br/>
[Steuerelemente](controls-mfc.md)
