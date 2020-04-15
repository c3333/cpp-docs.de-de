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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 6056ad8bac6561c0ce2902928364996b2be9ae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348250"
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

*sourceTime*<br/>
Zeiger auf die zu konvertierende Zeit.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Zeichenfolgenergebnis **NULL** wird zurückgegeben, wenn:

- *sourceTime* stellt ein Datum vor Mitternacht, 1. Januar 1970, UTC.

- Wenn Sie **_ctime32** oder **_wctime32** verwenden, stellt *sourceTime* ein Datum nach 23:59:59 Januar 18, 2038, UTC dar.

- Wenn Sie **_ctime64** oder **_wctime64** verwenden, stellt *sourceTime* ein Datum nach 23:59:59, 31. Dezember 3000, UTC dar.

**ctime** ist eine Inline-Funktion, die **_ctime64** auswertet und **time_t** **__time64_t**entspricht. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit-time_t zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. **time_t** Dadurch wird **ctime** zu **_ctime32**ausgewertet. Dies ist nicht zu empfehlen, weil Ihre Anwendung nach dem 18. Januar 2038 fehlschlagen kann. Die Verwendung dieses Makros ist auf 64-Bit-Plattformen nicht zulässig.

## <a name="remarks"></a>Bemerkungen

Die **ctime-Funktion** konvertiert einen als [time_t-Wert](../../c-runtime-library/standard-types.md) gespeicherten Zeitwert in eine Zeichenfolge. Der *sourceTime-Wert* wird in der Regel von einem Aufruf zur [Zeit](time-time32-time64.md)abgerufen, der die Anzahl der seit Mitternacht (00:00:00), dem 1. Januar 1970, koordinierten Universalzeit (UTC) verstrichenen Sekunden zurückgibt. Der Rückgabewert der Zeichenfolge enthält genau 26 Zeichen und sieht so aus:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Eine 24-Stunden-Uhr wird verwendet. Alle Felder haben eine feste Breite. Das Zeichen für neue Zeile ('\n') und das Nullzeichen ('\0') nehmen die letzten beiden Stellen der Zeichenfolge ein.

Die konvertierte Zeichenfolge wird auch gemäß den lokalen Zeitzoneneinstellungen angepasst. Informationen zum Konfigurieren der Ortszeit und der [funktion _tzset](tzset.md) finden Sie in den [Funktionen Zeit](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)und [Ortszeit](localtime-localtime32-localtime64.md) für Details zum Definieren der Zeitzonenumgebung und globaler Variablen.

Ein Aufruf von **ctime** ändert den einzelnen statisch zugewiesenen Puffer, der von den **funktionen gmtime** und **localtime** verwendet wird. Jeder Aufruf dieser Routinen zerstört das Ergebnis des vorherigen Aufrufs. **ctime** teilt einen statischen Puffer mit der **asctime-Funktion.** Daher zerstört ein Aufruf von **ctime** die Ergebnisse eines vorherigen Aufrufs von **asctime**, **localtime**oder **gmtime**.

**_wctime** und **_wctime64** sind die breitstellige Version von **ctime** und **_ctime64;** Zurückgeben eines Zeigers auf eine Zeichenfolge mit breitem Zeichen. Andernfalls verhalten **sich _ctime64**, **_wctime**und **_wctime64** identisch mit **ctime**.

Diese Funktionen überprüfen ihre Parameter. Wenn *sourceTime* ein Nullzeiger ist oder der *sourceTime-Wert* negativ ist, rufen diese Funktionen den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben die Funktionen **NULL** zurück und setzen **errno** auf **EINVAL**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**Ctime**|**Ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**Ctime**|\<time.h>|
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

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
