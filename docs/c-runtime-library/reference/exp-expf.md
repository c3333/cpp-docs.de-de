---
title: exp, expf, expl
ms.date: 4/2/2020
api_name:
- expf
- expl
- exp
- _o_exp
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
ms.openlocfilehash: 9872a83ba3ec5346b7aed5fb51ee837d3ed827aa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234171"
---
# <a name="exp-expf-expl"></a>exp, expf, expl

Berechnet den Bezeichner.

## <a name="syntax"></a>Syntax

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der Gleit Komma Wert, der die natürliche Logarithmus Basis *e* durch exponentiell berechnen soll.

## <a name="return-value"></a>Rückgabewert

Die **Exp** -Funktionen geben den Exponentialwert des Gleit Komma Parameters *x*zurück, wenn erfolgreich. Das Ergebnis ist " *e*<sup>*x*</sup>", wobei " *e* " die Basis des natürlichen Logarithmus ist. Bei einem Überlauf gibt die Funktion inf (unendlich) zurück. bei einem Unterlauf gibt **Exp** 0 zurück.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± Quiet NaN, unbestimmt|Keine|_DOMAIN|
|± Unendlich|INVALID|_DOMAIN|
|x ≥ 7.097827e+002|INEXACT+OVERFLOW|OVERFLOW|
|X ≤ -7.083964e+002|INEXACT+UNDERFLOW|UNDERFLOW|

Die **Exp** -Funktion verfügt über eine Implementierung, die Streaming SIMD Extensions 2 (SSE2) verwendet. Informationen und Einschränkungen zur Verwendung der SSE2-Implementierung finden Sie unter [_set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Bemerkungen

C++ ermöglicht überladen, sodass Sie über Ladungen von **Exp** aufzurufen können, die ein- **`float`** oder-Argument annehmen **`long double`** . In einem C-Programm übernimmt **Exp** immer und gibt einen zurück **`double`** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher C-Header|Erforderlicher C++-Header|
|--------------|---------------------|---|
|**Exp**, **expf**, **Expl**|\<math.h>|\<cmath> oder \<math.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>Siehe auch

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
