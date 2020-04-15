---
title: CD2DSizeF-Klasse
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: be050f98855e5af794166e1f86962111a23bfa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369069"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF-Klasse

Ein Wrapper für D2D1_SIZE_F.

## <a name="syntax"></a>Syntax

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Ist überladen. Erstellt ein `CD2DSizeF` Objekt `D2D1_SIZE_F` aus einem Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|Gibt einen **booleschen** Wert zurück, der angibt, ob ein Ausdruck keine gültigen Daten (NULL) enthält.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DSizeF::operator CSize](#operator_csize)|Konvertiert `CD2DSizeF` in `CSize` ein Objekt.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dsizefcd2dsizef"></a><a name="cd2dsizef"></a>CD2DSizeF::CD2DSizeF

Erstellt ein CD2DSizeF-Objekt aus dem CSize-Objekt.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Parameter

*Größe*<br/>
Quellgröße

*Cx*<br/>
Quellbreite

*Cy*<br/>
Quellhöhe

## <a name="cd2dsizefisnull"></a><a name="isnull"></a>CD2DSizeF::IsNull

Gibt einen booleschen Wert zurück, der angibt, ob ein Ausdruck keine gültigen Daten (Null) enthält.

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Breite und Höhe leer sind; andernfalls FALSE.

## <a name="cd2dsizefoperator-csize"></a><a name="operator_csize"></a>CD2DSizeF::operator CSize

Konvertiert CD2DSizeF in CSize-Objekt.

```
operator CSize();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert der D2D-Größe.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
