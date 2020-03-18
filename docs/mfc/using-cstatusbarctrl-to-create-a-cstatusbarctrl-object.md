---
title: Verwenden von CStatusBarCtrl zum Erstellen eines CStatusBarCtrl-Objekts
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 12d5664b9fc59c4569ec2ee7db4ae883911f7bcd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442380"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Verwenden von CStatusBarCtrl zum Erstellen eines CStatusBarCtrl-Objekts

Im folgenden finden Sie ein Beispiel für eine typische Verwendung von [cstatus-barstrg](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>So verwenden Sie ein StatusBar-Steuerelement mit Teilen

1. Erstellen Sie das `CStatusBarCtrl`-Objekt.

1. Aufrufen von [setMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) , wenn Sie die Mindesthöhe des Zeichnungs Bereichs des StatusBar-Steuer Elements festlegen möchten.

1. Aufrufen von [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) zum Festlegen der Hintergrundfarbe des StatusBar-Steuer Elements.

1. Aufrufen von [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) zum Festlegen der Anzahl der Teile in einem StatusBar-Steuerelement und der Koordinate des rechten Rands der einzelnen Teile.

1. Aufrufen von [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) , um den Text in einem bestimmten Teil des Status leisten-Steuer Elements festzulegen. Die Meldung erklärt den Teil des Steuer Elements für ungültig, der geändert wurde, sodass der neue Text angezeigt wird, wenn das Steuerelement das nächste Mal die WM_PAINT Nachricht empfängt.

In einigen Fällen muss in der Statusleiste nur eine Textzeile angezeigt werden. Führen Sie in diesem Fall einen aufzurufenden [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)-Befehl aus. Dadurch wird das StatusBar-Steuerelement in den "einfachen" Modus versetzt, in dem eine einzelne Textzeile angezeigt wird.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
