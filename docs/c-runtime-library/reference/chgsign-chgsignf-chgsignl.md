---
title: _chgsign, _chgsignf, _chgsignl
description: API-Referenz für _chgsign, _chgsignf und _chgsignl; , wodurch das Vorzeichen eines Gleit Komma Arguments umgekehrt wird.
ms.date: 04/05/2018
api_name:
- _chgsignl
- _chgsign
- _chgsignf
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
- _chgsignf
- chgsign
- _chgsignl
- _chgsign
helpviewer_keywords:
- _chgsignl function
- _chgsignf function
- chgsign function
- _chgsign function
ms.assetid: a6646f8e-213d-4564-8617-f43bc66f989f
ms.openlocfilehash: 7dc934f3c2d22cc36abe5f31f7d64e0674ccdd3a
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555201"
---
# <a name="_chgsign-_chgsignf-_chgsignl"></a>_chgsign, _chgsignf, _chgsignl

Kehrt das Zeichen eines Gleitkommaarguments um.

## <a name="syntax"></a>Syntax

```C
double _chgsign(
   double x
);
float _chgsignf(
   float x
);
long double _chgsignl(
   long double x
);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der zu ändernde Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **_chgsign** -Funktionen geben einen Wert zurück, der gleich dem Gleit Komma Argument *x*ist, aber mit umgekehrtem Vorzeichen. Es gibt keine Fehlerrückgabe.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_chgsign**|\<float.h>|
|**_chgsignf** **_chgsignl**|\<math.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)<br/>
