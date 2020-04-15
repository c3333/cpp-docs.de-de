---
title: 'Zwischenablage: Hinzufügen anderer Formate'
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 6f4e159cc1b6918843d4a164dcca88500eb7b038
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374607"
---
# <a name="clipboard-adding-other-formats"></a>Zwischenablage: Hinzufügen anderer Formate

In diesem Thema wird erläutert, wie Sie die Liste der unterstützten Formate erweitern, insbesondere für die OLE-Unterstützung. Das Thema [Zwischenablage: Kopieren und Einfügen von Daten](../mfc/clipboard-copying-and-pasting-data.md) beschreibt die minimale Implementierung, die erforderlich ist, um das Kopieren und Einfügen aus der Zwischenablage zu unterstützen. Wenn dies alles ist, was Sie implementieren, sind die einzigen Formate, die in der Zwischenablage platziert **werden, CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**und möglicherweise **CF_LINKSOURCE**. Die meisten Anwendungen benötigen mehr Formate in der Zwischenablage als diese drei.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Registrieren benutzerdefinierter Formate

Um eigene benutzerdefinierte Formate zu erstellen, gehen Sie wie folgt vor, wie Sie es beim Registrieren eines benutzerdefinierten Zwischenablageformats verwenden würden: Übergeben Sie den Namen des Formats an die **Funktion RegisterClipboardFormat,** und verwenden Sie den Rückgabewert als Format-ID.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Platzieren von Formaten in der Zwischenablage

Um den in der Zwischenablage platzierten Formaten `OnGetClipboardData` weitere Formate hinzuzufügen, `COleClientItem` `COleServerItem` müssen Sie die Funktion in der Klasse überschreiben, von der Sie entweder abgeleitet haben oder (je nachdem, ob die zu kopierenden Daten systemisch sind). In dieser Funktion sollten Sie das folgende Verfahren verwenden.

#### <a name="to-place-formats-on-the-clipboard"></a>So platzieren Sie Formate in der Zwischenablage

1. Erstellen eines `COleDataSource`-Objekts

1. Übergeben Sie diese Datenquelle an eine Funktion, die Ihre systemeigenen `COleDataSource::CacheGlobalData`Datenformate zur Liste der unterstützten Formate hinzufügt, indem Sie aufrufen.

1. Fügen Sie Standardformate hinzu, indem Sie für jedes Standardformat aufrufen, `COleDataSource::CacheGlobalData` das Sie unterstützen möchten.

Diese Technik wird im MFC OLE-Beispielprogramm [HIERSVR](../overview/visual-cpp-samples.md) (Untersuchung der `OnGetClipboardData` Memberfunktion der **CServerItem-Klasse)** verwendet. Der einzige Unterschied in diesem Beispiel besteht darin, dass Schritt drei nicht implementiert ist, da HIERSVR keine anderen Standardformate unterstützt.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [OLE-Datenobjekte und Datenquellen und gleichmäßige Datenübertragung](../mfc/data-objects-and-data-sources-ole.md)

- [Drag &amp; Drop (OLE)](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Siehe auch

[Zwischenablage: Verwenden des OLE-Zwischenablagemechanismus](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
