---
title: gmtime_s, _gmtime32_s, _gmtime64_s
ms.date: 4/2/2020
api_name:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
- _o__gmtime32_s
- _o__gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: e73d2d3cca852b657631361d8271bec7f9c86ac5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344078"
---
# <a name="gmtime_s-_gmtime32_s-_gmtime64_s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Konvertiert einen Zeitwert **tm** in eine tm-Struktur. Dies sind Versionen von [_gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md) mit Sicherheitsverbesserungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

## <a name="syntax"></a>Syntax

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>Parameter

*tmDest*<br/>
Zeiger auf [tm](../../c-runtime-library/standard-types.md) eine tm-Struktur. Die Felder der zurückgegebenen Struktur enthalten den ausgewerteten Wert des *Timerarguments* in UTC und nicht in der Ortszeit.

*sourceTime*<br/>
Zeiger auf die gespeicherte Zeit Die Zeit wird in Sekunden dargestellt, die seit dem 1. Januar 1970, Mitternacht (00:00: 00), verstrichen sind. Die Anzeige erfolgt im UTC-Format.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes werden in Errno.h definiert; eine Auflistung dieser Fehler finden Sie unter [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*tmDest*|*sourceTime*|Rückgabewert|Wert in *tmDest*|
|-----------|------------|------------|--------------------|
|**Null**|any|**Einval**|Nicht geändert.|
|Nicht **NULL** (zeigt auf gültigen Speicher)|**Null**|**Einval**|Alle Felder auf -1 festgelegt.|
|Nicht **NULL**|< 0|**Einval**|Alle Felder auf -1 festgelegt.|

Im Fall der ersten zwei Fehlerbedingungen, wird der ungültige Parameterhandler aufgerufen, so wie dies unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben **EINVAL**zurück.

## <a name="remarks"></a>Bemerkungen

Die **_gmtime32_s-Funktion** schlüsselt den *sourceTime-Wert* auf und speichert ihn in einer Struktur vom Typ **tm**, die in Time.h definiert ist. Die Adresse der Struktur wird in *tmDest*übergeben. Der Wert von *sourceTime* wird in der Regel von einem Aufruf der [Zeitfunktion](time-time32-time64.md) abgerufen.

> [!NOTE]
> Die Zielumgebung soll versuchen, zu bestimmen, ob die Sommerzeit wirksam ist. Die C-Laufzeitbibliothek wendet die Regeln der Vereinigten Staaten an, um die Berechnung der Sommerzeit zu implementieren.

Jedes der Strukturfelder ist vom Typ **int**, wie in der folgenden Tabelle dargestellt.

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
|**tm_isdst**|Immer 0 für **gmtime_s**.|

**_gmtime64_s**, die die **__time64_t-Struktur** verwendet, erlaubt, Datumsangaben bis 23:59:59, 31. Dezember 3000, UTC, ausgedrückt zu werden; während **gmtime32_s** nur Daten bis 23:59:59 Januar 18, 2038, UTC darstellen. Der 1. Januar 1970 (Mitternacht) ist der untere Datumsbereich für diese beiden Funktionen.

**gmtime_s** ist eine Inline-Funktion, die **_gmtime64_s** auswertet und **time_t** **entspricht __time64_t**. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit-time_t zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. **time_t** Dadurch wird **gmtime_s** **in _gmtime32_s**ausgekleidet. Dies ist nicht zu empfehlen, weil Ihre Anwendung nach dem 18. Januar 2038 fehlschlagen kann. Die Verwendung dieses Makros ist auf 64-Bit-Plattformen nicht zulässig.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------------|---------------------|-|
|**gmtime_s**, **_gmtime32_s**, **_gmtime64_s**|\<time.h>|\<ctime> \<oder time.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
