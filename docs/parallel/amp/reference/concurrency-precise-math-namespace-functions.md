---
title: Concurrency::precise_math-Namespace-Funktionen
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::precise_math::acos
- amp_math/Concurrency::precise_math::acosh
- amp_math/Concurrency::precise_math::acoshf
- amp_math/Concurrency::precise_math::asinf
- amp_math/Concurrency::precise_math::asinh
- amp_math/Concurrency::precise_math::atan
- amp_math/Concurrency::precise_math::atan2
- amp_math/Concurrency::precise_math::atanf
- amp_math/Concurrency::precise_math::atanh
- amp_math/Concurrency::precise_math::cbrt
- amp_math/Concurrency::precise_math::cbrtf
- amp_math/Concurrency::precise_math::ceilf
- amp_math/Concurrency::precise_math::copysign
- amp_math/Concurrency::precise_math::cos
- amp_math/Concurrency::precise_math::cosf
- amp_math/Concurrency::precise_math::coshf
- amp_math/Concurrency::precise_math::cospi
- amp_math/Concurrency::precise_math::erf
- amp_math/Concurrency::precise_math::erfc
- amp_math/Concurrency::precise_math::erfcinv
- amp_math/Concurrency::precise_math::erfcinvf
- amp_math/Concurrency::precise_math::erfinv
- amp_math/Concurrency::precise_math::erfinvf
- amp_math/Concurrency::precise_math::exp10
- amp_math/Concurrency::precise_math::exp10f
- amp_math/Concurrency::precise_math::exp2f
- amp_math/Concurrency::precise_math::expf
- amp_math/Concurrency::precise_math::expm1f
- amp_math/Concurrency::precise_math::fabs
- amp_math/Concurrency::precise_math::floor
- amp_math/Concurrency::precise_math::fdim
- amp_math/Concurrency::precise_math::floorf
- amp_math/Concurrency::precise_math::fmaf
- amp_math/Concurrency::precise_math::fmaxf
- amp_math/Concurrency::precise_math::fmin
- amp_math/Concurrency::precise_math::fmod
- amp_math/Concurrency::precise_math::fmodf
- amp_math/Concurrency::precise_math::frexp
- amp_math/Concurrency::precise_math::frexpf
- amp_math/Concurrency::precise_math::hypotf
- amp_math/Concurrency::precise_math::ilogb
- amp_math/Concurrency::precise_math::isfinite
- amp_math/Concurrency::precise_math::isinf
- amp_math/Concurrency::precise_math::isnormal
- amp_math/Concurrency::precise_math::ldexp
- amp_math/Concurrency::precise_math::lgamma
- amp_math/Concurrency::precise_math::lgammaf
- amp_math/Concurrency::precise_math::log10
- amp_math/Concurrency::precise_math::log10f
- amp_math/Concurrency::precise_math::log1pf
- amp_math/Concurrency::precise_math::log2
- amp_math/Concurrency::precise_math::logb
- amp_math/Concurrency::precise_math::logbf
- amp_math/Concurrency::precise_math::modf
- amp_math/Concurrency::precise_math::modff
- amp_math/Concurrency::precise_math::nanf
- amp_math/Concurrency::precise_math::nearbyint
- amp_math/Concurrency::precise_math::nextafter
- amp_math/Concurrency::precise_math::nextafterf
- amp_math/Concurrency::precise_math::phif
- amp_math/Concurrency::precise_math::pow
- amp_math/Concurrency::precise_math::probit
- amp_math/Concurrency::precise_math::probitf
- amp_math/Concurrency::precise_math::rcbrtf
- amp_math/Concurrency::precise_math::remainder
- amp_math/Concurrency::precise_math::remquo
- amp_math/Concurrency::precise_math::remquof
- amp_math/Concurrency::precise_math::roundf
- amp_math/Concurrency::precise_math::rsqrt
- amp_math/Concurrency::precise_math::scalb
- amp_math/Concurrency::precise_math::scalbf
- amp_math/Concurrency::precise_math::scalbnf
- amp_math/Concurrency::precise_math::signbit
- amp_math/Concurrency::precise_math::sin
- amp_math/Concurrency::precise_math::sincos
- amp_math/Concurrency::precise_math::sinf
- amp_math/Concurrency::precise_math::sinh
- amp_math/Concurrency::precise_math::sinpi
- amp_math/Concurrency::precise_math::sinpif
- amp_math/Concurrency::precise_math::sqrtf
- amp_math/Concurrency::precise_math::tan
- amp_math/Concurrency::precise_math::tanh
- amp_math/Concurrency::precise_math::tanhf
- amp_math/Concurrency::precise_math::tanpif
- amp_math/Concurrency::precise_math::tgamma
- amp_math/Concurrency::precise_math::trunc
- amp_math/Concurrency::precise_math::truncf
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
ms.openlocfilehash: ee6ab2313fbdc288ebba1b3fdacf192b7b578eb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321847"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math-Namespace-Funktionen

||||
|-|-|-|
|[Acos](#acos)|[acosf](#acosf)|[acosh](#acosh)|
|[acoshf](#acoshf)|[Asin](#asin)|[asinf](#asinf)|
|[asinh](#asinh)|[asinhf](#asinhf)|[Atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[ceil](#ceil)|[ceilf](#ceilf)|
|[Copysign](#copysign)|[copysignf](#copysignf)|[Cos](#cos)|
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|
|[cospi](#cospi)|[cospif](#cospif)|[Erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv](#erfinv)|
|[erfinvf](#erfinvf)|[Exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[Boden](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isfinit](#isfinite)|
|[isinf](#isinf)|[Isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[Protokoll](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[nextafterf](#nextafterf)|[Phi](#phi)|[phif](#phif)|
|[Pow](#pow)|[powf](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[Rest](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[Runde](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[Sünde](#sin)|
|[sincos](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[sinpi](#sinpi)|
|[sinpif](#sinpif)|[Sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[Tan](#tan)|[tanf](#tanf)|[Tanh](#tanh)|
|[tanhf](#tanhf)|[tanpi](#tanpi)|[tanpif](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[Trunc](#trunc)|
|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>Acos

Berechnet den Arkuskosinus des Arguments

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den arccosine-Wert des Arguments zurück

## <a name="acosf"></a><a name="acosf"></a>acosf

Berechnet den Arkuskosinus des Arguments

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den arccosine-Wert des Arguments zurück

## <a name="acosh"></a><a name="acosh"></a>acosh

Berechnet den inversen hyperbolischen Kosinus des Arguments

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den inversen hyperbolischen Kosinuswert des Arguments zurück

## <a name="acoshf"></a><a name="acoshf"></a>acoshf

Berechnet den inversen hyperbolischen Kosinus des Arguments

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den inversen hyperbolischen Kosinuswert des Arguments zurück

## <a name="asin"></a><a name="asin"></a>Asin

Berechnet den Arkussinus des Arguments

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den arcsine-Wert des Arguments zurück

## <a name="asinf"></a><a name="asinf"></a>asinf

Berechnet den Arkussinus des Arguments

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den arcsine-Wert des Arguments zurück

## <a name="asinh"></a><a name="asinh"></a>asinh

Berechnet den inversen hyperbolischen Sinus des Arguments

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den inversen hyperbolischen Sinuswert des Arguments zurück

## <a name="asinhf"></a><a name="asinhf"></a>asinhf

Berechnet den inversen hyperbolischen Sinus des Arguments

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den inversen hyperbolischen Sinuswert des Arguments zurück

## <a name="atan"></a><a name="atan"></a>Atan

Berechnet den Arkustangens des Arguments

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den arctangent-Wert des Arguments zurück

## <a name="atan2"></a><a name="atan2"></a>atan2

Berechnet den Arkustangens von _Y/_X

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);

inline double atan2(
    double _Y,
    double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Y*<br/>
Gleitkommawert

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den arctangent-Wert von _Y/_X zurück.

## <a name="atan2f"></a><a name="atan2f"></a>atan2f

Berechnet den Arkustangens von _Y/_X

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Y*<br/>
Gleitkommawert

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den arctangent-Wert von _Y/_X zurück.

## <a name="atanf"></a><a name="atanf"></a>atanf

Berechnet den Arkustangens des Arguments

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den arctangent-Wert des Arguments zurück

## <a name="atanh"></a><a name="atanh"></a>atanh

Berechnet die inverse hyperbolische Tangente des Arguments

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den inversen hyperbolischen Tangentenwert des Arguments zurück

## <a name="atanhf"></a><a name="atanhf"></a>atanhf

Berechnet die inverse hyperbolische Tangente des Arguments

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den inversen hyperbolischen Tangentenwert des Arguments zurück

## <a name="cbrt"></a><a name="cbrt"></a>cbrt

Berechnet die tatsächliche Cube-Wurzel des Arguments

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die tatsächliche Cubewurzel des Arguments zurück

## <a name="cbrtf"></a><a name="cbrtf"></a>cbrtf

Berechnet die tatsächliche Cube-Wurzel des Arguments

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die tatsächliche Cubewurzel des Arguments zurück

## <a name="ceil"></a><a name="ceil"></a>ceil

Berechnet die Höchstwert des Arguments

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Obergrenze des Arguments zurück

## <a name="ceilf"></a><a name="ceilf"></a>ceilf

Berechnet die Höchstwert des Arguments

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Obergrenze des Arguments zurück

## <a name="copysign"></a><a name="copysign"></a>Copysign

Erzeugt einen Wert mit der Größe von _X und dem Zeichen von _Y

```cpp
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert mit der Größe von _X und dem Vorzeichen _Y

## <a name="copysignf"></a><a name="copysignf"></a>copysignf

Erzeugt einen Wert mit der Größe von _X und dem Zeichen von _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert mit der Größe von _X und dem Vorzeichen _Y

## <a name="cos"></a><a name="cos"></a>Cos

Berechnet den Kosinus des Arguments

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kosinuswert des Arguments zurück

## <a name="cosf"></a><a name="cosf"></a>cosf

Berechnet den Kosinus des Arguments

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kosinuswert des Arguments zurück

## <a name="cosh"></a><a name="cosh"></a>Cosh

Berechnet den Hyperbelkosinuswert des Arguments

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Kosinuswert des Arguments zurück

## <a name="coshf"></a><a name="coshf"></a>coshf

Berechnet den Hyperbelkosinuswert des Arguments

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Kosinuswert des Arguments zurück

## <a name="cospi"></a><a name="cospi"></a>cospi

Berechnet den Kosinuswert von \* pi _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kosinuswert \* von pi _X zurück

## <a name="cospif"></a><a name="cospif"></a>cospif

Berechnet den Kosinuswert von \* pi _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kosinuswert \* von pi _X zurück

## <a name="erf"></a><a name="erf"></a>Erf

Berechnet die Fehlerfunktion von _X

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Fehlerfunktion von _X zurück

## <a name="erfc"></a><a name="erfc"></a>erfc

Berechnet die komplementäre Fehlerfunktion von _X

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die komplementäre Fehlerfunktion von _X

## <a name="erfcf"></a><a name="erfcf"></a>erfcf

Berechnet die komplementäre Fehlerfunktion von _X

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die komplementäre Fehlerfunktion von _X

## <a name="erfcinv"></a><a name="erfcinv"></a>erfcinv

Berechnet die inverse komplementäre Fehlerfunktion von _X

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die inverse komplementäre Fehlerfunktion von _X

## <a name="erfcinvf"></a><a name="erfcinvf"></a>erfcinvf

Berechnet die inverse komplementäre Fehlerfunktion von _X

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die inverse komplementäre Fehlerfunktion von _X

## <a name="erff"></a><a name="erff"></a>erff

Berechnet die Fehlerfunktion von _X

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Fehlerfunktion von _X zurück

## <a name="erfinv"></a><a name="erfinv"></a>erfinv

Berechnet die inverse Fehlerfunktion von _X

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die inverse Fehlerfunktion von _X zurück

## <a name="erfinvf"></a><a name="erfinvf"></a>erfinvf

Berechnet die inverse Fehlerfunktion von _X

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die inverse Fehlerfunktion von _X zurück

## <a name="exp10"></a><a name="exp10"></a>exp10

Berechnet die Basis-10 exponentiell des Arguments

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Basis-10 exponentiell des Arguments zurück

## <a name="exp10f"></a><a name="exp10f"></a>exp10f

Berechnet die Basis-10 exponentiell des Arguments

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Basis-10 exponentiell des Arguments zurück

## <a name="expm1"></a><a name="expm1"></a>expm1

Berechnet die Basis-E, die vom Argument exponential ist, minus 1

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Parameter

*Exponent*<br/>
Der exponentielle Begriff *n* des mathematischen Ausdrucks `e` <sup>n</sup>, wobei `e` die Basis des natürlichen Logarithmus ist.

### <a name="return-value"></a>Rückgabewert

Gibt die Basis-E, die vom Argument exponential ist, minus 1 zurück

## <a name="expm1f"></a><a name="expm1f"></a>expm1f

Berechnet die Basis-E, die vom Argument exponential ist, minus 1

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Parameter

*Exponent*<br/>
Der exponentielle Begriff *n* des mathematischen Ausdrucks `e` <sup>n</sup>, wobei `e` die Basis des natürlichen Logarithmus ist.

### <a name="return-value"></a>Rückgabewert

Gibt die Basis-E, die vom Argument exponential ist, minus 1 zurück

## <a name="exp"></a><a name="exp"></a>Exp

Berechnet die Basis-E, die vom Argument exponential ist

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt das Base-e exponentiell des Arguments zurück

## <a name="expf"></a><a name="expf"></a>expf

Berechnet die Basis-E, die vom Argument exponential ist

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt das Base-e exponentiell des Arguments zurück

## <a name="exp2"></a><a name="exp2"></a>exp2

Berechnet die Basis-2, die vom Argument exponential ist

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Exponenten zur Basis 2 des Arguments zurück.

## <a name="exp2f"></a><a name="exp2f"></a>exp2f

Berechnet die Basis-2, die vom Argument exponential ist

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Exponenten zur Basis 2 des Arguments zurück.

## <a name="fabs"></a><a name="fabs"></a>fabs

Gibt den absoluten Wert des Arguments zurück.

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den absoluten Wert des Arguments zurück.

## <a name="fabsf"></a><a name="fabsf"></a>fabsf

Gibt den absoluten Wert des Arguments zurück.

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den absoluten Wert des Arguments zurück.

## <a name="fdim"></a><a name="fdim"></a>fdim

Berechnet den positiven Unterschied zwischen den Argumenten.

```cpp
inline float fdim(
   float _X,
   float _Y
) restrict(amp);
inline double fdim(
   double _X,
   double _Y
) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert *_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Der Unterschied zwischen _X und _Y, wenn _X größer als _Y ist; andernfalls +0.

## <a name="fdimf"></a><a name="fdimf"></a>fdimf

Berechnet den positiven Unterschied zwischen den Argumenten.

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert *_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Der Unterschied zwischen _X und _Y, wenn _X größer als _Y ist; andernfalls +0.

## <a name="floor"></a><a name="floor"></a>Boden

Berechnet den Tiefstwert des Arguments

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Boden des Arguments zurück

## <a name="floorf"></a><a name="floorf"></a>floorf

Berechnet den Tiefstwert des Arguments

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Boden des Arguments zurück

## <a name="a-namefma-fma"></a><a name="fma">Fma

Berechnet das Produkt des ersten und zweiten angegebenen Arguments, fügt dann das dritte angegebene Argument dem Ergebnis hinzu. Die gesamte Berechnung wird als einzelner Vorgang ausgeführt.

```cpp
inline float fma(
   float _X,
   float _Y,
   float _Z
) restrict(amp);

inline double fma(
   double _X,
   double _Y,
   double _Z
) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Das erste Gleitkommaargument.
*_Y*<br/>
Das zweite Gleitkommaargument.
*_Z*<br/>
Das dritte Gleitkommaargument.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Ausdrucks (_X \* _Y) + _Z. Die gesamte Berechnung wird als einzelner Vorgang ausgeführt; das heißt, die Teilausdrücke werden mit unendlicher Genauigkeit berechnet und nur das Endergebnis wird gerundet.

## <a name="fmaf"></a><a name="fmaf"></a>fmaf

Berechnet das Produkt des ersten und zweiten angegebenen Arguments, fügt dann das dritte angegebene Argument dem Ergebnis hinzu. Die gesamte Berechnung wird als einzelner Vorgang ausgeführt.

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Das erste Gleitkommaargument.
*_Y*<br/>
Das zweite Gleitkommaargument.
*_Z*<br/>
Das dritte Gleitkommaargument.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis des Ausdrucks (_X \* _Y) + _Z. Die gesamte Berechnung wird als einzelner Vorgang ausgeführt; das heißt, die Teilausdrücke werden mit unendlicher Genauigkeit berechnet und nur das Endergebnis wird gerundet.

## <a name="fmax"></a><a name="fmax"></a>Fmax

Festlegung des höchsten numerischen Werts der Argumente

```cpp
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgabe des höchsten numerischen Werts der Argumente

## <a name="fmaxf"></a><a name="fmaxf"></a>fmaxf

Festlegung des höchsten numerischen Werts der Argumente

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgabe des höchsten numerischen Werts der Argumente

## <a name="fmin"></a><a name="fmin"></a>fmin

Festlegung des niedrigsten numerischen Werts der Argumente

```cpp
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgabe des niedrigsten numerischen Werts der Argumente

## <a name="fminf"></a><a name="fminf"></a>fminf

Festlegung des niedrigsten numerischen Werts der Argumente

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgabe des niedrigsten numerischen Werts der Argumente

## <a name="fmod-function-c-amp"></a><a name="fmod"></a>fmod-Funktion (C++ AMP)

Berechnet den Rest des angegebenen ersten Arguments dividiert durch das zweite angegebene Argument.

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Das erste Gleitkommaargument.

*_Y*<br/>
Das zweite Gleitkommaargument.

### <a name="return-value"></a>Rückgabewert

Der Rest `_X` geteilt `_Y`durch ; d. h. `_X`  -  `_Y`der Wert von *n*, wobei *n* eine `_X`  -  `_Y`ganze ganze Ganze B/000 ist, so dass die Größe von *n* kleiner als die Magnitude von `_Y`ist.

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

Berechnet den Rest des angegebenen ersten Arguments dividiert durch das zweite angegebene Argument.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Das erste Gleitkommaargument.

*_Y*<br/>
Das zweite Gleitkommaargument.

### <a name="return-value"></a>Rückgabewert

Der Rest `_X` geteilt `_Y`durch ; d. h. `_X`  -  `_Y`der Wert von *n*, wobei *n* eine `_X`  -  `_Y`ganze ganze Ganze B/000 ist, so dass die Größe von *n* kleiner als die Magnitude von `_Y`ist.

## <a name="fpclassify"></a><a name="fpclassify"></a>fpklassifizieren

Klassifiziert den Argumentwert als NaN, unendlich, normal, subnormal, Null

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Wert des Zahlenklassifizierungsmakros zurück, das dem Wert des Arguments entspricht.

## <a name="frexp"></a><a name="frexp"></a>frexp

Ruft die Mantisse und den Exponenten von _X ab

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Exp*<br/>
Gibt den Ganzzahlexponenten von _X im Gleitkommawert zurück.

### <a name="return-value"></a>Rückgabewert

Gibt die Mantissa _X zurück

## <a name="frexpf"></a><a name="frexpf"></a>frexpf

Ruft die Mantisse und den Exponenten von _X ab

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Exp*<br/>
Gibt den Ganzzahlexponenten von _X im Gleitkommawert zurück.

### <a name="return-value"></a>Rückgabewert

Gibt die Mantissa _X zurück

## <a name="hypot"></a><a name="hypot"></a>hypot

Berechnet die Quadratwurzel der Summe der Quadrate von _X und _Y

```cpp
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Quadratwurzel der Summe der Quadrate von _X und _Y zurück.

## <a name="hypotf"></a><a name="hypotf"></a>hypotf

Berechnet die Quadratwurzel der Summe der Quadrate von _X und _Y

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Quadratwurzel der Summe der Quadrate von _X und _Y zurück.

## <a name="ilogb"></a><a name="ilogb"></a>ilogb

Extrahieren Sie den Exponenten von _X als signierten Int-Wert

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Exponenten von _X als signierten Int-Wert zurück.

## <a name="ilogbf"></a><a name="ilogbf"></a>ilogbf

Extrahieren Sie den Exponenten von _X als signierten Int-Wert

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Exponenten von _X als signierten Int-Wert zurück.

## <a name="isfinite"></a><a name="isfinite"></a>isfinit

Bestimmt, ob das Argument einen über begrenzten Wert verfügt

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert ungleich Null zurück, wenn und nur wenn das Argument einen endlichen Wert hat

## <a name="isinf"></a><a name="isinf"></a>isinf

Bestimmt, ob das Argument unendlich ist

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert ungleich Null zurück, wenn und nur wenn das Argument einen unendlichen Wert hat

## <a name="isnan"></a><a name="isnan"></a>Isnan

Bestimmt, ob das Argument ein NaN

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert ungleich Null zurück, wenn und nur wenn das Argument einen NaN-Wert hat

## <a name="isnormal"></a><a name="isnormal"></a>isnormal

Bestimmt, ob das Argument ein normaler

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert ungleich Null zurück, wenn und nur wenn das Argument einen Normalwert hat

## <a name="ldexp"></a><a name="ldexp"></a>ldexp

Berechnet eine reelle Zahl aus der angegebenen Mantisse und dem Exponent.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert, Mantisse

*_Exp*<br/>
Ganze Zahl, Exponent

### <a name="return-value"></a>Rückgabewert

Gibt \* _X 2-_Exp zurück

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf

Berechnet eine reelle Zahl aus der angegebenen Mantisse und dem Exponent.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert, Mantisse

*_Exp*<br/>
Ganze Zahl, Exponent

### <a name="return-value"></a>Rückgabewert

Gibt \* _X 2-_Exp zurück

## <a name="lgamma"></a><a name="lgamma"></a>lgamma

Berechnet den natürlichen Logarithmus des absoluten Wertes von Gamma des Arguments

```cpp
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Sign*<br/>
Gibt das Zeichen zurück

### <a name="return-value"></a>Rückgabewert

Gibt den natürlichen Logarithmus des absoluten Wertes von Gamma des Arguments zurück

## <a name="lgammaf"></a><a name="lgammaf"></a>lgammaf

Berechnet den natürlichen Logarithmus des absoluten Wertes von Gamma des Arguments

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Sign*<br/>
Gibt das Zeichen zurück

### <a name="return-value"></a>Rückgabewert

Gibt den natürlichen Logarithmus des absoluten Wertes von Gamma des Arguments zurück

## <a name="log"></a><a name="log"></a>Protokoll

Berechnet den Basis-E-Logarithmus des Arguments

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Basislogarithmus des Arguments zurück

## <a name="log10"></a><a name="log10"></a>log10

Berechnet den Basis-10-Logarithmus des Arguments

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Basis-10-Logarithmus des Arguments zurück

## <a name="log10f"></a><a name="log10f"></a>log10f

Berechnet den Basis-10-Logarithmus des Arguments

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Basis-10-Logarithmus des Arguments zurück

## <a name="log1p"></a><a name="log1p"></a>log1p

Berechnet den Basis-e Logarithmus von 1 plus das Argument

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Basislogarithmus von 1 plus das Argument zurück.

## <a name="log1pf"></a><a name="log1pf"></a>log1pf

Berechnet den Basis-e Logarithmus von 1 plus das Argument

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Basislogarithmus von 1 plus das Argument zurück.

## <a name="log2"></a><a name="log2"></a>log2

Berechnet den Basis-2-Logarithmus des Arguments

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Basis-10-Logarithmus des Arguments zurück

## <a name="log2f"></a><a name="log2f"></a>log2f

Berechnet den Basis-2-Logarithmus des Arguments

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Basis-10-Logarithmus des Arguments zurück

## <a name="logb"></a><a name="logb"></a>logb

Extrahiert den Exponenten von _X als signierter Ganzzahlwert im Gleitkommaformat

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den signierten Exponenten von _X zurück

## <a name="logbf"></a><a name="logbf"></a>logbf

Extrahiert den Exponenten von _X als signierter Ganzzahlwert im Gleitkommaformat

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den signierten Exponenten von _X zurück

## <a name="logf"></a><a name="logf"></a>logf

Berechnet den Basis-E-Logarithmus des Arguments

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Basislogarithmus des Arguments zurück

## <a name="modf"></a><a name="modf"></a>modf

Teilt das angegebene Argument in Brüche und ganzzahlige Teile.

```cpp
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Iptr*<br/>
[out] Der ganzzahlige `_X`Teil von , als Gleitkommawert.

### <a name="return-value"></a>Rückgabewert

Der Bruchteil von `_X` mit Vorzeichen.

## <a name="modff"></a><a name="modff"></a>modff

Teilt das angegebene Argument in Brüche und ganzzahlige Teile.

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Iptr*<br/>
Der ganzzahlige Teil von `_X` als Gleitkommawert.

### <a name="return-value"></a>Rückgabewert

Gibt den Bruchteil mit Vorzeichen von `_X` zurück.

## <a name="nan"></a><a name="nan"></a>Nan

Gibt ein ruhiges NaN zurück

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Gibt eine ruhige NaN zurück, falls verfügbar, mit dem Inhalt, der in _X

## <a name="nanf"></a><a name="nanf"></a>nanf

Gibt ein ruhiges NaN zurück

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Gibt eine ruhige NaN zurück, falls verfügbar, mit dem Inhalt, der in _X

## <a name="nearbyint"></a><a name="nearbyint"></a>nearbyint

Rundet das Argument mithilfe der aktuellen Rundungsrichtung auf einen Ganzzahlwert im Gleitkommaformat.

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den gerundeten Ganzzahlwert zurück.

## <a name="nearbyintf"></a><a name="nearbyintf"></a>nearbyintf

Rundet das Argument mithilfe der aktuellen Rundungsrichtung auf einen Ganzzahlwert im Gleitkommaformat.

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den gerundeten Ganzzahlwert zurück.

## <a name="nextafter"></a><a name="nextafter"></a>nextafter

Bestimmen Sie den nächsten darstellbaren Wert, im Typ der Funktion, nach _X in Richtung _Y

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den nächsten darstellbaren Wert, im Typ der Funktion, nach _X in Richtung _Y zurück

## <a name="nextafterf"></a><a name="nextafterf"></a>nextafterf

Bestimmen Sie den nächsten darstellbaren Wert, im Typ der Funktion, nach _X in Richtung _Y

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den nächsten darstellbaren Wert, im Typ der Funktion, nach _X in Richtung _Y zurück

## <a name="phi"></a><a name="phi"></a>Phi

Gibt die kumulative Verteilungsfunktion des Arguments zurück

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die kumulative Verteilungsfunktion des Arguments zurück

## <a name="phif"></a><a name="phif"></a>phif

Gibt die kumulative Verteilungsfunktion des Arguments zurück

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die kumulative Verteilungsfunktion des Arguments zurück

## <a name="pow"></a><a name="pow"></a>Pow

Berechnet _X potenziert mit _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert, Basis

*_Y*<br/>
Gleitkommawert, Exponent

### <a name="return-value"></a>Rückgabewert

## <a name="powf"></a><a name="powf"></a>powf

Berechnet _X potenziert mit _Y

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert, Basis

*_Y*<br/>
Gleitkommawert, Exponent

### <a name="return-value"></a>Rückgabewert

## <a name="probit"></a><a name="probit"></a>probit

Gibt die inverse kumulative Verteilungsfunktion des Arguments zurück

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die inverse kumulative Verteilungsfunktion des Arguments zurück

## <a name="probitf"></a><a name="probitf"></a>probitf

Gibt die inverse kumulative Verteilungsfunktion des Arguments zurück

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die inverse kumulative Verteilungsfunktion des Arguments zurück

## <a name="rcbrt"></a><a name="rcbrt"></a>rcbrt

Gibt die Reziprok der Cubewurzel des Arguments zurück

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Reziprok der Cubewurzel des Arguments zurück

## <a name="rcbrtf"></a><a name="rcbrtf"></a>rcbrtf

Gibt die Reziprok der Cubewurzel des Arguments zurück

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Reziprok der Cubewurzel des Arguments zurück

## <a name="remainder"></a><a name="remainder"></a>Rest

Berechnet den Rest: _X REM _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgabe n _X REM-_Y

## <a name="remainderf"></a><a name="remainderf"></a>Restf

Berechnet den Rest: _X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgabe n _X REM-_Y

## <a name="remquo"></a><a name="remquo"></a>remquo

Berechnet den Rest des angegebenen ersten Arguments dividiert durch das zweite angegebene Argument. Berechnet auch den Quotient der angegebenen Mantisse des ersten Arguments, dividiert durch die Mantisse des zweiten angegebenen Arguments und gibt den Quotient mithilfe der im dritten Argument angegebenen Position zurück.

```cpp
inline float remquo(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);

inline double remquo(
    double _X,
    double _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Das erste Gleitkommaargument.

*_Y*<br/>
Das zweite Gleitkommaargument.

*_Quo*<br/>
[out] Die Adresse einer ganzzahligen Datei, die verwendet wird, um `_X` den Quotienten der `_Y`Bruchteilbits von geteilt durch die Bruchteilbits von zurückzugeben.

### <a name="return-value"></a>Rückgabewert

Gibt den Rest von `_X` dividiert durch `_Y` zurück.

## <a name="remquof"></a><a name="remquof"></a>remquof

Berechnet den Rest des angegebenen ersten Arguments dividiert durch das zweite angegebene Argument. Berechnet auch den Quotient der angegebenen Mantisse des ersten Arguments, dividiert durch die Mantisse des zweiten angegebenen Arguments und gibt den Quotient mithilfe der im dritten Argument angegebenen Position zurück.

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Das erste Gleitkommaargument.

*_Y*<br/>
Das zweite Gleitkommaargument.

*_Quo*<br/>
[out] Die Adresse einer ganzzahligen Datei, die verwendet wird, um `_X` den Quotienten der `_Y`Bruchteilbits von geteilt durch die Bruchteilbits von zurückzugeben.

### <a name="return-value"></a>Rückgabewert

Gibt den Rest von `_X` dividiert durch `_Y` zurück.

## <a name="round"></a><a name="round"></a>Runde

Rundet _X auf die nächste ganze Zahl

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die nächste ganze Zahl von _X zurück

## <a name="roundf"></a><a name="roundf"></a>roundf

Rundet _X auf die nächste ganze Zahl

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die nächste ganze Zahl von _X zurück

## <a name="rsqrt"></a><a name="rsqrt"></a>rsqrt

Gibt den Kehrwert der Quadratwurzel des Arguments zurück

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kehrwert der Quadratwurzel des Arguments zurück

## <a name="rsqrtf"></a><a name="rsqrtf"></a>rsqrtf

Gibt den Kehrwert der Quadratwurzel des Arguments zurück

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Kehrwert der Quadratwurzel des Arguments zurück

## <a name="scalb"></a><a name="scalb"></a>scalb

Multipliziert _X mit FLT_RADIX der _Y

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt \* _X zurück (FLT_RADIX _Y)

## <a name="scalbf"></a><a name="scalbf"></a>scalbf

Multipliziert _X mit FLT_RADIX der _Y

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt \* _X zurück (FLT_RADIX _Y)

## <a name="scalbn"></a><a name="scalbn"></a>scalbn

Multipliziert _X mit FLT_RADIX der _Y

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Gibt \* _X zurück (FLT_RADIX _Y)

## <a name="scalbnf"></a><a name="scalbnf"></a>scalbnf

Multipliziert _X mit FLT_RADIX der _Y

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_Y*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Gibt \* _X zurück (FLT_RADIX _Y)

## <a name="signbit"></a><a name="signbit"></a>signbit

Bestimmt, ob das Vorzeichen von _X negativ ist

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert ungleich Null zurück, wenn und nur wenn das Vorzeichen von _X negativ ist

## <a name="signbitf"></a><a name="signbitf"></a>signbitf

Bestimmt, ob das Vorzeichen von _X negativ ist

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert ungleich Null zurück, wenn und nur wenn das Vorzeichen von _X negativ ist

## <a name="sin"></a><a name="sin"></a>Sünde

Berechnet den Sinuswert des Arguments

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Sinuswert des Arguments zurück

## <a name="sinf"></a><a name="sinf"></a>sinf

Berechnet den Sinuswert des Arguments

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Sinuswert des Arguments zurück

## <a name="sincos"></a><a name="sincos"></a>sincos

Berechnet Sinus- und Kosinuswert von _X

```cpp
inline void sincos(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);

inline void sincos(
    double _X,
    _Out_ double* _S,
    _Out_ double* _C) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_S*<br/>
Gibt den Sinuswert von _X zurück.

*_C*<br/>
Gibt den Kosinuswert von _X zurück.

## <a name="sincosf"></a><a name="sincosf"></a>sincosf

Berechnet Sinus- und Kosinuswert von _X

```cpp
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

*_S*<br/>
Gibt den Sinuswert von _X zurück.

*_C*<br/>
Gibt den Kosinuswert von _X zurück.

## <a name="sinh"></a><a name="sinh"></a>Sinh

Berechnet den Hyperbelsinuswert des Arguments

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Sinuswert des Arguments zurück

## <a name="sinhf"></a><a name="sinhf"></a>sinhf

Berechnet den Hyperbelsinuswert des Arguments

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Sinuswert des Arguments zurück

## <a name="sinpi"></a><a name="sinpi"></a>sinpi

Berechnet den Sinuswert \* von pi _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Sinuswert \* von pi _X zurück

## <a name="sinpif"></a><a name="sinpif"></a>sinpif

Berechnet den Sinuswert \* von pi _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Sinuswert \* von pi _X zurück

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

Berechnet die Squre-Wurzel des Arguments

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Squre-Wurzel des Arguments zurück

## <a name="sqrtf"></a><a name="sqrtf"></a>sqrtf

Berechnet die Squre-Wurzel des Arguments

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die Squre-Wurzel des Arguments zurück

## <a name="tan"></a><a name="tan"></a>Tan

Berechnet den Tangenswert des Arguments

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Tangentenwert des Arguments zurück

## <a name="tanf"></a><a name="tanf"></a>tanf

Berechnet den Tangenswert des Arguments

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Tangentenwert des Arguments zurück

## <a name="tanh"></a><a name="tanh"></a>Tanh

Berechnet den Hyperbeltangenswert des Arguments

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Tangentenwert des Arguments zurück

## <a name="tanhf"></a><a name="tanhf"></a>tanhf

Berechnet den Hyperbeltangenswert des Arguments

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den hyperbolischen Tangentenwert des Arguments zurück

## <a name="tanpi"></a><a name="tanpi"></a>tanpi

Berechnet den Tangentenwert \* von pi _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Tangentenwert \* von pi _X zurück

## <a name="tanpif"></a><a name="tanpif"></a>tanpif

Berechnet den Tangentenwert \* von pi _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt den Tangentenwert \* von pi _X zurück

## <a name="tgamma"></a><a name="tgamma"></a>tgamma

Berechnet die Gammafunktion von _X

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis der Gammafunktion von _X zurück

## <a name="tgammaf"></a><a name="tgammaf"></a>tgammaf

Berechnet die Gammafunktion von _X

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis der Gammafunktion von _X zurück

## <a name="trunc"></a><a name="trunc"></a>Trunc

Schneidet das Argument der ganzzahligen Komponente ab

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die ganzzahlige Komponente des Arguments zurück

## <a name="truncf"></a><a name="truncf"></a>truncf

Schneidet das Argument der ganzzahligen Komponente ab

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt die ganzzahlige Komponente des Arguments zurück

## <a name="see-also"></a>Siehe auch

[Parallelität::precise_math Namespace](concurrency-precise-math-namespace.md)
