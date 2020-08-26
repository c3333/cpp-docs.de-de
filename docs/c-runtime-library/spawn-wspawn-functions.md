---
title: _spawn-, _wspawn-Funktionen
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
ms.openlocfilehash: 2f6aa420d7e6bb736721c4a68ff6451121da26ab
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840413"
---
# <a name="_spawn-_wspawn-functions"></a>_spawn-, _wspawn-Funktionen

Jede der `_spawn`-Funktionen erstellt einen neuen Prozess und führt ihn aus:

:::row:::
   :::column span="":::
      [_spawnl _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)\
      [_spawnle _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)\
      [_spawnlp _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)\
      [_spawnlpe _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)\
   :::column-end:::
   :::column span="":::
      [_spawnv _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)\
      [_spawnve _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)\
      [_spawnvp _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)\
      [_spawnvpe _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)\
   :::column-end:::
:::row-end:::

Die Buchstaben am Ende des Funktionsnamens bestimmen die Variante.

|Buchstabe|Variant|
|-|-|
| `e`  | `envp`: Array von Zeigern zu Umgebungseinstellungen, wird an den neuen Prozess übergeben.  |
| `l`  | Befehlszeilenargumente werden einzeln an die `_spawn`-Funktion übergeben. Dieses Suffix wird normalerweise verwendet, wenn die Anzahl der Parameter im neuen Prozess im Voraus bekannt ist.  |
| `p`  | Die `PATH`-Umgebungsvariable wird verwendet, um die auszuführende Datei zu suchen.  |
| `v`  | `argv`: Array von Zeigern zu Befehlszeilenargumenten, wird an die `_spawn`-Funktion übergeben. Dieses Suffix wird normalerweise verwendet, wenn die Anzahl der Parameter im neuen Prozess variabel ist.  |

## <a name="remarks"></a>Bemerkungen

Die `_spawn`-Funktionen erstellen und führen einen neuen Prozess aus. Sie behandeln Multibyte-Zeichenfolgenargumente automatisch richtig. Die Erkennung von Multibyte-Zeichenfolgen erfolgt auf der Grundlage der aktuell verwendeten Multibyte-Codeseite. Die `_wspawn`-Funktionen sind Breitzeichenversionen der `_spawn`-Funktionen; sie behandeln keine Multibyte-Zeichenfolgen. Andernfalls verhalten sich die `_wspawn`-Funktionen genauso wie ihre `_spawn`-Gegenstücke.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|

Zum Laden und Ausführen des neuen Prozesses muss ausreichend Speicher vorhanden sein. Das `mode`-Argument bestimmt, welche Aktion durch den aufrufenden Prozess vor und während `_spawn` durchgeführt wird. Die folgenden Werte für `mode` sind in Process.h definiert:

|Wert|Beschreibung|
|-|-|
| `_P_OVERLAY`  | Überlagert einen aufrufenden Prozess mit einem neuen Prozess, wobei der aufrufende Prozess vernichtet wird (gleiche Auswirkung wie `_exec`-Aufrufe).  |
| `_P_WAIT`  | Hält einen aufrufenden Thread bis zum Abschluss der Ausführung des neuen Prozesses an (synchrones `_spawn`).  |
| `_P_NOWAIT` oder `_P_NOWAITO`  | Setzt die Ausführung eines aufrufenden Prozesses gleichzeitig mit dem neuen Prozess fort (asynchrones `_spawn`).  |
| `_P_DETACH`  | Setzt die Ausführung des aufrufenden Prozesses fort; der neue Prozess wird im Hintergrund ohne Zugriff auf Konsole oder Tastatur ausgeführt. Aufrufe von `_cwait` gegen den neuen Prozess schlagen fehl (asynchrones `_spawn`).  |

Die `cmdname`-Argument gibt die Datei an, die als neuer Prozess ausgeführt wird, und kann einen vollständigen Pfad (über den Stamm), einen partiellen Pfad (über das aktuelle Arbeitsverzeichnis) oder nur einen Dateinamen angeben. Wenn `cmdname` keine Dateierweiterung hat oder nicht mit einem Punkt (.) endet, testet die `_spawn`-Funktion zunächst die Erweiterung .com und dann die Erweiterung .exe, die Erweiterung .bat und schließlich die Erweiterung .cmd.

Wenn `cmdname` eine Dateierweiterung hat, wird nur diese Erweiterung verwendet. Wenn `cmdname` mit einem Punkt endet, sucht die `_spawn`-Funktion nach `cmdname` ohne Dateierweiterung. `_spawnlp`, `_spawnlpe`, `_spawnvp` und `_spawnvpe` suchen in den Verzeichnissen, die durch die `PATH`-Umgebungsvariable angegeben werden, nach `cmdname` (mithilfe des gleichen Verfahrens).

Wenn der `cmdname`-Parameter eine Laufwerksangabe oder einen Schrägstrich enthält (d.h., wenn er ein relativer Pfad ist), sucht der `_spawn`-Aufruf nur nach der angegebenen Datei. Der Pfad wird nicht gesucht.

In der Vergangenheit haben einige dieser Funktionen `errno` bei Erfolg auf null gesetzt; das aktuelle Verhalten lässt `errno` gemäß dem C-Standard unverändert. Wenn Sie das alte Verhalten emulieren müssen, setzen Sie `errno` auf null, unmittelbar bevor Sie diese Funktionen aufrufen.

> [!NOTE]
> Um eine ordnungsgemäße Überlagerungsinitialisierung und -beendigung sicherzustellen, verwenden Sie die Funktion `setjmp` oder `longjmp` nicht, um eine Überlagerungsroutine einzugeben oder zu verlassen.

## <a name="arguments-for-the-spawned-process"></a>Argumente für den erzeugten Prozess

Um Argumente an den neuen Prozess zu übergeben, geben Sie mindestens einen Zeiger auf Zeichenfolgen als Argument im `_spawn`-Aufruf an. Diese Zeichenfolgen bilden die Argumentliste für den erzeugten Prozess. Die kombinierte Länge der Zeichenfolgen, die die Argumentliste für den neuen Prozess bilden, darf 1024 Bytes nicht überschreiten. Das abschließende NULL-Zeichen ('\0') für jede Zeichenfolge ist nicht in der Zählung enthalten. Es werden jedoch die Leerzeichen berücksichtigt (sie werden automatisch eingefügt, um Argumente zu trennen).

> [!NOTE]
> Die in den Zeichenfolgen eingebetteten Leerzeichen können zu einem unerwarteten Verhalten führen. Zum Beispiel führt die Zeichenfolge `_spawn` durch die Übergabe von `"hi there"` dazu, dass der neue Prozess zwei Argumente erhält: `"hi"` und `"there"`. Wenn der neue Prozess die benannte Datei "hi there" öffnen sollte, schlägt der Prozess fehl. Sie können dies verhindern, indem Sie die Zeichenfolge in Anführungszeichen setzen: `"\"hi there\""`.

> [!IMPORTANT]
> Übergeben Sie Benutzereingaben nicht an `_spawn`, ohne den Inhalt explizit zu überprüfen. `_spawn` führt zu einem Aufruf von [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw). Beachten Sie daher, dass nicht qualifizierte Pfadnamen zu potenziellen Sicherheitslücken führen können.

Sie können Argumentzeiger als separate Parameter übergeben (in `_spawnl`, `_spawnle`, `_spawnlp` und `_spawnlpe`) oder als ein Array von Zeigern (in `_spawnv`, `_spawnve`, `_spawnvp` und `_spawnvpe`). Sie müssen mindestens ein Argument, `arg0` oder `argv`[0], an den erzeugten Prozess übergeben. Gemäß Konvention ist dieses Argument der Name des Programms so, wie Sie ihn auf der Befehlszeile eingeben würden. Ein anderer Wert erzeugt keinen Fehler.

Die `_spawnl`-, `_spawnle`-, `_spawnlp`- und `_spawnlpe`-Aufrufe werden normalerweise verwendet, wenn die Anzahl der Argumente im Voraus bekannt ist. Das `arg0`-Argument ist normalerweise ein Zeiger auf `cmdname`. Die Argumente `arg1` bis `argn` sind Zeiger auf Zeichenfolgen, die die Argumentliste neu bilden. Nach `argn` muss ein **NULL**-Zeiger stehen, mit dem das Ende der Argumentliste markiert wird.

Die `_spawnv`-, `_spawnve`-, `_spawnvp`- und `_spawnvpe`-Aufrufe sind nützlich, wenn die Anzahl der Argumente im neuen Prozess variabel ist. Zeiger auf Argumente werden als Array, `argv`*, übergeben.* Das `argv`[0]-Argument ist gewöhnlich ein Zeiger auf einen Pfad im Echtzeitmodus oder auf den Programmnamen im geschützten Modus und `argv`[1] bis `argv`[`n`] sind Zeiger auf die Zeichenfolgen, die die neue Argumentliste bilden. Das Argument `argv`[`n` +1] muss ein **NULL**-Zeiger sein, um das Ende der Argumentliste zu markieren.

## <a name="environment-of-the-spawned-process"></a>Umgebung des erzeugten Prozesses

Dateien, die bei einem `_spawn`-Aufruf geöffnet waren, bleiben im neuen Prozess geöffnet. Bei `_spawnl`-, `_spawnlp`-, `_spawnv`- und `_spawnvp`-Aufrufen erbt der neue Prozess die Umgebung des aufrufenden Prozesses. Sie können mit `_spawnle`-, `_spawnlpe`-, `_spawnve`- und `_spawnvpe`-Aufrufen die Umgebung für den neuen Prozess ändern, indem eine Liste der Umgebungseinstellungen durch das `envp`-Argument übergeben wird. Das Argument `envp` ist ein Array von Zeichenzeigern, von denen jedes Element (außer dem letzten Element) auf eine auf NULL endende Zeichenfolge verweist, die eine Umgebungsvariable definiert. Solch eine Zeichenfolge hat normalerweise die Form `NAME`=`value`, wobei `NAME` der Name einer Umgebungsvariable und `value` der Zeichenfolgenwert ist, für den diese Variable festgelegt wird. (Beachten Sie, dass `value` nicht in doppelte Anführungszeichen eingeschlossen ist.) Das letzte Element des `envp` Arrays muss **null**sein. Wenn `envp` selbst **NULL** ist, erbt der generierte Prozess die Umgebungseinstellungen des übergeordneten Prozesses.

Die `_spawn`-Funktionen können alle Informationen über geöffnete Dateien, auch den Übersetzungsmodus, an den neuen Prozess übergeben. Diese Informationen werden im Echtzeitmodus über den `C_FILE_INFO`-Eintrag in der Umgebung übergeben. Der Startcode verarbeitet normalerweise diesen Eintrag und löscht ihn dann aus der Umgebung. Wenn jedoch eine `_spawn`-Funktion einen anderen als einen C-Prozess erzeugt, verbleibt der Eintrag in der Umgebung. Durch Drucken der Umgebung werden Grafikzeichen in der Definitionszeichenfolge für diesen Eintrag angezeigt, da die Umgebungsinformationen in binärer Form im Echtzeitmodus übergeben werden. Dies sollte keine andere Auswirkung auf den normalen Betrieb haben. Im geschützten Modus werden die Umgebungsinformationen in Textform übergeben und enthalten daher keine Grafikzeichen.

Vor dem `_spawn`-Funktionsaufruf müssen Sie jeden Stream explizit leeren (mithilfe von `fflush` oder `_flushall`) oder explizit schließen.

Neue Prozesse, die durch Aufrufe von `_spawn`-Routinen erstellt werden, behalten keine Signaleinstellungen bei. Stattdessen setzt der erzeugte Prozess die Signaleinstellungen auf die Standardeinstellungen zurück.

## <a name="redirecting-output"></a>Umleitung der Ausgabe

Wenn Sie `_spawn` über eine DLL- oder eine GUI-Anwendung aufrufen und die Ausgabe zu einer Pipe umleiten möchten, haben Sie zwei Möglichkeiten:

- Verwenden Sie die Win32-API zum Erstellen einer Pipe, rufen Sie dann [AllocConsole](/windows/console/allocconsole) auf, legen Sie die Handlewerte in der Startstruktur fest, und rufen Sie [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) auf.

- Rufen Sie [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md) auf, das eine Pipe erstellt und die Anwendung mit **cmd.exe/c** (oder **command.exe/c**) aufruft.

## <a name="example"></a>Beispiel

```c
// crt_spawn.c
// This program accepts a number in the range
// 1-8 from the command line. Based on the number it receives,
// it executes one of the eight different procedures that
// spawn the process named child. For some of these procedures,
// the CHILD.EXE file must be in the same directory; for
// others, it only has to be in the same path.
//

#include <stdio.h>
#include <process.h>

char *my_env[] =
{
   "THIS=environment will be",
   "PASSED=to child.exe by the",
   "_SPAWNLE=and",
   "_SPAWNLPE=and",
   "_SPAWNVE=and",
   "_SPAWNVPE=functions",
   NULL
};

int main( int argc, char *argv[] )
{
   char *args[4];

   // Set up parameters to be sent:
   args[0] = "child";
   args[1] = "spawn??";
   args[2] = "two";
   args[3] = NULL;

   if (argc <= 2)
   {
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }

   switch (argv[1][0])   // Based on first letter of argument
   {
   case '1':
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );
      break;
   case '2':
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",
               NULL, my_env );
      break;
   case '3':
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );
      break;
   case '4':
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",
                NULL, my_env );
      break;
   case '5':
      _spawnv( _P_OVERLAY, argv[2], args );
      break;
   case '6':
      _spawnve( _P_OVERLAY, argv[2], args, my_env );
      break;
   case '7':
      _spawnvp( _P_OVERLAY, argv[2], args );
      break;
   case '8':
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );
      break;
   default:
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }
   printf( "from SPAWN!\n" );
}
```

```Output
child process output
from SPAWN!
```

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../c-runtime-library/process-and-environment-control.md)<br/>
[Abbruch](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec, _wexec Funktionen](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
