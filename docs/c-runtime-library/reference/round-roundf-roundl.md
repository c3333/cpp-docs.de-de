---
title: round, roundf, roundl
description: API-Referenz für Round, roundf und roundl; , die einen Gleit Komma Wert auf den nächsten ganzzahligen Wert Runden.
ms.date: 09/25/2020
api_name:
- round
- roundl
- roundf
- _o_round
- _o_roundf
- _o_roundl
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
- roundf
- roundl
- round
helpviewer_keywords:
- roundl function
- round function
- roundf function
ms.assetid: 6be90877-193c-4b80-a32b-c3eca33f9c6f
ms.openlocfilehash: 2e51eb375ab814119dcf34d85c7f5aff11559784
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499171"
---
# <a name="round-roundf-roundl"></a>round, roundf, roundl

Rundet einen Gleit Komma Wert auf den nächsten ganzzahligen Wert.

## <a name="syntax"></a>Syntax

```C
double round(
   double x
);
float round(
   float x
);  // C++ only
long double round(
   long double x
);  // C++ only
float roundf(
   float x
);
long double roundl(
   long double x
);
#define round(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der zu rundende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **Round** -Funktionen geben einen Gleit Komma Wert zurück, der die nächste Ganzzahl in *x*darstellt. Halbe Werte werden kaufmännisch gerundet, unabhängig von der Einstellung des Gleitkomma-Rundungsmodus. Es gibt keine Fehlerrückgabe.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|Keine|**_DOMAIN**|

## <a name="remarks"></a>Bemerkungen

Da C++ das überladen zulässt, können Sie über Ladungen von **Round** aufzurufen, die **`float`** -und-Werte verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm, wenn Sie das- \<tgmath.h> Makro zum Abrufen dieser **round** Funktion verwenden, immer eine-Schleife durchführt und zurückgibt **`double`** .

Wenn Sie das- \<tgmath.h> `round()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**Round**, **roundf**, **roundl**|\<math.h>|
|**Round** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// Build with: cl /W3 /Tc
// This example displays the rounded
// results of floating-point values

#include <math.h>
#include <stdio.h>

int main()
{
    printf("===== Round a float\n\n");
    float floatValue = 2.4999999f; // float stores a value close to, but not exactly equal to, the initializer below. floatValue will contain 2.5 because it is the closest single precision value
    printf("roundf(%.1000g) is %.1000g\n", floatValue, roundf(floatValue));
    printf("roundf(%.1000g) is %.1000g\n", -floatValue, roundf(-floatValue));

    // double stores a value close to, but not exactly equal to, the initializer below. The closest double value is just slightly larger.
    double doubleValue = 2.4999999;
    printf("\n===== Round a double\n\n");
    printf("round(%.1000g) is %.1000g\n", doubleValue, round(doubleValue));
    printf("round(%.1000g) is %.1000g\n", -doubleValue, round(-doubleValue));

    // long double stores a value close to, but not exactly equal to, the initializer below. The closest long double value is just slightly larger.
    long double longDoubleValue = 2.4999999L;
    printf("\n===== Round a long double\n\n");
    printf("roundl(%.1000g) is %.1000g\n", longDoubleValue, roundl(longDoubleValue));
    printf("roundl(%.1000g) is %.1000g\n", -longDoubleValue, roundl(-longDoubleValue));

    return 0;
}
```

```Output
===== Round a float

roundf(2.5) is 3
roundf(-2.5) is -3

===== Round a double

round(2.499999900000000163657887242152355611324310302734375) is 2
round(-2.499999900000000163657887242152355611324310302734375) is -2

===== Round a long double

roundl(2.499999900000000163657887242152355611324310302734375) is 2
roundl(-2.499999900000000163657887242152355611324310302734375) is -2
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)\
[ceil, ceilf, ceil](ceil-ceilf-ceill.md)\
[Floor, floorf, floorl](floor-floorf-floorl.md)\
["f", "f"](fmod-fmodf.md)\
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)\
[lround, lroundf, lroundl, LlRound, llroundf, llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)\
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)\
[rint, rintf, rintl](rint-rintf-rintl.md)
