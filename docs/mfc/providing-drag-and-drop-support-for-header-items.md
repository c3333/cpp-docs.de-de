---
title: Bereitstellen von Drag &amp; Drop-Unterstützung für Headerelemente
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 8dfaabf3da62c216d3da662f59c57b63e695d9ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371166"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Bereitstellen von Drag &amp; Drop-Unterstützung für Headerelemente

Um Drag-and-Drop-Unterstützung für Kopfzeilen elemente bereitzustellen, geben Sie den stil HDS_DRAGDROP an. Drag-and-Drop-Unterstützung für Kopfzeilenelemente gibt dem Benutzer die Möglichkeit, die Kopfzeilenelemente eines Headersteuerelements neu anzuordnen. Das Standardverhalten stellt ein halbtransparentes Ziehbild des gezogenen Kopfelements und einen visuellen Indikator für die neue Position bereit, wenn das Kopfelement gelöscht wird.

Wie bei der üblichen Drag-and-Drop-Funktionalität können Sie das standardmäßige Drag-and-Drop-Verhalten erweitern, indem Sie die HDN_BEGINDRAG und HDN_ENDDRAG Benachrichtigungen verarbeiten. Sie können auch die Darstellung des Ziehbilds anpassen, indem Sie die [Abrichtfunktion CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) überschreiben.

> [!NOTE]
> Wenn Sie Drag-and-Drop-Unterstützung für ein eingebettetes Headersteuerelement in einem Listensteuerelement bereitstellen, lesen Sie den Abschnitt Erweiterter Stil im Thema Ändern von [Listensteuerungsstilen.](../mfc/changing-list-control-styles.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von CHeaderCtrl](../mfc/using-cheaderctrl.md)
