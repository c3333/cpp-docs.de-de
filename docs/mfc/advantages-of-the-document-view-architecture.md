---
title: Vorteile der Dokument-/Ansichtsarchitektur
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: 80f7141ec62d509defdea361586399bd375df0d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623277"
---
# <a name="advantages-of-the-documentview-architecture"></a>Vorteile der Dokument-/Ansichtarchitektur

Der Hauptvorteil bei der Verwendung der MFC-Dokument-/Ansichtarchitektur besteht darin, dass die Architektur mehrere Ansichten desselben Dokuments besonders gut unterstützt. (Wenn Sie nicht mehrere Ansichten benötigen und der kleine mehr Aufwand von Dokument/Ansicht in Ihrer Anwendung übermäßig hoch ist, können Sie die Architektur vermeiden. [Alternativen zur Dokument-/Ansichtarchitektur](alternatives-to-the-document-view-architecture.md).)

Angenommen, Ihre Anwendung ermöglicht Benutzern das Anzeigen numerischer Daten entweder in Tabellenform oder in Diagrammform. Ein Benutzer möchte möglicherweise sowohl die Rohdaten als auch die Daten in der Kalkulations Tabelle und ein Diagramm sehen, das sich aus den Daten ergibt. Diese separaten Sichten werden in separaten Rahmen Fenstern oder in Splitter Bereichen innerhalb eines einzelnen Fensters angezeigt. Angenommen, der Benutzer kann die Daten in der Kalkulations Tabelle bearbeiten und die Änderungen sehen, die im Diagramm sofort reflektiert werden.

In MFC basieren die tabellenkalkulationsansicht und die Diagramm Ansicht auf verschiedenen Klassen, die von CView abgeleitet werden. Beide Sichten werden einem einzelnen Dokument Objekt zugeordnet. Das Dokument speichert die Daten (oder bezieht Sie ggf. aus einer Datenbank). Beide Sichten greifen auf das Dokument zu und zeigen die Daten an, die Sie daraus abrufen.

Wenn ein Benutzer eine der Ansichten aktualisiert, ruft der Ansichts Objekt auf `CDocument::UpdateAllViews` . Diese Funktion benachrichtigt alle Sichten des Dokuments, und jede Ansicht wird mit den neuesten Daten aus dem Dokument aktualisiert. Mit dem einzelnen-Befehl werden `UpdateAllViews` die unterschiedlichen Ansichten synchronisiert.

Dieses Szenario wäre schwierig zu programmieren, ohne dass Daten aus der Ansicht getrennt werden. Dies gilt insbesondere, wenn die Sichten die Daten selbst gespeichert haben. Mit Dokument/Ansicht ist es ganz einfach. Das Framework führt den größten Teil der Koordination für Sie aus.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Alternativen zu Dokument/Ansicht](alternatives-to-the-document-view-architecture.md)

- [CDocument](reference/cdocument-class.md)

- [CView](reference/cview-class.md)

- [CDocument:: UpdateAllViews](reference/cdocument-class.md#updateallviews)

- [CView:: GetDocument](reference/cview-class.md#getdocument)

## <a name="see-also"></a>Siehe auch

[Dokument-/Ansichtarchitektur](document-view-architecture.md)
