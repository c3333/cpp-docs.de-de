---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 4/2/2020
api_name:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
- _o__utime32
- _o__utime64
- _o__wutime32
- _o__wutime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: dbff557cd116eb1df44f015b17716408c8dc54c2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912131"
---
# <a name="_utime-_utime32-_utime64-_wutime-_wutime32-_wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64

Legen Sie die Dateiänderungszeit fest.

## <a name="syntax"></a>Syntax

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>Parameter

*Einfügen*<br/>
Zeiger auf eine Zeichenfolge, die den Pfad oder Dateiname enthält.

*Vielfaches*<br/>
Zeiger auf die gespeicherten Zeitwerte.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt „0“ zurück, wenn die Dateiänderungszeit geändert wurde. Der Rückgabewert-1 gibt einen Fehler an. Wird ein ungültiger Parameter übergeben, wird der Handler für ungültige Parameter aufgerufen, wie unter [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen-1 zurück, und **errno** wird auf einen der folgenden Werte festgelegt:

|errno-Wert|Bedingung|
|-|-|
| **EACCES** | Pfad gibt Verzeichnis oder schreibgeschützte Datei an. |
| **Eingabe** | Ungültiges *Times* -Argument |
| **EMFILE** | Zu viele Dateien geöffnet. (Die Datei muss geöffnet werden, damit die Änderungszeit geändert werden kann.) |
| **ENOENT** | Pfad oder Dateiname wurde nicht gefunden. |

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Wenn das Datum der Änderung nach dem 1. Januar 1970, Mitternacht, und vor dem Enddatum für die Verwendung der Funktion liegt, kann das Datum für eine Datei geändert werden. **_utime** und **_wutime** einen 64-Bit-Uhrzeitwert verwenden, d. h., das Enddatum ist 23:59:59, der 31. Dezember 3000, UTC. Wenn **_USE_32BIT_TIME_T** definiert ist, um das alte Verhalten zu erzwingen, ist das Enddatum 23:59:59 Januar, 2038 UTC. **_utime32** oder **_wutime32** einen 32-Bit-Uhrzeittyp verwenden, unabhängig davon, ob **_USE_32BIT_TIME_T** definiert ist, und immer über das frühere Enddatum verfügen. **_utime64** oder **_wutime64** immer den 64-Bit-Uhrzeittyp verwenden, sodass diese Funktionen immer das spätere Enddatum unterstützen.

## <a name="remarks"></a>Hinweise

Die **_utime** -Funktion legt die Änderungszeit für die durch *filename*angegebene Datei fest. Damit die Zeit geändert werden kann, benötigt der Prozess Schreibzugriff für die Datei. Im Windows-Betriebssystem können Sie die Zugriffszeit und die Änderungszeit in der **_utimbuf** Struktur ändern. Wenn *Times* ein **null** -Zeiger ist, wird die Änderungszeit auf die aktuelle Ortszeit festgelegt. Andernfalls müssen *Uhrzeiten* auf eine Struktur des Typs **_utimbuf**verweisen, der in sys\utimedefiniert ist. Micha.

Die **_utimbuf** Struktur speichert Datei Zugriffs-und Änderungs Zeiten, die von **_utime** verwendet werden, um Datumsangaben zu Dateiänderungen zu ändern. Die Struktur verfügt über die folgenden Felder, die beide vom Typ **time_t**sind:

| Feld |   |
|-------|---|
| **actime** | Uhrzeit des Dateizugriffs |
| **modtime** | Uhrzeit der Dateiänderung |

Bestimmte Versionen der **_utimbuf** Struktur (**_utimebuf32** und **__utimbuf64**) werden mithilfe der 32-Bit-und 64-Bit-Versionen des Uhrzeittyps definiert. Diese werden in den 32-Bit- und 64-Bit-spezifischen Versionen dieser Funktion verwendet. **_utimbuf** selbst verwendet standardmäßig einen 64-Bit-Uhrzeittyp, es sei denn, **_USE_32BIT_TIME_T** ist definiert.

**_utime** ist mit **_futime** identisch, mit dem Unterschied, dass das *filename* -Argument von **_utime** ein Dateiname oder ein Pfad zu einer Datei ist, und nicht der Dateideskriptor einer geöffneten Datei.

**_wutime** ist eine breit Zeichen Version von **_utime**. Das *filename* -Argument für **_wutime** ist eine Zeichenfolge mit breit Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderliche Header|Optionale Header|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32** **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h> oder \<wchar.h>|\<errno.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Programm verwendet **_utime** , um die Datei Änderungszeit auf die aktuelle Zeit festzulegen.

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>Beispielausgabe

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>Weitere Informationen

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime, _futime32, _futime64](futime-futime32-futime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat, _wstat-Funktionen](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
