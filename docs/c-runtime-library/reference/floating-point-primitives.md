---
title: Gleitkommaprimitive
ms.date: 4/2/2020
api_name:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
- _o__d_int
- _o__dclass
- _o__dlog
- _o__dnorm
- _o__dpcomp
- _o__dpoly
- _o__dscale
- _o__dsign
- _o__dsin
- _o__dtest
- _o__dunscale
- _o__fd_int
- _o__fdclass
- _o__fdexp
- _o__fdlog
- _o__fdpcomp
- _o__fdpoly
- _o__fdscale
- _o__fdsign
- _o__fdsin
- _o__ld_int
- _o__ldclass
- _o__ldexp
- _o__ldlog
- _o__ldpcomp
- _o__ldpoly
- _o__ldscale
- _o__ldsign
- _o__ldsin
- _o__ldtest
- _o__ldunscale
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
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: c103d28dc111af4736bdc299b498b98eccb3af60
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916696"
---
# <a name="floating-point-primitives"></a>Gleitkommaprimitive

Microsoft-spezifische primitive Funktionen, die verwendet werden, um einige Standardfunktionen der C-Lauf Zeit Bibliothek (CRT) zu implementieren. Sie sind hier aus Gründen der Vollständigkeit dokumentiert, werden jedoch nicht für die Verwendung empfohlen. Einige dieser Funktionen werden als nicht verwendet bezeichnet, da sie bekanntermaßen Probleme in Bezug auf die Genauigkeit, die Ausnahmebehandlung und die Konformität mit IEEE-754-Verhalten haben. Sie sind in der Bibliothek nur aus Gründen der Abwärtskompatibilität vorhanden. Für das korrekte Verhalten, die Portabilität und die Einhaltung von Standards bevorzugen Sie die standardmäßigen Gleit Komma Funktionen für diese Funktionen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass _fdclass

### <a name="syntax"></a>Syntax

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gleit Komma Funktions Argument.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven implementieren die C-Versionen des CRT-Makros [fpklassifiziert](fpclassify.md) für Gleit Komma Typen. Die Klassifizierung des Arguments *x* wird als eine dieser Konstanten zurückgegeben, die in Math. h definiert ist:

|Value|Beschreibung|
|-----------|-----------------|
| **FP_NAN** | Ein stiller, signalisierender oder unbestimmter NaN |
| **FP_INFINITE** | Eine positive oder negative Unendlichkeit |
| **FP_NORMAL** | Ein positiver oder negativer ungleich null normalisierter Wert |
| **FP_SUBNORMAL** | Ein positiver oder negativer subnormal-Wert (Denormalized) |
| **FP_ZERO** | Ein positiver oder negativer Nullwert |

Um weitere Details zu erhalten, können Sie die Microsoft-spezifischen [_fpclass _fpclassf](fpclass-fpclassf.md) Funktionen verwenden. Verwenden Sie das [fpklassifiziert](fpclassify.md) -Makro oder die Funktion für die Portabilität.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign _fdsign

### <a name="syntax"></a>Syntax

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gleit Komma Funktions Argument.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven implementieren das [SignBit](signbit.md) -Makro oder die-Funktion in der CRT. Sie geben einen Wert ungleich 0 (null) zurück, wenn das Signier Bit in signifikanund (Mantisse) des Arguments *x*festgelegt ist, und 0, wenn das Signier Bit nicht festgelegt ist.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp _fdpcomp

### <a name="syntax"></a>Syntax

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parameter

*x*, *y*<br/>
Gleit Komma Funktionsargumente.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven akzeptieren zwei Argumente: *x* und *y*und geben einen Wert zurück, der ihre Reihenfolge Beziehung anzeigt, ausgedrückt als bitweises OR dieser Konstanten, die in Math. h definiert sind:

| Value | Beschreibung |
|------------|-----------------|
| **_FP_LT** | *x* kann als kleiner als *y* angesehen werden. |
| **_FP_EQ** | *x* kann als gleich *y* betrachtet werden. |
| **_FP_GT** | *x* kann als größer als *y* angesehen werden. |

Diese primitiven implementieren die Makros und Funktionen [isgreater, isgreaterequal, isless, islessequal, islessgreater und isunsortierte](floating-point-ordering.md) in der CRT.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest _fdtest

### <a name="syntax"></a>Syntax

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parameter

*entworfen*<br/>
Zeiger auf ein Gleit Komma Argument.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven implementieren die C++-Versionen der CRT-Funktion [fpklassifiziert](fpclassify.md) für Gleit Komma Typen. Das Argument *x* wird ausgewertet, und die Klassifizierung wird als eine dieser Konstanten zurückgegeben, die in Math. h definiert ist:

|Value|Beschreibung|
|-----------|-----------------|
| **FP_NAN** | Ein stiller, signalisierender oder unbestimmter NaN |
| **FP_INFINITE** | Eine positive oder negative Unendlichkeit |
| **FP_NORMAL** | Ein positiver oder negativer ungleich null normalisierter Wert |
| **FP_SUBNORMAL** | Ein positiver oder negativer subnormal-Wert (Denormalized) |
| **FP_ZERO** | Ein positiver oder negativer Nullwert |

Um weitere Details zu erhalten, können Sie die Microsoft-spezifischen [_fpclass _fpclassf](fpclass-fpclassf.md) Funktionen verwenden. Verwenden Sie die [fpklassifiziert](fpclassify.md) -Funktion für die Portabilität.

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int _fd_int

### <a name="syntax"></a>Syntax

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parameter

*entworfen*<br/>
Zeiger auf ein Gleit Komma Argument.

*Exp*<br/>
Ein Exponent als ganzzahliger Typ.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven akzeptieren einen Zeiger auf einen Gleit Komma Wert *px* und einen Exponent-Wert *Exp*und entfernen den Bruch Teil des Gleit Komma Werts, sofern möglich, unter den angegebenen Exponenten. Der zurückgegebene Wert ist das Ergebnis von **fpklassifiziert** für den Eingabe Wert in *px* , wenn er ein NaN oder unendlich ist, und andernfalls für den Ausgabewert in *px* .

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale _fdscale

### <a name="syntax"></a>Syntax

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parameter

*entworfen*<br/>
Zeiger auf ein Gleit Komma Argument.

*Exp*<br/>
Ein Exponent als ganzzahliger Typ.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven übernehmen einen Zeiger auf einen Gleit Komma Wert *px* und einen Exponent-Wert *Exp*und Skalieren den Wert in *px* um 2<sup>*Exp*</sup>, wenn möglich. Der zurückgegebene Wert ist das Ergebnis von **fpklassifiziert** für den Eingabe Wert in *px* , wenn er ein NaN oder unendlich ist, und andernfalls für den Ausgabewert in *px* . Bevorzugen Sie für die Portabilität die [ldexp-, ldexpf-und ldexpl-](ldexp.md) Funktionen.

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale _fdunscale

### <a name="syntax"></a>Syntax

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parameter

*pexp*<br/>
Ein Zeiger auf einen Exponenten als ganzzahliger Typ.

*entworfen*<br/>
Zeiger auf ein Gleit Komma Argument.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven unterbrechen den Gleit Komma Wert, auf den von *px* gezeigt wird, in einen signifikan(Mantisse) und einen Exponenten, wenn möglich. Der signifiund wird so skaliert, dass der absolute Wert größer oder gleich 0,5 und kleiner als 1,0 ist. Der Exponent ist der Wert *n*, bei dem der ursprüngliche Gleit Komma Wert gleich dem skalierten signifikanand 2<sup>*n*</sup>ist. Dieser ganzzahlige *Exponent wird* an dem Speicherort gespeichert, auf den von *pexp*verwiesen wird. Der zurückgegebene Wert ist das Ergebnis von **fpklassifiziert** für den Eingabe Wert in *px* , wenn es sich um einen NaN-Wert oder unendlich handelt, und andernfalls auf dem Ausgabewert. Bevorzugen Sie für die Portabilität die [frexp-, frexpf-und frexpl](frexp.md) -Funktionen.

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp _fdexp

### <a name="syntax"></a>Syntax

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parameter

*Teenie*<br/>
Gleit Komma Funktions Argument.

*entworfen*<br/>
Zeiger auf ein Gleit Komma Argument.

*Exp*<br/>
Ein Exponent als ganzzahliger Typ.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven erstellen einen Gleit Komma Wert in dem Speicherort, auf den von *px* mit *y* * 2<sup>*Exp*</sup>gezeigt wird. Der zurückgegebene Wert ist das Ergebnis von **fpklassifiziert** für den Eingabe Wert in *y* , wenn er ein NaN oder unendlich ist, und andernfalls für den Ausgabewert in *px* . Bevorzugen Sie für die Portabilität die [ldexp-, ldexpf-und ldexpl-](ldexp.md) Funktionen.

## <a name="_dnorm-_fdnorm"></a>_dnorm _fdnorm

### <a name="syntax"></a>Syntax

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parameter

*ps*<br/>
Ein Zeiger auf die bitweise Darstellung eines Gleit Komma Werts, ausgedrückt als Array von **Ganzzahl ohne Vorzeichen** **Short**.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven normalisieren den Bruch Teil eines Gleit Komma Werts mit Unterlauf und passen das *Merkmal*oder den dezischen Exponent entsprechend an. Der-Wert wird als bitweise Darstellung des Gleit Komma Typs übergeben, der in ein Array vom Typ " **Ganzzahl ohne Vorzeichen** **Short** " konvertiert `_double_val`wird `_ldouble_val`, der `_float_val` durch die-,-oder-Typ-punning-Union in Math. h konvertiert wurde. Der Rückgabewert ist das Ergebnis von **fpklassifiziert** für den Eingabe Gleit Komma Wert, wenn es sich um einen NaN-Wert oder unendlich handelt, und andernfalls auf dem Ausgabewert.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly _fdpoly

### <a name="syntax"></a>Syntax

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gleit Komma Funktions Argument.

*Tabelle*<br/>
Zeiger auf eine Tabelle konstanter Koeffizienten für ein polynomal.

*n*<br/>
Die Reihenfolge des auszuwertenden Polynoms.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven geben die Auswertung von *x* im Polynoms der Reihenfolge *n* zurück, deren Koeffizienten durch die entsprechenden Konstanten Werte in der *Tabelle*dargestellt werden. Wenn z. b. *Tabelle*\[0] = 3,0, *Tabelle*\[1] = 4,0 *, Tabelle*\[2] = 5,0 und *n* = 2 ist, stellt Sie die Polynoms 5.0 x<sup>2</sup> + 4.0 x + 3,0 dar. Wenn diese polynommial für *x* von 2,0 ausgewertet wird, ist das Ergebnis 31,0. Diese Funktionen werden intern nicht verwendet.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog _dlog

### <a name="syntax"></a>Syntax

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gleit Komma Funktions Argument.

*base_flag*<br/>
Flag, das die zu verwendende Basis steuert, 0 für Basis *e* und ungleich NULL für Basis 10.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven geben das natürliche Protokoll von *x*, ln (*x*) oder log<sub>*e*</sub>(*x*) zurück, wenn *base_flag* 0 ist. Sie geben die Protokoll Basis 10 von *x*oder log<sub>10</sub>(*x*) zurück, wenn *base_flag* ungleich 0 (null) ist. Diese Funktionen werden intern nicht verwendet. Bevorzugen Sie für die Portabilität die Funktionen [Log, logf, logl, log10, log10f und log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin _fdsin

### <a name="syntax"></a>Syntax

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gleit Komma Funktions Argument.

*stran*<br/>
Der Quadranten Offset von 0, 1, 2 oder 3, der zum erzielen `sin`der `cos`Ergebnisse `-sin`,, `-cos` und verwendet wird.

### <a name="remarks"></a>Hinweise

Diese Gleit Komma primitiven geben den Sinus des *x* -Offsets von der *Quadranten* -modulo 4 zurück. Effektiv geben Sie den Sinus, Kosinus,-Sinus und-Kosinus von *x* zurück, wenn *Quadrant* modulo 4 0, 1, 2 bzw. 3 ist. Diese Funktionen werden intern nicht verwendet. Bevorzugen Sie für die Portabilität die Funktionen [Sin, sinf, sinl](sin-sinf-sinl.md), [cos, cosf und COSL](cos-cosf-cosl.md) .

## <a name="requirements"></a>Anforderungen

Header: \<Math. h>

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[LDE XP, ldexpf und ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
