---
title: carg, cargf, cargl
description: API-Referenz für CARG, cargf und Kargl; , die das Argument einer komplexen Zahl mit einem Verzweigungs Ausschnitt entlang der negativen reellen Achse abrufen.
ms.date: 9/2/2020
api_name:
- carg
- cargf
- cargl
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
- carg
- cargf
- cargl
- complex/carg
- complex/cargf
- complex/cargl
helpviewer_keywords:
- carg function
- cargf function
- cargl function
ms.assetid: 610d6a93-b929-46ab-a966-b77db0b804be
ms.openlocfilehash: 907694904b260c44dde84724c739c62dfe46dbde
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555812"
---
# <a name="carg-cargf-cargl"></a>carg, cargf, cargl

Ruft das Argument einer komplexen Zahl mit einem Verzweigungs Ausschnitt entlang der negativen reellen Achse ab.

## <a name="syntax"></a>Syntax

```C
double carg(
   _Dcomplex z
);
float carg(
   _Fcomplex z
);  // C++ only
long double carg(
   _Lcomplex z
);  // C++ only
float cargf(
   _Fcomplex z
);
long double cargl(
   _Lcomplex z
);
#define carg(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*z*\
Eine komplexe Zahl.

## <a name="return-value"></a>Rückgabewert

Das Argument (auch als Phase bezeichnet) von *z*. Das Ergebnis ist das Intervall [-, +.].

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **CARG** aufzurufen, die **_Fcomplex** -oder **_Lcomplex** -Werte annehmen und-oder-Werte zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm nicht das- \<tgmath.h> Makro verwenden, um diese Funktion aufzurufen, nimmt **CARG** immer einen **_Dcomplex** Wert und gibt einen **`double`** Wert zurück.

Wenn Sie das- \<tgmath.h> `carg()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**CARG**, **cargf**, **cargl**|\<complex.h>|\<ccomplex>|
|**CARG** -Makro | \<tgmath.h> ||

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
