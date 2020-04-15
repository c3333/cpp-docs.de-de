---
title: _strtime, _wstrtime
ms.date: 4/2/2020
api_name:
- _wstrtime
- _strtime
- _o__strtime
- _o__wstrtime
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
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
ms.openlocfilehash: 827e5a579d801c12b932440fcbbaa18343ad7ece
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316881"
---
# <a name="_strtime-_wstrtime"></a>_strtime, _wstrtime

Kopieren der Zeit in einen Puffer. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_strtime_s, _wstrtime_s](strtime-s-wstrtime-s.md).

## <a name="syntax"></a>Syntax

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>Parameter

*timestr*<br/>
Zeitzeichenfolge

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die resultierende Zeichenfolge *timestr*zurück.

## <a name="remarks"></a>Bemerkungen

Die **_strtime-Funktion** kopiert die aktuelle Ortszeit in den Puffer, auf den die *Timestr*zeigt. Die Zeit wird als **hh:mm:ss** formatiert, wobei **hh** zwei Ziffern ist, die die Stunde in 24-Stunden-Notation darstellen, **mm** ist zweistellig, die Minuten nach der Stunde und **ss** zweistellig, was Sekunden darstellt. Beispielsweise stellt die Zeichenfolge **18:23:44** 23 Minuten und 44 Sekunden nach 18 Uhr dar. Der Puffer muss mindestens 9 Bytes lang sein.

**_wstrtime** ist eine breit **gefächerte**Version von _strtime ; Das Argument und der Rückgabewert von **_wstrtime** sind Zeichenfolgen mit großen Zeichen. Anderenfalls verhalten sich diese Funktionen identisch. Wenn *timestr* ein **NULL-Zeiger** ist oder *timestr* falsch formatiert ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausnahme fortgesetzt werden darf, geben diese Funktionen einen **NULL** zurück und setzen **errno** auf **EINVAL,** wenn *timestr* ein **NULL** war, oder setzen **errno** auf **ERANGE,** wenn *timestr* falsch formatiert ist.

In C++ haben diese Funktionen Vorlagenüberladungen, mit denen die neueren, sicheren Entsprechungen dieser Funktionen aufgerufen werden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<time.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
```

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
