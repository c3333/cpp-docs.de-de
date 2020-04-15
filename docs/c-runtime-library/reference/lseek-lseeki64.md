---
title: _lseek, _lseeki64
ms.date: 4/2/2020
api_name:
- _lseeki64
- _lseek
- _o__lseek
- _o__lseeki64
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
- _lseeki64
- _lseek
- lseeki64
helpviewer_keywords:
- lseek function
- _lseek function
- _lseeki64 function
- lseeki64 function
- file pointers [C++], moving
- seek file pointers
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
ms.openlocfilehash: d35b3db157d4f33e3a8490c6620a08000ff090f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341615"
---
# <a name="_lseek-_lseeki64"></a>_lseek, _lseeki64

Verschiebt einen Dateizeiger zum angegebenen Speicherort.

## <a name="syntax"></a>Syntax

```C
long _lseek(
   int fd,
   long offset,
   int origin
);
__int64 _lseeki64(
   int fd,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Dateideskriptor, der auf eine geöffnete Datei verweist.

*offset*<br/>
Anzahl von Bytes von *origin*.

*Ursprung*<br/>
Ursprüngliche Position

## <a name="return-value"></a>Rückgabewert

**_lseek** gibt den Offset der neuen Position vom Anfang der Datei in Bytes zurück. **_lseeki64** gibt den Offset in einer 64-Bit-Ganzzahl zurück. Die Funktion gibt -1L zurück, um einen Fehler anzuzeigen. Wenn ein ungültiger Parameter übergeben wird, z.B. ein fehlerhafter Dateideskriptor, oder der Wert für *origin* oder die von *offset* festgelegte Position vor dem Anfang der Datei ungültig ist, wird der Handler für ungültige Parameter aufgerufen, so wie unter [Parameter Validation (Parametervalidierung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EBADF** und geben -1L zurück. Auf Geräten, die über keine Suchfunktion verfügen (z.B. Terminals oder Drucker), ist der Rückgabewert undefiniert.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_lseek-Funktion** verschiebt den Dateizeiger, der fd zugeordnet *ist,* an eine neue Position, die *Versatzbytes* vom *Ursprung*ist. Der nächste Vorgang für die Datei tritt am neuen Speicherort auf. Das Argument *origin* muss Teil der folgenden Konstante sein, die allesamt in „Stdio.h“ definiert sind.

|*Ursprungswert*||
|-|-|
| **SEEK_SET** | Anfang der Datei |
| **SEEK_CUR** | Aktuelle Position des Dateizeigers |
| **SEEK_END** | Ende der Datei |

Sie können **_lseek** verwenden, um den Zeiger an einer beliebigen Stelle in einer Datei oder über das Ende der Datei hinaus neu zu positionieren.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_lseek**|\<io.h>|
|**_lseeki64**|\<io.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_lseek.c
/* This program first opens a file named lseek.txt.
* It then uses _lseek to find the beginning of the file,
* to find the current position in the file, and to find
* the end of the file.
*/

#include <io.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh;
   long pos;               /* Position of file pointer */
   char buffer[10];

   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );

   /* Seek the beginning of the file: */
   pos = _lseek( fh, 0L, SEEK_SET );
   if( pos == -1L )
      perror( "_lseek to beginning failed" );
   else
      printf( "Position for beginning of file seek = %ld\n", pos );

   /* Move file pointer a little */
    _read( fh, buffer, 10 );

   /* Find current position: */
   pos = _lseek( fh, 0L, SEEK_CUR );
   if( pos == -1L )
      perror( "_lseek to current position failed" );
   else
      printf( "Position for current position seek = %ld\n", pos );

   /* Set the end of the file: */
   pos = _lseek( fh, 0L, SEEK_END );
   if( pos == -1L )
      perror( "_lseek to end failed" );
   else
      printf( "Position for end of file seek = %ld\n", pos );

   _close( fh );
}
```

### <a name="input-crt_lseekc_input"></a>Eingabe: crt_lseek.c_input

```Input
Line one.
Line two.
Line three.
Line four.
Line five.
```

### <a name="output"></a>Output

```Output
Position for beginning of file seek = 0
Position for current position seek = 10
Position for end of file seek = 57
```

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
