---
title: Listenelemente und Bildlisten
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 14abf72551d39b2d1b2069bd17da308b39d7f6cc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621401"
---
# <a name="list-items-and-image-lists"></a>Listenelemente und Bildlisten

Ein "Item" in einem Listen Steuerelement ([CListCtrl](reference/clistctrl-class.md)) besteht aus einem Symbol, einer Bezeichnung und möglicherweise weiteren Informationen (in "SubItems").

Die Symbole für Listen Steuerungselemente sind in Bildlisten enthalten. Eine Bildliste enthält Symbole in voller Größe, die in der Symbol Ansicht verwendet werden. Eine zweite, optionale Bildliste enthält kleinere Versionen derselben Symbole für die Verwendung in anderen Ansichten des Steuer Elements. Eine dritte optionale Liste enthält Bilder mit dem Status "State" (z. b. Kontrollkästchen) für die Anzeige vor den kleinen Symbolen in bestimmten Ansichten. Eine vierte optionale Liste enthält Bilder, die in einzelnen Header Elementen des Listen Steuer Elements angezeigt werden.

> [!NOTE]
> Wenn ein Listenansicht-Steuerelement mit dem LVS_SHAREIMAGELISTS-Format erstellt wird, sind Sie dafür verantwortlich, die Bildlisten zu zerstören, wenn Sie nicht mehr verwendet werden. Geben Sie diesen Stil an, wenn Sie denselben Bildlisten mehrere Listenansicht-Steuerelemente zuweisen. Andernfalls können mehr als ein Steuerelement versuchen, dieselbe Bildliste zu zerstören.

Weitere Informationen zu Listenelementen finden Sie Unterlisten [Ansichts Bildlisten](/windows/win32/Controls/using-list-view-controls) und [Elemente und unter Elemente](/windows/win32/Controls/using-list-view-controls) in der Windows SDK. Siehe auch Klasse [CImageList](reference/cimagelist-class.md) in der *MFC-Referenz* und [Verwenden von CImageList](using-cimagelist.md) in dieser Artikel Familie.

Zum Erstellen eines Listen Steuer Elements müssen Sie Bildlisten bereitstellen, die verwendet werden sollen, wenn Sie neue Elemente in die Liste einfügen. Im folgenden Beispiel wird dieses Verfahren veranschaulicht, bei dem *m_pImagelist* ein Zeiger vom Typ `CImageList` und *m_listctrl* ein `CListCtrl` Datenmember ist.

[!code-cpp[NVC_MFCControlLadenDialog#19](codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Wenn Sie jedoch keine Symbole in der Listenansicht oder im Listen Steuerelement anzeigen möchten, benötigen Sie keine Bildlisten.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
