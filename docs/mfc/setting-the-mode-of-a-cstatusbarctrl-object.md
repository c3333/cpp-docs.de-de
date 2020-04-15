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
ms.openlocfilehash: e09a7bd274c44df2da48bbc007a95802fadd8cf0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365420"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Festlegen des CStatusBarCtrl-Objektmodus

Es gibt zwei Modi `CStatusBarCtrl` für ein Objekt: einfach und nicht einfach. In den meisten Fällen besteht das Steuerelement der Statusleiste aus einem oder mehreren Teilen, zusammen mit Text und möglicherweise einem Symbol oder Symbolen. Dies wird als nicht einfacher Modus bezeichnet. Weitere Informationen zu diesem Modus finden Sie unter [Initialisieren der Teile eines CStatusBarCtrl-Objekts](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Es gibt jedoch Fälle, in denen Sie nur eine einzelne Textzeile anzeigen müssen. In diesem Fall ist der einfache Modus ausreichend für Ihre Bedürfnisse. Um den Modus `CStatusBarCtrl` des Objekts in einfach zu ändern, rufen Sie die [SetSimple-Memberfunktion](../mfc/reference/cstatusbarctrl-class.md#setsimple) auf. Sobald sich das Statusleistensteuerelement im einfachen Modus `SetText` befindet, legen Sie den Text fest, indem Sie die Memberfunktion aufrufen und 255 als Wert für den *nPane-Parameter* übergeben.

Sie können die [IsSimple-Funktion](../mfc/reference/cstatusbarctrl-class.md#issimple) verwenden, um zu bestimmen, in welchem Modus sich das `CStatusBarCtrl` Objekt befindet.

> [!NOTE]
> Wenn das Statusleistenobjekt von nicht einfach in einfach oder umgekehrt geändert wird, wird das Fenster sofort neu gezeichnet, und ggf. werden alle definierten Teile automatisch wiederhergestellt.

## <a name="see-also"></a>Siehe auch

[Verwenden von CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
