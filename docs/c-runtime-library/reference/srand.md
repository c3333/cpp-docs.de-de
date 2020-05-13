---
title: srand
ms.date: 4/2/2020
api_name:
- srand
- _o_srand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- srand
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.openlocfilehash: 3f6f97ad9a3bd0d7e4e88ad1797d369f012bbe5e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913598"
---
# <a name="srand"></a>srand

Legt den Startwert für den von der **Rand** -Funktion verwendeten Pseudo Zufalls Number-Generator fest.

## <a name="syntax"></a>Syntax

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parameter

*seed*<br/>
Startwert für die Pseudozufallszahlengenerierung

## <a name="remarks"></a>Hinweise

Die **srand** -Funktion legt den Ausgangspunkt für das Erstellen einer Reihe von Pseudo Zufalls-Ganzzahlen im aktuellen Thread fest. Um den Generator erneut zu initialisieren, um dieselbe Sequenz von Ergebnissen zu erstellen, rufen Sie die **srand** -Funktion auf, und verwenden Sie das gleiche *Seed* -Argument erneut. Jeder andere Wert für *Seed* legt den Generator auf einen anderen Startpunkt in der Pseudo Zufalls-Sequenz fest. **Rand** Ruft die zu Generier baren Pseudo Zufalls-Zahlen ab. Der Aufruf von **Rand** vor jedem Aufruf von **srand** generiert dieselbe Sequenz wie der *Aufruf von* **srand** mit einem als 1 bestandenen Ausgangswerten.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [rand](rand.md).

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
