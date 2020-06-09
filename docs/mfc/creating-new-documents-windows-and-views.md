---
title: Erstellen neuer Dokumente, Fenster und Ansichten
ms.date: 11/19/2018
helpviewer_keywords:
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
ms.openlocfilehash: 7a714b5d7ba97c12b7134fa4890bddf5ed095c5b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620563"
---
# <a name="creating-new-documents-windows-and-views"></a>Erstellen neuer Dokumente, Fenster und Ansichten

Die folgenden Abbildungen bieten einen Überblick über den Erstellungs Prozess für Dokumente, Ansichten und Rahmen Fenster. Weitere Details finden Sie in anderen Artikeln, die sich auf die beteiligten Objekte konzentrieren.

Nach Abschluss dieses Vorgangs sind die zusammen mit den Zusammenarbeit bestehenden Objekte vorhanden und speichern Zeiger aufeinander. Die folgenden Abbildungen zeigen die Reihenfolge, in der-Objekte erstellt werden. Sie können die Sequenz von Abbildung zu Abbildung befolgen.

![Sequenz für die Erstellung eines Dokuments](../mfc/media/vc387l1.gif "Sequenz für die Erstellung eines Dokuments") <br/>
Reihenfolge beim Erstellen eines Dokuments

![Reihenfolge der Rahmenfenstererstellung](../mfc/media/vc387l2.png "Reihenfolge der Rahmenfenstererstellung") <br/>
Reihenfolge beim Erstellen eines Rahmenfensters

![Sequenz für die Erstellung einer Ansicht](../mfc/media/vc387l3.gif "Sequenz für die Erstellung einer Ansicht") <br/>
Reihenfolge beim Erstellen einer Ansicht

Informationen dazu, wie das Framework neue Dokument-, Ansichts-und Rahmen Fenster Objekte initialisiert, finden Sie Unterklassen [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [CFrameWnd](reference/cframewnd-class.md), [CMDIFrameWnd](reference/cmdiframewnd-class.md)und [CMDIChildWnd](reference/cmdichildwnd-class.md) in der MFC-Bibliotheks Referenz. Siehe auch [Technical Note 22](tn022-standard-commands-implementation.md), in der die Erstellungs-und Initialisierungs Prozesse weiter unten in der Erörterung der Standard Befehle des Frameworks für die **neuen** und **geöffneten** Elemente im Menü **Datei** erläutert werden.

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>Initialisieren ihrer eigenen Ergänzungen zu diesen Klassen

In den vorangehenden Abbildungen werden auch die Punkte vorgeschlagen, an denen Sie Element Funktionen überschreiben können, um die Objekte Ihrer Anwendung zu initialisieren. Eine außer Kraft Setzung von `OnInitialUpdate` in ihrer Ansichts Klasse ist der beste Ort zum Initialisieren der Sicht. Der-Befehl `OnInitialUpdate` tritt unmittelbar nach dem Erstellen des Rahmen Fensters auf, und die Ansicht im Rahmen Fenster wird an das zugehörige Dokument angefügt. Wenn Ihre Ansicht z. b. eine scrollansicht (von abgeleitet ist, die von abgeleitet ist `CScrollView` `CView` ), sollten Sie die Ansichts Größe basierend auf der Dokument Größe in der `OnInitialUpdate` außer Kraft Setzung festlegen. (Dieser Vorgang wird in der Beschreibung der Klasse [CScrollView](reference/cscrollview-class.md)beschrieben.) Sie können die Element `CDocument` Funktionen `OnNewDocument` überschreiben und `OnOpenDocument` die anwendungsspezifische Initialisierung des Dokuments bereitstellen. In der Regel müssen Sie beide überschreiben, da ein Dokument auf zwei Arten erstellt werden kann.

In den meisten Fällen sollte Ihre außer Kraft Setzung die Basisklassen Version aufzurufen. Weitere Informationen finden Sie in der MFC-Bibliotheks Referenz unter den benannten Member-Funktionen der Klassen [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [CFrameWnd](reference/cframewnd-class.md)und [CWinApp](reference/cwinapp-class.md) .

## <a name="see-also"></a>Siehe auch

[Dokumentvorlagen und der Erstellungsvorgang für Dokumente und Ansichten](document-templates-and-the-document-view-creation-process.md)<br/>
[Erstellen von Dokumentvorlagen](document-template-creation.md)<br/>
[Erstellen von Dokument/Ansicht](document-view-creation.md)<br/>
[Beziehungen zwischen MFC-Objekten](relationships-among-mfc-objects.md)
