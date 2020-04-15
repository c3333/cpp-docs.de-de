---
title: CD2DPointF-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: 5d66c31289f9e17df99df4681cff1d5cf6a0ec86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369158"
---
# <a name="cd2dpointf-class"></a>CD2DPointF-Klasse

Ein Wrapper für `D2D1_POINT_2F`.

## <a name="syntax"></a>Syntax

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Ist überladen. Erstellt ein `CD2DPointF` Objekt `D2D1_POINT_2F` aus einem Objekt.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DPointF::operator CPoint](#operator_cpoint)|Konvertiert `CD2DPointF` in `CPoint` ein Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dpointfcd2dpointf"></a><a name="cd2dpointf"></a>CD2DPointF::CD2DPointF

Erstellt ein CD2DPointF-Objekt aus dem CPoint-Objekt.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Quellpunkt

*Fx*<br/>
Quelle X

*Fy*<br/>
Quelle Y

## <a name="cd2dpointfoperator-cpoint"></a><a name="operator_cpoint"></a>CD2DPointF::operator CPoint

Konvertiert CD2DPointF in CPoint-Objekt.

```
operator CPoint();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert des D2D-Punkts.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
