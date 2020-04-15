---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 4/2/2020
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
- _o__fstat32
- _o__fstat32i64
- _o__fstat64
- _o__fstat64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
ms.openlocfilehash: 02d297fec2ada545a8b693abacfecc7981149dae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345668"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

Ruft Informationen über eine geöffnete Datei ab

## <a name="syntax"></a>Syntax

```C
int _fstat(
   int fd,
   struct _stat *buffer
);
int _fstat32(
   int fd,
   struct __stat32 *buffer
);
int _fstat64(
   int fd,
   struct __stat64 *buffer
);
int _fstati64(
   int fd,
   struct _stati64 *buffer
);
int _fstat32i64(
   int fd,
   struct _stat32i64 *buffer
);
int _fstat64i32(
   int fd,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Dateideskriptor der geöffneten Datei.

*Puffer*<br/>
Zeiger auf die Struktur zum Speichern der Ergebnisse

## <a name="return-value"></a>Rückgabewert

Gibt 0 zurück, wenn die Dateistatusinformationen abgerufen werden Ein Rückgabewert von -1 gibt einen Fehler an. Wenn der Dateideskriptor ungültig ist oder *Puffer* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EBADF**, im Falle eines ungültigen Dateideskriptors oder **auf EINVAL**, wenn *der Puffer* **NULL**ist, festgelegt.

## <a name="remarks"></a>Bemerkungen

Die **_fstat-Funktion** erhält Informationen über die geöffnete Datei, die *fd* zugeordnet ist, und speichert sie in der Struktur, auf die durch *Puffer*verwiesen wird. Die **_stat** Struktur, die in SYS-Stat.h definiert ist, enthält die folgenden Felder.

|Feld|Bedeutung|
|-|-|
| **st_atime** | Zeitpunkt des letzten Zugriffs auf die Datei |
| **st_ctime** | Zeitpunkt der Erstellung der Datei. |
| **st_dev** | Wenn ein Gerät, *fd*; andernfalls 0. |
| **st_mode** | Bitmaske für Dateimodusinformationen. Das **_S_IFCHR** Bit wird eingestellt, wenn *fd* auf ein Gerät verweist. Das **_S_IFREG** Bit wird festgelegt, wenn *fd* auf eine gewöhnliche Datei verweist. Die Bits für den Lese-/Schreibzugriff werden gemäß dem Dateiberechtigungsmodus festgelegt. **_S_IFCHR** und andere Konstanten sind in SYS-Stat.h definiert. |
| **st_mtime** | Uhrzeit der letzten Änderung der Datei |
| **st_nlink** | Bei Nicht-NTFS-Dateisystemen immer „1“. |
| **st_rdev** | Wenn ein Gerät, *fd*; andernfalls 0. |
| **st_size** | Die Länge der Datei in Bytes. |

Wenn *fd* auf ein Gerät verweist, sind die Felder **st_atime**, **st_ctime**, **st_mtime**und **st_size** nicht aussagekräftig.

Da Stat.h den Typ [_dev_t](../../c-runtime-library/standard-types.md) verwendet, der in Types.h definiert ist, müssen Sie Types.h vor Stat.h in Ihrem Code einschließen.

**_fstat64**, die die **__stat64-Struktur** verwendet, ermöglicht die Aussaierung von Dateierstellungsdaten bis 23:59:59, 31. Dezember 3000, UTC; während die anderen Funktionen nur Datumsangaben bis 23:59:59 Januar 18, 2038, UTC darstellen. Der 1. Januar 1970 (Mitternacht) ist der älteste mögliche Datumsbereich für beide Funktionen.

Varianten dieser Funktionen unterstützen 32-Bit- oder 64-Bit-Zeittypen und 32-Bit- oder 64-Bit-Dateilängen. Das erste numerische Suffix (**32** oder **64**) gibt die Größe des verwendeten Zeittyps an; Das zweite Suffix lautet entweder **i32** oder **i64**, was angibt, ob die Dateigröße als 32-Bit- oder 64-Bit-Ganzzahl dargestellt wird.

**_fstat** entspricht **_fstat64i32**, und **die** **Struktur_stat** enthält eine 64-Bit-Zeit. Dies gilt, es sei **denn, _USE_32BIT_TIME_T** definiert ist, in diesem Fall ist das alte Verhalten wirksam; **_fstat** verwendet eine 32-Bit-Zeit, und **die _stat** **enthält** eine 32-Bit-Zeit. Dasselbe gilt für **_fstati64**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>_stat-Variationen des Uhrzeittyps und Dateilängentyps

|Functions|_USE_32BIT_TIME_T definiert?|Uhrzeittyp|Dateilängentyp|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Nicht definiert|64 Bit|32 Bit|
|**_fstat**|Definiert|32 Bit|32 Bit|
|**_fstat32**|Nicht von der Makrodefinition betroffen|32 Bit|32 Bit|
|**_fstat64**|Nicht von der Makrodefinition betroffen|64 Bit|64 Bit|
|**_fstati64**|Nicht definiert|64 Bit|64 Bit|
|**_fstati64**|Definiert|32 Bit|64 Bit|
|**_fstat32i64**|Nicht von der Makrodefinition betroffen|32 Bit|64 Bit|
|**_fstat64i32**|Nicht von der Makrodefinition betroffen|64 Bit|32 Bit|

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> and \<sys/types.h>|
|**_fstat32**|\<sys/stat.h> and \<sys/types.h>|
|**_fstat64**|\<sys/stat.h> and \<sys/types.h>|
|**_fstati64**|\<sys/stat.h> and \<sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> and \<sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> and \<sys/types.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fstat.c
// This program uses _fstat to report
// the size of a file named F_STAT.OUT.

#include <io.h>
#include <fcntl.h>
#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <share.h>

int main( void )
{
   struct _stat buf;
   int fd, result;
   char buffer[] = "A line to output";
   char timebuf[26];
   errno_t err;

   _sopen_s( &fd,
             "f_stat.out",
             _O_CREAT | _O_WRONLY | _O_TRUNC,
             _SH_DENYNO,
             _S_IREAD | _S_IWRITE );
   if( fd != -1 )
      _write( fd, buffer, strlen( buffer ) );

   // Get data associated with "fd":
   result = _fstat( fd, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      if (errno == EBADF)
        printf( "Bad file descriptor.\n" );
      else if (errno == EINVAL)
        printf( "Invalid argument to _fstat.\n" );
   }
   else
   {
      printf( "File size     : %ld\n", buf.st_size );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid argument to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
   _close( fd );
}
```

```Output
File size     : 16
Time modified : Wed May 07 15:25:11 2003
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, _wstat-Funktionen](stat-functions.md)<br/>
