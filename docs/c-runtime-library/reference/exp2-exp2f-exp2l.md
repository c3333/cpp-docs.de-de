---
title: exp2, exp2f, exp2l
description: API-Verweis für exp2 (), exp2f () und exp2l (), deren Compute 2 auf den angegebenen Wert aufgestuft wird.
ms.date: 9/1/2020
api_name:
- exp2
- exp2f
- exp2l
- _o_exp2
- _o_exp2f
- _o_exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: 518525a38ef575583fde3b7732561f2fa553dd18
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556618"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Berechnet 2 bis zum angegebenen Wert.

## <a name="syntax"></a>Syntax

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
#define exp2(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der Wert des Exponenten.

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung wird der Basis-2-Exponent von *x*zurückgegeben, d. h. 2<sup>x</sup>. Andernfalls wird einer der folgenden Werte zurückgegeben:

|Problem|Rückgabewert|
|-----------|------------|
|*x* = ± 0|1|
|*x* =-unendlich|+0|
|*x* = + unendlich|+INFINITY|
|*x* = Nan|NaN|
|Überlaufbereichsfehler|+HUGE_VAL, +HUGE_VALF, oder +HUGE_VALL|
|Unterlaufbereichsfehler|Korrektes Ergebnis nach dem runden|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **exp2** aufzurufen, die **`float`** -und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das- \<tgmath.h> Makro zum aufruft dieser Funktion nicht verwenden, verwendet **exp2** immer, und gibt **`double`** es zurück, es sei denn, Sie verwenden das-Makro in <tgmath. h->.

Wenn Sie das- \<tgmath.h> `exp2()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**exp2**, **expf2**, **expl2**|\<math.h>|\<cmath>|
|**exp2** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
