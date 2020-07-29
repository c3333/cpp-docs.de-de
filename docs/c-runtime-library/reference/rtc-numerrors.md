---
title: _RTC_NumErrors
ms.date: 11/04/2016
api_name:
- _RTC_NumErrors
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
- DLLExport
topic_type:
- apiref
f1_keywords:
- _RTC_NumErrors
- RTC_NumErrors
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
ms.openlocfilehash: 0e0af8596dbc7f48bc3f6b996219ec7c7a57749d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234028"
---
# <a name="_rtc_numerrors"></a>_RTC_NumErrors

Gibt die Gesamtzahl der Fehler zurück, die durch die Fehlerprüfung zur Laufzeit (RTC) erkannt werden können. Sie können diese Zahl als Steuerelement in einer- **`for`** Schleife verwenden, wobei jeder Wert in der Schleife an [_RTC_GetErrDesc](rtc-geterrdesc.md)-Element übermittelt wird.

## <a name="syntax"></a>Syntax

```C

int _RTC_NumErrors( void );
```

## <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, deren Wert die Gesamtzahl der Fehler darstellt, die von den Visual C++-Fehlerprüfungen zur Laufzeit erkannt werden können.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_RTC_NumErrors**|\<rtcapi.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Siehe auch

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[Laufzeitfehlerüberprüfung](../../c-runtime-library/run-time-error-checking.md)<br/>
