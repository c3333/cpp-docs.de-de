---
title: Globale Funktionen der Pixel-HIMETRIC-Konvertierung
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 43a12985f259603a9b67f22f7a7891bf847c0b0f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862918"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Globale Funktionen der Pixel-/himetri-Konvertierung

Diese Funktionen bieten Unterstützung für das umstellen in und aus Pixel-und HIMETRIC-Einheiten.

> [!IMPORTANT]
>  Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[Atlhimetrictopixel](#atlhimetrictopixel)|Konvertiert HIMETRIC-Einheiten (jede Einheit ist 0,01 Millimeter) in Pixel.|
|[Atlpixel$ HIMETRIC](#atlpixeltohimetric)|Konvertiert Pixel in himetrische Einheiten (jede Einheit ist 0,01 Millimeter).|

##  <a name="atlhimetrictopixel"></a>Atlhimetrictopixel

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

##  <a name="atlpixeltohimetric"></a>Atlpixel$ HIMETRIC

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

## <a name="see-also"></a>Weitere Informationen

[Funktionen](../../atl/reference/atl-functions.md)
