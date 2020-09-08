---
title: imaxabs
description: API-Referenz für imaxabs, die den absoluten Wert einer ganzen Zahl beliebiger Größe berechnet.
ms.date: 04/05/2018
api_name:
- imaxabs
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
- imaxabs
helpviewer_keywords:
- imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
ms.openlocfilehash: 599e8a0cb20f24bda24201be40fa1acc0ade993c
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555500"
---
# <a name="imaxabs"></a>imaxabs

Berechnet den absoluten Wert einer ganzen Zahl beliebiger Größe.

## <a name="syntax"></a>Syntax

```C
intmax_t imaxabs(
   intmax_t n
);
```

### <a name="parameters"></a>Parameter

*n*<br/>
Wert für ganze Zahl.

## <a name="return-value"></a>Rückgabewert

Die **imaxabs** -Funktion gibt den absoluten Wert des Arguments zurück. Es gibt keine Fehlerrückgabe.

> [!NOTE]
> Da der Bereich von negativen ganzen Zahlen, der mithilfe von **intmax_t** dargestellt werden kann, größer als der Bereich von positiven ganzen Zahlen ist, die dargestellt werden können, ist es möglich, ein Argument für **imaxabs** bereitzustellen, das nicht konvertiert werden kann. Wenn der absolute Wert des Arguments nicht durch den Rückgabetyp dargestellt werden kann, ist das Verhalten von **imaxabs** nicht definiert.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**imaxabs**|\<inttypes.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_imaxabs.c
// Build using: cl /W3 /Tc crt_imaxabs.c
// This example calls imaxabs to compute an
// absolute value, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x = LLONG_MIN + 2;

   printf("The absolute value of %lld is %lld\n", x, imaxabs(x));
}
```

```Output
The absolute value of -9223372036854775806 is 9223372036854775806
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
