---
title: CMFCPropertyGridToolTipCtrl-Klasse
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
ms.openlocfilehash: 94d75f914e5f7928d08dd2a87997ab02c4f16832
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361791"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl-Klasse

Implementiert ein QuickInfo-Steuerelement, das die [CMFCPropertyGridCtrl-Klasse](../../mfc/reference/cmfcpropertygridctrl-class.md) zum Anzeigen von QuickInfos verwendet.

## <a name="syntax"></a>Syntax

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipRl](#cmfcpropertygridtooltipctrl)|Erstellt ein `CMFCPropertyGridToolTipCtrl`-Objekt.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCPropertyGridToolTipCtrl::Erstellen](#create)|Erstellt ein Fenster für das QuickInfo-Steuerelement.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Deaktiviert und blendet das QuickInfo-Steuerelement aus.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Gibt die Koordinaten der letzten Position des QuickInfo-Steuerelements zurück.|
|[CMFCPropertyGridToolTipCtrl::Ausblenden](#hide)|Blendet das QuickInfo-Steuerelement aus.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Wird von der Klasse [CWinApp](../../mfc/reference/cwinapp-class.md) verwendet, um Fensternachrichten zu übersetzen, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. (Überschreibt [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Legt den Abstand zwischen dem QuickInfo-Text und dem Rahmen des QuickInfo-Fensters fest.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Zeigt das QuickInfo-Steuerelement an.|

## <a name="remarks"></a>Bemerkungen

QuickInfos werden angezeigt, wenn der Zeiger auf einem Eigenschaftsnamen ruht. Die [CMFCPropertyGridToolTipCtrl-Klasse](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) zeigt eine QuickInfo an, sodass sie für den Benutzer leicht lesbar ist. Normalerweise wird die Position einer QuickInfo durch die Position des Zeigers bestimmt. Wenn Sie diese Klasse verwenden, wird die QuickInfo über dem Eigenschaftennamen angezeigt und ähnelt der Natürlicheneigenschaftserweiterung, sodass der Eigenschaftsname vollständig sichtbar ist.

MFC erstellt dieses Steuerelement automatisch und verwendet es in der [CMFCPropertyGridCtrl-Klasse](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCPropertyGridToolTipCtrl` wie ein Objekt der Klasse erstellt und das QuickInfo-Steuerelement angezeigt wird.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxpropertygridtooltipctrl.h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipRl

Erstellt ein `CMFCPropertyGridToolTipCtrl`-Objekt.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a>CMFCPropertyGridToolTipCtrl::Erstellen

Erstellt ein Fenster für das QuickInfo-Steuerelement.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parameter

*pWndParent*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Fenster erfolgreich erstellt wurde; andernfalls FALSE.

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deactivate

Deaktiviert und blendet das QuickInfo-Steuerelement aus.

```
void Deactivate();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode legt die letzte Position und den letzten Text auf leere Werte fest, sodass zukünftige Aufrufe von [CMFCPropertyGridToolTipCtrl::Track](#track) die QuickInfo anzeigen.

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect

Gibt die Koordinaten der letzten Position des QuickInfo-Steuerelements zurück.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[out] Enthält die letzte Position des QuickInfo-Steuerelements.

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a>CMFCPropertyGridToolTipCtrl::Ausblenden

Blendet das QuickInfo-Steuerelement aus.

```
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin

Legt den Abstand zwischen dem QuickInfo-Text und dem Rahmen des QuickInfo-Fensters fest.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parameter

*nTextMargin*<br/>
[in] Gibt den Abstand zwischen dem QuickInfo-Steuertext und dem Rahmen des QuickInfo-Fensters an. Der Standardwert ist 10 Pixel.

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a>CMFCPropertyGridToolTipCtrl::Track

Zeigt das QuickInfo-Steuerelement an.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Gibt die Position und Größe des QuickInfo-Steuerelements an.

*strText*<br/>
[in] Gibt den Text an, der in der QuickInfo angezeigt werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode zeigt das QuickInfo-Steuerelement an der Position und Größe an, die durch *rect*angegeben wird. Wenn sich Position, Größe und Text seit dem letzten Aufruf dieser Methode nicht geändert haben, hat diese Methode keine Auswirkungen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
