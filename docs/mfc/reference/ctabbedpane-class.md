---
title: Ctabbedpane-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
ms.openlocfilehash: cfc0a3099b1d5ff9bd1093cc911745bd61cde64c
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686638"
---
# <a name="ctabbedpane-class"></a>Ctabbedpane-Klasse

Implementiert die Funktionalität eines Bereichs mit abtrennbaren Registerkarten.

oder ausführlichere Informationen finden Sie im Quellcode, der sich im Ordner **VC \\ atlmfc \\ src \\ MFC** Ihrer Visual Studio-Installation befindet.

## <a name="syntax"></a>Syntax

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|Standardkonstruktor|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|(Überschreibt [cbasetabbedpane::D etachpane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Aktiviert oder deaktiviert die automatische Registerkartenfärbung.|
|[CTabbedPane::FloatTab](#floattab)|Gibt einen Bereich aus, aber nur, wenn sich der Bereich derzeit in einer ablösbaren Registerkarte befindet. (überschreibt [cbasetabbedpane:: floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Gibt die Größe und Position des Registerkartenbereichs im Fenster im Registerkartenformat zurück.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Bestimmt, ob der Bereich im Registerkartenformat automatisch in den Hintergrundmodus gewechselt werden kann. (Überschreibt [cbasetabbedpane:: hasautohidemode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Bestimmt, ob sich die Registerkarten am unteren Rand des Fensters befinden.|
|[CTabbedPane::ResetTabs](#resettabs)|Setzt alle Bereiche im Registerkartenformat auf den Standardstatus zurück.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Legt eine Liste benutzerdefinierter Farben fest, die verwendet werden kann, wenn die Funktion für automatische Farben aktiviert ist.|

### <a name="data-members"></a>Datenelemente

|name|Beschreibung|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Die Standardposition für Registerkarten in der Anwendung.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Laufzeitklasseninformationen für ein benutzerdefiniertes `CMFCTabCtrl`-abgeleitetes Objekt.|

## <a name="remarks"></a>Bemerkungen

Das Framework erstellt automatisch eine Instanz dieser Klasse, wenn ein Benutzer einen Bereich an einen anderen anfügt, indem es auf die Beschriftung des zweiten Bereichs verweist. Alle der vom Framework erstellten Bereiche im Registerkartenformat besitzen eine ID von "-1".

Um reguläre Registerkarten anstelle von Registerkarten im Outlook-Stil anzugeben, übergeben Sie den AFX_CBRS_REGULAR_TABS Stil an die [CDockablePane:: foateex](../../mfc/reference/cdockablepane-class.md#createex) -Methode.

Wenn Sie einen Bereich im Registerkartenformat mit abtrennbaren Registerkarten erstellen, kann der Bereich automatisch durch das Framework zerstört werden. Speichern Sie daher nicht den Zeiger. Um einen Zeiger zum Bereich im Registerkartenformat zu erhalten, rufen Sie die `CBasePane::GetParentTabbedPane`-Methode auf.

## <a name="examples"></a>Beispiele

In diesem Beispiel erstellen wir ein `CTabbedPane`-Objekt. Als nächstes verwenden wir [cbasetabbedpane:: addTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) , um zusätzliche Registerkarten anzufügen.

```cpp
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),
    TRUE,
    (UINT) -1,
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |
    WS_CLIPCHILDREN | CBRS_LEFT |
    CBRS_FLOAT_MULTI))
{
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create
}

pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```

Eine weitere Möglichkeit zum Erstellen eines Steuer leisten Objekts im Registerkarten Format ist die Verwendung von [CDockablePane:: attachdetabwnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). Die- `AttachToTabWnd` Methode erstellt dynamisch ein Pane-Objekt im Registerkarten Format mit Lauf Zeit Klassen Informationen, die von [CDockablePane:: settabbedpanertc](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)festgelegt werden.

In diesem Beispiel erstellen wir einen dynamischen Bereich im Registerkartenformat, fügen zwei Registerkarten an und legen die zweite Registerkarte als nicht entfernbar fest.

```cpp
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxtabbedpane. h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a> Ctabbedpane::D etachpane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

in *pbar*<br/>

in *Bhide*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a> Ctabbedpane:: enabletabautocolor

Aktiviert oder deaktiviert die automatische Registerkartenfärbung.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*benabel*<br/>
in TRUE, um die automatische Farbgebung von Registerkarten zu aktivieren. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese statische Methode, um die automatische Farbgebung von Registerkarten in allen Bereichen im Registerkarten Format in der Anwendung zu aktivieren oder zu deaktivieren. Wenn diese Funktion aktiviert ist, wird jede Registerkarte mit ihrer eigenen Farbe gefüllt. Sie finden die Liste der Farben, die zum Durchführen der Farben der Registerkarten verwendet werden, indem Sie die [cmfcbasetabctrl:: getautocolors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) -Methode aufrufen.

Sie können die Liste der Farben angeben, die für Registerkarten verwendet werden, indem Sie [ctabbedpane:: settabautocolors](#settabautocolors)aufrufen.

Diese Option ist standardmäßig deaktiviert.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a> Ctabbedpane:: floattab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

in *pbar*<br/>
in *ntabid*<br/>
in *dockmethod*<br/>
in *Bhide*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a> Ctabbedpane:: gettabarea

Gibt die Größe und Position des Registerkarten Bereichs im Fenster im Registerkarten Format zurück.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parameter

*recttabareon*<br/>
vorgenommen Enthält die Größe und Position des oberen Registerkarten Bereichs in Bildschirm Koordinaten.

*recttabareabottom*<br/>
vorgenommen Enthält die Größe und Position des unteren Registerkarten Bereichs in Bildschirm Koordinaten.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, um zu bestimmen, wie ein Bereich Andocken soll, den ein Benutzer zieht. Wenn der Benutzer einen Bereich über den Registerkarten Bereich des Zielbereichs zieht, versucht das Framework, ihn als neue Registerkarte im Zielbereich hinzuzufügen. Andernfalls wird versucht, den Bereich an der Seite des Zielbereichs anzudocken. Dies umfasst das Erstellen eines neuen Bereichs Containers mit einem Bereichs Teiler, der die beiden Bereiche trennt.

Überschreiben Sie diese Methode in einer `CTabbedPane` von abgeleiteten Klasse, um dieses Verhalten zu ändern.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a> Ctabbedpane:: gettabwnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a> Ctabbedpane:: hasautohidemode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a> Ctabbedpane:: istablocationbottom

Bestimmt, ob sich die Registerkarten am unteren Rand des Fensters befinden.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich der Registerkarten Bereich unten im Fenster im Registerkarten Format befindet. andernfalls false.

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a> Ctabbedpane:: m_bTabsAlwaysTop

Die Standardposition für Registerkarten in der Anwendung.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie dieses statische Element auf "true" fest, um zu erzwingen, dass alle Registerkarten in der Anwendung oben im Registerkarten Bereich angezeigt werden.

Dieser Wert muss festgelegt werden, bevor ein Bereich im Registerkarten Format erstellt wurde.

Der Standardwert ist FALSE.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a> Ctabbedpane:: m_pTabWndRTC

Laufzeitklasseninformationen für ein benutzerdefiniertes `CMFCTabCtrl`-abgeleitetes Objekt.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diese statische Member-Variable auf einen Zeiger auf die Lauf Zeit Klassen Informationen eines von `CMFCTabCtrl` abgeleiteten Objekts fest, wenn Sie ein benutzerdefiniertes Fenster im Registerkarten Format verwenden.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a> Ctabbedpane:: resettabs

Setzt alle Bereiche im Registerkartenformat auf den Standardstatus zurück.

```
static void ResetTabs();
```

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie alle Bereiche im Registerkarten Format auf ihren Standardzustand zurücksetzen. Wenn diese Methode aufgerufen wird, setzt diese Methode die Rahmengrößen und den automatischen Farb Status aller Bereiche im Registerkarten Format zurück.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a> Ctabbedpane:: settabautocolors

Legt eine Liste benutzerdefinierter Farben fest, die verwendet werden, wenn die Funktion für automatische Farben aktiviert ist.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parameter

*arcolors*<br/>
in Enthält das Array von Farben, die festgelegt werden sollen.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Liste der Farben anzupassen, die verwendet werden, wenn die Funktion für automatische Farben aktiviert ist. Dies ist eine statische Funktion und wirkt sich auf alle Bereiche im Registerkarten Format in der Anwendung aus.

Verwenden Sie [ctabbedpane:: enabletabautocolor](#enabletabautocolor) , um das Feature für automatische Farben zu aktivieren oder zu deaktivieren.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md)<br/>
[Cbasetabbedpane-Klasse](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md)
