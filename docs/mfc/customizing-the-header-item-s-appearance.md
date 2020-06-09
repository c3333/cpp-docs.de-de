---
title: Anpassen der Darstellung des Header Elements&#39;s
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 8bf1bdad6a0408746b50b6b0dcbecbce308f5ede
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617092"
---
# <a name="customizing-the-header-item39s-appearance"></a>Anpassen der Darstellung des Header Elements&#39;s

Wenn Sie den *dwstyle* -Parameter festlegen, wenn Sie erstmalig ein Header Steuerelement erstellen ([CHeaderCtrl:: Create](reference/cheaderctrl-class.md#create)), können Sie die Darstellung und das Verhalten von Header Elementen oder dem Header Steuerelement selbst definieren.

Im folgenden finden Sie eine Stichprobe der Stile, die Sie festlegen können, und deren Zweck:

- Wenn ein Header Element wie ein PUSHBUTTON aussehen soll, verwenden Sie den **HDS_BUTTONS** Stil.

   Verwenden Sie dieses Format, wenn Sie Aktionen als Reaktion auf Mausklicks für ein Header Element ausführen möchten, z. b. das Sortieren von Daten nach einer bestimmten Spalte, wie dies in Microsoft Outlook der Fall ist.

- Um dem Header Elemente eine "Hot Tracking"-Darstellung zu übergeben, wenn der Mauszeiger darüber bewegt wird, verwenden Sie den **HDS_HOTTRACK** Stil.

   Bei der aktiven Nachverfolgung wird eine 3D-Gliederung angezeigt, während der Zeiger über ein Element in einem andernfalls flachen Balken verläuft.

- Verwenden Sie den **HDS_HIDDEN** Stil, um anzugeben, dass das Header Steuerelement ausgeblendet werden soll.

   Der **HDS_HIDDEN** Stil gibt an, dass das Header Steuerelement als Datencontainer und nicht als visuelles Steuerelement verwendet werden soll. Dieser Stil verbirgt das Steuerelement nicht automatisch, sondern wirkt sich stattdessen auf das Verhalten von aus `CHeaderCtrl::Layout` . Der im *CY* -Member der-Struktur zurückgegebene Wert ist `WINDOWPOS` 0 (null), um anzugeben, dass das Steuerelement für den Benutzer nicht sichtbar sein soll.

Weitere Informationen zu diesen Eigenschaften finden Sie unter [Items](/windows/win32/Controls/header-controls) in the Windows SDK. Weitere Informationen zum Hinzufügen von Elementen zu einem Header Steuerelement finden [Sie unter Hinzufügen von Elementen zum Header Steuer](adding-items-to-the-header-control.md)Element.

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](using-cheaderctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
