---
title: tgamma, tgammaf, tgammal
description: API-Referenz für tgamma, tgammaf und tgammal; , die die Gamma Funktion des angegebenen Werts ermitteln.
ms.date: 9/1/2020
api_name:
- tgamma
- tgammaf
- tgammal
- _o_tgamma
- _o_tgammaf
- _o_tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: b49020ca0697e920dccf188df4ad024820966571
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555175"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Bestimmt die Gammafunktion des angegebenen Werts.

## <a name="syntax"></a>Syntax

```C
double tgamma(
   double x
);

float tgammaf(
   float x
);

long double tgammal(
   long double x
);

#define tgamma(X) // Requires C11 or higher

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der Wert, dessen Gamma gefunden werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, wird das Gamma von *x*zurückgegeben.

Ein Bereichs Fehler kann auftreten, wenn die Größe von *x* für den Datentyp zu groß oder zu klein ist. Wenn *x* <= 0 ist, kann ein Domänen Fehler oder ein Bereichs Fehler auftreten.

|Problem|Rückgabewert|
|-----------|------------|
|x = ± 0|± Unendlich|
|x = negative ganze Zahl|NaN|
|x =-unendlich|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|Domänenfehler|NaN|
|pole-Fehler|± HUGE_VAL, ± HUGE_VALF oder ± HUGE_VALL|
|Überlaufbereichsfehler|± HUGE_VAL, ± HUGE_VALF oder ± HUGE_VALL|
|Unterlaufbereichsfehler|Richtiger Wert nach dem Runden|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **tgamma** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, verwendet **tgamma** immer, und gibt es zurück **`double`** .

Wenn Sie das- \<tgmath.h> `tgamma()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Wenn x eine natürliche Zahl ist, gibt diese Funktion die Fakultät von (x-1) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**,  **tgammal**|\<math.h>|\<cmath>|
|**tgamma** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
