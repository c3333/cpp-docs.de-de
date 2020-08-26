---
title: _exec- und _wexec-Funktionen
ms.date: 11/04/2016
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
ms.openlocfilehash: ecfcf88b09a4383fc050e9737a0ffe7203f9a050
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839724"
---
# <a name="_exec-_wexec-functions"></a>_exec- und _wexec-Funktionen

Jede Funktion in dieser Familie lädt einen neuen Prozess und führt ihn aus:

:::row:::
   :::column span="":::
      [_execl _wexecl](../c-runtime-library/reference/execl-wexecl.md)\
      [_execv _wexecv](../c-runtime-library/reference/execv-wexecv.md)\
      [_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)
   :::column-end:::
   :::column span="":::
      [_execve _wexecve](../c-runtime-library/reference/execve-wexecve.md)\
      [_execlp _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)\
      [_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)
   :::column-end:::
   :::column span="":::
      [_execlpe _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)\
      [_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)
   :::column-end:::
:::row-end:::

Der Buchstabe am Ende des Funktionsnamens bestimmt die Variante.

|_exec-Funktionssuffix|Beschreibung|
|----------------------------|-----------------|
|`e`|`envp`: Array von Zeigern zu Umgebungseinstellungen, wird an den neuen Prozess übergeben.|
|`l`|Befehlszeilenargumente werden einzeln an die `_exec`-Funktion übergeben. Wird normalerweise verwendet, wenn die Anzahl der Parameter im neuen Prozess im Voraus bekannt ist.|
|`p`|Die `PATH`-Umgebungsvariable wird verwendet, um die auszuführende Datei zu suchen.|
|`v`|`argv`: Array von Zeigern zu Befehlszeilenargumenten, wird an die `_exec`-Funktion übergeben. Wird normalerweise verwendet, wenn die Anzahl der Parameter im neuen Prozess variabel ist.|

## <a name="remarks"></a>Bemerkungen

Jede `_exec`-Funktion lädt einen neuen Prozess und führt ihn aus. Alle `_exec`-Funktionen verwenden die gleiche Betriebssystemfunktion ([CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)). Die `_exec`-Funktionen behandeln ggf. automatisch Argumente mit Multibyte-Zeichenfolgen, wobei Multibyte-Zeichensequenzen entsprechend der derzeit verwendeten Multibyte-Codepage erkannt werden. Die `_wexec`-Funktionen sind Breitzeichenversionen der `_exec`-Funktionen. Die `_wexec`-Funktionen verhalten sich genauso wie ihre entsprechenden `_exec`-Familien, allerdings behandeln sie keine Multibyte-Zeichenfolgen.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_texecl`|`_execl`|`_execl`|`_wexecl`|
|`_texecle`|`_execle`|`_execle`|`_wexecle`|
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|
|`_texecv`|`_execv`|`_execv`|`_wexecv`|
|`_texecve`|`_execve`|`_execve`|`_wexecve`|
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|

Der `cmdname`-Parameter gibt die Datei an, die als neuer Prozess ausgeführt werden soll. Er kann einen vollständigen Pfad (ausgehend vom Stamm), einen partiellen Pfad (im aktuellen Arbeitsverzeichnis) oder einen Dateinamen angeben. Wenn `cmdname` keine Dateinamenerweiterung hat oder nicht mit einem Punkt (.) endet, sucht die `_exec`-Funktion nach der benannten Datei. Wenn die Suche fehlschlägt, versucht die Funktion denselben Basisnamen mit der COM-Dateinamenerweiterung und dann mit den EXE-, BAT- und CMD-Dateinamenerweiterungen. Wenn `cmdname` eine Dateinamenerweiterung hat, wird nur diese Erweiterung in der Suche verwendet. Wenn `cmdname` mit einem Punkt endet, sucht die `_exec`-Funktion nach `cmdname` ohne Dateinamenerweiterung. `_execlp`, `_execlpe`, `_execvp` und `_execvpe` suchen in den Verzeichnissen, die durch die `cmdname`-Umgebungsvariable angegeben werden, nach `PATH` (mithilfe des gleichen Verfahrens). Wenn der `cmdname`-Parameter eine Laufwerkangabe oder einen Schrägstrich enthält (d. h., wenn er ein relativer Pfad ist), sucht der `_exec`-Aufruf nur nach der angegebenen Datei. Der Pfad wird nicht gesucht.

Parameter werden an den neuen Prozess übergeben, indem ein oder mehrere Zeiger als Parameter im `_exec`-Aufruf an die Zeichenfolgen übergeben werden. Diese Zeichenfolgen bilden die Parameterliste für den neuen Prozess. Die kombinierte Länge der geerbten Umgebungseinstellungen und der Zeichenfolgen, die die Parameterliste für den neuen Prozess bilden, darf 32 KB nicht überschreiten. Das abschließende Nullzeichen ('\0') für jede Zeichenfolge ist nicht in der Zählung enthalten, es werden jedoch die Leerzeichen gezählt (sie werden automatisch eingefügt, um die Parameter zu trennen).

> [!NOTE]
> Die in den Zeichenfolgen eingebetteten Leerzeichen können zu einem unerwarteten Verhalten führen. Zum Beispiel führt die Zeichenfolge `_exec` durch die Übergabe von `"hi there"` dazu, dass der neue Prozess zwei Argumente erhält: `"hi"` und `"there"`. Wenn der neue Prozess die benannte Datei "hi there" öffnen sollte, schlägt der Prozess fehl. Sie können dies verhindern, indem Sie die Zeichenfolge in Anführungszeichen setzen: `"\"hi there\""`.

> [!IMPORTANT]
> Übergeben Sie Benutzereingaben nicht an `_exec`, ohne den Inhalt explizit zu überprüfen. `_exec` führt zu einem Aufruf von [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw). Beachten Sie daher, dass nicht qualifizierte Pfadnamen zu potenziellen Sicherheitslücken führen können.

Die `_exec`-Funktionen überprüfen ihre Parameter. Wenn erwartete Parameter NULL-Zeiger oder leere Zeichenfolgen sind bzw. ausgelassen werden, ruft die `_exec`-Funktion den Handler für ungültige Parameter auf, wie unter [Parametervalidierung](../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, stellen diese Funktionen `errno` auf `EINVAL` ein und geben -1 zurück. Es wird kein neuer Prozess ausgeführt.

Die Argumentzeiger können als separate Parameter übergeben werden (in `_execl`, `_execle`, `_execlp` und `_execlpe`) oder als ein Array von Zeigern (in `_execv`, `_execve`, `_execvp` und `_execvpe`). Es muss mindestens ein Parameter, nämlich `arg0`, an den neuen Prozess übergeben werden. Dieser Parameter ist `argv`[0] des neuen Prozesses. Normalerweise ist dieser Parameter eine Kopie von `cmdname`. (Ein anderer Wert erzeugt keinen Fehler.)

Die `_execl`-, `_execle`-, `_execlp`- und `_execlpe`-Aufrufe werden normalerweise verwendet, wenn die Anzahl der Parameter im Voraus bekannt ist. Der `arg0`-Parameter ist normalerweise ein Zeiger auf `cmdname`. Die Parameter von `arg1` bis `argn` weisen auf die Zeichenfolgen hin, aus denen die neue Parameterliste besteht. Ein NULL-Zeiger muss `argn` folgen, um das Ende der Parameterliste zu markieren.

Die `_execv`-, `_execve`-, `_execvp`- und `_execvpe`-Aufrufe sind nützlich, wenn die Anzahl der Parameter im neuen Prozess variabel ist. Zeiger auf Parameter werden als Array, nämlich `argv`, übergeben. Der `argv`[0]-Parameter ist normalerweise ein Zeiger auf `cmdname`. Die Parameter von `argv`[1] bis `argv`[`n`] weisen auf die Zeichenfolgen hin, aus denen die neue Parameterliste besteht. Der `argv`[`n`+1]-Parameter muss ein **NULL**-Zeiger sein, um das Ende der Parameterliste zu markieren.

Dateien, die beim Aufrufen von `_exec` geöffnet waren, bleiben im neuen Prozess geöffnet. Bei `_execl`-, `_execlp`-, `_execv`- und `_execvp`-Aufrufen erbt der neue Prozess die Umgebung des aufrufenden Prozesses. `_execle`-, `_execlpe`-, `_execve`- und `_execvpe`-Aufrufe ändern die Umgebung für den neuen Prozess, indem eine Liste der Umgebungseinstellungen durch den `envp`-Parameter übergeben wird. `envp` ist ein Array von Zeichenzeigern, von denen jedes Element (außer dem letzten Element) auf eine auf NULL endende Zeichenfolge verweist, die eine Umgebungsvariable definiert. Solch eine Zeichenfolge hat normalerweise die Form `NAME`=`value`, wobei `NAME` der Name einer Umgebungsvariable und `value` der Zeichenfolgenwert ist, für den diese Variable festgelegt wird. (Beachten Sie, dass `value` nicht in doppelte Anführungszeichen eingeschlossen ist.) Das letzte Element des `envp` Arrays muss **null**sein. Wenn `envp` selbst **NULL** ist, erbt der neue Prozess die Umgebungseinstellungen des aufrufenden Prozesses.

Ein Programm, das mit einer der `_exec`-Funktionen ausgeführt wird, wird immer in den Speicher geladen, als ob das Feld für die maximale Speicherbelegung in der Kopfzeile der EXE-Datei des Programms auf den Standardwert "0xFFFFH" festgelegt wäre.

Die `_exec`-Aufrufe behalten keine Übersetzungsmodi von geöffneten Dateien bei. Wenn der neue Prozess Dateien verwenden muss, die vom aufrufenden Prozess geerbt wurden, verwenden Sie die [_setmode](../c-runtime-library/reference/setmode.md)-Routine, um den Übersetzungsmodus dieser Dateien auf den gewünschten Modus einzustellen. Vor dem `fflush`-Funktionsaufruf müssen Sie jeden Stream explizit leeren (mithilfe von `_flushall` oder `_exec`) oder explizit schließen. In den neuen Prozessen, die durch Aufrufe der `_exec`-Routinen erstellt werden, werden Signaleinstellungen nicht beibehalten. Die Signaleinstellungen werden im neuen Prozess auf die Standardwerte zurückgesetzt.

## <a name="example"></a>Beispiel

```c
// crt_args.c
// Illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
// This program will be executed by crt_exec which follows.

#include <stdio.h>

int main( int argc,  // Number of strings in array argv
char *argv[],       // Array of command-line argument strings
char **envp )       // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf( "  %s\n", *(envp++) );

    return;
}
```

Führen Sie das folgende Programm aus, um "Crt_args.exe" auszuführen:

```c
// crt_exec.c
// Illustrates the different versions of exec, including
//      _execl          _execle          _execlp          _execlpe
//      _execv          _execve          _execvp          _execvpe
//
// Although CRT_EXEC.C can exec any program, you can verify how
// different versions handle arguments and environment by
// compiling and specifying the sample program CRT_ARGS.C. See
// "_spawn, _wspawn Functions" for examples of the similar spawn
// functions.

#include <stdio.h>
#include <conio.h>
#include <process.h>

char *my_env[] =     // Environment for exec?e
{
   "THIS=environment will be",
   "PASSED=to new process by",
   "the EXEC=functions",
   NULL
};

int main( int ac, char* av[] )
{
   char *args[4];
   int ch;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );
      return;
   }

   // Arguments for _execv?
   args[0] = av[1];
   args[1] = "exec??";
   args[2] = "two";
   args[3] = NULL;

   switch( atoi( av[2] ) )
   {
   case 1:
      _execl( av[1], av[1], "_execl", "two", NULL );
      break;
   case 2:
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );
      break;
   case 3:
      _execlp( av[1], av[1], "_execlp", "two", NULL );
      break;
   case 4:
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );
      break;
   case 5:
      _execv( av[1], args );
      break;
   case 6:
      _execve( av[1], args, my_env );
      break;
   case 7:
      _execvp( av[1], args );
      break;
   case 8:
      _execvpe( av[1], args, my_env );
      break;
   default:
      break;
   }

   // This point is reached only if exec fails.
   printf( "\nProcess was not execed." );
   exit( 0 );
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** process.h

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../c-runtime-library/process-and-environment-control.md)<br/>
[Abbruch](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn, _wspawn Funktionen](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
