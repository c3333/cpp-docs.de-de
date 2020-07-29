---
title: fmin, fminf, fminl
ms.date: 04/05/2018
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
ms.openlocfilehash: d6cd16c298c3f4bedb8064d66efd2d4bbe20c22b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216985"
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
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der erste zu vergleichende Wert.

*Teenie*<br/>
Der zweite zu vergleichende Wert.

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung wird der kleinere von *x* oder *y*zurückgegeben.

|Eingabe|Ergebnis|
|-----------|------------|
|*x* ist NaN|*Teenie*|
|*y* ist NaN|*x*|
|*x* und *y* sind Nan|NaN|

Die Funktion bewirkt nicht, dass [_matherr](matherr.md) aufgerufen wird, keine Gleit Komma Ausnahmen verursachen oder den Wert von **errno**ändern.

## <a name="remarks"></a>Bemerkungen

Da C++ das überladen zulässt, können Sie über Ladungen von **FMIN** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . In einem C-Programm nimmt die **Formatierung immer eine** an und gibt Sie zurück **`double`** .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|" **f**" **, "f**" **, "f"**|Scher\<math.h><br />C++: \<math.h> oder\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
