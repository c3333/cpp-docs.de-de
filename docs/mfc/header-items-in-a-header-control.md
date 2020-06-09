---
title: Headerelemente in einem Headersteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
ms.openlocfilehash: a70d1d9225d2ac8ef2f7ed3ad9f603a64a937bc7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620088"
---
# <a name="header-items-in-a-header-control"></a>Headerelemente in einem Headersteuerelement

Sie haben eine beträchtliche Kontrolle über die Darstellung und das Verhalten der Header Elemente, die ein Header Steuerelement bilden ([CHeaderCtrl](reference/cheaderctrl-class.md)). Jedes Header Element kann eine Zeichenfolge, ein bitzugeordnetes Bild, ein Bild aus einer zugeordneten Bildliste oder einen Anwendungs definierten 32-Bit-Wert aufweisen. Die Zeichenfolge, die Bitmap oder das Bild werden im Header Element angezeigt.

Sie können die Darstellung und den Inhalt neuer Elemente anpassen, wenn Sie erstellt werden, indem Sie einen [callcheaderctrl:: InsertItem](reference/cheaderctrl-class.md#insertitem) aufrufen oder ein vorhandenes Element ändern, indem Sie den Befehl " [CHeaderCtrl:: GetItem](reference/cheaderctrl-class.md#getitem) " und " [CHeaderCtrl:: abtitem](reference/cheaderctrl-class.md#setitem)" aufrufen.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Anpassen der Darstellung des Header Elements](customizing-the-header-item-s-appearance.md)

- [Anordnen von Elementen im Headersteuerelement](ordering-items-in-the-header-control.md)

- [Bereitstellen von Drag & Drop-Unterstützung für die Header Elemente](providing-drag-and-drop-support-for-header-items.md)

- [Verwenden von Bildlisten mit Header Steuerelementen](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](using-cheaderctrl.md)
