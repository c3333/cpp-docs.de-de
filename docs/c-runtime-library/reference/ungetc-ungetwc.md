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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 406ce7d8befd1d9e9e6a065f2549bacf46d2fd6e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915981"
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

*scher*<br/>
Zu verschiebendes Zeichen.

*Streich*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg gibt jede dieser Funktionen das Zeichen Argument *c*zurück. Wenn *c* nicht zurückgeschoben werden kann oder wenn kein Zeichen gelesen wurde, bleibt der Eingabestream unverändert, und **ungetc** gibt **EOF**zurück. **ungetwc** gibt **WEOF**zurück. Wenn *stream* der Stream **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **EOF** oder **WEOF** zurückgegeben, und **errno** ist auf **EINVAL**festgelegt.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **ungetc** -Funktion schiebt das Zeichen *c* zurück auf den *Stream* und löscht den Dateiende-Indikator. Der Stream muss zum Lesen geöffnet sein. Ein nachfolgende Lesevorgang für den *Stream* beginnt mit " *c*". Der Versuch, **EOF** mithilfe von **ungetc** auf den Stream zu überführen, wird ignoriert.

Zeichen, die von **ungetc** im Stream abgelegt werden, können gelöscht werden, wenn **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**oder [Rewind](rewind.md) aufgerufen wird, bevor das Zeichen aus dem Stream gelesen wird. Der Dateipositionszeiger erhält den Wert, den er auch schon hatte, bevor die Zeichen zurückgeschoben wurden. Der dem Stream entsprechende externe Speicher ist unverändert. Bei einem erfolgreichen **ungetc** -Aufrufe für einen Textstream wird der Datei Positionsindikator so lange nicht angegeben, bis alle zurückgelegten Zeichen gelesen oder verworfen wurden. Bei jedem erfolgreichen **ungetc** -Befehl für einen binären Stream wird der Datei Positionsindikator dekrementiert. Wenn der Wert vor einem-Befehl 0 war, ist der Wert nach dem-aufrufundefiniert.

Die Ergebnisse sind unvorhersehbar, wenn **ungetc** zweimal ohne Lese-oder Datei Positionierungs Vorgang zwischen den beiden Aufrufen aufgerufen wird. Nach einem **fscanf-fscanf**kann ein **ungetc** -Aufrufe fehlschlagen, es sei denn, ein anderer Lesevorgang (z. **b. getc**) wurde ausgeführt. Der Grund hierfür ist **, dass der** Aufruf von " **ungetc**" von "f.

**ungetwc** ist eine breit Zeichen Version von **ungetc**. Bei jedem erfolgreichen **ungetwc** -Rückruf für einen Text-oder Binärstream wird der Wert des Datei Positions Indikators jedoch nicht angegeben, bis alle zurückgelegten Zeichen gelesen oder verworfen werden.

Diese Funktionen sind während der Ausführung threadsicher und sperrabhängige Daten. Eine nicht sperrende Version finden Sie unter [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> oder \<wchar.h>|

Die-Konsole wird in universelle Windows-Plattform-Apps (UWP) nicht unterstützt. Die Standarddaten Strom Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor Sie von C-Lauf Zeitfunktionen in UWP-Apps verwendet werden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
