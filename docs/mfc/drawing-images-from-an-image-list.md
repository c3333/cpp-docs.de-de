---
title: Darstellen von Bildern aus einer Bildliste
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: 55c16ce5bff102d670e46867e121b0a0a2f304ac
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622849"
---
# <a name="drawing-images-from-an-image-list"></a>Darstellen von Bildern aus einer Bildliste

Um ein Bild zu zeichnen, verwenden Sie die Funktion [CImageList::D RAW](reference/cimagelist-class.md#draw) Member. Sie geben einen Zeiger auf ein Gerätekontext Objekt, den Index des zu zeichnenden Bilds, die Position im Gerätekontext, an dem das Bild gezeichnet werden soll, und einen Satz von Flags zum Angeben der Zeichnungs Art an.

Wenn Sie den **ILD_TRANSPARENT** Stil angeben, wird `Draw` von ein zweistufiger Prozess zum Zeichnen eines maskierten Bilds verwendet. Zuerst führt Sie eine logische and-Operation für die Bits des Bilds und die Bits der Maske aus. Anschließend führt er einen logischen XOR-Vorgang für die Ergebnisse des ersten Vorgangs und die hintergrundbits des Zielgeräte Kontexts aus. Dieser Prozess erstellt transparente Bereiche im resultierenden Image. Das heißt, jedes weiße Bit in der Maske bewirkt, dass das entsprechende Bit im resultierenden Bild transparent ist.

Vor dem Zeichnen eines maskierten Bilds auf einem voll Tonfarben-Hintergrund sollten Sie die Element Funktion [SetBkColor](reference/cimagelist-class.md#setbkcolor) verwenden, um die Hintergrundfarbe der Bildliste auf die gleiche Farbe wie das Ziel festzulegen. Durch das Festlegen der Farbe entfällt die Notwendigkeit, transparente Bereiche im Bild zu erstellen, und es wird ermöglicht, `Draw` das Bild einfach in den Zielgeräte Kontext zu kopieren, was zu einer deutlichen Leistungssteigerung führt. Um das Bild zu zeichnen, geben Sie den **ILD_NORMAL** Stil an, wenn Sie aufrufen `Draw` .

Sie können die Hintergrundfarbe für eine maskierte Bildliste ([CImageList](reference/cimagelist-class.md)) jederzeit festlegen, damit Sie auf einem beliebigen Solid-Hintergrund ordnungsgemäß funktioniert. Das Festlegen der Hintergrundfarbe auf **CLR_NONE** bewirkt, dass Bilder standardmäßig transparent gezeichnet werden. Um die Hintergrundfarbe einer Bildliste abzurufen, verwenden Sie die [GetBkColor](reference/cimagelist-class.md#getbkcolor) -Member-Funktion.

Die **ILD_BLEND25** -und **ILD_BLEND50** Stile weisen das Bild mit der Hervorhebungs Farbe des Systems an. Diese Stile sind nützlich, wenn Sie ein maskiertes Bild verwenden, um ein Objekt darzustellen, das der Benutzer auswählen kann. Beispielsweise können Sie den **ILD_BLEND50** Stil zum Zeichnen des Bilds verwenden, wenn es vom Benutzer ausgewählt wird.

Ein nicht maskiertes Bild wird mithilfe des Raster Vorgangs in den Zielgeräte Kontext kopiert `SRCCOPY` . Die Farben im Bild erscheinen unabhängig von der Hintergrundfarbe des Geräte Kontexts identisch. Die in angegebenen Zeichnungs Stile `Draw` haben auch keine Auswirkung auf das Aussehen eines nicht maskierten Bilds.

Zusätzlich zur Draw-Member-Funktion erweitert eine andere Funktion, [DrawIndirect](reference/cimagelist-class.md#drawindirect), die Fähigkeit zum Rendering eines Bilds. `DrawIndirect`übernimmt als Parameter eine [imagelistdrawparameams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) -Struktur. Diese Struktur kann zum Anpassen des Renderings des aktuellen Bilds verwendet werden, einschließlich der Verwendung von "Raster Operation (ROP)"-Codes. Weitere Informationen zu den Code-Codes finden Sie unter [Raster Vorgangs Codes](/windows/win32/gdi/raster-operation-codes) und [Bitmaps als Pinsel](/windows/win32/gdi/bitmaps-as-brushes) in der Windows SDK.

## <a name="see-also"></a>Siehe auch

[Verwenden von CImageList](using-cimagelist.md)<br/>
[Steuerelemente](controls-mfc.md)
