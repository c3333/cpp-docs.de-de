---
title: _popen, _wpopen
description: Ein Verweis auf die Funktionen _popen der Microsoft C-Lauf Zeit Bibliothek ( _wpopenCRT) und.
ms.date: 4/2/2020
api_name:
- _popen
- _wpopen
- _o__popen
- _o__wpopen
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
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
no-loc:
- _popen
- _wpopen
- _tpopen
- _doserrno
- errno
- _sys_errlist
- _sys_nerr
- EINVAL
ms.openlocfilehash: 37e5bb491234e46a0e3330bc2fd42c16e54793fc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915290"
---
# <a name="_popen-_wpopen"></a>_popen, _wpopen

Erstellt eine Pipe und führt einen Befehl aus.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>Parameter

*s*\
Befehl, der ausgeführt werden soll.

*Spar*\
Modus des zurückgegebenen Streams.

## <a name="return-value"></a>Rückgabewert

Gibt einen Stream zurück, der einem Ende der erstellten Pipe zugeordnet ist. Das andere Ende der Pipe ist der Standardeingabe oder Standardausgabe des erzeugten Befehls zugeordnet. Die Funktionen geben bei einem Fehler **NULL** zurück. Wenn der Fehler durch einen ungültigen Parameter verursacht wird, wird **errno** auf **EINVAL**festgelegt. Gültige Modi können Sie dem Abschnitt mit den Hinweisen entnehmen.

Weitere Informationen über diese und andere Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_popen** -Funktion erstellt eine Pipe. Anschließend führt Sie asynchron eine generierte Kopie des Befehls Prozessors aus und verwendet den *Befehl* als Befehlszeile. Die Zeichenfolge *mode* gibt den angeforderten Zugriffstyp wie folgt an.

|Zugriffsmodus|Beschreibung|
|-|-|
|**r**|Der aufrufende Prozess kann die Standardausgabe des erzeugten Befehls mit dem zurückgegebenen Stream lesen.|
|**Löw**|Der aufrufende Prozess kann die Standardeingabe des erzeugten Befehls mit dem zurückgegebenen Stream schreiben.|
|**b**|Öffnen im binären Modus.|
|**Bund**|Öffnen im Textmodus.|

> [!NOTE]
> Wenn die **_popen** -Funktion in einem Windows-Programm verwendet wird, gibt Sie einen ungültigen Dateizeiger zurück, der bewirkt, dass das Programm unbegrenzt nicht mehr reagiert. **_popen** funktioniert ordnungsgemäß in einer Konsolenanwendung. Informationen zum Erstellen einer Windows-Anwendung, die die Eingabe und Ausgabe umleitet, finden Sie unter [Erstellen eines untergeordneten Prozesses mit umgeleiteter Eingabe und Ausgabe](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) in der Windows SDK.

**_wpopen** ist eine breit Zeichen Version von **_popen**. Das *path* -Argument für **_wpopen** ist eine Zeichenfolge mit breit Zeichen. **_wpopen** und **_popen** Verhalten sich andernfalls identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      puts(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

Bei dieser Ausgabe wird davon ausgegangen, dass das aktuelle Verzeichnis nur eine Datei mit `.c` einer Dateinamenerweiterung enthält.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)\
[_pclose](pclose.md)\
[_pipe](pipe.md)
