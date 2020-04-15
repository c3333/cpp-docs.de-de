---
title: Ändern der Stile von Listensteuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 5f45e0549c3fc0f5747f8dd12a6310fafd7dd7bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370816"
---
# <a name="changing-list-control-styles"></a>Ändern der Stile von Listensteuerelementen

Sie können den Fensterstil eines Listensteuerelements ([CListCtrl](../mfc/reference/clistctrl-class.md)) jederzeit nach dem Erstellen ändern. Durch Ändern des Fensterstils ändern Sie die Art der Ansicht, die das Steuerelement verwendet. Um beispielsweise den Explorer zu emulieren, können Sie Menüelemente oder Symbolleistenschaltflächen zum Wechseln des Steuerelements zwischen verschiedenen Ansichten angeben: Symbolansicht, Listenansicht usw.

Wenn der Benutzer beispielsweise Ihr Menüelement auswählt, können Sie [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) aufrufen, um den aktuellen Stil des Steuerelements abzurufen, und dann [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) aufrufen, um den Stil zurückzusetzen. Weitere Informationen finden Sie unter [Verwenden von Listenansichtssteuerelementen](/windows/win32/Controls/using-list-view-controls) im Windows SDK.

Verfügbare Stile werden unter [Erstellen](../mfc/reference/clistctrl-class.md#create)von aufgeführt. Die Stile **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**und **LVS_REPORT** die vier Listensteuerelementansichten festlegen.

## <a name="extended-styles"></a>Erweiterte Stile

Zusätzlich zu den Standardformatvorlagen für ein Listensteuerelement gibt es einen weiteren Satz, der als erweiterte Stile bezeichnet wird. Diese Stile, die in [erweiterten Listenansichtsstilen](/windows/win32/Controls/extended-list-view-styles) im Windows SDK erläutert werden, bieten eine Vielzahl nützlicher Features, die das Verhalten des Listensteuerelements anpassen. Um das Verhalten eines bestimmten Stils (z. B. Hoverauswahl) zu implementieren, rufen Sie [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle)auf, um den erforderlichen Stil zu übergeben. Das folgende Beispiel veranschaulicht den Funktionsaufruf:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> Damit die Hoverauswahl funktioniert, müssen Sie auch **entweder LVS_EX_ONECLICKACTIVATE** oder **LVS_EX_TWOCLICKACTIVATE** aktiviert haben.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](../mfc/using-clistctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
