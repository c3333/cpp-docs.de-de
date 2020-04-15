---
title: CMFCDropDownToolBar-Klasse
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: 68dd976471b39d7f50c2f0378b2fce99ad3feeca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367603"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar-Klasse

Eine Symbolleiste, die angezeigt wird, wenn der Benutzer eine Symbolleisten-Schaltfläche der obersten Ebene drückt und gedrückt hält.

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDropDownToolbar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Überschreibt `CPane::AllowShowOnPaneMenu`.)|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Überschreibt [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Überschreibt [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolbar::OnLButtonup](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Überschreibt `CMFCToolBar::OnSendCommand`.)|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Überschreibt [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Bemerkungen

Ein `CMFCDropDownToolBar` Objekt kombiniert das visuelle Erscheinungsbild einer Symbolleiste mit dem Verhalten eines Popupmenüs. Wenn ein Benutzer eine Dropdown-Symbolleistenschaltfläche drückt und hält (siehe [CMFCDropDownToolbarButton Class),](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)wird eine Dropdown-Symbolleiste angezeigt, und der Benutzer kann eine Schaltfläche aus der Dropdown-Symbolleiste auswählen, indem er zu ihr scrollt und die Maustaste loslässt. Nachdem der Benutzer eine Schaltfläche in der Dropdown-Symbolleiste ausgewählt hat, wird diese Schaltfläche als aktuelle Schaltfläche auf der Symbolleiste der obersten Ebene angezeigt.

Eine Dropdown-Symbolleiste kann nicht angepasst oder angedockt werden, und sie hat keinen Abreißzustand.

Die folgende Abbildung `CMFCDropDownToolBar` zeigt ein Objekt:

![Beispiel für CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "Beispiel für CMFCDropDownToolbar")

Sie erstellen `CMFCDropDownToolBar` ein Objekt auf die gleiche Weise wie eine gewöhnliche Symbolleiste (siehe [CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)).

So fügen Sie die Dropdown-Symbolleiste in eine übergeordnete Symbolleiste ein:

1. Reservieren Sie eine Platzhalterressourcen-ID für die Schaltfläche in der übergeordneten Symbolleistenressource.

2. Erstellen `CMFCDropDownToolBarButton` Sie ein Objekt, das die Dropdown-Symbolleiste enthält (weitere Informationen finden Sie unter [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Ersetzen Sie die `CMFCDropDownToolBarButton` Dummy-Schaltfläche durch das Objekt mithilfe von [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Weitere Informationen zu Symbolleistenschaltflächen finden Sie unter [Exemplarische Vorgehensweise: Einstecken von Steuerelementen auf Symbolleisten](../../mfc/walkthrough-putting-controls-on-toolbars.md). Ein Beispiel für eine Dropdown-Symbolleiste finden Sie im Beispielprojekt VisualStudioDemo.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `Create` veranschaulicht, `CMFCDropDownToolBar` wie die Methode in der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Visual Studio Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCDropDownToolbar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFCDropDownToolBar::LoadBitmap

Lädt Symbolleistenbilder aus Anwendungsressourcen.

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>Parameter

*uiResID*<br/>
[in] Die Ressourcen-ID der Bitmap, die auf die heißen Symbolleistenbilder verweist.

*uiColdResID*<br/>
[in] Die Ressourcen-ID der Bitmap, die auf die kalten Symbolleistenbilder verweist.

*uiMenuResID*<br/>
[in] Die Ressourcen-ID der Bitmap, die auf die regulären Menübilder verweist.

*Blockiert*<br/>
[in] TRUE, um die Symbolleiste zu sperren; andernfalls FALSE.

*uiDisabledResID*<br/>
[in] Die Ressourcen-ID der Bitmap, die auf die deaktivierten Symbolleistenbilder verweist.

*uiMenuDisabledResID*<br/>
[in] Die Ressourcen-ID der Bitmap, die auf die deaktivierten Menübilder verweist.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die Methode erfolgreich ausgeführt wird, andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Die [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) -Methode ruft diese Methode auf, um die Bilder zu laden, die der Symbolleiste zugeordnet sind. Setzen Sie diese Methode außer Kraft, um die Bildressourcen benutzerdefiniert zu laden.

Rufen Sie die `LoadBitmapEx` -Methode auf, um nach der Erstellung der Symbolleiste weitere Bilder zu laden.

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFCDropDownToolBar::LoadToolBar

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>Parameter

[in] *uiResID*<br/>

[in] *uiColdResID*<br/>

[in] *uiMenuResID*<br/>

[in] *BOOL*<br/>

[in] *uiDisabledResID*<br/>

[in] *uiMenuDisabledResID*<br/>

[in] *uiHotResID*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a>CMFCDropDownToolbar::OnLButtonup

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parameter

[in] *nFlags*<br/>

[in] *Punkt*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a>CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parameter

[in] *nFlags*<br/>

[in] *Punkt*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a>CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parameter

[in] *pButton*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parameter

[in] *pTarget*<br/>

[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Erstellen](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton-Klasse](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen](../../mfc/walkthrough-putting-controls-on-toolbars.md)
