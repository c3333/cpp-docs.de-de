---
title: clog, clogf, clogl
description: API-Referenz für Clog, clogf und clogl , die den natürlichen Logarithmus einer komplexen Zahl mit einem Verzweigungs Ausschnitt entlang der negativen reellen Achse abrufen.
ms.date: 11/04/2016
api_name:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: 255f83a93c5c7a0c724fad143f028c2832be3173
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555071"
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

Ruft den natürlichen Logarithmus einer komplexen Zahl mit einem Achsenabschnitt auf der negativen reellen Achse ab.

## <a name="syntax"></a>Syntax

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parameter

*z*\
Die Basis des Logarithmus.

## <a name="return-value"></a>Rückgabewert

Der natürliche Logarithmus von *z*. Das Ergebnis wird an der realen Achse und im Intervall [-ID, + iy] entlang der imaginären Achse gebunden.

Die möglichen Rückgabewerte sind:

|z Parameter|Rückgabewert|
|-----------------|------------------|
|Positiv|Der Logarithmus zur Basis 10 von z|
|Zero|- ∞|
|Negativ|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **Clog** aufzurufen, die **_Fcomplex** -und **_Lcomplex** -Werte verwenden und zurückgeben. In einem C-Programm nimmt **Clog** immer einen **_Dcomplex** Wert an und gibt diesen zurück.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|**Clog**,               **clogf**, **clogl**|\<complex.h>|\<ccomplex>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
