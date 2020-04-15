---
title: tgamma, tgammaf, tgammal
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d7e27e8b818a16cb0c18f58e2f40c0090dd13ecf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362503"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Bestimmt die Gammafunktion des angegebenen Werts.

## <a name="syntax"></a>Syntax

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Der Wert, dessen Gamma gefunden werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, gibt das Gamma von *x*zurück.

Ein Bereichsfehler kann auftreten, wenn die Größe von *x* zu groß oder zu klein für den Datentyp ist. Ein Domänenfehler oder Bereichsfehler kann auftreten, wenn *x* <= 0.

|Problem|Rückgabewert|
|-----------|------------|
|x = 0 €|•INFINITY|
|x = negative ganze Zahl|NaN|
|x = -INFINITY|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|Domänenfehler|NaN|
|pole-Fehler|HUGE_VAL, HUGE_VALF oder HUGE_VALL|
|Überlaufbereichsfehler|HUGE_VAL, HUGE_VALF oder HUGE_VALL|
|Unterlaufbereichsfehler|Richtiger Wert nach dem Runden|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Bemerkungen

Da C++ eine Überlastung ermöglicht, können Sie Überladungen von **tgamma** aufrufen, die **Float-** und **lange** **Doppeltypen** aufnehmen und zurückgeben. In einem C-Programm nimmt **tgamma** immer eine **doppelte**.

Wenn x eine natürliche Zahl ist, gibt diese Funktion die Fakultät von (x-1) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**, **tgammal**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
