---
title: Einstellungen für CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: 18c4c780ecf7865d8d648bfa4c54961bbffe7b18
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446386"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Einstellungen für CStatusBarCtrl

Die Standardposition eines [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) -Status Fensters befindet sich am unteren Rand des übergeordneten Fensters, Sie können jedoch den CCS_TOP Stil angeben, damit er am oberen Rand des Client Bereichs des übergeordneten Fensters angezeigt wird.

Sie können den SBARS_SIZEGRIP Stil angeben, um einen Größen Zieh Punkt am rechten Ende des Fensters "`CStatusBarCtrl` Status" einzuschließen. Ein Größen Zieh Punkt ähnelt einem Größen Anpassungsrahmen. Es ist ein rechteckiger Bereich, auf den der Benutzer klicken und ziehen kann, um die Größe des übergeordneten Fensters zu ändern.

> [!NOTE]
>  Wenn Sie die CCS_TOP-und SBARS_SIZEGRIP Stile kombinieren, ist der resultierende Größen Zieh Punkt nicht funktionsfähig, auch wenn das System ihn im Statusfenster zeichnet.

Die Fenster Prozedur für das Statusfenster legt automatisch die anfängliche Größe und Position des Steuerelement Fensters fest. Die Breite ist mit der Breite des Client Bereichs des übergeordneten Fensters identisch. Die Höhe basiert auf den Metriken der Schriftart, die derzeit im Gerätekontext des Status Fensters und in der Breite der Fensterränder ausgewählt ist.

Die Fenster Prozedur passt automatisch die Größe des Status Fensters an, wenn eine WM_SIZE Nachricht empfangen wird. Wenn sich die Größe des übergeordneten Fensters ändert, sendet das übergeordnete Fenster in der Regel eine WM_SIZE Meldung an das Statusfenster.

Sie können die Mindesthöhe des Zeichnungs Bereichs eines Status Fensters festlegen, indem Sie [setMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)aufrufen und dabei die Mindesthöhe in Pixel angeben. Der Zeichenbereich schließt die Rahmen des Fensters nicht ein.

Sie rufen die breiten der Rahmen eines Status Fensters durch Aufrufen von [getrahmens](../mfc/reference/cstatusbarctrl-class.md#getborders)ab. Diese Member-Funktion schließt den Zeiger auf ein Array mit drei Elementen ein, das die Breite des horizontalen Rahmens, den vertikalen Rahmen und den Rahmen zwischen Rechtecke empfängt.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrollen](../mfc/controls-mfc.md)
