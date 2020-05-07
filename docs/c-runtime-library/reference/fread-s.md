---
title: fread_s
ms.date: 4/2/2020
api_name:
- fread_s
- _o_fread_s
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
- fread_s
- stdio/fread_s
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
ms.openlocfilehash: 340d8188deb34166b1bea58cfc4fe7985cdc5e05
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919461"
---
# <a name="fread_s"></a>fread_s

Liest Daten aus einem Stream Diese Version von [fread](fread.md) enthält Sicherheitserweiterungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
size_t fread_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Speicherort für Daten.

*bufferSize*<br/>
Größe des Zielpuffers in Byte.

*für Element Size*<br/>
Größe des zu lesenden Elements in Byte.

*count*<br/>
Maximale Anzahl der zu lesenden Elemente.

*Streich*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

**fread_s** gibt die Anzahl der (gesamten) Elemente zurück, die in den Puffer gelesen wurden. Dies kann kleiner *als die Anzahl sein* , wenn ein Lesefehler oder das Ende der Datei gefunden wird, bevor die *Anzahl* erreicht wird. Verwenden Sie die Funktion " **feof** " oder " **ferror** ", um einen Fehler von einer dateiendebedingung zu unterscheiden. Wenn " *size* " oder " *count* " 0 ist, gibt **fread_s** 0 zurück, und der Pufferinhalt bleibt unverändert. Wenn *Stream* oder *buffer* ein NULL-Zeiger ist, ruft **fread_s** den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion **errno** auf **EINVAL** fest und gibt 0 zurück.

Weitere Informationen zu diesen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **fread_s** -Funktion liest zum *zählen* von Elementen aus *ElementSize* -Bytes aus dem Eingabestream und speichert Sie im *Puffer*. *stream*  Der Dateizeiger, der dem *Stream* zugeordnet ist (falls vorhanden), wird um die Anzahl der tatsächlich gelesenen Bytes erweitert. Wenn der angegebene Stream im Textmodus geöffnet wird, werden Wagen Rücklauf-und Zeilenvorschub Paare durch Einzel-Zeilenvorschub Zeichen ersetzt. Dieser Vorgang hat keine Auswirkung auf den Dateizeiger oder den Rückgabewert. Die Position des Dateizeigers ist unbestimmt, wenn ein Fehler auftritt. Der Wert eines teilweise gelesenen Elements kann nicht bestimmt werden.

Diese Funktion sperrt alle anderen Threads. Wenn Sie eine nicht sperrende Version benötigen, verwenden Sie **_fread_nolock**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fread_s**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```cpp
// crt_fread_s.c
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c
//
// This program opens a file that's named FREAD.OUT and
// writes characters to the file. It then tries to open
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

#define BUFFERSIZE 30
#define DATASIZE 22
#define ELEMENTCOUNT 2
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)
#define FILENAME "FREAD.OUT"

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   for ( i = 0; i < DATASIZE; i++ )
      list[i] = (char)('z' - i);
   list[DATASIZE] = '\0'; // terminal null so we can print it

   // Open file in text mode:
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )
   {
      // Write DATASIZE characters to stream
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );
      printf( "Wrote %d items\n\n", numwritten );
      fclose( stream );
   } else {
      printf( "Problem opening the file\n" );
      return -1;
   }

   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {
      // Attempt to read in characters in 2 blocks of 11
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );
      printf( "Contents of buffer after write/read:\n\t%s\n", list );
      fclose( stream );
   } else {
      printf( "File could not be opened\n" );
      return -1;
   }
}
```

```Output
Contents of buffer before write/read:
        zyxwvutsrqponmlkjihgfe

Wrote 22 items

Number of 11-byte elements read = 2

Contents of buffer after write/read:
        zyxwvutsrqponmlkjihgfe
```

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
