---
title: isfinite, _finite, _finitef
ms.date: 01/31/2019
api_name:
- _finite
- _finitef
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- isfinite
- finite
- _finite
- _finitef
- math/isfinite
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: 7e15a6619e584ff52c07048fcf591835b799587f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218701"
---
# <a name="isfinite-_finite-_finitef"></a>isfinite, _finite, _finitef

Bestimmt, ob ein Gleitkommawert endlich ist.

## <a name="syntax"></a>Syntax

```C
int isfinite(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isfinite(
   FloatingType x
) throw(); /* C++-only template function */

int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der zu testende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Das `isfinite` Makro und die `_finite` -und `_finitef` -Funktionen geben einen Wert ungleich 0 (null) zurück, wenn *x* entweder ein normaler oder ein subnormaler Endwert ist. Sie geben 0 zurück, wenn das Argument unendlich oder ein NaN-Wert ist. Die C++-Inline Vorlagen Funktion `isfinite` verhält sich auf dieselbe Weise, gibt jedoch **`true`** oder zurück **`false`** .

## <a name="remarks"></a>Bemerkungen

`isfinite`ist ein Makro, wenn es als C kompiliert wird, und eine Inline-Vorlagen Funktion, wenn Sie als C++ kompiliert werden. Die `_finite` `_finitef` Funktionen und sind Microsoft-spezifisch. Die Funktion `_finitef` ist nur verfügbar, wenn sie für x86, ARM- oder ARM64-Plattformen kompiliert wurde.

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h> oder \<math.h>|\<float.h>, \<math.h>, \<cfloat> oder \<cmath>|
|`isfinite`, `_finitef`|\<math.h>|\<math.h> oder \<cmath>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
