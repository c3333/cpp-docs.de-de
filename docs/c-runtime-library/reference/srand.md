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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a8d018d429b2a484f88b7c1e0679f1f799983910
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355489"
---
# <a name="srand"></a>srand

Legt den Start-Ausgangswert für den Pseudozufallszahlengenerator fest, der von der **Rand-Funktion** verwendet wird.

## <a name="syntax"></a>Syntax

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parameter

*seed*<br/>
Startwert für die Pseudozufallszahlengenerierung

## <a name="remarks"></a>Bemerkungen

Die **srand-Funktion** legt den Ausgangspunkt für die Generierung einer Reihe von Pseudozufallsganzen im aktuellen Thread fest. Um den Generator erneut zu initialisieren, um dieselbe Sequenz von Ergebnissen zu erstellen, rufen Sie die **srand-Funktion** auf und verwenden Sie das gleiche *Seed-Argument* erneut. Jeder andere Wert für *Seed* legt den Generator auf einen anderen Startpunkt in der Pseudozufallssequenz fest. **rand** ruft die pseudozufallszahlen ab, die generiert werden. Der Aufruf von **Rand** vor jedem Aufruf von **srand** erzeugt die gleiche Sequenz wie der Aufruf von **srand** mit *einem Alsat.*

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [rand](rand.md).

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
