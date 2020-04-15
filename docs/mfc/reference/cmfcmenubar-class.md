---
title: CMFCMenuBar-Klasse
ms.date: 10/18/2018
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
helpviewer_keywords:
- CMFCMenuBar [MFC], AdjustLocations
- CMFCMenuBar [MFC], AllowChangeTextLabels
- CMFCMenuBar [MFC], AllowShowOnPaneMenu
- CMFCMenuBar [MFC], CalcFixedLayout
- CMFCMenuBar [MFC], CalcLayout
- CMFCMenuBar [MFC], CalcMaxButtonHeight
- CMFCMenuBar [MFC], CanBeClosed
- CMFCMenuBar [MFC], CanBeRestored
- CMFCMenuBar [MFC], Create
- CMFCMenuBar [MFC], CreateEx
- CMFCMenuBar [MFC], CreateFromMenu
- CMFCMenuBar [MFC], EnableHelpCombobox
- CMFCMenuBar [MFC], EnableMenuShadows
- CMFCMenuBar [MFC], GetAvailableExpandSize
- CMFCMenuBar [MFC], GetColumnWidth
- CMFCMenuBar [MFC], GetDefaultMenu
- CMFCMenuBar [MFC], GetDefaultMenuResId
- CMFCMenuBar [MFC], GetFloatPopupDirection
- CMFCMenuBar [MFC], GetForceDownArrows
- CMFCMenuBar [MFC], GetHelpCombobox
- CMFCMenuBar [MFC], GetHMenu
- CMFCMenuBar [MFC], GetMenuFont
- CMFCMenuBar [MFC], GetMenuItem
- CMFCMenuBar [MFC], GetRowHeight
- CMFCMenuBar [MFC], GetSystemButton
- CMFCMenuBar [MFC], GetSystemButtonsCount
- CMFCMenuBar [MFC], GetSystemMenu
- CMFCMenuBar [MFC], HighlightDisabledItems
- CMFCMenuBar [MFC], IsButtonExtraSizeAvailable
- CMFCMenuBar [MFC], IsHighlightDisabledItems
- CMFCMenuBar [MFC], IsMenuShadows
- CMFCMenuBar [MFC], IsRecentlyUsedMenus
- CMFCMenuBar [MFC], IsShowAllCommands
- CMFCMenuBar [MFC], IsShowAllCommandsDelay
- CMFCMenuBar [MFC], LoadState
- CMFCMenuBar [MFC], OnChangeHot
- CMFCMenuBar [MFC], OnDefaultMenuLoaded
- CMFCMenuBar [MFC], OnSendCommand
- CMFCMenuBar [MFC], OnSetDefaultButtonText
- CMFCMenuBar [MFC], OnToolHitTest
- CMFCMenuBar [MFC], PreTranslateMessage
- CMFCMenuBar [MFC], RestoreOriginalstate
- CMFCMenuBar [MFC], SaveState
- CMFCMenuBar [MFC], SetDefaultMenuResId
- CMFCMenuBar [MFC], SetForceDownArrows
- CMFCMenuBar [MFC], SetMaximizeMode
- CMFCMenuBar [MFC], SetMenuButtonRTC
- CMFCMenuBar [MFC], SetMenuFont
- CMFCMenuBar [MFC], SetRecentlyUsedMenus
- CMFCMenuBar [MFC], SetShowAllCommands
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
ms.openlocfilehash: 50dd488d1f59c99b8fee1eb96acf6d0041547df9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369687"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar-Klasse

Eine Menüleiste, die Andocken implementiert.
Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Überschreibt `CMFCToolBar::AdjustLocations`.)|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Gibt an, ob Textbeschriftungen unter Bildern auf den Symbolleistenschaltflächen angezeigt werden können. (Überschreibt [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Überschreibt `CPane::AllowShowOnPaneMenu`.)|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Berechnet die horizontale Größe der Symbolleiste. (Überschreibt [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|
|[CMFCMenuBar::CalcLayout](#calclayout)|(Überschreibt `CMFCToolBar::CalcLayout`.)|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Berechnet die maximale Höhe der Schaltflächen in der Symbolleiste. (Überschreibt [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Gibt an, ob ein Benutzer die Symbolleiste schließen kann. (Überschreibt [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|
|[CMFCMenuBar::CanBeRestored](#canberestored)|Bestimmt, ob das System eine Symbolleiste nach der Anpassung in den ursprünglichen Zustand zurückversetzen kann. (Überschreibt [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCMenuBar::Erstellen](#create)|Erstellt ein Menüsteuerelement und fügt `CMFCMenuBar` es an ein Objekt an.|
|[CMFCMenuBar::CreateEx](#createex)|Erstellt `CMFCMenuBar` ein Objekt mit zusätzlichen Stiloptionen.|
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Initialisiert ein `CMFCMenuBar`-Objekt. Akzeptiert einen HMENU-Parameter, der als `CMFCMenuBar`Vorlage für eine gefüllte dient.|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Aktiviert **Help** ein Hilfekombinationsfeld, das sich auf der rechten Seite der Menüleiste befindet.|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Gibt an, ob Schatten für Popupmenüs angezeigt werden sollen.|
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Überschreibt [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Gibt die Breite der Symbolleistenschaltflächen zurück. (Überschreibt [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Gibt ein Handle an das ursprüngliche Menü in der Ressourcendatei zurück.|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Gibt den Ressourcenbezeichner für das ursprüngliche Menü in der Ressourcendatei zurück.|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Gibt einen Zeiger **Help** auf das Hilfekombinationsfeld zurück.|
|[CMFCMenuBar::GetHMenu](#gethmenu)|Gibt das Handle an das Menü `CMFCMenuBar` zurück, das an das Objekt angefügt ist.|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Gibt die aktuelle globale Schriftart für Menüobjekte zurück.|
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Gibt die Symbolleistenschaltfläche zurück, die dem bereitgestellten Elementindex zugeordnet ist.|
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Gibt die Höhe der Symbolleistenschaltflächen zurück. (Überschreibt [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Gibt an, ob deaktivierte Menüelemente hervorgehoben sind.|
|[CMFCMenuBar::IsButtonExtraSizeVerfügbar](#isbuttonextrasizeavailable)|Bestimmt, ob die Symbolleiste Schaltflächen mit erweiterten Rahmen anzeigen kann. (Überschreibt [CMFCToolBar::IsButtonExtraSizeVerfügbar](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Gibt an, ob deaktivierte Elemente hervorgehoben sind.|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Gibt an, ob Schatten für Popupmenüs gezeichnet werden.|
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Gibt an, ob kürzlich verwendete Menübefehle in der Menüleiste angezeigt werden.|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Gibt an, ob Popupmenüs alle Befehle anzeigen.|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Gibt an, ob Menüs alle Befehle nach einer kurzen Verzögerung anzeigen.|
|[CMFCMenuBar::LoadState](#loadstate)|Lädt den Status `CMFCMenuBar` des Objekts aus der Registrierung.|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Wird vom Framework aufgerufen, wenn ein Benutzer eine Schaltfläche auf der Symbolleiste auswählt. (Überschreibt [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Wird vom Framework aufgerufen, wenn ein Rahmenfenster das Standardmenü aus der Ressourcendatei lädt.|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Überschreibt `CMFCToolBar::OnSendCommand`.)|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Wird vom Framework aufgerufen, wenn sich ein Menü im Anpassungsmodus befindet und der Benutzer den Text eines Menüelements ändert.|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Überschreibt `CMFCToolBar::OnToolHitTest`.)|
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Überschreibt `CMFCToolBar::PreTranslateMessage`.)|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Wird vom Framework aufgerufen, wenn sich ein Menü im Anpassungsmodus befindet und der Benutzer für eine Menüleiste **Zurücksetzen** auswählt.|
|[CMFCMenuBar::SaveState](#savestate)|Speichert den Status `CMFCMenuBar` des Objekts in der Registrierung.|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Legt das ursprüngliche Menü in der Ressourcendatei fest.|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Wird vom Framework aufgerufen, wenn ein untergeordnetes MDI-Fenster seinen Anzeigemodus ändert. Wenn das untergeordnete MDI-Fenster neu maximiert oder nicht mehr maximiert ist, aktualisiert diese Methode die Menüleiste.|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Legt die Laufzeitklasseninformationen fest, die generiert werden, wenn der Benutzer menüschaltflächen dynamisch erstellt.|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Legt die Schriftart für alle Menüs in der Anwendung fest.|
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Gibt an, ob eine Menüleiste zuletzt verwendete Menübefehle anzeigt.|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Gibt an, ob in der Menüleiste alle Befehle angezeigt werden.|

## <a name="remarks"></a>Bemerkungen

Die `CMFCMenuBar` Klasse ist eine Menüleiste, die Andockfunktionen implementiert. Es ähnelt einer Symbolleiste, obwohl es nicht geschlossen werden kann - es wird immer angezeigt.

`CMFCMenuBar`unterstützt die Option, zuletzt verwendete Menüelementobjekte anzuzeigen. Wenn diese Option aktiviert `CMFCMenuBar` ist, zeigt die nur eine Teilmenge der verfügbaren Befehle bei der ersten Anzeige an. Danach werden kürzlich verwendete Befehle zusammen mit der ursprünglichen Teilmenge der Befehle angezeigt. Darüber hinaus kann der Benutzer das Menü jederzeit erweitern, um alle verfügbaren Befehle anzuzeigen. Daher ist jeder verfügbare Befehl so konfiguriert, dass er ständig oder nur dann angezeigt wird, wenn er kürzlich ausgewählt wurde.

Um ein `CMFCMenuBar` Objekt zu verwenden, betten Sie es in das Rahmenobjekt des Hauptfensters ein. Bei der `WM_CREATE` Verarbeitung `CMFCMenuBar::Create` der `CMFCMenuBar::CreateEx`Nachricht rufen Sie an oder . Unabhängig davon, welche Erstellungsfunktion Sie verwenden, übergeben Sie einen Zeiger auf das Hauptrahmenfenster. Aktivieren Sie dann das Andocken, indem Sie [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking)aufrufen. Docken Sie dieses Menü an, indem Sie [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane)aufrufen.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCMenuBar` -Klasse. Das Beispiel zeigt, wie Sie den Stil des Bereichs festlegen, die Schaltfläche Anpassen aktivieren, ein Hilfefeld aktivieren, Schatten für Popupmenüs aktivieren und die Menüleiste aktualisieren. Dieser Codeausschnitt ist Teil des [IE-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmenubar.h

## <a name="cmfcmenubaradjustlocations"></a><a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations

Passt die Positionen der Menüpunkte in der Menüleiste an.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels

Bestimmt, ob Textbeschriftungen unter Bildern in der Menüleiste zulässig sind.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Benutzer Textbeschriftungen unter Bildern anzeigen kann.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

[in] *bStretch*<br/>

[in] *bHorz*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarcalclayout"></a><a name="calclayout"></a>CMFCMenuBar::CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>Parameter

[in] *dwMode*<br/>

[in] *nLänge*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarcanbeclosed"></a><a name="canbeclosed"></a>CMFCMenuBar::CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarcanberestored"></a><a name="canberestored"></a>CMFCMenuBar::CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarcreate"></a><a name="create"></a>CMFCMenuBar::Erstellen

Erstellt ein Menüsteuerelement und fügt es an ein [CMFCMenuBar-Objekt](../../mfc/reference/cmfcmenubar-class.md) an.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
[in] Zeigen Sie mit dem Zeiger `CMFCMenuBar` auf das übergeordnete Fenster für das neue Objekt.

*dwStyle*<br/>
[in] Der Stil der neuen Menüleiste.

*nID*<br/>
[in] Die ID für das untergeordnete Fenster der Menüleiste.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Nachdem Sie `CMFCMenuBar` ein Objekt erstellt `Create`haben, müssen Sie aufrufen. Diese Methode `CMFCMenuBar` erstellt das Steuerelement und `CMFCMenuBar` fügt es an das Objekt an.

Weitere Informationen zu Symbolleistenstilen finden Sie unter [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).

## <a name="cmfcmenubarcreateex"></a><a name="createex"></a>CMFCMenuBar::CreateEx

Erstellt ein [CMFCMenuBar-Objekt](../../mfc/reference/cmfcmenubar-class.md) mit angegebenen erweiterten Stilen.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    CRect rcBorders = CRect(1,
    1,
    1,
    1),
    UINT nID =AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
[in] Zeigen Sie mit dem Zeiger `CMFCMenuBar` auf das übergeordnete Fenster des neuen Objekts.

*dwCtrlStyle*<br/>
[in] Zusätzliche Stile für die neue Menüleiste.

*dwStyle*<br/>
[in] Der Hauptstil der neuen Menüleiste.

*rcBorders*<br/>
[in] Ein `CRect` Parameter, der die Größen für `CMFCMenuBar` die Ränder des Objekts angibt.

*nID*<br/>
[in] Die ID für das untergeordnete Fenster der Menüleiste.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie sollten diese Funktion anstelle von [CMFCMenuBar::Create](#create) verwenden, wenn Sie Stile zusätzlich zum Symbolleistenstil angeben möchten. Einige häufig verwendete zusätzliche Stile werden TBSTYLE_TRANSPARENT und CBRS_TOP.

Listen mit zusätzlichen Stilen finden Sie unter [Werkzeugleistensteuerung und Schaltflächenstile](/windows/win32/Controls/toolbar-control-and-button-styles), [allgemeine Steuerelementstile](/windows/win32/Controls/common-control-styles)und [allgemeine Fensterstile](/windows/win32/winmsg/window-styles).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CreateEx` veranschaulicht, `CMFCMenuBar` wie die Methode der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [IE-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

## <a name="cmfcmenubarcreatefrommenu"></a><a name="createfrommenu"></a>CMFCMenuBar::CreateFromMenu

Initialisiert ein [CMFCMenuBar-Objekt.](../../mfc/reference/cmfcmenubar-class.md) Diese Methode `CMFCMenuBar` modelliert das Objekt nach einem HMENU-Parameter.

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>Parameter

*Hmenu*<br/>
[in] Ein Handle für eine Menüressource. `CreateFromMenu`verwendet diese Ressource als `CMFCMenuBar`Vorlage für die .

*bDefaultMenu*<br/>
[in] Ein boolescher Wert, der angibt, ob das neue Menü das Standardmenü ist.

*bForceUpdate*<br/>
[in] Ein boolescher Wert, der angibt, ob diese Methode eine Menüaktualisierung erzwingt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, wenn ein Menüsteuerelement dieselben Menüelemente wie eine Menüressource enthalten soll. Sie rufen diese Methode auf, nachdem Sie entweder [CMFCMenuBar::Create](#create) oder [CMFCMenuBar::CreateEx](#createex)aufrufen.

## <a name="cmfcmenubarenablehelpcombobox"></a><a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox

Aktiviert **Help** ein Hilfekombinationsfeld, das sich auf der rechten Seite der Menüleiste befindet.

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Die Befehls-ID für **Help** die Schaltfläche des Hilfekombinationsfelds.

*lpszPrompt*<br/>
[in] Eine Zeichenfolge, die den Text enthält, den das Framework im Kombinationsfeld anzeigt, wenn er leer und nicht aktiv ist. Beispiel: "Geben Sie den Text hier ein".

*nComboBoxWidth*<br/>
[in] Die Breite der Schaltfläche für das Kombinationsfeld in Pixel.

### <a name="remarks"></a>Bemerkungen

Das Feld **Hilfekombination** ähnelt dem **Feld Hilfekombination** in der Menüleiste von Microsoft Word.

Wenn Sie diese Methode aufrufen, wobei *uiID* auf 0 festgelegt ist, blendet diese Methode das Kombinationsfeld aus. Andernfalls zeigt diese Methode das Kombinationsfeld automatisch auf der rechten Seite der Menüleiste an. Rufen Sie nach dem Aufruf dieser Methode [CMFCMenuBar::GetHelpCombobox](#gethelpcombobox) auf, um einen Zeiger auf das eingefügte [CMFCToolBarComboBoxButton-Objekt](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) zu erhalten.

## <a name="cmfcmenubarenablemenushadows"></a><a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows

Aktiviert Schatten für Popupmenüs.

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] Ein boolescher Parameter, der angibt, ob Schatten für Popupmenüs aktiviert werden sollen.

### <a name="remarks"></a>Bemerkungen

Der von dieser Methode verwendete Algorithmus ist komplex und kann die Leistung Ihrer Anwendung auf langsameren Systemen beeinträchtigen.

## <a name="cmfcmenubargetavailableexpandsize"></a><a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubargetdefaultmenu"></a><a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu

Ruft ein Handle im ursprünglichen Menü ab. Das Framework lädt das ursprüngliche Menü aus der Ressourcendatei.

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für eine Menüressource.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung ein Menü anpasst, können Sie diese Methode verwenden, um ein Handle im ursprünglichen Menü abzurufen.

## <a name="cmfcmenubargetdefaultmenuresid"></a><a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId

Ruft den Ressourcenbezeichner für das Standardmenü ab.

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Menüressourcenbezeichner.

### <a name="remarks"></a>Bemerkungen

Das Framework lädt das `CMFCMenuBar` Standardmenü für das Objekt aus der Ressourcendatei.

## <a name="cmfcmenubargetfloatpopupdirection"></a><a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>Parameter

[in] *pButton*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubargetforcedownarrows"></a><a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubargethelpcombobox"></a><a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox

Gibt einen Zeiger **Help** auf das Hilfekombinationsfeld zurück.

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf **Help** das Hilfekombinationsfeld. NULL, wenn das **Feld Hilfekombination** ausgeblendet oder nicht aktiviert ist.

### <a name="remarks"></a>Bemerkungen

Das **Help** Hilfe-Kombinationsfeld befindet sich auf der rechten Seite der Menüleiste. Rufen Sie die Methode [CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox) auf, um dieses Kombinationsfeld zu aktivieren.

## <a name="cmfcmenubargethmenu"></a><a name="gethmenu"></a>CMFCMenuBar::GetHMenu

Ruft das Handle für das Menü ab, das an das [CMFCMenuBar-Objekt](../../mfc/reference/cmfcmenubar-class.md) angefügt ist.

```
HMENU GetHMenu() const;
```

## <a name="cmfcmenubargetmenufont"></a><a name="getmenufont"></a>CMFCMenuBar::GetMenuFont

Ruft die aktuelle Menüschriftart ab.

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parameter

*bHorz*<br/>
[in] Ein boolescher Parameter, der angibt, ob die horizontale oder vertikale Schriftart zurückgegeben werden soll. TRUE gibt die horizontale Schriftart an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf einen [CFont-Parameter,](../../mfc/reference/cfont-class.md) der die aktuelle Menüleistenschriftart enthält.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebene Schriftart ist ein globaler Parameter für die Anwendung. Für alle Objekte werden `CMFCMenuBar` zwei globale Schriftarten beibehalten. Diese separaten Schriftarten werden für horizontale und vertikale Menüleisten verwendet.

## <a name="cmfcmenubargetmenuitem"></a><a name="getmenuitem"></a>CMFCMenuBar::GetMenuItem

Ruft ein [CMFCToolBarButton-Objekt](../../mfc/reference/cmfctoolbarbutton-class.md) in einer Menüleiste basierend auf dem Elementindex ab.

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>Parameter

*iItem*<br/>
[in] Der Index des zurückzugebenden Menüelements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CMFCToolBarButton` das Objekt, das mit dem von *iItem*angegebenen Index übereinstimmt. NULL, wenn der Index ungültig ist.

## <a name="cmfcmenubargetrowheight"></a><a name="getrowheight"></a>CMFCMenuBar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubargetsystembutton"></a><a name="getsystembutton"></a>CMFCMenuBar::GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>Parameter

[in] *uiBtn*<br/>

[in] *bByCommand*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubargetsystembuttonscount"></a><a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubargetsystemmenu"></a><a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarhighlightdisableditems"></a><a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems

Steuert, ob das Framework deaktivierte Menüelemente hervorhebt.

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>Parameter

*bHighlight*<br/>
[in] Ein boolescher Parameter, der angibt, ob das Framework nicht verfügbare Menüelemente hervorhebt.

### <a name="remarks"></a>Bemerkungen

Standardmäßig hebt das Framework nicht verfügbare Menüelemente nicht hervor, wenn der Benutzer den Mauszeiger darüber positioniert.

## <a name="cmfcmenubarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtraSizeVerfügbar

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarishighlightdisableditems"></a><a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems

Gibt an, ob das Framework nicht verfügbare Menüelemente hervorhebt.

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn nicht verfügbare Menüelemente hervorgehoben werden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Standardmäßig hebt das Framework nicht verfügbare Menüelemente nicht hervor, wenn der Benutzer den Mauszeiger darüber positioniert. Verwenden Sie die [CMFCMenuBar::HighlightDisabledItems-Methode,](#highlightdisableditems) um diese Funktion zu aktivieren.

## <a name="cmfcmenubarismenushadows"></a><a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows

Gibt an, ob das Framework Schatten für Popupmenüs zeichnet.

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Framework Menüschatten zeichnet; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CMFCMenuBar::EnableMenuShadows-Methode,](#enablemenushadows) um diese Funktion zu aktivieren oder zu deaktivieren.

## <a name="cmfcmenubarisrecentlyusedmenus"></a><a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus

Gibt an, ob kürzlich verwendete Menübefehle in der Menüleiste angezeigt werden.

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CMFCMenuBar` ungleich Null, wenn das Objekt zuletzt verwendete Menübefehle anzeigt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die Funktion [CMFCMenuBar::SetRecentlyUsedMenus,](#setrecentlyusedmenus) um zu steuern, ob die Menüleiste zuletzt verwendete Menübefehle anzeigt.

## <a name="cmfcmenubarisshowallcommands"></a><a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands

Gibt an, ob Menüs alle Befehle anzeigen.

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CMFCMenuBar` ungleich Null, wenn der alle Befehle anzeigt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein `CMFCMenuBar` Objekt kann so konfiguriert werden, dass entweder alle Befehle oder nur eine Teilmenge von Befehlen angezeigt werden. Weitere Informationen zu dieser Funktion finden Sie unter [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md).

`IsShowAllCommands`zeigt Ihnen an, wie diese `CMFCMenuBar` Funktion für das Objekt konfiguriert ist. Um zu steuern, welche Menübefehle angezeigt werden, verwenden Sie die Methoden [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) und [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).

## <a name="cmfcmenubarisshowallcommandsdelay"></a><a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay

Gibt an, ob das [CMFCMenuBar-Objekt](../../mfc/reference/cmfcmenubar-class.md) alle Befehle nach einer kurzen Verzögerung anzeigt.

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Menüleiste nach einer kurzen Verzögerung vollständige Menüs anzeigt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie eine Menüleiste so konfigurieren, dass zuletzt verwendete Elemente angezeigt werden, wird in der Menüleiste das vollständige Menü auf zwei Arten angezeigt:

- Zeigen Sie das vollständige Menü nach einer programmierten Verzögerung an, wenn der Benutzer den Cursor über den Pfeil am unteren Rand des Menüs zeigt.

- Zeigen Sie das vollständige Menü an, nachdem der Benutzer auf den Pfeil am unteren Rand des Menüs geklickt hat.

Standardmäßig verwenden `CMFCMenuBar` alle Objekte die Option, um das vollständige Menü nach einer kurzen Verzögerung anzuzeigen. Diese Option kann in der `CMFCMenuBar` Klasse nicht programmgesteuert geändert werden. Ein Benutzer kann das Verhalten jedoch während der Symbolleistenanpassung ändern, indem er das Dialogfeld **Anpassen** verwendet.

## <a name="cmfcmenubarloadstate"></a><a name="loadstate"></a>CMFCMenuBar::LoadState

Lädt den Status der Menüleiste aus der Windows-Registrierung.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Eine Zeichenfolge, die den Pfad eines Windows-Registrierungsschlüssels enthält.

*nIndex*<br/>
[in] Die Steuer-ID für die Menüleiste.

*uiID*<br/>
[in] Ein reservierter Wert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CMFCMenuBar::SaveState-Methode,](#savestate) um den Status der Menüleiste in der Registrierung zu speichern. Die gespeicherten Informationen umfassen die Menüelemente, den Dockstatus und die Position der Menüleiste.

In den meisten Fällen `LoadState`ruft Ihre Anwendung nicht auf. Das Framework ruft diese Methode auf, wenn der Arbeitsbereich initialisiert wird.

## <a name="cmfcmenubaronchangehot"></a><a name="onchangehot"></a>CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>Parameter

[in] *iHot*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarondefaultmenuloaded"></a><a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded

Das Framework ruft diese Methode auf, wenn es die Menüressource aus der Ressourcendatei lädt.

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>Parameter

*Hmenu*<br/>
[in] Das Handle für das `CMFCMenuBar` Menü, das an das Objekt angefügt ist.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung dieser Funktion wird keine Aktion ausgeführt. Überschreiben Sie diese Funktion, um benutzerdefinierten Code auszuführen, nachdem das Framework eine Menüressource aus der Ressourcendatei geladen hat.

## <a name="cmfcmenubaronsendcommand"></a><a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parameter

[in] *pButton*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText

Das Framework ruft diese Methode auf, wenn der Benutzer den Text eines Elements in der Menüleiste ändert.

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parameter

*pButton*<br/>
[in] Ein Zeiger auf das [CMFCToolBarButton-Objekt,](../../mfc/reference/cmfctoolbarbutton-class.md) das der Benutzer anpassen möchte.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Framework den Benutzer auf die Menüleiste ändert; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung für diese Methode ändert den Text der Schaltfläche in den Vom Benutzer bereitstellten Text.

## <a name="cmfcmenubarontoolhittest"></a><a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parameter

[in] *Punkt*<br/>

[in] *pTI*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuBar::PreTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

[in] *pMsg*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate

Wird vom Framework aufgerufen, wenn der Benutzer im Dialogfeld **Anpassen** die Option **Zurücksetzen** auswählt.

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn der Benutzer im Anpassungsmenü **Zurücksetzen** auswählt. Sie können diese Methode auch manuell aufrufen, um den Status der Menüleiste programmgesteuert zurückzusetzen. Diese Methode lädt den ursprünglichen Status aus der Ressourcendatei.

Überschreiben Sie diese Methode, wenn Sie eine Verarbeitung durchführen möchten, wenn der Benutzer die Option **Zurücksetzen** auswählt.

## <a name="cmfcmenubarsavestate"></a><a name="savestate"></a>CMFCMenuBar::SaveState

Speichert den Status des [CMFCMenuBar-Objekts](../../mfc/reference/cmfcmenubar-class.md) in der Windows-Registrierung.

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parameter

*lpszProfileName*<br/>
[in] Eine Zeichenfolge, die den Pfad eines Windows-Registrierungsschlüssels enthält.

*nIndex*<br/>
[in] Die Steuer-ID für die Menüleiste.

*uiID*<br/>
[in] Ein reservierter Wert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich; andernfalls FALSE;

### <a name="remarks"></a>Bemerkungen

In der Regel ruft `SaveState`Ihre Anwendung nicht auf. Das Framework ruft diese Methode auf, wenn der Arbeitsbereich serialisiert wird. Weitere Informationen finden Sie unter [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

Die gespeicherten Informationen umfassen die Menüelemente, den Dockstatus und die Position der Menüleiste.

## <a name="cmfcmenubarsetdefaultmenuresid"></a><a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId

Legt das Standardmenü für ein [CMFCMenuBar-Objekt](../../mfc/reference/cmfcmenubar-class.md) basierend auf der Ressourcen-ID fest.

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>Parameter

*uiResId*<br/>
[in] Die Ressourcen-ID für das neue Standardmenü.

### <a name="remarks"></a>Bemerkungen

Die [CMFCMenuBar::RestoreOriginalstate-Methode](#restoreoriginalstate) stellt das Standardmenü aus der Ressourcendatei wieder her.

Verwenden Sie die [CMFCMenuBar::GetDefaultMenuResId-Methode,](#getdefaultmenuresid) um das Standardmenü abzurufen, ohne es wiederherzustellen.

## <a name="cmfcmenubarsetforcedownarrows"></a><a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>Parameter

[in] *bValue*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubarsetmaximizemode"></a><a name="setmaximizemode"></a>CMFCMenuBar::SetMaximizeMode

Das Framework ruft diese Methode auf, wenn ein MDI seinen Anzeigemodus ändert und die Menüleiste aktualisiert werden muss.

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Parameter

*bMax*<br/>
[in] Ein boolescher, der den Modus angibt. Weitere Informationen finden Sie im Abschnitt zu den Hinweisen.

*pWnd*<br/>
[in] Ein Zeiger auf das untergeordnete MDI-Fenster, das sich ändert.

*bRecalcLayout*<br/>
[in] Ein boolescher Wert, der angibt, ob das Layout der Menüleiste sofort neu berechnet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn ein untergeordnetes MDI-Fenster maximiert wird, zeigt eine Menüleiste, die an das MDI-Hauptrahmenfenster angefügt ist, das Systemmenü und die **Schaltflächen Minimieren**, **Maximieren** und **Schließen** an. Wenn *bMax* TRUE und *pWnd* nicht NULL ist, wird das untergeordnete MDI-Fenster maximiert, und die Menüleiste muss die zusätzlichen Steuerelemente enthalten. Andernfalls kehrt die Menüleiste in ihren regulären Zustand zurück.

## <a name="cmfcmenubarsetmenubuttonrtc"></a><a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC

Legt die Laufzeitklasseninformationen fest, die das Framework verwendet, wenn der Benutzer Menüschaltflächen erstellt.

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>Parameter

*pMenuButtonRTC*<br/>
[in] Die [CRuntimeClass-Informationen](../../mfc/reference/cruntimeclass-structure.md) für eine Klasse, die von der [CMFCMenuButton-Klasse](../../mfc/reference/cmfcmenubutton-class.md)abgeleitet wurde.

### <a name="remarks"></a>Bemerkungen

Wenn ein Benutzer der Menüleiste neue Schaltflächen hinzufügt, erstellt das Framework die Schaltflächen dynamisch. Standardmäßig werden Objekte `CMFCMenuButton` erstellt. Überschreiben Sie diese Methode, um den Typ der vom Framework erstellten Schaltflächenobjekte zu ändern.

## <a name="cmfcmenubarsetmenufont"></a><a name="setmenufont"></a>CMFCMenuBar::SetMenuFont

Legt die Schriftart für alle Menüleisten in der Anwendung fest.

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parameter

*lpLogFont*<br/>
[in] Ein Zeiger auf eine [LOGFONT-Struktur,](/windows/win32/api/dimm/ns-dimm-logfonta) die die festzulegende Schriftart definiert.

*bHorz*<br/>
[in] TRUE, wenn der Parameter *lpLogFont* für die vertikale Schriftart verwendet werden soll, FALSE, wenn er für die horizontale Schriftart verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Für alle Objekte werden `CMFCMenuBar` zwei Schriftarten verwendet. Diese separaten Schriftarten werden für horizontale und vertikale Menüleisten verwendet.

Die Schriftarteinstellungen sind globale `CMFCMenuBar` Variablen und wirken sich auf alle Objekte aus.

## <a name="cmfcmenubarsetrecentlyusedmenus"></a><a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus

Steuert, ob eine Menüleiste zuletzt verwendete Menübefehle anzeigt.

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parameter

*Bon*<br/>
[in] Ein boolescher, der steuert, ob kürzlich verwendete Menübefehle angezeigt werden.

## <a name="cmfcmenubarsetshowallcommands"></a><a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands

Steuert, ob ein Menü alle verfügbaren Befehle anzeigt.

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>Parameter

*bShowAllCommands*<br/>
[in] Ein boolescher Parameter, der angibt, ob im Popupmenü alle Menübefehle angezeigt werden.

### <a name="remarks"></a>Bemerkungen

Wenn in einem Menü nicht alle Menübefehle angezeigt werden, werden die Befehle ausgeblendet, die selten verwendet werden. Weitere Informationen zum Anzeigen von Menübefehlen finden Sie unter [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)
