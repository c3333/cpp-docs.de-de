---
title: log1p, log1pf, log1pl2
ms.date: 4/2/2020
api_name:
- log1p
- log1pf
- log1pl
- _o_log1p
- _o_log1pf
- _o_log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
ms.openlocfilehash: b4e077f5b806dbe38ed4a4f4e8eef0259170cb7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341810"
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

Berechnet den natürlichen Logarithmus von 1 plus den angegebenen Ausdruck.

## <a name="syntax"></a>Syntax

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Das Gleitkommaargument.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, gibt das natürliche (base-*e*) Protokoll von (*x* + 1) zurück.

Andernfalls wird möglicherweise einer der folgenden Werte zurückgeben:

|Eingabe|Ergebnis|SEH-Ausnahme|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Abbrüche|Identisch mit der Eingabe|UNDERFLOW||
|€0|Identisch mit der Eingabe|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|€SNaN|Identisch mit der Eingabe|INVALID||
|QNaN, unbestimmt|Identisch mit der Eingabe|||

Der **errno-Wert** wird auf ERANGE gesetzt, wenn *x* = -1. Der **errno-Wert** wird auf **EDOM** gesetzt, wenn *x* < -1.

## <a name="remarks"></a>Bemerkungen

Die **log1p-Funktionen** sind möglicherweise `log(x + 1)` genauer als bei Verwendung von *x* in der Nähe von 0.

Da C++ eine Überlastung ermöglicht, können Sie Überladungen von **log1p** aufrufen, die **float** und **lange** **doppelte** Typen aufnehmen und zurückgeben. In einem C-Programm nimmt **log1p** immer eine **doppelte**.

Wenn *x* eine natürliche Zahl ist, gibt diese Funktion den Logarithmus des Faktors von (*x* - 1) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
