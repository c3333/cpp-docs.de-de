---
title: mktime, _mktime32, _mktime64
ms.date: 4/2/2020
api_name:
- _mktime32
- mktime
- _mktime64
- _o__mktime32
- _o__mktime64
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
- mktime
- _mktime64
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
ms.openlocfilehash: b0981f33d70945083eacd28eb7517e80b3f2539f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338703"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime, _mktime32, _mktime64

Konvertiert die Ortszeit in einen Kalenderwert.

## <a name="syntax"></a>Syntax

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>Parameter

*timeptr*<br/>
Zeiger auf Zeitstruktur. Weitere Informationen finden Sie unter [asctime](asctime-wasctime.md).

## <a name="return-value"></a>Rückgabewert

**_mktime32** gibt die angegebene Kalenderzeit zurück, die als Wert vom Typ [time_t](../../c-runtime-library/standard-types.md)codiert ist. Wenn *timeptr* auf ein Datum vor Mitternacht, dem 1. Januar 1970, verweist oder die Kalenderzeit nicht dargestellt werden kann, **gibt _mktime32** -1 -1 -cast zurück, um **time_t**einzugeben. Wenn **sie _mktime32** verwenden und wenn *timeptr* auf ein Datum nach 23:59:59 18. Januar 2038, Koordinierte Weltzeit (UTC) verweist, gibt er -1 cast zurück, um **time_t**einzugeben.

**_mktime64** gibt -1-Umwandlung zurück, um **__time64_t** *einzugeben, wenn timeptr* auf ein Datum nach 23:59:59, 31. Dezember 3000, UTC verweist.

## <a name="remarks"></a>Bemerkungen

Die Funktionen **mktime** **, _mktime32** und **_mktime64** wandeln die angegebene (möglicherweise unvollständige) Zeitstruktur, auf die durch *Timeptr* verwiesen wird, in eine vollständig definierte Struktur mit normalisierten Werten um und wandeln sie dann in einen **time_t** Kalenderzeitwert um. Die konvertierte Zeit hat dieselbe Codierung wie die Werte, die von der Funktion [Uhrzeit](time-time32-time64.md) zurückgegeben wurden. Die ursprünglichen Werte der **tm_wday** und **tm_yday** Komponenten der *Timeptrstruktur* werden ignoriert, und die ursprünglichen Werte der anderen Komponenten sind nicht auf ihre normalen Bereiche beschränkt.

**mktime** ist eine Inlinefunktion, die **_mktime64**entspricht, es sei **denn, _USE_32BIT_TIME_T** definiert ist, in diesem Fall entspricht sie **_mktime32**.

Nach einer Anpassung an **UTC, _mktime32** Handles Daten von Mitternacht, 1. Januar 1970, bis 23:59:59 Januar 18, 2038, UTC. **_mktime64** Handles datiert von Mitternacht, 1. Januar 1970 bis 23:59:59, 31. Dezember 3000. Diese Anpassung kann dazu führen, dass diese Funktionen -1 zurückgeben (in **time_t**, **__time32_t** oder **__time64_t**umgegossen), obwohl sich das angegebene Datum innerhalb des Bereichs befindet. Wenn Sie sich zum Beispiel im ägyptischen Kairo aufhalten, wo die Ortszeit zwei Stunden vor der UTC liegt, werden diese zwei Stunden zunächst von dem in *timeptr* angegebenen Datum abgezogen. Dadurch liegt das Datum nun möglicherweise außerhalb des zulässigen Bereichs.

Diese Funktionen können zum Überprüfen und Ausfüllen einer tm-Struktur verwendet werden. Wenn diese Funktionen erfolgreich sind, legen sie die Werte **von tm_wday** und **tm_yday** entsprechend fest und legen die anderen Komponenten so fest, dass sie die angegebene Kalenderzeit darstellen, wobei ihre Werte jedoch in die normalen Bereiche erzwungen werden. Der endgültige Wert von **tm_mday** wird erst festgelegt, wenn **tm_mon** und **tm_year** bestimmt sind. Wenn Sie eine **tm-Strukturzeit** angeben, legen Sie das Feld **tm_isdst** auf:

- Null (0) weist darauf hin, dass die Normalzeit gilt.

- Ein Wert größer als 0 weist darauf hin, dass die Sommerzeit gilt.

- Ein Wert kleiner als null gibt an, dass der C-Laufzeitbibliothekscode berechnet, ob Normalzeit oder Sommerzeit gilt.

Die C-Laufzeitbibliothek bestimmt das Sommerzeitverhalten anhand der [ZZ](tzset.md)-Umgebungsvariable. Wenn **TZ** nicht festgelegt ist, wird der Win32-API-Aufruf [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) verwendet, um die Sommerzeitinformationen vom Betriebssystem abzurufen. Wenn dies fehlschlägt, geht die Bibliothek davon aus, dass die Regeln der Vereinigten Staaten für die Implementierung der Berechnung der Sommerzeit angewendet werden. **tm_isdst** ist ein pflichtgemäßes Feld. Wenn es nicht festgelegt wird, wird sein Wert nicht definiert und der Rückgabewert dieser Funktionen ist unvorhersehbar. Wenn *timeptr* auf eine **tm-Struktur** verweist, die von einem vorherigen Aufruf von [asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)oder [localtime](localtime-localtime32-localtime64.md) (oder Varianten dieser Funktionen) zurückgegeben wurde, enthält das **Feld tm_isdst** den richtigen Wert.

Beachten Sie, dass **gmtime** und **localtime** (und **_gmtime32**, **_gmtime64**, **_localtime32**und **_localtime64**) einen einzelnen Puffer pro Thread für die Konvertierung verwenden. Wenn Sie diesen Puffer an **mktime**, **_mktime32** oder **_mktime64**angeben, werden die vorherigen Inhalte zerstört.

Diese Funktionen überprüfen ihre Parameter. Handelt es sich bei *timeptr* um einen NULL-Zeiger, wird der ungültige Parameterhandler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben aufgerufen. Wenn die Ausführung fortgesetzt werden darf, geben die Funktionen -1 zurück und setzen **errno** auf **EINVAL**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>Beispielausgabe

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
