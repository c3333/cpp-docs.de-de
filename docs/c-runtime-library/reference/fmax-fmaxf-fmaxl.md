---
title: fmax, fmaxf, fmaxl
description: API-Referenz für "f Max", "f maxf" und "smaxl;" , der die größere von zwei numerischen Werten bestimmt.
ms.date: 9/1/2020
api_name:
- fmax
- fmaxf
- fmaxl
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 4f38db64b30598e7cfb4eb4d0f57dccf257dabc5
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556683"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Bestimmen Sie den größeren von zwei angegebenen numerischen Werten.

## <a name="syntax"></a>Syntax

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);

#define fmax(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der erste zu vergleichende Wert.

*Teenie*\
Der zweite zu vergleichende Wert.

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung wird der größere von *x* oder *y*zurückgegeben. Der zurückgegebene Wert ist genau und erfordert keinerlei Rundung.

Andernfalls wird möglicherweise einer der folgenden Werte zurückgeben:

|Problem|Rückgabewert|
|-----------|------------|
|*x* = Nan|*y*|
|*y* = Nan|*x*|
|*x* und *y* = Nan|NaN|

Diese Funktion verwendet nicht die in [_matherr](matherr.md) angegebenen Fehler.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von Fmax aufzurufen, die- `float` und-Typen verwenden und zurückgeben `long double` . Wenn Sie in einem C-Programm nicht das- \<tgmath.h> Makro verwenden, um diese Funktion aufzurufen, `fmax` nimmt immer einen Double-Wert an und gibt ihn zurück.

Wenn Sie das- \<tgmath.h> `fmax()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|" **f**" **, "f"**, "f", " **f** "|\<math.h>|\<cmath> oder \<math.h>|
|**mamax** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
