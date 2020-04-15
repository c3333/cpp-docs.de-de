---
title: asctime, _wasctime
ms.date: 4/2/2020
api_name:
- _wasctime
- asctime
- _o__wasctime
- _o_asctime
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
- _tasctime
- asctime
- _wasctime
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: bda14f3b6046378ad23148371f354bb910163d3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350479"
---
# <a name="asctime-_wasctime"></a>asctime, _wasctime

Konvertieren Sie eine **tm-Zeitstruktur** in eine Zeichenfolge. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

## <a name="syntax"></a>Syntax

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>Parameter

*timeptr*<br/>
Zeit-/Datumsstruktur.

## <a name="return-value"></a>Rückgabewert

**asctime** gibt einen Zeiger auf das Ergebnis der Zeichenfolge zurück. **_wasctime** gibt einen Zeiger auf das Ergebnis der Zeichenfolge mit großen Zeichen zurück. Es gibt keinen Fehlerrückgabewert.

## <a name="remarks"></a>Bemerkungen

Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

Die **asctime-Funktion** konvertiert eine als Struktur gespeicherte Zeit in eine Zeichenfolge. Der *timeptr-Wert* wird in der Regel von einem Aufruf von **gmtime** oder **localtime**abgerufen, die beide einen Zeiger an eine **tm-Struktur** zurückgeben, die in TIME definiert ist. H.

|timeptr.member|Wert|
|--------------------|-----------|
|**tm_hour**|Stunden seit Mitternacht (0-23)|
|**tm_isdst**|Positiv bei Sommerzeit; 0 bei Winterzeit; negativ bei unbekannter Zeit. Die C-Laufzeitbibliothek wendet die Regeln der Vereinigten Staaten an, um die Berechnung der Sommerzeit (DST, Daylight Saving Time) zu implementieren.|
|**tm_mday**|Monat des Monats (1-31)|
|**tm_min**|Minuten nach Stunde (0-59)|
|**tm_mon**|Monat (0-11; Januar = 0)|
|**tm_sec**|Sekunden nach Minute (0-59)|
|**tm_wday**|Wochentag (0-6; Sonntag = 0)|
|**tm_yday**|Tag des Jahres (0-365; 1. Januar = 0)|
|**tm_year**|Jahr (aktuelles Jahr minus 1900)|

Die konvertierte Zeichenfolge wird auch gemäß den lokalen Zeitzoneneinstellungen angepasst. Informationen zur Konfiguration der Zeitzonen finden Sie unter den [time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md) und [localtime](localtime-localtime32-localtime64.md)-Funktionen. Informationen zur Definition der Zeitzonenumgebung und globalen Variablen finden Sie unter der [_tzset](tzset.md)-Funktion.

Das von **asctime** erzeugte Zeichenfolgenergebnis enthält `Wed Jan 02 02:03:55 1980\n\0`genau 26 Zeichen und hat das Formular . Eine 24-Stunden-Uhr wird verwendet. Alle Felder haben eine feste Breite. Die Zeilenwechsel- und Nullzeichen nehmen die letzten beiden Stellen der Zeichenfolge ein. **asctime** verwendet einen einzelnen, statisch zugewiesenen Puffer, um die Rückgabezeichenfolge zu halten. Jeder Aufruf dieser Funktion zerstört das Ergebnis des vorherigen Aufrufs.

**_wasctime** ist eine breitgefächerte Version von **asctime**. **_wasctime** und **asctime** verhalten sich ansonsten gleich.

Diese Funktionen überprüfen ihre Parameter. Wenn *timeptr* ein Nullzeiger ist oder Werte aneben enthalten, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion **NULL** zurück und setzt **errno** auf **EINVAL**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Routinemäßige Allgemeintext-Zuordnung

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> oder \<wchar.h>|

## <a name="example"></a>Beispiel

Dieses Programm platziert die Systemzeit in der langen ganzzahligen **Uhr**, übersetzt sie in die Struktur **newtime** und konvertiert sie dann in String-Form für die Ausgabe, mit der **asctime-Funktion.**

```C
// crt_asctime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
    struct tm   *newTime;
    time_t      szClock;

    // Get time in seconds
    time( &szClock );

    // Convert time to struct tm form
    newTime = localtime( &szClock );

    // Print local time as a string.
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996
    // Note: asctime is deprecated; consider using asctime_s instead
}
```

```Output
Current date and time: Sun Feb 03 11:38:58 2002
```

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
