---
title: cosh, coshf, coshl
ms.date: 4/2/2020
api_name:
- cosh
- coshf
- coshl
- _o_cosh
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: fb171d622d5bc187342054a74e8aa19f83c3c560
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213605"
---
# <a name="cosh-coshf-coshl"></a>cosh, coshf, coshl

Berechnet den hyperbolischen Kosinus.

## <a name="syntax"></a>Syntax

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
```

```cpp
float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>Parameter

*x*<br/>
Winkel im Bogenmaß.

## <a name="return-value"></a>Rückgabewert

Der hyperbolische Kosinus von *x*.

Wenn das Ergebnis in einem **cosh**-, **coshf**-oder **coshl** -Befehl zu groß ist, gibt die Funktion standardmäßig **HUGE_VAL** zurück und legt **errno** auf **ERANGE**fest.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|Keine|**_DOMAIN**|
|*x* 104760e e + 002|**Ungenau** + **Überlauf**|**Läufen**|

## <a name="remarks"></a>Bemerkungen

Da C++ das überladen zulässt, können Sie über Ladungen von **cosh** aufzurufen, die-oder-Werte verwenden und zurückgeben **`float`** **`long double`** . In einem C-Programm übernimmt **cosh** immer und gibt einen zurück **`double`** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|-------------|---------------------|-|
|**coshf**, **COSL**, **coshl**|\<math.h>|\<cmath> oder \<math.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel in [sinh, Sinhf, sinhl](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
