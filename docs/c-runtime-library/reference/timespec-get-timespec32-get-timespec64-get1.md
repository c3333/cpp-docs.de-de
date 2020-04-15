---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 4/2/2020
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
- _o__timespec32_get
- _o__timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: fc6d91b076f2dd2e25c55d9cf7062e81c3fab11a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362492"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get, _timespec32_get, _timespec64_get

Legt das Intervall, auf das das erste Argument verweist, auf die aktuelle Kalenderzeit fest, basierend auf der angegebenen Zeitbasis.

## <a name="syntax"></a>Syntax

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>Parameter

*time_spec*<br/>
Zeiger auf eine Struktur, die auf die seit dem Beginn der Epoche verstrichene Zeit in Sekunden und Nanosekunden festgelegt ist.

*base*<br/>
Ein implementierungsspezifischer Wert ungleich null, der die Zeitbasis angibt.

## <a name="return-value"></a>Rückgabewert

Der Wert der *Basis,* wenn sie erfolgreich ist, andernfalls gibt sie Null zurück.

## <a name="remarks"></a>Bemerkungen

Die **timespec_get-Funktionen** legen die aktuelle Zeit in der Struktur fest, auf die das *Argument time_spec* zeigt. Alle Versionen dieser Struktur haben zwei Member, **tv_sec** und **tv_nsec**. Der **tv_sec** Wert wird auf die gesamte Anzahl der Sekunden festgelegt und **tv_nsec** auf die integrale Anzahl von Nanosekunden, gerundet auf die Auflösung der Systemuhr, seit dem Beginn der Epoche durch *Basis*angegeben .

**Microsoft Specific**

Diese Funktionen unterstützen nur **TIME_UTC** als *Basiswert.* Dadurch wird der *time_spec* Wert auf die Anzahl der Sekunden und Nanosekunden seit dem Epochenbeginn, Mitternacht, 1. Januar 1970, Koordinierte Weltzeit (UTC) festgelegt. In einer **Struktur** **_timespec32**ist **tv_sec** ein **__time32_t** Wert. In einer **Struktur** **_timespec64**ist **tv_sec** ein **__time64_t** Wert. In einer **Strukturzeitspezifikation** **ist tv_sec** ein **struct** **time_t** Typ, der 32 Bit oder 64 Bit lang ist, je nachdem, ob das Präprozessormakro _USE_32BIT_TIME_T definiert ist. Die **timespec_get-Funktion** ist eine Inline-Funktion, die **_timespec32_get** aufruft, wenn _USE_32BIT_TIME_T definiert ist. Andernfalls ruft sie **_timespec64_get**auf.

**Ende Microsoft-spezifisch**

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C: \<time.h>, C++: \<ctime> oder \<time.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
