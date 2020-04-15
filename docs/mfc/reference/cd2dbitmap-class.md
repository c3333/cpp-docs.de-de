---
title: CD2DBitmap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
ms.openlocfilehash: ce4fe49e8af85c4b63be31bf10e9f196f85c019f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369319"
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap-Klasse

Ein Wrapper für ID2D1Bitmap.

## <a name="syntax"></a>Syntax

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Ist überladen. Erstellt ein CD2DBitmap-Objekt aus HBITMAP.|
|[CD2DBitmap::-CD2DBitmap](#_dtorcd2dbitmap)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Bitmapobjekt zerstört wird.|

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Ist überladen. Erstellt ein CD2DBitmap-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmap::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Kopiert den angegebenen Bereich aus der angegebenen Bitmap in die aktuelle Bitmap|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Kopiert den angegebenen Bereich aus dem Speicher in die aktuelle Bitmap|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Kopiert den angegebenen Bereich aus dem angegebenen Renderziel in die aktuelle Bitmap|
|[CD2DBitmap::Erstellen](#create)|Erstellt eine CD2DBitmap. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::Destroy](#destroy)|Zerstört ein CD2DBitmap-Objekt. (Überschreibt [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBitmap::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DBitmap::Get](#get)|Gibt ID2D1Bitmap-Schnittstelle zurück|
|[CD2DBitmap::GetDPI](#getdpi)|Geben Sie die Punkte pro Zoll (DPI) der Bitmap zurück|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Ruft das Pixelformat und den Alphamodus der Bitmap ab|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Gibt die Größe der Bitmap in geräteabhängigen Einheiten (Pixel) zurück|
|[CD2DBitmap::GetSize](#getsize)|Gibt die Größe der Bitmap in geräteunabhängigen Pixeln (DIPs) zurück.|
|[CD2DBitmap::IsValid](#isvalid)|Überprüft die Ressourcengültigkeit (Überschreibt [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|Initialisiert das Objekt|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmap::operator ID2D1Bitmap*](#operator_id2d1bitmap_star)|Gibt ID2D1Bitmap-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|TRUE, wenn m_hBmpSrc zerstört werden sollen; andernfalls FALSE.|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Quell-Bitmap-Handle.|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Ressourcentyp.|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Speichert einen Zeiger auf ein ID2D1Bitmap-Objekt.|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Bitmap-Zielgröße.|
|[CD2DBitmap::m_strPath](#m_strpath)|Botmap-Dateipfad.|
|[CD2DBitmap::m_uiResID](#m_uiresid)|Bitmap-Ressourcen-ID.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dbitmapcd2dbitmap"></a><a name="_dtorcd2dbitmap"></a>CD2DBitmap::-CD2DBitmap

Der Destruktor. Wird aufgerufen, wenn ein D2D-Bitmapobjekt zerstört wird.

```
virtual ~CD2DBitmap();
```

## <a name="cd2dbitmapattach"></a><a name="attach"></a>CD2DBitmap::Anfügen

Fügt dem Objekt eine vorhandene Ressourcenschnittstelle an.

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Lässt keine NULL-Werte zu.

## <a name="cd2dbitmapcd2dbitmap"></a><a name="cd2dbitmap"></a>CD2DBitmap::CD2DBitmap

Erstellt ein CD2DBitmap-Objekt aus der Ressource.

```
CD2DBitmap(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszPath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    HBITMAP hbmpSrc,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*uiResID*<br/>
Die Ressourcen-ID-Nummer der Ressource.

*lpszType*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Ressourcentyp enthält.

*sizeDest*<br/>
Zielgröße der Bitmap.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

*lpszPath*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Datei enthält.

*hbmpSrc*<br/>
Handle zur Bitmap.

## <a name="cd2dbitmapcommoninit"></a><a name="commoninit"></a>CD2DBitmap::CommonInit

Initialisiert das Objekt.

```
void CommonInit();
```

## <a name="cd2dbitmapcopyfrombitmap"></a><a name="copyfrombitmap"></a>CD2DBitmap::CopyFromBitmap

Kopiert den angegebenen Bereich aus der angegebenen Bitmap in die aktuelle Bitmap.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parameter

*pBitmap*<br/>
Die Bitmap, aus der kopiert werden soll.

*DestPoint*<br/>
In der aktuellen Bitmap wird die obere linke Ecke des Bereichs kopiert, in den der von srcRect angegebene Bereich eingefügt wird.

*Srcrect*<br/>
Der zu kopierende Bereich der Bitmap.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dbitmapcopyfrommemory"></a><a name="copyfrommemory"></a>CD2DBitmap::CopyFromMemory

Kopiert den angegebenen Bereich aus dem Speicher in die aktuelle Bitmap.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>Parameter

*srcData*<br/>
Die zu kopierenden Daten.

*Pitch*<br/>
Der Schritt oder die Tonhöhe der Quellbitmap, die in srcData gespeichert ist. Der Schritt ist die Byteanzahl einer Scanlinie (eine Pixelzeile im Speicher). Der Schritt kann aus der folgenden Formel \* berechnet werden: Pixelbreite Bytes pro Pixel + Speicherauffüllung.

*Destrect*<br/>
In der aktuellen Bitmap wird die obere linke Ecke des Bereichs kopiert, in den der von srcRect angegebene Bereich eingefügt wird.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dbitmapcopyfromrendertarget"></a><a name="copyfromrendertarget"></a>CD2DBitmap::CopyFromRenderTarget

Kopiert den angegebenen Bereich aus dem angegebenen Renderziel in die aktuelle Bitmap.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Das Renderziel, das die zu kopierende Region enthält.

*DestPoint*<br/>
In der aktuellen Bitmap wird die obere linke Ecke des Bereichs kopiert, in den der von srcRect angegebene Bereich eingefügt wird.

*Srcrect*<br/>
Der zu kopierende Bereich von renderTarget.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dbitmapcreate"></a><a name="create"></a>CD2DBitmap::Erstellen

Erstellt eine CD2DBitmap.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dbitmapdestroy"></a><a name="destroy"></a>CD2DBitmap::Destroy

Zerstört ein CD2DBitmap-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dbitmapdetach"></a><a name="detach"></a>CD2DBitmap::Detach

Trennt die Ressourcenschnittstelle vom Objekt.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dbitmapget"></a><a name="get"></a>CD2DBitmap::Get

Gibt die ID2D1Bitmap-Schnittstelle zurück.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Bitmap-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dbitmapgetdpi"></a><a name="getdpi"></a>CD2DBitmap::GetDPI

Geben Sie die Punkte pro Zoll (DPI) der Bitmap zurück.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>Rückgabewert

Der horizontale und vertikale DPI der Bitmap.

## <a name="cd2dbitmapgetpixelformat"></a><a name="getpixelformat"></a>CD2DBitmap::GetPixelFormat

Ruft das Pixelformat und den Alphamodus der Bitmap ab

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>Rückgabewert

Das Pixelformat und der Alphamodus der Bitmap.

## <a name="cd2dbitmapgetpixelsize"></a><a name="getpixelsize"></a>CD2DBitmap::GetPixelSize

Gibt die Größe der Bitmap in geräteabhängigen Einheiten (Pixel) zurück.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der Bitmap in Pixel.

## <a name="cd2dbitmapgetsize"></a><a name="getsize"></a>CD2DBitmap::GetSize

Gibt die Größe der Bitmap in geräteunabhängigen Pixeln (DIPs) zurück.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der Bitmap in DIPs.

## <a name="cd2dbitmapisvalid"></a><a name="isvalid"></a>CD2DBitmap::IsValid

Überprüft die Gültigkeit der Ressource.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource gültig ist; andernfalls FALSE.

## <a name="cd2dbitmapm_bautodestroyhbmp"></a><a name="m_bautodestroyhbmp"></a>CD2DBitmap::m_bAutoDestroyHBMP

TRUE, wenn m_hBmpSrc zerstört werden sollen; andernfalls FALSE.

```
BOOL m_bAutoDestroyHBMP;
```

## <a name="cd2dbitmapm_hbmpsrc"></a><a name="m_hbmpsrc"></a>CD2DBitmap::m_hBmpSrc

Quell-Bitmap-Handle.

```
HBITMAP m_hBmpSrc;
```

## <a name="cd2dbitmapm_lpsztype"></a><a name="m_lpsztype"></a>CD2DBitmap::m_lpszType

Ressourcentyp.

```
LPCTSTR m_lpszType;
```

## <a name="cd2dbitmapm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmap::m_pBitmap

Speichert einen Zeiger auf ein ID2D1Bitmap-Objekt.

```
ID2D1Bitmap* m_pBitmap;
```

## <a name="cd2dbitmapm_sizedest"></a><a name="m_sizedest"></a>CD2DBitmap::m_sizeDest

Bitmap-Zielgröße.

```
CD2DSizeU m_sizeDest;
```

## <a name="cd2dbitmapm_strpath"></a><a name="m_strpath"></a>CD2DBitmap::m_strPath

Botmap-Dateipfad.

```
CString m_strPath;
```

## <a name="cd2dbitmapm_uiresid"></a><a name="m_uiresid"></a>CD2DBitmap::m_uiResID

Bitmap-Ressourcen-ID.

```
UINT m_uiResID;
```

## <a name="cd2dbitmapoperator-id2d1bitmap"></a><a name="operator_id2d1bitmap_star"></a>CD2DBitmap::operator ID2D1Bitmap*

Gibt ID2D1Bitmap-Schnittstelle zurück

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Bitmap-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
