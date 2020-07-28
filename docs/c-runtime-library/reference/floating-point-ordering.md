---
title: isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 907b26f4e1824d7ef5c7c1a36b4e4d8ccb74c978
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220716"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered

Bestimmt die Reihenfolge Beziehung zwischen zwei Gleit Komma Werten.

## <a name="syntax"></a>Syntax

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parameter

*x*, *y*<br/>
Die zu vergleichenden Gleit Komma Werte.

## <a name="return-value"></a>Rückgabewert

Bei allen vergleichen werden Unendlichkeiten desselben Zeichens als gleich verglichen. Minus unendlich ist kleiner als jeder endliche Wert oder positiv unendlich. "Positiv unendlich" ist größer als jeder endliche Wert oder minus unendlich. Nullen sind unabhängig vom Vorzeichen gleich. Nans sind nicht kleiner, gleich oder größer als ein beliebiger Wert, einschließlich eines anderen NaN-Werts.

Wenn keines der Argumente ein NaN ist, geben die Bestell Makros **isgreater**, **isgreaterequal**, **isless**und **islessequal** einen Wert ungleich 0 (null) zurück, wenn die angegebene Reihenfolge Beziehung zwischen *x* und *y* true ist. Diese Makros geben 0 zurück, wenn ein oder beide Argumente Nane sind oder wenn die Reihenfolge Beziehung false lautet. Die Funktionsformen Verhalten sich auf dieselbe Weise, geben aber **`true`** oder zurück **`false`** .

Das **islessgreater** -Makro gibt einen Wert ungleich 0 (null) zurück, wenn sowohl *x* als auch *y* nicht Nane sind und *x* entweder kleiner als oder größer als *y*ist. Es wird 0 zurückgegeben, wenn eines oder beide Argumente Nane sind oder wenn die Werte gleich sind. Das Funktions Formular verhält sich wie, gibt jedoch **`true`** oder zurück **`false`** .

Das **isungeordnete** -Makro gibt einen Wert ungleich 0 (null) zurück, wenn entweder *x*, *y*oder beides Nane sind. Andernfalls wird 0 zurückgegeben. Das Funktions Formular verhält sich wie, gibt jedoch **`true`** oder zurück **`false`** .

## <a name="remarks"></a>Bemerkungen

Diese Vergleichs Vorgänge werden als Makros implementiert, wenn Sie als C kompiliert werden, und als Inline Vorlagen Funktionen, wenn Sie als C++ kompiliert werden.

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**, **isgreaterequal**, **isless**,<br/>**islessequal**, **islessgreater**, **isunsortiert** | \<math.h> | \<math.h> oder \<cmath> |

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
