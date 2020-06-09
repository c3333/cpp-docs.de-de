---
title: Herausziehen von Bildern aus einer Bildliste
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 5d15b0b66d2270174dbfbcfd21bb77f5f41558c7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626485"
---
# <a name="dragging-images-from-an-image-list"></a>Herausziehen von Bildern aus einer Bildliste

[CImageList](reference/cimagelist-class.md) enthält Funktionen zum Ziehen eines Bilds auf dem Bildschirm. Die Zieh Funktionen verschieben ein Bild reibungslos, in Farbe und ohne Blinken des Cursors. Sowohl maskierte als auch unmaskierte Bilder können gezogen werden.

Die [BeginDrag](reference/cimagelist-class.md#begindrag) -Member-Funktion beginnt einen Zieh Vorgang. Zu den Parametern gehören der Index des zu ziehenden Bilds und der Speicherort des Hotspots innerhalb des Bilds. Der Hotspot ist ein einzelnes Pixel, das von den Zieh Funktionen als exakte Bildschirmposition des Bilds erkannt wird. In der Regel legt eine Anwendung den Hotspot fest, sodass Sie mit dem Hotspot des Mauszeigers übereinstimmt. Die [DragMove](reference/cimagelist-class.md#dragmove) -Member-Funktion verschiebt das Bild an einen neuen Speicherort.

Die Funktion [DragEnter](reference/cimagelist-class.md#dragenter) Member legt die Anfangsposition des Zieh Bilds innerhalb eines Fensters fest und zeichnet das Bild an der Position. Die Parameter enthalten einen Zeiger auf das Fenster, in dem das Bild gezeichnet werden soll, und einen Punkt, der die Koordinaten der ursprünglichen Position im Fenster angibt. Die Koordinaten sind relativ zur linken oberen Ecke des Fensters, nicht zum Client Bereich. Dasselbe gilt für alle Bild Zieh Funktionen, die Koordinaten als Parameter annehmen. Dies bedeutet, dass Sie die Breite von Fensterelementen, z. b. Rahmen, Titelleiste und Menüleiste, beim Angeben der Koordinaten ausgleichen müssen. Wenn Sie ein **null** -Fenster Handle beim Aufrufen `DragEnter` von angeben, zeichnen die Zieh Funktionen das Bild im Gerätekontext, der dem Desktop Fenster zugeordnet ist, und die Koordinaten sind relativ zur oberen linken Ecke des Bildschirms.

`DragEnter`sperrt alle anderen Updates für das angegebene Fenster während des Zieh Vorgangs. Wenn Sie während eines Zieh Vorgangs eine Zeichnung durchführen müssen, z. b. das Ziel eines Drag & Drop-Vorgangs, können Sie das gezogene Bild temporär ausblenden, indem Sie die [DragLeave](reference/cimagelist-class.md#dragleave) -Member-Funktion verwenden. Sie können auch die [DragShowNoLock](reference/cimagelist-class.md#dragshownolock) -Member-Funktion verwenden.

Ruft [EndDrag](reference/cimagelist-class.md#enddrag) auf, wenn Sie das Ziehen des Bilds abgeschlossen haben.

Die Member-Funktion [SetDragCursorImage](reference/cimagelist-class.md#setdragcursorimage) erstellt ein neues Zieh Bild, indem das angegebene Bild (in der Regel ein Mauszeiger Bild) mit dem aktuellen Drag-Bild kombiniert wird. Da die Zieh Funktionen das neue Bild während eines Zieh Vorgangs verwenden, sollten Sie die Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) -Funktion verwenden, um den eigentlichen Mauszeiger nach dem Aufruf von auszublenden `SetDragCursorImage` . Andernfalls weist das System möglicherweise zwei Mauszeiger auf die Dauer des Zieh Vorgangs auf.

Wenn eine Anwendung aufruft `BeginDrag` , erstellt das System eine temporäre, interne Bildliste und kopiert das angegebene Zieh Bild in die interne Liste. Mithilfe der [GetDragImage](reference/cimagelist-class.md#getdragimage) -Member-Funktion können Sie einen Zeiger auf die temporäre Ziehbild Liste abrufen. Die-Funktion ruft außerdem die aktuelle Zieh Position und den Offset des Zieh Bilds in Relation zur Zieh Position ab.

## <a name="see-also"></a>Siehe auch

[Verwenden von CImageList](using-cimagelist.md)<br/>
[Steuerelemente](controls-mfc.md)
