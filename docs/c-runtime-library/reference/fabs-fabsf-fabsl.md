---
title: fabs, fabsf, fabsl
description: API-Referenz für Fabs, fabsf und fabsl; , die den absoluten Wert eines Gleit Komma Werts berechnen.
ms.date: 08/31/2020
api_name:
- fabsf
- fabs
- fabsl
- _o_fabs
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
ms.openlocfilehash: a819172fc94224ff4c51c8fc342b142ffbe05ae7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554837"
---
# <a name="fabs-fabsf-fabsl"></a>fabs, fabsf, fabsl

Berechnet den absoluten Wert des Gleitkommaarguments.

## <a name="syntax"></a>Syntax

```C
double fabs(
   double x
);
float fabs(
   float x
); // C++ only
long double fabs(
   long double x
); // C++ only
float fabsf(
   float x
);
long double fabsl(
   long double x
);

#define fabs(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*Stuben*\
Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **Fabs** -Funktionen geben den absoluten Wert des Arguments *x*zurück. Es gibt keine Fehlerrückgabe.

|Eingabe|SEH-Ausnahme|Matherr-Ausnahme|
|-----------|-------------------|-----------------------|
|± QNAN,IND|Keine|_DOMAIN|

## <a name="remarks"></a>Hinweise

C++ ermöglicht überladen, sodass Sie über Ladungen von **Fabs** aufzurufen können, wenn Sie den- \<cmath> Header einschließen. Wenn Sie in einem C-Programm das-Makro verwenden, \<tgmath.h> um diese Funktion aufzurufen, nimmt **Fabs** immer eine an und gibt Sie zurück **`double`** .

Wenn Sie das- \<tgmath.h> `fabs()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher C-Header|Erforderlicher C++-Header|
|--------------|-----------------------|---------------------------|
|**Fabs**, **fabsf**, **fabsl**|\<math.h>|\<cmath> oder \<math.h>|
|**Fabs** -Makro | \<tgmath.h> ||

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [abs](abs-labs-llabs-abs64.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
