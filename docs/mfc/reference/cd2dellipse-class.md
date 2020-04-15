---
title: CD2DEllipse-Klasse
ms.date: 08/29/2019
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 82ad2fbfb8558486134f85d7ec9bcaa6eb4e7507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369257"
---
# <a name="cd2dellipse-class"></a>CD2DEllipse-Klasse

Ein Wrapper für `D2D1_ELLIPSE`.

## <a name="syntax"></a>Syntax

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Ist überladen. Erstellt ein `CD2DEllipse` Objekt `D2D1_ELLIPSE` aus einem Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dellipsecd2dellipse"></a><a name="cd2dellipse"></a>CD2DEllipse::CD2DEllipse

Erstellt ein CD2DEllipse-Objekt aus dem CD2DRectF-Objekt.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Quellrechteck

*ellipse*<br/>
Quellellipse

*ptCenter*<br/>
Der Mittelpunkt der Ellipse.

*sizeRadius*<br/>
Der X-Radius und der Y-Radius der Ellipse.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
