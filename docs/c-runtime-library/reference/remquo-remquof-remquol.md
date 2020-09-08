---
title: remquo, remquof, remquol
description: API-Referenz für remquo, remquof und remquol; , die den Rest von zwei ganzzahligen Werten berechnet und einen ganzzahligen Wert mit dem Vorzeichen und der ungefähren Größe des Quotienten an einem Speicherort speichert, der in einem Parameter angegeben ist.
ms.date: 9/1/2020
api_name:
- remquof
- remquo
- remquol
- _o_remquo
- _o_remquof
- _o_remquol
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
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: d99204ad9a80c6320869cbb72aee905981a5224d
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554967"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Berechnet den Rest von zwei ganzzahligen Werten und speichert einen ganzzahligen Wert mit dem Zeichen und der ungefähren Größe des Quotienten an einem Speicherort, der in einem Parameter angegeben ist.

## <a name="syntax"></a>Syntax

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
#define remquo(X, Y, INT_PTR) // Requires C11 or higher

float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>Parameter

*Zahl*\
Der Zähler.

*Denom*\
Der Nenner.

*beizubehalten*\
Ein Zeiger auf eine ganze Zahl zum Speichern eines Werts, der das Zeichen und die ungefähre Größe des Quotienten hat.

## <a name="return-value"></a>Rückgabewert

**remquo** gibt den Gleit Komma Rest von *x*  /  *y*zurück. Wenn der Wert von *y* 0,0 ist, gibt **remquo** einen stillen NaN-Wert zurück. Informationen zur Darstellung eines stillen Nan durch die **printf** -Familie finden Sie unter [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Hinweise

Die **remquo** -Funktion berechnet den Gleit Komma Rest *f* von *x*  /  *y* , sodass *x*  =  *i* \* *y*  +  *f*, bei *i* dem es sich um eine ganze Zahl handelt, *f* das gleiche Vorzeichen wie *x*hat und der absolute Wert von *f* kleiner ist als der absolute Wert von *y*.

C++ ermöglicht überladen, sodass Sie über Ladungen von **remquo** aufgerufen werden können, die-oder-Werte verwenden und zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, nimmt **remquo** immer zwei **`double`** Argumente an und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `remquo()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|--------------|---------------------|-|
|**remquo**, **remquof**, **remquol**|\<math.h>|\<cmath> oder \<math.h>|
|**remquo** -Makro | \<tgmath.h> ||

Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_remquo.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;
   int quo = 0;

   z = remquo(w, x, &quo);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
   printf("Approximate signed quotient is %d\n", quo);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
Approximate signed quotient is -3
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
