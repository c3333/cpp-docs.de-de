---
title: CD2DGradientBrush-Klasse
ms.date: 03/27/2019
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
ms.openlocfilehash: 861bc32382737bd6482a3d51eb8470bf834e8508
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369220"
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush-Klasse

Die Basisklasse der CD2DLinearGradientBrush- und CD2DRadialGradientBrush-Klassen.

## <a name="syntax"></a>Syntax

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|Erstellt ein CD2DGradientBrush-Objekt.|
|[CD2DGradientBrush::-CD2DGradientBrush](#_dtorcd2dgradientbrush)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Gradientenpinselobjekt zerstört wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGradientBrush::Destroy](#destroy)|Zerstört ein CD2DGradientBrush-Objekt. (Überschreibt [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|Array der D2D1_GRADIENT_STOP Strukturen.|
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|Der Bereich, in dem die Farbinterpolation zwischen den Farbverlaufsstopps durchgeführt wird.|
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|Das Verhalten des Farbverlaufs außerhalb des normalisierten Bereichs [0,1].|
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|Ein Zeiger auf ein Array von D2D1_GRADIENT_STOP Strukturen.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="_dtorcd2dgradientbrush"></a>CD2DGradientBrush::-CD2DGradientBrush

Der Destruktor. Wird aufgerufen, wenn ein D2D-Gradientenpinselobjekt zerstört wird.

```
virtual ~CD2DGradientBrush();
```

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="cd2dgradientbrush"></a>CD2DGradientBrush::CD2DGradientBrush

Erstellt ein CD2DGradientBrush-Objekt.

```
CD2DGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
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

*colorInterpolationGamma*<br/>
Der Bereich, in dem die Farbinterpolation zwischen den Farbverlaufsstopps durchgeführt wird.

*extendMode*<br/>
Das Verhalten des Farbverlaufs außerhalb des normalisierten Bereichs [0,1].

*pBrushProperties*<br/>
Ein Zeiger auf die Deckkraft und Transformation eines Pinsels.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dgradientbrushdestroy"></a><a name="destroy"></a>CD2DGradientBrush::Destroy

Zerstört ein CD2DGradientBrush-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dgradientbrushm_argradientstops"></a><a name="m_argradientstops"></a>CD2DGradientBrush::m_arGradientStops

Array der D2D1_GRADIENT_STOP Strukturen.

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

## <a name="cd2dgradientbrushm_colorinterpolationgamma"></a><a name="m_colorinterpolationgamma"></a>CD2DGradientBrush::m_colorInterpolationGamma

Der Bereich, in dem die Farbinterpolation zwischen den Farbverlaufsstopps durchgeführt wird.

```
D2D1_GAMMA m_colorInterpolationGamma;
```

## <a name="cd2dgradientbrushm_extendmode"></a><a name="m_extendmode"></a>CD2DGradientBrush::m_extendMode

Das Verhalten des Farbverlaufs außerhalb des normalisierten Bereichs [0,1].

```
D2D1_EXTEND_MODE m_extendMode;
```

## <a name="cd2dgradientbrushm_pgradientstops"></a><a name="m_pgradientstops"></a>CD2DGradientBrush::m_pGradientStops

Ein Zeiger auf ein Array von D2D1_GRADIENT_STOP Strukturen.

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
