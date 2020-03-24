---
title: cos, cosf, cosl
ms.date: 04/05/2018
api_name:
- cos
- cosf
- cosl
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
- cos
- cosf
- cosl
helpviewer_keywords:
- cosines
- cosl function
- calculating cosine
- cosf function
- cos function
- trigonometric functions
- cosines, calculating
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
ms.openlocfilehash: 9ec612aa9f8c6eaf1731d62b654d45841cdfa159
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170254"
---
# <a name="cos-cosf-cosl"></a>cos, cosf, cosl

Berechnet den Kosinus.

## <a name="syntax"></a>Syntax

```C
double cos( double x );
float cosf( float x );
long double cosl( long double x );
```

```cpp
float cos( float x );  // C++ only
long double cos( long double x );  // C++ only
```

### <a name="parameters"></a>Parameter

*x*<br/>
Winkel im Bogenmaß.

## <a name="return-value"></a>Rückgabewert

Der Kosinus von *x*. Wenn *x* größer oder gleich 263 oder kleiner oder gleich-263 ist, tritt ein Bedeutungsverlust im Ergebnis auf.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± QNAN, IND|none|**_DOMAIN**|
|± INF|**Ungültig**|**_DOMAIN**|

## <a name="remarks"></a>Bemerkungen

Da C++ das überladen zulässt, können Sie über Ladungen von **cos** aufzurufen, die **float** -oder **Long** **Double** -Werte verwenden und zurückgeben. In einem C-Programm nimmt **cos** immer einen **Double**-Wert an und gibt ihn zurück.

## <a name="requirements"></a>Requirements (Anforderungen)

|Routine|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------------|---------------------|-|
|**cos**, **cosh**, **cosf**|\<math.h>|\<cmath> oder \<math.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel in [Sin, sinf, sinl](sin-sinf-sinl.md)an.

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIcos](../../c-runtime-library/cicos.md)<br/>
