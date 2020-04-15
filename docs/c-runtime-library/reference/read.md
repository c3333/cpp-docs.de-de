---
title: _read
ms.date: 4/2/2020
api_name:
- _read
- _o__read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: db3726b85bb4ba7c8e9a691bef3fb063ec5709c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338130"
---
# <a name="_read"></a>_read

Liest Daten aus einer Datei.

## <a name="syntax"></a>Syntax

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Dateideskriptor, der auf die geöffnete Datei verweist.

*Puffer*<br/>
Speicherort für Daten.

*buffer_size*<br/>
Maximale Anzahl zu lesender Bytes.

## <a name="return-value"></a>Rückgabewert

**_read** gibt die Anzahl der gelesenen Bytes zurück, die möglicherweise kleiner als *buffer_size* sind, wenn weniger als *buffer_size* Bytes in der Datei verbleiben oder wenn die Datei im Textmodus geöffnet wurde. Im Textmodus wird jedes Wagen-Rücklaufpaar `\r\n` durch ein `\n`einzelnes Zeilenvorschubzeichen ersetzt. Nur das einzeilige Vorschubzeichen wird im Rückgabewert gezählt. Der Ersatz hat keine Auswirkung auf den Rückgabezeiger.

Wenn die Funktion versucht, am Ende der Datei zu lesen, wird 0 zurückgegeben. Wenn *fd* ungültig ist, die Datei nicht zum Lesen geöffnet ist oder die Datei gesperrt ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion -1 zurück und setzt **errno** auf **EBADF**.

Wenn *buffer* **NULL**ist oder *wenn buffer_size* > **INT_MAX**wird der ungültige Parameterhandler aufgerufen. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion -1 zurück und **errno** wird auf **EINVAL**gesetzt.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_read-Funktion** liest maximal *buffer_size* Bytes aus der Datei, die *fd*zugeordnet ist, in den *Puffer.* Der Lesevorgang beginnt an der aktuellen Position des Dateizeigers für die betreffende Datei. Nach dem Lesevorgang zeigt der Dateizeiger auf das nächste ungelesene Zeichen.

Wenn die Datei im Textmodus geöffnet wurde, wird der Lesefehler beendet, wenn **_read** auf ein STRG+Z-Zeichen trifft, das als Dateiende-Indikator behandelt wird. Verwenden Sie [_lseek](lseek-lseeki64.md), um den Dateiende-Indikator zu löschen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_read**|\<io.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_read.c
/* This program opens a file named crt_read.txt
* and tries to read 60,000 bytes from
* that file using _read. It then displays the
* actual number of bytes read.
*/

#include <fcntl.h>      /* Needed only for _O_RDWR definition */
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

char buffer[60000];

int main( void )
{
   int fh, bytesread;
   unsigned int nbytes = 60000;

   /* Open file for input: */
   if ( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ))
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if (( bytesread = _read( fh, buffer, nbytes )) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crt_readtxt"></a>Eingabe: crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
