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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e8f6021a0b770f6b435653c190d5968f9ac50a57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345757"
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

*Stream*<br/>
Zeiger auf die **FILE**-Struktur.

*offset*<br/>
Anzahl von Bytes von *origin*.

*Ursprung*<br/>
Ursprüngliche Position

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, **fseek** und **_fseeki64** gibt 0 zurück. Andernfalls gibt es einen Wert ungleich 0 (null) zurück. Auf Geräten, die Suchvorgänge nicht unterstützen, ist der Rückgabewert nicht definiert. Wenn *stream* ein Nullzeiger ist oder der *Ursprung* nicht einer der unten beschriebenen zulässigen Werte ist, rufen **fseek** und **_fseeki64** den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben -1 zurück.

## <a name="remarks"></a>Bemerkungen

Die **Funktionen fseek** und **_fseeki64** verschiebt den dem *Stream* zugeordneten Dateizeiger (falls vorhanden) an eine neue Position, die Bytes vom *Ursprung* *versetzt.* Der nächste Vorgang im Stream tritt am neuen Speicherort auf. Für einen updatebereiten Stream kann der nächste Vorgang ein Lese- oder Schreibvorgang sein. Der *Argumentursprung* muss eine der folgenden Konstanten sein, die in STDIO definiert sind. H:

|Ursprungswert|Bedeutung|
|-|-|
| **SEEK_CUR** | Aktuelle Position des Dateizeigers |
| **SEEK_END** | Ende der Datei |
| **SEEK_SET** | Anfang der Datei |

Sie können **fseek** und **_fseeki64** verwenden, um den Zeiger an einer beliebigen Stelle in einer Datei neu zu positionieren. Der Zeiger kann auch nach dem Ende der Datei positioniert werden. **fseek** und **_fseeki64** löscht den End-of-File-Indikator und negiert die Wirkung aller vorherigen [ungetc-Aufrufe](ungetc-ungetwc.md) gegen *Stream*.

Wenn eine Datei zum Anfügen von Daten geöffnet wird, wird die aktuelle Dateiposition vom letzten E/A-Vorgang nicht dadurch bestimmt, wo der nächste Schreibvorgang erfolgt. Wenn noch kein E/A-Vorgang für eine zum Anhängen geöffnete Datei stattgefunden hat, ist die Dateiposition der Anfang der Datei.

Für Streams, die im Textmodus geöffnet werden, haben **fseek** und **_fseeki64** nur eingeschränkten Nutzen, da Rücklauf-Feed-Übersetzungen **fseek** und **_fseeki64** zu unerwarteten Ergebnissen führen können. Die einzigen **fseek** und **_fseeki64** Operationen garantiert auf Streams im Textmodus geöffnet arbeiten sind:

- Suchen mit einem Offset von 0 hinsichtlich der ursprünglichen Werte

- Suchen vom Anfang der Datei mit einem Offsetwert, der von einem Aufruf an [ftell](ftell-ftelli64.md) zurückgegeben wird, wenn **fseek** oder [_ftelli64](ftell-ftelli64.md) verwendet wird, wenn **_fseeki64 verwendet**wird.

Im Textmodus wird STRG+Z als ein Dateiendezeichen in der Eingabe interpretiert. In Dateien, die zum Lesen/Schreiben geöffnet wurden, suchen [fopen](fopen-wfopen.md) und alle zugehörigen Routinen nach einem STRG+Z am Ende der Datei und entfernen es nach Möglichkeit. Dies geschieht, weil die Kombination aus **fseek** und [ftell](ftell-ftelli64.md) oder **_fseeki64** und [_ftelli64](ftell-ftelli64.md), innerhalb einer Datei zu verschieben, die mit einer STRG+Z endet, kann dazu führen, dass **fseek** oder **_fseeki64** sich am Ende der Datei falsch verhalten.

Wenn CRT eine Datei öffnet, die mit einer Bytereihenfolge-Marke (Byte Order Mark, BOM) beginnt, wird der Dateizeiger nach der BOM positioniert (d.h. am Anfang des tatsächlichen Dateiinhalts). Wenn Sie bis zum Anfang der Datei **suchen** müssen, verwenden Sie [ftell,](ftell-ftelli64.md) um die Ausgangsposition zu erhalten, und **suchen** Sie sie, anstatt position 0 zu positionieren.

Diese Funktion sperrt alle anderen Threads während der Ausführung und ist daher threadsicher. Eine nicht sperrende Version finden Sie unter [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[Zurückspulen](rewind.md)<br/>
