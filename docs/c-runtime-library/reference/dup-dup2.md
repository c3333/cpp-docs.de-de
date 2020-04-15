---
title: _dup, _dup2
ms.date: 4/2/2020
api_name:
- _dup
- _dup2
- _o__dup
- _o__dup2
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
- _dup2
- _dup
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
ms.openlocfilehash: 239f857bb40c9609cb6f7ff373295a7a1f8523a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348115"
---
# <a name="_dup-_dup2"></a>_dup, _dup2

Erstellt einen zweiten Dateideskriptor für eine geöffnete Datei (**_dup**) oder weist einen Dateideskriptor (**_dup2**) neu zu.

## <a name="syntax"></a>Syntax

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parameter

*fd*, *fd1*<br/>
Dateideskriptoren, die auf die geöffnete Datei verweisen.

*fd2*<br/>
Jeder beliebige Dateideskriptor.

## <a name="return-value"></a>Rückgabewert

**_dup** gibt einen neuen Dateideskriptor zurück. **_dup2** gibt 0 zurück, um den Erfolg anzuzeigen. Wenn ein Fehler auftritt, gibt jede Funktion -1 zurück und setzt **errno** auf **EBADF,** wenn der Dateideskriptor ungültig ist, oder auf **EMFILE,** wenn keine weiteren Dateideskriptoren verfügbar sind. Bei einem ungültigen Dateideskriptor ruft die Funktion auch den Handler für ungültige Parameter auf, wie unter [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_dup-** und **_dup2-Funktionen** verknüpfen einen zweiten Dateideskriptor mit einer aktuell geöffneten Datei. Diese Funktionen können verwendet werden, um einen vordefinierten Dateideskriptor, z. B. den für **stdout**, einer anderen Datei zuzuordnen. Das Durchführen von Operationen an der Datei ist mit jedem der beiden Dateideskriptoren möglich. Der für die Datei zulässige Zugriffstyp ist von der Erstellung eines neuen Deskriptors nicht betroffen. **_dup** gibt den nächsten verfügbaren Dateideskriptor für die angegebene Datei zurück. **_dup2** zwingt *fd2,* auf dieselbe Datei wie *fd1*zu verweisen. Wenn *fd2* zum Zeitpunkt des Aufrufs einer geöffneten Datei zugeordnet ist, wird diese Datei geschlossen.

Sowohl **_dup** **als auch _dup2** Dateideskriptoren als Parameter akzeptieren. Um einen Stream`FILE *`( ) an eine dieser Funktionen zu übergeben, verwenden Sie [_fileno](fileno.md). Die **fileno-Routine** gibt den Dateideskriptor zurück, der derzeit dem angegebenen Stream zugeordnet ist. Das folgende Beispiel zeigt, wie **stderr** (definiert als `FILE *` in Stdio.h) einem Dateideskriptor zugeordnet wird:

```C
int cstderr = _dup( _fileno( stderr ));
```

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

Die Konsole wird in UWP-Apps (Universelle Windows-Plattform) nicht unterstützt. Die Standard-Stream-Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor C-Laufzeitfunktionen sie in UWP-Apps verwenden können. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_dup.c
// This program uses the variable old to save
// the original stdout. It then opens a new file named
// DataFile and forces stdout to refer to it. Finally, it
// restores stdout to its original state.

#include <io.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int old;
   FILE *DataFile;

   old = _dup( 1 );   // "old" now refers to "stdout"
                      // Note:  file descriptor 1 == "stdout"
   if( old == -1 )
   {
      perror( "_dup( 1 ) failure" );
      exit( 1 );
   }
   _write( old, "This goes to stdout first\n", 26 );
   if( fopen_s( &DataFile, "data", "w" ) != 0 )
   {
      puts( "Can't open file 'data'\n" );
      exit( 1 );
   }

   // stdout now refers to file "data"
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )
   {
      perror( "Can't _dup2 stdout" );
      exit( 1 );
   }
   puts( "This goes to file 'data'\n" );

   // Flush stdout stream buffer so it goes to correct file
   fflush( stdout );
   fclose( DataFile );

   // Restore original stdout
   _dup2( old, 1 );
   puts( "This goes to stdout\n" );
   puts( "The file 'data' contains:" );
   _flushall();
   system( "type data" );
}
```

```Output
This goes to stdout first
This goes to stdout

The file 'data' contains:
This goes to file 'data'
```

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
