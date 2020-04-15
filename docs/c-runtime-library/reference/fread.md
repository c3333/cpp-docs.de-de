---
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 26ffd56072f1a5fddc3131a42cd47c145e437b60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346063"
---
# <a name="fread"></a>fread

Liest Daten aus einem Stream

## <a name="syntax"></a>Syntax

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*Puffer*<br/>
Speicherort für Daten.

*Größe*<br/>
Elementgröße in Bytes.

*count*<br/>
Maximale Anzahl der zu lesenden Elemente.

*Stream*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

**fread** gibt die Anzahl der tatsächlich gelesenen vollständigen Elemente zurück, die möglicherweise kleiner als *die Anzahl* sind, wenn ein Fehler auftritt oder wenn das Ende der Datei vor erreichen der *Anzahl*gefunden wird. Verwenden Sie die **feof-** oder **ferror-Funktion,** um einen Lesefehler von einer End-of-File-Bedingung zu unterscheiden. Wenn *Größe* oder *Anzahl* 0 ist, gibt **fread** 0 zurück, und der Pufferinhalt bleibt unverändert. Wenn *Stream* oder *Puffer* ein Nullzeiger ist, ruft **fread** den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt 0 zurück.

Weitere Informationen zu diesen Fehlercodes finden Sie [ \_unter doserrno, \_errno,\_sys errlist und \_sys\_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Bemerkungen

Die **Fread-Funktion** liest bis zu, um Elemente der *Größe* Bytes aus dem *Eingabestream* zu *zählen,* und speichert sie im *Puffer*. Der Dateizeiger, der dem *Stream* zugeordnet ist (falls vorhanden), wird um die Anzahl der tatsächlich gelesenen Bytes erhöht. Wenn der angegebene Stream im [Textmodus](../../c-runtime-library/text-and-binary-mode-file-i-o.md)geöffnet wird, werden Neuezeilen im Windows-Stil in Zeilenlinien im Unix-Stil konvertiert. Das heißt, CRLF-Paare (Carriage Return-line Feed) werden durch LF-Zeichen (Single Line Feed) ersetzt. Dieser Vorgang hat keine Auswirkung auf den Dateizeiger oder den Rückgabewert. Die Position des Dateizeigers ist unbestimmt, wenn ein Fehler auftritt. Der Wert eines teilweise gelesenen Elements kann nicht bestimmt werden.

Wenn die angeforderte Datenmenge (d. h. *die Größenanzahl* \* *count*) größer oder gleich der internen **FILE-Puffergröße** \* ist (standardmäßig 4096 Byte, konfigurierbar mit [setvbuf](../../c-runtime-library/reference/setvbuf.md)), werden Streamdaten direkt in den vom Benutzer bereitgestellten Puffer kopiert, und die Zeilenumkehr erfolgt in diesem Puffer. Da die konvertierten Daten kürzer sein können als die *buffer*in den Puffer kopierten Streamdaten, können Daten, die\[*return_value* \* *Größe*einfügen, (wobei *return_value* der Rückgabewert von **fread**ist) nicht konvertierte Daten aus der Datei enthalten. Aus diesem Grund empfehlen wir Ihnen, Zeichendaten im *Puffer*\[*return_value* \* *Größe*] null zu beenden, wenn die Absicht des Puffers darin besteht, als Zeichenfolge im C-Stil zu fungieren. Weitere Informationen zu den Auswirkungen des Textmodus und des Binärmodus finden Sie unter [fopen.](fopen-wfopen.md)

Diese Funktion sperrt alle anderen Threads. Wenn Sie eine nicht sperrende Version benötigen, verwenden Sie **_fread_nolock**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[Text und Binärdatei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
