---
title: expm1, expm1f, expm1l
ms.date: 04/05/2018
api_name:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 63e984f2228ac6896cd9d2ea959b491565bfb8d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234132"
---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l

Berechnet das base-e-Exponential eines Werts minus eins.

## <a name="syntax"></a>Syntax

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Das Exponential des Gleitkommawerts.

## <a name="return-value"></a>Rückgabewert

Die **expm1** -Funktionen geben einen Gleit Komma Wert zurück, der e<sup>x</sup> -1 darstellt, wenn erfolgreich. Bei einem Überlauf **expm1** gibt expm1 **HUGE_VAL**zurück, **expm1f** gibt **HUGE_VALF**zurück, **expm1l** gibt **HUGE_VALL**zurück, und **errno** wird auf **ERANGE**festgelegt. Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Da C++ das überladen zulässt, können Sie über Ladungen von **expm1** aufzurufen, die **`float`** -und-Werte verwenden und zurückgeben **`long double`** . In einem C-Programm übernimmt **expm1** immer und gibt einen zurück **`double`** .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**expm1**, **expm1f**, **expm1l**|\<math.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
