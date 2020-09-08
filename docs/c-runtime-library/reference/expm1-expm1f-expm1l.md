---
title: expm1, expm1f, expm1l
description: API-Referenz für expm1, expm1f und expm1; , die den Exponentialwert eines Werts von minus 1 berechnen.
ms.date: 9/1/2020
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
ms.openlocfilehash: 6d352e91d895cd63c7134faff90bc1bc43a50708
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556501"
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
#define expm1(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Das Exponential des Gleitkommawerts.

## <a name="return-value"></a>Rückgabewert

Die **expm1** -Funktionen geben einen Gleit Komma Wert zurück, der e<sup>x</sup> -1 darstellt, wenn erfolgreich. Bei einem Überlauf **expm1** gibt expm1 **HUGE_VAL**zurück, **expm1f** gibt **HUGE_VALF**zurück, **expm1l** gibt **HUGE_VALL**zurück, und **errno** wird auf **ERANGE**festgelegt. Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **expm1** aufzurufen, die **`float`** -und-Werte verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm nicht das- \<tgmath.h> Makro verwenden, um diese Funktion aufzurufen, führt **expm1** immer einen aus und gibt zurück **`double`** .

Wenn Sie das- \<tgmath.h> `expm1()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**expm1**, **expm1f**, **expm1l**|\<math.h>|
|**expm1** -Makro | \<tgmath.h> |

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
