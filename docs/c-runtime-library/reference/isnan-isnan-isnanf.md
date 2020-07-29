---
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: 5aebacd15000e0202a26f600614900390c1ba7a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213540"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan, _isnan, _isnanf

Testet, ob ein Gleitkommawert keine Zahl ist (NAN).

## <a name="syntax"></a>Syntax

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der zu testende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

In C geben das **isNaN** -Makro und die Funktionen **_isnan** und **_isnanf** einen Wert ungleich 0 (null) zurück, wenn das Argument *x* ein NaN-Wert ist. Andernfalls wird 0 zurückgegeben.

In C++ gibt die **isNaN** -Vorlagen Funktion zurück, **`true`** Wenn das Argument *x* ein NaN ist; andernfalls wird zurückgegeben **`false`** .

## <a name="remarks"></a>Bemerkungen

Da ein NaN-Wert nicht mit einem anderen NaN-Wert übereinstimmt, müssen Sie eine dieser Funktionen oder Makros verwenden, um eine zu erkennen. Ein NaN-Wert wird generiert, wenn das Ergebnis einer Gleit Komma Operation nicht im IEEE-754-Gleit Komma Format für den angegebenen Typ dargestellt werden kann. Informationen dazu, wie ein NaN für die Ausgabe dargestellt wird, finden Sie unter [printf](printf-printf-l-wprintf-wprintf-l.md).

Bei der Kompilierung als C++ ist das **isNaN** -Makro nicht definiert, und stattdessen wird eine **isNaN** -Vorlagen Funktion definiert. Sie verhält sich genauso wie das Makro, gibt jedoch einen Wert vom Typ **`bool`** anstelle einer Ganzzahl zurück.

Die Funktionen **_isnan** und **_isnanf** sind Microsoft-spezifisch. Die **_isnanf** -Funktion ist nur verfügbar, wenn Sie für x64 kompiliert wird.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN**, **_isnanf**|\<math.h>|\<math.h> oder \<cmath>|
|**_isnan**|\<float.h>|\<float.h> oder \<cfloat>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
