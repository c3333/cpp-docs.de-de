---
title: carg, cargf, cargl
ms.date: 11/04/2016
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
ms.openlocfilehash: 883710ad4538fb9081ad0c8cfaa169380ddbaf55
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213618"
---
# <a name="carg-cargf-cargl"></a>carg, cargf, cargl

Ruft das Argument einer komplexen Zahl mit einem Achsenabschnitt auf der negativen reellen Achse ab.

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
```

### <a name="parameters"></a>Parameter

*z*<br/>
Eine komplexe Zahl.

## <a name="return-value"></a>Rückgabewert

Das Argument (auch als Phase bezeichnet) von *z*. Das Ergebnis ist das Intervall [-, +.].

## <a name="remarks"></a>Bemerkungen

Da C++ das überladen zulässt, können Sie über Ladungen von **CARG** aufzurufen, die **_Fcomplex** -oder **_Lcomplex** -Werte annehmen und-oder-Werte zurückgeben **`float`** **`long double`** . In einem C-Programm nimmt **CARG** immer einen **_Dcomplex** Wert und gibt einen **`double`** Wert zurück.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**CARG**, **cargf**, **cargl**|\<complex.h>|\<ccomplex>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
