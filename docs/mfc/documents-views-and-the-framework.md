---
title: Dokumente, Ansichten und das Framework
ms.date: 11/19/2018
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
ms.openlocfilehash: 17956c0b175e978c6e4e2fefcdad5f744929d457
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621838"
---
# <a name="documents-views-and-the-framework"></a>Dokumente, Ansichten und das Framework

Das Herzstück des MFC-Frameworks sind die Konzepte von Dokument und Sicht. Ein Dokument ist ein Datenobjekt, mit dem der Benutzer in einer Bearbeitungs Sitzung interagiert. Sie wird über den Befehl " **neu** " oder " **Öffnen** " im Menü " **Datei** " erstellt und in der Regel in einer Datei gespeichert. (Von der-Klasse abgeleitete Standard-MFC-Dokumente `CDocument` unterscheiden sich von aktiven Dokumenten und OLE-Verbund Dokumenten.) Eine Sicht ist ein Fenster Objekt, über das der Benutzer mit einem Dokument interagiert.

Die wichtigsten Objekte in einer laufenden Anwendung sind:

- Das Dokument oder die Dokumente.

   Die von [CDocument](reference/cdocument-class.md)abgeleitete Dokument Klasse gibt die Daten Ihrer Anwendung an.

   Wenn Sie OLE-Funktionalität in der Anwendung wünschen, leiten Sie die Dokument Klasse abhängig von dem benötigten Funktionstyp von [COleDocument](reference/coledocument-class.md) oder einer der abgeleiteten Klassen ab.

- Die Ansicht oder Sichten.

   Ihre Ansichts Klasse (abgeleitet von [CView](reference/cview-class.md)) ist das "Fenster der Daten" des Benutzers. Die View-Klasse steuert, wie der Benutzer die Daten des Dokuments sieht und mit ihm interagiert. In einigen Fällen möchten Sie möglicherweise, dass ein Dokument mehrere Ansichten der Daten besitzt.

   Wenn Sie einen Bildlauf ausführen möchten, leiten Sie von [CScrollView](reference/cscrollview-class.md)ab. Wenn Ihre Ansicht über eine Benutzeroberfläche verfügt, die in einer Dialogfeld Vorlagen-Ressource angeordnet ist, leiten Sie von [CFormView](reference/cformview-class.md)ab. Verwenden Sie für einfache Textdaten, oder leiten Sie Sie von [CEditView](reference/ceditview-class.md)ab. Leiten Sie für eine Formular basierte Datenzugriffs Anwendung (z. b. ein Dateneingabe Programm) von [CRecordView](reference/crecordview-class.md) (für ODBC) ab. Außerdem sind die Klassen [CTreeView](reference/ctreeview-class.md), [CListView](reference/clistview-class.md)und [CRichEditView](reference/cricheditview-class.md)verfügbar.

- Die Rahmen Fenster

   Sichten werden in "Dokument Rahmen Fenster" angezeigt. In einer SDI-Anwendung ist das Dokument Rahmen Fenster auch das "Hauptrahmen Fenster" für die Anwendung. In einer MDI-Anwendung werden Dokument Fenster in einem Hauptrahmen Fenster angezeigt. Die abgeleitete Hauptrahmen Fenster Klasse gibt die Stile und andere Eigenschaften der Rahmen Fenster an, die ihre Ansichten enthalten. Wenn Sie Frame Fenster anpassen müssen, leiten Sie von [CFrameWnd](reference/cframewnd-class.md) ab, um das Dokument Rahmen Fenster für SDI-Anwendungen anzupassen. Leiten Sie von [CMDIFrameWnd](reference/cmdiframewnd-class.md) ab, um das Hauptrahmen Fenster für MDI-Anwendungen anzupassen. Leiten Sie außerdem eine Klasse von [CMDIChildWnd](reference/cmdichildwnd-class.md) ab, um die verschiedenen Arten von MDI-Dokument Rahmen Fenstern anzupassen, die von der Anwendung unterstützt werden.

- Die Dokument Vorlage oder Vorlagen

   Eine Dokument Vorlage orchestriert die Erstellung von Dokumenten, Sichten und Frame Fenstern. Eine bestimmte Dokumentvorlagen Klasse, die von der [CDocTemplate](reference/cdoctemplate-class.md)-Klasse abgeleitet wird, erstellt und verwaltet alle geöffneten Dokumente eines Typs. Anwendungen, die mehr als einen Dokumenttyp unterstützen, verfügen über mehrere Dokumentvorlagen. Verwenden Sie die [CSingleDocTemplate](reference/csingledoctemplate-class.md) -Klasse für SDI-Anwendungen, oder verwenden Sie die [CMultiDocTemplate](reference/cmultidoctemplate-class.md) -Klasse für MDI-Anwendungen.

- Das Anwendungs Objekt

   Ihre Anwendungsklasse (abgeleitet von [CWinApp](reference/cwinapp-class.md)) steuert alle oben aufgeführten Objekte und gibt das Anwendungsverhalten an, z. b. die Initialisierung und Bereinigung. Das einzige Anwendungs Objekt der Anwendung erstellt und verwaltet die Dokumentvorlagen für alle Dokumenttypen, die von der Anwendung unterstützt werden.

- Thread Objekte

   Wenn die Anwendung separate Ausführungs Threads erstellt – z. b. zum Ausführen von Berechnungen im Hintergrund – verwenden Sie Klassen, die von [CWinThread](reference/cwinthread-class.md)abgeleitet werden. [CWinApp](reference/cwinapp-class.md) selbst wird von abgeleitet `CWinThread` und stellt den primären Ausführungs Thread (oder den Hauptprozess) in der Anwendung dar. Sie können MFC auch in sekundären Threads verwenden.

In einer ausgeführten Anwendung reagieren diese Objekte kooperativ auf Benutzeraktionen, die durch Befehle und andere Nachrichten verbunden sind. Ein einzelnes Anwendungs Objekt verwaltet eine oder mehrere Dokumentvorlagen. Jede Dokument Vorlage erstellt und verwaltet ein oder mehrere Dokumente (abhängig davon, ob die Anwendung SDI oder MDI ist). Der Benutzer zeigt ein Dokument an und bearbeitet es über eine Ansicht, die in einem Rahmen Fenster enthalten ist. Die folgende Abbildung zeigt die Beziehungen zwischen diesen Objekten für eine SDI-Anwendung.

![Objekte in einer laufenden SDI-Anwendung](../mfc/media/vc386v1.gif "Objekte in einer ausgeführten SDI-Anwendung") <br/>
Objekte in einer ausgeführten SDI-Anwendung

Der Rest dieser Artikel Familie erläutert, wie die Framework-Tools, der MFC-Anwendungs-Assistent und die Ressourcen-Editoren diese Objekte erstellen, wie Sie zusammenarbeiten und wie Sie Sie in der Programmierung verwenden. Dokumente, Ansichten und Rahmen Fenster werden in [Fenster Objekten](window-objects.md) und [Dokument-/Ansichtarchitektur](document-view-architecture.md)ausführlicher erläutert.

## <a name="see-also"></a>Siehe auch

[Verwenden der Klassen zum Schreiben von Anwendungen für Windows](using-the-classes-to-write-applications-for-windows.md)
