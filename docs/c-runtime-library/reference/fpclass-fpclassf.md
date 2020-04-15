---
title: _fpclass, _fpclassf
ms.date: 4/2/2020
api_name:
- _fpclass
- _fpclassf
- _o__fpclass
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
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: b16655fed046114e9dd8592c5e1fd3fc5f7ed4bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346275"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass, _fpclassf

Gibt einen Wert zurück, der die Gleitkommaklassifizierung des Arguments angibt.

## <a name="syntax"></a>Syntax

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>Parameter

*X*<br/>
Der zu testende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die **_fpclass-** und **_fpclassf-Funktionen** geben einen Ganzzahlwert zurück, der die Gleitkommaklassifizierung des Arguments *x*angibt. Die Klassifizierung weist möglicherweise einen der folgenden, in \<float.h> definierten Werte auf.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|**_FPCLASS_SNAN**|Signalisierender NaN|
|**_FPCLASS_QNAN**|Stiller NaN|
|**_FPCLASS_NINF**|Negative Unendlichkeit ( -INF)|
|**_FPCLASS_NN**|Negativ normalisierter ungleich null-Wert|
|**_FPCLASS_ND**|Negativ denormalisiert|
|**_FPCLASS_NZ**|Negative Null ( - 0)|
|**_FPCLASS_PZ**|Positiv 0 (+0)|
|**_FPCLASS_PD**|Positiv denormalisiert|
|**_FPCLASS_PN**|Positiv normalisierter ungleich null-Wert|
|**_FPCLASS_PINF**|Positiv unendlich|

## <a name="remarks"></a>Bemerkungen

Die **_fpclass-** und **_fpclassf** Funktionen sind Microsoft-spezifisch. Sie ähneln [fpclassify](fpclassify.md), geben jedoch detaillierte Informationen über das Argument zurück. Die **_fpclassf** Funktion ist nur verfügbar, wenn sie für die x64-Plattform kompiliert wird.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h>|

Weitere Informationen zur Kompatibilität und Konformität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
