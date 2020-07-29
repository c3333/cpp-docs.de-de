---
title: abs, labs, llabs, _abs64
ms.date: 04/05/2018
api_name:
- abs
- _abs64
- labs
- llabs
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- stdlib/_abs64
- math/abs
- _abs64
- abs
- labs
- math/labs
- llabs
- math/llabs
- cmath/abs
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
ms.openlocfilehash: 96363f8d2139a5c75ee25a2c43b4c7ef55094f13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221990"
---
# <a name="abs-labs-llabs-_abs64"></a>abs, labs, llabs, _abs64

Berechnet den absoluten Wert des Arguments.

## <a name="syntax"></a>Syntax

```C
int abs( int n );
long labs( long n );
long long llabs( long long n );
__int64 _abs64( __int64 n );
```

```cpp
long abs( long n );   // C++ only
long long abs( long long n );   // C++ only
double abs( double n );   // C++ only
long double abs( long double n );   // C++ only
float abs( float n );   // C++ only
```

### <a name="parameters"></a>Parameter

*n*<br/>
Ein numerischer Wert.

## <a name="return-value"></a>Rückgabewert

Die Funktionen **ABS**, **Labs**, **llabs** und **_abs64** geben den absoluten Wert des Parameters *n*zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Bemerkungen

Da C++ das überladen zulässt, können Sie über Ladungen von **ABS** aufzurufen, die-, **`long`** **`long long`** -,-, **`float`** **`double`** -und- **`long double`** Werte verwenden und zurückgeben. Diese über Ladungen werden im- \<cmath> Header definiert. In einem C-Programm nimmt **ABS** immer an und gibt einen zurück **`int`** .

**Microsoft-spezifisch**: da der Bereich von negativen ganzen Zahlen, der mithilfe eines ganzzahligen Typs dargestellt werden kann, größer als der Bereich von positiven ganzen Zahlen ist, die mithilfe dieses Typs dargestellt werden können, kann ein Argument für diese Funktionen bereitgestellt werden, die nicht konvertiert werden können. Wenn der absolute Wert des Arguments nicht durch den Rückgabetyp dargestellt werden kann, geben die **ABS** -Funktionen den Argument Wert unverändert zurück. Insbesondere gibt `abs(INT_MIN)``INT_MIN` zurück, `labs(LONG_MIN)` gibt `LONG_MIN` zurück, `llabs(LLONG_MIN)` gibt `LLONG_MIN` zurück und `_abs64(_I64_MIN)` gibt `_I64_MIN` zurück. Dies bedeutet, dass die **ABS** -Funktionen nicht verwendet werden können, um einen positiven Wert sicherzustellen.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------------|-----------------------|---------------------------|
|**ABS**, **Labs**, **llabs**|\<math.h> oder \<stdlib.h>|\<cmath>, \<cstdlib>, \<stdlib.h> oder \<math.h>|
|**_abs64**|\<stdlib.h>|\<cstdlib> oder \<stdlib.h>|

Wenn Sie die überladenen Versionen von **ABS** in C++ verwenden möchten, müssen Sie den- \<cmath> Header einschließen.

## <a name="example"></a>Beispiel

Dieses Programm berechnet die absoluten Werte einiger Zahlen und zeigt sie an.

```C
// crt_abs.c
// Build: cl /W3 /TC crt_abs.c
// This program demonstrates the use of the abs function
// by computing and displaying the absolute values of
// several numbers.

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <limits.h>

int main( void )
{
    int ix = -4;
    long lx = -41567L;
    long long llx = -9876543210LL;
    __int64 wx = -1;

    // absolute 32 bit integer value
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));

    // absolute long integer value
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));

    // absolute long long integer value
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));

    // absolute 64 bit integer value
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,
        _abs64(wx));

    // Integer error cases:
    printf_s("Microsoft implementation-specific results:\n");
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));
}
```

```Output
The absolute value of -4 is 4
The absolute value of -41567 is 41567
The absolute value of -9876543210 is 9876543210
The absolute value of 0xffffffffffffffff is 0x0000000000000001
Microsoft implementation-specific results:
abs(INT_MIN) returns -2147483648
labs(LONG_MIN) returns -2147483648
llabs(LLONG_MIN) returns -9223372036854775808
_abs64(_I64_MIN) returns 0x8000000000000000
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[imaxabs](imaxabs.md)
