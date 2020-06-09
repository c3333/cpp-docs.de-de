---
title: Headersteuerelement und Listensteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: f9dd34b27ddbdc0b99fafbb23ad1cf9782d98605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626416"
---
# <a name="header-control-and-list-control"></a>Headersteuerelement und Listensteuerelement

In den meisten Fällen verwenden Sie das Header Steuerelement, das in einem [CListCtrl](reference/clistctrl-class.md) -oder [CListView](reference/clistview-class.md) -Objekt eingebettet ist. Es gibt jedoch Fälle, in denen ein separates Header Steuerelement Objekt wünschenswert ist, z. b. das Bearbeiten von Daten in Spalten oder Zeilen in einem von [CView](reference/cview-class.md)abgeleiteten Objekt. In diesen Fällen benötigen Sie eine bessere Kontrolle über die Darstellung und das Standardverhalten eines eingebetteten Header Steuer Elements.

Wenn Sie möchten, dass ein Header Steuerelement Standard, Standardverhalten bereitstellt, können Sie stattdessen [CListCtrl](reference/clistctrl-class.md) oder [CListView](reference/clistview-class.md) verwenden. Verwenden `CListCtrl` Sie, wenn Sie die Funktionalität eines Standard Header-Steuer Elements verwenden möchten, das in ein häufig verwendeter Listenansicht eingebettet ist. Verwenden Sie [CListView](reference/clistview-class.md) , wenn Sie die Funktionalität eines Standard Header-Steuer Elements verwenden möchten, das in ein Ansichts Objekt eingebettet ist.

> [!NOTE]
> Diese Steuerelemente enthalten nur ein integriertes Header Steuerelement, wenn das Listenansicht-Steuerelement mithilfe des **LVS_REPORT** Stils erstellt wird.

In den meisten Fällen kann die Darstellung des eingebetteten Header Steuer Elements geändert werden, indem die Stile des enthaltenden Listenansicht-Steuer Elements geändert werden. Darüber hinaus können Informationen über das Header Steuerelement über Element Funktionen des übergeordneten Listenansicht-Steuer Elements abgerufen werden. Für die umfassende Kontrolle und den Zugriff auf die Attribute und Stile des eingebetteten Header Steuer Elements wird jedoch empfohlen, einen Zeiger auf das Header Steuerelement-Objekt zu erhalten.

Der Zugriff auf das eingebettete Header Steuerelement Objekt ist entweder von `CListCtrl` oder `CListView` mit einem Aufrufen der Member-Funktion der jeweiligen Klasse möglich `GetHeaderCtrl` . Dies veranschaulicht der folgende Code:

[!code-cpp[NVC_MFCControlLadenDialog#14](codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Verwenden von Bildlisten mit Header Steuerelementen](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](using-cheaderctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
