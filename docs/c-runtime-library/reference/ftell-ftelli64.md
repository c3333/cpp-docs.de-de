---
title: ftell, _ftelli64
ms.date: 4/2/2020
api_name:
- _ftelli64
- ftell
- _o__ftelli64
- _o_ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: bfe79610161a7f4032517d9f7eaa0de50be18e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345615"
---
# <a name="ftell-_ftelli64"></a>ftell, _ftelli64

Ruft die aktuelle Position eines Dateizeigers ab

## <a name="syntax"></a>Syntax

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*Stream*<br/>
**ZielDATEIstruktur.**

## <a name="return-value"></a>Rückgabewert

**ftell** und **_ftelli64** geben die aktuelle Dateiposition zurück. Der von **ftell** und **_ftelli64** zurückgegebene Wert spiegelt möglicherweise nicht den physischen Byteversatz für Streams wider, die im Textmodus geöffnet werden, da der Textmodus zur Rücklaufübersetzung des Wagens führt. Verwenden Sie **ftell** mit [fseek](fseek-fseeki64.md) oder **_ftelli64** mit [_fseeki64,](fseek-fseeki64.md) um korrekt zu Dateispeicherorten zurückzukehren. Bei Fehler rufen **ftell** und **_ftelli64** den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen -1L zurück und setzen **errno** auf eine von zwei Konstanten, die in ERRNO definiert sind. H. Die **EBADF-Konstante** bedeutet, dass das *Streamargument* kein gültiger Dateizeigerwert ist oder nicht auf eine geöffnete Datei verweist. **EINVAL** bedeutet, dass ein ungültiges *Streamargument* an die Funktion übergeben wurde. Bei Geräten, die nicht gesucht werden können (z. B. Terminals und Drucker), oder wenn der *Stream* nicht auf eine geöffnete Datei verweist, ist der Rückgabewert nicht definiert.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **Funktionen ftell** und **_ftelli64** rufen die aktuelle Position des Dateizeigers (falls vorhanden) ab, der dem *Stream*zugeordnet ist. Die Position wird als ein Offset relativ zum Anfang des Streams ausgedrückt.

Beachten Sie, dass wenn eine Datei zum Anfügen von Daten geöffnet wird, die aktuelle Dateiposition vom letzten E/A-Vorgang nicht dadurch bestimmt wird, wo der nächste Schreibvorgang erfolgt. Wenn eine Datei für einen Anfügevorgang geöffnet wird und der letzte Vorgang ein Lesevorgang war, ist die Dateiposition der Punkt, an dem der nächste Lesevorgang gestartet wird, aber nicht der nächste Schreibvorgang. (Wenn eine Datei zum Anhängen geöffnet wird, wird die Dateiposition vor jedem Schreibvorgang an das Ende der Datei verschoben.) Wenn für eine zum Anhängen geöffnete Datei noch kein E/A-Vorgang aufgetreten ist, ist die Dateiposition der Anfang der Datei.

Im Textmodus wird STRG+Z in der Eingabe als Dateiendezeichen interpretiert. In Dateien, die zum Lesen/Schreiben geöffnet wurden, suchen **fopen** und alle zugehörigen Routinen nach einem STRG+Z am Ende der Datei und entfernen es nach Möglichkeit. Dies geschieht, weil die Kombination von **ftell** und [fseek](fseek-fseeki64.md) oder **_ftelli64** und [_fseeki64](fseek-fseeki64.md), um innerhalb einer Datei zu verschieben, die mit einem STRG+Z endet, kann dazu führen, dass **ftell** oder **_ftelli64** sich am Ende der Datei falsch verhalten.

Diese Funktion sperrt den aufrufenden Thread während der Ausführung und ist threadsicher. Eine nicht sperrende Version finden Sie **unter _ftell_nolock**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|Optionale Header|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
