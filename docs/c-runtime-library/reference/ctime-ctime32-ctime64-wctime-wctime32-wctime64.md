---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 4/2/2020
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
- _o__wctime32
- _o__wctime64
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
ms.openlocfilehash: 7dc87f417db93f8ad0d90de1270c19997669fb7c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914835"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Konvertieren Sie einen Zeitwert in eine Zeichenfolge, und passen Sie sie an die Zeitzoneneinstellungen an. Sicherere Versionen dieser Funktionen sind verfügbar. Sie finden sie unter [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

## <a name="syntax"></a>Syntax

```C
char *ctime( const time_t *sourceTime );
char *_ctime32( const __time32_t *sourceTime );
char *_ctime64( const __time64_t *sourceTime );
wchar_t *_wctime( const time_t *sourceTime );
wchar_t *_wctime32( const __time32_t *sourceTime );
wchar_t *_wctime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parameter

*sourcetime*<br/>
Zeiger auf die zu konvertierende gespeicherte Zeit.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Zeichenfolgenergebnis **Null** wird zurückgegeben, wenn Folgendes gilt:

- *sourcetime* stellt ein Datum vor Mitternacht (1. Januar 1970 UTC) dar.

- Wenn Sie **_ctime32** oder **_wctime32** verwenden und *sourcetime* ein Datum 23:59:59 nach dem 18. Januar 2038 UTC (UTC) darstellt.

- Wenn Sie **_ctime64** oder **_wctime64** verwenden und *sourcetime* ein Datum nach 23:59:59, dem 31. Dezember 3000, UTC darstellt.

**ctime** ist eine Inline Funktion, die zu **_ctime64** ausgewertet wird und **time_t** **__time64_t**entspricht. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit- **time_t**zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. Dies führt dazu, dass **ctime** zu **_ctime32**ausgewertet wird. Dies ist nicht zu empfehlen, weil Ihre Anwendung nach dem 18. Januar 2038 fehlschlagen kann. Die Verwendung dieses Makros ist auf 64-Bit-Plattformen nicht zulässig.

## <a name="remarks"></a>Hinweise

Die **ctime** -Funktion konvertiert einen als [time_t](../../c-runtime-library/standard-types.md) Wert gespeicherten Zeitwert in eine Zeichenfolge. Der *sourcetime* -Wert wird in der Regel von einem Aufruf an [time](time-time32-time64.md)abgerufen, der die Anzahl der Sekunden zurückgibt, die seit Mitternacht (00:00:00), dem 1. Januar 1970, der koordinierten Weltzeit (UTC) vergangen sind. Der Rückgabewert der Zeichenfolge enthält genau 26 Zeichen und sieht so aus:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Eine 24-Stunden-Uhr wird verwendet. Alle Felder haben eine feste Breite. Das Zeichen für neue Zeile ('\n') und das Nullzeichen ('\0') nehmen die letzten beiden Stellen der Zeichenfolge ein.

Die konvertierte Zeichenfolge wird auch gemäß den lokalen Zeitzoneneinstellungen angepasst. Weitere Informationen zum Konfigurieren der Ortszeit und der [_tzset](tzset.md) -Funktion finden Sie unter [time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)und [localtime](localtime-localtime32-localtime64.md) -Funktionen. hier finden Sie ausführliche Informationen zum Definieren der Zeit Zonen Umgebung und der globalen Variablen.

Ein Aufruf von **ctime** ändert den einzelnen statisch zugewiesenen Puffer, der von den **gmtime** -und **localtime** -Funktionen verwendet wird. Jeder Aufruf dieser Routinen zerstört das Ergebnis des vorherigen Aufrufs. **ctime** gibt einen statischen Puffer mit der **Asctime** -Funktion frei. Folglich zerstört ein Aufruf von **ctime** die Ergebnisse aller vorherigen Aufrufe von **Asctime**, **localtime**oder **gmtime**.

**_wctime** und **_wctime64** sind die breit Zeichen Version von **ctime** und **_ctime64**. Zurückgeben eines Zeigers auf eine breit Zeichen-Zeichenfolge. Andernfalls Verhalten sich **_ctime64**, **_wctime**und **_wctime64** identisch mit **ctime**.

Diese Funktionen überprüfen ihre Parameter. Wenn *sourcetime* ein NULL-Zeiger ist oder der *sourcetime* -Wert negativ ist, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben die Funktionen **null** zurück und legen **errno** auf **EINVAL**fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**CTime**|**CTime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**CTime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<time.h> oder \<wchar.h>|
|**_wctime32**|\<time.h> oder \<wchar.h>|
|**_wctime64**|\<time.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_ctime64.c
// compile with: /W3
/* This program gets the current
* time in _time64_t form, then uses ctime to
* display the time in string form.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   __time64_t ltime;

   _time64( &ltime );
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996
   // Note: _ctime64 is deprecated; consider using _ctime64_s
}
```

```Output
The time is Wed Feb 13 16:04:43 2002
```

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
