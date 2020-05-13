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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a6591d9348739d27831785a05f4a602aacdd4d0c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914846"
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

*x*<br/>
Der zu testende Gleitkommawert.

## <a name="return-value"></a>Rückgabewert

Die Funktionen **_fpclass** und **_fpclassf** geben einen ganzzahligen Wert zurück, der die Gleit Komma Klassifizierung des Arguments *x*angibt. Die Klassifizierung weist möglicherweise einen der folgenden, in \<float.h> definierten Werte auf.

|Value|Beschreibung|
|-----------|-----------------|
|**_FPCLASS_SNAN**|Signalisierender NaN|
|**_FPCLASS_QNAN**|Stiller NaN|
|**_FPCLASS_NINF**|Minus unendlich (-INF)|
|**_FPCLASS_NN**|Negativ normalisierter ungleich null-Wert|
|**_FPCLASS_ND**|Negativ denormalisiert|
|**_FPCLASS_NZ**|Negatives NULL-Wert (-0)|
|**_FPCLASS_PZ**|Positiv 0 (+0)|
|**_FPCLASS_PD**|Positiv denormalisiert|
|**_FPCLASS_PN**|Positiv normalisierter ungleich null-Wert|
|**_FPCLASS_PINF**|Positiv unendlich|

## <a name="remarks"></a>Hinweise

Die Funktionen **_fpclass** und **_fpclassf** sind Microsoft-spezifisch. Sie ähneln [fpclassify](fpclassify.md), geben jedoch detaillierte Informationen über das Argument zurück. Die **_fpclassf** -Funktion ist nur verfügbar, wenn Sie für die x64-Plattform kompiliert ist.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fpclass** **_fpclassf**|\<float.h>|

Weitere Informationen zur Kompatibilität und Konformität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
