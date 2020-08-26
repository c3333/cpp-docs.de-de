---
title: Bitmap-Funktionen zu Ausgrauen und Dithering
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: 57f163fd36c0f25508d94a84495fcaf1956e277d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837202"
---
# <a name="gray-and-dithered-bitmap-functions"></a>Bitmap-Funktionen zu Ausgrauen und Dithering

**Ausgegraute Bitmap-Funktionen**

MFC enthält zwei Funktionen, die verwendet werden können, um einer Bitmap das Aussehen eines deaktivierten Steuerelements zu verleihen.

![Vergleich von grauen und ursprünglichen Symbolversionen](../../mfc/reference/media/vcgraybitmap.gif "Vergleich von grauen und ursprünglichen Symbolversionen")

|Name|Beschreibung|
|-|-|
|[Afxdrawgraybitmap](#afxdrawgraybitmap)|Zeichnet eine graue Version einer Bitmap.|
|[Afxgetgraybitmap](#afxgetgraybitmap)|Kopiert eine graue Version einer Bitmap.|

**Bitmap-Funktionen mit Dithering**

MFC enthält außerdem zwei Funktionen, mit denen der Hintergrund einer Bitmap durch ein gedithertes Muster ersetzt werden kann.

![Vergleich von geditherten und ursprünglichen Symbolversionen](../../mfc/reference/media/vcditheredbitmap.gif "Vergleich von geditherten und ursprünglichen Symbolversionen")

|Name|Beschreibung|
|-|-|
|[Afxdrawditheredbitmap](#afxdrawditheredbitmap)|Zeichnet eine Bitmap mit gedithertem Hintergrund.|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|Kopiert eine Bitmap mit gedithertem Hintergrund.|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a> Afxdrawgraybitmap

Zeichnet eine graue Version einer Bitmap.

```cpp
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
Zeigt auf den Ziel-DC.

*x*<br/>
Die X-Koordinate des Ziels.

*y*<br/>
Die Y-Koordinate des Ziels.

*rSrc*<br/>
Die Quellbitmap.

*crbackground*<br/>
Die neue Hintergrundfarbe (normalerweise grau, wie etwa COLOR_MENU).

### <a name="remarks"></a>Bemerkungen

Eine mit `AfxDrawGrayBitmap` gezeichnete Bitmap hat das Aussehen eines deaktivierten Steuerelements.

![Vergleich von grauen und ursprünglichen Symbolversionen](../../mfc/reference/media/vcgraybitmap.gif "Vergleich von grauen und ursprünglichen Symbolversionen")

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a> Afxgetgraybitmap

Kopiert eine graue Version einer Bitmap.

```cpp
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Die Quellbitmap.

*pDest*<br/>
Die Zielbitmap.

*crbackground*<br/>
Die neue Hintergrundfarbe (normalerweise grau, wie etwa COLOR_MENU).

### <a name="remarks"></a>Bemerkungen

Eine mit `AfxGetGrayBitmap` kopierte Bitmap hat das Aussehen eines deaktivierten Steuerelements.

![Vergleich von grauen und ursprünglichen Symbolversionen](../../mfc/reference/media/vcgraybitmap.gif "Vergleich von grauen und ursprünglichen Symbolversionen")

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a> Afxdrawditheredbitmap

Zeichnet eine Bitmap und ersetzt Ihren Hintergrund durch ein Dithering-Muster (Checker).

```cpp
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
Zeigt auf den Ziel-DC.

*x*<br/>
Die X-Koordinate des Ziels.

*y*<br/>
Die Y-Koordinate des Ziels.

*rSrc*<br/>
Die Quellbitmap.

*cr1*<br/>
Eine der beiden Dithering-Farben, normalerweise weiß.

*cr2*<br/>
Die andere Dithering-Farbe, normalerweise hellgrau (COLOR_MENU).

### <a name="remarks"></a>Bemerkungen

Die Quell Bitmap wird auf dem Ziel-DC mit einem zweifarbigen, CR1-und *CR2*-Muster (*cr1* und) gezeichnet, das den Hintergrund der Bitmap ersetzt. Der Hintergrund der Quell Bitmap wird als weiße Pixel und alle Pixel definiert, die mit der Farbe des Pixels in der oberen linken Ecke der Bitmap übereinstimmen.

![Vergleich von geditherten und ursprünglichen Symbolversionen](../../mfc/reference/media/vcditheredbitmap.gif "Vergleich von geditherten und ursprünglichen Symbolversionen")

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a> Afxgetditheredbitmap

Kopiert eine Bitmap und ersetzt Ihren Hintergrund durch ein Dithering (Checker)-Muster.

```cpp
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Die Quellbitmap.

*pDest*<br/>
Die Zielbitmap.

*cr1*<br/>
Eine der beiden Dithering-Farben, normalerweise weiß.

*cr2*<br/>
Die andere Dithering-Farbe, normalerweise hellgrau (COLOR_MENU).

### <a name="remarks"></a>Bemerkungen

Die Quell Bitmap wird in die Ziel Bitmap kopiert. dabei wird ein zweifarbiges Muster (*CR1* und *CR2*) durchsucht, das den Hintergrund der Quell Bitmap ersetzt. Der Hintergrund der Quell Bitmap wird als weiße Pixel und alle Pixel definiert, die mit der Farbe des Pixels in der oberen linken Ecke der Bitmap übereinstimmen.

![Vergleich von geditherten und ursprünglichen Symbolversionen](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
