---
title: pow, powf, powl
description: API-Referenz für POW, powf und powl die die Erhöhung in eine Potenz berechnen.
ms.date: 08/31/2020
api_name:
- powl
- pow
- powf
- _o_pow
- _o_powf
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
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: 8fb6679e2b509274b4ea60c410a81b54df866416
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505563"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Berechnet das in *y*angegebene *x* .

## <a name="syntax"></a>Syntax

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
define pow(X, Y) // Requires C11 or higher

double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Basis.

*Teenie*\
Exponent.

## <a name="return-value"></a>Rückgabewert

Gibt den Wert von *x*<sup>*y*</sup>zurück. Zu Überlauf oder Unterlauf wird keine Fehlermeldung ausgegeben.

|Werte von x und y|Rückgabewert von "pow"|
|-----------------------|-------------------------|
|*x* ! = 0,0 und *y* = = 0,0|1|
|*x* = = 0,0 und *y* = = 0,0|1|
|*x* = = 0,0 und *y* < 0|INF|

## <a name="remarks"></a>Bemerkungen

**Pow** erkennt keine ganzzahligen Gleit Komma Werte, die größer als 2<sup>64</sup> sind (z. b. 1.0 E100).

**Pow** verfügt über eine Implementierung, die Streaming SIMD Extensions 2 (SSE2) verwendet. Informationen und Einschränkungen zur Verwendung der SSE2-Implementierung finden Sie unter [_set_SSE2_enable](set-sse2-enable.md).

Da C++ das überladen zulässt, können Sie jede der verschiedenen über Ladungen von **Pow**aufzurufen. Wenn Sie in einem C-Programm diese Funktion nicht mit dem- \<tgmath.h> Makro aufzurufen, nimmt **Pow** immer zwei **`double`** Werte an und gibt einen **`double`** Wert zurück.

Wenn Sie das- \<tgmath.h> `pow()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Die `pow(int, int)`-Überladung ist nicht mehr verfügbar. Wenn Sie diese Überladung verwenden, gibt der Compiler möglicherweise [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md)aus. Um dieses Problem zu vermeiden, wandeln Sie den ersten Parameter in **`double`** , **`float`** oder um **`long double`** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|-|-|-|
|**Pow**, **powf**, **powl**|\<math.h>|\<math.h> oder \<cmath>|
|**Pow** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
