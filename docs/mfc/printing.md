---
title: Drucken
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: a46096592c9983d04d2122bfabb56ece9346c4bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371203"
---
# <a name="printing"></a>Drucken

Microsoft Windows implementiert eine geräteunabhängige Anzeige. In MFC bedeutet dies, dass dieselben `OnDraw` Zeichnungsaufrufe in der Memberfunktion Ihrer Ansichtsklasse für das Zeichnen auf dem Display und auf anderen Geräten, z. B. Druckern, verantwortlich sind. Für die Druckvorschau ist das Zielgerät eine simulierte Druckerausgabe für das Display.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Ihre Rolle im Druck im Vergleich zur Rolle des Frameworks

Ihre Ansichtsklasse hat die folgenden Aufgaben:

- Informieren Sie das Framework, wie viele Seiten sich im Dokument befinden.

- Wenn Sie aufgefordert werden, eine angegebene Seite zu drucken, zeichnen Sie diesen Teil des Dokuments.

- Zuweisen und Zuweisen von Schriftarten oder anderen GDI-Ressourcen (Graphics Device Interface), die für das Drucken erforderlich sind.

- Senden Sie ggf. Escapecodes, die zum Ändern des Druckermodus erforderlich sind, bevor Sie eine bestimmte Seite drucken, z. B. um die Druckausrichtung pro Seite zu ändern.

Der Rahmen hat folgende Aufgaben:

- Zeigen Sie das Dialogfeld **Drucken** an.

- Erstellen Sie ein [CDC-Objekt](../mfc/reference/cdc-class.md) für den Drucker.

- Rufen Sie die [StartDoc-](../mfc/reference/cdc-class.md#startdoc) und `CDC` [EndDoc-Memberfunktionen](../mfc/reference/cdc-class.md#enddoc) des Objekts auf.

- Rufen Sie wiederholt die [StartPage-Memberfunktion](../mfc/reference/cdc-class.md#startpage) des `CDC` Objekts auf, informieren Sie die Ansichtsklasse, welche Seite gedruckt werden soll, und rufen Sie die [EndPage-Memberfunktion](../mfc/reference/cdc-class.md#endpage) des `CDC` Objekts auf.

- Rufen Sie überschreibbare Funktionen in der Ansicht zu den entsprechenden Zeiten auf.

In den folgenden Artikeln wird erläutert, wie das Framework Drucken und Druckvorschau unterstützt:

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Wie Standarddruck erfolgt](../mfc/how-default-printing-is-done.md)

- [Mehrseitige Dokumente](../mfc/multipage-documents.md)

- [Kopf- und Fußzeilen](../mfc/headers-and-footers.md)

- [Zuweisen von GDI-Ressourcen für den Druck](../mfc/allocating-gdi-resources.md)

- [Seitenansicht](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Siehe auch

[Drucken und Druckvorschau](../mfc/printing-and-print-preview.md)
