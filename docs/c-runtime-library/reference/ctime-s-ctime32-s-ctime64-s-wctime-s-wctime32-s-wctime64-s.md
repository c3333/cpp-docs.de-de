---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 4/2/2020
api_name:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
- _o__ctime32_s
- _o__ctime64_s
- _o__wctime32_s
- _o__wctime64_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
ms.openlocfilehash: ca7636f7054b6c7e228b57e0e776250f1b4ccb32
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914822"
---
# <a name="ctime_s-_ctime32_s-_ctime64_s-_wctime_s-_wctime32_s-_wctime64_s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Konvertieren Sie einen Zeitwert in eine Zeichenfolge, und passen Sie sie an die Zeitzoneneinstellungen an. Dies sind Versionen von [ctime, _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) mit Sicherheitserweiterungen, wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Muss groß genug für 26 Zeichen sein. Ein Zeiger auf das Ergebnis der Zeichenfolge oder **null** , wenn:

- *sourcetime* stellt ein Datum vor Mitternacht (1. Januar 1970 UTC) dar.

- Wenn Sie **_ctime32_s** oder **_wctime32_s** verwenden und *sourcetime* ein Datum 23:59:59 nach dem 18. Januar 2038 UTC (UTC) darstellt.

- Wenn Sie **_ctime64_s** oder **_wctime64_s** verwenden und *sourcetime* ein Datum nach 23:59:59, dem 31. Dezember 3000, UTC darstellt.

- Wenn Sie **_ctime_s** oder **_wctime_s**verwenden, sind diese Funktionen Wrapper für die vorherigen Funktionen. Weitere Informationen finden Sie im Abschnitt mit den Hinweisen.

*numberOfElements*<br/>
Die Größe des Puffers.

*sourcetime*<br/>
Zeiger auf die gespeicherte Zeit

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich. Wenn ein Fehler aufgrund eines ungültigen Parameters auftritt, wird der Handler für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird ein Fehlercode zurückgegeben. Fehlercodes sind in „ERRNO.H“ definiert. Eine Liste dieser Fehler finden Sie unter [errno](../../c-runtime-library/errno-constants.md). Die jeweiligen Fehlercodes, die für jede Fehlerbedingung zurückgegeben werden, sind in folgender Tabelle aufgelistet.

## <a name="error-conditions"></a>Fehlerbedingungen

|*ert*|*numberOfElements*|*sourcetime*|Rückgabewert|Wert im *Puffer*|
|--------------|------------------------|------------|------------|-----------------------|
|**Normal**|any|any|**Eingabe**|Nicht geändert|
|Not **null** (zeigt auf gültigen Speicher)|0|any|**Eingabe**|Nicht geändert|
|Nicht **null**|0<Größe<26|any|**Eingabe**|leere Zeichenfolge|
|Nicht **null**|>= 26|NULL|**Eingabe**|leere Zeichenfolge|
|Nicht **null**|>= 26|< 0|**Eingabe**|leere Zeichenfolge|

## <a name="remarks"></a>Hinweise

Die **ctime_s** -Funktion konvertiert einen als [time_t](../../c-runtime-library/standard-types.md) Struktur gespeicherten Zeitwert in eine Zeichenfolge. Der *sourcetime* -Wert wird in der Regel von einem Aufruf an [time](time-time32-time64.md)abgerufen, der die Anzahl der Sekunden zurückgibt, die seit Mitternacht (00:00:00), dem 1. Januar 1970, der koordinierten Weltzeit (UTC) vergangen sind. Der Rückgabewert der Zeichenfolge enthält genau 26 Zeichen und sieht so aus:

`Wed Jan 02 02:03:55 1980\n\0`

Eine 24-Stunden-Uhr wird verwendet. Alle Felder haben eine feste Breite. Das Zeichen für neue Zeile ('\n') und das Nullzeichen ('\0') nehmen die letzten beiden Stellen der Zeichenfolge ein.

Die konvertierte Zeichenfolge wird auch gemäß den lokalen Zeitzoneneinstellungen angepasst. Weitere Informationen zum Konfigurieren der Ortszeit und der [_tzset](tzset.md) -Funktion finden Sie in den Funktionen [time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)und [localtime32_s](localtime-s-localtime32-s-localtime64-s.md) für Informationen zum Definieren der Zeit Zonen Umgebung und der globalen Variablen.

**_wctime32_s** und **_wctime64_s** sind die breit Zeichen Version von **_ctime32_s** und **_ctime64_s**. Zurückgeben eines Zeigers auf eine breit Zeichen-Zeichenfolge. Andernfalls Verhalten sich **_ctime64_s**, **_wctime32_s**und **_wctime64_s** identisch mit **_ctime32_s**.

**ctime_s** ist eine Inline Funktion, die **_ctime64_s** ergibt, und **time_t** entspricht **__time64_t**. Wenn Sie den Compiler zwingen müssen, **time_t** als den alten 32-Bit- **time_t**zu interpretieren, können Sie **_USE_32BIT_TIME_T**definieren. Dies führt dazu, dass **ctime_s** zu **_ctime32_s**ausgewertet wird. Dies ist nicht zu empfehlen, weil Ihre Anwendung nach dem 18. Januar 2038 fehlschlagen kann. Die Verwendung dieses Makros ist auf 64-Bit-Plattformen nicht zulässig.

Die Verwendung dieser Funktionen in C++ wird durch Überladungen (als Vorlagen vorhanden) vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debug-Bibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s** **_ctime64_s**|\<time.h>|
|**_wctime_s**, **_wctime32_s** **_wctime64_s**|\<time.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

#include <time.h>
#include <stdio.h>

#define SIZE 26

int main( void )
{
   time_t ltime;
   wchar_t buf[SIZE];
   errno_t err;

   time( &ltime );

   err = _wctime_s( buf, SIZE, &ltime );
   if (err != 0)
   {
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);
   }
   wprintf_s( L"The time is %s\n", buf );
}
```

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
