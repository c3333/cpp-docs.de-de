---
title: getenv_s, _wgetenv_s
description: Beschreibt die Microsoft C-Lauf getenv_s Zeit _wgetenv_s Bibliothek und-Funktionen.
ms.date: 4/2/2020
api_name:
- getenv_s
- _wgetenv_s
- _o__wgetenv_s
- _o_getenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getenv_s
- _tgetenv_s
- _wgetenv_s
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
no-loc:
- getenv_s
- _wgetenv_s
- _putenv_s
- main
- wmain
- errno
- EINVAL
- ERANGE
- _environ
- _wenviron
- _putenv
- _wputenv
- _tgetenv_s
- _tzset
- _dupenv_s
- _wdupenv_s
ms.openlocfilehash: 0713ed5735916c31edaab1a178a5e9b1b7cf5377
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913682"
---
# <a name="getenv_s-_wgetenv_s"></a>getenv_s, _wgetenv_s

Ruft einen Wert aus der aktuellen Umgebung ab. Diese Versionen von [getenv, _wgetenv](getenv-wgetenv.md) enthalten Sicherheitserweiterungen, wie unter [Sicherheitserweiterungen im CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t getenv_s(
   size_t *pReturnValue,
   char* buffer,
   size_t numberOfElements,
   const char *varname
);
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *varname
);
template <size_t size>
errno_t getenv_s(
   size_t *pReturnValue,
   char (&buffer)[size],
   const char *varname
); // C++ only
template <size_t size>
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t (&buffer)[size],
   const wchar_t *varname
); // C++ only
```

### <a name="parameters"></a>Parameter

*pReturnValue*<br/>
Die erforderliche Größe des Puffers, oder 0, wenn die Variable nicht gefunden wird.

*ert*<br/>
Puffer zum Speichern des Werts der Umgebungsvariablen.

*numberOfElements*<br/>
Größe des *Puffers*.

*varname*<br/>
Umgebungsvariablenname.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, andernfalls ein Fehlercode, wenn ein Fehler auftritt.

### <a name="error-conditions"></a>Fehlerbedingungen

|*pReturnValue*|*ert*|*numberOfElements*|*varname*|Rückgabewert|
|--------------------|--------------|------------------------|---------------|------------------|
|**Normal**|any|any|any|**Eingabe**|
|any|**Normal**|>0|any|**Eingabe**|
|any|any|any|**Normal**|**Eingabe**|

Bei diesen Fehlerbedingungen wird ein Handler für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen die Funktionen " **errno** " auf " **EINVAL** " fest und geben " **EINVAL**" zurück.

Wenn der Puffer zu klein ist, geben diese Funktionen auch **ERANGE**zurück. Sie rufen keinen Handler für ungültige Parameter auf. Sie schreiben die erforderliche Puffergröße in *pReturnValue*und ermöglichen es Programmen, die Funktion erneut mit einem größeren Puffer aufzurufen.

## <a name="remarks"></a>Hinweise

Die **getenv_s** -Funktion durchsucht die Liste der Umgebungsvariablen nach *varname*. beim Windows-Betriebssystem wird **getenv_s** die Groß-/Kleinschreibung nicht beachtet. **getenv_s** und [_putenv_s](putenv-s-wputenv-s.md) verwenden Sie die Kopie der Umgebung, auf die die globale **_environ** Variable verweist, um auf die Umgebung zuzugreifen. **getenv_s** funktioniert nur für die Datenstrukturen, auf die die Lauf Zeit Bibliothek zugreifen kann, und nicht für das Umgebungs Segment, das vom Betriebssystem für den Prozess erstellt wird. Programme, die das Argument " *TVP* " für [Main](../../cpp/main-function-command-line-args.md) oder [wmain](../../cpp/main-function-command-line-args.md) verwenden, rufen daher möglicherweise ungültige Informationen ab.

**_wgetenv_s** ist eine breit Zeichen Version von **getenv_s**. Das Argument und der Rückgabewert von **_wgetenv_s** sind Zeichen folgen mit breit Zeichen. Die **_wenviron** globale Variable ist eine breit Zeichen Version von **_environ**.

In einem MBCS-Programm (z. b. in einem SBCS-ASCII-Programm) ist **_wenviron** anfänglich **null** , da die Umgebung aus Multibyte-Zeichen folgen besteht. Wenn bereits eine (MBCS)-Umgebung vorhanden ist, wird beim ersten [_wputenv](putenv-wputenv.md)oder beim ersten **_wgetenv_s**eine entsprechende breit Zeichen-Zeichen folgen Umgebung erstellt, auf die dann von **_wenviron**verwiesen wird.

Ähnlich in einem Unicode-Programm (**_wmain**) ist **_environ** anfänglich **null** , da die Umgebung aus Zeichen folgen mit breit Zeichen besteht. Wenn bereits eine (Unicode)-Umgebung vorhanden ist, wird beim ersten [_putenv](putenv-wputenv.md)oder beim ersten **getenv_s** eine entsprechende MBCS-Umgebung erstellt, auf die dann von **_environ**verwiesen wird.

Wenn in einem Programm zwei Kopien der Umgebung (MBCS und Unicode) gleichzeitig vorhanden sind, muss das Laufzeitsystem beide Kopien verwalten, wodurch sich die Ausführungszeit verlangsamt. Wenn Sie z. b. **_putenv**aufzurufen, wird auch automatisch ein **_wputenv** ausgeführt, sodass die beiden Umgebungs Zeichenfolgen übereinstimmen.

> [!CAUTION]
> In seltenen Fällen, wenn das Laufzeitsystem sowohl eine Unicodeversion als auch eine Multibyteversion der Umgebung verwaltet, stimmen diese zwei Versionen möglicherweise nicht exakt überein. Dies liegt daran, dass die Zuordnung von einer eindeutigen Unicodezeichenfolge zu einer Multibyte-Zeichenfolge nicht unbedingt eindeutig ist, obwohl sich jede eindeutige Multibyte-Zeichenfolge einer eindeutigen Unicodezeichenfolge zuordnen lässt. Weitere Informationen finden Sie unter [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Die **_putenv_s** -und **_getenv_s** Familien von Funktionen sind nicht Thread sicher. **_getenv_s** könnte einen Zeichen folgen Zeiger zurückgeben, während **_putenv_s** die Zeichenfolge ändert und somit zufällige Fehler verursacht. Stellen Sie sicher, dass Aufrufe dieser Funktionen synchronisiert sind.

Die Verwendung dieser Funktionen in C++ wird durch Vorlagenüberladungen vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Um den Wert der **TZ** -Umgebungsvariablen zu überprüfen oder zu ändern, verwenden Sie je nach Bedarf **getenv_s**, **_putenv**und **_tzset**. Weitere Informationen zu **TZ**finden Sie unter [_tzset](tzset.md) und [_daylight, _dstbias, _timezone und _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_getenv_s.c
// This program uses getenv_s to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* libvar;
   size_t requiredSize;

   getenv_s( &requiredSize, NULL, 0, "LIB");
   if (requiredSize == 0)
   {
      printf("LIB doesn't exist!\n");
      exit(1);
   }

   libvar = (char*) malloc(requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects
   // the environment variable of the current process. The command
   // processor's environment is not changed.
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );

   getenv_s( &requiredSize, NULL, 0, "LIB");

   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the new value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "New LIB variable is: %s\n", libvar );

   free(libvar);
}
```

```Output
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[Umgebungs Konstanten](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
