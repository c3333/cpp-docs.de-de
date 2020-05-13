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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 81c272187c681010e7b8560d43f2fad87e1e0fdc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910124"
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

*FD*<br/>
Dateideskriptor der geöffneten Datei.

*ert*<br/>
Zeiger auf die Struktur zum Speichern der Ergebnisse

## <a name="return-value"></a>Rückgabewert

Gibt 0 zurück, wenn die Dateistatusinformationen abgerufen werden Der Rückgabewert-1 gibt einen Fehler an. Wenn der Dateideskriptor ungültig ist oder *buffer* der Puffer **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EBADF**festgelegt, bei einem ungültigen Dateideskriptor oder auf **EINVAL**, wenn der *Puffer* **null**ist.

## <a name="remarks"></a>Hinweise

Die **_fstat** Funktion Ruft Informationen über die geöffnete Datei ab, die mit *FD* verknüpft ist, und speichert Sie in der Struktur, auf die von *buffer*verwiesen wird. Die **_stat** -Struktur, die in sys\status .h definiert ist, enthält die folgenden Felder.

|Feld|Bedeutung|
|-|-|
| **st_atime** | Zeitpunkt des letzten Zugriffs auf die Datei |
| **st_ctime** | Zeitpunkt der Erstellung der Datei. |
| **st_dev** | Wenn ein Gerät, *FD*; andernfalls 0. |
| **st_mode** | Bitmaske für Dateimodusinformationen. Das **_S_IFCHR** Bit wird festgelegt, wenn *FD* auf ein Gerät verweist. Das **_S_IFREG** Bit wird festgelegt, wenn *FD* auf eine gewöhnliche Datei verweist. Die Bits für den Lese-/Schreibzugriff werden gemäß dem Dateiberechtigungsmodus festgelegt. **_S_IFCHR** und andere Konstanten werden in sys\status h. definiert. |
| **st_mtime** | Uhrzeit der letzten Änderung der Datei |
| **st_nlink** | Bei Nicht-NTFS-Dateisystemen immer „1“. |
| **st_rdev** | Wenn ein Gerät, *FD*; andernfalls 0. |
| **st_size** | Die Länge der Datei in Bytes. |

Wenn *FD* auf ein Gerät verweist, sind die Felder **st_atime**, **st_ctime**, **st_mtime**und **st_size** nicht sinnvoll.

Da Stat.h den Typ [_dev_t](../../c-runtime-library/standard-types.md) verwendet, der in Types.h definiert ist, müssen Sie Types.h vor Stat.h in Ihrem Code einschließen.

**_fstat64**, die die **__stat64** -Struktur verwendet, ermöglicht das Ausdrücken von Datei Erstellungs Daten bis 23:59:59, 31. Dezember 3000, UTC; während die anderen Funktionen nur Datumsangaben 23:59:59 bis zum 18. Januar 2038 (UTC) darstellen. Der 1. Januar 1970 (Mitternacht) ist der älteste mögliche Datumsbereich für beide Funktionen.

Varianten dieser Funktionen unterstützen 32-Bit- oder 64-Bit-Zeittypen und 32-Bit- oder 64-Bit-Dateilängen. Das erste numerische Suffix (**32** oder **64**) gibt die Größe des verwendeten Zeittyps an. Das zweite Suffix ist entweder **i32** oder **I64**, das angibt, ob die Dateigröße als 32-Bit-oder 64-Bit-Ganzzahl dargestellt wird.

**_fstat** entspricht **_fstat64i32**, und die **Struktur** **_stat** eine 64-Bit-Zeit enthält. Dies trifft zu, wenn **_USE_32BIT_TIME_T** nicht definiert ist. in diesem Fall ist das alte Verhalten wirksam. **_fstat** verwendet einen 32-Bit-Zeitpunkt, und die **Struktur** **_stat** eine 32-Bit-Zeit enthält. Das gleiche gilt für **_fstati64**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>_stat-Variationen des Uhrzeittyps und Dateilängentyps

|Functions|_USE_32BIT_TIME_T definiert?|Uhrzeittyp|Dateilängentyp|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Nicht definiert|64-Bit|32-Bit|
|**_fstat**|Definiert|32-Bit|32-Bit|
|**_fstat32**|Nicht von der Makrodefinition betroffen|32-Bit|32-Bit|
|**_fstat64**|Nicht von der Makrodefinition betroffen|64-Bit|64-Bit|
|**_fstati64**|Nicht definiert|64-Bit|64-Bit|
|**_fstati64**|Definiert|32-Bit|64-Bit|
|**_fstat32i64**|Nicht von der Makrodefinition betroffen|32-Bit|64-Bit|
|**_fstat64i32**|Nicht von der Makrodefinition betroffen|64-Bit|32-Bit|

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

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, _wstat-Funktionen](stat-functions.md)<br/>
