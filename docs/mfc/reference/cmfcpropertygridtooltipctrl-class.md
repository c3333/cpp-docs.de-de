---
title: Cmfcpropertygridtooltipctrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: 82d5f021204628121be242845583797348d02120
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840751"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Cmfcpropertygridtooltipctrl-Klasse

Implementiert ein QuickInfo-Steuerelement, das von der [cmfcpropertygridctrl-Klasse](../../mfc/reference/cmfcpropertygridctrl-class.md) verwendet wird, um Quick Infos anzuzeigen.

## <a name="syntax"></a>Syntax

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|[Cmfcpropertygridtooltipctrl:: cmfcpropertygridtooltipctrl](#cmfcpropertygridtooltipctrl)|Erstellt ein `CMFCPropertyGridToolTipCtrl`-Objekt.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[Cmfcpropertygridtooltipctrl:: Create](#create)|Erstellt ein Fenster für das QuickInfo-Steuerelement.|
|[Cmfcpropertygridtooltipctrl::D eaktivierungs](#deactivate)|Deaktiviert das ToolTip-Steuerelement und blendet es aus.|
|[Cmfcpropertygridtooltipctrl:: getlastrect](#getlastrect)|Gibt die Koordinaten der letzten Position des QuickInfo-Steuer Elements zurück.|
|[Cmfcpropertygridtooltipctrl:: Hide](#hide)|Verbirgt das ToolTip-Steuerelement.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Wird von der [CWinApp](../../mfc/reference/cwinapp-class.md) -Klasse verwendet, um Fenster Meldungen zu übersetzen, bevor diese an die Windows-Funktionen [translatemess](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. (Überschreibt [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[Cmfcpropertygridtooltipctrl:: settextmargin](#settextmargin)|Legt den Abstand zwischen dem QuickInfo-Text und dem Rahmen des QuickInfo-Fensters fest.|
|[Cmfcpropertygridtooltipctrl:: Track](#track)|Zeigt das ToolTip-Steuerelement an.|

## <a name="remarks"></a>Bemerkungen

Quick Infos werden angezeigt, wenn der Zeiger auf einen Eigenschaftsnamen zeigt. Die [cmfcpropertygridtooltipctrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) -Klasse zeigt eine QuickInfo an, sodass Sie vom Benutzer leicht lesbar ist. Normalerweise wird die Position einer QuickInfo durch die Position des Zeigers bestimmt. Mit dieser Klasse wird die QuickInfo über dem Eigenschaftsnamen angezeigt und ähnelt der Erweiterung der natürlichen Eigenschaft, sodass der Eigenschaftsname vollständig sichtbar ist.

MFC erstellt dieses Steuerelement automatisch und verwendet es in der [cmfcpropertygridctrl-Klasse](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein Objekt der `CMFCPropertyGridToolTipCtrl` -Klasse erstellt wird und wie das ToolTip-Steuerelement angezeigt wird.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Cmfcpropertygridtooltipctrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxpropertygridtooltipctrl. h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a> Cmfcpropertygridtooltipctrl:: cmfcpropertygridtooltipctrl

Erstellt ein `CMFCPropertyGridToolTipCtrl`-Objekt.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a> Cmfcpropertygridtooltipctrl:: Create

Erstellt ein Fenster für das QuickInfo-Steuerelement.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parameter

*pwndparent*<br/>
in Ein Zeiger auf das übergeordnete Fenster.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Fenster erfolgreich erstellt wurde. andernfalls false.

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a> Cmfcpropertygridtooltipctrl::D eaktivierungs

Deaktiviert das ToolTip-Steuerelement und blendet es aus.

```cpp
void Deactivate();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode legt die letzte Position und den Text auf leere Werte fest, sodass in zukünftigen Aufrufen von [cmfcpropertygridtooltipctrl:: Track](#track) die QuickInfo angezeigt wird.

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a> Cmfcpropertygridtooltipctrl:: getlastrect

Gibt die Koordinaten der letzten Position des QuickInfo-Steuer Elements zurück.

```cpp
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
vorgenommen Enthält die letzte Position des QuickInfo-Steuer Elements.

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a> Cmfcpropertygridtooltipctrl:: Hide

Verbirgt das ToolTip-Steuerelement.

```cpp
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a> Cmfcpropertygridtooltipctrl:: settextmargin

Legt den Abstand zwischen dem QuickInfo-Text und dem Rahmen des QuickInfo-Fensters fest.

```cpp
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parameter

*ntextmargin*<br/>
in Gibt den Abstand zwischen dem QuickInfo-Steuerelement Text und dem Rahmen des QuickInfo-Fensters an. Der Standardwert ist 10 Pixel.

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a> Cmfcpropertygridtooltipctrl:: Track

Zeigt das ToolTip-Steuerelement an.

```cpp
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
in Gibt die Position und die Größe des QuickInfo-Steuer Elements an.

*Text*<br/>
in Gibt den Text an, der in der QuickInfo angezeigt werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode zeigt das QuickInfo-Steuerelement an der von *Rect*angegebenen Position und Größe an. Wenn Position, Größe und Text seit dem letzten Aufruf dieser Methode nicht geändert wurden, hat diese Methode keine Auswirkungen.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
