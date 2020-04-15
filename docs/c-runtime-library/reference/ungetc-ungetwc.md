---
title: ungetc, ungetwc
ms.date: 4/2/2020
api_name:
- ungetwc
- ungetc
- _o_ungetc
- _o_ungetwc
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: 484af7b72f860a8a9d12cf0b62444871caad4675
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361298"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Schiebt ein Zeichen zurück auf den Stream.

## <a name="syntax"></a>Syntax

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu verschiebendes Zeichen.

*Stream*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg gibt jede dieser Funktionen das Zeichenargument *c*zurück. Wenn *c* nicht zurückgedrückt werden kann oder kein Zeichen gelesen wurde, bleibt der Eingabestream unverändert und **ungetc** gibt **EOF**zurück; **ungetwc** gibt **WEOF**zurück. Wenn *Der Stream* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **EOF** oder **WEOF** zurückgegeben und **errno** auf **EINVAL**gesetzt.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **ungetc-Funktion** schiebt das Zeichen *c* zurück in den *Stream* und löscht den End-of-File-Indikator. Der Stream muss zum Lesen geöffnet sein. Ein nachfolgender Lesevorgang auf *stream* beginnt mit *c*. Ein Versuch, **EOF** mithilfe von **ungetc** auf den Stream zu übertragen, wird ignoriert.

Zeichen, die von **ungetc** auf dem Stream platziert werden, können gelöscht werden, wenn **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**oder [reswind](rewind.md) aufgerufen wird, bevor das Zeichen aus dem Stream gelesen wird. Der Dateipositionszeiger erhält den Wert, den er auch schon hatte, bevor die Zeichen zurückgeschoben wurden. Der dem Stream entsprechende externe Speicher ist unverändert. Bei einem erfolgreichen **ungetc-Aufruf** gegen einen Textstream wird die Dateipositionsanzeige nicht angegeben, bis alle zurückgedrückten Zeichen gelesen oder verworfen werden. Bei jedem erfolgreichen **ungetc-Aufruf** gegen einen binären Stream wird der Dateipositionsindikator dekrementiert; Wenn sein Wert vor einem Aufruf 0 war, ist der Wert nach dem Aufruf nicht definiert.

Die Ergebnisse sind unvorhersehbar, wenn **ungetc** zweimal ohne Lese- oder Dateipositionierungsvorgang zwischen den beiden Aufrufen aufgerufen wird. Nach einem Aufruf von **fscanf**kann ein Aufruf von **ungetc** fehlschlagen, es sei denn, ein anderer Lesevorgang (z. B. **getc**) wurde ausgeführt. Das liegt daran, dass **fscanf** selbst **ungetc**aufruft.

**ungetwc** ist eine Breitzeichenversion von **ungetc**. Bei jedem erfolgreichen **ungetwc-Aufruf** für einen Text- oder Binärstream wird der Wert des Dateipositionsindikators jedoch nicht angegeben, bis alle zurückgeschobenen Zeichen gelesen oder verworfen werden.

Diese Funktionen sind während der Ausführung threadsicher und sperrabhängige Daten. Eine nicht sperrende Version finden Sie unter [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> oder \<wchar.h>|

Die Konsole wird in UWP-Apps (Universelle Windows-Plattform) nicht unterstützt. Die Standard-Stream-Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor C-Laufzeitfunktionen sie in UWP-Apps verwenden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
