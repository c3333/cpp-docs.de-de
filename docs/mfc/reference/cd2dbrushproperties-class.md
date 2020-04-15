---
title: CD2DBrushProperties-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
ms.openlocfilehash: bf6399d2a245addb7e2e65100d33643fcd54e893
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369289"
---
# <a name="cd2dbrushproperties-class"></a>CD2DBrushProperties-Klasse

Ein Wrapper für `D2D1_BRUSH_PROPERTIES`.

## <a name="syntax"></a>Syntax

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBrushEigenschaften::CD2DBrushEigenschaften](#cd2dbrushproperties)|Ist überladen. Erstellt `CD2D_BRUSH_PROPERTIES` eine Struktur|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DBrushEigenschaften::CommonInit](#commoninit)|Initialisiert das Objekt|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a>CD2DBrushEigenschaften::CD2DBrushEigenschaften

Erstellt eine CD2D_BRUSH_PROPERTIES Struktur

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>Parameter

*_opacity*<br/>
Die Grunddeckkraft des Pinsels. Der Standardwert ist 1,0.

*_transform*<br/>
Die Transformation, die auf den Pinsel angewendet werden soll

## <a name="cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a>CD2DBrushEigenschaften::CommonInit

Initialisiert das Objekt

```
void CommonInit();
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
