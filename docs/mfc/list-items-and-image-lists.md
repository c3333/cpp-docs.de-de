---
title: Listenelemente und Bildlisten
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: d378c6e07280349f9995981ad794039ebc015b25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353048"
---
# <a name="list-items-and-image-lists"></a>Listenelemente und Bildlisten

Ein "Element" in einem Listensteuerelement ([CListCtrl](../mfc/reference/clistctrl-class.md)) besteht aus einem Symbol, einer Beschriftung und möglicherweise anderen Informationen (in "Unterpositionen").

Die Symbole für Listensteuerelemente sind in Bildlisten enthalten. Eine Bildliste enthält Symbole in voller Größe, die in der Symbolansicht verwendet werden. Eine zweite, optionale Bildliste enthält kleinere Versionen derselben Symbole für die Verwendung in anderen Ansichten des Steuerelements. Eine dritte optionale Liste enthält "Zustandsbilder", z. B. Kontrollkästchen, um sie vor den kleinen Symbolen in bestimmten Ansichten anzuzeigen. Eine vierte optionale Liste enthält Bilder, die in einzelnen Kopfzeilenelementen des Listensteuerelements angezeigt werden.

> [!NOTE]
> Wenn ein Listenansichtssteuerelement mit dem stilLVS_SHAREIMAGELISTS erstellt wird, sind Sie dafür verantwortlich, die Bildlisten zu zerstören, wenn sie nicht mehr verwendet werden. Geben Sie diesen Stil an, wenn Sie denselben Bildlisten mehreren Listenansichtssteuerelementen zuweisen. Andernfalls könnte mehr als ein Steuerelement versuchen, dieselbe Bildliste zu zerstören.

Weitere Informationen zu Listenelementen finden Sie unter [Listenansicht von Bildlisten](/windows/win32/Controls/using-list-view-controls) und [Elementen und Unterelementen](/windows/win32/Controls/using-list-view-controls) im Windows SDK. Siehe auch Klasse [CImageList](../mfc/reference/cimagelist-class.md) in der *MFC-Referenz* und [Verwenden von CImageList](../mfc/using-cimagelist.md) in dieser Artikelfamilie.

Um ein Listensteuerelement zu erstellen, müssen Sie Bildlisten angeben, die beim Einfügen neuer Elemente in die Liste verwendet werden sollen. Im folgenden Beispiel wird *m_pImagelist* dieses Verfahren veranschaulicht, `CImageList` wobei m_pImagelist ein Zeiger des Typs und *m_listctrl* ein `CListCtrl` Datenmember ist.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Wenn Sie jedoch nicht beabsichtigen, Symbole in der Listenansicht oder im Listensteuerelement anzuzeigen, benötigen Sie keine Bildlisten.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](../mfc/using-clistctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
