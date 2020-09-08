---
title: sinh, sinhf, sinhl
description: API-Referenz zum Berechnen des hyperbolischen Sinus eines Gleit Komma Werts.
ms.date: 08/31/2020
api_name:
- sinh
- sinhl
- sinhf
- sinhl
- _o_sinh
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
- sinh
- sinhf
- sinhl
helpviewer_keywords:
- sinh function
- sinhl function
- sinhf function
- calculating hyperbolic sines
- trigonometric functions
- sinhf function
- sinhl function
- hyperbolic functions
ms.openlocfilehash: 6a8c9c4195eab66a46230e7a3baf6194e17c4519
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556176"
---
# <a name="sinh-sinhf-sinhl"></a>sinh, sinhf, sinhl

Berechnet den hyperbolischen Sinus.

## <a name="syntax"></a>Syntax

```C
double sinh(double x);
float sinhf(float x);
long double sinhl(long double x);
#define sinh(x) // Requires C11 or higher

float sinh(float x);  // C++ only
long double sinh(long double x);  // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Winkel im Bogenmaß.

## <a name="return-value"></a>Rückgabewert

Die **sinh** -Funktionen geben den hyperbolischen Sinus von *x*zurück. Wenn das Ergebnis zu groß ist, legt **sinh** standardmäßig **errno** auf **ERANGE** fest und gibt "±**HUGE_VAL**" zurück.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± QNAN,IND|Keine|_DOMAIN|
|&#124;x&#124; 104760e e + 002|OVERFLOW+INEXACT|OVERFLOW|

Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **sinh** aufrufen, die-oder-Werte verwenden und zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm nicht das- \<tgmath.h> Makro verwenden, um diese Funktion aufzurufen, führt **sinh** immer aus und gibt zurück **`double`** .

Wenn Sie das- \<tgmath.h> `sinh()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|-|-|-|
|**sinh**, **Sinhf**, **sinhl**|\<math.h>|\<cmath> oder \<math.h>|
|**sinh ()** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_sinhcosh.c
// This program displays the hyperbolic
// sine and hyperbolic cosine of pi / 2.
// Compile by using: cl /W4 crt_sinhcosh.c

#include <math.h>
#include <stdio.h>

int main( void)
{
   double pi = 3.1415926535;
   double x, y;

   x = pi / 2;
   y = sinh( x );
   printf( "sinh( %f ) = %f\n",x, y );
   y = cosh( x );
   printf( "cosh( %f ) = %f\n",x, y );
}
```

```Output
sinh( 1.570796 ) = 2.301299
cosh( 1.570796 ) = 2.509178
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
