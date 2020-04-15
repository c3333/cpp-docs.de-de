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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d861fbf2b71d557354a60f65b8a76dc24ca1dd13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346714"
---
# <a name="floating-point-primitives"></a>Gleitkommaprimitive

Microsoft-spezifische primitive Funktionen, die zum Implementieren einiger CrT-Gleitkommafunktionen (Standard C-Laufzeitbibliothek) verwendet werden. Sie sind hier der Vollständigkeit nach dokumentiert, werden jedoch nicht zur Verwendung empfohlen. Einige dieser Funktionen werden als nicht verwendet bezeichnet, da bekannt ist, dass sie Probleme in Bezug auf Genauigkeit, Ausnahmebehandlung und Übereinstimmung mit dem IEEE-754-Verhalten haben. Sie sind nur aus Gründen der Abwärtskompatibilität in der Bibliothek vorhanden. Für korrektes Verhalten, Portabilität und Einhaltung von Standards bevorzugen Sie die standardmäßigen Gleitkommafunktionen gegenüber diesen Funktionen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Syntax

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gleitkommafunktionsargument.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven implementieren die C-Versionen des CRT-Makros [fpclassify](fpclassify.md) für Gleitkommatypen. Die Klassifizierung des Arguments *x* wird als eine dieser konstanten konstanten zurückgegeben, die in math.h definiert ist:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
| **FP_NAN** | Ein stiller, signalisierender oder unbestimmter NaN |
| **FP_INFINITE** | Eine positive oder negative Unendlichkeit |
| **FP_NORMAL** | Ein positiver oder negativer ungleich null normalisierter Wert |
| **FP_SUBNORMAL** | Ein positiver oder negativer subnormaler (denormalisierter) Wert |
| **FP_ZERO** | Ein positiver oder negativer Nullwert |

Für weitere Details können Sie die Microsoft-spezifischen [_fpclass _fpclassf](fpclass-fpclassf.md) Funktionen verwenden. Verwenden Sie das makro oder die Funktion [fpclassify](fpclassify.md) für die Portabilität.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign _fdsign

### <a name="syntax"></a>Syntax

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gleitkommafunktionsargument.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven implementieren das [Signbitmakro](signbit.md) oder die Funktion in der CRT. Sie geben einen Wert ungleich Null zurück, wenn das Signbit im Significand (Mantissa) des Arguments *x*gesetzt ist, und 0, wenn das Signbit nicht gesetzt ist.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp _fdpcomp

### <a name="syntax"></a>Syntax

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parameter

*x*, *y*<br/>
Gleitkommafunktionsargumente.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven verwenden zwei Argumente, *x* und *y*, und geben einen Wert zurück, der ihre Reihenfolgenbeziehung anzeigt, ausgedrückt als bitweise oder dieser Konstanten, definiert in math.h:

| Wert | BESCHREIBUNG |
|------------|-----------------|
| **_FP_LT** | *x* kann als kleiner als *y* betrachtet werden |
| **_FP_EQ** | *x* kann als gleich *y* betrachtet werden |
| **_FP_GT** | *x* kann als größer als *y* betrachtet werden |

Diese Primitive implementieren die [isgreater, isgreaterequal, isless, islessequal, islessgreater, and isunordered](floating-point-ordering.md) macros and functions in the CRT.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Syntax

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parameter

*Pixel*<br/>
Zeiger auf ein Gleitkommaargument.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven implementieren die C++-Versionen der CRT-Funktion [fpclassify](fpclassify.md) für Gleitkommatypen. Das Argument *x* wird ausgewertet, und die Klassifizierung wird als eine dieser konstanten zurückgegeben, die in math.h definiert ist:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
| **FP_NAN** | Ein stiller, signalisierender oder unbestimmter NaN |
| **FP_INFINITE** | Eine positive oder negative Unendlichkeit |
| **FP_NORMAL** | Ein positiver oder negativer ungleich null normalisierter Wert |
| **FP_SUBNORMAL** | Ein positiver oder negativer subnormaler (denormalisierter) Wert |
| **FP_ZERO** | Ein positiver oder negativer Nullwert |

Für weitere Details können Sie die Microsoft-spezifischen [_fpclass _fpclassf](fpclass-fpclassf.md) Funktionen verwenden. Verwenden Sie die [fpclassify-Funktion](fpclassify.md) für die Portabilität.

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int _fd_int

### <a name="syntax"></a>Syntax

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parameter

*Pixel*<br/>
Zeiger auf ein Gleitkommaargument.

*Exp*<br/>
Ein Exponent als integraler Typ.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven nehmen einen Zeiger auf einen Gleitkommawert *px* und einen Exponentenwert *exp*und entfernen nach Möglichkeit den Bruchteil des Gleitkommawerts unterhalb des angegebenen Exponenten. Der zurückgegebene Wert ist das Ergebnis von **fpclassify** auf dem Eingabewert in *px,* wenn es sich um einen NaN oder unendlich ist, und auf den Ausgabewert in *px* sonst.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale _fdscale

### <a name="syntax"></a>Syntax

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parameter

*Pixel*<br/>
Zeiger auf ein Gleitkommaargument.

*Exp*<br/>
Ein Exponent als integraler Typ.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven nehmen einen Zeiger auf einen Gleitkommawert *px* und einen Exponentenwert *exp*und skalieren den Wert in px um *2* <sup>*exp*</sup>, wenn möglich. Der zurückgegebene Wert ist das Ergebnis von **fpclassify** auf dem Eingabewert in *px,* wenn es sich um einen NaN oder unendlich ist, und auf den Ausgabewert in *px* sonst. Für die Portabilität bevorzugen Sie die Funktionen [ldexp, ldexpf und ldexpl.](ldexp.md)

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Syntax

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parameter

*pexp*<br/>
Ein Zeiger auf einen Exponenten als integralen Typ.

*Pixel*<br/>
Zeiger auf ein Gleitkommaargument.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven brechen den Gleitkommawert, auf den *px* zeigt, nach Möglichkeit in ein Signifikantund (Mantisse) und einen Exponenten auf. Der Significand wird so skaliert, dass der absolute Wert größer oder gleich 0,5 und kleiner als 1,0 ist. Der Exponent ist der Wert *n*, wobei der ursprüngliche Gleitkommawert gleich dem skalierten Significund mal 2<sup>*n*</sup>ist. Dieser ganzzahlige Exponent *n* wird an der Position gespeichert, auf die *pexp*zeigt. Der zurückgegebene Wert ist das Ergebnis von **fpclassify** auf den Eingabewert in *px,* wenn es sich um einen NaN oder unendlich ist, und auf den Ausgabewert andernfalls. Für die Portabilität, bevorzugen Sie die [frexp, frexpf, frexpl](frexp.md) Funktionen.

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Syntax

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parameter

*y*<br/>
Gleitkommafunktionsargument.

*Pixel*<br/>
Zeiger auf ein Gleitkommaargument.

*Exp*<br/>
Ein Exponent als integraler Typ.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven erstellen einen Gleitkommawert an der Position, auf die *px* gleich *y* * 2<sup>*exp*</sup>zeigt. Der zurückgegebene Wert ist das Ergebnis von **fpclassify** auf dem Eingabewert in *y,* wenn es sich um einen NaN oder unendlich ist, und auf den Ausgabewert in *px* sonst. Für die Portabilität bevorzugen Sie die Funktionen [ldexp, ldexpf und ldexpl.](ldexp.md)

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Syntax

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parameter

*ps*<br/>
Zeiger auf die bitweise Darstellung eines Gleitkommawerts, ausgedrückt als Array von **nicht signierten** **short**.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven normalisieren den Bruchteil eines unterlaufenden Gleitkommawerts und passen das *Merkmal*oder den voreingenommenen Exponenten an. Der Wert wird übergeben, wenn die bitweise Darstellung des Gleitkommatyps `_ldouble_val`in `_float_val` ein Array von **nicht signierten** **Short** durch die `_double_val`, oder Typ-Wortspiel-Union in math.h konvertiert wird. Der Rückgabewert ist das Ergebnis von **fpclassify** auf dem Eingabe-Gleitkommawert, wenn es sich um einen NaN- oder Unendlichkeitswert handelt, und auf dem Ausgabewert andernfalls.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly _fdpoly

### <a name="syntax"></a>Syntax

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gleitkommafunktionsargument.

*Tabelle*<br/>
Zeiger auf eine Tabelle mit konstanten Koeffizienten für ein Polynom.

*n*<br/>
Reihenfolge des zu bewertenden Polynoms.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven geben die Auswertung von *x* im Polynom der Ordnung *n* zurück, deren Koeffizienten durch die entsprechenden konstanten Werte in *der Tabelle*dargestellt werden. Wenn z. B. *Tabelle*\[0] = 3.0, *Tabelle*\[1] = 4.0, *Tabelle*\[2] = 5.0 und *n* = 2, stellt sie das Polynom 5.0x<sup>2</sup> + 4.0x + 3.0 dar. Wenn dieses Polynom für *x* von 2,0 ausgewertet wird, ist das Ergebnis 31,0. Diese Funktionen werden intern nicht verwendet.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Syntax

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gleitkommafunktionsargument.

*base_flag*<br/>
Flag, das die zu verwendende Basis steuert, 0 für Basis *e* und ungleich Null für Basis 10.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven geben das natürliche Protokoll von *x*, ln(*x*) oder log<sub>*e*</sub>(*x*) zurück, wenn *base_flag* 0 ist. Sie geben die Protokollbasis 10 von *x*oder log<sub>10</sub>(*x*) zurück, wenn *base_flag* ungleich Null ist. Diese Funktionen werden intern nicht verwendet. Für die Portabilität bevorzugen Sie die Funktionen [log, logf, logl, log10, log10f und log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin _fdsin

### <a name="syntax"></a>Syntax

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gleitkommafunktionsargument.

*Quadranten*<br/>
Quadrantenoffset von 0, 1, 2 oder `sin` `cos`3, der zum Erstellen von , , `-sin`und `-cos` Ergebnissen verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Gleitkommaprimitiven geben den Sinus von *x* offset durch das *Quadrantmodul* 4 zurück. Effektiv geben sie den Sinus, den Kosinus, den -sinus und den -kosinus *x* zurück, wenn *Quadrant* modulo 4 0, 1, 2 bzw. 3 ist. Diese Funktionen werden intern nicht verwendet. Für die Portabilität, bevorzugen Sie die [Sinf, Sinf, Sinl,](sin-sinf-sinl.md) [cos, cosf, und cosl](cos-cosf-cosl.md) Funktionen.

## <a name="requirements"></a>Anforderungen

Kopfzeile: \<math.h>

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexpf und ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
