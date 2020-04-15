---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 92e3a744ef8069d45733c06b7a2681905c3eab55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338587"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Rundet den angegebenen Gleitkommawert auf eine ganze Zahl und gibt diesen Wert in einem Gleitkommaformat zurück.

## <a name="syntax"></a>Syntax

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Parameter

*X*<br/>
Der zu rundende Wert.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, wird *x*zurückgegeben, gerundet auf die nächste ganze Zahl, mit dem aktuellen Rundungsformat, wie von [fegetround](fegetround-fesetround2.md)gemeldet. Andernfalls gibt die Funktion möglicherweise einen der folgenden Werte zurück:

|Problem|Rückgabewert|
|-----------|------------|
|*x* =|•INFINITY, unverändert|
|*x* = 0 €|0, unverändert|
|*x* = NaN|NaN|

Fehler werden nicht über [_matherr](matherr.md)gemeldet. Diese Funktion meldet insbesondere keine **FE_INEXACT** Ausnahmen.

## <a name="remarks"></a>Bemerkungen

Der Hauptunterschied zwischen dieser Funktion und [dem Rint](rint-rintf-rintl.md) besteht darin, dass diese Funktion nicht die ungenaue Gleitkommaausnahme auslöst.

Da die maximalen Gleitkommawerte genaue ganze Zahlen sind, überläuft diese Funktion nie von selbst. Stattdessen ist es möglich, dass der Rückgabewert je nach Version der verwendeten Funktion von der Ausgabe überlaufen wird.

C++ ermöglicht Eine Überlastung, sodass Sie Überladungen von **Nearbyint** aufrufen können, die **Float-** oder **lange** **Doppelparameter** aufnehmen und zurückgeben. In einem **C-Programm nimmt nearbyint** immer zwei Doppeltewerte und gibt einen doppelten Wert zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> oder \<math.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[Mathematische Unterstützung und Gleitkommaunterstützung](../floating-point-support.md)<br/>
