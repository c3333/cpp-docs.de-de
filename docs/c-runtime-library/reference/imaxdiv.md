---
title: imaxdiv
ms.date: 04/05/2018
api_name:
- imaxdiv
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
- imaxdiv
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
ms.openlocfilehash: 298356da8e8e76c132b963ef4f71db6a3d0e74f7
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505626"
---
# <a name="imaxdiv"></a>imaxdiv

Berechnet den Quotienten und den Rest von zwei ganzzahligen Werten beliebiger Größe als einzelnen Vorgang.

## <a name="syntax"></a>Syntax

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>Parameter

*Zahl*<br/>
Der Zähler.

*Denom*<br/>
Der Nenner.

## <a name="return-value"></a>Rückgabewert

**imaxdiv** wurde mit Argumenten vom Typ aufgerufen [intmax_t](../../c-runtime-library/standard-types.md) gibt eine Struktur vom Typ [imaxdiv_t](../../c-runtime-library/standard-types.md) zurück, die den Quotienten und den Rest enthält.

## <a name="remarks"></a>Bemerkungen

Die **imaxdiv** -Funktion dividiert den *Zahl* durch *denom* und berechnet dadurch den Quotienten und den Rest. Die **imaxdiv_t** Struktur enthält den Quotienten **intmax_t** **quot**und den Rest **intmax_t** **REM**. Das Vorzeichen des Quotienten entspricht dem des mathematischen Quotienten. Der absolute Wert ist die größte ganze Zahl, die kleiner ist als der absolute Wert des mathematischen Quotienten. Wenn der Nenner 0 ist, wird das Programm mit einer Fehlermeldung beendet.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

Wenn der Code mit den Befehlszeilenparametern von `9460730470000000 8766` erstellt und anschließend aufgerufen wird, wird diese Ausgabe generiert:

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv, lldiv](./div.md)<br/>
