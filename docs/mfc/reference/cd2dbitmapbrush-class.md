---
title: CD2DBitmapBrush-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: e26202392bf4783598aec0dddfea514fce806a8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369303"
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush-Klasse

Ein Wrapper für ID2D1BitmapBrush.

## <a name="syntax"></a>Syntax

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Ist überladen. Erstellt ein CD2DBitmapBrush-Objekt aus einer Datei.|
|[CD2DBitmapBrush::-CD2DBitmapBrush](#dtor)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Bitmap-Pinselobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmapBrush::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DBitmapBrush::Erstellen](#create)|Erstellt einen CD2DBitmapBrush. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::Destroy](#destroy)|Zerstört ein CD2DBitmapBrush-Objekt. (Überschreibt [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DBitmapBrush::Get](#get)|Gibt ID2D1BitmapBrush-Schnittstelle zurück|
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Ruft die Bitmapquelle ab, die dieser Pinsel zum Malen verwendet|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Ruft die Methode ab, mit der der Pinsel die Bereiche, die sich über die Bitmap hinaus erstrecken, horizontal kachelt.|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Ruft die Methode ab, mit der der Pinsel die Bereiche vertikal kachelt, die sich über die Bitmap erstrecken.|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Ruft die Interpolationsmethode ab, die verwendet wird, wenn die Pinselbitmap skaliert oder gedreht wird|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Gibt die Bitmapquelle an, die dieser Pinsel zum Malen verwendet|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Gibt an, wie der Pinsel die Bereiche horizontal kachelt, die sich über seine Bitmap erstrecken.|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Gibt an, wie der Pinsel die Bereiche vertikal kachelt, die sich über seine Bitmap erstrecken|
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Gibt den Interpolationsmodus an, der verwendet wird, wenn die Pinselbitmap skaliert oder gedreht wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Initialisiert das Objekt|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmapBrush::operator ID2D1BitmapBrush*](#operator_id2d1bitmapbrush_star)|Gibt ID2D1BitmapBrush-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Speichert einen Zeiger auf ein CD2DBitmap-Objekt.|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Speichert einen Zeiger auf ein ID2D1BitmapBrush-Objekt.|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Bitmap-Pinseleigenschaften.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a>CD2DBitmapBrush::-CD2DBitmapBrush

Der Destruktor. Wird aufgerufen, wenn ein D2D-Bitmap-Pinselobjekt zerstört wird.

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a>CD2DBitmapBrush::Anfügen

Fügt vorhandene Ressourcenschnittstelle an das Objekt an

```
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Kann nicht NULL sein

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush

Erstellt ein CD2DBitmapBrush-Objekt.

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*pBitmapBrushProperties*<br/>
Ein Zeiger auf die Erweiterungsmodi und den Interpolationsmodus eines Bitmappinsels.

*pBrushProperties*<br/>
Ein Zeiger auf die Deckkraft und Transformation eines Pinsels.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

*uiResID*<br/>
Die Ressourcen-ID-Nummer der Ressource.

*lpszType*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Ressourcentyp enthält.

*sizeDest*<br/>
Zielgröße der Bitmap.

*lpszImagePath*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen der Datei enthält.

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a>CD2DBitmapBrush::CommonInit

Initialisiert das Objekt

```
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Parameter

*pBitmapBrushProperties*<br/>
Ein Zeiger auf die Bitmap-Pinseleigenschaften.

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a>CD2DBitmapBrush::Erstellen

Erstellt einen CD2DBitmapBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a>CD2DBitmapBrush::Destroy

Zerstört ein CD2DBitmapBrush-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a>CD2DBitmapBrush::Detach

Trennen der Ressourcenschnittstelle vom Objekt

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dbitmapbrushget"></a><a name="get"></a>CD2DBitmapBrush::Get

Gibt ID2D1BitmapBrush-Schnittstelle zurück

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1BitmapBrush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a>CD2DBitmapBrush::GetBitmap

Ruft die Bitmapquelle ab, die dieser Pinsel zum Malen verwendet

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf ein CD2DBitmap-Objekt oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX

Ruft die Methode ab, mit der der Pinsel die Bereiche, die sich über die Bitmap hinaus erstrecken, horizontal kachelt.

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der angibt, wie der Pinsel die Bereiche horizontal kachelt, die sich über seine Bitmap erstrecken

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY

Ruft die Methode ab, mit der der Pinsel die Bereiche vertikal kachelt, die sich über die Bitmap erstrecken.

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der angibt, wie der Pinsel die Bereiche vertikal kachelt, die sich über seine Bitmap erstrecken

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode

Ruft die Interpolationsmethode ab, die verwendet wird, wenn die Pinselbitmap skaliert oder gedreht wird

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Rückgabewert

Die Interpolationsmethode, die verwendet wird, wenn die Pinselbitmap skaliert oder gedreht wird

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap

Speichert einen Zeiger auf ein CD2DBitmap-Objekt.

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush

Speichert einen Zeiger auf ein ID2D1BitmapBrush-Objekt.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties

Bitmap-Pinseleigenschaften.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::operator ID2D1BitmapBrush*

Gibt ID2D1BitmapBrush-Schnittstelle zurück

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1BitmapBrush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap

Gibt die Bitmapquelle an, die dieser Pinsel zum Malen verwendet

```
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Parameter

*pBitmap*<br/>
Die bitmap-Quelle, die vom Pinsel verwendet wird

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX

Gibt an, wie der Pinsel die Bereiche horizontal kachelt, die sich über seine Bitmap erstrecken.

```
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Parameter

*extendModeX*<br/>
Ein Wert, der angibt, wie der Pinsel die Bereiche horizontal kachelt, die sich über seine Bitmap erstrecken

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY

Gibt an, wie der Pinsel die Bereiche vertikal kachelt, die sich über seine Bitmap erstrecken

```
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Parameter

*extendModeY*<br/>
Ein Wert, der angibt, wie der Pinsel die Bereiche vertikal kachelt, die sich über seine Bitmap erstrecken

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a>CD2DBitmapBrush::SetInterpolationMode

Gibt den Interpolationsmodus an, der verwendet wird, wenn die Pinselbitmap skaliert oder gedreht wird.

```
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Parameter

*Interpolationmode*<br/>
Der Interpolationsmodus, der verwendet wird, wenn die Pinselbitmap skaliert oder gedreht wird

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
