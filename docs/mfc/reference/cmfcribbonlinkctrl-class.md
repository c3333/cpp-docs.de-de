---
title: CMFCRibbonLinkCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
ms.openlocfilehash: 5d00c17b2ede654b9bdd214a8649f1237b9d9fdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375119"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl-Klasse

Implementiert einen Hyperlink, der auf einem Menüband positioniert wird. Wenn Sie den Hyperlink anklicken, wird eine Webseite geöffnet.
Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|Erstellt und initialisiert ein `CMFCRibbonLinkCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Überschreibt `CMFCRibbonButton::CopyFrom`.)|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Überschreibt [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Gibt den Wert des Links zurück.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Überschreibt [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Überschreibt [CMFCRibbonButton::GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Überschreibt `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Überschreibt [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Überschreibt [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Überschreibt `CMFCRibbonButton::OnMouseMove`.)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Öffnet die im Link angegebene Webseite.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Legt den Wert des Links fest.|

## <a name="remarks"></a>Bemerkungen

Nachdem Sie einen Hyperlink erstellt haben, fügen Sie ihn einem Bedienfeld hinzu, indem Sie [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)aufrufen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxRibbonLinkCtrl.h

## <a name="cmfcribbonlinkctrlcmfcribbonlinkctrl"></a><a name="cmfcribbonlinkctrl"></a>CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

Erstellt und initialisiert ein [CMFCRibbonLinkCtrl-Objekt.](../../mfc/reference/cmfcribbonlinkctrl-class.md)

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
[in] Gibt die Befehls-ID des Befehls an, der ausgeführt wird, wenn auf das Verknüpfungssteuerelement geklickt wird.

*lpszText*<br/>
[in] Gibt die Bezeichnung an, die im Verknüpfungssteuerelement angezeigt werden soll.

*lpszLink*<br/>
[in] Gibt den Hyperlink an, der dem Verknüpfungssteuerelement zugeordnet ist.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie `CMFCRibbonLinkCtrl` der Konstruktor der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des Beispiels für [Multifunktionsleisten-Gadgets](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

## <a name="cmfcribbonlinkctrlcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonLinkCtrl::Kopievon

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parameter

[in] *src*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonLinkCtrl::GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlgetlink"></a><a name="getlink"></a>CMFCRibbonLinkCtrl::GetLink

Gibt den Wert des Links zurück.

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>Rückgabewert

Der aktuelle Wert des Hyperlinks.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonLinkCtrl::GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlgettooltiptext"></a><a name="gettooltiptext"></a>CMFCRibbonLinkCtrl::GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonLinkCtrl::OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parameter

[in] *CDC&#42;*<br/>
[in] *CRect*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlondraw"></a><a name="ondraw"></a>CMFCRibbonLinkCtrl::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlonmousemove"></a><a name="onmousemove"></a>CMFCRibbonLinkCtrl::OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>Parameter

[in] *Punkt*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlonseticon"></a><a name="onseticon"></a>CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonlinkctrlopenlink"></a><a name="openlink"></a>CMFCRibbonLinkCtrl::OpenLink

Öffnet die im Link angegebene Webseite.

```
BOOL OpenLink();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die zugehörige Webseite erfolgreich geöffnet wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Öffnet eine Webseite mit dem `CMFCRibbonLinkCtrl` Hyperlink, der dem Objekt zugeordnet ist.

## <a name="cmfcribbonlinkctrlsetlink"></a><a name="setlink"></a>CMFCRibbonLinkCtrl::SetLink

Legt den Wert des Links fest.

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parameter

*lpszLink*<br/>
[in] Gibt den Hyperlinktext an.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton-Klasse](../../mfc/reference/cmfcribbonbutton-class.md)
