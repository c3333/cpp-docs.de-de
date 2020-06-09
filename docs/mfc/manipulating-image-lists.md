---
title: Bearbeiten von Bildlisten
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: cb7376241febd6bd1545cd183147e14a15313820
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622459"
---
# <a name="manipulating-image-lists"></a>Bearbeiten von Bildlisten

Die [Replace](reference/cimagelist-class.md#replace) Member-Funktion ersetzt ein Bild in einer Bildliste ([CImageList](reference/cimagelist-class.md)) durch ein neues Bild. Diese Funktion ist auch nützlich, wenn Sie die Anzahl von Bildern in einem Bildlisten Objekt dynamisch erhöhen müssen. Die [Funktion "](reference/cimagelist-class.md#setimagecount) " der Funktion "-Funktion" ändert die Anzahl der in der Bildliste gespeicherten Bilder dynamisch. Wenn Sie die Größe der Bildliste vergrößern, wird aufgerufen, `Replace` um den neuen Bild Slots Bilder hinzuzufügen. Wenn Sie die Größe der Bildliste verringern, werden die Images, die die neue Größe überschreiten, freigegeben.

Die [Remove](reference/cimagelist-class.md#remove) Member-Funktion entfernt ein Bild aus einer Bildliste. Die [Copy](reference/cimagelist-class.md#copy) -Member-Funktion kann Bilder in einer Bildliste kopieren oder austauschen. Mit dieser Funktion können Sie angeben, ob das Quell Abbild in den Zielindex kopiert werden soll, oder ob die Quell-und Ziel Images ausgetauscht werden sollen.

Um eine neue Bildliste durch Zusammenführen von zwei Bildlisten zu erstellen, verwenden Sie die entsprechende Überladung der [Create](reference/cimagelist-class.md#create) Member-Funktion. Diese Überladung von führt `Create` das erste Bild der vorhandenen Bildlisten zusammen, wobei das resultierende Bild in einem neuen Bildlisten Objekt gespeichert wird. Das neue Bild wird erstellt, indem das zweite Bild transparent über das erste gezeichnet wird. Die Maske für das neue Image ist das Ergebnis der Ausführung einer logischen OR-Operation auf den Bits der Masken für die beiden vorhandenen Bilder.

Dies wird wiederholt, bis alle Bilder zusammengeführt und dem neuen Bildlisten Objekt hinzugefügt wurden.

Sie können die Bild Informationen in ein Archiv schreiben, indem Sie die Funktion zum [Schreiben](reference/cimagelist-class.md#write) von Membern aufrufen und Sie zurück lesen, indem Sie die Funktion zum [Lesen](reference/cimagelist-class.md#read) von Membern aufrufen.

Die Funktionen " [gezafehandle](reference/cimagelist-class.md#getsafehandle)", " [Attach](reference/cimagelist-class.md#attach)" und " [Detach](reference/cimagelist-class.md#detach) " ermöglichen es Ihnen, das Handle der an das Objekt angefügten Bildliste zu bearbeiten `CImageList` , während die Member-Funktion von [DeleteImageList](reference/cimagelist-class.md#deleteimagelist) die Bildliste löscht, ohne das Objekt zu zerstören `CImageList` .

## <a name="see-also"></a>Siehe auch

[Verwenden von CImageList](using-cimagelist.md)<br/>
[Steuerelemente](controls-mfc.md)
