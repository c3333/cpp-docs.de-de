---
title: log2, log2f, log2l
ms.date: 4/2/2020
api_name:
- log2
- log2l
- log2f
- _o_log2
- _o_log2f
- _o_log2l
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
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: 58da7790e6fbce915c16a02a1b0d972a6fe1049e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911420"
---
# <a name="log2-log2f-log2l"></a>log2, log2f, log2l

Bestimmt den binären Logarithmus (Basis 2) des angegebenen Werts.

## <a name="syntax"></a>Syntax

```C
double log2(
   double x
);

float log2(
   float x
); //C++ only

long double log2(
   long double x
); //C++ only

float log2f(
   float x
);

long double log2l(
   long double x
);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der Wert, um den Basis 2-Logarithmus zu bestimmen.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg wird return log2 *x*zurückgegeben.

Andernfalls wird möglicherweise einer der folgenden Werte zurückgeben:

|Problem|Rückgabewert|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ± 0|-UNENDLICH|
|*x* = 1|+0|
|+INFINITY|+INFINITY|
|NaN|NaN|
|Domänenfehler|NaN|
|pole-Fehler|-HUGE_VAL, -HUGE_VALF, oder -HUGE_VALL|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Hinweise

Wenn x eine ganze Zahl ist, gibt diese Funktion im Grunde den NULL basierten Index des signifikantesten 1 Bits von *x*zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**log2**, **log2f**, **log2l**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
