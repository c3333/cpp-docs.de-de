---
title: Rahmenfenster
ms.date: 11/19/2018
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame windows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
ms.openlocfilehash: 39c0b4b866fa123d8bcae639342c925570d96e1b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625820"
---
# <a name="frame-windows"></a>Rahmenfenster

Wenn eine Anwendung unter Windows ausgeführt wird, interagiert der Benutzer mit Dokumenten, die in Frame Fenstern angezeigt werden. Ein Dokument Rahmen Fenster besteht aus zwei Hauptkomponenten: dem Frame und dem Inhalt, der von ihm umrahmt wird. Ein Dokument Rahmen Fenster kann ein [einzelnes Dokument Schnittstellen](sdi-and-mdi.md) Fenster (SDI) oder ein untergeordnetes MDI-Fenster ( [Multiple Document Interface](sdi-and-mdi.md) ) sein. Windows verwaltet den größten Teil der Interaktion des Benutzers mit dem Rahmen Fenster: Verschieben und Ändern der Größe des Fensters, Schließen des Fensters und minimieren und maximieren. Sie verwalten die Inhalte im Frame.

## <a name="frame-windows-and-views"></a>Rahmen Fenster und-Ansichten

Das MFC-Framework verwendet Rahmen Fenster, um Ansichten zu enthalten. Die beiden Komponenten – Frame und Content – werden von zwei verschiedenen Klassen in MFC dargestellt und verwaltet. Eine Frame Fenster Klasse verwaltet den Frame, und eine Ansichts Klasse verwaltet den Inhalt. Das Ansichts Fenster ist ein untergeordnetes Element des Rahmen Fensters. Das Zeichnen und andere Benutzerinteraktionen mit dem Dokument erfolgen im Client Bereich der Ansicht, nicht im Client Bereich des Rahmen Fensters. Das Rahmen Fenster bietet einen sichtbaren Rahmen um eine Ansicht, den Abschluss mit einer Titelleiste und Standardfenster Steuerelementen, wie z. b. ein Steuerelement Menü, Schaltflächen zum minimieren und maximieren des Fensters und Steuerelemente zum Ändern der Größe des Fensters. Der "Inhalt" besteht aus dem Client Bereich des Fensters, der vollständig von einem untergeordneten Fenster belegt wird – der Ansicht. Die folgende Abbildung zeigt die Beziehung zwischen einem Rahmen Fenster und einer Ansicht.

![Rahmen Fensteransicht](../mfc/media/vc37fx1.gif "Rahmenfensteransicht") <br/>
Rahmenfenster und -ansicht

## <a name="frame-windows-and-splitter-windows"></a>Rahmen Fenster und Splitter Fenster

Eine weitere gängige Anordnung besteht darin, dass das Rahmen Fenster mehrere Ansichten einrichtet, in der Regel mithilfe eines [Splitter Fensters](multiple-document-types-views-and-frame-windows.md). In einem Splitter Fenster wird der Client Bereich des Frame Fensters von einem Splitter Fenster belegt, das wiederum über mehrere untergeordnete Fenster verfügt, die als Bereiche bezeichnet werden. Dies sind Ansichten.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

**Allgemeine Rahmen Fenster Themen**

- [Fenster Objekte](window-objects.md)

- [Rahmen Fenster Klassen](frame-window-classes.md)

- [Die vom Anwendungs-Assistenten erstellten Frame-Window-Klassen](frame-window-classes-created-by-the-application-wizard.md)

- [Rahmen Fenster Stile](frame-window-styles-cpp.md)

- [Funktionsumfang von Rahmen Fenstern](what-frame-windows-do.md)

**Themen zur Verwendung von Rahmen Fenstern**

- [Verwenden von Rahmen Fenstern](using-frame-windows.md)

- [Erstellen von Dokument Rahmen Fenstern](creating-document-frame-windows.md)

- [Zerstören von Rahmenfenstern](destroying-frame-windows.md)

- [Verwalten von untergeordneten MDI-Fenstern](managing-mdi-child-windows.md)

- [Verwalten der aktuellen Ansicht](managing-the-current-view.md) in einem Rahmen Fenster, das mehr als eine Ansicht enthält

- [Verwalten von Menüs, Steuer leisten und Zugriffstasten (andere Objekte, die den Bereich des Rahmen Fensters teilen)](managing-menus-control-bars-and-accelerators.md)

**Themen zu speziellen Rahmen Fenster Funktionen**

- [Ziehen und Ablegen von Dateien](dragging-and-dropping-files-in-a-frame-window.md) aus dem Datei-Explorer oder Datei-Manager in ein Rahmen Fenster

- [Reagieren auf den dynamischen Datenaustausch (DDE)](responding-to-dynamic-data-exchange-dde.md)

- [Semimodale Zustände: kontextbezogene Windows-Hilfe (orchestrieren anderer Fenster Aktionen)](orchestrating-other-window-actions.md)

- [Semimodale Zustände: Druck-und Druckvorschau (orchestrieren anderer Fenster Aktionen)](orchestrating-other-window-actions.md)

**Themen zu anderen Arten von Fenstern**

- [Verwenden von Ansichten](using-views.md)

- [Dialogfelder](dialog-boxes.md)

- [Steuerelemente](controls-mfc.md)

## <a name="see-also"></a>Siehe auch

[Windows](windows.md)
