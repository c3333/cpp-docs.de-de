---
title: _strtime_s, _wstrtime_s
ms.date: 4/2/2020
api_name:
- _wstrtime_s
- _strtime_s
- _o__strtime_s
- _o__wstrtime_s
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
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
ms.openlocfilehash: 771dfdb6bd8035fe8683d62d52b3b4980ecda215
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316936"
---
# <a name="_strtime_s-_wstrtime_s"></a>_strtime_s, _wstrtime_s

Kopieren der aktuellen Zeit in einen Puffer. Dies sind Versionen von [_strtime, _wstrtime](strtime-wstrtime.md) mit Sicherheitsverbesserungen wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _strtime_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrtime_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strtime_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrtime_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parameter

*Puffer*<br/>
Ein mindestens 10 Bytes langer Puffer, in den die Zeit geschrieben wird.

*Sizeinbytes*<br/>
Die Größe des Puffers.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich.

Wenn ein Fehler auftritt, wird der Handler für ungültige Parameter aufgerufen, wie unter [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Der Rückgabewert ist ein Fehlercode, wenn ein Fehler auftritt. Fehlercodes sind in ERRNO.H definiert. Die genauen Fehler, die von der Funktion generiert werden, finden Sie in der folgenden Tabelle. Weitere Informationen über Fehlercodes finden Sie unter [errno-Konstanten](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*Puffer*|*Sizeinbytes*|Rückgabewert|Inhalt des *Puffers*|
|--------------|------------------------|------------|--------------------------|
|**Null**|(alle)|**Einval**|Nicht geändert|
|Nicht **NULL** (zeigt auf gültigen Puffer)|0|**Einval**|Nicht geändert|
|Nicht **NULL** (zeigt auf gültigen Puffer)|0 < Größe < 9|**Einval**|leere Zeichenfolge|
|Nicht **NULL** (zeigt auf gültigen Puffer)|Größe > 9|0|Aktuelle Zeit, wie sie in den Hinweisen angegeben wurde|

## <a name="security-issues"></a>Sicherheitsprobleme

Das Übergeben eines ungültigen**Nicht-NULL-Werts** für den Puffer führt zu einer Zugriffsverletzung, wenn der Parameter *numberOfElements* größer als 9 ist.

Das Übergeben eines Werts für *numberOfElements,* der größer als die tatsächliche Größe des Puffers ist, führt zu einem Pufferüberlauf.

## <a name="remarks"></a>Bemerkungen

Diese Funktionen bieten sicherere Versionen von [_strtime](strtime-wstrtime.md) und [_wstrtime](strtime-wstrtime.md). Die **_strtime_s-Funktion** kopiert die aktuelle Ortszeit in den Puffer, auf den die *Timestr*zeigt. Die Zeit wird als **hh:mm:ss** formatiert, wobei **hh** zwei Ziffern ist, die die Stunde in 24-Stunden-Notation darstellen, **mm** ist zweistellig, die Minuten nach der Stunde und **ss** zweistellig, was Sekunden darstellt. Beispielsweise stellt die Zeichenfolge **18:23:44** 23 Minuten und 44 Sekunden nach 18 Uhr dar. Der Puffer muss mindestens 9 Bytes lang sein. Die tatsächliche Größe wird durch den zweiten Parameter angegeben.

**_wstrtime** ist eine breit **gefächerte**Version von _strtime ; Das Argument und der Rückgabewert von **_wstrtime** sind Zeichenfolgen mit großen Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugbibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Zuordnung generischer Textroutinen:

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_strtime_s**|\<time.h>|
|**_wstrtime_s**|\<time.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// strtime_s.c

#include <time.h>
#include <stdio.h>

int main()
{
    char tmpbuf[9];
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    err = _strtime_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
      exit(1);
    }
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    err = _strdate_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
       exit(1);
    }
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

}
```

```Output
OS time:            14:37:49
OS date:            04/25/03
```

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
