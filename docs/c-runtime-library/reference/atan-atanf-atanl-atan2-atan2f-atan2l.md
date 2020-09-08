---
title: atan, atanf, atanl, atan2, atan2f, atan2l
description: API-Referenz für atan, atanf, atanl, atan2, atan2f und atan2l; , die den Arkus Tangens eines Gleit Komma Werts berechnen.
ms.date: 08/31/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
- _o_atan2f
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
ms.openlocfilehash: 1f1d33aac86d94ab3731dd5cf5b124af99ccb3f2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555630"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Berechnet den Arkus Tangens **von x** (**Atan**, **atanf**und **atanl**) oder den Arkus Tangens von **y** / **x** (**atan2**, **atan2f**und **atan2l**).

## <a name="syntax"></a>Syntax

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );
#define atan(X) // Requires C11 or higher

float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
#define atan2(Y, X) // Requires C11 or higher

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>Parameter

*x*, *y*\
Alle Zahlen.

## <a name="return-value"></a>Rückgabewert

**Atan** gibt den Arkus Tangens von *x* im Bereich von Bereich-/2 zu adressiert/2 zurück. **atan2** gibt den Arkus Tangens von *y* / *x* im Bereich von Bereich zu adressiert zurück. Wenn *x* 0 ist, gibt **Atan** 0 zurück. Wenn beide Parameter von **atan2** 0 sind, gibt die Funktion 0 zurück. Alle Ergebnisse sind in Bogenmaß.

**atan2** verwendet die Zeichen beider Parameter, um den Quadranten des Rückgabewerts zu bestimmen.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|Keine|**_DOMAIN**|

## <a name="remarks"></a>Hinweise

Die **Atan** -Funktion berechnet den Arkus Tangens (die umgekehrte Tangens Funktion) von *x*. **atan2** berechnet den Arkus Tangens von *y* / *x* ( *Wenn x* gleich 0 ist, gibt **atan2** den Wert 1 zurück, wenn *y* positiv ist, d/2, wenn *y* negativ ist, oder 0, wenn *y* gleich 0 ist.)

Wenn Sie das- \<tgmath.h> `atan()` Makro oder das- `atan2()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

**Atan** verfügt über eine Implementierung, die Streaming SIMD Extensions 2 (SSE2) verwendet. Informationen und Einschränkungen zur Verwendung der SSE2-Implementierung finden Sie unter [_set_SSE2_enable](set-sse2-enable.md).

Da C++ das überladen zulässt, können Sie über Ladungen von **Atan** und **atan2** , die-oder-Argumente annehmen, aufgerufen werden **`float`** **`long double`** . Wenn Sie in einem C-Programm das \<tgmath.h> -Makro verwenden, um diese Funktion aufzurufen, nehmen **Atan** und **atan2** immer **`double`** Argumente an und geben ein zurück **`double`** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|-------------|---------------------|-|
|**Atan**, **atan2**, **atanf**, **atan2f**, **atanl**, **atan2l**|\<math.h>|\<cmath> oder \<math.h>|
|**Atan ()**, **atan2** -Makros | \<tgmath.h> ||

## <a name="example"></a>Beispiel

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
