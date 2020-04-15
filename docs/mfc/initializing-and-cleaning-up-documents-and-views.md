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
ms.openlocfilehash: 3c92d60941cd6542bd0d6c27e8a879dc85e3a3d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377200"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Initialisieren und Bereinigen von Dokumenten und Ansichten

Verwenden Sie die folgenden Richtlinien zum Initialisieren und Bereinigen nach Dokumenten und Ansichten:

- Das MFC-Framework initialisiert Dokumente und Ansichten. Sie initialisieren alle Daten, die Sie ihnen hinzufügen.

- Der Rahmen bereinigt, wenn Dokumente und Ansichten geschlossen werden; Sie müssen den Speicher, den Sie auf dem Heap zugewiesen haben, innerhalb der Memberfunktionen dieser Dokumente und Ansichten aufteilen.

> [!NOTE]
> Denken Sie daran, dass die Initialisierung für die gesamte Anwendung am `CWinApp`besten in Ihrer Außerkraftsetzung der [InitInstance-Memberfunktion](../mfc/reference/cwinapp-class.md#initinstance) der Klasse erfolgt und die Bereinigung für die gesamte Anwendung am besten in Ihrer Außerkraftsetzung der `CWinApp` Memberfunktion [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)erfolgt.

Der Lebenszyklus eines Dokuments (und sein Rahmenfenster und ansichten oder Ansichten) in einer MDI-Anwendung ist wie folgt:

1. Während der dynamischen Erstellung wird der Dokumentkonstruktor aufgerufen.

1. Für jedes neue Dokument wird [Das Dokument OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) oder [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) aufgerufen.

1. Der Benutzer interagiert während seiner gesamten Lebensdauer mit dem Dokument. In der Regel geschieht dies, wenn der Benutzer über die Ansicht an Dokumentdaten arbeitet und die Daten auswählt und bearbeitet. Die Ansicht übergibt Änderungen an das Dokument zum Speichern und Aktualisieren anderer Ansichten. Während dieser Zeit können sowohl das Dokument als auch die Ansicht Befehle verarbeiten.

1. Das Framework ruft [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) auf, um Daten zu löschen, die für ein Dokument spezifisch sind.

1. Der Destruktor des Dokuments wird aufgerufen.

In einer SDI-Anwendung wird Schritt 1 einmal ausgeführt, wenn das Dokument zum ersten Mal erstellt wird. Dann werden die Schritte 2 bis 4 wiederholt durchgeführt, wenn ein neues Dokument geöffnet wird. Das neue Dokument verwendet das vorhandene Dokumentobjekt wieder. Schließlich wird Schritt 5 ausgeführt, wenn die Anwendung endet.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Initialisieren von Dokumenten und Ansichten](../mfc/initializing-documents-and-views.md)

- [Bereinigen von Dokumenten und Ansichten](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Siehe auch

[Dokument-/Ansichtsarchitektur](../mfc/document-view-architecture.md)
