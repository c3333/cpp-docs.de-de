---
title: fmin, fminf, fminl
description: API-Referenz für "vollständig", "vollständig", "f" und "f" , der den kleineren von zwei Werten bestimmt.
ms.date: 9/1/2020
api_name:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: 6a070835d809c6adcb5b7bfd57b5373886b348ca
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556709"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Bestimmt den kleineren von zwei angegebenen Werten.

## <a name="syntax"></a>Syntax

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);

#define fmin(x) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der erste zu vergleichende Wert.

*Teenie*\
Der zweite zu vergleichende Wert.

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung wird der kleinere von *x* oder *y*zurückgegeben.

|Eingabe|Ergebnis|
|-----------|------------|
|*x* ist NaN|*y*|
|*y* ist NaN|*x*|
|*x* und *y* sind Nan|NaN|

Die Funktion bewirkt nicht, dass [_matherr](matherr.md) aufgerufen wird, keine Gleit Komma Ausnahmen verursachen oder den Wert von **errno**ändern.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **FMIN** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, verwendet **FMIN** immer und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `fmin()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|" **f**" **, "f**" **, "f"**|Scher \<math.h><br />C++: \<math.h> oder \<cmath>|
|**Mamin** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
