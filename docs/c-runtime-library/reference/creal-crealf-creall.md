---
title: creal, crealf, creall
description: API-Referenz für "kreal", "krealf", "alle" , die den Realteil einer komplexen Zahl abrufen.
ms.date: 9/2/2020
api_name:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: 4f375bbe8813ba67130f8b56d8e2c99d5b734764
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555929"
---
# <a name="creal-crealf-creall"></a>creal, crealf, creall

Ruft den Realteil einer komplexen Zahl ab

## <a name="syntax"></a>Syntax

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
#define creal(X) // Requires C11 or higher

float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parameter

*z*<br/>
Eine komplexe Zahl.

## <a name="return-value"></a>Rückgabewert

Der reelle Teil von *z*.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von der-Funktion **aufrufen, die** **_Fcomplex** -oder **_Lcomplex** -Werte annehmen und-oder-Werte zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm das- \<tgmath.h> Makro nicht zum Aufrufen dieser Funktion verwenden **creal** , nimmt die-Funktion immer einen **_Dcomplex** Wert und gibt einen- **`double`** Wert zurück.

Wenn Sie das- \<tgmath.h> `creal()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|"|" **, "** **kreal**", " **alle** "|\<complex.h>|\<ccomplex>|
|**kreal** -Makro | \<tgmath.h> ||

Die Typen **_Fcomplex**, **_Dcomplex**und **_Lcomplex** sind Microsoft-spezifische Entsprechungen der nicht implementierten systemeigenen C99-Typen **float _Complex**, **Double _Complex**und **long Double _Complex**bzw. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
