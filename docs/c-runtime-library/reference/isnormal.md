---
title: isnormal
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: 2e12cabb57f2e51c08b4d93af33dae85164d016b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213527"
---
# <a name="isnormal"></a>isnormal

Bestimmt, ob ein Gleit Komma Wert ein normaler Wert ist.

## <a name="syntax"></a>Syntax

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only function template */
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der zu testende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

**isnormal** gibt einen Wert ungleich 0 (null) zurück ( **`true`** in C++-Code), wenn das Argument *x* weder NULL, subnormal, unendlich noch ein NaN ist. Andernfalls gibt **isnormal** 0 ( **`false`** in C++-Code) zurück.

## <a name="remarks"></a>Bemerkungen

**isnormal** ist ein Makro, wenn es als C kompiliert wird, und eine Inline Funktions Vorlage, wenn Sie als C++ kompiliert werden.

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<math.h> oder \<cmath>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
