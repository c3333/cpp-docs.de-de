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
ms.openlocfilehash: 52089364a6be423c69a7031cd0d99e1924de1444
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626062"
---
# <a name="clipboard-adding-other-formats"></a>Zwischenablage: Hinzufügen anderer Formate

In diesem Thema wird erläutert, wie Sie die Liste der unterstützten Formate erweitern, insbesondere für die OLE-Unterstützung. Im Thema [Zwischenablage: Kopieren und Einfügen von Daten](clipboard-copying-and-pasting-data.md) wird die minimale Implementierung beschrieben, die zum unterstützen von kopieren und Einfügen aus der Zwischenablage erforderlich ist. Wenn Sie alle implementieren, sind die einzigen Formate, die in der Zwischenablage platziert werden, **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**und möglicherweise **CF_LINKSOURCE**. Die meisten Anwendungen benötigen mehr Formate in der Zwischenablage als diese drei.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Registrieren von benutzerdefinierten Formaten

Um eigene benutzerdefinierte Formate zu erstellen, befolgen Sie die gleiche Vorgehensweise wie beim Registrieren eines benutzerdefinierten Zwischenablage Formats: übergeben Sie den Namen des Formats an die **RegisterClipboardFormat** -Funktion, und verwenden Sie den Rückgabewert als Format-ID.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Platzieren von Formaten in der Zwischenablage

Wenn Sie in der Zwischenablage weitere Formate hinzufügen möchten, müssen Sie die `OnGetClipboardData` Funktion in der Klasse überschreiben, die Sie von oder abgeleitet haben `COleClientItem` `COleServerItem` (abhängig davon, ob die zu kopierenden Daten nativ sind). In dieser Funktion sollten Sie das folgende Verfahren verwenden.

#### <a name="to-place-formats-on-the-clipboard"></a>So platzieren Sie Formate in der Zwischenablage

1. Erstellen eines `COleDataSource`-Objekts

1. Übergeben Sie diese Datenquelle an eine Funktion, mit der die systemeigenen Datenformate der Liste der unterstützten Formate hinzugefügt werden, indem aufgerufen wird `COleDataSource::CacheGlobalData` .

1. Fügen Sie Standardformate hinzu `COleDataSource::CacheGlobalData` , indem Sie für jedes Standardformat aufrufen, das Sie unterstützen möchten.

Diese Technik wird im MFC-OLE-Beispielprogramm [Hierarchien](../overview/visual-cpp-samples.md) verwendet (untersuchen Sie die `OnGetClipboardData` Member-Funktion der **CServerItem** -Klasse). Der einzige Unterschied in diesem Beispiel besteht darin, dass Schritt 3 nicht implementiert wird, da HIERSVR keine anderen Standardformate unterstützt.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [OLE-Datenobjekte und Datenquellen und einheitliche Datenübertragung](data-objects-and-data-sources-ole.md)

- [Drag &amp; Drop (OLE)](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>Siehe auch

[Zwischenablage: Verwenden des OLE-Zwischenablagemechanismus](clipboard-using-the-ole-clipboard-mechanism.md)
