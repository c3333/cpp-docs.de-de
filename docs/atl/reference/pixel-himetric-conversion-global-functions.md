---
title: Globale Funktionen der Pixel-HIMETRIC-Konvertierung
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: e71dccbccbe43ea7df3b6a7005da138a8e31aeb3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834686"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Globale Funktionen der Pixel-/himetri-Konvertierung

Diese Funktionen bieten Unterstützung für das umstellen in und aus Pixel-und HIMETRIC-Einheiten.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|Name|Beschreibung|
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Konvertiert HIMETRIC-Einheiten (jede Einheit ist 0,01 Millimeter) in Pixel.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Konvertiert Pixel in himetrische Einheiten (jede Einheit ist 0,01 Millimeter).|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a> Atlhimetrictopixel

Konvertiert die Größe eines Objekts von HIMETRIC-Einheiten (à 0,01 Millimeter) in Pixel auf dem Bildschirmgerät.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parameter

*lpsizone HIMETRIC*<br/>
in Ein Zeiger auf die Größe des Objekts in HIMETRIC-Einheiten.

*lpsizone pix*<br/>
vorgenommen Ein Zeiger auf den Speicherort, an dem die Größe des Objekts in Pixel zurückgegeben werden soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a> Atlpixel$ HIMETRIC

Konvertiert die Größe eines Objekts von Pixeln auf dem Bildschirmgerät in HIMETRIC-Einheiten (à 0,01 Millimeter).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parameter

*lpsizone pix*<br/>
in Zeiger auf die Größe des Objekts in Pixel.

*lpsizone HIMETRIC*<br/>
vorgenommen Ein Zeiger auf den Speicherort, an dem die Größe des Objekts in HIMETRIC-Einheiten zurückgegeben werden soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)
