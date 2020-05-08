---
title: exp2, exp2f, exp2l
ms.date: 4/2/2020
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
ms.openlocfilehash: 3a80efab34b45348ca00f09b2fd6e2ea5077fd86
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909624"
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
```

### <a name="parameters"></a>Parameter

*x*<br/>
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

Da C++ das überladen zulässt, können Sie über Ladungen von **exp2** aufzurufen, die **float** -und **long Double** -Typen annehmen und zurückgeben. In einem C-Programm nimmt **exp2** immer einen **Double**-Wert an und gibt ihn zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|C-Header|C++-Header|
|-------------|--------------|------------------|
|**Exp**, **expf**, **Expl**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
