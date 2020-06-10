---
title: Anordnen von Elementen im Headersteuerelement
ms.date: 11/04/2016
f1_keywords:
- DS_DRAGDROP
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
ms.openlocfilehash: c4b4711729c6c3a4b63d4ad05252a5c49df98a0c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622136"
---
# <a name="ordering-items-in-the-header-control"></a>Anordnen von Elementen im Headersteuerelement

Nachdem Sie [einem Header Steuerelement Elemente hinzugefügt](adding-items-to-the-header-control.md)haben, können Sie mit den folgenden Funktionen Informationen zu Ihrer Bestellung bearbeiten oder erhalten:

- [CHeaderCtrl:: getor Array](reference/cheaderctrl-class.md#getorderarray) und [CHeaderCtrl:: abderarray](reference/cheaderctrl-class.md#setorderarray)

   Ruft die Reihenfolge der Header Elemente von links nach rechts ab und legt Sie fest.

- [CHeaderCtrl:: orderto Index](reference/cheaderctrl-class.md#ordertoindex).

   Ruft den Indexwert für ein bestimmtes Header Element ab.

Zusätzlich zu den vorherigen Member-Funktionen ermöglicht das HDS_DRAGDROP Format dem Benutzer das ziehen und Ablegen von Header Elementen innerhalb des Header Steuer Elements. Weitere Informationen finden Sie [unter Bereitstellen von Drag & Drop-Unterstützung für Header Elemente](providing-drag-and-drop-support-for-header-items.md).

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](using-cheaderctrl.md)
