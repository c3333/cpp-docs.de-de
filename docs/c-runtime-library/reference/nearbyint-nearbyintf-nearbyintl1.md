---
title: nearbyint, nearbyintf, nearbyintl
description: API-Referenz für nearbyint, nearbyintf und nearbyintl; rundet den angegebenen Gleit Komma Wert auf eine ganze Zahl auf und gibt diesen Wert in einem Gleit Komma Format zurück.
ms.date: 9/1/2020
api_name:
- nearbyint
- nearbyintf
- nearbyintl
- _o_nearbyint
- _o_nearbyintf
- _o_nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: 9717559518032c6f1f2126c7ded7cb90603bce64
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556384"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Rundet den angegebenen Gleitkommawert auf eine ganze Zahl und gibt diesen Wert in einem Gleitkommaformat zurück.

## <a name="syntax"></a>Syntax

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
#define nearbyint( X ) // Requires C11 or higher

float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der zu rundende Wert.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, wird *x*(auf die nächste ganze Zahl gerundet) zurückgegeben, wobei das aktuelle Rundungs Format verwendet wird, wie von [fegetround](fegetround-fesetround2.md)gemeldet. Andernfalls gibt die Funktion möglicherweise einen der folgenden Werte zurück:

|Problem|Rückgabewert|
|-----------|------------|
|*x* = ± unendlich|± Unendlich, unverändert|
|*x* = ± 0|± 0, unverändert|
|*x* = Nan|NaN|

Fehler werden nicht über [_matherr](matherr.md)gemeldet; Diese Funktion meldet insbesondere keine **FE_INEXACT** Ausnahmen.

## <a name="remarks"></a>Hinweise

Der primäre Unterschied zwischen dieser Funktion und [rint](rint-rintf-rintl.md) besteht darin, dass diese Funktion nicht die inexakte Gleit Komma Ausnahme auslöst.

Da die maximalen Gleitkommawerte genaue ganze Zahlen sind, überläuft diese Funktion nie von selbst. Stattdessen ist es möglich, dass der Rückgabewert je nach Version der verwendeten Funktion von der Ausgabe überlaufen wird.

C++ ermöglicht überladen, sodass Sie über Ladungen von **nearbyint** aufzurufen können, die-oder-Parameter verwenden und zurückgeben **`float`** **`long double`** . Wenn Sie in einem C-Programm diese Funktion nicht mit dem- \<tgmath.h> Makro aufzurufen, verwendet **nearbyint** immer zwei Double-Werte und gibt einen Double-Wert zurück.

Wenn Sie das- \<tgmath.h> `nearbyint()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> oder \<math.h>|
|**nearbyint** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[Mathematische Unterstützung und Gleitkommaunterstützung](../floating-point-support.md)<br/>
