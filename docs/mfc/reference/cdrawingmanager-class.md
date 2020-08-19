---
title: Cdrawingmanager-Klasse
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
ms.openlocfilehash: 1cc469b63e448e964dacc4d853905b22155dfe0e
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561634"
---
# <a name="cdrawingmanager-class"></a>Cdrawingmanager-Klasse

Die- `CDrawingManager` Klasse implementiert komplexe Zeichnungs Algorithmen.

## <a name="syntax"></a>Syntax

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[Cdrawingmanager:: cdrawingmanager](#cdrawingmanager)|Erstellt ein `CDrawingManager`-Objekt.|
|`CDrawingManager::~CDrawingManager`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Cdrawingmanager:: CreateBitmap_32](#createbitmap_32)|Erstellt eine 32-Bit-geräteunabhängige Bitmap (DIB), mit der Anwendungen direkt in schreiben können.|
|[Cdrawingmanager::D rawalpha](#drawalpha)|Zeigt Bitmaps mit transparenten oder semitransparenten Pixeln an.|
|[Cdrawingmanager::D rawgedreht](#drawrotated)|Rotiert einen Quell-DC-Inhalt innerhalb des angegebenen Rechtecks um +/-90 Grad.|
|[Cdrawingmanager::D rawellipse](#drawellipse)|Zeichnet eine Ellipse mit den angegebenen Füll-und Rahmenfarben.|
|[Cdrawingmanager::D rawgradientring](#drawgradientring)|Zeichnet einen Ring und füllt ihn mit einem Farbverlauf.|
|[Cdrawingmanager::D rawline, cdrawingmanager::D rawlinea](#drawline_cdrawingmanager__drawlinea)|Zeichnet eine Linie.|
|[Cdrawingmanager::D rawrect](#drawrect)|Zeichnet ein Rechteck mit den angegebenen Füll-und Rahmenfarben.|
|[Cdrawingmanager::D rawshadow](#drawshadow)|Zeichnet einen Schatten für einen rechteckigen Bereich.|
|[Cdrawingmanager:: Fill4ColorsGradient](#fill4colorsgradient)|Füllt einen rechteckigen Bereich mit zwei Farbverläufen.|
|[Cdrawingmanager:: fillgradient](#fillgradient)|Füllt einen rechteckigen Bereich mit einem angegebenen Farbverlauf aus.|
|[Cdrawingmanager:: FillGradient2](#fillgradient2)|Füllt einen rechteckigen Bereich mit einem angegebenen Farbverlauf aus. Außerdem wird die Richtung der Farbänderung des Farbverlaufs angegeben.|
|[Cdrawingmanager:: grayrect](#grayrect)|Füllt ein Rechteck mit einer angegebenen grauen Farbe aus.|
|[Cdrawingmanager:: highlightrect](#highlightrect)|Markiert einen rechteckigen Bereich.|
|[Cdrawingmanager:: HLStoRGB_ONE](#hlstorgb_one)|Konvertiert eine Farbe aus einer HLS-Darstellung in eine RGB-Darstellung.|
|[Cdrawingmanager:: HLStoRGB_TWO](#hlstorgb_two)|Konvertiert eine Farbe aus einer HLS-Darstellung in eine RGB-Darstellung.|
|[Cdrawingmanager:: hsvtor GB](#hsvtorgb)|Konvertiert eine Farbe aus einer HSV-Darstellung in eine RGB-Darstellung.|
|[Cdrawingmanager:: huetorgb](#huetorgb)|Hilfsmethode, die einen Hue-Wert in eine rote, grüne oder blaue Komponente konvertiert.|
|[Cdrawingmanager:: mirrorrect](#mirrorrect)|Flippt einen rechteckigen Bereich.|
|[Cdrawingmanager::P ixelalpha](#pixelalpha)|Hilfsmethode, die die endgültige Farbe für ein semitransparentes Pixel bestimmt.|
|[Cdrawingmanager::P "Analyse-hadowmask"](#prepareshadowmask)|Erstellt eine Bitmap, die als Schatten verwendet werden kann.|
|[Cdrawingmanager:: rgbto HSL](#rgbtohsl)|Konvertiert eine Farbe aus einer RGB-Darstellung in eine HSL-Darstellung.|
|[Cdrawingmanager:: rgbto HSV](#rgbtohsv)|Konvertiert eine Farbe aus einer RGB-Darstellung in eine HSV-Darstellung.|
|[Cdrawingmanager:: abkphapixel](#setalphapixel)|Hilfsmethode zum Farben eines teilweise transparenten Pixels in einer Bitmap.|
|[Cdrawingmanager:: SetPixel](#setpixel)|Hilfsmethode, die ein einzelnes Pixel in einer Bitmap in die angegebene Farbe ändert.|
|[Cdrawingmanager:: smartmixcolors](#smartmixcolors)|Kombiniert zwei Farben basierend auf einem gewichteten Verhältnis.|

## <a name="remarks"></a>Bemerkungen

Die- `CDrawingManager` Klasse stellt Funktionen zum Zeichnen von Schatten, Farbverläufen und markierten Rechtecke bereit. Außerdem wird ein Alpha Mischungs Vorgang durchführt. Sie können diese Klasse verwenden, um die Benutzeroberfläche Ihrer Anwendung direkt zu ändern.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdrawmanager. h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a> Cdrawingmanager:: cdrawingmanager

Erstellt ein [cdrawingmanager](../../mfc/reference/cdrawingmanager-class.md) -Objekt.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parameter

*DC*<br/>
in Ein Verweis auf einen Gerätekontext. Der `CDrawingManager` verwendet diesen Kontext zum Zeichnen.

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a> Cdrawingmanager:: CreateBitmap_32

Erstellt eine 32-Bit-geräteunabhängige Bitmap (DIB), mit der Anwendungen direkt in schreiben können.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>Parameter

*Größe*\
in Ein [CSize](../../atl-mfc-shared/reference/csize-class.md) -Parameter, der die Größe der Bitmap angibt.

*PBITS*\
vorgenommen Ein Zeiger auf einen Datenzeiger, der den Speicherort der Bitwerte des DIB empfängt.

*Bitmap*\
Ein Handle für die ursprüngliche Bitmap.

*clrtransparent*\
Ein RGB-Wert, der die transparente Farbe der ursprünglichen Bitmap angibt.

### <a name="return-value"></a>Rückgabewert

Ein Handle für die neu erstellte DIB-Bitmap, wenn diese Methode erfolgreich ist. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum Erstellen einer DIB-Bitmap finden Sie unter " [kreatedibsection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap)".

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a> Cdrawingmanager::D rawalpha

Zeigt Bitmaps mit transparenten oder semitransparenten Pixeln an.

```cpp
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parameter

*pdstdc*<br/>
in Ein Zeiger auf den Gerätekontext für das Ziel.

*rectdst*<br/>
in Das Ziel Rechteck.

*psrcdc*<br/>
in Ein Zeiger auf den Gerätekontext für die Quelle.

*reckategorirc*<br/>
in Das Quell Rechteck.

### <a name="remarks"></a>Bemerkungen

Diese Methode führt Alpha Mischungs Vorgänge für zwei Bitmaps aus. Weitere Informationen zur Alpha Mischung finden Sie unter [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) in der Windows SDK.

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a> Cdrawingmanager::D rawellipse

Zeichnet eine Ellipse mit den angegebenen Füll-und Rahmenfarben.

```cpp
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
in Das umgebende Rechteck für die Ellipse.

*clrfill*<br/>
in Die Farbe, die diese Methode zum Auffüllen der Ellipse verwendet.

*clrline*<br/>
in Die Farbe, die diese Methode als Rahmen der Ellipse verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt zurück, ohne eine Ellipse zu zeichnen, wenn eine der beiden Farben auf-1 festgelegt ist. Es wird auch zurückgegeben, ohne eine Ellipse zu zeichnen, wenn eine der Dimensionen des umgebenden Rechtecks 0 ist.

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a> Cdrawingmanager::D rawgradientring

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
in Ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Parameter, der die Grenze für den Farbverlaufs Ring angibt.

*colorstart*<br/>
in Die erste Farbe für den Farbverlauf.

*colorfinish*<br/>
in Die letzte Farbe für den Farbverlauf.

*colorborder*<br/>
in Die Farbe des Rahmens.

*Nangle*<br/>
in Ein-Parameter, der den anfänglichen Farbverlaufs Zeichnungs Winkel angibt. Dieser Wert muss zwischen 0 und 360 liegen.

*nwidth*<br/>
in Die Breite des Rahmens für den Ring.

*clrface*<br/>
in Die Farbe des Inneren des Rings.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Das durch *Rect* definierte Rechteck muss mindestens 5 Pixel breit und 5 Pixel hoch sein.

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a> Cdrawingmanager::D rawline, cdrawingmanager::D rawlinea

Zeichnet eine Linie.

```cpp
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

*x1*\
in Die x-Koordinate, an der die Zeile beginnt.

*Y1*\
in Die y-Koordinate, an der die Zeile beginnt.

*x2*\
in Die x-Koordinate, an der die Linie endet.

*Y2*\
in Die y-Koordinate, an der die Linie endet.

*clrline*\
in Die Farbe der Linie.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn *clrline* -1 entspricht.

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a> Cdrawingmanager::D rawrect

Zeichnet ein Rechteck mit den angegebenen Füll-und Rahmenfarben.

```cpp
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
in Die Begrenzungen für das Rechteck.

*clrfill*<br/>
in Die Farbe, die diese Methode zum Ausfüllen des Rechtecks verwendet.

*clrline*<br/>
in Die Farbe, die diese Methode für den Rahmen des Rechtecks verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt zurück, ohne ein Rechteck zu zeichnen, wenn eine der beiden Farben auf-1 festgelegt ist. Es wird auch zurückgegeben, wenn eine der beiden Dimensionen des Rechtecks 0 ist.

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a> Cdrawingmanager::D rawshadow

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
in Ein rechteckiger Bereich in der Anwendung. Der Zeichnungs-Manager zeichnet einen Schatten unterhalb dieses Bereichs.

*ntiefe*<br/>
in Die Breite und Höhe des Schattens.

*iminhelligkeit*<br/>
in Die minimale Helligkeit des Schattens.

*imaxhelligkeit*<br/>
in Die maximale Helligkeit des Schattens.

*pbmpsavebottom*<br/>
in Ein Zeiger auf eine Bitmap, die das Bild für den unteren Teil des Schattens enthält.

*pbmpsaveright*<br/>
in Ein Zeiger auf eine Bitmap, die das Bild für den Schatten enthält, der auf der rechten Seite des Rechtecks gezeichnet wird.

*clrbase*<br/>
in Die Farbe des Schattens.

*brightshadow*<br/>
in Ein boolescher Parameter, der angibt, wie der Schatten gezeichnet wird. Wenn *brightshadow* ist `TRUE` , `DrawShadow` zeichnet einen Schatten auf der rechten Seite des Rechtecks.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie können zwei gültige Bitmaps für den unteren und den rechten Schatten mit den Parametern *pbmpsavebottom* und *pbmpsaveright*bereitstellen. Wenn diese [CBitmap](../../mfc/reference/cbitmap-class.md) -Objekte über ein angefügtes GDI-Objekt verfügen, `DrawShadow` werden diese Bitmaps von als Schatten verwendet. Wenn die `CBitmap` Parameter kein angefügtes GDI-Objekt aufweisen, `DrawShadow` zeichnet den Schatten und fügt die Bitmaps den Parametern an. In zukünftigen Aufrufen von `DrawShadow` können Sie diese Bitmaps bereitstellen, um den Zeichnungsprozess zu beschleunigen. Weitere Informationen zu den `CBitmap` Klassen-und GDI-Objekten finden Sie unter [Graphic Objects](../../mfc/graphic-objects.md).

Wenn einer dieser Parameter ist `NULL` , `DrawShadow` wird der Schatten von automatisch gezeichnet.

Wenn Sie *brightshadow* auf false festlegen, wird der Schatten unterhalb und links neben dem rechteckigen Bereich gezeichnet.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die- `DrawShadow` Methode der-Klasse verwendet wird `CDrawingManager` . Dieser Code Ausschnitt ist Teil des Beispiel für ein " [Prop Sheet Demo](../../overview/visual-cpp-samples.md)".

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a> Cdrawingmanager:: Fill4ColorsGradient

Füllt einen rechteckigen Bereich mit zwei Farbverläufen.

```cpp
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
in Das zu füllende Rechteck.

*colorStart1*<br/>
in Die Anfangs Farbe für den ersten Farbverlauf.

*colorFinish1*<br/>
in Die endgültige Farbe für den ersten Farbverlauf.

*colorStart2*<br/>
in Die Anfangs Farbe für den zweiten Farbverlauf.

*colorFinish2*<br/>
in Die endgültige Farbe für den zweiten Farbverlauf.

*bhorz*<br/>
in Ein boolescher Parameter, der angibt, ob `Fill4ColorsGradient` Farben ein horizontaler oder vertikaler Farbverlauf ist. TRUE gibt einen horizontalen Farbverlauf an.

*nprozentsatz*<br/>
in Eine ganze Zahl zwischen 0-100. Dieser Wert gibt den Prozentsatz des Rechtecks an, das mit dem ersten Farbverlauf aufgefüllt werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn ein Rechteck mit zwei Farbverläufen gefüllt ist, befinden Sie sich entweder oberhalb oder nebeneinander, abhängig vom Wert von *bhorz*. Jeder Farbverlauf wird unabhängig von der Methode [cdrawingmanager:: fillgradient](#fillgradient)berechnet.

Diese Methode generiert einen Fehler bei der Übersetzung, wenn *nprozentsatz* kleiner als 0 oder größer als 100 ist.

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a> Cdrawingmanager:: fillgradient

Füllt einen rechteckigen Bereich mit dem angegebenen Farbverlauf aus.

```cpp
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
in Der zu füllende rechteckige Bereich.

*colorstart*<br/>
in Die erste Farbe für den Farbverlauf.

*colorfinish*<br/>
in Die endgültige Farbe für den Farbverlauf.

*bhorz*<br/>
in Ein boolescher Parameter, der angibt, ob `FillGradient` ein horizontaler oder vertikaler Farbverlauf zeichnen soll.

*nstartflatprozentsatz*<br/>
in Der Prozentsatz des Rechtecks, das `FillGradient` mit *colorstart* gefüllt wird, bevor der Farbverlauf gestartet wird.

*nendflatprozentsatz*<br/>
in Der Prozentsatz des Rechtecks, das `FillGradient` mit *colorfinish* aufgefüllt wird, nachdem der Farbverlauf abgeschlossen wurde.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die- `FillGradient` Methode der-Klasse verwendet wird `CDrawingManager` . Dieser Code Ausschnitt ist Teil des Beispiel- [Demo Beispiels von MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a> Cdrawingmanager:: FillGradient2

Füllt einen rechteckigen Bereich mit einem angegebenen Farbverlauf aus.

```cpp
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
in Der zu füllende rechteckige Bereich.

*colorstart*<br/>
in Die erste Farbe des Farbverlaufs.

*colorfinish*<br/>
in Die letzte Farbe des Farbverlaufs.

*Nangle*<br/>
in Eine ganze Zahl zwischen 0 und 360. Dieser Parameter gibt die Richtung des Farbverlaufs an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie *Nangle* , um die Richtung des Farbverlaufs anzugeben. Wenn Sie die Richtung des Farbverlaufs angeben, geben Sie auch an, wo der Farbverlauf beginnt. Der Wert 0 für *Nangle* gibt an, dass der Farbverlauf am oberen Rand des Rechtecks beginnt. Wenn sich das *Nangle* vergrößert, wird die Anfangsposition für den Farbverlauf auf der Grundlage des Winkels gegen den Uhrzeigersinn verschoben.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die- `FillGradient2` Methode der-Klasse verwendet wird `CDrawingManager` . Dieser Code Ausschnitt ist Teil des Beispiels " [neue Steuerelemente](../../overview/visual-cpp-samples.md)".

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a> Cdrawingmanager:: grayrect

Füllt ein Rechteck mit einer angegebenen grauen Farbe aus.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
in Der zu füllende rechteckige Bereich.

*nprozentsatz*<br/>
in Der Prozentsatz des grauen Werts im Rechteck.

*clrtransparent*<br/>
in Die transparente Farbe.

*clrdeaktiviert*<br/>
in Die Farbe, die diese Methode für die Aufhebung der Sättigung verwendet, wenn *nprozentsatz* auf-1 festgelegt ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Bei dem *nprozentsatz*des Parameters gibt ein niedrigerer Wert eine dunklere Farbe an.

Der maximale Wert für *nprozentsatz* beträgt 200. Ein Wert, der größer als 200 ist, ändert nicht die Darstellung des Rechtecks. Wenn der Wert-1 ist, verwendet diese Methode *clrdeaktiviert* , um die Sättigung des Rechtecks einzuschränken.

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a> Cdrawingmanager:: highlightrect

Markiert einen rechteckigen Bereich.

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
in Ein rechteckiger Bereich zum hervorheben.

*nprozentsatz*<br/>
in Ein Prozentsatz, der angibt, wie transparent die Hervorhebung sein sollte.

*clrtransparent*<br/>
in Die transparente Farbe.

*ntoleranz*<br/>
in Eine ganze Zahl zwischen 0 und 255, die die Farbtoleranz angibt.

*clrblend*<br/>
in Die Basis Farbe für das Mischen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn der *nprozentsatz* zwischen 0 und 99 liegt, wird von `HighlightRect` der Alpha Mischungs Algorithmus verwendet. Weitere Informationen zur Alpha Mischung finden Sie unter [Alpha Blending von Linien und Füllungen](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Wenn *nprozentsatz* -1 ist, verwendet diese Methode die Standard Hervorhebungs Ebene. Wenn *nprozentsatz* 100 ist, führt diese Methode keine Aktion aus und gibt true zurück.

Die-Methode verwendet den Parameter *ntolerance* , um zu bestimmen, ob der rechteckige Bereich hervorgehoben werden soll. Um das Rechteck hervorzuheben, muss der Unterschied zwischen der Hintergrundfarbe der Anwendung und *clrtransparent* in jeder Farbkomponente (rot, grün und blau) kleiner als *ntolerance* sein.

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a> Cdrawingmanager:: HLStoRGB_ONE

Konvertiert eine Farbe aus einer HLS-Darstellung in eine RGB-Darstellung.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parameter

*H*<br/>
in Eine Zahl zwischen 0 und 1, die den Farbton für die Farbe darstellt.

*Int*<br/>
in Eine Zahl zwischen 0 und 1, die die Helligkeit für die Farbe angibt.

*S*<br/>
in Eine Zahl zwischen 0 und 1, die die Sättigung der Farbe angibt.

### <a name="return-value"></a>Rückgabewert

Die RGB-Darstellung der angegebenen HLS-Farbe.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Helligkeit) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den unterschiedlichen Darstellungen von Farben finden Sie unter [Color](/windows/win32/uxguide/vis-color).

Diese Methode und die- `CDrawingManager::HLStoRGB_TWO` Methode führen denselben Vorgang aus, erfordern jedoch unterschiedliche Werte für den *H* -Parameter. Bei dieser Methode ist *H* ein Prozentsatz des Kreises. In der- `CDrawingManager::HLStoRGB_TWO` Methode ist *H* ein gradewert zwischen 0 und 360, der beide rot darstellt. Beispielsweise `HLStoRGB_ONE` entspricht der Wert 0,25 für *H* dem Wert 90 mit dem Wert `HLStoRGB_TWO` .

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a> Cdrawingmanager:: HLStoRGB_TWO

Konvertiert eine Farbe aus einer HLS-Darstellung in eine RGB-Darstellung.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parameter

*H*<br/>
in Eine Zahl zwischen 0 und 360, die den Farbton für die Farbe darstellt.

*Int*<br/>
in Eine Zahl zwischen 0 und 1, die die Helligkeit für die Farbe angibt.

*S*<br/>
in Eine Zahl zwischen 0 und 1, die die Sättigung der Farbe angibt.

### <a name="return-value"></a>Rückgabewert

Die RGB-Darstellung der angegebenen HLS-Farbe.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Helligkeit) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den unterschiedlichen Darstellungen von Farben finden Sie unter [Color](/windows/win32/uxguide/vis-color).

Diese Methode und die [cdrawingmanager:: HLStoRGB_ONE](#hlstorgb_one) -Methode führen denselben Vorgang aus, erfordern jedoch unterschiedliche Werte für den *H* -Parameter. Bei dieser Methode ist *H* ein Grad-Wert zwischen 0 und 360, der beide rot darstellt. In der [cdrawingmanager:: HLStoRGB_ONE](#hlstorgb_one) -Methode ist *H* ein Prozentsatz des Kreises. Beispielsweise `HLStoRGB_ONE` entspricht der Wert 0,25 für *H* dem Wert 90 mit dem Wert `HLStoRGB_TWO` .

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a> Cdrawingmanager:: hsvtor GB

Konvertiert eine Farbe aus einer HSV-Darstellung in eine RGB-Darstellung.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>Parameter

*Micha*\
in Eine Zahl zwischen 0 und 360, die den Farbton für die Farbe angibt.

*Hymnen*\
in Eine Zahl zwischen 0 und 1, die die Sättigung der Farbe angibt.

*Ramelow*\
in Eine Zahl zwischen 0 und 1, die den Wert für die Farbe angibt.

### <a name="return-value"></a>Rückgabewert

Die RGB-Darstellung der bereitgestellten HSV-Farbe.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Helligkeit) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den unterschiedlichen Darstellungen von Farben finden Sie unter [Color](/windows/win32/uxguide/vis-color).

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a> Cdrawingmanager:: huetorgb

Konvertiert einen Hue-Wert in eine rote, grüne oder blaue Komponente.

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

*M1*<br/>
in Siehe Hinweise.

*groß*<br/>
in Siehe Hinweise.

*h*<br/>
in Siehe Hinweise.

*rm1*<br/>
in Siehe Hinweise.

*rm2*<br/>
in Siehe Hinweise.

*RH*<br/>
in Siehe Hinweise.

### <a name="return-value"></a>Rückgabewert

Die einzelnen roten, grünen oder blauen Komponenten für den bereitgestellten Farbton.

### <a name="remarks"></a>Bemerkungen

Diese Methode ist eine Hilfsmethode, die `CDrawingManager` von der-Klasse verwendet wird, um die einzelnen roten, grünen und blauen Komponenten einer Farbe in einer HSV-oder HSL-Darstellung zu berechnen. Diese Methode ist nicht für den direkten Aufruf durch den Programmierer konzipiert. Die Eingabeparameter sind Werte, die vom Konvertierungs Algorithmus abhängen.

Um eine HSV-oder HSL-Farbe in eine RGB-Darstellung zu konvertieren, wenden Sie eine der folgenden Methoden an:

- [Cdrawingmanager:: hsvtor GB](#hsvtorgb)

- [Cdrawingmanager:: HLStoRGB_ONE](#hlstorgb_one)

- [Cdrawingmanager:: HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a> Cdrawingmanager:: mirrorrect

Flippt einen rechteckigen Bereich.

```cpp
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
in Das umschließende Rechteck des umzuschenden Bereichs.

*bhorz*<br/>
in Ein boolescher Parameter, der angibt, ob das Rechteck horizontal oder vertikal gedreht wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann jeden Bereich des Geräte Kontexts kippen, der im Besitz der- `CDrawingManager` Klasse ist. Wenn *bhorz* auf true festgelegt ist, kippt diese Methode den Bereich horizontal. Andernfalls wird der Bereich vertikal gekippt.

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a> Cdrawingmanager::P ixelalpha

Berechnet die endgültige Farbe eines semitransparenten Pixels.

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

*srcpixel*<br/>
in Die Anfangs Farbe für das Pixel.

*prozenti*<br/>
in Eine Zahl zwischen 0 und 100, die den Prozentsatz der Transparenz darstellt. Der Wert 100 gibt an, dass die Anfangs Farbe vollständig transparent ist.

*prozentur*<br/>
in Eine Zahl zwischen 0 und 100, die den Prozentsatz der Transparenz für die rote Komponente darstellt.

*prozentug*<br/>
in Eine Zahl zwischen 0 und 100, die den Prozentsatz der Transparenz für die grüne Komponente darstellt.

*prozentuv*<br/>
in Eine Zahl zwischen 0 und 100, die den Prozentsatz der Transparenz für die blaue Komponente darstellt.

*dstpixel*<br/>
in Die Basis Farbe des Pixels.

### <a name="return-value"></a>Rückgabewert

Die endgültige Farbe für das semitransparente Pixel.

### <a name="remarks"></a>Bemerkungen

Dabei handelt es sich um eine Hilfsklasse für die Farbgebung von semitransparenten Bitmaps, die nicht direkt vom Programmierer aufgerufen werden soll.

Wenn Sie die Version der Methode verwenden, die über *dstpixel*verfügt, ist die endgültige Farbe eine Kombination aus *dstpixel* und *srcpixel*. Die *srcpixel* -Farbe ist die teilweise transparente Farbe für die Basis Farbe von *dstpixel*.

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a> Cdrawingmanager::P "Analyse-hadowmask"

Erstellt eine Bitmap, die als Schatten verwendet werden kann.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parameter

*ntiefe*<br/>
in Die Breite und Höhe des Schattens.

*clrbase*<br/>
in Die Farbe des Schattens.

*iminhelligkeit*<br/>
in Die minimale Helligkeit des Schattens.

*imaxhelligkeit*<br/>
in Die maximale Helligkeit des Schattens.

### <a name="return-value"></a>Rückgabewert

Ein Handle für die erstellte Bitmap, wenn diese Methode erfolgreich ist. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn *ntiefe* auf 0 festgelegt ist, wird diese Methode beendet und gibt NULL zurück. Wenn *ntiefe* kleiner als 3 ist, werden Breite und Höhe des Schattens auf 3 Pixel festgelegt.

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a> Cdrawingmanager:: rgbto HSL

Konvertiert eine Farbe aus einer roten, grünen und blauen Darstellung (RGB) in eine Darstellung von Hue, Sättigung und Helligkeit (HSL).

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>Parameter

*Set*\
in Die Farbe in RGB-Werten.

*Micha*\
vorgenommen Ein Zeiger auf einen Double-Wert, an dem die-Methode den Farbton für die Farbe speichert.

*Hymnen*\
vorgenommen Ein Zeiger auf einen Double-Wert, bei dem die-Methode die Sättigung der Farbe speichert.

*Int*\
vorgenommen Ein Zeiger auf einen Double-Wert, bei dem die-Methode die Helligkeit für die Farbe speichert.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Helligkeit) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den unterschiedlichen Darstellungen von Farben finden Sie unter [Color](/windows/win32/uxguide/vis-color).

Der zurückgegebene Wert für *H* wird als Bruchteil zwischen 0 und 1 dargestellt, wobei 0 und 1 rot darstellen. Die zurückgegebenen Werte für *S* und *L* sind Zahlen zwischen 0 und 1.

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a> Cdrawingmanager:: rgbto HSV

Konvertiert eine Farbe aus einer RGB-Darstellung in eine HSV-Darstellung.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parameter

*Set*<br/>
in Die Farbe, die in eine RGB-Darstellung konvertiert werden soll.

*H*<br/>
vorgenommen Ein Zeiger auf einen Double-Wert, in dem diese Methode den resultierenden Farbton für die Farbe speichert.

*S*<br/>
vorgenommen Ein Zeiger auf einen Double-Wert, in dem diese Methode die resultierende Sättigung für die Farbe speichert.

*Ramelow*<br/>
vorgenommen Ein Zeiger auf einen Double-Wert, in dem diese Methode den resultierenden Wert für die Farbe speichert.

### <a name="remarks"></a>Bemerkungen

Eine Farbe kann als HSV (Farbton, Sättigung und Wert), HSL (Farbton, Sättigung und Helligkeit) oder RGB (rot, grün und blau) dargestellt werden. Weitere Informationen zu den unterschiedlichen Darstellungen von Farben finden Sie unter [Color](/windows/win32/uxguide/vis-color).

Der zurückgegebene Wert für *H* ist eine Zahl zwischen 0 und 360, wobei 0 und 360 rot angeben. Die Rückgabewerte für *S* und *V* sind Zahlen zwischen 0 und 1.

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a> Cdrawingmanager:: abkphapixel

Farben eines transparenten Pixels in einer Bitmap.

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

*PBITS*<br/>
in Ein Zeiger auf die Bitwerte für die Bitmap.

*Rect*<br/>
in Ein rechteckiger Bereich in der Anwendung. Der Zeichnungs-Manager zeichnet einen Schatten unterhalb und rechts neben diesem Bereich.

*x*<br/>
in Die horizontale Koordinate des zu farbenden Pixels.

*y*<br/>
in Die vertikale Koordinate des zu farbenden Pixels.

*prozenti*<br/>
in Der Prozentsatz der Transparenz.

*ishadowsize*<br/>
in Die Breite und Höhe des Schattens.

*clrbase*<br/>
in Die Farbe des Schattens.

*bisright*<br/>
in Ein boolescher Parameter, der angibt, welches Pixel farblich angezeigt werden soll. Weitere Informationen finden Sie im Abschnitt Hinweise.

### <a name="remarks"></a>Bemerkungen

Diese Methode ist eine Hilfsmethode, die von der [cdrawingmanager::D rawshadow](#drawshadow) -Methode verwendet wird. Wenn Sie einen Schatten zeichnen möchten, wird empfohlen, stattdessen aufzurufen `CDrawingManager::DrawShadow` .

Wenn *bisright* auf true festgelegt ist, wird das Pixel in Farbe *x* Pixel vom rechten Rand von *Rect*gemessen. Wenn der Wert false ist, wird das Pixel bis zur Farbe *x* Pixel vom linken Rand von *Rect*gemessen.

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a> Cdrawingmanager:: SetPixel

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

*PBITS*\
in Ein Zeiger auf die Bitwerte der Bitmap.

*verschoben*\
in Die Gesamtbreite der Bitmap.

*CY*\
in Die Gesamthöhe der Bitmap.

*Stuben*\
in Die x-Koordinate des Pixels in der Bitmap, die geändert werden soll.

*Teenie*\
in Die y-Koordinate des Pixels in der Bitmap, die geändert werden soll.

*Farbe*\
in Die neue Farbe für das Pixel, das durch die angegebenen Koordinaten identifiziert wird.

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a> Cdrawingmanager:: smartmixcolors

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

*color1*\
in Die erste zu Mischungs Farbe.

*color2*\
in Die zweite zu Mischungs Farbe.

*dbllumschlag-Verhältnis*\
in Das Verhältnis für die Leuchtkraft der neuen Farbe. `SmartMixColors` multipliziert die Leuchtkraft der gemischten Farbe mit diesem Verhältnis, bevor eine endgültige Farbe festgelegt wird.

*K1*\
in Das gewichtete Verhältnis für die erste Farbe.

*K2*\
in Das gewichtete Verhältnis für die zweite Farbe.

### <a name="return-value"></a>Rückgabewert

Eine Farbe, die eine gewichtete Mischung der angegebenen Farben darstellt.

### <a name="remarks"></a>Bemerkungen

Bei dieser Methode tritt ein Fehler auf, wenn *K1* oder *K2* kleiner als 0 (null) ist. Wenn beide Parameter auf 0 festgelegt sind, gibt die Methode zurück `RGB(0, 0, 0)` .

Das gewichtete Verhältnis wird mit der folgenden Formel berechnet: (color1 \* K1 + color2 \* K2)/(K1 + K2). Nachdem das gewichtete Verhältnis festgelegt wurde, berechnet die Methode die Helligkeit für die gemischte Farbe. Anschließend wird die Helligkeit von *dbllumschlag Ratio*multipliziert. Wenn der Wert größer als 1,0 ist, legt die-Methode die Leuchtkraft für die gemischte Farbe auf den neuen Wert fest. Andernfalls wird die Helligkeit auf 1,0 festgelegt.

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a> Cdrawingmanager::D rawgedreht

Rotiert einen Quell-DC-Inhalt innerhalb des angegebenen Rechtecks um 90 Grad.

```cpp
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parameter

*neusten*<br/>
Ziel Rechteck.

*dcsrc*<br/>
Der Quell Gerätekontext.

*buhrzeiger Sinn*<br/>
TRUE gibt Drehung + 90 Grad an; FALSE gibt die Drehung um 90 Grad an.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
