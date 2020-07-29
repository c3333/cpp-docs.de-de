---
title: fpclassify
ms.date: 04/05/2018
api_name:
- fpclassify
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
api_type:
- HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: 75cfdc33c21059e190fd04f4cd1b73716e74ac42
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213579"
---
# <a name="fpclassify"></a>fpclassify

Gibt die Gleitkommaklassifizierung des Arguments zurück.

## <a name="syntax"></a>Syntax

```C
int fpclassify(
   /* floating-point */ x
);

int fpclassify(
   float x
); // C++ only

int fpclassify(
   double x
); // C++ only

int fpclassify(
   long double x
); // C++ only
```

### <a name="parameters"></a>Parameter

*x*<br/>
Der zu testende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

**fpklassifiklassifiziert** gibt einen ganzzahligen Wert zurück, der die Gleit Komma Klasse des Arguments *x*angibt. Diese Tabelle zeigt die möglichen Werte, die von **fpklassifiziert**zurückgegeben werden, die in definiert sind \<math.h> .

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|**FP_NAN**|Ein stiller, signalisierender oder unbestimmter NaN|
|**FP_INFINITE**|Eine positive oder negative Unendlichkeit|
|**FP_NORMAL**|Ein positiver oder negativer ungleich null normalisierter Wert|
|**FP_SUBNORMAL**|Ein positiver oder negativer denormalisierter Wert|
|**FP_ZERO**|Ein positiver oder negativer Nullwert|

## <a name="remarks"></a>Bemerkungen

In C ist **fpklassifiziert** ein Makro. in C++ ist **fpklassifiziert** eine Funktion, die mithilfe von Argument Typen von, oder überladen wird **`float`** **`double`** **`long double`** . In beiden Fällen hängt der zurückgegebene Wert vom tatsächlichen Typ des Argumentausdrucks ab, und nicht von einer Zwischendarstellung. Beispielsweise kann ein normaler- **`double`** Wert oder ein- **`long double`** Wert bei der Konvertierung in einen-Wert von unendlich, DENORMAL oder NULL werden **`float`** .

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion/Makro|Erforderlicher Header (C)|Erforderlicher Header (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> oder \<cmath>|

Das **fpklassifiziert** -Makro und die **fpklassifiziert** -Funktionen entsprechen den Spezifikationen ISO C99 und c++ 11. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Unterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
