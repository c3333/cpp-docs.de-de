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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a616df570d266c335337d897da59a2a0ec69b40e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367396"
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

*Fd*<br/>
Dateideskriptor der Datei, in die die Daten geschrieben werden.

*Puffer*<br/>
Zu schreibende Daten.

*count*<br/>
Die Anzahl von Bytes.

## <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, **gibt _write** die Anzahl der geschriebenen Bytes zurück. Wenn der tatsächlich verbleibende Speicherplatz auf dem Datenträger kleiner als die Größe des Puffers ist, versucht die Funktion, auf den Datenträger zu schreiben, **schlägt _write** fehl und löscht keinen Inhalt des Puffers auf den Datenträger. Ein Rückgabewert von -1 gibt einen Fehler an. Wenn ungültige Parameter übergeben werden, ruft diese Funktion den Handler für ungültige Parameter auf, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion -1 zurück, und **errno** wird auf einen von drei Werten gesetzt: **EBADF**, was bedeutet, dass der Dateideskriptor ungültig ist oder die Datei nicht zum Schreiben geöffnet wird. **ENOSPC**, was bedeutet, dass nicht mehr genügend Speicherplatz auf dem Gerät für den Betrieb vorhanden ist; oder **EINVAL**, was bedeutet, dass *der Puffer* ein Nullzeiger war oder dass eine ungerade *Anzahl* von Bytes übergeben wurde, um im Unicode-Modus in eine Datei geschrieben zu werden.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Wenn die Datei im Textmodus geöffnet wird, wird jedes Zeilenvorschubzeichen in der Ausgabe durch ein Wagen-Rücklaufpaar ersetzt. Die Ersetzung wirkt sich nicht auf den Rückgabewert aus.

Wenn die Datei im Unicode-Übersetzungsmodus geöffnet wird, z. B. Wenn *fd* mit **_open** oder **_sopen** und einem Modusparameter geöffnet wird, der **_O_WTEXT**, **_O_U16TEXT**oder **_O_U8TEXT**enthält, oder wenn es mit **fopen** und einem Modusparameter geöffnet wird, der **ccs=UNICODE**, **ccs=UTF-16LE**oder **ccs=UTF-8**enthält, oder wenn der Modus mithilfe von **_setmode**in einen Unicode-Übersetzungsmodus geändert wird – wird der*Puffer* als Pointer **auf ein** Array von wchar_t interpretiert, die **UTF-16-Daten** enthält. Der Versuch, in diesem Modus eine ungerade Anzahl von Bytes zu schreiben, führt zu einem Parametervalidierungsfehler.

## <a name="remarks"></a>Bemerkungen

Die **_write-Funktion** *schreibt Zählbytes* aus dem *Puffer* in die Datei, die *fd*zugeordnet ist. Der Schreibvorgang beginnt an der aktuellen Position des Dateizeigers (falls vorhanden) für die betreffende Datei. Wenn die Datei zum Anhängen geöffnet ist, beginnt der Vorgang am aktuellen Dateiende. Nach dem Schreibvorgang wird der Dateizeiger um die Anzahl der geschriebenen Bytes erhöht.

Beim Schreiben in Dateien, die im Textmodus geöffnet werden, behandelt **_write** ein STRG+Z-Zeichen als logisches Ende der Datei. Beim Schreiben auf ein Gerät behandelt **_write** ein STRG+Z-Zeichen im Puffer als Ausgabeabschluss.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
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

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
