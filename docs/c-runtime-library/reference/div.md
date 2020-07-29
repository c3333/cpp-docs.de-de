---
title: div, ldiv, lldiv
ms.date: 04/05/2018
api_name:
- div
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
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 24432ec1514f6cd2d569fd5752a8ed7118059d6a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234223"
---
# <a name="div-ldiv-lldiv"></a>div, ldiv, lldiv

Berechnet den Quotienten und den Rest von zwei ganzzahligen Werten.

## <a name="syntax"></a>Syntax

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>Parameter

*Zahl*<br/>
Der Zähler.

*Denom*<br/>
Der Nenner.

## <a name="return-value"></a>Rückgabewert

**div** , das mithilfe von Argumenten des Typs aufgerufen **`int`** wurde, gibt eine Struktur vom Typ **div_t**zurück, die den Quotienten und den Rest enthält. Der Rückgabewert mit Argumenten vom Typ **`long`** ist **ldiv_t**, und der Rückgabewert mit Argumenten des Typs **`long long`** ist **lldiv_t**. **div_t**, **ldiv_t**und **lldiv_t** sind in definiert \<stdlib.h> .

## <a name="remarks"></a>Bemerkungen

Die **div** -Funktion dividiert den *Zahl* durch *denom* und berechnet dadurch den Quotienten und den Rest. Die [div_t](../../c-runtime-library/standard-types.md) Struktur enthält den Quotienten, **quot**und den Rest, **REM**. Das Vorzeichen des Quotienten entspricht dem des mathematischen Quotienten. Der absolute Wert ist die größte ganze Zahl, die kleiner ist als der absolute Wert des mathematischen Quotienten. Wenn der Nenner 0 ist, wird das Programm mit einer Fehlermeldung beendet.

Die über Ladungen von **div** , die Argumente des Typs **`long`** oder verwenden, **`long long`** sind nur für C++-Code verfügbar. Die Rückgabe Typen [ldiv_t](../../c-runtime-library/standard-types.md) und [lldiv_t](../../c-runtime-library/standard-types.md) die Member **quot** und **REM**enthalten, die die gleiche Bedeutung wie die Member von **div_t**haben.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**div**, **ldiv**, **lldiv**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>Siehe auch

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
