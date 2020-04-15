---
title: Beziehungen zwischen MFC-Objekten
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: d7e40e25b405d3f8ec50a518889cc2b89bc8c725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372814"
---
# <a name="relationships-among-mfc-objects"></a>Beziehungen zwischen MFC-Objekten

Um den Erstellungsprozess des Dokuments/der Ansicht zu relativieren, sollten Sie ein laufendes Programm in Betracht ziehen: ein Dokument, das Rahmenfenster, das die Ansicht enthält, und die dem Dokument zugeordnete Ansicht.

- Ein Dokument enthält eine Liste der Ansichten dieses Dokuments und einen Zeiger auf die Dokumentvorlage, die das Dokument erstellt hat.

- Eine Ansicht hält einen Zeiger auf das Dokument und ist ein untergeordnetes Element des übergeordneten Rahmenfensters.

- Ein Dokumentrahmenfenster hält einen Zeiger auf die aktuelle aktive Ansicht.

- Eine Dokumentvorlage enthält eine Liste der geöffneten Dokumente.

- Die Anwendung führt eine Liste ihrer Dokumentvorlagen.

- Windows verfolgt alle geöffneten Fenster, damit es Nachrichten an sie senden kann.

Diese Beziehungen werden während der Dokument-/Ansichtserstellung eingerichtet. Die folgende Tabelle zeigt, wie Objekte in einem laufenden Programm auf andere Objekte zugreifen können. Jedes Objekt kann einen Zeiger auf das Anwendungsobjekt abrufen, indem es die globale Funktion [AfxGetApp aufruft.](../mfc/reference/application-information-and-management.md#afxgetapp)

### <a name="gaining-access-to-other-objects-in-your-application"></a>Zugriff auf andere Objekte in Ihrer Anwendung

|Vom Objekt|So greifen Sie auf andere Objekte zu|
|-----------------|---------------------------------|
|Dokument|Verwenden Sie [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) und [GetNextView,](../mfc/reference/cdocument-class.md#getnextview) um auf die Ansichtsliste des Dokuments zuzugreifen.<br /><br /> Rufen Sie [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) auf, um die Dokumentvorlage abzurufen.|
|Sicht|Rufen Sie [GetDocument](../mfc/reference/cview-class.md#getdocument) auf, um das Dokument abzurufen.<br /><br /> Rufen Sie [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) auf, um das Rahmenfenster abzurufen.|
|Dokumentrahmenfenster|Rufen Sie [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) auf, um die aktuelle Ansicht abzurufen.<br /><br /> Rufen Sie [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) auf, um das Dokument an die aktuelle Ansicht anzuhängen.|
|MDI-Rahmenfenster|Rufen Sie [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) auf, um den aktuell aktiven [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)abzurufen.|

In der Regel verfügt ein Rahmenfenster über eine Ansicht, aber manchmal enthält dasselbe Rahmenfenster, wie in Splitterfenstern, mehrere Ansichten. Das Rahmenfenster hält einen Zeiger auf die aktuell aktive Ansicht. Der Zeiger wird jedes Mal aktualisiert, wenn eine andere Ansicht aktiviert wird.

> [!NOTE]
> Ein Zeiger auf das Hauptrahmenfenster wird in der [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) Membervariable des Anwendungsobjekts gespeichert. Ein Aufruf `OnFileNew` in Ihrer Außerkraftsetzung `InitInstance` `CWinApp` der Memberfunktion von Sets *m_pMainWnd* für Sie. Wenn Sie nicht `OnFileNew`aufrufen, müssen Sie den `InitInstance` Wert der Variablen in sich selbst festlegen. (SDI COM-Komponentenanwendungen (Serveranwendungen) können die Variable nicht festlegen, wenn sich /Embedding in der Befehlszeile befindet.) Beachten Sie, dass *m_pMainWnd* `CWinThread` jetzt `CWinApp`ein Member der Klasse und nicht .

## <a name="see-also"></a>Siehe auch

[Dokumentvorlagen und der Erstellungsvorgang für Dokumente und Ansichten](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Erstellen von Dokumentvorlagen](../mfc/document-template-creation.md)<br/>
[Erstellen von Dokument/Ansicht](../mfc/document-view-creation.md)<br/>
[Erstellen neuer Dokumente, Fenster und Ansichten](../mfc/creating-new-documents-windows-and-views.md)
