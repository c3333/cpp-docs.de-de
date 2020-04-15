---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
description: Beschreibt die _mkgmtime-, _mkgmtime32- und _mkgmtime64 C-Runtime-Bibliotheksfunktionen und gibt Beispiele für deren Verwendung.
ms.date: 4/2/2020
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
- _o__mkgmtime32
- _o__mkgmtime64
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
ms.openlocfilehash: e8b3170fc0413a878777035fd76aac5eefa7b6bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338775"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Konvertiert eine UTC-Zeit, die durch eine **Struktur** **tm** dargestellt wird, in eine UTC-Zeit, die durch einen **time_t-Typ** dargestellt wird.

## <a name="syntax"></a>Syntax

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>Parameter

*timeptr*\
Ein Zeiger auf die UTC-Zeit als zu konvertierende **Struktur** **tm.**

## <a name="return-value"></a>Rückgabewert

Eine Menge vom Typ **__time32_t** oder **__time64_t,** die die Anzahl der Sekunden darstellt, die seit Mitternacht, dem 1. Januar 1970, in der koordinierten Weltzeit (UTC) verstrichen sind. Wenn das Datum anicht zulässig ist (siehe Abschnitt "Bemerkungen") oder die Eingabe nicht als gültige Zeit interpretiert werden kann, beträgt der Rückgabewert -1.

## <a name="remarks"></a>Bemerkungen

Die **_mkgmtime32-** und **_mkgmtime64-Funktionen** konvertieren eine UTC-Zeit in einen **__time32_t-** oder **__time64_t-Typ,** der die Zeit in UTC darstellt. Um eine lokale Zeit in UTC-Zeit zu konvertieren, verwenden Sie stattdessen **mktime**, **_mktime32**und **_mktime64.**

**_mkgmtime** ist eine Inlinefunktion, die **_mkgmtime64**auswertet, und **time_t** entspricht **__time64_t**. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit-time_t zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. **time_t** Wir empfehlen es nicht, da Ihre Anwendung nach dem 18. Januar 2038, **time_t**dem maximalen Bereich eines 32-Bit-time_t, möglicherweise fehlschlägt. Auf 64-Bit-Plattformen ist das überhaupt nicht erlaubt.

Die übergebene Zeitstruktur wird wie folgt geändert, so wie sie von den **_mktime** Funktionen geändert wird: Die **Felder tm_wday** und **tm_yday** werden basierend auf den Werten **von tm_mday** und **tm_year**auf neue Werte festgelegt. Da davon ausgegangen wird, dass die Zeit UTC ist, wird das **tm_isdst** Feld ignoriert.

Der Bereich der **_mkgmtime32-Funktion** reicht von Mitternacht, 1. Januar 1970, UTC bis 23:59:59 Januar 18, 2038, UTC. Die Reichweite von **_mkgmtime64** reicht von Mitternacht, 1. Januar 1970, UTC bis 23:59:59, 31. Dezember 3000, UTC. Ein Out-of-Range-Datum ergibt einen Rückgabewert von -1. Der Bereich der **_mkgmtime** hängt davon ab, ob **_USE_32BIT_TIME_T** definiert ist. Wenn er nicht definiert ist, was der Standardwert ist, entspricht der Bereich **_mkgmtime64**. Andernfalls ist der Bereich auf den 32-Bit-Bereich von **_mkgmtime32**beschränkt.

Sowohl **gmtime als** auch **localtime** verwenden einen gemeinsamen statischen Puffer für die Konvertierung. Wenn Sie diesen Puffer **für _mkgmtime**bereitstellen, werden die vorherigen Inhalte zerstört.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="examples"></a>Beispiele

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

Das folgende Beispiel zeigt, wie die unvollständige Struktur durch **_mkgmtime**ausgefüllt wird. Es berechnet Werte sowohl für den Wochentag als auch für das Jahr.

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)\
[asctime, _wasctime](asctime-wasctime.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s, _gmtime32_s _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[time, _time32, _time64](time-time32-time64.md)
