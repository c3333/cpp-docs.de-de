---
title: Drucken und Druckvorschau
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 26ced8172a36d34883d6b65997bb3a81fdc3c319
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625277"
---
# <a name="printing-and-print-preview"></a>Drucken und Druckvorschau

MFC unterstützt Druck-und Druckvorschau für die Dokumente Ihres Programms über die [CView](reference/cview-class.md)-Klasse. Überschreiben Sie für die Standarddruck-und Druckvorschau einfach die [OnDraw](reference/cview-class.md#ondraw) -Member-Funktion Ihrer Ansichts Klasse, was Sie trotzdem tun müssen. Diese Funktion kann auf die Ansicht auf dem Bildschirm, auf einen Drucker Gerätekontext für einen echten Drucker oder auf einen Gerätekontext, der den Drucker auf dem Bildschirm simuliert, zeichnen.

Sie können auch Code hinzufügen, um das Drucken und die Vorschau der mehrseitigen Dokumente zu verwalten, die gedruckten Dokumente zu paginieren und Ihnen Kopf-und Fußzeilen hinzuzufügen.

Diese Artikel Familie erläutert, wie das Drucken in der Microsoft Foundation Class-Bibliothek (MFC) implementiert wird und wie die in das Framework integrierte Druck Architektur genutzt wird. In den Artikeln wird auch erläutert, wie MFC eine einfache Implementierung der Funktionen der Druckvorschau unterstützt und wie Sie diese Funktionen verwenden und ändern können.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Drucken](printing.md)

- [Architektur der Druckvorschau](print-preview-architecture.md)

- [Beispiel](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)
