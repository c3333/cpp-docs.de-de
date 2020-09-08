---
title: acos, acosf, acosl
description: API-Referenz für `acos` , `acosf` und, die den Arkus `acosl` Kosinus eines Gleit Komma Werts berechnen.
ms.date: 08/31/2020
api_name:
- acosf
- acos
- acosl
- _o_acos
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
- acos
- acosl
- acosf
- math/acosf
- math/acosl
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
ms.openlocfilehash: eeee51cea2a81882ee1ed8b014312ee9f9095dc6
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555097"
---
# <a name="acos-acosf-acosl"></a>acos, acosf, acosl

Berechnet den Arkuskosinus.

## <a name="syntax"></a>Syntax

```C
double acos( double x );
float acosf( float x );
long double acosl( long double x );
#define acos(X) // Requires C11 or higher

float acos( float x );   // C++ only
long double acos( long double x );   // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der Wert zwischen-1 und 1, für den der Arkus Kosinus berechnet werden soll (umgekehrter Kosinus).

## <a name="return-value"></a>Rückgabewert

Die **ACOS** -Funktion gibt den Arkus Kosinus von *x* im Bereich 0 bis adressiert zurück.

Wenn *x* kleiner als-1 oder größer als 1 ist, gibt **ACOS** standardmäßig einen unbestimmten Wert zurück.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± ∞|INVALID|_DOMAIN|
|± QNAN,IND|Keine|_DOMAIN|
|&#124;x&#124;>1|INVALID|_DOMAIN|

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **ACOS** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, nimmt **ACOS** immer eine an und gibt Sie zurück **`double`** .

Wenn Sie das- \<tgmath.h> `acos()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|Optionale Header|
|-------------|---------------------|----------------------|
|**ACOS**, **Acosf**, **acosl**|\<math.h>|\<errno.h>|
|**ACOS ()** -Makro | \<tgmath.h> ||

## <a name="example"></a>Beispiel

Dieses Programm fordert zur Eingabe eines Werts im – 1 bis 1 auf. Eingabewerte außerhalb dieses Bereichs erzeugen `_DOMAIN`-Fehlermeldungen. Wenn ein gültiger Wert eingegeben wird, gibt das Programm den Arkussinus und den Arkuskosinus dieses Werts aus.

```C
// crt_asincos.c
// arguments: 0

#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int ac, char* av[] )
{
    double  x,
            y;
    errno_t err;

    // argument checking
    if (ac != 2)
    {
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",
                   av[0]);
        return 1;
    }

    // Convert argument into a double value
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)
    {
        fprintf_s( stderr, "Error converting argument into ",
                   "double value.\n");
        return 1;
    }

    // Arcsine of X
    y = asin( x );
    printf_s( "Arcsine of %f = %f\n", x, y );

    // Arccosine of X
    y = acos( x );
    printf_s( "Arccosine of %f = %f\n", x, y );
}
```

```Output
Arcsine of 0.000000 = 0.000000
Arccosine of 0.000000 = 1.570796
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)
