---
title: ilogb, ilogbf, ilogbl2
description: API-Referenz für ilogb, ilogbf und ilogbl2; , die eine ganze Zahl abrufen, die den unausgewogenen Basis-2-Exponent des angegebenen Werts darstellt.
ms.date: 9/1/2020
api_name:
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
ms.openlocfilehash: b27c329cca1edb9d30bb6b9b641f94d174c9c406
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556371"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb, ilogbf, ilogbl

Ruft eine Ganzzahl ab, die den unausgewogenen Basis-2-Exponenten des angegebenen Werts darstellt.

## <a name="syntax"></a>Syntax

```C
int ilogb(
   double x
);

int ilogb(
   float x
); //C++ only

int ilogb(
   long double x
); //C++ only

int ilogbf(
   float x
);

int ilogbl(
   long double x
);

#define ilogbl(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der angegebene Wert.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, wird der Basis-2-Exponent von *x* als-Wert zurückgegeben **`signed int`** .

Andernfalls wird einer der folgenden Werte zurückgegeben, der in definiert ist \<math.h> :

|Eingabe|Ergebnis|
|-----------|------------|
|± 0|FP_ILOGB0|
|± inf, ± Nan, unbegrenzt|FP_ILOGBNAN|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **ilogb** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm nicht das- \<tgmath.h> Makro verwenden, um diese Funktion aufzurufen, verwendet **ilogb** immer und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `ilogb()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Das Aufrufen dieser Funktion ähnelt dem Aufrufen der entsprechenden **logb** -Funktion und dem anschließenden Umwandeln des Rückgabewerts in **`int`** .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**ilogb**, **ilogbf**, **ilogbl**|\<math.h>|\<cmath>|
|**ilogb** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb, logbf, logbl, _logb, _logbf](logb-logbf-logbl-logb-logbf.md)<br/>
