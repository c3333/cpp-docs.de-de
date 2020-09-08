---
title: asin, asinf, asinl
description: API-Referenz für ASIN, asinf und asinl; , die den Arkus Sinus eines Gleit Komma Werts berechnen.
ms.date: 08/31/2020
api_name:
- asinf
- asinl
- asin
- _o_asin
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
ms.openlocfilehash: 7167debcfb605ab05720d9441943439ea9982324
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556657"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Berechnet den Arkussinus.

## <a name="syntax"></a>Syntax

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
#define asin(X) // Requires C11 or higher

float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Wert, dessen Arkussinus berechnet werden soll.

## <a name="return-value"></a>Rückgabewert

Die **ASIN** -Funktion gibt den Arkus Sinus (die umgekehrte Sinusfunktion) von x im Bereich von "Bereich-/2" bis " *x* 2" zurück.

Wenn *x* kleiner als-1 oder größer als 1 ist, gibt **ASIN** standardmäßig einen unbestimmten Wert zurück.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± ∞|**Ungültig**|**_DOMAIN**|
|± **QNAN**, **IND**|Keine|**_DOMAIN**|
|&#124;x&#124;>1|**Ungültig**|**_DOMAIN**|

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **ASIN** mit **`float`** -und-Werten aufzurufen **`long double`** . Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, übernimmt **ASIN** immer und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `asin()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|-------------|---------------------|-|
|**ASIN**, **asinf**, **asinl**|\<math.h>|\<cmath> oder \<math.h>|
|**ASIN ()** -Makro | \<tgmath.h> ||

## <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [acos, acosf, acosl](acos-acosf-acosl.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
