---
title: lgamma, lgammaf, lgammal
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e2bdfbeac7b995be0b589156437a3ded39114adf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342161"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Bestimmt den natürlichen Logarithmus des absoluten Werts der Gammafunktion des angegebenen Werts.

## <a name="syntax"></a>Syntax

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parameter

*X*<br/>
Der zu berechnende Wert.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, geben Sie den natürlichen Logarithmus des absoluten Wertes der Gammafunktion von *x*zurück.

|Problem|Rückgabewert|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = 0 €|+INFINITY|
|*x*= negative ganze Zahl|+INFINITY|
|•INFINITY|+INFINITY|
|pole-Fehler|+HUGE_VAL, +HUGE_VALF, oder +HUGE_VALL|
|Überlaufbereichsfehler|HUGE_VAL, HUGE_VALF oder HUGE_VALL|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Bemerkungen

Da C++ eine Überlastung ermöglicht, können Sie Überladungen von **Lgamma** aufrufen, die **Float-** und **lange** **Doppeltypen** aufnehmen und zurückgeben. In einem C-Programm nimmt und gibt **lgamma** immer eine **doppelte**zurück.

Wenn x eine rationale Zahl ist, gibt diese Funktion den Logarithmus des Faktors (x - 1) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**lgamma**, **lgammaf**, **lgammal**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
