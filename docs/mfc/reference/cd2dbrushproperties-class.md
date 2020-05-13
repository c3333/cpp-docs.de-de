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
ms.openlocfilehash: 2db720fd09c62f8b86baecea9229d946f3892333
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754183"
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

## <a name="requirements"></a>Requirements (Anforderungen)

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

```cpp
void CommonInit();
```

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)
