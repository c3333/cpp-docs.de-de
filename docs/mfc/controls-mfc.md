---
title: Steuerelemente (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: accbee66cdee4e7b849da2b034d253b1c206d8f1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617178"
---
# <a name="controls-mfc"></a>Steuerelemente (MFC)

Steuerelemente stellen Objekte dar, mit denen Benutzer arbeiten können, um Daten einzugeben oder zu ändern. Sie werden im Allgemeinen in Dialogfeldern oder auf Symbolleisten angezeigt. Diese Themenfamilie umfasst drei grundlegende Arten von Steuerelementen:

- Allgemeine Windows-Steuerelemente, einschließlich Ownerdrawn-Schaltflächen

- ActiveX-Steuerelemente

- Andere Steuerelementklassen, die durch die Microsoft Foundation Class-Bibliothek (MFC-Bibliothek) bereitgestellt werden

## <a name="windows-common-controls"></a>Allgemeine Windows-Steuerelemente

Das Windows-Betriebssystem verfügt immer über einige allgemeine Windows-Steuerelemente. Diese Steuerelementobjekte sind programmierbar, und der Dialog-Editor von Visual C++ unterstützt, dass sie in den Dialogfeldern hinzugefügt werden. Die Microsoft Foundation Class-Bibliothek (MFC-Bibliothek) stellt Klassen bereit, die jedes dieser Steuerelemente umfassen. Dies ist in der Tabelle [Allgemeine Windows-Steuerelemente und MFC-Klassen](#_core_windows_common_controls_and_mfc_classes)dargestellt. (Einige Elemente in der Tabelle sind mit Themen verknüpft, in denen sie weiter beschrieben werden. Informationen zu Steuerelementen, die nicht mit Themen verknüpft sind, finden Sie in der Dokumentation für die MFC-Klasse.)

Die Klasse [CWnd](reference/cwnd-class.md) ist die Basisklasse aller Fensterklassen, einschließlich aller Steuerelementklassen.

## <a name="activex-controls"></a>ActiveX-Steuerelemente

ActiveX-Steuerelemente, früher bekannt als OLE-Steuerelemente, können in Dialogfeldern in Anwendungen für Windows oder auf HTML-Seiten im World Wide Web verwendet werden. Weitere Informationen finden Sie unter [MFC-ActiveX](mfc-activex-controls.md)-Steuerelemente.

## <a name="other-mfc-control-classes"></a>Andere MFC-Steuerelementklassen

Zusätzlich zu den Klassen, die alle allgemeinen Windows-Steuerelemente umfassen und die Programmierung eigener ActiveX-Steuerelemente unterstützen (oder ActiveX-Steuerelemente von Drittanbietern verwenden), stellt MFC die folgenden Steuerelementklassen selbst bereit:

- [CBitmapButton](reference/cbitmapbutton-class.md)

- [CCheckListBox](reference/cchecklistbox-class.md)

- [CDragListBox](reference/cdraglistbox-class.md)

## <a name="finding-information-about-windows-common-controls"></a><a name="_core_finding_information_about_windows_common_controls"></a> Suchen von Informationen über allgemeine Windows-Steuerelemente

In der folgenden Tabelle werden die einzelnen allgemeinen Windows-Steuerelemente, einschließlich der MFC-Wrapperklasse des jeweiligen Steuerelements kurz beschrieben.

### <a name="windows-common-controls-and-mfc-classes"></a><a name="_core_windows_common_controls_and_mfc_classes"></a>Allgemeine Windows-Steuerelemente und MFC-Klassen

|Control|MFC-Klasse|Beschreibung|Neu in Windows 95|
|-------------|---------------|-----------------|------------------------|
|[Animationen](using-canimatectrl.md)|[CAnimateCtrl](reference/canimatectrl-class.md)|Zeigt aufeinander folgende Rahmen eines AVI-Videoclips an|Ja|
|Schaltfläche|[CButton](reference/cbutton-class.md)|Druckknöpfe, die eine Aktion auslösen; wird auch für Kontrollkästchen, Optionsfelder und Gruppenfelder verwendet|Nein|
|Kombinationsfeld|[CComboBox](reference/ccombobox-class.md)|Kombination eines Eingabefelds und eines Listenfelds|Nein|
|[Datums-/Zeitauswahl](using-cdatetimectrl.md)|[CDateTimeCtrl](reference/cdatetimectrl-class.md)|Ermöglicht es Benutzern, ein bestimmtes Datum oder einen Zeitwert auszuwählen|Ja|
|Eingabefeld|[CEdit](reference/cedit-class.md)|Felder zum Eingeben von Text|Nein|
|[Erweitertes Kombinationsfeld](using-ccomboboxex.md)|[CComboBoxEx](reference/ccomboboxex-class.md)|Ein Kombinationsfeld-Steuerelement mit der Möglichkeit der Anzeige von Bildern|Ja|
|[Header](using-cheaderctrl.md)|[CHeaderCtrl](reference/cheaderctrl-class.md)|Schaltfläche, die über einer Textspalte angezeigt wird; steuert die Breite des angezeigten Texts|Ja|
|[Hotkey](using-chotkeyctrl.md)|[CHotKeyCtrl](reference/chotkeyctrl-class.md)|Fenster, in dem Benutzer eine "Abkürzungstaste" erstellen können, mit der eine Aktion schnell ausgeführt werden kann|Ja|
|[Bildliste](using-cimagelist.md)|[CImageList](reference/cimagelist-class.md)|Sammlung von Bildern, mit der große Mengen von Symbolen oder Bitmaps verwaltet werden (bei der Bildliste handelt es sich nicht um ein richtiges Steuerelement; es unterstützt die Listen, die von anderen Steuerelementen verwendet werden)|Ja|
|[list](using-clistctrl.md)|[CListCtrl](reference/clistctrl-class.md)|Fenster, in dem eine Liste von Text mit Symbolen anzeigt wird|Ja|
|Listenfeld|[CListBox](reference/clistbox-class.md)|Feld, das eine Liste von Zeichenfolgen enthält|Nein|
|[Monatskalender](using-cmonthcalctrl.md)|[CMonthCalCtrl](reference/cmonthcalctrl-class.md)|Steuerelement, mit dem Datumsinformationen angezeigt werden|Ja|
|[Progress](using-cprogressctrl.md)|[CProgressCtrl](reference/cprogressctrl-class.md)|Fenster, in dem der Status eines langen Vorgangs angezeigt wird|Ja|
|[Infoleiste](using-crebarctrl.md)|[CRebarCtrl](reference/crebarctrl-class.md)|Symbolleiste, die zusätzliche untergeordnete Fenster in Form von Steuerelementen enthalten kann|Ja|
|[Rich-Edit](using-cricheditctrl.md)|[CRichEditCtrl](reference/cricheditctrl-class.md)|Fenster, das ein Benutzer mit Zeichen- und Absatzformatierung bearbeiten kann (siehe [Klassen für Rich-Edit-Steuerelemente](classes-related-to-rich-edit-controls.md))|Ja|
|Bildlaufleiste|[CScrollBar](reference/cscrollbar-class.md)|Bildlaufleiste, die als Steuerelement innerhalb eines Dialogfelds (nicht in einem Fenster) verwendet wird|Nein|
|[keits](using-csliderctrl.md)|[CSliderCtrl](reference/csliderctrl-class.md)|Fenster, das ein Schieberegler-Steuerelement mit optionalen Teilstrichen enthält|Ja|
|[Drehfeld](using-cspinbuttonctrl.md)|[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)|Paar von Pfeilschaltflächen, auf die der Benutzer klicken kann, um einen Wert zu erhöhen oder zu verringern|Ja|
|Statischer Text|[CStatic](reference/cstatic-class.md)|Text für das Bezeichnen anderer Steuerelemente|Nein|
|[Statusleiste](using-cstatusbarctrl.md)|[CStatusBarCtrl](reference/cstatusbarctrl-class.md)|Fenster zum Anzeigen von Statusinformationen, ähnlich der MFC-Klasse `CStatusBar`|Ja|
|[Zeche](using-ctabctrl.md)|[CTabCtrl](reference/ctabctrl-class.md)|Analog den Trennblättern in einem Ordner; wird in Dialogfeldern auf Registerkarten oder in Eigenschaftenblättern verwendet|Ja|
|[Suchfeld](using-ctoolbarctrl.md)|[CToolBarCtrl](reference/ctoolbarctrl-class.md)|Fenster mit den Schaltflächen zum Generieren von Befehlen, ähnlich der MFC-Klasse `CToolBar`|Ja|
|[QuickInfo](using-ctooltipctrl.md)|[CToolTipCtrl](reference/ctooltipctrl-class.md)|Kleines Popupfenster, in dem der Zweck einer Symbolleisten-Schaltfläche oder eines anderen Werkzeugs beschrieben wird|Ja|
|[tree](using-ctreectrl.md)|[CTreeCtrl](reference/ctreectrl-class.md)|Fenster, in dem eine hierarchische Liste von Elementen angezeigt wird|Ja|

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- Ein einzelnes Steuerelement: Links zu allen Steuerelementen finden Sie in der Tabelle [Allgemeine Windows-Steuerelemente und MFC-Klassen](#_core_windows_common_controls_and_mfc_classes) in diesem Thema

- [Erstellen und Verwenden von Steuerelementen](making-and-using-controls.md)

- [Verwenden des Dialog-Editors zum Hinzufügen von Steuerelementen](using-the-dialog-editor-to-add-controls.md)

- [Manuelles Hinzufügen von Steuerelementen in einem Dialogfeld](adding-controls-by-hand.md)

- [Ableiten von Steuerelementklassen von den MFC-Steuerelementklassen](deriving-controls-from-a-standard-control.md)

- [Verwenden von allgemeinen Steuerelementen als untergeordnete Fenster](using-a-common-control-as-a-child-window.md)

- [Benachrichtigungen aus allgemeinen Steuerelementen](receiving-notification-from-common-controls.md)

- [Hinzufügen allgemeiner Steuerelemente zum Dialogfeld](using-common-controls-in-a-dialog-box.md)

- [Berechnen eines Steuerelements aus einem Windows-Standardsteuerelement](deriving-controls-from-a-standard-control.md)

- [Zugriff auf Dialogfeld-Steuerelemente mit Typsicherheit](type-safe-access-to-controls-in-a-dialog-box.md)

- [Empfangen von Benachrichtigungsmeldungen aus den allgemeinen Steuerelementen](receiving-notification-from-common-controls.md)

- [Beispiele](common-control-sample-list.md)

Informationen zu allgemeinen Windows-Steuerelementen in der Windows SDK finden Sie unter [Allgemeine Steuerelemente](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)<br/>
[Dialog-Editor](../windows/dialog-editor.md)
