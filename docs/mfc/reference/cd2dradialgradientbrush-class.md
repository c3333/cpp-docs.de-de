---
title: CD2DRadialGradientBrush-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: 450314fdbf8441b0cc345430518d083573659add
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750308"
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush-Klasse

Ein Wrapper für ID2D1RadialGradientBrush.

## <a name="syntax"></a>Syntax

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Erstellt ein CD2DLinearGradientBrush-Objekt.|
|[CD2DRadialGradientBrush::-CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Radialgradientenpinselobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRadialGradientBrush::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DRadialGradientBrush::Erstellen](#create)|Erstellt einen CD2DRadialGradientBrush. (Überschreibt [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Zerstört ein CD2DRadialGradientBrush-Objekt. (Überschreibt [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DRadialGradientBrush::Get](#get)|Gibt ID2D1RadialGradientBrush-Schnittstelle zurück|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Ruft die Mitte der Gradientenellipse ab|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Ruft den Offset des Gradientenursprungs relativ zum Mittelpunkt der Gradientenellipse ab|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Ruft den x-Radius der Gradientenellipse ab|
|[CD2DRadialGradientBrush::Getradiusy](#getradiusy)|Ruft den y-Radius der Gradientenellipse ab|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Gibt die Mitte der Farbverlaufsellipse im Koordinatenraum des Pinsels an.|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Gibt den Versatz des Gradientenursprungs relativ zum Mittelpunkt der Gradientenellipse an.|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Gibt den x-Radius der Farbverlaufsellipse im Koordinatenraum des Pinsels an.|
|[CD2DRadialGradientBrush::SetRadiusy](#setradiusy)|Gibt den y-Radius der Farbverlaufsellipse im Koordinatenraum des Pinsels an.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*](#operator_id2d1radialgradientbrush_star)|Gibt ID2D1RadialGradientBrush-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Ein Zeiger auf einen ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Der Mittelpunkt, der Gradientenursprungversetzt und der x-Radius und der y-Radius des Farbverlaufs des Pinsels.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush::-CD2DRadialGradientBrush

Der Destruktor. Wird aufgerufen, wenn ein D2D-Radialgradientenpinselobjekt zerstört wird.

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a>CD2DRadialGradientBrush::Anfügen

Fügt vorhandene Ressourcenschnittstelle an das Objekt an

```cpp
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Kann nicht NULL sein

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush

Erstellt ein CD2DLinearGradientBrush-Objekt.

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
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

*RadialGradientBrushEigenschaften*<br/>
Der Mittelpunkt, der Gradientenursprungversetzt und der x-Radius und der y-Radius des Farbverlaufs des Pinsels.

*colorInterpolationGamma*<br/>
Der Bereich, in dem die Farbinterpolation zwischen den Farbverlaufsstopps durchgeführt wird.

*extendMode*<br/>
Das Verhalten des Farbverlaufs außerhalb des normalisierten Bereichs [0,1].

*pBrushProperties*<br/>
Ein Zeiger auf die Deckkraft und Transformation eines Pinsels.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a>CD2DRadialGradientBrush::Erstellen

Erstellt einen CD2DRadialGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parameter

*pRenderTarget*<br/>
Ein Zeiger auf das Renderziel.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a>CD2DRadialGradientBrush::Destroy

Zerstört ein CD2DRadialGradientBrush-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a>CD2DRadialGradientBrush::Detach

Trennen der Ressourcenschnittstelle vom Objekt

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a>CD2DRadialGradientBrush::Get

Gibt ID2D1RadialGradientBrush-Schnittstelle zurück

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1RadialGradientBrush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter

Ruft die Mitte der Gradientenellipse ab

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Rückgabewert

Die Mitte der Gradientenellipse. Dieser Wert wird im Koordinatenraum des Pinsels ausgedrückt.

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset

Ruft den Offset des Gradientenursprungs relativ zum Mittelpunkt der Gradientenellipse ab

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Rückgabewert

Der Offset des Gradientenursprungs aus der Mitte der Gradientenellipse. Dieser Wert wird im Koordinatenraum des Pinsels ausgedrückt.

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX

Ruft den x-Radius der Gradientenellipse ab

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Rückgabewert

Der x-Radius der Gradientenellipse. Dieser Wert wird im Koordinatenraum des Pinsels ausgedrückt.

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a>CD2DRadialGradientBrush::Getradiusy

Ruft den y-Radius der Gradientenellipse ab

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Rückgabewert

Der y-Radius der Gradientenellipse. Dieser Wert wird im Koordinatenraum des Pinsels ausgedrückt.

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush

Ein Zeiger auf einen ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties

Der Mittelpunkt, der Gradientenursprungversetzt und der x-Radius und der y-Radius des Farbverlaufs des Pinsels.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*

Gibt ID2D1RadialGradientBrush-Schnittstelle zurück

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1RadialGradientBrush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter

Gibt die Mitte der Farbverlaufsellipse im Koordinatenraum des Pinsels an.

```cpp
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Die Mitte der Gradientenellipse im Koordinatenraum des Pinsels

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset

Gibt den Versatz des Gradientenursprungs relativ zum Mittelpunkt der Gradientenellipse an.

```cpp
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Parameter

*gradientOriginOffset*<br/>
Der Offset des Gradientenursprungs aus der Mitte der Gradientenellipse

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX

Gibt den x-Radius der Farbverlaufsellipse im Koordinatenraum des Pinsels an.

```cpp
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Parameter

*Radiusx*<br/>
Der x-Radius der Gradientenellipse. Dieser Wert befindet sich im Koordinatenraum des Pinsels.

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusy

Gibt den y-Radius der Farbverlaufsellipse im Koordinatenraum des Pinsels an.

```cpp
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Parameter

*Radiusy*<br/>
Der y-Radius der Gradientenellipse. Dieser Wert befindet sich im Koordinatenraum des Pinsels.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)
