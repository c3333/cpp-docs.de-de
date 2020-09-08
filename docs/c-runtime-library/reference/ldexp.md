---
title: ldexp, ldexpf, ldexpl
description: API-Referenz für LDE XP, ldexpf und ldexpl; Dadurch wird eine Gleit Komma Zahl mit einer ganzzahligen Potenz von zwei multipliziert.
ms.date: 9/1/2020
api_name:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
- _o_ldexp
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- ldexpf function
- ldexpl function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
ms.openlocfilehash: 6ce6bcbc8adbc62e8d8598b97a6f77e04fee1511
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555448"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp, ldexpf, ldexpl

Multipliziert eine Gleitkommazahl mit einer ganzzahligen Potenz von zwei.

## <a name="syntax"></a>Syntax

```C
double ldexp(
   double x,
   int exp
);
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
#define ldexp(X, INT) // Requires C11 or higher

float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Gleitkommawert.

*Exp*\
Ganzzahlexponent.

## <a name="return-value"></a>Rückgabewert

Die **ldexp** -Funktionen geben bei Erfolg den Wert von *x* \* 2<sup>*Exp*</sup> zurück. Bei einem Überlauf und abhängig vom Vorzeichen von *x*gibt **LDE XP** +/- **HUGE_VAL**; zurück. der **errno** -Wert ist auf **ERANGE**festgelegt.

Weitere Informationen zu **errno** und möglichen Fehlerrückgabe Werten finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **LDE XP** aufzurufen, die- **`float`** oder- **`long double`** Typen verwenden. Wenn Sie in einem C-Programm das \<tgmath.h> -Makro verwenden, um diese Funktion aufzurufen, verwendet **ldebug** immer **`double`** und **`int`** und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `ldexp()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**LDE XP**, **ldexpf**, **ldexpl**|\<math.h>|\<cmath>|
|**LDE XP** -Makro | \<tgmath.h> ||

Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_ldexp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 4.0, y;
   int p = 3;

   y = ldexp( x, p );
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );
}
```

## <a name="output"></a>Output

```Output
4.0 times two to the power of 3 is 32.0
```

## <a name="see-also"></a>Siehe auch

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
