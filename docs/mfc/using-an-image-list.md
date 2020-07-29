---
title: Verwenden einer Bildliste
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 710831ea8ef6b52292ba3e8eb84a69575c6c7508
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226827"
---
# <a name="using-an-image-list"></a>Verwenden einer Bildliste

Die typische Verwendung einer Bildliste folgt dem folgenden Muster:

- Erstellen Sie ein [CImageList](../mfc/reference/cimagelist-class.md) -Objekt, und rufen Sie eine der über Ladungen der [Create](../mfc/reference/cimagelist-class.md#create) -Funktion auf, um eine Bildliste zu erstellen und Sie an das-Objekt anzufügen `CImageList` .

- Wenn Sie beim Erstellen der Bildliste keine Images hinzugefügt haben, fügen Sie der Bildliste Bilder hinzu, indem Sie die [Add](../mfc/reference/cimagelist-class.md#add) -oder [Read](../mfc/reference/cimagelist-class.md#read) Member-Funktion aufrufen.

- Ordnen Sie die Bildliste einem Steuerelement zu, indem Sie die entsprechende Member-Funktion des Steuer Elements aufrufen, oder zeichnen Sie Bilder aus der Bildliste selbst mithilfe der [Draw](../mfc/reference/cimagelist-class.md#draw) -Member-Funktion der Bildliste.

- Ermöglicht es dem Benutzer möglicherweise, ein Bild mithilfe der integrierten Unterstützung der Bildliste für das ziehen zu ziehen.

> [!NOTE]
> Wenn die Bildliste mit dem-Operator erstellt wurde **`new`** , müssen Sie das-Objekt zerstören, `CImageList` Wenn Sie damit abgeschlossen sind.

## <a name="see-also"></a>Siehe auch

[Verwenden von CImageList](../mfc/using-cimagelist.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
