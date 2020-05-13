---
title: fseek, _fseeki64
ms.date: 4/2/2020
api_name:
- _fseeki64
- fseek
- _o__fseeki64
- _o_fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: c9bfc9a575504d890d0021937713c720c4557441
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910197"
---
# <a name="fseek-_fseeki64"></a>fseek, _fseeki64

Verschiebt den Dateizeiger in einen angegebenen Speicherort

## <a name="syntax"></a>Syntax

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parameter

*Streich*<br/>
Zeiger auf die **FILE**-Struktur.

*offset*<br/>
Anzahl von Bytes von *origin*.

*Entstehungs*<br/>
Ursprüngliche Position

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, gibt " **f Seek** " und " **_fseeki64** " 0 zurück. Andernfalls gibt es einen Wert ungleich 0 (null) zurück. Auf Geräten, die Suchvorgänge nicht unterstützen, ist der Rückgabewert nicht definiert. Wenn *der Stream* ein NULL-Zeiger ist oder der *Ursprung* keinen der unten beschriebenen zulässigen Werte ist, rufen Sie **fseek** und **_fseeki64** den Handler für ungültige Parameter auf, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL** fest und geben-1 zurück.

## <a name="remarks"></a>Hinweise

Die **fseek** -und **_fseeki64** -Funktion verschiebt den Dateizeiger (sofern vorhanden), der mit *Stream* verknüpft ist, an einen neuen Speicherort, der aus dem *Ursprung* *Offset* Bytes ist. Der nächste Vorgang im Stream tritt am neuen Speicherort auf. Für einen updatebereiten Stream kann der nächste Vorgang ein Lese- oder Schreibvorgang sein. Der Argument *Ursprung* muss eine der folgenden Konstanten sein, die in stdio definiert ist. Micha

|Ursprungs Wert|Bedeutung|
|-|-|
| **SEEK_CUR** | Aktuelle Position des Dateizeigers |
| **SEEK_END** | Ende der Datei |
| **SEEK_SET** | Anfang der Datei |

Sie können **fseek** und **_fseeki64** verwenden, um den Zeiger an einer beliebigen Stelle in einer Datei neu zu positionieren. Der Zeiger kann auch nach dem Ende der Datei positioniert werden. der dateiendeindikator **und der** **_fseeki64** löscht den Dateiende-Indikator und negiert die Auswirkungen aller vorherigen [ungetc](ungetc-ungetwc.md) -Aufrufe auf den *Stream*.

Wenn eine Datei zum Anfügen von Daten geöffnet wird, wird die aktuelle Dateiposition vom letzten E/A-Vorgang nicht dadurch bestimmt, wo der nächste Schreibvorgang erfolgt. Wenn noch kein E/A-Vorgang für eine zum Anhängen geöffnete Datei stattgefunden hat, ist die Dateiposition der Anfang der Datei.

Für Datenströme, die im Textmodus geöffnet wurden, sind **fseek** und **_fseeki64** eingeschränkt, da Wagen Rücklauf-Zeilenvorschub Übersetzungen bewirken können, dass **fseek** und **_fseeki64** unerwartete Ergebnisse erzeugen. Die einzigen **fseek** -und **_fseeki64** Vorgänge, die für im Textmodus geöffnete Streams garantiert werden, sind:

- Suchen mit einem Offset von 0 hinsichtlich der ursprünglichen Werte

- Suchen von dem Anfang der Datei mit einem Offset Wert, der von einem [ftell](ftell-ftelli64.md) -Befehl zurückgegeben wird, wenn **fseek** verwendet wird, oder [_ftelli64](ftell-ftelli64.md) , wenn **_fseeki64**verwendet wird.

Im Textmodus wird STRG+Z als ein Dateiendezeichen in der Eingabe interpretiert. In Dateien, die für Lese-/Schreibvorgänge geöffnet sind, überprüfen Sie, ob die Datei mit dem Namen STRG + Z am Ende der Datei ist [, und entfernen](fopen-wfopen.md) Sie Sie, wenn möglich. Dies geschieht, da die Kombination von **fseek** und [ftell](ftell-ftelli64.md) oder **_fseeki64** und [_ftelli64](ftell-ftelli64.md)die Verschiebung in einer Datei, die mit STRG + Z endet, dazu führen kann, dass sich **fseek** oder **_fseeki64** in der Nähe des Datei Endes nicht ordnungsgemäß verhält.

Wenn CRT eine Datei öffnet, die mit einer Bytereihenfolge-Marke (Byte Order Mark, BOM) beginnt, wird der Dateizeiger nach der BOM positioniert (d.h. am Anfang des tatsächlichen Dateiinhalts). Wenn Sie an den Anfang der Datei **Suchen** müssen, verwenden Sie [ftell](ftell-ftelli64.md) , um die Anfangsposition zu ermitteln, und **Suchen Sie danach** , anstatt die Position 0 zu positionieren.

Diese Funktion sperrt alle anderen Threads während der Ausführung und ist daher threadsicher. Eine nicht sperrende Version finden Sie unter [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[Rewind](rewind.md)<br/>
