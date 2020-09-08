---
title: cimag, cimagf, cimagl
description: API-Referenz für Cimag, cimagf und cimagl; , die den imaginären Teil einer komplexen Zahl abrufen.
ms.date: 9/2/2020
api_name:
- cimag
- cimagf
- cimagl
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
- cimagf
- cimagl
- complex/cimag
- complex/cimagf
- complex/cimagl
- cimag
helpviewer_keywords:
- cimag function
- cimagf function
- cimagl function
ms.assetid: 0d8836f5-d61d-44cd-8731-6f75cb776def
ms.openlocfilehash: 41631a161a47e247b12a39e312a3f40084c8f22f
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555839"
---
# <a name="cimag-cimagf-cimagl"></a>cimag, cimagf, cimagl

Ruft den Imaginärteil einer komplexen Zahl ab.

## <a name="syntax"></a>Syntax

```C
double cimag( _Dcomplex z );
float cimagf( _Fcomplex z );
long double cimagl( _Lcomplex z );
#define cimag(X) // Requires C11 or higher

float cimag( _Fcomplex z );  // C++ only
long double cimag( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parameter

*z*\
Eine komplexe Zahl.

## <a name="return-value"></a>Rückgabewert

Der imaginäre Teil von *z*.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **Cimag** aufzurufen, die **_Fcomplex** -oder **_Lcomplex** -Werte annehmen und-oder-Werte zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm nicht das- \<tgmath.h> Makro verwenden, um diese Funktion aufzurufen, nimmt **Cimag** immer einen **_Dcomplex** Wert und gibt einen **`double`** Wert zurück.

Wenn Sie das- \<tgmath.h> `cimag()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**Cimag**, **cimagf**, **cimagl**|\<complex.h>|\<ccomplex>|
|**Cimag** -Makro | \<tgmath.h> ||

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
