---
title: gmtime, _gmtime32, _gmtime64
ms.date: 4/2/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: 16f4315837873c8d78065ea97a11188bdddedbed
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916239"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

Konvertiert einen **time_t** Zeitwert in eine **TM** -Struktur. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntax

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parameter

*sourcetime*<br/>
Zeiger auf die gespeicherte Zeit. Die Zeit wird in Sekunden dargestellt, die seit dem 1. Januar 1970, Mitternacht (00:00: 00), verstrichen sind. Die Anzeige erfolgt im UTC-Format.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Struktur des Typs [tm](../../c-runtime-library/standard-types.md). Die Felder der zurückgegebenen Struktur enthalten den ausgewerteten Wert des *sourcetime* -Arguments in UTC und nicht in Ortszeit. Jedes der Struktur Felder hat den Typ " **int**", wie im folgenden dargestellt:

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
|**tm_isdst**|Immer 0 für **gmtime**.|

Sowohl die 32-Bit-als auch die 64-Bit-Version von **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)und [localtime](localtime-localtime32-localtime64.md) verwenden jeweils eine gemeinsame **TM** -Struktur pro Thread für die Konvertierung. Jeder Aufruf dieser Funktionen zerstört das Ergebnis des vorherigen Aufrufs. Wenn *sourcetime* ein Datum vor Mitternacht (1. Januar 1970) darstellt, gibt **gmtime** den Wert **null**zurück. Es gibt keine Fehlerrückgabe.

**_gmtime64**, die die **__time64_t** Struktur verwendet, ermöglicht das Ausdrücken von Datumsangaben bis 23:59:59, 31. Dezember 3000, UTC, während **_gmtime32** nur Datumsangaben bis zum 18. Januar 23:59:59, 2038, UTC darstellen. Der 1. Januar 1970 (Mitternacht) ist der untere Datumsbereich für beide Funktionen.

**gmtime** ist eine Inline Funktion, die zu **_gmtime64**ausgewertet wird, und **time_t** entspricht **__time64_t** , es sei denn, **_USE_32BIT_TIME_T** definiert ist. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit- **time_t**zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. Dies bewirkt jedoch, dass die **gmtime** -Funktion in **_gmtime32** und **time_t** als **__time32_t**definiert wird. Diese Aktion sollte nicht durchgeführt werden, da sie auf 64-Bit-Plattformen nicht zugelassen ist und die Anwendung auf jedem Fall nach dem 18. Januar 2038 fehlschlägt.

Diese Funktionen überprüfen ihre Parameter. Wenn *sourcetime* ein NULL-Zeiger ist oder der *sourcetime* -Wert negativ ist, rufen diese Funktionen einen Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben die Funktionen **null** zurück und legen **errno** auf **EINVAL**fest.

## <a name="remarks"></a>Hinweise

Die **_gmtime32** -Funktion unterteilt den *sourcetime* -Wert und speichert ihn in einer statisch zugeordneten Struktur vom Typ **TM**, die zeitlich definiert ist. Micha. Der Wert von *sourcetime* wird in der Regel durch einen Aufruf der [time](time-time32-time64.md) -Funktion abgerufen.

> [!NOTE]
> In den meisten Fällen versucht die Zielumgebung zu bestimmen, ob die Sommerzeit wirksam ist. Die C-Laufzeitbibliothek geht davon aus, dass die Regeln der Vereinigten Staaten für die Implementierung der Berechnung der Sommerzeit (DST, Daylight Saving Time) angewendet werden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32** **_gmtime64**|\<time.h>|\<CTime-> \<oder Time. h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
