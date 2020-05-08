---
title: hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl
ms.date: 4/2/2020
api_name:
- _hypotf
- hypot
- hypotf
- _hypot
- _hypotl
- hypotl
- _o__hypot
- _o__hypotf
- _o_hypot
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
- hypotf
- hypotl
- _hypotl
- hypot
- _hypot
- _hypotf
helpviewer_keywords:
- hypotenuse calculation
- hypot function
- hypotf function
- triangles, calculating hypotenuse
- hypotl function
- calculating hypotenuses
- _hypot function
ms.assetid: 6a13887f-bd53-43fc-9d77-5b42d6e49925
ms.openlocfilehash: 16db920d6e7d3836eb4a395b2029e2f9329f2681
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919835"
---
# <a name="hypot-hypotf-hypotl-_hypot-_hypotf-_hypotl"></a>hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl

Berechnet die Hypotenuse.

## <a name="syntax"></a>Syntax

```C
double hypot(
   double x,
   double y
);
float hypotf(
   float x,
   float y
);
long double hypotl(
   long double x,
   long double y
);
double _hypot(
   double x,
   double y
);
float _hypotf(
   float x,
   float y
);
long double _hypotl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parameter

*x*, *y*<br/>
Gleitkommawerte.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, gibt **hypot** die Länge der Hypotenuse zurück. bei einem Überlauf gibt **hypot** inf (Infinity) zurück, und die **errno** -Variable wird auf **ERANGE**festgelegt. Sie können **_matherr** verwenden, um die Fehlerbehandlung zu ändern.

Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **hypot** -Funktionen berechnen die Länge der Hypotenuse eines rechtwinkligen Dreiecks mit der Länge der beiden Seiten *x* und *y* (d. h. die Quadratwurzel von *x*<sup>2</sup> + *y*<sup>2</sup>).

Die Versionen der Funktionen mit führenden Unterstrichen unterstützen die Kompatibilität mit früheren Standards. Ihr Verhalten ist mit den Versionen identisch, die keine führende Unterstriche haben. Es empfiehlt sich, die Versionen ohne führende Unterstriche für neuen Code zu verwenden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**hypot**, **hypotf**, **hypotl**, **_hypot** **_hypotf**, **_hypotl**|\<math.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_hypot.c
// This program prints the hypotenuse of a right triangle.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 3.0, y = 4.0;

   printf( "If a right triangle has sides %2.1f and %2.1f, "
           "its hypotenuse is %2.1f\n", x, y, _hypot( x, y ) );
}
```

```Output
If a right triangle has sides 3.0 and 4.0, its hypotenuse is 5.0
```

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[_matherr](matherr.md)<br/>
