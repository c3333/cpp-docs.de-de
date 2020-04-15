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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3c5d194da85eb5d008dfc9cf19f222ebb575747d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342119"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s, _localtime32_s, _localtime64_s

Konvertiert einen **time_t** Zeitwert in eine **tm-Struktur** und korrigiert die lokale Zeitzone. Dies sind Versionen von [localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md) mit Sicherheitsverbesserungen wie in den [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

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

*tmDest*<br/>
Ein Zeiger auf die Zeitstruktur, die ausgefüllt wird

*sourceTime*<br/>
Zeiger auf die gespeicherte Zeit.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes sind in Errno.h definiert. Eine Liste dieser Fehler finden Sie unter [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*tmDest*|*sourceTime*|Rückgabewert|Wert in *tmDest*|Ruft ungültige Parametertyphandler auf|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**Null**|any|**Einval**|Nicht geändert|Ja|
|Nicht **NULL** (zeigt auf gültigen Speicher)|**Null**|**Einval**|Alle Felder auf-1 festgelegt|Ja|
|Nicht **NULL** (zeigt auf gültigen Speicher)|kleiner als 0 oder größer als **_MAX__TIME64_T**|**Einval**|Alle Felder auf-1 festgelegt|Nein|

Im Fall der ersten zwei Fehlerbedingungen, wird der ungültige Parameterhandler aufgerufen, so wie dies unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben **EINVAL**zurück.

## <a name="remarks"></a>Bemerkungen

Die **localtime_s-Funktion** konvertiert eine als [time_t-Wert](../../c-runtime-library/standard-types.md) gespeicherte Zeit und speichert das Ergebnis in einer Struktur vom Typ [tm](../../c-runtime-library/standard-types.md). Der **time_t-Wert** *sourceTime* stellt die Sekunden dar, die seit Mitternacht (00:00:00), 1. Januar 1970, UTC verstrichen sind. Dieser Wert wird in der Regel aus der [Zeitfunktion](time-time32-time64.md) abgerufen.

**localtime_s** für die lokale Zeitzone korrigiert, wenn der Benutzer zuerst die globale Umgebungsvariable **TZ**festlegt. Wenn **TZ** gesetzt ist, werden auch drei weitere Umgebungsvariablen (**_timezone**, **_daylight**und **_tzname**) automatisch festgelegt. Wenn die **TZ-Variable** nicht festgelegt ist, **versucht localtime_s,** die in der Datums-/Uhrzeitanwendung in der Systemsteuerung angegebenen Zeitzoneninformationen zu verwenden. Wenn diese Information nicht abgerufen werden kann, wird standardmäßig PST8PDT verwendet, was die Zeitzone Pacific (PTC) darstellt. Unter [_tzset](tzset.md) finden Sie eine Beschreibung dieser Variablen. **TZ** ist eine Microsoft-Erweiterung und nicht Teil der ANSI-Standarddefinition von **Localtime**.

> [!NOTE]
> Die Zielumgebung soll versuchen zu bestimmen, ob die Sommerzeit wirksam ist.

**_localtime64_s**, die die **__time64_t-Struktur** verwendet, erlaubt, Daten bis 23:59:59, 18. Januar 3001, koordinierte Weltzeit (UTC) auszudrücken, während **_localtime32_s** Datumsangaben bis 23:59:59 Januar 18, 2038, UTC darstellt.

**localtime_s** ist eine Inline-Funktion, die **_localtime64_s**auswertet, und **time_t** entspricht **__time64_t**. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit-time_t zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. **time_t** Dadurch wird **localtime_s** **ausgewertet,** um _localtime32_s . Dies ist nicht zu empfehlen, weil Ihre Anwendung nach dem 18. Januar 2038 fehlschlagen kann. Die Verwendung dieses Makros ist auf 64-Bit-Plattformen nicht zulässig.

Die Felder des Strukturtyps [tm](../../c-runtime-library/standard-types.md) speichern die folgenden Werte, von denen jeder ein **int**ist.

|Feld|BESCHREIBUNG|
|-|-|
|**tm_sec**|Sekunden nach Minute (0- 59).|
|**tm_min**|Minuten nach Stunde (0- 59).|
|**tm_hour**|Stunden seit Mitternacht (0 - 23).|
|**tm_mday**|Monat des Monats (1 - 31).|
|**tm_mon**|Monat (0 - 11; Januar = 0).|
|**tm_year**|Jahr (aktuelles Jahr minus 1900).|
|**tm_wday**|Wochentag (0 - 6; Sonntag = 0).|
|**tm_yday**|Tag des Jahres (0 - 365; 1. Januar = 0).|
|**tm_isdst**|Positiver Wert bei Sommerzeit; 0 bei Winterzeit; negativ bei unbekannter Zeit.|

Wenn die **Umgebungsvariable TZ** festgelegt ist, übernimmt die C-Laufzeitbibliothek Regeln, die den USA für die Implementierung der Berechnung der Sommerzeit (DST) angemessen sind.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<ctime> \<oder time.h>|

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

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
