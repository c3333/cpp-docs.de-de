---
title: clock
ms.date: 11/04/2016
api_name:
- clock
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 03d1a9ece92dbedfdceb89488e5d0440dc64f7ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220729"
---
# <a name="clock"></a>clock

Berechnet die durch den aufrufenden Prozess verwendete Wanduhrzeit.

## <a name="syntax"></a>Syntax

```C
clock_t clock( void );
```

## <a name="return-value"></a>Rückgabewert

Die verstrichene Zeit seit der CRT-Initialisierung zu Beginn des Prozesses, gemessen in **CLOCKS_PER_SEC** Einheiten pro Sekunde. Wenn die verstrichene Zeit nicht verfügbar ist oder die maximale positive Zeit überschritten hat, die als **clock_t** Typ aufgezeichnet werden kann, gibt die Funktion den Wert zurück `(clock_t)(-1)` .

## <a name="remarks"></a>Bemerkungen

Die **Clock** -Funktion gibt an, wie viel Zeit seit der CRT-Initialisierung während des Prozess Starts vergangen ist. Beachten Sie, dass diese Funktion nicht streng mit ISO C konform ist, welche die Netto-CPU-Zeit als Rückgabewert nennt. Verwenden Sie zum Abrufen von CPU-Zeiten die Win32-Funktion [GetProcessTimes](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocesstimes). Um die verstrichene Zeit in Sekunden zu ermitteln, teilen Sie den von der **Clock** -Funktion zurückgegebenen Wert durch das Makro **CLOCKS_PER_SEC**.

Wenn genug Zeit ist, kann der von der **Uhr** zurückgegebene Wert den maximalen positiven Wert von **clock_t**überschreiten. Wenn der Prozess länger ausgeführt wurde, ist der von der **Uhr** zurückgegebene Wert immer `(clock_t)(-1)` , wie vom ISO C99-Standard (7.23.2.1) und ISO C11 Standard (7.27.2.1) angegeben. Microsoft implementiert **clock_t** als **`long`** , eine ganze Zahl mit Vorzeichen und 32 eine ganze Zahl mit Vorzeichen, und das **CLOCKS_PER_SEC** -Makro wird als 1000 definiert. Dies ergibt **einen maximalen Wert** für die Zeit Rückgabewert von 2147483,647 Sekunden oder etwa 24,8 Tage. Verlassen Sie sich nicht auf den von der **Uhr** zurückgegebenen Wert in Prozessen, die länger als diesen Zeitraum ausgeführt wurden. Sie können die 64-Bit- [Zeit](time-time32-time64.md) Funktion oder die Windows [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) -Funktion verwenden, um Prozess verstrichene Zeiten von vielen Jahren aufzuzeichnen.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**clock**|\<time.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_clock.c
// This sample uses clock() to 'sleep' for three
// seconds, then determines how long it takes
// to execute an empty loop 600000000 times.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Pauses for a specified number of clock cycles.
void do_sleep( clock_t wait )
{
   clock_t goal;
   goal = wait + clock();
   while( goal > clock() )
      ;
}

const long num_loops = 600000000L;

int main( void )
{
   long    i = num_loops;
   clock_t start, finish;
   double  duration;

   // Delay for a specified time.
   printf( "Delay for three seconds\n" );
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );
   printf( "Done!\n" );

   // Measure the duration of an event.
   start = clock();
   while( i-- )
      ;
   finish = clock();
   duration = (double)(finish - start) / CLOCKS_PER_SEC;
   printf( "Time to do %ld empty loops is ", num_loops );
   printf( "%2.3f seconds\n", duration );
}
```

```Output
Delay for three seconds
Done!
Time to do 600000000 empty loops is 1.354 seconds
```

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[difftime, _difftime32, _difftime64](difftime-difftime32-difftime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
