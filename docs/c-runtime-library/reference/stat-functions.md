---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
ms.date: 4/2/2020
api_name:
- _wstat64
- _stati64
- _stat32
- _stat32i64
- _stat
- _wstati64
- _wstat32
- _wstat64i32
- _wstat
- _stat64
- _stat64i32
- _wstat32i64
- _o__stat32
- _o__stat32i64
- _o__stat64
- _o__stat64i32
- _o__wstat32
- _o__wstat32i64
- _o__wstat64
- _o__wstat64i32
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
- tstat32
- tstat
- _tstat64i32
- tstati64
- _wstat64
- _wstat32
- wstati64
- tstat64
- _stati64
- _wstat
- wstat64i32
- stat32i64
- tstat32i64
- _tstat
- _wstati64
- _tstati64
- _wstat32i64
- wstat32
- _wstat64i32
- _stat
- _tstat32
- stat64i32
- wstat64
- stat
- _stat32i64
- _stat32
- stati64
- wstat
- _stat64i32
- stat32
- _tstat32i64
- tstat64i32
- _tstat64
- _stat64
- stat/_stat
- stat/_stat32
- stat/_stat64
- stat/_stati64
- stat/_stat32i64
- stat/_stat64i32
- stat/_wstat
- stat/_wstat32
- stat/_wstat64
- stat/_wstati64
- stat/_wstat32i64
- stat/_wstat64i32
helpviewer_keywords:
- files [C++], status information
- _stat function
- _wstat function
- _stat64i32 function
- tstat function
- _tstat64i32 function
- _stati64 function
- _stat64 function
- tstati64 function
- wstati64 function
- wstat64 function
- _wstat64i32 function
- _tstat32i64 function
- _stat32i64 function
- stat function
- status of files
- _tstat32 function
- tstat64 function
- _wstat64 function
- _tstat function
- _stat32 function
- wstat function
- _wstat32i64 function
- _tstati64 function
- _wstat32 function
- stat64 function
- stati64 function
- _wstati64 function
- _tstat64 function
- files [C++], getting status information
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
ms.openlocfilehash: 607a7aff3acf923e0dd62e0dc332283f66b436b1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918322"
---
# <a name="_stat-_stat32-_stat64-_stati64-_stat32i64-_stat64i32-_wstat-_wstat32-_wstat64-_wstati64-_wstat32i64-_wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Abrufen von Statusinformationen zu einer Datei.

## <a name="syntax"></a>Syntax

```C
int _stat(
   const char *path,
   struct _stat *buffer
);
int _stat32(
   const char *path,
   struct __stat32 *buffer
);
int _stat64(
   const char *path,
   struct __stat64 *buffer
);
int _stati64(
   const char *path,
   struct _stati64 *buffer
);
int _stat32i64(
   const char *path,
   struct _stat32i64 *buffer
);
int _stat64i32(
   const char *path,
   struct _stat64i32 *buffer
);
int _wstat(
   const wchar_t *path,
   struct _stat *buffer
);
int _wstat32(
   const wchar_t *path,
   struct __stat32 *buffer
);
int _wstat64(
   const wchar_t *path,
   struct __stat64 *buffer
);
int _wstati64(
   const wchar_t *path,
   struct _stati64 *buffer
);
int _wstat32i64(
   const wchar_t *path,
   struct _stat32i64 *buffer
);
int _wstat64i32(
   const wchar_t *path,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>Parameter

*path*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Pfad einer vorhandenen Datei oder eines vorhandenen Verzeichnisses enthält.

*ert*<br/>
Ein Zeiger auf die Struktur, in der die Ergebnisse gespeichert werden.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt „0“ zurück, wenn die Dateistatusinformationen abgerufen werden. Der Rückgabewert-1 gibt einen Fehler an. in diesem Fall wird **errno** auf **ENOENT**festgelegt, um anzugeben, dass der Dateiname oder Pfad nicht gefunden werden konnte. Der Rückgabewert von " **einmal** " gibt einen ungültigen Parameter an. **errno** wird in diesem Fall ebenfalls auf **EINVAL** festgelegt.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

Der Datumsstempel einer Datei kann dargestellt werden, wenn Sie später als Mitternacht, 1. Januar 1970 und vor 23:59:59 am 31. Dezember 3000 UTC ist, es sei denn, Sie verwenden **_stat32** oder **_wstat32**oder haben **_USE_32BIT_TIME_T**definiert. in diesem Fall kann das Datum nur bis 23:59:59 zum 18. Januar 2038,, UTC dargestellt werden.

## <a name="remarks"></a>Hinweise

Die **_stat** Funktion Ruft Informationen über die Datei oder das Verzeichnis ab, die von *path* angegeben werden, und speichert Sie in der Struktur, auf die von *buffer*verwiesen wird. **_stat** automatisch Multibytezeichen-Zeichen folgen Argumente behandelt, wobei Multibytezeichen-Zeichensequenzen gemäß der derzeit verwendeten Multibytezeichen-Codepage erkannt werden.

**_wstat** ist eine breit Zeichen Version von **_stat**. Das *path* -Argument für **_wstat** ist eine Zeichenfolge mit breit Zeichen. **_wstat** und **_stat** Verhalten sich identisch, mit dem Unterschied, dass **_wstat** keine Multibyte-Zeichen folgen verarbeitet.

Varianten dieser Funktionen unterstützen 32-Bit- oder 64-Bit-Zeittypen und 32-Bit- oder 64-Bit-Dateilängen. Das erste numerische Suffix (**32** oder **64**) gibt die Größe des verwendeten Zeittyps an. Das zweite Suffix ist entweder **i32** oder **I64**, das angibt, ob die Dateigröße als 32-Bit-oder 64-Bit-Ganzzahl dargestellt wird.

**_stat** entspricht **_stat64i32**, und die **Struktur** **_stat** eine 64-Bit-Zeit enthält. Dies trifft zu, wenn **_USE_32BIT_TIME_T** nicht definiert ist. in diesem Fall ist das alte Verhalten wirksam. **_stat** verwendet einen 32-Bit-Zeitpunkt, und die **Struktur** **_stat** eine 32-Bit-Zeit enthält. Das gleiche gilt für **_stati64**.

> [!NOTE]
> **_wstat** funktioniert nicht mit symbolischen Verknüpfungen von Windows Vista. In diesen Fällen wird **_wstat** immer eine Dateigröße von 0 melden. **_stat** funktioniert mit symbolischen Verknüpfungen ordnungsgemäß.

Diese Funktion überprüft ihre Parameter. Wenn ein *Pfad* oder *buffer* ein Puffer **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>_stat-Variationen des Uhrzeittyps und Dateilängentyps

|Functions|_USE_32BIT_TIME_T definiert?|Uhrzeittyp|Dateilängentyp|
|---------------|------------------------------------|---------------|----------------------|
|**_stat** **_wstat**|Nicht definiert|64-Bit|32-Bit|
|**_stat** **_wstat**|Definiert|32-Bit|32-Bit|
|**_stat32** **_wstat32**|Nicht von der Makrodefinition betroffen|32-Bit|32-Bit|
|**_stat64** **_wstat64**|Nicht von der Makrodefinition betroffen|64-Bit|64-Bit|
|**_stati64** **_wstati64**|Nicht definiert|64-Bit|64-Bit|
|**_stati64** **_wstati64**|Definiert|32-Bit|64-Bit|
|**_stat32i64** **_wstat32i64**|Nicht von der Makrodefinition betroffen|32-Bit|64-Bit|
|**_stat64i32** **_wstat64i32**|Nicht von der Makrodefinition betroffen|64-Bit|32-Bit|

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

Die **_stat** -Struktur, die in sys\status definiert ist. H enthält die folgenden Felder.

|Feld||
|-|-|
| **st_gid** | Numerischer Bezeichner der Gruppe, die die Datei besitzt (UNIX-spezifisch). Dieses Feld weist auf Windows-Systemen immer den Wert „0“ (null) auf. Eine umgeleitete Datei wird als Windows-Datei klassifiziert. |
| **st_atime** | Zeitpunkt des letzten Zugriffs auf die Datei. Gültig auf NTFS-, aber nicht auf FAT-formatierten Laufwerken. |
| **st_ctime** | Uhrzeit der Dateierstellung. Gültig auf NTFS-, aber nicht auf FAT-formatierten Laufwerken. |
| **st_dev** | Laufwerksnummer des Datenträgers, der die Datei enthält (identisch mit **st_rdev**). |
| **st_ino** | Anzahl der Informations Knoten (der **tatsächliche**) für die Datei (Unix-spezifisch). Auf UNIX-Dateisystemen beschreibt die **tatsächliche** die Datums-und Zeitstempel, Berechtigungen und Inhalte der Datei. Wenn Dateien hart miteinander verknüpft sind, verwenden Sie dieselbe **tatsächliche**. Die **tatsächliche**und somit **st_ino**haben keine Bedeutung in den FAT-, HPFS-oder NTFS-Dateisystemen. |
| **st_mode** | Bitmaske für Dateimodusinformationen. Das **_S_IFDIR** Bit wird festgelegt, wenn der *Pfad* ein Verzeichnis angibt. Das **_S_IFREG** Bit ist festgelegt, wenn *path* eine gewöhnliche Datei oder ein Gerät angibt. Lese-/Schreibbits für Benutzer werden entsprechend dem Berechtigungsmodus der Datei festgelegt; Ausführungsbits für Benutzer werden entsprechend der Dateierweiterung festgelegt. |
| **st_mtime** | Uhrzeit der letzten Änderung der Datei. |
| **st_nlink** | Bei Nicht-NTFS-Dateisystemen immer „1“. |
| **st_rdev** | Laufwerksnummer des Datenträgers, der die Datei enthält (identisch mit **st_dev**). |
| **st_size** | Größe der Datei in Bytes. eine 64-Bit-Ganzzahl für Variationen mit dem **I64** -Suffix. |
| **st_uid** | Numerischer Bezeichner des Benutzers, der die Datei besitzt (UNIX-spezifisch). Dieses Feld hat bei Windows-Systemen immer den Wert „0“. Eine umgeleitete Datei wird als Windows-Datei klassifiziert. |

Wenn *path* auf ein Gerät verweist, sind die **st_size**, verschiedene Zeitfelder, **st_dev**und **st_rdev** Felder in der **_stat** Struktur bedeutungslos. Da „STAT.H“ den [_dev_t](../../c-runtime-library/standard-types.md)-Typ verwendet, der in „TYPES.H“ definiert ist, müssen Sie „TYPES.H“ vor „STAT.H“ in Ihrem Code einschließen.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionale Header|
|-------------|---------------------|----------------------|
|**_stat**, **_stat32**, **_stat64**, **_stati64**, **_stat32i64** **_stat64i32**|\<sys/types.h> gefolgt von \<sys/stat.h>|\<errno.h>|
|**_wstat**, **_wstat32**, **_wstat64**, **_wstati64**, **_wstat32i64** **_wstat64i32**|\<sys/types.h> gefolgt von \<sys/stat.h> oder \<wchar.h>|\<errno.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_stat.c
// This program uses the _stat function to
// report information about the file named crt_stat.c.

#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   struct _stat buf;
   int result;
   char timebuf[26];
   char* filename = "crt_stat.c";
   errno_t err;

   // Get data associated with "crt_stat.c":
   result = _stat( filename, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      perror( "Problem getting information" );
      switch (errno)
      {
         case ENOENT:
           printf("File %s not found.\n", filename);
           break;
         case EINVAL:
           printf("Invalid parameter to _stat.\n");
           break;
         default:
           /* Should never be reached. */
           printf("Unexpected error in _stat.\n");
      }
   }
   else
   {
      // Output some of the statistics:
      printf( "File size     : %ld\n", buf.st_size );
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid arguments to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
}
```

```Output
File size     : 732
Drive         : C:
Time modified : Thu Feb 07 14:39:36 2002
```

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
