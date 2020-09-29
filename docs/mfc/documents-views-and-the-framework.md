---
title: Dokumente, Ansichten und das Microsoft Foundation Class (MFC)-Bibliotheks Framework
description: Eine Beschreibung der Dokumente und Sichten in der MFC-Bibliothek (Microsoft Foundation Class).
ms.date: 09/25/2020
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
ms.openlocfilehash: 41e145224e512b95d8674109f6ed3dcee39fffb1
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414099"
---
# <a name="documents-views-and-the-framework"></a>Dokumente, Ansichten und das Framework

Das Herzstück des MFC-Frameworks sind die Konzepte von Dokument und Sicht. Ein Dokument ist ein Datenobjekt, mit dem der Benutzer in einer Bearbeitungs Sitzung interagiert. Sie wird über den Befehl " **neu** " oder " **Öffnen** " im Menü " **Datei** " erstellt und in der Regel in einer Datei gespeichert. (Von der-Klasse abgeleitete Standard-MFC-Dokumente `CDocument` unterscheiden sich von aktiven Dokumenten und OLE-Verbund Dokumenten.) Eine Sicht ist ein Fenster Objekt, über das der Benutzer mit einem Dokument interagiert.

Die wichtigsten Objekte in einer laufenden Anwendung sind:

- Thread Objekte

   Wenn die Anwendung separate Ausführungs Threads erstellt – z. b. für Berechnungen im Hintergrund – verwenden Sie Klassen, die von abgeleitet sind [`CWinThread`](reference/cwinthread-class.md) . [`CWinApp`](reference/cwinapp-class.md) selbst wird von abgeleitet `CWinThread` und stellt den primären Ausführungs Thread (oder den Hauptprozess) in der Anwendung dar. Sie können MFC auch in sekundären Threads verwenden.

- Das Anwendungs Objekt

   Ihre Anwendungsklasse (abgeleitet von [`CWinApp`](reference/cwinapp-class.md) ) steuert alle oben aufgeführten Objekte und gibt das Anwendungsverhalten an, z. b. die Initialisierung und Bereinigung. Das einzige Anwendungs Objekt der Anwendung erstellt und verwaltet die Dokumentvorlagen für alle Dokumenttypen, die von der Anwendung unterstützt werden.

- Die Dokument Vorlage oder Vorlagen

   Eine Dokument Vorlage orchestriert die Erstellung von Dokumenten, Sichten und Frame Fenstern. Eine bestimmte Dokumentvorlagen Klasse, die von der-Klasse abgeleitet [`CDocTemplate`](reference/cdoctemplate-class.md) wird, erstellt und verwaltet alle geöffneten Dokumente eines Typs. Anwendungen, die mehr als einen Dokumenttyp unterstützen, verfügen über mehrere Dokumentvorlagen. Verwenden Sie die Klasse [CSingleDocTemplate](reference/csingledoctemplate-class.md) für SDI-Anwendungen, oder verwenden Sie die Klasse [`CMultiDocTemplate`](reference/cmultidoctemplate-class.md) für MDI-Anwendungen.

- Die Rahmen Fenster

   Sichten werden in "Dokument Rahmen Fenster" angezeigt. In einer SDI-Anwendung ist das Dokument Rahmen Fenster auch das "Hauptrahmen Fenster" für die Anwendung. In einer MDI-Anwendung werden Dokument Fenster in einem Hauptrahmen Fenster angezeigt. Die abgeleitete Hauptrahmen Fenster Klasse gibt die Stile und andere Eigenschaften der Rahmen Fenster an, die ihre Ansichten enthalten. Wenn Sie Frame Fenster anpassen müssen, leiten Sie von ab, [`CFrameWnd`](reference/cframewnd-class.md) um das Dokument Rahmen Fenster für SDI-Anwendungen anzupassen. Leiten Sie von ab [`CMDIFrameWnd`](reference/cmdiframewnd-class.md) , um das Hauptrahmen Fenster für MDI-Anwendungen anzupassen. Leiten Sie außerdem eine Klasse von ab [`CMDIChildWnd`](reference/cmdichildwnd-class.md) , um die verschiedenen Arten von MDI-Dokument Rahmen Fenstern anzupassen, die von der Anwendung unterstützt werden.

- Das Dokument oder die Dokumente.

   Ihre-Dokument Klasse (abgeleitet von [`CDocument`](reference/cdocument-class.md) ) gibt die Daten Ihrer Anwendung an.

   Wenn Sie OLE-Funktionalität in der Anwendung wünschen, leiten Sie die Dokument Klasse von [`COleDocument`](reference/coledocument-class.md) oder einer der abgeleiteten Klassen ab, abhängig von der Art der benötigten Funktionalität.

- Die Ansicht oder Sichten.

   Ihre Ansichts Klasse (abgeleitet von [`CView`](reference/cview-class.md) ) ist das Fenster "Benutzer" der Daten. Die View-Klasse steuert, wie der Benutzer die Daten des Dokuments sieht und mit ihm interagiert. In einigen Fällen möchten Sie möglicherweise, dass ein Dokument mehrere Ansichten der Daten besitzt.

   Wenn Sie einen Bildlauf benötigen, leiten Sie von ab [`CScrollView`](reference/cscrollview-class.md) . Wenn Ihre Ansicht über eine Benutzeroberfläche verfügt, die in einer Dialogfeld Vorlagen-Ressource angeordnet ist, leiten Sie von ab [`CFormView`](reference/cformview-class.md) . Verwenden Sie für einfache Textdaten, oder leiten Sie von ab [`CEditView`](reference/ceditview-class.md) . Leiten Sie für eine Formular basierte Datenzugriffs Anwendung (z. b. ein Dateneingabe Programm) von [`CRecordView`](reference/crecordview-class.md) (für ODBC) ab. Außerdem sind die Klassen [`CTreeView`](reference/ctreeview-class.md) , [`CListView`](reference/clistview-class.md) und verfügbar [`CRichEditView`](reference/cricheditview-class.md) .

In einer ausgeführten Anwendung reagieren diese Objekte kooperativ auf Benutzeraktionen, die durch Befehle und andere Nachrichten verbunden sind. Ein einzelnes Anwendungs Objekt verwaltet eine oder mehrere Dokumentvorlagen. Jede Dokument Vorlage erstellt und verwaltet ein oder mehrere Dokumente (abhängig davon, ob die Anwendung SDI oder MDI ist). Der Benutzer zeigt ein Dokument an und bearbeitet es über eine Ansicht, die in einem Rahmen Fenster enthalten ist. Die folgende Abbildung zeigt die Beziehungen zwischen diesen Objekten für eine SDI-Anwendung.

![Objekte in einer laufenden SDI-Anwendung](../mfc/media/vc386v1.gif "Objekte in einer ausgeführten SDI-Anwendung")\
Objekte in einer ausgeführten SDI-Anwendung

Der Rest dieser Artikel Familie erläutert, wie die Framework-Tools, der MFC-Anwendungs-Assistent und die Ressourcen-Editoren diese Objekte erstellen, wie Sie zusammenarbeiten und wie Sie Sie in der Programmierung verwenden. Dokumente, Ansichten und Rahmen Fenster werden in [Fenster Objekten](window-objects.md) und [Dokument-/Ansichtarchitektur](document-view-architecture.md)ausführlicher erläutert.

## <a name="see-also"></a>Weitere Informationen

[Verwenden der Klassen zum Schreiben von Anwendungen für Windows](using-the-classes-to-write-applications-for-windows.md)
