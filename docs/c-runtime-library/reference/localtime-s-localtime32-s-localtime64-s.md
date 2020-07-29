---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 4/2/2020
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
- _o__localtime32_s
- _o__localtime64_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
ms.openlocfilehash: 26ebadf49632b9e312f3d0c0a0788720d3230312
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218610"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s, _localtime32_s, _localtime64_s

Konvertiert einen **time_t** Zeitwert in eine **TM** -Struktur und korrigiert für die lokale Zeitzone. Dies sind Versionen von [localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md) mit Sicherheitsverbesserungen wie in den [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t localtime_s(
   struct tm* const tmDest,
   time_t const* const sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   __time32_t const* sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   __time64_t const* sourceTime
);
```

### <a name="parameters"></a>Parameter

*tmdest*<br/>
Ein Zeiger auf die Zeitstruktur, die ausgefüllt wird

*sourcetime*<br/>
Zeiger auf die gespeicherte Zeit.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes sind in Errno.h definiert. Eine Liste dieser Fehler finden Sie unter [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*tmdest*|*sourcetime*|Rückgabewert|Wert in *tmdest*|Ruft ungültige Parametertyphandler auf|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|any|**Eingabe**|Nicht geändert|Ja|
|Not **null** (zeigt auf gültigen Speicher)|**NULL**|**Eingabe**|Alle Felder auf-1 festgelegt|Ja|
|Not **null** (zeigt auf gültigen Speicher)|kleiner als 0 (null) oder größer als **_MAX__TIME64_T**|**Eingabe**|Alle Felder auf-1 festgelegt|Nein|

Im Fall der ersten zwei Fehlerbedingungen, wird der ungültige Parameterhandler aufgerufen, so wie dies unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen " **errno** " auf " **EINVAL** " fest und geben " **EINVAL**" zurück.

## <a name="remarks"></a>Bemerkungen

Die **localtime_s** -Funktion konvertiert eine Zeit, die als [time_t](../../c-runtime-library/standard-types.md) Wert gespeichert ist, und speichert das Ergebnis in einer Struktur vom Typ [TM](../../c-runtime-library/standard-types.md). Der **time_t** Wert *sourcetime* stellt die Sekunden dar, die seit Mitternacht (00:00:00), 1. Januar 1970 UTC, verstrichen sind. Dieser Wert wird normalerweise aus der [time](time-time32-time64.md) -Funktion abgerufen.

**localtime_s** für die lokale Zeitzone korrigiert, wenn der Benutzer zuerst die globale Umgebungsvariable **TZ**festlegt. Wenn **TZ** festgelegt ist, werden auch drei andere Umgebungsvariablen (**_timezone**, **_daylight**und **_tzname**) automatisch festgelegt. Wenn die **TZ** -Variable nicht festgelegt ist, versucht **localtime_s** , die in der Systemsteuerung in der Datums-/uhrzeitanwendung angegebenen Zeitzoneninformationen zu verwenden. Wenn diese Information nicht abgerufen werden kann, wird standardmäßig PST8PDT verwendet, was die Zeitzone Pacific (PTC) darstellt. Unter [_tzset](tzset.md) finden Sie eine Beschreibung dieser Variablen. **TZ** ist eine Microsoft-Erweiterung, die nicht Teil der ANSI-Standard Definition von **localtime**ist.

> [!NOTE]
> Die Zielumgebung soll versuchen zu bestimmen, ob die Sommerzeit wirksam ist.

**_localtime64_s**, die die **__time64_t** Struktur verwendet, ermöglicht das Ausdrücken von Datumsangaben bis 23:59:59, 18. Januar 3001, koordinierte Weltzeit (UTC), während **_localtime32_s** Datumsangaben bis zum 18. Januar 23:59:59, 2038 UTC, darstellt.

**localtime_s** ist eine Inline Funktion, die **_localtime64_s**ergibt, und **time_t** entspricht **__time64_t**. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit- **time_t**zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. Dies führt dazu, dass **localtime_s** zu **_localtime32_s**ausgewertet wird. Dies ist nicht zu empfehlen, weil Ihre Anwendung nach dem 18. Januar 2038 fehlschlagen kann. Die Verwendung dieses Makros ist auf 64-Bit-Plattformen nicht zulässig.

Die Felder des Struktur Typs [TM](../../c-runtime-library/standard-types.md) speichern die folgenden Werte, von denen jeder eine ist **`int`** .

|Feld|BESCHREIBUNG|
|-|-|
|**tm_sec**|Sekunden nach Minute (0-59).|
|**tm_min**|Minuten nach Stunde (0-59).|
|**tm_hour**|Stunden seit Mitternacht (0-23).|
|**tm_mday**|Tag des Monats (1-31).|
|**tm_mon**|Monat (0-11; Januar = 0).|
|**tm_year**|Jahr (aktuelles Jahr minus 1900).|
|**tm_wday**|Wochentag (0-6; Sonntag = 0).|
|**tm_yday**|Tag des Jahres (0-365; 1. Januar = 0).|
|**tm_isdst**|Positiver Wert bei Sommerzeit; 0 bei Winterzeit; negativ bei unbekannter Zeit.|

Wenn die **TZ** -Umgebungsvariable festgelegt ist, setzt die C-Lauf Zeit Bibliothek voraus, dass die Regeln für die USA für die Implementierung der Berechnung der Sommerzeit (DST) angemessen sind.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s** **_localtime64_s**|\<time.h>|\<ctime> oder \<time.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_localtime_s.c
// This program uses _time64 to get the current time
// and then uses _localtime64_s() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm newtime;
    char am_pm[] = "AM";
    __time64_t long_time;
    char timebuf[26];
    errno_t err;

    // Get time as 64-bit integer.
    _time64( &long_time );
    // Convert to local time.
    err = _localtime64_s( &newtime, &long_time );
    if (err)
    {
        printf("Invalid argument to _localtime64_s.");
        exit(1);
    }
    if( newtime.tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime.tm_hour > 12 )        // Convert from 24-hour
        newtime.tm_hour -= 12;        // to 12-hour clock.
    if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime.tm_hour = 12;

    // Convert to an ASCII representation.
    err = asctime_s(timebuf, 26, &newtime);
    if (err)
    {
        printf("Invalid argument to asctime_s.");
        exit(1);
    }
    printf( "%.19s %s\n", timebuf, am_pm );
}
```

```Output
Fri Apr 25 01:19:27 PM
```

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
