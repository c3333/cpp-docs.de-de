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
ms.openlocfilehash: 898544f5b191eb68e0ed6f17d7c3c7df849e8d11
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216855"
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

*x*<br/>
Der zu rundende Wert.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, wird *x*(auf die nächste ganze Zahl gerundet) zurückgegeben, wobei das aktuelle Rundungs Format verwendet wird, wie von [fegetround](fegetround-fesetround2.md)gemeldet. Andernfalls gibt die Funktion möglicherweise einen der folgenden Werte zurück:

|Problem|Rückgabewert|
|-----------|------------|
|*x* = ± unendlich|± Unendlich, unverändert|
|*x* = ± 0|± 0, unverändert|
|*x* = Nan|NaN|

Fehler werden nicht über [_matherr](matherr.md)gemeldet; Diese Funktion meldet insbesondere keine **FE_INEXACT** Ausnahmen.

## <a name="remarks"></a>Bemerkungen

Der primäre Unterschied zwischen dieser Funktion und [rint](rint-rintf-rintl.md) besteht darin, dass diese Funktion nicht die inexakte Gleit Komma Ausnahme auslöst.

Da die maximalen Gleitkommawerte genaue ganze Zahlen sind, überläuft diese Funktion nie von selbst. Stattdessen ist es möglich, dass der Rückgabewert je nach Version der verwendeten Funktion von der Ausgabe überlaufen wird.

C++ ermöglicht überladen, sodass Sie über Ladungen von **nearbyint** aufzurufen können, die-oder-Parameter verwenden und zurückgeben **`float`** **`long double`** . In einem C-Programm übernimmt **nearbyint** immer zwei Double-Werte und gibt einen Double-Wert zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|C-Header|C++-Header|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> oder \<math.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[Mathematische Unterstützung und Gleitkommaunterstützung](../floating-point-support.md)<br/>
