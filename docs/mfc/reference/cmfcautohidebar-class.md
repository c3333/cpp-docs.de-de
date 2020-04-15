---
title: CMFCAutoHideBar-Klasse
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
ms.openlocfilehash: 62750f4fb1261f4f30286297c3a240ab67e6df1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369899"
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar-Klasse

Die `CMFCAutoHideBar`-Klasse ist eine besondere Symbolleistenklasse, die die Funktion „Automatisch im Hintergrund“ implementiert.

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Überschreibt `CPane::AllowShowOnPaneMenu`.)|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Überschreibt [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCAutoHideBar::Create](#create)|Erstellt eine Steuerleiste und fügt sie an das [CPane-Objekt](../../mfc/reference/cpane-class.md) an. (Überschreibt [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Wird von Framework aufgerufen, kurz bevor ein spezielles Bereichsmenü angezeigt wird. (Überschreibt [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Überschreibt [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Streckt einen Bereich vertikal oder horizontal. (Überschreibt [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|Die Zeitverzögerung zwischen dem Zeitpunkt, zu dem der Benutzer den Mauszeiger über eine [CMFCAutoHideButton-Klasse](../../mfc/reference/cmfcautohidebutton-class.md) setzt, und dem Zeitpunkt, zu dem das Framework das zugehörige Fenster anzeigt.|

## <a name="remarks"></a>Bemerkungen

Wenn der Benutzer für einen Dockbereich den Modus „Automatisches Ausblenden“ auswählt, erstellt das Framework automatisch ein `CMFCAutoHideBar`-Objekt. Außerdem werden die erforderlichen [CAutoHideDockSite-](../../mfc/reference/cautohidedocksite-class.md) und [CMFCAutoHideButton-Objekte](../../mfc/reference/cmfcautohidebutton-class.md) erstellt. Jedes `CAutoHideDockSite`-Objekt bezieht sich auf ein einzelne `CMFCAutoHideButton`.

Die `CMFCAutoHideBar`-Klasse implementiert die Anzeige einer `CAutoHideDockSite`, wenn ein Benutzer die Maus über eine `CMFCAutoHideButton` bewegt. Wenn die Symbolleiste eine WM_MOUSEMOVE-Meldung empfängt, startet `CMFCAutoHideBar` einen Timer. Wenn der Timer fertig ist, sendet er eine WM_TIMER-Ereignisbenachrichtigung an die Symbolleiste. Die Symbolleiste verarbeitet dieses Ereignis, indem geprüft wird, ob sich der Mauszeiger über der gleichen automatisch ausblendbaren Schaltfläche befindet, über der er sich befand, als der Zeitgeber gestartet wurde. Wenn dies der Fall ist, wird die angehängte `CAutoHideDockSite` angezeigt.

Sie können die Länge der Verzögerung für den Timer durch Festlegen von `m_nShowAHWndDelay` steuern. Der Standardwert ist 400 ms.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Erstellen eines `CMFCAutoHideBar`-Objekts und die Verwendung der `GetDockSiteRow`-Methode.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxautohidebar.h

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a>CMFCAutoHideBar::AddAutoHideWindow

Fügt einem `CDockablePane` .Fenster Funktionalität hinzu, die ihm automatisches Ausblenden ermöglicht.

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parameter

*pAutoHideWnd*<br/>
[in] Das Fenster, das Sie ausblenden möchten.

*dwAlignment*<br/>
[in] Ein Wert, der die Ausrichtung der Schaltfläche "Auto-Hide" mit dem Anwendungsfenster angibt.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Der *Parameter dwAlignment* gibt an, wo sich die Schaltfläche zum automatischen Ausblenden in der Anwendung befindet. Der Parameter kann auf einen der folgenden Werte festgelegt werden:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCAutoHidebar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCAutoHideBar::CalcFixedLayout

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

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a>CMFCAutoHideBar::CMFCAutoHideBar

Erstellt ein CMFCAutoHideBar-Objekt.

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebarcreate"></a><a name="create"></a>CMFCAutoHideBar::Erstellen

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>

*dwStyle*<br/>

*Rect*<br/>

*pParentWnd*<br/>

*nID*<br/>

*dwControlBarStyle*<br/>

*pContext*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a>CMFCAutoHideBar::GetFirstAHWindow

Gibt einen Zeiger auf das erste automatisch ausblendbare Fenster in der Anwendung zurück.

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>Rückgabewert

Das erste automatisch ausblendbare Fenster in der Anwendung oder NULL, wenn keines vorhanden ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a>CMFCAutoHideBar::GetVisibleCount

Ruft die Anzahl der angezeigten automatisch ausblendbaren Schaltflächen ab.

```
int GetVisibleCount();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der angezeigten automatisch ausblendbaren Schaltflächen zurück.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a>CMFCAutoHideBar::m_nShowAHWndDelay

Die Zeitverzögerung zwischen dem Zeitpunkt, zu dem der Benutzer den Mauszeiger über eine [CMFCAutoHideButton-Klasse](../../mfc/reference/cmfcautohidebutton-class.md) setzt, und dem Zeitpunkt, zu dem das Framework das zugehörige Fenster anzeigt.

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer den Mauszeiger über einem `CMFCAutoHideButton`platziert, kommt es zu einer leichten Verzögerung, bevor das Framework das zugehörige Fenster anzeigt. Dieser Parameter bestimmt die Länge dieser Verzögerung in Millisekunden.

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCAutoHideBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parameter

[in] *CPoint*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a>CMFCAutoHideBar::RemoveAutoHideWindow

Entfernt und zerstört das Automatisch-im-Hintergrund-Fenster.

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>Parameter

CDockablePane* *pAutoHideWnd* Das zu entfernende automatische Ausblendfenster.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a>CMFCAutoHideBar::SetActiveInGroup

Kennzeichnet eine Automatisch-im-Hintergrund-Leiste als aktiv.

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>Parameter

[in] BOOL *bActive* TRUE, um auf aktiv zu setzen; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Siehe [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a>CMFCAutoHideBar::SetRecentVisibleState

```
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>Parameter

*bState*<br/>
[in] Zustand, den festgelegt werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a>CMFCAutoHideBar::ShowAutoHideWindow

Zeigt das automatisch ausblendbare Fenster an.

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parameter

*pAutoHideWnd*<br/>
[in] Fenster, das angezeigt werden soll.

*bShow*<br/>
[in] TRUE, um das Fenster anzuzeigen.

*bDelay*<br/>
[in] Dieser Parameter wird ignoriert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a>CMFCAutoHideBar::StretchPane

Ändert die Größe der automatisch ausblendbaren Leiste im reduzierten Zustand, um dem `CMFCAutoHideButton` -Objekt zu entsprechen.

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>Parameter

*nLänge*<br/>
[in] Der Wert wird in der Basisimplementierung nicht verwendet. Verwenden Sie diesen Wert in abgeleiteten Implementierungen, um die Länge des Bereichs mit der geänderten Größe anzuzeigen.

*bVert*<br/>
[in] Der Wert wird in der Basisimplementierung nicht verwendet. Verwenden Sie in abgeleiteten Implementierungen TRUE, um den Fall zu behandeln, in dem die automatische Ausblendleiste vertikal reduziert wird, und FALSE für den Fall, dass die automatische Ausblendleiste horizontal reduziert wird.

### <a name="return-value"></a>Rückgabewert

Die resultierende Größe des Bereichs, dessen Größe geändert wurde.

### <a name="remarks"></a>Bemerkungen

Abgeleitete Klassen können diese Methode zum Anpassen des Verhaltens außer Kraft setzen.

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideBar::UnSetAutoHideMode

Deaktiviert den automatischen Ausblendemodus für eine Gruppe von automatisch ausblendbaren Leisten.

```
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>Parameter

[in] pFirstBarInGroup A-Zeiger auf die erste auto-hide-Leiste in der Gruppe.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a>CMFCAutoHideBar::UpdateVisibleState

Wird vom Framework aufgerufen, wenn die automatisch ausblendbare Leiste neu gezeichnet werden muss.

```
void UpdateVisibleState();
```

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[CAutoHideDockSite-Klasse](../../mfc/reference/cautohidedocksite-class.md)<br/>
[CMFCAutoHideButton-Klasse](../../mfc/reference/cmfcautohidebutton-class.md)
