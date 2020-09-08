---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
description: API-Referenz für "lrint ()", "lrintf ()", "lrintl ()", "llrint ()", "llrintf ()" und "llrintl ();" rundet den angegebenen Gleit Komma Wert mit dem aktuellen Rundungs Modus und der angegebenen Richtung auf den nächstgelegenen ganzzahligen Wert.
ms.date: 9/1/2020
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
- _o_llrint
- _o_llrintf
- _o_llrintl
- _o_lrint
- _o_lrintf
- _o_lrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: f208c183400aac7a110bb6fd87398d4377fe8f06
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555019"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Rundet den angegebenen Gleitkommawert auf den nächsten ganzzahligen Wert mit dem aktuellen Rundungsmodus und Richtung.

## <a name="syntax"></a>Syntax

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);

#define lrint(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der zu rundende Wert.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, wird der abgerundete ganzzahlige Wert von *x*zurückgegeben.

|Problem|Rückgabewert|
|-----------|------------|
|*x* liegt außerhalb des Bereichs des Rückgabe Typs.<br /><br /> *x* = ± \<br /><br /> *x* = Nan|Löst **FE_INVALID** aus und gibt NULL (0) zurück.|

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **lrint** und **llrint** aufzurufen, die **`float`** -und- **`long double`** Typen verwenden. Wenn Sie in einem C-Programm das \<tgmath.h> -Makro verwenden, um diese Funktion aufzurufen, nehmen **lrint** und **llrint** immer eine **`double`** .

Wenn Sie das- \<tgmath.h> `llrint()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Wenn *x* die Gleit Komma Entsprechung eines ganzzahligen Werts nicht darstellt, erhöhen diese Funktionen **FE_INEXACT**.

**Microsoft-spezifisch**: Wenn das Ergebnis außerhalb des Bereichs des Rückgabe Typs liegt oder wenn der Parameter ein NaN oder unendlich ist, wird der Rückgabewert von der Implementierung definiert. Der Microsoft-Compiler gibt den Wert 0 (null) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|
|**lrint** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)
