---
title: Cautohidedocksite-Klasse
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
ms.openlocfilehash: 2779e643b15179b0017535fbfbb144f94e1aedbe
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562011"
---
# <a name="cautohidedocksite-class"></a>Cautohidedocksite-Klasse

Der `CAutoHideDockSite` erweitert die [cdocksite-Klasse](../../mfc/reference/cdocksite-class.md) , um die automatisch Ausblend baren Andock Bereiche zu implementieren.

## <a name="syntax"></a>Syntax

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|name|BESCHREIBUNG|
|`CAutoHideDockSite::CAutoHideDockSite`|Erstellt ein `CAutoHideDockSite`-Objekt.|
|`CAutoHideDockSite::~CAutoHideDockSite`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|name|BESCHREIBUNG|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Gibt an, ob das `CAutoHideDockSite` im Menübereich angezeigt wird.|
|[Cautohidedocksite:: canakzeptpane](#canacceptpane)|Bestimmt, ob ein Basis Fenster Objekt von der [cmfcautohidebar-Klasse](../../mfc/reference/cmfcautohidebar-class.md)abgeleitet wird.|
|[Cautohidedocksite::D ockpane](#dockpane)|Dockt einen Bereich an dieses `CAuotHideDockSite` Objekt an.|
|[Cautohidedocksite:: getalignrect](#getalignrect)|Ruft die Größe der Dock Site in Bildschirm Koordinaten ab.|
|[Cautohidedocksite:: repositionbereichs](#repositionpanes)|Zeichnet den Bereich auf dem `CAutoHideDockSite` mit den globalen Rändern und dem Schaltflächen Abstand neu.|
|[Cautohidedocksite:: Seto ffsetleft](#setoffsetleft)|Legt den Rand auf der linken Seite der Andock Leiste fest.|
|[Cautohidedocksite:: s](#setoffsetright)|Legt den Rand auf der rechten Seite der Andock Leiste fest.|
|[Cautohidedocksite:: undortaudehidemode](#unsetautohidemode)|Ruft [cmfcautohidebar:: unsetaudehidemode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) für-Objekte auf dem-Objekt auf `CAutoHideDockSite` .|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|Name|BESCHREIBUNG|
|[Cautohidedocksite:: m_nExtraSpace](#m_nextraspace)|Definiert die Größe des Leerraums zwischen den Symbolleisten und dem Rand der Andock Leiste. Dieser Platz wird vom linken oder oberen Rand abhängig von der Ausrichtung des Andock Bereichs gemessen.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie [CFrameWndEx:: enableautohidebereiche](../../mfc/reference/cframewndex-class.md#enableautohidepanes)aufzurufen, erstellt das Framework automatisch ein- `CAutoHideDockSite` Objekt. In den meisten Fällen ist es nicht erforderlich, diese Klasse direkt zu instanziieren oder zu verwenden.

Die Andock Leiste ist die Lücke zwischen der linken Seite des Andock Bereichs und der linken Seite der [cmfcautohidebutton-Klasse](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein `CAutoHideDockSite` -Objekt von einem `CMFCAutoHideBar` -Objekt abgerufen wird und wie der linke und rechte Rand der Andock Leiste festgelegt wird.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxautohidedocksite. h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a> Cautohidedocksite:: canakzeptpane

Bestimmt, ob ein Basis Fenster ein [cmfcautohidebar](../../mfc/reference/cmfcautohidebar-class.md) -Objekt ist oder von abgeleitet ist `CMFCAutoHideBar` .

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parameter

*pbar*\
in Der Basisbereich, den das Framework testet.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn *pbar* von abgeleitet ist `CMFCAutoHideBar` . Andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn ein Basis Bereichs Objekt von abgeleitet ist `CMFCAutoHideBar` , kann es einen enthalten `CAutoHideDockSite` .

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a> Cautohidedocksite::D ockpane

Dockt einen Bereich an dieses [cautohidedocksite](../../mfc/reference/cautohidedocksite-class.md) -Objekt an.

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parameter

*folgenden*\
in Der Bereich, der vom Framework angedockt wird.

*dockmethod*\
in Andock Optionen für den Bereich.

*lprect*\
in Ein Rechteck, das die Begrenzungen für den angedockten Bereich angibt.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung verwendet nicht den Parameter *dockmethod*, der zur zukünftigen Verwendung bereitgestellt wird.

Wenn *lprect* auf NULL festgelegt ist, legt das Framework den Bereich am Standard Speicherort auf der Dock Site ab. Wenn die Dock Site horizontal ist, befindet sich der Standard Speicherort ganz links von der Dock Site. Andernfalls befindet sich der Standard Speicherort am oberen Rand der Dock Site.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a> Cautohidedocksite:: getalignrect

Ruft die Größe der Dock Site in Bildschirm Koordinaten ab.

```cpp
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Parameter

*Rect*\
in Ein Verweis auf ein Rechteck. Die-Methode speichert die Größe der Dock Site in diesem Rechteck.

### <a name="remarks"></a>Bemerkungen

Das Rechteck wird an die Offset Ränder angepasst, sodass Sie nicht eingeschlossen werden.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a> Cautohidedocksite:: m_nExtraSpace

Die Größe des Leerraums zwischen den Rändern der [cautohidedocksite-Klasse](../../mfc/reference/cautohidedocksite-class.md) und den [cmfcautohidebar-Klassen](../../mfc/reference/cmfcautohidebar-class.md) Objekten.

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Bemerkungen

Wenn eine `CMFCAutoHideBar` an einem angedockt wird `CAutoHideDockSite` , sollte Sie nicht die gesamte Dock Site belegen. Diese globale Variable steuert den zusätzlichen Leerraum zwischen dem linken oder oberen Rand von `CMFCAutoHideBar` und dem entsprechenden `CAutoHideDockSite` Rand. Ob der obere oder linke Rand verwendet wird, hängt von der aktuellen Ausrichtung ab.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a> Cautohidedocksite:: Seto ffsetleft

Legt den Rand auf der linken Seite der Andock Leiste fest.

```cpp
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Parameter

*nOffset*<br/>
in Der neue Offset.

### <a name="remarks"></a>Bemerkungen

[Cmfcautohidebar](../../mfc/reference/cmfcautohidebar-class.md) -Objekte werden statisch auf dem- `CAutoHideDockSite` Objekt positioniert. Dies bedeutet, dass der Benutzer den Speicherort von Objekten nicht manuell ändern kann `CMFCAutoHideBar` . Die `SetOffsetLeft` -Methode steuert den Abstand zwischen der linken Seite `CMFCAutoHideBar` und der linken Seite des `CAutoHideDockSite` .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a> Cautohidedocksite:: s

Legt den Rand auf der rechten Seite der Andock Leiste fest.

```cpp
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Parameter

*nOffset*<br/>
in Der neue Offset.

### <a name="remarks"></a>Bemerkungen

[Cmfcautohidebar](../../mfc/reference/cmfcautohidebar-class.md) -Objekte werden statisch auf dem- `CAutoHideDockSite` Objekt positioniert. Dies bedeutet, dass der Benutzer den Speicherort der Objekte nicht manuell ändern kann `CMFCAutoHideBar` . Die `SetOffsetRight` -Methode steuert den Abstand zwischen der rechten Seite der rechten `CMFCAutoHideBar` und der rechten Seite von `CAutoHideDockSite` .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a> Cautohidedocksite:: repositionbereichs

Zeichnet die Bereiche auf der [cautohidedocksite](../../mfc/reference/cautohidedocksite-class.md)neu.

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parameter

*rectnewclientarea*\
in Ein reservierter Wert.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung verwendet nicht " *rectnewclientarea*". Die Bereiche werden mithilfe der globalen Symbolleisten Ränder und des Schaltflächen Abstands neu gezeichnet.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a> Cautohidedocksite:: undortaudehidemode

Ruft [cmfcautohidebar:: unsetaudehidemode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) für Objekte auf der Dock Site auf.

```cpp
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Parameter

*paudehidetoolbar*\
in Ein Zeiger auf einen [cmfcautohidebar](../../mfc/reference/cmfcautohidebar-class.md) -Objektbereich, der sich auf dem befindet `CAutoHideDockSite` .

### <a name="remarks"></a>Bemerkungen

Diese Methode sucht nach der Zeile, die " *paudehidetoolbar*" enthält. Er ruft `CMFCAutoHideBar.UnSetAutoHideMode` für alle- `CMFCAutoHideBar` Objekte in dieser Zeile auf. Wenn *paudehidetoolbar* nicht gefunden wird oder NULL ist, ruft diese Methode `CMFCAutoHideBar.UnSetAutoHideMode` für alle- `CMFCAutoHideBar` Objekte im-Objekt auf `CAutoHideDockSite` .

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cdocksite-Klasse](../../mfc/reference/cdocksite-class.md)
