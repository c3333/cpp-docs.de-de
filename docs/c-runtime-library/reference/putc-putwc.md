---
title: putc, putwc
ms.date: 4/2/2020
api_name:
- putwc
- putc
- _o_putc
- _o_putwc
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
- _puttc
- putwc
- putc
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
ms.openlocfilehash: 8809595c90c48976d9f28ffa659714f5b9d919c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338459"
---
# <a name="putc-putwc"></a>putc, putwc

Schreibt ein Zeichen in einen Stream.

## <a name="syntax"></a>Syntax

```C
int putc(
   int c,
   FILE *stream
);
wint_t putwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu schreibende Zeichen.

*Stream*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

Gibt das geschriebene Zeichen zurück. Um einen Fehler oder eine Dateiendbedingung anzuzeigen, geben **putc** und **putchar** **EOF**zurück; **putwc** und **putwchar** return **WEOF**. Verwenden Sie bei allen vier Routinen [ferror](ferror.md) oder [feof](feof.md), um auf einen Fehler oder ein Dateiende zu prüfen. Wenn ein Nullzeiger für *stream*übergeben wird, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen **EOF** oder **WEOF** zurück und setzen **errno** auf **EINVAL**.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **putc-Routine** schreibt das einzelne Zeichen *c* an der aktuellen Position in den *Ausgabestrom.* Jede ganze Zahl kann an **putc**übergeben werden, aber nur die unteren 8 Bits werden geschrieben. Die **putchar-Routine** `putc( c, stdout )`ist identisch mit . Wenn ein Lesefehler auftritt, wird für jede Routine die Fehleranzeige für den Stream festgelegt. **putc** und **putchar** ähneln **fputc** und **_fputchar**, werden aber sowohl als Funktionen als auch als Makros implementiert (siehe [Auswählen zwischen Funktionen und Makros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** und **putwchar** sind breitstellige Versionen von **putc** bzw. **putchar.** **putwc** und **putc** verhalten sich identisch, wenn der Stream im ANSI-Modus geöffnet wird. **putc** unterstützt derzeit keine Ausgabe in einem UNICODE-Stream.

Die Versionen mit dem Suffix **_nolock** sind identisch, allerdings sind sie nicht vor Störungen durch andere Threads geschützt. Weitere Informationen finden Sie unter **_putc_nolock, _putwc_nolock**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h> oder \<wchar.h>|

Die Konsole wird in UWP-Apps (Universelle Windows-Plattform) nicht unterstützt. Die Standard-Stream-Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor C-Laufzeitfunktionen sie in UWP-Apps verwenden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_putc.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putc( *p, stream );
}
```

### <a name="output"></a>Output

```Output
This is the line of output
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
