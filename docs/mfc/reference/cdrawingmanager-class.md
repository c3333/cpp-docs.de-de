---
title: CDrawingManager-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: 59c34a69b96cc9986db99b5f34bc38cf76f4909a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374019"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager-Klasse

Die `CDrawingManager` Klasse implementiert komplexe Zeichnungsalgorithmen.

## <a name="syntax"></a>Syntax

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Erstellt ein `CDrawingManager`-Objekt.|
|`CDrawingManager::~CDrawingManager`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Erstellt eine geräteunabhängige 32-Bit-Bitmap (DIB), in die Anwendungen direkt schreiben können.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Zeigt Bitmaps mit transparenten oder halbtransparenten Pixeln an.|
|[CDrawingManager::DrawRotated](#drawrotated)|Dreht einen Quell-DC-Inhalt innerhalb des angegebenen Rechtecks um +/- 90 Grad|
|[CDrawingManager::DrawEllipse](#drawellipse)|Zeichnet eine Ellipse mit den mitgelieferten Füll- und Rahmenfarben.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Zeichnet einen Ring und füllt ihn mit einem Farbverlauf.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Zeichnet eine Linie.|
|[CDrawingManager::DrawRect](#drawrect)|Zeichnet ein Rechteck mit den mitgelieferten Füll- und Rahmenfarben.|
|[CDrawingManager::DrawShadow](#drawshadow)|Zeichnet einen Schatten für einen rechteckigen Bereich.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Füllt einen rechteckigen Bereich mit zwei Farbverläufen.|
|[CDrawingManager::FillGradient](#fillgradient)|Füllt einen rechteckigen Bereich mit einem angegebenen Farbverlauf.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Füllt einen rechteckigen Bereich mit einem angegebenen Farbverlauf. Die Richtung der Farbänderung des Farbverlaufs wird ebenfalls angegeben.|
|[CDrawingManager::GrayRect](#grayrect)|Füllt ein Rechteck mit einer angegebenen grauen Farbe.|
|[CDrawingManager::HighlightRect](#highlightrect)|Hebt einen rechteckigen Bereich hervor.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Konvertiert eine Farbe von einer HLS-Darstellung in eine RGB-Darstellung.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Konvertiert eine Farbe von einer HLS-Darstellung in eine RGB-Darstellung.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Konvertiert eine Farbe von einer HSV-Darstellung in eine RGB-Darstellung.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Hilfsmethode, die einen Farbtonwert in eine rote, grüne oder blaue Komponente konvertiert.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Dreht einen rechteckigen Bereich um.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Hilfsmethode, die die endgültige Farbe für ein halbtransparentes Pixel bestimmt.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Erstellt eine Bitmap, die als Schatten verwendet werden kann.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Konvertiert eine Farbe von einer RGB-Darstellung in eine HSL-Darstellung.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Konvertiert eine Farbe von einer RGB-Darstellung in eine HSV-Darstellung.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Hilfsmethode, die ein teilweise transparentes Pixel in einer Bitmap färbt.|
|[CDrawingManager::SetPixel](#setpixel)|Hilfsmethode, die ein einzelnes Pixel in einer Bitmap in die angegebene Farbe ändert.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Kombiniert zwei Farben basierend auf einem gewichteten Verhältnis.|

## <a name="remarks"></a>Bemerkungen

Die `CDrawingManager` Klasse bietet Funktionen zum Zeichnen von Schatten, Farbverläufen und hervorgehobenen Rechtecken. Es führt auch Alpha-Mischung. Sie können diese Klasse verwenden, um die Benutzeroberfläche Ihrer Anwendung direkt zu ändern.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdrawmanager.h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

Erstellt ein [CDrawingManager-Objekt.](../../mfc/reference/cdrawingmanager-class.md)

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parameter

*Dc*<br/>
[in] Ein Verweis auf einen Gerätekontext. Der `CDrawingManager` verwendet diesen Kontext zum Zeichnen.

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32

Erstellt eine geräteunabhängige 32-Bit-Bitmap (DIB), in die Anwendungen direkt schreiben können.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*Größe*|[in] Ein [CSize-Parameter,](../../atl-mfc-shared/reference/csize-class.md) der die Größe der Bitmap angibt.|
|*pBits*|[out] Ein Zeiger auf einen Datenzeiger, der die Position der Bitwerte des DIB empfängt.|
|*Bitmap*|Ein Handle zur ursprünglichen Bitmap|
|*clrTransparent*|Ein RGB-Wert, der die transparente Farbe der ursprünglichen Bitmap angibt.|

### <a name="return-value"></a>Rückgabewert

Ein Handle für die neu erstellte DIB-Bitmap, wenn diese Methode erfolgreich ist. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Erstellen einer DIB-Bitmap finden Sie unter [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a>CDrawingManager::DrawAlpha

Zeigt Bitmaps mit transparenten oder halbtransparenten Pixeln an.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parameter

*pDstDC*<br/>
[in] Ein Zeiger auf den Gerätekontext für das Ziel.

*rectDst*<br/>
[in] Das Zielrechteck.

*pSrcDC*<br/>
[in] Ein Zeiger auf den Gerätekontext für die Quelle.

*rectSrc*<br/>
[in] Das Quellrechteck.

### <a name="remarks"></a>Bemerkungen

Diese Methode führt Alpha-Mischungen für zwei Bitmaps durch. Weitere Informationen zum Alpha-Blending finden Sie unter [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) im Windows SDK.

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a>CDrawingManager::DrawEllipse

Zeichnet eine Ellipse mit den mitgelieferten Füll- und Rahmenfarben.

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Das umgrenzende Rechteck für die Ellipse.

*clrFill*<br/>
[in] Die Farbe, die diese Methode zum Ausfüllen der Ellipse verwendet.

*clrLine*<br/>
[in] Die Farbe, die diese Methode als Rahmen der Ellipse verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird zurückgegeben, ohne eine Ellipse zu zeichnen, wenn eine der Farben auf -1 festgelegt ist. Es wird auch zurückgegeben, ohne eine Ellipse zu zeichnen, wenn eine der beiden Bemaßungen des umgrenzenden Rechtecks 0 ist.

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a>CDrawingManager::DrawGradientRing

Zeichnet einen Ring und füllt ihn mit einem Farbverlauf.

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Ein [CRect-Parameter,](../../atl-mfc-shared/reference/crect-class.md) der die Grenze für den Farbverlaufsring angibt.

*colorStart*<br/>
[in] Die erste Farbe für den Farbverlauf.

*colorFinish*<br/>
[in] Die letzte Farbe für den Farbverlauf.

*colorBorder*<br/>
[in] Die Farbe des Rahmens.

*nAngle*<br/>
[in] Ein Parameter, der den anfänglichen Zeichnungswinkel des Farbverlaufs angibt. Dieser Wert sollte zwischen 0 und 360 liegen.

*nWidth*<br/>
[in] Die Breite des Rahmens für den Ring.

*clrFace*<br/>
[in] Die Farbe des Inneren des Rings.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das durch *Rekt* definierte Rechteck muss mindestens 5 Pixel breit und 5 Pixel hoch sein.

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Zeichnet eine Linie.

```
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*x1*|[in] Die x-Koordinate, an der die Linie beginnt.|
|*y1*|[in] Die y-Koordinate, an der die Linie beginnt.|
|*x2*|[in] Die x-Koordinate, an der die Linie endet.|
|*y2*|[in] Die y-Koordinate, an der die Linie endet.|
|*clrLine*|[in] Die Farbe der Linie.|

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn *clrLine* gleich -1 ist.

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a>CDrawingManager::DrawRect

Zeichnet ein Rechteck mit den mitgelieferten Füll- und Rahmenfarben.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Die Grenzen für das Rechteck.

*clrFill*<br/>
[in] Die Farbe, die diese Methode verwendet, um das Rechteck auszufüllen.

*clrLine*<br/>
[in] Die Farbe, die diese Methode für den Rahmen des Rechtecks verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird zurückgegeben, ohne ein Rechteck zu zeichnen, wenn eine der Farben auf -1 festgelegt ist. Es wird auch zurückgegeben, wenn eine der beiden Dimensionen des Rechtecks 0 ist.

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a>CDrawingManager::DrawShadow

Zeichnet einen Schatten für einen rechteckigen Bereich.

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Ein rechteckiger Bereich in Ihrer Anwendung. Der Zeichnungsmanager zeichnet einen Schatten unter diesen Bereich.

*nTiefe*<br/>
[in] Die Breite und Höhe des Schattens.

*iMinBrightness*<br/>
[in] Die minimale Helligkeit des Schattens.

*iMaxBrightness*<br/>
[in] Die maximale Helligkeit des Schattens.

*pBmpSaveBottom*<br/>
[in] Ein Zeiger auf eine Bitmap, die das Bild für den unteren Teil des Schattens enthält.

*pBmpSaveRight*<br/>
[in] Ein Zeiger auf eine Bitmap, die das Bild für den Schatten enthält, der auf der rechten Seite des Rechtecks gezeichnet wird.

*clrBase*<br/>
[in] Die Farbe des Schattens.

*bRightShadow*<br/>
[in] Ein boolescher Parameter, der angibt, wie der Schatten gezeichnet wird. Wenn *bRightShadow* `DrawShadow` ist, `TRUE`zeichnet ein Schatten auf der rechten Seite des Rechtecks.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie können zwei gültige Bitmaps für den unteren und rechten Schatten bereitstellen, indem Sie die Parameter *pBmpSaveBottom* und *pBmpSaveRight*verwenden. Wenn diese [CBitmap-Objekte](../../mfc/reference/cbitmap-class.md) über ein `DrawShadow` angehängtes GDI-Objekt verfügen, werden diese Bitmaps als Schatten verwendet. Wenn `CBitmap` die Parameter kein angehängtes `DrawShadow` GDI-Objekt haben, zeichnet der Schatten und fügt die Bitmaps an die Parameter an. In zukünftigen `DrawShadow`Aufrufen von können Sie diese Bitmaps bereitstellen, um den Zeichnungsprozess zu beschleunigen. Weitere Informationen zu `CBitmap` den Klassen- und GDI-Objekten finden Sie unter [Grafikobjekte](../../mfc/graphic-objects.md).

Wenn einer dieser `NULL`Parameter `DrawShadow` ist, wird automatisch der Schatten gezeichnet.

Wenn Sie *bRightShadow* auf FALSE setzen, wird der Schatten unter und links vom rechteckigen Bereich gezeichnet.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `DrawShadow` veranschaulicht, `CDrawingManager` wie die Methode der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Prop Sheet Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient

Füllt einen rechteckigen Bereich mit zwei Farbverläufen.

```
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Das zu füllende Rechteck.

*colorStart1*<br/>
[in] Die Anfangsfarbe für den ersten Farbverlauf.

*colorFinish1*<br/>
[in] Die endgültige Farbe für den ersten Farbverlauf.

*colorStart2*<br/>
[in] Die Anfangsfarbe für den zweiten Farbverlauf.

*colorFinish2*<br/>
[in] Die endgültige Farbe für den zweiten Farbverlauf.

*bHorz*<br/>
[in] Ein boolescher Parameter, der angibt, ob `Fill4ColorsGradient` ein horizontaler oder vertikaler Farbverlauf färbt. TRUE gibt einen horizontalen Farbverlauf an.

*nProzentsatz*<br/>
[in] Eine ganze Zahl von 0-100. Dieser Wert gibt den Prozentsatz des Rechtecks an, das mit dem ersten Farbverlauf gefüllt werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn ein Rechteck mit zwei Farbverläufen gefüllt ist, befinden sie sich je nach Wert von *bHorz*entweder übereinander oder nebeneinander. Jeder Farbverlauf wird unabhängig mit der Methode [CDrawingManager::FillGradient](#fillgradient)berechnet.

Diese Methode generiert einen Assertionsfehler, wenn *nPercentage* kleiner als 0 oder mehr als 100 ist.

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a>CDrawingManager::FillGradient

Füllt einen rechteckigen Bereich mit dem angegebenen Farbverlauf.

```
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Der rechteckige Bereich, der gefüllt werden soll.

*colorStart*<br/>
[in] Die erste Farbe für den Farbverlauf.

*colorFinish*<br/>
[in] Die endgültige Farbe für den Farbverlauf.

*bHorz*<br/>
[in] Ein boolescher Parameter, `FillGradient` der angibt, ob ein horizontaler oder vertikaler Farbverlauf gezeichnet werden soll.

*nStartFlatPercentage*<br/>
[in] Der Prozentsatz des `FillGradient` Rechtecks, das mit *colorStart* gefüllt wird, bevor der Farbverlauf gestartet wird.

*nEndFlatPercentage*<br/>
[in] Der Prozentsatz des `FillGradient` Rechtecks, das nach Abschluss des Farbverlaufs mit *colorFinish* gefüllt wird.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `FillGradient` veranschaulicht, `CDrawingManager` wie die Methode der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [MS Office 2007-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a>CDrawingManager::FillGradient2

Füllt einen rechteckigen Bereich mit einem angegebenen Farbverlauf.

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Der rechteckige Bereich, der gefüllt werden soll.

*colorStart*<br/>
[in] Die erste Farbe des Farbverlaufs.

*colorFinish*<br/>
[in] Die letzte Farbe des Farbverlaufs.

*nAngle*<br/>
[in] Eine ganze Zahl zwischen 0 und 360. Dieser Parameter gibt die Richtung des Farbverlaufs an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie *nAngle,* um die Richtung des Farbverlaufs anzugeben. Wenn Sie die Richtung des Farbverlaufs angeben, geben Sie auch an, wo der Farbverlauf beginnt. Der Wert 0 für *nAngle* gibt an, dass der Farbverlauf vom oberen Rand des Rechtecks beginnt. Wenn *nAngle* zunimmt, bewegt sich die Startposition für den Farbverlauf in einer gegen den Uhrzeigersinn gerichteten Richtung, basierend auf dem Winkel.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `FillGradient2` veranschaulicht, `CDrawingManager` wie die Methode der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a>CDrawingManager::GrayRect

Füllt ein Rechteck mit einer angegebenen grauen Farbe.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Der rechteckige Bereich, der gefüllt werden soll.

*nProzentsatz*<br/>
[in] Der gewünschte Grauprozentsatz im Rechteck.

*clrTransparent*<br/>
[in] Die transparente Farbe.

*clrDisabled*<br/>
[in] Die Farbe, die diese Methode für die Desättigung verwendet, wenn *nPercentage* auf -1 festgelegt ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Für den Parameter *nPercentage*gibt ein niedrigerer Wert eine dunklere Farbe an.

Der Maximalwert für *nPercentage* ist 200. Ein Wert größer als 200 ändert nicht die Darstellung des Rechtecks. Wenn der Wert -1 ist, verwendet diese Methode *clrDisabled,* um die Sättigung des Rechtecks einzuschränken.

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a>CDrawingManager::HighlightRect

Hebt einen rechteckigen Bereich hervor.

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Ein rechteckiger Bereich, der hervorgehoben werden soll.

*nProzentsatz*<br/>
[in] Ein Prozentsatz, der angibt, wie transparent die Hervorhebung sein soll.

*clrTransparent*<br/>
[in] Die transparente Farbe.

*nToleranz*<br/>
[in] Eine ganze Zahl zwischen 0 und 255, die die Farbtoleranz angibt.

*clrBlend*<br/>
[in] Die Grundfarbe für die Überblendung.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn *nPercentage* zwischen 0 und `HighlightRect` 99 liegt, wird der Alpha-Mischalgorithmus verwendet. Weitere Informationen zum Alpha-Mischen finden Sie unter [Alpha-Mischlinien und Füllungen](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Wenn *nPercentage* -1 ist, verwendet diese Methode die Standardhervorhebungsstufe. Wenn *nPercentage* 100 ist, führt diese Methode nichts aus und gibt TRUE zurück.

Die Methode verwendet den Parameter *nTolerance,* um zu bestimmen, ob der rechteckige Bereich hervorgehoben werden soll. Um das Rechteck hervorzuheben, muss der Unterschied zwischen der Hintergrundfarbe der Anwendung und *clrTransparent* in jeder Farbkomponente (rot, grün und blau) kleiner als *nToleranz* sein.

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

Konvertiert eine Farbe von einer HLS-Darstellung in eine RGB-Darstellung.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parameter

*H*<br/>
[in] Eine Zahl zwischen 0 und 1, die den Farbton für die Farbe darstellt.

*L*<br/>
[in] Eine Zahl zwischen 0 und 1, die die Leuchtkraft für die Farbe angibt.

*E*<br/>
[in] Eine Zahl zwischen 0 und 1, die die Sättigung für die Farbe angibt.

### <a name="return-value"></a>Rückgabewert

Die RGB-Darstellung der bereitgestellten HLS-Farbe.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Leuchtkraft) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den verschiedenen Farbdarstellungen finden Sie unter [Farbe](/windows/win32/uxguide/vis-color).

Diese Methode `CDrawingManager::HLStoRGB_TWO` und die Methode führen denselben Vorgang aus, erfordern jedoch unterschiedliche Werte für den *H-Parameter.* Bei dieser Methode ist *H* ein Prozentsatz des Kreises. Bei `CDrawingManager::HLStoRGB_TWO` der Methode ist *H* ein Gradwert zwischen 0 und 360, die beide rot darstellen. Bei ist `HLStoRGB_ONE`z. B. ein Wert von 0,25 für `HLStoRGB_TWO` *H* einem Wert von 90 mit entspricht.

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

Konvertiert eine Farbe von einer HLS-Darstellung in eine RGB-Darstellung.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parameter

*H*<br/>
[in] Eine Zahl zwischen 0 und 360, die den Farbton für die Farbe darstellt.

*L*<br/>
[in] Eine Zahl zwischen 0 und 1, die die Leuchtkraft für die Farbe angibt.

*E*<br/>
[in] Eine Zahl zwischen 0 und 1, die die Sättigung für die Farbe angibt.

### <a name="return-value"></a>Rückgabewert

Die RGB-Darstellung der bereitgestellten HLS-Farbe.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Leuchtkraft) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den verschiedenen Farbdarstellungen finden Sie unter [Farbe](/windows/win32/uxguide/vis-color).

Diese Methode und die [CDrawingManager::HLStoRGB_ONE-Methode](#hlstorgb_one) führen denselben Vorgang aus, erfordern jedoch unterschiedliche Werte für den *H-Parameter.* Bei dieser Methode ist *H* ein Gradwert zwischen 0 und 360, die beide rot darstellen. In der [CDrawingManager::HLStoRGB_ONE-Methode](#hlstorgb_one) ist *H* ein Prozentsatz des Kreises. Bei ist `HLStoRGB_ONE`z. B. ein Wert von 0,25 für `HLStoRGB_TWO` *H* einem Wert von 90 mit entspricht.

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

Konvertiert eine Farbe von einer HSV-Darstellung in eine RGB-Darstellung.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*H*|[in] Eine Zahl zwischen 0 und 360, die den Farbton für die Farbe angibt.|
|*E*|[in] Eine Zahl zwischen 0 und 1, die die Sättigung für die Farbe angibt.|
|*V*|[in] Eine Zahl zwischen 0 und 1, die den Wert für die Farbe angibt.|

### <a name="return-value"></a>Rückgabewert

Die RGB-Darstellung der bereitgestellten HSV-Farbe.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Leuchtkraft) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den verschiedenen Farbdarstellungen finden Sie unter [Farbe](/windows/win32/uxguide/vis-color).

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a>CDrawingManager::HuetoRGB

Konvertiert einen Farbtonwert in eine rote, grüne oder blaue Komponente.

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>Parameter

*m1*<br/>
[in] Siehe Bemerkungen.

*m2*<br/>
[in] Siehe Bemerkungen.

*H*<br/>
[in] Siehe Bemerkungen.

*rm1*<br/>
[in] Siehe Bemerkungen.

*rm2*<br/>
[in] Siehe Bemerkungen.

*Rh*<br/>
[in] Siehe Bemerkungen.

### <a name="return-value"></a>Rückgabewert

Die einzelne rote, grüne oder blaue Komponente für den angegebenen Farbton.

### <a name="remarks"></a>Bemerkungen

Diese Methode ist eine Hilfsmethode, die von der `CDrawingManager` Klasse verwendet wird, um die einzelnen roten, grünen und blauen Komponenten einer Farbe in einer HSV- oder HSL-Darstellung zu berechnen. Diese Methode ist nicht so konzipiert, dass sie direkt vom Programmierer aufgerufen wird. Die Eingabeparameter sind Werte, die vom Konvertierungsalgorithmus abhängen.

Um eine HSV- oder HSL-Farbe in eine RGB-Darstellung zu konvertieren, rufen Sie eine der folgenden Methoden auf:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a>CDrawingManager::MirrorRect

Dreht einen rechteckigen Bereich um.

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
[in] Das umgrenzende Rechteck des zu kippenden Bereichs.

*bHorz*<br/>
[in] Ein boolescher Parameter, der angibt, ob das Rechteck horizontal oder vertikal umgedreht wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann jeden Bereich des Gerätekontexts, der der Klasse gehört, `CDrawingManager` umkehren. Wenn *bHorz* auf TRUE gesetzt ist, wird der Bereich mit dieser Methode horizontal umgedreht. Andernfalls wird der Bereich vertikal umgedreht.

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a>CDrawingManager::PixelAlpha

Berechnet die endgültige Farbe für ein halbtransparentes Pixel.

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>Parameter

*srcPixel*<br/>
[in] Die Anfangsfarbe für das Pixel.

*Prozent*<br/>
[in] Eine Zahl zwischen 0 und 100, die den Prozentsatz der Transparenz darstellt. Der Wert 100 gibt an, dass die Anfangsfarbe vollständig transparent ist.

*prozentR*<br/>
[in] Eine Zahl zwischen 0 und 100, die den Prozentsatz der Transparenz für die rote Komponente darstellt.

*prozentG*<br/>
[in] Eine Zahl zwischen 0 und 100, die den Prozentsatz der Transparenz für die grüne Komponente darstellt.

*ProzentB*<br/>
[in] Eine Zahl zwischen 0 und 100, die den Prozentsatz der Transparenz für die blaue Komponente darstellt.

*dstPixel*<br/>
[in] Die Grundfarbe für das Pixel.

### <a name="return-value"></a>Rückgabewert

Die endgültige Farbe für das halbtransparente Pixel.

### <a name="remarks"></a>Bemerkungen

Dies ist eine Hilfsklasse zum Färben von halbtransparenten Bitmaps und wurde nicht direkt vom Programmierer aufgerufen.

Wenn Sie die Version der Methode mit *dstPixel*verwenden, ist die endgültige Farbe eine Kombination aus *dstPixel* und *srcPixel*. Die *srcPixel-Farbe* ist die teilweise transparente Farbe über der Grundfarbe von *dstPixel*.

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask

Erstellt eine Bitmap, die als Schatten verwendet werden kann.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parameter

*nTiefe*<br/>
[in] Die Breite und Höhe des Schattens.

*clrBase*<br/>
[in] Die Farbe des Schattens.

*iMinBrightness*<br/>
[in] Die minimale Helligkeit des Schattens.

*iMaxBrightness*<br/>
[in] Die maximale Helligkeit des Schattens.

### <a name="return-value"></a>Rückgabewert

Ein Handle für die erstellte Bitmap, wenn diese Methode erfolgreich ist. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn *nDepth* auf 0 gesetzt ist, wird diese Methode beendet und gibt NULL zurück. Wenn *nDepth* kleiner als 3 ist, werden die Breite und Höhe des Schattens auf 3 Pixel festgelegt.

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL

Konvertiert eine Farbe aus einer Rot-, Grün- und Blaudarstellung (RGB) in eine Farbton-, Sättigungs- und Lightness-Darstellung (HSL).

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*Rgb*|[in] Die Farbe in RGB-Werten.|
|*H*|[out] Ein Zeiger auf ein Double, bei dem die Methode den Farbton für die Farbe speichert.|
|*E*|[out] Ein Zeiger auf ein Double, bei dem die Methode die Sättigung für die Farbe speichert.|
|*L*|[out] Ein Zeiger auf ein Double, bei dem die Methode die Leichtigkeit für die Farbe speichert.|

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Leuchtkraft) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den verschiedenen Farbdarstellungen finden Sie unter [Farbe](/windows/win32/uxguide/vis-color).

Der zurückgegebene Wert für *H* wird als Bruch zwischen 0 und 1 dargestellt, wobei sowohl 0 als auch 1 rot darstellen. Die zurückgegebenen Werte für *S* und *L* sind Zahlen zwischen 0 und 1.

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

Konvertiert eine Farbe von einer RGB-Darstellung in eine HSV-Darstellung.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parameter

*Rgb*<br/>
[in] Die Farbe, die in einer RGB-Darstellung konvertiert werden soll.

*H*<br/>
[out] Ein Zeiger auf ein Double, bei dem diese Methode den resultierenden Farbton für die Farbe speichert.

*E*<br/>
[out] Ein Zeiger auf ein Double, bei dem diese Methode die resultierende Sättigung für die Farbe speichert.

*V*<br/>
[out] Ein Zeiger auf ein Double, bei dem diese Methode den resultierenden Wert für die Farbe speichert.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Leuchtkraft) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den verschiedenen Farbdarstellungen finden Sie unter [Farbe](/windows/win32/uxguide/vis-color).

Der zurückgegebene Wert für *H* ist eine Zahl zwischen 0 und 360, wobei sowohl 0 als auch 360 rot anzeigen. Die Rückgabewerte für *S* und *V* sind Zahlen zwischen 0 und 1.

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel

Färbt ein transparentes Pixel in einer Bitmap.

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>Parameter

*pBits*<br/>
[in] Ein Zeiger auf die Bitwerte für die Bitmap.

*Rect*<br/>
[in] Ein rechteckiger Bereich in Ihrer Anwendung. Der Zeichnungsmanager zeichnet einen Schatten unter und rechts von diesem Bereich.

*X*<br/>
[in] Die horizontale Koordinate des Pixels, das farbet.

*y*<br/>
[in] Die vertikale Koordinate des Pixels, das farbet.

*Prozent*<br/>
[in] Der Prozentsatz der Transparenz.

*iShadowSize*<br/>
[in] Die Breite und Höhe des Schattens.

*clrBase*<br/>
[in] Die Farbe des Schattens.

*bIsRight*<br/>
[in] Ein boolescher Parameter, der angibt, welches Pixel farbet. Weitere Informationen finden Sie im Abschnitt zu den Hinweisen.

### <a name="remarks"></a>Bemerkungen

Diese Methode ist eine Hilfsmethode, die von der [CDrawingManager::DrawShadow-Methode](#drawshadow) verwendet wird. Wir empfehlen, dass, wenn Sie `CDrawingManager::DrawShadow` einen Schatten zeichnen möchten, rufen Sie stattdessen an.

Wenn *bIsRight* auf TRUE festgelegt ist, wird das Pixel in Farbe *x* Pixel vom rechten Rand der *Korrektur*gemessen. Wenn es FALSE ist, wird das Pixel zu Farbe *x* Pixel vom linken Rand der *Korrektur*gemessen.

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a>CDrawingManager::SetPixel

Ändert ein einzelnes Pixel in einer Bitmap in die angegebene Farbe.

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*pBits*|[in] Ein Zeiger auf die Bitwerte der Bitmap.|
|*Cx*|[in] Die Gesamtbreite der Bitmap.|
|*Cy*|[in] Die Gesamthöhe der Bitmap.|
|*X*|[in] Die x-Koordinate des pixeligen Pixels in der zu ändernden Bitmap.|
|*y*|[in] Die y-Koordinate des zu ändernden Pixels in der Bitmap.|
|*Farbe*|[in] Die neue Farbe für das Pixel, das durch die angegebenen Koordinaten identifiziert wird.|

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a>CDrawingManager::SmartMixColors

Kombiniert zwei Farben basierend auf einem gewichteten Verhältnis.

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|BESCHREIBUNG|
|*Farbe1*|[in] Die erste Farbe, die gemischt werden soll.|
|*farbe2*|[in] Die zweite Farbe, die gemischt werden soll.|
|*dblLumRatio*|[in] Das Verhältnis für die Leuchtkraft der neuen Farbe. `SmartMixColors`multipliziert die Leuchtkraft der gemischten Farbe mit diesem Verhältnis, bevor eine endgültige Farbe bestimmt wird.|
|*k1*|[in] Das gewichtete Verhältnis für die erste Farbe.|
|*k2*|[in] Das gewichtete Verhältnis für die zweite Farbe.|

### <a name="return-value"></a>Rückgabewert

Eine Farbe, die eine gewichtete Mischung der gelieferten Farben darstellt.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt mit einem Fehler fehl, wenn *k1* oder *k2* kleiner als Null ist. Wenn beide Parameter auf 0 festgelegt sind, gibt die Methode zurück. `RGB(0, 0, 0)`

Das gewichtete Verhältnis wird mit der folgenden \* Formel berechnet: \* (farbe1 k1 + farbe2 k2)/(k1 + k2). Nachdem das gewichtete Verhältnis bestimmt wurde, berechnet die Methode die Leuchtkraft für die gemischte Farbe. Anschließend multipliziert es die Leuchtkraft mit *dblLumRatio*. Wenn der Wert größer als 1,0 ist, legt die Methode die Leuchtkraft für die gemischte Farbe auf den neuen Wert fest. Andernfalls wird die Leuchtkraft auf 1,0 gesetzt.

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a>CDrawingManager::DrawRotated

Dreht einen Quell-DC-Inhalt innerhalb des angegebenen Rechtecks um 90 Grad.

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parameter

*rectDest*<br/>
Zielrechteck.

*dcSrc*<br/>
Der Quellgerätekontext.

*bClockWise*<br/>
TRUE zeigt +90 Grad rotieren; FALSE zeigt rotieren -90 Grad an.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
