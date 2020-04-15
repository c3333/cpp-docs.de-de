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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0abab77b1429b263c7e5d84a6d395f0411ebf8a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345300"
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

Null, wenn erfolgreich oder ein **Errno-Wert,** wenn ein Fehler auftritt.

## <a name="remarks"></a>Bemerkungen

Die **_get_daylight-Funktion** ruft die Anzahl der Stunden in der Sommerzeit als ganzzahlige ab. Wenn die Sommerzeit gültig ist, beträgt die Standardzeitverschiebung eine Stunde (obwohl in ein paar Regionen eine Zeitverschiebung von zwei Stunden gilt).

Wenn *Stunden* **NULL**ist, wird der ungültige Parameterhandler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben aufgerufen. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt **EINVAL**zurück.

Es wird empfohlen, diese Funktion anstelle des **Makros _daylight** oder der veralteten Funktion **__daylight zu**verwenden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_get_daylight**|\<time.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
