---
title: remainder, remainderf, remainderl
description: API-Referenz für Rest, restderf und restderl; , die den Rest des Quotienten von zwei Gleit Komma Werten berechnen, die auf den nächstgelegenen integralen Wert gerundet werden.
ms.date: 9/1/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 288d6b0d373a5b318a139b030181c671e2c01048
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507583"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Berechnet den Rest des Quotienten aus zwei Gleitkommawerten, gerundet auf den nächsten ganzzahligen Wert.

## <a name="syntax"></a>Syntax

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
#define remainder(X, Y) // Requires C11 or higher

float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der Zähler.

*Teenie*\
Der Nenner.

## <a name="return-value"></a>Rückgabewert

Der Gleit Komma Rest von *x*  /  *y*. Wenn der Wert von *y* 0,0 ist, gibt **Rest** einen stillen NaN-Wert zurück. Informationen zur Darstellung eines stillen Nan durch die **printf** -Familie finden Sie unter [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Bemerkungen

Die **Rest** -Funktionen berechnen den Gleit Komma Rest *r* von *x*  /  *y* , d. h. *x*  =  *n* \* *y*  +  *r*, wobei *n*die Ganzzahl ist, die dem Wert am nächsten liegt, bis zu *x*  /  *y* , und *n*ist auch immer, wenn &#124; *n*  -  *x*  /  *y* &#124; = 1/2. Wenn *r* = 0 ist, hat *r* das gleiche Vorzeichen wie *x*.

Da C++ das überladen zulässt, können Sie über Ladungen von **Restwerten** aufzurufen, die-oder-Werte verwenden und zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm nicht das- \<tgmath.h> Makro verwenden, um diese Funktion aufzurufen, übernimmt **Rest** immer zwei **`double`** Argumente und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `remainder()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|--------------|---------------------|-|
|**Restwert, Restwert, Restwert** **remainderf** **remainderl**|\<math.h>|\<cmath> oder \<math.h>|
|**restmakro** | \<tgmath.h> ||

Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)\
[ldiv, lldiv](./div.md)\
[imaxdiv](imaxdiv.md)\
["f", "f"](fmod-fmodf.md)\
[remquo, remquof, remquol](remquo-remquof-remquol.md)
