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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: debb617afea26437df16150592e631461d82c6b8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918220"
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

*x*<br/>
Gleitkommawert mit doppelter Genauigkeit.

*Exp*<br/>
Ganzzahlexponent.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg einen Exponentialwert zurück. Bei einem Überlauf (abhängig vom Vorzeichen von *x*) gibt **_scalb** +/- **HUGE_VAL**; zurück. die **errno** -Variable ist auf **ERANGE**festgelegt.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_scalb** -Funktion berechnet den Wert von *x* \* 2<sup>*Exp*</sup>.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_scalb** **_scalbf**|\<float.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
