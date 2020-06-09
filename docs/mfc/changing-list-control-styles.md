---
title: Ändern der Stile von Listensteuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: e515f56f00aa45a14c24bcd635770e803f7f8e70
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615989"
---
# <a name="changing-list-control-styles"></a>Ändern der Stile von Listensteuerelementen

Sie können den Fenster Stil eines Listen Steuer Elements ([CListCtrl](reference/clistctrl-class.md)) jederzeit ändern, nachdem Sie es erstellt haben. Durch Ändern des Fenster Stils ändern Sie die Art der Ansicht, die vom Steuerelement verwendet wird. Wenn Sie z. b. den Explorer emulieren möchten, können Sie Menü Elemente oder Symbolleisten Schaltflächen angeben, um das Steuerelement zwischen verschiedenen Ansichten zu wechseln: Symbol Ansicht, Listenansicht usw.

Wenn der Benutzer z. b. das Menü Element auswählt, können Sie [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) aufrufen, um den aktuellen Stil des Steuer Elements abzurufen, und dann [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) aufrufen, um den Stil zurückzusetzen. Weitere Informationen finden Sie unter [Verwenden von Listenansicht](/windows/win32/Controls/using-list-view-controls) -Steuerelementen in der Windows SDK.

Verfügbare Stile sind unter [Erstellen](reference/clistctrl-class.md#create)aufgeführt. Die Stile **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**und **LVS_REPORT** bestimmen die vier Listen Steuerelement Ansichten.

## <a name="extended-styles"></a>Erweiterte Stile

Zusätzlich zu den Standard Stilen für ein Listen Steuerelement gibt es eine andere Gruppe, die als erweiterte Stile bezeichnet wird. Diese Stile, die unter [Erweiterte Listen Ansichts Stile](/windows/win32/Controls/extended-list-view-styles) in der Windows SDK erläutert werden, bieten eine Vielzahl nützlicher Features, die das Verhalten des Listen Steuer Elements anpassen. Um das Verhalten eines bestimmten Stils (z. b. die Auswahl des Mauszeigers) zu implementieren, führen Sie [CListCtrl:: abtextendedstyle](reference/clistctrl-class.md#setextendedstyle)aus, und übergeben Sie dabei den erforderlichen Stil. Das folgende Beispiel veranschaulicht den Funktions aufzurufen:

[!code-cpp[NVC_MFCControlLadenDialog#22](codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> Damit die Hover-Auswahl funktioniert, müssen Sie auch entweder **LVS_EX_ONECLICKACTIVATE** oder **LVS_EX_TWOCLICKACTIVATE** aktiviert haben.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
