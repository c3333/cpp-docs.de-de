---
title: CAutoHideDockSite-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
ms.openlocfilehash: 3a4593ac17f0af26517144edb7b01a9ca4203b1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352982"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite-Klasse

Der `CAutoHideDockSite` erweitert die [CDockSite-Klasse,](../../mfc/reference/cdocksite-class.md) um automatisch ausblendende Dockbereiche zu implementieren.

## <a name="syntax"></a>Syntax

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|`CAutoHideDockSite::CAutoHideDockSite`|Erstellt ein `CAutoHideDockSite`-Objekt.|
|`CAutoHideDockSite::~CAutoHideDockSite`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Gibt an, ob der `CAutoHideDockSite` im Bereichsmenü angezeigt wird.|
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Bestimmt, ob ein Basisbereichsobjekt von der [CMFCAutoHideBar-Klasse](../../mfc/reference/cmfcautohidebar-class.md)abgeleitet wird.|
|[CAutoHideDockSite::DockPane](#dockpane)|Dockt einen Bereich `CAuotHideDockSite` an dieses Objekt an.|
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Ruft die Größe der Dock-Site in Bildschirmkoordinaten ab.|
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|Zeichnet den Bereich `CAutoHideDockSite` auf der mit den globalen Rändern und Schaltflächenabständen neu.|
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Legt den Rand auf der linken Seite der Dockingleiste fest.|
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Legt den Rand auf der rechten Seite der Dockingleiste fest.|
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Ruft [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) für `CAutoHideDockSite`Objekte auf der auf.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|Name|BESCHREIBUNG|
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Definiert die Größe des Abstands zwischen den Symbolleisten und dem Rand der Andockleiste. Dieser Raum wird je nach Ausrichtung für den Dock-Raum entweder von der linken kante oder vom oberen Rand gemessen.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)aufrufen, erstellt `CAutoHideDockSite` das Framework automatisch ein Objekt. In den meisten Fällen sollten Sie diese Klasse nicht direkt instanziieren oder verwenden müssen.

Die Dockingleiste ist der Abstand zwischen der linken Seite des Dockfensters und der linken Seite der [CMFCAutoHideButton-Klasse](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CAutoHideDockSite` veranschaulicht, `CMFCAutoHideBar` wie ein Objekt aus einem Objekt abgerufen wird und wie der linke und rechte Rand der Andockleiste festgelegt werden.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopf:** afxautohidedocksite.h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane

Bestimmt, ob ein Basisbereich ein [CMFCAutoHideBar-Objekt](../../mfc/reference/cmfcautohidebar-class.md) ist oder von `CMFCAutoHideBar`abgeleitet wird.

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*Pbar*|[in] Der Basisbereich, den das Framework testet.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn *pBar* von `CMFCAutoHideBar`abgeleitet ist ; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Wenn ein Basisbereichsobjekt `CMFCAutoHideBar`von abgeleitet wird, kann es eine `CAutoHideDockSite`enthalten.

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a>CAutoHideDockSite::DockPane

Dockt einen Bereich an dieses [CAutoHideDockSite-Objekt](../../mfc/reference/cautohidedocksite-class.md) an.

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*pWnd*|[in] Der Bereich, den das Framework andockt.|
|*dockMethode*|[in] Dockingoptionen für den Bereich.|
|*lpRect*|[in] Ein Rechteck, das die Grenzen für den angedockten Bereich angibt.|

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung verwendet nicht den Parameter *dockMethod*, der für die zukünftige Verwendung bereitgestellt wird.

Wenn *lpRect* NULL ist, legt das Framework den Bereich an der Standardposition auf der Docksite ab. Wenn die Dock-Site horizontal ist, befindet sich die Standardposition ganz links vom Dock-Standort. Andernfalls befindet sich der Standardspeicherort am oberen Rand der Dock-Site.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect

Ruft die Größe der Dock-Site in Bildschirmkoordinaten ab.

```
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*Rect*|[in] Ein Verweis auf ein Rechteck. Die Methode speichert die Größe der Dock-Site in diesem Rechteck.|

### <a name="remarks"></a>Bemerkungen

Das Rechteck wird für die Versatzränder angepasst, sodass sie nicht einbezogen werden.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace

Die Größe des Abstands zwischen den Kanten der [CAutoHideDockSite-Klasse](../../mfc/reference/cautohidedocksite-class.md) und der [CMFCAutoHideBar-Klasse.](../../mfc/reference/cmfcautohidebar-class.md)

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Bemerkungen

Wenn `CMFCAutoHideBar` a an einem `CAutoHideDockSite`angedockt ist, sollte es nicht die gesamte Dock-Site belegen. Diese globale Variable steuert den zusätzlichen Abstand zwischen `CMFCAutoHideBar` dem `CAutoHideDockSite` linken oder oberen Rand der und der entsprechenden Kante. Ob der obere oder linke Rand verwendet wird, hängt von der aktuellen Ausrichtung ab.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft

Legt den Rand auf der linken Seite der Dockingleiste fest.

```
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Parameter

*nOffset*<br/>
[in] Der neue Offset.

### <a name="remarks"></a>Bemerkungen

[CMFCAutoHideBar-Objekte](../../mfc/reference/cmfcautohidebar-class.md) werden statisch `CAutoHideDockSite` auf dem Objekt positioniert. Dies bedeutet, dass der Benutzer `CMFCAutoHideBar` den Speicherort von Objekten nicht manuell ändern kann. Die `SetOffsetLeft` Methode steuert den Abstand zwischen der `CMFCAutoHideBar` linken Seite der `CAutoHideDockSite`linken und der linken Seite des .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight

Legt den Rand auf der rechten Seite der Dockingleiste fest.

```
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Parameter

*nOffset*<br/>
[in] Der neue Offset.

### <a name="remarks"></a>Bemerkungen

[CMFCAutoHideBar-Objekte](../../mfc/reference/cmfcautohidebar-class.md) werden statisch `CAutoHideDockSite` auf dem Objekt positioniert. Dies bedeutet, dass der Benutzer den `CMFCAutoHideBar` Speicherort der Objekte nicht manuell ändern kann. Die `SetOffsetRight` Methode steuert den Abstand zwischen der `CMFCAutoHideBar` rechten Seite der `CAutoHideDockSite`rechten und der rechten Seite des .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes

Zeichnet die Bereiche auf der [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)neu.

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*rectNewClientArea*|[in] Ein reservierter Wert.|

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung verwendet nicht *rectNewClientArea*. Es zeichnet die Bereiche mit den globalen Symbolleistenrändern und Demonkenabständen neu.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode

Ruft [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) für Objekte auf der Dock-Site auf.

```
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pAutoHideToolbar*|[in] Ein Zeiger auf einen [CMFCAutoHideBar-Objektbereich,](../../mfc/reference/cmfcautohidebar-class.md) der sich auf der `CAutoHideDockSite`befindet.|

### <a name="remarks"></a>Bemerkungen

Diese Methode sucht nach der Zeile, die *pAutoHideToolbar*enthält. Es `CMFCAutoHideBar.UnSetAutoHideMode` ruft nach `CMFCAutoHideBar` allen Objekten in dieser Zeile. Wenn *pAutoHideToolbar* nicht gefunden wird oder NULL `CMFCAutoHideBar.UnSetAutoHideMode` ist, `CMFCAutoHideBar` ruft `CAutoHideDockSite`diese Methode alle Objekte auf der auf.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite-Klasse](../../mfc/reference/cdocksite-class.md)
