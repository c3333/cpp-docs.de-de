---
title: Pixel-HIMETRIC Konvertierung Globale Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 08c72c0d8f3d061950d6945d9fb412c0a16355da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326143"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Pixel/HIMETRIC Konvertierung Globale Funktionen

Diese Funktionen unterstützen die Konvertierung von und nach Pixel- und HIMETRIC-Einheiten.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Konvertiert HIMETRIC-Einheiten (jede Einheit ist 0,01 Millimeter) in Pixel.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Konvertiert Pixel in HIMETRIC-Einheiten (jede Einheit ist 0,01 Millimeter).|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a>AtlHiMetricToPixel

Konvertiert die Größe eines Objekts von HIMETRIC-Einheiten (à 0,01 Millimeter) in Pixel auf dem Bildschirmgerät.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parameter

*lpSizeInHiMetric*<br/>
[in] Zeiger auf die Größe des Objekts in HIMETRIC-Einheiten.

*lpSizeInPix*<br/>
[out] Zeiger auf die Stelle, an der die Größe des Objekts in Pixel zurückgegeben werden soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a>AtlPixelToHiMetric

Konvertiert die Größe eines Objekts von Pixeln auf dem Bildschirmgerät in HIMETRIC-Einheiten (à 0,01 Millimeter).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parameter

*lpSizeInPix*<br/>
[in] Zeiger auf die Größe des Objekts in Pixel.

*lpSizeInHiMetric*<br/>
[out] Zeiger auf die Stelle, an der die Größe des Objekts in HIMETRIC-Einheiten zurückgegeben werden soll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)
