---
title: Zerstören des Listensteuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: d128a613a2a4cb595f362f843a5ae2eba830e538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621901"
---
# <a name="destroying-the-list-control"></a>Zerstören des Listensteuerelements

Wenn Sie das [CListCtrl](reference/clistctrl-class.md) -Objekt als Datenmember einer Sicht oder Dialogfeld Klasse einbetten, wird es zerstört, wenn der Besitzer zerstört wird. Wenn Sie eine [CListView](reference/clistview-class.md)verwenden, zerstört das Framework das Steuerelement, wenn es die Ansicht zerstört.

Wenn Sie festlegen, dass einige der Listen Daten in der Anwendung und nicht im Listen Steuerelement gespeichert werden sollen, müssen Sie die Aufhebung der Zuordnung anordnen. Weitere Informationen finden Sie unter [Rückruf Elemente und Rückruf Maske](/windows/win32/Controls/using-list-view-controls) in der Windows SDK.

Außerdem sind Sie verantwortlich für das Aufheben der Zuordnung von Image Listen, die Sie erstellt und mit dem Listen Steuerelement-Objekt verknüpft haben.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
