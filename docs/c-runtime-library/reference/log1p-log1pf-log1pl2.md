---
title: log1p, log1pf, log1pl2
description: API-Referenz für log1p, log1pf, log1pl2; , bei der der natürliche Logarithmus von 1 plus dem angegebenen Wert berechnet wird.
ms.date: 9/1/2020
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
ms.openlocfilehash: 8858d761428d4dad6e3fe836b82041ae92f1827a
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556229"
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

Berechnet den natürlichen Logarithmus von 1 plus den angegebenen Ausdruck.

## <a name="syntax"></a>Syntax

```C
double log1p(
   double x
);
float log1pf(
   float x
);
long double log1pl(
   long double x
);

#define log1p(X) // Requires C11 or higher

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
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

Die **log1p** -Funktionen sind möglicherweise präziser als die Verwendung `log(x + 1)` von, wenn *x* nahe 0 (null) ist.

Da C++ das überladen zulässt, können Sie über Ladungen von **log1p** aufzurufen, die **`float`** -und-Typen verwenden und zurückgeben **`long double`** . Wenn Sie in einem C-Programm nicht das- \<tgmath.h> Makro verwenden, um diese Funktion aufzurufen, führt **log1p** immer einen aus und gibt zurück **`double`** .

Wenn Sie das- \<tgmath.h> `log1p()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Wenn *x* eine natürliche Zahl ist, gibt diese Funktion den Logarithmus der Fakultät von (*x* -1) zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|
|**log1p** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)\
[log2, log2f, log2l](log2-log2f-log2l.md)\
[log, logf, log10, log10f](log-logf-log10-log10f.md)
