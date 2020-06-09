---
title: Erstellen des Headersteuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: b08dd4d3f12c70ae495b20b936d44f6a695d1ae1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616247"
---
# <a name="creating-the-header-control"></a>Erstellen des Headersteuerelements

Das Header Steuerelement ist im Dialog-Editor nicht direkt verfügbar (Sie können jedoch ein Listen Steuerelement hinzufügen, das ein Header Steuerelement enthält).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>So platzieren Sie ein Header-Steuerelement in einem Dialogfeld

1. Fügen Sie eine Member-Variable vom Typ " [CHeaderCtrl](reference/cheaderctrl-class.md) " manuell in die Dialogfeld Klasse ein.

1. Erstellen und legen Sie in [OnInitDialog](reference/cdialog-class.md#oninitdialog)die Stile für die fest `CHeaderCtrl` , positionieren Sie Sie, und zeigen Sie Sie an.

1. Fügen Sie dem Header Steuerelement Elemente hinzu.

1. Verwenden Sie den [Klassen-Assistenten](reference/mfc-class-wizard.md) , um Handlerfunktionen in der Dialogfeld Klasse für alle zu behandelnden Header-Steuerelement-Benachrichtigungs Meldungen zuzuordnen (Weitere Informationen finden Sie unterzuordnen [von Meldungen zu Funktionen](reference/mapping-messages-to-functions.md))

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>So platzieren Sie ein Header Steuerelement in einer Ansicht (keine CListView)

1. Betten Sie ein [CHeaderCtrl](reference/cheaderctrl-class.md) -Objekt in Ihre Ansichts Klasse ein.

1. Stil, Position und Anzeige des Header-Steuerelement Fensters in der [OnInitialUpdate](reference/cview-class.md#oninitialupdate) -Member-Funktion der Ansicht.

1. Fügen Sie dem Header Steuerelement Elemente hinzu.

1. Verwenden Sie den [Klassen-Assistenten](reference/mfc-class-wizard.md) , um Handlerfunktionen in der Ansichts Klasse für alle Header-Steuerelement-Benachrichtigungs Meldungen zuzuordnen, die Sie behandeln müssen (siehe zuordnen [von Meldungen zu Funktionen](reference/mapping-messages-to-functions.md)).

In beiden Fällen wird das eingebettete Steuerelement Objekt erstellt, wenn die Sicht oder das Dialog Objekt erstellt wird. Anschließend müssen Sie [CHeaderCtrl:: Create](reference/cheaderctrl-class.md#create) anrufen, um das Steuerelement Fenster zu erstellen. Um das Steuerelement zu positionieren, müssen Sie [CHeaderCtrl:: Layout](reference/cheaderctrl-class.md#layout) aufrufen, um die anfängliche Größe und Position des Steuer Elements zu bestimmen, und [SetWindowPos](reference/cwnd-class.md#setwindowpos) , um die gewünschte Position festzulegen. Fügen Sie dann Elemente hinzu, wie unter [Hinzufügen von Elementen zum Header Steuer](adding-items-to-the-header-control.md)Element beschrieben.

Weitere Informationen finden Sie unter [Erstellen eines Header Steuer](/windows/win32/Controls/header-controls) Elements in der Windows SDK.

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](using-cheaderctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
