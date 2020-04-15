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
ms.openlocfilehash: aa1c58b02df92d79ca9915032b97fb5c0e2eaffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371669"
---
# <a name="creating-new-documents-windows-and-views"></a>Erstellen neuer Dokumente, Fenster und Ansichten

Die folgenden Abbildungen geben einen Überblick über den Erstellungsprozess für Dokumente, Ansichten und Rahmenfenster. Weitere Artikel, die sich auf die beteiligten Objekte konzentrieren, enthalten weitere Details.

Nach Abschluss dieses Vorgangs sind die kooperierenden Objekte vorhanden und speichern Zeiger aufeinander. Die folgenden Abbildungen zeigen die Reihenfolge, in der Objekte erstellt werden. Sie können die Reihenfolge von Figur zu Abbildung verfolgen.

![Sequenz für die Erstellung eines Dokuments](../mfc/media/vc387l1.gif "Sequenz für die Erstellung eines Dokuments") <br/>
Reihenfolge beim Erstellen eines Dokuments

![Reihenfolge der Rahmenfenstererstellung](../mfc/media/vc387l2.png "Reihenfolge der Rahmenfenstererstellung") <br/>
Reihenfolge beim Erstellen eines Rahmenfensters

![Sequenz für die Erstellung einer Ansicht](../mfc/media/vc387l3.gif "Sequenz für die Erstellung einer Ansicht") <br/>
Reihenfolge beim Erstellen einer Ansicht

Informationen dazu, wie das Framework die neuen Dokument-, Ansichts- und Framefensterobjekte initialisiert, finden Sie unter Klassen [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)und [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) in der MFC-Bibliotheksreferenz. Siehe auch [Technical Note 22](../mfc/tn022-standard-commands-implementation.md), in dem die Erstellungs- und Initialisierungsprozesse unter der Erörterung der Standardbefehle des Frameworks für die Elemente **"Neue"** und **"Öffnen"** im Menü **Datei** näher erläutert werden.

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>Initialisieren eigener Ergänzungen zu diesen Klassen

Die vorstehenden Abbildungen schlagen auch die Punkte vor, an denen Sie Memberfunktionen überschreiben können, um die Objekte Ihrer Anwendung zu initialisieren. Eine Außerkraftsetzung in `OnInitialUpdate` ihrer Ansichtsklasse ist der beste Ort, um die Ansicht zu initialisieren. Der `OnInitialUpdate` Aufruf erfolgt unmittelbar nach dem Erstellen des Rahmenfensters und der Anschrift der Ansicht innerhalb des Rahmenfensters an das Dokument. Wenn es sich bei der Ansicht beispielsweise `CScrollView` um `CView`eine Bildlaufansicht handelt (die nicht `OnInitialUpdate` von abgeleitet wird), sollten Sie die Ansichtsgröße basierend auf der Dokumentgröße in der Außerkraftsetzung festlegen. (Dieser Prozess wird in der Beschreibung der Klasse [CScrollView](../mfc/reference/cscrollview-class.md)beschrieben.) Sie können die `CDocument` `OnNewDocument` Memberfunktionen `OnOpenDocument` überschreiben und eine anwendungsspezifische Initialisierung des Dokuments bereitstellen. In der Regel müssen Sie beides überschreiben, da ein Dokument auf zwei Arten erstellt werden kann.

In den meisten Fällen sollte Ihre Außerkraftsetzung die Basisklassenversion aufrufen. Weitere Informationen finden Sie in den benannten Memberfunktionen der Klassen [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md)und [CWinApp](../mfc/reference/cwinapp-class.md) in der MFC-Bibliotheksreferenz.

## <a name="see-also"></a>Siehe auch

[Dokumentvorlagen und der Erstellungsvorgang für Dokumente und Ansichten](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Erstellen von Dokumentvorlagen](../mfc/document-template-creation.md)<br/>
[Erstellen von Dokument/Ansicht](../mfc/document-view-creation.md)<br/>
[Beziehungen zwischen MFC-Objekten](../mfc/relationships-among-mfc-objects.md)
