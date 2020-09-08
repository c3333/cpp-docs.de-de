---
title: lgamma, lgammaf, lgammal
description: API-Referenz für lgamma, lgammaf und lgammal; , der den natürlichen Logarithmus des absoluten Werts der Gamma Funktion des angegebenen Werts bestimmt.
ms.date: 9/1/2020
api_name:
- lgamma
- lgammaf
- lgammal
- _o_lgamma
- _o_lgammaf
- _o_lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: 202250f3575f61fcef1cf29a687b8fdf36e6db33
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555396"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Bestimmt den natürlichen Logarithmus des absoluten Werts der Gammafunktion des angegebenen Werts.

## <a name="syntax"></a>Syntax

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
#define lgammal(X) // Requires C11 or higher

float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der zu berechnende Wert.

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung wird der natürliche Logarithmus des absoluten Werts der Gamma-Funktion von *x*zurückgegeben.

|Problem|Rückgabewert|
|-----------|------------|
|*x* = Nan|NaN|
|*x* = ± 0|+INFINITY|
|*x*= negative ganze Zahl|+INFINITY|
|± Unendlich|+INFINITY|
|pole-Fehler|+HUGE_VAL, +HUGE_VALF, oder +HUGE_VALL|
|Überlaufbereichsfehler|± HUGE_VAL, ± HUGE_VALF oder ± HUGE_VALL|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **lgamma** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, verwendet **lgamma** immer, und gibt es zurück **`double`** .

Wenn Sie das- \<tgmath.h> `lgamma()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Wenn x eine rationale Zahl ist, gibt diese Funktion den Logarithmus der Fakultät von (x-1) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**lgamma**, **lgammaf**, **lgammal**|\<math.h>|\<cmath>|
|**lgamma** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
