---
title: trunc, truncf, truncl
description: API-Referenz für trunc, truncf, truncl; , die die nächstgelegene Ganzzahl ermitteln, die kleiner oder gleich dem angegebenen Gleit Komma Wert ist.
ms.date: 9/1/2020
api_name:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: f1f2fde95bb944aa461bb95a9ad30fac204552b9
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556631"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Bestimmt die nächste ganze Zahl, die kleiner oder gleich dem angegebenen Gleitkommawert ist.

## <a name="syntax"></a>Syntax

```C
double trunc( double x );
long double truncl( long double x );
#define trunc(X) // Requires C11 or higher

long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der abzuschneidende Wert.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg einen ganzzahligen Wert von *x*zurück, der auf NULL gerundet wird.

Andernfalls wird möglicherweise einer der folgenden Werte zurückgeben:

|Problem|Rückgabewert|
|-----------|------------|
|*x* = ± unendlich|w|
|*x* = ± 0|w|
|*x* = Nan|NaN|

Fehler werden gemäß den Angaben in [_matherr](matherr.md) gemeldet.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **trunc** aufzurufen, die- **`float`** und-Typen verwenden und zurückgeben **`long double`** . In einem C-Programm verwendet trunc immer, wenn Sie das- \<tgmath.h> Makro verwenden **trunc** , um diese Funktion aufzurufen, und gibt es zurück **`double`** .

Wenn Sie das- \<tgmath.h> `trunc()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Da die größten Gleitkommawerte exakte ganze Zahlen sind, wird diese Funktion nicht eigenständig überlaufen. Sie können diese Funktion jedoch möglicherweise bei der Rückgabe eines Werts in einen ganzzahligen Typ zum Überlaufen bringen.

Sie können auch abrunden, indem Sie Gleitkommazahlen implizit in ganzzahlige konvertieren. Dies ist jedoch nur für die Werte möglich, die im Zieltyp gespeichert werden können.

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**trunc**, **truncf**, **truncl**|\<math.h>|\<cmath>|
|**trunc** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
