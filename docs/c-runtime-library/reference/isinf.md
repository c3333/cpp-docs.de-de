---
title: isinf
ms.date: 01/31/2019
f1_keywords:
- isinf
- math/isinf
helpviewer_keywords:
- isinf function
ms.openlocfilehash: 7366f340477bf1bb50ebe1e53bcec1f3e16e0863
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234093"
---
# <a name="isinf"></a>isinf

Bestimmt, ob ein Gleit Komma Wert unendlich ist.

## <a name="syntax"></a>Syntax

```C
int isinf(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isinf(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der zu testende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

**isinf** gibt einen Wert ungleich 0 (null) zurück ( **`true`** in C++-Code), wenn das Argument *x* ein positives oder negatives Unendlichkeits Wert ist. **isinf** gibt 0 ( **`false`** in C++-Code) zurück, wenn das Argument Finite oder NaN ist. Sowohl normale als auch subnormale Gleit Komma Werte werden als Endpunkte betrachtet.

## <a name="remarks"></a>Bemerkungen

**isinf** ist ein Makro, wenn es als C kompiliert wird, und eine Inline-Vorlagen Funktion, wenn Sie als C++ kompiliert werden.

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|--------------|---------------------------|-------------------------------|
|**isinf**|\<math.h>|\<math.h> oder \<cmath>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
