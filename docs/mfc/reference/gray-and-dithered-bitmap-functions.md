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
ms.openlocfilehash: bbc64aad0d65c0430ad23b96f635be8fe2b396e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357040"
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

```
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

*X*<br/>
Die X-Koordinate des Ziels.

*y*<br/>
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

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a>AfxGetGrayBitmap

Kopiert eine graue Version einer Bitmap.

```
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

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a>AfxDrawDitheredBitmap

Zeichnet eine Bitmap und ersetzt ihren Hintergrund durch ein gezaudertes (Prüfmuster) Muster.

```
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

*X*<br/>
Die X-Koordinate des Ziels.

*y*<br/>
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

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a>AfxGetDitheredBitmap

Kopiert eine Bitmap und ersetzt den Hintergrund durch ein gezaudertes (Prüfmuster) Muster.

```
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

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
