---
title: CD2DLinearGradientBrush-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: d87cdae5c24eae391be8db2fcdd04f91d592e427
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753154"
---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush-Klasse

Ein Wrapper für ID2D1LinearGradientBrush.

## <a name="syntax"></a>Syntax

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Erstellt ein CD2DLinearGradientBrush-Objekt.|
|[CD2DLinearGradientBrush::-CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Der Destruktor. Wird aufgerufen, wenn ein lineares D2D-Gradientenpinselobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DLinearGradientBrush::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DLinearGradientBrush::Erstellen](#create)|Erstellt einen CD2DLinearGradientBrush. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLinearGradientBrush::Destroy](#destroy)|Zerstört ein CD2DLinearGradientBrush-Objekt. (Überschreibt [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DLinearGradientBrush::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DLinearGradientBrush::Get](#get)|Gibt ID2D1LinearGradientBrush-Schnittstelle zurück|
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Ruft die Endkoordinaten des linearen Farbverlaufs ab|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Ruft die Startkoordinaten des linearen Farbverlaufs ab|
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Legt die Endkoordinaten des linearen Farbverlaufs im Koordinatenraum des Pinsels fest|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Legt die Startkoordinaten des linearen Farbverlaufs im Koordinatenraum des Pinsels fest|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush*](#operator_id2d1lineargradientbrush_star)|Gibt ID2D1LinearGradientBrush-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Der Anfangs- und Endpunkt des Farbverlaufs.|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Ein Zeiger auf einen ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush::-CD2DLinearGradientBrush

Der Destruktor. Wird aufgerufen, wenn ein lineares D2D-Gradientenpinselobjekt zerstört wird.

```
virtual ~CD2DLinearGradientBrush();
```

## <a name="cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2DLinearGradientBrush::Anfügen

Fügt vorhandene Ressourcenschnittstelle an das Objekt an

```cpp
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Kann nicht NULL sein

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush

Erstellt ein CD2DLinearGradientBrush-Objekt.

```
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*Gradientstops*<br/>
Ein Zeiger auf ein Array von D2D1_GRADIENT_STOP Strukturen.

*gradientStopsCount*<br/>
Ein Wert größer oder gleich 1, der die Anzahl der Verlaufsstopps im array gradientStops angibt.

*LinearGradientBrushProperties*<br/>
Der Anfangs- und Endpunkt des Farbverlaufs.

*colorInterpolationGamma*<br/>
Der Bereich, in dem die Farbinterpolation zwischen den Farbverlaufsstopps durchgeführt wird.

*extendMode*<br/>
Das Verhalten des Farbverlaufs außerhalb des normalisierten Bereichs [0,1].

*pBrushProperties*<br/>
Ein Zeiger auf die Deckkraft und Transformation eines Pinsels.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2DLinearGradientBrush::Erstellen

Erstellt einen CD2DLinearGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2DLinearGradientBrush::Destroy

Zerstört ein CD2DLinearGradientBrush-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2DLinearGradientBrush::Detach

Trennen der Ressourcenschnittstelle vom Objekt

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dlineargradientbrushget"></a><a name="get"></a>CD2DLinearGradientBrush::Get

Gibt ID2D1LinearGradientBrush-Schnittstelle zurück

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1LinearGradientBrush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint

Ruft die Endkoordinaten des linearen Farbverlaufs ab

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Rückgabewert

Die endende zweidimensionale Koordinaten des linearen Farbverlaufs im Koordinatenraum des Pinsels

## <a name="cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint

Ruft die Startkoordinaten des linearen Farbverlaufs ab

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Rückgabewert

Die beginnenden zweidimensionalen Koordinaten des linearen Farbverlaufs im Koordinatenraum des Pinsels

## <a name="cd2dlineargradientbrushm_lineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties

Der Anfangs- und Endpunkt des Farbverlaufs.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

## <a name="cd2dlineargradientbrushm_plineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush

Ein Zeiger auf einen ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

## <a name="cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush*

Gibt ID2D1LinearGradientBrush-Schnittstelle zurück

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1LinearGradientBrush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint

Legt die Endkoordinaten des linearen Farbverlaufs im Koordinatenraum des Pinsels fest

```cpp
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Die endende zweidimensionale Koordinaten des linearen Farbverlaufs im Koordinatenraum des Pinsels

## <a name="cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint

Legt die Startkoordinaten des linearen Farbverlaufs im Koordinatenraum des Pinsels fest

```cpp
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Die beginnenden zweidimensionalen Koordinaten des linearen Farbverlaufs im Koordinatenraum des Pinsels

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)
