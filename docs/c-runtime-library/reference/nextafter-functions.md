---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 4/2/2020
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: b137fd131536da6b8630b9cadf69238ce48964bf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909337"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Gibt den nächsten darstellbaren Gleitkommawert zurück.

## <a name="syntax"></a>Syntax

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der Gleitkommawert, der den Startpunkt markiert.

*Teenie*<br/>
Der Gleitkommawert, der den Zielpunkt markiert.

## <a name="return-value"></a>Rückgabewert

Gibt den nächsten darstellbaren Gleit Komma Wert des Rückgabe Typs nach *x* in der Richtung *y*zurück. Wenn *x* und *y* gleich sind, gibt die Funktion *y*in den Rückgabetyp konvertiert zurück, ohne dass eine Ausnahme ausgelöst wird. Wenn *x* nicht gleich *y*ist und das Ergebnis ein DENORMAL oder NULL ist, werden die **FE_UNDERFLOW** -und **FE_INEXACT** Gleit Komma Ausnahmezustände festgelegt, und das korrekte Ergebnis wird zurückgegeben. Wenn " *x* " oder " *y* " ein NaN-Wert ist, ist der Rückgabewert einer der Eingabe-Nans. Wenn *x* begrenzt ist und das Ergebnis unendlich oder nicht im Typ darstellbar ist, wird eine ordnungsgemäß signierte unendlich oder NaN zurückgegeben, die **FE_OVERFLOW** -und **FE_INEXACT** Gleit Komma Ausnahmezustände werden festgelegt, und **errno** wird auf **ERANGE**festgelegt.

## <a name="remarks"></a>Hinweise

Die **nextafter** -und **NexTTo** -Funktions Familien sind äquivalent, außer dem Parametertyp *y*. Wenn *x* und *y* gleich sind, wird der zurückgegebene Wert *y* in den Rückgabetyp konvertiert.

Da C++ das überladen zulässt, können Sie \<, wenn Sie cmath-> einschließen, über Ladungen von **nextafter** und **NexTTo** aufzurufen, die **float** -und **Long** **Double** -Typen zurückgeben. In einem C-Programm geben **nextafter** und **NexTTo** immer **Double**zurück.

Die Funktionen **_nextafter** und **_nextafterf** sind Microsoft-spezifisch. Die **_nextafterf** -Funktion ist nur verfügbar, wenn für x64 kompiliert wird.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**, **nextaf terf**, **nextaf Terl**, **_nextafterf**, **NexTTo**, **NexTTo wardf**, **nextin wardl**|\<math.h>|\<math.h> oder \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> oder \<cfloat>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
