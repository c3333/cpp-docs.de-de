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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 2f43fc54a0092afc6ab5855c160a7879747faef7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919514"
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

*FD*<br/>
Dateideskriptor, der auf die geöffnete Datei verweist.

*ert*<br/>
Speicherort für Daten.

*buffer_size*<br/>
Maximale Anzahl der zu lesenden Bytes.

## <a name="return-value"></a>Rückgabewert

**_read** gibt die Anzahl der gelesenen Bytes zurück, die möglicherweise kleiner als *buffer_size* ist, wenn in der Datei weniger als *buffer_size* Bytes verbleiben oder wenn die Datei im Textmodus geöffnet wurde. Im Textmodus wird jedes Wagen Rücklauf-Zeilenvorschub-Paar `\r\n` durch ein Einzel Zeilen- `\n`Feed-Zeichen ersetzt. Nur das einzeilige Einfügezeichen wird im Rückgabewert gezählt. Der Ersatz hat keine Auswirkung auf den Rückgabezeiger.

Wenn die Funktion versucht, am Ende der Datei zu lesen, wird 0 zurückgegeben. Wenn *FD* nicht gültig ist, die Datei nicht zum Lesen geöffnet ist oder die Datei gesperrt ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion-1 zurück und legt **errno** auf **EBADF**fest.

Wenn *buffer* der Puffer **null**ist, oder wenn *buffer_size* > **INT_MAX**, wird der Handler für ungültige Parameter aufgerufen. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion-1 zurück, und **errno** ist auf **EINVAL**festgelegt.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_read** -Funktion liest maximal *buffer_size* Bytes aus der Datei, die mit *FD*verknüpft ist, in den *Puffer* . Der Lesevorgang beginnt an der aktuellen Position des Dateizeigers für die betreffende Datei. Nach dem Lesevorgang zeigt der Dateizeiger auf das nächste ungelesene Zeichen.

Wenn die Datei im Textmodus geöffnet wurde, wird der Lesevorgang beendet, wenn **_read** ein STRG + Z-Zeichen trifft, das als Dateiende-Indikator behandelt wird. Verwenden Sie [_lseek](lseek-lseeki64.md), um den Dateiende-Indikator zu löschen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

[E/a auf niedriger Ebene](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
