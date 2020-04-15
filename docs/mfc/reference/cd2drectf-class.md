---
title: CD2DRectF-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 33d3c5f9e795ad6c91b689436e8a3b1b56966dce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369124"
---
# <a name="cd2drectf-class"></a>CD2DRectF-Klasse

Ein Wrapper für `D2D1_RECT_F`.

## <a name="syntax"></a>Syntax

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|Ist überladen. Erstellt ein `CD2DRectF` Objekt `D2D1_RECT_F` aus einem Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|Gibt einen **booleschen** Wert zurück, der angibt, ob ein Ausdruck keine gültigen Daten (NULL) enthält.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRectF::operator CRect](#operator_crect)|Konvertiert `CD2DRectF` in `CRect` ein Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a>CD2DRectF::CD2DRectF

Erstellt ein CD2DRectF-Objekt aus dem CRect-Objekt.

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Quellrechteck

*fLeft*<br/>
Quell-Links-Koordinate

*fTop*<br/>
Quell-Top-Koordinate

*Schreck*<br/>
Quell-Rechte-Koordinate

*fBottom*<br/>
Quell-Bodenkoordinate

## <a name="cd2drectfisnull"></a><a name="isnull"></a>CD2DRectF::IsNull

Gibt einen booleschen Wert zurück, der angibt, ob ein Ausdruck keine gültigen Daten (Null) enthält.

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die oberen, linken, unteren und rechten Werte des Rechtecks alle gleich 0 sind. andernfalls FALSE.

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a>CD2DRectF::operator CRect

Konvertiert CD2DRectF in CRect-Objekt.

```
operator CRect();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert des D2D-Rechtecks.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
