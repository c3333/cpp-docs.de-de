---
title: rint, rintf, rintl
description: API-Referenz für rint, rintf und rintl; , die einen Gleit Komma Wert auf die nächste Ganzzahl im Gleit Komma Format Runden.
ms.date: 9/1/2020
api_name:
- rintf
- rintl
- rint
- _o_rint
- _o_rintf
- _o_rintl
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
- rintf
- rintl
- rint
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
ms.openlocfilehash: 1ed1fa279694d3df75db5963e5a571d58299e415
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555344"
---
# <a name="rint-rintf-rintl"></a>rint, rintf, rintl

Rundet einen Gleitkommawert auf die nächste Ganzzahl im Gleitkommaformat.

## <a name="syntax"></a>Syntax

```C
double rint( double x );
float rintf( float x );
long double rintl( long double x );
#define rint(X) // Requires C11 or higher

float rint( float x );  // C++ only
long double rint( long double x );  // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der zu rundende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **rint** -Funktionen geben einen Gleit Komma Wert zurück, der die nächste Ganzzahl in *x*darstellt. Die halbwerte werden entsprechend der aktuellen Einstellung des Gleit Komma-Rundungs Modus gerundet, identisch mit den **nearbyint** -Funktionen. Im Gegensatz zu den **nearbyint** -Funktionen können die **rint** -Funktionen die **FE_INEXACT** -Gleit Komma Ausnahme auslöst, wenn sich das Ergebnis in dem Wert des-Arguments unterscheidet. Es gibt keine Fehlerrückgabe.

|Eingabe|SEH-Ausnahme|**_matherr** Distanzieren|
|-----------|-------------------|--------------------------|
|± ∞, QNAN, IND|Keine|Keine|
|Abbrüche|EXCEPTION_FLT_UNDERFLOW|Keine|

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **rint** aufzurufen, die **`float`** -und-Werte verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, übernimmt **rint** immer und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `rint()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**rint**, **rintf**, **rintl**|\<math.h>|\<cmath>|
|**rint** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_rint.c
// Build with: cl /W3 /Tc crt_rint.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 2.5 and -2.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 2.5;

   printf("rint(%f) is %.0f\n", x, rint (x));
   printf("rint(%f) is %.0f\n", -x, rint (-x));
   printf("rintf(%f) is %.0f\n", y, rintf(y));
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));
}
```

```Output
rint(2.499999) is 2
rint(-2.499999) is -2
rintf(2.800000) is 3
rintf(-2.800000) is -3
rintl(2.500000) is 3
rintl(-2.500000) is -3
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround, lroundf, lroundl, llround, llroundf, llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint](rint-rintf-rintl.md)<br/>
