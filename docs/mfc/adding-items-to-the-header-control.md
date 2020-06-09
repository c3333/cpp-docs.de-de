---
title: Hinzufügen von Elementen zum Headersteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 5749a0cae2dfe7e6c9f4c166eca487e36c2d21d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616467"
---
# <a name="adding-items-to-the-header-control"></a>Hinzufügen von Elementen zum Headersteuerelement

Nachdem Sie das Header Steuerelement ([CHeaderCtrl](reference/cheaderctrl-class.md)) in seinem übergeordneten Fenster erstellt haben, fügen Sie beliebig viele "Header Elemente" hinzu, wie Sie benötigen: normalerweise eine pro Spalte.

### <a name="to-add-a-header-item"></a>So fügen Sie ein Header Element hinzu

1. Bereiten Sie eine [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) Struktur vor.

1. Ruft [CHeaderCtrl:: InsertItem](reference/cheaderctrl-class.md#insertitem)auf und übergibt die Struktur.

1. Wiederholen Sie die Schritte 1 und 2 für weitere Elemente.

Weitere Informationen finden Sie unter [Hinzufügen eines Elements zu einem Header-Steuerelement](/windows/win32/Controls/header-controls) in der Windows SDK.

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](using-cheaderctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
