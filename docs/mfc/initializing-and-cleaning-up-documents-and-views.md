---
title: Initialisieren und Bereinigen von Dokumenten und Ansichten
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
ms.openlocfilehash: c5beed5618d4fa991160ad1688a5a686aeaa842f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626366"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Initialisieren und Bereinigen von Dokumenten und Ansichten

Verwenden Sie die folgenden Richtlinien für die Initialisierung und Bereinigung nach Ihren Dokumenten und Ansichten:

- Das MFC-Framework initialisiert Dokumente und Sichten. Sie initialisieren alle Daten, die Sie zu Ihnen hinzufügen.

- Das Framework wird beim Schließen von Dokumenten und Ansichten bereinigt. Sie müssen die Zuordnung von Arbeitsspeicher, den Sie auf dem Heap zugeordnet haben, aus den Element Funktionen dieser Dokumente und Sichten aufheben.

> [!NOTE]
> Denken Sie daran, dass die Initialisierung für die gesamte Anwendung am besten in der Überschreibung der [InitInstance](reference/cwinapp-class.md#initinstance) -Member-Funktion der-Klasse durchgeführt wird `CWinApp` und die Bereinigung für die gesamte Anwendung am besten in der Überschreibung der `CWinApp` Member-Funktion [ExitInstance](reference/cwinapp-class.md#exitinstance)erfolgt.

Der Lebenszyklus eines Dokuments (und dessen Rahmen Fenster und Ansicht oder Ansichten) in einer MDI-Anwendung lautet wie folgt:

1. Während der dynamischen Erstellung wird der Dokumentkonstruktor aufgerufen.

1. Für jedes neue Dokument wird das [OnNewDocument](reference/cdocument-class.md#onnewdocument) -oder [OnOpenDocument](reference/cdocument-class.md#onopendocument) -Dokument des Dokuments aufgerufen.

1. Der Benutzer interagiert während der gesamten Lebensdauer mit dem Dokument. Dies geschieht in der Regel, wenn der Benutzer an Dokument Daten über die Sicht arbeitet und die Daten auswählt und bearbeitet. Die Ansicht übergibt Änderungen an dem Dokument zum Speichern und aktualisieren anderer Sichten. Während dieser Zeit können sowohl das Dokument als auch die Ansicht Befehle verarbeiten.

1. Das Framework ruft [deletecontent](reference/cdocument-class.md#deletecontents) zum Löschen von Daten ab, die für ein Dokument spezifisch sind.

1. Der Dekonstruktor des Dokuments wird aufgerufen.

In einer SDI-Anwendung wird Schritt 1 einmal ausgeführt, wenn das Dokument erstmalig erstellt wird. Die Schritte 2 bis 4 werden immer wiederholt ausgeführt, wenn ein neues Dokument geöffnet wird. Das neue Dokument verwendet das vorhandene Dokument Objekt wieder. Zum Schluss wird Schritt 5 ausgeführt, wenn die Anwendung beendet wird.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Initialisieren von Dokumenten und Ansichten](initializing-documents-and-views.md)

- [Bereinigen von Dokumenten und Ansichten](cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Siehe auch

[Dokument-/Ansichtarchitektur](document-view-architecture.md)
