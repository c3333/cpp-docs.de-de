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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5511e7a7d17c47deaaaf61eedf3c00eec12db119
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234184"
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

*x*<br/>
Ein Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **ERF** -Funktionen geben die Gauß-Fehlerfunktion von *x*zurück. Die **erfc** -Funktionen geben die komplementäre Gauß-Fehlerfunktion von *x*zurück.

## <a name="remarks"></a>Bemerkungen

Die **ERF** -Funktionen berechnen die Gauß-Fehlerfunktion von *x*, die wie folgt definiert ist:

![Die Fehlerfunktion von x](media/crt_erf_formula.PNG "Die Fehlerfunktion von x")

Die komplementäre Gauß-Fehlerfunktion ist als 1-ERF (x) definiert. Die **ERF** -Funktionen geben einen Wert im Bereich von-1,0 bis 1,0 zurück. Es gibt keine Fehlerrückgabe. Die **erfc** -Funktionen geben einen Wert im Bereich 0 bis 2 zurück. Wenn *x* für **erfc**zu groß ist, wird die **errno** -Variable auf **ERANGE**festgelegt.

Da C++ das überladen zulässt, können Sie über Ladungen von **ERF** und **erfc** aufzurufen, die **`float`** -und-Typen verwenden und zurückgeben **`long double`** . In einem C-Programm verwenden **ERF** und **erfc** immer einen **`double`** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**ERF**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<math.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
