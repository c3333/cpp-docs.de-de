---
title: Concurrency::fast_math-Namespace-Funktionen
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: 3652e02d9f3ff7b09ee7334dba20188e40344cb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865469"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math-Namespace-Funktionen

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[asin](#asin)|
|[asinf](#asinf)|[atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[ceil](#ceil)|
|[ceilf](#ceilf)|[cos](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|
|[isFinite](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[log](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[pow](#pow)|[powf](#powf)|
|[round](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[sin](#sin)|[SinCos](#sincos)|[sincosf](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[tan](#tan)|
|[tanf](#tanf)|[tanh](#tanh)|[tanhf](#tanhf)|
|[trunc](#trunc)|[truncf](#truncf)|

## <a name="acos"></a> acos

Berechnet den Arkuskosinus des Arguments

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Arkus Kosinus-Wert des Arguments zurück.

## <a name="acosf"></a>Acosf

Berechnet den Arkuskosinus des Arguments

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Arkus Kosinus-Wert des Arguments zurück.

## <a name="asin"></a> asin

Berechnet den Arkussinus des Arguments

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Arkus Sinus-Wert des Arguments zurück.

## <a name="asinf"></a>asinf

Berechnet den Arkussinus des Arguments

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Arkus Sinus-Wert des Arguments zurück.

## <a name="atan"></a> atan

Berechnet den Arkustangens des Arguments

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Arkus Tangens Wert des Arguments zurück.

## <a name="atan2"></a> atan2

Berechnet den Arkustangens von _Y/_X

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Y*<br/>
Gleitkommawert

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Arkus Tangens Wert _Y/_x

## <a name="atan2f"></a>atan2f

Berechnet den Arkustangens von _Y/_X

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Y*<br/>
Gleitkommawert

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Arkus Tangens Wert _Y/_x

## <a name="atanf"></a>atanf

Berechnet den Arkustangens des Arguments

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Arkus Tangens Wert des Arguments zurück.

## <a name="ceil"></a>ceil

Berechnet die Höchstwert des Arguments

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Obergrenze des Arguments zurück.

## <a name="ceilf"></a>ceilf

Berechnet die Höchstwert des Arguments

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Obergrenze des Arguments zurück.

## <a name="cosf"></a>cosf

Berechnet den Kosinus des Arguments

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kosinus-Wert des Arguments zurück.

## <a name="coshf"></a>coshf

Berechnet den Hyperbelkosinuswert des Arguments

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Kosinus-Wert des Arguments zurück.

## <a name="cos"></a> cos

Berechnet den Kosinus des Arguments

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kosinus-Wert des Arguments zurück.

## <a name="cosh"></a> cosh

Berechnet den Hyperbelkosinuswert des Arguments

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Kosinus-Wert des Arguments zurück.

## <a name="exp"></a> exp

Berechnet die Basis-E, die vom Argument exponential ist

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Exponentialwert des Arguments zurück.

## <a name="exp2"></a>exp2

Berechnet die Basis-2, die vom Argument exponential ist

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Exponenten zur Basis 2 des Arguments zurück.

## <a name="exp2f"></a>exp2f

Berechnet die Basis-2, die vom Argument exponential ist

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Exponenten zur Basis 2 des Arguments zurück.

## <a name="expf"></a>expf

Berechnet die Basis-E, die vom Argument exponential ist

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Exponentialwert des Arguments zurück.

## <a name="fabs"></a>Fabs

Gibt den absoluten Wert des Arguments zurück.

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Gibt den absoluten Wert des Arguments zurück.

## <a name="fabsf"></a>fabsf

Gibt den absoluten Wert des Arguments zurück.

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den absoluten Wert des Arguments zurück.

## <a name="floor"></a>Steh

Berechnet den Tiefstwert des Arguments

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Boden des Arguments zurück.

## <a name="floorf"></a>floorf

Berechnet den Tiefstwert des Arguments

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Boden des Arguments zurück.

## <a name="fmax"></a>Fmax

Festlegung des höchsten numerischen Werts der Argumente

```cpp
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Ganzzahliger Wert

*_Y*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Rückgabe des höchsten numerischen Werts der Argumente

## <a name="fmaxf"></a>fmaxf

Festlegung des höchsten numerischen Werts der Argumente

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgabe des höchsten numerischen Werts der Argumente

## <a name="fmin"></a>FMIN

Festlegung des niedrigsten numerischen Werts der Argumente

```cpp
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Ganzzahliger Wert

*_Y*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Rückgabe des niedrigsten numerischen Werts der Argumente

## <a name="fminf"></a>fminf

Festlegung des niedrigsten numerischen Werts der Argumente

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgabe des niedrigsten numerischen Werts der Argumente

## <a name="fmod"></a>FMOD

Berechnet den Gleitkommarest von _X/_Y

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Gleit Komma Rest von _x/_Y

## <a name="fmodf"></a>fmodf

Berechnet den Gleit Komma Rest von _x/_Y.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Gleit Komma Rest von _x/_Y

## <a name="frexp"></a>frexp

Ruft die Mantisse und den Exponenten von _X ab

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_Exp*<br/>
Gibt den ganzzahligen Exponent _x in einem Gleit Komma Wert zurück.

### <a name="return-value"></a>Rückgabewert

Gibt die Mantisse zurück _x

## <a name="frexpf"></a>frexpf

Ruft die Mantisse und den Exponenten von _X ab

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_Exp*<br/>
Gibt den ganzzahligen Exponent _x in einem Gleit Komma Wert zurück.

### <a name="return-value"></a>Rückgabewert

Gibt die Mantisse zurück _x

## <a name="isfinite"></a>isFinite

Bestimmt, ob das Argument einen über begrenzten Wert verfügt

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn das Argument über einen endlichen Wert verfügt.

## <a name="isinf"></a>isinf

Bestimmt, ob das Argument unendlich ist

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn das Argument über einen unendlichen Wert verfügt.

## <a name="isnan"></a>IsNaN

Bestimmt, ob das Argument ein NaN

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn das Argument einen NaN-Wert aufweist.

## <a name="ldexp"></a>ldexp

Berechnet eine reelle Zahl aus der Mantisse und dem Exponent

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleit Komma Wert, mentisse

*_Exp*<br/>
Ganzzahliger Exponent

### <a name="return-value"></a>Rückgabewert

Gibt _x \* 2 ^ zurück _Exp

## <a name="ldexpf"></a>ldexpf

Berechnet eine reelle Zahl aus der Mantisse und dem Exponent

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleit Komma Wert, mentisse

*_Exp*<br/>
Ganzzahliger Exponent

### <a name="return-value"></a>Rückgabewert

Gibt _x \* 2 ^ zurück _Exp

## <a name="log"></a> log

Berechnet den Basis-E-Logarithmus des Arguments

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Logarithmus der Basis-e des Arguments zurück.

## <a name="log10"></a> log10

Berechnet den Basis-10-Logarithmus des Arguments

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Logarithmus des Arguments zur Basis 10 zurück.

## <a name="log10f"></a>log10f

Berechnet den Basis-10-Logarithmus des Arguments

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Logarithmus des Arguments zur Basis 10 zurück.

## <a name="log2"></a>log2

Berechnet den Logarithmus zur Basis 2 des Arguments.

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Logarithmus zur Basis 2 des Arguments zurück.

## <a name="log2f"></a>log2f

Berechnet den Logarithmus zur Basis 2 des Arguments.

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Logarithmus des Arguments zur Basis 10 zurück.

## <a name="logf"></a>logf

Berechnet den Basis-E-Logarithmus des Arguments

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Logarithmus der Basis-e des Arguments zurück.

## <a name="modf"></a>modf

Teilt _X in Nachkommastellen und ganze Zahlen auf.

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_Ip*<br/>
Empfängt einen ganzzahligen Teil des Werts

### <a name="return-value"></a>Rückgabewert

Gibt den Teil mit Vorzeichen zurück _x

## <a name="modff"></a>modff

Teilt _X in Nachkommastellen und ganze Zahlen auf.

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_Ip*<br/>
Empfängt einen ganzzahligen Teil des Werts

### <a name="return-value"></a>Rückgabewert

Gibt den Teil mit Vorzeichen zurück _x

## <a name="pow"></a> pow

Berechnet _X potenziert mit _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleit Komma Wert, Basis

*_Y*<br/>
Gleit Komma Wert, Exponent

### <a name="return-value"></a>Rückgabewert

Gibt den Wert der _x ausgelöst, die _Y

## <a name="powf"></a>powf

Berechnet _X potenziert mit _Y

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleit Komma Wert, Basis

*_Y*<br/>
Gleit Komma Wert, Exponent

### <a name="return-value"></a>Rückgabewert

## <a name="round"></a>umgekehrt

Rundet _X auf die nächste ganze Zahl

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die nächste ganze Zahl von _x

## <a name="roundf"></a>roundf

Rundet _X auf die nächste ganze Zahl

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die nächste ganze Zahl von _x

## <a name="rsqrt"></a>rsqrt

Gibt den Kehrwert der Quadratwurzel des Arguments zurück

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kehrwert der Quadratwurzel des Arguments zurück

## <a name="rsqrtf"></a>rsqrtf

Gibt den Kehrwert der Quadratwurzel des Arguments zurück

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kehrwert der Quadratwurzel des Arguments zurück

## <a name="signbit"></a>SignBit

Bestimmt, ob das Vorzeichen _x negativ ist.

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn das Vorzeichen _x negativ ist.

## <a name="signbitf"></a>signbitf

Bestimmt, ob das Vorzeichen _x negativ ist.

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt nur dann einen Wert ungleich 0 (null) zurück, wenn das Vorzeichen _x negativ ist.

## <a name="sin"></a> sin

Berechnet den Sinuswert des Arguments

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Sinus Wert des Arguments zurück.

## <a name="sinf"></a>sinf

Berechnet den Sinuswert des Arguments

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Sinus Wert des Arguments zurück.

## <a name="sincos"></a>SinCos

Berechnet Sinus- und Kosinuswert von _X

```cpp
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_S*<br/>
Gibt den Sinus Wert _x

*_C*<br/>
Gibt den Kosinus-Wert _x

## <a name="sincosf"></a>sincosf

Berechnet Sinus- und Kosinuswert von _X

```cpp
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

*_S*<br/>
Gibt den Sinus Wert _x

*_C*<br/>
Gibt den Kosinus-Wert _x

## <a name="sinh"></a> sinh

Berechnet den Hyperbelsinuswert des Arguments

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Sinus Wert des Arguments zurück.

## <a name="sinhf"></a>Sinhf

Berechnet den Hyperbelsinuswert des Arguments

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Sinus Wert des Arguments zurück.

## <a name="sqrt"></a> sqrt

Berechnet den sqfroot-Stamm des Arguments.

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Squre-Stamm des Arguments zurück.

## <a name="sqrtf"></a>sqrtf

Berechnet den sqfroot-Stamm des Arguments.

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Squre-Stamm des Arguments zurück.

## <a name="tan"></a> tan

Berechnet den Tangenswert des Arguments

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Tangens Wert des Arguments zurück.

## <a name="tanf"></a>TANF

Berechnet den Tangenswert des Arguments

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Tangens Wert des Arguments zurück.

## <a name="tanh"></a> tanh

Berechnet den Hyperbeltangenswert des Arguments

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Tangens Wert des Arguments zurück.

## <a name="tanhf"></a>tanhf

Berechnet den Hyperbeltangenswert des Arguments

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Tangens Wert des Arguments zurück.

## <a name="trunc"></a>trunc

Schneidet das Argument der ganzzahligen Komponente ab

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die ganzzahlige Komponente des Arguments zurück.

## <a name="truncf"></a>truncf

Schneidet das Argument der ganzzahligen Komponente ab

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_X*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die ganzzahlige Komponente des Arguments zurück.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amp_math. h- **Namespace:** Parallelität:: fast_math

## <a name="see-also"></a>Weitere Informationen

[Concurrency::fast_math Namespace](concurrency-fast-math-namespace.md)
