---
title: copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl
description: API-Verweis zum Zurückgeben eines Werts, der die Größe eines Arguments und das Vorzeichen eines anderen Arguments mithilfe von copysign () hat.
ms.date: 9/1/2020
api_name:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
ms.openlocfilehash: 8f9ffe56e82f6a82da15fde3f8efea60fc1c0f9f
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554863"
---
# <a name="copysign-copysignf-copysignl-_copysign-_copysignf-_copysignl"></a>copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl

Gibt einen Wert zurück, der die Größe eines Arguments und das Zeichen eines anderen Arguments aufweist.

## <a name="syntax"></a>Syntax

```C
double copysign(
   double x,
   double y
);
float copysign(
   float x,
   float y
); // C++ only
long double copysign(
   long double x,
   long double y
); // C++ only
float copysignf(
   float x,
   float y
); // C++ only
long double copysignl(
   long double x,
   long double y
); // C++ only
double _copysign(
   double x,
   double y
);
long double _copysignl(
   long double x,
   long double y
);
#define copysign(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Der Gleitkommawert, der als Betrag des Ergebnisses zurückgegeben wird.

*Teenie*\
Der Gleitkommawert, der als Zeichen des Ergebnisses zurückgegeben wird.

[Floating-Point Support Routines (Routinen für die Gleitkommaunterstützung)](../../c-runtime-library/floating-point-support.md)

## <a name="return-value"></a>Rückgabewert

Die **copysign** -Funktionen geben einen Gleit Komma Wert zurück, der die Größe von *x* und das Vorzeichen von *y*kombiniert. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Hinweise

Da C++ das überladen zulässt, können Sie über Ladungen von **copysign** aufzurufen, die-oder-Werte verwenden und zurückgeben **`float`** **`long double`** . In einem C-Programm verwendet copysign immer, wenn Sie das- \<tgmath.h> Makro verwenden **copysign** , um diese Funktion aufzurufen, und gibt es zurück **`double`** .

Wenn Sie das- \<tgmath.h> `copysign()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_copysign**|\<float.h>|
|**copysign**, **copysignf**, **copysignl**, **_copysignf** **_copysignl**|\<math.h>|
|**copysign** -Makro | \<tgmath.h> |

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[_chgsign, _chgsignf, _chgsignl](chgsign-chgsignf-chgsignl.md)<br/>
