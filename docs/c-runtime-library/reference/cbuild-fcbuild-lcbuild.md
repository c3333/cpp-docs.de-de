---
title: _Cbuild, _FCbuild, _LCbuild
ms.date: 03/30/2018
api_name:
- _Cbuild
- _FCbuild
- _LCbuild
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
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
ms.openlocfilehash: d521fdb0d79e1e4ff6e6c1b01ce40941ed5c8c0a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221964"
---
# <a name="_cbuild-_fcbuild-_lcbuild"></a>_Cbuild, _FCbuild, _LCbuild

Erstellt eine komplexe Zahl aus reellen und imaginären teilen.

## <a name="syntax"></a>Syntax

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>Parameter

*real*<br/>
Der reelle Teil der zu erstellenden komplexen Zahl.

*imaginären*<br/>
Der Imaginärteil der zu erstellenden komplexen Zahl.

## <a name="return-value"></a>Rückgabewert

Eine **_Dcomplex**-, **_Fcomplex**-oder **_Lcomplex** -Struktur, die die komplexe Zahl (*Real*, *imaginär* \* i) für Werte des angegebenen Gleit Komma Typs darstellt.

## <a name="remarks"></a>Bemerkungen

Die Funktionen **_Cbuild**, **_FCbuild**und **_LCbuild** vereinfachen die Erstellung komplexer Typen. Verwenden Sie die Funktionen "up" [, "fialf", "fiall](creal-crealf-creall.md) " und " [Cimag", "cimagf" und "cimagl](cimag-cimagf-cimagl.md) ", um die tatsächlichen und imaginären Teile der dargestellten komplexen Zahlen abzurufen

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**_Cbuild**, **_FCbuild** **_LCbuild**|\<complex.h>|\<ccomplex>|

Diese Funktionen sind Microsoft-spezifisch. Die Typen **_Dcomplex**, **_Fcomplex**und **_Lcomplex** sind Microsoft-spezifische Entsprechungen für die nicht implementierten C99-systemeigenen Typen, **`double _Complex`** **`float _Complex`** **`long double _Complex`** bzw.. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
