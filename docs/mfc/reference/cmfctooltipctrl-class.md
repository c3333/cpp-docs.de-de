---
title: CMFCToolTipCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
ms.openlocfilehash: 6c8bb41b82d1dca9235e1184c2152a61c07c8071
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377353"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl-Klasse

Eine erweiterte QuickInfo-Implementierung auf Grundlage von [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md). Eine QuickInfo auf Grundlage der `CMFCToolTipCtrl` -Klasse kann ein Symbol, eine Bezeichnung und eine Beschreibung anzeigen. Sie können das Aussehen anpassen, indem Sie einen Farbverlauf, einen benutzerdefinierter Text, Rahmenfarben, fetten Text, abgerundete Ecken oder ein Sprechblasenformat verwenden.

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```cpp
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Der Standardkonstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Gibt die Größe eines QuickInfo-Symbols zurück.|
|[CMFCToolTipCtrl::GetParams](#getparams)|Gibt die Anzeigeeinstellungen für QuickInfo zurück.|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Zeichnet den QuickInfo-Rahmen.|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Zeigt ein QuickInfo-Symbol an.|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Gibt die QuickInfo-Bezeichnung an oder berechnet die Bezeichnungsgröße.|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Zeichnet die Trennlinie zwischen der QuickInfo-Bezeichnung und -Beschreibung.|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Füllt den QuickInfo-Hintergrund.|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Legt die von der QuickInfo angezeigte Beschreibung fest.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Gibt die visuelle Darstellung einer QuickInfo mit einem `CMFCToolTipInfo`-Objekt an.|

## <a name="remarks"></a>Bemerkungen

Verwenden `CMFCToolTipCtrl` `CMFCToolTipInfo`Sie , und [CTooltipManager-Klassenobjekte](../../mfc/reference/ctooltipmanager-class.md) zusammen, um benutzerdefinierte QuickInfos in Ihrer Anwendung zu implementieren.

Befolgen Sie die folgenden Schritte, wenn Sie beispielsweise QuickInfo-Sprechblasen verwenden möchten:

1. Verwenden Sie die [CWinAppEx Class-Methode,](../../mfc/reference/cwinappex-class.md) um den QuickInfo-Manager in Ihrer Anwendung zu initialisieren.

2. Erstellen Sie eine `CMFCToolTipInfo`-Struktur, um den gewünschten visuellen Stil anzugeben:

    ```cpp
    CMFCToolTipInfo params;
    params.m_bBoldLabel = FALSE;
    params.m_bDrawDescription = FALSE;
    params.m_bDrawIcon = FALSE;
    params.m_bRoundedCorners = TRUE;
    params.m_bDrawSeparator = FALSE;
    if (m_bCustomColors)
    {
        params.m_clrFill = RGB (255, 255, 255);
        params.m_clrFillGradient = RGB (228, 228, 240);
        params.m_clrText = RGB (61, 83, 80);
        params.m_clrBorder = RGB (144, 149, 168);

    }
    ```

3. Verwenden Sie die [CTooltipManager::SetTooltipParams-Methode,](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) um den visuellen Stil für alle `CMFCToolTipInfo` QuickInfos in der Anwendung mithilfe der im Objekt definierten Stile festzulegen:

    ```cpp
    theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
        RUNTIME_CLASS (CMFCToolTipCtrl), &params);
    ```

Zum Steuern des QuickInfo-Verhaltens und -Renderings können Sie auch eine neue Klasse von `CMFCToolTipCtrl` ableiten. Verwenden Sie zum Angeben einer neuen QuickInfo-Steuerelementklasse die `CTooltipManager::SetTooltipParams`-Methode:

```cpp
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

Legen Sie zum Wiederherstellen der standardmäßigen QuickInfo-Steuerelementklasse und zum Zurücksetzen des QuickInfo-Formats auf die Standardeinstellung die Laufzeitklasse und die QuickInfo-Parameter von `SetTooltipParams` auf NULL fest.

```cpp
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie ein `CMFCToolTipCtrl`-Objekt erstellen, die von der QuickInfo angezeigte Beschreibung und die Breite des Tooltip-Steuerelements festlegen können.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxtooltipctrl.h

## <a name="cmfctooltipctrlcmfctooltipctrl"></a><a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl

```cpp
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Parameter

[in] *pParams*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctooltipctrlgeticonsize"></a><a name="geticonsize"></a>CMFCToolTipCtrl::GetIconSize

Gibt die Größe eines QuickInfo-Symbols zurück.

```cpp
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Rückgabewert

Die Größe des Symbols in Pixel.

## <a name="cmfctooltipctrlgetparams"></a><a name="getparams"></a>CMFCToolTipCtrl::GetParams

Gibt die Anzeigeeinstellungen für QuickInfo zurück.

```cpp
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuellen QuickInfo-Anzeigeeinstellungen , die in einem [CMFCToolTipInfo-Klassenobjekt](../../mfc/reference/cmfctooltipinfo-class.md) gespeichert sind.

## <a name="cmfctooltipctrlondrawborder"></a><a name="ondrawborder"></a>CMFCToolTipCtrl::OnDrawBorder

Zeichnet den QuickInfo-Rahmen.

```cpp
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Das umgrenzende Rechteck der QuickInfo.

*clrLine*<br/>
[in] Rahmenfarbe.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um die Darstellung des QuickInfo-Rahmens anzupassen.

## <a name="cmfctooltipctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCToolTipCtrl::OnDrawBeschreibung

```cpp
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parameter

[in] *pDC*<br/>
[in] *rect*<br/>
[in] *bCalcOnly*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctooltipctrlondrawicon"></a><a name="ondrawicon"></a>CMFCToolTipCtrl::OnDrawIcon

Zeigt ein QuickInfo-Symbol an.

```cpp
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*rectImage*<br/>
[in] Koordinaten des Symbols.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Symbol gezeichnet wurde. Andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um ein benutzerdefiniertes Symbol anzuzeigen. Sie müssen auch [CMFCToolTipCtrl::GetIconSize](#geticonsize) überschreiben, damit die QuickInfo das Layout von Text und Beschreibung korrekt berechnen kann.

## <a name="cmfctooltipctrlondrawlabel"></a><a name="ondrawlabel"></a>CMFCToolTipCtrl::OnDrawLabel

Gibt die QuickInfo-Bezeichnung an oder berechnet die Bezeichnungsgröße.

```cpp
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Begrenzungsrechteck des Beschriftungsbereichs.

*bCalcOnly*<br/>
[in] Wenn TRUE, wird die Beschriftung nicht gezeichnet.

### <a name="return-value"></a>Rückgabewert

Größe der Beschriftung in Pixel.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, wenn Sie die Darstellung der QuickInfo-Beschriftung anpassen möchten.

## <a name="cmfctooltipctrlondrawseparator"></a><a name="ondrawseparator"></a>CMFCToolTipCtrl::OnDrawSeparator

Zeichnet die Trennlinie zwischen der QuickInfo-Bezeichnung und -Beschreibung.

```cpp
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*x1*<br/>
[in] Horizontale Koordinate des linken Endes des Trennzeichens.

*x2*<br/>
[in] Horizontale Koordinate des rechten Endes des Trennzeichens.

*Y*<br/>
[in] Vertikale Koordinate des Trennzeichens.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung zeichnet eine Linie vom Punkt (x1, y) zum Punkt (x2, y).

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um die Darstellung des Trennzeichens anzupassen.

## <a name="cmfctooltipctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCToolTipCtrl::OnFillBackground

Füllt den QuickInfo-Hintergrund.

```cpp
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*Rect*<br/>
[in] Gibt das umschließende Rechteck des zu füllenden Bereichs an.

*clrText*<br/>
[in] Quickinfo-Vordergrundfarbe.

*clrLine*<br/>
[in] Farbe der Rahmen und Trennlinie zwischen Beschriftung und Beschreibung.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung füllt das Rechteck, das durch *Korrektur* angegeben wird, mit der Farbe oder dem Muster, die durch den letzten Aufruf von [CMFCToolTipCtrl::SetParams](#setparams)angegeben wurde.

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, wenn Sie die Darstellung der QuickInfo anpassen möchten.

## <a name="cmfctooltipctrlsetdescription"></a><a name="setdescription"></a>CMFCToolTipCtrl::SetDescription

Legt die von der QuickInfo angezeigte Beschreibung fest.

```cpp
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Parameter

*strDesrciption*<br/>
[in] Beschreibungstext.

### <a name="remarks"></a>Bemerkungen

Der Beschreibungstext wird auf der QuickInfo unter dem Trennzeichen angezeigt.

## <a name="cmfctooltipctrlsetfixedwidth"></a><a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth

```cpp
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Parameter

[in] *nWidthRegular*<br/>
[in] *nWidthLargeImage*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctooltipctrlsethotribbonbutton"></a><a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton

```cpp
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Parameter

[in] *pRibbonButton*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctooltipctrlsetlocation"></a><a name="setlocation"></a>CMFCToolTipCtrl::SetLocation

```cpp
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Parameter

[in] *pt*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfctooltipctrlsetparams"></a><a name="setparams"></a>CMFCToolTipCtrl::SetParams

Gibt die visuelle Darstellung einer QuickInfo mithilfe eines [CMFCToolTipInfo-Klassenobjekts](../../mfc/reference/cmfctooltipinfo-class.md) an.

```cpp
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Parameter

*pParams*<br/>
[in] Zeiger auf ein [CMFCToolTipInfo-Klassenobjekt,](../../mfc/reference/cmfctooltipinfo-class.md) das die Anzeigeparameter enthält.

### <a name="remarks"></a>Bemerkungen

Immer wenn die QuickInfo angezeigt wird, wird sie mithilfe der Farben und visuellen Stile gezeichnet, die *pParams* angibt. Der Wert von *pParams* wird `m_Params`im geschützten Member gespeichert, auf den von einer abgeleiteten Klasse zugegriffen werden kann, die [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl::OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)oder [CMFCToolTipCtrl::OnFillBackground](#onfillbackground) überschreibt, um das angegebene Erscheinungsbild beizubehalten.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl-Klasse](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager-Klasse](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo-Klasse](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)
