---
title: _fgetc_nolock, _fgetwc_nolock
ms.date: 4/2/2020
api_name:
- _fgetc_nolock
- _fgetwc_nolock
- _o__fgetc_nolock
- _o__fgetwc_nolock
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
- _fgetwc_nolock
- fgettc_nolock
- fgetwc_nolock
- _fgetc_nolock
- _fgettc_nolock
- fgetc_nolock
helpviewer_keywords:
- fgetc_nolock function
- fgetwc_nolock function
- _fgetwc_nolock function
- characters, reading
- _fgetc_nolock function
- streams, reading characters from
- fgettc_nolock function
- reading characters from streams
- _fgettc_nolock function
ms.assetid: fb8e7c5b-4503-493a-879e-6a1db75aa114
ms.openlocfilehash: 2744dc17c79fc1e3e568dd3b7a62602b75603be0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912771"
---
# <a name="_fgetc_nolock-_fgetwc_nolock"></a>_fgetc_nolock, _fgetwc_nolock

Liest ein Zeichen in einem Stream, ohne den Thread zu sperren.

## <a name="syntax"></a>Syntax

```C
int _fgetc_nolock(
   FILE *stream
);
wint_t _fgetwc_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*Streich*<br/>
Zeiger zur **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

Weitere Informationen finden Sie unter [fgetc, fgetwc](fgetc-fgetwc.md).

## <a name="remarks"></a>Hinweise

**_fgetc_nolock** und **_fgetwc_nolock** sind mit **fgetc** bzw. **fgetwc**identisch, mit dem Unterschied, dass Sie nicht vor Störungen durch andere Threads geschützt sind. Sie sind möglicherweise schneller, da kein Mehraufwand zur Sperrung anderer Threads erforderlich ist. Verwenden Sie diese Funktionen nur in threadsichere Kontexten wie z. B. in Singlethreadanwendungen oder in Fällen, in denen der aufrufende Bereich die Threadisolation bereits handhabt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fgettc_nolock**|**_fgetc_nolock**|**_fgetc_nolock**|**_fgetwc_nolock**|

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fgetc_nolock**|\<stdio.h>|
|**_fgetwc_nolock**|\<stdio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fgetc_nolock.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   if( fopen_s( &stream, "crt_fgetc_nolock.txt", "r" ) != 0 )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = _fgetc_nolock( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crt_fgetc_nolocktxt"></a>Eingabe: crt_fgetc_nolock.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
