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
ms.openlocfilehash: 5b5ef833a3755b07e42a60b24464b1f260062d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317811"
---
# <a name="cimage-class"></a>CImage-Klasse

`CImage`bietet erweiterte Bitmap-Unterstützung, einschließlich der Möglichkeit, Bilder in JPEG-, GIF-, BMP- und PORTABLE Network Graphics (PNG)-Formaten zu laden und zu speichern.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CImage
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CImage::CImage](#cimage)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|Zeigt Bitmaps mit transparenten oder halbtransparenten Pixeln an.|
|[CImage::Attach](#attach)|Fügt ein HBITMAP `CImage` an ein Objekt an. Kann entweder mit Nicht-DIB-Abschnittsbitmaps oder DIB-Abschnittsbitmaps verwendet werden.|
|[CImage::BitBlt](#bitblt)|Kopiert eine Bitmap aus dem Quellgerätekontext in diesen aktuellen Gerätekontext.|
|[CImage::Erstellen](#create)|Erstellt eine DIB-Abschnittsbitmap und fügt `CImage` sie an das zuvor erstellte Objekt an.|
|[CImage::CreateEx](#createex)|Erstellt eine DIB-Abschnittsbitmap (mit zusätzlichen Parametern) `CImage` und fügt sie an das zuvor erstellte Objekt an.|
|[CImage::Destroy](#destroy)|Trennt die Bitmap vom `CImage` Objekt und zerstört die Bitmap.|
|[CImage::Detach](#detach)|Trennt die Bitmap von `CImage` einem Objekt.|
|[CImage::Draw](#draw)|Kopiert eine Bitmap aus einem Quellrechteck in ein Zielrechteck. `Draw`dehnt oder komprimiert die Bitmap, um sie bei Bedarf an die Abmessungen des Zielrechtecks anzupassen, und verarbeitet Alpha-Verschmelzungen und transparente Farben.|
|[CImage::GetBits](#getbits)|Ruft einen Zeiger auf die tatsächlichen Pixelwerte der Bitmap ab.|
|[CImage::GetBPP](#getbpp)|Ruft die Bits pro Pixel ab.|
|[CImage::GetColorTable](#getcolortable)|Ruft rote, grüne, blaue (RGB) Farbwerte aus einem Bereich von Einträgen in der Farbtabelle ab.|
|[CImage::GetDC](#getdc)|Ruft den Gerätekontext ab, in dem die aktuelle Bitmap ausgewählt ist.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Sucht die verfügbaren Bildformate und deren Beschreibungen.|
|[CImage::GetHeight](#getheight)|Ruft die Höhe des aktuellen Bildes in Pixel ab.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Sucht die verfügbaren Bildformate und deren Beschreibungen.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Ruft die maximale Anzahl von Einträgen in der Farbtabelle ab.|
|[CImage::GetPitch](#getpitch)|Ruft die Tonhöhe des aktuellen Bildes in Bytes ab.|
|[CImage::GetPixel](#getpixel)|Ruft die Farbe des Pixels ab, das durch *x* und *y*angegeben wird.|
|[CImage::GetPixelAddress](#getpixeladdress)|Ruft die Adresse eines bestimmten Pixels ab.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Ruft die Position der transparenten Farbe in der Farbtabelle ab.|
|[CImage::GetWidth](#getwidth)|Ruft die Breite des aktuellen Bildes in Pixel ab.|
|[CImage::IsDIBSection](#isdibsection)|Bestimmt, ob es sich bei der angehängten Bitmap um einen DIB-Abschnitt handelt.|
|[CImage::IsIndexed](#isindexed)|Gibt an, dass die Farben einer Bitmap einer indizierten Palette zugeordnet sind.|
|[CImage::IsNull](#isnull)|Gibt an, ob eine Quellbitmap aktuell geladen ist.|
|[CImage::IsTransparencySupported](#istransparencysupported)|Gibt an, ob die Anwendung transparente Bitmaps unterstützt.|
|[CImage::Laden](#load)|Lädt ein Bild aus der angegebenen Datei.|
|[CImage::LoadFromResource](#loadfromresource)|Lädt ein Bild aus der angegebenen Ressource.|
|[CImage::MaskBlt](#maskblt)|Kombiniert die Farbdaten für die Quell- und Zielbitmaps mithilfe der angegebenen Masken- und Raster-Operation.|
|[CImage::PlgBlt](#plgblt)|Führt eine Bitblockübertragung von einem Rechteck in einem Quellgerätekontext in ein Parallelogramm in einem Zielgerätekontext durch.|
|[CImage::ReleaseDC](#releasedc)|Gibt den Gerätekontext frei, der mit [CImage::GetDC](#getdc)abgerufen wurde.|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Gibt Ressourcen frei, die von GDI+ verwendet werden. Muss aufgerufen werden, um Ressourcen `CImage` freizugeben, die von einem globalen Objekt erstellt wurden.|
|[CImage::Speichern](#save)|Speichert ein Bild als angegebenen Typ. `Save`Bildoptionen können nicht angegeben werden.|
|[CImage::SetColorTable](#setcolortable)|Legt rote, grüne, blaue RGB-Farbwerte in einem Bereich von Einträgen in der Farbtabelle des DIB-Abschnitts fest.|
|[CImage::SetPixel](#setpixel)|Legt das Pixel an den angegebenen Koordinaten auf die angegebene Farbe fest.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Legt das Pixel an den angegebenen Koordinaten auf die Farbe am angegebenen Index der Palette fest.|
|[CImage::SetPixelRGB](#setpixelrgb)|Legt das Pixel an den angegebenen Koordinaten auf den angegebenen roten, grünen, blauen (RGB)-Wert fest.|
|[CImage::SetTransparentColor](#settransparentcolor)|Legt den Index der Farbe fest, die als transparent behandelt werden soll. Nur eine Farbe in einer Palette kann transparent sein.|
|[CImage::StretchBlt](#stretchblt)|Kopiert eine Bitmap aus einem Quellrechteck in ein Zielrechteck, indem die Bitmap bei Bedarf an die Abmessungen des Zielrechtecks gegliedert oder komprimiert wird.|
|[CImage::TransparentBlt](#transparentblt)|Kopiert eine Bitmap mit transparenter Farbe aus dem Quellgerätekontext in diesen aktuellen Gerätekontext.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CImage::operator HBITMAP](#operator_hbitmap)|Gibt das Windows-Handle `CImage` zurück, das an das Objekt angefügt ist.|

## <a name="remarks"></a>Bemerkungen

`CImage`nimmt Bitmaps, die entweder geräteunabhängige Bitmap-Abschnitte (DIB) sind oder nicht; Sie können jedoch [Create](#create) oder [CImage::Load](#load) nur mit DIB-Abschnitten verwenden. Sie können eine Nicht-DIB-Abschnittsbitmap mit [Attach](#attach)an ein `CImage` `CImage` Objekt anfügen, aber dann können Sie nicht die folgenden Methoden verwenden, die nur DIB-Abschnittsbitmaps unterstützen:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Um zu ermitteln, ob eine angehängte Bitmap ein DIB-Abschnitt ist, rufen Sie [IsDibSection](#isdibsection)auf.

> [!NOTE]
> In Visual Studio .NET 2003 wird in dieser `CImage` Klasse die Anzahl der erstellten Objekte gezählt. Wenn die Anzahl auf 0 `GdiplusShutdown` geht, wird die Funktion automatisch aufgerufen, um Ressourcen freizugeben, die von GDI+ verwendet werden. Dadurch wird `CImage` sichergestellt, dass alle Objekte, die direkt oder `GdiplusShutdown` indirekt `DllMain`von DLLs erstellt werden, immer ordnungsgemäß zerstört werden und nicht von aufgerufen werden.

> [!NOTE]
> Die `CImage` Verwendung globaler Objekte in einer DLL wird nicht empfohlen. Wenn Sie ein globales `CImage` Objekt in einer DLL verwenden müssen, rufen Sie [CImage::ReleaseGDIPlus](#releasegdiplus) auf, um Ressourcen, die von GDI+ verwendet werden, explizit freizugeben.

`CImage`kann nicht in ein neues [CDC](../../mfc/reference/cdc-class.md)ausgewählt werden. `CImage`erstellt einen eigenen HDC für das Bild. Da ein HBITMAP jeweils nur in einem HDC ausgewählt werden kann, kann der HBITMAP, der dem `CImage` zugeordnet ist, nicht in einem anderen HDC ausgewählt werden. Wenn Sie ein CDC benötigen, rufen `CImage` Sie den HDC aus dem ab und geben Sie ihn [an CDC::FromHandle weiter.](../../mfc/reference/cdc-class.md#fromhandle)

## <a name="example"></a>Beispiel

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Wenn Sie `CImage` in einem MFC-Projekt verwenden, beachten Sie, welche Memberfunktionen in Ihrem Projekt einen Zeiger auf ein [CBitmap-Objekt](../../mfc/reference/cbitmap-class.md) erwarten. Wenn Sie mit `CImage` einer solchen Funktion wie [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)verwenden möchten, verwenden Sie `CImage` [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), übergeben Sie es Ihrem HBITMAP, und verwenden Sie die zurückgegebene `CBitmap*`.

## <a name="example"></a>Beispiel

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

Durch `CImage`haben Sie Zugriff auf die eigentlichen Bits eines DIB-Abschnitts. Sie können `CImage` ein Objekt überall dort verwenden, wo Sie zuvor einen Win32 HBITMAP- oder DIB-Abschnitt verwendet haben.

Sie können `CImage` entweder von MFC oder ATL verwendet werden.

> [!NOTE]
> Wenn Sie ein `CImage`Projekt mit `CString` erstellen, müssen Sie definieren, bevor Sie *atlimage.h*einschließen. Wenn Ihr Projekt ATL ohne MFC verwendet, schließen Sie *atlstr.h* ein, bevor Sie *atlimage.h*einschließen. Wenn Ihr Projekt MFC verwendet (oder wenn es sich um ein ATL-Projekt mit MFC-Unterstützung handelt), schließen Sie *afxstr.h ein,* bevor Sie *atlimage.h*einschließen.<br/>
> <br/>
> Ebenso müssen Sie *atlimage.h* einschließen, bevor Sie *atlimpl.cpp*einschließen. Um dies ganz einfach zu erreichen, fügen Sie *atlimage.h* in Ihre *pch.h* (*stdafx.h* in Visual Studio 2017 und früher) ein.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlimage.h

## <a name="cimagealphablend"></a><a name="alphablend"></a>CImage::AlphaBlend

Zeigt Bitmaps mit transparenten oder halbtransparenten Pixeln an.

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

*hDestDC*<br/>
Handle für den Zielgerätekontext.

*xDest*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*yDest*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*bSrcAlpha*<br/>
Ein Alphatransparenzwert, der für die gesamte Quellbitmap verwendet werden soll. Der Standardwert 0xff (255) geht davon aus, dass das Bild undurchsichtig ist und Sie nur Alphawerte pro Pixel verwenden möchten.

*bBlendOp*<br/>
Die Alpha-Verschmelzungsfunktion für Quell- und Zielbitmaps, ein globaler Alphawert, der auf die gesamte Quellbitmap angewendet werden soll, und Formatinformationen für die Quellbitmap. Die Quell- und Ziel-Mischfunktionen sind derzeit auf AC_SRC_OVER beschränkt.

*pointDest*<br/>
Ein Verweis [POINT](/previous-versions/dd162805\(v=vs.85\)) auf eine POINT-Struktur, die die obere linke Ecke des Zielrechtecks in logischen Einheiten identifiziert.

*nDestWidth*<br/>
Die Breite des Zielrechtecks in logischen Einheiten.

*nDestHeight*<br/>
Die Höhe des Zielrechtecks in logischen Einheiten.

*xSrc*<br/>
Die logische x-Koordinate der oberen linken Ecke des Quellrechtecks.

*ySrc*<br/>
Die logische y-Koordinate der oberen linken Ecke des Quellrechtecks.

*nSrcWidth*<br/>
Die Breite des Quellrechtecks in logischen Einheiten.

*nSrcHeight*<br/>
Die Höhe des Quellrechtecks in logischen Einheiten.

*rectDest*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die das Ziel identifiziert.

*rectSrc*<br/>
Ein Verweis `RECT` auf eine Struktur, der die Quelle identifiziert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Alpha-Blend-Bitmaps unterstützen die Farbverschmelzung pro Pixel.

Wenn *bBlendOp* auf den Standardwert AC_SRC_OVER festgelegt ist, wird die Quellbitmap basierend auf den Alphawerten der Quellpixel über der Zielbitmap platziert.

## <a name="cimageattach"></a><a name="attach"></a>CImage::Attach

Fügt *hBitmap* an `CImage` ein Objekt an.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parameter

*hBitmap*<br/>
Ein Handle für einen HBITMAP.

*eOrientation*<br/>
Gibt die Ausrichtung der Bitmap an. Dabei kann es sich um eine der folgenden Methoden handeln:

- DIBOR_DEFAULT Die Ausrichtung der Bitmap wird vom Betriebssystem bestimmt.

- DIBOR_BOTTOMUP Die Zeilen der Bitmap befinden sich in umgekehrter Reihenfolge. Dies bewirkt, dass [CImage::GetBits](#getbits) einen Zeiger am Ende des Bitmappuffers und [CImage::GetPitch](#getpitch) eine negative Zahl zurückgibt.

- DIBOR_TOPDOWN Die Zeilen der Bitmap befinden sich in der oberen bis unteren Reihenfolge. Dies bewirkt, dass [CImage::GetBits](#getbits) einen Zeiger auf das erste Byte des Bitmappuffers und [CImage::GetPitch](#getpitch) eine positive Zahl zurückgibt.

### <a name="remarks"></a>Bemerkungen

Die Bitmap kann entweder eine Nicht-DIB-Abschnittsbitmap oder eine DIB-Abschnittsbitmap sein. Eine Liste der Methoden, die Sie nur mit DIB-Abschnittsbitmaps verwenden können, finden Sie unter [IsDIBSection.](#isdibsection)

## <a name="cimagebitblt"></a><a name="bitblt"></a>CImage::BitBlt

Kopiert eine Bitmap aus dem Quellgerätekontext in diesen aktuellen Gerätekontext.

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

*hDestDC*<br/>
Das Ziel HDC.

*xDest*<br/>
Die logische x-Koordinate der oberen linken Ecke des Zielrechtecks.

*yDest*<br/>
Die logische y-Koordinate der oberen linken Ecke des Zielrechtecks.

*dwROP*<br/>
Der zu durchführende Raster-Vorgang. Raster-Vorgangscodes definieren genau, wie die Bits der Quelle, des Ziels und des Musters (wie durch den aktuell ausgewählten Pinsel definiert) zu dem Ziel kombiniert werden. Eine Liste anderer Raster-Vorgangscodes und deren Beschreibungen finden Sie unter [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) im Windows SDK.

*pointDest*<br/>
Eine [POINT](/previous-versions/dd162805\(v=vs.85\)) POINT-Struktur, die die obere linke Ecke des Zielrechtecks angibt.

*nDestWidth*<br/>
Die Breite des Zielrechtecks in logischen Einheiten.

*nDestHeight*<br/>
Die Höhe des Zielrechtecks in logischen Einheiten.

*xSrc*<br/>
Die logische x-Koordinate der oberen linken Ecke des Quellrechtecks.

*ySrc*<br/>
Die logische y-Koordinate der oberen linken Ecke des Quellrechtecks.

*rectDest*<br/>
Eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die das Zielrechteck angibt.

*pointSrc*<br/>
Eine `POINT` Struktur, die die obere linke Ecke des Quellrechtecks angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) im Windows SDK.

## <a name="cimagecimage"></a><a name="cimage"></a>CImage::CImage

Erstellt ein `CImage`-Objekt.

```
CImage() throw();
```

### <a name="remarks"></a>Bemerkungen

Nachdem Sie das Objekt erstellt haben, rufen Sie [Create](#create), [Load](#load), [LoadFromResource](#loadfromresource)oder [Attach](#attach) auf, um eine Bitmap an das Objekt anzufügen.

**Hinweis** In Visual Studio wird in dieser Klasse `CImage` die Anzahl der erstellten Objekte gezählt. Wenn die Anzahl auf 0 `GdiplusShutdown` geht, wird die Funktion automatisch aufgerufen, um Ressourcen freizugeben, die von GDI+ verwendet werden. Dadurch wird `CImage` sichergestellt, dass alle Objekte, die direkt oder `GdiplusShutdown` indirekt von DLLs erstellt werden, immer ordnungsgemäß zerstört werden und nicht von DllMain aufgerufen werden.

Die `CImage` Verwendung globaler Objekte in einer DLL wird nicht empfohlen. Wenn Sie ein globales `CImage` Objekt in einer DLL verwenden müssen, rufen Sie [CImage::ReleaseGDIPlus](#releasegdiplus) auf, um Ressourcen, die von GDI+ verwendet werden, explizit freizugeben.

## <a name="cimagecreate"></a><a name="create"></a>CImage::Erstellen

Erstellt `CImage` eine Bitmap und fügt `CImage` sie an das zuvor erstellte Objekt an.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parameter

*nWidth*<br/>
Die Breite `CImage` der Bitmap in Pixel.

*nHeight*<br/>
Die Höhe `CImage` der Bitmap in Pixel. Wenn *nHeight* positiv ist, ist die Bitmap ein DIB von unten nach oben und ihr Ursprung ist die linke untere Ecke. Wenn *nHeight* negativ ist, ist die Bitmap ein DIB von oben nach unten und sein Ursprung ist die obere linke Ecke.

*nBPP*<br/>
Die Anzahl der Bits pro Pixel in der Bitmap. Normalerweise 4, 8, 16, 24 oder 32. Kann 1 für monochrome Bitmaps oder Masken sein.

*dwFlags*<br/>
Gibt an, ob das Bitmapobjekt über einen Alphakanal verfügt. Kann eine Kombination aus Null oder mehr der folgenden Werte sein:

- *createAlphaChannel* Kann nur verwendet werden, wenn *nBPP* 32 ist und *eCompression* BI_RGB ist. Wenn angegeben, hat das erstellte Bild einen Alphawert (Transparenz) für jedes Pixel, das im 4. Byte jedes Pixels gespeichert ist (nicht in einem nicht-alpha 32-Bit-Bild verwendet). Dieser Alphakanal wird automatisch beim Aufrufen von [CImage::AlphaBlend](#alphablend)verwendet.

> [!NOTE]
> Bei Aufrufen von [CImage::Draw](#draw)werden Bilder mit einem Alphakanal automatisch alpha mit dem Ziel vermischt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="cimagecreateex"></a><a name="createex"></a>CImage::CreateEx

Erstellt `CImage` eine Bitmap und fügt `CImage` sie an das zuvor erstellte Objekt an.

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

*nWidth*<br/>
Die Breite `CImage` der Bitmap in Pixel.

*nHeight*<br/>
Die Höhe `CImage` der Bitmap in Pixel. Wenn *nHeight* positiv ist, ist die Bitmap ein DIB von unten nach oben und ihr Ursprung ist die linke untere Ecke. Wenn *nHeight* negativ ist, ist die Bitmap ein DIB von oben nach unten und sein Ursprung ist die obere linke Ecke.

*nBPP*<br/>
Die Anzahl der Bits pro Pixel in der Bitmap. Normalerweise 4, 8, 16, 24 oder 32. Kann 1 für monochrome Bitmaps oder Masken sein.

*eCompression*<br/>
Gibt den Komprimierungstyp für eine komprimierte Bottom-up-Bitmap an (TOP-down-DIBs können nicht komprimiert werden). Es kann sich um einen der folgenden Werte handeln:

- BI_RGB Das Format ist unkomprimiert. Die Angabe dieses `CImage::CreateEx` Werts beim `CImage::Create`Aufrufen ist gleichbedeutend mit dem Aufrufen von .

- BI_BITFIELDS Das Format ist unkomprimiert, und die Farbtabelle besteht aus drei DWORD-Farbmasken, die die roten, grünen und blauen Komponenten jedes Pixels angeben. Dies gilt bei Verwendung mit 16- und 32-bpp-Bitmaps.

*pdwBitfields*<br/>
Wird nur verwendet, wenn *eCompression* auf BI_BITFIELDS festgelegt ist, andernfalls muss es NULL sein. Ein Zeiger auf ein Array von drei DWORD-Bitmasken, das angibt, welche Bits jedes Pixels für die roten, grünen und blauen Komponenten der Farbe verwendet werden. Informationen zu Einschränkungen für die Bitfelder finden Sie unter [BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) im Windows SDK.

*dwFlags*<br/>
Gibt an, ob das Bitmapobjekt über einen Alphakanal verfügt. Kann eine Kombination aus Null oder mehr der folgenden Werte sein:

- *createAlphaChannel* Kann nur verwendet werden, wenn *nBPP* 32 ist und *eCompression* BI_RGB ist. Wenn angegeben, hat das erstellte Bild einen Alphawert (Transparenz) für jedes Pixel, das im 4. Byte jedes Pixels gespeichert ist (nicht in einem nicht-alpha 32-Bit-Bild verwendet). Dieser Alphakanal wird automatisch beim Aufrufen von [CImage::AlphaBlend](#alphablend)verwendet.

   > [!NOTE]
   > Bei Aufrufen von [CImage::Draw](#draw)werden Bilder mit einem Alphakanal automatisch alpha mit dem Ziel vermischt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich. Andernfalls FALSE.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine 100x100-Pixel-Bitmap erstellt, mit der jedes Pixel mit 16 Bit kodiert wird. In einem bestimmten 16-Bit-Pixel kodieren die Bits 0-3 die rote Komponente, die Bits 4-7 grün und die Bits 8-11 blau. Die restlichen 4 Bits sind nicht verwendet.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a>CImage::Destroy

Trennt die Bitmap vom `CImage` Objekt und zerstört die Bitmap.

```
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a>CImage::Detach

Trennt eine Bitmap von `CImage` einem Objekt.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle an die Bitmap getrennt, oder NULL, wenn keine Bitmap angefügt ist.

## <a name="cimagedraw"></a><a name="draw"></a>CImage::Draw

Kopiert eine Bitmap aus dem Quellgerätekontext in den aktuellen Gerätekontext.

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

*hDestDC*<br/>
Ein Handle für den Zielgerätekontext.

*xDest*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*yDest*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*nDestWidth*<br/>
Die Breite des Zielrechtecks in logischen Einheiten.

*nDestHeight*<br/>
Die Höhe des Zielrechtecks in logischen Einheiten.

*xSrc*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Quellrechtecks.

*ySrc*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Quellrechtecks.

*nSrcWidth*<br/>
Die Breite des Quellrechtecks in logischen Einheiten.

*nSrcHeight*<br/>
Die Höhe des Quellrechtecks in logischen Einheiten.

*rectDest*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die das Ziel identifiziert.

*rectSrc*<br/>
Ein Verweis `RECT` auf eine Struktur, der die Quelle identifiziert.

*pointDest*<br/>
Ein Verweis [POINT](/previous-versions/dd162805\(v=vs.85\)) auf eine POINT-Struktur, die die obere linke Ecke des Zielrechtecks in logischen Einheiten identifiziert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

`Draw`führt den gleichen Vorgang wie [StretchBlt](#stretchblt)aus, es sei denn, das Bild enthält eine transparente Farbe oder einen Alphakanal. Führt in `Draw` diesem Fall den gleichen Vorgang wie [TransparentBlt](#transparentblt) oder [AlphaBlend](#alphablend) aus.

Für Versionen, die `Draw` kein Quellrechteck angeben, ist das gesamte Quellbild die Standardeinstellung. Für die `Draw` Version, die keine Größe für das Zielrechteck angibt, ist die Größe des Quellbilds die Standardeinstellung, und es tritt kein Dehnen oder Verkleinern auf.

## <a name="cimagegetbits"></a><a name="getbits"></a>CImage::GetBits

Ruft einen Zeiger auf die tatsächlichen Bitwerte eines bestimmten Pixels in einer Bitmap ab.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Bitmappuffer. Wenn es sich bei der Bitmap um einen DIB von unten nach oben handelt, zeigt der Zeiger am Ende des Puffers. Wenn es sich bei der Bitmap um einen DIB von oben nach unten handelt, zeigt der Zeiger auf das erste Byte des Puffers.

### <a name="remarks"></a>Bemerkungen

Mit diesem Zeiger und dem von [GetPitch](#getpitch)zurückgegebenen Wert können Sie einzelne Pixel in einem Bild suchen und ändern.

> [!NOTE]
> Diese Methode unterstützt nur DIB-Abschnittsbitmaps. Folglich greifen Sie auf die `CImage` Pixel eines Objekts auf die gleiche Weise wie die Pixel eines DIB-Abschnitts zu. Der zurückgegebene Zeiger zeigt auf das Pixel an der Position (0, 0).

## <a name="cimagegetbpp"></a><a name="getbpp"></a>CImage::GetBPP

Ruft den Bit-pro-Pixel-Wert ab.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bits pro Pixel.

### <a name="remarks"></a>Bemerkungen

Dieser Wert bestimmt die Anzahl der Bits, die jedes Pixel definieren, und die maximale Anzahl von Farben in der Bitmap.

Die Bits pro Pixel sind in der Regel 1, 4, 8, 16, 24 oder 32. Weitere `biBitCount` Informationen zu diesem Wert finden Sie unter [bitMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) im Windows SDK.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a>CImage::GetColorTable

Ruft rote, grüne, blaue (RGB) Farbwerte aus einem Bereich von Einträgen in der Palette des DIB-Abschnitts ab.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parameter

*iFirstColor*<br/>
Der Farbtabellenindex des ersten abzurufenden Eintrags.

*nFarben*<br/>
Die Anzahl der abzurufenden Farbtabelleneinträge.

*prgbColors*<br/>
Ein Zeiger auf das Array von [RGBQUAD-Strukturen,](/windows/win32/api/wingdi/ns-wingdi-rgbquad) um die Farbtabelleneinträge abzurufen.

## <a name="cimagegetdc"></a><a name="getdc"></a>CImage::GetDC

Ruft den Gerätekontext ab, in dem derzeit das Bild ausgewählt ist.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für einen Gerätekontext.

### <a name="remarks"></a>Bemerkungen

Für jeden `GetDC`Aufruf von benötigen Sie einen nachfolgenden Aufruf von [ReleaseDC](#releasedc).

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage::GetExporterFilterString

Sucht Bildformate, die zum Speichern von Bildern verfügbar sind.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parameter

*strExporteure*<br/>
Ein Verweis auf ein `CSimpleString`-Objekt. Weitere Informationen finden Sie unter **Bemerkungen.**

*aguidFileTypes*<br/>
Ein Array von GUIDs, wobei jedes Element einem der Dateitypen in der Zeichenfolge entspricht. Im Beispiel in *pszAllFilesDescription* unten ist *aguidFileTypes*[0] GUID_NULL und die verbleibenden Arraywerte sind die Bilddateiformate, die vom aktuellen Betriebssystem unterstützt werden.

> [!NOTE]
> Eine vollständige Liste der Konstanten finden Sie unter **Bilddateiformatkonstanten** im Windows SDK.

*pszAllFilesBeschreibung*<br/>
Wenn dieser Parameter nicht NULL ist, verfügt die Filterzeichenfolge über einen zusätzlichen Filter am Anfang der Liste. Dieser Filter hat den aktuellen Wert von *pszAllFilesDescription* für seine Beschreibung und akzeptiert Dateien jeder Erweiterung, die von einem anderen Exporteur in der Liste unterstützt wird.

Beispiel:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Satz von Bitflags, die angeben, welche Dateitypen aus der Liste ausgeschlossen werden sollen. Zulässige Flags sind:

- `excludeGIF`= 0x01 Schließt GIF-Dateien aus.

- `excludeBMP`= 0x02 Schließt BMP-Dateien (Windows Bitmap) aus.

- `excludeEMF`= 0x04 Schließt EMF-Dateien (Enhanced Metafile) aus.

- `excludeWMF`= 0x08 Schließt WMF-Dateien (Windows Metafile) aus.

- `excludeJPEG`= 0x10 Schließt JPEG-Dateien aus.

- `excludePNG`= 0x20 Schließt PNG-Dateien aus.

- `excludeTIFF`= 0x40 Schließt TIFF-Dateien aus.

- `excludeIcon`= 0x80 schließt ICO-Dateien (Windows Icon) aus.

- `excludeOther`= 0x80000000 Schließt alle anderen Dateitypen aus, die oben nicht aufgeführt sind.

- `excludeDefaultLoad`= 0 Für das Laden sind standardmäßig alle Dateitypen enthalten

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Zum Speichern werden diese Dateien standardmäßig ausgeschlossen, da sie in der Regel spezielle Anforderungen haben.

*chSeparator*<br/>
Das Zwischen den Bildformaten verwendete Trennzeichen. Weitere Informationen finden Sie unter **Bemerkungen.**

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Sie können die resultierende Formatzeichenfolge an Ihr MFC [CFileDialog-Objekt](../../mfc/reference/cfiledialog-class.md) übergeben, um die Dateierweiterungen der verfügbaren Bildformate im Dialogfeld Dateispeichern als verfügbar verfügbar zu machen.

Der Parameter *strExporter* hat das Format:

Dateibeschreibung0 \*&#124;.ext0&#124;\*dateidescription1&#124;.ext1&#124;... Dateibeschreibung *n* n \*&#124;.ext *n*&#124;&#124;

wobei '&#124;' das Trennzeichen `chSeparator`ist, das durch angegeben wird. Beispiel:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Verwenden Sie das Standardtrennzeichen '&#124;', wenn `CFileDialog` Sie diese Zeichenfolge an ein MFC-Objekt übergeben. Verwenden Sie das Nulltrennzeichen '''', wenn Sie diese Zeichenfolge an ein gemeinsames Dialogfeld Dateispeichern übergeben.

## <a name="cimagegetheight"></a><a name="getheight"></a>CImage::GetHeight

Ruft die Höhe eines Bildes in Pixel ab.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Höhe eines Bildes in Pixel.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage::GetImporterFilterString

Sucht Bildformate, die zum Laden von Bildern verfügbar sind.

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parameter

*strImporters*<br/>
Ein Verweis auf ein `CSimpleString`-Objekt. Weitere Informationen finden Sie unter **Bemerkungen.**

*aguidFileTypes*<br/>
Ein Array von GUIDs, wobei jedes Element einem der Dateitypen in der Zeichenfolge entspricht. Im Beispiel in *pszAllFilesDescription* unten wird *aguidFileTypes*[0] GUID_NULL mit den verbleibenden Arraywerten sind die Bilddateiformate, die vom aktuellen Betriebssystem unterstützt werden.

> [!NOTE]
> Eine vollständige Liste der Konstanten finden Sie unter **Bilddateiformatkonstanten** im Windows SDK.

*pszAllFilesBeschreibung*<br/>
Wenn dieser Parameter nicht NULL ist, verfügt die Filterzeichenfolge über einen zusätzlichen Filter am Anfang der Liste. Dieser Filter hat den aktuellen Wert von *pszAllFilesDescription* für seine Beschreibung und akzeptiert Dateien jeder Erweiterung, die von einem anderen Exporteur in der Liste unterstützt wird.

Beispiel:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Satz von Bitflags, die angeben, welche Dateitypen aus der Liste ausgeschlossen werden sollen. Zulässige Flags sind:

- `excludeGIF`= 0x01 Schließt GIF-Dateien aus.

- `excludeBMP`= 0x02 Schließt BMP-Dateien (Windows Bitmap) aus.

- `excludeEMF`= 0x04 Schließt EMF-Dateien (Enhanced Metafile) aus.

- `excludeWMF`= 0x08 Schließt WMF-Dateien (Windows Metafile) aus.

- `excludeJPEG`= 0x10 Schließt JPEG-Dateien aus.

- `excludePNG`= 0x20 Schließt PNG-Dateien aus.

- `excludeTIFF`= 0x40 Schließt TIFF-Dateien aus.

- `excludeIcon`= 0x80 schließt ICO-Dateien (Windows Icon) aus.

- `excludeOther`= 0x80000000 Schließt alle anderen Dateitypen aus, die oben nicht aufgeführt sind.

- `excludeDefaultLoad`= 0 Für das Laden sind standardmäßig alle Dateitypen enthalten

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Zum Speichern werden diese Dateien standardmäßig ausgeschlossen, da sie in der Regel spezielle Anforderungen haben.

*chSeparator*<br/>
Das Zwischen den Bildformaten verwendete Trennzeichen. Weitere Informationen finden Sie unter **Bemerkungen.**

### <a name="remarks"></a>Bemerkungen

Sie können die resultierende Formatzeichenfolge an Ihr MFC [CFileDialog-Objekt](../../mfc/reference/cfiledialog-class.md) übergeben, um die Dateierweiterungen der verfügbaren Bildformate im Dialogfeld **Dateiöffnung** verfügbar zu machen.

Der Parameter *strImporter* hat das Format:

Dateibeschreibung0 \*&#124;.ext0&#124;\*dateidescription1&#124;.ext1&#124;... Dateibeschreibung *n* n \*&#124;.ext *n*&#124;&#124;

wobei '&#124;' das Trennzeichen ist, das von *chSeparator*angegeben wird. Beispiel:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Verwenden Sie das Standardtrennzeichen '&#124;', wenn `CFileDialog` Sie diese Zeichenfolge an ein MFC-Objekt übergeben. Verwenden Sie das Nulltrennzeichen '''', wenn Sie diese Zeichenfolge an ein gemeinsames **Dialogfeld Datei** öffnen übergeben.

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage::GetMaxColorTableEntries

Ruft die maximale Anzahl von Einträgen in der Farbtabelle ab.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Einträge in der Farbtabelle.

### <a name="remarks"></a>Bemerkungen

Diese Methode unterstützt nur DIB-Abschnittsbitmaps.

## <a name="cimagegetpitch"></a><a name="getpitch"></a>CImage::GetPitch

Ruft die Tonhöhe eines Bildes ab.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Tonhöhe des Bildes. Wenn der Rückgabewert negativ ist, ist die Bitmap ein DIB von unten nach oben und ihr Ursprung ist die linke untere Ecke. Wenn der Rückgabewert positiv ist, ist die Bitmap ein DIB von oben nach unten und ihr Ursprung ist die obere linke Ecke.

### <a name="remarks"></a>Bemerkungen

Die Tonhöhe ist der Abstand in Bytes zwischen zwei Speicheradressen, die den Anfang einer Bitmaplinie und den Anfang der nächsten Bitmaplinie darstellen. Da die Tonhöhe in Bytes gemessen wird, hilft Ihnen die Tonhöhe eines Bildes, das Pixelformat zu bestimmen. Die Tonhöhe kann auch zusätzlichen Speicher enthalten, der für die Bitmap reserviert ist.

Verwenden `GetPitch` Sie [getBits,](#getbits) um einzelne Pixel eines Bildes zu finden.

> [!NOTE]
> Diese Methode unterstützt nur DIB-Abschnittsbitmaps.

## <a name="cimagegetpixel"></a><a name="getpixel"></a>CImage::GetPixel

Ruft die Farbe des Pixels an der von *x* und *y*angegebenen Position ab.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Die x-Koordinate des Pixels.

*y*<br/>
Die y-Koordinate des Pixels.

### <a name="return-value"></a>Rückgabewert

Der rote, grüne, blaue (RGB) Wert des Pixels. Wenn sich das Pixel außerhalb des aktuellen Zuschneidebereichs befindet, wird der Rückgabewert CLR_INVALID.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage::GetPixelAddress

Ruft die genaue Adresse eines Pixels ab.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Die x-Koordinate des Pixels.

*y*<br/>
Die y-Koordinate des Pixels.

### <a name="remarks"></a>Bemerkungen

Die Adresse wird anhand der Koordinaten eines Pixels, der Tonhöhe der Bitmap und der Bits pro Pixel bestimmt.

Bei Formaten mit weniger als 8 Bit pro Pixel gibt diese Methode die Adresse des Bytes zurück, das das Pixel enthält. Wenn Ihr Bildformat beispielsweise 4 Bit `GetPixelAddress` pro Pixel aufweist, gibt die Adresse des ersten Pixels im Byte zurück, und Sie müssen für 2 Pixel pro Byte berechnen.

> [!NOTE]
> Diese Methode unterstützt nur DIB-Abschnittsbitmaps.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage::GetTransparentColor

Ruft die indizierte Position der transparenten Farbe in der Farbpalette ab.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Index der transparenten Farbe.

## <a name="cimagegetwidth"></a><a name="getwidth"></a>CImage::GetWidth

Ruft die Breite eines Bildes in Pixel ab.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Breite der Bitmap in Pixel.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a>CImage::IsDIBSection

Bestimmt, ob es sich bei der angehängten Bitmap um einen DIB-Abschnitt handelt.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die angehängte Bitmap ein DIB-Abschnitt ist. Andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn es sich bei der Bitmap nicht um `CImage` einen DIB-Abschnitt handelt, können Sie nicht die folgenden Methoden verwenden, die nur DIB-Abschnittsbitmaps unterstützen:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a>CImage::IsIndexed

Bestimmt, ob die Pixel einer Bitmap einer Farbpalette zugeordnet sind.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn indiziert; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt TRUE nur zurück, wenn die Bitmap 8 Bit (256 Farben) oder weniger ist.

> [!NOTE]
> Diese Methode unterstützt nur DIB-Abschnittsbitmaps.

## <a name="cimageisnull"></a><a name="isnull"></a>CImage::IsNull

Bestimmt, ob eine Bitmap aktuell geladen ist.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt TRUE zurück, wenn eine Bitmap derzeit nicht geladen ist. andernfalls FALSE.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage::IsTransparencySupported

Gibt an, ob die Anwendung transparente Bitmaps unterstützt.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die aktuelle Plattform Transparenz unterstützt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn der Rückgabewert ungleich Null ist und Transparenz unterstützt wird, verarbeitet ein Aufruf von [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)oder [Draw](#draw) transparente Farben.

## <a name="cimageload"></a><a name="load"></a>CImage::Laden

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

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Lädt das von *pszFileName* oder *pStream*angegebene Abbild .

Gültige Bildtypen sind BMP, GIF, JPEG, PNG und TIFF.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a>CImage::LoadFromResource

Lädt ein Bild aus einer BITMAP-Ressource.

```
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

*pszResourceName*<br/>
Ein Zeiger auf die Zeichenfolge, die den Namen der Ressource enthält, die das zu ladende Bild enthält.

*nIDResource*<br/>
Die ID der zu ladenden Ressource

### <a name="remarks"></a>Bemerkungen

Die Ressource muss vom Typ BITMAP sein.

## <a name="cimagemaskblt"></a><a name="maskblt"></a>CImage::MaskBlt

Kombiniert die Farbdaten für die Quell- und Zielbitmaps mithilfe der angegebenen Masken- und Raster-Operation.

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

*hDestDC*<br/>
Das Handle für das Modul, dessen ausführbare Datei die Ressource enthält.

*xDest*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*yDest*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*nDestWidth*<br/>
Die Breite des Zielrechtecks und der Quellbitmap in logischen Einheiten.

*nDestHeight*<br/>
Die Höhe des Zielrechtecks und der Quellbitmap in logischen Einheiten.

*xSrc*<br/>
Die logische x-Koordinate der oberen linken Ecke der Quellbitmap.

*ySrc*<br/>
Die logische y-Koordinate der oberen linken Ecke der Quellbitmap.

*hbmMask*<br/>
Behandeln Sie die monochrome Maskenbitmap in Kombination mit der Farbbitmap im Quellgerätekontext.

*xMaske*<br/>
Der horizontale Pixelversatz für die Maskenbitmap, die durch den Parameter *hbmMask* angegeben wird.

*yMask*<br/>
Der vertikale Pixelversatz für die Maskenbitmap, die durch den Parameter *hbmMask* angegeben wird.

*dwROP*<br/>
Gibt sowohl Vordergrund- als auch Hintergrund-Raster-Arbeitscodes an, die von der Methode zum Steuern der Kombination von Quell- und Zieldaten verwendet werden. Der Hintergrund-Raster-Vorgangscode wird im Hochwertbyte des Hochauftragsdieses dieses Werts gespeichert. Der Vordergrund-Raster-Vorgangscode wird im Low-Order-Byte des Hochauftrags dieses Werts gespeichert. Das Wort dieser Position niedriger Ordnung wird ignoriert und sollte Null sein. Eine Erläuterung von Vordergrund und Hintergrund im Kontext `MaskBlt` dieser Methode finden Sie im Windows SDK. Eine Liste der allgemeinen Raster-Vorgangscodes finden `BitBlt` Sie im Windows SDK.

*rectDest*<br/>
Ein Verweis `RECT` auf eine Struktur, der das Ziel identifiziert.

*pointSrc*<br/>
Eine `POINT` Struktur, die die obere linke Ecke des Quellrechtecks angibt.

*pointMaske*<br/>
Eine `POINT` Struktur, die die obere linke Ecke der Maskenbitmap angibt.

*pointDest*<br/>
Ein Verweis `POINT` auf eine Struktur, die die obere linke Ecke des Zielrechtecks in logischen Einheiten identifiziert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Methode gilt nur für Windows NT, Versionen 4.0 und höher.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage::operator HBITMAP

Verwenden Sie diesen Operator, um das `CImage` angefügte Windows GDI-Handle des Objekts abzubekommen. Dieser Operator ist ein Gießoperator, der die direkte Verwendung eines HBITMAP-Objekts unterstützt.

## <a name="cimageplgblt"></a><a name="plgblt"></a>CImage::PlgBlt

Führt eine Bitblockübertragung von einem Rechteck in einem Quellgerätekontext in ein Parallelogramm in einem Zielgerätekontext durch.

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

*hDestDC*<br/>
Ein Handle für den Zielgerätekontext.

*pPoints*<br/>
Ein Zeiger auf ein Array von drei Punkten im logischen Raum, die drei Ecken des Zielparallelogramms identifizieren. Die obere linke Ecke des Quellrechtecks wird dem ersten Punkt in diesem Array, der oberen rechten Ecke dem zweiten Punkt in diesem Array und der unteren linken Ecke dem dritten Punkt zugeordnet. Die untere rechte Ecke des Quellrechtecks wird dem impliziten vierten Punkt im Parallelogramm zugeordnet.

*hbmMask*<br/>
Ein Handle für eine optionale monochrome Bitmap, die zum Maskieren der Farben des Quellrechtecks verwendet wird.

*xSrc*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Quellrechtecks.

*ySrc*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Quellrechtecks.

*nSrcWidth*<br/>
Die Breite des Quellrechtecks in logischen Einheiten.

*nSrcHeight*<br/>
Die Höhe des Quellrechtecks in logischen Einheiten.

*xMaske*<br/>
Die x-Koordinate der oberen linken Ecke der monochromen Bitmap.

*yMask*<br/>
Die y-Koordinate der oberen linken Ecke der monochromen Bitmap.

*rectSrc*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die die Koordinaten des Quellrechtecks angibt.

*pointMaske*<br/>
Eine [POINT](/previous-versions/dd162805\(v=vs.85\)) POINT-Struktur, die die obere linke Ecke der Maskenbitmap angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn *hbmMask* eine gültige monochrome `PlgBit` Bitmap identifiziert, verwendet diese Bitmap, um die Bits von Farbdaten aus dem Quellrechteck zu maskieren.

Diese Methode gilt nur für Windows NT, Versionen 4.0 und höher. Ausführlichere Informationen finden Sie unter [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) im Windows SDK.

## <a name="cimagereleasedc"></a><a name="releasedc"></a>CImage::ReleaseDC

Gibt den Gerätekontext frei.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Bemerkungen

Da jeweils nur eine Bitmap in einem Gerätekontext ausgewählt `ReleaseDC` werden kann, müssen Sie für jeden Aufruf von [GetDC](#getdc)aufrufen.

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage::ReleaseGDIPlus

Gibt Ressourcen frei, die von GDI+ verwendet werden.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode muss aufgerufen werden, um `CImage` Ressourcen freizugeben, die von einem globalen Objekt zugewiesen werden. Siehe [CImage::CImage](#cimage).

## <a name="cimagesave"></a><a name="save"></a>CImage::Speichern

Speichert ein Abbild im angegebenen Stream oder in der angegebenen Datei auf dem Datenträger.

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
Ein Zeiger auf ein COM IStream-Objekt, das die Dateibilddaten enthält.

*pszFileName*<br/>
Ein Zeiger auf den Dateinamen für das Bild.

*guidFileType*<br/>
Der Dateityp, unter dem das Bild gespeichert werden soll. Dabei kann es sich um eine der folgenden Methoden handeln:

- `ImageFormatBMP`Ein unkomprimiertes Bitmapbild.

- `ImageFormatPNG`Ein komprimiertes Bild (Portable Network Graphic, PNG).

- `ImageFormatJPEG`Ein JPEG-komprimiertes Bild.

- `ImageFormatGIF`Ein GIF-komprimiertes Bild.

> [!NOTE]
> Eine vollständige Liste der Konstanten finden Sie unter **Bilddateiformatkonstanten** im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um das Bild mit einem angegebenen Namen und Typ zu speichern. Wenn der Parameter *guidFileType* nicht enthalten ist, wird die Dateierweiterung des Dateinamens verwendet, um das Bildformat zu bestimmen. Wenn keine Erweiterung bereitgestellt wird, wird das Bild im BMP-Format gespeichert.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a>CImage::SetColorTable

Legt die Roten, Grünen, Blauen (RGB) Farbwerte für einen Bereich von Einträgen in der Palette des DIB-Abschnitts fest.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parameter

*iFirstColor*<br/>
Der Farbtabellenindex des ersten festzulegenden Eintrags.

*nFarben*<br/>
Die Anzahl der festzulegenden Farbtabelleneinträge.

*prgbColors*<br/>
Ein Zeiger auf das Array von [RGBQUAD-Strukturen,](/windows/win32/api/wingdi/ns-wingdi-rgbquad) um die Farbtabelleneinträge festzulegen.

### <a name="remarks"></a>Bemerkungen

Diese Methode unterstützt nur DIB-Abschnittsbitmaps.

## <a name="cimagesetpixel"></a><a name="setpixel"></a>CImage::SetPixel

Legt die Farbe eines Pixels an einer bestimmten Position in der Bitmap fest.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Die horizontale Position des festzulegenden Pixels.

*y*<br/>
Die vertikale Position des festzulegenden Pixels.

*Farbe*<br/>
Die Farbe, auf die Sie das Pixel festlegen.

### <a name="remarks"></a>Bemerkungen

Diese Methode schlägt fehl, wenn die Pixelkoordinaten außerhalb des ausgewählten Zuschneidebereichs liegen.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage::SetPixelIndexed

Legt die Pixelfarbe auf die Farbe fest, die sich in *iIndex* in der Farbpalette befindet.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Die horizontale Position des festzulegenden Pixels.

*y*<br/>
Die vertikale Position des festzulegenden Pixels.

*iIndex*<br/>
Der Index einer Farbe in der Farbpalette.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage::SetPixelRGB

Legt das Pixel an den von *x* und *y* angegebenen Positionen auf die Farben *fest,* die durch r , *g*und *b*in einem roten, grünen, blauen (RGB)-Bild angegeben sind.

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Die horizontale Position des festzulegenden Pixels.

*y*<br/>
Die vertikale Position des festzulegenden Pixels.

*R*<br/>
Die Intensität der roten Farbe.

*G*<br/>
Die Intensität der grünen Farbe.

*B*<br/>
Die Intensität der blauen Farbe.

### <a name="remarks"></a>Bemerkungen

Die roten, grünen und blauen Parameter werden jeweils durch eine Zahl zwischen 0 und 255 dargestellt. Wenn Sie alle drei Parameter auf Null setzen, ist die kombinierte resultierende Farbe schwarz. Wenn Sie alle drei Parameter auf 255 festlegen, ist die kombinierte resultierende Farbe weiß.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage::SetTransparentColor

Legt eine Farbe an einer angegebenen indizierten Position als transparent fest.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parameter

*iTransparentColor*<br/>
Der Index der Farbe, die auf transparent festgelegt werden soll, in einer Farbpalette. Wenn -1, wird keine Farbe auf transparent gesetzt.

### <a name="return-value"></a>Rückgabewert

Der Index der Farbe, die zuvor als transparent festgelegt wurde.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a>CImage::StretchBlt

Kopiert eine Bitmap aus dem Quellgerätekontext in diesen aktuellen Gerätekontext.

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

*hDestDC*<br/>
Ein Handle für den Zielgerätekontext.

*xDest*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*yDest*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*nDestWidth*<br/>
Die Breite des Zielrechtecks in logischen Einheiten.

*nDestHeight*<br/>
Die Höhe des Zielrechtecks in logischen Einheiten.

*dwROP*<br/>
Der zu durchführende Raster-Vorgang. Raster-Vorgangscodes definieren genau, wie die Bits der Quelle, des Ziels und des Musters (wie durch den aktuell ausgewählten Pinsel definiert) zu dem Ziel kombiniert werden. Eine Liste anderer Raster-Vorgangscodes und deren Beschreibungen finden Sie unter [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) im Windows SDK.

*rectDest*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die das Ziel identifiziert.

*xSrc*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Quellrechtecks.

*ySrc*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Quellrechtecks.

*nSrcWidth*<br/>
Die Breite des Quellrechtecks in logischen Einheiten.

*nSrcHeight*<br/>
Die Höhe des Quellrechtecks in logischen Einheiten.

*rectSrc*<br/>
Ein Verweis `RECT` auf eine Struktur, der die Quelle identifiziert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) im Windows SDK.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a>CImage::TransparentBlt

Kopiert eine Bitmap aus dem Quellgerätekontext in diesen aktuellen Gerätekontext.

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

*hDestDC*<br/>
Ein Handle für den Zielgerätekontext.

*xDest*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*yDest*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Zielrechtecks.

*nDestWidth*<br/>
Die Breite des Zielrechtecks in logischen Einheiten.

*nDestHeight*<br/>
Die Höhe des Zielrechtecks in logischen Einheiten.

*crTransparent*<br/>
Die Farbe in der Quellbitmap, die als transparent behandelt werden soll. Standardmäßig CLR_INVALID, was angibt, dass die Farbe, die derzeit als transparente Farbe des Bildes festgelegt ist, verwendet werden soll.

*rectDest*<br/>
Ein Verweis auf eine [RECT-Struktur,](/previous-versions/dd162897\(v=vs.85\)) die das Ziel identifiziert.

*xSrc*<br/>
Die x-Koordinate in logischen Einheiten der oberen linken Ecke des Quellrechtecks.

*ySrc*<br/>
Die y-Koordinate in logischen Einheiten der oberen linken Ecke des Quellrechtecks.

*nSrcWidth*<br/>
Die Breite des Quellrechtecks in logischen Einheiten.

*nSrcHeight*<br/>
Die Höhe des Quellrechtecks in logischen Einheiten.

*rectSrc*<br/>
Ein Verweis `RECT` auf eine Struktur, der die Quelle identifiziert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

`TransparentBlt`wird für Quellbitmaps mit 4 Bit pro Pixel und 8 Bit pro Pixel unterstützt. Verwenden Sie [CImage::AlphaBlend,](#alphablend) um 32 Bit-pro-Pixel-Bitmaps mit Transparenz anzugeben.

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

## <a name="see-also"></a>Siehe auch

[MMXSwarm-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[SimpleImage-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Geräteunabhängige Bitmaps](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)<br/>
[Geräteunabhängige Bitmaps](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
