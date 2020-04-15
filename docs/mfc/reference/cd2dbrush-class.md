---
title: CD2DBrush-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
ms.openlocfilehash: d03fb6f398e18957f68fc18c78d8a397efc67506
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369277"
---
# <a name="cd2dbrush-class"></a>CD2DBrush-Klasse

Ein Wrapper für ID2D1Brush.

## <a name="syntax"></a>Syntax

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Erstellt ein CD2DBrush-Objekt.|
|[CD2DBrush::-CD2DBrush](#_dtorcd2dbrush)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Pinselobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBrush::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DBrush::Destroy](#destroy)|Zerstört ein CD2DBrush-Objekt. (Überschreibt [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBrush::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DBrush::Get](#get)|Gibt ID2D1Brush-Schnittstelle zurück|
|[CD2DBrush::GetOpacity](#getopacity)|Ruft den Grad der Deckkraft dieses Pinsels ab|
|[CD2DBrush::GetTransform](#gettransform)|Ruft die aktuelle Transformation des Renderziels ab|
|[CD2DBrush::IsValid](#isvalid)|Überprüft die Ressourcengültigkeit (Überschreibt [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DBrush::SetOpacity](#setopacity)|Legt den Grad der Deckkraft dieses Pinsels fest|
|[CD2DBrush::SetTransform](#settransform)|Wendet die angegebene Transformation auf das Renderziel an und ersetzt die vorhandene Transformation. Alle nachfolgenden Zeichnungsvorgänge erfolgen im transformierten Raum|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBrush::operator ID2D1Brush*](#operator_id2d1brush_star)|Gibt ID2D1Brush-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|Speichert einen Zeiger auf ein ID2D1Brush-Objekt.|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Pinseleigenschaften.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a>CD2DBrush::-CD2DBrush

Der Destruktor. Wird aufgerufen, wenn ein D2D-Pinselobjekt zerstört wird.

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a>CD2DBrush::Anfügen

Fügt dem Objekt eine vorhandene Ressourcenschnittstelle an.

```
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Lässt keine NULL-Werte zu.

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a>CD2DBrush::CD2DBrush

Erstellt ein CD2DBrush-Objekt.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*pBrushProperties*<br/>
Ein Zeiger auf die Deckkraft und Transformation eines Pinsels.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a>CD2DBrush::Destroy

Zerstört ein CD2DBrush-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a>CD2DBrush::Detach

Trennt die Ressourcenschnittstelle vom Objekt.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dbrushget"></a><a name="get"></a>CD2DBrush::Get

Gibt ID2D1Brush-Schnittstelle zurück

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Brush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a>CD2DBrush::GetOpacity

Ruft den Grad der Deckkraft dieses Pinsels ab

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert zwischen Null und 1, der die Deckkraft des Pinsels angibt. Dieser Wert ist ein konstanter Multiplikator, der den Alphawert aller pixelgefüllten Pixel linear skaliert. Die Deckkraftwerte werden im Bereich von 0 bis 1 eingespannt, bevor sie multipliziert werden.

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a>CD2DBrush::GetTransform

Ruft die aktuelle Transformation des Renderziels ab

```
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>Parameter

*Verwandeln*<br/>
Wenn diese Zurückgabe zurückgegeben wird, enthält die aktuelle Transformation des Renderziels. Dieser Parameter wird nicht initialisiert übergeben.

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a>CD2DBrush::IsValid

Überprüft die Gültigkeit der Ressource

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource gültig ist; andernfalls FALSE.

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a>CD2DBrush::m_pBrush

Speichert einen Zeiger auf ein ID2D1Brush-Objekt.

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a>CD2DBrush::m_pBrushProperties

Pinseleigenschaften.

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a>CD2DBrush::operator ID2D1Brush*

Gibt ID2D1Brush-Schnittstelle zurück

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Brush-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a>CD2DBrush::SetOpacity

Legt den Grad der Deckkraft dieses Pinsels fest

```
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>Parameter

*Deckkraft*<br/>
Ein Wert zwischen Null und 1, der die Deckkraft des Pinsels angibt. Dieser Wert ist ein konstanter Multiplikator, der den Alphawert aller pixelgefüllten Pixel linear skaliert. Die Deckkraftwerte werden im Bereich von 0 bis 1 eingespannt, bevor sie multipliziert werden.

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a>CD2DBrush::SetTransform

Wendet die angegebene Transformation auf das Renderziel an und ersetzt die vorhandene Transformation. Alle nachfolgenden Zeichnungsvorgänge finden im transformierten Raum statt.

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>Parameter

*Verwandeln*<br/>
Die Transformation, die auf das Renderziel angewendet werden soll

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
