---
title: Verwenden einer Bildliste
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 0d9566739a15e5d216eb052a7265313850515648
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366571"
---
# <a name="using-an-image-list"></a>Verwenden einer Bildliste

Die typische Verwendung einer Bildliste folgt dem folgenden Muster:

- Erstellen Sie ein [CImageList-Objekt,](../mfc/reference/cimagelist-class.md) und rufen Sie eine der Überladungen `CImageList` der [Create-Funktion](../mfc/reference/cimagelist-class.md#create) auf, um eine Bildliste zu erstellen und an das Objekt anzufügen.

- Wenn Sie beim Erstellen der Bildliste keine Bilder hinzugefügt haben, fügen Sie der Bildliste Bilder hinzu, indem Sie die Funktion Member [hinzufügen](../mfc/reference/cimagelist-class.md#add) oder [Lesen](../mfc/reference/cimagelist-class.md#read) aufrufen.

- Ordnen Sie die Bildliste einem Steuerelement zu, indem Sie die entsprechende Memberfunktion dieses Steuerelements [Draw](../mfc/reference/cimagelist-class.md#draw) aufrufen, oder zeichnen Sie Bilder aus der Bildliste selbst mithilfe der Draw-Memberfunktion der Bildliste.

- Möglicherweise kann der Benutzer ein Bild ziehen, indem er die integrierte Unterstützung der Bildliste zum Ziehen verwendet.

> [!NOTE]
> Wenn die Bildliste mit dem **neuen** Operator `CImageList` erstellt wurde, müssen Sie das Objekt zerstören, wenn Sie damit fertig sind.

## <a name="see-also"></a>Siehe auch

[Verwenden von CImageList](../mfc/using-cimagelist.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
