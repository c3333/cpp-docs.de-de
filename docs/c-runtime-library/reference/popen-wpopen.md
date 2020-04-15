---
title: _popen, _wpopen
description: Eine Referenz für die Bibliotheksfunktionen _popen der Microsoft _wpopenC-Laufzeit (CRT) und .
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5b478893ef8f201f39cb63ecfc7ab174d16b86de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338516"
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

*Befehl*\
Befehl, der ausgeführt werden soll.

*Modus*\
Modus des zurückgegebenen Streams.

## <a name="return-value"></a>Rückgabewert

Gibt einen Stream zurück, der einem Ende der erstellten Pipe zugeordnet ist. Das andere Ende der Pipe ist der Standardeingabe oder Standardausgabe des erzeugten Befehls zugeordnet. Die Funktionen geben bei einem Fehler **NULL** zurück. Wenn der Fehler durch einen ungültigen Parameter verursacht wird, wird **errno** auf **EINVAL**gesetzt. Gültige Modi können Sie dem Abschnitt mit den Hinweisen entnehmen.

Weitere Informationen über diese und andere Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_popen-Funktion** erstellt eine Pipe. Anschließend wird asynchron eine erstellte Kopie des Befehlsprozessors ausgeführt und der *Befehl* als Befehlszeile verwendet. Die Zeichenfolge *mode* gibt den angeforderten Zugriffstyp wie folgt an.

|Zugriffsmodus|BESCHREIBUNG|
|-|-|
|**"r"**|Der aufrufende Prozess kann die Standardausgabe des erzeugten Befehls mit dem zurückgegebenen Stream lesen.|
|**"w"**|Der aufrufende Prozess kann die Standardeingabe des erzeugten Befehls mit dem zurückgegebenen Stream schreiben.|
|**"b"**|Öffnen im binären Modus.|
|**"t"**|Öffnen im Textmodus.|

> [!NOTE]
> Wenn die _popen Funktion **in** einem Windows-Programm verwendet wird, gibt sie einen ungültigen Dateizeiger zurück, der dazu führt, dass das Programm nicht mehr unbegrenzt reagiert. **_popen** funktioniert in einer Konsolenanwendung ordnungsgemäß. Informationen zum Erstellen einer Windows-Anwendung, die Ein- und Ausgabe umleitet, finden Sie unter [Erstellen eines untergeordneten Prozesses mit umgeleiteter Eingabe und Ausgabe](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) im Windows SDK.

**_wpopen** ist eine breit gefächerte Version von **_popen**; Das *Pfadargument* zu **_wpopen** ist eine Zeichenfolge mit großen Zeichen. **_wpopen** und **_popen** verhalten sich ansonsten gleich.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

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

Bei dieser Ausgabe wird davon ausgegangen, dass sich `.c` nur eine Datei im aktuellen Verzeichnis mit der Dateinamenerweiterung befindet.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Siehe auch

[Prozess- und Umgebungskontrolle](../../c-runtime-library/process-and-environment-control.md)\
[_pclose](pclose.md)\
[_pipe](pipe.md)
