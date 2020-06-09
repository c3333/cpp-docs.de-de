---
title: Drucken
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: 3d2ef494be66171cbcbf2b8b9e19c29c8bdc5c2f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619802"
---
# <a name="printing"></a>Drucken

Microsoft Windows implementiert geräteunabhängige Anzeige. In MFC bedeutet dies, dass die gleichen Zeichnungs Aufrufe in der `OnDraw` Member-Funktion der Ansichts Klasse für das Zeichnen auf der Anzeige und auf anderen Geräten, z. b. Druckern, verantwortlich sind. Bei der Seitenansicht ist das Zielgerät eine simulierte Druckerausgabe für die Anzeige.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Ihre Rolle im Druck Vergleich mit der Rolle des Frameworks

Ihre Ansichts Klasse hat die folgenden Zuständigkeiten:

- Informieren Sie das Framework darüber, wie viele Seiten im Dokument enthalten sind.

- Wenn Sie aufgefordert werden, eine angegebene Seite auszugeben, zeichnen Sie den Teil des Dokuments.

- Weisen Sie alle Schriftarten oder anderen GDI-Ressourcen (Graphics Device Interface) zu, die für den Druck benötigt werden

- Senden Sie ggf. alle Escapecodes, die erforderlich sind, um den Drucker Modus zu ändern, bevor Sie eine bestimmte Seite drucken, um z. b. die Druck Ausrichtung auf Seitenbasis zu ändern.

Die Zuständigkeiten des Frameworks lauten wie folgt:

- Zeigen Sie das Dialogfeld **Drucken** an.

- Erstellen Sie ein [CDC](reference/cdc-class.md) -Objekt für den Drucker.

- Aufrufen der [StartDoc](reference/cdc-class.md#startdoc) -und [EndDoc](reference/cdc-class.md#enddoc) -Member-Funktionen des- `CDC` Objekts.

- Aufrufen der [Startpage](reference/cdc-class.md#startpage) -Member-Funktion des-Objekts wiederholt `CDC` , informieren der Ansichts Klasse, welche Seite gedruckt werden soll, und Aufrufen der [EndPage](reference/cdc-class.md#endpage) -Member-Funktion des- `CDC` Objekts.

- Über schreibbare Funktionen in der Ansicht zu den entsprechenden Zeitpunkten aufzurufen.

In den folgenden Artikeln wird erläutert, wie das Framework Druck-und Druckvorschau unterstützt:

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Funktionsweise des Standard Drucks](how-default-printing-is-done.md)

- [Mehrseitige Dokumente](multipage-documents.md)

- [Kopf-und Fußzeilen](headers-and-footers.md)

- [Zuordnen von GDI-Ressourcen zum Drucken](allocating-gdi-resources.md)

- [Seitenansicht](print-preview-architecture.md)

## <a name="see-also"></a>Siehe auch

[Drucken und Druckvorschau](printing-and-print-preview.md)
