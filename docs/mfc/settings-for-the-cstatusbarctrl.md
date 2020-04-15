---
title: Einstellungen für CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: dd7c68d6721c48f751c04437e43c8770f6ec5736
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365379"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Einstellungen für CStatusBarCtrl

Die Standardposition eines [CStatusBarCtrl-Statusfensters](../mfc/reference/cstatusbarctrl-class.md) befindet sich am unteren Rand des übergeordneten Fensters, Sie können jedoch den CCS_TOP-Stil angeben, damit er oben im Clientbereich des übergeordneten Fensters angezeigt wird.

Sie können den SBARS_SIZEGRIP-Stil angeben, der einen Größengriff am rechten Ende des `CStatusBarCtrl` Statusfensters einschließen soll. Ein Größengriff ähnelt einem Größenrahmen. Es handelt sich um einen rechteckigen Bereich, auf den der Benutzer klicken und ziehen kann, um die Größe des übergeordneten Fensters zu ändern.

> [!NOTE]
> Wenn Sie die CCS_TOP- und SBARS_SIZEGRIP-Stile kombinieren, ist der resultierende Größengriff nicht funktionsfähig, obwohl das System ihn im Statusfenster zeichnet.

Die Fensterprozedur für das Statusfenster legt automatisch die Anfangsgröße und Position des Steuerfensters fest. Die Breite entspricht der des Clientbereichs des übergeordneten Fensters. Die Höhe basiert auf den Metriken der Schriftart, die derzeit im Gerätekontext des Statusfensters ausgewählt ist, und auf der Breite der Ränder des Fensters.

Die Fensterprozedur passt automatisch die Größe des Statusfensters an, wenn eine WM_SIZE Nachricht empfängt wird. Wenn sich die Größe des übergeordneten Fensters ändert, sendet das übergeordnete Element in der Regel eine WM_SIZE Nachricht an das Statusfenster.

Sie können die minimale Höhe des Zeichenbereichs eines Statusfensters festlegen, indem Sie [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)aufrufen und die minimale Höhe in Pixel angeben. Der Zeichenbereich enthält nicht die Ränder des Fensters.

Sie rufen die Breiten der Ränder eines Statusfensters ab, indem Sie [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders)aufrufen. Diese Memberfunktion enthält den Zeiger auf ein Array mit drei Elementen, das die Breite des horizontalen Rahmens, den vertikalen Rahmen und den Rahmen zwischen Rechtecken empfängt.

## <a name="see-also"></a>Siehe auch

[Verwenden von CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
