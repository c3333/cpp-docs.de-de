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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 48d1104d9680fe8ab88f0f73bfc179f3e4cf45a6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919071"
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

**_mktime32** gibt die angegebene Kalenderzeit zurück, die als Wert des Typs [time_t](../../c-runtime-library/standard-types.md)codiert ist. Wenn *Timeptr* auf ein Datum vor Mitternacht, 1. Januar 1970 oder die Kalenderzeit nicht dargestellt werden kann, gibt **_mktime32** -1-Umwandlung in den Typ **time_t**zurück. Bei Verwendung **_mktime32** und wenn *Timeptr* auf ein Datum 23:59:59 nach dem 18. Januar 2038 (koordinierte Weltzeit, UTC) verweist, wird-1 in den Typ **time_t**umgewandelt.

der **_mktime64** gibt-1 in den Typ **__time64_t** zurück, wenn *Timeptr* auf ein Datum nach 23:59:59, dem 31. Dezember 3000, UTC verweist.

## <a name="remarks"></a>Hinweise

Die Funktionen **mktime**, **_mktime32** und **_mktime64** konvertieren die angegebene Zeitstruktur (möglicherweise unvollständig), auf die durch *Timeptr* verwiesen wird, in eine vollständig definierte Struktur mit normalisierten Werten. Anschließend wird Sie in einen **time_t** Calendar Time-Wert konvertiert. Die konvertierte Zeit hat dieselbe Codierung wie die Werte, die von der Funktion [Uhrzeit](time-time32-time64.md) zurückgegeben wurden. Die ursprünglichen Werte der **Tm_wday** -und **tm_yday** Komponenten der *Timeptr* -Struktur werden ignoriert, und die ursprünglichen Werte der anderen Komponenten sind nicht auf die normalen Bereiche beschränkt.

**mktime** ist eine Inline Funktion, die **_mktime64**entspricht, es sei denn, **_USE_32BIT_TIME_T** ist definiert. in diesem Fall entspricht Sie **_mktime32**.

Nach einer Anpassung an die UTC werden von **_mktime32** Datumsangaben von Mitternacht, 1. Januar 1970 bis 23:59:59. Januar 2038 UTC verarbeitet. **_mktime64** verarbeitet Datumsangaben von Mitternacht, dem 1. Januar 1970 bis 23:59:59, dem 31. Dezember 3000. Diese Anpassung kann bewirken, dass diese Funktionen-1 zurückgeben (umgewandelt in **time_t**, **__time32_t** oder **__time64_t**), obwohl sich das von Ihnen angegebene Datum innerhalb des gültigen Bereichs befindet. Wenn Sie sich zum Beispiel im ägyptischen Kairo aufhalten, wo die Ortszeit zwei Stunden vor der UTC liegt, werden diese zwei Stunden zunächst von dem in *timeptr* angegebenen Datum abgezogen. Dadurch liegt das Datum nun möglicherweise außerhalb des zulässigen Bereichs.

Diese Funktionen können zum Überprüfen und Ausfüllen einer tm-Struktur verwendet werden. Bei erfolgreicher Ausführung legen diese Funktionen die Werte von **Tm_wday** und **tm_yday** entsprechend fest und legen fest, dass die anderen Komponenten die angegebene Kalenderzeit darstellen, wobei die Werte jedoch auf die normalen Bereiche gesetzt werden. Der endgültige Wert von **tm_mday** wird erst festgelegt, wenn **Tm_mon** und **Tm_year** bestimmt werden. Wenn Sie eine **TM** -Struktur Zeit angeben, legen Sie das **Tm_isdst** -Feld auf Folgendes fest:

- Null (0) weist darauf hin, dass die Normalzeit gilt.

- Ein Wert größer als 0 weist darauf hin, dass die Sommerzeit gilt.

- Ein Wert kleiner als null gibt an, dass der C-Laufzeitbibliothekscode berechnet, ob Normalzeit oder Sommerzeit gilt.

Die C-Laufzeitbibliothek bestimmt das Sommerzeitverhalten anhand der [ZZ](tzset.md)-Umgebungsvariable. Wenn **TZ** nicht festgelegt ist, wird der Win32-API-Aufruf [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) verwendet, um die Informationen zur Sommerzeit vom Betriebssystem abzurufen. Wenn dies fehlschlägt, geht die Bibliothek davon aus, dass die Regeln der Vereinigten Staaten für die Implementierung der Berechnung der Sommerzeit angewendet werden. **Tm_isdst** ist ein erforderliches Feld. Wenn es nicht festgelegt wird, wird sein Wert nicht definiert und der Rückgabewert dieser Funktionen ist unvorhersehbar. Wenn *Timeptr* auf eine **TM** -Struktur verweist, die von einem vorherigen Aufruf von [Asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)oder [localtime](localtime-localtime32-localtime64.md) zurückgegeben wurde (oder Varianten dieser Funktionen), enthält das **Tm_isdst** Feld den richtigen Wert.

Beachten Sie, dass **gmtime** und **localtime** (und **_gmtime32**, **_gmtime64**, **_localtime32**und **_localtime64**) einen einzelnen Puffer pro Thread für die Konvertierung verwenden. Wenn Sie diesen Puffer für **mktime**, **_mktime32** oder **_mktime64**angeben, wird der vorherige Inhalt zerstört.

Diese Funktionen überprüfen ihre Parameter. Handelt es sich bei *timeptr* um einen NULL-Zeiger, wird der ungültige Parameterhandler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben aufgerufen. Wenn die weitere Ausführung zugelassen wird, geben die Funktionen-1 zurück und legen **errno** auf **EINVAL**fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
