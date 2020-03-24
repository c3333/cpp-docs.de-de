---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cabs
helpviewer_keywords:
- cabs function
- absolute values
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 2c2bd6b3f097095514e47b757306b4d83a990e45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170340"
---
# <a name="_cabs"></a>_cabs

Berechnet den absoluten Wert einer komplexen Zahl.

## <a name="syntax"></a>Syntax

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Parameter

*z*<br/>
Komplexe Zahl.

## <a name="return-value"></a>Rückgabewert

**_cabs** gibt bei erfolgreicher Ausführung den absoluten Wert des Arguments zurück. Bei einem Überlauf **_cabs** gibt _cabs **HUGE_VAL** zurück und legt **errno** auf **ERANGE**fest. Sie können die Fehlerbehandlung mit [_matherr](matherr.md) ändern.

## <a name="remarks"></a>Bemerkungen

Die **_cabs** -Funktion berechnet den absoluten Wert einer komplexen Zahl, die eine Struktur vom Typ [_complex](../../c-runtime-library/standard-types.md)sein muss. Die Struktur *z* besteht aus einer echten Komponente *x* und einer imaginären Komponente *y*. Ein **_cabs** -Aufrufe erzeugt einen Wert, der dem des Ausdrucks `sqrt( z.x * z.x + z.y * z.y )`entspricht.

## <a name="requirements"></a>Requirements (Anforderungen)

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)
