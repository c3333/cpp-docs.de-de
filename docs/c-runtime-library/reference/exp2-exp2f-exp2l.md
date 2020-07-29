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
ms.openlocfilehash: d2eb3f6d27e943110c5e82968d4fee949644601f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234158"
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

## <a name="remarks"></a>Bemerkungen

Da C++ das überladen zulässt, können Sie über Ladungen von **exp2** aufzurufen, die **`float`** -und-Typen verwenden und zurückgeben **`long double`** . In einem C-Programm übernimmt **exp2** immer und gibt einen zurück **`double`** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**Exp**, **expf**, **Expl**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
