---
title: CMFCToolTipInfo-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
ms.openlocfilehash: 000a2fd33928e59685efa6f145406542a4935819
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377338"
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo-Klasse

Speichert Informationen über die visuelle Darstellung von QuickInfos.

## <a name="syntax"></a>Syntax

```
class CMFCToolTipInfo
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolTipInfo::operator=](#operator_eq)||

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|Eine boolesche Variable, die angibt, ob die QuickInfo über eine Sprechblasendarstellung verfügt.|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|Eine boolesche Variable, die angibt, ob die QuickInfo-Bezeichnungen in fett formatierter Schrift angezeigt werden.|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|Eine boolesche Variable, die angibt, ob die QuickInfo eine Beschreibung enthält.|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|Eine boolesche Variable, die angibt, ob die QuickInfo ein Symbol enthält.|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|Eine boolesche Variable, die angibt, ob eine Trennzeichen zwischen der QuickInfo-Bezeichnung und der QuickInfo-Beschreibung angezeigt wird.|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|Eine boolesche Variable, die angibt, ob die QuickInfo abgerundete Ecken besitzt.|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|Eine boolesche Variable, die angibt, ob das Erscheinungsbild der QuickInfo von einem visuellen Manager gesteuert werden soll (siehe [CMFCVisualManager-Klasse](../../mfc/reference/cmfcvisualmanager-class.md)).|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|Die Farbe des QuickInfo-Rahmens.|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|Die Farbe des QuickInfo-Hintergrunds.|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|Die Farbe der Verlaufsfläche in der QuickInfo.|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|Die Textfarbe in der QuickInfo.|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|Der Winkel der Verlaufsfläche in der QuickInfo.|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|Die maximal mögliche Breite der Beschreibung in der QuickInfo in Pixel.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie [die CMFCToolTipCtrl-Klasse](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`und die [CTooltipManager-Klasse](../../mfc/reference/ctooltipmanager-class.md) zusammen, um benutzerdefinierte QuickInfos in Ihrer Anwendung zu implementieren. Ein Beispiel für die Verwendung dieser QuickInfo-Klassen finden Sie im Thema [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) Class.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Festlegung der Werte für die verschiedenen Membervariablen in der `CMFCToolTipInfo`-Klasse veranschaulicht.

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxtooltipctrl.h

## <a name="cmfctooltipinfom_bballoontooltip"></a><a name="m_bballoontooltip"></a>CMFCToolTipInfo::m_bBalloonTooltip

Gibt den Anzeigestil aller QuickInfos an.

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>Bemerkungen

TRUE gibt an, dass QuickInfos den Sprechblasenstil verwenden, FALSE gibt an, dass QuickInfos den rechteckigen Stil verwenden.

## <a name="cmfctooltipinfom_bboldlabel"></a><a name="m_bboldlabel"></a>CMFCToolTipInfo::m_bBoldLabel

Gibt an, ob die Schriftart des QuickInfo-Texts fett formatiert ist.

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Member auf TRUE fest, um QuickInfo-Text mit fett formatierter Schrift anzuzeigen, oder FALSE, um QuickInfo-Beschriftungen mit nicht fett formatierter Schrift anzuzeigen.

## <a name="cmfctooltipinfom_bdrawdescription"></a><a name="m_bdrawdescription"></a>CMFCToolTipInfo::m_bDrawDescription

Gibt an, ob jede QuickInfo Beschreibungstext anzeigt.

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Member auf TRUE fest, um die Beschreibung anzuzeigen, oder FALSE, um die Beschreibung auszublenden. Sie können die Beschreibung auf einer QuickInfo angeben, indem Sie [CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription) aufrufen.

## <a name="cmfctooltipinfom_bdrawicon"></a><a name="m_bdrawicon"></a>CMFCToolTipInfo::m_bDrawIcon

Gibt an, ob alle QuickInfos Symbole anzeigen.

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Member auf TRUE fest, um ein Symbol auf jeder QuickInfo anzuzeigen, oder FALSE, um QuickInfos ohne Symbole anzuzeigen.

## <a name="cmfctooltipinfom_bdrawseparator"></a><a name="m_bdrawseparator"></a>CMFCToolTipInfo::m_bDrawSeparator

Gibt an, ob jede QuickInfo über ein Trennzeichen zwischen ihrer Beschriftung und ihrer Beschreibung verfügt.

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Member auf TRUE fest, um das Trennzeichen zwischen QuickInfo-Beschriftung und -Beschreibung anzuzeigen, oder FALSE, um QuickInfos ohne Trennzeichen anzuzeigen.

## <a name="cmfctooltipinfom_broundedcorners"></a><a name="m_broundedcorners"></a>CMFCToolTipInfo::m_bRoundedCorners

Gibt an, ob alle QuickInfos abgerundete Ecken haben.

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Member auf TRUE fest, um abgerundete Ecken auf QuickInfos anzuzeigen, oder FALSE, um rechteckige Ecken auf QuickInfos anzuzeigen.

## <a name="cmfctooltipinfom_clrborder"></a><a name="m_clrborder"></a>CMFCToolTipInfo::m_clrBorder

Gibt die Farbe der Rahmen auf allen QuickInfos an.

```
COLORREF m_clrBorder;
```

## <a name="cmfctooltipinfom_clrfill"></a><a name="m_clrfill"></a>CMFCToolTipInfo::m_clrFill

Gibt die Farbe der QuickInfo-Hintergründe an.

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>Bemerkungen

Wenn [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) -1 ist, lautet `m_clrFill`die Hintergrundfarbe der QuickInfo . Andernfalls `m_clrFill` wird die Farbe des Anfangs des `m_clrFillGradient` Farbverlaufs und die Farbe des Endes des Farbverlaufs angegeben. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) bestimmt die Richtung des Farbverlaufs.

## <a name="cmfctooltipinfom_clrfillgradient"></a><a name="m_clrfillgradient"></a>CMFCToolTipInfo::m_clrFillGradient

Gibt die Endfarbe für einen Farbverlaufshintergrund für QuickInfos an.

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>Bemerkungen

Wenn `m_clrFillGradient` -1 ist, gibt es keinen Farbverlauf. Andernfalls wird die Farbverlaufsanfangsfarbe durch [CMFCToolTipInfo::m_clrFill](#m_clrfill) und `m_clrFillGradient`die Farbverlaufsgüte durch angegeben. [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle) bestimmt die Richtung des Farbverlaufs.

## <a name="cmfctooltipinfom_clrtext"></a><a name="m_clrtext"></a>CMFCToolTipInfo::m_clrText

Gibt die Textfarbe aller QuickInfos an.

```
COLORREF m_clrText;
```

## <a name="cmfctooltipinfom_ngradientangle"></a><a name="m_ngradientangle"></a>CMFCToolTipInfo::m_nGradientAngle

Gibt den Winkel an, in dem ein Farbverlauf auf dem Hintergrund von QuickInfos gezeichnet wird.

```
int m_nGradientAngle;
```

### <a name="remarks"></a>Bemerkungen

`m_nGradientAngle`gibt den Winkel in Grad an, in dem der Farbverlauf im Hintergrund der QuickInfos horizontal versetzt wird. Wenn `m_nGradientAngle` es sich um 0 handelt, wird der Farbverlauf von links nach rechts gezeichnet. Wenn `m_nGradientAngle` zwischen 1 und 360 liegt, dreht sich der Farbverlauf im Uhrzeigersinn um diese Anzahl von Graden. Wenn `m_nGradientAngle` -1 ist, was der Standardwert ist, wird der Farbverlauf von oben nach unten gezeichnet. Dies ist das `m_nGradientAngle` gleiche wie die Einstellung auf 90.

[CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill` gibt die Farbe des Anfangs des Farbverlaufs an und [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient` gibt die Farbe des Endes des Farbverlaufs an. Wenn `m_clrFillGradient` -1 ist, gibt es keinen Farbverlauf.

## <a name="cmfctooltipinfom_nmaxdescrwidth"></a><a name="m_nmaxdescrwidth"></a>CMFCToolTipInfo::m_nMaxDescrWidth

Gibt die maximale Breite der Beschreibung an, die in jeder QuickInfo angezeigt wird. Wenn die Beschreibungsbreite den angegebenen Wert überschreitet, wird der Text umbrochen.

```
int m_nMaxDescrWidth;
```

## <a name="cmfctooltipinfom_bvislmanagertheme"></a><a name="m_bvislmanagertheme"></a>CMFCToolTipInfo::m_bVislManagerTheme

Gibt an, ob der visuelle Manager der Anwendung die Darstellung aller QuickInfos steuert.

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>Bemerkungen

Wenn `m_bVislManagerTheme` TRUE ist, fordert jede QuickInfo eine neue [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) vom visuellen Manager der Anwendung an, bevor sie auf dem Bildschirm angezeigt werden, und verwendet die Werte in diesem Objekt, um deren Darstellung zu bestimmen. Die anderen Member Ihres [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) werden ignoriert.

## <a name="cmfctooltipinfooperator"></a><a name="operator_eq"></a>CMFCToolTipInfo::operator=

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>Parameter

[in] *src*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CTooltipManager-Klasse](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipCtrl-Klasse](../../mfc/reference/cmfctooltipctrl-class.md)
