---
title: In MFC verfügbare abgeleitete Ansichtsklassen
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 12b31074e4fcc2ed6a83e3669e1044f5b9caedab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373504"
---
# <a name="derived-view-classes-available-in-mfc"></a>In MFC verfügbare abgeleitete Ansichtsklassen

Die folgende Tabelle zeigt die Ansichtsklassen von MFC und ihre Beziehungen zueinander. Die Funktionen Ihrer Ansichtsklasse hängen von der MFC-Ansichtsklasse ab, von der sie ableitet.

### <a name="view-classes"></a>Klassen anzeigen

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|Basisklasse aller Ansichten.|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Basisklasse `CTreeView`von `CListView` `CEditView`, `CRichEditView`, und . Mit diesen Klassen können Sie die Dokument-/Ansichtsarchitektur mit den angegebenen allgemeinen Windows-Steuerelementen verwenden.|
|[CEditView](../mfc/reference/ceditview-class.md)|Eine einfache Ansicht basierend auf dem Windows-Bearbeitungsfeldsteuerelement. Ermöglicht die Eingabe und Bearbeitung von Text und kann als Grundlage für eine einfache Texteditor-Anwendung verwendet werden. Siehe auch `CRichEditView`.|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Eine Ansicht, die ein [CRichEditCtrl-Objekt](../mfc/reference/cricheditctrl-class.md) enthält. Diese Klasse ist `CEditView`analog zu `CEditView` `CRichEditView` , aber im Gegensatz zu behandelt formatierten Text.|
|[CListView](../mfc/reference/clistview-class.md)|Eine Ansicht, die ein [CListCtrl-Objekt](../mfc/reference/clistctrl-class.md) enthält.|
|[CTreeView](../mfc/reference/ctreeview-class.md)|Eine Ansicht, die ein [CTreeCtrl-Objekt](../mfc/reference/ctreectrl-class.md) enthält, für Ansichten, die dem Projektmappen-Explorer-Fenster in Visual C++ ähneln.|
|[CScrollView](../mfc/reference/cscrollview-class.md)|Basisklasse `CFormView`von `CRecordView`, `CDaoRecordView`, und . Implementiert das Scrollen des Ansichtsinhalts.|
|[CFormView](../mfc/reference/cformview-class.md)|Eine Formularansicht, eine Ansicht, die Steuerelemente enthält. Eine formularbasierte Anwendung stellt eine oder mehrere solche Formularschnittstellen bereit.|
|[Chtmlview](../mfc/reference/chtmlview-class.md)|Eine Webbrowseransicht, mit der der Benutzer der Anwendung Websites im World Wide Web sowie Ordner im lokalen Dateisystem und in einem Netzwerk durchsuchen kann. Die Webbrowseransicht kann auch als Active-Dokumentcontainer verwendet werden.|
|[CRecordView](../mfc/reference/crecordview-class.md)|Eine Formularansicht, die ODBC-Datenbankdatensätze in Steuerelementen anzeigt. Wenn Sie in Ihrem Projekt ODBC-Unterstützung auswählen, `CRecordView`lautet die Basisklasse der Ansicht . Die Ansicht ist `CRowset` mit einem Objekt verbunden.|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Eine Formularansicht, die DAO-Datenbankdatensätze in Steuerelementen anzeigt. Wenn Sie daO-Unterstützung in Ihrem Projekt auswählen, `CDaoRecordView`lautet die Basisklasse der Ansicht . Die Ansicht ist `CDaoRecordset` mit einem Objekt verbunden.|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Eine Formularansicht, die OLE DB-Datensätze in Steuerelementen anzeigt. Wenn Sie in Ihrem Projekt die OLE DB-Unterstützung `COleDBRecordView`auswählen, lautet die Basisklasse der Ansicht . Die Ansicht ist `CRowset` mit einem Objekt verbunden.|

> [!NOTE]
> Ab MFC Version 4.0 `CEditView` wird `CCtrlView`von abgeleitet.

Um diese Klassen in der Anwendung zu verwenden, leiten Sie die Ansichtsklassen der Anwendung daraus ab. Weitere Informationen finden Sie unter [Scrollen und Skalieren](../mfc/scrolling-and-scaling-views.md)von Ansichten . Weitere Informationen zu den Datenbankklassen finden Sie unter [Übersicht: Datenbankprogrammierung](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Siehe auch

[Verwenden von Ansichten](../mfc/using-views.md)
