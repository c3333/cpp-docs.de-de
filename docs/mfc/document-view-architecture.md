---
title: Dokument-/Ansichtarchitektur
ms.date: 11/19/2018
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
ms.openlocfilehash: a74aeba651d385cf3a5386e94ec20e4e56b7cd57
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624786"
---
# <a name="documentview-architecture"></a>Dokument-/Ansichtsarchitektur

Der MFC-Anwendungs-Assistent erstellt standardmäßig ein Anwendungs Skelett mit einer Dokument Klasse und einer Ansichts Klasse. MFC trennt die Datenverwaltung in diese beiden Klassen. Das Dokument speichert die Daten und verwaltet das Drucken der Daten und Koordinaten zum Aktualisieren mehrerer Sichten der Daten. In der Ansicht werden die Daten angezeigt und die Benutzerinteraktion mit dem Benutzer, einschließlich Auswahl und Bearbeitung, verwaltet.

In diesem Modell liest und schreibt ein MFC-Dokument Objektdaten in den persistenten Speicher. Das Dokument kann auch eine Schnittstelle zu den Daten bereitstellen, wo Sie sich befindet (z. b. in einer Datenbank). Ein separates Ansichts Objekt verwaltet die Datenanzeige, von der Darstellung der Daten in einem Fenster bis zur Benutzer Auswahl und Bearbeitung von Daten. In der Ansicht werden Anzeigedaten aus dem Dokument abgerufen, und es werden alle Datenänderungen an das Dokument übermittelt.

Obwohl Sie die Trennung von Dokumenten/Ansichten problemlos überschreiben oder ignorieren können, gibt es in den meisten Fällen überzeugende Gründe, dieses Modell zu befolgen. Eine der besten ist, wenn Sie mehrere Ansichten desselben Dokuments benötigen, z. b. eine Tabelle und eine Diagramm Ansicht. Mit dem Dokument-/ansichtenmodell kann ein separates Ansichts Objekt jede Ansicht der Daten darstellen, während sich der Code, der für alle Sichten (z. b. ein Berechnungsmodul) üblich ist, im Dokument befinden kann. Außerdem übernimmt das Dokument die Aufgabe, alle Sichten zu aktualisieren, wenn sich die Daten ändern.

Die MFC-Dokument-/Ansichtarchitektur erleichtert die Unterstützung mehrerer Sichten, mehrerer Dokumenttypen, Splitter Fenster und anderer wertvoller Benutzeroberflächen Features.

Die Teile des MFC-Frameworks, die sowohl für den Benutzer als auch für Sie, Programmierer, sichtbar sind, sind das Dokument und die Ansicht. Die meiste Arbeit bei der Entwicklung einer Anwendung mit dem Framework führt Sie in das Schreiben von Dokument-und Ansichts Klassen. In dieser Artikel Familie wird Folgendes beschrieben:

- Der Zweck von Dokumenten und Sichten und deren Interaktion im Framework.

- Was Sie tun müssen, um Sie zu implementieren.

Das Herzstück der Dokumente/Ansicht sind vier Schlüssel Klassen:

Die [CDocument](reference/cdocument-class.md) -Klasse (oder [COleDocument](reference/coledocument-class.md)) unterstützt Objekte, die zum Speichern oder Steuern der Programm Daten verwendet werden, und stellt die grundlegende Funktionalität für von einem Programmierer definierte Dokument Klassen bereit. Ein Dokument stellt die Einheit der Daten dar, die der Benutzer in der Regel mit dem Befehl Öffnen im Menü Datei öffnet, und speichert mit dem Befehl Speichern im Menü Datei.

Die [CView](reference/cview-class.md) (oder eine der vielen abgeleiteten Klassen) stellt die grundlegende Funktionalität für von Programmierern definierte Ansichts Klassen bereit. Eine Sicht wird an ein Dokument angefügt und fungiert als Vermittler zwischen dem Dokument und dem Benutzer: die Ansicht rendert ein Bild des Dokuments auf dem Bildschirm und interpretiert Benutzereingaben als Vorgänge für das Dokument. Die Ansicht rendert auch das Bild für Druck-und Druckvorschau.

[CFrameWnd](reference/cframewnd-class.md) (oder eine der zugehörigen Variationen) unterstützt Objekte, die den Frame um eine oder mehrere Ansichten eines Dokuments bereitstellen.

[CDocTemplate](reference/cdoctemplate-class.md) (oder [CSingleDocTemplate](reference/csingledoctemplate-class.md) oder [CMultiDocTemplate](reference/cmultidoctemplate-class.md)) unterstützt ein Objekt, das ein oder mehrere vorhandene Dokumente eines bestimmten Typs koordiniert und das Erstellen der richtigen Dokument-, Ansichts-und Rahmen Fenster Objekte für diesen Typ verwaltet.

Die folgende Abbildung zeigt die Beziehung zwischen einem Dokument und seiner Ansicht.

![Die Ansicht ist Teil des angezeigten Dokuments](../mfc/media/vc379n1.gif "Die Ansicht ist Teil des angezeigten Dokuments") <br/>
Dokument und Ansicht

Die Dokument-/Ansicht-Implementierung in der Klassenbibliothek trennt die Daten selbst von der Anzeige und von Benutzer Vorgängen für die Daten. Alle Änderungen an den Daten werden über die Document-Klasse verwaltet. Die Ansicht ruft diese Schnittstelle auf, um auf die Daten zuzugreifen und diese zu aktualisieren.

Dokumente, ihre zugeordneten Sichten und die Rahmen Fenster, in denen die Ansichten Frame laufen, werden von einer Dokument Vorlage erstellt. Die Dokument Vorlage ist für das Erstellen und Verwalten aller Dokumente eines Dokument Typs zuständig.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Ein Hochformat der Dokument-/Ansichtarchitektur](a-portrait-of-the-document-view-architecture.md)

- [Vorteile der Dokument-/Ansichtarchitektur](advantages-of-the-document-view-architecture.md)

- [Vom Anwendungs-Assistenten erstellte Dokument-und Ansichts Klassen](document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [Alternativen zur Dokument-/Ansichtarchitektur](alternatives-to-the-document-view-architecture.md)

- [Hinzufügen mehrerer Ansichten zu einem Dokument](adding-multiple-views-to-a-single-document.md)

- [Verwenden von Dokumenten](using-documents.md)

- [Verwenden von Ansichten](using-views.md)

- [Mehrere Dokumenttypen, Ansichten und Rahmenfenster](multiple-document-types-views-and-frame-windows.md)

- [Initialisieren und Bereinigen von Dokumenten und Sichten](initializing-and-cleaning-up-documents-and-views.md)

- [Initialisieren Sie Ihre eigenen Ergänzungen für die Dokument & Ansichts Klassen](creating-new-documents-windows-and-views.md)

- [Verwenden von Datenbankklassen mit Dokumenten und Ansichten](../data/mfc-using-database-classes-with-documents-and-views.md)

- [Verwenden von Datenbankklassen ohne Dokumente und Ansichten](../data/mfc-using-database-classes-without-documents-and-views.md)

- [Beispiele](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)<br/>
[Windows](windows.md)<br/>
[Rahmenfenster](frame-windows.md)<br/>
[Dokumentvorlagen und der Erstellungsvorgang für Dokumente und Ansichten](document-templates-and-the-document-view-creation-process.md)<br/>
[Erstellen von Dokument/Ansicht](document-view-creation.md)<br/>
[Erstellen neuer Dokumente, Fenster und Ansichten](creating-new-documents-windows-and-views.md)
