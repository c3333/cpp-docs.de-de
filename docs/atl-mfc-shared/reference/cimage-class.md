---
title: CImage-Klasse
ms.date: 08/19/2019
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
ms.openlocfilehash: 6e7197648fd91b2280d406c19c1019ca23f6a470
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684299"
---
# <a name="cimage-class"></a>CImage-Klasse

`CImage` bietet erweiterte Unterstützung für Bitmap, einschließlich der Möglichkeit, Bilder in JPEG-, GIF-, BMP-und Portable Network Graphics-Formaten (PNG) zu laden und zu speichern.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
class CImage
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CImage:: CImage](#cimage)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CImage:: AlphaBlend](#alphablend)|Zeigt Bitmaps mit transparenten oder semitransparenten Pixeln an.|
|[CImage:: Attach](#attach)|Fügt ein HBITMAP an ein- `CImage` Objekt an. Kann entweder mit nicht-DIB-Abschnitts Bitmaps oder DIB-Abschnitts Bitmaps verwendet werden.|
|[CImage:: BitBLT](#bitblt)|Kopiert eine Bitmap aus dem Quell Gerätekontext in diesen aktuellen Gerätekontext.|
|[CImage:: Create](#create)|Erstellt eine DIB-Abschnitts Bitmap und fügt Sie an das zuvor erstellte- `CImage` Objekt an.|
|[CImage:: kreateex](#createex)|Erstellt eine DIB-Abschnitts Bitmap (mit zusätzlichen Parametern) und fügt Sie an das zuvor erstellte `CImage` Objekt an.|
|[CImage::D estroy](#destroy)|Trennt die Bitmap vom `CImage` -Objekt und zerstört die Bitmap.|
|[CImage::D Etach](#detach)|Trennt die Bitmap von einem- `CImage` Objekt.|
|[CImage::D RAW](#draw)|Kopiert eine Bitmap aus einem Quell Rechteck in ein Ziel Rechteck. `Draw` stremiert oder komprimiert die Bitmap, sodass Sie ggf. den Abmessungen des Ziel Rechtecks entspricht, und behandelt Alpha Mischungen und transparente Farben.|
|[CImage:: GetBits](#getbits)|Ruft einen Zeiger auf die eigentlichen Pixelwerte der Bitmap ab.|
|[CImage:: getbpp](#getbpp)|Ruft die Bits pro Pixel ab.|
|[CImage:: getcolortable](#getcolortable)|Ruft rote, grüne, blaue (RGB) Farbwerte aus einem Bereich von Einträgen in der Farbtabelle ab.|
|[CImage:: GetDC](#getdc)|Ruft den Gerätekontext ab, in dem die aktuelle Bitmap ausgewählt wird.|
|[CImage:: getexporterfilterstring](#getexporterfilterstring)|Sucht die verfügbaren Bildformate und deren Beschreibungen.|
|[CImage:: GetHeight](#getheight)|Ruft die Höhe des aktuellen Bilds in Pixel ab.|
|[CImage:: getimporterfilterstring](#getimporterfilterstring)|Sucht die verfügbaren Bildformate und deren Beschreibungen.|
|[CImage:: getmaxcolortableentries](#getmaxcolortableentries)|Ruft die maximale Anzahl von Einträgen in der Farbtabelle ab.|
|[CImage:: getPitch](#getpitch)|Ruft die Tonhöhe des aktuellen Bilds in Bytes ab.|
|[CImage:: GetPixel](#getpixel)|Ruft die Farbe des Pixels ab, das von *x* und *y*angegeben wird.|
|[CImage:: getpixeladdress](#getpixeladdress)|Ruft die Adresse eines gegebenen Pixels ab.|
|[CImage:: gettransparentcolor](#gettransparentcolor)|Ruft die Position der transparenten Farbe in der Farbtabelle ab.|
|[CImage:: getWidth](#getwidth)|Ruft die Breite des aktuellen Bilds in Pixel ab.|
|[CImage:: isdibsection](#isdibsection)|Bestimmt, ob die angefügte Bitmap ein DIB-Abschnitt ist.|
|[CImage:: isindebug](#isindexed)|Gibt an, dass die Farben einer Bitmap einer indizierten Palette zugeordnet werden.|
|[CImage:: IsNull](#isnull)|Gibt an, ob eine Quell Bitmap momentan geladen ist.|
|[CImage:: istransparkocysupported](#istransparencysupported)|Gibt an, ob die Anwendung transparente Bitmaps unterstützt.|
|[CImage:: Load](#load)|Lädt ein Bild aus der angegebenen Datei.|
|[CImage:: loadfromresource](#loadfromresource)|Lädt ein Bild aus der angegebenen Ressource.|
|[CImage:: MaskBlt](#maskblt)|Kombiniert die Farbdaten für die Quell-und Ziel Bitmaps mithilfe der angegebenen Maske und des Raster Vorgangs.|
|[CImage::P lgblt](#plgblt)|Führt eine Bitblock Übertragung von einem Rechteck in einem Quell Gerätekontext in ein Parallelogramm in einem Zielgeräte Kontext aus.|
|[CImage:: ReleaseDC](#releasedc)|Gibt den Gerätekontext frei, der mit [CImage:: GetDC](#getdc)abgerufen wurde.|
|[CImage:: releasegdiplus](#releasegdiplus)|Gibt die von GDI+ verwendeten Ressourcen frei. Muss aufgerufen werden, um Ressourcen freizugeben, die von einem globalen Objekt erstellt wurden `CImage` .|
|[CImage:: Save](#save)|Speichert ein Bild als den angegebenen Typ. `Save` die Bild Optionen können nicht angegeben werden.|
|[CImage:: setcolortable](#setcolortable)|Legt farbige, grüne und blaue RGB-Farbwerte in einem Bereich von Einträgen in der Farbtabelle des DIB-Abschnitts fest.|
|[CImage:: SetPixel](#setpixel)|Legt das Pixel an den angegebenen Koordinaten auf die angegebene Farbe fest.|
|[CImage:: setpixelindiziert](#setpixelindexed)|Legt das Pixel an den angegebenen Koordinaten auf die Farbe am angegebenen Index der Palette fest.|
|[CImage:: setpixelrgb](#setpixelrgb)|Legt das Pixel an den angegebenen Koordinaten auf den angegebenen roten, grünen, blauen (RGB) Wert fest.|
|[CImage:: settransparentcolor](#settransparentcolor)|Legt den Index der Farbe fest, die als transparent behandelt werden soll. Nur eine Farbe in einer Palette kann transparent sein.|
|[CImage:: StretchBlt](#stretchblt)|Kopiert eine Bitmap aus einem Quell Rechteck in ein Ziel Rechteck, wobei die Bitmap bei Bedarf an die Abmessungen des Ziel Rechtecks angepasst oder komprimiert wird.|
|[CImage:: TransparentBlt](#transparentblt)|Kopiert eine Bitmap mit transparenter Farbe aus dem Quell Gerätekontext in diesen aktuellen Gerätekontext.|

### <a name="public-operators"></a>Öffentliche Operatoren

|name|Beschreibung|
|----------|-----------------|
|[CImage:: Operator HBITMAP](#operator_hbitmap)|Gibt das an das-Objekt angefügte Windows-Handle zurück `CImage` .|

## <a name="remarks"></a>Bemerkungen

`CImage` erfordert Bitmaps, bei denen es sich entweder um einen geräteunabhängigen Bitmap-Abschnitt (DIB) handelt oder nicht. Sie können jedoch [Create](#create) oder [CImage:: Load](#load) nur mit DIB-Abschnitten verwenden. Sie können eine nicht-DIB-Abschnitts Bitmap an ein-Objekt anfügen `CImage` , indem Sie [Anfügen](#attach)verwenden. Sie können jedoch nicht die folgenden `CImage` Methoden verwenden, die nur DIB-Abschnitts Bitmaps unterstützen:

- [GetBits](#getbits)

- [Getcolortable](#getcolortable)

- [Getmaxcolortableentries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [Getpixeladdress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [Setcolortable](#setcolortable)

Um zu ermitteln, ob eine angefügte Bitmap ein DIB-Abschnitt ist, nennen Sie [isdibsection](#isdibsection).

> [!NOTE]
> In Visual Studio .NET 2003 behält diese Klasse die Anzahl der `CImage` erstellten Objekte bei. Wenn die Anzahl auf 0 (null) sinkt, wird die Funktion `GdiplusShutdown` automatisch aufgerufen, um von GDI+ verwendete Ressourcen freizugeben. Dadurch wird sichergestellt, dass alle `CImage` direkt oder indirekt durch DLLs erstellten Objekte ordnungsgemäß zerstört werden und `GdiplusShutdown` nicht von aufgerufen werden `DllMain` .

> [!NOTE]
> `CImage`Es wird nicht empfohlen, globale Objekte in einer DLL zu verwenden. Wenn Sie ein globales `CImage` Objekt in einer DLL verwenden müssen, nennen Sie [CImage:: releasegdiplus](#releasegdiplus) , um die von GDI+ verwendeten Ressourcen explizit freizugeben.

`CImage` kann nicht in einem neuen [CDC](../../mfc/reference/cdc-class.md)ausgewählt werden. `CImage` erstellt einen eigenen HDC für das Image. Da eine HBITMAP nur jeweils in einem hdc ausgewählt werden kann, kann die HBITMAP, die dem zugeordnet ist, `CImage` nicht in einem anderen HDC ausgewählt werden. Wenn Sie eine CDC benötigen, rufen Sie den hdc aus dem ab, `CImage` und übergeben Sie ihn an [CDC:: FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="examples"></a>Beispiele

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Beachten Sie bei `CImage` der Verwendung von in einem MFC-Projekt, welche Member-Funktionen in Ihrem Projekt einen Zeiger auf ein [CBitmap](../../mfc/reference/cbitmap-class.md) -Objekt erwarten. Wenn Sie `CImage` mit einer solchen Funktion verwenden möchten, z. b. [CMenu:: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), verwenden Sie [CBitmap:: FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), übergeben Sie Ihr `CImage` hBitmap, und verwenden Sie die zurückgegebene `CBitmap*` .

```cpp
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
    UNREFERENCED_PARAMETER(nFlags);

    CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
    m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
    ClientToScreen(&point);
    m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x,
    point.y, this);
}
```

Mithilfe `CImage` von haben Sie Zugriff auf die tatsächlichen Bits eines DIB-Abschnitts. Sie können ein- `CImage` Objekt überall dort verwenden, wo Sie zuvor einen Win32-HBITMAP-oder DIB-Abschnitt verwendet haben.

Sie können `CImage` entweder von MFC oder ATL verwenden.

> [!NOTE]
> Wenn Sie ein Projekt mit erstellen `CImage` , müssen Sie definieren, `CString` bevor Sie *atlimage. h*einschließen. Wenn Ihr Projekt ATL ohne MFC verwendet, fügen Sie " *atlstr. h* " ein, bevor Sie " *atlimage. h*" einschließen. Wenn für Ihr Projekt MFC verwendet wird (oder wenn es sich um ein ATL-Projekt mit MFC-Unterstützung handelt), schließen Sie *afxstr. h* ein, bevor Sie *atlimage. h*einschließen.
>
> Ebenso müssen Sie *atlimage. h* einschließen, bevor Sie *Atlimpl. cpp*einschließen. Um dies zu erreichen, fügen Sie " *atlimage. h* " in die Datei " *PCH. h* " ein (*stdafx. h* in Visual Studio 2017 und früher).

## <a name="requirements"></a>Anforderungen

**Header:** atlimage. h

## <a name="cimagealphablend"></a><a name="alphablend"></a> CImage:: AlphaBlend

Zeigt Bitmaps mit transparenten oder semitransparenten Pixeln an.

```
BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    const POINT& pointDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);
```

### <a name="parameters"></a>Parameter

*hdestdc*<br/>
Handle für den Zielgeräte Kontext.

*xdest*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ydest*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*bsrcalpha*<br/>
Ein Alpha Transparenz Wert, der für die gesamte Quell Bitmap verwendet werden soll. Der Standardwert 0xFF (255) setzt voraus, dass das Bild nicht transparent ist, und dass Sie nur Pixel-Alpha Werte pro Pixel verwenden möchten.

*bblendop*<br/>
Die Alpha Mischungs Funktion für Quell-und Ziel Bitmaps, einen globalen Alpha-Wert, der auf die gesamte Quell Bitmap angewendet werden soll, und Formatierungsinformationen für die Quell Bitmap. Die Blend-Funktionen für Quelle und Ziel sind zurzeit auf AC_SRC_OVER beschränkt.

*pointdest*<br/>
Ein Verweis auf eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur, die die linke obere Ecke des Ziel Rechtecks in logischen Einheiten bezeichnet.

*ndestwidth*<br/>
Die Breite des Ziel Rechtecks in logischen Einheiten.

*ndestheight*<br/>
Die Höhe des Ziel Rechtecks in logischen Einheiten.

*xsrc*<br/>
Die logische x-Koordinate der oberen linken Ecke des Quell Rechtecks.

*ysrc*<br/>
Die logische y-Koordinate der oberen linken Ecke des Quell Rechtecks.

*nsrcwidth*<br/>
Die Breite des Quell Rechtecks in logischen Einheiten.

*nsrcheight*<br/>
Die Höhe des Quell Rechtecks in logischen Einheiten.

*neusten*<br/>
Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die das Ziel identifiziert.

*reckategorirc*<br/>
Ein Verweis auf eine- `RECT` Struktur, die die Quelle identifiziert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Alpha-Blend-Bitmaps unterstützen Farb Mischungs Farben pro Pixel.

Wenn *bblendop* auf den Standardwert AC_SRC_OVER festgelegt ist, wird die Quell Bitmap auf der Zielbitmap basierend auf den Alpha Werten der Quell Pixel platziert.

## <a name="cimageattach"></a><a name="attach"></a> CImage:: Attach

Fügt *hBitmap* an ein- `CImage` Objekt an.

```cpp
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parameter

*HBITMAP*<br/>
Ein Handle für eine HBITMAP.

*eorientation*<br/>
Gibt die Ausrichtung der Bitmap an. Dabei kann es sich um eine der folgenden Methoden handeln:

- DIBOR_DEFAULT die Ausrichtung der Bitmap durch das Betriebssystem bestimmt wird.

- DIBOR_BOTTOMUP die Zeilen der Bitmap in umgekehrter Reihenfolge angezeigt werden. Dies bewirkt, dass [CImage:: GetBits](#getbits) einen Zeiger in der Nähe des Endes des bitmappuffers und [CImage:: getPitch](#getpitch) zurückgibt, um eine negative Zahl zurückzugeben.

- DIBOR_TOPDOWN die Zeilen der Bitmap in der Reihenfolge von oben nach unten angezeigt werden. Dies bewirkt, dass [CImage:: GetBits](#getbits) einen Zeiger auf das erste Byte des bitmappuffers und [CImage:: getPitch](#getpitch) zurückgibt, um eine positive Zahl zurückzugeben.

### <a name="remarks"></a>Bemerkungen

Die Bitmap kann entweder eine nicht-DIB-Abschnitts Bitmap oder eine DIB-Abschnitts Bitmap sein. Eine Liste der Methoden, die Sie nur mit DIB-Abschnitts Bitmaps verwenden können, finden Sie unter [isdibsection](#isdibsection) .

## <a name="cimagebitblt"></a><a name="bitblt"></a> CImage:: BitBLT

Kopiert eine Bitmap aus dem Quell Gerätekontext in diesen aktuellen Gerätekontext.

```
BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const POINT& pointDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parameter

*hdestdc*<br/>
Der Ziel-hdc.

*xdest*<br/>
Die logische x-Koordinate der oberen linken Ecke des Ziel Rechtecks.

*ydest*<br/>
Die logische y-Koordinate der oberen linken Ecke des Ziel Rechtecks.

*dwrop*<br/>
Der auszuführende Raster Vorgang. Raster-Vorgangs Codes definieren genau, wie die Bits der Quelle, des Ziels und des Musters (wie durch den aktuell ausgewählten Pinsel definiert) zum bilden des Ziels kombiniert werden. Unter [BitBLT](/windows/win32/api/wingdi/nf-wingdi-bitblt) im Windows SDK finden Sie eine Liste mit anderen Code für den Raster Betrieb und deren Beschreibungen.

*pointdest*<br/>
Eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur, die die linke obere Ecke des Ziel Rechtecks angibt.

*ndestwidth*<br/>
Die Breite des Ziel Rechtecks in logischen Einheiten.

*ndestheight*<br/>
Die Höhe des Ziel Rechtecks in logischen Einheiten.

*xsrc*<br/>
Die logische x-Koordinate der oberen linken Ecke des Quell Rechtecks.

*ysrc*<br/>
Die logische y-Koordinate der oberen linken Ecke des Quell Rechtecks.

*neusten*<br/>
Eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die das Ziel Rechteck angibt.

*Point RC*<br/>
Eine- `POINT` Struktur, die die linke obere Ecke des Quell Rechtecks angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [BitBLT](/windows/win32/api/wingdi/nf-wingdi-bitblt) in der Windows SDK.

## <a name="cimagecimage"></a><a name="cimage"></a> CImage:: CImage

Erstellt ein `CImage`-Objekt.

```
CImage() throw();
```

### <a name="remarks"></a>Bemerkungen

Nachdem Sie das Objekt erstellt haben, rufen Sie [Create](#create), [Load](#load), [loadfromresource](#loadfromresource)oder [Attach](#attach) auf, um eine Bitmap an das Objekt anzufügen.

**Hinweis** In Visual Studio behält diese Klasse die Anzahl der `CImage` erstellten Objekte bei. Wenn die Anzahl auf 0 (null) sinkt, wird die Funktion `GdiplusShutdown` automatisch aufgerufen, um von GDI+ verwendete Ressourcen freizugeben. Dadurch wird sichergestellt, dass alle `CImage` direkt oder indirekt durch DLLs erstellten Objekte ordnungsgemäß zerstört werden und `GdiplusShutdown` nicht von DllMain aufgerufen werden.

`CImage`Es wird nicht empfohlen, globale Objekte in einer DLL zu verwenden. Wenn Sie ein globales `CImage` Objekt in einer DLL verwenden müssen, nennen Sie [CImage:: releasegdiplus](#releasegdiplus) , um die von GDI+ verwendeten Ressourcen explizit freizugeben.

## <a name="cimagecreate"></a><a name="create"></a> CImage:: Create

Erstellt eine `CImage` Bitmap und fügt Sie an das zuvor erstellte- `CImage` Objekt an.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*nwidth*<br/>
Die Breite der `CImage` Bitmap in Pixel.

*nheight*<br/>
Die Höhe der `CImage` Bitmap in Pixel. Wenn *nheight* positiv ist, ist die Bitmap ein Bottom-up-DIB, und der Ursprung ist die untere linke Ecke. Wenn *nheight* negativ ist, ist die Bitmap eine Top-Down-DIB, und Ihr Ursprung ist die linke obere Ecke.

*nbpp*<br/>
Die Anzahl der Bits pro Pixel in der Bitmap. Normalerweise 4, 8, 16, 24 oder 32. Kann für monochrome Bitmaps oder-Masken 1 sein.

*dwFlags*<br/>
Gibt an, ob das Bitmap-Objekt über einen Alpha-Kanal verfügt. Kann eine Kombination aus null oder mehr der folgenden Werte sein:

- " *kreatealphachannel* " Kann nur verwendet werden, wenn *nbpp* 32 und *ecompression* BI_RGB ist. Wenn angegeben, hat das erstellte Image einen Alpha-Wert (Transparenz) für jedes Pixel, das im 4. Byte der einzelnen Pixel gespeichert wird (nicht verwendet in einem nicht-alpha-32-Bit-Bild). Dieser Alphakanal wird automatisch verwendet, wenn [CImage:: AlphaBlend](#alphablend)aufgerufen wird.

> [!NOTE]
> In Aufrufen von [CImage::D RAW](#draw)werden Bilder mit einem Alphakanal automatisch mit dem Ziel gemischt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="cimagecreateex"></a><a name="createex"></a> CImage:: kreateex

Erstellt eine `CImage` Bitmap und fügt Sie an das zuvor erstellte- `CImage` Objekt an.

```
BOOL CreateEx(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD eCompression,
    const DWORD* pdwBitmasks = NULL,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*nwidth*<br/>
Die Breite der `CImage` Bitmap in Pixel.

*nheight*<br/>
Die Höhe der `CImage` Bitmap in Pixel. Wenn *nheight* positiv ist, ist die Bitmap ein Bottom-up-DIB, und der Ursprung ist die untere linke Ecke. Wenn *nheight* negativ ist, ist die Bitmap eine Top-Down-DIB, und Ihr Ursprung ist die linke obere Ecke.

*nbpp*<br/>
Die Anzahl der Bits pro Pixel in der Bitmap. Normalerweise 4, 8, 16, 24 oder 32. Kann für monochrome Bitmaps oder-Masken 1 sein.

*ecompression*<br/>
Gibt den Komprimierungstyp für eine komprimierte Bottom-up-Bitmap an (Top-Down-Disb können nicht komprimiert werden). Es kann sich um einen der folgenden Werte handeln:

- BI_RGB das Format ist nicht komprimiert. Die Angabe dieses Werts beim Aufrufen `CImage::CreateEx` von entspricht dem Aufrufen von `CImage::Create` .

- BI_BITFIELDS das Format unkomprimiert ist, und die Farbtabelle besteht aus drei DWORD-Farb Masken, die jeweils die roten, grünen und blauen Komponenten der einzelnen Pixel angeben. Dies ist gültig bei Verwendung mit 16-und 32-bpp-Bitmaps.

*pdwbitfields*<br/>
Wird nur verwendet, wenn *ecompression* auf BI_BITFIELDS festgelegt ist, andernfalls muss Sie NULL sein. Ein Zeiger auf ein Array von drei DWORD-Bitmasks, das angibt, welche Bits jedes Pixels für die rot-, grün-und Blau-Komponenten der Farbe verwendet werden. Informationen zu Einschränkungen für Bitfields finden Sie unter [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) in der Windows SDK.

*dwFlags*<br/>
Gibt an, ob das Bitmap-Objekt über einen Alpha-Kanal verfügt. Kann eine Kombination aus null oder mehr der folgenden Werte sein:

- " *kreatealphachannel* " Kann nur verwendet werden, wenn *nbpp* 32 und *ecompression* BI_RGB ist. Wenn angegeben, hat das erstellte Image einen Alpha-Wert (Transparenz) für jedes Pixel, das im 4. Byte der einzelnen Pixel gespeichert wird (nicht verwendet in einem nicht-alpha-32-Bit-Bild). Dieser Alphakanal wird automatisch verwendet, wenn [CImage:: AlphaBlend](#alphablend)aufgerufen wird.

   > [!NOTE]
   > In Aufrufen von [CImage::D RAW](#draw)werden Bilder mit einem Alphakanal automatisch mit dem Ziel gemischt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich. Andernfalls false.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine 100 x 100 Pixel-Bitmap erstellt, wobei 16 Bits zum Codieren der einzelnen Pixel verwendet werden. In einem angegebenen 16-Bit-Pixel codieren Bits 0-3 die rote Komponente, Bits 4-7 codieren grün und Bits 8-11 codieren blau. Die verbleibenden 4 Bits werden nicht verwendet.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a> CImage::D estroy

Trennt die Bitmap vom `CImage` -Objekt und zerstört die Bitmap.

```cpp
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a> CImage::D Etach

Trennt eine Bitmap von einem- `CImage` Objekt.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für die getrennte Bitmap oder NULL, wenn keine Bitmap angefügt ist.

## <a name="cimagedraw"></a><a name="draw"></a> CImage::D RAW

Kopiert eine Bitmap aus dem Quell Gerätekontext in den aktuellen Gerätekontext.

```
BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest) const throw();

BOOL Draw(
    HDC hDestDC,
    const POINT& pointDest) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest) const throw();
```

### <a name="parameters"></a>Parameter

*hdestdc*<br/>
Ein Handle für den Zielgeräte Kontext.

*xdest*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ydest*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ndestwidth*<br/>
Die Breite des Ziel Rechtecks in logischen Einheiten.

*ndestheight*<br/>
Die Höhe des Ziel Rechtecks in logischen Einheiten.

*xsrc*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Quell Rechtecks.

*ysrc*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Quell Rechtecks.

*nsrcwidth*<br/>
Die Breite des Quell Rechtecks in logischen Einheiten.

*nsrcheight*<br/>
Die Höhe des Quell Rechtecks in logischen Einheiten.

*neusten*<br/>
Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die das Ziel identifiziert.

*reckategorirc*<br/>
Ein Verweis auf eine- `RECT` Struktur, die die Quelle identifiziert.

*pointdest*<br/>
Ein Verweis auf eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur, die die linke obere Ecke des Ziel Rechtecks in logischen Einheiten bezeichnet.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

`Draw` führt den gleichen Vorgang wie [StretchBlt](#stretchblt)aus, es sei denn, das Bild enthält eine transparente Farbe oder einen Alphakanal. In diesem Fall `Draw` führt den gleichen Vorgang wie erforderlich aus, um entweder [TransparentBlt](#transparentblt) oder [AlphaBlend](#alphablend) durchführen zu können.

Bei Versionen von, die `Draw` kein Quell Rechteck angeben, ist das gesamte Quell Image der Standard. Bei der-Version `Draw` , die keine Größe für das Ziel Rechteck angibt, ist die Größe des Quell Bilds der Standardwert, und es erfolgt keine Streckung oder Verkleinerung.

## <a name="cimagegetbits"></a><a name="getbits"></a> CImage:: GetBits

Ruft einen Zeiger auf die tatsächlichen Bitwerte eines angegebenen Pixels in einer Bitmap ab.

```cpp
void* GetBits() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den bitmappuffer. Wenn die Bitmap ein Bottom-up-DIB ist, zeigt der Zeiger auf das Ende des Puffers. Wenn die Bitmap ein Top-Down-DIB ist, zeigt der Zeiger auf das erste Byte des Puffers.

### <a name="remarks"></a>Bemerkungen

Mithilfe dieses Zeigers können Sie zusammen mit dem von [getPitch](#getpitch)zurückgegebenen Wert einzelne Pixel in einem Bild suchen und ändern.

> [!NOTE]
> Diese Methode unterstützt nur DIB-Abschnitts Bitmaps. Folglich greifen Sie auf die Pixel eines- `CImage` Objekts auf die gleiche Weise wie die Pixel eines DIB-Abschnitts zu. Der zurückgegebene Zeiger zeigt auf das Pixel an der Position (0,0).

## <a name="cimagegetbpp"></a><a name="getbpp"></a> CImage:: getbpp

Ruft den Wert für Bits pro Pixel ab.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bits pro Pixel.

### <a name="remarks"></a>Bemerkungen

Dieser Wert bestimmt die Anzahl der Bits, die jedes Pixel definieren, sowie die maximale Anzahl von Farben in der Bitmap.

Die Bits pro Pixel sind normalerweise 1, 4, 8, 16, 24 oder 32. `biBitCount`Weitere Informationen zu diesem Wert finden Sie unter dem-Member von [BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader) im Windows SDK.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a> CImage:: getcolortable

Ruft rote, grüne, blaue (RGB) Farbwerte aus einem Bereich von Einträgen in der Palette des DIB-Abschnitts ab.

```cpp
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parameter

*ifirstcolor*<br/>
Der Farbtabellen Index des ersten Eintrags, der abgerufen werden soll.

*ncolors*<br/>
Die Anzahl der abzurufenden farbtabelleneinträge.

*prgbcolors*<br/>
Ein Zeiger auf das Array von [rgbquad](/windows/win32/api/wingdi/ns-wingdi-rgbquad) -Strukturen zum Abrufen der farbtabelleneinträge.

## <a name="cimagegetdc"></a><a name="getdc"></a> CImage:: GetDC

Ruft den Gerätekontext ab, in dem das Bild derzeit ausgewählt ist.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für einen Gerätekontext.

### <a name="remarks"></a>Bemerkungen

Für jeden-aufrufbedarf benötigen `GetDC` Sie einen nachfolgenden-aufrufbefehl für [ReleaseDC](#releasedc).

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a> CImage:: getexporterfilterstring

Findet Bildformate, die zum Speichern von Bildern verfügbar sind.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parameter

*strexporters*<br/>
Ein Verweis auf ein `CSimpleString`-Objekt. Weitere Informationen finden Sie unter " **Hinweise** ".

*aguidfiletypes*<br/>
Ein Array von GUIDs, wobei jedes Element einem der Dateitypen in der Zeichenfolge entspricht. Im Beispiel in *pszallfilesdescription* unten ist *aguidfiletypes*[0] GUID_NULL, und die restlichen Array Werte sind die Bild Dateiformate, die vom aktuellen Betriebssystem unterstützt werden.

> [!NOTE]
> Eine umfassende Liste der Konstanten finden Sie unter **Bild Datei Format Konstanten** in der Windows SDK.

*pszallfilesdescription*<br/>
Wenn dieser Parameter nicht NULL ist, weist die Filter Zeichenfolge am Anfang der Liste einen zusätzlichen Filter auf. Dieser Filter enthält den aktuellen Wert von " *pszallfilesdescription* " für seine Beschreibung und akzeptiert Dateien jeder beliebigen Erweiterung, die von einem anderen Exportprogramm in der Liste unterstützt wird.

Beispiel:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwexclude*<br/>
Ein Satz von Bitflags, die angeben, welche Dateitypen aus der Liste ausgeschlossen werden sollen. Zulässige Flags sind:

- `excludeGIF` = 0x01 schließt GIF-Dateien aus.

- `excludeBMP` = 0x02 schließt BMP-Dateien (Windows-Bitmap) aus.

- `excludeEMF` = 0x04 schließt EMF (Enhanced Metafile)-Dateien aus.

- `excludeWMF` = 0x08 schließt WMF-Dateien (Windows Metafile) aus.

- `excludeJPEG` = 0x10 schließt JPEG-Dateien aus.

- `excludePNG` = 0x20 schließt PNG-Dateien aus.

- `excludeTIFF` = 0x40 schließt TIFF-Dateien aus.

- `excludeIcon` = 0x80 schließt ICO-Dateien (Windows-Symbol Dateien) aus.

- `excludeOther` = 0x80000000 schließt alle anderen Dateitypen aus, die oben nicht aufgeführt sind.

- `excludeDefaultLoad` = 0 beim Laden werden alle Dateitypen standardmäßig eingeschlossen.

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Zum Speichern werden diese Dateien standardmäßig ausgeschlossen, da Sie in der Regel über besondere Anforderungen verfügen.

*chseparator*<br/>
Das Trennzeichen, das zwischen den Bildformaten verwendet wird. Weitere Informationen finden Sie unter " **Hinweise** ".

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Sie können die resultierende Format Zeichenfolge an Ihr MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) -Objekt übergeben, um die Dateierweiterungen der verfügbaren Bildformate im Dialogfeld Datei speichern unter verfügbar zu machen.

Der Parameter " *strexporter* " weist das folgende Format auf:

Datei description0&#124;\* . ext0&#124;filedescription1&#124;\* . EXT1&#124;... Dateibeschreibung *n*&#124;\* . ext *n*&#124;&#124;

wobei ' &#124; ' das von angegebene Trennzeichen ist `chSeparator` . Beispiel:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Verwenden Sie das Standard Trennzeichen "&#124;", wenn Sie diese Zeichenfolge an ein MFC- `CFileDialog` Objekt übergeben. Verwenden Sie das NULL Trennzeichen "\ 0", wenn Sie diese Zeichenfolge an ein gemeinsames Dialogfeld zum Speichern von Dateien übergeben.

## <a name="cimagegetheight"></a><a name="getheight"></a> CImage:: GetHeight

Ruft die Höhe eines Bilds in Pixel ab.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Höhe eines Bilds in Pixel.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a> CImage:: getimporterfilterstring

Findet Bildformate, die zum Laden von Bildern verfügbar sind.

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parameter

*strimporters*<br/>
Ein Verweis auf ein `CSimpleString`-Objekt. Weitere Informationen finden Sie unter " **Hinweise** ".

*aguidfiletypes*<br/>
Ein Array von GUIDs, wobei jedes Element einem der Dateitypen in der Zeichenfolge entspricht. Im Beispiel in der folgenden Abbildung von *pszallfilesdescription* wird *aguidfiletypes*[0] mit den verbleibenden Array Werten GUID_NULL, die vom aktuellen Betriebssystem unterstützt werden.

> [!NOTE]
> Eine umfassende Liste der Konstanten finden Sie unter **Bild Datei Format Konstanten** in der Windows SDK.

*pszallfilesdescription*<br/>
Wenn dieser Parameter nicht NULL ist, weist die Filter Zeichenfolge am Anfang der Liste einen zusätzlichen Filter auf. Dieser Filter enthält den aktuellen Wert von " *pszallfilesdescription* " für seine Beschreibung und akzeptiert Dateien jeder beliebigen Erweiterung, die von einem anderen Exportprogramm in der Liste unterstützt wird.

Beispiel:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwexclude*<br/>
Ein Satz von Bitflags, die angeben, welche Dateitypen aus der Liste ausgeschlossen werden sollen. Zulässige Flags sind:

- `excludeGIF` = 0x01 schließt GIF-Dateien aus.

- `excludeBMP` = 0x02 schließt BMP-Dateien (Windows-Bitmap) aus.

- `excludeEMF` = 0x04 schließt EMF (Enhanced Metafile)-Dateien aus.

- `excludeWMF` = 0x08 schließt WMF-Dateien (Windows Metafile) aus.

- `excludeJPEG` = 0x10 schließt JPEG-Dateien aus.

- `excludePNG` = 0x20 schließt PNG-Dateien aus.

- `excludeTIFF` = 0x40 schließt TIFF-Dateien aus.

- `excludeIcon` = 0x80 schließt ICO-Dateien (Windows-Symbol Dateien) aus.

- `excludeOther` = 0x80000000 schließt alle anderen Dateitypen aus, die oben nicht aufgeführt sind.

- `excludeDefaultLoad` = 0 beim Laden werden alle Dateitypen standardmäßig eingeschlossen.

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Zum Speichern werden diese Dateien standardmäßig ausgeschlossen, da Sie in der Regel über besondere Anforderungen verfügen.

*chseparator*<br/>
Das Trennzeichen, das zwischen den Bildformaten verwendet wird. Weitere Informationen finden Sie unter " **Hinweise** ".

### <a name="remarks"></a>Bemerkungen

Sie können die resultierende Format Zeichenfolge an Ihr MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) -Objekt übergeben, um die Dateierweiterungen der verfügbaren Bildformate im Dialogfeld **Datei öffnen** verfügbar zu machen.

Der *strimporter* -Parameter hat folgendes Format:

Datei description0&#124;\* . ext0&#124;filedescription1&#124;\* . EXT1&#124;... Dateibeschreibung *n*&#124;\* . ext *n*&#124;&#124;

Dabei ist ' &#124; ' das von ' *chseparator*' angegebene Trennzeichen. Beispiel:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Verwenden Sie das Standard Trennzeichen "&#124;", wenn Sie diese Zeichenfolge an ein MFC- `CFileDialog` Objekt übergeben. Verwenden Sie das NULL Trennzeichen "\ 0", wenn Sie diese Zeichenfolge an ein gemeinsames Dialogfeld zum **Öffnen von Dateien** übergeben.

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a> CImage:: getmaxcolortableentries

Ruft die maximale Anzahl von Einträgen in der Farbtabelle ab.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Einträge in der Farbtabelle.

### <a name="remarks"></a>Bemerkungen

Diese Methode unterstützt nur DIB-Abschnitts Bitmaps.

## <a name="cimagegetpitch"></a><a name="getpitch"></a> CImage:: getPitch

Ruft die Tonhöhe eines Bilds ab.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Darstellung des Bilds. Wenn der Rückgabewert negativ ist, ist die Bitmap ein Bottom-up-DIB, und der Ursprung ist die untere linke Ecke. Wenn der Rückgabewert positiv ist, ist die Bitmap ein Top-Down-DIB, und der Ursprung ist die linke obere Ecke.

### <a name="remarks"></a>Bemerkungen

Die Tonhöhe ist der Abstand zwischen zwei Speicheradressen (in Bytes), die den Anfang einer bitmaplinie darstellen, und dem Anfang der nächsten Bitmap-Linie. Da die Tonhöhe in Bytes gemessen wird, hilft Ihnen die Darstellung eines Bilds dabei, das Pixel Format zu bestimmen. Die Tonhöhe kann auch zusätzlichen Arbeitsspeicher enthalten, der für die Bitmap reserviert ist.

Verwenden `GetPitch` Sie mit [GetBits](#getbits) , um einzelne Pixel eines Bilds zu suchen.

> [!NOTE]
> Diese Methode unterstützt nur DIB-Abschnitts Bitmaps.

## <a name="cimagegetpixel"></a><a name="getpixel"></a> CImage:: GetPixel

Ruft die Farbe des Pixels an der von *x* und *y*angegebenen Position ab.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Die x-Koordinate des Pixels.

*y*<br/>
Die y-Koordinate des Pixels.

### <a name="return-value"></a>Rückgabewert

Der rote, grüne und blaue (RGB) Wert des Pixels. Wenn das Pixel außerhalb des aktuellen Clippingbereichs liegt, wird der Rückgabewert CLR_INVALID.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a> CImage:: getpixeladdress

Ruft die genaue Adresse eines Pixels ab.

```cpp
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Die x-Koordinate des Pixels.

*y*<br/>
Die y-Koordinate des Pixels.

### <a name="remarks"></a>Bemerkungen

Die Adresse wird gemäß den Koordinaten eines Pixels, der Tonhöhe der Bitmap und den Bits pro Pixel bestimmt.

Bei Formaten, die weniger als 8 Bits pro Pixel aufweisen, gibt diese Methode die Adresse des Bytes zurück, das das Pixel enthält. Wenn Ihr Bildformat z. b. 4 Bits pro Pixel hat, `GetPixelAddress` gibt die Adresse des ersten Pixels im Byte zurück, und Sie müssen 2 Pixel pro Byte berechnen.

> [!NOTE]
> Diese Methode unterstützt nur DIB-Abschnitts Bitmaps.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a> CImage:: gettransparentcolor

Ruft den indizierten Speicherort der transparenten Farbe in der Farbpalette ab.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Index der transparenten Farbe.

## <a name="cimagegetwidth"></a><a name="getwidth"></a> CImage:: getWidth

Ruft die Breite eines Bilds in Pixel ab.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Breite der Bitmap in Pixel.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a> CImage:: isdibsection

Bestimmt, ob die angefügte Bitmap ein DIB-Abschnitt ist.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die angefügte Bitmap ein DIB-Abschnitt ist. Andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn die Bitmap kein DIB-Abschnitt ist, können Sie die folgenden Methoden nicht verwenden `CImage` , die nur DIB-Abschnitts Bitmaps unterstützen:

- [GetBits](#getbits)

- [Getcolortable](#getcolortable)

- [Getmaxcolortableentries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [Getpixeladdress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [Setcolortable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a> CImage:: isindebug

Bestimmt, ob die Pixel einer Bitmap einer Farbpalette zugeordnet werden.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn indiziert. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt nur dann true zurück, wenn die Bitmap 8-Bit (256 Farben) oder kleiner ist.

> [!NOTE]
> Diese Methode unterstützt nur DIB-Abschnitts Bitmaps.

## <a name="cimageisnull"></a><a name="isnull"></a> CImage:: IsNull

Bestimmt, ob eine Bitmap momentan geladen ist.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt true zurück, wenn eine Bitmap zurzeit nicht geladen ist. andernfalls false.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a> CImage:: istransparkocysupported

Gibt an, ob die Anwendung transparente Bitmaps unterstützt.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die aktuelle Plattform Transparenz unterstützt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert ungleich 0 (null) ist und Transparenz unterstützt wird, behandelt ein Aufrufen von [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)oder [Draw](#draw) transparente Farben.

## <a name="cimageload"></a><a name="load"></a> CImage:: Load

Lädt ein Bild

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parameter

*pszFileName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu ladenden Bilddatei enthält.

*pStream*<br/>
Ein Zeiger auf einen Stream, der den Namen der zu ladenden Bilddatei enthält.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Lädt das von *pszFileName* oder *pStream*angegebene Bild.

Gültige Bildtypen sind BMP, GIF, JPEG, PNG und TIFF.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a> CImage:: loadfromresource

Lädt ein Bild aus einer Bitmap-Ressource.

```cpp
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
Handle für eine Instanz des Moduls, das das zu ladende Bild enthält.

*pszresourcename*<br/>
Ein Zeiger auf die Zeichenfolge, die den Namen der Ressource enthält, die das zu ladende Bild enthält.

*nidresource*<br/>
Die ID der zu ladenden Ressource

### <a name="remarks"></a>Bemerkungen

Die Ressource muss den Typ "Bitmap" aufweisen.

## <a name="cimagemaskblt"></a><a name="maskblt"></a> CImage:: MaskBlt

Kombiniert die Farbdaten für die Quell-und Ziel Bitmaps mithilfe der angegebenen Maske und des Raster Vorgangs.

```
BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    HBITMAP hbmMask,
    int xMask,
    int yMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    HBITMAP hbmMask,
    const POINT& pointMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const POINT& pointDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parameter

*hdestdc*<br/>
Das Handle für das Modul, dessen ausführbare Datei die Ressource enthält.

*xdest*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ydest*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ndestwidth*<br/>
Die Breite des Ziel Rechtecks und der Quell Bitmap in logischen Einheiten.

*ndestheight*<br/>
Die Höhe des Ziel Rechtecks und der Quell Bitmap in logischen Einheiten.

*xsrc*<br/>
Die logische x-Koordinate der oberen linken Ecke der Quell Bitmap.

*ysrc*<br/>
Die logische y-Koordinate der oberen linken Ecke der Quell Bitmap.

*hbmmask*<br/>
Handle für die Chrome-Masken Bitmap, kombiniert mit der Farb Bitmap im Quell Gerätekontext.

*xmask*<br/>
Der horizontale Pixel Offset für die Maske-Bitmap, die durch den *hbmmask* -Parameter angegeben wird.

*ymask*<br/>
Der vertikale Pixel Offset für die Maske-Bitmap, die durch den *hbmmask* -Parameter angegeben wird.

*dwrop*<br/>
Gibt die ternären Raster Vorgangs Codes für Vordergrund und Hintergrund an, die die-Methode verwendet, um die Kombination von Quell-und Zieldaten zu steuern. Der Code für den Hintergrund Raster Vorgang wird im hochwertigen Byte des höherwertigen Worts dieses Werts gespeichert. der Code für den Vordergrund-Raster Vorgang wird in einem nieder wertigen Byte des höchst wertigen Worts dieses Werts gespeichert. Das nieder wertige Wort dieses Werts wird ignoriert und sollte NULL sein. Eine Erläuterung der Vordergrund-und Hintergrundinformationen im Kontext dieser Methode finden Sie unter `MaskBlt` in der Windows SDK. Eine Liste der allgemeinen Raster Vorgangs Codes finden Sie unter `BitBlt` in der Windows SDK.

*neusten*<br/>
Ein Verweis auf eine- `RECT` Struktur, die das Ziel identifiziert.

*Point RC*<br/>
Eine- `POINT` Struktur, die die linke obere Ecke des Quell Rechtecks angibt.

*pointmaske*<br/>
Eine- `POINT` Struktur, die die linke obere Ecke der Masken Bitmap angibt.

*pointdest*<br/>
Ein Verweis auf eine- `POINT` Struktur, die die linke obere Ecke des Ziel Rechtecks in logischen Einheiten bezeichnet.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode gilt nur für Windows NT, Version 4,0 und höher.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a> CImage:: Operator HBITMAP

Verwenden Sie diesen Operator, um das angefügte Windows-GDI-Handle des-Objekts zu erhalten `CImage` . Dieser Operator ist ein Typumwandlungs Operator, der die direkte Verwendung eines HBITMAP-Objekts unterstützt.

## <a name="cimageplgblt"></a><a name="plgblt"></a> CImage::P lgblt

Führt eine Bitblock Übertragung von einem Rechteck in einem Quell Gerätekontext in ein Parallelogramm in einem Zielgeräte Kontext aus.

```
BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    HBITMAP hbmMask = NULL,
    int xMask = 0,
    int yMask = 0) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    const RECT& rectSrc,
    HBITMAP hbmMask = NULL,
    const POINT& pointMask = CPoint(0, 0)) const throw();
```

### <a name="parameters"></a>Parameter

*hdestdc*<br/>
Ein Handle für den Zielgeräte Kontext.

*ppoints*<br/>
Ein Zeiger auf ein Array von drei Punkten im logischen Raum, der drei Ecken des Ziel-parallelograms identifiziert. Die linke obere Ecke des Quell Rechtecks wird dem ersten Punkt in diesem Array zugeordnet, der oberen rechten Ecke des zweiten Punkts in diesem Array und der unteren linken Ecke zum dritten Punkt. Die untere rechte Ecke des Quell Rechtecks wird dem impliziten vierten Punkt im Parallelogram zugeordnet.

*hbmmask*<br/>
Ein Handle für eine optionale monochrome Bitmap, mit der die Farben des Quell Rechtecks maskiert werden.

*xsrc*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Quell Rechtecks.

*ysrc*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Quell Rechtecks.

*nsrcwidth*<br/>
Die Breite des Quell Rechtecks in logischen Einheiten.

*nsrcheight*<br/>
Die Höhe des Quell Rechtecks in logischen Einheiten.

*xmask*<br/>
Die x-Koordinate der oberen linken Ecke der monochrome Bitmap.

*ymask*<br/>
Die y-Koordinate der oberen linken Ecke der monochrome Bitmap.

*reckategorirc*<br/>
Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die die Koordinaten des Quell Rechtecks angibt.

*pointmaske*<br/>
Eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur, die die linke obere Ecke der Masken Bitmap angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn *hbmmask* eine gültige monochrome Bitmap identifiziert, `PlgBit` verwendet diese Bitmap, um die Bits der Farbdaten aus dem Quell Rechteck zu maskieren.

Diese Methode gilt nur für Windows NT, Version 4,0 und höher. Ausführlichere Informationen finden Sie unter [plgblt](/windows/win32/api/wingdi/nf-wingdi-plgblt) in der Windows SDK.

## <a name="cimagereleasedc"></a><a name="releasedc"></a> CImage:: ReleaseDC

Gibt den Gerätekontext frei.

```cpp
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Bemerkungen

Da jeweils nur eine Bitmap in einem Gerätekontext ausgewählt werden kann, müssen Sie `ReleaseDC` für jeden Aufruf von [GetDC](#getdc)aufrufen.

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a> CImage:: releasegdiplus

Gibt die von GDI+ verwendeten Ressourcen frei.

```cpp
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode muss aufgerufen werden, um Ressourcen freizugeben, die von einem globalen Objekt zugeordnet werden `CImage` . Weitere Informationen finden Sie unter [CImage:: CImage](#cimage).

## <a name="cimagesave"></a><a name="save"></a> CImage:: Save

Speichert ein Bild im angegebenen Stream oder in der angegebenen Datei auf dem Datenträger.

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
Ein Zeiger auf ein COM-IStream-Objekt, das die Datei image Daten enthält.

*pszFileName*<br/>
Ein Zeiger auf den Dateinamen des Bilds.

*guidfiletype*<br/>
Der Dateityp, in dem das Bild gespeichert werden soll. Dabei kann es sich um eine der folgenden Methoden handeln:

- `ImageFormatBMP` Ein unkomprimiertes Bitmap-Bild.

- `ImageFormatPNG` Ein komprimiertes Bild für eine Portable Netzwerk Grafik (PNG).

- `ImageFormatJPEG` Ein mit JPEG komprimiertes Bild.

- `ImageFormatGIF` Ein mit GIF komprimiertes Bild.

> [!NOTE]
> Eine umfassende Liste der Konstanten finden Sie unter **Bild Datei Format Konstanten** in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion können Sie das Bild unter Verwendung eines angegebenen Namens und Typs speichern. Wenn der *guidfiletype* -Parameter nicht enthalten ist, wird die Dateierweiterung des Datei namens verwendet, um das Bildformat zu bestimmen. Wenn keine Erweiterung bereitgestellt wird, wird das Bild im BMP-Format gespeichert.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a> CImage:: setcolortable

Legt die roten, grünen, blauen (RGB) Farbwerte für einen Bereich von Einträgen in der Palette des DIB-Abschnitts fest.

```cpp
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parameter

*ifirstcolor*<br/>
Der Farbtabellen Index des ersten Eintrags, der festgelegt werden soll.

*ncolors*<br/>
Die Anzahl der festzulegenden farbtabelleneinträge.

*prgbcolors*<br/>
Ein Zeiger auf das Array von [rgbquad](/windows/win32/api/wingdi/ns-wingdi-rgbquad) -Strukturen, um die farbtabelleneinträge festzulegen.

### <a name="remarks"></a>Bemerkungen

Diese Methode unterstützt nur DIB-Abschnitts Bitmaps.

## <a name="cimagesetpixel"></a><a name="setpixel"></a> CImage:: SetPixel

Legt die Farbe eines Pixels an einer bestimmten Position in der Bitmap fest.

```cpp
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Die horizontale Position des festzulegenden Pixels.

*y*<br/>
Die vertikale Position des festzulegenden Pixels.

*color*<br/>
Die Farbe, in der das Pixel festgelegt wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn die Pixelkoordinaten außerhalb des ausgewählten Clippingbereichs liegen.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a> CImage:: setpixelindiziert

Legt die Pixelfarbe auf die Farbe fest, die sich in der Farbpalette unter *iIndex* befindet.

```cpp
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Die horizontale Position des festzulegenden Pixels.

*y*<br/>
Die vertikale Position des festzulegenden Pixels.

*iIndex*<br/>
Der Index einer Farbe in der Farbpalette.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a> CImage:: setpixelrgb

Legt das Pixel an den durch *x* und *y* angegebenen Positionen auf die durch *r*, *g*und *b*angegebenen Farben in einem roten, grünen, blauen (RGB) Bild fest.

```cpp
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Die horizontale Position des festzulegenden Pixels.

*y*<br/>
Die vertikale Position des festzulegenden Pixels.

*r*<br/>
Die Intensität der roten Farbe.

*g*<br/>
Die Intensität der grünen Farbe.

*b*<br/>
Die Intensität der blauen Farbe.

### <a name="remarks"></a>Bemerkungen

Die roten, grünen und blauen Parameter werden jeweils durch eine Zahl zwischen 0 und 255 dargestellt. Wenn Sie alle drei Parameter auf 0 (null) festlegen, ist die kombinierte resultierende Farbe schwarz. Wenn Sie alle drei Parameter auf 255 festlegen, ist die kombinierte resultierende Farbe weiß.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a> CImage:: settransparentcolor

Legt eine Farbe an einer angegebenen indizierten Position als transparent fest.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parameter

*itransparentcolor*<br/>
Der Index der Farbe, die auf transparent festgelegt werden soll, in einer Farbpalette. Wenn-1, wird keine Farbe auf transparent festgelegt.

### <a name="return-value"></a>Rückgabewert

Der Index der Farbe, die zuvor als transparent festgelegt wurde.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a> CImage:: StretchBlt

Kopiert eine Bitmap aus dem Quell Gerätekontext in diesen aktuellen Gerätekontext.

```
BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parameter

*hdestdc*<br/>
Ein Handle für den Zielgeräte Kontext.

*xdest*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ydest*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ndestwidth*<br/>
Die Breite des Ziel Rechtecks in logischen Einheiten.

*ndestheight*<br/>
Die Höhe des Ziel Rechtecks in logischen Einheiten.

*dwrop*<br/>
Der auszuführende Raster Vorgang. Raster-Vorgangs Codes definieren genau, wie die Bits der Quelle, des Ziels und des Musters (wie durch den aktuell ausgewählten Pinsel definiert) zum bilden des Ziels kombiniert werden. Unter [BitBLT](/windows/win32/api/wingdi/nf-wingdi-bitblt) im Windows SDK finden Sie eine Liste mit anderen Code für den Raster Betrieb und deren Beschreibungen.

*neusten*<br/>
Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die das Ziel identifiziert.

*xsrc*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Quell Rechtecks.

*ysrc*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Quell Rechtecks.

*nsrcwidth*<br/>
Die Breite des Quell Rechtecks in logischen Einheiten.

*nsrcheight*<br/>
Die Höhe des Quell Rechtecks in logischen Einheiten.

*reckategorirc*<br/>
Ein Verweis auf eine- `RECT` Struktur, die die Quelle identifiziert.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) in der Windows SDK.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a> CImage:: TransparentBlt

Kopiert eine Bitmap aus dem Quell Gerätekontext in diesen aktuellen Gerätekontext.

```
BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    UINT crTransparent = CLR_INVALID) const throw();
```

### <a name="parameters"></a>Parameter

*hdestdc*<br/>
Ein Handle für den Zielgeräte Kontext.

*xdest*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ydest*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Ziel Rechtecks.

*ndestwidth*<br/>
Die Breite des Ziel Rechtecks in logischen Einheiten.

*ndestheight*<br/>
Die Höhe des Ziel Rechtecks in logischen Einheiten.

*crtransparent*<br/>
Die Farbe in der Quell Bitmap, die als transparent behandelt werden soll. Standardmäßig CLR_INVALID, das angibt, dass die Farbe, die derzeit als transparente Farbe des Bilds festgelegt ist, verwendet werden soll.

*neusten*<br/>
Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die das Ziel identifiziert.

*xsrc*<br/>
Die x-Koordinate (in logischen Einheiten) der oberen linken Ecke des Quell Rechtecks.

*ysrc*<br/>
Die y-Koordinate (in logischen Einheiten) der oberen linken Ecke des Quell Rechtecks.

*nsrcwidth*<br/>
Die Breite des Quell Rechtecks in logischen Einheiten.

*nsrcheight*<br/>
Die Höhe des Quell Rechtecks in logischen Einheiten.

*reckategorirc*<br/>
Ein Verweis auf eine- `RECT` Struktur, die die Quelle identifiziert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls false.

### <a name="remarks"></a>Bemerkungen

`TransparentBlt` wird für Quell Bitmaps von 4 Bits pro Pixel und 8 Bits pro Pixel unterstützt. Verwenden Sie [CImage:: AlphaBlend](#alphablend) , um 32 Bits pro Pixel-Bitmaps mit Transparenz anzugeben.

### <a name="example"></a>Beispiel

```cpp
// Performs a transparent blit from the source image to the destination
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage,
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
    HDC hDstDC = NULL;
    BOOL bResult;

    if(pSrcImage == NULL || pDstImage == NULL)
    {
        // Invalid parameter
        return FALSE;
    }

    // Obtain a DC to the destination image
    hDstDC = pDstImage->GetDC();
    // Perform the blit
    bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

    // Release the destination DC
    pDstImage->ReleaseDC();

    return bResult;
}
```

## <a name="see-also"></a>Weitere Informationen

[MMXSwarm-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[SimpleImage-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Geräteunabhängige Bitmaps](/windows/win32/gdi/device-independent-bitmaps)<br/>
["Kreatedibsection"](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)<br/>
[Geräteunabhängige Bitmaps](/windows/win32/gdi/device-independent-bitmaps)<br/>
["Kreatedibsection"](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
