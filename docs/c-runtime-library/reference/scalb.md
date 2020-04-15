---
title: _scalb, _scalbf
ms.date: 4/2/2020
api_name:
- _scalb
- _scalbf
- _o__scalb
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scalb
- _scalb
- _scalbf
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
ms.openlocfilehash: 6501fe53e67d0f277fa64c08e0edbff1d7eeb61a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332690"
---
# <a name="_scalb-_scalbf"></a>_scalb, _scalbf

Skaliert das Argument als zweite Potenz.

## <a name="syntax"></a>Syntax

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gleitkommawert mit doppelter Genauigkeit.

*Exp*<br/>
Ganzzahlexponent.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg einen Exponentialwert zurück. Bei Überlauf (je nach Vorzeichen von *x*), **gibt _scalb** +/- **HUGE_VAL**zurück; Die **errno-Variable** ist auf **ERANGE**gesetzt.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_scalb-Funktion** berechnet den Wert von *x* \* 2<sup>*exp*</sup>.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_scalb**, **_scalbf**|\<float.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
