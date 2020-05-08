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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 21bba72b204f975b806e43cdc6d36d8efa173b9b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911428"
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

*x*<br/>
Das Gleitkommaargument.

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung wird das natürliche Protokoll (Base-*e*) von (*x* + 1) zurückgegeben.

Andernfalls wird möglicherweise einer der folgenden Werte zurückgeben:

|Eingabe|Ergebnis|SEH-Ausnahme|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Abbrüche|Identisch mit der Eingabe|UNDERFLOW||
|± 0|Identisch mit der Eingabe|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|± Snan|Identisch mit der Eingabe|INVALID||
|± QNAN, unbegrenzt|Identisch mit der Eingabe|||

Der **errno** -Wert ist auf ERANGE festgelegt, wenn *x* =-1. Der **errno** -Wert ist auf **Edom** festgelegt, wenn *x* <-1.

## <a name="remarks"></a>Hinweise

Die **log1p** -Funktionen sind möglicherweise präziser als `log(x + 1)` die Verwendung von, wenn *x* nahe 0 (null) ist.

Da C++ das überladen zulässt, können Sie über Ladungen von **log1p** aufzurufen, die **float** -und **Long** **Double** -Typen annehmen und zurückgeben. In einem C-Programm nimmt **log1p** immer einen **Double**-Wert an und gibt ihn zurück.

Wenn *x* eine natürliche Zahl ist, gibt diese Funktion den Logarithmus der Fakultät von (*x* -1) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
