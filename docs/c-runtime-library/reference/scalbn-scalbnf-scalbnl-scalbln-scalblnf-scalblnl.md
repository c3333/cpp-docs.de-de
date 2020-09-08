---
title: scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl
description: API-Referenz für scalbn, scalbnf, scalbnl, scalbln, scalblnf und scalblnl; Dadurch wird eine Gleit Komma Zahl mit einer ganzzahligen Potenz von multipliziert `FLT_RADIX` .
ms.date: 9/1/2020
api_name:
- scalblnl
- scalbnl
- scalbnf
- scalblnf
- scalbn
- scalbln
- _o_scalbln
- _o_scalblnf
- _o_scalblnl
- _o_scalbn
- _o_scalbnf
- _o_scalbnl
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
- scalblnf
- scalbnl
- scalblnl
- scalbln
- scalbn
- scalbnf
helpviewer_keywords:
- scalbn function
- scalbln function
- scalblnl function
- scalbnl function
- scalbnf function
- scalblnf function
ms.assetid: df2f1543-8e39-4af4-a5cf-29307e64807d
ms.openlocfilehash: 1a01811e5fcfb28c0557e0232d76649c867748b1
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556670"
---
# <a name="scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl"></a>scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl

Multipliziert eine Gleitkommazahl mit einer ganzzahligen Potenz von FLT_RADIX.

## <a name="syntax"></a>Syntax

```C
double scalbn(
   double x,
   int exp
);
float scalbn(
   float x,
   int exp
);  // C++ only
long double scalbn(
   long double x,
   int exp
);  // C++ only
float scalbnf(
   float x,
   int exp
);
long double scalbnl(
   long double x,
   int exp
);

#define scalbn(X, INT) // Requires C11 or higher

double scalbln(
   double x,
   long exp
);

float scalblnf(
   float x,
   long exp
);
long double scalblnl(
   long double x,
   long exp
);

#define scalbln(X, LONG) // Requires C11 or higher

float scalbln(
   float x,
   long exp
);  // C++ only
long double scalbln(
   long double x,
   long exp
);  // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Gleitkommawert.

*Exp*\
Ganzzahlexponent.

## <a name="return-value"></a>Rückgabewert

Die **scalbn** -Funktionen geben den Wert von *x* \* **FLT_RADIX**<sup>Exp</sup> zurück, wenn erfolgreich. Bei einem Überlauf (abhängig vom Vorzeichen von *x*) gibt **scalbn** +/- **HUGE_VAL**; zurück. der **errno** -Wert ist auf **ERANGE**festgelegt.

Weitere Informationen zu **errno** und möglichen Fehlerrückgabe Werten finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

**FLT_RADIX** ist in als System eigenes Gleit Komma Basis definiert \<float.h> ; in binären Systemen hat es den Wert 2, und **scalbn** entspricht [LDE XP](ldexp.md).

Da C++ das überladen zulässt, können Sie über Ladungen von **scalbn** und **scalbln** aufzurufen, die-oder-Typen verwenden und zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm das \<tgmath.h> -Makro nicht zum aufruft dieser Funktion verwenden, verwendet **scalbn** immer **`double`** und und **`int`** gibt einen zurück **`double`** , und **scalbln** übernimmt immer **`double`** und und **`long`** gibt eine zurück **`double`** .

Wenn Sie das-Makro oder das-Makro verwenden \<tgmath.h> `scalbn()` `scalbln` , bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**scalbn**, **scalbnf**, **scalbnl**, **scalbln**, **scalblnf**, **scalblnl**|\<math.h>|\<cmath>|
|**scalbn ()-oder scalbln** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_scalbn.c
// Compile using: cl /W4 crt_scalbn.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 6.4, y;
   int p = 3;

   y = scalbn( x, p );
   printf( "%2.1f times FLT_RADIX to the power of %d is %2.1f\n", x, p, y );
}
```

### <a name="output"></a>Output

```Output
6.4 times FLT_RADIX to the power of 3 is 51.2
```

## <a name="see-also"></a>Siehe auch

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
