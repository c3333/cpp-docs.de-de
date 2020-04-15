---
title: _tell, _telli64
ms.date: 4/2/2020
api_name:
- _telli64
- _tell
- _o__tell
- _o__telli64
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
- telli64
- _telli64
- _tell
helpviewer_keywords:
- tell function
- file pointers [C++], getting
- _tell function
- file pointers [C++]
- telli64 function
- _telli64 function
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
ms.openlocfilehash: 111d5745703d15fccf0b2a941248203cc80d07a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362558"
---
# <a name="_tell-_telli64"></a>_tell, _telli64

Aktuelle Position des Dateizeigers

## <a name="syntax"></a>Syntax

```C
long _tell(
   int handle
);
__int64 _telli64(
   int handle
);
```

### <a name="parameters"></a>Parameter

*Behandeln*<br/>
Dateideskriptoren, die auf eine geöffnete Datei verweisen.

## <a name="return-value"></a>Rückgabewert

Aktuelle Position des Dateizeigers Auf Geräten, die Suchvorgänge nicht unterstützen, ist der Rückgabewert nicht definiert.

Ein Rückgabewert von -1L gibt einen Fehler an. Wenn *handle* ein ungültiger Dateideskriptor ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EBADF** und geben -1L zurück.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Bemerkungen

Die **_tell-Funktion** ruft die aktuelle Position des Dateizeigers (falls vorhanden) ab, der dem *handle-Argument* zugeordnet ist. Die Position wird als Anzahl von Bytes ab dem Anfang der Datei angegeben. Für die **_telli64** Funktion wird dieser Wert als 64-Bit-Ganzzahl ausgedrückt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_tell**, **_telli64**|\<io.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_tell.c
// This program uses _tell to tell the
// file pointer position after a file read.
//

#include <io.h>
#include <stdio.h>
#include <fcntl.h>
#include <share.h>
#include <string.h>

int main( void )
{
   int  fh;
   char buffer[500];

   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )
   {
      char buff[50];
      _strerror_s( buff, sizeof(buff), NULL );
      printf( buff );
      exit( -1 );
   }

   if( _read( fh, buffer, 500 ) > 0 )
      printf( "Current file position is: %d\n", _tell( fh ) );
   _close( fh );
}
```

### <a name="input-crt_telltxt"></a>Eingabe: crt_tell.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Current file position is: 20
```

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
