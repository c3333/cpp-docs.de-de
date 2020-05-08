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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ec5af25070e253f6c04d1aab13404306251ed716
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912697"
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

*ert*<br/>
Speicherort für Daten.

*size*<br/>
Elementgröße in Bytes.

*count*<br/>
Maximale Anzahl der zu lesenden Elemente.

*Streich*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

**fread** gibt die Anzahl der tatsächlich gelesenen vollständigen Elemente zurück. diese kann *kleiner als die Anzahl sein* , wenn ein Fehler auftritt oder das Ende der Datei vor dem Erreichen der *Anzahl*erreicht wird. Verwenden Sie die Funktion " **feof** " oder " **ferror** ", um einen Lesefehler von einer dateiendebedingung zu unterscheiden. Wenn " *size* " oder " *count* " den Wert 0 hat, gibt **fread** 0 zurück, und der Pufferinhalt bleibt unverändert Wenn *Stream* oder *buffer* ein NULL-Zeiger ist, ruft **fread** den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion **errno** auf **EINVAL** fest und gibt 0 zurück.

Weitere Informationen zu diesen Fehlercodes finden [ \_Sie unter \_"\_doserrno \_"\_, "errno", "sys errlist" und "sys NERR](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ".

## <a name="remarks"></a>Hinweise

Die **fread** -Funktion liest zum *zählen* von Elementen der *Größe* von Bytes aus dem Eingabestream und speichert Sie im *Puffer*. *stream* Der dem *Stream* zugeordnete Dateizeiger (sofern vorhanden) wird um die Anzahl der tatsächlich gelesenen Bytes erweitert. Wenn der angegebene Stream im [Textmodus](../../c-runtime-library/text-and-binary-mode-file-i-o.md)geöffnet ist, werden Zeilenumbrüche im Windows-Stil in eine neue Zeile im UNIX-Format konvertiert. Das heißt, dass Wagen Rücklauf-Zeilenvorschub-Paare (CRLF-Paare) durch Einzel Zeilenvorschub Zeichen (LF) ersetzt werden. Dieser Vorgang hat keine Auswirkung auf den Dateizeiger oder den Rückgabewert. Die Position des Dateizeigers ist unbestimmt, wenn ein Fehler auftritt. Der Wert eines teilweise gelesenen Elements kann nicht bestimmt werden.

Wenn die Menge der angeforderten Daten (d. h. die *Größe der Größe* \* *) größer*als die oder gleich der Größe des internen **Datei** \* Puffers ist (standardmäßig 4096 Bytes, mithilfe von [setvbuf](../../c-runtime-library/reference/setvbuf.md)konfigurierbar), werden Streamdaten direkt in den vom Benutzer bereitgestellten Puffer kopiert, und in diesem Puffer wird die zeilenweise Konvertierung durchgeführt. Da die konvertierten Daten möglicherweise kürzer sind, als die in den Puffer kopierten Daten in den Puffer kopiert werden, können Daten über *Puffer*\[*return_value* \* *Größe*] (wobei *return_value* der Rückgabewert von **fread**ist) möglicherweise nicht konvertierte Daten aus der Datei enthalten. Aus diesem Grund wird empfohlen, Zeichendaten bei *Puffer*\[*return_value* \* *Größe*] mit NULL zu beenden, wenn die Absicht des Puffers als Zeichenfolge im C-Stil fungieren soll. Weitere Informationen zu den Auswirkungen des Textmodus und des binären Modus finden Sie unter " [f](fopen-wfopen.md) ".

Diese Funktion sperrt alle anderen Threads. Wenn Sie eine nicht sperrende Version benötigen, verwenden Sie **_fread_nolock**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[Text-und Binärdatei-e/a](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
