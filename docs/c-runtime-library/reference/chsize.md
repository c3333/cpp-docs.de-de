---
title: _chsize
ms.date: 4/2/2020
api_name:
- _chsize
- _o__chsize
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
- _chsize
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
ms.openlocfilehash: 5b9b58cf3ca4e167b5d54f871ac31c5295adc48b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917202"
---
# <a name="_chsize"></a>_chsize

Ändert die Größe einer Datei. Es ist eine sicherere Version verfügbar. Informationen dazu finden Sie unter [_chsize_s](chsize-s.md).

## <a name="syntax"></a>Syntax

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>Parameter

*FD*<br/>
Dateideskriptor, der auf eine geöffnete Datei verweist.

*size*<br/>
Neue Länge der Datei in Bytes.

## <a name="return-value"></a>Rückgabewert

**_chsize** gibt den Wert 0 (null) zurück, wenn die Dateigröße erfolgreich geändert wurde. Der Rückgabewert-1 weist auf einen Fehler hin: **errno** ist auf **EACCES** festgelegt, wenn die angegebene Datei schreibgeschützt ist oder die angegebene Datei für den Zugriff gesperrt ist, auf **EBADF** , wenn der Deskriptor ungültig ist, **ENOSPC** , wenn kein Speicherplatz auf dem Gerät vorhanden ist, oder **EINVAL** , wenn die *Größe* kleiner als 0 (null) ist.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_chsize** -Funktion erweitert oder verkürzt die mit *FD* zugeordnete Datei mit der durch *size*angegebenen Länge. Die Datei muss in einem Modus geöffnet sein, der Schreiben zulässt. Wenn die Datei erweitert wird, werden NULL-Zeichen ('\0') angefügt. Wenn die Datei abgeschnitten wird, gehen alle Daten vom Ende der gekürzten Datei bis zur ursprünglichen Länge der Datei verloren.

Diese Funktion überprüft ihre Parameter. Wenn die *Größe* kleiner als 0 (null) oder *FD* ein fehlerhafter Dateideskriptor ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_chsize.c
// This program uses _filelength to report the size
// of a file before and after modifying it with _chsize.

#include <io.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh, result;
   unsigned int nbytes = BUFSIZ;

   // Open a file
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,
                 _S_IREAD | _S_IWRITE ) == 0 )
   {
      printf( "File length before: %ld\n", _filelength( fh ) );
      if( ( result = _chsize( fh, 329678 ) ) == 0 )
         printf( "Size successfully changed\n" );
      else
         printf( "Problem in changing the size\n" );
      printf( "File length after:  %ld\n", _filelength( fh ) );
      _close( fh );
   }
}
```

```Output
File length before: 0
Size successfully changed
File length after:  329678
```

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
