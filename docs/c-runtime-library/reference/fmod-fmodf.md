---
title: fmod, fmodf, fmodl
description: API-Referenz für "f", "f" und "f" der den Gleit Komma Rest berechnet.
ms.date: 9/1/2020
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: 2b610dec79c98b973af09f8efb147ad6797f7946
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556085"
---
# <a name="fmod-fmodf-fmodl"></a>fmod, fmodf, fmodl

Berechnet den Gleitkommarest.

## <a name="syntax"></a>Syntax

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);

#define fmod(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*x*, *y*\
Gleitkommawerte.

## <a name="return-value"></a>Rückgabewert

" **f** " gibt den Gleit Komma Rest von *x*  /  *y*zurück. Wenn der Wert von *y* 0,0 ist, gibt " **f** " einen stillen NaN-Wert zurück. Informationen zur Darstellung eines stillen Nan durch die **printf** -Familie finden Sie unter [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Hinweise

Die **Funktion "** f" berechnet den Gleit Komma Rest *f* von *x*  /  *y* , sodass *x*  =  *i* \* *y*  +  *f*, wobei *i* es sich um eine ganze Zahl handelt, *f* dasselbe Vorzeichen wie " *x*" hat und der absolute Wert von " *f* " kleiner ist als der absolute Wert von " *y*".

C++ ermöglicht überladen, sodass Sie über Ladungen von **FMOD** abrufen können, die- **`float`** und-Werte verwenden und zurückgeben **`long double`** . In einem C-Programm verwendet \<tgmath.h> **FMOD** immer zwei **`double`** Argumente und gibt einen zurück, es sei denn, Sie verwenden das-Makro, um diese Funktion aufzurufen **`double`** .

Wenn Sie das- \<tgmath.h> `fmod()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|" **f**" **, "** f", " **f** ", "f"|\<math.h>|
|**mamod** -Makro | \<tgmath.h> |

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
