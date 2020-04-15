---
title: CTabbedPane-Klasse
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
ms.openlocfilehash: 17351eaed585ec34117a2ef825964fd51bd0d86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365949"
---
# <a name="ctabbedpane-class"></a>CTabbedPane-Klasse

Implementiert die Funktionalität eines Bereichs mit abtrennbaren Registerkarten.

oder genauer, siehe den Quellcode im **Ordner\\\\VC\\atlmfc src mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|(Überschreibt [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Aktiviert oder deaktiviert die automatische Registerkartenfärbung.|
|[CTabbedPane::FloatTab](#floattab)|Überschreibt einen Bereich, jedoch nur, wenn sich der Bereich derzeit in einer abnehmbaren Registerkarte befindet. (Überschreibt [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Gibt die Größe und Position des Registerkartenbereichs im Fenster im Registerkartenformat zurück.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Bestimmt, ob der Bereich im Registerkartenformat automatisch in den Hintergrundmodus gewechselt werden kann. (Überschreibt [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Bestimmt, ob sich die Registerkarten am unteren Rand des Fensters befinden.|
|[CTabbedPane::ResetTabs](#resettabs)|Setzt alle Bereiche im Registerkartenformat auf den Standardstatus zurück.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Legt eine Liste benutzerdefinierter Farben fest, die verwendet werden kann, wenn die Funktion für automatische Farben aktiviert ist.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Die Standardposition für Registerkarten in der Anwendung.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Laufzeitklasseninformationen für ein benutzerdefiniertes `CMFCTabCtrl`-abgeleitetes Objekt.|

## <a name="remarks"></a>Bemerkungen

Das Framework erstellt automatisch eine Instanz dieser Klasse, wenn ein Benutzer einen Bereich an einen anderen anfügt, indem es auf die Beschriftung des zweiten Bereichs verweist. Alle der vom Framework erstellten Bereiche im Registerkartenformat besitzen eine ID von "-1".

Um reguläre Registerkarten anstelle von Registerkarten im Outlook-Stil anzugeben, übergeben Sie den AFX_CBRS_REGULAR_TABS-Stil an die [CDockablePane::CreateEx-Methode.](../../mfc/reference/cdockablepane-class.md#createex)

Wenn Sie einen Bereich im Registerkartenformat mit abtrennbaren Registerkarten erstellen, kann der Bereich automatisch durch das Framework zerstört werden. Speichern Sie daher nicht den Zeiger. Um einen Zeiger zum Bereich im Registerkartenformat zu erhalten, rufen Sie die `CBasePane::GetParentTabbedPane`-Methode auf.

## <a name="example"></a>Beispiel

In diesem Beispiel erstellen wir ein `CTabbedPane`-Objekt. Als Nächstes verwenden wir [CBaseTabbedPane::AddTab,](../../mfc/reference/cbasetabbedpane-class.md#addtab) um zusätzliche Registerkarten anzuhängen.

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

## <a name="example"></a>Beispiel

Eine weitere Möglichkeit zum Erstellen eines Registerkarten-Steuerleistenobjekts ist die Verwendung von [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). Die `AttachToTabWnd` Methode erstellt dynamisch ein Registerkartenbereichsobjekt mithilfe von Laufzeitklasseninformationen, die von [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)festgelegt wurden.

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

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxTabbedPane.h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a>CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

[in] *pBar*<br/>

[in] *bHide*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a>CTabbedPane::EnableTabAutoColor

Aktiviert oder deaktiviert die automatische Registerkartenfärbung.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] TRUE, um die automatische Färbung von Registerkarten zu aktivieren; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese statische Methode, um die automatische Färbung von Registerkarten in allen Registerkarten in der Anwendung zu aktivieren oder zu deaktivieren. Wenn diese Funktion aktiviert ist, wird jede Registerkarte mit einer eigenen Farbe gefüllt. Sie können die Liste der Farben finden, die zum Färben der Registerkarten verwendet werden, indem Sie die [CMFCBaseTabCtrl::GetAutoColors-Methode](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) aufrufen.

Sie können die Liste der Farben angeben, die für Registerkarten verwendet werden, indem Sie [CTabbedPane::SetTabAutoColors](#settabautocolors)aufrufen.

Diese Option ist standardmäßig deaktiviert.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a>CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parameter

[in] *pBar*<br/>
[in] *nTabID*<br/>
[in] *dockMethode*<br/>
[in] *bHide*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a>CTabbedPane::GetTabArea

Gibt die Größe und Position des Tabstoppbereichs im Registerkartenfenster zurück.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parameter

*rectTabAreaTop*<br/>
[out] Enthält die Größe und Position des oberen Tabalsbereichs in Bildschirmkoordinaten.

*rectTabAreaBottom*<br/>
[out] Enthält die Größe und Position des unteren Tabalsbereichs in Bildschirmkoordinaten.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, um zu bestimmen, wie ein Bereich angedockt wird, den ein Benutzer zieht. Wenn der Benutzer einen Bereich über den Registerkartenbereich des Zielbereichs zieht, versucht das Framework, ihn als neue Registerkarte des Zielbereichs hinzuzufügen. Andernfalls wird versucht, den Bereich an die Seite des Zielbereichs anzudocken, wodurch ein neuer Bereichscontainer mit einem Bereichsteiler erstellt wird, der die beiden Bereiche trennt.

Überschreiben Sie diese `CTabbedPane`Methode in einer -derived-Klasse, um dieses Verhalten zu ändern.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a>CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a>CTabbedPane::IsTabLocationBottom

Bestimmt, ob sich die Registerkarten am unteren Rand des Fensters befinden.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn sich der Tabstoppbereich am unteren Rand des Registerkartenfensters befindet. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a>CTabbedPane::m_bTabsAlwaysTop

Die Standardposition für Registerkarten in der Anwendung.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen statischen Member auf TRUE fest, um zu erzwingen, dass alle Registerkarten in der Anwendung oben im Registerkartenbereich angezeigt werden.

Sie müssen diesen Wert festlegen, bevor ein Registerkartenbereich erstellt wurde.

Der Standardwert ist FALSE.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC

Laufzeitklasseninformationen für ein benutzerdefiniertes `CMFCTabCtrl`-abgeleitetes Objekt.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diese statische Membervariable auf einen Zeiger `CMFCTabCtrl`auf die Laufzeitklasseninformationen eines -derived-Objekts fest, wenn Sie ein benutzerdefiniertes Registerkartenfenster in einem Registerkartenbereich verwenden.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a>CTabbedPane::ResetTabs

Setzt alle Bereiche im Registerkartenformat auf den Standardstatus zurück.

```
static void ResetTabs();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um alle Registerkartenbereiche in ihren Standardzustand zurückzuversetzen. Beim Aufruf setzt diese Methode die Rahmengrößen und den automatischen Farbstatus aller Registerkartenbereiche zurück.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a>CTabbedPane::SetTabAutoColors

Legt eine Liste benutzerdefinierter Farben fest, die verwendet werden, wenn die automatische Farbfunktion aktiviert ist.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parameter

*arColors*<br/>
[in] Enthält das zu setzende Farbarray.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Liste der Farben anzupassen, die verwendet werden, wenn die automatische Farbfunktion aktiviert ist. Dies ist eine statische Funktion und wirkt sich auf alle Registerkartenbereiche in der Anwendung aus.

Verwenden Sie [CTabbedPane::EnableTabAutoColor,](#enabletabautocolor) um die funktion für die automatische Farbe zu aktivieren oder zu deaktivieren.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane-Klasse](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane-Klasse](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar-Klasse](../../mfc/reference/cmfcoutlookbar-class.md)
