---
title: CMFCReBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
ms.openlocfilehash: a07f30fb00dd00e7a6315b8935731ccfc7500843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361697"
---
# <a name="cmfcrebar-class"></a>CMFCReBar-Klasse

Ein `CMFCReBar` Objekt ist eine Steuerleiste, die Layout-, Persistenz- und Statusinformationen für Bewehrungssteuerelemente bereitstellt.
Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|Fügt einer Bewehrung ein Band hinzu.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Überschreibt [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCReBar::CanFloat](#canfloat)|(Überschreibt [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CMFCReBar::Erstellen](#create)|Erstellt das Bewehrungssteuerelement und `CMFCReBar` fügt es an das Objekt an.|
|[CMFCReBar::EnableDocking](#enabledocking)|(Überschreibt [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCReBar::GetRebarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Bietet direkten Zugriff auf das zugrunde liegende gemeinsame [CReBarCtrl-Steuerelement.](../../mfc/reference/crebarctrl-class.md)|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Überschreibt [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCRebar::OnToolHittest](#ontoolhittest)|(Überschreibt [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Überschreibt [CBasePane::OnUpdateCmdUI](cbasepane-class.md).)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Überschreibt [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>Bemerkungen

Ein `CMFCReBar` Objekt kann eine Vielzahl von untergeordneten Fenstern enthalten. Dazu gehören Bearbeitungsfelder, Symbolleisten und Listenfelder. Sie können die Größe der Bewehrung programmgesteuert ändern, oder der Benutzer kann die Größe der Bewehrung manuell ändern, indem Er die Greiferleiste gezogen wird. Sie können den Hintergrund eines Bewehrungsobjekts auch auf eine Bitmap Ihrer Wahl festlegen.

Ein Bewehrungsobjekt verhält sich ähnlich wie ein Symbolleistenobjekt. Ein Bewehrungssteuerelement kann ein oder mehrere Bänder enthalten, und jedes Band kann eine Greiferleiste, eine Bitmap, eine Textbeschriftung und ein untergeordnetes Fenster enthalten.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCReBar` -Klasse. Das Beispiel zeigt, wie Sie ein Bewehrungssteuerelement erstellen und ihm ein Band hinzufügen. Das Band fungiert als interne Symbolleiste. Dieser Codeausschnitt ist Teil des [Rebar-Testbeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)\
&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;€&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;€&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;€&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxRebar.h

## <a name="cmfcrebaraddbar"></a><a name="addbar"></a>CMFCReBar::AddBar

Fügt einer Bewehrung ein Band hinzu.

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
[in, out] Ein Zeiger auf das untergeordnete Fenster, das in die Bewehrung eingefügt werden soll. Das referenzierte Objekt muss über den **WS_CHILD** Fensterstil verfügen.

*pszText*<br/>
[in] Gibt den Text an, der auf der Bewehrung angezeigt werden soll. Der Text ist nicht Teil des untergeordneten Fensters. Vielmehr wird es auf der Bewehrung selbst angezeigt.

*pbmp*<br/>
[in, out] Gibt die Bitmap an, die auf dem Bewehrungshintergrund angezeigt werden soll.

*dwStyle*<br/>
[in] Enthält den Stil, der auf das Band angewendet werden soll. Eine vollständige Liste der Bandstile finden `fStyle` Sie in der [REBARBANDINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) in der Windows SDK-Dokumentation.

*clrFore*<br/>
[in] Stellt die Vordergrundfarbe der Bewehrung dar.

*clrBack*<br/>
[in] Stellt die Hintergrundfarbe der Bewehrung dar.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Band erfolgreich zur Bewehrung hinzugefügt wurde; andernfalls FALSE.

## <a name="cmfcrebarcreate"></a><a name="create"></a>CMFCReBar::Erstellen

Erstellt das Bewehrungssteuerelement und fügt es an das [CMFCReBar-Objekt](../../mfc/reference/cmfcrebar-class.md) an.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
[in, out] Ein Zeiger auf das übergeordnete Fenster dieses Bewehrungssteuerelements.

*dwCtrlStyle*<br/>
[in] Gibt den Stil für das Bewehrungssteuerelement an. Der Standardstilwert ist **RBS_BANDBORDERS**, der schmale Linien anzeigt, um benachbarte Bänder auf dem Bewehrungssteuerelement zu trennen. Eine Liste gültiger Stile finden Sie unter [Bewehrungssteuerungsstile](/windows/win32/Controls/rebar-control-styles) in der Windows SDK-Dokumentation.

*dwStyle*<br/>
[in] Der Fensterstil des Bewehrungssteuerelements. Eine Liste gültiger Stile finden Sie unter [Fensterformate](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
[in] Die untergeordnete Fenster-ID der Bewehrung.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Bewehrung erfolgreich erstellt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcrebargetrebarctrl"></a><a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl

Bietet direkten `CReBarCtrl` Zugriff auf das `CMFCReBar` zugrunde liegende allgemeine Steuerelement für Objekte.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf `CReBarCtrl` das zugrunde liegende Objekt.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die allgemeine Steuerungsfunktionalität von Windows zu nutzen, wenn Sie die Bewehrung anpassen.

## <a name="cmfcrebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

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

## <a name="cmfcrebarcanfloat"></a><a name="canfloat"></a>CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcrebarenabledocking"></a><a name="enabledocking"></a>CMFCReBar::EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parameter

[in] *dwDockStyle*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcrebargetrebarbandinfosize"></a><a name="getrebarbandinfosize"></a>CMFCReBar::GetRebarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcrebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parameter

[in] *CPoint*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcrebarontoolhittest"></a><a name="ontoolhittest"></a>CMFCRebar::OnToolHittest

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

## <a name="cmfcrebaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parameter

[in] *pTarget*<br/>
[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcrebarsetpanealignment"></a><a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Parameter

[in] *dwAlignment*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl-Klasse](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
