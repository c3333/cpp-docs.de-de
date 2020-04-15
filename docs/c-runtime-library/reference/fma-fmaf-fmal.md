---
title: fma, fmaf, fmal
ms.date: 4/2/2020
api_name:
- fma
- fmaf
- fmal
- _o_fma
- _o_fmaf
- _o_fmal
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
ms.openlocfilehash: 993ca4d57202b3789929161a964b3e41d48fd98f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346568"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Multipliziert zwei Werte, addiert einen dritten und rundet das Ergebnis, ohne Genauigkeit aufgrund von vorherigen Rundungen einzubüßen.

## <a name="syntax"></a>Syntax

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Der erste zu multiplizierende Wert.

*y*<br/>
Der zweite zu multiplizierende Wert.

*Z*<br/>
Der hinzuzufügende Wert.

## <a name="return-value"></a>Rückgabewert

Gibt `(x * y) + z` zurück. Der Rückgabewert wird dann mit dem aktuellen Rundungsformat gerundet.

Andernfalls wird möglicherweise einer der folgenden Werte zurückgeben:

|Problem|Rückgabewert|
|-----------|------------|
|*x* = INFINITY, *y* = 0 oder<br /><br /> *x* = 0, *y* = INFINITY|NaN|
|*x* oder *y* = exakt - INFINITY, *z* = INFINITY mit dem entgegengesetzten Vorzeichen|NaN|
|*x* oder *y* = NaN|NaN|
|nicht (*x* = 0, *y*= unbestimmt) und *z* = NaN<br /><br /> nicht (*x*=unbestimmt, *y*=0) und *z* = NaN|NaN|
|Überlaufbereichsfehler|HUGE_VAL, HUGE_VALF oder HUGE_VALL|
|Unterlaufbereichsfehler|Richtige Wert nach dem Runden|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Bemerkungen

Da C++ eine Überlastung ermöglicht, können Sie Überladungen von **fma** aufrufen, die **Float-** und **lange** **Doppeltypen** aufnehmen und zurückgeben. In einem C-Programm nimmt und gibt **fma** immer ein **Double**zurück.

Diese Funktion berechnet den Wert mit unendlicher Genauigkeit und rundet das endgültige Ergebnis dann.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fmal**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
