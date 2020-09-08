---
title: fdim, fdimf, fdiml
description: API-Referenz für "f", "f dimf" und "f" , der den positiven Unterschied zwischen zwei Werten bestimmt.
ms.date: 9/1/2020
api_name:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
ms.openlocfilehash: 406fc5cfe543aa0865760df9ff780c62e78510fc
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554785"
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Bestimmt den positiven Unterschied zwischen den ersten und zweiten Werten.

## <a name="syntax"></a>Syntax

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);

#define fdim(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der erste Wert.

*Teenie*\
Der zweite Wert.

## <a name="return-value"></a>Rückgabewert

Gibt den positiven Unterschied zwischen *x* und *y*zurück:

|Rückgabewert|Szenario|
|------------------|--------------|
|x-y|wenn x > y|
|0|wenn x <= y|

Andernfalls wird einer der folgenden Fehler zurückgeben:

|Problem|Rückgabewert|
|-----------|------------|
|Überlaufbereichsfehler|+HUGE_VAL, +HUGE_VALF, oder +HUGE_VALL|
|Unterlaufbereichsfehler|Richtiger Wert (nach dem Runden)|
|*x* oder *y* ist NaN|NaN|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **fdim** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das- \<tgmath.h> Makro nicht zum aufruft dieser Funktion verwenden, verwendet **fdim** immer und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `fdim()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Mit Ausnahme der Nan-Behandlung entspricht diese Funktion `fmax(x - y, 0)` .

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|" **f**", "f **dimf**", " **f** "|\<math.h>|\<cmath>|
|**madim** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
