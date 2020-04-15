---
title: CD2DSolidColorBrush-Klasse
ms.date: 03/27/2019
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
ms.openlocfilehash: 5aa3d7688046b0c1b04983f2d27fe5579dd7c680
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369059"
---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush-Klasse

Ein Wrapper für ID2D1SolidColorBrush.

## <a name="syntax"></a>Syntax

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DsolidColorBrush::CD2DsolidColorBrush](#cd2dsolidcolorbrush)|Ist überladen. Erstellt ein CD2DSolidColorBrush-Objekt.|
|[CD2DsolidColorBrush::-CD2DsolidColorBrush](#_dtorcd2dsolidcolorbrush)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Volumenkörper-Pinselobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DSolidColorBrush::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DSolidColorBrush::Erstellen](#create)|Erstellt einen CD2DSolidColorBrush. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DSolidColorBrush::Destroy](#destroy)|Zerstört ein CD2DSolidColorBrush-Objekt. (Überschreibt [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DSolidColorBrush::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DSolidColorBrush::Get](#get)|Gibt ID2D1SolidColorBrush-Schnittstelle zurück|
|[CD2DSolidColorBrush::GetColor](#getcolor)|Ruft die Farbe des Einfarbigen Pinsels ab|
|[CD2DSolidColorBrush::SetColor](#setcolor)|Gibt die Farbe dieses Einfarbigen Pinsels an|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush*](#operator_id2d1solidcolorbrush_star)|Gibt ID2D1SolidColorBrush-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Pinsel Volltonfarbe.|
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Speichert einen Zeiger auf ein ID2D1SolidColorBrush-Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a>CD2DsolidColorBrush::-CD2DsolidColorBrush

Der Destruktor. Wird aufgerufen, wenn ein D2D-Volumenkörper-Pinselobjekt zerstört wird.

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a>CD2DSolidColorBrush::Anfügen

Fügt vorhandene Ressourcenschnittstelle an das Objekt an

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Kann nicht NULL sein

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a>CD2DsolidColorBrush::CD2DsolidColorBrush

Erstellt ein CD2DSolidColorBrush-Objekt.

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*Farbe*<br/>
Die roten, grünen, blauen und Alphawerte der Pinselfarbe.

*pBrushProperties*<br/>
Ein Zeiger auf die Deckkraft und Transformation eines Pinsels.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

*nAlpha*<br/>
Die Deckkraft der Farbe des Pinsels.

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a>CD2DSolidColorBrush::Erstellen

Erstellt einen CD2DSolidColorBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a>CD2DSolidColorBrush::Destroy

Zerstört ein CD2DSolidColorBrush-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a>CD2DSolidColorBrush::Detach

Trennen der Ressourcenschnittstelle vom Objekt

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a>CD2DSolidColorBrush::Get

Gibt ID2D1SolidColorBrush-Schnittstelle zurück

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1SolidColorBrush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a>CD2DSolidColorBrush::GetColor

Ruft die Farbe des Einfarbigen Pinsels ab

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die Farbe dieses einfarbigen Pinsels

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a>CD2DSolidColorBrush::m_colorSolid

Pinsel Volltonfarbe.

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a>CD2DSolidColorBrush::m_pSolidColorBrush

Speichert einen Zeiger auf ein ID2D1SolidColorBrush-Objekt.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a>CD2DSolidColorBrush::operator ID2D1SolidColorBrush*

Gibt ID2D1SolidColorBrush-Schnittstelle zurück

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1SolidColorBrush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a>CD2DSolidColorBrush::SetColor

Gibt die Farbe dieses Einfarbigen Pinsels an

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
Die Farbe dieses einfarbigen Pinsels

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
