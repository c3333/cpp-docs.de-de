---
title: _get_daylight
ms.date: 4/2/2020
api_name:
- __daylight
- _get_daylight
- _o___daylight
- _o__get_daylight
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: 226242c5dd6c3c204d2449bd14ee7dee4f5fe7b5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919401"
---
# <a name="_get_daylight"></a>_get_daylight

Ruft die Sommerzeitverschiebung in Stunden ab.

## <a name="syntax"></a>Syntax

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Parameter

*hours*<br/>
Die Verschiebung der Sommerzeit in Stunden.

## <a name="return-value"></a>Rückgabewert

NULL, wenn erfolgreich, oder ein **errno** -Wert, wenn ein Fehler auftritt.

## <a name="remarks"></a>Hinweise

Die **_get_daylight** -Funktion Ruft die Anzahl der Stunden in der Sommerzeit als Ganzzahl ab. Wenn die Sommerzeit gültig ist, beträgt die Standardzeitverschiebung eine Stunde (obwohl in ein paar Regionen eine Zeitverschiebung von zwei Stunden gilt).

Wenn *Hours* den Wert **null**hat, wird der Handler für ungültige Parameter aufgerufen, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion " **errno** " auf " **EINVAL** " fest und gibt " **EINVAL**" zurück.

Es wird empfohlen, diese Funktion anstelle des Makros **_daylight** oder der veralteten Funktion **__daylight**zu verwenden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
