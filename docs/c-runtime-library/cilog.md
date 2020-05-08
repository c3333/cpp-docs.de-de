---
title: _CIlog
ms.date: 4/2/2020
api_name:
- _CIlog
- _o__CIlog
api_location:
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIlog
- CIlog
helpviewer_keywords:
- _CIlog intrinsic
- CIlog intrinsic
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
ms.openlocfilehash: 405af59eab918498578c2d62c66be1017ecf156f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918063"
---
# <a name="_cilog"></a>_CIlog

Berechnet den natürlichen Logarithmus des obersten Werts im Stapel.

## <a name="syntax"></a>Syntax

```cpp
void __cdecl _CIlog();
```

## <a name="remarks"></a>Hinweise

Diese Version der `log`-Funktion verfügt über eine spezielle Aufrufkonvention, die der Compiler versteht. Sie beschleunigt die Ausführung, da sie das Generieren von Kopien verhindert und bei der Registerzuweisung hilft.

Der resultierende Wert wird oben auf dem Stapel abgelegt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](global-state.md).

## <a name="requirements"></a>Anforderungen

**Plattform:** x86

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)
