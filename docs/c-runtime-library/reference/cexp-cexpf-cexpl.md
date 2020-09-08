---
title: cexp, cexpf, cexpl
description: API-Referenz für cexp, cexpf und cexpl; , die den Exponentialwert einer komplexen Zahl berechnen.
ms.date: 11/04/2016
api_name:
- cexp
- cexpf
- cexpl
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
- cexp
- cexpf
- cexpl
- complex/cepx
- complex/cexpf
- complex/cexpl
helpviewer_keywords:
- cexp function
- cexpl function
- cexpf function
ms.assetid: f27fd5a9-70c7-4957-a7ee-5256d19bd1da
ms.openlocfilehash: 66f7b687e8da12473abef4dbc44831e175956ac0
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555214"
---
# <a name="cexp-cexpf-cexpl"></a>cexp, cexpf, cexpl

Berechnet die Exponentialzahl zur Basis e einer komplexen Zahl.

## <a name="syntax"></a>Syntax

```C
_Dcomplex cexp( _Dcomplex z );
_Fcomplex cexpf( _Fcomplex z );
_Lcomplex cexpl( _Lcomplex z );

_Fcomplex cexp( _Fcomplex z );  // C++ only
_Lcomplex cexp( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parameter

*z*\
Eine komplexe Zahl, die den Exponenten darstellt.

## <a name="return-value"></a>Rückgabewert

Der Wert von **e** wird auf die Potenz von *z (z*) gesteigert.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **cexp** aufzurufen, die **_Fcomplex** -und **_Lcomplex** -Werte verwenden und zurückgeben. In einem C-Programm übernimmt **cexp** immer einen **_Dcomplex** Wert und gibt ihn zurück.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**cexp**, **cexpf**, **cexpl**|\<complex.h>|\<complex.h>|

Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)\
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)\
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)\
[clog, clogf, clogl](clog-clogf-clogl.md)
