---
title: ctanh, ctanhf, ctanhl
description: API-Referenz für ctanh, ctanhf, ctanhl; berechnet den komplexen hyperbolischen Tangens einer komplexen Zahl.
ms.date: 11/04/2016
api_name:
- ctanh
- ctanhf
- ctanhl
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
- ctanh
- ctanhf
- ctanhl
- complex/ctanh
- complex/ctanhf
- complex/ctanhl
helpviewer_keywords:
- ctanh function
- ctanhl function
- ctanhf function
ms.assetid: 807f2cd1-8740-4988-afff-5911c346385b
ms.openlocfilehash: 959d48853e3edac707a7daea615270b20dad37e7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555865"
---
# <a name="ctanh-ctanhf-ctanhl"></a>ctanh, ctanhf, ctanhl

Berechnet den komplexen Tangens Hyperbolicus einer komplexen Zahl

## <a name="syntax"></a>Syntax

```C
_Dcomplex ctanh(
   _Dcomplex z
);
_Fcomplex ctanh(
   _Fcomplex z
);  // C++ only
_Lcomplex ctanh(
   _Lcomplex z
);  // C++ only
_Fcomplex ctanhf(
   _Fcomplex z
);
_Lcomplex ctanhl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parameter

*z*\
Eine komplexe Zahl, die einen Winkel als Bogenmaß darstellt

## <a name="return-value"></a>Rückgabewert

Der komplexe hyperbolische Tangens von *z*.

|Eingabe|SEH-Ausnahme|**_matherr** Distanzieren|
|-----------|-------------------|--------------------------|
|± ∞, QNAN, IND|Keine|_DOMAIN|
|± (Tan, tanf)|INVALID|_DOMAIN|

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **ctanh** aufzurufen, die **_Fcomplex** -und **_Lcomplex** -Werte verwenden und zurückgeben. In einem C-Programm übernimmt **ctanh** immer einen **_Dcomplex** Wert und gibt ihn zurück.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**ctanh**,               **ctanhf**, **ctanhl**|\<complex.h>|\<ccomplex>|

Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
