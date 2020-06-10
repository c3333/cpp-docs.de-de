---
title: Steuerelementklassen
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: 277802bff3e4833396c4bf114ff8880fcd26343d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622999"
---
# <a name="control-classes"></a>Steuerelementklassen

Steuerelement Klassen Kapseln eine Vielzahl von standardmäßigen Windows-Steuerelementen, die von statischen Text Steuerelementen bis hin zu Struktur Steuerelementen reichen. Außerdem bietet MFC einige neue Steuerelemente, einschließlich Schaltflächen mit Bitmaps und Steuer leisten.

Die Steuerelemente, deren Klassennamen auf "**STRG**" enden, waren in Windows 95 und Windows NT Version 3,51 neu.

## <a name="static-display-controls"></a>Statische Anzeige Steuerelemente

[CStatic](reference/cstatic-class.md)<br/>
Ein statisches Anzeige Fenster. Statische Steuerelemente werden verwendet, um andere Steuerelemente in einem Dialogfeld oder Fenster zu beschriften, zu unterteilen oder zu trennen. Sie können auch grafische Bilder anstelle von Text oder Box anzeigen.

## <a name="text-controls"></a>Text Steuerelemente

[CEdit](reference/cedit-class.md)<br/>
Ein Editier bares Text Steuerelement Fenster. Bearbeitungs Steuerelemente werden verwendet, um Texteingaben vom Benutzer zu akzeptieren.

[CIPAddressCtrl](reference/cipaddressctrl-class.md)<br/>
Unterstützt ein Bearbeitungsfeld zum Bearbeiten einer IP-Adresse (Internet Protocol).

[CRichEditCtrl](reference/cricheditctrl-class.md)<br/>
Ein Steuerelement, in dem der Benutzer Text eingeben und bearbeiten kann. Anders als das in gekapselte Steuerelement `CEdit` unterstützt ein Rich Edit-Steuerelement Zeichen-und Absatz Formatierung sowie OLE-Objekte

## <a name="controls-that-represent-numbers"></a>Steuerelemente, die Zahlen darstellen

[CSliderCtrl](reference/csliderctrl-class.md)<br/>
Ein Steuerelement, das einen Schieberegler enthält, den der Benutzer zum Auswählen eines Werts oder einer Gruppe von Werten verschiebt.

[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)<br/>
Ein paar von Pfeil Schaltflächen, auf die der Benutzer klicken kann, um einen Wert zu erhöhen oder zu verringern.

[CProgressCtrl](reference/cprogressctrl-class.md)<br/>
Zeigt ein Rechteck an, das allmählich von links nach rechts aufgefüllt wird, um den Fortschritt eines Vorgangs anzuzeigen.

[CScrollBar](reference/cscrollbar-class.md)<br/>
Ein ScrollBar-Steuerelement Fenster. Die-Klasse stellt die Funktionalität einer Schiebe Leiste zur Verfügung, die als Steuerelement in einem Dialogfeld oder Fenster verwendet werden kann, über das der Benutzer eine Position innerhalb eines Bereichs angeben kann.

## <a name="buttons"></a>Schaltflächen

[CButton](reference/cbutton-class.md)<br/>
Ein Schaltflächen-Steuerelement Fenster. Die-Klasse stellt eine programmgesteuerte Schnittstelle für eine Schaltfläche, ein Kontrollkästchen oder ein Optionsfeld in einem Dialogfeld oder Fenster bereit.

[CBitmapButton](reference/cbitmapbutton-class.md)<br/>
Eine Schaltfläche mit einer Bitmap anstelle einer Text Beschriftung.

## <a name="lists"></a>Listen

[CListBox](reference/clistbox-class.md)<br/>
Ein Listenfeld-Steuerelement Fenster. Ein Listenfeld zeigt eine Liste von Elementen an, die der Benutzer anzeigen und auswählen kann.

[CDragListBox](reference/cdraglistbox-class.md)<br/>
Stellt die Funktionalität eines Windows-Listen Felds bereit. ermöglicht dem Benutzer das Verschieben von Listenfeld Elementen, z. b. Dateinamen und Zeichenfolgenliteralen, innerhalb des Listen Felds. Listenfelder mit dieser Funktion sind für eine Elementliste in einer anderen Reihenfolge als alphabetisch, z. b. beim Einschließen von Pfadnamen oder Dateien in einem Projekt.

[CComboBox](reference/ccombobox-class.md)<br/>
Ein Kombinations Feld-Steuerelement Fenster. Ein Kombinations Feld besteht aus einem Bearbeitungs Steuerelement plus einem Listenfeld.

[CComboBoxEx](reference/ccomboboxex-class.md)<br/>
Erweitert das Kombinationsfeld-Steuerelement durch die Unterstützung für Bildlisten.

[CCheckListBox](reference/cchecklistbox-class.md)<br/>
Zeigt eine Liste von Elementen mit Kontrollkästchen an, die der Benutzer neben jedem Element überprüfen oder deaktivieren kann.

[CListCtrl](reference/clistctrl-class.md)<br/>
Zeigt eine Auflistung von Elementen an, die jeweils aus einem Symbol und einer Bezeichnung bestehen, ähnlich wie im rechten Bereich des Datei-Explorers.

[CTreeCtrl](reference/ctreectrl-class.md)<br/>
Zeigt eine hierarchische Liste von Symbolen und Bezeichnungen ähnlich wie im linken Bereich des Datei-Explorers an.

## <a name="toolbars-and-status-bars"></a>Symbolleisten und Status leisten

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Stellt die Funktionalität des allgemeinen Windows-Symbolleisten-Steuerelements bereit. Die meisten MFC-Programme verwenden die [CToolBar](reference/ctoolbar-class.md) anstelle dieser Klasse.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
Ein horizontales Fenster, das normalerweise in Bereiche unterteilt ist, in denen eine Anwendung Statusinformationen anzeigen kann. Die meisten MFC-Programme verwenden [CStatusBar](reference/cstatusbar-class.md) anstelle dieser Klasse.

## <a name="miscellaneous-controls"></a>Verschiedene Steuerelemente

[CAnimateCtrl](reference/canimatectrl-class.md)<br/>
Zeigt einen einfachen Videoclip an.

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
Ein kleines Popup Fenster, das eine einzelne Textzeile anzeigt, die den Zweck eines Tools in einer Anwendung beschreibt.

[CDateTimeCtrl](reference/cdatetimectrl-class.md)<br/>
Unterstützt entweder ein erweitertes Bearbeitungs Steuerelement oder ein einfaches Steuerelement für die Kalender Schnittstelle, mit dem Benutzer einen bestimmten Datums-oder Uhrzeitwert auswählen können.

[CHeaderCtrl](reference/cheaderctrl-class.md)<br/>
Zeigt Titel oder Bezeichnungen für Spalten an.

[CMonthCalCtrl](reference/cmonthcalctrl-class.md)<br/>
Unterstützt ein einfaches Calendar Interface-Steuerelement, mit dem ein Benutzer ein Datum auswählen kann.

[CTabCtrl](reference/ctabctrl-class.md)<br/>
Ein Steuerelement mit Registerkarten, auf die der Benutzer klicken kann, analog zu den unter Teilern in einem Notebook.

[CHotKeyCtrl](reference/chotkeyctrl-class.md)<br/>
Ermöglicht es dem Benutzer, eine Tastenkombination zu erstellen, die der Benutzer drücken kann, um eine Aktion schnell auszuführen.

[CLinkCtrl](reference/clinkctrl-class.md)<br/>
Rendert markierten Text und öffnet geeignete Anwendungen, wenn der Benutzer auf den eingebetteten Link klickt.

[CHtmlEditCtrl](reference/chtmleditctrl-class.md)<br/>
Stellt die Funktionalität des WebBrowser-ActiveX-Steuerelements in einem MFC-Fenster bereit.

## <a name="related-classes"></a>Verwandte Klassen

[CImageList](reference/cimagelist-class.md)<br/>
Stellt die Funktionalität der Windows-Bildliste bereit. Bildlisten werden mit Listen Steuerelementen und Struktur Steuerelementen verwendet. Sie können auch zum Speichern und Archivieren eines Satzes von Bitmaps gleicher Größen verwendet werden.

[CCtrlView](reference/cctrlview-class.md)<br/>
Die Basisklasse für alle Sichten, die Windows-Steuerelementen zugeordnet sind. Die Sichten, die auf-Steuerelementen basieren, werden unten beschrieben.

[CEditView](reference/ceditview-class.md)<br/>
Eine Ansicht, die ein Windows-Standard Bearbeitungs Steuerelement enthält.

[CRichEditView](reference/cricheditview-class.md)<br/>
Eine Ansicht, die ein umfassendes Windows-Bearbeitungs Steuerelement enthält.

[CListView](reference/clistview-class.md)<br/>
Eine Ansicht, die ein Windows-Listen Steuerelement enthält.

[CTreeView](reference/ctreeview-class.md)<br/>
Eine Ansicht, die ein Windows Tree-Steuerelement enthält.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
