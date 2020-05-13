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
ms.openlocfilehash: a220596b880ee74d5f9ebf683d087156224ee7c5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751476"
---
# <a name="gray-and-dithered-bitmap-functions"></a>Bitmap-Funktionen zu Ausgrauen und Dithering

**Ausgegraute Bitmap-Funktionen**

MFC enthält zwei Funktionen, die verwendet werden können, um einer Bitmap das Aussehen eines deaktivierten Steuerelements zu verleihen.

![Vergleich von grauen und ursprünglichen Symbolversionen](../../mfc/reference/media/vcgraybitmap.gif "Vergleich von grauen und ursprünglichen Symbolversionen")

|||
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|Zeichnet eine graue Version einer Bitmap.|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|Kopiert eine graue Version einer Bitmap.|

**Bitmap-Funktionen mit Dithering**

MFC enthält außerdem zwei Funktionen, mit denen der Hintergrund einer Bitmap durch ein gedithertes Muster ersetzt werden kann.

![Vergleich von geditherten und ursprünglichen Symbolversionen](../../mfc/reference/media/vcditheredbitmap.gif "Vergleich von geditherten und ursprünglichen Symbolversionen")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|Zeichnet eine Bitmap mit gedithertem Hintergrund.|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|Kopiert eine Bitmap mit gedithertem Hintergrund.|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a>AfxDrawGrayBitmap

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

*pDC*<br/>
Zeigt auf den Ziel-DC.

*x*<br/>
Die X-Koordinate des Ziels.

*Y*<br/>
Die Y-Koordinate des Ziels.

*rSrc*<br/>
Die Quellbitmap.

*crBackground*<br/>
Die neue Hintergrundfarbe (normalerweise grau, wie etwa COLOR_MENU).

### <a name="remarks"></a>Bemerkungen

Eine mit `AfxDrawGrayBitmap` gezeichnete Bitmap hat das Aussehen eines deaktivierten Steuerelements.

![Vergleich von grauen und ursprünglichen Symbolversionen](../../mfc/reference/media/vcgraybitmap.gif "Vergleich von grauen und ursprünglichen Symbolversionen")

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a>AfxGetGrayBitmap

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

*crBackground*<br/>
Die neue Hintergrundfarbe (normalerweise grau, wie etwa COLOR_MENU).

### <a name="remarks"></a>Bemerkungen

Eine mit `AfxGetGrayBitmap` kopierte Bitmap hat das Aussehen eines deaktivierten Steuerelements.

![Vergleich von grauen und ursprünglichen Symbolversionen](../../mfc/reference/media/vcgraybitmap.gif "Vergleich von grauen und ursprünglichen Symbolversionen")

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a>AfxDrawDitheredBitmap

Zeichnet eine Bitmap und ersetzt ihren Hintergrund durch ein gezaudertes (Prüfmuster) Muster.

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

*pDC*<br/>
Zeigt auf den Ziel-DC.

*x*<br/>
Die X-Koordinate des Ziels.

*Y*<br/>
Die Y-Koordinate des Ziels.

*rSrc*<br/>
Die Quellbitmap.

*cr1*<br/>
Eine der beiden dither Farben, in der Regel weiß.

*cr2*<br/>
Die andere dither Farbe, in der Regel hellgrau (COLOR_MENU).

### <a name="remarks"></a>Bemerkungen

Die Quell-Bitmap wird auf dem Ziel-DC mit einem zweifarbigen (*cr1* und *cr2*) karierten Muster gezeichnet, das den Hintergrund der Bitmap ersetzt. Der Hintergrund der Quellbitmap ist definiert als seine weißen Pixel und alle Pixel, die der Farbe des Pixels in der oberen linken Ecke der Bitmap entsprechen.

![Vergleich von geditherten und ursprünglichen Symbolversionen](../../mfc/reference/media/vcditheredbitmap.gif "Vergleich von geditherten und ursprünglichen Symbolversionen")

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a>AfxGetDitheredBitmap

Kopiert eine Bitmap und ersetzt den Hintergrund durch ein gezaudertes (Prüfmuster) Muster.

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
Eine der beiden dither Farben, in der Regel weiß.

*cr2*<br/>
Die andere dither Farbe, in der Regel hellgrau (COLOR_MENU).

### <a name="remarks"></a>Bemerkungen

Die Quellbitmap wird mit einem zweifarbigen (*cr1* und *cr2*) karierten Muster, das den Hintergrund der Quellbitmap ersetzt, in die Zielbitmap kopiert. Der Hintergrund der Quellbitmap ist definiert als seine weißen Pixel und alle Pixel, die der Farbe des Pixels in der oberen linken Ecke der Bitmap entsprechen.

![Vergleich von geditherten und ursprünglichen Symbolversionen](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
