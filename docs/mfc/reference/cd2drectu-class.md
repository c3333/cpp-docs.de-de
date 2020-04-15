---
title: CD2DRectU-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: 26e647ae01a498a6ad8ca2d7c866f33b01910881
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369113"
---
# <a name="cd2drectu-class"></a>CD2DRectU-Klasse

Ein Wrapper für `D2D1_RECT_U`.

## <a name="syntax"></a>Syntax

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|Ist überladen. Erstellt ein `CD2DRectU` Objekt `D2D1_RECT_U` aus einem Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|Gibt einen **booleschen** Wert zurück, der angibt, ob ein Ausdruck keine gültigen Daten (NULL) enthält.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DRectU::operator CRect](#operator_crect)|Konvertiert `CD2DRectU` in `CRect` ein Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a>CD2DRectU::CD2DRectU

Erstellt ein CD2DRectU-Objekt aus dem CRect-Objekt.

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Quellrechteck

*uLeft*<br/>
Quell-Links-Koordinate

*uTop*<br/>
Quell-Top-Koordinate

*uRight*<br/>
Quell-Rechte-Koordinate

*uBottom*<br/>
Quell-Bodenkoordinate

## <a name="cd2drectuisnull"></a><a name="isnull"></a>CD2DRectU::IsNull

Gibt einen booleschen Wert zurück, der angibt, ob ein Ausdruck keine gültigen Daten (Null) enthält.

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die oberen, linken, unteren und rechten Werte des Rechtecks alle gleich 0 sind. andernfalls FALSE.

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a>CD2DRectU::operator CRect

Konvertiert CD2DRectU in CRect-Objekt.

```
operator CRect();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert des D2D-Rechtecks.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
