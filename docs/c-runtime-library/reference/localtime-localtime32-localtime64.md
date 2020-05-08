---
title: localtime, _localtime32, _localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: 764a3768610d97df2eb3af4ed0425065aba4b4fa
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916422"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime, _localtime32, _localtime64

Konvertiert einen Zeitwert und berichtigt die lokale Zeitzone. Sicherere Versionen dieser Funktionen sind verfügbar. Diese finden Sie unter [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md).

## <a name="syntax"></a>Syntax

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parameter

*sourcetime*<br/>
Zeiger auf die gespeicherte Zeit

## <a name="return-value"></a>Rückgabewert

Geben Sie einen Zeiger auf das Struktur Ergebnis oder **null** zurück, wenn das an die Funktion über gegebene Datum wie folgt lautet:

- Vor Mitternacht, 1. Januar 1970

- Nach 03:14:07, 19. Januar 2038, UTC (mit **_time32** und **time32_t**).

- Nach 23:59:59, dem 31. Dezember 3000, UTC (mit **_time64** und **__time64_t**).

**_localtime64**, die die **__time64_t** Struktur verwendet, ermöglicht das Ausdrücken von Datumsangaben bis 23:59:59, 31. Dezember 3000, koordinierte Weltzeit (UTC), während **_localtime32** Datumsangaben bis zum 18. Januar 23:59:59, 2038 UTC, darstellt.

**localtime** ist eine Inline Funktion, die als **_localtime64**ausgewertet wird und **time_t** Äquivalent zu **__time64_t**ist. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit- **time_t**zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. Dies führt dazu, dass " **localtime** " zu **_localtime32**ausgewertet wird. Dies ist nicht zu empfehlen, weil Ihre Anwendung nach dem 18. Januar 2038 fehlschlagen kann. Die Verwendung dieses Makros ist auf 64-Bit-Plattformen nicht zulässig.

Die Felder des Struktur Typs [TM](../../c-runtime-library/standard-types.md) speichern die folgenden Werte, von denen jeder ein **int**ist:

|Feld|Beschreibung|
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

## <a name="remarks"></a>Hinweise

Die **localtime** -Funktion konvertiert eine Zeit, die als [time_t](../../c-runtime-library/standard-types.md) Wert gespeichert ist, und speichert das Ergebnis in einer Struktur vom Typ [TM](../../c-runtime-library/standard-types.md). Der **lange** Wert *sourcetime* stellt die seit Mitternacht (00:00:00), 1, 1970, UTC verstrichenen Sekunden dar. Dieser Wert wird normalerweise aus der [time](time-time32-time64.md) -Funktion abgerufen.

Sowohl die 32-Bit-als auch die 64-Bit-Version von [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)und **localtime** verwenden jeweils eine einzelne **TM** -Struktur pro Thread für die Konvertierung. Jeder Aufruf dieser Routinen zerstört das Ergebnis des vorherigen Aufrufs.

" **localtime** " wird für die lokale Zeitzone korrigiert, wenn der Benutzer zunächst die globale Umgebungsvariable " **TZ**" festlegt. Wenn **TZ** festgelegt ist, werden auch drei andere Umgebungsvariablen (**_timezone**, **_daylight**und **_tzname**) automatisch festgelegt. Wenn die **TZ** -Variable nicht festgelegt ist, versucht **localtime** , die Zeitzoneninformationen zu verwenden, die in der Datums-/Uhrzeit-Anwendung in der Systemsteuerung angegeben sind. Wenn diese Information nicht abgerufen werden kann, wird standardmäßig PST8PDT verwendet, was die Zeitzone Pacific (PTC) darstellt. Unter [_tzset](tzset.md) finden Sie eine Beschreibung dieser Variablen. **TZ** ist eine Microsoft-Erweiterung, die nicht Teil der ANSI-Standard Definition von **localtime**ist.

> [!NOTE]
> Die Zielumgebung soll versuchen zu bestimmen, ob die Sommerzeit wirksam ist.

Diese Funktionen überprüfen ihre Parameter. Wenn *sourcetime* ein NULL-Zeiger ist oder der *sourcetime* -Wert negativ ist, rufen diese Funktionen einen Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben die Funktionen **null** zurück und legen **errno** auf **EINVAL**fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------------|---------------------|-|
|**localtime**, **_localtime32** **_localtime64**|\<time.h>|\<CTime-> \<oder Time. h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
    if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime->tm_hour = 12;

    char buff[30];
    asctime_s( buff, sizeof(buff), newtime );
    printf( "%.19s %s\n", buff, am_pm );
}
```

```Output
Tue Feb 12 10:05:58 AM
```

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
