---
title: In MFC verfügbare abgeleitete Ansichtsklassen
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: dc0f0b10ea291db32c576a7d36b7fc19728fa6ce
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616985"
---
# <a name="derived-view-classes-available-in-mfc"></a>In MFC verfügbare abgeleitete Ansichtsklassen

In der folgenden Tabelle werden die Ansichts Klassen von MFC und deren Beziehungen zueinander aufgeführt. Die Funktionen der Ansichts Klasse hängen von der MFC-Ansichts Klasse ab, von der Sie abgeleitet ist.

### <a name="view-classes"></a>Klassen anzeigen

|Klasse|Beschreibung|
|-----------|-----------------|
|[CView](reference/cview-class.md)|Basisklasse aller Ansichten.|
|[CCtrlView](reference/cctrlview-class.md)|Basisklasse von `CTreeView` , `CListView` , `CEditView` und `CRichEditView` . Mit diesen Klassen können Sie die Dokument-/Ansichtsarchitektur mit den genannten allgemeinen Windows-Steuerelementen verwenden.|
|[CEditView](reference/ceditview-class.md)|Eine einfache Ansicht, die auf dem Windows-Bearbeitungsfeld-Steuerelement basiert. Ermöglicht das eingeben und Bearbeiten von Text und kann als Grundlage für eine einfache Text-Editor-Anwendung verwendet werden. Siehe auch `CRichEditView`.|
|[CRichEditView](reference/cricheditview-class.md)|Eine Ansicht, die ein [CRichEditCtrl](reference/cricheditctrl-class.md) -Objekt enthält. Diese Klasse ist analog zu `CEditView` , aber im Gegensatz zu `CEditView` `CRichEditView` behandelt formatierten Text.|
|[CListView](reference/clistview-class.md)|Eine Ansicht, die ein [CListCtrl](reference/clistctrl-class.md) -Objekt enthält.|
|[CTreeView](reference/ctreeview-class.md)|Eine Ansicht, die ein [CTreeCtrl](reference/ctreectrl-class.md) -Objekt enthält, für Sichten, die dem Projektmappen-Explorer Fenster in Visual C++ ähneln.|
|[CScrollView](reference/cscrollview-class.md)|Basisklasse von `CFormView` , `CRecordView` und `CDaoRecordView` . Implementiert den Bildlauf für den Inhalt der Ansicht.|
|[CFormView](reference/cformview-class.md)|Eine Formularansicht, eine Ansicht, die-Steuerelemente enthält. Eine Formular basierte Anwendung stellt eine oder mehrere derartige Formular Schnittstellen bereit.|
|[CHtmlView](reference/chtmlview-class.md)|Eine Webbrowser Ansicht, mit der der Benutzer der Anwendung Websites auf dem World Wide Web durchsuchen kann, sowie Ordner im lokalen Dateisystem und in einem Netzwerk. Die Webbrowser Ansicht kann auch als aktiver Dokument Container verwendet werden.|
|[CRecordView](reference/crecordview-class.md)|Eine Formularansicht, in der ODBC-Datensätze in Steuerelementen angezeigt werden. Wenn Sie die ODBC-Unterstützung in Ihrem Projekt auswählen, ist die Basisklasse der Sicht `CRecordView` . Die Sicht ist mit einem- `CRowset` Objekt verbunden.|
|[CDaoRecordView](reference/cdaorecordview-class.md)|Eine Formularansicht, in der DAO-Datensätze in Steuerelementen angezeigt werden. Wenn Sie in Ihrem Projekt DAO-Unterstützung auswählen, ist die Basisklasse der Sicht `CDaoRecordView` . Die Sicht ist mit einem- `CDaoRecordset` Objekt verbunden.|
|[COleDBRecordView](reference/coledbrecordview-class.md)|Eine Formularansicht, die OLE DB Datensätze in Steuerelementen anzeigt. Wenn Sie OLE DB-Unterstützung in Ihrem Projekt auswählen, ist die Basisklasse der Sicht `COleDBRecordView` . Die Sicht ist mit einem- `CRowset` Objekt verbunden.|

> [!NOTE]
> Ab MFC-Version 4,0 `CEditView` wird von abgeleitet `CCtrlView` .

Um diese Klassen in der Anwendung zu verwenden, leiten Sie die Ansichts Klassen der Anwendung von Ihnen ab. Weitere Informationen finden Sie unter [scrollen und Skalieren von Sichten](scrolling-and-scaling-views.md). Weitere Informationen zu den Datenbankklassen finden Sie unter [Übersicht: Datenbankprogrammierung](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Siehe auch

[Verwenden von Ansichten](using-views.md)
