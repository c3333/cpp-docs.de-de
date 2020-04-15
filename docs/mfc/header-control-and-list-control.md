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
ms.openlocfilehash: 53dd6f1a7878d82a7f7ac48dd7082d791323941b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370471"
---
# <a name="header-control-and-list-control"></a>Headersteuerelement und Listensteuerelement

In den meisten Fällen verwenden Sie das Headersteuerelement, das in ein [CListCtrl-](../mfc/reference/clistctrl-class.md) oder [CListView-Objekt](../mfc/reference/clistview-class.md) eingebettet ist. Es gibt jedoch Fälle, in denen ein separates Headersteuerelementobjekt wünschenswert ist, z. B. das Bearbeiten von Daten, die in Spalten oder Zeilen angeordnet sind, in einem [von CView](../mfc/reference/cview-class.md)abgeleiteten Objekt. In diesen Fällen benötigen Sie eine bessere Kontrolle über das Erscheinungsbild und das Standardverhalten eines eingebetteten Headersteuerelements.

In dem allgemeinen Fall, dass ein Headersteuerelement standard- und standardverhalten bereitstellen soll, können Sie stattdessen [CListCtrl](../mfc/reference/clistctrl-class.md) oder [CListView](../mfc/reference/clistview-class.md) verwenden. Verwenden `CListCtrl` Sie diese Option, wenn Sie die Funktionalität eines Standardheadersteuerelements verwenden möchten, das in ein allgemeines Steuerelement in der Listenansicht eingebettet werden soll. Verwenden Sie [CListView,](../mfc/reference/clistview-class.md) wenn Sie die Funktionalität eines Standardheadersteuerelements benötigen, das in ein Ansichtsobjekt eingebettet werden soll.

> [!NOTE]
> Diese Steuerelemente enthalten nur dann ein integriertes Headersteuerelement, wenn das Listenansichtssteuerelement mit dem **Stil LVS_REPORT** erstellt wird.

In den meisten Fällen kann die Darstellung des eingebetteten Headersteuerelements geändert werden, indem die Stile des enthaltenden Listenansichtssteuerelements geändert werden. Darüber hinaus können Informationen über das Headersteuerelement über Memberfunktionen des übergeordneten Listenansichtssteuerelements abgerufen werden. Für die vollständige Steuerung und den Zugriff auf die Attribute und Stile des eingebetteten Headersteuerelements wird jedoch empfohlen, einen Zeiger auf das Headersteuerelement abrufe.

Auf das eingebettete Header-Steuerelementobjekt kann entweder oder `CListCtrl` `CListView` mit `GetHeaderCtrl` einem Aufruf an die Memberfunktion der jeweiligen Klasse zugegriffen werden. Dies veranschaulicht der folgende Code:

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Verwenden von Bildlisten mit Headersteuerelementen](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
