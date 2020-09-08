---
title: fma, fmaf, fmal
description: API-Referenz für FMA, f MAF und f Dabei werden zwei Werte multipliziert, ein Dritter Wert hinzugefügt und dann das Ergebnis gerundet, ohne dass die Genauigkeit aufgrund von Vermittler Rundungen verloren geht.
ms.date: 9/1/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: e9ae92c28f24b6281d73450c7cabaad775a84d42
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556696"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Multipliziert zwei Werte, fügt einen dritten Wert hinzu und rundet dann das Ergebnis, ohne dass die Genauigkeit aufgrund von Vermittler Umrundungen verloren geht.

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

#define fma(X, Y, Z) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der erste zu multiplizierende Wert.

*Teenie*\
Der zweite zu multiplizierende Wert.

*z*\
Der hinzuzufügende Wert.

## <a name="return-value"></a>Rückgabewert

Gibt `(x * y) + z`zurück. Der Rückgabewert wird dann mit dem aktuellen Rundungsformat gerundet.

Andernfalls wird möglicherweise einer der folgenden Werte zurückgeben:

|Problem|Rückgabewert|
|-----------|------------|
|*x* = unendlich, *y* = 0 oder<br /><br /> *x* = 0, *y* = unendlich|NaN|
|*x* oder *y* = Exact ± unendlich, *z* = unendlich mit umgekehrtem Vorzeichen|NaN|
|*x* oder *y* = Nan|NaN|
|nicht (*x* = 0, *y*= unbegrenzt) und *z* = Nan<br /><br /> nicht (*x*= unbegrenzt, *y*= 0) und *z* = Nan|NaN|
|Überlaufbereichsfehler|± HUGE_VAL, ± HUGE_VALF oder ± HUGE_VALL|
|Unterlaufbereichsfehler|Richtige Wert nach dem Runden|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **FMA** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das- \<tgmath.h> Makro nicht zum aufruft dieser Funktion verwenden, verwendet **FMA** immer, und gibt es zurück **`double`** .

Wenn Sie das- \<tgmath.h> `fma()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Diese Funktion berechnet den Wert mit unendlicher Genauigkeit und rundet das endgültige Ergebnis dann.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**FMA**, f **MAF**, **f**|\<math.h>|\<cmath>|
|**FMA** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
