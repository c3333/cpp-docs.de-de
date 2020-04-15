---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 6283cffaa094af4484d48781b5bb92d0339d38d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341670"
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
```

### <a name="parameters"></a>Parameter

*X*<br/>
Der zu rundende Wert.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, gibt der gerundete Integralwert von *x*zurück.

|Problem|Rückgabewert|
|-----------|------------|
|*x* liegt außerhalb des Bereichs des Rückgabetyps<br /><br /> *x* =<br /><br /> *x* = NaN|Erhöht **FE_INVALID** und gibt Null (0) zurück.|

## <a name="remarks"></a>Bemerkungen

Da C++ eine Überlastung ermöglicht, können Sie Überladungen von **lrint** und **llrint** aufrufen, die **float-** und **lange** **Doppeltypen** annehmen. In einem C-Programm nehmen **lrint** und **llrint** immer ein **Double**.

Wenn *x* nicht das Gleitkommaäquivalent eines integralen Wertes darstellt, erhöhen diese Funktionen **FE_INEXACT**.

**Microsoft-spezifisch:** Wenn das Ergebnis außerhalb des Bereichs des Rückgabetyps liegt oder wenn der Parameter ein NaN oder unendlich ist, ist der Rückgabewert Implementierung definiert. Der Microsoft-Compiler gibt den Wert 0 (null) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
