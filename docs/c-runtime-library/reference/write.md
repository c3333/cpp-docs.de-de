---
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 02864a797a64e6c1b1d836edf4e435cdb43d0932
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211618"
---
# <a name="_write"></a>_write

Schreibt Daten in eine Datei.

## <a name="syntax"></a>Syntax

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Parameter

*FD*<br/>
Dateideskriptor der Datei, in die die Daten geschrieben werden.

*ert*<br/>
Zu schreibende Daten.

*count*<br/>
Die Anzahl von Bytes.

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung gibt **_write** die Anzahl der geschriebenen Bytes zurück. Wenn der tatsächliche Speicherplatz auf dem Datenträger kleiner ist als die Größe des Puffers, der von der Funktion auf den Datenträger geschrieben werden soll, **_write** fehl, und der Inhalt des Puffers wird nicht auf den Datenträger geleert. Der Rückgabewert-1 gibt einen Fehler an. Wenn ungültige Parameter übergeben werden, ruft diese Funktion den Handler für ungültige Parameter auf, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion-1 zurück, und **errno** wird auf einen von drei Werten festgelegt: **EBADF**, was bedeutet, dass der Dateideskriptor ungültig ist oder die Datei nicht zum Schreiben geöffnet ist. **ENOSPC**, was bedeutet, dass auf dem Gerät nicht genügend Speicherplatz für den Vorgang vorhanden ist. oder **EINVAL**, d. h., der *Puffer* war ein NULL-Zeiger, oder es wurde eine ungerade *Anzahl* von Bytes an eine Datei im Unicode-Modus übermittelt.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Wenn die Datei im Textmodus geöffnet ist, wird jedes Zeilenvorschub Zeichen durch ein Wagen Rücklauf-Zeilenvorschub-Paar in der Ausgabe ersetzt. Der Ersatz wirkt sich nicht auf den Rückgabewert aus.

Wenn die Datei im Unicode-Übersetzungsmodus geöffnet wird – z. b. Wenn *FD* mit **_open** oder **_sopen** geöffnet wird und ein Modusparameter **_O_WTEXT**enthält, **_O_U16TEXT**oder **_O_U8TEXT**oder wenn es mit **fopen** und einem Modusparameter, der **CCS = Unicode**, **CCS = UTF-16LE**oder **CCS = UTF-8**enthält, oder wenn der Modus in einen Unicode-Übersetzungsmodus geändert wird, mithilfe **_setmode**–-*Puffer* als Zeiger auf ein-Array interpretiert wird, **`wchar_t`** das **UTF-16-** Daten enthält. Der Versuch, in diesem Modus eine ungerade Anzahl von Bytes zu schreiben, führt zu einem Parametervalidierungsfehler.

## <a name="remarks"></a>Bemerkungen

Die **_write** -Funktion schreibt *count* -Bytes aus dem *Puffer* in die mit *FD*verknüpfte Datei. Der Schreibvorgang beginnt an der aktuellen Position des Dateizeigers (falls vorhanden) für die betreffende Datei. Wenn die Datei zum Anhängen geöffnet ist, beginnt der Vorgang am aktuellen Dateiende. Nach dem Schreibvorgang wird der Dateizeiger um die Anzahl der geschriebenen Bytes erweitert.

Beim Schreiben in Dateien, die im Textmodus geöffnet wurden, behandelt **_write** ein STRG + Z-Zeichen als logisches Dateiende. Beim Schreiben auf ein Gerät behandelt **_write** ein STRG + Z-Zeichen im Puffer als Ausgabe Abschluss Zeichen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_write**|\<io.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occurred
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>Weitere Informationen

[E/a auf niedriger Ebene](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
