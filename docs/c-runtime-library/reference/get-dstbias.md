---
title: _get_dstbias
ms.date: 4/2/2020
api_name:
- _get_dstbias
- __dstbias
- _o___dstbias
- _o__get_dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: 969b6d2dfd83a1a136fdfb3d17f8f843337b792c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345228"
---
# <a name="_get_dstbias"></a>_get_dstbias

Ruft die Sommerzeitverschiebung in Sekunden ab.

## <a name="syntax"></a>Syntax

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>Parameter

*seconds*<br/>
Die Verschiebung der Sommerzeit in Sekunden.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich oder ein **Errno-Wert,** wenn ein Fehler auftritt.

## <a name="remarks"></a>Bemerkungen

Die **_get_dstbias-Funktion** ruft die Anzahl der Sekunden in der Sommerzeit als ganzzahlige Abruf. Wenn die Sommerzeit gültig ist, beträgt die Standardzeitverschiebung 3600 Sekunden. Dies ist die Anzahl der Sekunden in einer Stunde (obwohl in ein paar Regionen eine Zeitverschiebung von zwei Stunden gilt).

Wenn *Sekunden* **NULL**ist, wird der ungültige Parameterhandler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben aufgerufen. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt **EINVAL**zurück.

Es wird empfohlen, diese Funktion anstelle des **Makros _dstbias** oder der veralteten Funktion **__dstbias**zu verwenden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
