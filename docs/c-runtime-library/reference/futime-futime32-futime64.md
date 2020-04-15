---
title: _futime, _futime32, _futime64
ms.date: 4/2/2020
api_name:
- _futime64
- _futime32
- _futime
- _o__futime32
- _o__futime64
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- futime
- _futime
- futime64
- _futime64
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
ms.openlocfilehash: 1f60bb3b366c48e3d53368f81ebc2528694794f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345506"
---
# <a name="_futime-_futime32-_futime64"></a>_futime, _futime32, _futime64

Legt das Änderungsdatum einer offenen Datei fest

## <a name="syntax"></a>Syntax

```C
int _futime(
   int fd,
   struct _utimbuf *filetime
);
int _futime32(
   int fd,
   struct __utimbuf32 *filetime
);
int _futime64(
   int fd,
   struct __utimbuf64 *filetime
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Dateideskriptor der geöffneten Datei

*Filetime*<br/>
Zeiger auf die Struktur, die das neue Änderungsdatum enthält

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg 0 zurück. Wenn ein Fehler auftritt, wird der Handler für ungültige Parameter aufgerufen, so wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion -1 zurück, und **errno** wird auf **EBADF**gesetzt, was auf einen ungültigen Dateideskriptor oder **EINVAL**hinweist, der einen ungültigen Parameter angibt.

## <a name="remarks"></a>Bemerkungen

Die **_futime-Routine** legt das Änderungsdatum und die Zugriffszeit für die geöffnete Datei fest, die *fd*zugeordnet ist. **_futime** ist identisch mit [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), außer dass sein Argument der Dateideskriptor einer geöffneten Datei ist und nicht der Name einer Datei oder eines Pfads zu einer Datei. Die **_utimbuf** Struktur enthält Felder für das neue Änderungsdatum und die neue Zugriffszeit. Beide Felder müssen gültige Werte enthalten. **_utimbuf32** und **_utimbuf64** sind identisch mit **_utimbuf** mit Ausnahme der Verwendung der 32-Bit- bzw. 64-Bit-Zeittypen. **_futime** und **_utimbuf** einen 64-Bit-Zeittyp verwenden, und **_futime** ist im Verhalten mit **_futime64**identisch. Wenn Sie das alte Verhalten erzwingen müssen, definieren Sie **_USE_32BIT_TIME_T**. Dadurch wird **_futime** im Verhalten **mit _futime32** identisch und die **_utimbuf** Struktur verwendet den 32-Bit-Zeittyp, so dass er **__utimbuf32**entspricht.

**_futime64**, die die **__utimbuf64-Struktur** verwendet, können Dateidaten bis 23:59:59, 31. Dezember 3000, UTC lesen und ändern; während ein Aufruf an **_futime32** fehlschlägt, wenn das Datum in der Datei nach 23:59:59 Januar 18, 2038, UTC. Der 1. Januar 1970 (Mitternacht) ist der älteste mögliche Datumsbereich für diese Funktionen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|Optionaler Header|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_futime.c
// This program uses _futime to set the
// file-modification time to the current time.

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <io.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/utime.h>
#include <share.h>

int main( void )
{
   int hFile;

   // Show file time before and after.
   system( "dir crt_futime.c_input" );

   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );

   if( _futime( hFile, NULL ) == -1 )
      perror( "_futime failed\n" );
   else
      printf( "File time modified\n" );

   _close (hFile);

   system( "dir crt_futime.c_input" );
}
```

### <a name="input-crt_futimec_input"></a>Eingabe: crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>Beispielausgabe

```Output
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:40 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:41 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
File time modified
```

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
