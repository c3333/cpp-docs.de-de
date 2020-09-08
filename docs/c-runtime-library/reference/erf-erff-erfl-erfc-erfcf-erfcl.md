---
title: erf, erff, erfl, erfc, erfcf, erfcl
description: API-Referenz für ERF, erff, erfl, erfc, erfcf und erfcl; berechnet die Fehlerfunktion oder die komplementäre Fehlerfunktion eines Werts.
ms.date: 9/1/2020
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
ms.openlocfilehash: ef83275515c66341798395bbfc2bb5b088e6cfb7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555643"
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
#define erf(X) // Requires C11 or higher
#define erfc(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Ein Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **ERF** -Funktionen geben die Gauß-Fehlerfunktion von *x*zurück. Die **erfc** -Funktionen geben die komplementäre Gauß-Fehlerfunktion von *x*zurück.

## <a name="remarks"></a>Hinweise

Die **ERF** -Funktionen berechnen die Gauß-Fehlerfunktion von *x*, die wie folgt definiert ist:

![Die Fehlerfunktion von x](media/crt_erf_formula.PNG "Die Fehlerfunktion von x")

Die komplementäre Gauß-Fehlerfunktion ist als 1-ERF (x) definiert. Die **ERF** -Funktionen geben einen Wert im Bereich von-1,0 bis 1,0 zurück. Es gibt keine Fehlerrückgabe. Die **erfc** -Funktionen geben einen Wert im Bereich 0 bis 2 zurück. Wenn *x* für **erfc**zu groß ist, wird die **errno** -Variable auf **ERANGE**festgelegt.

Da C++ das überladen zulässt, können Sie über Ladungen von **ERF** und **erfc** aufzurufen, die **`float`** -und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das \<tgmath.h> -Makro verwenden, um diese Funktion aufzurufen, nehmen **ERF** und **erfc** immer eine auf und geben zurück **`double`** .

Wenn Sie das- \<tgmath.h> `erf()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**ERF**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<math.h>|
|**ERF** -Makro | \<tgmath.h> |

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
