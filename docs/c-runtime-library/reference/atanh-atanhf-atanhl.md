---
title: atanh, atanhf, atanhl
description: API-Referenz für atanh, atanhf und atanhl; , die den umgekehrten hyperbolischen Tangens eines Gleit Komma Werts berechnen.
ms.date: 08/31/2020
api_name:
- atanhl
- atanhf
- atanh
- _o_atanh
- _o_atanhf
- _o_atanhl
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
- atanhl
- atanhf
- atanh
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
ms.openlocfilehash: c0a8e06963519553144c7e49d26e61dbbde51c21
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555591"
---
# <a name="atanh-atanhf-atanhl"></a>atanh, atanhf, atanhl

Berechnet den umgekehrten hyperbolischen Tangens.

## <a name="syntax"></a>Syntax

```C
double atanh( double x );
float atanhf( float x );
long double atanhl( long double x );
#define atanh(X) // Requires C11 or higher

float atanh( float x );  // C++ only
long double atanh( long double x );  // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **atanh** -Funktionen geben den umgekehrten hyberbolischen Tangens (hyperbolischen Arkus Tangens) von *x*zurück. Wenn *x* größer als 1 oder kleiner als-1 ist, wird **errno** auf **Edom** festgelegt, und das Ergebnis ist ein stilles Nan. Wenn *x* gleich 1 oder-1 ist, wird ein positives oder negatives Unendlichkeits Wert zurückgegeben, und **errno** wird auf **ERANGE**festgelegt.

|Eingabe|SEH-Ausnahme|**Matherr** Distanzieren|
|-----------|-------------------|-------------------------|
|± QNAN,IND|Keine|Keine|
|*X* 1; *x* -1|Keine|Keine|

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **atanh** aufzurufen, die-oder-Werte verwenden und zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, führt **atanh** immer aus und gibt zurück **`double`** .

Wenn Sie das- \<tgmath.h> `atanh()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**atanh**, **atanhf**, **atanhl**|\<math.h>|\<cmath> oder \<math.h>|
|**atanh ()** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_atanh.c
// This program displays the hyperbolic tangent of pi / 4
// and the arc hyperbolic tangent of the result.
//

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = tanh( pi / 4 );
   y = atanh( x );
   printf( "tanh( %f ) = %f\n", pi/4, x );
   printf( "atanh( %f ) = %f\n", x, y );
}
```

```Output
tanh( 0.785398 ) = 0.655794
atanh( 0.655794 ) = 0.785398
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
