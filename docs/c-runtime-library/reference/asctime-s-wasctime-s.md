---
title: asctime_s, _wasctime_s
ms.date: 4/2/2020
api_name:
- _wasctime_s
- asctime_s
- _o__wasctime_s
- _o_asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 529663a8c36a1b934a4dd99852aee19fb1a1e6e6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217011"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Konvertiert eine **TM** -Zeitstruktur in eine Zeichenfolge. Diese Funktionen sind Versionen von [asctime, _wasctime](asctime-wasctime.md) mit Sicherheitsverbesserungen wie in [Sicherheitsfunktionen](../../c-runtime-library/security-features-in-the-crt.md) in der CRT beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Ein Zeiger auf einen Puffer, um das Ergebnis der Zeichenfolge zu speichern. Diese Funktion nimmt einen Zeiger auf einen gültigen Speicherort mit einer Größe an, die von " *numofelements*" angegeben wird.

*numberOfElements*<br/>
Die Größe des Puffers, der zum Speichern des Ergebnisses verwendet wird.

*tmsource*<br/>
Zeit-/Datumsstruktur. Diese Funktion nimmt einen Zeiger auf ein gültiges **`struct`** **TM** -Objekt an.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Wenn es einen Fehler gibt, wird der ungültige Parameterhandler wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben aufgerufen. Wenn die weitere Ausführung zugelassen wird, ist der Rückgabewert ein Fehlercode. Fehlercodes sind in ERRNO.H definiert. Weitere Informationen finden Sie unter [errno-Konstanten](../../c-runtime-library/errno-constants.md). Die jeweiligen Fehlercodes, die für jede Fehlerbedingung zurückgegeben werden, sind in folgender Tabelle aufgelistet.

### <a name="error-conditions"></a>Fehlerbedingungen

|*ert*|*numberOfElements*|*tmsource*|Rückgabewert|Wert im *Puffer*|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|Any|Any|**Eingabe**|Nicht geändert|
|Not **null** (zeigt auf gültigen Speicher)|0|Any|**Eingabe**|Nicht geändert|
|Nicht **null**|0<Größe<26|Any|**Eingabe**|leere Zeichenfolge|
|Nicht **null**|>= 26|**NULL**|**Eingabe**|leere Zeichenfolge|
|Nicht **null**|>= 26|Ungültige Zeitstruktur oder Zeitkomponentenwerte außerhalb des Bereichs|**Eingabe**|leere Zeichenfolge|

> [!NOTE]
> Fehlerbedingungen für **wasctime_s** ähneln **asctime_s** , mit der Ausnahme, dass die Größenbeschränkung in Wörtern gemessen wird.

## <a name="remarks"></a>Bemerkungen

Die **Asctime** -Funktion konvertiert eine als-Struktur gespeicherte Zeit in eine Zeichenfolge. Der *tmsource* -Wert wird normalerweise durch einen Aufruf von **gmtime** oder **localtime**abgerufen. Beide Funktionen können verwendet werden, um eine **TM** -Struktur zu füllen, wie Sie in Time definiert ist. Micha.

|timeptr.member|Wert|
|--------------------|-----------|
|**tm_hour**|Stunden seit Mitternacht (0-23)|
|**tm_isdst**|Positiv bei Sommerzeit; 0 bei Winterzeit; negativ bei unbekannter Zeit. Die C-Laufzeitbibliothek wendet die Regeln der Vereinigten Staaten an, um die Berechnung der Sommerzeit (DST, Daylight Saving Time) zu implementieren.|
|**tm_mday**|Tag des Monats (1–31)|
|**tm_min**|Minuten nach Stunde (0-59)|
|**tm_mon**|Monat (0-11; Januar = 0)|
|**tm_sec**|Sekunden nach Minute (0-59)|
|**tm_wday**|Wochentag (0-6; Sonntag = 0)|
|**tm_yday**|Tag des Jahres (0-365; 1. Januar = 0)|
|**tm_year**|Jahr (aktuelles Jahr minus 1900)|

Die konvertierte Zeichenfolge wird auch gemäß den lokalen Zeitzoneneinstellungen angepasst. Informationen zur Konfiguration der Zeitzonen finden Sie unter den [time, _time32, _time64](time-time32-time64.md), [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) und [localtime_s, _localtime32_s, _localtime64_2](localtime-s-localtime32-s-localtime64-s.md)-Funktionen. Informationen zur Definition der Zeitzonenumgebung und globalen Variablen finden Sie unter der [_tzset](tzset.md)-Funktion.

Das von **asctime_s** erzeugte Zeichen folgen Ergebnis enthält genau 26 Zeichen und hat das Formular `Wed Jan 02 02:03:55 1980\n\0` . Eine 24-Stunden-Uhr wird verwendet. Alle Felder haben eine feste Breite. Die Zeilenwechsel- und Nullzeichen nehmen die letzten beiden Stellen der Zeichenfolge ein. Der Wert, der als zweiter Parameter übergeben wird, sollte mindestens so hoch sein. Wenn der Wert kleiner ist, wird der Fehlercode " **Eingabe**" zurückgegeben.

**_wasctime_s** ist eine breit Zeichen Version von **asctime_s**. **_wasctime_s** und **asctime_s** Verhalten sich andernfalls identisch.

Die Debug-Bibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Routinemäßige Allgemeintext-Zuordnung

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

Die Verwendung dieser Funktionen in C++ wird durch Überladungen (als Vorlagen vorhanden) vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> oder \<wchar.h>|

## <a name="security"></a>Sicherheit

Wenn der Puffer Zeiger nicht **null** ist und der Zeiger nicht auf einen gültigen Puffer zeigt, überschreibt die Funktion das, was sich am Speicherort befindet. Dies kann auch zu einer Zugriffsverletzung führen.

Wenn das übergebene Größenargument größer als die tatsächliche Puffergröße ist, kann ein [Pufferüberlauf](/windows/win32/SecBP/avoiding-buffer-overruns) auftreten.

## <a name="example"></a>Beispiel

Dieses Programm versetzt die Systemzeit in die lange ganzzahlige **aclock**, übersetzt Sie in die Struktur **newTime** und konvertiert Sie dann mithilfe der **asctime_s** -Funktion in eine Zeichenfolge Form für die Ausgabe.

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
