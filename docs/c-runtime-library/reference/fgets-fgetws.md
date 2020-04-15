---
title: fgets, fgetws
ms.date: 4/2/2020
api_name:
- fgets
- fgetws
- _o_fgets
- _o_fgetws
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
- _fgetts
- fgetws
- fgets
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
ms.openlocfilehash: a1120529157801aac5cf1c4fd61f844fde443bed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346864"
---
# <a name="fgets-fgetws"></a>fgets, fgetws

Ruft eine Zeichenfolge aus einem Stream ab

## <a name="syntax"></a>Syntax

```C
char *fgets(
   char *str,
   int numChars,
   FILE *stream
);
wchar_t *fgetws(
   wchar_t *str,
   int numChars,
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Speicherort für Daten.

*numChars*<br/>
Die maximale Anzahl der zu lesenden Zeichen

*Stream*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt *str*zurück. **NULL** wird zurückgegeben, um einen Fehler oder eine End-of-File-Bedingung anzuzeigen. Verwenden Sie **feof** oder **ferror,** um zu bestimmen, ob ein Fehler aufgetreten ist. Wenn *str* oder *stream* ein Nullzeiger ist oder *numChars* kleiner oder gleich Null ist, ruft diese Funktion den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt, und die Funktion gibt **NULL**zurück.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **fgets-Funktion** liest eine Zeichenfolge aus dem *Eingabestreamargument* und speichert sie in *str*. **fgets** liest Zeichen von der aktuellen Stream-Position zum ersten Zeilenumlauf-Zeichen und einschließlich des ersten Zeilenumlaufzeichens bis zum Ende des Streams, oder bis die Anzahl der gelesenen Zeichen gleich *numChars* - 1 ist, je nachdem, was zuerst eintritt. Das in *str* gespeicherte Ergebnis wird mit einem Nullzeichen angehängt. Das Zeilenumbruchzeichen wird, wenn es gelesen wird, in die Zeichenfolge aufgenommen.

**fgetws** ist eine Breitzeichenversion von **fgets**.

**fgetws** liest das Breitzeichenargument *str* als Multibyte-Zeichen-Zeichenfolge oder als Breitzeichenzeichenfolge, je nachdem, ob *der Stream* im Textmodus bzw. im Binärmodus geöffnet wird. Weitere Informationen zur Anwendung von Text- und Binärmodi in Unicode- und Multibyte-Stream-E/A finden Sie unter [Text- und Binärmodus-Datei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md) und [Unicode-Stream-E/A in Text- und Binärmodi](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fgets.c
// This program uses fgets to display
// the first line from a file.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[100];

   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )
   {
      if( fgets( line, 100, stream ) == NULL)
         printf( "fgets error\numChars" );
      else
         printf( "%s", line);
      fclose( stream );
   }
}
```

### <a name="input-crt_fgetstxt"></a>Eingabe: crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
