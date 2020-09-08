---
title: frexp, frexpf, frexpl
description: API-Referenz für frexp, frexpf und frexpl; die die Mantisse und den Exponenten einer Gleit Komma Zahl abruft.
ms.date: 9/1/2020
api_name:
- frexp
- _o_frexp
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
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: a23de4160abcfab2518125bfa0fd35a389901674
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555747"
---
# <a name="frexp-frexpf-frexpl"></a>frexp, frexpf, frexpl

Ruft die Mantisse und den Exponenten einer Gleitkommazahl ab

## <a name="syntax"></a>Syntax

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
#define frexpl(X, INT_PTR) // Requires C11 or higher
```

```cpp
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Gleitkommawert.

*expptr*\
Zeiger auf gespeicherten Integer-Exponenten

## <a name="return-value"></a>Rückgabewert

**frexp** gibt die Mantisse zurück. Wenn *x* gleich 0 ist, gibt die Funktion 0 für die Mantisse und den Exponenten zurück. Wenn *expptr* **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion **errno** auf **EINVAL** fest und gibt 0 zurück.

## <a name="remarks"></a>Hinweise

Die **frexp** -Funktion teilt den Gleit Komma Wert (*x*) in eine Mantisse (*m*) und einen Exponenten (*n*) auf, sodass der absolute Wert von *m* größer oder gleich 0,5 und kleiner als 1,0 und *x*  =  *m* * 2<sup>*n*</sup>ist. Der ganzzahlige Exponent *n* wird an dem Speicherort gespeichert, auf den von *expptr*verwiesen wird.

C++ ermöglicht überladen, sodass Sie über Ladungen von **frexp**abrufen können. Wenn Sie in einem C-Programm das \<tgmath.h> -Makro zum aufruft dieser Funktion nicht verwenden, verwendet **frexp** immer **`double`** und einen- **`int`** Zeiger und gibt einen zurück **`double`** .

Wenn Sie das- \<tgmath.h> `frexp()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**frexp**, **frexpf**, **frexpl**|\<math.h>|
|**frexp** -Makro | \<tgmath.h> |

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
