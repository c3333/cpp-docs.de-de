---
title: Festlegen des CStatusBarCtrl-Objektmodus
ms.date: 11/04/2016
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: 79b499533196447898ce62ea9dc86c1674fc0302
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446430"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Festlegen des CStatusBarCtrl-Objektmodus

Es gibt zwei Modi für ein `CStatusBarCtrl` Objekt: einfach und nicht einfach. In den meisten Fällen weist das StatusBar-Steuerelement einen oder mehrere Teile sowie Text und möglicherweise ein Symbol oder ein Symbol auf. Dies wird als nicht einfacher Modus bezeichnet. Weitere Informationen zu diesem Modus finden Sie unter [Initialisieren der Teile eines cstatus-barctrl-Objekts](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Es gibt jedoch Fälle, in denen Sie nur eine einzelne Textzeile anzeigen müssen. In diesem Fall ist der einfache Modus für Ihre Bedürfnisse ausreichend. Um den Modus des `CStatusBarCtrl` Objekts in Simple zu ändern, führen Sie einen Aufrufen der [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) -Member-Funktion aus. Wenn sich das StatusBar-Steuerelement im einfachen Modus befindet, legen Sie den Text fest, indem Sie die `SetText` Member-Funktion aufrufen und 255 als Wert für den *npane* -Parameter übergeben.

Sie können die [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) -Funktion verwenden, um zu bestimmen, in welchem Modus sich das `CStatusBarCtrl` Objekt befindet.

> [!NOTE]
>  Wenn das Status leisten Objekt von nicht einfache in Simple geändert wird (oder umgekehrt), wird das Fenster sofort neu gezeichnet, und ggf. werden alle definierten Teile automatisch wieder hergestellt.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
