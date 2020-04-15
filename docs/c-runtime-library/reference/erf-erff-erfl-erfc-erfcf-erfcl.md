---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 4/2/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ad7ad279d3686e4f33a6f5f901c60348c131b89a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347920"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Berechnet die Fehlerfunktion oder die komplementäre Fehlerfunktion eines Werts.

## <a name="syntax"></a>Syntax

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Ein Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **erf-Funktionen** geben die Gauß-Fehlerfunktion von *x*zurück. Die **erfc-Funktionen** geben die komplementäre Gauß-Fehlerfunktion von *x*zurück.

## <a name="remarks"></a>Bemerkungen

Die **erf-Funktionen** berechnen die Gauß-Fehlerfunktion von *x*, die wie folgt definiert ist:

![Die Fehlerfunktion von x](media/crt_erf_formula.PNG "Die Fehlerfunktion von x")

Die komplementäre Gauß-Fehlerfunktion ist definiert als 1 - erf(x). Die **erf-Funktionen** geben einen Wert im Bereich -1.0 bis 1.0 zurück. Es gibt keine Fehlerrückgabe. Die **erfc-Funktionen** geben einen Wert im Bereich 0 bis 2 zurück. Wenn *x* für **erfc**zu groß ist, wird die **errno-Variable** auf **ERANGE**gesetzt.

Da C++ eine Überlastung ermöglicht, können Sie Überladungen von **erf** und **erfc** aufrufen, die **Float-** und **lange** **Doppeltypen** aufnehmen und zurückgeben. In einem C-Programm nehmen **erf** und **erfc** immer ein **Double**und geben es zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**erf**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<math.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
