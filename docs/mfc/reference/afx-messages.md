---
title: AFX-Meldungen
ms.date: 11/04/2016
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: b4ed86c11d3c5b5f1ce38e3146533109f3a6b00d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363595"
---
# <a name="afx-messages"></a>AFX-Meldungen

Diese Meldungen werden in MFC verwendet.

## <a name="messages"></a>Meldungen

In der folgenden Tabelle sind Nachrichten aufgeführt, die in der MFC-Bibliothek verwendet werden:

||||||
|-|-|-|-|-|
|`Message`|BESCHREIBUNG|[in] *wParam*|*lParam* (Alle Parameter sind [in], sofern nicht anders angegeben.)|Rückgabewert|
|AFX_WM_ACCGETOBJECT|Wird nicht verwendet.|Wird nicht verwendet.|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_ACCGETSTATE|Wird für die Barrierefreiheitsunterstützung verwendet. Senden Sie `CMFCPopupMenu` diese `CMFCRibbonPanelMenu` Nachricht an das aktuelle Element oder , um den Status des aktuellen Elements abzurufen.|Index des Elements, der eine Menüschaltfläche oder ein Trennzeichen sein kann.|Wird nicht verwendet.|Der Elementstatus. Es ist -1, wenn der Index ungültig ist, 0, wenn die Menüschaltfläche keine speziellen Attribute hat. Andernfalls handelt es sich um eine Kombination der folgenden Flags:<br /><br /> TBBS_DISABLED — Element ist deaktiviert<br /><br /> TBBS_CHECKED — Artikel wird geprüft<br /><br /> TBBS_BUTTON — der Artikel ist ein Standard-Taster<br /><br /> TBBS_PRESSED — Taste wird gedrückt<br /><br /> TBBS_INDETERMINATE — nicht definierter Zustand<br /><br /> TBBS_SEPARATOR - anstelle einer Menüschaltfläche bildet dieses Element eine Trennung zwischen anderen Menüelementen|
|AFX_WM_CHANGE_ACTIVE_TAB|Das Framework sendet diese Nachricht an das Steuerelement der geänderten Steuerleiste. Verarbeiten Sie diese Nachricht, `CMFCTabCtrl` um Benachrichtigungen von Objekten zu erhalten, wenn ein Benutzer eine aktive Registerkarte ändert.|Der Index einer Registerkarte.|Wird nicht verwendet.|Nonzero.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Das Framework sendet diese Nachricht `CMFCShellListCtrl` an das übergeordnete Element, wenn der Benutzer den aktuellen Ordner geändert hat.|Wird nicht verwendet.|Wird nicht verwendet.|Wird nicht verwendet.|
|AFX_WM_CHANGEVISUALMANAGER|Das Framework sendet diese Nachricht an alle Rahmenfenster, wenn der Benutzer den aktuellen Visual Manager ändert. Als Reaktion auf diese Meldung berechnet ein Rahmenfenster seinen Bereich neu und passt andere Parameter nach Bedarf an. Sie können die AFX_WM_CHANGEVISUALMANAGER Nachricht in Ihrer Anwendung verarbeiten, wenn Sie über dieses Ereignis benachrichtigt werden müssen. Sie müssen den Basisklassenhandler (`OnChangeVisualManager`) aufrufen, um sicherzustellen, dass die interne Verarbeitung dieses Ereignisses durch das Framework stattfindet.|Wird nicht verwendet.|Wird nicht verwendet.|Wird nicht verwendet.|
|AFX_WM_CHANGING_ACTIVE_TAB|Wird an das `CMFCTabCtrl` übergeordnete Objekt gesendet.  Verarbeiten Sie diese Meldung, wenn `CMFCTabCtrl` Sie Benachrichtigungen von Objekten erhalten möchten, wenn ein Benutzer eine Registerkarte zurücksetzt.|Der Index der Registerkarte, die aktiviert wird.|Wird nicht verwendet.|Nonzero.|
|AFX_WM_CHECKEMPTYMINIFRAME|Nur zur internen Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_CREATETOOLBAR|Gesendet `CMFCToolBarsListPropertyPage` von, wenn ein Benutzer während des Anpassungsprozesses eine neue Symbolleiste erstellt. Sie können diese Nachricht verarbeiten, um ein benutzerdefiniertes CMFCToolBar-abgeleitetes Objekt zu instanziieren. Wenn Sie diese Nachricht behandeln und eine eigene Symbolleiste erstellen, lassen Sie den Aufruf an den Standardhandler weg.|Wird nicht verwendet.|Ein Zeiger auf eine Zeichenfolge, die den Namen der Symbolleiste enthält.|Ein Zeiger auf die neu erstellte Symbolleiste. NULL gibt an, dass die Symbolleistenerstellung abgebrochen wurde.|
|AFX_WM_CUSTOMIZEHELP|Wird vom Anpassungseigenschaftenblatt `CMFCToolbarCustomize Dialog` an das Hauptrahmenfenster gesendet, wenn der Benutzer die **Hilfetaste** oder die F1-Taste drückt.|Gibt die aktive Seite des Anpassungseigenschaftenblatts an.|Ein Zeiger auf ein `CMFCToolbarCustomize Dialog`-Objekt.|Keinen.|
|AFX_WM_CUSTOMIZETOOLBAR|Der `CMFCToolbarCustomize Dialog` sendet diese Nachricht, um den übergeordneten Frame darüber zu informieren, dass der Benutzer eine neue Symbolleiste erstellt.|TRUE beim Starten der Anpassung, FALSE, wenn die Anpassung abgeschlossen ist.|Wird nicht verwendet.|Keinen.|
|AFX_WM_DELETETOOLBAR|Wird an das Hauptrahmenfenster gesendet, wenn der Benutzer eine Symbolleiste im Anpassungsmodus löschen möchte.<br /><br /> Verarbeiten Sie diese Meldung, um zusätzliche Aktionen auszuführen, wenn ein Benutzer eine Symbolleiste im Anpassungsmodus löscht. Sie sollten auch den`OnToolbarDelete`Standardhandler ( ) aufrufen, der die Symbolleiste löscht. Der Standardhandler gibt einen Wert zurück, der angibt, ob es möglich ist, die Symbolleiste zu löschen.|Wird nicht verwendet.|Zeiger auf `CMFCToolBar` ein zu löschendes Objekt.|Ein Wert ungleich Null, wenn eine Symbolleiste nicht gelöscht werden kann. andernfalls 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`sendet diese Nachricht an das Hauptrahmenfenster, um die Dokumentfarben abzurufen.|Wird nicht verwendet.|[in, out] Zeiger auf `CList<COLORREF, COLORREF>` ein Objekt.|Keinen.|
|AFX_WM_GETDRAGBOUNDS|Nur zur internen Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Wird an das Hauptrahmenfenster gesendet, wenn ein Benutzer ein Menübandlistenelement hervorhebt.|Index des hervorgehobenen Elements|Ein Zeiger auf`CMFCBaseRibbonElement`|Wird nicht verwendet.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Wird an ein `CMFCShellListCtrl` `CMFCShellTreeCtrl` übergeordnetes Element oder Steuerelemente gesendet, wenn ein Benutzer die Ausführung eines Shellbefehls beendet.|Die ID des Befehls, den der Benutzer ausgeführt hat|Wird nicht verwendet.|Wenn die Anwendung diese Meldung verarbeitet, sollte sie Null zurückgeben.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Das Framework sendet diese Nachricht an das übergeordnete Menü des Menübands, bevor es das Popupmenü anzeigt. Sie können diese Meldung jederzeit verarbeiten und Popupmenüs ändern.|Wird nicht verwendet.|Ein Zeiger auf`CMFCBaseRibbonElement`|Wird nicht verwendet.|
|AFX_WM_ON_CANCELTABMOVE|Nur zur internen Verwendung.|Nicht zutreffend|Nicht zutreffend||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Das Framework sendet diese Nachricht an den Hauptframe, wenn der Benutzer die aktive Kategorie "Multifunktionsleistensteuerung" ändert.|Wird nicht verwendet.|Ein Zeiger auf `CMFCRibbonBar` die Kategorie, deren Kategorie geändert wurde.|Wird nicht verwendet.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Das Framework sendet diese Nachricht, `CMFCDesktopAlertWnd` um den Besitzer darüber zu informieren, dass das Fenster kurz vor dem Schließen steht.|Wird nicht verwendet.|Ein Zeiger `CMFCDesktopAlertWnd` auf das Objekt.|Wird nicht verwendet.|
|AFX_WM_ON_DRAGCOMPLETE|Nur zur internen Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_ON_GET_TAB_TOOLTIP|Wird an das Hauptrahmenfenster gesendet, wenn ein Registerkartenfenster eine QuickInfo für eine Registerkarte anzeigen soll, wenn benutzerdefinierte QuickInfos aktiviert sind.|Wird nicht verwendet.|Ein Zeiger auf `CMFCTabToolTipInfo` eine Struktur.|Wird nicht verwendet.|
|AFX_WM_ON_HSCROLL|Wird an die steuerbare Steuerelementsteuerung gesendet. Verarbeiten Sie diese Nachricht, `CMFCTabCtrl` um Benachrichtigungen von Objekten zu erhalten, wenn ein Bildlaufereignis in der horizontalen Bildlaufleiste des Widgets mit Registerkarten auftritt.|Das Wort niedriger Ordnung gibt einen Bildlaufleistenwert an, der die Bildlaufanforderung des Benutzers angibt.  Weitere Informationen finden Sie in der Tabelle weiter unten in diesem Thema.|Wird nicht verwendet.|Nonzero.|
|AFX_WM_ON_MOVE_TAB|Wird an das übergeordnete Element eines Registerkartenfensters gesendet, wenn ein Benutzer eine Registerkarte an eine neue Position zieht.|Der Null-basierte Index der Registerkarte in ihrer ursprünglichen Position.|[out] Der Null-basierte Index der Registerkarte in seiner neuen Position.|Keinen.|
|AFX_WM_ON_MOVETABCOMPLETE|Nur zur internen Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_ON_MOVETOTABGROUP|Wird an das Hauptrahmenfenster gesendet, wenn ein Benutzer ein untergeordnetes MDI-Fenster von einer Registerkartengruppe in eine andere verschiebt.|Ein Handle für das`CMFCTabCtrl`Registerkartenfenster ( ), aus dem das untergeordnete MDI-Fenster entfernt wurde.|[out] Ein Handle für das`CMFCTabCtrl`Registerkartenfenster ( ), in das das untergeordnete MDI-Fenster eingefügt wurde.|Ignoriert.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Wird an ein `CDockablePane` übergeordnetes Element gesendet, wenn der Benutzer auf die Schaltfläche **Schließen** in der Beschriftung der Steuerleiste klickt.|Wird nicht verwendet.|Ein Zeiger auf einen andockbaren Bereich, auf den der Benutzer auf die Schaltfläche **Schließen** geklickt hat.|TRUE, wenn ein Bereich nicht geschlossen werden kann; andernfalls FALSE.|
|AFX_WM_ON_RENAME_TAB|Wird an das übergeordnete Fenster des Registerkartenfensters gesendet, nachdem der Benutzer eine bearbeitbare Registerkarte umbenannt hat.|Der nullbasierte Index der umbenannten Registerkarte.|[out] Ein Zeiger auf eine Zeichenfolge, die den neuen Registerkartennamen enthält.|Ein Wert ungleich Null, wenn die Anwendung diese Meldung verarbeitet; Das Framework unterdrückt den `CMFCBaseTabCtrl::SetTabLabel`Aufruf von .  Wenn Null zurückgegeben `CMFCBaseTabCtrl::SetTabLabel` wird, wird das Framework aufgerufen.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Wird an den übergeordneten Frame gesendet, wenn der Benutzer mit der Anpassung beginnt. Verarbeiten Sie diese Meldung, wenn Sie Ihr eigenes Anpassungsdialogfeld anzeigen möchten.|Wird nicht verwendet.|Ein Zeiger auf das zu benutzerdefinierte Menübandsteuerelement.|Ein Wert ungleich Null, wenn die Anwendung diese Meldung verarbeitet und ein eigenes Anpassungsdialogfeld anzeigt. Wenn die Anwendung Null zurückgibt, zeigt das Framework das integrierte Anpassungsdialogfeld an.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Nur zur internen Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_POSTSETPREVIEWFRAME|Gesendet, um den Hauptframe zu benachrichtigen, dass der Benutzer den Druckvorschaumodus geändert hat|TRUE gibt an, dass der Druckvorschaumodus eingestellt ist. FALSE gibt an, dass der Druckvorschaumodus deaktiviert ist.|Wird nicht verwendet.|Wird nicht verwendet.|
|AFX_WM_PROPERTY_CHANGED|Wird an den Besitzer des`CMFCPropertyGridCtrl`Eigenschaftenrastersteuerelements ( ) gesendet, wenn der Benutzer den Wert der ausgewählten Eigenschaft ändert.|Die Steuerelement-ID der Eigenschaftenliste.|Ein Zeiger auf die`CMFCPropertyGridProperty`Eigenschaft ( ), die sich geändert hat.|Wird nicht verwendet.|
|AFX_WM_RESETCONTEXTMENU|Wird an das Hauptrahmenfenster gesendet, wenn der Benutzer das Kontextmenü während der Anpassung zurücksetzt.|Die Ressourcen-ID des Kontextmenüs.|Ein Zeiger auf das aktuelle `CMFCPopupMenu`Kontextmenü , .|Wird nicht verwendet.|
|AFX_WM_RESETKEYBOARD|Das Framework sendet diese Nachricht an das Hauptrahmenfenster, wenn der Benutzer während der Anpassung alle Tastaturbeschleuniger zurücksetzt.|Wird nicht verwendet.|Wird nicht verwendet.|Wird nicht verwendet.|
|AFX_WM_RESETMENU|Das Framework sendet diese Nachricht an den Menübesitzer (ein Rahmenfenster), wenn der Benutzer während der Anpassung ein Anwendungsrahmenmenü zurücksetzt.|Die Menüressourcen-ID.|Wird nicht verwendet.|Wird nicht verwendet.|
|AFX_WM_RESETPROMPT|Das Framework sendet diese Meldung, wenn der Benutzer eine Symbolleiste aus dem Dialogfeld "Anpassen der Symbolleiste" zurücksetzt. Der Standardhandler zeigt ein Meldungsfeld an, in dem gefragt wird, ob der Benutzer die Symbolleiste zurücksetzen möchte.|Wird nicht verwendet.|Wird nicht verwendet.|Wird nicht verwendet.|
|AFX_WM_RESETTOOLBAR|Ein `CMFCToolBar` Objekt sendet diese Nachricht, wenn eine Symbolleiste in ihren ursprünglichen Zustand wiederhergestellt wird, d. h. aus den Ressourcen geladen wird. Verarbeiten Sie diese Meldung, um Symbolleistenschaltflächen erneut einzufügen, deren Klassen von `CMFCToolbarButton`abgeleitet sind. Weitere Informationen finden Sie unter `CMFCToolbarComboBoxButton`.|Die Ressourcen-ID einer Symbolleiste, deren Status wiederhergestellt wurde.|Wird nicht verwendet.|Keinen.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`Das Objekt sendet diese Nachricht an seinen Besitzer, wenn der Benutzer auf eine normale Menüschaltfläche klickt. Verarbeiten Sie diese Meldung `CMFCToolbarMenuButton` jedes Mal, wenn Sie ein Popupmenü anzeigen, wenn der Benutzer auf eine Schaltfläche klickt.|Die Befehls-ID einer Schaltfläche, die die Nachricht sendet.|Bildschirmkoordinaten des Cursors. Das Wort niedriger Ordnung gibt die x-Koordinate an. Das Wort hoher Ordnung gibt die y-Koordinate an.|Wird nicht verwendet.|
|AFX_WM_TOOLBARMENU|Wird an das Hauptbildfenster gesendet, wenn der Benutzer die rechte Maustaste loslässt, während sich der Mauszeiger im Client- oder Nicht-Clientbereich eines Bereichs befindet.|Wird nicht verwendet.|Bildschirmkoordinaten des Mauszeigers. Das Wort niedriger Ordnung gibt die x-Koordinate an. Das Wort hoher Ordnung gibt die y-Koordinate an.|Null, wenn die Anwendung diese Meldung verarbeitet; andernfalls ungleich Null.|
|AFX_WM_UPDATETOOLTIPS|Wird an alle QuickInfo-Besitzer gesendet, um anzugeben, dass ihre QuickInfo-Steuerelemente neu erstellt werden sollen.|Der Typ des Steuerelements, das diese Nachricht verarbeiten soll. Eine Liste möglicher Werte finden Sie in der Tabelle weiter unten in diesem Thema.|Wird nicht verwendet.|Wird nicht verwendet.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`sendet diese Nachricht an den übergeordneten Frame, wenn der Benutzer auf die **Hilfeschaltfläche** klickt oder in den Hilfemodus wechselt, indem er auf die Schaltfläche **"Hilfebeschriftung"** oder die F1-Taste klickt.|Wird nicht verwendet.|Ein Zeiger auf die `CMFCWindowsManagerDialog`Instanz von .|Wird nicht verwendet.|

Die folgende Tabelle zeigt die Werte für das niedrige Wort des *lParam-Parameters* der AFX_WM_HSCROLL-Methode:

|||
|-|-|
|Wert|Bedeutung|
|SB_ENDSCROLL|Der Benutzer beendet den Bildlauf.|
|SB_LEFT|Der Benutzer scrollt nach links oben.|
|SB_RIGHT|Der Benutzer scrollt nach unten rechts.|
|SB_LINELEFT|Der Benutzer scrollt von einer Einheit links.|
|SB_LINERIGHT|Der Benutzer scrollt nach rechts um eine Einheit.|
|SB_PAGELEFT|Der Benutzer scrollt links durch die Breite des Fensters.|
|SB_PAGERIGHT|Der Benutzer scrollt nach rechts durch die Breite des Fensters.|
|SB_THUMBPOSITION|Der Benutzer hat das Bildlauffeld (Daumen) gezogen und die Maustaste losgelassen. Das Wort hoher Ordnung gibt die Position des Bildlauffelds am Ende des Ziehvorgangs an.|
|SB_THUMBTRACK|Der Benutzer zieht die Bildlaufbox. Die AFX_WM_ON_HSCROLL Nachricht wird wiederholt mit diesem Wert gesendet, bis der Benutzer die Maustaste loslässt. Das Wort hoher Ordnung gibt die Position an, an die das Bildlauffeld gezogen wurde.|

> [!NOTE]
> Das Hochrangwort des *Parameters lParam* gibt die aktuelle Position des Bildlauffelds an, wenn das Wort niedriger Ordnung SB_THUMBPOSITION oder SB_THUMBTRACK ist. Andernfalls wird dieses Wort nicht verwendet.

In der folgenden Tabelle sind die Flagwerte für den *LParam-Parameter* der AFX_WM_UPDATETOOLTIPS-Meldung aufgeführt:

|||
|-|-|
|Flag|Wert|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xffff|

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
