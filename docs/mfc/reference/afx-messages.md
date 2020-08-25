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
ms.openlocfilehash: 409760eff6ba6b31413c11fb45ea91a6d07b9485
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832398"
---
# <a name="afx-messages"></a>AFX-Meldungen

Diese Nachrichten werden in MFC verwendet.

## <a name="messages"></a>Meldungen

In der folgenden Tabelle sind die in der MFC-Bibliothek verwendeten Meldungen aufgeführt:

|`Message`|BESCHREIBUNG|in *wParam*|*LPARAM* (alle Parameter sind [in], sofern nicht anders angegeben.)|Rückgabewert|
|-|-|-|-|-|
|AFX_WM_ACCGETOBJECT|Nicht verwendet.|Nicht verwendet.|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_ACCGETSTATE|Wird für Barrierefreiheits Unterstützung verwendet. Sendet diese Nachricht an `CMFCPopupMenu` oder `CMFCRibbonPanelMenu` , um den Status des aktuellen Elements abzurufen.|Index des Elements, das eine Menü Schaltfläche oder ein Trennzeichen sein kann.|Wird nicht verwendet.|Der Element Zustand. Der Wert ist-1, wenn der Index ungültig ist, 0, wenn die Menü Schaltfläche keine besonderen Attribute aufweist. Andernfalls handelt es sich um eine Kombination der folgenden Flags:<br /><br /> TBBS_DISABLED – Element ist deaktiviert.<br /><br /> TBBS_CHECKED – Element ist aktiviert.<br /><br /> TBBS_BUTTON – das Element ist ein Standard-PUSHBUTTON.<br /><br /> TBBS_PRESSED –-Schaltfläche wird gedrückt<br /><br /> TBBS_INDETERMINATE – nicht definierter Zustand<br /><br /> TBBS_SEPARATOR-anstelle einer Menü Schaltfläche bildet dieses Element eine Trennung zwischen anderen Menü Elementen.|
|AFX_WM_CHANGE_ACTIVE_TAB|Das Framework sendet diese Nachricht an das Steuerelement leisten-Steuerelement, das geändert werden können. Verarbeiten Sie diese Nachricht, um Benachrichtigungen von Objekten zu empfangen, `CMFCTabCtrl` Wenn ein Benutzer eine aktive Registerkarte ändert.|Der Index einer Registerkarte.|Wird nicht verwendet.|Ungleich NULL.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Das Framework sendet diese Nachricht an das übergeordnete Element von, `CMFCShellListCtrl` Wenn der Benutzer den aktuellen Ordner geändert hat.|Nicht verwendet.|Nicht verwendet.|Nicht verwendet.|
|AFX_WM_CHANGEVISUALMANAGER|Das Framework sendet diese Nachricht an alle Rahmen Fenster, wenn der Benutzer den aktuellen Visual Manager ändert. Als Antwort auf diese Nachricht berechnet ein Rahmen Fenster seinen Bereich neu und passt andere Parameter nach Bedarf an. Sie können die AFX_WM_CHANGEVISUALMANAGER Nachricht in Ihrer Anwendung verarbeiten, wenn Sie über dieses Ereignis benachrichtigt werden müssen. Sie müssen den Basisklassen Handler ( `OnChangeVisualManager` ) abrufen, um sicherzustellen, dass die interne Verarbeitung dieses Ereignisses des Frameworks stattfindet.|Nicht verwendet.|Nicht verwendet.|Nicht verwendet.|
|AFX_WM_CHANGING_ACTIVE_TAB|Wird an das übergeordnete `CMFCTabCtrl` Objekt des-Objekts gesendet.  Verarbeiten Sie diese Meldung, wenn Sie Benachrichtigungen von Objekten empfangen möchten, `CMFCTabCtrl` Wenn ein Benutzer eine Registerkarte zurücksetzt.|Der Index der Registerkarte, die aktiviert wird.|Wird nicht verwendet.|Ungleich NULL.|
|AFX_WM_CHECKEMPTYMINIFRAME|Nur für interne Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_CREATETOOLBAR|Wird von gesendet, `CMFCToolBarsListPropertyPage` Wenn ein Benutzer während des Anpassungs Vorgangs eine neue Symbolleiste erstellt. Sie können diese Nachricht verarbeiten, um ein benutzerdefiniertes cmfctoolbar-abgeleitetes Objekt zu instanziieren. Wenn Sie diese Meldung verarbeiten und eine eigene Symbolleiste erstellen, lassen Sie den-Befehl für den Standard Handler Weg.|Wird nicht verwendet.|Ein Zeiger auf eine Zeichenfolge, die den Namen der Symbolleiste enthält.|Ein Zeiger auf die neu erstellte Symbolleiste. NULL gibt an, dass die Erstellung der Symbolleiste abgebrochen wurde.|
|AFX_WM_CUSTOMIZEHELP|Wird vom Eigenschaften Blatt für die Anpassung an das Hauptrahmen Fenster gesendet, `CMFCToolbarCustomize Dialog` Wenn der Benutzer die **Hilfe** Schaltfläche oder die F1-Taste drückt.|Gibt die aktive Seite des Anpassungs Eigenschaften Blatts an.|Ein Zeiger auf ein `CMFCToolbarCustomize Dialog`-Objekt.|Keinen.|
|AFX_WM_CUSTOMIZETOOLBAR|Der `CMFCToolbarCustomize Dialog` sendet diese Meldung, um den übergeordneten Frame zu benachrichtigen, dass der Benutzer eine neue Symbolleiste erstellt.|TRUE, wenn die Anpassung gestartet wird, false, wenn die Anpassung abgeschlossen ist.|Wird nicht verwendet.|Keinen.|
|AFX_WM_DELETETOOLBAR|Wird an das Hauptrahmen Fenster gesendet, wenn der Benutzer im Begriff ist, eine Symbolleiste im Anpassungsmodus zu löschen.<br /><br /> Verarbeiten Sie diese Meldung, um zusätzliche Aktionen auszuführen, wenn ein Benutzer eine Symbolleiste im Anpassungsmodus löscht. Sie sollten auch den Standard Handler ( `OnToolbarDelete` ) verwenden, mit dem die Symbolleiste gelöscht wird. Der Standard Handler gibt einen Wert zurück, der angibt, ob es möglich ist, die Symbolleiste zu löschen.|Wird nicht verwendet.|Zeiger auf ein- `CMFCToolBar` Objekt, das gelöscht werden soll.|Ungleich NULL, wenn eine Symbolleiste nicht gelöscht werden kann. andernfalls 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` sendet diese Meldung an das Hauptrahmen Fenster, um die Dokument Farben abzurufen.|Wird nicht verwendet.|[in, out] Zeiger auf ein- `CList<COLORREF, COLORREF>` Objekt.|Keinen.|
|AFX_WM_GETDRAGBOUNDS|Nur für interne Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Wird an das Hauptrahmen Fenster gesendet, wenn ein Benutzer ein Menü Band Listenelement hervorhebt.|Index des hervorgehobenen Elements|Ein Zeiger auf `CMFCBaseRibbonElement`|Wird nicht verwendet.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Wird an ein übergeordnetes Element von oder gesendet, `CMFCShellListCtrl` `CMFCShellTreeCtrl` Wenn ein Benutzer die Ausführung eines Shellbefehls beendet.|Die ID des vom Benutzer ausgeführten Befehls.|Wird nicht verwendet.|Wenn die Anwendung diese Nachricht verarbeitet, sollte Sie 0 (null) zurückgeben.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Das Framework sendet diese Nachricht an das übergeordnete Element des Menübands, bevor es das Popup Menü anzeigt. Sie können diese Nachricht jederzeit verarbeiten und Popup Menüs ändern.|Wird nicht verwendet.|Ein Zeiger auf `CMFCBaseRibbonElement`|Wird nicht verwendet.|
|AFX_WM_ON_CANCELTABMOVE|Nur für interne Verwendung.|Nicht zutreffend|Nicht zutreffend||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Das Framework sendet diese Nachricht an den Hauptframe, wenn der Benutzer die Kategorie des aktiven Menüband-Steuer Elements ändert.|Wird nicht verwendet.|Ein Zeiger auf den, `CMFCRibbonBar` dessen Kategorie geändert wurde.|Wird nicht verwendet.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Das Framework sendet diese Nachricht, um den Besitzer darüber zu benachrichtigen `CMFCDesktopAlertWnd` , dass das Fenster geschlossen wird.|Wird nicht verwendet.|Ein Zeiger auf das- `CMFCDesktopAlertWnd` Objekt.|Wird nicht verwendet.|
|AFX_WM_ON_DRAGCOMPLETE|Nur für interne Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_ON_GET_TAB_TOOLTIP|Wird an das Hauptrahmen Fenster gesendet, wenn ein Registerkarten Fenster im Begriff ist, eine QuickInfo für eine Registerkarte anzuzeigen, wenn benutzerdefinierte Quick Infos aktiviert sind.|Wird nicht verwendet.|Ein Zeiger auf eine- `CMFCTabToolTipInfo` Struktur.|Wird nicht verwendet.|
|AFX_WM_ON_HSCROLL|Wird an das Steuerelement leisten-Steuerelement in der Größe geändert. Verarbeiten Sie diese Nachricht, um Benachrichtigungen von Objekten zu empfangen, `CMFCTabCtrl` Wenn ein scrollereignis auf der horizontalen Scrollleiste des Widgets im Registerkarten Format auftritt.|Das nieder wertige Wort gibt einen Scrollleisten-Wert an, der die scrollanforderung des Benutzers angibt.  Weitere Informationen finden Sie in der Tabelle weiter unten in diesem Thema.|Wird nicht verwendet.|Ungleich NULL.|
|AFX_WM_ON_MOVE_TAB|Wird an das übergeordnete Element eines Fensters im Registerkarten Format gesendet, wenn ein Benutzer eine Registerkarte an eine neue Position zieht.|Der null basierte Index der Registerkarte an der ursprünglichen Position.|vorgenommen Der null basierte Index der Registerkarte an der neuen Position.|Keinen.|
|AFX_WM_ON_MOVETABCOMPLETE|Nur für interne Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_ON_MOVETOTABGROUP|Wird an das Hauptrahmen Fenster gesendet, wenn ein Benutzer ein untergeordnetes MDI-Fenster von einer Gruppe im Registerkarten Format zu einem anderen verschiebt.|Ein Handle für das Fenster im Registerkarten Format ( `CMFCTabCtrl` ), aus dem das untergeordnete MDI-Fenster entfernt wurde.|vorgenommen Ein Handle für das Fenster im Registerkarten Format ( `CMFCTabCtrl` ), in das das untergeordnete MDI-Fenster eingefügt wurde.|Ignoriert.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Wird an ein übergeordnetes Element von gesendet, `CDockablePane` Wenn der Benutzer auf die Schaltfläche **Schließen** auf der Beschriftung der Steuerleiste klickt.|Wird nicht verwendet.|Ein Zeiger auf einen andockbaren Bereich, auf den der Benutzer auf die Schaltfläche **Schließen** geklickt hat.|TRUE, wenn ein Bereich nicht geschlossen werden kann. andernfalls false.|
|AFX_WM_ON_RENAME_TAB|Wird an das übergeordnete Fenster des Fensters im Registerkarten Format gesendet, nachdem der Benutzer eine Bearbeitungs Registerkarte umbenannt hat.|Der null basierte Index der umbenannten Registerkarte.|vorgenommen Ein Zeiger auf eine Zeichenfolge, die den neuen Namen der Registerkarte enthält.|Ungleich 0 (null), wenn die Anwendung diese Nachricht verarbeitet. Das Framework unterdrückt den-Aufrufvorgang `CMFCBaseTabCtrl::SetTabLabel` .  Wenn 0 (null) zurückgegeben wird, `CMFCBaseTabCtrl::SetTabLabel` wird vom Framework aufgerufen.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Wird an den übergeordneten Frame gesendet, wenn der Benutzer die Anpassung startet. Verarbeiten Sie diese Meldung, wenn Sie Ihr eigenes Anpassungs Dialogfeld anzeigen möchten.|Wird nicht verwendet.|Ein Zeiger auf das Menüband-Steuerelement, das angepasst werden soll.|Ein Wert ungleich 0 (null), wenn die Anwendung diese Nachricht verarbeitet und Ihr eigenes Anpassungs Dialogfeld anzeigt. Wenn die Anwendung 0 (null) zurückgibt, zeigt das Framework das integrierte Anpassungs Dialogfeld an.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Nur für interne Verwendung.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|AFX_WM_POSTSETPREVIEWFRAME|Wird gesendet, um den Hauptrahmen zu benachrichtigen, dass der Benutzer den Seiten Ansichtsmodus geändert hat|TRUE gibt an, dass der Druckvor Schau Modus festgelegt ist. FALSE gibt an, dass der Seiten Ansichtsmodus deaktiviert ist.|Nicht verwendet.|Nicht verwendet.|
|AFX_WM_PROPERTY_CHANGED|Wird an den Besitzer des Eigenschaften Raster-Steuer Elements () gesendet, `CMFCPropertyGridCtrl` Wenn der Benutzer den Wert der ausgewählten Eigenschaft ändert.|Die Steuerelement-ID der Eigenschaften Liste.|Ein Zeiger auf die-Eigenschaft ( `CMFCPropertyGridProperty` ), die geändert wurde.|Wird nicht verwendet.|
|AFX_WM_RESETCONTEXTMENU|Wird an das Hauptrahmen Fenster gesendet, wenn der Benutzer das Kontextmenü während der Anpassung zurücksetzt.|Die Ressourcen-ID des Kontextmenüs.|Ein Zeiger auf das aktuelle Kontextmenü `CMFCPopupMenu` .|Wird nicht verwendet.|
|AFX_WM_RESETKEYBOARD|Das Framework sendet diese Meldung an das Hauptrahmen Fenster, wenn der Benutzer während der Anpassung alle Tastaturbeschleuniger zurücksetzt.|Nicht verwendet.|Nicht verwendet.|Nicht verwendet.|
|AFX_WM_RESETMENU|Das Framework sendet diese Nachricht an den Menü Besitzer (ein Rahmen Fenster), wenn der Benutzer während der Anpassung ein Anwendungs Frame Menü zurücksetzt.|Die Menü Ressourcen-ID.|Nicht verwendet.|Nicht verwendet.|
|AFX_WM_RESETPROMPT|Das Framework sendet diese Nachricht, wenn der Benutzer eine Symbolleiste aus dem Dialogfeld "Symbolleiste anpassen" zurücksetzt. Der Standard Handler zeigt ein Meldungs Feld an, in dem gefragt wird, ob der Benutzer die Symbolleiste zurücksetzen möchte.|Nicht verwendet.|Nicht verwendet.|Nicht verwendet.|
|AFX_WM_RESETTOOLBAR|Ein- `CMFCToolBar` Objekt sendet diese Nachricht, wenn eine Symbolleiste in ihren ursprünglichen Zustand wieder hergestellt wird, d. h. aus den Ressourcen geladen. Verarbeiten Sie diese Meldung, um Symbolleisten Schaltflächen wiederherzustellen, deren Klassen von abgeleitet werden `CMFCToolbarButton` . Weitere Informationen finden Sie unter `CMFCToolbarComboBoxButton`.|Die Ressourcen-ID einer Symbolleiste, deren Zustand wieder hergestellt wurde.|Wird nicht verwendet.|Keinen.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` das Objekt sendet diese Nachricht an den Besitzer, wenn der Benutzer auf eine reguläre Menü Schaltfläche klickt. Verarbeiten Sie diese Nachricht jedes Mal, wenn Sie verwenden `CMFCToolbarMenuButton` , um ein Popupmenü anzuzeigen, wenn der Benutzer auf eine Schaltfläche klickt.|Die Befehls-ID einer Schaltfläche, die die Nachricht sendet.|Bildschirm Koordinaten des Cursors. Mit dem nieder wertigen Wort wird die x-Koordinate angegeben. Das höchst wertige Wort gibt die y-Koordinate an.|Wird nicht verwendet.|
|AFX_WM_TOOLBARMENU|Wird an das Hauptrahmen Fenster gesendet, wenn der Benutzer die Rechte Maustaste loslässt, während sich der Mauszeiger im Client-oder nicht-Client Bereich eines Bereichs befindet.|Wird nicht verwendet.|Bildschirm Koordinaten des Mauszeigers. Mit dem nieder wertigen Wort wird die x-Koordinate angegeben. Das höchst wertige Wort gibt die y-Koordinate an.|0 (null), wenn die Anwendung diese Nachricht verarbeitet. Andernfalls ungleich 0 (null).|
|AFX_WM_UPDATETOOLTIPS|Wird an alle ToolTip-Besitzer gesendet, um anzugeben, dass die QuickInfo-Steuerelemente neu erstellt werden sollen.|Der Typ des Steuer Elements, von dem diese Nachricht verarbeitet werden soll. Eine Liste möglicher Werte finden Sie in der Tabelle weiter unten in diesem Thema.|Nicht verwendet.|Nicht verwendet.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` sendet diese Meldung an den übergeordneten Frame, wenn der Benutzer auf die Schaltfläche " **Hilfe** " klickt, oder wechselt in den Hilfe Modus, indem er auf die Schaltfläche " **Hilfe** Beschriftung" oder die Taste|Wird nicht verwendet.|Ein Zeiger auf die Instanz von `CMFCWindowsManagerDialog` .|Wird nicht verwendet.|

In der folgenden Tabelle sind die Werte für das niedrige Wort des *LPARAM* -Parameters der AFX_WM_HSCROLL-Methode aufgeführt:

|Wert|Bedeutung|
|-|-|
|SB_ENDSCROLL|Der Benutzer beendet den Bildlauf.|
|SB_LEFT|Der Benutzer scrollt in der linken oberen Ecke.|
|SB_RIGHT|Der Benutzer führt einen Bildlauf nach unten rechts aus.|
|SB_LINELEFT|Der Benutzer scrollt nach links um eine Einheit.|
|SB_LINERIGHT|Der Benutzer scrollt nach rechts um eine Einheit.|
|SB_PAGELEFT|Der Benutzer führt einen Bildlauf nach links um die Breite des Fensters aus.|
|SB_PAGERIGHT|Der Benutzer führt einen Bildlauf nach rechts durch die Breite des Fensters aus.|
|SB_THUMBPOSITION|Der Benutzer hat das Bild Lauf Feld (Thumb) gezogen und die Maustaste losgelassen. Das höchst wertige Wort gibt die Position des Bild Lauf Felds am Ende des Zieh Vorgangs an.|
|SB_THUMBTRACK|Der Benutzer zieht die Bildlaufbox. Die AFX_WM_ON_HSCROLL Nachricht wird wiederholt mit diesem Wert gesendet, bis der Benutzer die Maustaste loslässt. Das höchst wertige Wort gibt die Position an, an der das Bild Lauf Feld gezogen wurde.|

> [!NOTE]
> Das höchst wertige Wort des *LPARAM* -Parameters gibt die aktuelle Position des Bild Lauf Felds an, wenn das nieder wertige Wort SB_THUMBPOSITION oder SB_THUMBTRACK ist. Andernfalls wird dieses Wort nicht verwendet.

In der folgenden Tabelle sind die Flagwerte für den *LPARAM* -Parameter der AFX_WM_UPDATETOOLTIPS Meldung aufgeführt:

|Flag|Wert|
|-|-|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
