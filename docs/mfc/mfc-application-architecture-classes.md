---
title: Klassen der MFC-Anwendungsarchitektur
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 455a49a4f93f2fb2590447071edca76a32cbc5dd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618023"
---
# <a name="mfc-application-architecture-classes"></a>Klassen der MFC-Anwendungsarchitektur

Klassen in dieser Kategorie tragen zur Architektur einer Framework-Anwendung bei. Sie stellen Funktionen bereit, die den meisten Anwendungen gemeinsam sind. Sie füllen das Framework aus, um anwendungsspezifische Funktionen hinzuzufügen. Dies geschieht in der Regel durch Ableiten von neuen Klassen aus den Architektur Klassen und anschließendes Hinzufügen neuer Member oder Überschreiben vorhandener Element Funktionen.

[Anwendungs Assistenten](reference/mfc-application-wizard.md) generieren verschiedene Anwendungs Typen, die alle das Anwendungs Framework auf unterschiedliche Weise verwenden. SDI (Single Document Interface) und MDI (Multiple Document Interface)-Anwendungen verwenden einen Teil des Frameworks, der als Dokument-/Ansichtarchitektur bezeichnet wird. Andere Arten von Anwendungen, wie z. b. Dialogfeld basierte Anwendungen, Formular basierte Anwendungen und DLLs, verwenden nur einige der Funktionen für Dokument-/Ansichtarchitektur.

Dokument-/ansichtenanwendungen enthalten mindestens eine Reihe von Dokumenten, Sichten und Rahmen Fenstern. Ein Dokument-Template-Objekt ordnet die Klassen für jedes Dokument/jede Ansicht/jeden Frame Satz zu.

Obwohl Sie die Dokument-/Ansichtarchitektur in ihrer MFC-Anwendung nicht verwenden müssen, gibt es eine Reihe von Vorteilen. Die MFC-OLE-Container-und Serverunterstützung basiert auf Dokument-/Ansichtarchitektur, ebenso wie die Unterstützung für Druck-und Druckvorschau.

Alle MFC-Anwendungen haben mindestens zwei Objekte: ein von [CWinApp](reference/cwinapp-class.md)abgeleitetes Anwendungs Objekt und eine Art von Hauptfenster Objekt, das von [CWnd](reference/cwnd-class.md)abgeleitet (häufig indirekt). (Meistens wird das Hauptfenster von [CFrameWnd](reference/cframewnd-class.md), [CMDIFrameWnd](reference/cmdiframewnd-class.md)oder [CDialog](reference/cdialog-class.md)abgeleitet, die alle von abgeleitet sind `CWnd` .)

Anwendungen, die die Dokument-/Ansichtarchitektur verwenden, enthalten zusätzliche Objekte. Prinzipal Objekte sind:

- Ein von der [CWinApp](reference/cwinapp-class.md)-Klasse abgeleitetes Anwendungs Objekt, wie zuvor erwähnt.

- Mindestens ein Dokument Klassenobjekt, das von der [CDocument](reference/cdocument-class.md)-Klasse abgeleitet ist. Dokument Klassen Objekte sind für die interne Darstellung der in der Sicht bearbeiteten Daten verantwortlich. Sie können einer Datendatei zugeordnet werden.

- Mindestens ein Ansichts Objekt, das von der [CView](reference/cview-class.md)-Klasse abgeleitet ist. Jede Ansicht ist ein Fenster, das an ein Dokument angefügt und einem Rahmen Fenster zugeordnet wird. Sichten zeigen die in einem Dokument Klassenobjekt enthaltenen Daten an und bearbeiten Sie.

Dokument-/Ansichts Anwendungen enthalten außerdem Rahmen Fenster (abgeleitet von [CFrameWnd](reference/cframewnd-class.md)) und Dokumentvorlagen (abgeleitet von [CDocTemplate](reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
